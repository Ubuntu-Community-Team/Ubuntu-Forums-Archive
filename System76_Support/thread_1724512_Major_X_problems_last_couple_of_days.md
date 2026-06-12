---
title: "Major X problems last couple of days"
date: 2011-04-08
forum: System76 Support
---

### Post by jbraswell on 2011-04-08
Edit: system model is leo1 and I'm running 10.10

I have a Leopard Extreme with the GeForce GTS 450. It's been running fine since December or so when I got it, but suddenly, over the past few days, X has been going nuts somewhere between, say, 2 and 5 times a day. When I move or drag a window, it duplicates the window, leaving the old image in place, and very quickly the whole thing grinds to a halt. I can't just reboot the server, I have to reboot the machine to recover. 

I don't have Flash installed on the box, and I don't have any Flash plugins enabled in Firefox or Chrome.

Besides the normal Ubuntu updates, I haven't installed anything recently that has anything to do with graphics/video card, just FF 4.0, a few Python modules, and bazaar. I can't recall exactly what day is started so it's hard to correlate with a particular update.

I'm running two 24-inch Asus VE247s. I don't have any visual effects enabled at all, and I'm using the proprietary NVIDIA drivers from the repository.

The only programs in common to all of the screwups is Eclipse and vi/emacs, but I'm running those 99.0% of the time I have my computer on anyway, so it doesn't really mean much.

Here's the log from the last shutdown.

```
[  5465.191] (WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
[  5465.191] (WW) NVIDIA(0):     back to write-back cached memory.
[  5559.348] 
Backtrace:
[  5559.355] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[  5559.355] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[  5559.355] 2: /lib/libpthread.so.0 (0x7f8862ba7000+0xfb40) [0x7f8862bb6b40]
[  5559.355] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f885d51f000+0xd6694) [0x7f885d5f5694]
[  5559.355] 4: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f885d51f000+0xd87e
3) [0x7f885d5f77e3]
[  5559.355] 5: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f885d51f000+0xa5130) [0x7f885d5c4130]
[  5559.355] 6: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f885d51f000+0xa5579) [0x7f885d5c4579]
[  5559.355] Segmentation fault at address (nil)
[  5559.355] 
Caught signal 11 (Segmentation fault). Server aborting
[  5559.355] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[  5559.355] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  5559.355] 
[  5559.480] (II) Power Button: Close
[  5559.481] (II) UnloadModule: "evdev"
[  5559.680] (II) Sleep Button: Close
[  5559.681] (II) UnloadModule: "evdev"
[  5559.961] (II) DELL Dell QuietKey Keyboard: Close
[  5559.961] (II) UnloadModule: "evdev"
[  5560.084] (II) USB Optical Mouse: Close
[  5560.084] (II) UnloadModule: "evdev"
```

Any help would be greatly appreciated.  It's kind of driving me nuts.

---

### Post by jbraswell on 2011-04-08
Oh, scratch that. I had to restart right after that last post, and nothing was running but Chrome and a few terminals.

For what it's worth, here's the entire log from that run:

