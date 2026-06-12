---
title: "Graphics not working on HP EliteOne 800 G2 AiO"
date: 2016-09-29
forum: Ubuntu Development Version
---

### Post by andrewp235 on 2016-09-29
I am having the same problem. Here is my Xorg.0.log (created from Ubuntu 16.10 daily, downloaded today.)
A monitor connected to the display port connector works fine. This is the touchscreen version of the display. The touchscreen seems to get the correct coordinates (as if the display was correct).

```
[    45.561] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    45.561] X Protocol Version 11, Revision 0
[    45.561] Build Operating System: Linux 3.13.0-95-generic x86_64 Ubuntu
[    45.561] Current Operating System: Linux ubuntu 4.8.0-17-generic #19-Ubuntu SMP Sun Sep 25 05:29:05 UTC 2016 x86_64
[    45.561] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --- maybe-ubiquity
[    45.561] Build Date: 07 September 2016  05:11:52AM
[    45.561] xorg-server 2:1.18.4-1ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    45.561] Current version of pixman: 0.33.6
[    45.561]  Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    45.561] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.561] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 29 14:49:16 2016
[    45.562] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.562] (==) No Layout section.  Using the first Screen section.
[    45.562] (==) No screen section available. Using defaults.
[    45.562] (**) |-->Screen "Default Screen Section" (0)
[    45.562] (**) |   |-->Monitor "<default monitor>"
[    45.563] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    45.563] (==) Automatically adding devices
[    45.563] (==) Automatically enabling devices
[    45.563] (==) Automatically adding GPU devices
[    45.563] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    45.563] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.563]  Entry deleted from font path.
[    45.563] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    45.563]  Entry deleted from font path.
[    45.563] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.563]  Entry deleted from font path.
[    45.563] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    45.563]  Entry deleted from font path.
[    45.563] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.563]  Entry deleted from font path.
[    45.563] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    45.563] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.563] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.563] (II) Loader magic: 0x55b587ee2020
[    45.563] (II) Module ABI versions:
[    45.563]  X.Org ANSI C Emulation: 0.4
[    45.563]  X.Org Video Driver: 20.0
[    45.563]  X.Org XInput driver : 22.1
[    45.563]  X.Org Server Extension : 9.0
[    45.564] (++) using VT number 7

[    45.564] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    45.565] (II) xfree86: Adding drm device (/dev/dri/card0)
[    45.568] (--) PCI:*(0:0:2:0) 8086:1912:103c:8058 rev 6, Mem @ 0xd0000000/16777216, 0xc0000000/268435456, I/O @ 0x00003000/64, BIOS @ 0x????????/131072
[    45.568] (II) LoadModule: "glx"
[    45.569] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    45.571] (II) Module glx: vendor="X.Org Foundation"
[    45.571]  compiled for 1.18.4, module version = 1.0.0
[    45.571]  ABI class: X.Org Server Extension, version 9.0
[    45.571] (==) AIGLX enabled
[    45.571] (==) Matched modesetting as autoconfigured driver 0
[    45.571] (==) Matched fbdev as autoconfigured driver 1
[    45.571] (==) Matched vesa as autoconfigured driver 2
[    45.571] (==) Assigned the driver to the xf86ConfigLayout
[    45.571] (II) LoadModule: "modesetting"
[    45.571] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    45.571] (II) Module modesetting: vendor="X.Org Foundation"
[    45.571]  compiled for 1.18.4, module version = 1.18.4
[    45.571]  Module class: X.Org Video Driver
[    45.571]  ABI class: X.Org Video Driver, version 20.0
[    45.571] (II) LoadModule: "fbdev"
[    45.572] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    45.572] (II) Module fbdev: vendor="X.Org Foundation"
[    45.572]  compiled for 1.18.1, module version = 0.4.4
[    45.572]  Module class: X.Org Video Driver
[    45.572]  ABI class: X.Org Video Driver, version 20.0
[    45.572] (II) LoadModule: "vesa"
[    45.572] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    45.572] (II) Module vesa: vendor="X.Org Foundation"
[    45.572]  compiled for 1.18.1, module version = 2.3.4
[    45.572]  Module class: X.Org Video Driver
[    45.573]  ABI class: X.Org Video Driver, version 20.0
[    45.573] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    45.573] (II) FBDEV: driver for framebuffer: fbdev
[    45.573] (II) VESA: driver for VESA chipsets: vesa
[    45.599] (II) modeset(0): using drv /dev/dri/card0
[    45.599] (WW) Falling back to old probe method for fbdev
[    45.599] (II) Loading sub module "fbdevhw"
[    45.599] (II) LoadModule: "fbdevhw"
[    45.600] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    45.600] (II) Module fbdevhw: vendor="X.Org Foundation"
[    45.600]  compiled for 1.18.4, module version = 0.0.2
[    45.600]  ABI class: X.Org Video Driver, version 20.0
[    45.600] (WW) Falling back to old probe method for vesa
[    45.601] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    45.601] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[    45.601] (==) modeset(0): RGB weight 888
[    45.601] (==) modeset(0): Default visual is TrueColor
[    45.601] (II) Loading sub module "glamoregl"
[    45.601] (II) LoadModule: "glamoregl"
[    45.601] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    45.609] (II) Module glamoregl: vendor="X.Org Foundation"
[    45.609]  compiled for 1.18.4, module version = 1.0.0
[    45.609]  ABI class: X.Org ANSI C Emulation, version 0.4
[    45.609] (II) glamor: OpenGL accelerated X.org driver based.
[    45.630] (II) glamor: EGL version 1.4 (DRI2):
[    45.633] (II) modeset(0): glamor initialized
[    45.635] (II) modeset(0): Output eDP-1 has no monitor section
[    45.638] (II) modeset(0): Output DP-1 has no monitor section
[    45.796] (II) modeset(0): Output HDMI-1 has no monitor section
[    45.799] (II) modeset(0): EDID for output eDP-1
[    45.799] (II) modeset(0): Printing probed modes for output eDP-1
[    45.799] (II) modeset(0): Modeline "1920x1080"x60.0  133.10  1920 1952 1980 2004  1080 1088 1092 1107 -hsync -vsync (66.4 kHz P)
[    45.799] (II) modeset(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[    45.799] (II) modeset(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[    45.799] (II) modeset(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[    45.799] (II) modeset(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    45.799] (II) modeset(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    45.799] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    45.799] (II) modeset(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    45.799] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    45.799] (II) modeset(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    45.799] (II) modeset(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    45.799] (II) modeset(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    45.799] (II) modeset(0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    45.800] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    45.800] (II) modeset(0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    45.800] (II) modeset(0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    45.800] (II) modeset(0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    45.800] (II) modeset(0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    45.800] (II) modeset(0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    45.800] (II) modeset(0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    45.800] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    45.800] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    45.800] (II) modeset(0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    45.800] (II) modeset(0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    45.800] (II) modeset(0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    45.800] (II) modeset(0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    45.800] (II) modeset(0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    45.800] (II) modeset(0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    45.800] (II) modeset(0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    45.800] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    45.800] (II) modeset(0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    45.800] (II) modeset(0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    45.800] (II) modeset(0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    45.800] (II) modeset(0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    45.800] (II) modeset(0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    45.800] (II) modeset(0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    45.800] (II) modeset(0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    45.802] (II) modeset(0): EDID for output DP-1
[    45.960] (II) modeset(0): EDID for output HDMI-1
[    45.960] (II) modeset(0): Output eDP-1 connected
[    45.960] (II) modeset(0): Output DP-1 disconnected
[    45.960] (II) modeset(0): Output HDMI-1 disconnected
[    45.960] (II) modeset(0): Using exact sizes for initial modes
[    45.960] (II) modeset(0): Output eDP-1 using initial mode 1920x1080 +0+0
[    45.960] (II) modeset(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    45.960] (==) modeset(0): DPI set to (96, 96)
[    45.960] (II) Loading sub module "fb"
[    45.960] (II) LoadModule: "fb"
[    45.961] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.961] (II) Module fb: vendor="X.Org Foundation"
[    45.961]  compiled for 1.18.4, module version = 1.0.0
[    45.961]  ABI class: X.Org ANSI C Emulation, version 0.4
[    45.961] (II) UnloadModule: "fbdev"
[    45.961] (II) Unloading fbdev
[    45.961] (II) UnloadSubModule: "fbdevhw"
[    45.961] (II) Unloading fbdevhw
[    45.961] (II) UnloadModule: "vesa"
[    45.961] (II) Unloading vesa
[    45.961] (==) Depth 24 pixmap format is 32 bpp
[    46.021] (==) modeset(0): Backing store enabled
[    46.021] (==) modeset(0): Silken mouse enabled
[    46.021] (II) modeset(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    46.021] (==) modeset(0): DPMS enabled
[    46.021] (II) modeset(0): [DRI2] Setup complete
[    46.021] (II) modeset(0): [DRI2]   DRI driver: i965
[    46.021] (II) modeset(0): [DRI2]   VDPAU driver: i965
[    46.066] (--) RandR disabled
[    46.069] (II) SELinux: Disabled on system
[    46.074] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    46.074] (II) AIGLX: enabled GLX_ARB_create_context
[    46.074] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    46.074] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    46.074] (II) AIGLX: enabled GLX_INTEL_swap_event
[    46.074] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    46.074] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    46.074] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    46.074] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    46.074] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    46.074] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    46.074] (II) AIGLX: Loaded and initialized i965
[    46.074] (II) GLX: Initialized DRI2 GL provider for screen 0
[    46.117] (II) modeset(0): Damage tracking initialized
[    46.117] (II) modeset(0): Setting screen physical size to 508 x 285
[    46.155] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    46.155] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    46.155] (II) LoadModule: "evdev"
[    46.155] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    46.155] (II) Module evdev: vendor="X.Org Foundation"
[    46.155]  compiled for 1.18.3, module version = 2.10.2
[    46.155]  Module class: X.Org XInput Driver
[    46.155]  ABI class: X.Org XInput driver, version 22.1
[    46.155] (II) Using input driver 'evdev' for 'Power Button'
[    46.155] (**) Power Button: always reports core events
[    46.155] (**) evdev: Power Button: Device: "/dev/input/event2"
[    46.155] (--) evdev: Power Button: Vendor 0 Product 0x1
[    46.155] (--) evdev: Power Button: Found keys
[    46.155] (II) evdev: Power Button: Configuring as keyboard
[    46.156] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    46.156] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    46.156] (**) Option "xkb_rules" "evdev"
[    46.156] (**) Option "xkb_model" "pc105"
[    46.156] (**) Option "xkb_layout" "us"
[    46.156] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    46.156] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    46.156] (II) Using input driver 'evdev' for 'Video Bus'
[    46.156] (**) Video Bus: always reports core events
[    46.156] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    46.156] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    46.156] (--) evdev: Video Bus: Found keys
[    46.156] (II) evdev: Video Bus: Configuring as keyboard
[    46.156] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6/event3"
[    46.156] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    46.156] (**) Option "xkb_rules" "evdev"
[    46.156] (**) Option "xkb_model" "pc105"
[    46.156] (**) Option "xkb_layout" "us"
[    46.156] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    46.156] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    46.156] (II) Using input driver 'evdev' for 'Power Button'
[    46.156] (**) Power Button: always reports core events
[    46.156] (**) evdev: Power Button: Device: "/dev/input/event1"
[    46.156] (--) evdev: Power Button: Vendor 0 Product 0x1
[    46.156] (--) evdev: Power Button: Found keys
[    46.156] (II) evdev: Power Button: Configuring as keyboard
[    46.156] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    46.156] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    46.156] (**) Option "xkb_rules" "evdev"
[    46.156] (**) Option "xkb_model" "pc105"
[    46.156] (**) Option "xkb_layout" "us"
[    46.157] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    46.157] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    46.157] (II) Using input driver 'evdev' for 'Sleep Button'
[    46.157] (**) Sleep Button: always reports core events
[    46.157] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    46.157] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    46.157] (--) evdev: Sleep Button: Found keys
[    46.157] (II) evdev: Sleep Button: Configuring as keyboard
[    46.157] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    46.157] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    46.157] (**) Option "xkb_rules" "evdev"
[    46.157] (**) Option "xkb_model" "pc105"
[    46.157] (**) Option "xkb_layout" "us"
[    46.157] (II) config/udev: Adding input device HP 2.0MP High Definition Webcam (/dev/input/event9)
[    46.157] (**) HP 2.0MP High Definition Webcam: Applying InputClass "evdev keyboard catchall"
[    46.157] (II) Using input driver 'evdev' for 'HP 2.0MP High Definition Webcam'
[    46.157] (**) HP 2.0MP High Definition Webcam: always reports core events
[    46.157] (**) evdev: HP 2.0MP High Definition Webcam: Device: "/dev/input/event9"
[    46.157] (--) evdev: HP 2.0MP High Definition Webcam: Vendor 0x4f2 Product 0xb508
[    46.157] (--) evdev: HP 2.0MP High Definition Webcam: Found keys
[    46.157] (II) evdev: HP 2.0MP High Definition Webcam: Configuring as keyboard
[    46.157] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-12/1-12:1.0/input/input13/event9"
[    46.157] (II) XINPUT: Adding extended input device "HP 2.0MP High Definition Webcam" (type: KEYBOARD, id 10)
[    46.157] (**) Option "xkb_rules" "evdev"
[    46.157] (**) Option "xkb_model" "pc105"
[    46.157] (**) Option "xkb_layout" "us"
[    46.158] (II) config/udev: Adding input device Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU (/dev/input/event4)
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Applying InputClass "evdev keyboard catchall"
[    46.158] (II) Using input driver 'evdev' for 'Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU'
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: always reports core events
[    46.158] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Device: "/dev/input/event4"
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Vendor 0x3f0 Product 0x1a4a
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found keys
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Configuring as keyboard
[    46.158] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:03F0:1A4A.0001/input/input7/event4"
[    46.158] (II) XINPUT: Adding extended input device "Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU" (type: KEYBOARD, id 11)
[    46.158] (**) Option "xkb_rules" "evdev"
[    46.158] (**) Option "xkb_model" "pc105"
[    46.158] (**) Option "xkb_layout" "us"
[    46.158] (II) config/udev: Adding input device Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU (/dev/input/event5)
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Applying InputClass "evdev keyboard catchall"
[    46.158] (II) Using input driver 'evdev' for 'Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU'
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: always reports core events
[    46.158] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Device: "/dev/input/event5"
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Vendor 0x3f0 Product 0x1a4a
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found 1 mouse buttons
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found scroll wheel(s)
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found relative axes
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Forcing relative x/y axes to exist.
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found absolute axes
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Forcing absolute x/y axes to exist.
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found keys
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Configuring as mouse
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Configuring as keyboard
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Adding scrollwheel support
[    46.158] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: YAxisMapping: buttons 4 and 5
[    46.158] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.158] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.1/0003:03F0:1A4A.0002/input/input8/event5"
[    46.158] (II) XINPUT: Adding extended input device "Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU" (type: KEYBOARD, id 12)
[    46.158] (**) Option "xkb_rules" "evdev"
[    46.158] (**) Option "xkb_model" "pc105"
[    46.158] (**) Option "xkb_layout" "us"
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: initialized for relative axes.
[    46.158] (WW) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: ignoring absolute axes.
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) keeping acceleration scheme 1
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration profile 0
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration factor: 2.000
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration threshold: 4
[    46.159] (II) config/udev: Adding input device Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU (/dev/input/event6)
[    46.159] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Applying InputClass "evdev pointer catchall"
[    46.159] (II) Using input driver 'evdev' for 'Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU'
[    46.159] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: always reports core events
[    46.159] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Device: "/dev/input/event6"
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Vendor 0x3f0 Product 0x1a4a
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found 3 mouse buttons
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found scroll wheel(s)
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found relative axes
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found x and y relative axes
[    46.216] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Configuring as mouse
[    46.216] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Adding scrollwheel support
[    46.216] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: YAxisMapping: buttons 4 and 5
[    46.216] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.216] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/0003:03F0:1A4A.0003/input/input9/event6"
[    46.216] (II) XINPUT: Adding extended input device "Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU" (type: MOUSE, id 13)
[    46.216] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: initialized for relative axes.
[    46.217] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) keeping acceleration scheme 1
[    46.217] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration profile 0
[    46.217] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration factor: 2.000
[    46.217] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration threshold: 4
[    46.218] (II) config/udev: Adding input device Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU (/dev/input/mouse0)
[    46.218] (II) No input driver specified, ignoring this device.
[    46.218] (II) This device may have been added with another device file.
[    46.219] (II) config/udev: Adding input device USBest Technology SiS HID Touch Controller (/dev/input/event7)
[    46.219] (**) USBest Technology SiS HID Touch Controller: Applying InputClass "evdev touchscreen catchall"
[    46.219] (II) Using input driver 'evdev' for 'USBest Technology SiS HID Touch Controller'
[    46.219] (**) USBest Technology SiS HID Touch Controller: always reports core events
[    46.219] (**) evdev: USBest Technology SiS HID Touch Controller: Device: "/dev/input/event7"
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Vendor 0x457 Product 0x111a
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute axes
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute multitouch axes
[    46.276] (II) evdev: USBest Technology SiS HID Touch Controller: No buttons found, faking one.
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Found x and y absolute axes
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute touchscreen
[    46.276] (II) evdev: USBest Technology SiS HID Touch Controller: Configuring as touchscreen
[    46.276] (**) evdev: USBest Technology SiS HID Touch Controller: YAxisMapping: buttons 4 and 5
[    46.276] (**) evdev: USBest Technology SiS HID Touch Controller: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.276] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:0457:111A.0004/input/input10/event7"
[    46.276] (II) XINPUT: Adding extended input device "USBest Technology SiS HID Touch Controller" (type: TOUCHSCREEN, id 14)
[    46.276] (II) evdev: USBest Technology SiS HID Touch Controller: initialized for absolute axes.
[    46.276] (**) USBest Technology SiS HID Touch Controller: (accel) keeping acceleration scheme 1
[    46.277] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration profile 0
[    46.277] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration factor: 2.000
[    46.277] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration threshold: 4
[    46.278] (II) config/udev: Adding input device USBest Technology SiS HID Touch Controller (/dev/input/mouse1)
[    46.278] (II) No input driver specified, ignoring this device.
[    46.278] (II) This device may have been added with another device file.
[    46.278] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    46.278] (II) No input driver specified, ignoring this device.
[    46.278] (II) This device may have been added with another device file.
[    46.279] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event11)
[    46.279] (II) No input driver specified, ignoring this device.
[    46.279] (II) This device may have been added with another device file.
[    46.280] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    46.280] (II) No input driver specified, ignoring this device.
[    46.280] (II) This device may have been added with another device file.
[    46.280] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event13)
[    46.280] (II) No input driver specified, ignoring this device.
[    46.280] (II) This device may have been added with another device file.
[    46.281] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event14)
[    46.281] (II) No input driver specified, ignoring this device.
[    46.281] (II) This device may have been added with another device file.
[    46.284] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event8)
[    46.284] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    46.284] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    46.284] (**) HP WMI hotkeys: always reports core events
[    46.284] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event8"
[    46.284] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    46.284] (--) evdev: HP WMI hotkeys: Found keys
[    46.284] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    46.284] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event8"
[    46.284] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 15)
[    46.284] (**) Option "xkb_rules" "evdev"
[    46.284] (**) Option "xkb_model" "pc105"
[    46.284] (**) Option "xkb_layout" "us"
```

