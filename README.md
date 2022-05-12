# swift_make_thumbnail_image_out_of_video_extension

```swift

extension URL {
    
    func makeThumbnail() -> UIImage? {
        do {
            let asset: AVURLAsset = AVURLAsset(url: self, options: nil)
            let imgGenerator: AVAssetImageGenerator = AVAssetImageGenerator(asset: asset)
            imgGenerator.appliesPreferredTrackTransform = true
            let cgImage: CGImage = try imgGenerator.copyCGImage(at: CMTime(value: 0, timescale: 1), actualTime: nil)
            let uiImage: UIImage = UIImage(cgImage: cgImage)
            return uiImage
        } catch {
            print("Error generating thumbnail: \(error)")
        }
        return nil
    }
    
}

```