```
[    23.937] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    23.937] X Protocol Version 11, Revision 0
[    23.937] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    23.937] Current Operating System: Linux lx4head-08 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64
[    23.937] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro quiet splash
[    23.937] Build Date: 09 January 2011  12:14:27PM
[    23.937] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    23.937] Current version of pixman: 0.18.4
[    23.937] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    23.937] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.937] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr  8 10:56:40 2011
[    23.937] (==) Using config file: "/etc/X11/xorg.conf"
[    23.937] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.937] (==) ServerLayout "Layout0"
[    23.937] (**) |-->Screen "Screen0" (0)
[    23.937] (**) |   |-->Monitor "Monitor0"
[    23.937] (**) |   |-->Device "Device0"
[    23.937] (**) |-->Input Device "Keyboard0"
[    23.937] (**) |-->Input Device "Mouse0"
[    23.937] (**) Option "Xinerama" "0"
[    23.937] (==) Automatically adding devices
[    23.937] (==) Automatically enabling devices
[    23.937] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.937] 	Entry deleted from font path.
[    23.937] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    23.937] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.937] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    23.937] (WW) Disabling Keyboard0
[    23.937] (WW) Disabling Mouse0
[    23.937] (II) Loader magic: 0x7d17a0
[    23.937] (II) Module ABI versions:
[    23.937] 	X.Org ANSI C Emulation: 0.4
[    23.937] 	X.Org Video Driver: 8.0
[    23.937] 	X.Org XInput driver : 11.0
[    23.937] 	X.Org Server Extension : 4.0
[    23.938] (--) PCI:*(0:2:0:0) 10de:0dc4:3842:1450 rev 161, Mem @ 0xd0000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    23.938] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.938] (II) LoadModule: "extmod"
[    23.938] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.939] (II) Module extmod: vendor="X.Org Foundation"
[    23.939] 	compiled for 1.9.0, module version = 1.0.0
[    23.939] 	Module class: X.Org Server Extension
[    23.939] 	ABI class: X.Org Server Extension, version 4.0
[    23.939] (II) Loading extension MIT-SCREEN-SAVER
[    23.939] (II) Loading extension XFree86-VidModeExtension
[    23.939] (II) Loading extension XFree86-DGA
[    23.939] (II) Loading extension DPMS
[    23.939] (II) Loading extension XVideo
[    23.939] (II) Loading extension XVideo-MotionCompensation
[    23.939] (II) Loading extension X-Resource
[    23.939] (II) LoadModule: "dbe"
[    23.939] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.939] (II) Module dbe: vendor="X.Org Foundation"
[    23.939] 	compiled for 1.9.0, module version = 1.0.0
[    23.939] 	Module class: X.Org Server Extension
[    23.939] 	ABI class: X.Org Server Extension, version 4.0
[    23.939] (II) Loading extension DOUBLE-BUFFER
[    23.939] (II) LoadModule: "glx"
[    23.939] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    23.944] (II) Module glx: vendor="NVIDIA Corporation"
[    23.944] 	compiled for 4.0.2, module version = 1.0.0
[    23.944] 	Module class: X.Org Server Extension
[    23.944] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[    23.944] (II) Loading extension GLX
[    23.944] (II) LoadModule: "record"
[    23.944] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.944] (II) Module record: vendor="X.Org Foundation"
[    23.944] 	compiled for 1.9.0, module version = 1.13.0
[    23.944] 	Module class: X.Org Server Extension
[    23.944] 	ABI class: X.Org Server Extension, version 4.0
[    23.944] (II) Loading extension RECORD
[    23.944] (II) LoadModule: "dri"
[    23.944] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.944] (II) Module dri: vendor="X.Org Foundation"
[    23.944] 	compiled for 1.9.0, module version = 1.0.0
[    23.944] 	ABI class: X.Org Server Extension, version 4.0
[    23.944] (II) Loading extension XFree86-DRI
[    23.944] (II) LoadModule: "dri2"
[    23.944] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.944] (II) Module dri2: vendor="X.Org Foundation"
[    23.944] 	compiled for 1.9.0, module version = 1.2.0
[    23.944] 	ABI class: X.Org Server Extension, version 4.0
[    23.944] (II) Loading extension DRI2
[    23.944] (II) LoadModule: "nvidia"
[    23.944] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    23.945] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.945] 	compiled for 4.0.2, module version = 1.0.0
[    23.945] 	Module class: X.Org Video Driver
[    23.945] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[    23.945] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    23.945] (++) using VT number 7

[    23.945] (II) Loading sub module "fb"
[    23.945] (II) LoadModule: "fb"
[    23.945] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.945] (II) Module fb: vendor="X.Org Foundation"
[    23.945] 	compiled for 1.9.0, module version = 1.0.0
[    23.945] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.945] (II) Loading sub module "wfb"
[    23.945] (II) LoadModule: "wfb"
[    23.945] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.945] (II) Module wfb: vendor="X.Org Foundation"
[    23.945] 	compiled for 1.9.0, module version = 1.0.0
[    23.945] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.945] (II) Loading sub module "ramdac"
[    23.945] (II) LoadModule: "ramdac"
[    23.945] (II) Module "ramdac" already built-in
[    23.945] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    23.945] (==) NVIDIA(0): RGB weight 888
[    23.945] (==) NVIDIA(0): Default visual is TrueColor
[    23.945] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.945] (**) NVIDIA(0): Option "TwinView" "1"
[    23.945] (**) NVIDIA(0): Option "MetaModes" "DFP-0: 1920x1080 +0+1080, DFP-2: 1920x1080 +0+0"
[    23.945] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
[    23.946] (**) NVIDIA(0): Enabling RENDER acceleration
[    23.946] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    23.946] (II) NVIDIA(0):     enabled.
[    24.612] (II) NVIDIA(0): NVIDIA GPU GeForce GTS 450 (GF106) at PCI:2:0:0 (GPU-0)
[    24.612] (--) NVIDIA(0): Memory: 1048576 kBytes
[    24.612] (--) NVIDIA(0): VideoBIOS: 70.06.13.00.52
[    24.612] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    24.612] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    24.612] (--) NVIDIA(0): Connected display device(s) on GeForce GTS 450 at PCI:2:0:0
[    24.612] (--) NVIDIA(0):     Ancor Communications Inc VE247 (DFP-0)
[    24.612] (--) NVIDIA(0):     Ancor Communications Inc VE247 (DFP-2)
[    24.612] (--) NVIDIA(0): Ancor Communications Inc VE247 (DFP-0): 330.0 MHz maximum
[    24.612] (--) NVIDIA(0):     pixel clock
[    24.612] (--) NVIDIA(0): Ancor Communications Inc VE247 (DFP-0): Internal Dual Link
[    24.612] (--) NVIDIA(0):     TMDS
[    24.612] (--) NVIDIA(0): Ancor Communications Inc VE247 (DFP-2): 330.0 MHz maximum
[    24.612] (--) NVIDIA(0):     pixel clock
[    24.612] (--) NVIDIA(0): Ancor Communications Inc VE247 (DFP-2): Internal Dual Link
[    24.612] (--) NVIDIA(0):     TMDS
[    24.617] (**) NVIDIA(0): TwinView enabled
[    24.617] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-2
[    24.654] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-2
[    24.654] (II) NVIDIA(0): Validated modes:
[    24.654] (II) NVIDIA(0):     "DFP-0:1920x1080+0+1080,DFP-2:1920x1080+0+0"
[    24.654] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 2160
[    24.683] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[    24.683] (--) NVIDIA(0):     option
[    24.683] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    24.683] (--) Depth 24 pixmap format is 32 bpp
[    24.683] (II) NVIDIA: Using 3069.00 MB of virtual memory for indirect memory
[    24.683] (II) NVIDIA:     access.
[    24.685] (II) NVIDIA(0): Initialized GPU GART.
[    24.694] (II) NVIDIA(0): Setting mode "DFP-0:1920x1080+0+1080,DFP-2:1920x1080+0+0"
[    24.777] (II) Loading extension NV-GLX
[    24.877] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    24.878] (==) NVIDIA(0): Disabling shared memory pixmaps
[    24.878] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    24.878] (==) NVIDIA(0): Backing store disabled
[    24.878] (==) NVIDIA(0): Silken mouse enabled
[    24.898] (**) NVIDIA(0): DPMS enabled
[    24.898] (II) Loading extension NV-CONTROL
[    24.899] (II) Loading extension XINERAMA
[    24.899] (II) Loading sub module "dri2"
[    24.899] (II) LoadModule: "dri2"
[    24.899] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.899] (II) NVIDIA(0): [DRI2] Setup complete
[    24.899] (==) RandR enabled
[    24.899] (II) Initializing built-in extension Generic Event Extension
[    24.899] (II) Initializing built-in extension SHAPE
[    24.899] (II) Initializing built-in extension MIT-SHM
[    24.899] (II) Initializing built-in extension XInputExtension
[    24.899] (II) Initializing built-in extension XTEST
[    24.899] (II) Initializing built-in extension BIG-REQUESTS
[    24.899] (II) Initializing built-in extension SYNC
[    24.899] (II) Initializing built-in extension XKEYBOARD
[    24.899] (II) Initializing built-in extension XC-MISC
[    24.899] (II) Initializing built-in extension SECURITY
[    24.899] (II) Initializing built-in extension XINERAMA
[    24.899] (II) Initializing built-in extension XFIXES
[    24.899] (II) Initializing built-in extension RENDER
[    24.899] (II) Initializing built-in extension RANDR
[    24.899] (II) Initializing built-in extension COMPOSITE
[    24.899] (II) Initializing built-in extension DAMAGE
[    24.899] (II) Initializing built-in extension GESTURE
[    24.900] (II) Initializing extension GLX
[    24.918] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.922] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.922] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.922] (II) LoadModule: "evdev"
[    24.922] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.922] (II) Module evdev: vendor="X.Org Foundation"
[    24.922] 	compiled for 1.9.0, module version = 2.3.2
[    24.922] 	Module class: X.Org XInput Driver
[    24.922] 	ABI class: X.Org XInput driver, version 11.0
[    24.922] (**) Power Button: always reports core events
[    24.922] (**) Power Button: Device: "/dev/input/event1"
[    25.020] (II) Power Button: Found keys
[    25.020] (II) Power Button: Configuring as keyboard
[    25.020] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.020] (**) Option "xkb_rules" "evdev"
[    25.020] (**) Option "xkb_model" "microsoft7000"
[    25.020] (**) Option "xkb_layout" "us"
[    25.021] (II) XKB: reuse xkmfile /var/lib/xkb/server-82B6862F3FA11126BCFEE3AA1C76805C0E7833B5.xkm
[    25.022] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    25.022] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.022] (**) Sleep Button: always reports core events
[    25.022] (**) Sleep Button: Device: "/dev/input/event0"
[    25.101] (II) Sleep Button: Found keys
[    25.101] (II) Sleep Button: Configuring as keyboard
[    25.101] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    25.101] (**) Option "xkb_rules" "evdev"
[    25.101] (**) Option "xkb_model" "microsoft7000"
[    25.101] (**) Option "xkb_layout" "us"
[    25.102] (II) config/udev: Adding input device DELL Dell QuietKey Keyboard (/dev/input/event2)
[    25.102] (**) DELL Dell QuietKey Keyboard: Applying InputClass "evdev keyboard catchall"
[    25.102] (**) DELL Dell QuietKey Keyboard: always reports core events
[    25.102] (**) DELL Dell QuietKey Keyboard: Device: "/dev/input/event2"
[    25.181] (II) DELL Dell QuietKey Keyboard: Found keys
[    25.191] (II) DELL Dell QuietKey Keyboard: Configuring as keyboard
[    25.191] (II) XINPUT: Adding extended input device "DELL Dell QuietKey Keyboard" (type: KEYBOARD)
[    25.191] (**) Option "xkb_rules" "evdev"
[    25.191] (**) Option "xkb_model" "microsoft7000"
[    25.191] (**) Option "xkb_layout" "us"
[    25.193] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    25.193] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    25.193] (**) USB Optical Mouse: always reports core events
[    25.193] (**) USB Optical Mouse: Device: "/dev/input/event3"
[    25.301] (II) USB Optical Mouse: Found 3 mouse buttons
[    25.301] (II) USB Optical Mouse: Found scroll wheel(s)
[    25.301] (II) USB Optical Mouse: Found relative axes
[    25.301] (II) USB Optical Mouse: Found x and y relative axes
[    25.301] (II) USB Optical Mouse: Configuring as mouse
[    25.301] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    25.301] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.301] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    25.301] (II) USB Optical Mouse: initialized for relative axes.
[    25.301] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    25.301] (II) No input driver/identifier specified (ignoring)
[  1938.864] (WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
[  1938.864] (WW) NVIDIA(0):     back to write-back cached memory.
[  1961.061] (II) Power Button: Close
[  1961.061] (II) UnloadModule: "evdev"
[  1961.141] (II) Sleep Button: Close
[  1961.141] (II) UnloadModule: "evdev"
[  1961.271] (II) DELL Dell QuietKey Keyboard: Close
[  1961.271] (II) UnloadModule: "evdev"
[  1961.341] (II) USB Optical Mouse: Close
[  1961.341] (II) UnloadModule: "evdev"
[  1961.914]  ddxSigGiveUp: Closing log
```