---

### Post by howefield on 2016-09-29
Post moved to own thread and the "*Ubuntu Development Version*" forums from [ here]("https://ubuntuforums.org/showthread.php?t=2333464").

---

### Post by andrewp235 on 2016-09-30
I am having the same problem.
Here is my Xorg.0.log (from Ubuntu 16.10 daily, downloaded yesterday)

```
[    45.561] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    45.561] X Protocol Version 11, Revision 0
[    45.561] Build Operating System: Linux 3.13.0-95-generic x86_64 Ubuntu
[    45.561] Current Operating System: Linux ubuntu 4.8.0-17-generic #19-Ubuntu SMP Sun Sep 25 05:29:05 UTC 2016 x86_64
[    45.561] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --- maybe-ubiquity
[    45.561] Build Date: 07 September 2016  05:11:52AM
[    45.561] xorg-server 2:1.18.4-1ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    45.561] Current version of pixman: 0.33.6
[    45.561]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    45.561] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.561] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 29 14:49:16 2016
[    45.562] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.562] (==) No Layout section.  Using the first Screen section.
[    45.562] (==) No screen section available. Using defaults.
[    45.562] (**) |-->Screen "Default Screen Section" (0)
[    45.562] (**) |   |-->Monitor "<default monitor>"
[    45.563] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    45.563] (==) Automatically adding devices
[    45.563] (==) Automatically enabling devices
[    45.563] (==) Automatically adding GPU devices
[    45.563] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    45.563] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.563]     Entry deleted from font path.
[    45.563] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    45.563]     Entry deleted from font path.
[    45.563] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.563]     Entry deleted from font path.
[    45.563] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    45.563]     Entry deleted from font path.
[    45.563] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.563]     Entry deleted from font path.
[    45.563] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    45.563] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.563] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.563] (II) Loader magic: 0x55b587ee2020
[    45.563] (II) Module ABI versions:
[    45.563]     X.Org ANSI C Emulation: 0.4
[    45.563]     X.Org Video Driver: 20.0
[    45.563]     X.Org XInput driver : 22.1
[    45.563]     X.Org Server Extension : 9.0
[    45.564] (++) using VT number 7

[    45.564] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    45.565] (II) xfree86: Adding drm device (/dev/dri/card0)
[    45.568] (--) PCI:*(0:0:2:0) 8086:1912:103c:8058 rev 6, Mem @ 0xd0000000/16777216, 0xc0000000/268435456, I/O @ 0x00003000/64, BIOS @ 0x????????/131072
[    45.568] (II) LoadModule: "glx"
[    45.569] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    45.571] (II) Module glx: vendor="X.Org Foundation"
[    45.571]     compiled for 1.18.4, module version = 1.0.0
[    45.571]     ABI class: X.Org Server Extension, version 9.0
[    45.571] (==) AIGLX enabled
[    45.571] (==) Matched modesetting as autoconfigured driver 0
[    45.571] (==) Matched fbdev as autoconfigured driver 1
[    45.571] (==) Matched vesa as autoconfigured driver 2
[    45.571] (==) Assigned the driver to the xf86ConfigLayout
[    45.571] (II) LoadModule: "modesetting"
[    45.571] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    45.571] (II) Module modesetting: vendor="X.Org Foundation"
[    45.571]     compiled for 1.18.4, module version = 1.18.4
[    45.571]     Module class: X.Org Video Driver
[    45.571]     ABI class: X.Org Video Driver, version 20.0
[    45.571] (II) LoadModule: "fbdev"
[    45.572] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    45.572] (II) Module fbdev: vendor="X.Org Foundation"
[    45.572]     compiled for 1.18.1, module version = 0.4.4
[    45.572]     Module class: X.Org Video Driver
[    45.572]     ABI class: X.Org Video Driver, version 20.0
[    45.572] (II) LoadModule: "vesa"
[    45.572] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    45.572] (II) Module vesa: vendor="X.Org Foundation"
[    45.572]     compiled for 1.18.1, module version = 2.3.4
[    45.572]     Module class: X.Org Video Driver
[    45.573]     ABI class: X.Org Video Driver, version 20.0
[    45.573] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    45.573] (II) FBDEV: driver for framebuffer: fbdev
[    45.573] (II) VESA: driver for VESA chipsets: vesa
[    45.599] (II) modeset(0): using drv /dev/dri/card0
[    45.599] (WW) Falling back to old probe method for fbdev
[    45.599] (II) Loading sub module "fbdevhw"
[    45.599] (II) LoadModule: "fbdevhw"
[    45.600] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    45.600] (II) Module fbdevhw: vendor="X.Org Foundation"
[    45.600]     compiled for 1.18.4, module version = 0.0.2
[    45.600]     ABI class: X.Org Video Driver, version 20.0
[    45.600] (WW) Falling back to old probe method for vesa
[    45.601] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    45.601] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[    45.601] (==) modeset(0): RGB weight 888
[    45.601] (==) modeset(0): Default visual is TrueColor
[    45.601] (II) Loading sub module "glamoregl"
[    45.601] (II) LoadModule: "glamoregl"
[    45.601] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    45.609] (II) Module glamoregl: vendor="X.Org Foundation"
[    45.609]     compiled for 1.18.4, module version = 1.0.0
[    45.609]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.609] (II) glamor: OpenGL accelerated X.org driver based.
[    45.630] (II) glamor: EGL version 1.4 (DRI2):
[    45.633] (II) modeset(0): glamor initialized
[    45.635] (II) modeset(0): Output eDP-1 has no monitor section
[    45.638] (II) modeset(0): Output DP-1 has no monitor section
[    45.796] (II) modeset(0): Output HDMI-1 has no monitor section
[    45.799] (II) modeset(0): EDID for output eDP-1
[    45.799] (II) modeset(0): Printing probed modes for output eDP-1
[    45.799] (II) modeset(0): Modeline "1920x1080"x60.0  133.10  1920 1952 1980 2004  1080 1088 1092 1107 -hsync -vsync (66.4 kHz P)
[    45.799] (II) modeset(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[    45.799] (II) modeset(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[    45.799] (II) modeset(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[    45.799] (II) modeset(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    45.799] (II) modeset(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    45.799] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    45.799] (II) modeset(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    45.799] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    45.799] (II) modeset(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    45.799] (II) modeset(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    45.799] (II) modeset(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    45.799] (II) modeset(0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    45.800] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    45.800] (II) modeset(0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    45.800] (II) modeset(0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    45.800] (II) modeset(0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    45.800] (II) modeset(0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    45.800] (II) modeset(0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    45.800] (II) modeset(0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    45.800] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    45.800] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    45.800] (II) modeset(0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    45.800] (II) modeset(0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    45.800] (II) modeset(0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    45.800] (II) modeset(0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    45.800] (II) modeset(0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    45.800] (II) modeset(0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    45.800] (II) modeset(0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    45.800] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    45.800] (II) modeset(0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    45.800] (II) modeset(0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    45.800] (II) modeset(0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    45.800] (II) modeset(0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    45.800] (II) modeset(0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    45.800] (II) modeset(0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    45.800] (II) modeset(0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    45.802] (II) modeset(0): EDID for output DP-1
[    45.960] (II) modeset(0): EDID for output HDMI-1
[    45.960] (II) modeset(0): Output eDP-1 connected
[    45.960] (II) modeset(0): Output DP-1 disconnected
[    45.960] (II) modeset(0): Output HDMI-1 disconnected
[    45.960] (II) modeset(0): Using exact sizes for initial modes
[    45.960] (II) modeset(0): Output eDP-1 using initial mode 1920x1080 +0+0
[    45.960] (II) modeset(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    45.960] (==) modeset(0): DPI set to (96, 96)
[    45.960] (II) Loading sub module "fb"
[    45.960] (II) LoadModule: "fb"
[    45.961] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.961] (II) Module fb: vendor="X.Org Foundation"
[    45.961]     compiled for 1.18.4, module version = 1.0.0
[    45.961]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.961] (II) UnloadModule: "fbdev"
[    45.961] (II) Unloading fbdev
[    45.961] (II) UnloadSubModule: "fbdevhw"
[    45.961] (II) Unloading fbdevhw
[    45.961] (II) UnloadModule: "vesa"
[    45.961] (II) Unloading vesa
[    45.961] (==) Depth 24 pixmap format is 32 bpp
[    46.021] (==) modeset(0): Backing store enabled
[    46.021] (==) modeset(0): Silken mouse enabled
[    46.021] (II) modeset(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    46.021] (==) modeset(0): DPMS enabled
[    46.021] (II) modeset(0): [DRI2] Setup complete
[    46.021] (II) modeset(0): [DRI2]   DRI driver: i965
[    46.021] (II) modeset(0): [DRI2]   VDPAU driver: i965
[    46.066] (--) RandR disabled
[    46.069] (II) SELinux: Disabled on system
[    46.074] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    46.074] (II) AIGLX: enabled GLX_ARB_create_context
[    46.074] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    46.074] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    46.074] (II) AIGLX: enabled GLX_INTEL_swap_event
[    46.074] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    46.074] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    46.074] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    46.074] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    46.074] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    46.074] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    46.074] (II) AIGLX: Loaded and initialized i965
[    46.074] (II) GLX: Initialized DRI2 GL provider for screen 0
[    46.117] (II) modeset(0): Damage tracking initialized
[    46.117] (II) modeset(0): Setting screen physical size to 508 x 285
[    46.155] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    46.155] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    46.155] (II) LoadModule: "evdev"
[    46.155] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    46.155] (II) Module evdev: vendor="X.Org Foundation"
[    46.155]     compiled for 1.18.3, module version = 2.10.2
[    46.155]     Module class: X.Org XInput Driver
[    46.155]     ABI class: X.Org XInput driver, version 22.1
[    46.155] (II) Using input driver 'evdev' for 'Power Button'
[    46.155] (**) Power Button: always reports core events
[    46.155] (**) evdev: Power Button: Device: "/dev/input/event2"
[    46.155] (--) evdev: Power Button: Vendor 0 Product 0x1
[    46.155] (--) evdev: Power Button: Found keys
[    46.155] (II) evdev: Power Button: Configuring as keyboard
[    46.156] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    46.156] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    46.156] (**) Option "xkb_rules" "evdev"
[    46.156] (**) Option "xkb_model" "pc105"
[    46.156] (**) Option "xkb_layout" "us"
[    46.156] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    46.156] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    46.156] (II) Using input driver 'evdev' for 'Video Bus'
[    46.156] (**) Video Bus: always reports core events
[    46.156] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    46.156] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    46.156] (--) evdev: Video Bus: Found keys
[    46.156] (II) evdev: Video Bus: Configuring as keyboard
[    46.156] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6/event3"
[    46.156] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    46.156] (**) Option "xkb_rules" "evdev"
[    46.156] (**) Option "xkb_model" "pc105"
[    46.156] (**) Option "xkb_layout" "us"
[    46.156] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    46.156] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    46.156] (II) Using input driver 'evdev' for 'Power Button'
[    46.156] (**) Power Button: always reports core events
[    46.156] (**) evdev: Power Button: Device: "/dev/input/event1"
[    46.156] (--) evdev: Power Button: Vendor 0 Product 0x1
[    46.156] (--) evdev: Power Button: Found keys
[    46.156] (II) evdev: Power Button: Configuring as keyboard
[    46.156] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    46.156] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    46.156] (**) Option "xkb_rules" "evdev"
[    46.156] (**) Option "xkb_model" "pc105"
[    46.156] (**) Option "xkb_layout" "us"
[    46.157] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    46.157] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    46.157] (II) Using input driver 'evdev' for 'Sleep Button'
[    46.157] (**) Sleep Button: always reports core events
[    46.157] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    46.157] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    46.157] (--) evdev: Sleep Button: Found keys
[    46.157] (II) evdev: Sleep Button: Configuring as keyboard
[    46.157] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    46.157] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    46.157] (**) Option "xkb_rules" "evdev"
[    46.157] (**) Option "xkb_model" "pc105"
[    46.157] (**) Option "xkb_layout" "us"
[    46.157] (II) config/udev: Adding input device HP 2.0MP High Definition Webcam (/dev/input/event9)
[    46.157] (**) HP 2.0MP High Definition Webcam: Applying InputClass "evdev keyboard catchall"
[    46.157] (II) Using input driver 'evdev' for 'HP 2.0MP High Definition Webcam'
[    46.157] (**) HP 2.0MP High Definition Webcam: always reports core events
[    46.157] (**) evdev: HP 2.0MP High Definition Webcam: Device: "/dev/input/event9"
[    46.157] (--) evdev: HP 2.0MP High Definition Webcam: Vendor 0x4f2 Product 0xb508
[    46.157] (--) evdev: HP 2.0MP High Definition Webcam: Found keys
[    46.157] (II) evdev: HP 2.0MP High Definition Webcam: Configuring as keyboard
[    46.157] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-12/1-12:1.0/input/input13/event9"
[    46.157] (II) XINPUT: Adding extended input device "HP 2.0MP High Definition Webcam" (type: KEYBOARD, id 10)
[    46.157] (**) Option "xkb_rules" "evdev"
[    46.157] (**) Option "xkb_model" "pc105"
[    46.157] (**) Option "xkb_layout" "us"
[    46.158] (II) config/udev: Adding input device Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU (/dev/input/event4)
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Applying InputClass "evdev keyboard catchall"
[    46.158] (II) Using input driver 'evdev' for 'Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU'
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: always reports core events
[    46.158] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Device: "/dev/input/event4"
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Vendor 0x3f0 Product 0x1a4a
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found keys
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Configuring as keyboard
[    46.158] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:03F0:1A4A.0001/input/input7/event4"
[    46.158] (II) XINPUT: Adding extended input device "Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU" (type: KEYBOARD, id 11)
[    46.158] (**) Option "xkb_rules" "evdev"
[    46.158] (**) Option "xkb_model" "pc105"
[    46.158] (**) Option "xkb_layout" "us"
[    46.158] (II) config/udev: Adding input device Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU (/dev/input/event5)
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Applying InputClass "evdev keyboard catchall"
[    46.158] (II) Using input driver 'evdev' for 'Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU'
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: always reports core events
[    46.158] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Device: "/dev/input/event5"
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Vendor 0x3f0 Product 0x1a4a
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found 1 mouse buttons
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found scroll wheel(s)
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found relative axes
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Forcing relative x/y axes to exist.
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found absolute axes
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Forcing absolute x/y axes to exist.
[    46.158] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found keys
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Configuring as mouse
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Configuring as keyboard
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Adding scrollwheel support
[    46.158] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: YAxisMapping: buttons 4 and 5
[    46.158] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.158] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.1/0003:03F0:1A4A.0002/input/input8/event5"
[    46.158] (II) XINPUT: Adding extended input device "Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU" (type: KEYBOARD, id 12)
[    46.158] (**) Option "xkb_rules" "evdev"
[    46.158] (**) Option "xkb_model" "pc105"
[    46.158] (**) Option "xkb_layout" "us"
[    46.158] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: initialized for relative axes.
[    46.158] (WW) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: ignoring absolute axes.
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) keeping acceleration scheme 1
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration profile 0
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration factor: 2.000
[    46.158] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration threshold: 4
[    46.159] (II) config/udev: Adding input device Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU (/dev/input/event6)
[    46.159] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Applying InputClass "evdev pointer catchall"
[    46.159] (II) Using input driver 'evdev' for 'Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU'
[    46.159] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: always reports core events
[    46.159] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Device: "/dev/input/event6"
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Vendor 0x3f0 Product 0x1a4a
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found 3 mouse buttons
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found scroll wheel(s)
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found relative axes
[    46.216] (--) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Found x and y relative axes
[    46.216] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Configuring as mouse
[    46.216] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: Adding scrollwheel support
[    46.216] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: YAxisMapping: buttons 4 and 5
[    46.216] (**) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.216] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/0003:03F0:1A4A.0003/input/input9/event6"
[    46.216] (II) XINPUT: Adding extended input device "Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU" (type: MOUSE, id 13)
[    46.216] (II) evdev: Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: initialized for relative axes.
[    46.217] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) keeping acceleration scheme 1
[    46.217] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration profile 0
[    46.217] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration factor: 2.000
[    46.217] (**) Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU: (accel) acceleration threshold: 4
[    46.218] (II) config/udev: Adding input device Lite-On Technology Corp. HP Wireless Slim Keyboard - Skylab EU (/dev/input/mouse0)
[    46.218] (II) No input driver specified, ignoring this device.
[    46.218] (II) This device may have been added with another device file.
[    46.219] (II) config/udev: Adding input device USBest Technology SiS HID Touch Controller (/dev/input/event7)
[    46.219] (**) USBest Technology SiS HID Touch Controller: Applying InputClass "evdev touchscreen catchall"
[    46.219] (II) Using input driver 'evdev' for 'USBest Technology SiS HID Touch Controller'
[    46.219] (**) USBest Technology SiS HID Touch Controller: always reports core events
[    46.219] (**) evdev: USBest Technology SiS HID Touch Controller: Device: "/dev/input/event7"
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Vendor 0x457 Product 0x111a
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute axes
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute multitouch axes
[    46.276] (II) evdev: USBest Technology SiS HID Touch Controller: No buttons found, faking one.
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Found x and y absolute axes
[    46.276] (--) evdev: USBest Technology SiS HID Touch Controller: Found absolute touchscreen
[    46.276] (II) evdev: USBest Technology SiS HID Touch Controller: Configuring as touchscreen
[    46.276] (**) evdev: USBest Technology SiS HID Touch Controller: YAxisMapping: buttons 4 and 5
[    46.276] (**) evdev: USBest Technology SiS HID Touch Controller: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    46.276] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:0457:111A.0004/input/input10/event7"
[    46.276] (II) XINPUT: Adding extended input device "USBest Technology SiS HID Touch Controller" (type: TOUCHSCREEN, id 14)
[    46.276] (II) evdev: USBest Technology SiS HID Touch Controller: initialized for absolute axes.
[    46.276] (**) USBest Technology SiS HID Touch Controller: (accel) keeping acceleration scheme 1
[    46.277] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration profile 0
[    46.277] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration factor: 2.000
[    46.277] (**) USBest Technology SiS HID Touch Controller: (accel) acceleration threshold: 4
[    46.278] (II) config/udev: Adding input device USBest Technology SiS HID Touch Controller (/dev/input/mouse1)
[    46.278] (II) No input driver specified, ignoring this device.
[    46.278] (II) This device may have been added with another device file.
[    46.278] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    46.278] (II) No input driver specified, ignoring this device.
[    46.278] (II) This device may have been added with another device file.
[    46.279] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event11)
[    46.279] (II) No input driver specified, ignoring this device.
[    46.279] (II) This device may have been added with another device file.
[    46.280] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    46.280] (II) No input driver specified, ignoring this device.
[    46.280] (II) This device may have been added with another device file.
[    46.280] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event13)
[    46.280] (II) No input driver specified, ignoring this device.
[    46.280] (II) This device may have been added with another device file.
[    46.281] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event14)
[    46.281] (II) No input driver specified, ignoring this device.
[    46.281] (II) This device may have been added with another device file.
[    46.284] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event8)
[    46.284] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    46.284] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    46.284] (**) HP WMI hotkeys: always reports core events
[    46.284] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event8"
[    46.284] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    46.284] (--) evdev: HP WMI hotkeys: Found keys
[    46.284] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    46.284] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event8"
[    46.284] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 15)
[    46.284] (**) Option "xkb_rules" "evdev"
[    46.284] (**) Option "xkb_model" "pc105"
[    46.284] (**) Option "xkb_layout" "us"
```

---

### Post by wildmanne39 on 2016-09-30
*Thread moved to **Ubuntu Development Version**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

