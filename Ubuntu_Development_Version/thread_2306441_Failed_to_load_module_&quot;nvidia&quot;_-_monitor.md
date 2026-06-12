---
title: "Failed to load module &quot;nvidia&quot; - monitor not detected"
date: 2015-12-15
forum: Ubuntu Development Version
---

### Post by VMC on 2015-12-15
I have found out that nvidia will not load, using proprietary, tested (see below.)
I found and followed [this thread]("http://ubuntuforums.org/showthread.php?t=2279938"), since it describes my situation exactly.

This occurs on any current Ubuntu.

Here are my log files - Xorg.0.log, kern.log. I grep for nvidia and found the errors.

Xorg:
```
[    15.057] 
X.Org X Server 1.17.3
Release Date: 2015-10-26
[    15.058] X Protocol Version 11, Revision 0
[    15.058] Build Operating System: Linux 3.19.0-33-generic x86_64 Ubuntu
[    15.058] Current Operating System: Linux 14 4.3.0-2-generic #11-Ubuntu SMP Fri Dec 4 20:37:48 UTC 2015 x86_64
[    15.058] Kernel command line: BOOT_IMAGE=/vmlinuz root=UUID=107bf235-82e7-4095-8e55-397abe9ab3b3 ro splash quiet
[    15.058] Build Date: 25 November 2015  04:17:13PM
[    15.058] xorg-server 2:1.17.3-2ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    15.058] Current version of pixman: 0.33.4
[    15.058]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.058] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.058] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 14 16:40:32 2015
[    15.068] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.068] (==) No Layout section.  Using the first Screen section.
[    15.068] (==) No screen section available. Using defaults.
[    15.068] (**) |-->Screen "Default Screen Section" (0)
[    15.068] (**) |   |-->Monitor "<default monitor>"
[    15.069] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    15.069] (==) Automatically adding devices
[    15.069] (==) Automatically enabling devices
[    15.069] (==) Automatically adding GPU devices
[    15.069] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.069]     Entry deleted from font path.
[    15.069] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.069]     Entry deleted from font path.
[    15.069] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.069]     Entry deleted from font path.
[    15.069] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.069]     Entry deleted from font path.
[    15.069] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.069]     Entry deleted from font path.
[    15.069] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    15.069] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.069] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.069] (II) Loader magic: 0x565129158da0
[    15.069] (II) Module ABI versions:
[    15.069]     X.Org ANSI C Emulation: 0.4
[    15.069]     X.Org Video Driver: 19.0
[    15.069]     X.Org XInput driver : 21.0
[    15.069]     X.Org Server Extension : 9.0
[    15.070] (EE) systemd-logind: failed to get session: PID 689 does not belong to any known session
[    15.071] (--) PCI:*(0:0:13:0) 10de:03d0:103c:2a99 rev 162, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xf9000000/16777216, BIOS @ 0x????????/131072
[    15.071] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    15.071] (II) "glx" will be loaded by default.
[    15.071] (II) LoadModule: "glx"
[    15.075] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    15.416] (II) Module glx: vendor="NVIDIA Corporation"
[    15.416]     compiled for 4.0.2, module version = 1.0.0
[    15.416]     Module class: X.Org Server Extension
[    15.416] (II) NVIDIA GLX Module  304.131  Sun Nov  8 22:03:20 PST 2015
[    15.416] (==) Matched nvidia as autoconfigured driver 0
[    15.416] (==) Matched nouveau as autoconfigured driver 1
[    15.416] (==) Matched modesetting as autoconfigured driver 2
[    15.416] (==) Matched fbdev as autoconfigured driver 3
[    15.416] (==) Matched vesa as autoconfigured driver 4
[    15.416] (==) Assigned the driver to the xf86ConfigLayout
[    15.416] (II) LoadModule: "nvidia"
[    15.416] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.464] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.464]     compiled for 4.0.2, module version = 1.0.0
[    15.464]     Module class: X.Org Video Driver
[    15.505] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    15.505] (EE) NVIDIA:     system's kernel log for additional error messages.
[    15.505] (II) UnloadModule: "nvidia"
[    15.505] (II) Unloading nvidia
[    15.505] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    15.505] (II) LoadModule: "nouveau"
[    15.505] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    15.514] (II) Module nouveau: vendor="X.Org Foundation"
[    15.514]     compiled for 1.17.1, module version = 1.0.11
[    15.514]     Module class: X.Org Video Driver
[    15.514]     ABI class: X.Org Video Driver, version 19.0
[    15.514] (II) LoadModule: "modesetting"
[    15.514] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    15.514] (II) Module modesetting: vendor="X.Org Foundation"
[    15.514]     compiled for 1.17.3, module version = 1.17.3
[    15.514]     Module class: X.Org Video Driver
[    15.514]     ABI class: X.Org Video Driver, version 19.0
[    15.514] (II) LoadModule: "fbdev"
[    15.514] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.514] (II) Module fbdev: vendor="X.Org Foundation"
[    15.514]     compiled for 1.17.1, module version = 0.4.4
[    15.514]     Module class: X.Org Video Driver
[    15.514]     ABI class: X.Org Video Driver, version 19.0
[    15.514] (II) LoadModule: "vesa"
[    15.515] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.515] (II) Module vesa: vendor="X.Org Foundation"
[    15.515]     compiled for 1.17.1, module version = 2.3.4
[    15.515]     Module class: X.Org Video Driver
[    15.515]     ABI class: X.Org Video Driver, version 19.0
[    15.515] (==) Matched nvidia as autoconfigured driver 0
[    15.515] (==) Matched nouveau as autoconfigured driver 1
[    15.515] (==) Matched modesetting as autoconfigured driver 2
[    15.515] (==) Matched fbdev as autoconfigured driver 3
[    15.515] (==) Matched vesa as autoconfigured driver 4
[    15.515] (==) Assigned the driver to the xf86ConfigLayout
[    15.515] (II) LoadModule: "nvidia"
[    15.515] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.515] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.515]     compiled for 4.0.2, module version = 1.0.0
[    15.515]     Module class: X.Org Video Driver
[    15.548] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    15.548] (EE) NVIDIA:     system's kernel log for additional error messages.
[    15.548] (II) UnloadModule: "nvidia"
[    15.548] (II) Unloading nvidia
[    15.549] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    15.549] (II) LoadModule: "nouveau"
[    15.549] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    15.549] (II) Module nouveau: vendor="X.Org Foundation"
[    15.549]     compiled for 1.17.1, module version = 1.0.11
[    15.549]     Module class: X.Org Video Driver
[    15.549]     ABI class: X.Org Video Driver, version 19.0
[    15.549] (II) UnloadModule: "nouveau"
[    15.549] (II) Unloading nouveau
[    15.549] (II) Failed to load module "nouveau" (already loaded, 0)
[    15.549] (II) LoadModule: "modesetting"
[    15.549] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    15.549] (II) Module modesetting: vendor="X.Org Foundation"
[    15.549]     compiled for 1.17.3, module version = 1.17.3
[    15.549]     Module class: X.Org Video Driver
[    15.549]     ABI class: X.Org Video Driver, version 19.0
[    15.549] (II) UnloadModule: "modesetting"
[    15.549] (II) Unloading modesetting
[    15.549] (II) Failed to load module "modesetting" (already loaded, 0)
[    15.549] (II) LoadModule: "fbdev"
[    15.549] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.549] (II) Module fbdev: vendor="X.Org Foundation"
[    15.549]     compiled for 1.17.1, module version = 0.4.4
[    15.549]     Module class: X.Org Video Driver
[    15.549]     ABI class: X.Org Video Driver, version 19.0
[    15.549] (II) UnloadModule: "fbdev"
[    15.549] (II) Unloading fbdev
[    15.549] (II) Failed to load module "fbdev" (already loaded, 0)
[    15.549] (II) LoadModule: "vesa"
[    15.549] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.549] (II) Module vesa: vendor="X.Org Foundation"
[    15.549]     compiled for 1.17.1, module version = 2.3.4
[    15.549]     Module class: X.Org Video Driver
[    15.549]     ABI class: X.Org Video Driver, version 19.0
[    15.549] (II) UnloadModule: "vesa"
[    15.549] (II) Unloading vesa
[    15.549] (II) Failed to load module "vesa" (already loaded, 0)
[    15.549] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    15.549] (II) NOUVEAU driver for NVIDIA chipset families :
[    15.549]     RIVA TNT        (NV04)
[    15.549]     RIVA TNT2       (NV05)
[    15.549]     GeForce 256     (NV10)
[    15.549]     GeForce 2       (NV11, NV15)
[    15.549]     GeForce 4MX     (NV17, NV18)
[    15.549]     GeForce 3       (NV20)
[    15.549]     GeForce 4Ti     (NV25, NV28)
[    15.549]     GeForce FX      (NV3x)
[    15.549]     GeForce 6       (NV4x)
[    15.549]     GeForce 7       (G7x)
[    15.549]     GeForce 8       (G8x)
[    15.549]     GeForce GTX 200 (NVA0)
[    15.549]     GeForce GTX 400 (NVC0)
[    15.549] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    15.549] (II) FBDEV: driver for framebuffer: fbdev
[    15.549] (II) VESA: driver for VESA chipsets: vesa
[    15.549] (++) using VT number 7

[    15.558] (EE) [drm] KMS not enabled
[    15.558] (EE) [drm] KMS not enabled
[    15.558] (EE) open /dev/dri/card0: No such file or directory
[    15.558] (EE) open /dev/dri/card0: No such file or directory
[    15.558] (WW) Falling back to old probe method for modesetting
[    15.558] (EE) open /dev/dri/card0: No such file or directory
[    15.558] (EE) open /dev/dri/card0: No such file or directory
[    15.558] (II) Loading sub module "fbdevhw"
[    15.558] (II) LoadModule: "fbdevhw"
[    15.558] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.558] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.558]     compiled for 1.17.3, module version = 0.0.2
[    15.558]     ABI class: X.Org Video Driver, version 19.0
[    15.558] (**) FBDEV(2): claimed PCI slot 0@0:13:0
[    15.558] (II) FBDEV(2): using default device
[    15.558] (WW) Falling back to old probe method for vesa
[    15.558] (EE) Screen 0 deleted because of no matching config section.
[    15.558] (II) UnloadModule: "modesetting"
[    15.558] (EE) Screen 0 deleted because of no matching config section.
[    15.558] (II) UnloadModule: "modesetting"
[    15.558] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 16/16
[    15.558] (==) FBDEV(0): Depth 16, (==) framebuffer bpp 16
[    15.558] (==) FBDEV(0): RGB weight 565
[    15.558] (==) FBDEV(0): Default visual is TrueColor
[    15.558] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.558] (II) FBDEV(0): hardware: VESA VGA (video memory: 1536kB)
[    15.559] (II) FBDEV(0): checking modes against framebuffer device...
[    15.559] (II) FBDEV(0): checking modes against monitor...
[    15.559] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    15.559] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[    15.559] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[    15.559] (==) FBDEV(0): DPI set to (96, 96)
[    15.559] (II) Loading sub module "fb"
[    15.559] (II) LoadModule: "fb"
[    15.559] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.559] (II) Module fb: vendor="X.Org Foundation"
[    15.559]     compiled for 1.17.3, module version = 1.0.0
[    15.559]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.559] (**) FBDEV(0): using shadow framebuffer
[    15.559] (II) Loading sub module "shadow"
[    15.559] (II) LoadModule: "shadow"
[    15.559] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.559] (II) Module shadow: vendor="X.Org Foundation"
[    15.559]     compiled for 1.17.3, module version = 1.1.0
[    15.559]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.559] (II) UnloadModule: "vesa"
[    15.559] (II) Unloading vesa
[    15.560] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    15.560] (==) FBDEV(0): Backing store enabled
[    15.560] (==) FBDEV(0): DPMS enabled
[    15.560] (==) RandR enabled
[    15.563] (II) SELinux: Disabled on system
[    15.571] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    15.597] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.606] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.606] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.606] (II) LoadModule: "evdev"
[    15.606] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.628] (II) Module evdev: vendor="X.Org Foundation"
[    15.628]     compiled for 1.17.1, module version = 2.9.2
[    15.628]     Module class: X.Org XInput Driver
[    15.628]     ABI class: X.Org XInput driver, version 21.0
[    15.628] (II) Using input driver 'evdev' for 'Power Button'
[    15.628] (**) Power Button: always reports core events
[    15.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    15.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.628] (--) evdev: Power Button: Found keys
[    15.628] (II) evdev: Power Button: Configuring as keyboard
[    15.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    15.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.628] (**) Option "xkb_rules" "evdev"
[    15.628] (**) Option "xkb_model" "pc105"
[    15.628] (**) Option "xkb_layout" "us"
[    15.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.629] (II) Using input driver 'evdev' for 'Power Button'
[    15.629] (**) Power Button: always reports core events
[    15.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    15.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.629] (--) evdev: Power Button: Found keys
[    15.629] (II) evdev: Power Button: Configuring as keyboard
[    15.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    15.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    15.629] (**) Option "xkb_rules" "evdev"
[    15.629] (**) Option "xkb_model" "pc105"
[    15.629] (**) Option "xkb_layout" "us"
[    15.629] (II) config/udev: Adding input device MLK wireless combo (/dev/input/event2)
[    15.629] (**) MLK wireless combo: Applying InputClass "evdev keyboard catchall"
[    15.629] (II) Using input driver 'evdev' for 'MLK wireless combo'
[    15.629] (**) MLK wireless combo: always reports core events
[    15.629] (**) evdev: MLK wireless combo: Device: "/dev/input/event2"
[    15.629] (--) evdev: MLK wireless combo: Vendor 0x4fc Product 0x5d8
[    15.629] (--) evdev: MLK wireless combo: Found keys
[    15.629] (II) evdev: MLK wireless combo: Configuring as keyboard
[    15.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/0003:04FC:05D8.0001/input/input5/event2"
[    15.630] (II) XINPUT: Adding extended input device "MLK wireless combo" (type: KEYBOARD, id 8)
[    15.630] (**) Option "xkb_rules" "evdev"
[    15.630] (**) Option "xkb_model" "pc105"
[    15.630] (**) Option "xkb_layout" "us"
[    15.630] (II) config/udev: Adding input device MLK wireless combo (/dev/input/event3)
[    15.630] (**) MLK wireless combo: Applying InputClass "evdev pointer catchall"
[    15.630] (**) MLK wireless combo: Applying InputClass "evdev keyboard catchall"
[    15.630] (II) Using input driver 'evdev' for 'MLK wireless combo'
[    15.630] (**) MLK wireless combo: always reports core events
[    15.630] (**) evdev: MLK wireless combo: Device: "/dev/input/event3"
[    15.630] (--) evdev: MLK wireless combo: Vendor 0x4fc Product 0x5d8
[    15.630] (--) evdev: MLK wireless combo: Found 9 mouse buttons
[    15.630] (--) evdev: MLK wireless combo: Found scroll wheel(s)
[    15.630] (--) evdev: MLK wireless combo: Found relative axes
[    15.630] (--) evdev: MLK wireless combo: Found x and y relative axes
[    15.630] (--) evdev: MLK wireless combo: Found absolute axes
[    15.630] (II) evdev: MLK wireless combo: Forcing absolute x/y axes to exist.
[    15.630] (--) evdev: MLK wireless combo: Found keys
[    15.630] (II) evdev: MLK wireless combo: Configuring as mouse
[    15.630] (II) evdev: MLK wireless combo: Configuring as keyboard
[    15.630] (II) evdev: MLK wireless combo: Adding scrollwheel support
[    15.630] (**) evdev: MLK wireless combo: YAxisMapping: buttons 4 and 5
[    15.630] (**) evdev: MLK wireless combo: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.630] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/0003:04FC:05D8.0002/input/input6/event3"
[    15.630] (II) XINPUT: Adding extended input device "MLK wireless combo" (type: KEYBOARD, id 9)
[    15.630] (**) Option "xkb_rules" "evdev"
[    15.630] (**) Option "xkb_model" "pc105"
[    15.630] (**) Option "xkb_layout" "us"
[    15.631] (II) evdev: MLK wireless combo: initialized for relative axes.
[    15.631] (WW) evdev: MLK wireless combo: ignoring absolute axes.
[    15.631] (**) MLK wireless combo: (accel) keeping acceleration scheme 1
[    15.631] (**) MLK wireless combo: (accel) acceleration profile 0
[    15.631] (**) MLK wireless combo: (accel) acceleration factor: 2.000
[    15.631] (**) MLK wireless combo: (accel) acceleration threshold: 4
[    15.631] (II) config/udev: Adding input device MLK wireless combo (/dev/input/mouse0)
[    15.631] (II) No input driver specified, ignoring this device.
[    15.631] (II) This device may have been added with another device file.
[    15.631] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event7)
[    15.631] (II) No input driver specified, ignoring this device.
[    15.631] (II) This device may have been added with another device file.
[    15.632] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event4)
[    15.632] (II) No input driver specified, ignoring this device.
[    15.632] (II) This device may have been added with another device file.
[    15.632] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event5)
[    15.632] (II) No input driver specified, ignoring this device.
[    15.632] (II) This device may have been added with another device file.
[    15.632] (II) config/udev: Adding input device HDA NVidia Line Out (/dev/input/event6)
[    15.632] (II) No input driver specified, ignoring this device.
[    15.632] (II) This device may have been added with another device file.
[    15.637] (EE) FBDEV(0): FBIOBLANK: Invalid argument
```

