---
title: "I hate Ubuntu. I hate linux. I am going back- INTEL 945GM"
date: 2010-11-30
forum: Testimonials &amp; Experiences
---

### Post by linuxgeek77 on 2010-11-30
WHY is Ubuntu ignoring all the Intel problems after Ubuntu 10.04 got released? Ubuntu Never had a problem with intel cards in 9.10 --No luck with intel 945GM? I looked everywhere with loads of bug reports and No solution. I had this problem since ubuntu 10.4 but it started in 9.10. I only get 30-40 FPS on glxgear which used to give me 1500+ before. I cant play a simple 2D game anymore. There are no solutions I have looked. WHY did ubuntu / linux/ MESS UP intel so bad? I have been using ubuntu / linux in gerneral for 4 years and I am going back to windows. F linux. F ubuntu. IF you have an intel card and run ubuntu YOU CANT DO ANY OF the stuff you were able to do a YEAR AGO. Linux will never reach the seamless stability of proprietary software. 

IF the new kernel+intel drivers dont work then DONT use them. use a different older driver. DONT integrate things that dont work. TEST IT OUT ON REAL HARDWARE AND ACTUALLY FIX IT. 

I am done with ubuntu. I am here to say good bye for all the frustrations ubuntu caused me after it gave me a false hope. 

AND YES I HAVE TRIED EVERYTHING 
HERE IS MY XORG.LOG file:

