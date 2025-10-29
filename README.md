# Kali NetHunter for KernelSU Next

Flashable Kali NetHunter module for rooted Android with Magisk or KernelSU Next. Bundles NetHunter apps, BusyBox, HID/NFC tools, wallpapers, and Kali chroot, then auto-detects your root manager to stage files and hook BusyBox via post-fs-data. Flash once, finalize inside the NetHunter app, and you're ready to pentest on mobile.

## Features

- **Cross-Root Compatibility**: Works with both Magisk and KernelSU Next by auto-detecting the environment.
- **Complete NetHunter Suite**: Includes NetHunter, NetHunter Terminal, NetHunter KeX, NetHunter Store, and privileged extension apps.
- **BusyBox Integration**: Installs NetHunter's BusyBox with full applet symlinks.
- **HID/NFC Tools**: Bundles HID keyboard and NFC utilities.
- **Kali Chroot Support**: Sets up the Kali Linux chroot environment.
- **Wallpaper and Boot Animation**: Includes custom NetHunter wallpapers and boot animation.
- **Addon.d Backup**: Supports system backup and restore via addon.d scripts.
- **Post-FS-Data Hooks**: Ensures BusyBox and scripts are available early in boot.

## Requirements

- Rooted Android device with either Magisk (v20.4+) or KernelSU Next installed.
- Sufficient storage space (at least 500MB free for the module and chroot).
- Android 8.0+ (Oreo) or higher for optimal app installation.

## Installation

### Step 1: Download the Original NetHunter Module

1. Download the official Kali NetHunter module ZIP from the [NetHunter Store](https://store.nethunter.com/) or GitHub releases (look for the latest `kali-nethunter-*-arm64-*.zip`).

### Step 2: Extract Required Files

1. Unzip the downloaded NetHunter module ZIP.
2. Locate the `data/app/` folder and `kalifs-minimal-arm64.tar.xz` file inside the extracted archive.
3. Copy `data/app/` and `kalifs-minimal-arm64.tar.xz` to the root folder of this repository (where `module.prop`, `post-fs-data.sh`, etc., are located).

### Step 3: Repackage the Module

1. Ensure all files are in the correct structure (no extra top-level folders).
2. Zip the entire contents into a new ZIP file (e.g., `nethunter-ksu.zip`). Use a command like:
   ```bash
   cd /path/to/repo
   zip -r ../nethunter-ksu.zip *
   ```

### Step 4: Flash via KernelSU

1. Transfer the ZIP to your device.
2. Open KernelSU Manager.
3. Go to the module installation section.
4. Select and flash the ZIP.
5. Reboot your device.
6. Open the NetHunter app and complete the setup (update via NetHunter Store if prompted).

## Usage

- After installation, launch the NetHunter app to access the full suite.
- Use NetHunter Terminal for command-line access.
- NetHunter KeX provides a graphical desktop environment.
- The chroot is automatically mounted on boot; use `bootkali` scripts for manual control.

## Troubleshooting

- **Installation Fails**: Ensure the ZIP is correctly packaged without nested folders. Check KernelSU logs for errors.
- **Apps Not Installing**: Verify your Android version; system apps require Android 8+.
- **BusyBox Not Working**: Check `/data/adb/ksu/modules/<moduleId>/system/bin/` for symlinks after reboot.
- **Chroot Issues**: Ensure `kalifs-minimal-arm64.tar.xz` is present and valid.
- **Kernel Flashing**: Only supported under Magisk; skipped in KernelSU.

## Project Background

This project adapts the official Kali NetHunter Magisk module for compatibility with KernelSU Next. The original NetHunter module is designed exclusively for Magisk, limiting users on KernelSU-based root solutions. By modifying the installer scripts to detect and handle KernelSU environments, this fork enables NetHunter on a broader range of rooted devices. Changes include fallback utilities, adjusted module paths, and conditional logic to bypass Magisk-specific features while maintaining full functionality.

## Contributing

Contributions are welcome! Fork the repo, make changes, and submit a pull request. Please test on both Magisk and KernelSU setups.

## License

This project is based on the official Kali NetHunter module. Refer to the original license for terms. Modifications are provided under the same or compatible license.