kern.log:
```
Dec 14 14:21:42 14 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 14 14:21:42 14 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 14 14:21:42 14 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Dec 14 14:21:42 14 kernel: [    0.000000] Linux version 4.3.0-2-generic (buildd@lgw01-24) (gcc version 5.2.1 20151129 (Ubuntu 5.2.1-27ubuntu1) ) #11-Ubuntu SMP Fri Dec 4 20:37:48 UTC 2015 (Ubuntu 4.3.0-2.11-generic 4.3.0)
Dec 14 14:21:42 14 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-2-generic root=UUID=107bf235-82e7-4095-8e55-397abe9ab3b3 ro
Dec 14 14:21:42 14 kernel: [    0.000000] KERNEL supported cpus:
Dec 14 14:21:42 14 kernel: [    0.000000]   Intel GenuineIntel
Dec 14 14:21:42 14 kernel: [    0.000000]   AMD AuthenticAMD
Dec 14 14:21:42 14 kernel: [    0.000000]   Centaur CentaurHauls
Dec 14 14:21:42 14 kernel: [    0.000000] tseg: 0000000000
Dec 14 14:21:42 14 kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
Dec 14 14:21:42 14 kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Dec 14 14:21:42 14 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cffaffff] usable
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffb0000-0x00000000cffbdfff] ACPI data
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffbe000-0x00000000cffeffff] ACPI NVS
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfff0000-0x00000000cfffffff] reserved
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Dec 14 14:21:42 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
Dec 14 14:21:42 14 kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 14 14:21:42 14 kernel: [    0.000000] SMBIOS 2.5 present.
Dec 14 14:21:42 14 kernel: [    0.000000] DMI: HP-Pavilion AY652AA-ABA s5310y/Narra6, BIOS 5.17    01/07/2010
Dec 14 14:21:42 14 kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Dec 14 14:21:42 14 kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Dec 14 14:21:42 14 kernel: [    0.000000] AGP: No AGP bridge found
Dec 14 14:21:42 14 kernel: [    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x400000000
Dec 14 14:21:42 14 kernel: [    0.000000] MTRR default type: uncachable
Dec 14 14:21:42 14 kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 14 14:21:42 14 kernel: [    0.000000]   00000-9FFFF write-back
Dec 14 14:21:42 14 kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 14 14:21:42 14 kernel: [    0.000000]   C0000-CFFFF write-protect
Dec 14 14:21:42 14 kernel: [    0.000000]   D0000-EFFFF uncachable
Dec 14 14:21:42 14 kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 14 14:21:42 14 kernel: [    0.000000] MTRR variable ranges enabled:
Dec 14 14:21:42 14 kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Dec 14 14:21:42 14 kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Dec 14 14:21:42 14 kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Dec 14 14:21:42 14 kernel: [    0.000000]   3 disabled
Dec 14 14:21:42 14 kernel: [    0.000000]   4 disabled
Dec 14 14:21:42 14 kernel: [    0.000000]   5 disabled
Dec 14 14:21:42 14 kernel: [    0.000000]   6 disabled
Dec 14 14:21:42 14 kernel: [    0.000000]   7 disabled
Dec 14 14:21:42 14 kernel: [    0.000000] TOM2: 0000000120000000 aka 4608M
Dec 14 14:21:42 14 kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Dec 14 14:21:42 14 kernel: [    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Dec 14 14:21:42 14 kernel: [    0.000000] e820: last_pfn = 0xcffb0 max_arch_pfn = 0x400000000
Dec 14 14:21:42 14 kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
Dec 14 14:21:42 14 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 14 14:21:42 14 kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Dec 14 14:21:42 14 kernel: [    0.000000] Using GB pages for direct mapping
Dec 14 14:21:42 14 kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Dec 14 14:21:42 14 kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Dec 14 14:21:42 14 kernel: [    0.000000] BRK [0x021f6000, 0x021f6fff] PGTABLE
Dec 14 14:21:42 14 kernel: [    0.000000] BRK [0x021f7000, 0x021f7fff] PGTABLE
Dec 14 14:21:42 14 kernel: [    0.000000] BRK [0x021f8000, 0x021f8fff] PGTABLE
Dec 14 14:21:42 14 kernel: [    0.000000] init_memory_mapping: [mem 0x11fe00000-0x11fffffff]
Dec 14 14:21:42 14 kernel: [    0.000000]  [mem 0x11fe00000-0x11fffffff] page 2M
Dec 14 14:21:42 14 kernel: [    0.000000] BRK [0x021f9000, 0x021f9fff] PGTABLE
Dec 14 14:21:42 14 kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11fdfffff]
Dec 14 14:21:42 14 kernel: [    0.000000]  [mem 0x100000000-0x11fdfffff] page 2M
Dec 14 14:21:42 14 kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xcffaffff]
Dec 14 14:21:42 14 kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Dec 14 14:21:42 14 kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Dec 14 14:21:42 14 kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Dec 14 14:21:42 14 kernel: [    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
Dec 14 14:21:42 14 kernel: [    0.000000]  [mem 0xcfe00000-0xcffaffff] page 4k
Dec 14 14:21:42 14 kernel: [    0.000000] RAMDISK: [mem 0x33d6e000-0x35eaefff]
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: Early table checksum verification disabled
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: RSDP 0x00000000000FB220 000014 (v00 HPQOEM)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: RSDT 0x00000000CFFB0000 000040 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: FACP 0x00000000CFFB0200 000084 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: DSDT 0x00000000CFFB0450 0043AF (v01 HPQOEM SLIC-CPC 00000001 INTL 20051117)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: FACS 0x00000000CFFBE000 000040
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: APIC 0x00000000CFFB0390 000080 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: MCFG 0x00000000CFFB0410 00003C (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: OEMB 0x00000000CFFBE040 000072 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: HPET 0x00000000CFFB4800 000038 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: SLIC 0x00000000CFFBE0C0 000176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: SSDT 0x00000000CFFB4840 000458 (v01 HPQOEM SLIC-CPC 00000001 AMD  00000001)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 14:21:42 14 kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Dec 14 14:21:42 14 kernel: [    0.000000] No NUMA configuration found
Dec 14 14:21:42 14 kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011fffffff]
Dec 14 14:21:42 14 kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x11fff9000-0x11fffdfff]
Dec 14 14:21:42 14 kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011ba00000-ffff88011f5fffff] on node 0
Dec 14 14:21:42 14 kernel: [    0.000000] Zone ranges:
Dec 14 14:21:42 14 kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Dec 14 14:21:42 14 kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Dec 14 14:21:42 14 kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000011fffffff]
Dec 14 14:21:42 14 kernel: [    0.000000] Movable zone start for each node
Dec 14 14:21:42 14 kernel: [    0.000000] Early memory node ranges
Dec 14 14:21:42 14 kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
Dec 14 14:21:42 14 kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x00000000cffaffff]
Dec 14 14:21:42 14 kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000011fffffff]
Dec 14 14:21:42 14 kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000011fffffff]
Dec 14 14:21:42 14 kernel: [    0.000000] On node 0 totalpages: 982862
Dec 14 14:21:42 14 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Dec 14 14:21:42 14 kernel: [    0.000000]   DMA zone: 21 pages reserved
Dec 14 14:21:42 14 kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Dec 14 14:21:42 14 kernel: [    0.000000]   DMA32 zone: 13247 pages used for memmap
Dec 14 14:21:42 14 kernel: [    0.000000]   DMA32 zone: 847792 pages, LIFO batch:31
Dec 14 14:21:42 14 kernel: [    0.000000]   Normal zone: 2048 pages used for memmap
Dec 14 14:21:42 14 kernel: [    0.000000]   Normal zone: 131072 pages, LIFO batch:31
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 14:21:42 14 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: IRQ14 used by override.
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: IRQ15 used by override.
Dec 14 14:21:42 14 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 14 14:21:42 14 kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Dec 14 14:21:42 14 kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcffb0000-0xcffbdfff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcffbe000-0xcffeffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcfff0000-0xcfffffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd0000000-0xfebfffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfeefffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffefffff]
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfff00000-0xffffffff]
Dec 14 14:21:42 14 kernel: [    0.000000] e820: [mem 0xd0000000-0xfebfffff] available for PCI devices
Dec 14 14:21:42 14 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 14 14:21:42 14 kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Dec 14 14:21:42 14 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Dec 14 14:21:42 14 kernel: [    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88011fc00000 s97304 r8192 d29672 u524288
Dec 14 14:21:42 14 kernel: [    0.000000] pcpu-alloc: s97304 r8192 d29672 u524288 alloc=1*2097152
Dec 14 14:21:42 14 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Dec 14 14:21:42 14 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 967482
Dec 14 14:21:42 14 kernel: [    0.000000] Policy zone: Normal
Dec 14 14:21:42 14 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-2-generic root=UUID=107bf235-82e7-4095-8e55-397abe9ab3b3 ro
Dec 14 14:21:42 14 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 14 14:21:42 14 kernel: [    0.000000] AGP: Checking aperture...
Dec 14 14:21:42 14 kernel: [    0.000000] AGP: No AGP bridge found
Dec 14 14:21:42 14 kernel: [    0.000000] AGP: Node 0: aperture [bus addr 0xc4000000-0xc5ffffff] (32MB)
Dec 14 14:21:42 14 kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Dec 14 14:21:42 14 kernel: [    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
Dec 14 14:21:42 14 kernel: [    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
Dec 14 14:21:42 14 kernel: [    0.000000] AGP: This costs you 64MB of RAM
Dec 14 14:21:42 14 kernel: [    0.000000] AGP: Mapping aperture over RAM [mem 0xc4000000-0xc7ffffff] (65536KB)
Dec 14 14:21:42 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
Dec 14 14:21:42 14 kernel: [    0.000000] Memory: 3685064K/3931448K available (8191K kernel code, 1251K rwdata, 3852K rodata, 1464K init, 1300K bss, 246384K reserved, 0K cma-reserved)
Dec 14 14:21:42 14 kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec 14 14:21:42 14 kernel: [    0.000000] Hierarchical RCU implementation.
Dec 14 14:21:42 14 kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Dec 14 14:21:42 14 kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Dec 14 14:21:42 14 kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
Dec 14 14:21:42 14 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:456 16
Dec 14 14:21:42 14 kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec 14 14:21:42 14 kernel: [    0.000000] Console: colour dummy device 80x25
Dec 14 14:21:42 14 kernel: [    0.000000] console [tty0] enabled
Dec 14 14:21:42 14 kernel: [    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 76450417870 ns
Dec 14 14:21:42 14 kernel: [    0.000000] hpet clockevent registered
Dec 14 14:21:42 14 kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Dec 14 14:21:42 14 kernel: [    0.000000] tsc: Detected 3013.704 MHz processor
Dec 14 14:21:42 14 kernel: [    0.000028] Calibrating delay loop (skipped), value calculated using timer frequency.. 6027.40 BogoMIPS (lpj=12054816)
Dec 14 14:21:42 14 kernel: [    0.000037] pid_max: default: 32768 minimum: 301
Dec 14 14:21:42 14 kernel: [    0.000045] ACPI: Core revision 20150818
Dec 14 14:21:42 14 kernel: [    0.002296] ACPI: 2 ACPI AML tables successfully acquired and loaded
Dec 14 14:21:42 14 kernel: [    0.002319] Security Framework initialized
Dec 14 14:21:42 14 kernel: [    0.002324] Yama: becoming mindful.
Dec 14 14:21:42 14 kernel: [    0.002339] AppArmor: AppArmor initialized
Dec 14 14:21:42 14 kernel: [    0.002578] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec 14 14:21:42 14 kernel: [    0.003653] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 14 14:21:42 14 kernel: [    0.004176] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Dec 14 14:21:42 14 kernel: [    0.004185] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Dec 14 14:21:42 14 kernel: [    0.004396] Initializing cgroup subsys io
Dec 14 14:21:42 14 kernel: [    0.004405] Initializing cgroup subsys memory
Dec 14 14:21:42 14 kernel: [    0.004416] Initializing cgroup subsys devices
Dec 14 14:21:42 14 kernel: [    0.004421] Initializing cgroup subsys freezer
Dec 14 14:21:42 14 kernel: [    0.004426] Initializing cgroup subsys net_cls
Dec 14 14:21:42 14 kernel: [    0.004431] Initializing cgroup subsys perf_event
Dec 14 14:21:42 14 kernel: [    0.004436] Initializing cgroup subsys net_prio
Dec 14 14:21:42 14 kernel: [    0.004441] Initializing cgroup subsys hugetlb
Dec 14 14:21:42 14 kernel: [    0.004447] Initializing cgroup subsys pids
Dec 14 14:21:42 14 kernel: [    0.004468] CPU: Physical Processor ID: 0
Dec 14 14:21:42 14 kernel: [    0.004472] CPU: Processor Core ID: 0
Dec 14 14:21:42 14 kernel: [    0.004476] mce: CPU supports 6 MCE banks
Dec 14 14:21:42 14 kernel: [    0.004484] LVT offset 0 assigned for vector 0xf9
Dec 14 14:21:42 14 kernel: [    0.004490] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Dec 14 14:21:42 14 kernel: [    0.004494] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64, 1GB 0
Dec 14 14:21:42 14 kernel: [    0.004707] Freeing SMP alternatives memory: 28K (ffffffff820a8000 - ffffffff820af000)
Dec 14 14:21:42 14 kernel: [    0.006165] ftrace: allocating 31335 entries in 123 pages
Dec 14 14:21:42 14 kernel: [    0.018515] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 14 14:21:42 14 kernel: [    0.165900] smpboot: CPU0: AMD Athlon(tm) II X2 250 Processor (family: 0x10, model: 0x6, stepping: 0x2)
Dec 14 14:21:42 14 kernel: [    0.165929] Performance Events: AMD PMU driver.
Dec 14 14:21:42 14 kernel: [    0.165936] ... version:                0
Dec 14 14:21:42 14 kernel: [    0.165939] ... bit width:              48
Dec 14 14:21:42 14 kernel: [    0.165942] ... generic registers:      4
Dec 14 14:21:42 14 kernel: [    0.165946] ... value mask:             0000ffffffffffff
Dec 14 14:21:42 14 kernel: [    0.165950] ... max period:             00007fffffffffff
Dec 14 14:21:42 14 kernel: [    0.165953] ... fixed-purpose events:   0
Dec 14 14:21:42 14 kernel: [    0.165956] ... event mask:             000000000000000f
Dec 14 14:21:42 14 kernel: [    0.166566] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Dec 14 14:21:42 14 kernel: [    0.166640] x86: Booting SMP configuration:
Dec 14 14:21:42 14 kernel: [    0.166645] .... node  #0, CPUs:      #1
Dec 14 14:21:42 14 kernel: [    0.179629] x86: Booted up 1 node, 2 CPUs
Dec 14 14:21:42 14 kernel: [    0.179635] smpboot: Total of 2 processors activated (12054.81 BogoMIPS)
Dec 14 14:21:42 14 kernel: [    0.180236] devtmpfs: initialized
Dec 14 14:21:42 14 kernel: [    0.183531] evm: security.selinux
Dec 14 14:21:42 14 kernel: [    0.183535] evm: security.SMACK64
Dec 14 14:21:42 14 kernel: [    0.183539] evm: security.SMACK64EXEC
Dec 14 14:21:42 14 kernel: [    0.183542] evm: security.SMACK64TRANSMUTE
Dec 14 14:21:42 14 kernel: [    0.183545] evm: security.SMACK64MMAP
Dec 14 14:21:42 14 kernel: [    0.183549] evm: security.ima
Dec 14 14:21:42 14 kernel: [    0.183552] evm: security.capability
Dec 14 14:21:42 14 kernel: [    0.183639] PM: Registering ACPI NVS region [mem 0xcffbe000-0xcffeffff] (204800 bytes)
Dec 14 14:21:42 14 kernel: [    0.183709] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Dec 14 14:21:42 14 kernel: [    0.183786] pinctrl core: initialized pinctrl subsystem
Dec 14 14:21:42 14 kernel: [    0.183897] RTC time: 14:21:31, date: 12/14/15
Dec 14 14:21:42 14 kernel: [    0.184008] NET: Registered protocol family 16
Dec 14 14:21:42 14 kernel: [    0.193949] cpuidle: using governor ladder
Dec 14 14:21:42 14 kernel: [    0.205957] cpuidle: using governor menu
Dec 14 14:21:42 14 kernel: [    0.205971] PCCT header not found.
Dec 14 14:21:42 14 kernel: [    0.205979] node 0 link 0: io port [1000, ffffff]
Dec 14 14:21:42 14 kernel: [    0.205982] TOM: 00000000e0000000 aka 3584M
Dec 14 14:21:42 14 kernel: [    0.205986] Fam 10h mmconf [mem 0xfc000000-0xfdffffff]
Dec 14 14:21:42 14 kernel: [    0.205988] node 0 link 0: mmio [fc000000, fdffffff] ==> none
Dec 14 14:21:42 14 kernel: [    0.205990] node 0 link 0: mmio [e0000000, fbffffff]
Dec 14 14:21:42 14 kernel: [    0.205992] node 0 link 0: mmio [fe000000, fe0bffff]
Dec 14 14:21:42 14 kernel: [    0.205993] node 0 link 0: mmio [a0000, bffff]
Dec 14 14:21:42 14 kernel: [    0.205995] TOM2: 0000000120000000 aka 4608M
Dec 14 14:21:42 14 kernel: [    0.205999] bus: [bus 00-07] on node 0 link 0
Dec 14 14:21:42 14 kernel: [    0.206000] bus: 00 [io  0x0000-0xffff]
Dec 14 14:21:42 14 kernel: [    0.206001] bus: 00 [mem 0xe0000000-0xfbffffff]
Dec 14 14:21:42 14 kernel: [    0.206002] bus: 00 [mem 0xfe000000-0xffffffff]
Dec 14 14:21:42 14 kernel: [    0.206003] bus: 00 [mem 0x000a0000-0x000bffff]
Dec 14 14:21:42 14 kernel: [    0.206004] bus: 00 [mem 0x120000000-0xfcffffffff]
Dec 14 14:21:42 14 kernel: [    0.206087] ACPI: bus type PCI registered
Dec 14 14:21:42 14 kernel: [    0.206091] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Dec 14 14:21:42 14 kernel: [    0.206176] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
Dec 14 14:21:42 14 kernel: [    0.206183] PCI: not using MMCONFIG
Dec 14 14:21:42 14 kernel: [    0.206187] PCI: Using configuration type 1 for base access
Dec 14 14:21:42 14 kernel: [    0.206190] PCI: Using configuration type 1 for extended access
Dec 14 14:21:42 14 kernel: [    0.206354] mtrr: your CPUs had inconsistent variable MTRR settings
Dec 14 14:21:42 14 kernel: [    0.206358] mtrr: probably your BIOS does not setup all CPUs.
Dec 14 14:21:42 14 kernel: [    0.206361] mtrr: corrected configuration.
Dec 14 14:21:42 14 kernel: [    0.218432] ACPI: Added _OSI(Module Device)
Dec 14 14:21:42 14 kernel: [    0.218440] ACPI: Added _OSI(Processor Device)
Dec 14 14:21:42 14 kernel: [    0.218444] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 14 14:21:42 14 kernel: [    0.218448] ACPI: Added _OSI(Processor Aggregator Device)
Dec 14 14:21:42 14 kernel: [    0.219533] ACPI: Executed 1 blocks of module-level executable AML code
Dec 14 14:21:42 14 kernel: [    0.220620] ACPI: Interpreter enabled
Dec 14 14:21:42 14 kernel: [    0.220631] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150818/hwxface-580)
Dec 14 14:21:42 14 kernel: [    0.220648] ACPI: (supports S0 S1 S3 S4 S5)
Dec 14 14:21:42 14 kernel: [    0.220651] ACPI: Using IOAPIC for interrupt routing
Dec 14 14:21:42 14 kernel: [    0.220681] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
Dec 14 14:21:42 14 kernel: [    0.221255] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
Dec 14 14:21:42 14 kernel: [    0.221267] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 14 14:21:42 14 kernel: [    0.224633] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 14 14:21:42 14 kernel: [    0.224642] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Dec 14 14:21:42 14 kernel: [    0.224754] acpi PNP0A03:00: _OSC: platform does not support [PCIeHotplug PME PCIeCapability]
Dec 14 14:21:42 14 kernel: [    0.224809] acpi PNP0A03:00: _OSC: not requesting control; platform does not support [PCIeCapability]
Dec 14 14:21:42 14 kernel: [    0.224817] acpi PNP0A03:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
Dec 14 14:21:42 14 kernel: [    0.224823] acpi PNP0A03:00: _OSC: platform willing to grant [AER]
Dec 14 14:21:42 14 kernel: [    0.224828] acpi PNP0A03:00: _OSC failed (AE_SUPPORT); disabling ASPM
Dec 14 14:21:42 14 kernel: [    0.224890] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1f] only partially covers this bridge
Dec 14 14:21:42 14 kernel: [    0.224988] PCI host bridge to bus 0000:00
Dec 14 14:21:42 14 kernel: [    0.224993] pci_bus 0000:00: root bus resource [bus 00-ff]
Dec 14 14:21:42 14 kernel: [    0.224998] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Dec 14 14:21:42 14 kernel: [    0.225003] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Dec 14 14:21:42 14 kernel: [    0.225007] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Dec 14 14:21:42 14 kernel: [    0.225014] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
Dec 14 14:21:42 14 kernel: [    0.225021] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfbffffff window]
Dec 14 14:21:42 14 kernel: [    0.225027] pci_bus 0000:00: root bus resource [mem 0xfe000000-0xfebfffff window]
Dec 14 14:21:42 14 kernel: [    0.225048] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
Dec 14 14:21:42 14 kernel: [    0.225230] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
Dec 14 14:21:42 14 kernel: [    0.225237] pci 0000:00:01.0: reg 0x10: [io  0x4f00-0x4fff]
Dec 14 14:21:42 14 kernel: [    0.225307] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
Dec 14 14:21:42 14 kernel: [    0.225320] pci 0000:00:01.1: reg 0x10: [io  0x4900-0x493f]
Dec 14 14:21:42 14 kernel: [    0.225334] pci 0000:00:01.1: reg 0x20: [io  0x4d00-0x4d3f]
Dec 14 14:21:42 14 kernel: [    0.225338] pci 0000:00:01.1: reg 0x24: [io  0x4e00-0x4e3f]
Dec 14 14:21:42 14 kernel: [    0.225355] pci 0000:00:01.1: PME# supported from D3hot D3cold
Dec 14 14:21:42 14 kernel: [    0.225382] pci 0000:00:01.1: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.225416] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
Dec 14 14:21:42 14 kernel: [    0.225483] pci 0000:00:02.0: [10de:03f1] type 00 class 0x0c0310
Dec 14 14:21:42 14 kernel: [    0.225494] pci 0000:00:02.0: reg 0x10: [mem 0xfbfff000-0xfbffffff]
Dec 14 14:21:42 14 kernel: [    0.225521] pci 0000:00:02.0: supports D1 D2
Dec 14 14:21:42 14 kernel: [    0.225522] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:21:42 14 kernel: [    0.225545] pci 0000:00:02.0: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.225582] pci 0000:00:02.1: [10de:03f2] type 00 class 0x0c0320
Dec 14 14:21:42 14 kernel: [    0.225594] pci 0000:00:02.1: reg 0x10: [mem 0xfbffec00-0xfbffecff]
Dec 14 14:21:42 14 kernel: [    0.225624] pci 0000:00:02.1: supports D1 D2
Dec 14 14:21:42 14 kernel: [    0.225625] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:21:42 14 kernel: [    0.225648] pci 0000:00:02.1: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.225689] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
Dec 14 14:21:42 14 kernel: [    0.225732] pci 0000:00:04.0: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.225768] pci 0000:00:05.0: [10de:03f0] type 00 class 0x040300
Dec 14 14:21:42 14 kernel: [    0.225781] pci 0000:00:05.0: reg 0x10: [mem 0xfbff8000-0xfbffbfff]
Dec 14 14:21:42 14 kernel: [    0.225810] pci 0000:00:05.0: PME# supported from D3hot D3cold
Dec 14 14:21:42 14 kernel: [    0.225832] pci 0000:00:05.0: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.225874] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
Dec 14 14:21:42 14 kernel: [    0.225885] pci 0000:00:07.0: reg 0x10: [mem 0xfbffd000-0xfbffdfff]
Dec 14 14:21:42 14 kernel: [    0.225889] pci 0000:00:07.0: reg 0x14: [io  0xe480-0xe487]
Dec 14 14:21:42 14 kernel: [    0.225910] pci 0000:00:07.0: supports D1 D2
Dec 14 14:21:42 14 kernel: [    0.225912] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:21:42 14 kernel: [    0.225940] pci 0000:00:07.0: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.225975] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
Dec 14 14:21:42 14 kernel: [    0.225984] pci 0000:00:08.0: reg 0x10: [io  0xe400-0xe407]
Dec 14 14:21:42 14 kernel: [    0.225988] pci 0000:00:08.0: reg 0x14: [io  0xe080-0xe083]
Dec 14 14:21:42 14 kernel: [    0.225992] pci 0000:00:08.0: reg 0x18: [io  0xe000-0xe007]
Dec 14 14:21:42 14 kernel: [    0.225995] pci 0000:00:08.0: reg 0x1c: [io  0xdc00-0xdc03]
Dec 14 14:21:42 14 kernel: [    0.225998] pci 0000:00:08.0: reg 0x20: [io  0xd880-0xd88f]
Dec 14 14:21:42 14 kernel: [    0.226002] pci 0000:00:08.0: reg 0x24: [mem 0xfbffc000-0xfbffcfff]
Dec 14 14:21:42 14 kernel: [    0.226057] pci 0000:00:08.1: [10de:03f6] type 00 class 0x010185
Dec 14 14:21:42 14 kernel: [    0.226066] pci 0000:00:08.1: reg 0x10: [io  0xd800-0xd807]
Dec 14 14:21:42 14 kernel: [    0.226070] pci 0000:00:08.1: reg 0x14: [io  0xd480-0xd483]
Dec 14 14:21:42 14 kernel: [    0.226074] pci 0000:00:08.1: reg 0x18: [io  0xd400-0xd407]
Dec 14 14:21:42 14 kernel: [    0.226077] pci 0000:00:08.1: reg 0x1c: [io  0xd080-0xd083]
Dec 14 14:21:42 14 kernel: [    0.226080] pci 0000:00:08.1: reg 0x20: [io  0xd000-0xd00f]
Dec 14 14:21:42 14 kernel: [    0.226084] pci 0000:00:08.1: reg 0x24: [mem 0xfbff7000-0xfbff7fff]
Dec 14 14:21:42 14 kernel: [    0.226145] pci 0000:00:09.0: [10de:03e8] type 01 class 0x060400
Dec 14 14:21:42 14 kernel: [    0.226167] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:21:42 14 kernel: [    0.226189] pci 0000:00:09.0: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.226225] pci 0000:00:0b.0: [10de:03e9] type 01 class 0x060400
Dec 14 14:21:42 14 kernel: [    0.226246] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:21:42 14 kernel: [    0.226269] pci 0000:00:0b.0: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.226305] pci 0000:00:0c.0: [10de:03e9] type 01 class 0x060400
Dec 14 14:21:42 14 kernel: [    0.226326] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:21:42 14 kernel: [    0.226348] pci 0000:00:0c.0: System wakeup disabled by ACPI
Dec 14 14:21:42 14 kernel: [    0.226383] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
Dec 14 14:21:42 14 kernel: [    0.226391] pci 0000:00:0d.0: reg 0x10: [mem 0xfa000000-0xfaffffff]
Dec 14 14:21:42 14 kernel: [    0.226396] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
Dec 14 14:21:42 14 kernel: [    0.226400] pci 0000:00:0d.0: reg 0x1c: [mem 0xf9000000-0xf9ffffff 64bit]
Dec 14 14:21:42 14 kernel: [    0.226405] pci 0000:00:0d.0: reg 0x30: [mem 0xfbfc0000-0xfbfdffff pref]
Dec 14 14:21:42 14 kernel: [    0.226464] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Dec 14 14:21:42 14 kernel: [    0.226514] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Dec 14 14:21:42 14 kernel: [    0.226562] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Dec 14 14:21:42 14 kernel: [    0.226609] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Dec 14 14:21:42 14 kernel: [    0.226659] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Dec 14 14:21:42 14 kernel: [    0.226759] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
Dec 14 14:21:42 14 kernel: [    0.226767] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
Dec 14 14:21:42 14 kernel: [    0.226769] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
Dec 14 14:21:42 14 kernel: [    0.226771] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
Dec 14 14:21:42 14 kernel: [    0.226772] pci 0000:00:04.0:   bridge window [mem 0x000d0000-0x000dffff window] (subtractive decode)
Dec 14 14:21:42 14 kernel: [    0.226774] pci 0000:00:04.0:   bridge window [mem 0xe0000000-0xfbffffff window] (subtractive decode)
Dec 14 14:21:42 14 kernel: [    0.226776] pci 0000:00:04.0:   bridge window [mem 0xfe000000-0xfebfffff window] (subtractive decode)
Dec 14 14:21:42 14 kernel: [    0.226800] pci 0000:00:09.0: PCI bridge to [bus 02]
Dec 14 14:21:42 14 kernel: [    0.226830] pci 0000:00:0b.0: PCI bridge to [bus 03]
Dec 14 14:21:42 14 kernel: [    0.226861] pci 0000:00:0c.0: PCI bridge to [bus 04]
Dec 14 14:21:42 14 kernel: [    0.226874] pci_bus 0000:00: on NUMA node 0
Dec 14 14:21:42 14 kernel: [    0.227205] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.227287] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.227368] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.227448] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.227528] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.227608] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.227688] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.227769] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.227851] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *14
Dec 14 14:21:42 14 kernel: [    0.227932] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *7
Dec 14 14:21:42 14 kernel: [    0.228014] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
Dec 14 14:21:42 14 kernel: [    0.228095] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
Dec 14 14:21:42 14 kernel: [    0.228177] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *10
Dec 14 14:21:42 14 kernel: [    0.228260] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
Dec 14 14:21:42 14 kernel: [    0.228340] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.228422] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
Dec 14 14:21:42 14 kernel: [    0.228504] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *5
Dec 14 14:21:42 14 kernel: [    0.228592] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Dec 14 14:21:42 14 kernel: [    0.228758] vgaarb: setting as boot device: PCI:0000:00:0d.0
Dec 14 14:21:42 14 kernel: [    0.228763] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
Dec 14 14:21:42 14 kernel: [    0.228770] vgaarb: loaded
Dec 14 14:21:42 14 kernel: [    0.228773] vgaarb: bridge control possible 0000:00:0d.0
Dec 14 14:21:42 14 kernel: [    0.229002] SCSI subsystem initialized
Dec 14 14:21:42 14 kernel: [    0.229069] libata version 3.00 loaded.
Dec 14 14:21:42 14 kernel: [    0.229090] ACPI: bus type USB registered
Dec 14 14:21:42 14 kernel: [    0.229108] usbcore: registered new interface driver usbfs
Dec 14 14:21:42 14 kernel: [    0.229120] usbcore: registered new interface driver hub
Dec 14 14:21:42 14 kernel: [    0.229135] usbcore: registered new device driver usb
Dec 14 14:21:42 14 kernel: [    0.229281] PCI: Using ACPI for IRQ routing
Dec 14 14:21:42 14 kernel: [    0.229917] PCI: pci_cache_line_size set to 64 bytes
Dec 14 14:21:42 14 kernel: [    0.229949] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Dec 14 14:21:42 14 kernel: [    0.229951] e820: reserve RAM buffer [mem 0xcffb0000-0xcfffffff]
Dec 14 14:21:42 14 kernel: [    0.230052] NetLabel: Initializing
Dec 14 14:21:42 14 kernel: [    0.230056] NetLabel:  domain hash size = 128
Dec 14 14:21:42 14 kernel: [    0.230059] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 14 14:21:42 14 kernel: [    0.230074] NetLabel:  unlabeled traffic allowed by default
Dec 14 14:21:42 14 kernel: [    0.230170] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Dec 14 14:21:42 14 kernel: [    0.230178] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Dec 14 14:21:42 14 kernel: [    0.230183] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Dec 14 14:21:42 14 kernel: [    0.232315] clocksource: Switched to clocksource hpet
Dec 14 14:21:42 14 kernel: [    0.238233] AppArmor: AppArmor Filesystem Enabled
Dec 14 14:21:42 14 kernel: [    0.238313] pnp: PnP ACPI init
Dec 14 14:21:42 14 kernel: [    0.238403] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 14 14:21:42 14 kernel: [    0.238520] system 00:01: [io  0x0a00-0x0adf] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238527] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 14:21:42 14 kernel: [    0.238796] system 00:02: [io  0x04d0-0x04d1] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238801] system 00:02: [io  0x0800-0x080f] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238806] system 00:02: [io  0x4000-0x407f] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.238811] system 00:02: [io  0x4080-0x40ff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238815] system 00:02: [io  0x4400-0x447f] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238820] system 00:02: [io  0x4480-0x44ff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238824] system 00:02: [io  0x4800-0x487f] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238829] system 00:02: [io  0x4880-0x48ff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238833] system 00:02: [io  0x4c00-0x4c7f] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238838] system 00:02: [io  0x4c80-0x4cff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238843] system 00:02: [mem 0x000d0000-0x000d3fff window] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238850] system 00:02: [mem 0x000d4000-0x000d7fff window] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238857] system 00:02: [mem 0x000de000-0x000dffff window] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238864] system 00:02: [mem 0xfec80000-0x1fd93ffff] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.238869] system 00:02: [mem 0xfefe0000-0xfefe01ff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238873] system 00:02: [mem 0xfefe1000-0xfefe1fff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238878] system 00:02: [mem 0xfee01000-0xfeefffff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238883] system 00:02: [mem 0xffb80000-0xffffffff] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.238888] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 14:21:42 14 kernel: [    0.238984] system 00:03: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.238989] system 00:03: [mem 0xfee00000-0xfee00fff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.238995] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 14:21:42 14 kernel: [    0.239048] system 00:04: [mem 0xfc000000-0xfdffffff] has been reserved
Dec 14 14:21:42 14 kernel: [    0.239054] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 14:21:42 14 kernel: [    0.239172] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.239177] system 00:05: [mem 0x000c0000-0x000cffff] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.239182] system 00:05: [mem 0x000e0000-0x000fffff] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.239187] system 00:05: [mem 0x00100000-0xdfffffff] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.239192] system 00:05: [mem 0xfec00000-0xffffffff] could not be reserved
Dec 14 14:21:42 14 kernel: [    0.239197] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 14 14:21:42 14 kernel: [    0.239408] pnp: PnP ACPI: found 6 devices
Dec 14 14:21:42 14 kernel: [    0.245846] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Dec 14 14:21:42 14 kernel: [    0.245870] pci 0000:00:04.0: PCI bridge to [bus 01]
Dec 14 14:21:42 14 kernel: [    0.245879] pci 0000:00:09.0: PCI bridge to [bus 02]
Dec 14 14:21:42 14 kernel: [    0.245886] pci 0000:00:0b.0: PCI bridge to [bus 03]
Dec 14 14:21:42 14 kernel: [    0.245892] pci 0000:00:0c.0: PCI bridge to [bus 04]
Dec 14 14:21:42 14 kernel: [    0.245899] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
Dec 14 14:21:42 14 kernel: [    0.245901] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
Dec 14 14:21:42 14 kernel: [    0.245903] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
Dec 14 14:21:42 14 kernel: [    0.245905] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
Dec 14 14:21:42 14 kernel: [    0.245906] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfbffffff window]
Dec 14 14:21:42 14 kernel: [    0.245908] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff window]
Dec 14 14:21:42 14 kernel: [    0.245910] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7 window]
Dec 14 14:21:42 14 kernel: [    0.245912] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff window]
Dec 14 14:21:42 14 kernel: [    0.245913] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff window]
Dec 14 14:21:42 14 kernel: [    0.245915] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff window]
Dec 14 14:21:42 14 kernel: [    0.245917] pci_bus 0000:01: resource 8 [mem 0xe0000000-0xfbffffff window]
Dec 14 14:21:42 14 kernel: [    0.245918] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff window]
Dec 14 14:21:42 14 kernel: [    0.245950] NET: Registered protocol family 2
Dec 14 14:21:42 14 kernel: [    0.246104] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Dec 14 14:21:42 14 kernel: [    0.246199] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Dec 14 14:21:42 14 kernel: [    0.246322] TCP: Hash tables configured (established 32768 bind 32768)
Dec 14 14:21:42 14 kernel: [    0.246363] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Dec 14 14:21:42 14 kernel: [    0.246389] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Dec 14 14:21:42 14 kernel: [    0.246468] NET: Registered protocol family 1
Dec 14 14:21:42 14 kernel: [    0.324483] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:21:42 14 kernel: [    0.324531] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:21:42 14 kernel: [    0.324577] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:21:42 14 kernel: [    0.324625] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:21:42 14 kernel: [    0.324672] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:21:42 14 kernel: [    0.324722] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:21:42 14 kernel: [    0.324773] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:21:42 14 kernel: [    0.324827] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:21:42 14 kernel: [    0.324835] pci 0000:00:0d.0: Video device with shadowed ROM
Dec 14 14:21:42 14 kernel: [    0.324844] PCI: CLS 64 bytes, default 64
Dec 14 14:21:42 14 kernel: [    0.324902] Trying to unpack rootfs image as initramfs...
Dec 14 14:21:42 14 kernel: [    0.801422] Freeing initrd memory: 34052K (ffff880033d6e000 - ffff880035eaf000)
Dec 14 14:21:42 14 kernel: [    0.801749] ACPI: PCI Interrupt Link [LSMB] enabled at IRQ 23
Dec 14 14:21:42 14 kernel: [    0.801959] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
Dec 14 14:21:42 14 kernel: [    0.802145] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
Dec 14 14:21:42 14 kernel: [    0.802335] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
Dec 14 14:21:42 14 kernel: [    0.802519] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
Dec 14 14:21:42 14 kernel: [    0.802706] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
Dec 14 14:21:42 14 kernel: [    0.802891] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 21
Dec 14 14:21:42 14 kernel: [    0.803089] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 20
Dec 14 14:21:42 14 kernel: [    0.803158] PCI-DMA: Disabling AGP.
Dec 14 14:21:42 14 kernel: [    0.803233] PCI-DMA: aperture base @ c4000000 size 65536 KB
Dec 14 14:21:42 14 kernel: [    0.803237] PCI-DMA: using GART IOMMU.
Dec 14 14:21:42 14 kernel: [    0.803242] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Dec 14 14:21:42 14 kernel: [    0.805750] microcode: CPU0: patch_level=0x01000098
Dec 14 14:21:42 14 kernel: [    0.805774] microcode: CPU1: patch_level=0x01000098
Dec 14 14:21:42 14 kernel: [    0.805858] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Dec 14 14:21:42 14 kernel: [    0.805870] LVT offset 1 assigned for vector 0x400
Dec 14 14:21:42 14 kernel: [    0.805879] IBS: LVT offset 1 assigned
Dec 14 14:21:42 14 kernel: [    0.805891] perf: AMD IBS detected (0x0000001f)
Dec 14 14:21:42 14 kernel: [    0.805928] Scanning for low memory corruption every 60 seconds
Dec 14 14:21:42 14 kernel: [    0.806204] futex hash table entries: 1024 (order: 4, 65536 bytes)
Dec 14 14:21:42 14 kernel: [    0.806241] audit: initializing netlink subsys (disabled)
Dec 14 14:21:42 14 kernel: [    0.806263] audit: type=2000 audit(1450102891.700:1): initialized
Dec 14 14:21:42 14 kernel: [    0.806489] Initialise system trusted keyring
Dec 14 14:21:42 14 kernel: [    0.806618] HugeTLB registered 1 GB page size, pre-allocated 0 pages
Dec 14 14:21:42 14 kernel: [    0.806624] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 14 14:21:42 14 kernel: [    0.808012] zbud: loaded
Dec 14 14:21:42 14 kernel: [    0.808281] VFS: Disk quotas dquot_6.6.0
Dec 14 14:21:42 14 kernel: [    0.808321] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 14 14:21:42 14 kernel: [    0.808791] fuse init (API version 7.23)
Dec 14 14:21:42 14 kernel: [    0.808946] Key type big_key registered
Dec 14 14:21:42 14 kernel: [    0.809366] Key type asymmetric registered
Dec 14 14:21:42 14 kernel: [    0.809377] Asymmetric key parser 'x509' registered
Dec 14 14:21:42 14 kernel: [    0.809405] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
Dec 14 14:21:42 14 kernel: [    0.809454] io scheduler noop registered
Dec 14 14:21:42 14 kernel: [    0.809459] io scheduler deadline registered (default)
Dec 14 14:21:42 14 kernel: [    0.809497] io scheduler cfq registered
Dec 14 14:21:42 14 kernel: [    0.809734] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 14 14:21:42 14 kernel: [    0.809743] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 14 14:21:42 14 kernel: [    0.809771] vesafb: mode is 640x480x32, linelength=2560, pages=0
Dec 14 14:21:42 14 kernel: [    0.809775] vesafb: scrolling: redraw
Dec 14 14:21:42 14 kernel: [    0.809779] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Dec 14 14:21:42 14 kernel: [    0.809793] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90000800000, using 1216k, total 1216k
Dec 14 14:21:42 14 kernel: [    0.815145] Console: switching to colour frame buffer device 80x30
Dec 14 14:21:42 14 kernel: [    0.820516] fb0: VESA VGA frame buffer device
Dec 14 14:21:42 14 kernel: [    0.820716] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 14 14:21:42 14 kernel: [    0.820927] ACPI: Power Button [PWRB]
Dec 14 14:21:42 14 kernel: [    0.821054] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 14 14:21:42 14 kernel: [    0.827476] ACPI: Power Button [PWRF]
Dec 14 14:21:42 14 kernel: [    0.830818] GHES: HEST is not enabled!
Dec 14 14:21:42 14 kernel: [    0.834065] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 14 14:21:42 14 kernel: [    0.838805] Linux agpgart interface v0.103
Dec 14 14:21:42 14 kernel: [    0.844633] brd: module loaded
Dec 14 14:21:42 14 kernel: [    0.849166] loop: module loaded
Dec 14 14:21:42 14 kernel: [    0.852880] libphy: Fixed MDIO Bus: probed
Dec 14 14:21:42 14 kernel: [    0.856041] tun: Universal TUN/TAP device driver, 1.6
Dec 14 14:21:42 14 kernel: [    0.859249] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 14 14:21:42 14 kernel: [    0.862619] PPP generic driver version 2.4.2
Dec 14 14:21:42 14 kernel: [    0.866002] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 14 14:21:42 14 kernel: [    0.869352] ehci-pci: EHCI PCI platform driver
Dec 14 14:21:42 14 kernel: [    0.872674] ehci-pci 0000:00:02.1: EHCI Host Controller
Dec 14 14:21:42 14 kernel: [    0.875963] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
Dec 14 14:21:42 14 kernel: [    0.882579] ehci-pci 0000:00:02.1: debug port 1
Dec 14 14:21:42 14 kernel: [    0.885960] ehci-pci 0000:00:02.1: cache line size of 64 is not supported
Dec 14 14:21:42 14 kernel: [    0.885980] ehci-pci 0000:00:02.1: irq 21, io mem 0xfbffec00
Dec 14 14:21:42 14 kernel: [    0.900788] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
Dec 14 14:21:42 14 kernel: [    0.904103] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Dec 14 14:21:42 14 kernel: [    0.907445] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 14 14:21:42 14 kernel: [    0.914006] usb usb1: Product: EHCI Host Controller
Dec 14 14:21:42 14 kernel: [    0.917263] usb usb1: Manufacturer: Linux 4.3.0-2-generic ehci_hcd
Dec 14 14:21:42 14 kernel: [    0.920500] usb usb1: SerialNumber: 0000:00:02.1
Dec 14 14:21:42 14 kernel: [    0.923863] hub 1-0:1.0: USB hub found
Dec 14 14:21:42 14 kernel: [    0.926976] hub 1-0:1.0: 10 ports detected
Dec 14 14:21:42 14 kernel: [    0.930155] ehci-platform: EHCI generic platform driver
Dec 14 14:21:42 14 kernel: [    0.933221] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 14 14:21:42 14 kernel: [    0.936247] ohci-pci: OHCI PCI platform driver
Dec 14 14:21:42 14 kernel: [    0.939277] ohci-pci 0000:00:02.0: OHCI PCI host controller
Dec 14 14:21:42 14 kernel: [    0.942258] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
Dec 14 14:21:42 14 kernel: [    0.948217] ohci-pci 0000:00:02.0: irq 22, io mem 0xfbfff000
Dec 14 14:21:42 14 kernel: [    1.006888] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Dec 14 14:21:42 14 kernel: [    1.010012] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 14 14:21:42 14 kernel: [    1.016268] usb usb2: Product: OHCI PCI host controller
Dec 14 14:21:42 14 kernel: [    1.019496] usb usb2: Manufacturer: Linux 4.3.0-2-generic ohci_hcd
Dec 14 14:21:42 14 kernel: [    1.022715] usb usb2: SerialNumber: 0000:00:02.0
Dec 14 14:21:42 14 kernel: [    1.026016] hub 2-0:1.0: USB hub found
Dec 14 14:21:42 14 kernel: [    1.029132] hub 2-0:1.0: 10 ports detected
Dec 14 14:21:42 14 kernel: [    1.032341] ohci-platform: OHCI generic platform driver
Dec 14 14:21:42 14 kernel: [    1.035437] uhci_hcd: USB Universal Host Controller Interface driver
Dec 14 14:21:42 14 kernel: [    1.038621] i8042: PNP: No PS/2 controller found. Probing ports directly.
Dec 14 14:21:42 14 kernel: [    1.043994] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 14 14:21:42 14 kernel: [    1.047156] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 14 14:21:42 14 kernel: [    1.050450] mousedev: PS/2 mouse device common for all mice
Dec 14 14:21:42 14 kernel: [    1.053792] rtc_cmos 00:00: RTC can wake from S4
Dec 14 14:21:42 14 kernel: [    1.057055] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
Dec 14 14:21:42 14 kernel: [    1.060218] rtc_cmos 00:00: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Dec 14 14:21:42 14 kernel: [    1.066314] i2c /dev entries driver
Dec 14 14:21:42 14 kernel: [    1.069397] device-mapper: uevent: version 1.0.3
Dec 14 14:21:42 14 kernel: [    1.072520] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
Dec 14 14:21:42 14 kernel: [    1.078788] ledtrig-cpu: registered to indicate activity on CPUs
Dec 14 14:21:42 14 kernel: [    1.082397] NET: Registered protocol family 10
Dec 14 14:21:42 14 kernel: [    1.085824] NET: Registered protocol family 17
Dec 14 14:21:42 14 kernel: [    1.088978] Key type dns_resolver registered
Dec 14 14:21:42 14 kernel: [    1.092449] registered taskstats version 1
Dec 14 14:21:42 14 kernel: [    1.095562] Loading compiled-in X.509 certificates
Dec 14 14:21:42 14 kernel: [    1.099571] Loaded X.509 cert 'Build time autogenerated kernel key: 529a908f1f1fa68336efe06eb8e57dd6a88b5796'
Dec 14 14:21:42 14 kernel: [    1.105762] zswap: loaded using pool lzo/zbud
Dec 14 14:21:42 14 kernel: [    1.110607] Key type trusted registered
Dec 14 14:21:42 14 kernel: [    1.117042] Key type encrypted registered
Dec 14 14:21:42 14 kernel: [    1.120027] AppArmor: AppArmor sha1 policy hashing enabled
Dec 14 14:21:42 14 kernel: [    1.123056] ima: No TPM chip found, activating TPM-bypass!
Dec 14 14:21:42 14 kernel: [    1.126120] evm: HMAC attrs: 0x1
Dec 14 14:21:42 14 kernel: [    1.129300]   Magic number: 11:396:384
Dec 14 14:21:42 14 kernel: [    1.132300] usb usb2: hash matches
Dec 14 14:21:42 14 kernel: [    1.135360] rtc_cmos 00:00: setting system clock to 2015-12-14 14:21:32 UTC (1450102892)
Dec 14 14:21:42 14 kernel: [    1.141451] acpi-cpufreq: overriding BIOS provided _PSD data
Dec 14 14:21:42 14 kernel: [    1.144550] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 14 14:21:42 14 kernel: [    1.147709] EDD information not available.
Dec 14 14:21:42 14 kernel: [    1.150857] PM: Hibernation image not present or could not be loaded.
Dec 14 14:21:42 14 kernel: [    1.151309] Freeing unused kernel memory: 1464K (ffffffff81f3a000 - ffffffff820a8000)
Dec 14 14:21:42 14 kernel: [    1.157644] Write protecting the kernel read-only data: 14336k
Dec 14 14:21:42 14 kernel: [    1.161692] Freeing unused kernel memory: 2036K (ffff880001803000 - ffff880001a00000)
Dec 14 14:21:42 14 kernel: [    1.168326] Freeing unused kernel memory: 244K (ffff880001dc3000 - ffff880001e00000)
Dec 14 14:21:42 14 kernel: [    1.197058] random: systemd-udevd urandom read with 2 bits of entropy available
Dec 14 14:21:42 14 kernel: [    1.226483] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
Dec 14 14:21:42 14 kernel: [    1.239208] sata_nv 0000:00:08.0: version 3.5
Dec 14 14:21:42 14 kernel: [    1.239629] scsi host0: sata_nv
Dec 14 14:21:42 14 kernel: [    1.243146] usb 1-1: new high-speed USB device number 2 using ehci-pci
Dec 14 14:21:42 14 kernel: [    1.249031] scsi host1: sata_nv
Dec 14 14:21:42 14 kernel: [    1.252535] ata1: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 22
Dec 14 14:21:42 14 kernel: [    1.256114] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 22
Dec 14 14:21:42 14 kernel: [    1.259306] [drm] Initialized drm 1.1.0 20060810
Dec 14 14:21:42 14 kernel: [    1.263482] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Dec 14 14:21:42 14 kernel: [    1.286994] wmi: Mapper loaded
Dec 14 14:21:42 14 kernel: [    1.379668] usb 1-1: New USB device found, idVendor=04b4, idProduct=6830
Dec 14 14:21:42 14 kernel: [    1.383371] usb 1-1: New USB device strings: Mfr=56, Product=78, SerialNumber=100
Dec 14 14:21:42 14 kernel: [    1.390672] usb 1-1: Product: USB2.0 Storage Device
Dec 14 14:21:42 14 kernel: [    1.394312] usb 1-1: Manufacturer: Cypress Semiconductor
Dec 14 14:21:42 14 kernel: [    1.397919] usb 1-1: SerialNumber: DEF10A366B82
Dec 14 14:21:42 14 kernel: [    1.569218] usb 1-9: new high-speed USB device number 4 using ehci-pci
Dec 14 14:21:42 14 kernel: [    1.703626] usb 1-9: New USB device found, idVendor=058f, idProduct=6366
Dec 14 14:21:42 14 kernel: [    1.707214] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 14 14:21:42 14 kernel: [    1.710736] usb 1-9: Product: Mass Storage Device
Dec 14 14:21:42 14 kernel: [    1.714195] usb 1-9: Manufacturer: Generic
Dec 14 14:21:42 14 kernel: [    1.717581] usb 1-9: SerialNumber: 058F63666471
Dec 14 14:21:42 14 kernel: [    1.729346] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 14:21:42 14 kernel: [    1.737759] ata1.00: ATA-8: WDC WD10EZEX-00ZF5A0, 80.00A80, max UDMA/133
Dec 14 14:21:42 14 kernel: [    1.741060] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 14:21:42 14 kernel: [    1.749786] ata1.00: configured for UDMA/133
Dec 14 14:21:42 14 kernel: [    1.753391] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EZEX-00Z 0A80 PQ: 0 ANSI: 5
Dec 14 14:21:42 14 kernel: [    1.757349] usb 2-4: new low-speed USB device number 2 using ohci-pci
Dec 14 14:21:42 14 kernel: [    1.763596] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 14:21:42 14 kernel: [    1.770270] sd 0:0:0:0: [sda] 4096-byte physical blocks
Dec 14 14:21:42 14 kernel: [    1.773631] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 14 14:21:42 14 kernel: [    1.777064] sd 0:0:0:0: [sda] Write Protect is off
Dec 14 14:21:42 14 kernel: [    1.780351] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 14 14:21:42 14 kernel: [    1.780363] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 14:21:42 14 kernel: [    1.794064] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr e0:cb:4e:9b:e8:4d
Dec 14 14:21:42 14 kernel: [    1.800805] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
Dec 14 14:21:42 14 kernel: [    1.804808] scsi host2: sata_nv
Dec 14 14:21:42 14 kernel: [    1.808855] forcedeth 0000:00:07.0 enp0s7: renamed from eth0
Dec 14 14:21:42 14 kernel: [    1.809401] tsc: Refined TSC clocksource calibration: 3013.705 MHz
Dec 14 14:21:42 14 kernel: [    1.809404] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b70d7a0847, max_idle_ns: 440795224568 ns
Dec 14 14:21:42 14 kernel: [    1.812862] scsi host3: sata_nv
Dec 14 14:21:42 14 kernel: [    1.812937] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 21
Dec 14 14:21:42 14 kernel: [    1.812939] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 21
Dec 14 14:21:42 14 kernel: [    1.813354] checking generic (e0000000 130000) vs hw (e0000000 10000000)
Dec 14 14:21:42 14 kernel: [    1.813355] fb: switching to nouveaufb from VESA VGA
Dec 14 14:21:42 14 kernel: [    1.837043] Console: switching to colour dummy device 80x25
Dec 14 14:21:42 14 kernel: [    1.837150] nouveau 0000:00:0d.0: NVIDIA C61 (04c000a2)
Dec 14 14:21:42 14 kernel: [    1.846682] nouveau 0000:00:0d.0: bios: version 05.61.32.28.00
Dec 14 14:21:42 14 kernel: [    1.846953] nouveau 0000:00:0d.0: disp: dcb 1 type 4 unknown
Dec 14 14:21:42 14 kernel: [    1.847271] nouveau 0000:00:0d.0: fb: 256 MiB of unknown memory type
Dec 14 14:21:42 14 kernel: [    1.868443]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
Dec 14 14:21:42 14 kernel: [    1.868828] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 14 14:21:42 14 kernel: [    1.869416] usb-storage 1-9:1.0: USB Mass Storage device detected
Dec 14 14:21:42 14 kernel: [    1.872335] scsi host4: usb-storage 1-9:1.0
Dec 14 14:21:42 14 kernel: [    1.872419] usbcore: registered new interface driver usb-storage
Dec 14 14:21:42 14 kernel: [    1.873807] usbcore: registered new interface driver uas
Dec 14 14:21:42 14 kernel: [    1.874972] ums-cypress 1-1:1.0: USB Mass Storage device detected
Dec 14 14:21:42 14 kernel: [    1.875925] scsi host5: usb-storage 1-1:1.0
Dec 14 14:21:42 14 kernel: [    1.875993] usbcore: registered new interface driver ums-cypress
Dec 14 14:21:42 14 kernel: [    1.898492] [TTM] Zone  kernel: Available graphics memory: 1894420 kiB
Dec 14 14:21:42 14 kernel: [    1.898498] [TTM] Initializing pool allocator
Dec 14 14:21:42 14 kernel: [    1.898504] [TTM] Initializing DMA pool allocator
Dec 14 14:21:42 14 kernel: [    1.898518] nouveau 0000:00:0d.0: DRM: VRAM: 253 MiB
Dec 14 14:21:42 14 kernel: [    1.898523] nouveau 0000:00:0d.0: DRM: GART: 512 MiB
Dec 14 14:21:42 14 kernel: [    1.898529] nouveau 0000:00:0d.0: DRM: TMDS table version 1.1
Dec 14 14:21:42 14 kernel: [    1.898534] nouveau 0000:00:0d.0: DRM: DCB version 3.0
Dec 14 14:21:42 14 kernel: [    1.898539] nouveau 0000:00:0d.0: DRM: DCB outp 00: 01000310 00000023
Dec 14 14:21:42 14 kernel: [    1.898544] nouveau 0000:00:0d.0: DRM: DCB outp 01: 00110204 942b0003
Dec 14 14:21:42 14 kernel: [    1.898548] nouveau 0000:00:0d.0: DRM: DCB conn 00: 0000
Dec 14 14:21:42 14 kernel: [    1.898552] nouveau 0000:00:0d.0: DRM: DCB conn 01: 1131
Dec 14 14:21:42 14 kernel: [    1.898556] nouveau 0000:00:0d.0: DRM: DCB conn 02: 0110
Dec 14 14:21:42 14 kernel: [    1.898560] nouveau 0000:00:0d.0: DRM: DCB conn 03: 0111
Dec 14 14:21:42 14 kernel: [    1.898564] nouveau 0000:00:0d.0: DRM: DCB conn 04: 0113
Dec 14 14:21:42 14 kernel: [    1.898832] nouveau 0000:00:0d.0: DRM: DCB type 4 not known
Dec 14 14:21:42 14 kernel: [    1.898838] nouveau 0000:00:0d.0: DRM: Unknown-1 has no encoders, removing
Dec 14 14:21:42 14 kernel: [    1.899906] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Dec 14 14:21:42 14 kernel: [    1.899910] [drm] Driver supports precise vblank timestamp query.
Dec 14 14:21:42 14 kernel: [    1.901708] nouveau 0000:00:0d.0: DRM: MM: using M2MF for buffer copies
Dec 14 14:21:42 14 kernel: [    1.930297] nouveau 0000:00:0d.0: DRM: allocated 1600x900 fb: 0x9000, bo ffff880119e9f800
Dec 14 14:21:42 14 kernel: [    1.930426] fbcon: nouveaufb (fb0) is primary device
Dec 14 14:21:42 14 kernel: [    1.968522] usb 2-4: New USB device found, idVendor=04fc, idProduct=05d8
Dec 14 14:21:42 14 kernel: [    1.968524] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 14 14:21:42 14 kernel: [    1.968525] usb 2-4: Product: wireless combo
Dec 14 14:21:42 14 kernel: [    1.968526] usb 2-4: Manufacturer: MLK
Dec 14 14:21:42 14 kernel: [    1.986846] hidraw: raw HID events driver (C) Jiri Kosina
Dec 14 14:21:42 14 kernel: [    2.003884] usbcore: registered new interface driver usbhid
Dec 14 14:21:42 14 kernel: [    2.003884] usbhid: USB HID core driver
Dec 14 14:21:42 14 kernel: [    2.006861] input: MLK wireless combo as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/0003:04FC:05D8.0001/input/input5
Dec 14 14:21:42 14 kernel: [    2.034025] Console: switching to colour frame buffer device 200x56
Dec 14 14:21:42 14 kernel: [    2.036244] nouveau 0000:00:0d.0: fb0: nouveaufb frame buffer device
Dec 14 14:21:42 14 kernel: [    2.045535] [drm] Initialized nouveau 1.3.0 20120801 for 0000:00:0d.0 on minor 0
Dec 14 14:21:42 14 kernel: [    2.061683] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK wireless combo] on usb-0000:00:02.0-4/input0
Dec 14 14:21:42 14 kernel: [    2.061727] sunplus 0003:04FC:05D8.0002: fixing up Sunplus Wireless Desktop report descriptor
Dec 14 14:21:42 14 kernel: [    2.062460] input: MLK wireless combo as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/0003:04FC:05D8.0002/input/input6
Dec 14 14:21:42 14 kernel: [    2.095817] ata2: SATA link down (SStatus 0 SControl 300)
Dec 14 14:21:42 14 kernel: [    2.118530] sunplus 0003:04FC:05D8.0002: input,hiddev0,hidraw1: USB HID v1.00 Mouse [MLK wireless combo] on usb-0000:00:02.0-4/input1
Dec 14 14:21:42 14 kernel: [    2.131837] ata3: SATA link down (SStatus 0 SControl 300)
Dec 14 14:21:42 14 kernel: [    2.452021] ata4: SATA link down (SStatus 0 SControl 300)
Dec 14 14:21:42 14 kernel: [    2.806160] clocksource: Switched to clocksource tsc
Dec 14 14:21:42 14 kernel: [    2.871008] scsi 4:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
Dec 14 14:21:42 14 kernel: [    2.871500] sd 4:0:0:0: Attached scsi generic sg1 type 0
Dec 14 14:21:42 14 kernel: [    2.873411] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Dec 14 14:21:42 14 kernel: [    2.876161] scsi 5:0:0:0: Direct-Access     TOSHIBA  MK6025GAS        0000 PQ: 0 ANSI: 0
Dec 14 14:21:42 14 kernel: [    2.876936] sd 5:0:0:0: Attached scsi generic sg2 type 0
Dec 14 14:21:42 14 kernel: [    2.877900] sd 5:0:0:0: [sdc] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
Dec 14 14:21:42 14 kernel: [    2.878783] sd 5:0:0:0: [sdc] Write Protect is off
Dec 14 14:21:42 14 kernel: [    2.878799] sd 5:0:0:0: [sdc] Mode Sense: 27 00 00 00
Dec 14 14:21:42 14 kernel: [    2.879658] sd 5:0:0:0: [sdc] No Caching mode page found
Dec 14 14:21:42 14 kernel: [    2.879673] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Dec 14 14:21:42 14 kernel: [    2.965716]  sdc: sdc1 sdc2 < > sdc3
Dec 14 14:21:42 14 kernel: [    2.968600] sd 5:0:0:0: [sdc] Attached SCSI disk
Dec 14 14:21:42 14 kernel: [    3.415630] random: nonblocking pool is initialized
Dec 14 14:21:42 14 kernel: [    3.826994] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Dec 14 14:21:42 14 kernel: [    5.794400] lp: driver loaded but no devices found
Dec 14 14:21:42 14 kernel: [    5.824868] ppdev: user-space parallel port driver
Dec 14 14:21:42 14 kernel: [    6.184422] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Dec 14 14:21:42 14 kernel: [    6.868646] i2c i2c-4: nForce2 SMBus adapter at 0x4d00
Dec 14 14:21:42 14 kernel: [    6.868693] i2c i2c-5: nForce2 SMBus adapter at 0x4e00
Dec 14 14:21:42 14 kernel: [    6.908766] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 14 14:21:42 14 kernel: [    6.956245] EDAC MC: Ver: 3.0.0
Dec 14 14:21:42 14 kernel: [    6.979869] MCE: In-kernel MCE decoding enabled.
Dec 14 14:21:42 14 kernel: [    7.021833] AMD64 EDAC driver v3.4.0
Dec 14 14:21:42 14 kernel: [    7.021867] EDAC amd64: DRAM ECC disabled.
Dec 14 14:21:42 14 kernel: [    7.021872] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Dec 14 14:21:42 14 kernel: [    7.021872]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Dec 14 14:21:42 14 kernel: [    7.021872]  (Note that use of the override may cause unknown side effects.)
Dec 14 14:21:42 14 kernel: [    7.274132] kvm: disabled by bios
Dec 14 14:21:42 14 kernel: [    7.770639] snd_hda_intel 0000:00:05.0: Disabling MSI
Dec 14 14:21:42 14 kernel: [    8.473692] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC662 rev1: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
Dec 14 14:21:42 14 kernel: [    8.473697] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Dec 14 14:21:42 14 kernel: [    8.473699] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Dec 14 14:21:42 14 kernel: [    8.473701] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Dec 14 14:21:42 14 kernel: [    8.473703] snd_hda_codec_realtek hdaudioC0D0:    inputs:
Dec 14 14:21:42 14 kernel: [    8.473704] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
Dec 14 14:21:42 14 kernel: [    8.473706] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
Dec 14 14:21:42 14 kernel: [    8.609621] Adding 2047996k swap on /dev/sda5.  Priority:-1 extents:1 across:2047996k FS
Dec 14 14:21:42 14 kernel: [    8.723833] audit: type=1400 audit(1450131700.079:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.723843] audit: type=1400 audit(1450131700.079:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.726794] audit: type=1400 audit(1450131700.083:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.726804] audit: type=1400 audit(1450131700.083:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.726808] audit: type=1400 audit(1450131700.083:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.726812] audit: type=1400 audit(1450131700.083:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.742937] audit: type=1400 audit(1450131700.099:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.742948] audit: type=1400 audit(1450131700.099:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.742952] audit: type=1400 audit(1450131700.099:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    8.742956] audit: type=1400 audit(1450131700.099:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=433 comm="apparmor_parser"
Dec 14 14:21:42 14 kernel: [    9.820960] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
Dec 14 14:21:42 14 kernel: [    9.821028] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
Dec 14 14:21:42 14 kernel: [    9.821086] input: HDA NVidia Line Out as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
Dec 14 14:21:42 14 kernel: [    9.821146] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
Dec 14 14:21:43 14 kernel: [   11.671561] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
Dec 14 14:21:43 14 kernel: [   11.672259] forcedeth 0000:00:07.0 enp0s7: MSI enabled
Dec 14 14:21:43 14 kernel: [   11.672518] forcedeth 0000:00:07.0 enp0s7: no link during initialization
Dec 14 14:21:43 14 kernel: [   11.672812] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
Dec 14 14:21:44 14 kernel: [   12.798038] nouveau 0000:00:0d.0: bus: MMIO write of 005c0001 FAULT at 00b000
Dec 14 14:21:55 14 kernel: [   23.790261] nouveau 0000:00:0d.0: bus: MMIO write of 01060001 FAULT at 00b010
Dec 14 14:21:55 14 kernel: [   23.791682] nouveau 0000:00:0d.0: bus: MMIO write of 01060001 FAULT at 00b010
Dec 14 14:21:56 14 kernel: [   25.477707] nouveau 0000:00:0d.0: bus: MMIO write of 00000000 FAULT at 00b010
Dec 14 14:22:18 14 kernel: [   47.578262] forcedeth 0000:00:07.0 enp0s7: link up
Dec 14 14:22:18 14 kernel: [   47.578590] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s7: link becomes ready
Dec 14 14:23:06 14 kernel: [   96.295260] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Dec 14 14:34:32 14 kernel: [  781.365010] nvidia: module license 'NVIDIA' taints kernel.
Dec 14 14:34:32 14 kernel: [  781.365015] Disabling lock debugging due to kernel taint
Dec 14 14:34:32 14 kernel: [  781.373127] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Dec 14 14:34:32 14 kernel: [  781.373429] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:34:32 14 kernel: [  781.373584] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 14:34:32 14 kernel: [  781.410570] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:34:32 14 kernel: [  781.410727] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 14:34:32 14 kernel: [  781.496855] nouveau 0000:00:0d.0: bus: MMIO write of 00000000 FAULT at 00b000
Dec 14 14:34:32 14 kernel: [  781.498901] nouveau 0000:00:0d.0: bus: MMIO write of 005c0001 FAULT at 00b000
Dec 14 14:35:32 14 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 14 14:35:32 14 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 14 14:35:32 14 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Dec 14 14:35:32 14 kernel: [    0.000000] Linux version 4.3.0-2-generic (buildd@lgw01-24) (gcc version 5.2.1 20151129 (Ubuntu 5.2.1-27ubuntu1) ) #11-Ubuntu SMP Fri Dec 4 20:37:48 UTC 2015 (Ubuntu 4.3.0-2.11-generic 4.3.0)
Dec 14 14:35:32 14 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-2-generic root=UUID=107bf235-82e7-4095-8e55-397abe9ab3b3 ro
Dec 14 14:35:32 14 kernel: [    0.000000] KERNEL supported cpus:
Dec 14 14:35:32 14 kernel: [    0.000000]   Intel GenuineIntel
Dec 14 14:35:32 14 kernel: [    0.000000]   AMD AuthenticAMD
Dec 14 14:35:32 14 kernel: [    0.000000]   Centaur CentaurHauls
Dec 14 14:35:32 14 kernel: [    0.000000] tseg: 0000000000
Dec 14 14:35:32 14 kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
Dec 14 14:35:32 14 kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Dec 14 14:35:32 14 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cffaffff] usable
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffb0000-0x00000000cffbdfff] ACPI data
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffbe000-0x00000000cffeffff] ACPI NVS
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfff0000-0x00000000cfffffff] reserved
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Dec 14 14:35:32 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
Dec 14 14:35:32 14 kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 14 14:35:32 14 kernel: [    0.000000] SMBIOS 2.5 present.
Dec 14 14:35:32 14 kernel: [    0.000000] DMI: HP-Pavilion AY652AA-ABA s5310y/Narra6, BIOS 5.17    01/07/2010
Dec 14 14:35:32 14 kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Dec 14 14:35:32 14 kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Dec 14 14:35:32 14 kernel: [    0.000000] AGP: No AGP bridge found
Dec 14 14:35:32 14 kernel: [    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x400000000
Dec 14 14:35:32 14 kernel: [    0.000000] MTRR default type: uncachable
Dec 14 14:35:32 14 kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 14 14:35:32 14 kernel: [    0.000000]   00000-9FFFF write-back
Dec 14 14:35:32 14 kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 14 14:35:32 14 kernel: [    0.000000]   C0000-CFFFF write-protect
Dec 14 14:35:32 14 kernel: [    0.000000]   D0000-EFFFF uncachable
Dec 14 14:35:32 14 kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 14 14:35:32 14 kernel: [    0.000000] MTRR variable ranges enabled:
Dec 14 14:35:32 14 kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Dec 14 14:35:32 14 kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Dec 14 14:35:32 14 kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Dec 14 14:35:32 14 kernel: [    0.000000]   3 disabled
Dec 14 14:35:32 14 kernel: [    0.000000]   4 disabled
Dec 14 14:35:32 14 kernel: [    0.000000]   5 disabled
Dec 14 14:35:32 14 kernel: [    0.000000]   6 disabled
Dec 14 14:35:32 14 kernel: [    0.000000]   7 disabled
Dec 14 14:35:32 14 kernel: [    0.000000] TOM2: 0000000120000000 aka 4608M
Dec 14 14:35:32 14 kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Dec 14 14:35:32 14 kernel: [    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Dec 14 14:35:32 14 kernel: [    0.000000] e820: last_pfn = 0xcffb0 max_arch_pfn = 0x400000000
Dec 14 14:35:32 14 kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
Dec 14 14:35:32 14 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 14 14:35:32 14 kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Dec 14 14:35:32 14 kernel: [    0.000000] Using GB pages for direct mapping
Dec 14 14:35:32 14 kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Dec 14 14:35:32 14 kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Dec 14 14:35:32 14 kernel: [    0.000000] BRK [0x021f6000, 0x021f6fff] PGTABLE
Dec 14 14:35:32 14 kernel: [    0.000000] BRK [0x021f7000, 0x021f7fff] PGTABLE
Dec 14 14:35:32 14 kernel: [    0.000000] BRK [0x021f8000, 0x021f8fff] PGTABLE
Dec 14 14:35:32 14 kernel: [    0.000000] init_memory_mapping: [mem 0x11fe00000-0x11fffffff]
Dec 14 14:35:32 14 kernel: [    0.000000]  [mem 0x11fe00000-0x11fffffff] page 2M
Dec 14 14:35:32 14 kernel: [    0.000000] BRK [0x021f9000, 0x021f9fff] PGTABLE
Dec 14 14:35:32 14 kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11fdfffff]
Dec 14 14:35:32 14 kernel: [    0.000000]  [mem 0x100000000-0x11fdfffff] page 2M
Dec 14 14:35:32 14 kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xcffaffff]
Dec 14 14:35:32 14 kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Dec 14 14:35:32 14 kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Dec 14 14:35:32 14 kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Dec 14 14:35:32 14 kernel: [    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
Dec 14 14:35:32 14 kernel: [    0.000000]  [mem 0xcfe00000-0xcffaffff] page 4k
Dec 14 14:35:32 14 kernel: [    0.000000] RAMDISK: [mem 0x33e8e000-0x35f3efff]
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: Early table checksum verification disabled
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: RSDP 0x00000000000FB220 000014 (v00 HPQOEM)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: RSDT 0x00000000CFFB0000 000040 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: FACP 0x00000000CFFB0200 000084 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: DSDT 0x00000000CFFB0450 0043AF (v01 HPQOEM SLIC-CPC 00000001 INTL 20051117)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: FACS 0x00000000CFFBE000 000040
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: APIC 0x00000000CFFB0390 000080 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: MCFG 0x00000000CFFB0410 00003C (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: OEMB 0x00000000CFFBE040 000072 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: HPET 0x00000000CFFB4800 000038 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: SLIC 0x00000000CFFBE0C0 000176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: SSDT 0x00000000CFFB4840 000458 (v01 HPQOEM SLIC-CPC 00000001 AMD  00000001)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 14:35:32 14 kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Dec 14 14:35:32 14 kernel: [    0.000000] No NUMA configuration found
Dec 14 14:35:32 14 kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011fffffff]
Dec 14 14:35:32 14 kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x11fff9000-0x11fffdfff]
Dec 14 14:35:32 14 kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011ba00000-ffff88011f5fffff] on node 0
Dec 14 14:35:32 14 kernel: [    0.000000] Zone ranges:
Dec 14 14:35:32 14 kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Dec 14 14:35:32 14 kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Dec 14 14:35:32 14 kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000011fffffff]
Dec 14 14:35:32 14 kernel: [    0.000000] Movable zone start for each node
Dec 14 14:35:32 14 kernel: [    0.000000] Early memory node ranges
Dec 14 14:35:32 14 kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
Dec 14 14:35:32 14 kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x00000000cffaffff]
Dec 14 14:35:32 14 kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000011fffffff]
Dec 14 14:35:32 14 kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000011fffffff]
Dec 14 14:35:32 14 kernel: [    0.000000] On node 0 totalpages: 982862
Dec 14 14:35:32 14 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Dec 14 14:35:32 14 kernel: [    0.000000]   DMA zone: 21 pages reserved
Dec 14 14:35:32 14 kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Dec 14 14:35:32 14 kernel: [    0.000000]   DMA32 zone: 13247 pages used for memmap
Dec 14 14:35:32 14 kernel: [    0.000000]   DMA32 zone: 847792 pages, LIFO batch:31
Dec 14 14:35:32 14 kernel: [    0.000000]   Normal zone: 2048 pages used for memmap
Dec 14 14:35:32 14 kernel: [    0.000000]   Normal zone: 131072 pages, LIFO batch:31
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 14:35:32 14 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: IRQ14 used by override.
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: IRQ15 used by override.
Dec 14 14:35:32 14 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 14 14:35:32 14 kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Dec 14 14:35:32 14 kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcffb0000-0xcffbdfff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcffbe000-0xcffeffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcfff0000-0xcfffffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd0000000-0xfebfffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfeefffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffefffff]
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfff00000-0xffffffff]
Dec 14 14:35:32 14 kernel: [    0.000000] e820: [mem 0xd0000000-0xfebfffff] available for PCI devices
Dec 14 14:35:32 14 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 14 14:35:32 14 kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Dec 14 14:35:32 14 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Dec 14 14:35:32 14 kernel: [    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88011fc00000 s97304 r8192 d29672 u524288
Dec 14 14:35:32 14 kernel: [    0.000000] pcpu-alloc: s97304 r8192 d29672 u524288 alloc=1*2097152
Dec 14 14:35:32 14 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Dec 14 14:35:32 14 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 967482
Dec 14 14:35:32 14 kernel: [    0.000000] Policy zone: Normal
Dec 14 14:35:32 14 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-2-generic root=UUID=107bf235-82e7-4095-8e55-397abe9ab3b3 ro
Dec 14 14:35:32 14 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 14 14:35:32 14 kernel: [    0.000000] AGP: Checking aperture...
Dec 14 14:35:32 14 kernel: [    0.000000] AGP: No AGP bridge found
Dec 14 14:35:32 14 kernel: [    0.000000] AGP: Node 0: aperture [bus addr 0xc4000000-0xc5ffffff] (32MB)
Dec 14 14:35:32 14 kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Dec 14 14:35:32 14 kernel: [    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
Dec 14 14:35:32 14 kernel: [    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
Dec 14 14:35:32 14 kernel: [    0.000000] AGP: This costs you 64MB of RAM
Dec 14 14:35:32 14 kernel: [    0.000000] AGP: Mapping aperture over RAM [mem 0xc4000000-0xc7ffffff] (65536KB)
Dec 14 14:35:32 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
Dec 14 14:35:32 14 kernel: [    0.000000] Memory: 3685640K/3931448K available (8191K kernel code, 1251K rwdata, 3852K rodata, 1464K init, 1300K bss, 245808K reserved, 0K cma-reserved)
Dec 14 14:35:32 14 kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec 14 14:35:32 14 kernel: [    0.000000] Hierarchical RCU implementation.
Dec 14 14:35:32 14 kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Dec 14 14:35:32 14 kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Dec 14 14:35:32 14 kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
Dec 14 14:35:32 14 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:456 16
Dec 14 14:35:32 14 kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec 14 14:35:32 14 kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 14 14:35:32 14 kernel: [    0.000000] console [tty0] enabled
Dec 14 14:35:32 14 kernel: [    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 76450417870 ns
Dec 14 14:35:32 14 kernel: [    0.000000] hpet clockevent registered
Dec 14 14:35:32 14 kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Dec 14 14:35:32 14 kernel: [    0.000000] tsc: Detected 3013.673 MHz processor
Dec 14 14:35:32 14 kernel: [    0.000029] Calibrating delay loop (skipped), value calculated using timer frequency.. 6027.34 BogoMIPS (lpj=12054692)
Dec 14 14:35:32 14 kernel: [    0.000144] pid_max: default: 32768 minimum: 301
Dec 14 14:35:32 14 kernel: [    0.000205] ACPI: Core revision 20150818
Dec 14 14:35:32 14 kernel: [    0.002511] ACPI: 2 ACPI AML tables successfully acquired and loaded
Dec 14 14:35:32 14 kernel: [    0.002670] Security Framework initialized
Dec 14 14:35:32 14 kernel: [    0.002727] Yama: becoming mindful.
Dec 14 14:35:32 14 kernel: [    0.002793] AppArmor: AppArmor initialized
Dec 14 14:35:32 14 kernel: [    0.003084] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec 14 14:35:32 14 kernel: [    0.004218] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 14 14:35:32 14 kernel: [    0.004797] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Dec 14 14:35:32 14 kernel: [    0.004861] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Dec 14 14:35:32 14 kernel: [    0.005128] Initializing cgroup subsys io
Dec 14 14:35:32 14 kernel: [    0.005188] Initializing cgroup subsys memory
Dec 14 14:35:32 14 kernel: [    0.005250] Initializing cgroup subsys devices
Dec 14 14:35:32 14 kernel: [    0.005308] Initializing cgroup subsys freezer
Dec 14 14:35:32 14 kernel: [    0.005365] Initializing cgroup subsys net_cls
Dec 14 14:35:32 14 kernel: [    0.005423] Initializing cgroup subsys perf_event
Dec 14 14:35:32 14 kernel: [    0.005481] Initializing cgroup subsys net_prio
Dec 14 14:35:32 14 kernel: [    0.005538] Initializing cgroup subsys hugetlb
Dec 14 14:35:32 14 kernel: [    0.005596] Initializing cgroup subsys pids
Dec 14 14:35:32 14 kernel: [    0.005669] CPU: Physical Processor ID: 0
Dec 14 14:35:32 14 kernel: [    0.005744] CPU: Processor Core ID: 0
Dec 14 14:35:32 14 kernel: [    0.005800] mce: CPU supports 6 MCE banks
Dec 14 14:35:32 14 kernel: [    0.005860] LVT offset 0 assigned for vector 0xf9
Dec 14 14:35:32 14 kernel: [    0.005919] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Dec 14 14:35:32 14 kernel: [    0.005977] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64, 1GB 0
Dec 14 14:35:32 14 kernel: [    0.006242] Freeing SMP alternatives memory: 28K (ffffffff820a8000 - ffffffff820af000)
Dec 14 14:35:32 14 kernel: [    0.007726] ftrace: allocating 31335 entries in 123 pages
Dec 14 14:35:32 14 kernel: [    0.020083] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 14 14:35:32 14 kernel: [    0.165795] smpboot: CPU0: AMD Athlon(tm) II X2 250 Processor (family: 0x10, model: 0x6, stepping: 0x2)
Dec 14 14:35:32 14 kernel: [    0.166011] Performance Events: AMD PMU driver.
Dec 14 14:35:32 14 kernel: [    0.166111] ... version:                0
Dec 14 14:35:32 14 kernel: [    0.166166] ... bit width:              48
Dec 14 14:35:32 14 kernel: [    0.166221] ... generic registers:      4
Dec 14 14:35:32 14 kernel: [    0.166277] ... value mask:             0000ffffffffffff
Dec 14 14:35:32 14 kernel: [    0.166334] ... max period:             00007fffffffffff
Dec 14 14:35:32 14 kernel: [    0.166390] ... fixed-purpose events:   0
Dec 14 14:35:32 14 kernel: [    0.166446] ... event mask:             000000000000000f
Dec 14 14:35:32 14 kernel: [    0.167111] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Dec 14 14:35:32 14 kernel: [    0.167249] x86: Booting SMP configuration:
Dec 14 14:35:32 14 kernel: [    0.167305] .... node  #0, CPUs:      #1
Dec 14 14:35:32 14 kernel: [    0.180412] x86: Booted up 1 node, 2 CPUs
Dec 14 14:35:32 14 kernel: [    0.180518] smpboot: Total of 2 processors activated (12054.69 BogoMIPS)
Dec 14 14:35:32 14 kernel: [    0.181165] devtmpfs: initialized
Dec 14 14:35:32 14 kernel: [    0.184496] evm: security.selinux
Dec 14 14:35:32 14 kernel: [    0.184551] evm: security.SMACK64
Dec 14 14:35:32 14 kernel: [    0.184605] evm: security.SMACK64EXEC
Dec 14 14:35:32 14 kernel: [    0.184660] evm: security.SMACK64TRANSMUTE
Dec 14 14:35:32 14 kernel: [    0.184715] evm: security.SMACK64MMAP
Dec 14 14:35:32 14 kernel: [    0.184770] evm: security.ima
Dec 14 14:35:32 14 kernel: [    0.184824] evm: security.capability
Dec 14 14:35:32 14 kernel: [    0.184949] PM: Registering ACPI NVS region [mem 0xcffbe000-0xcffeffff] (204800 bytes)
Dec 14 14:35:32 14 kernel: [    0.185085] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Dec 14 14:35:32 14 kernel: [    0.185229] pinctrl core: initialized pinctrl subsystem
Dec 14 14:35:32 14 kernel: [    0.185400] RTC time: 14:35:22, date: 12/14/15
Dec 14 14:35:32 14 kernel: [    0.185563] NET: Registered protocol family 16
Dec 14 14:35:32 14 kernel: [    0.196452] cpuidle: using governor ladder
Dec 14 14:35:32 14 kernel: [    0.208471] cpuidle: using governor menu
Dec 14 14:35:32 14 kernel: [    0.208538] PCCT header not found.
Dec 14 14:35:32 14 kernel: [    0.208598] node 0 link 0: io port [1000, ffffff]
Dec 14 14:35:32 14 kernel: [    0.208601] TOM: 00000000e0000000 aka 3584M
Dec 14 14:35:32 14 kernel: [    0.208658] Fam 10h mmconf [mem 0xfc000000-0xfdffffff]
Dec 14 14:35:32 14 kernel: [    0.208660] node 0 link 0: mmio [fc000000, fdffffff] ==> none
Dec 14 14:35:32 14 kernel: [    0.208662] node 0 link 0: mmio [e0000000, fbffffff]
Dec 14 14:35:32 14 kernel: [    0.208663] node 0 link 0: mmio [fe000000, fe0bffff]
Dec 14 14:35:32 14 kernel: [    0.208665] node 0 link 0: mmio [a0000, bffff]
Dec 14 14:35:32 14 kernel: [    0.208667] TOM2: 0000000120000000 aka 4608M
Dec 14 14:35:32 14 kernel: [    0.211944] bus: [bus 00-07] on node 0 link 0
Dec 14 14:35:32 14 kernel: [    0.211945] bus: 00 [io  0x0000-0xffff]
Dec 14 14:35:32 14 kernel: [    0.211946] bus: 00 [mem 0xe0000000-0xfbffffff]
Dec 14 14:35:32 14 kernel: [    0.211947] bus: 00 [mem 0xfe000000-0xffffffff]
Dec 14 14:35:32 14 kernel: [    0.211948] bus: 00 [mem 0x000a0000-0x000bffff]
Dec 14 14:35:32 14 kernel: [    0.211950] bus: 00 [mem 0x120000000-0xfcffffffff]
Dec 14 14:35:32 14 kernel: [    0.212032] ACPI: bus type PCI registered
Dec 14 14:35:32 14 kernel: [    0.212089] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Dec 14 14:35:32 14 kernel: [    0.212228] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
Dec 14 14:35:32 14 kernel: [    0.212300] PCI: not using MMCONFIG
Dec 14 14:35:32 14 kernel: [    0.212355] PCI: Using configuration type 1 for base access
Dec 14 14:35:32 14 kernel: [    0.212412] PCI: Using configuration type 1 for extended access
Dec 14 14:35:32 14 kernel: [    0.212618] mtrr: your CPUs had inconsistent variable MTRR settings
Dec 14 14:35:32 14 kernel: [    0.212677] mtrr: probably your BIOS does not setup all CPUs.
Dec 14 14:35:32 14 kernel: [    0.212734] mtrr: corrected configuration.
Dec 14 14:35:32 14 kernel: [    0.222321] ACPI: Added _OSI(Module Device)
Dec 14 14:35:32 14 kernel: [    0.222381] ACPI: Added _OSI(Processor Device)
Dec 14 14:35:32 14 kernel: [    0.222437] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 14 14:35:32 14 kernel: [    0.222493] ACPI: Added _OSI(Processor Aggregator Device)
Dec 14 14:35:32 14 kernel: [    0.223631] ACPI: Executed 1 blocks of module-level executable AML code
Dec 14 14:35:32 14 kernel: [    0.224851] ACPI: Interpreter enabled
Dec 14 14:35:32 14 kernel: [    0.224914] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150818/hwxface-580)
Dec 14 14:35:32 14 kernel: [    0.225077] ACPI: (supports S0 S1 S3 S4 S5)
Dec 14 14:35:32 14 kernel: [    0.225133] ACPI: Using IOAPIC for interrupt routing
Dec 14 14:35:32 14 kernel: [    0.225216] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
Dec 14 14:35:32 14 kernel: [    0.225867] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
Dec 14 14:35:32 14 kernel: [    0.225944] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 14 14:35:32 14 kernel: [    0.229359] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 14 14:35:32 14 kernel: [    0.229421] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Dec 14 14:35:32 14 kernel: [    0.229598] acpi PNP0A03:00: _OSC: platform does not support [PCIeHotplug PME PCIeCapability]
Dec 14 14:35:32 14 kernel: [    0.229717] acpi PNP0A03:00: _OSC: not requesting control; platform does not support [PCIeCapability]
Dec 14 14:35:32 14 kernel: [    0.229789] acpi PNP0A03:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
Dec 14 14:35:32 14 kernel: [    0.229862] acpi PNP0A03:00: _OSC: platform willing to grant [AER]
Dec 14 14:35:32 14 kernel: [    0.229920] acpi PNP0A03:00: _OSC failed (AE_SUPPORT); disabling ASPM
Dec 14 14:35:32 14 kernel: [    0.230039] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1f] only partially covers this bridge
Dec 14 14:35:32 14 kernel: [    0.230206] PCI host bridge to bus 0000:00
Dec 14 14:35:32 14 kernel: [    0.230264] pci_bus 0000:00: root bus resource [bus 00-ff]
Dec 14 14:35:32 14 kernel: [    0.230322] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Dec 14 14:35:32 14 kernel: [    0.230381] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Dec 14 14:35:32 14 kernel: [    0.230441] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Dec 14 14:35:32 14 kernel: [    0.230510] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
Dec 14 14:35:32 14 kernel: [    0.230579] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfbffffff window]
Dec 14 14:35:32 14 kernel: [    0.230649] pci_bus 0000:00: root bus resource [mem 0xfe000000-0xfebfffff window]
Dec 14 14:35:32 14 kernel: [    0.230733] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
Dec 14 14:35:32 14 kernel: [    0.230915] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
Dec 14 14:35:32 14 kernel: [    0.230923] pci 0000:00:01.0: reg 0x10: [io  0x4f00-0x4fff]
Dec 14 14:35:32 14 kernel: [    0.230993] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
Dec 14 14:35:32 14 kernel: [    0.231006] pci 0000:00:01.1: reg 0x10: [io  0x4900-0x493f]
Dec 14 14:35:32 14 kernel: [    0.231019] pci 0000:00:01.1: reg 0x20: [io  0x4d00-0x4d3f]
Dec 14 14:35:32 14 kernel: [    0.231024] pci 0000:00:01.1: reg 0x24: [io  0x4e00-0x4e3f]
Dec 14 14:35:32 14 kernel: [    0.231041] pci 0000:00:01.1: PME# supported from D3hot D3cold
Dec 14 14:35:32 14 kernel: [    0.231067] pci 0000:00:01.1: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.231155] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
Dec 14 14:35:32 14 kernel: [    0.231223] pci 0000:00:02.0: [10de:03f1] type 00 class 0x0c0310
Dec 14 14:35:32 14 kernel: [    0.231233] pci 0000:00:02.0: reg 0x10: [mem 0xfbfff000-0xfbffffff]
Dec 14 14:35:32 14 kernel: [    0.231260] pci 0000:00:02.0: supports D1 D2
Dec 14 14:35:32 14 kernel: [    0.231261] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:35:32 14 kernel: [    0.231283] pci 0000:00:02.0: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.231373] pci 0000:00:02.1: [10de:03f2] type 00 class 0x0c0320
Dec 14 14:35:32 14 kernel: [    0.231385] pci 0000:00:02.1: reg 0x10: [mem 0xfbffec00-0xfbffecff]
Dec 14 14:35:32 14 kernel: [    0.231414] pci 0000:00:02.1: supports D1 D2
Dec 14 14:35:32 14 kernel: [    0.231415] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:35:32 14 kernel: [    0.231438] pci 0000:00:02.1: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.231534] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
Dec 14 14:35:32 14 kernel: [    0.231578] pci 0000:00:04.0: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.231667] pci 0000:00:05.0: [10de:03f0] type 00 class 0x040300
Dec 14 14:35:32 14 kernel: [    0.231681] pci 0000:00:05.0: reg 0x10: [mem 0xfbff8000-0xfbffbfff]
Dec 14 14:35:32 14 kernel: [    0.231710] pci 0000:00:05.0: PME# supported from D3hot D3cold
Dec 14 14:35:32 14 kernel: [    0.231732] pci 0000:00:05.0: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.231828] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
Dec 14 14:35:32 14 kernel: [    0.231839] pci 0000:00:07.0: reg 0x10: [mem 0xfbffd000-0xfbffdfff]
Dec 14 14:35:32 14 kernel: [    0.231843] pci 0000:00:07.0: reg 0x14: [io  0xe480-0xe487]
Dec 14 14:35:32 14 kernel: [    0.231864] pci 0000:00:07.0: supports D1 D2
Dec 14 14:35:32 14 kernel: [    0.231865] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:35:32 14 kernel: [    0.231889] pci 0000:00:07.0: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.231978] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
Dec 14 14:35:32 14 kernel: [    0.231987] pci 0000:00:08.0: reg 0x10: [io  0xe400-0xe407]
Dec 14 14:35:32 14 kernel: [    0.231991] pci 0000:00:08.0: reg 0x14: [io  0xe080-0xe083]
Dec 14 14:35:32 14 kernel: [    0.231994] pci 0000:00:08.0: reg 0x18: [io  0xe000-0xe007]
Dec 14 14:35:32 14 kernel: [    0.231998] pci 0000:00:08.0: reg 0x1c: [io  0xdc00-0xdc03]
Dec 14 14:35:32 14 kernel: [    0.232001] pci 0000:00:08.0: reg 0x20: [io  0xd880-0xd88f]
Dec 14 14:35:32 14 kernel: [    0.232005] pci 0000:00:08.0: reg 0x24: [mem 0xfbffc000-0xfbffcfff]
Dec 14 14:35:32 14 kernel: [    0.232061] pci 0000:00:08.1: [10de:03f6] type 00 class 0x010185
Dec 14 14:35:32 14 kernel: [    0.232070] pci 0000:00:08.1: reg 0x10: [io  0xd800-0xd807]
Dec 14 14:35:32 14 kernel: [    0.232074] pci 0000:00:08.1: reg 0x14: [io  0xd480-0xd483]
Dec 14 14:35:32 14 kernel: [    0.232077] pci 0000:00:08.1: reg 0x18: [io  0xd400-0xd407]
Dec 14 14:35:32 14 kernel: [    0.232081] pci 0000:00:08.1: reg 0x1c: [io  0xd080-0xd083]
Dec 14 14:35:32 14 kernel: [    0.232084] pci 0000:00:08.1: reg 0x20: [io  0xd000-0xd00f]
Dec 14 14:35:32 14 kernel: [    0.232088] pci 0000:00:08.1: reg 0x24: [mem 0xfbff7000-0xfbff7fff]
Dec 14 14:35:32 14 kernel: [    0.232149] pci 0000:00:09.0: [10de:03e8] type 01 class 0x060400
Dec 14 14:35:32 14 kernel: [    0.232171] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:35:32 14 kernel: [    0.232194] pci 0000:00:09.0: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.232284] pci 0000:00:0b.0: [10de:03e9] type 01 class 0x060400
Dec 14 14:35:32 14 kernel: [    0.232304] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:35:32 14 kernel: [    0.232326] pci 0000:00:0b.0: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.232416] pci 0000:00:0c.0: [10de:03e9] type 01 class 0x060400
Dec 14 14:35:32 14 kernel: [    0.232436] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 14:35:32 14 kernel: [    0.232458] pci 0000:00:0c.0: System wakeup disabled by ACPI
Dec 14 14:35:32 14 kernel: [    0.232548] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
Dec 14 14:35:32 14 kernel: [    0.232556] pci 0000:00:0d.0: reg 0x10: [mem 0xfa000000-0xfaffffff]
Dec 14 14:35:32 14 kernel: [    0.232560] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
Dec 14 14:35:32 14 kernel: [    0.232565] pci 0000:00:0d.0: reg 0x1c: [mem 0xf9000000-0xf9ffffff 64bit]
Dec 14 14:35:32 14 kernel: [    0.232570] pci 0000:00:0d.0: reg 0x30: [mem 0xfbfc0000-0xfbfdffff pref]
Dec 14 14:35:32 14 kernel: [    0.232629] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Dec 14 14:35:32 14 kernel: [    0.232679] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Dec 14 14:35:32 14 kernel: [    0.232727] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Dec 14 14:35:32 14 kernel: [    0.232774] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Dec 14 14:35:32 14 kernel: [    0.232823] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Dec 14 14:35:32 14 kernel: [    0.232924] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
Dec 14 14:35:32 14 kernel: [    0.232986] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
Dec 14 14:35:32 14 kernel: [    0.232988] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
Dec 14 14:35:32 14 kernel: [    0.232990] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
Dec 14 14:35:32 14 kernel: [    0.232992] pci 0000:00:04.0:   bridge window [mem 0x000d0000-0x000dffff window] (subtractive decode)
Dec 14 14:35:32 14 kernel: [    0.232993] pci 0000:00:04.0:   bridge window [mem 0xe0000000-0xfbffffff window] (subtractive decode)
Dec 14 14:35:32 14 kernel: [    0.232995] pci 0000:00:04.0:   bridge window [mem 0xfe000000-0xfebfffff window] (subtractive decode)
Dec 14 14:35:32 14 kernel: [    0.233021] pci 0000:00:09.0: PCI bridge to [bus 02]
Dec 14 14:35:32 14 kernel: [    0.233103] pci 0000:00:0b.0: PCI bridge to [bus 03]
Dec 14 14:35:32 14 kernel: [    0.233185] pci 0000:00:0c.0: PCI bridge to [bus 04]
Dec 14 14:35:32 14 kernel: [    0.233251] pci_bus 0000:00: on NUMA node 0
Dec 14 14:35:32 14 kernel: [    0.233579] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.234043] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.234504] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.234965] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.235425] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.235885] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.236345] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.236806] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.237268] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *14
Dec 14 14:35:32 14 kernel: [    0.237688] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *7
Dec 14 14:35:32 14 kernel: [    0.238109] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
Dec 14 14:35:32 14 kernel: [    0.238529] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
Dec 14 14:35:32 14 kernel: [    0.238950] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *10
Dec 14 14:35:32 14 kernel: [    0.239370] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
Dec 14 14:35:32 14 kernel: [    0.239789] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.240251] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
Dec 14 14:35:32 14 kernel: [    0.240671] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *5
Dec 14 14:35:32 14 kernel: [    0.241098] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Dec 14 14:35:32 14 kernel: [    0.241654] vgaarb: setting as boot device: PCI:0000:00:0d.0
Dec 14 14:35:32 14 kernel: [    0.241712] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
Dec 14 14:35:32 14 kernel: [    0.241782] vgaarb: loaded
Dec 14 14:35:32 14 kernel: [    0.241836] vgaarb: bridge control possible 0000:00:0d.0
Dec 14 14:35:32 14 kernel: [    0.242124] SCSI subsystem initialized
Dec 14 14:35:32 14 kernel: [    0.242243] libata version 3.00 loaded.
Dec 14 14:35:32 14 kernel: [    0.242267] ACPI: bus type USB registered
Dec 14 14:35:32 14 kernel: [    0.242338] usbcore: registered new interface driver usbfs
Dec 14 14:35:32 14 kernel: [    0.242403] usbcore: registered new interface driver hub
Dec 14 14:35:32 14 kernel: [    0.242475] usbcore: registered new device driver usb
Dec 14 14:35:32 14 kernel: [    0.242686] PCI: Using ACPI for IRQ routing
Dec 14 14:35:32 14 kernel: [    0.243371] PCI: pci_cache_line_size set to 64 bytes
Dec 14 14:35:32 14 kernel: [    0.243397] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Dec 14 14:35:32 14 kernel: [    0.243399] e820: reserve RAM buffer [mem 0xcffb0000-0xcfffffff]
Dec 14 14:35:32 14 kernel: [    0.243502] NetLabel: Initializing
Dec 14 14:35:32 14 kernel: [    0.243557] NetLabel:  domain hash size = 128
Dec 14 14:35:32 14 kernel: [    0.243612] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 14 14:35:32 14 kernel: [    0.243679] NetLabel:  unlabeled traffic allowed by default
Dec 14 14:35:32 14 kernel: [    0.243827] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Dec 14 14:35:32 14 kernel: [    0.243890] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Dec 14 14:35:32 14 kernel: [    0.244111] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Dec 14 14:35:32 14 kernel: [    0.246299] clocksource: Switched to clocksource hpet
Dec 14 14:35:32 14 kernel: [    0.252293] AppArmor: AppArmor Filesystem Enabled
Dec 14 14:35:32 14 kernel: [    0.252423] pnp: PnP ACPI init
Dec 14 14:35:32 14 kernel: [    0.252569] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 14 14:35:32 14 kernel: [    0.252689] system 00:01: [io  0x0a00-0x0adf] has been reserved
Dec 14 14:35:32 14 kernel: [    0.252750] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 14:35:32 14 kernel: [    0.253019] system 00:02: [io  0x04d0-0x04d1] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253078] system 00:02: [io  0x0800-0x080f] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253137] system 00:02: [io  0x4000-0x407f] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.253196] system 00:02: [io  0x4080-0x40ff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253255] system 00:02: [io  0x4400-0x447f] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253313] system 00:02: [io  0x4480-0x44ff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253372] system 00:02: [io  0x4800-0x487f] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253430] system 00:02: [io  0x4880-0x48ff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253488] system 00:02: [io  0x4c00-0x4c7f] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253547] system 00:02: [io  0x4c80-0x4cff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253606] system 00:02: [mem 0x000d0000-0x000d3fff window] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253676] system 00:02: [mem 0x000d4000-0x000d7fff window] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253745] system 00:02: [mem 0x000de000-0x000dffff window] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253815] system 00:02: [mem 0xfec80000-0x1fd93ffff] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.253875] system 00:02: [mem 0xfefe0000-0xfefe01ff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253934] system 00:02: [mem 0xfefe1000-0xfefe1fff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.253994] system 00:02: [mem 0xfee01000-0xfeefffff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.254053] system 00:02: [mem 0xffb80000-0xffffffff] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.254114] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 14:35:32 14 kernel: [    0.254211] system 00:03: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.254271] system 00:03: [mem 0xfee00000-0xfee00fff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.254347] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 14:35:32 14 kernel: [    0.254402] system 00:04: [mem 0xfc000000-0xfdffffff] has been reserved
Dec 14 14:35:32 14 kernel: [    0.254462] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 14:35:32 14 kernel: [    0.254578] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.254638] system 00:05: [mem 0x000c0000-0x000cffff] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.254698] system 00:05: [mem 0x000e0000-0x000fffff] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.254758] system 00:05: [mem 0x00100000-0xdfffffff] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.254818] system 00:05: [mem 0xfec00000-0xffffffff] could not be reserved
Dec 14 14:35:32 14 kernel: [    0.254878] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 14 14:35:32 14 kernel: [    0.255087] pnp: PnP ACPI: found 6 devices
Dec 14 14:35:32 14 kernel: [    0.261571] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Dec 14 14:35:32 14 kernel: [    0.261660] pci 0000:00:04.0: PCI bridge to [bus 01]
Dec 14 14:35:32 14 kernel: [    0.261722] pci 0000:00:09.0: PCI bridge to [bus 02]
Dec 14 14:35:32 14 kernel: [    0.261781] pci 0000:00:0b.0: PCI bridge to [bus 03]
Dec 14 14:35:32 14 kernel: [    0.261841] pci 0000:00:0c.0: PCI bridge to [bus 04]
Dec 14 14:35:32 14 kernel: [    0.261900] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
Dec 14 14:35:32 14 kernel: [    0.261902] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
Dec 14 14:35:32 14 kernel: [    0.261904] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
Dec 14 14:35:32 14 kernel: [    0.261906] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
Dec 14 14:35:32 14 kernel: [    0.261908] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfbffffff window]
Dec 14 14:35:32 14 kernel: [    0.261909] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff window]
Dec 14 14:35:32 14 kernel: [    0.261911] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7 window]
Dec 14 14:35:32 14 kernel: [    0.261913] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff window]
Dec 14 14:35:32 14 kernel: [    0.261915] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff window]
Dec 14 14:35:32 14 kernel: [    0.261916] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff window]
Dec 14 14:35:32 14 kernel: [    0.261918] pci_bus 0000:01: resource 8 [mem 0xe0000000-0xfbffffff window]
Dec 14 14:35:32 14 kernel: [    0.261920] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff window]
Dec 14 14:35:32 14 kernel: [    0.261954] NET: Registered protocol family 2
Dec 14 14:35:32 14 kernel: [    0.262158] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Dec 14 14:35:32 14 kernel: [    0.262324] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Dec 14 14:35:32 14 kernel: [    0.262500] TCP: Hash tables configured (established 32768 bind 32768)
Dec 14 14:35:32 14 kernel: [    0.262600] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Dec 14 14:35:32 14 kernel: [    0.262683] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Dec 14 14:35:32 14 kernel: [    0.262820] NET: Registered protocol family 1
Dec 14 14:35:32 14 kernel: [    0.338465] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:35:32 14 kernel: [    0.338567] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:35:32 14 kernel: [    0.338667] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:35:32 14 kernel: [    0.338768] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:35:32 14 kernel: [    0.338868] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:35:32 14 kernel: [    0.338971] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:35:32 14 kernel: [    0.339076] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:35:32 14 kernel: [    0.339183] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 14:35:32 14 kernel: [    0.339244] pci 0000:00:0d.0: Video device with shadowed ROM
Dec 14 14:35:32 14 kernel: [    0.339253] PCI: CLS 64 bytes, default 64
Dec 14 14:35:32 14 kernel: [    0.339314] Trying to unpack rootfs image as initramfs...
Dec 14 14:35:32 14 kernel: [    0.805554] Freeing initrd memory: 33476K (ffff880033e8e000 - ffff880035f3f000)
Dec 14 14:35:32 14 kernel: [    0.805973] ACPI: PCI Interrupt Link [LSMB] enabled at IRQ 23
Dec 14 14:35:32 14 kernel: [    0.806235] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
Dec 14 14:35:32 14 kernel: [    0.806475] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
Dec 14 14:35:32 14 kernel: [    0.806748] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
Dec 14 14:35:32 14 kernel: [    0.806987] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
Dec 14 14:35:32 14 kernel: [    0.807227] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
Dec 14 14:35:32 14 kernel: [    0.807467] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 21
Dec 14 14:35:32 14 kernel: [    0.807720] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 20
Dec 14 14:35:32 14 kernel: [    0.807841] PCI-DMA: Disabling AGP.
Dec 14 14:35:32 14 kernel: [    0.807961] PCI-DMA: aperture base @ c4000000 size 65536 KB
Dec 14 14:35:32 14 kernel: [    0.808019] PCI-DMA: using GART IOMMU.
Dec 14 14:35:32 14 kernel: [    0.808076] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Dec 14 14:35:32 14 kernel: [    0.810591] microcode: CPU0: patch_level=0x01000098
Dec 14 14:35:32 14 kernel: [    0.810670] microcode: CPU1: patch_level=0x01000098
Dec 14 14:35:32 14 kernel: [    0.810805] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Dec 14 14:35:32 14 kernel: [    0.810886] LVT offset 1 assigned for vector 0x400
Dec 14 14:35:32 14 kernel: [    0.810955] IBS: LVT offset 1 assigned
Dec 14 14:35:32 14 kernel: [    0.811029] perf: AMD IBS detected (0x0000001f)
Dec 14 14:35:32 14 kernel: [    0.811142] Scanning for low memory corruption every 60 seconds
Dec 14 14:35:32 14 kernel: [    0.811472] futex hash table entries: 1024 (order: 4, 65536 bytes)
Dec 14 14:35:32 14 kernel: [    0.814775] audit: initializing netlink subsys (disabled)
Dec 14 14:35:32 14 kernel: [    0.814847] audit: type=2000 audit(1450103721.712:1): initialized
Dec 14 14:35:32 14 kernel: [    0.815122] Initialise system trusted keyring
Dec 14 14:35:32 14 kernel: [    0.815302] HugeTLB registered 1 GB page size, pre-allocated 0 pages
Dec 14 14:35:32 14 kernel: [    0.815365] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 14 14:35:32 14 kernel: [    0.816793] zbud: loaded
Dec 14 14:35:32 14 kernel: [    0.817118] VFS: Disk quotas dquot_6.6.0
Dec 14 14:35:32 14 kernel: [    0.817208] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 14 14:35:32 14 kernel: [    0.817762] fuse init (API version 7.23)
Dec 14 14:35:32 14 kernel: [    0.818006] Key type big_key registered
Dec 14 14:35:32 14 kernel: [    0.818521] Key type asymmetric registered
Dec 14 14:35:32 14 kernel: [    0.818582] Asymmetric key parser 'x509' registered
Dec 14 14:35:32 14 kernel: [    0.818663] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
Dec 14 14:35:32 14 kernel: [    0.818791] io scheduler noop registered
Dec 14 14:35:32 14 kernel: [    0.818848] io scheduler deadline registered (default)
Dec 14 14:35:32 14 kernel: [    0.818939] io scheduler cfq registered
Dec 14 14:35:32 14 kernel: [    0.819220] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 14 14:35:32 14 kernel: [    0.819283] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 14 14:35:32 14 kernel: [    0.819429] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 14 14:35:32 14 kernel: [    0.819501] ACPI: Power Button [PWRB]
Dec 14 14:35:32 14 kernel: [    0.819591] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 14 14:35:32 14 kernel: [    0.819660] ACPI: Power Button [PWRF]
Dec 14 14:35:32 14 kernel: [    0.819872] GHES: HEST is not enabled!
Dec 14 14:35:32 14 kernel: [    0.820029] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 14 14:35:32 14 kernel: [    0.821488] Linux agpgart interface v0.103
Dec 14 14:35:32 14 kernel: [    0.824168] brd: module loaded
Dec 14 14:35:32 14 kernel: [    0.825453] loop: module loaded
Dec 14 14:35:32 14 kernel: [    0.826008] libphy: Fixed MDIO Bus: probed
Dec 14 14:35:32 14 kernel: [    0.826066] tun: Universal TUN/TAP device driver, 1.6
Dec 14 14:35:32 14 kernel: [    0.826122] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 14 14:35:32 14 kernel: [    0.826253] PPP generic driver version 2.4.2
Dec 14 14:35:32 14 kernel: [    0.826397] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 14 14:35:32 14 kernel: [    0.826465] ehci-pci: EHCI PCI platform driver
Dec 14 14:35:32 14 kernel: [    0.826592] ehci-pci 0000:00:02.1: EHCI Host Controller
Dec 14 14:35:32 14 kernel: [    0.826653] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
Dec 14 14:35:32 14 kernel: [    0.826759] ehci-pci 0000:00:02.1: debug port 1
Dec 14 14:35:32 14 kernel: [    0.826840] ehci-pci 0000:00:02.1: cache line size of 64 is not supported
Dec 14 14:35:32 14 kernel: [    0.826859] ehci-pci 0000:00:02.1: irq 21, io mem 0xfbffec00
Dec 14 14:35:32 14 kernel: [    0.838732] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
Dec 14 14:35:32 14 kernel: [    0.838841] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Dec 14 14:35:32 14 kernel: [    0.838900] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 14 14:35:32 14 kernel: [    0.838970] usb usb1: Product: EHCI Host Controller
Dec 14 14:35:32 14 kernel: [    0.839027] usb usb1: Manufacturer: Linux 4.3.0-2-generic ehci_hcd
Dec 14 14:35:32 14 kernel: [    0.839086] usb usb1: SerialNumber: 0000:00:02.1
Dec 14 14:35:32 14 kernel: [    0.839316] hub 1-0:1.0: USB hub found
Dec 14 14:35:32 14 kernel: [    0.839379] hub 1-0:1.0: 10 ports detected
Dec 14 14:35:32 14 kernel: [    0.839601] ehci-platform: EHCI generic platform driver
Dec 14 14:35:32 14 kernel: [    0.839671] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 14 14:35:32 14 kernel: [    0.839732] ohci-pci: OHCI PCI platform driver
Dec 14 14:35:32 14 kernel: [    0.839884] ohci-pci 0000:00:02.0: OHCI PCI host controller
Dec 14 14:35:32 14 kernel: [    0.839946] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
Dec 14 14:35:32 14 kernel: [    0.840041] ohci-pci 0000:00:02.0: irq 22, io mem 0xfbfff000
Dec 14 14:35:32 14 kernel: [    0.896795] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Dec 14 14:35:32 14 kernel: [    0.896858] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 14 14:35:32 14 kernel: [    0.896927] usb usb2: Product: OHCI PCI host controller
Dec 14 14:35:32 14 kernel: [    0.896984] usb usb2: Manufacturer: Linux 4.3.0-2-generic ohci_hcd
Dec 14 14:35:32 14 kernel: [    0.897043] usb usb2: SerialNumber: 0000:00:02.0
Dec 14 14:35:32 14 kernel: [    0.897270] hub 2-0:1.0: USB hub found
Dec 14 14:35:32 14 kernel: [    0.897332] hub 2-0:1.0: 10 ports detected
Dec 14 14:35:32 14 kernel: [    0.897560] ohci-platform: OHCI generic platform driver
Dec 14 14:35:32 14 kernel: [    0.897630] uhci_hcd: USB Universal Host Controller Interface driver
Dec 14 14:35:32 14 kernel: [    0.897739] i8042: PNP: No PS/2 controller found. Probing ports directly.
Dec 14 14:35:32 14 kernel: [    0.900030] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 14 14:35:32 14 kernel: [    0.900100] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 14 14:35:32 14 kernel: [    0.900332] mousedev: PS/2 mouse device common for all mice
Dec 14 14:35:32 14 kernel: [    0.900581] rtc_cmos 00:00: RTC can wake from S4
Dec 14 14:35:32 14 kernel: [    0.900811] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
Dec 14 14:35:32 14 kernel: [    0.900905] rtc_cmos 00:00: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Dec 14 14:35:32 14 kernel: [    0.900980] i2c /dev entries driver
Dec 14 14:35:32 14 kernel: [    0.901093] device-mapper: uevent: version 1.0.3
Dec 14 14:35:32 14 kernel: [    0.901241] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
Dec 14 14:35:32 14 kernel: [    0.901328] ledtrig-cpu: registered to indicate activity on CPUs
Dec 14 14:35:32 14 kernel: [    0.901712] NET: Registered protocol family 10
Dec 14 14:35:32 14 kernel: [    0.902017] NET: Registered protocol family 17
Dec 14 14:35:32 14 kernel: [    0.902091] Key type dns_resolver registered
Dec 14 14:35:32 14 kernel: [    0.902502] registered taskstats version 1
Dec 14 14:35:32 14 kernel: [    0.902568] Loading compiled-in X.509 certificates
Dec 14 14:35:32 14 kernel: [    0.903594] Loaded X.509 cert 'Build time autogenerated kernel key: 529a908f1f1fa68336efe06eb8e57dd6a88b5796'
Dec 14 14:35:32 14 kernel: [    0.903681] zswap: loaded using pool lzo/zbud
Dec 14 14:35:32 14 kernel: [    0.905719] Key type trusted registered
Dec 14 14:35:32 14 kernel: [    0.909270] Key type encrypted registered
Dec 14 14:35:32 14 kernel: [    0.909336] AppArmor: AppArmor sha1 policy hashing enabled
Dec 14 14:35:32 14 kernel: [    0.909396] ima: No TPM chip found, activating TPM-bypass!
Dec 14 14:35:32 14 kernel: [    0.909471] evm: HMAC attrs: 0x1
Dec 14 14:35:32 14 kernel: [    0.909716]   Magic number: 11:602:586
Dec 14 14:35:32 14 kernel: [    0.909877] rtc_cmos 00:00: setting system clock to 2015-12-14 14:35:22 UTC (1450103722)
Dec 14 14:35:32 14 kernel: [    0.910028] acpi-cpufreq: overriding BIOS provided _PSD data
Dec 14 14:35:32 14 kernel: [    0.910148] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 14 14:35:32 14 kernel: [    0.910206] EDD information not available.
Dec 14 14:35:32 14 kernel: [    0.910311] PM: Hibernation image not present or could not be loaded.
Dec 14 14:35:32 14 kernel: [    0.910794] Freeing unused kernel memory: 1464K (ffffffff81f3a000 - ffffffff820a8000)
Dec 14 14:35:32 14 kernel: [    0.910868] Write protecting the kernel read-only data: 14336k
Dec 14 14:35:32 14 kernel: [    0.911710] Freeing unused kernel memory: 2036K (ffff880001803000 - ffff880001a00000)
Dec 14 14:35:32 14 kernel: [    0.911901] Freeing unused kernel memory: 244K (ffff880001dc3000 - ffff880001e00000)
Dec 14 14:35:32 14 kernel: [    0.927474] random: systemd-udevd urandom read with 2 bits of entropy available
Dec 14 14:35:32 14 kernel: [    0.959649] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
Dec 14 14:35:32 14 kernel: [    0.961143] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Dec 14 14:35:32 14 kernel: [    1.150921] usb 1-1: new high-speed USB device number 2 using ehci-pci
Dec 14 14:35:32 14 kernel: [    1.285646] usb 1-1: New USB device found, idVendor=04b4, idProduct=6830
Dec 14 14:35:32 14 kernel: [    1.285710] usb 1-1: New USB device strings: Mfr=56, Product=78, SerialNumber=100
Dec 14 14:35:32 14 kernel: [    1.285780] usb 1-1: Product: USB2.0 Storage Device
Dec 14 14:35:32 14 kernel: [    1.285838] usb 1-1: Manufacturer: Cypress Semiconductor
Dec 14 14:35:32 14 kernel: [    1.285895] usb 1-1: SerialNumber: DEF10A366B82
Dec 14 14:35:32 14 kernel: [    1.289313] usbcore: registered new interface driver usb-storage
Dec 14 14:35:32 14 kernel: [    1.290678] usbcore: registered new interface driver uas
Dec 14 14:35:32 14 kernel: [    1.291890] ums-cypress 1-1:1.0: USB Mass Storage device detected
Dec 14 14:35:32 14 kernel: [    1.292173] scsi host0: usb-storage 1-1:1.0
Dec 14 14:35:32 14 kernel: [    1.292299] usbcore: registered new interface driver ums-cypress
Dec 14 14:35:32 14 kernel: [    1.451118] usb 1-9: new high-speed USB device number 4 using ehci-pci
Dec 14 14:35:32 14 kernel: [    1.475477] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr e0:cb:4e:9b:e8:4d
Dec 14 14:35:32 14 kernel: [    1.475552] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
Dec 14 14:35:32 14 kernel: [    1.475737] sata_nv 0000:00:08.0: version 3.5
Dec 14 14:35:32 14 kernel: [    1.476576] forcedeth 0000:00:07.0 enp0s7: renamed from eth0
Dec 14 14:35:32 14 kernel: [    1.476973] scsi host1: sata_nv
Dec 14 14:35:32 14 kernel: [    1.477182] scsi host2: sata_nv
Dec 14 14:35:32 14 kernel: [    1.477284] ata1: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 22
Dec 14 14:35:32 14 kernel: [    1.477351] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 22
Dec 14 14:35:32 14 kernel: [    1.477957] scsi host3: sata_nv
Dec 14 14:35:32 14 kernel: [    1.478298] scsi host4: sata_nv
Dec 14 14:35:32 14 kernel: [    1.478427] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 21
Dec 14 14:35:32 14 kernel: [    1.478489] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 21
Dec 14 14:35:32 14 kernel: [    1.585590] usb 1-9: New USB device found, idVendor=058f, idProduct=6366
Dec 14 14:35:32 14 kernel: [    1.585655] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 14 14:35:32 14 kernel: [    1.585715] usb 1-9: Product: Mass Storage Device
Dec 14 14:35:32 14 kernel: [    1.585772] usb 1-9: Manufacturer: Generic
Dec 14 14:35:32 14 kernel: [    1.585828] usb 1-9: SerialNumber: 058F63666471
Dec 14 14:35:32 14 kernel: [    1.586408] usb-storage 1-9:1.0: USB Mass Storage device detected
Dec 14 14:35:32 14 kernel: [    1.586579] scsi host5: usb-storage 1-9:1.0
Dec 14 14:35:32 14 kernel: [    1.639239] usb 2-4: new low-speed USB device number 2 using ohci-pci
Dec 14 14:35:32 14 kernel: [    1.797586] ata3: SATA link down (SStatus 0 SControl 300)
Dec 14 14:35:32 14 kernel: [    1.807345] tsc: Refined TSC clocksource calibration: 3013.705 MHz
Dec 14 14:35:32 14 kernel: [    1.807409] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b70d7a0847, max_idle_ns: 440795224568 ns
Dec 14 14:35:32 14 kernel: [    1.854424] usb 2-4: New USB device found, idVendor=04fc, idProduct=05d8
Dec 14 14:35:32 14 kernel: [    1.854487] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 14 14:35:32 14 kernel: [    1.854547] usb 2-4: Product: wireless combo
Dec 14 14:35:32 14 kernel: [    1.854603] usb 2-4: Manufacturer: MLK
Dec 14 14:35:32 14 kernel: [    1.872668] hidraw: raw HID events driver (C) Jiri Kosina
Dec 14 14:35:32 14 kernel: [    1.889532] usbcore: registered new interface driver usbhid
Dec 14 14:35:32 14 kernel: [    1.889595] usbhid: USB HID core driver
Dec 14 14:35:32 14 kernel: [    1.891332] input: MLK wireless combo as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/0003:04FC:05D8.0001/input/input5
Dec 14 14:35:32 14 kernel: [    1.943454] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 14:35:32 14 kernel: [    1.947576] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK wireless combo] on usb-0000:00:02.0-4/input0
Dec 14 14:35:32 14 kernel: [    1.947677] sunplus 0003:04FC:05D8.0002: fixing up Sunplus Wireless Desktop report descriptor
Dec 14 14:35:32 14 kernel: [    1.948578] input: MLK wireless combo as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/0003:04FC:05D8.0002/input/input6
Dec 14 14:35:32 14 kernel: [    1.951863] ata1.00: ATA-8: WDC WD10EZEX-00ZF5A0, 80.00A80, max UDMA/133
Dec 14 14:35:32 14 kernel: [    1.951928] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 14:35:32 14 kernel: [    1.959882] ata1.00: configured for UDMA/133
Dec 14 14:35:32 14 kernel: [    1.960139] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EZEX-00Z 0A80 PQ: 0 ANSI: 5
Dec 14 14:35:32 14 kernel: [    1.960530] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 14:35:32 14 kernel: [    1.960605] sd 1:0:0:0: [sda] 4096-byte physical blocks
Dec 14 14:35:32 14 kernel: [    1.960681] sd 1:0:0:0: Attached scsi generic sg0 type 0
Dec 14 14:35:32 14 kernel: [    1.960757] sd 1:0:0:0: [sda] Write Protect is off
Dec 14 14:35:32 14 kernel: [    1.960822] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 14 14:35:32 14 kernel: [    1.960874] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 14:35:32 14 kernel: [    2.003681] sunplus 0003:04FC:05D8.0002: input,hiddev0,hidraw1: USB HID v1.00 Mouse [MLK wireless combo] on usb-0000:00:02.0-4/input1
Dec 14 14:35:32 14 kernel: [    2.025471]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
Dec 14 14:35:32 14 kernel: [    2.026069] sd 1:0:0:0: [sda] Attached SCSI disk
Dec 14 14:35:32 14 kernel: [    2.281888] ata2: SATA link down (SStatus 0 SControl 300)
Dec 14 14:35:32 14 kernel: [    2.293825] scsi 0:0:0:0: Direct-Access     TOSHIBA  MK6025GAS        0000 PQ: 0 ANSI: 0
Dec 14 14:35:32 14 kernel: [    2.294231] sd 0:0:0:0: Attached scsi generic sg1 type 0
Dec 14 14:35:32 14 kernel: [    2.295575] sd 0:0:0:0: [sdb] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
Dec 14 14:35:32 14 kernel: [    2.296572] sd 0:0:0:0: [sdb] Write Protect is off
Dec 14 14:35:32 14 kernel: [    2.296635] sd 0:0:0:0: [sdb] Mode Sense: 27 00 00 00
Dec 14 14:35:32 14 kernel: [    2.297571] sd 0:0:0:0: [sdb] No Caching mode page found
Dec 14 14:35:32 14 kernel: [    2.297633] sd 0:0:0:0: [sdb] Assuming drive cache: write through
Dec 14 14:35:32 14 kernel: [    2.566865]  sdb: sdb1 sdb2 < > sdb3
Dec 14 14:35:32 14 kernel: [    2.570126] sd 0:0:0:0: [sdb] Attached SCSI disk
Dec 14 14:35:32 14 kernel: [    2.584754] scsi 5:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
Dec 14 14:35:32 14 kernel: [    2.585173] sd 5:0:0:0: Attached scsi generic sg2 type 0
Dec 14 14:35:32 14 kernel: [    2.587383] sd 5:0:0:0: [sdc] Attached SCSI removable disk
Dec 14 14:35:32 14 kernel: [    2.602108] ata4: SATA link down (SStatus 0 SControl 300)
Dec 14 14:35:32 14 kernel: [    2.808065] clocksource: Switched to clocksource tsc
Dec 14 14:35:32 14 kernel: [    3.267647] random: nonblocking pool is initialized
Dec 14 14:35:32 14 kernel: [    3.709429] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Dec 14 14:35:32 14 kernel: [    5.592404] lp: driver loaded but no devices found
Dec 14 14:35:32 14 kernel: [    5.617096] ppdev: user-space parallel port driver
Dec 14 14:35:32 14 kernel: [    6.659135] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Dec 14 14:35:32 14 kernel: [    7.459949] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
Dec 14 14:35:32 14 kernel: [    7.459995] i2c i2c-1: nForce2 SMBus adapter at 0x4e00
Dec 14 14:35:32 14 kernel: [    7.483511] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 14 14:35:32 14 kernel: [    7.562807] [drm] Initialized drm 1.1.0 20060810
Dec 14 14:35:32 14 kernel: [    7.614348] EDAC MC: Ver: 3.0.0
Dec 14 14:35:32 14 kernel: [    7.650057] MCE: In-kernel MCE decoding enabled.
Dec 14 14:35:32 14 kernel: [    7.696591] AMD64 EDAC driver v3.4.0
Dec 14 14:35:32 14 kernel: [    7.696622] EDAC amd64: DRAM ECC disabled.
Dec 14 14:35:32 14 kernel: [    7.696627] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Dec 14 14:35:32 14 kernel: [    7.696627]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Dec 14 14:35:32 14 kernel: [    7.696627]  (Note that use of the override may cause unknown side effects.)
Dec 14 14:35:32 14 kernel: [    8.040383] kvm: disabled by bios
Dec 14 14:35:32 14 kernel: [    8.356486] snd_hda_intel 0000:00:05.0: Disabling MSI
Dec 14 14:35:32 14 kernel: [    9.096049] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC662 rev1: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
Dec 14 14:35:32 14 kernel: [    9.096054] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Dec 14 14:35:32 14 kernel: [    9.096056] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Dec 14 14:35:32 14 kernel: [    9.096058] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Dec 14 14:35:32 14 kernel: [    9.096059] snd_hda_codec_realtek hdaudioC0D0:    inputs:
Dec 14 14:35:32 14 kernel: [    9.096061] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
Dec 14 14:35:32 14 kernel: [    9.096062] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
Dec 14 14:35:32 14 kernel: [    9.590396] Adding 2047996k swap on /dev/sda5.  Priority:-1 extents:1 across:2047996k FS
Dec 14 14:35:32 14 kernel: [   10.007388] nvidia: module license 'NVIDIA' taints kernel.
Dec 14 14:35:32 14 kernel: [   10.007392] Disabling lock debugging due to kernel taint
Dec 14 14:35:32 14 kernel: [   10.015029] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Dec 14 14:35:32 14 kernel: [   10.015310] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:35:32 14 kernel: [   10.015452] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 14:35:32 14 kernel: [   10.113843] audit: type=1400 audit(1450132531.695:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.113852] audit: type=1400 audit(1450132531.695:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.151310] audit: type=1400 audit(1450132531.731:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.151320] audit: type=1400 audit(1450132531.731:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.151325] audit: type=1400 audit(1450132531.731:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.151329] audit: type=1400 audit(1450132531.731:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.266691] audit: type=1400 audit(1450132531.847:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.266701] audit: type=1400 audit(1450132531.847:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.266706] audit: type=1400 audit(1450132531.847:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.266710] audit: type=1400 audit(1450132531.847:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=438 comm="apparmor_parser"
Dec 14 14:35:32 14 kernel: [   10.433617] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
Dec 14 14:35:32 14 kernel: [   10.433683] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
Dec 14 14:35:32 14 kernel: [   10.433744] input: HDA NVidia Line Out as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
Dec 14 14:35:32 14 kernel: [   10.433804] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
Dec 14 14:35:34 14 kernel: [   13.169568] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
Dec 14 14:35:34 14 kernel: [   13.170106] forcedeth 0000:00:07.0 enp0s7: MSI enabled
Dec 14 14:35:38 14 kernel: [   17.213701] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:35:38 14 kernel: [   17.213846] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 14:35:38 14 kernel: [   17.253947] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:35:38 14 kernel: [   17.254091] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 16:40:30 14 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 14 16:40:30 14 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 14 16:40:30 14 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Dec 14 16:40:30 14 kernel: [    0.000000] Linux version 4.3.0-2-generic (buildd@lgw01-24) (gcc version 5.2.1 20151129 (Ubuntu 5.2.1-27ubuntu1) ) #11-Ubuntu SMP Fri Dec 4 20:37:48 UTC 2015 (Ubuntu 4.3.0-2.11-generic 4.3.0)
Dec 14 16:40:30 14 kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz root=UUID=107bf235-82e7-4095-8e55-397abe9ab3b3 ro splash quiet
Dec 14 16:40:30 14 kernel: [    0.000000] KERNEL supported cpus:
Dec 14 16:40:30 14 kernel: [    0.000000]   Intel GenuineIntel
Dec 14 16:40:30 14 kernel: [    0.000000]   AMD AuthenticAMD
Dec 14 16:40:30 14 kernel: [    0.000000]   Centaur CentaurHauls
Dec 14 16:40:30 14 kernel: [    0.000000] tseg: 0000000000
Dec 14 16:40:30 14 kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
Dec 14 16:40:30 14 kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Dec 14 16:40:30 14 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cffaffff] usable
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffb0000-0x00000000cffbdfff] ACPI data
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cffbe000-0x00000000cffeffff] ACPI NVS
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfff0000-0x00000000cfffffff] reserved
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Dec 14 16:40:30 14 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
Dec 14 16:40:30 14 kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 14 16:40:30 14 kernel: [    0.000000] SMBIOS 2.5 present.
Dec 14 16:40:30 14 kernel: [    0.000000] DMI: HP-Pavilion AY652AA-ABA s5310y/Narra6, BIOS 5.17    01/07/2010
Dec 14 16:40:30 14 kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Dec 14 16:40:30 14 kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Dec 14 16:40:30 14 kernel: [    0.000000] AGP: No AGP bridge found
Dec 14 16:40:30 14 kernel: [    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x400000000
Dec 14 16:40:30 14 kernel: [    0.000000] MTRR default type: uncachable
Dec 14 16:40:30 14 kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 14 16:40:30 14 kernel: [    0.000000]   00000-9FFFF write-back
Dec 14 16:40:30 14 kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 14 16:40:30 14 kernel: [    0.000000]   C0000-CFFFF write-protect
Dec 14 16:40:30 14 kernel: [    0.000000]   D0000-EFFFF uncachable
Dec 14 16:40:30 14 kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 14 16:40:30 14 kernel: [    0.000000] MTRR variable ranges enabled:
Dec 14 16:40:30 14 kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Dec 14 16:40:30 14 kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Dec 14 16:40:30 14 kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Dec 14 16:40:30 14 kernel: [    0.000000]   3 disabled
Dec 14 16:40:30 14 kernel: [    0.000000]   4 disabled
Dec 14 16:40:30 14 kernel: [    0.000000]   5 disabled
Dec 14 16:40:30 14 kernel: [    0.000000]   6 disabled
Dec 14 16:40:30 14 kernel: [    0.000000]   7 disabled
Dec 14 16:40:30 14 kernel: [    0.000000] TOM2: 0000000120000000 aka 4608M
Dec 14 16:40:30 14 kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Dec 14 16:40:30 14 kernel: [    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Dec 14 16:40:30 14 kernel: [    0.000000] e820: last_pfn = 0xcffb0 max_arch_pfn = 0x400000000
Dec 14 16:40:30 14 kernel: [    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
Dec 14 16:40:30 14 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 14 16:40:30 14 kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Dec 14 16:40:30 14 kernel: [    0.000000] Using GB pages for direct mapping
Dec 14 16:40:30 14 kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Dec 14 16:40:30 14 kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Dec 14 16:40:30 14 kernel: [    0.000000] BRK [0x021f6000, 0x021f6fff] PGTABLE
Dec 14 16:40:30 14 kernel: [    0.000000] BRK [0x021f7000, 0x021f7fff] PGTABLE
Dec 14 16:40:30 14 kernel: [    0.000000] BRK [0x021f8000, 0x021f8fff] PGTABLE
Dec 14 16:40:30 14 kernel: [    0.000000] init_memory_mapping: [mem 0x11fe00000-0x11fffffff]
Dec 14 16:40:30 14 kernel: [    0.000000]  [mem 0x11fe00000-0x11fffffff] page 2M
Dec 14 16:40:30 14 kernel: [    0.000000] BRK [0x021f9000, 0x021f9fff] PGTABLE
Dec 14 16:40:30 14 kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11fdfffff]
Dec 14 16:40:30 14 kernel: [    0.000000]  [mem 0x100000000-0x11fdfffff] page 2M
Dec 14 16:40:30 14 kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xcffaffff]
Dec 14 16:40:30 14 kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Dec 14 16:40:30 14 kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Dec 14 16:40:30 14 kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
Dec 14 16:40:30 14 kernel: [    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
Dec 14 16:40:30 14 kernel: [    0.000000]  [mem 0xcfe00000-0xcffaffff] page 4k
Dec 14 16:40:30 14 kernel: [    0.000000] RAMDISK: [mem 0x33e8e000-0x35f3efff]
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: Early table checksum verification disabled
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: RSDP 0x00000000000FB220 000014 (v00 HPQOEM)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: RSDT 0x00000000CFFB0000 000040 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: FACP 0x00000000CFFB0200 000084 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: DSDT 0x00000000CFFB0450 0043AF (v01 HPQOEM SLIC-CPC 00000001 INTL 20051117)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: FACS 0x00000000CFFBE000 000040
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: APIC 0x00000000CFFB0390 000080 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: MCFG 0x00000000CFFB0410 00003C (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: OEMB 0x00000000CFFBE040 000072 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: HPET 0x00000000CFFB4800 000038 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: SLIC 0x00000000CFFBE0C0 000176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: SSDT 0x00000000CFFB4840 000458 (v01 HPQOEM SLIC-CPC 00000001 AMD  00000001)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 16:40:30 14 kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Dec 14 16:40:30 14 kernel: [    0.000000] No NUMA configuration found
Dec 14 16:40:30 14 kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011fffffff]
Dec 14 16:40:30 14 kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x11fff9000-0x11fffdfff]
Dec 14 16:40:30 14 kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011ba00000-ffff88011f5fffff] on node 0
Dec 14 16:40:30 14 kernel: [    0.000000] Zone ranges:
Dec 14 16:40:30 14 kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Dec 14 16:40:30 14 kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Dec 14 16:40:30 14 kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000011fffffff]
Dec 14 16:40:30 14 kernel: [    0.000000] Movable zone start for each node
Dec 14 16:40:30 14 kernel: [    0.000000] Early memory node ranges
Dec 14 16:40:30 14 kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
Dec 14 16:40:30 14 kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x00000000cffaffff]
Dec 14 16:40:30 14 kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000011fffffff]
Dec 14 16:40:30 14 kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000011fffffff]
Dec 14 16:40:30 14 kernel: [    0.000000] On node 0 totalpages: 982862
Dec 14 16:40:30 14 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Dec 14 16:40:30 14 kernel: [    0.000000]   DMA zone: 21 pages reserved
Dec 14 16:40:30 14 kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Dec 14 16:40:30 14 kernel: [    0.000000]   DMA32 zone: 13247 pages used for memmap
Dec 14 16:40:30 14 kernel: [    0.000000]   DMA32 zone: 847792 pages, LIFO batch:31
Dec 14 16:40:30 14 kernel: [    0.000000]   Normal zone: 2048 pages used for memmap
Dec 14 16:40:30 14 kernel: [    0.000000]   Normal zone: 131072 pages, LIFO batch:31
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 14 16:40:30 14 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: IRQ14 used by override.
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: IRQ15 used by override.
Dec 14 16:40:30 14 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 14 16:40:30 14 kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Dec 14 16:40:30 14 kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcffb0000-0xcffbdfff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcffbe000-0xcffeffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xcfff0000-0xcfffffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd0000000-0xfebfffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfeefffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffefffff]
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfff00000-0xffffffff]
Dec 14 16:40:30 14 kernel: [    0.000000] e820: [mem 0xd0000000-0xfebfffff] available for PCI devices
Dec 14 16:40:30 14 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 14 16:40:30 14 kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Dec 14 16:40:30 14 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Dec 14 16:40:30 14 kernel: [    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88011fc00000 s97304 r8192 d29672 u524288
Dec 14 16:40:30 14 kernel: [    0.000000] pcpu-alloc: s97304 r8192 d29672 u524288 alloc=1*2097152
Dec 14 16:40:30 14 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Dec 14 16:40:30 14 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 967482
Dec 14 16:40:30 14 kernel: [    0.000000] Policy zone: Normal
Dec 14 16:40:30 14 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz root=UUID=107bf235-82e7-4095-8e55-397abe9ab3b3 ro splash quiet
Dec 14 16:40:30 14 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 14 16:40:30 14 kernel: [    0.000000] AGP: Checking aperture...
Dec 14 16:40:30 14 kernel: [    0.000000] AGP: No AGP bridge found
Dec 14 16:40:30 14 kernel: [    0.000000] AGP: Node 0: aperture [bus addr 0xcee000000-0xcefffffff] (32MB)
Dec 14 16:40:30 14 kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Dec 14 16:40:30 14 kernel: [    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
Dec 14 16:40:30 14 kernel: [    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
Dec 14 16:40:30 14 kernel: [    0.000000] AGP: This costs you 64MB of RAM
Dec 14 16:40:30 14 kernel: [    0.000000] AGP: Mapping aperture over RAM [mem 0xc4000000-0xc7ffffff] (65536KB)
Dec 14 16:40:30 14 kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
Dec 14 16:40:30 14 kernel: [    0.000000] Memory: 3685640K/3931448K available (8191K kernel code, 1251K rwdata, 3852K rodata, 1464K init, 1300K bss, 245808K reserved, 0K cma-reserved)
Dec 14 16:40:30 14 kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec 14 16:40:30 14 kernel: [    0.000000] Hierarchical RCU implementation.
Dec 14 16:40:30 14 kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Dec 14 16:40:30 14 kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Dec 14 16:40:30 14 kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
Dec 14 16:40:30 14 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:456 16
Dec 14 16:40:30 14 kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Dec 14 16:40:30 14 kernel: [    0.000000] Console: colour dummy device 80x25
Dec 14 16:40:30 14 kernel: [    0.000000] console [tty0] enabled
Dec 14 16:40:30 14 kernel: [    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 76450417870 ns
Dec 14 16:40:30 14 kernel: [    0.000000] hpet clockevent registered
Dec 14 16:40:30 14 kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Dec 14 16:40:30 14 kernel: [    0.000000] tsc: Detected 3013.595 MHz processor
Dec 14 16:40:30 14 kernel: [    0.000028] Calibrating delay loop (skipped), value calculated using timer frequency.. 6027.19 BogoMIPS (lpj=12054380)
Dec 14 16:40:30 14 kernel: [    0.000031] pid_max: default: 32768 minimum: 301
Dec 14 16:40:30 14 kernel: [    0.000037] ACPI: Core revision 20150818
Dec 14 16:40:30 14 kernel: [    0.002286] ACPI: 2 ACPI AML tables successfully acquired and loaded
Dec 14 16:40:30 14 kernel: [    0.002306] Security Framework initialized
Dec 14 16:40:30 14 kernel: [    0.002308] Yama: becoming mindful.
Dec 14 16:40:30 14 kernel: [    0.002320] AppArmor: AppArmor initialized
Dec 14 16:40:30 14 kernel: [    0.002570] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec 14 16:40:30 14 kernel: [    0.003650] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 14 16:40:30 14 kernel: [    0.004171] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Dec 14 16:40:30 14 kernel: [    0.004177] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Dec 14 16:40:30 14 kernel: [    0.004384] Initializing cgroup subsys io
Dec 14 16:40:30 14 kernel: [    0.004390] Initializing cgroup subsys memory
Dec 14 16:40:30 14 kernel: [    0.004398] Initializing cgroup subsys devices
Dec 14 16:40:30 14 kernel: [    0.004401] Initializing cgroup subsys freezer
Dec 14 16:40:30 14 kernel: [    0.004404] Initializing cgroup subsys net_cls
Dec 14 16:40:30 14 kernel: [    0.004406] Initializing cgroup subsys perf_event
Dec 14 16:40:30 14 kernel: [    0.004408] Initializing cgroup subsys net_prio
Dec 14 16:40:30 14 kernel: [    0.004411] Initializing cgroup subsys hugetlb
Dec 14 16:40:30 14 kernel: [    0.004414] Initializing cgroup subsys pids
Dec 14 16:40:30 14 kernel: [    0.004432] CPU: Physical Processor ID: 0
Dec 14 16:40:30 14 kernel: [    0.004433] CPU: Processor Core ID: 0
Dec 14 16:40:30 14 kernel: [    0.004435] mce: CPU supports 6 MCE banks
Dec 14 16:40:30 14 kernel: [    0.004440] LVT offset 0 assigned for vector 0xf9
Dec 14 16:40:30 14 kernel: [    0.004444] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Dec 14 16:40:30 14 kernel: [    0.004446] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64, 1GB 0
Dec 14 16:40:30 14 kernel: [    0.004656] Freeing SMP alternatives memory: 28K (ffffffff820a8000 - ffffffff820af000)
Dec 14 16:40:30 14 kernel: [    0.006106] ftrace: allocating 31335 entries in 123 pages
Dec 14 16:40:30 14 kernel: [    0.018431] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 14 16:40:30 14 kernel: [    0.165906] smpboot: CPU0: AMD Athlon(tm) II X2 250 Processor (family: 0x10, model: 0x6, stepping: 0x2)
Dec 14 16:40:30 14 kernel: [    0.165930] Performance Events: AMD PMU driver.
Dec 14 16:40:30 14 kernel: [    0.165934] ... version:                0
Dec 14 16:40:30 14 kernel: [    0.165935] ... bit width:              48
Dec 14 16:40:30 14 kernel: [    0.165936] ... generic registers:      4
Dec 14 16:40:30 14 kernel: [    0.165937] ... value mask:             0000ffffffffffff
Dec 14 16:40:30 14 kernel: [    0.165938] ... max period:             00007fffffffffff
Dec 14 16:40:30 14 kernel: [    0.165938] ... fixed-purpose events:   0
Dec 14 16:40:30 14 kernel: [    0.165939] ... event mask:             000000000000000f
Dec 14 16:40:30 14 kernel: [    0.166546] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Dec 14 16:40:30 14 kernel: [    0.166615] x86: Booting SMP configuration:
Dec 14 16:40:30 14 kernel: [    0.166616] .... node  #0, CPUs:      #1
Dec 14 16:40:30 14 kernel: [    0.179599] x86: Booted up 1 node, 2 CPUs
Dec 14 16:40:30 14 kernel: [    0.179600] smpboot: Total of 2 processors activated (12054.38 BogoMIPS)
Dec 14 16:40:30 14 kernel: [    0.180207] devtmpfs: initialized
Dec 14 16:40:30 14 kernel: [    0.183505] evm: security.selinux
Dec 14 16:40:30 14 kernel: [    0.183506] evm: security.SMACK64
Dec 14 16:40:30 14 kernel: [    0.183507] evm: security.SMACK64EXEC
Dec 14 16:40:30 14 kernel: [    0.183508] evm: security.SMACK64TRANSMUTE
Dec 14 16:40:30 14 kernel: [    0.183509] evm: security.SMACK64MMAP
Dec 14 16:40:30 14 kernel: [    0.183510] evm: security.ima
Dec 14 16:40:30 14 kernel: [    0.183511] evm: security.capability
Dec 14 16:40:30 14 kernel: [    0.183603] PM: Registering ACPI NVS region [mem 0xcffbe000-0xcffeffff] (204800 bytes)
Dec 14 16:40:30 14 kernel: [    0.183668] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Dec 14 16:40:30 14 kernel: [    0.183738] pinctrl core: initialized pinctrl subsystem
Dec 14 16:40:30 14 kernel: [    0.183844] RTC time: 16:40:17, date: 12/14/15
Dec 14 16:40:30 14 kernel: [    0.183952] NET: Registered protocol family 16
Dec 14 16:40:30 14 kernel: [    0.193955] cpuidle: using governor ladder
Dec 14 16:40:30 14 kernel: [    0.205962] cpuidle: using governor menu
Dec 14 16:40:30 14 kernel: [    0.205972] PCCT header not found.
Dec 14 16:40:30 14 kernel: [    0.205977] node 0 link 0: io port [1000, ffffff]
Dec 14 16:40:30 14 kernel: [    0.205980] TOM: 00000000e0000000 aka 3584M
Dec 14 16:40:30 14 kernel: [    0.205982] Fam 10h mmconf [mem 0xfc000000-0xfdffffff]
Dec 14 16:40:30 14 kernel: [    0.205984] node 0 link 0: mmio [fc000000, fdffffff] ==> none
Dec 14 16:40:30 14 kernel: [    0.205986] node 0 link 0: mmio [e0000000, fbffffff]
Dec 14 16:40:30 14 kernel: [    0.205987] node 0 link 0: mmio [fe000000, fe0bffff]
Dec 14 16:40:30 14 kernel: [    0.205989] node 0 link 0: mmio [a0000, bffff]
Dec 14 16:40:30 14 kernel: [    0.205990] TOM2: 0000000120000000 aka 4608M
Dec 14 16:40:30 14 kernel: [    0.205992] bus: [bus 00-07] on node 0 link 0
Dec 14 16:40:30 14 kernel: [    0.205993] bus: 00 [io  0x0000-0xffff]
Dec 14 16:40:30 14 kernel: [    0.205994] bus: 00 [mem 0xe0000000-0xfbffffff]
Dec 14 16:40:30 14 kernel: [    0.205995] bus: 00 [mem 0xfe000000-0xffffffff]
Dec 14 16:40:30 14 kernel: [    0.205996] bus: 00 [mem 0x000a0000-0x000bffff]
Dec 14 16:40:30 14 kernel: [    0.205997] bus: 00 [mem 0x120000000-0xfcffffffff]
Dec 14 16:40:30 14 kernel: [    0.206090] ACPI: bus type PCI registered
Dec 14 16:40:30 14 kernel: [    0.206092] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Dec 14 16:40:30 14 kernel: [    0.206175] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
Dec 14 16:40:30 14 kernel: [    0.206177] PCI: not using MMCONFIG
Dec 14 16:40:30 14 kernel: [    0.206178] PCI: Using configuration type 1 for base access
Dec 14 16:40:30 14 kernel: [    0.206179] PCI: Using configuration type 1 for extended access
Dec 14 16:40:30 14 kernel: [    0.206344] mtrr: your CPUs had inconsistent variable MTRR settings
Dec 14 16:40:30 14 kernel: [    0.206345] mtrr: probably your BIOS does not setup all CPUs.
Dec 14 16:40:30 14 kernel: [    0.206346] mtrr: corrected configuration.
Dec 14 16:40:30 14 kernel: [    0.218437] ACPI: Added _OSI(Module Device)
Dec 14 16:40:30 14 kernel: [    0.218441] ACPI: Added _OSI(Processor Device)
Dec 14 16:40:30 14 kernel: [    0.218442] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 14 16:40:30 14 kernel: [    0.218443] ACPI: Added _OSI(Processor Aggregator Device)
Dec 14 16:40:30 14 kernel: [    0.219525] ACPI: Executed 1 blocks of module-level executable AML code
Dec 14 16:40:30 14 kernel: [    0.220613] ACPI: Interpreter enabled
Dec 14 16:40:30 14 kernel: [    0.220621] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150818/hwxface-580)
Dec 14 16:40:30 14 kernel: [    0.220632] ACPI: (supports S0 S1 S3 S4 S5)
Dec 14 16:40:30 14 kernel: [    0.220633] ACPI: Using IOAPIC for interrupt routing
Dec 14 16:40:30 14 kernel: [    0.220660] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
Dec 14 16:40:30 14 kernel: [    0.221228] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
Dec 14 16:40:30 14 kernel: [    0.221235] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 14 16:40:30 14 kernel: [    0.224585] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 14 16:40:30 14 kernel: [    0.224590] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Dec 14 16:40:30 14 kernel: [    0.224697] acpi PNP0A03:00: _OSC: platform does not support [PCIeHotplug PME PCIeCapability]
Dec 14 16:40:30 14 kernel: [    0.224747] acpi PNP0A03:00: _OSC: not requesting control; platform does not support [PCIeCapability]
Dec 14 16:40:30 14 kernel: [    0.224750] acpi PNP0A03:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
Dec 14 16:40:30 14 kernel: [    0.224751] acpi PNP0A03:00: _OSC: platform willing to grant [AER]
Dec 14 16:40:30 14 kernel: [    0.224753] acpi PNP0A03:00: _OSC failed (AE_SUPPORT); disabling ASPM
Dec 14 16:40:30 14 kernel: [    0.224813] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1f] only partially covers this bridge
Dec 14 16:40:30 14 kernel: [    0.224906] PCI host bridge to bus 0000:00
Dec 14 16:40:30 14 kernel: [    0.224908] pci_bus 0000:00: root bus resource [bus 00-ff]
Dec 14 16:40:30 14 kernel: [    0.224910] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Dec 14 16:40:30 14 kernel: [    0.224912] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Dec 14 16:40:30 14 kernel: [    0.224914] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Dec 14 16:40:30 14 kernel: [    0.224916] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
Dec 14 16:40:30 14 kernel: [    0.224917] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfbffffff window]
Dec 14 16:40:30 14 kernel: [    0.224919] pci_bus 0000:00: root bus resource [mem 0xfe000000-0xfebfffff window]
Dec 14 16:40:30 14 kernel: [    0.224935] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
Dec 14 16:40:30 14 kernel: [    0.225117] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
Dec 14 16:40:30 14 kernel: [    0.225125] pci 0000:00:01.0: reg 0x10: [io  0x4f00-0x4fff]
Dec 14 16:40:30 14 kernel: [    0.225195] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
Dec 14 16:40:30 14 kernel: [    0.225208] pci 0000:00:01.1: reg 0x10: [io  0x4900-0x493f]
Dec 14 16:40:30 14 kernel: [    0.225221] pci 0000:00:01.1: reg 0x20: [io  0x4d00-0x4d3f]
Dec 14 16:40:30 14 kernel: [    0.225226] pci 0000:00:01.1: reg 0x24: [io  0x4e00-0x4e3f]
Dec 14 16:40:30 14 kernel: [    0.225243] pci 0000:00:01.1: PME# supported from D3hot D3cold
Dec 14 16:40:30 14 kernel: [    0.225269] pci 0000:00:01.1: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.225301] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
Dec 14 16:40:30 14 kernel: [    0.225368] pci 0000:00:02.0: [10de:03f1] type 00 class 0x0c0310
Dec 14 16:40:30 14 kernel: [    0.225378] pci 0000:00:02.0: reg 0x10: [mem 0xfbfff000-0xfbffffff]
Dec 14 16:40:30 14 kernel: [    0.225405] pci 0000:00:02.0: supports D1 D2
Dec 14 16:40:30 14 kernel: [    0.225407] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 16:40:30 14 kernel: [    0.225429] pci 0000:00:02.0: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.225464] pci 0000:00:02.1: [10de:03f2] type 00 class 0x0c0320
Dec 14 16:40:30 14 kernel: [    0.225476] pci 0000:00:02.1: reg 0x10: [mem 0xfbffec00-0xfbffecff]
Dec 14 16:40:30 14 kernel: [    0.225505] pci 0000:00:02.1: supports D1 D2
Dec 14 16:40:30 14 kernel: [    0.225507] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 16:40:30 14 kernel: [    0.225529] pci 0000:00:02.1: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.225567] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
Dec 14 16:40:30 14 kernel: [    0.225610] pci 0000:00:04.0: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.225643] pci 0000:00:05.0: [10de:03f0] type 00 class 0x040300
Dec 14 16:40:30 14 kernel: [    0.225656] pci 0000:00:05.0: reg 0x10: [mem 0xfbff8000-0xfbffbfff]
Dec 14 16:40:30 14 kernel: [    0.225685] pci 0000:00:05.0: PME# supported from D3hot D3cold
Dec 14 16:40:30 14 kernel: [    0.225707] pci 0000:00:05.0: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.225747] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
Dec 14 16:40:30 14 kernel: [    0.225758] pci 0000:00:07.0: reg 0x10: [mem 0xfbffd000-0xfbffdfff]
Dec 14 16:40:30 14 kernel: [    0.225762] pci 0000:00:07.0: reg 0x14: [io  0xe480-0xe487]
Dec 14 16:40:30 14 kernel: [    0.225783] pci 0000:00:07.0: supports D1 D2
Dec 14 16:40:30 14 kernel: [    0.225784] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 16:40:30 14 kernel: [    0.225809] pci 0000:00:07.0: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.225840] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
Dec 14 16:40:30 14 kernel: [    0.225850] pci 0000:00:08.0: reg 0x10: [io  0xe400-0xe407]
Dec 14 16:40:30 14 kernel: [    0.225853] pci 0000:00:08.0: reg 0x14: [io  0xe080-0xe083]
Dec 14 16:40:30 14 kernel: [    0.225857] pci 0000:00:08.0: reg 0x18: [io  0xe000-0xe007]
Dec 14 16:40:30 14 kernel: [    0.225860] pci 0000:00:08.0: reg 0x1c: [io  0xdc00-0xdc03]
Dec 14 16:40:30 14 kernel: [    0.225864] pci 0000:00:08.0: reg 0x20: [io  0xd880-0xd88f]
Dec 14 16:40:30 14 kernel: [    0.225867] pci 0000:00:08.0: reg 0x24: [mem 0xfbffc000-0xfbffcfff]
Dec 14 16:40:30 14 kernel: [    0.225922] pci 0000:00:08.1: [10de:03f6] type 00 class 0x010185
Dec 14 16:40:30 14 kernel: [    0.225932] pci 0000:00:08.1: reg 0x10: [io  0xd800-0xd807]
Dec 14 16:40:30 14 kernel: [    0.225935] pci 0000:00:08.1: reg 0x14: [io  0xd480-0xd483]
Dec 14 16:40:30 14 kernel: [    0.225939] pci 0000:00:08.1: reg 0x18: [io  0xd400-0xd407]
Dec 14 16:40:30 14 kernel: [    0.225946] pci 0000:00:08.1: reg 0x1c: [io  0xd080-0xd083]
Dec 14 16:40:30 14 kernel: [    0.225949] pci 0000:00:08.1: reg 0x20: [io  0xd000-0xd00f]
Dec 14 16:40:30 14 kernel: [    0.225953] pci 0000:00:08.1: reg 0x24: [mem 0xfbff7000-0xfbff7fff]
Dec 14 16:40:30 14 kernel: [    0.226014] pci 0000:00:09.0: [10de:03e8] type 01 class 0x060400
Dec 14 16:40:30 14 kernel: [    0.226036] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 16:40:30 14 kernel: [    0.226059] pci 0000:00:09.0: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.226092] pci 0000:00:0b.0: [10de:03e9] type 01 class 0x060400
Dec 14 16:40:30 14 kernel: [    0.226113] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 16:40:30 14 kernel: [    0.226135] pci 0000:00:0b.0: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.226169] pci 0000:00:0c.0: [10de:03e9] type 01 class 0x060400
Dec 14 16:40:30 14 kernel: [    0.226189] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 14 16:40:30 14 kernel: [    0.226211] pci 0000:00:0c.0: System wakeup disabled by ACPI
Dec 14 16:40:30 14 kernel: [    0.226244] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
Dec 14 16:40:30 14 kernel: [    0.226251] pci 0000:00:0d.0: reg 0x10: [mem 0xfa000000-0xfaffffff]
Dec 14 16:40:30 14 kernel: [    0.226256] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
Dec 14 16:40:30 14 kernel: [    0.226260] pci 0000:00:0d.0: reg 0x1c: [mem 0xf9000000-0xf9ffffff 64bit]
Dec 14 16:40:30 14 kernel: [    0.226265] pci 0000:00:0d.0: reg 0x30: [mem 0xfbfc0000-0xfbfdffff pref]
Dec 14 16:40:30 14 kernel: [    0.226324] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
Dec 14 16:40:30 14 kernel: [    0.226375] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
Dec 14 16:40:30 14 kernel: [    0.226422] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
Dec 14 16:40:30 14 kernel: [    0.226470] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
Dec 14 16:40:30 14 kernel: [    0.226519] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
Dec 14 16:40:30 14 kernel: [    0.226620] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
Dec 14 16:40:30 14 kernel: [    0.226625] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
Dec 14 16:40:30 14 kernel: [    0.226626] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
Dec 14 16:40:30 14 kernel: [    0.226628] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
Dec 14 16:40:30 14 kernel: [    0.226630] pci 0000:00:04.0:   bridge window [mem 0x000d0000-0x000dffff window] (subtractive decode)
Dec 14 16:40:30 14 kernel: [    0.226632] pci 0000:00:04.0:   bridge window [mem 0xe0000000-0xfbffffff window] (subtractive decode)
Dec 14 16:40:30 14 kernel: [    0.226633] pci 0000:00:04.0:   bridge window [mem 0xfe000000-0xfebfffff window] (subtractive decode)
Dec 14 16:40:30 14 kernel: [    0.226658] pci 0000:00:09.0: PCI bridge to [bus 02]
Dec 14 16:40:30 14 kernel: [    0.226685] pci 0000:00:0b.0: PCI bridge to [bus 03]
Dec 14 16:40:30 14 kernel: [    0.226713] pci 0000:00:0c.0: PCI bridge to [bus 04]
Dec 14 16:40:30 14 kernel: [    0.226723] pci_bus 0000:00: on NUMA node 0
Dec 14 16:40:30 14 kernel: [    0.227054] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.227132] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.227209] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.227285] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.227361] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.227438] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.227514] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.227591] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.227669] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *14
Dec 14 16:40:30 14 kernel: [    0.227747] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *7
Dec 14 16:40:30 14 kernel: [    0.227825] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
Dec 14 16:40:30 14 kernel: [    0.227903] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
Dec 14 16:40:30 14 kernel: [    0.227981] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *10
Dec 14 16:40:30 14 kernel: [    0.228059] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
Dec 14 16:40:30 14 kernel: [    0.228137] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.228216] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
Dec 14 16:40:30 14 kernel: [    0.228294] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *5
Dec 14 16:40:30 14 kernel: [    0.228381] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Dec 14 16:40:30 14 kernel: [    0.228541] vgaarb: setting as boot device: PCI:0000:00:0d.0
Dec 14 16:40:30 14 kernel: [    0.228543] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
Dec 14 16:40:30 14 kernel: [    0.228544] vgaarb: loaded
Dec 14 16:40:30 14 kernel: [    0.228545] vgaarb: bridge control possible 0000:00:0d.0
Dec 14 16:40:30 14 kernel: [    0.228774] SCSI subsystem initialized
Dec 14 16:40:30 14 kernel: [    0.228837] libata version 3.00 loaded.
Dec 14 16:40:30 14 kernel: [    0.228858] ACPI: bus type USB registered
Dec 14 16:40:30 14 kernel: [    0.228873] usbcore: registered new interface driver usbfs
Dec 14 16:40:30 14 kernel: [    0.228882] usbcore: registered new interface driver hub
Dec 14 16:40:30 14 kernel: [    0.228894] usbcore: registered new device driver usb
Dec 14 16:40:30 14 kernel: [    0.229038] PCI: Using ACPI for IRQ routing
Dec 14 16:40:30 14 kernel: [    0.229668] PCI: pci_cache_line_size set to 64 bytes
Dec 14 16:40:30 14 kernel: [    0.229693] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Dec 14 16:40:30 14 kernel: [    0.229695] e820: reserve RAM buffer [mem 0xcffb0000-0xcfffffff]
Dec 14 16:40:30 14 kernel: [    0.229797] NetLabel: Initializing
Dec 14 16:40:30 14 kernel: [    0.229798] NetLabel:  domain hash size = 128
Dec 14 16:40:30 14 kernel: [    0.229799] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 14 16:40:30 14 kernel: [    0.229811] NetLabel:  unlabeled traffic allowed by default
Dec 14 16:40:30 14 kernel: [    0.229909] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Dec 14 16:40:30 14 kernel: [    0.229914] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Dec 14 16:40:30 14 kernel: [    0.229917] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Dec 14 16:40:30 14 kernel: [    0.232054] clocksource: Switched to clocksource hpet
Dec 14 16:40:30 14 kernel: [    0.237976] AppArmor: AppArmor Filesystem Enabled
Dec 14 16:40:30 14 kernel: [    0.238051] pnp: PnP ACPI init
Dec 14 16:40:30 14 kernel: [    0.238140] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 14 16:40:30 14 kernel: [    0.238258] system 00:01: [io  0x0a00-0x0adf] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238261] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 16:40:30 14 kernel: [    0.238531] system 00:02: [io  0x04d0-0x04d1] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238533] system 00:02: [io  0x0800-0x080f] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238535] system 00:02: [io  0x4000-0x407f] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238537] system 00:02: [io  0x4080-0x40ff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238539] system 00:02: [io  0x4400-0x447f] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238541] system 00:02: [io  0x4480-0x44ff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238542] system 00:02: [io  0x4800-0x487f] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238544] system 00:02: [io  0x4880-0x48ff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238546] system 00:02: [io  0x4c00-0x4c7f] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238548] system 00:02: [io  0x4c80-0x4cff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238550] system 00:02: [mem 0x000d0000-0x000d3fff window] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238552] system 00:02: [mem 0x000d4000-0x000d7fff window] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238554] system 00:02: [mem 0x000de000-0x000dffff window] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238556] system 00:02: [mem 0xfec80000-0x1fd93ffff] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238558] system 00:02: [mem 0xfefe0000-0xfefe01ff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238560] system 00:02: [mem 0xfefe1000-0xfefe1fff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238562] system 00:02: [mem 0xfee01000-0xfeefffff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238564] system 00:02: [mem 0xffb80000-0xffffffff] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238567] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 16:40:30 14 kernel: [    0.238662] system 00:03: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238665] system 00:03: [mem 0xfee00000-0xfee00fff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238667] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 16:40:30 14 kernel: [    0.238720] system 00:04: [mem 0xfc000000-0xfdffffff] has been reserved
Dec 14 16:40:30 14 kernel: [    0.238722] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 14 16:40:30 14 kernel: [    0.238839] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238842] system 00:05: [mem 0x000c0000-0x000cffff] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238844] system 00:05: [mem 0x000e0000-0x000fffff] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238846] system 00:05: [mem 0x00100000-0xdfffffff] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238847] system 00:05: [mem 0xfec00000-0xffffffff] could not be reserved
Dec 14 16:40:30 14 kernel: [    0.238850] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 14 16:40:30 14 kernel: [    0.239059] pnp: PnP ACPI: found 6 devices
Dec 14 16:40:30 14 kernel: [    0.245494] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Dec 14 16:40:30 14 kernel: [    0.245513] pci 0000:00:04.0: PCI bridge to [bus 01]
Dec 14 16:40:30 14 kernel: [    0.245519] pci 0000:00:09.0: PCI bridge to [bus 02]
Dec 14 16:40:30 14 kernel: [    0.245523] pci 0000:00:0b.0: PCI bridge to [bus 03]
Dec 14 16:40:30 14 kernel: [    0.245526] pci 0000:00:0c.0: PCI bridge to [bus 04]
Dec 14 16:40:30 14 kernel: [    0.245531] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
Dec 14 16:40:30 14 kernel: [    0.245532] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
Dec 14 16:40:30 14 kernel: [    0.245534] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
Dec 14 16:40:30 14 kernel: [    0.245536] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
Dec 14 16:40:30 14 kernel: [    0.245538] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfbffffff window]
Dec 14 16:40:30 14 kernel: [    0.245540] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff window]
Dec 14 16:40:30 14 kernel: [    0.245542] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7 window]
Dec 14 16:40:30 14 kernel: [    0.245543] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff window]
Dec 14 16:40:30 14 kernel: [    0.245545] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff window]
Dec 14 16:40:30 14 kernel: [    0.245547] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff window]
Dec 14 16:40:30 14 kernel: [    0.245548] pci_bus 0000:01: resource 8 [mem 0xe0000000-0xfbffffff window]
Dec 14 16:40:30 14 kernel: [    0.245550] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff window]
Dec 14 16:40:30 14 kernel: [    0.245583] NET: Registered protocol family 2
Dec 14 16:40:30 14 kernel: [    0.245734] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Dec 14 16:40:30 14 kernel: [    0.245823] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Dec 14 16:40:30 14 kernel: [    0.245944] TCP: Hash tables configured (established 32768 bind 32768)
Dec 14 16:40:30 14 kernel: [    0.245982] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Dec 14 16:40:30 14 kernel: [    0.246006] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Dec 14 16:40:30 14 kernel: [    0.246084] NET: Registered protocol family 1
Dec 14 16:40:30 14 kernel: [    0.320218] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 16:40:30 14 kernel: [    0.320262] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 16:40:30 14 kernel: [    0.320305] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 16:40:30 14 kernel: [    0.320350] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 16:40:30 14 kernel: [    0.320394] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 16:40:30 14 kernel: [    0.320440] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 16:40:30 14 kernel: [    0.320488] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 16:40:30 14 kernel: [    0.320539] pci 0000:00:00.0: Found enabled HT MSI Mapping
Dec 14 16:40:30 14 kernel: [    0.320544] pci 0000:00:0d.0: Video device with shadowed ROM
Dec 14 16:40:30 14 kernel: [    0.320553] PCI: CLS 64 bytes, default 64
Dec 14 16:40:30 14 kernel: [    0.320612] Trying to unpack rootfs image as initramfs...
Dec 14 16:40:30 14 kernel: [    0.787432] Freeing initrd memory: 33476K (ffff880033e8e000 - ffff880035f3f000)
Dec 14 16:40:30 14 kernel: [    0.787785] ACPI: PCI Interrupt Link [LSMB] enabled at IRQ 23
Dec 14 16:40:30 14 kernel: [    0.787991] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
Dec 14 16:40:30 14 kernel: [    0.788175] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
Dec 14 16:40:30 14 kernel: [    0.788364] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
Dec 14 16:40:30 14 kernel: [    0.788573] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
Dec 14 16:40:30 14 kernel: [    0.788759] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
Dec 14 16:40:30 14 kernel: [    0.788943] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 21
Dec 14 16:40:30 14 kernel: [    0.789141] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 20
Dec 14 16:40:30 14 kernel: [    0.789206] PCI-DMA: Disabling AGP.
Dec 14 16:40:30 14 kernel: [    0.789273] PCI-DMA: aperture base @ c4000000 size 65536 KB
Dec 14 16:40:30 14 kernel: [    0.789274] PCI-DMA: using GART IOMMU.
Dec 14 16:40:30 14 kernel: [    0.789276] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Dec 14 16:40:30 14 kernel: [    0.791729] microcode: CPU0: patch_level=0x01000098
Dec 14 16:40:30 14 kernel: [    0.791738] microcode: CPU1: patch_level=0x01000098
Dec 14 16:40:30 14 kernel: [    0.791819] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Dec 14 16:40:30 14 kernel: [    0.791823] LVT offset 1 assigned for vector 0x400
Dec 14 16:40:30 14 kernel: [    0.791830] IBS: LVT offset 1 assigned
Dec 14 16:40:30 14 kernel: [    0.791839] perf: AMD IBS detected (0x0000001f)
Dec 14 16:40:30 14 kernel: [    0.791874] Scanning for low memory corruption every 60 seconds
Dec 14 16:40:30 14 kernel: [    0.792154] futex hash table entries: 1024 (order: 4, 65536 bytes)
Dec 14 16:40:30 14 kernel: [    0.792188] audit: initializing netlink subsys (disabled)
Dec 14 16:40:30 14 kernel: [    0.792210] audit: type=2000 audit(1450111217.684:1): initialized
Dec 14 16:40:30 14 kernel: [    0.792455] Initialise system trusted keyring
Dec 14 16:40:30 14 kernel: [    0.792541] HugeTLB registered 1 GB page size, pre-allocated 0 pages
Dec 14 16:40:30 14 kernel: [    0.792542] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 14 16:40:30 14 kernel: [    0.793944] zbud: loaded
Dec 14 16:40:30 14 kernel: [    0.794210] VFS: Disk quotas dquot_6.6.0
Dec 14 16:40:30 14 kernel: [    0.794246] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 14 16:40:30 14 kernel: [    0.794749] fuse init (API version 7.23)
Dec 14 16:40:30 14 kernel: [    0.794937] Key type big_key registered
Dec 14 16:40:30 14 kernel: [    0.795376] Key type asymmetric registered
Dec 14 16:40:30 14 kernel: [    0.795378] Asymmetric key parser 'x509' registered
Dec 14 16:40:30 14 kernel: [    0.795392] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
Dec 14 16:40:30 14 kernel: [    0.795423] io scheduler noop registered
Dec 14 16:40:30 14 kernel: [    0.795426] io scheduler deadline registered (default)
Dec 14 16:40:30 14 kernel: [    0.795455] io scheduler cfq registered
Dec 14 16:40:30 14 kernel: [    0.795683] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 14 16:40:30 14 kernel: [    0.795689] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 14 16:40:30 14 kernel: [    0.795717] vesafb: mode is 1024x768x16, linelength=2048, pages=0
Dec 14 16:40:30 14 kernel: [    0.795718] vesafb: scrolling: redraw
Dec 14 16:40:30 14 kernel: [    0.795720] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
Dec 14 16:40:30 14 kernel: [    0.795733] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90000800000, using 1536k, total 1536k
Dec 14 16:40:30 14 kernel: [    0.802481] Console: switching to colour frame buffer device 128x48
Dec 14 16:40:30 14 kernel: [    0.809146] fb0: VESA VGA frame buffer device
Dec 14 16:40:30 14 kernel: [    0.809235] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec 14 16:40:30 14 kernel: [    0.809239] ACPI: Power Button [PWRB]
Dec 14 16:40:30 14 kernel: [    0.809273] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec 14 16:40:30 14 kernel: [    0.809275] ACPI: Power Button [PWRF]
Dec 14 16:40:30 14 kernel: [    0.809430] GHES: HEST is not enabled!
Dec 14 16:40:30 14 kernel: [    0.809523] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 14 16:40:30 14 kernel: [    0.810922] Linux agpgart interface v0.103
Dec 14 16:40:30 14 kernel: [    0.813480] brd: module loaded
Dec 14 16:40:30 14 kernel: [    0.814639] loop: module loaded
Dec 14 16:40:30 14 kernel: [    0.815131] libphy: Fixed MDIO Bus: probed
Dec 14 16:40:30 14 kernel: [    0.815134] tun: Universal TUN/TAP device driver, 1.6
Dec 14 16:40:30 14 kernel: [    0.815135] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 14 16:40:30 14 kernel: [    0.815203] PPP generic driver version 2.4.2
Dec 14 16:40:30 14 kernel: [    0.815265] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 14 16:40:30 14 kernel: [    0.815269] ehci-pci: EHCI PCI platform driver
Dec 14 16:40:30 14 kernel: [    0.815340] ehci-pci 0000:00:02.1: EHCI Host Controller
Dec 14 16:40:30 14 kernel: [    0.815346] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
Dec 14 16:40:30 14 kernel: [    0.815354] ehci-pci 0000:00:02.1: debug port 1
Dec 14 16:40:30 14 kernel: [    0.815380] ehci-pci 0000:00:02.1: cache line size of 64 is not supported
Dec 14 16:40:30 14 kernel: [    0.815398] ehci-pci 0000:00:02.1: irq 21, io mem 0xfbffec00
Dec 14 16:40:30 14 kernel: [    0.824485] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
Dec 14 16:40:30 14 kernel: [    0.824544] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Dec 14 16:40:30 14 kernel: [    0.824546] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 14 16:40:30 14 kernel: [    0.824548] usb usb1: Product: EHCI Host Controller
Dec 14 16:40:30 14 kernel: [    0.824549] usb usb1: Manufacturer: Linux 4.3.0-2-generic ehci_hcd
Dec 14 16:40:30 14 kernel: [    0.824551] usb usb1: SerialNumber: 0000:00:02.1
Dec 14 16:40:30 14 kernel: [    0.824688] hub 1-0:1.0: USB hub found
Dec 14 16:40:30 14 kernel: [    0.824693] hub 1-0:1.0: 10 ports detected
Dec 14 16:40:30 14 kernel: [    0.824867] ehci-platform: EHCI generic platform driver
Dec 14 16:40:30 14 kernel: [    0.824880] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 14 16:40:30 14 kernel: [    0.824883] ohci-pci: OHCI PCI platform driver
Dec 14 16:40:30 14 kernel: [    0.824981] ohci-pci 0000:00:02.0: OHCI PCI host controller
Dec 14 16:40:30 14 kernel: [    0.824986] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
Dec 14 16:40:30 14 kernel: [    0.825015] ohci-pci 0000:00:02.0: irq 22, io mem 0xfbfff000
Dec 14 16:40:30 14 kernel: [    0.882546] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Dec 14 16:40:30 14 kernel: [    0.882550] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Dec 14 16:40:30 14 kernel: [    0.882551] usb usb2: Product: OHCI PCI host controller
Dec 14 16:40:30 14 kernel: [    0.882553] usb usb2: Manufacturer: Linux 4.3.0-2-generic ohci_hcd
Dec 14 16:40:30 14 kernel: [    0.882554] usb usb2: SerialNumber: 0000:00:02.0
Dec 14 16:40:30 14 kernel: [    0.882734] hub 2-0:1.0: USB hub found
Dec 14 16:40:30 14 kernel: [    0.882742] hub 2-0:1.0: 10 ports detected
Dec 14 16:40:30 14 kernel: [    0.882912] ohci-platform: OHCI generic platform driver
Dec 14 16:40:30 14 kernel: [    0.882925] uhci_hcd: USB Universal Host Controller Interface driver
Dec 14 16:40:30 14 kernel: [    0.882980] i8042: PNP: No PS/2 controller found. Probing ports directly.
Dec 14 16:40:30 14 kernel: [    0.885275] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 14 16:40:30 14 kernel: [    0.885286] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 14 16:40:30 14 kernel: [    0.885467] mousedev: PS/2 mouse device common for all mice
Dec 14 16:40:30 14 kernel: [    0.885626] rtc_cmos 00:00: RTC can wake from S4
Dec 14 16:40:30 14 kernel: [    0.885799] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
Dec 14 16:40:30 14 kernel: [    0.885835] rtc_cmos 00:00: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
Dec 14 16:40:30 14 kernel: [    0.885842] i2c /dev entries driver
Dec 14 16:40:30 14 kernel: [    0.885901] device-mapper: uevent: version 1.0.3
Dec 14 16:40:30 14 kernel: [    0.885986] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
Dec 14 16:40:30 14 kernel: [    0.886004] ledtrig-cpu: registered to indicate activity on CPUs
Dec 14 16:40:30 14 kernel: [    0.886348] NET: Registered protocol family 10
Dec 14 16:40:30 14 kernel: [    0.886517] NET: Registered protocol family 17
Dec 14 16:40:30 14 kernel: [    0.886528] Key type dns_resolver registered
Dec 14 16:40:30 14 kernel: [    0.886871] registered taskstats version 1
Dec 14 16:40:30 14 kernel: [    0.886882] Loading compiled-in X.509 certificates
Dec 14 16:40:30 14 kernel: [    0.887830] Loaded X.509 cert 'Build time autogenerated kernel key: 529a908f1f1fa68336efe06eb8e57dd6a88b5796'
Dec 14 16:40:30 14 kernel: [    0.887846] zswap: loaded using pool lzo/zbud
Dec 14 16:40:30 14 kernel: [    0.889735] Key type trusted registered
Dec 14 16:40:30 14 kernel: [    0.893121] Key type encrypted registered
Dec 14 16:40:30 14 kernel: [    0.893131] AppArmor: AppArmor sha1 policy hashing enabled
Dec 14 16:40:30 14 kernel: [    0.893134] ima: No TPM chip found, activating TPM-bypass!
Dec 14 16:40:30 14 kernel: [    0.893153] evm: HMAC attrs: 0x1
Dec 14 16:40:30 14 kernel: [    0.893349]   Magic number: 11:917:691
Dec 14 16:40:30 14 kernel: [    0.893456] rtc_cmos 00:00: setting system clock to 2015-12-14 16:40:18 UTC (1450111218)
Dec 14 16:40:30 14 kernel: [    0.893549] acpi-cpufreq: overriding BIOS provided _PSD data
Dec 14 16:40:30 14 kernel: [    0.893607] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 14 16:40:30 14 kernel: [    0.893608] EDD information not available.
Dec 14 16:40:30 14 kernel: [    0.893664] PM: Hibernation image not present or could not be loaded.
Dec 14 16:40:30 14 kernel: [    0.894120] Freeing unused kernel memory: 1464K (ffffffff81f3a000 - ffffffff820a8000)
Dec 14 16:40:30 14 kernel: [    0.894123] Write protecting the kernel read-only data: 14336k
Dec 14 16:40:30 14 kernel: [    0.894916] Freeing unused kernel memory: 2036K (ffff880001803000 - ffff880001a00000)
Dec 14 16:40:30 14 kernel: [    0.895037] Freeing unused kernel memory: 244K (ffff880001dc3000 - ffff880001e00000)
Dec 14 16:40:30 14 kernel: [    0.910217] random: systemd-udevd urandom read with 2 bits of entropy available
Dec 14 16:40:30 14 kernel: [    0.942289] sata_nv 0000:00:08.0: version 3.5
Dec 14 16:40:30 14 kernel: [    0.945176] scsi host0: sata_nv
Dec 14 16:40:30 14 kernel: [    0.945307] scsi host1: sata_nv
Dec 14 16:40:30 14 kernel: [    0.945349] ata1: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 22
Dec 14 16:40:30 14 kernel: [    0.945351] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 22
Dec 14 16:40:30 14 kernel: [    0.945745] scsi host2: sata_nv
Dec 14 16:40:30 14 kernel: [    0.945810] scsi host3: sata_nv
Dec 14 16:40:30 14 kernel: [    0.945844] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 21
Dec 14 16:40:30 14 kernel: [    0.945846] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 21
Dec 14 16:40:30 14 kernel: [    0.945953] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Dec 14 16:40:30 14 kernel: [    0.949123] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
Dec 14 16:40:30 14 kernel: [    1.136676] usb 1-1: new high-speed USB device number 2 using ehci-pci
Dec 14 16:40:30 14 kernel: [    1.267001] ata3: SATA link down (SStatus 0 SControl 300)
Dec 14 16:40:30 14 kernel: [    1.271376] usb 1-1: New USB device found, idVendor=04b4, idProduct=6830
Dec 14 16:40:30 14 kernel: [    1.271381] usb 1-1: New USB device strings: Mfr=56, Product=78, SerialNumber=100
Dec 14 16:40:30 14 kernel: [    1.271383] usb 1-1: Product: USB2.0 Storage Device
Dec 14 16:40:30 14 kernel: [    1.271385] usb 1-1: Manufacturer: Cypress Semiconductor
Dec 14 16:40:30 14 kernel: [    1.271386] usb 1-1: SerialNumber: DEF10A366B82
Dec 14 16:40:30 14 kernel: [    1.274676] usbcore: registered new interface driver usb-storage
Dec 14 16:40:30 14 kernel: [    1.275988] usbcore: registered new interface driver uas
Dec 14 16:40:30 14 kernel: [    1.277151] ums-cypress 1-1:1.0: USB Mass Storage device detected
Dec 14 16:40:30 14 kernel: [    1.277399] scsi host4: usb-storage 1-1:1.0
Dec 14 16:40:30 14 kernel: [    1.277493] usbcore: registered new interface driver ums-cypress
Dec 14 16:40:30 14 kernel: [    1.412878] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 14 16:40:30 14 kernel: [    1.421119] ata1.00: ATA-8: WDC WD10EZEX-00ZF5A0, 80.00A80, max UDMA/133
Dec 14 16:40:30 14 kernel: [    1.421123] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 14 16:40:30 14 kernel: [    1.429115] ata1.00: configured for UDMA/133
Dec 14 16:40:30 14 kernel: [    1.429307] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EZEX-00Z 0A80 PQ: 0 ANSI: 5
Dec 14 16:40:30 14 kernel: [    1.429544] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 14 16:40:30 14 kernel: [    1.429546] sd 0:0:0:0: [sda] 4096-byte physical blocks
Dec 14 16:40:30 14 kernel: [    1.429582] sd 0:0:0:0: [sda] Write Protect is off
Dec 14 16:40:30 14 kernel: [    1.429584] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 14 16:40:30 14 kernel: [    1.429599] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 14 16:40:30 14 kernel: [    1.429659] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 14 16:40:30 14 kernel: [    1.436874] usb 1-9: new high-speed USB device number 4 using ehci-pci
Dec 14 16:40:30 14 kernel: [    1.461196] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr e0:cb:4e:9b:e8:4d
Dec 14 16:40:30 14 kernel: [    1.461200] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
Dec 14 16:40:30 14 kernel: [    1.462218] forcedeth 0000:00:07.0 enp0s7: renamed from eth0
Dec 14 16:40:30 14 kernel: [    1.493618]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
Dec 14 16:40:30 14 kernel: [    1.494061] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 14 16:40:30 14 kernel: [    1.571321] usb 1-9: New USB device found, idVendor=058f, idProduct=6366
Dec 14 16:40:30 14 kernel: [    1.571325] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 14 16:40:30 14 kernel: [    1.571327] usb 1-9: Product: Mass Storage Device
Dec 14 16:40:30 14 kernel: [    1.571328] usb 1-9: Manufacturer: Generic
Dec 14 16:40:30 14 kernel: [    1.571330] usb 1-9: SerialNumber: 058F63666471
Dec 14 16:40:30 14 kernel: [    1.571737] usb-storage 1-9:1.0: USB Mass Storage device detected
Dec 14 16:40:30 14 kernel: [    1.571918] scsi host5: usb-storage 1-9:1.0
Dec 14 16:40:30 14 kernel: [    1.624994] usb 2-4: new low-speed USB device number 2 using ohci-pci
Dec 14 16:40:30 14 kernel: [    1.751319] ata2: SATA link down (SStatus 0 SControl 300)
Dec 14 16:40:30 14 kernel: [    1.789097] tsc: Refined TSC clocksource calibration: 3013.705 MHz
Dec 14 16:40:30 14 kernel: [    1.789102] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b70d7a0847, max_idle_ns: 440795224568 ns
Dec 14 16:40:30 14 kernel: [    1.840179] usb 2-4: New USB device found, idVendor=04fc, idProduct=05d8
Dec 14 16:40:30 14 kernel: [    1.840183] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Dec 14 16:40:30 14 kernel: [    1.840185] usb 2-4: Product: wireless combo
Dec 14 16:40:30 14 kernel: [    1.840186] usb 2-4: Manufacturer: MLK
Dec 14 16:40:30 14 kernel: [    1.858439] hidraw: raw HID events driver (C) Jiri Kosina
Dec 14 16:40:30 14 kernel: [    1.875278] usbcore: registered new interface driver usbhid
Dec 14 16:40:30 14 kernel: [    1.875281] usbhid: USB HID core driver
Dec 14 16:40:30 14 kernel: [    1.876931] input: MLK wireless combo as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/0003:04FC:05D8.0001/input/input5
Dec 14 16:40:30 14 kernel: [    1.929342] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK wireless combo] on usb-0000:00:02.0-4/input0
Dec 14 16:40:30 14 kernel: [    1.929362] sunplus 0003:04FC:05D8.0002: fixing up Sunplus Wireless Desktop report descriptor
Dec 14 16:40:30 14 kernel: [    1.930083] input: MLK wireless combo as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/0003:04FC:05D8.0002/input/input6
Dec 14 16:40:30 14 kernel: [    1.985431] sunplus 0003:04FC:05D8.0002: input,hiddev0,hidraw1: USB HID v1.00 Mouse [MLK wireless combo] on usb-0000:00:02.0-4/input1
Dec 14 16:40:30 14 kernel: [    2.071517] ata4: SATA link down (SStatus 0 SControl 300)
Dec 14 16:40:30 14 kernel: [    2.279557] scsi 4:0:0:0: Direct-Access     TOSHIBA  MK6025GAS        0000 PQ: 0 ANSI: 0
Dec 14 16:40:30 14 kernel: [    2.279888] sd 4:0:0:0: Attached scsi generic sg1 type 0
Dec 14 16:40:30 14 kernel: [    2.280387] sd 4:0:0:0: [sdb] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
Dec 14 16:40:30 14 kernel: [    2.281298] sd 4:0:0:0: [sdb] Write Protect is off
Dec 14 16:40:30 14 kernel: [    2.281303] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
Dec 14 16:40:30 14 kernel: [    2.282302] sd 4:0:0:0: [sdb] No Caching mode page found
Dec 14 16:40:30 14 kernel: [    2.282376] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Dec 14 16:40:30 14 kernel: [    2.366852]  sdb: sdb1 sdb2 < > sdb3
Dec 14 16:40:30 14 kernel: [    2.369737] sd 4:0:0:0: [sdb] Attached SCSI disk
Dec 14 16:40:30 14 kernel: [    2.570617] scsi 5:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
Dec 14 16:40:30 14 kernel: [    2.570943] sd 5:0:0:0: Attached scsi generic sg2 type 0
Dec 14 16:40:30 14 kernel: [    2.573731] sd 5:0:0:0: [sdc] Attached SCSI removable disk
Dec 14 16:40:30 14 kernel: [    2.789813] clocksource: Switched to clocksource tsc
Dec 14 16:40:30 14 kernel: [    2.988428] random: nonblocking pool is initialized
Dec 14 16:40:30 14 kernel: [    3.219415] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Dec 14 16:40:30 14 kernel: [    5.177360] lp: driver loaded but no devices found
Dec 14 16:40:30 14 kernel: [    5.188626] ppdev: user-space parallel port driver
Dec 14 16:40:30 14 kernel: [    6.002240] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Dec 14 16:40:30 14 kernel: [    6.678077] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
Dec 14 16:40:30 14 kernel: [    6.678129] i2c i2c-1: nForce2 SMBus adapter at 0x4e00
Dec 14 16:40:30 14 kernel: [    6.734734] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 14 16:40:30 14 kernel: [    6.807280] EDAC MC: Ver: 3.0.0
Dec 14 16:40:30 14 kernel: [    6.818103] [drm] Initialized drm 1.1.0 20060810
Dec 14 16:40:30 14 kernel: [    6.847577] MCE: In-kernel MCE decoding enabled.
Dec 14 16:40:30 14 kernel: [    6.881245] AMD64 EDAC driver v3.4.0
Dec 14 16:40:30 14 kernel: [    6.881277] EDAC amd64: DRAM ECC disabled.
Dec 14 16:40:30 14 kernel: [    6.881282] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Dec 14 16:40:30 14 kernel: [    6.881282]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Dec 14 16:40:30 14 kernel: [    6.881282]  (Note that use of the override may cause unknown side effects.)
Dec 14 16:40:30 14 kernel: [    7.325125] kvm: disabled by bios
Dec 14 16:40:30 14 kernel: [    7.774931] snd_hda_intel 0000:00:05.0: Disabling MSI
Dec 14 16:40:30 14 kernel: [    8.549471] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC662 rev1: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
Dec 14 16:40:30 14 kernel: [    8.549475] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Dec 14 16:40:30 14 kernel: [    8.549478] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Dec 14 16:40:30 14 kernel: [    8.549479] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Dec 14 16:40:30 14 kernel: [    8.549481] snd_hda_codec_realtek hdaudioC0D0:    inputs:
Dec 14 16:40:30 14 kernel: [    8.549482] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
Dec 14 16:40:30 14 kernel: [    8.549484] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
Dec 14 16:40:30 14 kernel: [    8.869474] Adding 2047996k swap on /dev/sda5.  Priority:-1 extents:1 across:2047996k FS
Dec 14 16:40:30 14 kernel: [    9.208730] nvidia: module license 'NVIDIA' taints kernel.
Dec 14 16:40:30 14 kernel: [    9.208734] Disabling lock debugging due to kernel taint
Dec 14 16:40:30 14 kernel: [    9.216600] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Dec 14 16:40:30 14 kernel: [    9.216883] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 16:40:30 14 kernel: [    9.217025] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 16:40:30 14 kernel: [    9.456945] audit: type=1400 audit(1450140027.054:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.456954] audit: type=1400 audit(1450140027.054:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.520910] audit: type=1400 audit(1450140027.118:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.520919] audit: type=1400 audit(1450140027.118:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.520924] audit: type=1400 audit(1450140027.118:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.520928] audit: type=1400 audit(1450140027.118:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.687923] audit: type=1400 audit(1450140027.286:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.687935] audit: type=1400 audit(1450140027.286:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.687941] audit: type=1400 audit(1450140027.286:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.687945] audit: type=1400 audit(1450140027.286:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=442 comm="apparmor_parser"
Dec 14 16:40:30 14 kernel: [    9.887660] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
Dec 14 16:40:30 14 kernel: [    9.887722] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
Dec 14 16:40:30 14 kernel: [    9.887770] input: HDA NVidia Line Out as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
Dec 14 16:40:30 14 kernel: [    9.887817] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
Dec 14 16:40:30 14 kernel: [   12.976558] usb 1-1: USB disconnect, device number 2
Dec 14 16:40:32 14 kernel: [   14.458529] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
Dec 14 16:40:32 14 kernel: [   14.459125] forcedeth 0000:00:07.0 enp0s7: MSI enabled
Dec 14 16:40:33 14 kernel: [   15.606008] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 16:40:33 14 kernel: [   15.606153] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 16:40:33 14 kernel: [   15.646510] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 16:40:33 14 kernel: [   15.646656] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 16:40:42 14 kernel: [   24.567864] forcedeth 0000:00:07.0 enp0s7: link down
Dec 14 16:40:44 14 kernel: [   26.598317] forcedeth 0000:00:07.0 enp0s7: link up
```