```
    [    24.651]
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    24.652] X Protocol Version 11, Revision 0
[    24.652] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    24.652] Current Operating System: Linux danni-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    24.652] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=da6b1a2b-cc48-49fb-8836-3881c9478d5f ro quiet splash
[    24.652] Build Date: 16 September 2010  05:39:22PM
[    24.652] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    24.669] Current version of pixman: 0.18.4
[    24.669]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    24.669] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.669] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 29 23:08:27 2010
[    24.728] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.815] (==) No Layout section.  Using the first Screen section.
[    24.815] (==) No screen section available. Using defaults.
[    24.815] (**) |-->Screen "Default Screen Section" (0)
[    24.815] (**) |   |-->Monitor "<default monitor>"
[    24.816] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    24.816] (==) Automatically adding devices
[    24.816] (==) Automatically enabling devices
[    24.862] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.862]    Entry deleted from font path.
[    24.897] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    24.897] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.897] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.897] (II) Loader magic: 0x81f8e00
[    24.897] (II) Module ABI versions:
[    24.897]    X.Org ANSI C Emulation: 0.4
[    24.897]    X.Org Video Driver: 8.0
[    24.897]    X.Org XInput driver : 11.0
[    24.897]    X.Org Server Extension : 4.0
[    24.899] (--) PCI:*(0:0:2:0) 8086:27a2:1179:ff02 rev 3, Mem @ 0xdc100000/524288, 0xc0000000/268435456, 0xdc200000/262144, I/O @ 0x00001800/8
[    24.899] (--) PCI: (0:0:2:1) 8086:27a6:1179:ff02 rev 3, Mem @ 0xdc180000/524288
[    24.899] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    24.899] (II) LoadModule: "extmod"
[    25.023] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.035] (II) Module extmod: vendor="X.Org Foundation"
[    25.035]    compiled for 1.9.0, module version = 1.0.0
[    25.035]    Module class: X.Org Server Extension
[    25.035]    ABI class: X.Org Server Extension, version 4.0
[    25.035] (II) Loading extension MIT-SCREEN-SAVER
[    25.035] (II) Loading extension XFree86-VidModeExtension
[    25.035] (II) Loading extension XFree86-DGA
[    25.035] (II) Loading extension DPMS
[    25.035] (II) Loading extension XVideo
[    25.035] (II) Loading extension XVideo-MotionCompensation
[    25.035] (II) Loading extension X-Resource
[    25.035] (II) LoadModule: "dbe"
[    25.035] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.036] (II) Module dbe: vendor="X.Org Foundation"
[    25.036]    compiled for 1.9.0, module version = 1.0.0
[    25.036]    Module class: X.Org Server Extension
[    25.036]    ABI class: X.Org Server Extension, version 4.0
[    25.036] (II) Loading extension DOUBLE-BUFFER
[    25.036] (II) LoadModule: "glx"
[    25.036] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.048] (II) Module glx: vendor="X.Org Foundation"
[    25.048]    compiled for 1.9.0, module version = 1.0.0
[    25.048]    ABI class: X.Org Server Extension, version 4.0
[    25.049] (==) AIGLX enabled
[    25.049] (II) Loading extension GLX
[    25.049] (II) LoadModule: "record"
[    25.050] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.050] (II) Module record: vendor="X.Org Foundation"
[    25.050]    compiled for 1.9.0, module version = 1.13.0
[    25.050]    Module class: X.Org Server Extension
[    25.050]    ABI class: X.Org Server Extension, version 4.0
[    25.050] (II) Loading extension RECORD
[    25.050] (II) LoadModule: "dri"
[    25.051] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.074] (II) Module dri: vendor="X.Org Foundation"
[    25.074]    compiled for 1.9.0, module version = 1.0.0
[    25.074]    ABI class: X.Org Server Extension, version 4.0
[    25.074] (II) Loading extension XFree86-DRI
[    25.074] (II) LoadModule: "dri2"
[    25.075] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.075] (II) Module dri2: vendor="X.Org Foundation"
[    25.075]    compiled for 1.9.0, module version = 1.2.0
[    25.075]    ABI class: X.Org Server Extension, version 4.0
[    25.075] (II) Loading extension DRI2
[    25.075] (==) Matched intel as autoconfigured driver 0
[    25.075] (==) Matched vesa as autoconfigured driver 1
[    25.075] (==) Matched fbdev as autoconfigured driver 2
[    25.075] (==) Assigned the driver to the xf86ConfigLayout
[    25.075] (II) LoadModule: "intel"
[    25.076] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.106] (II) Module intel: vendor="X.Org Foundation"
[    25.106]    compiled for 1.9.0, module version = 2.12.0
[    25.106]    Module class: X.Org Video Driver
[    25.106]    ABI class: X.Org Video Driver, version 8.0
[    25.106] (II) LoadModule: "vesa"
[    25.106] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.118] (II) Module vesa: vendor="X.Org Foundation"
[    25.118]    compiled for 1.8.99.905, module version = 2.3.0
[    25.118]    Module class: X.Org Video Driver
[    25.118]    ABI class: X.Org Video Driver, version 8.0
[    25.118] (II) LoadModule: "fbdev"
[    25.118] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.154] (II) Module fbdev: vendor="X.Org Foundation"
[    25.154]    compiled for 1.8.99.905, module version = 0.4.2
[    25.154]    ABI class: X.Org Video Driver, version 8.0
[    25.154] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
        Sandybridge, Sandybridge
[    25.154] (II) VESA: driver for VESA chipsets: vesa
[    25.154] (II) FBDEV: driver for framebuffer: fbdev
[    25.154] (++) using VT number 7
 
[    25.155] (WW) Falling back to old probe method for vesa
[    25.161] (WW) Falling back to old probe method for fbdev
[    25.161] (II) Loading sub module "fbdevhw"
[    25.161] (II) LoadModule: "fbdevhw"
[    25.162] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.315] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.315]    compiled for 1.9.0, module version = 0.0.2
[    25.315]    ABI class: X.Org Video Driver, version 8.0
[    25.317] drmOpenDevice: node name is /dev/dri/card0
[    25.317] drmOpenDevice: open result is 8, (OK)
[    25.317] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    25.317] drmOpenDevice: node name is /dev/dri/card0
[    25.317] drmOpenDevice: open result is 8, (OK)
[    25.317] drmOpenByBusid: drmOpenMinor returns 8
[    25.317] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    25.318] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    25.318] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    25.318] (==) intel(0): RGB weight 888
[    25.318] (==) intel(0): Default visual is TrueColor
[    25.318] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    25.318] (--) intel(0): Chipset: "945GM"
[    25.318] (==) intel(0): video overlay key set to 0x101fe
[    25.368] (II) intel(0): Output VGA1 has no monitor section
[    25.368] (II) intel(0): Output LVDS1 has no monitor section
[    25.368] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    25.720] (II) intel(0): Output TV1 has no monitor section
[    25.752] (II) intel(0): EDID for output VGA1
[    25.752] (II) intel(0): EDID for output LVDS1
[    25.752] (II) intel(0): Manufacturer: CMO  Model: 1554  Serial#: 0
[    25.752] (II) intel(0): Year: 2007  Week: 40
[    25.752] (II) intel(0): EDID Version: 1.3
[    25.752] (II) intel(0): Digital Display Input
[    25.752] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    25.752] (II) intel(0): Gamma: 2.20
[    25.752] (II) intel(0): No DPMS capabilities specified
[    25.752] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    25.752] (II) intel(0): First detailed timing is preferred mode
[    25.752] (II) intel(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
[    25.752] (II) intel(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    25.752] (II) intel(0): Manufacturer's mask: 0
[    25.752] (II) intel(0): Supported detailed timing:
[    25.752] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    25.752] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    25.752] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    25.752] (II) intel(0):  N154I3-L03
[    25.752] (II) intel(0):  CMO
[    25.752] (II) intel(0):  N154I3-L03
[    25.752] (II) intel(0): EDID (in hex):
[    25.752] (II) intel(0):     00ffffffffffff000daf541500000000
[    25.752] (II) intel(0):     28110103802115780a07f59a574e8726
[    25.752] (II) intel(0):     1e505400000001010101010101010101
[    25.752] (II) intel(0):     010101010101bc1b00a0502017303020
[    25.752] (II) intel(0):     36004bcf10000018000000fe004e3135
[    25.752] (II) intel(0):     3449332d4c30330a2020000000fe0043
[    25.752] (II) intel(0):     4d4f0a202020202020202020000000fe
[    25.752] (II) intel(0):     004e31353449332d4c30330a202000a5
[    25.752] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.752] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.752] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.752] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.753] (II) intel(0): Printing probed modes for output LVDS1
[    25.753] (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    25.753] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.753] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.753] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.753] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.088] (II) intel(0): EDID for output TV1
[    26.088] (II) intel(0): Output VGA1 disconnected
[    26.088] (II) intel(0): Output LVDS1 connected
[    26.088] (II) intel(0): Output TV1 disconnected
[    26.088] (II) intel(0): Using exact sizes for initial modes
[    26.088] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    26.088] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.088] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    26.088] (==) intel(0): DPI set to (96, 96)
[    26.088] (II) Loading sub module "fb"
[    26.088] (II) LoadModule: "fb"
[    26.088] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.126] (II) Module fb: vendor="X.Org Foundation"
[    26.126]    compiled for 1.9.0, module version = 1.0.0
[    26.126]    ABI class: X.Org ANSI C Emulation, version 0.4
[    26.126] (II) UnloadModule: "vesa"
[    26.126] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.126] (II) UnloadModule: "fbdev"
[    26.126] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.126] (II) UnloadModule: "fbdevhw"
[    26.126] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    26.126] (==) Depth 24 pixmap format is 32 bpp
[    26.126] (II) intel(0): [DRI2] Setup complete
[    26.126] (II) intel(0): [DRI2]   DRI driver: i915
[    26.126] (**) intel(0): Tiling enabled
[    26.126] (**) intel(0): SwapBuffers wait enabled
[    26.126] (==) intel(0): VideoRam: 262144 KB
[    26.126] (II) intel(0): Allocated new frame buffer 1280x800 stride 8192, tiled
[    26.154] (II) UXA(0): Driver registered support for the following operations:
[    26.154] (II)         solid
[    26.154] (II)         copy
[    26.154] (II)         composite (RENDER acceleration)
[    26.154] (II)         put_image
[    26.154] (II)         get_image
[    26.154] (==) intel(0): Backing store disabled
[    26.154] (==) intel(0): Silken mouse enabled
[    26.157] (II) intel(0): Initializing HW Cursor
[    26.196] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.236] (==) intel(0): DPMS enabled
[    26.236] (==) intel(0): Intel XvMC decoder disabled
[    26.236] (II) intel(0): Set up textured video
[    26.236] (II) intel(0): Set up overlay video
[    26.236] (II) intel(0): direct rendering: DRI2 Enabled
[    26.236] (--) RandR disabled
[    26.236] (II) Initializing built-in extension Generic Event Extension
[    26.236] (II) Initializing built-in extension SHAPE
[    26.236] (II) Initializing built-in extension MIT-SHM
[    26.236] (II) Initializing built-in extension XInputExtension
[    26.236] (II) Initializing built-in extension XTEST
[    26.236] (II) Initializing built-in extension BIG-REQUESTS
[    26.236] (II) Initializing built-in extension SYNC
[    26.236] (II) Initializing built-in extension XKEYBOARD
[    26.236] (II) Initializing built-in extension XC-MISC
[    26.236] (II) Initializing built-in extension SECURITY
[    26.236] (II) Initializing built-in extension XINERAMA
[    26.236] (II) Initializing built-in extension XFIXES
[    26.236] (II) Initializing built-in extension RENDER
[    26.236] (II) Initializing built-in extension RANDR
[    26.236] (II) Initializing built-in extension COMPOSITE
[    26.236] (II) Initializing built-in extension DAMAGE
[    26.236] (II) Initializing built-in extension GESTURE
[    26.429] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.430] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.430] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.430] (II) AIGLX: enabled GLX_SGI_make_current_read
[    26.430] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.430] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    26.430] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.430] (II) intel(0): Setting screen physical size to 338 x 211
[    26.755] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.789] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    26.789] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.789] (II) LoadModule: "evdev"
[    26.823] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.858] (II) Module evdev: vendor="X.Org Foundation"
[    26.859]    compiled for 1.9.0, module version = 2.3.2
[    26.859]    Module class: X.Org XInput Driver
[    26.859]    ABI class: X.Org XInput driver, version 11.0
[    26.859] (**) Power Button: always reports core events
[    26.859] (**) Power Button: Device: "/dev/input/event2"
[    26.859] (II) Power Button: Found keys
[    26.859] (II) Power Button: Configuring as keyboard
[    26.859] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.859] (**) Option "xkb_rules" "evdev"
[    26.859] (**) Option "xkb_model" "pc105"
[    26.859] (**) Option "xkb_layout" "us"
[    26.860] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    26.860] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.860] (**) Video Bus: always reports core events
[    26.860] (**) Video Bus: Device: "/dev/input/event4"
[    26.860] (II) Video Bus: Found keys
[    26.860] (II) Video Bus: Configuring as keyboard
[    26.860] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.860] (**) Option "xkb_rules" "evdev"
[    26.860] (**) Option "xkb_model" "pc105"
[    26.860] (**) Option "xkb_layout" "us"
[    26.862] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.862] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.862] (**) Power Button: always reports core events
[    26.862] (**) Power Button: Device: "/dev/input/event1"
[    26.862] (II) Power Button: Found keys
[    26.862] (II) Power Button: Configuring as keyboard
[    26.862] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.862] (**) Option "xkb_rules" "evdev"
[    26.862] (**) Option "xkb_model" "pc105"
[    26.862] (**) Option "xkb_layout" "us"
[    26.863] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.863] (II) No input driver/identifier specified (ignoring)
[    26.870] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    26.870] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.871] (**) AT Translated Set 2 keyboard: always reports core events
[    26.871] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    26.871] (II) AT Translated Set 2 keyboard: Found keys
[    26.871] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.871] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.871] (**) Option "xkb_rules" "evdev"
[    26.871] (**) Option "xkb_model" "pc105"
[    26.871] (**) Option "xkb_layout" "us"
[    26.871] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    26.871] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    26.871] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    26.871] (II) LoadModule: "synaptics"
[    26.872] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.910] (II) Module synaptics: vendor="X.Org Foundation"
[    26.910]    compiled for 1.9.0, module version = 1.2.2
[    26.910]    Module class: X.Org XInput Driver
[    26.910]    ABI class: X.Org XInput driver, version 11.0
[    26.910] (II) Synaptics touchpad driver version 1.2.2
[    26.910] (**) Option "Device" "/dev/input/event5"
[    26.910] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    26.910] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    26.910] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    26.910] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    26.910] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    26.910] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    26.910] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.910] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    26.910] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    26.910] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    26.910] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    26.910] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    26.910] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    26.911] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    26.911] (II) No input driver/identifier specified (ignoring)
[    31.768] (II) intel(0): EDID vendor "CMO", prod id 5460
[    31.768] (II) intel(0): Printing DDC gathered Modelines:
[    31.768] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    32.136] (II) intel(0): EDID vendor "CMO", prod id 5460
[    32.136] (II) intel(0): Printing DDC gathered Modelines:
[    32.136] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    32.552] (II) intel(0): EDID vendor "CMO", prod id 5460
[    32.552] (II) intel(0): Printing DDC gathered Modelines:
[    32.552] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    32.920] (II) intel(0): EDID vendor "CMO", prod id 5460
[    32.920] (II) intel(0): Printing DDC gathered Modelines:
[    32.920] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    86.888] (II) intel(0): EDID vendor "CMO", prod id 5460
[    86.888] (II) intel(0): Printing DDC gathered Modelines:
[    86.888] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    87.260] (II) intel(0): EDID vendor "CMO", prod id 5460
[    87.260] (II) intel(0): Printing DDC gathered Modelines:
[    87.260] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    87.628] (II) intel(0): EDID vendor "CMO", prod id 5460
[    87.628] (II) intel(0): Printing DDC gathered Modelines:
[    87.628] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    87.996] (II) intel(0): EDID vendor "CMO", prod id 5460
[    87.996] (II) intel(0): Printing DDC gathered Modelines:
[    87.996] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    94.624] (II) intel(0): EDID vendor "CMO", prod id 5460
[    94.624] (II) intel(0): Printing DDC gathered Modelines:
[    94.624] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   162.535] (II) config/udev: Adding input device UVC Camera (046d:080f) (/dev/input/event6)
[   162.535] (**) UVC Camera (046d:080f): Applying InputClass "evdev keyboard catchall"
[   162.535] (**) UVC Camera (046d:080f): always reports core events
[   162.535] (**) UVC Camera (046d:080f): Device: "/dev/input/event6"
[   162.535] (II) UVC Camera (046d:080f): Found keys
[   162.535] (II) UVC Camera (046d:080f): Configuring as keyboard
[   162.535] (II) XINPUT: Adding extended input device "UVC Camera (046d:080f)" (type: KEYBOARD)
[   162.535] (**) Option "xkb_rules" "evdev"
[   162.535] (**) Option "xkb_model" "pc105"
[   162.535] (**) Option "xkb_layout" "us"
[   211.986] (II) config/udev: removing device UVC Camera (046d:080f)
[   211.987] (II) UVC Camera (046d:080f): Close
[   211.987] (II) UnloadModule: "evdev"
[   302.036] (II) intel(0): EDID vendor "CMO", prod id 5460
[   302.036] (II) intel(0): Printing DDC gathered Modelines:
[   302.036] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   305.168] (II) intel(0): EDID vendor "CMO", prod id 5460
[   305.168] (II) intel(0): Printing DDC gathered Modelines:
[   305.168] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   306.500] (II) intel(0): EDID vendor "CMO", prod id 5460
[   306.500] (II) intel(0): Printing DDC gathered Modelines:
[   306.500] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   339.968] (II) intel(0): EDID vendor "CMO", prod id 5460
[   339.968] (II) intel(0): Printing DDC gathered Modelines:
[   339.968] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
```