---

### Post by jbraswell on 2011-04-08
Here's my update history for Monday and Tuesday. (I'm pretty sure this started on Monday.)


```
Start-Date: 2011-04-04  08:47:00
Upgrade: libswscale0:amd64 (0.6.1-5ubuntu1~ppa1~maverick1, 0.6.1-5ubuntu2~ppa1~maverick1), emacs:amd64 (23.1+1-4ubuntu7.1+maverick1, 23.1+1-4ubuntu7.2+maverick1), libavutil50:amd64 (0.6.1-5ubuntu1~ppa1~maverick1, 0.6.1-5ubuntu2~ppa1~maverick1), emacs23-bin-common:amd64 (
23.1+1-4ubuntu7.1+maverick1, 23.1+1-4ubuntu7.2+maverick1), python-ubuntuone-client:amd64 (1.4.5-0ubuntu1, 1.4.6-0ubuntu2), ubuntuone-client:amd64 (1.4.5-0ubuntu1, 1.4.6-0ubuntu2), libdbus-1-3:amd64 (1.4.0-0ubuntu1.1, 1.4.0-0ubuntu1.2), libavfilter1:amd64 (0.6.1-5ubuntu1~
ppa1~maverick1, 0.6.1-5ubuntu2~ppa1~maverick1), transmission-gtk:amd64 (2.04-0ubuntu2, 2.05-0ubuntu0.2), libavdevice52:amd64 (0.6.1-5ubuntu1~ppa1~maverick1, 0.6.1-5ubuntu2~ppa1~maverick1), software-center:amd64 (3.0.7, 3.0.8), firefox-branding:amd64 (3.6.16~hg20110308r34
972+nobinonly-0ubuntu1~umd1~maverick, 3.6.16+build1+nobinonly-0ubuntu0.10.10.1), libavcodec52:amd64 (0.6.1-5ubuntu1~ppa1~maverick1, 0.6.1-5ubuntu2~ppa1~maverick1), transmission-common:amd64 (2.04-0ubuntu2, 2.05-0ubuntu0.2), linux-firmware:amd64 (1.38.4, 1.38.5), dbus:amd
64 (1.4.0-0ubuntu1.1, 1.4.0-0ubuntu1.2), firefox:amd64 (3.6.16~hg20110308r34972+nobinonly-0ubuntu1~umd1~maverick, 3.6.16+build1+nobinonly-0ubuntu0.10.10.1), libsyncdaemon-1.0-1:amd64 (1.4.5-0ubuntu1, 1.4.6-0ubuntu2), xulrunner-1.9.2:amd64 (1.9.2.15+build1+nobinonly-0ubun
tu0.10.10.1, 1.9.2.16+build1+nobinonly-0ubuntu0.10.10.1), ffmpeg:amd64 (0.6.1-5ubuntu1~ppa1~maverick1, 0.6.1-5ubuntu2~ppa1~maverick1), libpostproc51:amd64 (0.6.1-5ubuntu1~ppa1~maverick1, 0.6.1-5ubuntu2~ppa1~maverick1), libavformat52:amd64 (0.6.1-5ubuntu1~ppa1~maverick1, 
0.6.1-5ubuntu2~ppa1~maverick1), gnome-screensaver:amd64 (2.30.0-1ubuntu1, 2.30.0-1ubuntu1.1), emacs23:amd64 (23.1+1-4ubuntu7.1+maverick1, 23.1+1-4ubuntu7.2+maverick1), handbrake-gtk:amd64 (svn3870ppa1~maverick1, svn3899ppa1~maverick1), ubuntuone-client-gnome:amd64 (1.4.5
-0ubuntu1, 1.4.6-0ubuntu2), dbus-x11:amd64 (1.4.0-0ubuntu1.1, 1.4.0-0ubuntu1.2), emacs23-common:amd64 (23.1+1-4ubuntu7.1+maverick1, 23.1+1-4ubuntu7.2+maverick1), firefox-gnome-support:amd64 (3.6.16~hg20110308r34972+nobinonly-0ubuntu1~umd1~maverick, 3.6.16+build1+nobinonl
y-0ubuntu0.10.10.1)
End-Date: 2011-04-04  08:48:07

Start-Date: 2011-04-04  08:51:39
Install: libbluray0:amd64 (0.2~git20110213.20739ed-0ubuntu3~ppa1~maverick1)
Upgrade: libsmbclient:amd64 (3.5.4~dfsg-1ubuntu8.3, 3.5.4~dfsg-1ubuntu8.4), libldap-2.4-2:amd64 (2.4.23-0ubuntu3.4, 2.4.23-0ubuntu3.5), smbclient:amd64 (3.5.4~dfsg-1ubuntu8.3, 3.5.4~dfsg-1ubuntu8.4), libqt4-test:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-script:a
md64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-designer:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-network:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-dbus:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), mplayer:amd64 (1.0~rc4.dfsg1-1ubuntu1~ppa1~maverick1,
 1.0~rc4.dfsg1-1ubuntu3~ppa1~maverick1), libwbclient0:amd64 (3.5.4~dfsg-1ubuntu8.3, 3.5.4~dfsg-1ubuntu8.4), subversion:amd64 (1.6.12dfsg-1ubuntu1.1, 1.6.12dfsg-1ubuntu1.2), mencoder:amd64 (1.0~rc4.dfsg1-1ubuntu1~ppa1~maverick1, 1.0~rc4.dfsg1-1ubuntu3~ppa1~maverick1), lib
qt4-xmlpatterns:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libsvn1:amd64 (1.6.12dfsg-1ubuntu1.1, 1.6.12dfsg-1ubuntu1.2), samba-common:amd64 (3.5.4~dfsg-1ubuntu8.3, 3.5.4~dfsg-1ubuntu8.4), libvlc5:amd64 (1.1.7-3ubuntu1~ppa1~maverick1, 1.1.8-1ubuntu1~ppa1~maverick1), libq
t4-help:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), vlc-nox:amd64 (1.1.7-3ubuntu1~ppa1~maverick1, 1.1.8-1ubuntu1~ppa1~maverick1), gdm:amd64 (2.30.5-0ubuntu4, 2.30.5-0ubuntu4.1), libqtcore4:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), vlc-plugin-notify:amd64 (1.1.7-3ubuntu
1~ppa1~maverick1, 1.1.8-1ubuntu1~ppa1~maverick1), libqt4-sql:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-svg:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libservlet2.5-java:amd64 (6.0.28-2ubuntu1.1, 6.0.28-2ubuntu1.2), liborc-0.4-0:amd64 (0.4.6-1, 0.4.11-2~ppa1~mav
erick1), libqt4-xml:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libschroedinger-1.0-0:amd64 (1.0.9.really-1build1, 1.0.10-2~ppa1~maverick1), vlc:amd64 (1.1.7-3ubuntu1~ppa1~maverick1, 1.1.8-1ubuntu1~ppa1~maverick1), libqtgui4:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), vl
c-data:amd64 (1.1.7-3ubuntu1~ppa1~maverick1, 1.1.8-1ubuntu1~ppa1~maverick1), samba-common-bin:amd64 (3.5.4~dfsg-1ubuntu8.3, 3.5.4~dfsg-1ubuntu8.4), libqt4-sql-mysql:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3), libqt4-scripttools:amd64 (4.7.0-0ubuntu4.2, 4.7.0-0ubuntu4.3),
 libvlccore4:amd64 (1.1.7-3ubuntu1~ppa1~maverick1, 1.1.8-1ubuntu1~ppa1~maverick1), vlc-plugin-pulse:amd64 (1.1.7-3ubuntu1~ppa1~maverick1, 1.1.8-1ubuntu1~ppa1~maverick1)
End-Date: 2011-04-04  08:52:40

Start-Date: 2011-04-04  10:53:50
Commandline: apt-get remove firefox
Remove: firefox-branding:amd64 (3.6.16+build1+nobinonly-0ubuntu0.10.10.1), firefox:amd64 (3.6.16+build1+nobinonly-0ubuntu0.10.10.1), firefox-gnome-support:amd64 (3.6.16+build1+nobinonly-0ubuntu0.10.10.1)
End-Date: 2011-04-04  10:53:54

Start-Date: 2011-04-04  10:54:03
Commandline: apt-get remove firefox-4.0
Remove: firefox-4.0-globalmenu:amd64 (4.0~b13~hg20110321r63449+nobinonly-0ubuntu1~umd1~maverick), firefox-4.0-core:amd64 (4.0~b13~hg20110321r63449+nobinonly-0ubuntu1~umd1~maverick), firefox-4.0:amd64 (4.0~b13~hg20110321r63449+nobinonly-0ubuntu1~umd1~maverick)
End-Date: 2011-04-04  10:54:06

Start-Date: 2011-04-04  10:55:32
Commandline: apt-get upgrade
Upgrade: ubufox:amd64 (0.9~rc2-0ubuntu5.1, 0.9~rc2-0ubuntu11~mfs~maverick1), xul-ext-ubufox:amd64 (0.9~rc2-0ubuntu5.1, 0.9~rc2-0ubuntu11~mfs~maverick1), language-pack-ja-base:amd64 (10.10+20100930, 10.10+20110315+mfs1), language-pack-en-base:amd64 (10.10+20100930, 10.10+20110315+mfs1), language-pack-en:amd64 (10.10+20101204, 10.10+20110315+mfs1), language-pack-ja:amd64 (10.10+20101204, 10.10+20110315+mfs1)
End-Date: 2011-04-04  10:55:54

Start-Date: 2011-04-04  10:56:55
Commandline: apt-get install firefox
Install: firefox-globalmenu:amd64 (4.0+nobinonly-0ubuntu1~mfs~maverick1, automatic), firefox:amd64 (4.0+nobinonly-0ubuntu1~mfs~maverick1)
End-Date: 2011-04-04  10:57:01

Start-Date: 2011-04-04  11:33:23
Commandline: apt-get install pychecker
Install: pychecker:amd64 (0.8.18-4)
End-Date: 2011-04-04  11:33:28

Start-Date: 2011-04-05  08:24:27
Upgrade: tzdata-java:amd64 (2011d-0ubuntu0.10.10, 2011e-0ubuntu0.10.10), python-gtkspell:amd64 (2.25.3-5ubuntu2, 2.25.3-5ubuntu2.1), libtiff4:amd64 (3.9.4-2ubuntu0.2, 3.9.4-2ubuntu0.3), tzdata:amd64 (2011d-0ubuntu0.10.10, 2011e-0ubuntu0.10.10), handbrake-gtk:amd64 (svn3899ppa1~maverick1, svn3901ppa1~maverick1), nautilus-dropbox:amd64 (0.6.7, 0.6.7)
End-Date: 2011-04-05  08:24:46

Start-Date: 2011-04-05  14:20:48
Commandline: apt-get remove pylint
Remove: pylint:amd64 (0.21.1-1)
End-Date: 2011-04-05  14:20:54


Start-Date: 2011-04-05  15:17:10
Commandline: /usr/sbin/synaptic
Install: bzrtools:amd64 (2.2.0-2, automatic), python-paramiko:amd64 (1.7.6-2, automatic), bzr:amd64 (2.2.1-0ubuntu1), bzr-doc:amd64 (2.2.1-0ubuntu1), python-configobj:amd64 (4.7.2+ds-1, automatic)
End-Date: 2011-04-05  15:17:21

Start-Date: 2011-04-05  17:42:11
Commandline: /usr/sbin/synaptic
Remove: bzrtools:amd64 (2.2.0-2)
Purge: bzr:amd64 (2.2.1-0ubuntu1), bzr-doc:amd64 (2.2.1-0ubuntu1)
End-Date: 2011-04-05  17:42:16
```

