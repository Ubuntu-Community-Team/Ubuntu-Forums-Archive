---
title: "usb keyboard and mouse not working for about 20 seconds"
date: 2016-03-11
forum: Ubuntu Development Version
---

### Post by terry_gardener on 2016-03-11
I have a strange problem i have recently installed ubuntu 16.04 after using manjaro for a while. 
it installed fine and things a working as they should.
however when i boot and get to the login screen the keyboard and mouse doesn't work for about 20 seconds and then work as normal afterwards. 
keyboard and mouse both work in grub and bios and windows, they also worked fine in manjaro. 

anyone have any ideas why and how to fix it. 

i am using the nvidia drivers. 
also the keyboard and mouse are wired.

---

### Post by terry_gardener on 2016-03-11
```
[    18.631] 
X.Org X Server 1.18.1
Release Date: 2016-02-08
[    18.631] X Protocol Version 11, Revision 0
[    18.631] Build Operating System: Linux 3.13.0-79-generic x86_64 Ubuntu
[    18.631] Current Operating System: Linux terry-desktop 4.4.0-12-generic #28-Ubuntu SMP Wed Mar 9 00:33:55 UTC 2016 x86_64
[    18.631] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-12-generic root=UUID=366c0034-84c5-4b8b-bb48-1dff9c0534b4 ro quiet splash
[    18.631] Build Date: 11 March 2016  07:43:21AM
[    18.631] xorg-server 2:1.18.1-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    18.631] Current version of pixman: 0.33.6
[    18.631] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.631] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.631] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 11 21:53:50 2016
[    18.649] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.657] (==) No Layout section.  Using the first Screen section.
[    18.657] (==) No screen section available. Using defaults.
[    18.657] (**) |-->Screen "Default Screen Section" (0)
[    18.657] (**) |   |-->Monitor "<default monitor>"
[    18.676] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.676] (==) Automatically adding devices
[    18.676] (==) Automatically enabling devices
[    18.676] (==) Automatically adding GPU devices
[    18.676] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    18.676] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.676] 	Entry deleted from font path.
[    18.676] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.676] 	Entry deleted from font path.
[    18.676] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.676] 	Entry deleted from font path.
[    18.676] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.676] 	Entry deleted from font path.
[    18.676] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.676] 	Entry deleted from font path.
[    18.676] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.676] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.676] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.676] (II) Loader magic: 0x55966995edc0
[    18.676] (II) Module ABI versions:
[    18.676] 	X.Org ANSI C Emulation: 0.4
[    18.676] 	X.Org Video Driver: 20.0
[    18.676] 	X.Org XInput driver : 22.1
[    18.676] 	X.Org Server Extension : 9.0
[    18.677] (++) using VT number 7

[    18.677] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    18.677] (II) xfree86: Adding drm device (/dev/dri/card0)
[    18.678] (--) PCI:*(0:1:0:0) 10de:1401:1458:36c1 rev 161, Mem @ 0xf2000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    18.692] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    18.692] (II) "glx" will be loaded by default.
[    18.692] (II) LoadModule: "glx"
[    18.692] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    19.066] (II) Module glx: vendor="NVIDIA Corporation"
[    19.066] 	compiled for 4.0.2, module version = 1.0.0
[    19.066] 	Module class: X.Org Server Extension
[    19.066] (II) NVIDIA GLX Module  361.28  Wed Feb  3 15:10:57 PST 2016
[    19.066] (==) Matched nvidia as autoconfigured driver 0
[    19.066] (==) Matched nouveau as autoconfigured driver 1
[    19.066] (==) Matched nvidia as autoconfigured driver 2
[    19.066] (==) Matched nouveau as autoconfigured driver 3
[    19.066] (==) Matched modesetting as autoconfigured driver 4
[    19.066] (==) Matched fbdev as autoconfigured driver 5
[    19.066] (==) Matched vesa as autoconfigured driver 6
[    19.066] (==) Assigned the driver to the xf86ConfigLayout
[    19.066] (II) LoadModule: "nvidia"
[    19.066] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.092] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.092] 	compiled for 4.0.2, module version = 1.0.0
[    19.092] 	Module class: X.Org Video Driver
[    19.092] (II) LoadModule: "nouveau"
[    19.102] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.123] (II) Module nouveau: vendor="X.Org Foundation"
[    19.123] 	compiled for 1.18.1, module version = 1.0.12
[    19.123] 	Module class: X.Org Video Driver
[    19.123] 	ABI class: X.Org Video Driver, version 20.0
[    19.123] (II) LoadModule: "modesetting"
[    19.123] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    19.123] (II) Module modesetting: vendor="X.Org Foundation"
[    19.123] 	compiled for 1.18.1, module version = 1.18.1
[    19.123] 	Module class: X.Org Video Driver
[    19.123] 	ABI class: X.Org Video Driver, version 20.0
[    19.123] (II) LoadModule: "fbdev"
[    19.123] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.123] (II) Module fbdev: vendor="X.Org Foundation"
[    19.123] 	compiled for 1.18.1, module version = 0.4.4
[    19.123] 	Module class: X.Org Video Driver
[    19.123] 	ABI class: X.Org Video Driver, version 20.0
[    19.123] (II) LoadModule: "vesa"
[    19.123] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.123] (II) Module vesa: vendor="X.Org Foundation"
[    19.123] 	compiled for 1.18.1, module version = 2.3.4
[    19.123] 	Module class: X.Org Video Driver
[    19.123] 	ABI class: X.Org Video Driver, version 20.0
[    19.123] (II) NVIDIA dlloader X Driver  361.28  Wed Feb  3 14:48:10 PST 2016
[    19.123] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    19.124] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    19.124] (II) NOUVEAU driver for NVIDIA chipset families :
[    19.124] 	RIVA TNT        (NV04)
[    19.124] 	RIVA TNT2       (NV05)
[    19.124] 	GeForce 256     (NV10)
[    19.124] 	GeForce 2       (NV11, NV15)
[    19.124] 	GeForce 4MX     (NV17, NV18)
[    19.124] 	GeForce 3       (NV20)
[    19.124] 	GeForce 4Ti     (NV25, NV28)
[    19.124] 	GeForce FX      (NV3x)
[    19.124] 	GeForce 6       (NV4x)
[    19.124] 	GeForce 7       (G7x)
[    19.124] 	GeForce 8       (G8x)
[    19.124] 	GeForce GTX 200 (NVA0)
[    19.124] 	GeForce GTX 400 (NVC0)
[    19.124] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    19.124] (II) FBDEV: driver for framebuffer: fbdev
[    19.124] (II) VESA: driver for VESA chipsets: vesa
[    19.131] (II) Loading sub module "fb"
[    19.131] (II) LoadModule: "fb"
[    19.131] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.144] (II) Module fb: vendor="X.Org Foundation"
[    19.144] 	compiled for 1.18.1, module version = 1.0.0
[    19.144] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.144] (II) Loading sub module "wfb"
[    19.144] (II) LoadModule: "wfb"
[    19.144] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.150] (II) Module wfb: vendor="X.Org Foundation"
[    19.150] 	compiled for 1.18.1, module version = 1.0.0
[    19.150] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.150] (II) Loading sub module "ramdac"
[    19.150] (II) LoadModule: "ramdac"
[    19.150] (II) Module "ramdac" already built-in
[    19.151] (WW) Falling back to old probe method for modesetting
[    19.151] (WW) Falling back to old probe method for fbdev
[    19.151] (II) Loading sub module "fbdevhw"
[    19.151] (II) LoadModule: "fbdevhw"
[    19.151] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.151] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.151] 	compiled for 1.18.1, module version = 0.0.2
[    19.151] 	ABI class: X.Org Video Driver, version 20.0
[    19.151] (EE) open /dev/fb0: No such file or directory
[    19.151] (WW) Falling back to old probe method for vesa
[    19.151] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    19.151] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    19.151] (==) NVIDIA(0): RGB weight 888
[    19.151] (==) NVIDIA(0): Default visual is TrueColor
[    19.151] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.152] (**) NVIDIA(0): Enabling 2D acceleration
[    19.669] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    19.669] (--) NVIDIA(0):     CRT-0
[    19.669] (--) NVIDIA(0):     DFP-0
[    19.669] (--) NVIDIA(0):     DFP-1 (boot)
[    19.669] (--) NVIDIA(0):     DFP-2
[    19.669] (--) NVIDIA(0):     DFP-3
[    19.669] (--) NVIDIA(0):     DFP-4
[    19.669] (--) NVIDIA(0):     DFP-5
[    19.669] (--) NVIDIA(0):     DFP-6
[    19.669] (--) NVIDIA(0):     DFP-7
[    19.671] (--) NVIDIA(0): CRT-0: disconnected
[    19.671] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    19.671] (--) NVIDIA(0): 
[    19.673] (--) NVIDIA(0): DFP-0: disconnected
[    19.673] (--) NVIDIA(0): DFP-0: Internal TMDS
[    19.673] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    19.673] (--) NVIDIA(0): 
[    19.703] (--) NVIDIA(0): Samsung S23B550 (DFP-1): connected
[    19.703] (--) NVIDIA(0): Samsung S23B550 (DFP-1): Internal TMDS
[    19.703] (--) NVIDIA(0): Samsung S23B550 (DFP-1): 600.0 MHz maximum pixel clock
[    19.703] (--) NVIDIA(0): 
[    19.703] (--) NVIDIA(0): DFP-2: disconnected
[    19.703] (--) NVIDIA(0): DFP-2: Internal DisplayPort
[    19.703] (--) NVIDIA(0): DFP-2: 960.0 MHz maximum pixel clock
[    19.703] (--) NVIDIA(0): 
[    19.703] (--) NVIDIA(0): DFP-3: disconnected
[    19.703] (--) NVIDIA(0): DFP-3: Internal TMDS
[    19.703] (--) NVIDIA(0): DFP-3: 330.0 MHz maximum pixel clock
[    19.703] (--) NVIDIA(0): 
[    19.703] (--) NVIDIA(0): DFP-4: disconnected
[    19.703] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    19.703] (--) NVIDIA(0): DFP-4: 960.0 MHz maximum pixel clock
[    19.703] (--) NVIDIA(0): 
[    19.703] (--) NVIDIA(0): DFP-5: disconnected
[    19.703] (--) NVIDIA(0): DFP-5: Internal TMDS
[    19.703] (--) NVIDIA(0): DFP-5: 330.0 MHz maximum pixel clock
[    19.703] (--) NVIDIA(0): 
[    19.703] (--) NVIDIA(0): DFP-6: disconnected
[    19.704] (--) NVIDIA(0): DFP-6: Internal DisplayPort
[    19.704] (--) NVIDIA(0): DFP-6: 960.0 MHz maximum pixel clock
[    19.704] (--) NVIDIA(0): 
[    19.704] (--) NVIDIA(0): DFP-7: disconnected
[    19.704] (--) NVIDIA(0): DFP-7: Internal TMDS
[    19.704] (--) NVIDIA(0): DFP-7: 330.0 MHz maximum pixel clock
[    19.704] (--) NVIDIA(0): 
[    19.704] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    19.704] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 960 (GM206-A) at PCI:1:0:0 (GPU-0)
[    19.704] (--) NVIDIA(0): Memory: 4194304 kBytes
[    19.704] (--) NVIDIA(0): VideoBIOS: 84.06.26.00.12
[    19.704] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    19.704] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    19.704] (**) NVIDIA(0):     device Samsung S23B550 (DFP-1) (Using EDID frequencies has
[    19.704] (**) NVIDIA(0):     been enabled on all display devices.)
[    19.706] (==) NVIDIA(0): 
[    19.706] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    19.706] (==) NVIDIA(0):     will be used as the requested mode.
[    19.706] (==) NVIDIA(0): 
[    19.706] (II) NVIDIA(0): Validated MetaModes:
[    19.706] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select"
[    19.706] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    19.722] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[    19.722] (--) NVIDIA(0):     option
[    19.722] (II) UnloadModule: "nouveau"
[    19.722] (II) Unloading nouveau
[    19.722] (II) UnloadModule: "modesetting"
[    19.722] (II) Unloading modesetting
[    19.722] (II) UnloadModule: "fbdev"
[    19.722] (II) Unloading fbdev
[    19.722] (II) UnloadSubModule: "fbdevhw"
[    19.722] (II) Unloading fbdevhw
[    19.722] (II) UnloadModule: "vesa"
[    19.722] (II) Unloading vesa
[    19.722] (--) Depth 24 pixmap format is 32 bpp
[    19.723] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    19.723] (II) NVIDIA:     access.
[    19.762] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
[    19.828] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.828] (==) NVIDIA(0): Backing store enabled
[    19.828] (==) NVIDIA(0): Silken mouse enabled
[    19.829] (==) NVIDIA(0): DPMS enabled
[    19.829] (II) Loading sub module "x11glvnd"
[    19.829] (II) LoadModule: "x11glvnd"
[    19.830] (WW) Warning, couldn't open module x11glvnd
[    19.830] (II) UnloadModule: "x11glvnd"
[    19.830] (II) Unloading x11glvnd
[    19.830] (II) x11glvnd Loading
[    19.830] (II) Loading sub module "dri2"
[    19.830] (II) LoadModule: "dri2"
[    19.830] (II) Module "dri2" already built-in
[    19.830] (II) NVIDIA(0): [DRI2] Setup complete
[    19.830] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    19.830] (--) RandR disabled
[    19.832] (II) SELinux: Disabled on system
[    19.832] (II) Initializing extension GLX
[    19.832] (II) Indirect GLX disabled.
[    19.919] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.925] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.925] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.925] (II) LoadModule: "evdev"
[    19.925] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.937] (II) Module evdev: vendor="X.Org Foundation"
[    19.937] 	compiled for 1.18.1, module version = 2.10.1
[    19.937] 	Module class: X.Org XInput Driver
[    19.937] 	ABI class: X.Org XInput driver, version 22.1
[    19.937] (II) Using input driver 'evdev' for 'Power Button'
[    19.937] (**) Power Button: always reports core events
[    19.937] (**) evdev: Power Button: Device: "/dev/input/event1"
[    19.937] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.937] (--) evdev: Power Button: Found keys
[    19.937] (II) evdev: Power Button: Configuring as keyboard
[    19.937] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.937] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.937] (**) Option "xkb_rules" "evdev"
[    19.937] (**) Option "xkb_model" "pc105"
[    19.937] (**) Option "xkb_layout" "gb"
[    19.938] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    19.938] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.938] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.938] (II) Using input driver 'evdev' for 'Power Button'
[    19.938] (**) Power Button: always reports core events
[    19.938] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.938] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.938] (--) evdev: Power Button: Found keys
[    19.938] (II) evdev: Power Button: Configuring as keyboard
[    19.938] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    19.938] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    19.938] (**) Option "xkb_rules" "evdev"
[    19.938] (**) Option "xkb_model" "pc105"
[    19.938] (**) Option "xkb_layout" "gb"
[    19.938] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event9)
[    19.938] (II) No input driver specified, ignoring this device.
[    19.938] (II) This device may have been added with another device file.
[    19.939] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event10)
[    19.939] (II) No input driver specified, ignoring this device.
[    19.939] (II) This device may have been added with another device file.
[    19.939] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event11)
[    19.939] (II) No input driver specified, ignoring this device.
[    19.939] (II) This device may have been added with another device file.
[    19.939] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event12)
[    19.939] (II) No input driver specified, ignoring this device.
[    19.939] (II) This device may have been added with another device file.
[    19.939] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event7)
[    19.939] (II) No input driver specified, ignoring this device.
[    19.939] (II) This device may have been added with another device file.
[    19.939] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event8)
[    19.939] (II) No input driver specified, ignoring this device.
[    19.939] (II) This device may have been added with another device file.
[    19.939] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event2)
[    19.939] (II) No input driver specified, ignoring this device.
[    19.939] (II) This device may have been added with another device file.
[    19.939] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event3)
[    19.939] (II) No input driver specified, ignoring this device.
[    19.939] (II) This device may have been added with another device file.
[    19.939] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event4)
[    19.939] (II) No input driver specified, ignoring this device.
[    19.939] (II) This device may have been added with another device file.
[    19.940] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event5)
[    19.940] (II) No input driver specified, ignoring this device.
[    19.940] (II) This device may have been added with another device file.
[    19.940] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event6)
[    19.940] (II) No input driver specified, ignoring this device.
[    19.940] (II) This device may have been added with another device file.
[    22.831] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    22.831] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    22.831] (--) NVIDIA(GPU-0): 
[    22.833] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    22.833] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    22.833] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    22.833] (--) NVIDIA(GPU-0): 
[    22.864] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): connected
[    22.864] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): Internal TMDS
[    22.864] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): 600.0 MHz maximum pixel clock
[    22.864] (--) NVIDIA(GPU-0): 
[    22.864] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    22.864] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    22.864] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[    22.864] (--) NVIDIA(GPU-0): 
[    22.864] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    22.864] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    22.864] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    22.864] (--) NVIDIA(GPU-0): 
[    22.864] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    22.864] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    22.864] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    22.864] (--) NVIDIA(GPU-0): 
[    22.864] (--) NVIDIA(GPU-0): DFP-5: disconnected
[    22.864] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[    22.864] (--) NVIDIA(GPU-0): DFP-5: 330.0 MHz maximum pixel clock
[    22.864] (--) NVIDIA(GPU-0): 
[    22.864] (--) NVIDIA(GPU-0): DFP-6: disconnected
[    22.864] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[    22.864] (--) NVIDIA(GPU-0): DFP-6: 960.0 MHz maximum pixel clock
[    22.864] (--) NVIDIA(GPU-0): 
[    22.864] (--) NVIDIA(GPU-0): DFP-7: disconnected
[    22.864] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[    22.864] (--) NVIDIA(GPU-0): DFP-7: 330.0 MHz maximum pixel clock
[    22.864] (--) NVIDIA(GPU-0): 
[    42.740] (II) config/udev: Adding input device Primax USB OPTICAL MOUSE (/dev/input/mouse0)
[    42.740] (II) No input driver specified, ignoring this device.
[    42.740] (II) This device may have been added with another device file.
[    42.752] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 3000 (/dev/input/event14)
[    42.752] (**) Microsoft Comfort Curve Keyboard 3000: Applying InputClass "evdev keyboard catchall"
[    42.752] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 3000'
[    42.752] (**) Microsoft Comfort Curve Keyboard 3000: always reports core events
[    42.752] (**) evdev: Microsoft Comfort Curve Keyboard 3000: Device: "/dev/input/event14"
[    42.752] (--) evdev: Microsoft Comfort Curve Keyboard 3000: Vendor 0x45e Product 0x7b6
[    42.752] (--) evdev: Microsoft Comfort Curve Keyboard 3000: Found 1 mouse buttons
[    42.752] (--) evdev: Microsoft Comfort Curve Keyboard 3000: Found scroll wheel(s)
[    42.752] (--) evdev: Microsoft Comfort Curve Keyboard 3000: Found relative axes
[    42.752] (II) evdev: Microsoft Comfort Curve Keyboard 3000: Forcing relative x/y axes to exist.
[    42.752] (--) evdev: Microsoft Comfort Curve Keyboard 3000: Found absolute axes
[    42.752] (II) evdev: Microsoft Comfort Curve Keyboard 3000: Forcing absolute x/y axes to exist.
[    42.752] (--) evdev: Microsoft Comfort Curve Keyboard 3000: Found keys
[    42.752] (II) evdev: Microsoft Comfort Curve Keyboard 3000: Configuring as mouse
[    42.752] (II) evdev: Microsoft Comfort Curve Keyboard 3000: Configuring as keyboard
[    42.752] (II) evdev: Microsoft Comfort Curve Keyboard 3000: Adding scrollwheel support
[    42.752] (**) evdev: Microsoft Comfort Curve Keyboard 3000: YAxisMapping: buttons 4 and 5
[    42.752] (**) evdev: Microsoft Comfort Curve Keyboard 3000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.752] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.1/0003:045E:07B6.0002/input/input17/event14"
[    42.752] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 3000" (type: KEYBOARD, id 8)
[    42.752] (**) Option "xkb_rules" "evdev"
[    42.752] (**) Option "xkb_model" "pc105"
[    42.752] (**) Option "xkb_layout" "gb"
[    42.752] (WW) Option "xkb_variant" requires a string value
[    42.752] (WW) Option "xkb_options" requires a string value
[    42.752] (II) evdev: Microsoft Comfort Curve Keyboard 3000: initialized for relative axes.
[    42.752] (WW) evdev: Microsoft Comfort Curve Keyboard 3000: ignoring absolute axes.
[    42.753] (**) Microsoft Comfort Curve Keyboard 3000: (accel) keeping acceleration scheme 1
[    42.753] (**) Microsoft Comfort Curve Keyboard 3000: (accel) acceleration profile 0
[    42.753] (**) Microsoft Comfort Curve Keyboard 3000: (accel) acceleration factor: 2.000
[    42.753] (**) Microsoft Comfort Curve Keyboard 3000: (accel) acceleration threshold: 4
[    42.753] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 3000 (/dev/input/event13)
[    42.753] (**) Microsoft Comfort Curve Keyboard 3000: Applying InputClass "evdev keyboard catchall"
[    42.753] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 3000'
[    42.753] (**) Microsoft Comfort Curve Keyboard 3000: always reports core events
[    42.753] (**) evdev: Microsoft Comfort Curve Keyboard 3000: Device: "/dev/input/event13"
[    42.753] (--) evdev: Microsoft Comfort Curve Keyboard 3000: Vendor 0x45e Product 0x7b6
[    42.753] (--) evdev: Microsoft Comfort Curve Keyboard 3000: Found keys
[    42.753] (II) evdev: Microsoft Comfort Curve Keyboard 3000: Configuring as keyboard
[    42.753] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.0/0003:045E:07B6.0001/input/input16/event13"
[    42.753] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 3000" (type: KEYBOARD, id 9)
[    42.753] (**) Option "xkb_rules" "evdev"
[    42.753] (**) Option "xkb_model" "pc105"
[    42.753] (**) Option "xkb_layout" "gb"
[    42.753] (WW) Option "xkb_variant" requires a string value
[    42.753] (WW) Option "xkb_options" requires a string value
[    42.850] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    42.850] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    42.850] (--) NVIDIA(GPU-0): 
[    42.853] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    42.853] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    42.853] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    42.853] (--) NVIDIA(GPU-0): 
[    42.890] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): connected
[    42.890] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): Internal TMDS
[    42.890] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): 600.0 MHz maximum pixel clock
[    42.890] (--) NVIDIA(GPU-0): 
[    42.890] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    42.890] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    42.890] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[    42.890] (--) NVIDIA(GPU-0): 
[    42.890] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    42.890] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    42.890] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    42.890] (--) NVIDIA(GPU-0): 
[    42.890] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    42.890] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    42.890] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    42.890] (--) NVIDIA(GPU-0): 
[    42.890] (--) NVIDIA(GPU-0): DFP-5: disconnected
[    42.890] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[    42.890] (--) NVIDIA(GPU-0): DFP-5: 330.0 MHz maximum pixel clock
[    42.890] (--) NVIDIA(GPU-0): 
[    42.890] (--) NVIDIA(GPU-0): DFP-6: disconnected
[    42.890] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[    42.890] (--) NVIDIA(GPU-0): DFP-6: 960.0 MHz maximum pixel clock
[    42.890] (--) NVIDIA(GPU-0): 
[    42.890] (--) NVIDIA(GPU-0): DFP-7: disconnected
[    42.890] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[    42.890] (--) NVIDIA(GPU-0): DFP-7: 330.0 MHz maximum pixel clock
[    42.891] (--) NVIDIA(GPU-0): 
[    42.891] (II) config/udev: Adding input device Primax USB OPTICAL MOUSE (/dev/input/event15)
[    42.891] (**) Primax USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    42.891] (II) Using input driver 'evdev' for 'Primax USB OPTICAL MOUSE'
[    42.891] (**) Primax USB OPTICAL MOUSE: always reports core events
[    42.891] (**) evdev: Primax USB OPTICAL MOUSE: Device: "/dev/input/event15"
[    42.912] (--) evdev: Primax USB OPTICAL MOUSE: Vendor 0x461 Product 0x4de3
[    42.912] (--) evdev: Primax USB OPTICAL MOUSE: Found 9 mouse buttons
[    42.912] (--) evdev: Primax USB OPTICAL MOUSE: Found scroll wheel(s)
[    42.912] (--) evdev: Primax USB OPTICAL MOUSE: Found relative axes
[    42.912] (--) evdev: Primax USB OPTICAL MOUSE: Found x and y relative axes
[    42.912] (II) evdev: Primax USB OPTICAL MOUSE: Configuring as mouse
[    42.912] (II) evdev: Primax USB OPTICAL MOUSE: Adding scrollwheel support
[    42.912] (**) evdev: Primax USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    42.912] (**) evdev: Primax USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.912] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0/0003:0461:4DE3.0003/input/input18/event15"
[    42.912] (II) XINPUT: Adding extended input device "Primax USB OPTICAL MOUSE" (type: MOUSE, id 10)
[    42.912] (II) evdev: Primax USB OPTICAL MOUSE: initialized for relative axes.
[    42.912] (**) Primax USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    42.912] (**) Primax USB OPTICAL MOUSE: (accel) acceleration profile 0
[    42.912] (**) Primax USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    42.912] (**) Primax USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    48.233] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    48.233] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    48.233] (--) NVIDIA(GPU-0): 
[    48.235] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    48.235] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    48.235] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    48.235] (--) NVIDIA(GPU-0): 
[    48.266] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): connected
[    48.266] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): Internal TMDS
[    48.266] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): 600.0 MHz maximum pixel clock
[    48.266] (--) NVIDIA(GPU-0): 
[    48.266] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    48.266] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    48.266] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[    48.266] (--) NVIDIA(GPU-0): 
[    48.266] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    48.266] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    48.266] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    48.266] (--) NVIDIA(GPU-0): 
[    48.267] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    48.267] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    48.267] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    48.267] (--) NVIDIA(GPU-0): 
[    48.267] (--) NVIDIA(GPU-0): DFP-5: disconnected
[    48.267] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[    48.267] (--) NVIDIA(GPU-0): DFP-5: 330.0 MHz maximum pixel clock
[    48.267] (--) NVIDIA(GPU-0): 
[    48.267] (--) NVIDIA(GPU-0): DFP-6: disconnected
[    48.267] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[    48.267] (--) NVIDIA(GPU-0): DFP-6: 960.0 MHz maximum pixel clock
[    48.267] (--) NVIDIA(GPU-0): 
[    48.267] (--) NVIDIA(GPU-0): DFP-7: disconnected
[    48.267] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[    48.267] (--) NVIDIA(GPU-0): DFP-7: 330.0 MHz maximum pixel clock
[    48.267] (--) NVIDIA(GPU-0): 
[    49.290] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    49.290] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    49.290] (--) NVIDIA(GPU-0): 
[    49.292] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    49.292] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    49.292] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    49.292] (--) NVIDIA(GPU-0): 
[    49.323] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): connected
[    49.323] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): Internal TMDS
[    49.323] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): 600.0 MHz maximum pixel clock
[    49.323] (--) NVIDIA(GPU-0): 
[    49.323] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    49.323] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    49.323] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[    49.323] (--) NVIDIA(GPU-0): 
[    49.323] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    49.323] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    49.323] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    49.323] (--) NVIDIA(GPU-0): 
[    49.323] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    49.323] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    49.323] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    49.323] (--) NVIDIA(GPU-0): 
[    49.323] (--) NVIDIA(GPU-0): DFP-5: disconnected
[    49.323] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[    49.323] (--) NVIDIA(GPU-0): DFP-5: 330.0 MHz maximum pixel clock
[    49.323] (--) NVIDIA(GPU-0): 
[    49.323] (--) NVIDIA(GPU-0): DFP-6: disconnected
[    49.323] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[    49.323] (--) NVIDIA(GPU-0): DFP-6: 960.0 MHz maximum pixel clock
[    49.323] (--) NVIDIA(GPU-0): 
[    49.323] (--) NVIDIA(GPU-0): DFP-7: disconnected
[    49.323] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[    49.323] (--) NVIDIA(GPU-0): DFP-7: 330.0 MHz maximum pixel clock
[    49.323] (--) NVIDIA(GPU-0): 
[    51.405] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    51.405] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    51.405] (--) NVIDIA(GPU-0): 
[    51.407] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    51.407] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    51.407] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    51.407] (--) NVIDIA(GPU-0): 
[    51.438] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): connected
[    51.438] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): Internal TMDS
[    51.438] (--) NVIDIA(GPU-0): Samsung S23B550 (DFP-1): 600.0 MHz maximum pixel clock
[    51.438] (--) NVIDIA(GPU-0): 
[    51.438] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    51.438] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    51.438] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[    51.438] (--) NVIDIA(GPU-0): 
[    51.438] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    51.438] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    51.438] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    51.438] (--) NVIDIA(GPU-0): 
[    51.438] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    51.438] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    51.438] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    51.438] (--) NVIDIA(GPU-0): 
[    51.438] (--) NVIDIA(GPU-0): DFP-5: disconnected
[    51.438] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[    51.438] (--) NVIDIA(GPU-0): DFP-5: 330.0 MHz maximum pixel clock
[    51.438] (--) NVIDIA(GPU-0): 
[    51.438] (--) NVIDIA(GPU-0): DFP-6: disconnected
[    51.438] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[    51.438] (--) NVIDIA(GPU-0): DFP-6: 960.0 MHz maximum pixel clock
[    51.438] (--) NVIDIA(GPU-0): 
[    51.438] (--) NVIDIA(GPU-0): DFP-7: disconnected
[    51.438] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[    51.438] (--) NVIDIA(GPU-0): DFP-7: 330.0 MHz maximum pixel clock
[    51.438] (--) NVIDIA(GPU-0): 
[    51.761] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    51.766] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[    52.402] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm
[    52.406] (II) XKB: reuse xkmfile /var/lib/xkb/server-5841764B120E02BC6FD78DAB262CEA727EB95BEE.xkm

```

---

### Post by ELD on 2016-03-12
I had a similar problem with my new PC as it had Windows installed first, I had to reset the motherboard by holding a button down. This actually fixed it.

---

