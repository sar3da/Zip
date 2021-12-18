![Zip - Zip and unzip files in Swift](https://cloud.githubusercontent.com/assets/889949/12374908/252373d0-bcac-11e5-8ece-6933aeae8222.png)

[![Build Status](https://travis-ci.org/marmelroy/Zip.svg?branch=master)](https://travis-ci.org/marmelroy/Zip) [![Version](http://img.shields.io/cocoapods/v/Zip.svg)](http://cocoapods.org/?q=Zip) [![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage) [![SPM supported](https://img.shields.io/badge/SPM-supported-brightgreen.svg?style=flat)](https://swift.org/package-manager)


# Zip
A Swift framework for zipping and unzipping files. Simple and quick to use. Built on top of [minizip](https://github.com/nmoinvaz/minizip).

## Usage

Import Zip at the top of the Swift file.

```swift
import Zip
```

## Quick functions

The easiest way to use Zip is through quick functions. Both take local file paths as NSURLs, throw if an error is encountered and return an NSURL to the destination if successful.
```swift
do {
 
    let documentsDirectory = FileManager.default.urls(for:.documentDirectory, in: .userDomainMask)[0]
    let zipFilePath = documentsDirectory.appendingPathComponent("\("name Folder Saved")/\("name File Zip")")
    let unzipped = try Zip.quickUnzipFile(zipFilePath, "name Folder Saved") // Unzip
                    
}
catch {
  print("Something went wrong")
}
```

## Advanced Zip

For more advanced usage, Zip has functions that let you set custom  destination paths, work with password protected zips and use a progress handling closure. These functions throw if there is an error but don't return.
```swift
do {
                    
                    let documentsURL = try FileManager.default.url(for: .documentDirectory,in: .userDomainMask,appropriateFor: nil,create: false)
                    let zipFilePath = documentsDirectory.appendingPathComponent("\("name Folder Saved")/\("name File Zip")")
                    try Zip.unzipFile(zipFilePath, destination: documentsURL, overwrite: true, password: "", progress: { (progress) -> () in
                        print(progress)
                        if progress == 1 {
                            //self.closed = true
                            print(Finished)
                        }
                    })
                    
                }
                catch {
                    print("Something went wrong")
                }
```

## Custom File Extensions

Zip supports '.zip' and '.cbz' files out of the box. To support additional zip-derivative file extensions:
```swift
Zip.addCustomFileExtension("file-extension-here")
```

### [Preferred] Setting up with [Swift Package Manager](https://swift.org/package-manager)
To use Zip with Swift Package Manager, add it to your package's dependencies:
```swift
.package(url: "https://github.com/sar3da/Zip.git", .upToNextMinor(from: "2.1.0"))
```

### Setting up with [CocoaPods](http://cocoapods.org/?q=Zip)
```ruby
source 'https://github.com/CocoaPods/Specs.git'
pod 'Zip', '~> 2.1.0'
```

### Setting up with [Carthage](https://github.com/Carthage/Carthage)
To integrate Zip into your Xcode project using Carthage, specify it in your `Cartfile`:

```ogdl
github "sar3da/Zip" ~> 2.1.0
```

