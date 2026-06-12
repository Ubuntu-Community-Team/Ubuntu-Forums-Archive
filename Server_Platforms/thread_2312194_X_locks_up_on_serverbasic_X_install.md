---
title: "X locks up on server/basic X install"
date: 2016-02-02
forum: Server Platforms
---

### Post by le_jawa on 2016-02-02
I'm trying to use an Ubuntu server installation to create a basic X thin client implementation.  The bare-bones server boots fine on the terminal (Wyse R50L), but no matter what I do, X locks up whenever I start it.  I installed xinit, and all the dependencies that came with it, and I've tried multiple configurations with multiple drivers and none of them work.  Every time X loads, it displays an xterm, and stops there.  The hollow cursor on the xterm never flashes, and I can't use the keyboard at all except to flip to one of the virtual terminals and kill X.

If however, I boot a flash drive with the Live disc image on it, every thing works fine.

Both my install and the live USB drive are using Ubuntu 14.04.3.
Hardware info: 
-Video chip: ATI 690E
-Keyboard: Generic PS/2 keyboard
-Mouse: None

There are errors from loading and unloading video drivers in the Xorg log, but no errors at the end of the log that would suggest a problem.  Here's an example though:

Thank you for looking!
Jason

```
[   144.406] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   144.407] X Protocol Version 11, Revision 0
[   144.407] Build Operating System: Linux 3.2.0-75-generic i686 Ubuntu
[   144.407] Current Operating System: Linux ubuntu 3.16.0-60-generic #80~14.04.1-Ubuntu SMP Wed Jan 20 13:38:16 UTC 2016 i686
[   144.407] Kernel command line: BOOT_IMAGE=vmlinuz boot=nfs root=/dev/nfs initrd=initrd.img nfsroot=some.ip.add.ress:/m2/posterm/i386 ip=dhcp rw
[   144.407] Build Date: 12 February 2015  02:49:46PM
[   144.407] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   144.407] Current version of pixman: 0.30.2
[   144.408]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   144.408] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   144.410] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb  2 15:22:40 2016
[   144.427] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   144.451] (==) No Layout section.  Using the first Screen section.
[   144.451] (==) No screen section available. Using defaults.
[   144.451] (**) |-->Screen "Default Screen Section" (0)
[   144.451] (**) |   |-->Monitor "<default monitor>"
[   144.451] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   144.451] (==) Automatically adding devices
[   144.451] (==) Automatically enabling devices
[   144.451] (==) Automatically adding GPU devices
[   144.456] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   144.456]     Entry deleted from font path.
[   144.456] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   144.456]     Entry deleted from font path.
[   144.457] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   144.457]     Entry deleted from font path.
[   144.457] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[   144.457]     Entry deleted from font path.
[   144.457] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   144.457]     Entry deleted from font path.
[   144.457] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   144.457]     Entry deleted from font path.
[   144.457] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[   144.457] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   144.457] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   144.457] (II) Loader magic: 0xb77036c0
[   144.457] (II) Module ABI versions:
[   144.457]     X.Org ANSI C Emulation: 0.4
[   144.457]     X.Org Video Driver: 15.0
[   144.457]     X.Org XInput driver : 20.0
[   144.457]     X.Org Server Extension : 8.0
[   144.459] (--) PCI:*(0:1:5:0) 1002:791f:1002:053a rev 0, Mem @ 0xf0000000/134217728, 0xf8100000/65536, 0xf8000000/1048576, I/O @ 0x00009000/256
[   144.459] Initializing built-in extension Generic Event Extension
[   144.459] Initializing built-in extension SHAPE
[   144.460] Initializing built-in extension MIT-SHM
[   144.460] Initializing built-in extension XInputExtension
[   144.460] Initializing built-in extension XTEST
[   144.460] Initializing built-in extension BIG-REQUESTS
[   144.460] Initializing built-in extension SYNC
[   144.460] Initializing built-in extension XKEYBOARD
[   144.460] Initializing built-in extension XC-MISC
[   144.460] Initializing built-in extension SECURITY
[   144.460] Initializing built-in extension XINERAMA
[   144.460] Initializing built-in extension XFIXES
[   144.460] Initializing built-in extension RENDER
[   144.460] Initializing built-in extension RANDR
[   144.461] Initializing built-in extension COMPOSITE
[   144.461] Initializing built-in extension DAMAGE
[   144.461] Initializing built-in extension MIT-SCREEN-SAVER
[   144.461] Initializing built-in extension DOUBLE-BUFFER
[   144.461] Initializing built-in extension RECORD
[   144.461] Initializing built-in extension DPMS
[   144.461] Initializing built-in extension Present
[   144.461] Initializing built-in extension DRI3
[   144.461] Initializing built-in extension X-Resource
[   144.461] Initializing built-in extension XVideo
[   144.461] Initializing built-in extension XVideo-MotionCompensation
[   144.461] Initializing built-in extension SELinux
[   144.462] Initializing built-in extension XFree86-VidModeExtension
[   144.462] Initializing built-in extension XFree86-DGA
[   144.462] Initializing built-in extension XFree86-DRI
[   144.462] Initializing built-in extension DRI2
[   144.462] (II) LoadModule: "glx"
[   144.482] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   145.189] (II) Module glx: vendor="X.Org Foundation"
[   145.189]     compiled for 1.15.1, module version = 1.0.0
[   145.189]     ABI class: X.Org Server Extension, version 8.0
[   145.189] (==) AIGLX enabled
[   145.190] Loading extension GLX
[   145.190] (==) Matched fglrx as autoconfigured driver 0
[   145.190] (==) Matched ati as autoconfigured driver 1
[   145.190] (==) Matched modesetting as autoconfigured driver 2
[   145.190] (==) Matched fbdev as autoconfigured driver 3
[   145.190] (==) Matched vesa as autoconfigured driver 4
[   145.190] (==) Assigned the driver to the xf86ConfigLayout
[   145.190] (II) LoadModule: "fglrx"
[   145.203] (WW) Warning, couldn't open module fglrx
[   145.203] (II) UnloadModule: "fglrx"
[   145.203] (II) Unloading fglrx
[   145.203] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   145.203] (II) LoadModule: "ati"
[   145.206] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   145.209] (II) Module ati: vendor="X.Org Foundation"
[   145.209]     compiled for 1.15.1, module version = 7.3.0
[   145.209]     Module class: X.Org Video Driver
[   145.209]     ABI class: X.Org Video Driver, version 15.0
[   145.209] (II) LoadModule: "radeon"
[   145.212] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   145.278] (II) Module radeon: vendor="X.Org Foundation"
[   145.278]     compiled for 1.15.1, module version = 7.3.0
[   145.278]     Module class: X.Org Video Driver
[   145.278]     ABI class: X.Org Video Driver, version 15.0
[   145.278] (II) LoadModule: "modesetting"
[   145.290] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   145.296] (II) Module modesetting: vendor="X.Org Foundation"
[   145.297]     compiled for 1.15.0, module version = 0.8.1
[   145.297]     Module class: X.Org Video Driver
[   145.297]     ABI class: X.Org Video Driver, version 15.0
[   145.297] (II) LoadModule: "fbdev"
[   145.299] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   145.304] (II) Module fbdev: vendor="X.Org Foundation"
[   145.305]     compiled for 1.15.0, module version = 0.4.4
[   145.305]     Module class: X.Org Video Driver
[   145.305]     ABI class: X.Org Video Driver, version 15.0
[   145.305] (II) LoadModule: "vesa"
[   145.308] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   145.313] (II) Module vesa: vendor="X.Org Foundation"
[   145.313]     compiled for 1.15.0, module version = 2.3.3
[   145.313]     Module class: X.Org Video Driver
[   145.313]     ABI class: X.Org Video Driver, version 15.0
[   145.313] (==) Matched fglrx as autoconfigured driver 0
[   145.313] (==) Matched ati as autoconfigured driver 1
[   145.313] (==) Matched modesetting as autoconfigured driver 2
[   145.313] (==) Matched fbdev as autoconfigured driver 3
[   145.313] (==) Matched vesa as autoconfigured driver 4
[   145.314] (==) Assigned the driver to the xf86ConfigLayout
[   145.314] (II) LoadModule: "fglrx"
[   145.320] (WW) Warning, couldn't open module fglrx
[   145.320] (II) UnloadModule: "fglrx"
[   145.320] (II) Unloading fglrx
[   145.320] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   145.320] (II) LoadModule: "ati"
[   145.323] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   145.323] (II) Module ati: vendor="X.Org Foundation"
[   145.323]     compiled for 1.15.1, module version = 7.3.0
[   145.323]     Module class: X.Org Video Driver
[   145.323]     ABI class: X.Org Video Driver, version 15.0
[   145.323] (II) LoadModule: "modesetting"
[   145.326] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   145.326] (II) Module modesetting: vendor="X.Org Foundation"
[   145.326]     compiled for 1.15.0, module version = 0.8.1
[   145.326]     Module class: X.Org Video Driver
[   145.326]     ABI class: X.Org Video Driver, version 15.0
[   145.326] (II) UnloadModule: "modesetting"
[   145.326] (II) Unloading modesetting
[   145.326] (II) Failed to load module "modesetting" (already loaded, 0)
[   145.326] (II) LoadModule: "fbdev"
[   145.329] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   145.329] (II) Module fbdev: vendor="X.Org Foundation"
[   145.329]     compiled for 1.15.0, module version = 0.4.4
[   145.329]     Module class: X.Org Video Driver
[   145.329]     ABI class: X.Org Video Driver, version 15.0
[   145.329] (II) UnloadModule: "fbdev"
[   145.329] (II) Unloading fbdev
[   145.329] (II) Failed to load module "fbdev" (already loaded, 0)
[   145.329] (II) LoadModule: "vesa"
[   145.332] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   145.332] (II) Module vesa: vendor="X.Org Foundation"
[   145.332]     compiled for 1.15.0, module version = 2.3.3
[   145.332]     Module class: X.Org Video Driver
[   145.332]     ABI class: X.Org Video Driver, version 15.0
[   145.332] (II) UnloadModule: "vesa"
[   145.332] (II) Unloading vesa
[   145.332] (II) Failed to load module "vesa" (already loaded, 0)
[   145.332] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ...enumaration of all supported chips removed for some degree of brevity...
[   145.338] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   145.338] (II) FBDEV: driver for framebuffer: fbdev
[   145.338] (II) VESA: driver for VESA chipsets: vesa
[   145.338] (--) using VT number 7


[   145.341] (II) [KMS] drm report modesetting isn't supported.
[   145.341] (EE) open /dev/dri/card0: No such file or directory
[   145.341] (EE) open /dev/dri/card0: No such file or directory
[   145.341] (WW) Falling back to old probe method for modesetting
[   145.341] (EE) open /dev/dri/card0: No such file or directory
[   145.341] (EE) open /dev/dri/card0: No such file or directory
[   145.341] (II) Loading sub module "fbdevhw"
[   145.341] (II) LoadModule: "fbdevhw"
[   145.344] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   145.349] (II) Module fbdevhw: vendor="X.Org Foundation"
[   145.349]     compiled for 1.15.1, module version = 0.0.2
[   145.349]     ABI class: X.Org Video Driver, version 15.0
[   145.349] (EE) open /dev/fb0: No such file or directory
[   145.349] (II) Loading sub module "fbdevhw"
[   145.349] (II) LoadModule: "fbdevhw"
[   145.352] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   145.352] (II) Module fbdevhw: vendor="X.Org Foundation"
[   145.352]     compiled for 1.15.1, module version = 0.0.2
[   145.352]     ABI class: X.Org Video Driver, version 15.0
[   145.352] (EE) open /dev/fb0: No such file or directory
[   145.352] (WW) Falling back to old probe method for fbdev
[   145.352] (II) Loading sub module "fbdevhw"
[   145.353] (II) LoadModule: "fbdevhw"
[   145.356] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   145.356] (II) Module fbdevhw: vendor="X.Org Foundation"
[   145.356]     compiled for 1.15.1, module version = 0.0.2
[   145.356]     ABI class: X.Org Video Driver, version 15.0
[   145.356] (EE) open /dev/fb0: No such file or directory
[   145.356] (EE) open /dev/fb0: No such file or directory
[   145.356] (EE) Screen 0 deleted because of no matching config section.
[   145.356] (II) UnloadModule: "radeon"
[   145.356] (EE) Screen 0 deleted because of no matching config section.
[   145.356] (II) UnloadModule: "modesetting"
[   145.356] (EE) Screen 0 deleted because of no matching config section.
[   145.356] (II) UnloadModule: "modesetting"
[   145.356] (EE) Screen 0 deleted because of no matching config section.
[   145.356] (II) UnloadModule: "fbdev"
[   145.356] (II) UnloadSubModule: "fbdevhw"
[   145.356] (EE) Screen 0 deleted because of no matching config section.
[   145.356] (II) UnloadModule: "fbdev"
[   145.356] (II) UnloadSubModule: "fbdevhw"
[   145.356] (II) UnloadSubModule: "fbdevhw"
[   145.356] (II) Loading sub module "vbe"
[   145.356] (II) LoadModule: "vbe"
[   145.358] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   145.363] (II) Module vbe: vendor="X.Org Foundation"
[   145.363]     compiled for 1.15.1, module version = 1.1.0
[   145.363]     ABI class: X.Org Video Driver, version 15.0
[   145.363] (II) Loading sub module "int10"
[   145.363] (II) LoadModule: "int10"
[   145.364] (II) Loading /usr/lib/xorg/modules/libint10.so
[   145.382] (II) Module int10: vendor="X.Org Foundation"
[   145.382]     compiled for 1.15.1, module version = 1.0.0
[   145.382]     ABI class: X.Org Video Driver, version 15.0
[   145.382] (II) VESA(0): initializing int10
[   145.383] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   145.383] (II) VESA(0): VESA BIOS detected
[   145.383] (II) VESA(0): VESA VBE Version 3.0
[   145.383] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   145.383] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   145.383] (II) VESA(0): VESA VBE OEM Software Rev: 10.55
[   145.383] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   145.383] (II) VESA(0): VESA VBE OEM Product: RS690
[   145.383] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   145.403] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   145.404] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[   145.404] (==) VESA(0): RGB weight 888
[   145.404] (==) VESA(0): Default visual is TrueColor
[   145.404] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[   145.404] (II) Loading sub module "ddc"
[   145.404] (II) LoadModule: "ddc"
[   145.404] (II) Module "ddc" already built-in
[   145.404] (II) VESA(0): VESA VBE DDC supported
[   145.404] (II) VESA(0): VESA VBE DDC Level 2
[   145.404] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[   145.458] (II) VESA(0): VESA VBE DDC read successfully
[   145.458] (II) VESA(0): Manufacturer: ACR  Model: ad87  Serial#: 1933607110
[   145.458] (II) VESA(0): Year: 2007  Week: 34
[   145.458] (II) VESA(0): EDID Version: 1.3
[   145.458] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   145.458] (II) VESA(0): Sync:  Separate
[   145.458] (II) VESA(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[   145.458] (II) VESA(0): Gamma: 2.20
[   145.459] (II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   145.459] (II) VESA(0): First detailed timing not preferred mode in violation of standard!
[   145.459] (II) VESA(0): redX: 0.650 redY: 0.345   greenX: 0.287 greenY: 0.600
[   145.459] (II) VESA(0): blueX: 0.140 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
[   145.459] (II) VESA(0): Supported established timings:
[   145.459] (II) VESA(0): 720x400@70Hz
[   145.459] (II) VESA(0): 640x480@60Hz
[   145.459] (II) VESA(0): 640x480@67Hz
[   145.459] (II) VESA(0): 640x480@72Hz
[   145.459] (II) VESA(0): 640x480@75Hz
[   145.459] (II) VESA(0): 800x600@56Hz
[   145.459] (II) VESA(0): 800x600@60Hz
[   145.459] (II) VESA(0): 800x600@72Hz
[   145.459] (II) VESA(0): 800x600@75Hz
[   145.459] (II) VESA(0): 832x624@75Hz
[   145.459] (II) VESA(0): 1024x768@60Hz
[   145.459] (II) VESA(0): 1024x768@70Hz
[   145.459] (II) VESA(0): 1024x768@75Hz
[   145.459] (II) VESA(0): 1280x1024@75Hz
[   145.459] (II) VESA(0): 1152x864@75Hz
[   145.459] (II) VESA(0): Manufacturer's mask: 0
[   145.459] (II) VESA(0): Supported standard timings:
[   145.459] (II) VESA(0): #0: hsize: 1400  vsize 1050  refresh: 75  vid: 20368
[   145.459] (II) VESA(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[   145.459] (II) VESA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   145.459] (II) VESA(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   145.459] (II) VESA(0): #4: hsize: 1280  vsize 800  refresh: 75  vid: 3969
[   145.459] (II) VESA(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   145.459] (II) VESA(0): #6: hsize: 1152  vsize 921  refresh: 76  vid: 36977
[   145.459] (II) VESA(0): #7: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   145.459] (II) VESA(0): Supported detailed timing:
[   145.459] (II) VESA(0): clock: 89.0 MHz   Image Size:  410 x 257 mm
[   145.459] (II) VESA(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
[   145.459] (II) VESA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[   145.459] (II) VESA(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 84 kHz, PixClock max 145 MHz
[   145.459] (II) VESA(0): Serial No: L870C0444032
[   145.459] (II) VESA(0): Monitor name: AL1917W
[   145.459] (II) VESA(0): EDID (in hex):
[   145.459] (II) VESA(0):     00ffffffffffff00047287adc6804073
[   145.459] (II) VESA(0):     2211010308291a78e89ae5a658499923
[   145.459] (II) VESA(0):     115054bfef80904f950f81808140810f
[   145.459] (II) VESA(0):     81007190714fc422a0a050841a303020
[   145.459] (II) VESA(0):     36009a011100001e000000fd00384c1f
[   145.459] (II) VESA(0):     540e000a202020202020000000ff004c
[   145.459] (II) VESA(0):     38373043303434343033320a000000fc
[   145.459] (II) VESA(0):     00414c31393137570a202020202000b1
[   145.459] (II) VESA(0): EDID vendor "ACR", prod id 44423
[   145.459] (II) VESA(0): Using EDID range info for horizontal sync
[   145.459] (II) VESA(0): Using EDID range info for vertical refresh
[   145.459] (II) VESA(0): Printing DDC gathered Modelines:
[   145.459] (II) VESA(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[   145.459] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   145.459] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   145.459] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   145.459] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   145.459] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   145.459] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   145.459] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   145.459] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   145.459] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   145.459] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   145.459] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   145.459] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   145.459] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   145.459] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   145.459] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   145.459] (II) VESA(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[   145.459] (II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[   145.459] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   145.459] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   145.459] (II) VESA(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[   145.459] (II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[   145.459] (II) VESA(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[   145.459] (II) VESA(0): Searching for matching VESA mode(s):
[   145.460] Mode: 100 (640x400)
[   145.460]     ModeAttributes: 0xbb
[   145.460]     WinAAttributes: 0x7
[   145.460]     WinBAttributes: 0x0
[   145.460]     WinGranularity: 64
[   145.460]     WinSize: 64
[   145.460]     WinASegment: 0xa000
[   145.460]     WinBSegment: 0x0
[   145.460]     WinFuncPtr: 0xc0005237
[   145.460]     BytesPerScanline: 640
[   145.460]     XResolution: 640
[   145.460]     YResolution: 400
[   145.460]     XCharSize: 8
[   145.460]     YCharSize: 16
[   145.460]     NumberOfPlanes: 1
[   145.460]     BitsPerPixel: 8
[   145.460]     NumberOfBanks: 1
[   145.460]     MemoryModel: 4
[   145.460]     BankSize: 0
[   145.460]     NumberOfImages: 63
[   145.460]     RedMaskSize: 0
[   145.460]     RedFieldPosition: 0
[   145.460]     GreenMaskSize: 0
[   145.460]     GreenFieldPosition: 0
[   145.460]     BlueMaskSize: 0
[   145.460]     BlueFieldPosition: 0
[   145.460]     RsvdMaskSize: 0
[   145.460]     RsvdFieldPosition: 0
[   145.460]     DirectColorModeInfo: 0
[   145.460]     PhysBasePtr: 0xf0000000
[   145.460]     LinBytesPerScanLine: 640
[   145.460]     BnkNumberOfImagePages: 63
[   145.460]     LinNumberOfImagePages: 63
[   145.460]     LinRedMaskSize: 0
[   145.460]     LinRedFieldPosition: 0
[   145.460]     LinGreenMaskSize: 0
[   145.460]     LinGreenFieldPosition: 0
[   145.460]     LinBlueMaskSize: 0
[   145.460]     LinBlueFieldPosition: 0
[   145.460]     LinRsvdMaskSize: 0
[   145.460]     LinRsvdFieldPosition: 0
[   145.460]     MaxPixelClock: 400000000
[   145.461] Mode: 101 (640x480)
[   145.461]     ModeAttributes: 0xbb
[   145.461]     WinAAttributes: 0x7
[   145.461]     WinBAttributes: 0x0
[   145.461]     WinGranularity: 64
[   145.461]     WinSize: 64
[   145.461]     WinASegment: 0xa000
[   145.461]     WinBSegment: 0x0
[   145.461]     WinFuncPtr: 0xc0005237
[   145.461]     BytesPerScanline: 640
[   145.461]     XResolution: 640
[   145.461]     YResolution: 480
[   145.461]     XCharSize: 8
[   145.461]     YCharSize: 16
[   145.461]     NumberOfPlanes: 1
[   145.461]     BitsPerPixel: 8
[   145.461]     NumberOfBanks: 1
[   145.461]     MemoryModel: 4
[   145.461]     BankSize: 0
[   145.461]     NumberOfImages: 50
[   145.461]     RedMaskSize: 0
[   145.461]     RedFieldPosition: 0
[   145.461]     GreenMaskSize: 0
[   145.461]     GreenFieldPosition: 0
[   145.461]     BlueMaskSize: 0
[   145.461]     BlueFieldPosition: 0
[   145.461]     RsvdMaskSize: 0
[   145.461]     RsvdFieldPosition: 0
[   145.461]     DirectColorModeInfo: 0
[   145.461]     PhysBasePtr: 0xf0000000
[   145.461]     LinBytesPerScanLine: 640
[   145.461]     BnkNumberOfImagePages: 50
[   145.461]     LinNumberOfImagePages: 50
[   145.461]     LinRedMaskSize: 0
[   145.461]     LinRedFieldPosition: 0
[   145.461]     LinGreenMaskSize: 0
[   145.461]     LinGreenFieldPosition: 0
[   145.461]     LinBlueMaskSize: 0
[   145.461]     LinBlueFieldPosition: 0
[   145.461]     LinRsvdMaskSize: 0
[   145.461]     LinRsvdFieldPosition: 0
[   145.461]     MaxPixelClock: 400000000
[   145.461] Mode: 103 (800x600)
[   145.461]     ModeAttributes: 0xbb
[   145.461]     WinAAttributes: 0x7
[   145.461]     WinBAttributes: 0x0
[   145.461]     WinGranularity: 64
[   145.461]     WinSize: 64
[   145.461]     WinASegment: 0xa000
[   145.461]     WinBSegment: 0x0
[   145.461]     WinFuncPtr: 0xc0005237
[   145.461]     BytesPerScanline: 832
[   145.461]     XResolution: 800
[   145.461]     YResolution: 600
[   145.461]     XCharSize: 8
[   145.461]     YCharSize: 14
[   145.461]     NumberOfPlanes: 1
[   145.461]     BitsPerPixel: 8
[   145.461]     NumberOfBanks: 1
[   145.461]     MemoryModel: 4
[   145.461]     BankSize: 0
[   145.461]     NumberOfImages: 31
[   145.461]     RedMaskSize: 0
[   145.461]     RedFieldPosition: 0
[   145.461]     GreenMaskSize: 0
[   145.461]     GreenFieldPosition: 0
[   145.461]     BlueMaskSize: 0
[   145.461]     BlueFieldPosition: 0
[   145.461]     RsvdMaskSize: 0
[   145.461]     RsvdFieldPosition: 0
[   145.461]     DirectColorModeInfo: 0
[   145.461]     PhysBasePtr: 0xf0000000
[   145.461]     LinBytesPerScanLine: 832
[   145.461]     BnkNumberOfImagePages: 31
[   145.461]     LinNumberOfImagePages: 31
[   145.461]     LinRedMaskSize: 0
[   145.461]     LinRedFieldPosition: 0
[   145.461]     LinGreenMaskSize: 0
[   145.462]     LinGreenFieldPosition: 0
[   145.462]     LinBlueMaskSize: 0
[   145.462]     LinBlueFieldPosition: 0
[   145.462]     LinRsvdMaskSize: 0
[   145.462]     LinRsvdFieldPosition: 0
[   145.462]     MaxPixelClock: 400000000
[   145.462] Mode: 105 (1024x768)
[   145.462]     ModeAttributes: 0xbb
[   145.462]     WinAAttributes: 0x7
[   145.462]     WinBAttributes: 0x0
[   145.462]     WinGranularity: 64
[   145.462]     WinSize: 64
[   145.462]     WinASegment: 0xa000
[   145.462]     WinBSegment: 0x0
[   145.462]     WinFuncPtr: 0xc0005237
[   145.462]     BytesPerScanline: 1024
[   145.462]     XResolution: 1024
[   145.462]     YResolution: 768
[   145.462]     XCharSize: 8
[   145.462]     YCharSize: 16
[   145.462]     NumberOfPlanes: 1
[   145.462]     BitsPerPixel: 8
[   145.462]     NumberOfBanks: 1
[   145.462]     MemoryModel: 4
[   145.462]     BankSize: 0
[   145.462]     NumberOfImages: 18
[   145.462]     RedMaskSize: 0
[   145.462]     RedFieldPosition: 0
[   145.462]     GreenMaskSize: 0
[   145.462]     GreenFieldPosition: 0
[   145.462]     BlueMaskSize: 0
[   145.462]     BlueFieldPosition: 0
[   145.462]     RsvdMaskSize: 0
[   145.462]     RsvdFieldPosition: 0
[   145.462]     DirectColorModeInfo: 0
[   145.462]     PhysBasePtr: 0xf0000000
[   145.462]     LinBytesPerScanLine: 1024
[   145.462]     BnkNumberOfImagePages: 18
[   145.462]     LinNumberOfImagePages: 18
[   145.462]     LinRedMaskSize: 0
[   145.462]     LinRedFieldPosition: 0
[   145.462]     LinGreenMaskSize: 0
[   145.462]     LinGreenFieldPosition: 0
[   145.462]     LinBlueMaskSize: 0
[   145.462]     LinBlueFieldPosition: 0
[   145.462]     LinRsvdMaskSize: 0
[   145.462]     LinRsvdFieldPosition: 0
[   145.462]     MaxPixelClock: 400000000
[   145.463] Mode: 107 (1280x1024)
[   145.463]     ModeAttributes: 0xbb
[   145.463]     WinAAttributes: 0x7
[   145.463]     WinBAttributes: 0x0
[   145.463]     WinGranularity: 64
[   145.463]     WinSize: 64
[   145.463]     WinASegment: 0xa000
[   145.463]     WinBSegment: 0x0
[   145.463]     WinFuncPtr: 0xc0005237
[   145.463]     BytesPerScanline: 1280
[   145.463]     XResolution: 1280
[   145.463]     YResolution: 1024
[   145.463]     XCharSize: 8
[   145.463]     YCharSize: 16
[   145.463]     NumberOfPlanes: 1
[   145.463]     BitsPerPixel: 8
[   145.463]     NumberOfBanks: 1
[   145.463]     MemoryModel: 4
[   145.463]     BankSize: 0
[   145.463]     NumberOfImages: 11
[   145.463]     RedMaskSize: 0
[   145.463]     RedFieldPosition: 0
[   145.463]     GreenMaskSize: 0
[   145.463]     GreenFieldPosition: 0
[   145.463]     BlueMaskSize: 0
[   145.463]     BlueFieldPosition: 0
[   145.463]     RsvdMaskSize: 0
[   145.463]     RsvdFieldPosition: 0
[   145.463]     DirectColorModeInfo: 0
[   145.463]     PhysBasePtr: 0xf0000000
[   145.463]     LinBytesPerScanLine: 1280
[   145.463]     BnkNumberOfImagePages: 11
[   145.463]     LinNumberOfImagePages: 11
[   145.463]     LinRedMaskSize: 0
[   145.463]     LinRedFieldPosition: 0
[   145.463]     LinGreenMaskSize: 0
[   145.463]     LinGreenFieldPosition: 0
[   145.463]     LinBlueMaskSize: 0
[   145.463]     LinBlueFieldPosition: 0
[   145.463]     LinRsvdMaskSize: 0
[   145.463]     LinRsvdFieldPosition: 0
[   145.463]     MaxPixelClock: 400000000
[   145.463] Mode: 111 (640x480)
[   145.463]     ModeAttributes: 0xbb
[   145.463]     WinAAttributes: 0x7
[   145.463]     WinBAttributes: 0x0
[   145.463]     WinGranularity: 64
[   145.463]     WinSize: 64
[   145.463]     WinASegment: 0xa000
[   145.463]     WinBSegment: 0x0
[   145.463]     WinFuncPtr: 0xc0005237
[   145.463]     BytesPerScanline: 1280
[   145.463]     XResolution: 640
[   145.463]     YResolution: 480
[   145.463]     XCharSize: 8
[   145.463]     YCharSize: 16
[   145.463]     NumberOfPlanes: 1
[   145.463]     BitsPerPixel: 16
[   145.463]     NumberOfBanks: 1
[   145.463]     MemoryModel: 6
[   145.463]     BankSize: 0
[   145.463]     NumberOfImages: 24
[   145.463]     RedMaskSize: 5
[   145.463]     RedFieldPosition: 11
[   145.463]     GreenMaskSize: 6
[   145.463]     GreenFieldPosition: 5
[   145.463]     BlueMaskSize: 5
[   145.463]     BlueFieldPosition: 0
[   145.463]     RsvdMaskSize: 0
[   145.463]     RsvdFieldPosition: 0
[   145.463]     DirectColorModeInfo: 0
[   145.463]     PhysBasePtr: 0xf0000000
[   145.463]     LinBytesPerScanLine: 1280
[   145.463]     BnkNumberOfImagePages: 24
[   145.463]     LinNumberOfImagePages: 24
[   145.463]     LinRedMaskSize: 5
[   145.463]     LinRedFieldPosition: 11
[   145.463]     LinGreenMaskSize: 6
[   145.464]     LinGreenFieldPosition: 5
[   145.464]     LinBlueMaskSize: 5
[   145.464]     LinBlueFieldPosition: 0
[   145.464]     LinRsvdMaskSize: 0
[   145.464]     LinRsvdFieldPosition: 0
[   145.464]     MaxPixelClock: 400000000
[   145.464] Mode: 114 (800x600)
[   145.464]     ModeAttributes: 0xbb
[   145.464]     WinAAttributes: 0x7
[   145.464]     WinBAttributes: 0x0
[   145.464]     WinGranularity: 64
[   145.464]     WinSize: 64
[   145.464]     WinASegment: 0xa000
[   145.464]     WinBSegment: 0x0
[   145.464]     WinFuncPtr: 0xc0005237
[   145.464]     BytesPerScanline: 1600
[   145.464]     XResolution: 800
[   145.464]     YResolution: 600
[   145.464]     XCharSize: 8
[   145.464]     YCharSize: 14
[   145.464]     NumberOfPlanes: 1
[   145.464]     BitsPerPixel: 16
[   145.464]     NumberOfBanks: 1
[   145.464]     MemoryModel: 6
[   145.464]     BankSize: 0
[   145.464]     NumberOfImages: 16
[   145.464]     RedMaskSize: 5
[   145.464]     RedFieldPosition: 11
[   145.464]     GreenMaskSize: 6
[   145.464]     GreenFieldPosition: 5
[   145.464]     BlueMaskSize: 5
[   145.464]     BlueFieldPosition: 0
[   145.464]     RsvdMaskSize: 0
[   145.464]     RsvdFieldPosition: 0
[   145.464]     DirectColorModeInfo: 0
[   145.464]     PhysBasePtr: 0xf0000000
[   145.464]     LinBytesPerScanLine: 1600
[   145.464]     BnkNumberOfImagePages: 16
[   145.464]     LinNumberOfImagePages: 16
[   145.464]     LinRedMaskSize: 5
[   145.464]     LinRedFieldPosition: 11
[   145.464]     LinGreenMaskSize: 6
[   145.464]     LinGreenFieldPosition: 5
[   145.464]     LinBlueMaskSize: 5
[   145.464]     LinBlueFieldPosition: 0
[   145.464]     LinRsvdMaskSize: 0
[   145.464]     LinRsvdFieldPosition: 0
[   145.464]     MaxPixelClock: 400000000
[   145.465] Mode: 117 (1024x768)
[   145.465]     ModeAttributes: 0xbb
[   145.465]     WinAAttributes: 0x7
[   145.465]     WinBAttributes: 0x0
[   145.465]     WinGranularity: 64
[   145.465]     WinSize: 64
[   145.465]     WinASegment: 0xa000
[   145.465]     WinBSegment: 0x0
[   145.465]     WinFuncPtr: 0xc0005237
[   145.465]     BytesPerScanline: 2048
[   145.465]     XResolution: 1024
[   145.465]     YResolution: 768
[   145.465]     XCharSize: 8
[   145.465]     YCharSize: 16
[   145.465]     NumberOfPlanes: 1
[   145.465]     BitsPerPixel: 16
[   145.465]     NumberOfBanks: 1
[   145.465]     MemoryModel: 6
[   145.465]     BankSize: 0
[   145.465]     NumberOfImages: 9
[   145.465]     RedMaskSize: 5
[   145.465]     RedFieldPosition: 11
[   145.465]     GreenMaskSize: 6
[   145.465]     GreenFieldPosition: 5
[   145.465]     BlueMaskSize: 5
[   145.465]     BlueFieldPosition: 0
[   145.465]     RsvdMaskSize: 0
[   145.465]     RsvdFieldPosition: 0
[   145.465]     DirectColorModeInfo: 0
[   145.465]     PhysBasePtr: 0xf0000000
[   145.465]     LinBytesPerScanLine: 2048
[   145.465]     BnkNumberOfImagePages: 9
[   145.465]     LinNumberOfImagePages: 9
[   145.465]     LinRedMaskSize: 5
[   145.465]     LinRedFieldPosition: 11
[   145.465]     LinGreenMaskSize: 6
[   145.465]     LinGreenFieldPosition: 5
[   145.465]     LinBlueMaskSize: 5
[   145.465]     LinBlueFieldPosition: 0
[   145.465]     LinRsvdMaskSize: 0
[   145.465]     LinRsvdFieldPosition: 0
[   145.465]     MaxPixelClock: 400000000
[   145.465] Mode: 11a (1280x1024)
[   145.465]     ModeAttributes: 0xbb
[   145.465]     WinAAttributes: 0x7
[   145.465]     WinBAttributes: 0x0
[   145.465]     WinGranularity: 64
[   145.465]     WinSize: 64
[   145.465]     WinASegment: 0xa000
[   145.465]     WinBSegment: 0x0
[   145.465]     WinFuncPtr: 0xc0005237
[   145.465]     BytesPerScanline: 2560
[   145.465]     XResolution: 1280
[   145.465]     YResolution: 1024
[   145.465]     XCharSize: 8
[   145.465]     YCharSize: 16
[   145.465]     NumberOfPlanes: 1
[   145.465]     BitsPerPixel: 16
[   145.465]     NumberOfBanks: 1
[   145.465]     MemoryModel: 6
[   145.465]     BankSize: 0
[   145.465]     NumberOfImages: 5
[   145.465]     RedMaskSize: 5
[   145.465]     RedFieldPosition: 11
[   145.465]     GreenMaskSize: 6
[   145.465]     GreenFieldPosition: 5
[   145.465]     BlueMaskSize: 5
[   145.465]     BlueFieldPosition: 0
[   145.465]     RsvdMaskSize: 0
[   145.465]     RsvdFieldPosition: 0
[   145.465]     DirectColorModeInfo: 0
[   145.466]     PhysBasePtr: 0xf0000000
[   145.466]     LinBytesPerScanLine: 2560
[   145.466]     BnkNumberOfImagePages: 5
[   145.466]     LinNumberOfImagePages: 5
[   145.466]     LinRedMaskSize: 5
[   145.466]     LinRedFieldPosition: 11
[   145.466]     LinGreenMaskSize: 6
[   145.466]     LinGreenFieldPosition: 5
[   145.466]     LinBlueMaskSize: 5
[   145.466]     LinBlueFieldPosition: 0
[   145.466]     LinRsvdMaskSize: 0
[   145.466]     LinRsvdFieldPosition: 0
[   145.466]     MaxPixelClock: 400000000
[   145.466] Mode: 10e (320x200)
[   145.466]     ModeAttributes: 0xbb
[   145.466]     WinAAttributes: 0x7
[   145.466]     WinBAttributes: 0x0
[   145.466]     WinGranularity: 64
[   145.466]     WinSize: 64
[   145.466]     WinASegment: 0xa000
[   145.466]     WinBSegment: 0x0
[   145.466]     WinFuncPtr: 0xc0005237
[   145.466]     BytesPerScanline: 640
[   145.466]     XResolution: 320
[   145.466]     YResolution: 200
[   145.466]     XCharSize: 8
[   145.466]     YCharSize: 8
[   145.466]     NumberOfPlanes: 1
[   145.466]     BitsPerPixel: 16
[   145.466]     NumberOfBanks: 1
[   145.466]     MemoryModel: 6
[   145.466]     BankSize: 0
[   145.466]     NumberOfImages: 127
[   145.466]     RedMaskSize: 5
[   145.466]     RedFieldPosition: 11
[   145.466]     GreenMaskSize: 6
[   145.466]     GreenFieldPosition: 5
[   145.466]     BlueMaskSize: 5
[   145.466]     BlueFieldPosition: 0
[   145.466]     RsvdMaskSize: 0
[   145.466]     RsvdFieldPosition: 0
[   145.466]     DirectColorModeInfo: 0
[   145.466]     PhysBasePtr: 0xf0000000
[   145.466]     LinBytesPerScanLine: 640
[   145.466]     BnkNumberOfImagePages: 127
[   145.466]     LinNumberOfImagePages: 127
[   145.466]     LinRedMaskSize: 5
[   145.466]     LinRedFieldPosition: 11
[   145.466]     LinGreenMaskSize: 6
[   145.466]     LinGreenFieldPosition: 5
[   145.466]     LinBlueMaskSize: 5
[   145.466]     LinBlueFieldPosition: 0
[   145.466]     LinRsvdMaskSize: 0
[   145.466]     LinRsvdFieldPosition: 0
[   145.466]     MaxPixelClock: 400000000
[   145.467] *Mode: 120 (320x200)
[   145.467]     ModeAttributes: 0xbb
[   145.467]     WinAAttributes: 0x7
[   145.467]     WinBAttributes: 0x0
[   145.467]     WinGranularity: 64
[   145.467]     WinSize: 64
[   145.467]     WinASegment: 0xa000
[   145.467]     WinBSegment: 0x0
[   145.467]     WinFuncPtr: 0xc0005237
[   145.467]     BytesPerScanline: 1280
[   145.467]     XResolution: 320
[   145.467]     YResolution: 200
[   145.467]     XCharSize: 8
[   145.467]     YCharSize: 8
[   145.467]     NumberOfPlanes: 1
[   145.467]     BitsPerPixel: 32
[   145.467]     NumberOfBanks: 1
[   145.467]     MemoryModel: 6
[   145.467]     BankSize: 0
[   145.467]     NumberOfImages: 63
[   145.467]     RedMaskSize: 8
[   145.467]     RedFieldPosition: 16
[   145.467]     GreenMaskSize: 8
[   145.467]     GreenFieldPosition: 8
[   145.467]     BlueMaskSize: 8
[   145.467]     BlueFieldPosition: 0
[   145.467]     RsvdMaskSize: 0
[   145.467]     RsvdFieldPosition: 0
[   145.467]     DirectColorModeInfo: 0
[   145.467]     PhysBasePtr: 0xf0000000
[   145.467]     LinBytesPerScanLine: 1280
[   145.467]     BnkNumberOfImagePages: 63
[   145.467]     LinNumberOfImagePages: 63
[   145.467]     LinRedMaskSize: 8
[   145.467]     LinRedFieldPosition: 16
[   145.467]     LinGreenMaskSize: 8
[   145.467]     LinGreenFieldPosition: 8
[   145.467]     LinBlueMaskSize: 8
[   145.467]     LinBlueFieldPosition: 0
[   145.467]     LinRsvdMaskSize: 0
[   145.467]     LinRsvdFieldPosition: 0
[   145.467]     MaxPixelClock: 400000000
[   145.467] Mode: 193 (320x240)
[   145.467]     ModeAttributes: 0xbb
[   145.467]     WinAAttributes: 0x7
[   145.467]     WinBAttributes: 0x0
[   145.467]     WinGranularity: 64
[   145.467]     WinSize: 64
[   145.467]     WinASegment: 0xa000
[   145.467]     WinBSegment: 0x0
[   145.467]     WinFuncPtr: 0xc0005237
[   145.467]     BytesPerScanline: 320
[   145.467]     XResolution: 320
[   145.467]     YResolution: 240
[   145.467]     XCharSize: 8
[   145.467]     YCharSize: 8
[   145.467]     NumberOfPlanes: 1
[   145.467]     BitsPerPixel: 8
[   145.467]     NumberOfBanks: 1
[   145.467]     MemoryModel: 4
[   145.467]     BankSize: 0
[   145.467]     NumberOfImages: 127
[   145.467]     RedMaskSize: 0
[   145.467]     RedFieldPosition: 0
[   145.467]     GreenMaskSize: 0
[   145.467]     GreenFieldPosition: 0
[   145.467]     BlueMaskSize: 0
[   145.467]     BlueFieldPosition: 0
[   145.467]     RsvdMaskSize: 0
[   145.467]     RsvdFieldPosition: 0
[   145.467]     DirectColorModeInfo: 0
[   145.467]     PhysBasePtr: 0xf0000000
[   145.467]     LinBytesPerScanLine: 320
[   145.467]     BnkNumberOfImagePages: 127
[   145.467]     LinNumberOfImagePages: 127
[   145.467]     LinRedMaskSize: 0
[   145.468]     LinRedFieldPosition: 0
[   145.468]     LinGreenMaskSize: 0
[   145.468]     LinGreenFieldPosition: 0
[   145.468]     LinBlueMaskSize: 0
[   145.468]     LinBlueFieldPosition: 0
[   145.468]     LinRsvdMaskSize: 0
[   145.468]     LinRsvdFieldPosition: 0
[   145.468]     MaxPixelClock: 400000000
[   145.468] Mode: 195 (320x240)
[   145.468]     ModeAttributes: 0xbb
[   145.468]     WinAAttributes: 0x7
[   145.468]     WinBAttributes: 0x0
[   145.468]     WinGranularity: 64
[   145.468]     WinSize: 64
[   145.468]     WinASegment: 0xa000
[   145.468]     WinBSegment: 0x0
[   145.468]     WinFuncPtr: 0xc0005237
[   145.468]     BytesPerScanline: 640
[   145.468]     XResolution: 320
[   145.468]     YResolution: 240
[   145.468]     XCharSize: 8
[   145.468]     YCharSize: 8
[   145.468]     NumberOfPlanes: 1
[   145.468]     BitsPerPixel: 16
[   145.468]     NumberOfBanks: 1
[   145.468]     MemoryModel: 6
[   145.468]     BankSize: 0
[   145.468]     NumberOfImages: 84
[   145.468]     RedMaskSize: 5
[   145.468]     RedFieldPosition: 11
[   145.468]     GreenMaskSize: 6
[   145.468]     GreenFieldPosition: 5
[   145.468]     BlueMaskSize: 5
[   145.468]     BlueFieldPosition: 0
[   145.468]     RsvdMaskSize: 0
[   145.468]     RsvdFieldPosition: 0
[   145.468]     DirectColorModeInfo: 0
[   145.468]     PhysBasePtr: 0xf0000000
[   145.468]     LinBytesPerScanLine: 640
[   145.468]     BnkNumberOfImagePages: 84
[   145.468]     LinNumberOfImagePages: 84
[   145.468]     LinRedMaskSize: 5
[   145.468]     LinRedFieldPosition: 11
[   145.468]     LinGreenMaskSize: 6
[   145.468]     LinGreenFieldPosition: 5
[   145.468]     LinBlueMaskSize: 5
[   145.468]     LinBlueFieldPosition: 0
[   145.468]     LinRsvdMaskSize: 0
[   145.468]     LinRsvdFieldPosition: 0
[   145.468]     MaxPixelClock: 400000000
[   145.469] *Mode: 196 (320x240)
[   145.469]     ModeAttributes: 0xbb
[   145.469]     WinAAttributes: 0x7
[   145.469]     WinBAttributes: 0x0
[   145.469]     WinGranularity: 64
[   145.469]     WinSize: 64
[   145.469]     WinASegment: 0xa000
[   145.469]     WinBSegment: 0x0
[   145.469]     WinFuncPtr: 0xc0005237
[   145.469]     BytesPerScanline: 1280
[   145.469]     XResolution: 320
[   145.469]     YResolution: 240
[   145.469]     XCharSize: 8
[   145.469]     YCharSize: 8
[   145.469]     NumberOfPlanes: 1
[   145.469]     BitsPerPixel: 32
[   145.469]     NumberOfBanks: 1
[   145.469]     MemoryModel: 6
[   145.469]     BankSize: 0
[   145.469]     NumberOfImages: 50
[   145.469]     RedMaskSize: 8
[   145.469]     RedFieldPosition: 16
[   145.469]     GreenMaskSize: 8
[   145.469]     GreenFieldPosition: 8
[   145.469]     BlueMaskSize: 8
[   145.469]     BlueFieldPosition: 0
[   145.469]     RsvdMaskSize: 0
[   145.469]     RsvdFieldPosition: 0
[   145.469]     DirectColorModeInfo: 0
[   145.469]     PhysBasePtr: 0xf0000000
[   145.469]     LinBytesPerScanLine: 1280
[   145.469]     BnkNumberOfImagePages: 50
[   145.469]     LinNumberOfImagePages: 50
[   145.469]     LinRedMaskSize: 8
[   145.469]     LinRedFieldPosition: 16
[   145.469]     LinGreenMaskSize: 8
[   145.469]     LinGreenFieldPosition: 8
[   145.469]     LinBlueMaskSize: 8
[   145.469]     LinBlueFieldPosition: 0
[   145.469]     LinRsvdMaskSize: 0
[   145.469]     LinRsvdFieldPosition: 0
[   145.469]     MaxPixelClock: 400000000
[   145.469] Mode: 1b3 (512x384)
[   145.469]     ModeAttributes: 0xbb
[   145.469]     WinAAttributes: 0x7
[   145.469]     WinBAttributes: 0x0
[   145.469]     WinGranularity: 64
[   145.469]     WinSize: 64
[   145.469]     WinASegment: 0xa000
[   145.469]     WinBSegment: 0x0
[   145.469]     WinFuncPtr: 0xc0005237
[   145.469]     BytesPerScanline: 512
[   145.469]     XResolution: 512
[   145.469]     YResolution: 384
[   145.469]     XCharSize: 8
[   145.469]     YCharSize: 16
[   145.469]     NumberOfPlanes: 1
[   145.469]     BitsPerPixel: 8
[   145.469]     NumberOfBanks: 1
[   145.469]     MemoryModel: 4
[   145.469]     BankSize: 0
[   145.469]     NumberOfImages: 63
[   145.469]     RedMaskSize: 0
[   145.469]     RedFieldPosition: 0
[   145.469]     GreenMaskSize: 0
[   145.469]     GreenFieldPosition: 0
[   145.469]     BlueMaskSize: 0
[   145.469]     BlueFieldPosition: 0
[   145.469]     RsvdMaskSize: 0
[   145.469]     RsvdFieldPosition: 0
[   145.469]     DirectColorModeInfo: 0
[   145.469]     PhysBasePtr: 0xf0000000
[   145.470]     LinBytesPerScanLine: 512
[   145.470]     BnkNumberOfImagePages: 63
[   145.470]     LinNumberOfImagePages: 63
[   145.470]     LinRedMaskSize: 0
[   145.470]     LinRedFieldPosition: 0
[   145.470]     LinGreenMaskSize: 0
[   145.470]     LinGreenFieldPosition: 0
[   145.470]     LinBlueMaskSize: 0
[   145.470]     LinBlueFieldPosition: 0
[   145.470]     LinRsvdMaskSize: 0
[   145.470]     LinRsvdFieldPosition: 0
[   145.470]     MaxPixelClock: 400000000
[   145.470] Mode: 1b5 (512x384)
[   145.470]     ModeAttributes: 0xbb
[   145.470]     WinAAttributes: 0x7
[   145.470]     WinBAttributes: 0x0
[   145.470]     WinGranularity: 64
[   145.470]     WinSize: 64
[   145.470]     WinASegment: 0xa000
[   145.470]     WinBSegment: 0x0
[   145.470]     WinFuncPtr: 0xc0005237
[   145.470]     BytesPerScanline: 1024
[   145.470]     XResolution: 512
[   145.470]     YResolution: 384
[   145.470]     XCharSize: 8
[   145.470]     YCharSize: 16
[   145.470]     NumberOfPlanes: 1
[   145.470]     BitsPerPixel: 16
[   145.470]     NumberOfBanks: 1
[   145.470]     MemoryModel: 6
[   145.470]     BankSize: 0
[   145.470]     NumberOfImages: 35
[   145.470]     RedMaskSize: 5
[   145.470]     RedFieldPosition: 11
[   145.470]     GreenMaskSize: 6
[   145.470]     GreenFieldPosition: 5
[   145.470]     BlueMaskSize: 5
[   145.470]     BlueFieldPosition: 0
[   145.470]     RsvdMaskSize: 0
[   145.470]     RsvdFieldPosition: 0
[   145.470]     DirectColorModeInfo: 0
[   145.470]     PhysBasePtr: 0xf0000000
[   145.470]     LinBytesPerScanLine: 1024
[   145.470]     BnkNumberOfImagePages: 35
[   145.470]     LinNumberOfImagePages: 35
[   145.470]     LinRedMaskSize: 5
[   145.470]     LinRedFieldPosition: 11
[   145.470]     LinGreenMaskSize: 6
[   145.470]     LinGreenFieldPosition: 5
[   145.470]     LinBlueMaskSize: 5
[   145.470]     LinBlueFieldPosition: 0
[   145.470]     LinRsvdMaskSize: 0
[   145.470]     LinRsvdFieldPosition: 0
[   145.470]     MaxPixelClock: 400000000
[   145.471] *Mode: 1b6 (512x384)
[   145.471]     ModeAttributes: 0xbb
[   145.471]     WinAAttributes: 0x7
[   145.471]     WinBAttributes: 0x0
[   145.471]     WinGranularity: 64
[   145.471]     WinSize: 64
[   145.471]     WinASegment: 0xa000
[   145.471]     WinBSegment: 0x0
[   145.471]     WinFuncPtr: 0xc0005237
[   145.471]     BytesPerScanline: 2048
[   145.471]     XResolution: 512
[   145.471]     YResolution: 384
[   145.471]     XCharSize: 8
[   145.471]     YCharSize: 16
[   145.471]     NumberOfPlanes: 1
[   145.471]     BitsPerPixel: 32
[   145.471]     NumberOfBanks: 1
[   145.471]     MemoryModel: 6
[   145.471]     BankSize: 0
[   145.471]     NumberOfImages: 18
[   145.471]     RedMaskSize: 8
[   145.471]     RedFieldPosition: 16
[   145.471]     GreenMaskSize: 8
[   145.471]     GreenFieldPosition: 8
[   145.471]     BlueMaskSize: 8
[   145.471]     BlueFieldPosition: 0
[   145.471]     RsvdMaskSize: 0
[   145.471]     RsvdFieldPosition: 0
[   145.471]     DirectColorModeInfo: 0
[   145.471]     PhysBasePtr: 0xf0000000
[   145.471]     LinBytesPerScanLine: 2048
[   145.471]     BnkNumberOfImagePages: 18
[   145.471]     LinNumberOfImagePages: 18
[   145.471]     LinRedMaskSize: 8
[   145.471]     LinRedFieldPosition: 16
[   145.471]     LinGreenMaskSize: 8
[   145.471]     LinGreenFieldPosition: 8
[   145.471]     LinBlueMaskSize: 8
[   145.471]     LinBlueFieldPosition: 0
[   145.471]     LinRsvdMaskSize: 0
[   145.471]     LinRsvdFieldPosition: 0
[   145.471]     MaxPixelClock: 400000000
[   145.471] Mode: 1c3 (640x350)
[   145.471]     ModeAttributes: 0xbb
[   145.471]     WinAAttributes: 0x7
[   145.471]     WinBAttributes: 0x0
[   145.471]     WinGranularity: 64
[   145.471]     WinSize: 64
[   145.471]     WinASegment: 0xa000
[   145.471]     WinBSegment: 0x0
[   145.471]     WinFuncPtr: 0xc0005237
[   145.471]     BytesPerScanline: 640
[   145.471]     XResolution: 640
[   145.471]     YResolution: 350
[   145.471]     XCharSize: 8
[   145.471]     YCharSize: 14
[   145.471]     NumberOfPlanes: 1
[   145.471]     BitsPerPixel: 8
[   145.471]     NumberOfBanks: 1
[   145.471]     MemoryModel: 4
[   145.471]     BankSize: 0
[   145.471]     NumberOfImages: 63
[   145.471]     RedMaskSize: 0
[   145.471]     RedFieldPosition: 0
[   145.471]     GreenMaskSize: 0
[   145.471]     GreenFieldPosition: 0
[   145.471]     BlueMaskSize: 0
[   145.471]     BlueFieldPosition: 0
[   145.471]     RsvdMaskSize: 0
[   145.471]     RsvdFieldPosition: 0
[   145.471]     DirectColorModeInfo: 0
[   145.472]     PhysBasePtr: 0xf0000000
[   145.472]     LinBytesPerScanLine: 640
[   145.472]     BnkNumberOfImagePages: 63
[   145.472]     LinNumberOfImagePages: 63
[   145.472]     LinRedMaskSize: 0
[   145.472]     LinRedFieldPosition: 0
[   145.472]     LinGreenMaskSize: 0
[   145.472]     LinGreenFieldPosition: 0
[   145.472]     LinBlueMaskSize: 0
[   145.472]     LinBlueFieldPosition: 0
[   145.472]     LinRsvdMaskSize: 0
[   145.472]     LinRsvdFieldPosition: 0
[   145.472]     MaxPixelClock: 400000000
[   145.472] Mode: 1c5 (640x350)
[   145.472]     ModeAttributes: 0xbb
[   145.472]     WinAAttributes: 0x7
[   145.472]     WinBAttributes: 0x0
[   145.472]     WinGranularity: 64
[   145.472]     WinSize: 64
[   145.472]     WinASegment: 0xa000
[   145.472]     WinBSegment: 0x0
[   145.472]     WinFuncPtr: 0xc0005237
[   145.472]     BytesPerScanline: 1280
[   145.472]     XResolution: 640
[   145.472]     YResolution: 350
[   145.472]     XCharSize: 8
[   145.472]     YCharSize: 14
[   145.472]     NumberOfPlanes: 1
[   145.472]     BitsPerPixel: 16
[   145.472]     NumberOfBanks: 1
[   145.472]     MemoryModel: 6
[   145.472]     BankSize: 0
[   145.472]     NumberOfImages: 35
[   145.472]     RedMaskSize: 5
[   145.472]     RedFieldPosition: 11
[   145.472]     GreenMaskSize: 6
[   145.472]     GreenFieldPosition: 5
[   145.472]     BlueMaskSize: 5
[   145.472]     BlueFieldPosition: 0
[   145.472]     RsvdMaskSize: 0
[   145.472]     RsvdFieldPosition: 0
[   145.472]     DirectColorModeInfo: 0
[   145.472]     PhysBasePtr: 0xf0000000
[   145.472]     LinBytesPerScanLine: 1280
[   145.472]     BnkNumberOfImagePages: 35
[   145.472]     LinNumberOfImagePages: 35
[   145.472]     LinRedMaskSize: 5
[   145.472]     LinRedFieldPosition: 11
[   145.472]     LinGreenMaskSize: 6
[   145.472]     LinGreenFieldPosition: 5
[   145.472]     LinBlueMaskSize: 5
[   145.472]     LinBlueFieldPosition: 0
[   145.472]     LinRsvdMaskSize: 0
[   145.472]     LinRsvdFieldPosition: 0
[   145.472]     MaxPixelClock: 400000000
[   145.473] *Mode: 1c6 (640x350)
[   145.473]     ModeAttributes: 0xbb
[   145.473]     WinAAttributes: 0x7
[   145.473]     WinBAttributes: 0x0
[   145.473]     WinGranularity: 64
[   145.473]     WinSize: 64
[   145.473]     WinASegment: 0xa000
[   145.473]     WinBSegment: 0x0
[   145.473]     WinFuncPtr: 0xc0005237
[   145.473]     BytesPerScanline: 2560
[   145.473]     XResolution: 640
[   145.473]     YResolution: 350
[   145.473]     XCharSize: 8
[   145.473]     YCharSize: 14
[   145.473]     NumberOfPlanes: 1
[   145.473]     BitsPerPixel: 32
[   145.473]     NumberOfBanks: 1
[   145.473]     MemoryModel: 6
[   145.473]     BankSize: 0
[   145.473]     NumberOfImages: 17
[   145.473]     RedMaskSize: 8
[   145.473]     RedFieldPosition: 16
[   145.473]     GreenMaskSize: 8
[   145.473]     GreenFieldPosition: 8
[   145.473]     BlueMaskSize: 8
[   145.473]     BlueFieldPosition: 0
[   145.473]     RsvdMaskSize: 0
[   145.473]     RsvdFieldPosition: 0
[   145.473]     DirectColorModeInfo: 0
[   145.473]     PhysBasePtr: 0xf0000000
[   145.473]     LinBytesPerScanLine: 2560
[   145.473]     BnkNumberOfImagePages: 17
[   145.473]     LinNumberOfImagePages: 17
[   145.473]     LinRedMaskSize: 8
[   145.473]     LinRedFieldPosition: 16
[   145.473]     LinGreenMaskSize: 8
[   145.473]     LinGreenFieldPosition: 8
[   145.473]     LinBlueMaskSize: 8
[   145.473]     LinBlueFieldPosition: 0
[   145.473]     LinRsvdMaskSize: 0
[   145.473]     LinRsvdFieldPosition: 0
[   145.473]     MaxPixelClock: 400000000
[   145.473] Mode: 183 (640x400)
[   145.473]     ModeAttributes: 0xbb
[   145.473]     WinAAttributes: 0x7
[   145.473]     WinBAttributes: 0x0
[   145.473]     WinGranularity: 64
[   145.473]     WinSize: 64
[   145.473]     WinASegment: 0xa000
[   145.473]     WinBSegment: 0x0
[   145.473]     WinFuncPtr: 0xc0005237
[   145.473]     BytesPerScanline: 640
[   145.473]     XResolution: 640
[   145.473]     YResolution: 400
[   145.473]     XCharSize: 8
[   145.473]     YCharSize: 16
[   145.473]     NumberOfPlanes: 1
[   145.473]     BitsPerPixel: 8
[   145.473]     NumberOfBanks: 1
[   145.473]     MemoryModel: 4
[   145.473]     BankSize: 0
[   145.474]     NumberOfImages: 63
[   145.474]     RedMaskSize: 0
[   145.474]     RedFieldPosition: 0
[   145.474]     GreenMaskSize: 0
[   145.474]     GreenFieldPosition: 0
[   145.474]     BlueMaskSize: 0
[   145.474]     BlueFieldPosition: 0
[   145.474]     RsvdMaskSize: 0
[   145.474]     RsvdFieldPosition: 0
[   145.474]     DirectColorModeInfo: 0
[   145.474]     PhysBasePtr: 0xf0000000
[   145.474]     LinBytesPerScanLine: 640
[   145.474]     BnkNumberOfImagePages: 63
[   145.474]     LinNumberOfImagePages: 63
[   145.474]     LinRedMaskSize: 0
[   145.474]     LinRedFieldPosition: 0
[   145.474]     LinGreenMaskSize: 0
[   145.474]     LinGreenFieldPosition: 0
[   145.474]     LinBlueMaskSize: 0
[   145.474]     LinBlueFieldPosition: 0
[   145.474]     LinRsvdMaskSize: 0
[   145.474]     LinRsvdFieldPosition: 0
[   145.474]     MaxPixelClock: 400000000
[   145.474] Mode: 185 (640x400)
[   145.474]     ModeAttributes: 0xbb
[   145.474]     WinAAttributes: 0x7
[   145.474]     WinBAttributes: 0x0
[   145.474]     WinGranularity: 64
[   145.474]     WinSize: 64
[   145.474]     WinASegment: 0xa000
[   145.474]     WinBSegment: 0x0
[   145.474]     WinFuncPtr: 0xc0005237
[   145.474]     BytesPerScanline: 1280
[   145.474]     XResolution: 640
[   145.474]     YResolution: 400
[   145.474]     XCharSize: 8
[   145.474]     YCharSize: 16
[   145.474]     NumberOfPlanes: 1
[   145.474]     BitsPerPixel: 16
[   145.474]     NumberOfBanks: 1
[   145.474]     MemoryModel: 6
[   145.474]     BankSize: 0
[   145.474]     NumberOfImages: 31
[   145.474]     RedMaskSize: 5
[   145.474]     RedFieldPosition: 11
[   145.474]     GreenMaskSize: 6
[   145.474]     GreenFieldPosition: 5
[   145.474]     BlueMaskSize: 5
[   145.474]     BlueFieldPosition: 0
[   145.474]     RsvdMaskSize: 0
[   145.474]     RsvdFieldPosition: 0
[   145.474]     DirectColorModeInfo: 0
[   145.474]     PhysBasePtr: 0xf0000000
[   145.474]     LinBytesPerScanLine: 1280
[   145.474]     BnkNumberOfImagePages: 31
[   145.474]     LinNumberOfImagePages: 31
[   145.474]     LinRedMaskSize: 5
[   145.474]     LinRedFieldPosition: 11
[   145.474]     LinGreenMaskSize: 6
[   145.474]     LinGreenFieldPosition: 5
[   145.474]     LinBlueMaskSize: 5
[   145.474]     LinBlueFieldPosition: 0
[   145.474]     LinRsvdMaskSize: 0
[   145.474]     LinRsvdFieldPosition: 0
[   145.474]     MaxPixelClock: 400000000
[   145.475] *Mode: 186 (640x400)
[   145.475]     ModeAttributes: 0xbb
[   145.475]     WinAAttributes: 0x7
[   145.475]     WinBAttributes: 0x0
[   145.475]     WinGranularity: 64
[   145.475]     WinSize: 64
[   145.475]     WinASegment: 0xa000
[   145.475]     WinBSegment: 0x0
[   145.475]     WinFuncPtr: 0xc0005237
[   145.475]     BytesPerScanline: 2560
[   145.475]     XResolution: 640
[   145.475]     YResolution: 400
[   145.475]     XCharSize: 8
[   145.475]     YCharSize: 16
[   145.475]     NumberOfPlanes: 1
[   145.475]     BitsPerPixel: 32
[   145.475]     NumberOfBanks: 1
[   145.475]     MemoryModel: 6
[   145.475]     BankSize: 0
[   145.475]     NumberOfImages: 15
[   145.475]     RedMaskSize: 8
[   145.475]     RedFieldPosition: 16
[   145.475]     GreenMaskSize: 8
[   145.475]     GreenFieldPosition: 8
[   145.475]     BlueMaskSize: 8
[   145.475]     BlueFieldPosition: 0
[   145.475]     RsvdMaskSize: 0
[   145.475]     RsvdFieldPosition: 0
[   145.475]     DirectColorModeInfo: 0
[   145.475]     PhysBasePtr: 0xf0000000
[   145.475]     LinBytesPerScanLine: 2560
[   145.475]     BnkNumberOfImagePages: 15
[   145.475]     LinNumberOfImagePages: 15
[   145.475]     LinRedMaskSize: 8
[   145.475]     LinRedFieldPosition: 16
[   145.475]     LinGreenMaskSize: 8
[   145.475]     LinGreenFieldPosition: 8
[   145.475]     LinBlueMaskSize: 8
[   145.475]     LinBlueFieldPosition: 0
[   145.475]     LinRsvdMaskSize: 0
[   145.475]     LinRsvdFieldPosition: 0
[   145.475]     MaxPixelClock: 400000000
[   145.475] Mode: 133 (720x400)
[   145.475]     ModeAttributes: 0xbb
[   145.475]     WinAAttributes: 0x7
[   145.475]     WinBAttributes: 0x0
[   145.475]     WinGranularity: 64
[   145.475]     WinSize: 64
[   145.475]     WinASegment: 0xa000
[   145.475]     WinBSegment: 0x0
[   145.475]     WinFuncPtr: 0xc0005237
[   145.476]     BytesPerScanline: 768
[   145.476]     XResolution: 720
[   145.476]     YResolution: 400
[   145.476]     XCharSize: 8
[   145.476]     YCharSize: 16
[   145.476]     NumberOfPlanes: 1
[   145.476]     BitsPerPixel: 8
[   145.476]     NumberOfBanks: 1
[   145.476]     MemoryModel: 4
[   145.476]     BankSize: 0
[   145.476]     NumberOfImages: 50
[   145.476]     RedMaskSize: 0
[   145.476]     RedFieldPosition: 0
[   145.476]     GreenMaskSize: 0
[   145.476]     GreenFieldPosition: 0
[   145.476]     BlueMaskSize: 0
[   145.476]     BlueFieldPosition: 0
[   145.476]     RsvdMaskSize: 0
[   145.476]     RsvdFieldPosition: 0
[   145.476]     DirectColorModeInfo: 0
[   145.476]     PhysBasePtr: 0xf0000000
[   145.476]     LinBytesPerScanLine: 768
[   145.476]     BnkNumberOfImagePages: 50
[   145.476]     LinNumberOfImagePages: 50
[   145.476]     LinRedMaskSize: 0
[   145.476]     LinRedFieldPosition: 0
[   145.476]     LinGreenMaskSize: 0
[   145.476]     LinGreenFieldPosition: 0
[   145.476]     LinBlueMaskSize: 0
[   145.476]     LinBlueFieldPosition: 0
[   145.476]     LinRsvdMaskSize: 0
[   145.476]     LinRsvdFieldPosition: 0
[   145.476]     MaxPixelClock: 400000000
[   145.476] Mode: 135 (720x400)
[   145.476]     ModeAttributes: 0xbb
[   145.476]     WinAAttributes: 0x7
[   145.476]     WinBAttributes: 0x0
[   145.476]     WinGranularity: 64
[   145.476]     WinSize: 64
[   145.476]     WinASegment: 0xa000
[   145.476]     WinBSegment: 0x0
[   145.476]     WinFuncPtr: 0xc0005237
[   145.476]     BytesPerScanline: 1472
[   145.476]     XResolution: 720
[   145.476]     YResolution: 400
[   145.476]     XCharSize: 8
[   145.476]     YCharSize: 16
[   145.476]     NumberOfPlanes: 1
[   145.476]     BitsPerPixel: 16
[   145.476]     NumberOfBanks: 1
[   145.476]     MemoryModel: 6
[   145.476]     BankSize: 0
[   145.476]     NumberOfImages: 27
[   145.476]     RedMaskSize: 5
[   145.476]     RedFieldPosition: 11
[   145.476]     GreenMaskSize: 6
[   145.476]     GreenFieldPosition: 5
[   145.476]     BlueMaskSize: 5
[   145.476]     BlueFieldPosition: 0
[   145.476]     RsvdMaskSize: 0
[   145.476]     RsvdFieldPosition: 0
[   145.476]     DirectColorModeInfo: 0
[   145.476]     PhysBasePtr: 0xf0000000
[   145.476]     LinBytesPerScanLine: 1472
[   145.476]     BnkNumberOfImagePages: 27
[   145.476]     LinNumberOfImagePages: 27
[   145.476]     LinRedMaskSize: 5
[   145.476]     LinRedFieldPosition: 11
[   145.476]     LinGreenMaskSize: 6
[   145.476]     LinGreenFieldPosition: 5
[   145.476]     LinBlueMaskSize: 5
[   145.476]     LinBlueFieldPosition: 0
[   145.476]     LinRsvdMaskSize: 0
[   145.476]     LinRsvdFieldPosition: 0
[   145.476]     MaxPixelClock: 400000000
[   145.477] *Mode: 136 (720x400)
[   145.477]     ModeAttributes: 0xbb
[   145.477]     WinAAttributes: 0x7
[   145.477]     WinBAttributes: 0x0
[   145.477]     WinGranularity: 64
[   145.477]     WinSize: 64
[   145.477]     WinASegment: 0xa000
[   145.477]     WinBSegment: 0x0
[   145.477]     WinFuncPtr: 0xc0005237
[   145.477]     BytesPerScanline: 2944
[   145.477]     XResolution: 720
[   145.477]     YResolution: 400
[   145.477]     XCharSize: 8
[   145.477]     YCharSize: 16
[   145.477]     NumberOfPlanes: 1
[   145.477]     BitsPerPixel: 32
[   145.477]     NumberOfBanks: 1
[   145.477]     MemoryModel: 6
[   145.477]     BankSize: 0
[   145.477]     NumberOfImages: 13
[   145.477]     RedMaskSize: 8
[   145.477]     RedFieldPosition: 16
[   145.477]     GreenMaskSize: 8
[   145.477]     GreenFieldPosition: 8
[   145.477]     BlueMaskSize: 8
[   145.477]     BlueFieldPosition: 0
[   145.477]     RsvdMaskSize: 0
[   145.477]     RsvdFieldPosition: 0
[   145.477]     DirectColorModeInfo: 0
[   145.477]     PhysBasePtr: 0xf0000000
[   145.477]     LinBytesPerScanLine: 2944
[   145.477]     BnkNumberOfImagePages: 13
[   145.477]     LinNumberOfImagePages: 13
[   145.477]     LinRedMaskSize: 8
[   145.477]     LinRedFieldPosition: 16
[   145.477]     LinGreenMaskSize: 8
[   145.477]     LinGreenFieldPosition: 8
[   145.477]     LinBlueMaskSize: 8
[   145.477]     LinBlueFieldPosition: 0
[   145.477]     LinRsvdMaskSize: 0
[   145.477]     LinRsvdFieldPosition: 0
[   145.477]     MaxPixelClock: 400000000
[   145.478] Mode: 153 (1152x864)
[   145.478]     ModeAttributes: 0xbb
[   145.478]     WinAAttributes: 0x7
[   145.478]     WinBAttributes: 0x0
[   145.478]     WinGranularity: 64
[   145.478]     WinSize: 64
[   145.478]     WinASegment: 0xa000
[   145.478]     WinBSegment: 0x0
[   145.478]     WinFuncPtr: 0xc0005237
[   145.478]     BytesPerScanline: 1152
[   145.478]     XResolution: 1152
[   145.478]     YResolution: 864
[   145.478]     XCharSize: 8
[   145.478]     YCharSize: 16
[   145.478]     NumberOfPlanes: 1
[   145.478]     BitsPerPixel: 8
[   145.478]     NumberOfBanks: 1
[   145.478]     MemoryModel: 4
[   145.478]     BankSize: 0
[   145.478]     NumberOfImages: 15
[   145.478]     RedMaskSize: 0
[   145.478]     RedFieldPosition: 0
[   145.478]     GreenMaskSize: 0
[   145.478]     GreenFieldPosition: 0
[   145.478]     BlueMaskSize: 0
[   145.478]     BlueFieldPosition: 0
[   145.478]     RsvdMaskSize: 0
[   145.478]     RsvdFieldPosition: 0
[   145.478]     DirectColorModeInfo: 0
[   145.478]     PhysBasePtr: 0xf0000000
[   145.478]     LinBytesPerScanLine: 1152
[   145.478]     BnkNumberOfImagePages: 15
[   145.478]     LinNumberOfImagePages: 15
[   145.478]     LinRedMaskSize: 0
[   145.478]     LinRedFieldPosition: 0
[   145.478]     LinGreenMaskSize: 0
[   145.478]     LinGreenFieldPosition: 0
[   145.478]     LinBlueMaskSize: 0
[   145.478]     LinBlueFieldPosition: 0
[   145.478]     LinRsvdMaskSize: 0
[   145.478]     LinRsvdFieldPosition: 0
[   145.478]     MaxPixelClock: 400000000
[   145.478] Mode: 155 (1152x864)
[   145.478]     ModeAttributes: 0xbb
[   145.478]     WinAAttributes: 0x7
[   145.478]     WinBAttributes: 0x0
[   145.478]     WinGranularity: 64
[   145.478]     WinSize: 64
[   145.478]     WinASegment: 0xa000
[   145.478]     WinBSegment: 0x0
[   145.478]     WinFuncPtr: 0xc0005237
[   145.478]     BytesPerScanline: 2304
[   145.478]     XResolution: 1152
[   145.478]     YResolution: 864
[   145.478]     XCharSize: 8
[   145.478]     YCharSize: 16
[   145.478]     NumberOfPlanes: 1
[   145.478]     BitsPerPixel: 16
[   145.478]     NumberOfBanks: 1
[   145.478]     MemoryModel: 6
[   145.478]     BankSize: 0
[   145.478]     NumberOfImages: 7
[   145.478]     RedMaskSize: 5
[   145.478]     RedFieldPosition: 11
[   145.478]     GreenMaskSize: 6
[   145.478]     GreenFieldPosition: 5
[   145.478]     BlueMaskSize: 5
[   145.478]     BlueFieldPosition: 0
[   145.478]     RsvdMaskSize: 0
[   145.478]     RsvdFieldPosition: 0
[   145.479]     DirectColorModeInfo: 0
[   145.479]     PhysBasePtr: 0xf0000000
[   145.479]     LinBytesPerScanLine: 2304
[   145.479]     BnkNumberOfImagePages: 7
[   145.479]     LinNumberOfImagePages: 7
[   145.479]     LinRedMaskSize: 5
[   145.479]     LinRedFieldPosition: 11
[   145.479]     LinGreenMaskSize: 6
[   145.479]     LinGreenFieldPosition: 5
[   145.479]     LinBlueMaskSize: 5
[   145.479]     LinBlueFieldPosition: 0
[   145.479]     LinRsvdMaskSize: 0
[   145.479]     LinRsvdFieldPosition: 0
[   145.479]     MaxPixelClock: 400000000
[   145.479] *Mode: 156 (1152x864)
[   145.479]     ModeAttributes: 0xbb
[   145.479]     WinAAttributes: 0x7
[   145.479]     WinBAttributes: 0x0
[   145.479]     WinGranularity: 64
[   145.479]     WinSize: 64
[   145.479]     WinASegment: 0xa000
[   145.479]     WinBSegment: 0x0
[   145.479]     WinFuncPtr: 0xc0005237
[   145.479]     BytesPerScanline: 4608
[   145.479]     XResolution: 1152
[   145.479]     YResolution: 864
[   145.479]     XCharSize: 8
[   145.479]     YCharSize: 16
[   145.479]     NumberOfPlanes: 1
[   145.479]     BitsPerPixel: 32
[   145.479]     NumberOfBanks: 1
[   145.479]     MemoryModel: 6
[   145.479]     BankSize: 0
[   145.479]     NumberOfImages: 3
[   145.479]     RedMaskSize: 8
[   145.479]     RedFieldPosition: 16
[   145.479]     GreenMaskSize: 8
[   145.479]     GreenFieldPosition: 8
[   145.479]     BlueMaskSize: 8
[   145.479]     BlueFieldPosition: 0
[   145.479]     RsvdMaskSize: 0
[   145.479]     RsvdFieldPosition: 0
[   145.479]     DirectColorModeInfo: 0
[   145.479]     PhysBasePtr: 0xf0000000
[   145.479]     LinBytesPerScanLine: 4608
[   145.479]     BnkNumberOfImagePages: 3
[   145.479]     LinNumberOfImagePages: 3
[   145.479]     LinRedMaskSize: 8
[   145.479]     LinRedFieldPosition: 16
[   145.479]     LinGreenMaskSize: 8
[   145.479]     LinGreenFieldPosition: 8
[   145.479]     LinBlueMaskSize: 8
[   145.479]     LinBlueFieldPosition: 0
[   145.479]     LinRsvdMaskSize: 0
[   145.479]     LinRsvdFieldPosition: 0
[   145.479]     MaxPixelClock: 400000000
[   145.480] Mode: 163 (1280x1024)
[   145.480]     ModeAttributes: 0xbb
[   145.480]     WinAAttributes: 0x7
[   145.480]     WinBAttributes: 0x0
[   145.480]     WinGranularity: 64
[   145.480]     WinSize: 64
[   145.480]     WinASegment: 0xa000
[   145.480]     WinBSegment: 0x0
[   145.480]     WinFuncPtr: 0xc0005237
[   145.480]     BytesPerScanline: 1280
[   145.480]     XResolution: 1280
[   145.480]     YResolution: 1024
[   145.480]     XCharSize: 8
[   145.480]     YCharSize: 16
[   145.480]     NumberOfPlanes: 1
[   145.480]     BitsPerPixel: 8
[   145.480]     NumberOfBanks: 1
[   145.480]     MemoryModel: 4
[   145.480]     BankSize: 0
[   145.480]     NumberOfImages: 11
[   145.480]     RedMaskSize: 0
[   145.480]     RedFieldPosition: 0
[   145.480]     GreenMaskSize: 0
[   145.480]     GreenFieldPosition: 0
[   145.480]     BlueMaskSize: 0
[   145.480]     BlueFieldPosition: 0
[   145.480]     RsvdMaskSize: 0
[   145.480]     RsvdFieldPosition: 0
[   145.480]     DirectColorModeInfo: 0
[   145.480]     PhysBasePtr: 0xf0000000
[   145.480]     LinBytesPerScanLine: 1280
[   145.480]     BnkNumberOfImagePages: 11
[   145.480]     LinNumberOfImagePages: 11
[   145.480]     LinRedMaskSize: 0
[   145.480]     LinRedFieldPosition: 0
[   145.480]     LinGreenMaskSize: 0
[   145.480]     LinGreenFieldPosition: 0
[   145.480]     LinBlueMaskSize: 0
[   145.480]     LinBlueFieldPosition: 0
[   145.480]     LinRsvdMaskSize: 0
[   145.480]     LinRsvdFieldPosition: 0
[   145.480]     MaxPixelClock: 400000000
[   145.481] Mode: 165 (1280x1024)
[   145.481]     ModeAttributes: 0xbb
[   145.481]     WinAAttributes: 0x7
[   145.481]     WinBAttributes: 0x0
[   145.481]     WinGranularity: 64
[   145.481]     WinSize: 64
[   145.481]     WinASegment: 0xa000
[   145.481]     WinBSegment: 0x0
[   145.481]     WinFuncPtr: 0xc0005237
[   145.481]     BytesPerScanline: 2560
[   145.481]     XResolution: 1280
[   145.481]     YResolution: 1024
[   145.481]     XCharSize: 8
[   145.481]     YCharSize: 16
[   145.481]     NumberOfPlanes: 1
[   145.481]     BitsPerPixel: 16
[   145.481]     NumberOfBanks: 1
[   145.481]     MemoryModel: 6
[   145.481]     BankSize: 0
[   145.481]     NumberOfImages: 5
[   145.481]     RedMaskSize: 5
[   145.481]     RedFieldPosition: 11
[   145.481]     GreenMaskSize: 6
[   145.481]     GreenFieldPosition: 5
[   145.481]     BlueMaskSize: 5
[   145.481]     BlueFieldPosition: 0
[   145.481]     RsvdMaskSize: 0
[   145.481]     RsvdFieldPosition: 0
[   145.481]     DirectColorModeInfo: 0
[   145.481]     PhysBasePtr: 0xf0000000
[   145.481]     LinBytesPerScanLine: 2560
[   145.481]     BnkNumberOfImagePages: 5
[   145.481]     LinNumberOfImagePages: 5
[   145.481]     LinRedMaskSize: 5
[   145.481]     LinRedFieldPosition: 11
[   145.481]     LinGreenMaskSize: 6
[   145.481]     LinGreenFieldPosition: 5
[   145.481]     LinBlueMaskSize: 5
[   145.481]     LinBlueFieldPosition: 0
[   145.481]     LinRsvdMaskSize: 0
[   145.481]     LinRsvdFieldPosition: 0
[   145.481]     MaxPixelClock: 400000000
[   145.481] *Mode: 166 (1280x1024)
[   145.481]     ModeAttributes: 0xbb
[   145.481]     WinAAttributes: 0x7
[   145.481]     WinBAttributes: 0x0
[   145.481]     WinGranularity: 64
[   145.481]     WinSize: 64
[   145.481]     WinASegment: 0xa000
[   145.481]     WinBSegment: 0x0
[   145.481]     WinFuncPtr: 0xc0005237
[   145.481]     BytesPerScanline: 5120
[   145.481]     XResolution: 1280
[   145.481]     YResolution: 1024
[   145.481]     XCharSize: 8
[   145.481]     YCharSize: 16
[   145.481]     NumberOfPlanes: 1
[   145.481]     BitsPerPixel: 32
[   145.481]     NumberOfBanks: 1
[   145.481]     MemoryModel: 6
[   145.481]     BankSize: 0
[   145.481]     NumberOfImages: 2
[   145.481]     RedMaskSize: 8
[   145.481]     RedFieldPosition: 16
[   145.481]     GreenMaskSize: 8
[   145.481]     GreenFieldPosition: 8
[   145.481]     BlueMaskSize: 8
[   145.481]     BlueFieldPosition: 0
[   145.481]     RsvdMaskSize: 0
[   145.481]     RsvdFieldPosition: 0
[   145.481]     DirectColorModeInfo: 0
[   145.481]     PhysBasePtr: 0xf0000000
[   145.481]     LinBytesPerScanLine: 5120
[   145.481]     BnkNumberOfImagePages: 2
[   145.481]     LinNumberOfImagePages: 2
[   145.481]     LinRedMaskSize: 8
[   145.482]     LinRedFieldPosition: 16
[   145.482]     LinGreenMaskSize: 8
[   145.482]     LinGreenFieldPosition: 8
[   145.482]     LinBlueMaskSize: 8
[   145.482]     LinBlueFieldPosition: 0
[   145.482]     LinRsvdMaskSize: 0
[   145.482]     LinRsvdFieldPosition: 0
[   145.482]     MaxPixelClock: 400000000
[   145.482] *Mode: 121 (640x480)
[   145.482]     ModeAttributes: 0xbb
[   145.482]     WinAAttributes: 0x7
[   145.482]     WinBAttributes: 0x0
[   145.482]     WinGranularity: 64
[   145.482]     WinSize: 64
[   145.482]     WinASegment: 0xa000
[   145.482]     WinBSegment: 0x0
[   145.482]     WinFuncPtr: 0xc0005237
[   145.482]     BytesPerScanline: 2560
[   145.482]     XResolution: 640
[   145.482]     YResolution: 480
[   145.482]     XCharSize: 8
[   145.482]     YCharSize: 16
[   145.482]     NumberOfPlanes: 1
[   145.482]     BitsPerPixel: 32
[   145.482]     NumberOfBanks: 1
[   145.482]     MemoryModel: 6
[   145.482]     BankSize: 0
[   145.482]     NumberOfImages: 12
[   145.482]     RedMaskSize: 8
[   145.482]     RedFieldPosition: 16
[   145.482]     GreenMaskSize: 8
[   145.482]     GreenFieldPosition: 8
[   145.482]     BlueMaskSize: 8
[   145.482]     BlueFieldPosition: 0
[   145.482]     RsvdMaskSize: 0
[   145.482]     RsvdFieldPosition: 0
[   145.482]     DirectColorModeInfo: 0
[   145.482]     PhysBasePtr: 0xf0000000
[   145.482]     LinBytesPerScanLine: 2560
[   145.482]     BnkNumberOfImagePages: 12
[   145.482]     LinNumberOfImagePages: 12
[   145.482]     LinRedMaskSize: 8
[   145.482]     LinRedFieldPosition: 16
[   145.482]     LinGreenMaskSize: 8
[   145.482]     LinGreenFieldPosition: 8
[   145.482]     LinBlueMaskSize: 8
[   145.482]     LinBlueFieldPosition: 0
[   145.482]     LinRsvdMaskSize: 0
[   145.482]     LinRsvdFieldPosition: 0
[   145.482]     MaxPixelClock: 400000000
[   145.483] *Mode: 122 (800x600)
[   145.483]     ModeAttributes: 0xbb
[   145.483]     WinAAttributes: 0x7
[   145.483]     WinBAttributes: 0x0
[   145.483]     WinGranularity: 64
[   145.483]     WinSize: 64
[   145.483]     WinASegment: 0xa000
[   145.483]     WinBSegment: 0x0
[   145.483]     WinFuncPtr: 0xc0005237
[   145.483]     BytesPerScanline: 3200
[   145.483]     XResolution: 800
[   145.483]     YResolution: 600
[   145.483]     XCharSize: 8
[   145.483]     YCharSize: 14
[   145.483]     NumberOfPlanes: 1
[   145.483]     BitsPerPixel: 32
[   145.483]     NumberOfBanks: 1
[   145.483]     MemoryModel: 6
[   145.483]     BankSize: 0
[   145.483]     NumberOfImages: 7
[   145.483]     RedMaskSize: 8
[   145.483]     RedFieldPosition: 16
[   145.483]     GreenMaskSize: 8
[   145.483]     GreenFieldPosition: 8
[   145.483]     BlueMaskSize: 8
[   145.483]     BlueFieldPosition: 0
[   145.483]     RsvdMaskSize: 0
[   145.483]     RsvdFieldPosition: 0
[   145.483]     DirectColorModeInfo: 0
[   145.483]     PhysBasePtr: 0xf0000000
[   145.483]     LinBytesPerScanLine: 3200
[   145.483]     BnkNumberOfImagePages: 7
[   145.483]     LinNumberOfImagePages: 7
[   145.483]     LinRedMaskSize: 8
[   145.483]     LinRedFieldPosition: 16
[   145.483]     LinGreenMaskSize: 8
[   145.483]     LinGreenFieldPosition: 8
[   145.483]     LinBlueMaskSize: 8
[   145.483]     LinBlueFieldPosition: 0
[   145.483]     LinRsvdMaskSize: 0
[   145.483]     LinRsvdFieldPosition: 0
[   145.483]     MaxPixelClock: 400000000
[   145.483] *Mode: 123 (1024x768)
[   145.483]     ModeAttributes: 0xbb
[   145.483]     WinAAttributes: 0x7
[   145.483]     WinBAttributes: 0x0
[   145.483]     WinGranularity: 64
[   145.483]     WinSize: 64
[   145.483]     WinASegment: 0xa000
[   145.483]     WinBSegment: 0x0
[   145.483]     WinFuncPtr: 0xc0005237
[   145.483]     BytesPerScanline: 4096
[   145.483]     XResolution: 1024
[   145.484]     YResolution: 768
[   145.484]     XCharSize: 8
[   145.484]     YCharSize: 16
[   145.484]     NumberOfPlanes: 1
[   145.484]     BitsPerPixel: 32
[   145.484]     NumberOfBanks: 1
[   145.484]     MemoryModel: 6
[   145.484]     BankSize: 0
[   145.484]     NumberOfImages: 4
[   145.484]     RedMaskSize: 8
[   145.484]     RedFieldPosition: 16
[   145.484]     GreenMaskSize: 8
[   145.484]     GreenFieldPosition: 8
[   145.484]     BlueMaskSize: 8
[   145.484]     BlueFieldPosition: 0
[   145.484]     RsvdMaskSize: 0
[   145.484]     RsvdFieldPosition: 0
[   145.484]     DirectColorModeInfo: 0
[   145.484]     PhysBasePtr: 0xf0000000
[   145.484]     LinBytesPerScanLine: 4096
[   145.484]     BnkNumberOfImagePages: 4
[   145.484]     LinNumberOfImagePages: 4
[   145.484]     LinRedMaskSize: 8
[   145.484]     LinRedFieldPosition: 16
[   145.484]     LinGreenMaskSize: 8
[   145.484]     LinGreenFieldPosition: 8
[   145.484]     LinBlueMaskSize: 8
[   145.484]     LinBlueFieldPosition: 0
[   145.484]     LinRsvdMaskSize: 0
[   145.484]     LinRsvdFieldPosition: 0
[   145.484]     MaxPixelClock: 400000000
[   145.484] *Mode: 124 (1280x1024)
[   145.484]     ModeAttributes: 0xbb
[   145.484]     WinAAttributes: 0x7
[   145.484]     WinBAttributes: 0x0
[   145.484]     WinGranularity: 64
[   145.484]     WinSize: 64
[   145.484]     WinASegment: 0xa000
[   145.484]     WinBSegment: 0x0
[   145.484]     WinFuncPtr: 0xc0005237
[   145.484]     BytesPerScanline: 5120
[   145.484]     XResolution: 1280
[   145.484]     YResolution: 1024
[   145.484]     XCharSize: 8
[   145.484]     YCharSize: 16
[   145.484]     NumberOfPlanes: 1
[   145.484]     BitsPerPixel: 32
[   145.484]     NumberOfBanks: 1
[   145.484]     MemoryModel: 6
[   145.484]     BankSize: 0
[   145.484]     NumberOfImages: 2
[   145.484]     RedMaskSize: 8
[   145.484]     RedFieldPosition: 16
[   145.484]     GreenMaskSize: 8
[   145.484]     GreenFieldPosition: 8
[   145.484]     BlueMaskSize: 8
[   145.484]     BlueFieldPosition: 0
[   145.484]     RsvdMaskSize: 0
[   145.484]     RsvdFieldPosition: 0
[   145.484]     DirectColorModeInfo: 0
[   145.484]     PhysBasePtr: 0xf0000000
[   145.484]     LinBytesPerScanLine: 5120
[   145.484]     BnkNumberOfImagePages: 2
[   145.484]     LinNumberOfImagePages: 2
[   145.484]     LinRedMaskSize: 8
[   145.484]     LinRedFieldPosition: 16
[   145.484]     LinGreenMaskSize: 8
[   145.484]     LinGreenFieldPosition: 8
[   145.484]     LinBlueMaskSize: 8
[   145.484]     LinBlueFieldPosition: 0
[   145.484]     LinRsvdMaskSize: 0
[   145.484]     LinRsvdFieldPosition: 0
[   145.484]     MaxPixelClock: 400000000
[   145.485] Mode: 143 (1400x1050)
[   145.485]     ModeAttributes: 0xbb
[   145.485]     WinAAttributes: 0x7
[   145.485]     WinBAttributes: 0x0
[   145.485]     WinGranularity: 64
[   145.485]     WinSize: 64
[   145.485]     WinASegment: 0xa000
[   145.485]     WinBSegment: 0x0
[   145.485]     WinFuncPtr: 0xc0005237
[   145.485]     BytesPerScanline: 1408
[   145.485]     XResolution: 1400
[   145.485]     YResolution: 1050
[   145.485]     XCharSize: 8
[   145.485]     YCharSize: 16
[   145.485]     NumberOfPlanes: 1
[   145.485]     BitsPerPixel: 8
[   145.485]     NumberOfBanks: 1
[   145.485]     MemoryModel: 4
[   145.485]     BankSize: 0
[   145.485]     NumberOfImages: 10
[   145.485]     RedMaskSize: 0
[   145.485]     RedFieldPosition: 0
[   145.485]     GreenMaskSize: 0
[   145.485]     GreenFieldPosition: 0
[   145.485]     BlueMaskSize: 0
[   145.485]     BlueFieldPosition: 0
[   145.485]     RsvdMaskSize: 0
[   145.485]     RsvdFieldPosition: 0
[   145.485]     DirectColorModeInfo: 0
[   145.485]     PhysBasePtr: 0xf0000000
[   145.485]     LinBytesPerScanLine: 1408
[   145.485]     BnkNumberOfImagePages: 10
[   145.485]     LinNumberOfImagePages: 10
[   145.485]     LinRedMaskSize: 0
[   145.485]     LinRedFieldPosition: 0
[   145.485]     LinGreenMaskSize: 0
[   145.485]     LinGreenFieldPosition: 0
[   145.485]     LinBlueMaskSize: 0
[   145.485]     LinBlueFieldPosition: 0
[   145.485]     LinRsvdMaskSize: 0
[   145.485]     LinRsvdFieldPosition: 0
[   145.485]     MaxPixelClock: 400000000
[   145.486] Mode: 145 (1400x1050)
[   145.486]     ModeAttributes: 0xbb
[   145.486]     WinAAttributes: 0x7
[   145.486]     WinBAttributes: 0x0
[   145.486]     WinGranularity: 64
[   145.486]     WinSize: 64
[   145.486]     WinASegment: 0xa000
[   145.486]     WinBSegment: 0x0
[   145.486]     WinFuncPtr: 0xc0005237
[   145.486]     BytesPerScanline: 2816
[   145.486]     XResolution: 1400
[   145.486]     YResolution: 1050
[   145.486]     XCharSize: 8
[   145.486]     YCharSize: 16
[   145.486]     NumberOfPlanes: 1
[   145.486]     BitsPerPixel: 16
[   145.486]     NumberOfBanks: 1
[   145.486]     MemoryModel: 6
[   145.486]     BankSize: 0
[   145.486]     NumberOfImages: 4
[   145.486]     RedMaskSize: 5
[   145.486]     RedFieldPosition: 11
[   145.486]     GreenMaskSize: 6
[   145.486]     GreenFieldPosition: 5
[   145.486]     BlueMaskSize: 5
[   145.486]     BlueFieldPosition: 0
[   145.486]     RsvdMaskSize: 0
[   145.486]     RsvdFieldPosition: 0
[   145.486]     DirectColorModeInfo: 0
[   145.486]     PhysBasePtr: 0xf0000000
[   145.486]     LinBytesPerScanLine: 2816
[   145.486]     BnkNumberOfImagePages: 4
[   145.486]     LinNumberOfImagePages: 4
[   145.486]     LinRedMaskSize: 5
[   145.486]     LinRedFieldPosition: 11
[   145.486]     LinGreenMaskSize: 6
[   145.486]     LinGreenFieldPosition: 5
[   145.486]     LinBlueMaskSize: 5
[   145.486]     LinBlueFieldPosition: 0
[   145.486]     LinRsvdMaskSize: 0
[   145.486]     LinRsvdFieldPosition: 0
[   145.486]     MaxPixelClock: 400000000
[   145.486] *Mode: 146 (1400x1050)
[   145.486]     ModeAttributes: 0xbb
[   145.486]     WinAAttributes: 0x7
[   145.486]     WinBAttributes: 0x0
[   145.486]     WinGranularity: 64
[   145.486]     WinSize: 64
[   145.486]     WinASegment: 0xa000
[   145.486]     WinBSegment: 0x0
[   145.486]     WinFuncPtr: 0xc0005237
[   145.487]     BytesPerScanline: 5632
[   145.487]     XResolution: 1400
[   145.487]     YResolution: 1050
[   145.487]     XCharSize: 8
[   145.487]     YCharSize: 16
[   145.487]     NumberOfPlanes: 1
[   145.487]     BitsPerPixel: 32
[   145.487]     NumberOfBanks: 1
[   145.487]     MemoryModel: 6
[   145.487]     BankSize: 0
[   145.487]     NumberOfImages: 1
[   145.487]     RedMaskSize: 8
[   145.487]     RedFieldPosition: 16
[   145.487]     GreenMaskSize: 8
[   145.487]     GreenFieldPosition: 8
[   145.487]     BlueMaskSize: 8
[   145.487]     BlueFieldPosition: 0
[   145.487]     RsvdMaskSize: 0
[   145.487]     RsvdFieldPosition: 0
[   145.487]     DirectColorModeInfo: 0
[   145.487]     PhysBasePtr: 0xf0000000
[   145.487]     LinBytesPerScanLine: 5632
[   145.487]     BnkNumberOfImagePages: 1
[   145.487]     LinNumberOfImagePages: 1
[   145.487]     LinRedMaskSize: 8
[   145.487]     LinRedFieldPosition: 16
[   145.487]     LinGreenMaskSize: 8
[   145.487]     LinGreenFieldPosition: 8
[   145.487]     LinBlueMaskSize: 8
[   145.487]     LinBlueFieldPosition: 0
[   145.487]     LinRsvdMaskSize: 0
[   145.487]     LinRsvdFieldPosition: 0
[   145.487]     MaxPixelClock: 400000000
[   145.487] Mode: 173 (1600x1200)
[   145.487]     ModeAttributes: 0xbb
[   145.487]     WinAAttributes: 0x7
[   145.487]     WinBAttributes: 0x0
[   145.487]     WinGranularity: 64
[   145.487]     WinSize: 64
[   145.487]     WinASegment: 0xa000
[   145.487]     WinBSegment: 0x0
[   145.487]     WinFuncPtr: 0xc0005237
[   145.487]     BytesPerScanline: 1600
[   145.487]     XResolution: 1600
[   145.487]     YResolution: 1200
[   145.487]     XCharSize: 8
[   145.487]     YCharSize: 16
[   145.487]     NumberOfPlanes: 1
[   145.487]     BitsPerPixel: 8
[   145.487]     NumberOfBanks: 1
[   145.487]     MemoryModel: 4
[   145.487]     BankSize: 0
[   145.487]     NumberOfImages: 7
[   145.487]     RedMaskSize: 0
[   145.487]     RedFieldPosition: 0
[   145.487]     GreenMaskSize: 0
[   145.487]     GreenFieldPosition: 0
[   145.487]     BlueMaskSize: 0
[   145.487]     BlueFieldPosition: 0
[   145.487]     RsvdMaskSize: 0
[   145.487]     RsvdFieldPosition: 0
[   145.487]     DirectColorModeInfo: 0
[   145.487]     PhysBasePtr: 0xf0000000
[   145.487]     LinBytesPerScanLine: 1600
[   145.487]     BnkNumberOfImagePages: 7
[   145.487]     LinNumberOfImagePages: 7
[   145.487]     LinRedMaskSize: 0
[   145.487]     LinRedFieldPosition: 0
[   145.487]     LinGreenMaskSize: 0
[   145.487]     LinGreenFieldPosition: 0
[   145.487]     LinBlueMaskSize: 0
[   145.487]     LinBlueFieldPosition: 0
[   145.487]     LinRsvdMaskSize: 0
[   145.488]     LinRsvdFieldPosition: 0
[   145.488]     MaxPixelClock: 400000000
[   145.488] Mode: 175 (1600x1200)
[   145.488]     ModeAttributes: 0xbb
[   145.488]     WinAAttributes: 0x7
[   145.488]     WinBAttributes: 0x0
[   145.488]     WinGranularity: 64
[   145.488]     WinSize: 64
[   145.488]     WinASegment: 0xa000
[   145.488]     WinBSegment: 0x0
[   145.488]     WinFuncPtr: 0xc0005237
[   145.488]     BytesPerScanline: 3200
[   145.488]     XResolution: 1600
[   145.488]     YResolution: 1200
[   145.488]     XCharSize: 8
[   145.488]     YCharSize: 16
[   145.488]     NumberOfPlanes: 1
[   145.488]     BitsPerPixel: 16
[   145.488]     NumberOfBanks: 1
[   145.488]     MemoryModel: 6
[   145.488]     BankSize: 0
[   145.488]     NumberOfImages: 3
[   145.488]     RedMaskSize: 5
[   145.488]     RedFieldPosition: 11
[   145.488]     GreenMaskSize: 6
[   145.488]     GreenFieldPosition: 5
[   145.488]     BlueMaskSize: 5
[   145.488]     BlueFieldPosition: 0
[   145.488]     RsvdMaskSize: 0
[   145.488]     RsvdFieldPosition: 0
[   145.488]     DirectColorModeInfo: 0
[   145.488]     PhysBasePtr: 0xf0000000
[   145.488]     LinBytesPerScanLine: 3200
[   145.488]     BnkNumberOfImagePages: 3
[   145.488]     LinNumberOfImagePages: 3
[   145.488]     LinRedMaskSize: 5
[   145.488]     LinRedFieldPosition: 11
[   145.488]     LinGreenMaskSize: 6
[   145.488]     LinGreenFieldPosition: 5
[   145.488]     LinBlueMaskSize: 5
[   145.488]     LinBlueFieldPosition: 0
[   145.488]     LinRsvdMaskSize: 0
[   145.488]     LinRsvdFieldPosition: 0
[   145.488]     MaxPixelClock: 400000000
[   145.489] *Mode: 176 (1600x1200)
[   145.489]     ModeAttributes: 0xbb
[   145.489]     WinAAttributes: 0x7
[   145.489]     WinBAttributes: 0x0
[   145.489]     WinGranularity: 64
[   145.489]     WinSize: 64
[   145.489]     WinASegment: 0xa000
[   145.489]     WinBSegment: 0x0
[   145.489]     WinFuncPtr: 0xc0005237
[   145.489]     BytesPerScanline: 6400
[   145.489]     XResolution: 1600
[   145.489]     YResolution: 1200
[   145.489]     XCharSize: 8
[   145.489]     YCharSize: 16
[   145.489]     NumberOfPlanes: 1
[   145.489]     BitsPerPixel: 32
[   145.489]     NumberOfBanks: 1
[   145.489]     MemoryModel: 6
[   145.489]     BankSize: 0
[   145.489]     NumberOfImages: 1
[   145.489]     RedMaskSize: 8
[   145.489]     RedFieldPosition: 16
[   145.489]     GreenMaskSize: 8
[   145.489]     GreenFieldPosition: 8
[   145.489]     BlueMaskSize: 8
[   145.489]     BlueFieldPosition: 0
[   145.489]     RsvdMaskSize: 0
[   145.489]     RsvdFieldPosition: 0
[   145.489]     DirectColorModeInfo: 0
[   145.489]     PhysBasePtr: 0xf0000000
[   145.489]     LinBytesPerScanLine: 6400
[   145.489]     BnkNumberOfImagePages: 1
[   145.489]     LinNumberOfImagePages: 1
[   145.489]     LinRedMaskSize: 8
[   145.489]     LinRedFieldPosition: 16
[   145.489]     LinGreenMaskSize: 8
[   145.489]     LinGreenFieldPosition: 8
[   145.489]     LinBlueMaskSize: 8
[   145.489]     LinBlueFieldPosition: 0
[   145.489]     LinRsvdMaskSize: 0
[   145.489]     LinRsvdFieldPosition: 0
[   145.489]     MaxPixelClock: 400000000
[   145.489] Mode: 183 (640x400)
[   145.489]     ModeAttributes: 0xbb
[   145.489]     WinAAttributes: 0x7
[   145.489]     WinBAttributes: 0x0
[   145.489]     WinGranularity: 64
[   145.489]     WinSize: 64
[   145.489]     WinASegment: 0xa000
[   145.489]     WinBSegment: 0x0
[   145.490]     WinFuncPtr: 0xc0005237
[   145.490]     BytesPerScanline: 640
[   145.490]     XResolution: 640
[   145.490]     YResolution: 400
[   145.490]     XCharSize: 8
[   145.490]     YCharSize: 16
[   145.490]     NumberOfPlanes: 1
[   145.490]     BitsPerPixel: 8
[   145.490]     NumberOfBanks: 1
[   145.490]     MemoryModel: 4
[   145.490]     BankSize: 0
[   145.490]     NumberOfImages: 63
[   145.490]     RedMaskSize: 0
[   145.490]     RedFieldPosition: 0
[   145.490]     GreenMaskSize: 0
[   145.490]     GreenFieldPosition: 0
[   145.490]     BlueMaskSize: 0
[   145.490]     BlueFieldPosition: 0
[   145.490]     RsvdMaskSize: 0
[   145.490]     RsvdFieldPosition: 0
[   145.490]     DirectColorModeInfo: 0
[   145.490]     PhysBasePtr: 0xf0000000
[   145.490]     LinBytesPerScanLine: 640
[   145.490]     BnkNumberOfImagePages: 63
[   145.490]     LinNumberOfImagePages: 63
[   145.490]     LinRedMaskSize: 0
[   145.490]     LinRedFieldPosition: 0
[   145.490]     LinGreenMaskSize: 0
[   145.490]     LinGreenFieldPosition: 0
[   145.490]     LinBlueMaskSize: 0
[   145.490]     LinBlueFieldPosition: 0
[   145.490]     LinRsvdMaskSize: 0
[   145.490]     LinRsvdFieldPosition: 0
[   145.490]     MaxPixelClock: 400000000
[   145.490] Mode: 185 (640x400)
[   145.490]     ModeAttributes: 0xbb
[   145.490]     WinAAttributes: 0x7
[   145.490]     WinBAttributes: 0x0
[   145.490]     WinGranularity: 64
[   145.490]     WinSize: 64
[   145.490]     WinASegment: 0xa000
[   145.490]     WinBSegment: 0x0
[   145.490]     WinFuncPtr: 0xc0005237
[   145.490]     BytesPerScanline: 1280
[   145.490]     XResolution: 640
[   145.490]     YResolution: 400
[   145.490]     XCharSize: 8
[   145.490]     YCharSize: 16
[   145.490]     NumberOfPlanes: 1
[   145.490]     BitsPerPixel: 16
[   145.490]     NumberOfBanks: 1
[   145.490]     MemoryModel: 6
[   145.490]     BankSize: 0
[   145.490]     NumberOfImages: 31
[   145.490]     RedMaskSize: 5
[   145.490]     RedFieldPosition: 11
[   145.490]     GreenMaskSize: 6
[   145.490]     GreenFieldPosition: 5
[   145.490]     BlueMaskSize: 5
[   145.490]     BlueFieldPosition: 0
[   145.490]     RsvdMaskSize: 0
[   145.490]     RsvdFieldPosition: 0
[   145.490]     DirectColorModeInfo: 0
[   145.490]     PhysBasePtr: 0xf0000000
[   145.490]     LinBytesPerScanLine: 1280
[   145.490]     BnkNumberOfImagePages: 31
[   145.490]     LinNumberOfImagePages: 31
[   145.490]     LinRedMaskSize: 5
[   145.490]     LinRedFieldPosition: 11
[   145.490]     LinGreenMaskSize: 6
[   145.490]     LinGreenFieldPosition: 5
[   145.490]     LinBlueMaskSize: 5
[   145.490]     LinBlueFieldPosition: 0
[   145.490]     LinRsvdMaskSize: 0
[   145.490]     LinRsvdFieldPosition: 0
[   145.490]     MaxPixelClock: 400000000
[   145.491] *Mode: 186 (640x400)
[   145.491]     ModeAttributes: 0xbb
[   145.491]     WinAAttributes: 0x7
[   145.491]     WinBAttributes: 0x0
[   145.491]     WinGranularity: 64
[   145.491]     WinSize: 64
[   145.491]     WinASegment: 0xa000
[   145.491]     WinBSegment: 0x0
[   145.491]     WinFuncPtr: 0xc0005237
[   145.491]     BytesPerScanline: 2560
[   145.491]     XResolution: 640
[   145.491]     YResolution: 400
[   145.491]     XCharSize: 8
[   145.491]     YCharSize: 16
[   145.491]     NumberOfPlanes: 1
[   145.491]     BitsPerPixel: 32
[   145.491]     NumberOfBanks: 1
[   145.491]     MemoryModel: 6
[   145.491]     BankSize: 0
[   145.491]     NumberOfImages: 15
[   145.491]     RedMaskSize: 8
[   145.491]     RedFieldPosition: 16
[   145.491]     GreenMaskSize: 8
[   145.491]     GreenFieldPosition: 8
[   145.491]     BlueMaskSize: 8
[   145.491]     BlueFieldPosition: 0
[   145.491]     RsvdMaskSize: 0
[   145.491]     RsvdFieldPosition: 0
[   145.491]     DirectColorModeInfo: 0
[   145.491]     PhysBasePtr: 0xf0000000
[   145.491]     LinBytesPerScanLine: 2560
[   145.491]     BnkNumberOfImagePages: 15
[   145.491]     LinNumberOfImagePages: 15
[   145.491]     LinRedMaskSize: 8
[   145.491]     LinRedFieldPosition: 16
[   145.491]     LinGreenMaskSize: 8
[   145.491]     LinGreenFieldPosition: 8
[   145.491]     LinBlueMaskSize: 8
[   145.491]     LinBlueFieldPosition: 0
[   145.491]     LinRsvdMaskSize: 0
[   145.491]     LinRsvdFieldPosition: 0
[   145.491]     MaxPixelClock: 400000000
[   145.492] Mode: 1d3 (1856x1392)
[   145.492]     ModeAttributes: 0xba
[   145.492]     WinAAttributes: 0x7
[   145.492]     WinBAttributes: 0x0
[   145.492]     WinGranularity: 64
[   145.492]     WinSize: 64
[   145.492]     WinASegment: 0xa000
[   145.492]     WinBSegment: 0x0
[   145.492]     WinFuncPtr: 0xc0005237
[   145.492]     BytesPerScanline: 1856
[   145.492]     XResolution: 1856
[   145.492]     YResolution: 1392
[   145.492]     XCharSize: 8
[   145.492]     YCharSize: 16
[   145.492]     NumberOfPlanes: 1
[   145.492]     BitsPerPixel: 8
[   145.492]     NumberOfBanks: 1
[   145.492]     MemoryModel: 4
[   145.492]     BankSize: 0
[   145.492]     NumberOfImages: 5
[   145.492]     RedMaskSize: 0
[   145.492]     RedFieldPosition: 0
[   145.492]     GreenMaskSize: 0
[   145.492]     GreenFieldPosition: 0
[   145.492]     BlueMaskSize: 0
[   145.492]     BlueFieldPosition: 0
[   145.492]     RsvdMaskSize: 0
[   145.492]     RsvdFieldPosition: 0
[   145.492]     DirectColorModeInfo: 0
[   145.492]     PhysBasePtr: 0xf0000000
[   145.492]     LinBytesPerScanLine: 1856
[   145.492]     BnkNumberOfImagePages: 5
[   145.492]     LinNumberOfImagePages: 5
[   145.492]     LinRedMaskSize: 0
[   145.492]     LinRedFieldPosition: 0
[   145.492]     LinGreenMaskSize: 0
[   145.492]     LinGreenFieldPosition: 0
[   145.492]     LinBlueMaskSize: 0
[   145.492]     LinBlueFieldPosition: 0
[   145.492]     LinRsvdMaskSize: 0
[   145.492]     LinRsvdFieldPosition: 0
[   145.492]     MaxPixelClock: 400000000
[   145.493] Mode: 1d5 (1856x1392)
[   145.493]     ModeAttributes: 0xba
[   145.493]     WinAAttributes: 0x7
[   145.493]     WinBAttributes: 0x0
[   145.493]     WinGranularity: 64
[   145.493]     WinSize: 64
[   145.493]     WinASegment: 0xa000
[   145.493]     WinBSegment: 0x0
[   145.493]     WinFuncPtr: 0xc0005237
[   145.493]     BytesPerScanline: 3712
[   145.493]     XResolution: 1856
[   145.493]     YResolution: 1392
[   145.493]     XCharSize: 8
[   145.493]     YCharSize: 16
[   145.493]     NumberOfPlanes: 1
[   145.493]     BitsPerPixel: 16
[   145.493]     NumberOfBanks: 1
[   145.493]     MemoryModel: 6
[   145.493]     BankSize: 0
[   145.493]     NumberOfImages: 2
[   145.493]     RedMaskSize: 5
[   145.493]     RedFieldPosition: 11
[   145.493]     GreenMaskSize: 6
[   145.493]     GreenFieldPosition: 5
[   145.493]     BlueMaskSize: 5
[   145.493]     BlueFieldPosition: 0
[   145.493]     RsvdMaskSize: 0
[   145.493]     RsvdFieldPosition: 0
[   145.493]     DirectColorModeInfo: 0
[   145.493]     PhysBasePtr: 0xf0000000
[   145.493]     LinBytesPerScanLine: 3712
[   145.493]     BnkNumberOfImagePages: 2
[   145.493]     LinNumberOfImagePages: 2
[   145.493]     LinRedMaskSize: 5
[   145.493]     LinRedFieldPosition: 11
[   145.493]     LinGreenMaskSize: 6
[   145.493]     LinGreenFieldPosition: 5
[   145.493]     LinBlueMaskSize: 5
[   145.493]     LinBlueFieldPosition: 0
[   145.493]     LinRsvdMaskSize: 0
[   145.493]     LinRsvdFieldPosition: 0
[   145.493]     MaxPixelClock: 400000000
[   145.493] Mode: 1d6 (1856x1392)
[   145.493]     ModeAttributes: 0xba
[   145.493]     WinAAttributes: 0x7
[   145.493]     WinBAttributes: 0x0
[   145.493]     WinGranularity: 64
[   145.493]     WinSize: 64
[   145.493]     WinASegment: 0xa000
[   145.493]     WinBSegment: 0x0
[   145.493]     WinFuncPtr: 0xc0005237
[   145.493]     BytesPerScanline: 7424
[   145.493]     XResolution: 1856
[   145.494]     YResolution: 1392
[   145.494]     XCharSize: 8
[   145.494]     YCharSize: 16
[   145.494]     NumberOfPlanes: 1
[   145.494]     BitsPerPixel: 32
[   145.494]     NumberOfBanks: 1
[   145.494]     MemoryModel: 6
[   145.494]     BankSize: 0
[   145.494]     NumberOfImages: 1
[   145.494]     RedMaskSize: 8
[   145.494]     RedFieldPosition: 16
[   145.494]     GreenMaskSize: 8
[   145.494]     GreenFieldPosition: 8
[   145.494]     BlueMaskSize: 8
[   145.494]     BlueFieldPosition: 0
[   145.494]     RsvdMaskSize: 0
[   145.494]     RsvdFieldPosition: 0
[   145.494]     DirectColorModeInfo: 0
[   145.494]     PhysBasePtr: 0xf0000000
[   145.494]     LinBytesPerScanLine: 7424
[   145.494]     BnkNumberOfImagePages: 1
[   145.494]     LinNumberOfImagePages: 1
[   145.494]     LinRedMaskSize: 8
[   145.494]     LinRedFieldPosition: 16
[   145.494]     LinGreenMaskSize: 8
[   145.494]     LinGreenFieldPosition: 8
[   145.494]     LinBlueMaskSize: 8
[   145.494]     LinBlueFieldPosition: 0
[   145.494]     LinRsvdMaskSize: 0
[   145.494]     LinRsvdFieldPosition: 0
[   145.494]     MaxPixelClock: 400000000
[   145.494] Mode: 1e3 (1920x1440)
[   145.494]     ModeAttributes: 0xba
[   145.494]     WinAAttributes: 0x7
[   145.494]     WinBAttributes: 0x0
[   145.494]     WinGranularity: 64
[   145.494]     WinSize: 64
[   145.494]     WinASegment: 0xa000
[   145.494]     WinBSegment: 0x0
[   145.494]     WinFuncPtr: 0xc0005237
[   145.494]     BytesPerScanline: 1920
[   145.494]     XResolution: 1920
[   145.494]     YResolution: 1440
[   145.494]     XCharSize: 8
[   145.494]     YCharSize: 16
[   145.494]     NumberOfPlanes: 1
[   145.494]     BitsPerPixel: 8
[   145.494]     NumberOfBanks: 1
[   145.494]     MemoryModel: 4
[   145.494]     BankSize: 0
[   145.494]     NumberOfImages: 4
[   145.494]     RedMaskSize: 0
[   145.494]     RedFieldPosition: 0
[   145.494]     GreenMaskSize: 0
[   145.494]     GreenFieldPosition: 0
[   145.494]     BlueMaskSize: 0
[   145.494]     BlueFieldPosition: 0
[   145.495]     RsvdMaskSize: 0
[   145.495]     RsvdFieldPosition: 0
[   145.495]     DirectColorModeInfo: 0
[   145.495]     PhysBasePtr: 0xf0000000
[   145.495]     LinBytesPerScanLine: 1920
[   145.495]     BnkNumberOfImagePages: 4
[   145.495]     LinNumberOfImagePages: 4
[   145.495]     LinRedMaskSize: 0
[   145.495]     LinRedFieldPosition: 0
[   145.495]     LinGreenMaskSize: 0
[   145.495]     LinGreenFieldPosition: 0
[   145.495]     LinBlueMaskSize: 0
[   145.495]     LinBlueFieldPosition: 0
[   145.495]     LinRsvdMaskSize: 0
[   145.495]     LinRsvdFieldPosition: 0
[   145.495]     MaxPixelClock: 400000000
[   145.495] Mode: 1e5 (1920x1440)
[   145.495]     ModeAttributes: 0xba
[   145.495]     WinAAttributes: 0x7
[   145.495]     WinBAttributes: 0x0
[   145.495]     WinGranularity: 64
[   145.495]     WinSize: 64
[   145.495]     WinASegment: 0xa000
[   145.495]     WinBSegment: 0x0
[   145.495]     WinFuncPtr: 0xc0005237
[   145.495]     BytesPerScanline: 3840
[   145.495]     XResolution: 1920
[   145.495]     YResolution: 1440
[   145.495]     XCharSize: 8
[   145.495]     YCharSize: 16
[   145.495]     NumberOfPlanes: 1
[   145.495]     BitsPerPixel: 16
[   145.495]     NumberOfBanks: 1
[   145.495]     MemoryModel: 6
[   145.495]     BankSize: 0
[   145.495]     NumberOfImages: 2
[   145.495]     RedMaskSize: 5
[   145.495]     RedFieldPosition: 11
[   145.495]     GreenMaskSize: 6
[   145.495]     GreenFieldPosition: 5
[   145.495]     BlueMaskSize: 5
[   145.495]     BlueFieldPosition: 0
[   145.495]     RsvdMaskSize: 0
[   145.495]     RsvdFieldPosition: 0
[   145.495]     DirectColorModeInfo: 0
[   145.495]     PhysBasePtr: 0xf0000000
[   145.495]     LinBytesPerScanLine: 3840
[   145.495]     BnkNumberOfImagePages: 2
[   145.495]     LinNumberOfImagePages: 2
[   145.495]     LinRedMaskSize: 5
[   145.495]     LinRedFieldPosition: 11
[   145.495]     LinGreenMaskSize: 6
[   145.495]     LinGreenFieldPosition: 5
[   145.495]     LinBlueMaskSize: 5
[   145.495]     LinBlueFieldPosition: 0
[   145.495]     LinRsvdMaskSize: 0
[   145.495]     LinRsvdFieldPosition: 0
[   145.495]     MaxPixelClock: 400000000
[   145.496] Mode: 1e6 (1920x1440)
[   145.496]     ModeAttributes: 0xba
[   145.496]     WinAAttributes: 0x7
[   145.496]     WinBAttributes: 0x0
[   145.496]     WinGranularity: 64
[   145.496]     WinSize: 64
[   145.496]     WinASegment: 0xa000
[   145.496]     WinBSegment: 0x0
[   145.496]     WinFuncPtr: 0xc0005237
[   145.496]     BytesPerScanline: 7680
[   145.496]     XResolution: 1920
[   145.496]     YResolution: 1440
[   145.496]     XCharSize: 8
[   145.496]     YCharSize: 16
[   145.496]     NumberOfPlanes: 1
[   145.496]     BitsPerPixel: 32
[   145.496]     NumberOfBanks: 1
[   145.496]     MemoryModel: 6
[   145.496]     BankSize: 0
[   145.496]     NumberOfImages: 1
[   145.496]     RedMaskSize: 8
[   145.496]     RedFieldPosition: 16
[   145.496]     GreenMaskSize: 8
[   145.496]     GreenFieldPosition: 8
[   145.496]     BlueMaskSize: 8
[   145.496]     BlueFieldPosition: 0
[   145.496]     RsvdMaskSize: 0
[   145.496]     RsvdFieldPosition: 0
[   145.496]     DirectColorModeInfo: 0
[   145.496]     PhysBasePtr: 0xf0000000
[   145.496]     LinBytesPerScanLine: 7680
[   145.496]     BnkNumberOfImagePages: 1
[   145.496]     LinNumberOfImagePages: 1
[   145.496]     LinRedMaskSize: 8
[   145.496]     LinRedFieldPosition: 16
[   145.496]     LinGreenMaskSize: 8
[   145.496]     LinGreenFieldPosition: 8
[   145.496]     LinBlueMaskSize: 8
[   145.496]     LinBlueFieldPosition: 0
[   145.496]     LinRsvdMaskSize: 0
[   145.496]     LinRsvdFieldPosition: 0
[   145.496]     MaxPixelClock: 400000000
[   145.496] 
[   145.496] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[   145.496] (II) VESA(0): <default monitor>: Using hsync range of 31.00-84.00 kHz
[   145.497] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-76.00 Hz
[   145.497] (II) VESA(0): <default monitor>: Using maximum pixel clock of 145.00 MHz
[   145.497] (WW) VESA(0): Unable to estimate virtual size
[   145.497] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[   145.497] (II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
[   145.498] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[   145.498] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[   145.498] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[   145.498] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[   145.498] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[   145.498] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[   145.498] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[   145.498] (**) VESA(0): *Built-in mode "1280x1024"
[   145.498] (**) VESA(0): *Built-in mode "1280x1024"
[   145.498] (**) VESA(0): *Built-in mode "1152x864"
[   145.498] (**) VESA(0): *Built-in mode "1024x768"
[   145.498] (**) VESA(0): *Built-in mode "800x600"
[   145.498] (**) VESA(0): *Built-in mode "640x480"
[   145.498] (**) VESA(0): *Built-in mode "720x400"
[   145.498] (**) VESA(0): Display dimensions: (410, 260) mm
[   145.498] (**) VESA(0): DPI set to (79, 100)
[   145.498] (**) VESA(0): Using "Shadow Framebuffer"
[   145.498] (II) Loading sub module "shadow"
[   145.498] (II) LoadModule: "shadow"
[   145.499] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   145.506] (II) Module shadow: vendor="X.Org Foundation"
[   145.506]     compiled for 1.15.1, module version = 1.1.0
[   145.506]     ABI class: X.Org ANSI C Emulation, version 0.4
[   145.506] (II) Loading sub module "fb"
[   145.506] (II) LoadModule: "fb"
[   145.507] (II) Loading /usr/lib/xorg/modules/libfb.so
[   145.524] (II) Module fb: vendor="X.Org Foundation"
[   145.524]     compiled for 1.15.1, module version = 1.0.0
[   145.524]     ABI class: X.Org ANSI C Emulation, version 0.4
[   145.524] (==) Depth 24 pixmap format is 32 bpp
[   145.524] (II) Loading sub module "int10"
[   145.524] (II) LoadModule: "int10"
[   145.525] (II) Loading /usr/lib/xorg/modules/libint10.so
[   145.526] (II) Module int10: vendor="X.Org Foundation"
[   145.526]     compiled for 1.15.1, module version = 1.0.0
[   145.526]     ABI class: X.Org Video Driver, version 15.0
[   145.526] (II) VESA(0): initializing int10
[   145.526] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   145.527] (II) VESA(0): VESA BIOS detected
[   145.527] (II) VESA(0): VESA VBE Version 3.0
[   145.527] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   145.527] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   145.527] (II) VESA(0): VESA VBE OEM Software Rev: 10.55
[   145.527] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   145.527] (II) VESA(0): VESA VBE OEM Product: RS690
[   145.527] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   145.527] (II) VESA(0): virtual address = 0xb5984000,
    physical address = 0xf0000000, size = 16777216
[   145.533] (II) VESA(0): Setting up VESA Mode 0x166 (1280x1024)
[   145.534] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[   145.648] (==) VESA(0): Default visual is TrueColor
[   145.648] (==) VESA(0): Backing store enabled
[   145.649] (==) VESA(0): DPMS enabled
[   145.649] (==) RandR enabled
[   145.661] (II) SELinux: Disabled on system
[   145.663] (II) AIGLX: Screen 0 is not DRI2 capable
[   145.663] (EE) AIGLX: reverting to software rendering
[   148.017] (II) AIGLX: Loaded and initialized swrast
[   148.017] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   148.066] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   148.290] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   148.290] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   148.290] (II) LoadModule: "evdev"
[   148.295] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   148.310] (II) Module evdev: vendor="X.Org Foundation"
[   148.311]     compiled for 1.15.0, module version = 2.8.2
[   148.311]     Module class: X.Org XInput Driver
[   148.311]     ABI class: X.Org XInput driver, version 20.0
[   148.311] (II) Using input driver 'evdev' for 'Power Button'
[   148.311] (**) Power Button: always reports core events
[   148.311] (**) evdev: Power Button: Device: "/dev/input/event1"
[   148.311] (--) evdev: Power Button: Vendor 0 Product 0x1
[   148.311] (--) evdev: Power Button: Found keys
[   148.311] (II) evdev: Power Button: Configuring as keyboard
[   148.311] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   148.311] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   148.311] (**) Option "xkb_rules" "evdev"
[   148.311] (**) Option "xkb_model" "pc105"
[   148.311] (**) Option "xkb_layout" "us"
[   148.312] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   148.313] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   148.313] (II) Using input driver 'evdev' for 'Power Button'
[   148.313] (**) Power Button: always reports core events
[   148.313] (**) evdev: Power Button: Device: "/dev/input/event0"
[   148.313] (--) evdev: Power Button: Vendor 0 Product 0x1
[   148.313] (--) evdev: Power Button: Found keys
[   148.313] (II) evdev: Power Button: Configuring as keyboard
[   148.313] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   148.313] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   148.313] (**) Option "xkb_rules" "evdev"
[   148.313] (**) Option "xkb_model" "pc105"
[   148.313] (**) Option "xkb_layout" "us"
[   148.314] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event3)
[   148.314] (II) No input driver specified, ignoring this device.
[   148.314] (II) This device may have been added with another device file.
[   148.315] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event4)
[   148.315] (II) No input driver specified, ignoring this device.
[   148.315] (II) This device may have been added with another device file.
[   148.315] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   148.315] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   148.315] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   148.315] (**) AT Translated Set 2 keyboard: always reports core events
[   148.315] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   148.315] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   148.315] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   148.315] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   148.315] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   148.315] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[   148.315] (**) Option "xkb_rules" "evdev"
[   148.316] (**) Option "xkb_model" "pc105"
[   148.316] (**) Option "xkb_layout" "us"
[   345.245] (II) evdev: AT Translated Set 2 keyboard: Close
[   345.245] (II) UnloadModule: "evdev"
[   345.245] (II) evdev: Power Button: Close
[   345.245] (II) UnloadModule: "evdev"
[   345.245] (II) evdev: Power Button: Close
[   345.245] (II) UnloadModule: "evdev"
[   345.247] 7 XSELINUXs still allocated at reset
[   345.247] SCREEN: 0 objects of 192 bytes = 0 total bytes 0 private allocs
[   345.247] COLORMAP: 0 objects of 4 bytes = 0 total bytes 0 private allocs
[   345.247] DEVICE: 0 objects of 64 bytes = 0 total bytes 0 private allocs
[   345.247] CLIENT: 0 objects of 140 bytes = 0 total bytes 0 private allocs
[   345.247] WINDOW: 0 objects of 24 bytes = 0 total bytes 0 private allocs
[   345.247] PIXMAP: 2 objects of 8 bytes = 16 total bytes 0 private allocs
[   345.247] GC: 4 objects of 8 bytes = 32 total bytes 0 private allocs
[   345.247] CURSOR: 1 objects of 4 bytes = 4 total bytes 0 private allocs
[   345.247] TOTAL: 7 objects, 52 bytes, 0 allocs
[   345.247] 2 PIXMAPs still allocated at reset
[   345.247] PIXMAP: 2 objects of 8 bytes = 16 total bytes 0 private allocs
[   345.247] GC: 4 objects of 8 bytes = 32 total bytes 0 private allocs
[   345.247] CURSOR: 1 objects of 4 bytes = 4 total bytes 0 private allocs
[   345.247] TOTAL: 7 objects, 52 bytes, 0 allocs
[   345.247] 4 GCs still allocated at reset
[   345.247] GC: 4 objects of 8 bytes = 32 total bytes 0 private allocs
[   345.247] CURSOR: 1 objects of 4 bytes = 4 total bytes 0 private allocs
[   345.247] TOTAL: 5 objects, 36 bytes, 0 allocs
[   345.247] 1 CURSORs still allocated at reset
[   345.247] CURSOR: 1 objects of 4 bytes = 4 total bytes 0 private allocs
[   345.247] TOTAL: 1 objects, 4 bytes, 0 allocs
[   345.247] 1 CURSOR_BITSs still allocated at reset
[   345.247] TOTAL: 0 objects, 0 bytes, 0 allocs
[   345.259] (II) Loading sub module "int10"
[   345.259] (II) LoadModule: "int10"
[   345.265] (II) Loading /usr/lib/xorg/modules/libint10.so
[   345.265] (II) Module int10: vendor="X.Org Foundation"
[   345.265]     compiled for 1.15.1, module version = 1.0.0
[   345.265]     ABI class: X.Org Video Driver, version 15.0
[   345.265] (II) VESA(0): initializing int10
[   345.266] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   345.266] (II) VESA(0): VESA BIOS detected
[   345.266] (II) VESA(0): VESA VBE Version 3.0
[   345.266] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   345.266] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   345.266] (II) VESA(0): VESA VBE OEM Software Rev: 10.55
[   345.266] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   345.266] (II) VESA(0): VESA VBE OEM Product: RS690
[   345.266] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   345.268] (II) VESA(0): Setting up VESA Mode 0x166 (1280x1024)
[   345.379] (==) VESA(0): Default visual is TrueColor
[   345.379] (==) VESA(0): DPMS enabled
[   345.379] (==) RandR enabled
[   345.392] (II) SELinux: Disabled on system
[   345.394] (II) AIGLX: Screen 0 is not DRI2 capable
[   345.394] (EE) AIGLX: reverting to software rendering
[   345.408] (II) AIGLX: Loaded and initialized swrast
[   345.408] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   345.443] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   345.545] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   345.545] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   345.545] (II) Using input driver 'evdev' for 'Power Button'
[   345.545] (**) Power Button: always reports core events
[   345.545] (**) evdev: Power Button: Device: "/dev/input/event1"
[   345.545] (--) evdev: Power Button: Vendor 0 Product 0x1
[   345.545] (--) evdev: Power Button: Found keys
[   345.545] (II) evdev: Power Button: Configuring as keyboard
[   345.545] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   345.545] (**) Option "xkb_rules" "evdev"
[   345.545] (**) Option "xkb_model" "pc105"
[   345.545] (**) Option "xkb_layout" "us"
[   345.547] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   345.547] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   345.547] (II) Using input driver 'evdev' for 'Power Button'
[   345.547] (**) Power Button: always reports core events
[   345.547] (**) evdev: Power Button: Device: "/dev/input/event0"
[   345.547] (--) evdev: Power Button: Vendor 0 Product 0x1
[   345.547] (--) evdev: Power Button: Found keys
[   345.547] (II) evdev: Power Button: Configuring as keyboard
[   345.547] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   345.547] (**) Option "xkb_rules" "evdev"
[   345.547] (**) Option "xkb_model" "pc105"
[   345.547] (**) Option "xkb_layout" "us"
[   345.549] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event3)
[   345.549] (II) No input driver specified, ignoring this device.
[   345.549] (II) This device may have been added with another device file.
[   345.549] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event4)
[   345.549] (II) No input driver specified, ignoring this device.
[   345.549] (II) This device may have been added with another device file.
[   345.550] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   345.550] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   345.550] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   345.550] (**) AT Translated Set 2 keyboard: always reports core events
[   345.550] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   345.550] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   345.550] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   345.550] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   345.550] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   345.550] (**) Option "xkb_rules" "evdev"
[   345.550] (**) Option "xkb_model" "pc105"
[   345.550] (**) Option "xkb_layout" "us"
```

---

### Post by MAFoElffen on 2016-02-03
So, I might be the person to talk with... You know how X works, right? (In specific layers...)

What do you have as a GPU?
What are you trying to display and run in an X session?
What did you install, and in what order?

I install "min X" instances on some of my servers ... for maintenance and for some of my server management utilities. On my request, they start an instance of X. I do what I need to do. Then, and on exit of of the desktop, they unload that instance of X. If you searched in this section on My userID, there was a script for the install of, that I posted, years past. That script is dated, in that it would need to be updated to install more of the X-Server, instead of the bare-bone version I had back then... (X-Server changed).

Looks and sounds like X might be loading, but you do not have anything defined beyond that... Did you define a desktop? Or did you want to use someones desktop? For mine, I use OpenBox?

---

### Post by le_jawa on 2016-02-15
MAFoElffen,

Thanks for the quick response on this this.  I realized I had done a ton of hacking around on this thing and that I had probably messed something up in the process.  I completely started over and had it setup and running in pretty good time, so it looks like I'm set.

Thank you!

Jason

---

### Post by MAFoElffen on 2016-02-15
Just happy to hear it all worked out for you.

---