---

### Post by jbraswell on 2011-04-08
This was created after my last post.

---

### Post by jbraswell on 2011-04-08
So, I ran a few hours without this happening. I was running Eclipse and vlc pretty much the whole time. Then, I opened Chrome, and it happened soon thereafter.

Next, I installed the Midori browser from the Ubuntu software center since it appeared to be rather lightweight. I ran it, and it instantly crashed X.

Thus, it seems that most any browser is causing it.  However, I've now been using Eclipse's internal browser (a stripped down Chrome) for a while now with no problems.

In short, it *looks* like some plugin (or something used by that plugin) in most browsers (including default Midori) is the culprit.

---

### Post by jbraswell on 2011-04-11
Just happened again with no browser running. This time I was just running Eclipse in debugger mode and a few terminals.

---

### Post by isantop on 2011-04-11
The machine should have shipped with Flash support, so that may be it. Can you try reinstalling flash?

```
sudo apt-get clean
sudo apt-get remove --purge flashplugin-*
sudo apt-get install flashplugin-installer
```

---

### Post by jbraswell on 2011-04-11
No dice.  Like I said, I've now had it happen even without using any browser, but I went ahead and installed flash as you suggested and have already had to reboot twice.

I attached the logs from the latest meltdown, which happened fast this time.

---

