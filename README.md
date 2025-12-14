# ValheimExportHelper_LinuxCompat
AssetRipper plugin to make it easy to export Valheim to a Unity project - modified for ease of use on Linux.
This guide assumes that you have already installed [AssetRipper](https://github.com/AssetRipper/AssetRipper/releases/) 


## Linux Port Prerequisites -
Install .NET 7.0 Runtime

ValheimExportHelper requires .NET 7 runtime (even if .NET 9 is installed).

Download the official installer script:
```
cd /tmp
wget https://dot.net/v1/dotnet-install.sh
chmod +x dotnet-install.sh
```

Before we install, let's check to see what runtimes (if any) are already on the system:
```
dotnet --list-runtimes
```
<sup>You may not have any installed, or you may have several. If you see `Microsoft.NETCore.App 7.0.22 [/usr/lib/dotnet/shared/Microsoft.NETCore.App]` then you can skip this section. If you have alternate versions installed make note of what's here to ensure that these installs remain present, and `7.0.22` is added in the next steps. We'll check this again shortly.</sup>


Install .NET 7.0.22 runtime system-wide:
```
sudo ./dotnet-install.sh --runtime dotnet --version 7.0.22 --install-dir /usr/lib/dotnet
```

Verify installation:
```
dotnet --list-runtimes
```

Expected output:
```
Microsoft.NETCore.App 7.0.22 [/usr/lib/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 9.0.11 [/usr/lib/dotnet/shared/Microsoft.NETCore.App]
```
- (You can have multiple runtimes side by side; the host picks the correct one based on the app’s runtimeconfig.)
- Your output may vary if you have additional runtimes installed, the important thing is that you see `7.0.22` present in this list, and that none are missing from when we checked earlier.


## Building / Running -
### Clone & Build
Clone this repo to your machine. Navigate to the `ValheimExportHelper` directory containing `ValheimExportHelper.cs` and run:
```
dotnet build -c Release
```

Files will be generated in the subfolder `/bin/Release/net7.0` - copy these files to your `AssetRipper` directory (where `AssetRipper.exe` is located).

### Download Zip
1. Download ValheimExportHelper.zip from the releases section.
2. Extract all contents of downloaded zip folder to your `AssetRipper` directory (where `AssetRipper.exe` is located).

## Usage
1. Launch with `./ValheimExportHelper` or `dotnet ValheimExportHelper.dll` and proceed to load and extract Valheim as normal.

The following options are recommended:
- [x] **Skip StreamingAssets Folder**
- [x] **Ignore Engine Assets**
- **Shader Export Format:** Yaml Asset

Make any other changes at your own risk, the only other supported option is changing **Script Export Format** from *Decompiled* to *Dll Export Without Renaming*.


## Developing
Should be able to compile out of the box without any extra steps.

## Credit
Forked From [heinermann/ValheimExportHelper](https://github.com/heinermann/ValheimExportHelper)