---

### Post by linuxgeek77 on 2010-11-30
this is not CPU. this is VGA CARD!!!!!!

---

### Post by dcstar on 2010-11-30
> **linuxgeek77 said:**
> WHY is Ubuntu ignoring all the Intel problems after Ubuntu 10.04 got released? Ubuntu Never had a problem with intel cards in 9.10 
........

Because it probably is nothing that Ubuntu can control.

Ubuntu uses various Linux components, one being Xorg. When the latest Xorg release either drops support or only provide 2D support for old chipsets then it is bad luck - Ubuntu has to use what that component supplies.

As an example old Nvidia video chips disappeared from the Xorg support list a while ago, if old Ubuntu releases still support your hardware then the solution is to remain on that release or get a video card that is supported by the current Linux releases.

---

### Post by apollothethird on 2010-11-30
> **linuxgeek77 said:**
> WHY is Ubuntu ignoring all the Intel problems after Ubuntu 10.04 got released? Ubuntu Never had a problem with intel cards in 9.10 --No luck with intel 945GM? I looked everywhere with loads of bug reports and No solution. I had this problem since ubuntu 10.4 but it started in 9.10. I only get 30-40 FPS on glxgear which used to give me 1500+ before. I cant play a simple 2D game anymore. There are no solutions I have looked. WHY did ubuntu / linux/ MESS UP intel so bad? I have been using ubuntu / linux in gerneral for 4 years and I am going back to windows. F linux. F ubuntu. IF you have an intel card and run ubuntu YOU CANT DO ANY OF the stuff you were able to do a YEAR AGO. Linux will never reach the seamless stability of proprietary software. 