### Post by jbraswell on 2011-04-11
Should I try installing the latest Nvidia drivers from the Ubuntu-x-swat repository?

---

### Post by jbraswell on 2011-04-11
> **jbraswell said:**
> Should I try installing the latest Nvidia drivers from the Ubuntu-x-swat repository?

Scratch that.  I tried it and everything went to hell so I reverted. (Maybe some intermediary release would work, but the latest version supplied by that ppa was solidly rejected by the voters within my machine.)

---

### Post by isantop on 2011-04-12
Given that this is a problem that requires a reboot to recover, you might have a memory issue. Go ahead and reboot your machine. Then, immediately after the System76 splash page, press and hold Shift to access the Grub menu (This may take a couple of tries, as it's tricky to get the timing right.

Once there, select the MemTest86 option without the Serial Console, and let that run overnight to let it thoroughly check the RAM.

---

### Post by jbraswell on 2011-04-13
I get

```
error: too small lower memory (0x99100 > 0x8f000).

Press any key to continue...
```

I also tried the serial console option and got the same thing.:confused:

---

### Post by isantop on 2011-04-14
Ah. The version of MemTest86 included with Ubuntu 10.10 and earlier seems to have an issue checking system with 4GB of RAM or more. Could you create a MemTest86 LiveCD? The process is identical to creating a LiveCD for Ubuntu, and you can download the image here: [http://memtest86.org](http://memtest86.org)

---

### Post by jbraswell on 2011-04-15
Sure. I assume I can run it from a USB as well? (Don't have a CD drive.)

---

### Post by isantop on 2011-04-15
Yep, that won't be an issue. By the way, the URL in my previous post was wrong. It should be [http://memtest.org/](http://memtest.org/).

---

### Post by jbraswell on 2011-05-02
Sorry this has taken so long. The tolerability of the problem has varied with some of the latest updates so I've been living with it to some degree, and for various reasons memtest has been a pain to run.  However, just a moment ago, it completely went to crap, and it took over a minute to ssh into it and reboot. I'm running memtest right now and will post the results after a couple of passes.

Anyway, the Xorg log was slightly different this time so I thought I'd post it in the meantime.

```
[    86.912] (EE) NVIDIA(0): GpFifo object allocation failed: 0x2c
[    86.914] (WW) NVIDIA(0): Falling back to legacy push buffer interface
[    86.916] (EE) NVIDIA(0): Unsupported GPU family
[    86.916] (EE) NVIDIA(0):  *** Aborting ***
[    94.876] (EE) NVIDIA(0): Failed to allocate DMA push buffer
[    94.876] (EE) NVIDIA(0):  *** Aborting ***
[    94.876] (EE) NVIDIA(0): Error recovery failed.
[    94.876] (EE) NVIDIA(0):  *** Aborting ***
[    94.876] (EE) NVIDIA(0): Failed to restore the NVIDIA error handler!
[    94.877] 
Backtrace:
[    94.886] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[    94.886] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[    94.886] 2: /lib/libpthread.so.0 (0x7fd46f9eb000+0xfb40) [0x7fd46f9fab40]
[    94.886] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fd46a363000+0xd7ff1) [0x7fd46a43aff1]
[    94.886] 4: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fd46a363000+0x976b2) [0x7fd46a3fa6b2]
[    94.886] 5: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fd46a363000+0x3b622d) [0x7fd46a71922d]
[    94.886] 6: /usr/bin/X (0x400000+0xd57ec) [0x4d57ec]
[    94.886] 7: /usr/bin/X (0x400000+0x1254bc) [0x5254bc]
[    94.886] 8: /usr/bin/X (BlockHandler+0x50) [0x4360f0]
[    94.886] 9: /usr/bin/X (WaitForSomething+0x141) [0x464011]
[    94.886] 10: /usr/bin/X (0x400000+0x3f672) [0x43f672]
[    94.886] 11: /usr/bin/X (0x400000+0x2187b) [0x42187b]
[    94.886] 12: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fd46e956d8e]
[    94.886] 13: /usr/bin/X (0x400000+0x21409) [0x421409]
[    94.886] Segmentation fault at address 0x7fd4706b1a6c
[    94.886] 
Caught signal 11 (Segmentation fault). Server aborting
[    94.886] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[    94.886] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    94.886] 
[    94.971] (II) Power Button: Close
[    94.971] (II) UnloadModule: "evdev"
[    95.131] (II) Sleep Button: Close
[    95.131] (II) UnloadModule: "evdev"
[    95.251] (II) DELL Dell QuietKey Keyboard: Close
[    95.251] (II) UnloadModule: "evdev"
[    95.450] (II) USB Optical Mouse: Close
[    95.450] (II) UnloadModule: "evdev"

```

---

### Post by jbraswell on 2011-05-03
Well, memtest ran for 3 passes and found no errors, but I figured out the problem anyway: bad video card.

We've bought a number of these boxes recently so I swiped the video card off another box (another NVIDIA 450), and it's been running like a champ. I left it running all night with Compiz effects on, Eclipse in debug mode, VLC looping and Chrome and Firefox open each with Flash animations. Came back this morning and all was good.

---

### Post by jebus_beler on 2011-05-03
Hey not to jinx you or anything but you sure that's the problem.  There's a bug I've been having as have a few others that sounds quite similar to yours:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/600178)

Basically the nvidia drivers on natty seem to grind to a halt at some point semi-randomly.  If the problem crops up again you might want to look at that bug and this thread:

[http://ubuntuforums.org/showthread.php?p=10764312#post10764312](http://ubuntuforums.org/showthread.php?p=10764312#post10764312)

---

### Post by jbraswell on 2011-05-04
It was stable all of yesterday, so I'm hoping the problem is fixed, but thanks for the link. I'll check it out and keep it in mind if I have any more problems.

---