Xorg log file grepped:
```
[    15.416] (==) Matched nvidia as autoconfigured driver 0
[    15.416] (II) LoadModule: "nvidia"
[    15.416] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.464] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.505] (II) UnloadModule: "nvidia"
[    15.505] (II) Unloading nvidia
[    15.505] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    15.515] (==) Matched nvidia as autoconfigured driver 0
[    15.515] (II) LoadModule: "nvidia"
[    15.515] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.515] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.548] (II) UnloadModule: "nvidia"
[    15.548] (II) Unloading nvidia
[    15.549] [COLOR=#ff0000]**(EE) Failed to load module "nvidia"**[/COLOR] (module-specific error, 0)
```

kern.log grep:
```
Dec 14 14:34:32 14 kernel: [  781.365010] nvidia: module license 'NVIDIA' taints kernel.
Dec 14 14:34:32 14 kernel: [  781.373127] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Dec 14 14:34:32 14 kernel: [  781.373429] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:34:32 14 kernel: [  781.373584] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 14:34:32 14 kernel: [  781.410570] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:34:32 14 kernel: [  781.410727] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 14:35:32 14 kernel: [   10.007388] nvidia: module license 'NVIDIA' taints kernel.
Dec 14 14:35:32 14 kernel: [   10.015029] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Dec 14 14:35:32 14 kernel: [   10.015310] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:35:32 14 kernel: [   10.015452] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 14:35:38 14 kernel: [   17.213701] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:35:38 14 kernel: [   17.213846] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 14:35:38 14 kernel: [   17.253947] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 14:35:38 14 kernel: [   17.254091] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 16:40:30 14 kernel: [    9.208730] nvidia: module license 'NVIDIA' taints kernel.
Dec 14 16:40:30 14 kernel: [    9.216600] nvidia: module verification failed: signature and/or required key missing - tainting kernel
Dec 14 16:40:30 14 kernel: [    9.216883] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 16:40:30 14 kernel: [    9.217025] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 16:40:33 14 kernel: [   15.606008] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 16:40:33 14 kernel: [   15.606153] nvidia: Unknown symbol mtrr_add (err 0)
Dec 14 16:40:33 14 kernel: [   15.646510] nvidia: Unknown symbol mtrr_del (err 0)
Dec 14 16:40:33 14 kernel: [   15.646656] nvidia: Unknown symbol mtrr_add (err 0)
```