IF the new kernel+intel drivers dont work then DONT use them. use a different older driver. DONT integrate things that dont work. TEST IT OUT ON REAL HARDWARE AND ACTUALLY FIX IT. 

I am done with ubuntu. I am here to say good bye for all the frustrations ubuntu caused me after it gave me a false hope. 

AND YES I HAVE TRIED EVERYTHING 
HERE IS MY XORG.LOG file:

```
[    24.651]
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    24.652] X Protocol Version 11, Revision 0
[    24.652] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    24.652] Current Operating System: Linux danni-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    24.652] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=da6b1a2b-cc48-49fb-8836-3881c9478d5f ro quiet splash
[    24.652] Build Date: 16 September 2010  05:39:22PM
[    24.652] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    24.669] Current version of pixman: 0.18.4
[    24.669]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    24.669] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.669] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 29 23:08:27 2010
[    24.728] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.815] (==) No Layout section.  Using the first Screen section.
[    24.815] (==) No screen section available. Using defaults.
[    24.815] (**) |-->Screen "Default Screen Section" (0)
[    24.815] (**) |   |-->Monitor "<default monitor>"
[    24.816] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    24.816] (==) Automatically adding devices
[    24.816] (==) Automatically enabling devices
[    24.862] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.862]    Entry deleted from font path.
[    24.897] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    24.897] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.897] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.897] (II) Loader magic: 0x81f8e00
[    24.897] (II) Module ABI versions:
[    24.897]    X.Org ANSI C Emulation: 0.4
[    24.897]    X.Org Video Driver: 8.0
[    24.897]    X.Org XInput driver : 11.0
[    24.897]    X.Org Server Extension : 4.0
[    24.899] (--) PCI:*(0:0:2:0) 8086:27a2:1179:ff02 rev 3, Mem @ 0xdc100000/524288, 0xc0000000/268435456, 0xdc200000/262144, I/O @ 0x00001800/8
[    24.899] (--) PCI: (0:0:2:1) 8086:27a6:1179:ff02 rev 3, Mem @ 0xdc180000/524288
[    24.899] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    24.899] (II) LoadModule: "extmod"
[    25.023] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.035] (II) Module extmod: vendor="X.Org Foundation"
[    25.035]    compiled for 1.9.0, module version = 1.0.0
[    25.035]    Module class: X.Org Server Extension
[    25.035]    ABI class: X.Org Server Extension, version 4.0
[    25.035] (II) Loading extension MIT-SCREEN-SAVER
[    25.035] (II) Loading extension XFree86-VidModeExtension
[    25.035] (II) Loading extension XFree86-DGA
[    25.035] (II) Loading extension DPMS
[    25.035] (II) Loading extension XVideo
[    25.035] (II) Loading extension XVideo-MotionCompensation
[    25.035] (II) Loading extension X-Resource
[    25.035] (II) LoadModule: "dbe"
[    25.035] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.036] (II) Module dbe: vendor="X.Org Foundation"
[    25.036]    compiled for 1.9.0, module version = 1.0.0
[    25.036]    Module class: X.Org Server Extension
[    25.036]    ABI class: X.Org Server Extension, version 4.0
[    25.036] (II) Loading extension DOUBLE-BUFFER
[    25.036] (II) LoadModule: "glx"
[    25.036] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.048] (II) Module glx: vendor="X.Org Foundation"
[    25.048]    compiled for 1.9.0, module version = 1.0.0
[    25.048]    ABI class: X.Org Server Extension, version 4.0
[    25.049] (==) AIGLX enabled
[    25.049] (II) Loading extension GLX
[    25.049] (II) LoadModule: "record"
[    25.050] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.050] (II) Module record: vendor="X.Org Foundation"
[    25.050]    compiled for 1.9.0, module version = 1.13.0
[    25.050]    Module class: X.Org Server Extension
[    25.050]    ABI class: X.Org Server Extension, version 4.0
[    25.050] (II) Loading extension RECORD
[    25.050] (II) LoadModule: "dri"
[    25.051] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.074] (II) Module dri: vendor="X.Org Foundation"
[    25.074]    compiled for 1.9.0, module version = 1.0.0
[    25.074]    ABI class: X.Org Server Extension, version 4.0
[    25.074] (II) Loading extension XFree86-DRI
[    25.074] (II) LoadModule: "dri2"
[    25.075] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.075] (II) Module dri2: vendor="X.Org Foundation"
[    25.075]    compiled for 1.9.0, module version = 1.2.0
[    25.075]    ABI class: X.Org Server Extension, version 4.0
[    25.075] (II) Loading extension DRI2
[    25.075] (==) Matched intel as autoconfigured driver 0
[    25.075] (==) Matched vesa as autoconfigured driver 1
[    25.075] (==) Matched fbdev as autoconfigured driver 2
[    25.075] (==) Assigned the driver to the xf86ConfigLayout
[    25.075] (II) LoadModule: "intel"
[    25.076] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.106] (II) Module intel: vendor="X.Org Foundation"
[    25.106]    compiled for 1.9.0, module version = 2.12.0
[    25.106]    Module class: X.Org Video Driver
[    25.106]    ABI class: X.Org Video Driver, version 8.0
[    25.106] (II) LoadModule: "vesa"
[    25.106] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.118] (II) Module vesa: vendor="X.Org Foundation"
[    25.118]    compiled for 1.8.99.905, module version = 2.3.0
[    25.118]    Module class: X.Org Video Driver
[    25.118]    ABI class: X.Org Video Driver, version 8.0
[    25.118] (II) LoadModule: "fbdev"
[    25.118] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.154] (II) Module fbdev: vendor="X.Org Foundation"
[    25.154]    compiled for 1.8.99.905, module version = 0.4.2
[    25.154]    ABI class: X.Org Video Driver, version 8.0
[    25.154] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
        Sandybridge, Sandybridge
[    25.154] (II) VESA: driver for VESA chipsets: vesa
[    25.154] (II) FBDEV: driver for framebuffer: fbdev
[    25.154] (++) using VT number 7
 
[    25.155] (WW) Falling back to old probe method for vesa
[    25.161] (WW) Falling back to old probe method for fbdev
[    25.161] (II) Loading sub module "fbdevhw"
[    25.161] (II) LoadModule: "fbdevhw"
[    25.162] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.315] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.315]    compiled for 1.9.0, module version = 0.0.2
[    25.315]    ABI class: X.Org Video Driver, version 8.0
[    25.317] drmOpenDevice: node name is /dev/dri/card0
[    25.317] drmOpenDevice: open result is 8, (OK)
[    25.317] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    25.317] drmOpenDevice: node name is /dev/dri/card0
[    25.317] drmOpenDevice: open result is 8, (OK)
[    25.317] drmOpenByBusid: drmOpenMinor returns 8
[    25.317] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    25.318] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    25.318] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    25.318] (==) intel(0): RGB weight 888
[    25.318] (==) intel(0): Default visual is TrueColor
[    25.318] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    25.318] (--) intel(0): Chipset: "945GM"
[    25.318] (==) intel(0): video overlay key set to 0x101fe
[    25.368] (II) intel(0): Output VGA1 has no monitor section
[    25.368] (II) intel(0): Output LVDS1 has no monitor section
[    25.368] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    25.720] (II) intel(0): Output TV1 has no monitor section
[    25.752] (II) intel(0): EDID for output VGA1
[    25.752] (II) intel(0): EDID for output LVDS1
[    25.752] (II) intel(0): Manufacturer: CMO  Model: 1554  Serial#: 0
[    25.752] (II) intel(0): Year: 2007  Week: 40
[    25.752] (II) intel(0): EDID Version: 1.3
[    25.752] (II) intel(0): Digital Display Input
[    25.752] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    25.752] (II) intel(0): Gamma: 2.20
[    25.752] (II) intel(0): No DPMS capabilities specified
[    25.752] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    25.752] (II) intel(0): First detailed timing is preferred mode
[    25.752] (II) intel(0): redX: 0.602 redY: 0.340   greenX: 0.306 greenY: 0.530
[    25.752] (II) intel(0): blueX: 0.151 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    25.752] (II) intel(0): Manufacturer's mask: 0
[    25.752] (II) intel(0): Supported detailed timing:
[    25.752] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    25.752] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    25.752] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    25.752] (II) intel(0):  N154I3-L03
[    25.752] (II) intel(0):  CMO
[    25.752] (II) intel(0):  N154I3-L03
[    25.752] (II) intel(0): EDID (in hex):
[    25.752] (II) intel(0):     00ffffffffffff000daf541500000000
[    25.752] (II) intel(0):     28110103802115780a07f59a574e8726
[    25.752] (II) intel(0):     1e505400000001010101010101010101
[    25.752] (II) intel(0):     010101010101bc1b00a0502017303020
[    25.752] (II) intel(0):     36004bcf10000018000000fe004e3135
[    25.752] (II) intel(0):     3449332d4c30330a2020000000fe0043
[    25.752] (II) intel(0):     4d4f0a202020202020202020000000fe
[    25.752] (II) intel(0):     004e31353449332d4c30330a202000a5
[    25.752] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.752] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.752] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.752] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.753] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.753] (II) intel(0): Printing probed modes for output LVDS1
[    25.753] (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    25.753] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.753] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.753] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.753] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.088] (II) intel(0): EDID for output TV1
[    26.088] (II) intel(0): Output VGA1 disconnected
[    26.088] (II) intel(0): Output LVDS1 connected
[    26.088] (II) intel(0): Output TV1 disconnected
[    26.088] (II) intel(0): Using exact sizes for initial modes
[    26.088] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    26.088] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.088] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    26.088] (==) intel(0): DPI set to (96, 96)
[    26.088] (II) Loading sub module "fb"
[    26.088] (II) LoadModule: "fb"
[    26.088] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.126] (II) Module fb: vendor="X.Org Foundation"
[    26.126]    compiled for 1.9.0, module version = 1.0.0
[    26.126]    ABI class: X.Org ANSI C Emulation, version 0.4
[    26.126] (II) UnloadModule: "vesa"
[    26.126] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.126] (II) UnloadModule: "fbdev"
[    26.126] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.126] (II) UnloadModule: "fbdevhw"
[    26.126] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    26.126] (==) Depth 24 pixmap format is 32 bpp
[    26.126] (II) intel(0): [DRI2] Setup complete
[    26.126] (II) intel(0): [DRI2]   DRI driver: i915
[    26.126] (**) intel(0): Tiling enabled
[    26.126] (**) intel(0): SwapBuffers wait enabled
[    26.126] (==) intel(0): VideoRam: 262144 KB
[    26.126] (II) intel(0): Allocated new frame buffer 1280x800 stride 8192, tiled
[    26.154] (II) UXA(0): Driver registered support for the following operations:
[    26.154] (II)         solid
[    26.154] (II)         copy
[    26.154] (II)         composite (RENDER acceleration)
[    26.154] (II)         put_image
[    26.154] (II)         get_image
[    26.154] (==) intel(0): Backing store disabled
[    26.154] (==) intel(0): Silken mouse enabled
[    26.157] (II) intel(0): Initializing HW Cursor
[    26.196] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.236] (==) intel(0): DPMS enabled
[    26.236] (==) intel(0): Intel XvMC decoder disabled
[    26.236] (II) intel(0): Set up textured video
[    26.236] (II) intel(0): Set up overlay video
[    26.236] (II) intel(0): direct rendering: DRI2 Enabled
[    26.236] (--) RandR disabled
[    26.236] (II) Initializing built-in extension Generic Event Extension
[    26.236] (II) Initializing built-in extension SHAPE
[    26.236] (II) Initializing built-in extension MIT-SHM
[    26.236] (II) Initializing built-in extension XInputExtension
[    26.236] (II) Initializing built-in extension XTEST
[    26.236] (II) Initializing built-in extension BIG-REQUESTS
[    26.236] (II) Initializing built-in extension SYNC
[    26.236] (II) Initializing built-in extension XKEYBOARD
[    26.236] (II) Initializing built-in extension XC-MISC
[    26.236] (II) Initializing built-in extension SECURITY
[    26.236] (II) Initializing built-in extension XINERAMA
[    26.236] (II) Initializing built-in extension XFIXES
[    26.236] (II) Initializing built-in extension RENDER
[    26.236] (II) Initializing built-in extension RANDR
[    26.236] (II) Initializing built-in extension COMPOSITE
[    26.236] (II) Initializing built-in extension DAMAGE
[    26.236] (II) Initializing built-in extension GESTURE
[    26.429] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.430] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.430] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.430] (II) AIGLX: enabled GLX_SGI_make_current_read
[    26.430] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.430] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    26.430] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.430] (II) intel(0): Setting screen physical size to 338 x 211
[    26.755] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.789] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    26.789] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.789] (II) LoadModule: "evdev"
[    26.823] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.858] (II) Module evdev: vendor="X.Org Foundation"
[    26.859]    compiled for 1.9.0, module version = 2.3.2
[    26.859]    Module class: X.Org XInput Driver
[    26.859]    ABI class: X.Org XInput driver, version 11.0
[    26.859] (**) Power Button: always reports core events
[    26.859] (**) Power Button: Device: "/dev/input/event2"
[    26.859] (II) Power Button: Found keys
[    26.859] (II) Power Button: Configuring as keyboard
[    26.859] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.859] (**) Option "xkb_rules" "evdev"
[    26.859] (**) Option "xkb_model" "pc105"
[    26.859] (**) Option "xkb_layout" "us"
[    26.860] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    26.860] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.860] (**) Video Bus: always reports core events
[    26.860] (**) Video Bus: Device: "/dev/input/event4"
[    26.860] (II) Video Bus: Found keys
[    26.860] (II) Video Bus: Configuring as keyboard
[    26.860] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.860] (**) Option "xkb_rules" "evdev"
[    26.860] (**) Option "xkb_model" "pc105"
[    26.860] (**) Option "xkb_layout" "us"
[    26.862] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.862] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.862] (**) Power Button: always reports core events
[    26.862] (**) Power Button: Device: "/dev/input/event1"
[    26.862] (II) Power Button: Found keys
[    26.862] (II) Power Button: Configuring as keyboard
[    26.862] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.862] (**) Option "xkb_rules" "evdev"
[    26.862] (**) Option "xkb_model" "pc105"
[    26.862] (**) Option "xkb_layout" "us"
[    26.863] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.863] (II) No input driver/identifier specified (ignoring)
[    26.870] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    26.870] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.871] (**) AT Translated Set 2 keyboard: always reports core events
[    26.871] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    26.871] (II) AT Translated Set 2 keyboard: Found keys
[    26.871] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.871] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.871] (**) Option "xkb_rules" "evdev"
[    26.871] (**) Option "xkb_model" "pc105"
[    26.871] (**) Option "xkb_layout" "us"
[    26.871] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    26.871] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    26.871] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    26.871] (II) LoadModule: "synaptics"
[    26.872] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.910] (II) Module synaptics: vendor="X.Org Foundation"
[    26.910]    compiled for 1.9.0, module version = 1.2.2
[    26.910]    Module class: X.Org XInput Driver
[    26.910]    ABI class: X.Org XInput driver, version 11.0
[    26.910] (II) Synaptics touchpad driver version 1.2.2
[    26.910] (**) Option "Device" "/dev/input/event5"
[    26.910] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    26.910] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    26.910] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    26.910] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    26.910] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    26.910] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    26.910] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    26.910] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    26.910] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    26.910] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    26.910] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    26.910] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    26.910] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    26.911] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    26.911] (II) No input driver/identifier specified (ignoring)
[    31.768] (II) intel(0): EDID vendor "CMO", prod id 5460
[    31.768] (II) intel(0): Printing DDC gathered Modelines:
[    31.768] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    32.136] (II) intel(0): EDID vendor "CMO", prod id 5460
[    32.136] (II) intel(0): Printing DDC gathered Modelines:
[    32.136] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    32.552] (II) intel(0): EDID vendor "CMO", prod id 5460
[    32.552] (II) intel(0): Printing DDC gathered Modelines:
[    32.552] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    32.920] (II) intel(0): EDID vendor "CMO", prod id 5460
[    32.920] (II) intel(0): Printing DDC gathered Modelines:
[    32.920] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    86.888] (II) intel(0): EDID vendor "CMO", prod id 5460
[    86.888] (II) intel(0): Printing DDC gathered Modelines:
[    86.888] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    87.260] (II) intel(0): EDID vendor "CMO", prod id 5460
[    87.260] (II) intel(0): Printing DDC gathered Modelines:
[    87.260] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    87.628] (II) intel(0): EDID vendor "CMO", prod id 5460
[    87.628] (II) intel(0): Printing DDC gathered Modelines:
[    87.628] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    87.996] (II) intel(0): EDID vendor "CMO", prod id 5460
[    87.996] (II) intel(0): Printing DDC gathered Modelines:
[    87.996] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    94.624] (II) intel(0): EDID vendor "CMO", prod id 5460
[    94.624] (II) intel(0): Printing DDC gathered Modelines:
[    94.624] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   162.535] (II) config/udev: Adding input device UVC Camera (046d:080f) (/dev/input/event6)
[   162.535] (**) UVC Camera (046d:080f): Applying InputClass "evdev keyboard catchall"
[   162.535] (**) UVC Camera (046d:080f): always reports core events
[   162.535] (**) UVC Camera (046d:080f): Device: "/dev/input/event6"
[   162.535] (II) UVC Camera (046d:080f): Found keys
[   162.535] (II) UVC Camera (046d:080f): Configuring as keyboard
[   162.535] (II) XINPUT: Adding extended input device "UVC Camera (046d:080f)" (type: KEYBOARD)
[   162.535] (**) Option "xkb_rules" "evdev"
[   162.535] (**) Option "xkb_model" "pc105"
[   162.535] (**) Option "xkb_layout" "us"
[   211.986] (II) config/udev: removing device UVC Camera (046d:080f)
[   211.987] (II) UVC Camera (046d:080f): Close
[   211.987] (II) UnloadModule: "evdev"
[   302.036] (II) intel(0): EDID vendor "CMO", prod id 5460
[   302.036] (II) intel(0): Printing DDC gathered Modelines:
[   302.036] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   305.168] (II) intel(0): EDID vendor "CMO", prod id 5460
[   305.168] (II) intel(0): Printing DDC gathered Modelines:
[   305.168] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   306.500] (II) intel(0): EDID vendor "CMO", prod id 5460
[   306.500] (II) intel(0): Printing DDC gathered Modelines:
[   306.500] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[   339.968] (II) intel(0): EDID vendor "CMO", prod id 5460
[   339.968] (II) intel(0): Printing DDC gathered Modelines:
[   339.968] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz
```

Hi, Linuxgeek.

Will you post to us a list of links to the topics where you tried to get help for your issue so that we can see what has already failed?  Or some of your posts on the matter that went unanswered?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by proxess on 2010-11-30
3 or 4 year old GPU is old. My radeon 2350 or whatever it was got support dropped in under 2 years. It wasn't Ubuntu no Linux fault, it was AMDs. Actually, the community saved the CPU from peril with the decent FOSS Radeon drivers.

Now I've also got an EeePC with an Intel 945GME and it works more than fine.

---

### Post by linuxgeek77 on 2010-11-30
> **apollothethird said:**
> Hi, Linuxgeek.

Will you post to us a list of links to the topics where you tried to get help for your issue so that we can see what has already failed?  Or some of your posts on the matter that went unanswered?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)
I have tried everything I could find in the forums / google/ web8/ ubuntugeek. just google "intel 945GM ubuntu" I even tried to change kernels ( old/new). Install the older intel drivers. Edit Xorg.conf after creating one. Everything posted online I have tried. and if you take a look at the posts none of them were solved. There are plenty of online postings on intel 945GM none are resolved. there is one that suggests going back from 9.10 to 9.04. but that would not work from 10.10 to 9.04 the kernel would not allow it.

---

### Post by Quackers on 2010-11-30
To go back to a previous Ubuntu version you must re-install the previous version. There is no other way to regress.

---

### Post by uRock on 2010-11-30
I have removed all of the off topic posts, again. Please stay on topic.

Thanks,
uRock

---