I'm not sdure about the 'tainting' I googled signature and tainting. Nothing came up.

software-properties-gtk, Additional Drivers:

$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.131-0ubuntu2
  Candidate: 304.131-0ubuntu2
  Version table:
 *** 304.131-0ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/restricted amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by VMC on 2015-12-15
Created a [bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1526564"). Very similar to these reports:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1363675](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1363675) , which was fixed for Ubuntu 14.10.
Also this report, which is reported as "new" for Ubuntu 10.10 with nothing added:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/688837](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/688837)

If anyone has this issue, please add yourself to the report, thanks.

---

### Post by SeijiSensei on 2015-12-16
You haven't told us which model NVIDIA card you have.  For my 750 GT, I needed to use "nvidia-346" rather than "nvidia-current" in 14.04.

"Tainting" the kernel means that the OS is no longer entirely open-source ("free" in GNU/GPL sense) since the driver is a proprietary binary blob.

---

### Post by VMC on 2015-12-16
It's a "GeForce 6150 SE nForce 430", which works perfectly on xubuntu 14.04, with no issues.

---

### Post by VMC on 2016-03-16
Todays (March 15th) ISO fixed the nvidia issue. I was just getting together all info on re-compiling the kernel when installing the latest ISO had the fix.

---

### Post by Kotseto on 2016-03-16
Fixed  my a$$ [IMG][IMG]http://i63.tinypic.com/2llfuqe.png[/IMG][/IMG]

I had to use sudo apt-get remove nvidia*

sudo get-apt autoremove

and reboot to  avert Black screen of death  

Using proprietary tested nvidia drvier.


Seriously if they do not fix this , I will not use Ubuntu.

I am on Sony Vaio F series and tried Noveau drivers and they also hang and freeze the Os.

Now the proprietary tested also leads to this or low graphics mode problem.

I really am sick and tired of reinstalling every time.

---

