---
title: "Ubuntu 13.10 Blacksreen after Startx"
date: 2013-07-06
forum: Ubuntu Development Version
---

### Post by Scofa on 2013-07-06
Hey guys, i installed today Ubuntu 13.10 Saucy Salamander on my new MSI Gt70-One Laptop.

The installation of Ubuntu with kernel 3.10.0-2-generic worked perfectly.

Then i tryed to install the Nvidia  325.08 driver, all fine. The driver is installed and loaded

lsmod | grep nvidia:

[COLOR=#ff0000]nvidia[/COLOR]           9357002   0
drm              289960    4      i915,drm_kms_helper,[COLOR=#ff0000]nvidia[/COLOR]


but when i typ startx, i just get an blackscreen...

whos got any ideas?

---

### Post by zika on 2013-07-06
> **Scofa said:**
> Hey guys, i installed today Ubuntu 13.10 Saucy Salamander on my new MSI Gt70-One Laptop.

The installation of Ubuntu with kernel 3.10.0-2-generic worked perfectly.

Then i tryed to install the Nvidia  325.08 driver, all fine. The driver is installed and loaded

lsmod | grep nvidia:

[COLOR=#ff0000]nvidia[/COLOR]           9357002   0
drm              289960    4      i915,drm_kms_helper,[COLOR=#ff0000]nvidia[/COLOR]


but when i typ startx, i just get an blackscreen...

whos got any ideas?
What is in errors-log?

---

### Post by Scofa on 2013-07-06
Well i post it when im finish with the installation of Windows 7

---

### Post by wojox on 2013-07-06
Try:
```
sudo service lightdm start
```

---

### Post by grahammechanical on 2013-07-06
Revert back to the driver that was in use after after the installation.

Regards

---

### Post by Scofa on 2013-07-06
service lightdm start didnt work, becouse if got gdm, and the start of gdm didnt work too

ehm its an fresh installation, its used nouveau befor

---

### Post by wojox on 2013-07-06
You got a fresh install of 13.10 with Gdm installed by default?

---

### Post by Scofa on 2013-07-06
I installed Ubuntu Saucy Salamander Gnome. btw here are the ouputs of my Xorg log file:
```
[     5.477] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[     5.477] X Protocol Version 11, Revision 0
[     5.477] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[     5.477] Current Operating System: Linux Cru-Z 3.10.0-2-generic #10-Ubuntu SMP Fri Jul 5 18:03:52 UTC 2013 x86_64
[     5.477] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.10.0-2-generic root=UUID=a27b04f3-c658-4aa6-bb13-7098a3308a0c ro quiet splash
[     5.477] Build Date: 17 June 2013  12:30:59PM
[     5.477] xorg-server 2:1.13.3-0ubuntu13 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     5.477] Current version of pixman: 0.28.2
[     5.477]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     5.477] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.477] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  6 15:18:33 2013
[     5.477] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.477] (==) No Layout section.  Using the first Screen section.
[     5.477] (==) No screen section available. Using defaults.
[     5.478] (**) |-->Screen "Default Screen Section" (0)
[     5.478] (**) |   |-->Monitor "<default monitor>"
[     5.478] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.478] (==) Automatically adding devices
[     5.478] (==) Automatically enabling devices
[     5.478] (==) Automatically adding GPU devices
[     5.478] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.478]     Entry deleted from font path.
[     5.478] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.478]     Entry deleted from font path.
[     5.478] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.478]     Entry deleted from font path.
[     5.478] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.478]     Entry deleted from font path.
[     5.478] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.478]     Entry deleted from font path.
[     5.478] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     5.478]     Entry deleted from font path.
[     5.478] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.478] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.478] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.478] (II) Loader magic: 0x7f8d9993fd20
[     5.478] (II) Module ABI versions:
[     5.478]     X.Org ANSI C Emulation: 0.4
[     5.478]     X.Org Video Driver: 13.1
[     5.478]     X.Org XInput driver : 18.0
[     5.478]     X.Org Server Extension : 7.0
[     5.478] (II) config/udev: Adding drm device (/dev/dri/card0)
[     5.478] (II) config/udev: Adding drm device (/dev/dri/card1)
[     5.480] (--) PCI:*(0:0:2:0) 8086:0166:1462:10d9 rev 9, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[     5.480] (--) PCI: (0:1:0:0) 10de:11a7:1462:10d9 rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     5.480] (II) Open ACPI successful (/var/run/acpid.socket)
[     5.480] Initializing built-in extension Generic Event Extension
[     5.480] Initializing built-in extension SHAPE
[     5.480] Initializing built-in extension MIT-SHM
[     5.480] Initializing built-in extension XInputExtension
[     5.480] Initializing built-in extension XTEST
[     5.480] Initializing built-in extension BIG-REQUESTS
[     5.480] Initializing built-in extension SYNC
[     5.480] Initializing built-in extension XKEYBOARD
[     5.480] Initializing built-in extension XC-MISC
[     5.480] Initializing built-in extension SECURITY
[     5.480] Initializing built-in extension XINERAMA
[     5.480] Initializing built-in extension XFIXES
[     5.480] Initializing built-in extension RENDER
[     5.480] Initializing built-in extension RANDR
[     5.480] Initializing built-in extension COMPOSITE
[     5.480] Initializing built-in extension DAMAGE
[     5.480] Initializing built-in extension MIT-SCREEN-SAVER
[     5.480] Initializing built-in extension DOUBLE-BUFFER
[     5.480] Initializing built-in extension RECORD
[     5.480] Initializing built-in extension DPMS
[     5.480] Initializing built-in extension X-Resource
[     5.480] Initializing built-in extension XVideo
[     5.480] Initializing built-in extension XVideo-MotionCompensation
[     5.480] Initializing built-in extension SELinux
[     5.480] Initializing built-in extension XFree86-VidModeExtension
[     5.480] Initializing built-in extension XFree86-DGA
[     5.480] Initializing built-in extension XFree86-DRI
[     5.480] Initializing built-in extension DRI2
[     5.480] (II) LoadModule: "glx"
[     5.481] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     5.505] (II) Module glx: vendor="NVIDIA Corporation"
[     5.505]     compiled for 4.0.2, module version = 1.0.0
[     5.505]     Module class: X.Org Server Extension
[     5.505] (II) NVIDIA GLX Module  325.08  Wed Jun 26 17:51:26 PDT 2013
[     5.505] Loading extension GLX
[     5.505] (==) Matched intel as autoconfigured driver 0
[     5.505] (==) Matched nvidia as autoconfigured driver 1
[     5.505] (==) Matched nouveau as autoconfigured driver 2
[     5.505] (==) Matched intel as autoconfigured driver 3
[     5.505] (==) Matched vesa as autoconfigured driver 4
[     5.505] (==) Matched modesetting as autoconfigured driver 5
[     5.505] (==) Matched fbdev as autoconfigured driver 6
[     5.505] (==) Assigned the driver to the xf86ConfigLayout
[     5.506] (II) LoadModule: "intel"
[     5.507] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.508] (II) Module intel: vendor="X.Org Foundation"
[     5.508]     compiled for 1.13.3, module version = 2.21.9
[     5.508]     Module class: X.Org Video Driver
[     5.508]     ABI class: X.Org Video Driver, version 13.1
[     5.508] (II) LoadModule: "nvidia"
[     5.508] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.514] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.514]     compiled for 4.0.2, module version = 1.0.0
[     5.514]     Module class: X.Org Video Driver
[     5.515] (II) LoadModule: "nouveau"
[     5.515] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     5.517] (II) Module nouveau: vendor="X.Org Foundation"
[     5.517]     compiled for 1.13.3, module version = 1.0.8
[     5.517]     Module class: X.Org Video Driver
[     5.517]     ABI class: X.Org Video Driver, version 13.1
[     5.517] (II) LoadModule: "vesa"
[     5.517] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.517] (II) Module vesa: vendor="X.Org Foundation"
[     5.517]     compiled for 1.12.99.902, module version = 2.3.2
[     5.517]     Module class: X.Org Video Driver
[     5.517]     ABI class: X.Org Video Driver, version 13.0
[     5.517] (II) LoadModule: "modesetting"
[     5.518] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.518] (II) Module modesetting: vendor="X.Org Foundation"
[     5.518]     compiled for 1.13.3, module version = 0.8.0
[     5.518]     Module class: X.Org Video Driver
[     5.518]     ABI class: X.Org Video Driver, version 13.1
[     5.518] (II) LoadModule: "fbdev"
[     5.518] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.518] (II) Module fbdev: vendor="X.Org Foundation"
[     5.518]     compiled for 1.12.99.902, module version = 0.4.3
[     5.518]     Module class: X.Org Video Driver
[     5.518]     ABI class: X.Org Video Driver, version 13.0
[     5.518] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), HD Graphics, HD Graphics 4600,
    Haswell Desktop (GT3), HD Graphics, HD Graphics 4600,
    Haswell Mobile (GT3), HD Graphics, HD Graphics P4600/P4700,
    Haswell Server (GT3), Haswell (GT1), Haswell (GT2), Haswell (GT3),
    HD Graphics, Haswell (GT2), Haswell (GT3), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT3),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT3), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4400,
    HD Graphics 5000, Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Iris(TM) Graphics 5100, Haswell ULT (GT1), Haswell ULT (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4200,
    Iris(TM) Graphics 5100, Haswell CRW Desktop (GT1), HD Graphics 4600,
    Iris(TM) Pro Graphics 5200, Haswell CRW Mobile (GT1),
    HD Graphics 4600, Iris(TM) Pro Graphics 5200,
    Haswell CRW Server (GT1), Haswell CRW Server (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, ValleyView PO board
[     5.520] (II) NVIDIA dlloader X Driver  325.08  Wed Jun 26 17:32:32 PDT 2013
[     5.520] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.520] (II) NOUVEAU driver Date:   Wed Jun 12 10:46:39 2013 +0200
[     5.520] (II) NOUVEAU driver for NVIDIA chipset families :
[     5.520]     RIVA TNT        (NV04)
[     5.520]     RIVA TNT2       (NV05)
[     5.520]     GeForce 256     (NV10)
[     5.520]     GeForce 2       (NV11, NV15)
[     5.520]     GeForce 4MX     (NV17, NV18)
[     5.520]     GeForce 3       (NV20)
[     5.520]     GeForce 4Ti     (NV25, NV28)
[     5.520]     GeForce FX      (NV3x)
[     5.520]     GeForce 6       (NV4x)
[     5.520]     GeForce 7       (G7x)
[     5.520]     GeForce 8       (G8x)
[     5.520]     GeForce GTX 200 (NVA0)
[     5.520]     GeForce GTX 400 (NVC0)
[     5.520] (II) VESA: driver for VESA chipsets: vesa
[     5.520] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.520] (II) FBDEV: driver for framebuffer: fbdev
[     5.520] (++) using VT number 7

[     5.521] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.9-0ubuntu2 (Timo Aaltonen <tjaalton@ubuntu.com>)
[     5.521] (EE) [drm] KMS not enabled
[     5.521] (WW) Falling back to old probe method for vesa
[     5.521] (WW) Falling back to old probe method for modesetting
[     5.521] (WW) Falling back to old probe method for fbdev
[     5.521] (II) Loading sub module "fbdevhw"
[     5.521] (II) LoadModule: "fbdevhw"
[     5.521] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.521] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.521]     compiled for 1.13.3, module version = 0.0.2
[     5.521]     ABI class: X.Org Video Driver, version 13.1
[     5.521] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.521] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     5.521] (==) intel(0): RGB weight 888
[     5.521] (==) intel(0): Default visual is TrueColor
[     5.521] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[     5.522] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[     5.522] (**) intel(0): Framebuffer tiled
[     5.522] (**) intel(0): Pixmaps tiled
[     5.522] (**) intel(0): "Tear free" disabled
[     5.522] (**) intel(0): Forcing per-crtc-pixmaps? no
[     5.522] (II) intel(0): Output LVDS1 has no monitor section
[     5.558] (--) intel(0): found backlight control interface acpi_video1 (type 'firmware')
[     5.559] (II) intel(0): Output VGA1 has no monitor section
[     5.609] (II) intel(0): Output HDMI1 has no monitor section
[     5.660] (II) intel(0): Output DP1 has no monitor section
[     5.660] (II) intel(0): EDID for output LVDS1
[     5.660] (II) intel(0): Manufacturer: CMO  Model: 1720  Serial#: 0
[     5.660] (II) intel(0): Year: 2011  Week: 2
[     5.660] (II) intel(0): EDID Version: 1.3
[     5.660] (II) intel(0): Digital Display Input
[     5.660] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[     5.660] (II) intel(0): Gamma: 2.20
[     5.660] (II) intel(0): No DPMS capabilities specified
[     5.660] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     5.660] (II) intel(0): First detailed timing is preferred mode
[     5.660] (II) intel(0): redX: 0.640 redY: 0.333   greenX: 0.303 greenY: 0.613
[     5.660] (II) intel(0): blueX: 0.154 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[     5.660] (II) intel(0): Manufacturer's mask: 0
[     5.660] (II) intel(0): Supported detailed timing:
[     5.660] (II) intel(0): clock: 138.7 MHz   Image Size:  382 x 215 mm
[     5.660] (II) intel(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[     5.660] (II) intel(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[     5.660] (II) intel(0):  N173HGE-L11
[     5.660] (II) intel(0):  CMO
[     5.660] (II) intel(0):  N173HGE-L11
[     5.660] (II) intel(0): EDID (in hex):
[     5.660] (II) intel(0):     00ffffffffffff000daf201700000000
[     5.660] (II) intel(0):     02150103802615780ad895a3554d9d27
[     5.660] (II) intel(0):     0f505400000001010101010101010101
[     5.660] (II) intel(0):     0101010101012e3680a070381f403020
[     5.660] (II) intel(0):     35007ed710000018000000fe004e3137
[     5.660] (II) intel(0):     334847452d4c31310a20000000fe0043
[     5.660] (II) intel(0):     4d4f0a202020202020202020000000fe
[     5.660] (II) intel(0):     004e3137334847452d4c31310a20006e
[     5.660] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[     5.660] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[     5.660] (II) intel(0): Printing probed modes for output LVDS1
[     5.660] (II) intel(0): Modeline "1920x1080"x60.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[     5.660] (II) intel(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[     5.660] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[     5.660] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[     5.660] (II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[     5.660] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[     5.660] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[     5.660] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[     5.660] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[     5.660] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[     5.660] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[     5.660] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[     5.660] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[     5.660] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[     5.660] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[     5.661] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[     5.662] (II) intel(0): EDID for output VGA1
[     5.712] (II) intel(0): EDID for output HDMI1
[     5.712] (II) intel(0): Manufacturer: ACR  Model: ea  Serial#: 1086601
[     5.712] (II) intel(0): Year: 2010  Week: 1
[     5.712] (II) intel(0): EDID Version: 1.3
[     5.712] (II) intel(0): Digital Display Input
[     5.712] (II) intel(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[     5.712] (II) intel(0): Gamma: 2.20
[     5.712] (II) intel(0): DPMS capabilities: Off
[     5.712] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     5.712] (II) intel(0): First detailed timing is preferred mode
[     5.712] (II) intel(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[     5.712] (II) intel(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[     5.712] (II) intel(0): Supported established timings:
[     5.712] (II) intel(0): 720x400@70Hz
[     5.712] (II) intel(0): 640x480@60Hz
[     5.712] (II) intel(0): 640x480@67Hz
[     5.712] (II) intel(0): 800x600@56Hz
[     5.712] (II) intel(0): 800x600@60Hz
[     5.712] (II) intel(0): 1024x768@60Hz
[     5.712] (II) intel(0): 1024x768@70Hz
[     5.712] (II) intel(0): Manufacturer's mask: 0
[     5.712] (II) intel(0): Supported standard timings:
[     5.712] (II) intel(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     5.712] (II) intel(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     5.712] (II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     5.712] (II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     5.712] (II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     5.712] (II) intel(0): #5: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     5.712] (II) intel(0): Supported detailed timing:
[     5.712] (II) intel(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[     5.712] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     5.712] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     5.712] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[     5.712] (II) intel(0): Monitor name: Acer P225HQ
[     5.712] (II) intel(0): Serial No: LHJ0W0124311
[     5.712] (II) intel(0): Supported detailed timing:
[     5.712] (II) intel(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[     5.712] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[     5.712] (II) intel(0): v_active: 1080  v_sync: 1089  v_sync_end 1095 v_blanking: 1125 v_border: 0
[     5.712] (II) intel(0): Supported detailed timing:
[     5.712] (II) intel(0): clock: 74.2 MHz   Image Size:  477 x 268 mm
[     5.712] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     5.712] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     5.712] (II) intel(0): Supported detailed timing:
[     5.712] (II) intel(0): clock: 74.2 MHz   Image Size:  477 x 268 mm
[     5.712] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[     5.712] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     5.712] (II) intel(0): Supported detailed timing:
[     5.712] (II) intel(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[     5.712] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[     5.712] (II) intel(0): v_active: 1080  v_sync: 1082  v_sync_end 1087 v_blanking: 1125 v_border: 0
[     5.712] (II) intel(0): Number of EDID sections to follow: 1
[     5.713] (II) intel(0): EDID (in hex):
[     5.713] (II) intel(0):     00ffffffffffff000472ea0089941000
[     5.713] (II) intel(0):     0114010380301b782a3585a656489a24
[     5.713] (II) intel(0):     125054b30c00714f810081809500b300
[     5.713] (II) intel(0):     d1c001010101023a801871382d40582c
[     5.713] (II) intel(0):     4500dd0c1100001e000000fd00384b1e
[     5.713] (II) intel(0):     5311000a202020202020000000fc0041
[     5.713] (II) intel(0):     636572205032323548510a20000000ff
[     5.713] (II) intel(0):     004c484a3057303132343331310a01fe
[     5.713] (II) intel(0):     020321324f010203040590111213149f
[     5.713] (II) intel(0):     060715166c030c001000b8a5c0000000
[     5.713] (II) intel(0):     00023a80d072382d40102c9680dd0c11
[     5.713] (II) intel(0):     000018011d8018711c1620582c2500dd
[     5.713] (II) intel(0):     0c1100009e011d80d0721c1620102c25
[     5.713] (II) intel(0):     80dd0c1100009e023a80d072382d4010
[     5.713] (II) intel(0):     2c2580dd0c1100001e00000000000000
[     5.713] (II) intel(0):     000000000000000000000000000000e9
[     5.713] (II) intel(0): Printing probed modes for output HDMI1
[     5.713] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     5.713] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[     5.713] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1082 1087 1125 +hsync +vsync (56.2 kHz e)
[     5.713] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1089 1095 1125 -hsync -vsync (56.2 kHz e)
[     5.713] (II) intel(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     5.713] (II) intel(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     5.713] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     5.713] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     5.713] (II) intel(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     5.713] (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     5.713] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     5.713] (II) intel(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     5.713] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     5.713] (II) intel(0): Modeline "1440x576i"x50.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     5.713] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     5.713] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     5.713] (II) intel(0): Modeline "1440x480i"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     5.713] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     5.713] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     5.713] (II) intel(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     5.713] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     5.713] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     5.713] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.713] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.713] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     5.764] (II) intel(0): EDID for output DP1
[     5.764] (II) intel(0): Output LVDS1 connected
[     5.764] (II) intel(0): Output VGA1 disconnected
[     5.764] (II) intel(0): Output HDMI1 connected
[     5.764] (II) intel(0): Output DP1 disconnected
[     5.764] (II) intel(0): Using exact sizes for initial modes
[     5.764] (II) intel(0): Output LVDS1 using initial mode 1920x1080
[     5.764] (II) intel(0): Output HDMI1 using initial mode 1920x1080i
[     5.764] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     5.764] (==) intel(0): DPI set to (96, 96)
[     5.764] (II) Loading sub module "dri2"
[     5.764] (II) LoadModule: "dri2"
[     5.764] (II) Module "dri2" already built-in
[     5.764] (II) UnloadModule: "nvidia"
[     5.764] (II) Unloading nvidia
[     5.764] (II) UnloadModule: "vesa"
[     5.764] (II) Unloading vesa
[     5.764] (II) UnloadModule: "fbdev"
[     5.764] (II) Unloading fbdev
[     5.764] (II) UnloadSubModule: "fbdevhw"
[     5.764] (II) Unloading fbdevhw
[     5.764] (==) Depth 24 pixmap format is 32 bpp
[     5.764] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[     5.764] (==) intel(0): Backing store disabled
[     5.764] (==) intel(0): Silken mouse enabled
[     5.764] (II) intel(0): HW Cursor enabled
[     5.764] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.771] (==) intel(0): DPMS enabled
[     5.771] (II) intel(0): [DRI2] Setup complete
[     5.771] (II) intel(0): [DRI2]   DRI driver: i965
[     5.771] (II) intel(0): direct rendering: DRI2 Enabled
[     5.771] (==) intel(0): hotplug detection: "enabled"
[     5.771] (--) RandR disabled
[     5.777] (II) SELinux: Disabled on system
[     5.779] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[     5.779] (II) intel(0): switch to mode 1920x1080 on pipe 0 using LVDS1
[     5.844] (II) intel(0): switch to mode 1920x1080 on pipe 1 using HDMI1
[     6.060] (II) intel(0): Setting screen physical size to 508 x 285
[     6.065] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     6.066] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     6.066] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.066] (II) LoadModule: "evdev"
[     6.067] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.068] (II) Module evdev: vendor="X.Org Foundation"
[     6.068]     compiled for 1.13.3, module version = 2.7.3
[     6.068]     Module class: X.Org XInput Driver
[     6.068]     ABI class: X.Org XInput driver, version 18.0
[     6.068] (II) Using input driver 'evdev' for 'Power Button'
[     6.068] (**) Power Button: always reports core events
[     6.068] (**) evdev: Power Button: Device: "/dev/input/event2"
[     6.068] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.068] (--) evdev: Power Button: Found keys
[     6.068] (II) evdev: Power Button: Configuring as keyboard
[     6.068] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     6.068] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     6.068] (**) Option "xkb_rules" "evdev"
[     6.068] (**) Option "xkb_model" "pc105"
[     6.068] (**) Option "xkb_layout" "de"
[     6.070] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[     6.070] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[     6.070] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     6.070] (II) Using input driver 'evdev' for 'Video Bus'
[     6.070] (**) Video Bus: always reports core events
[     6.071] (**) evdev: Video Bus: Device: "/dev/input/event10"
[     6.071] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     6.071] (--) evdev: Video Bus: Found keys
[     6.071] (II) evdev: Video Bus: Configuring as keyboard
[     6.071] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10/event10"
[     6.071] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     6.071] (**) Option "xkb_rules" "evdev"
[     6.071] (**) Option "xkb_model" "pc105"
[     6.071] (**) Option "xkb_layout" "de"
[     6.071] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     6.071] (II) No input driver specified, ignoring this device.
[     6.071] (II) This device may have been added with another device file.
[     6.071] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[     6.071] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     6.071] (II) Using input driver 'evdev' for 'Video Bus'
[     6.071] (**) Video Bus: always reports core events
[     6.071] (**) evdev: Video Bus: Device: "/dev/input/event9"
[     6.071] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     6.071] (--) evdev: Video Bus: Found keys
[     6.071] (II) evdev: Video Bus: Configuring as keyboard
[     6.071] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a/LNXVIDEO:00/input/input9/event9"
[     6.071] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[     6.071] (**) Option "xkb_rules" "evdev"
[     6.071] (**) Option "xkb_model" "pc105"
[     6.071] (**) Option "xkb_layout" "de"
[     6.071] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     6.071] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.071] (II) Using input driver 'evdev' for 'Power Button'
[     6.071] (**) Power Button: always reports core events
[     6.071] (**) evdev: Power Button: Device: "/dev/input/event1"
[     6.071] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.071] (--) evdev: Power Button: Found keys
[     6.071] (II) evdev: Power Button: Configuring as keyboard
[     6.072] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[     6.072] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[     6.072] (**) Option "xkb_rules" "evdev"
[     6.072] (**) Option "xkb_model" "pc105"
[     6.072] (**) Option "xkb_layout" "de"
[     6.072] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[     6.072] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     6.072] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event17)
[     6.072] (II) No input driver specified, ignoring this device.
[     6.072] (II) This device may have been added with another device file.
[     6.072] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event18)
[     6.072] (II) No input driver specified, ignoring this device.
[     6.072] (II) This device may have been added with another device file.
[     6.072] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event19)
[     6.072] (II) No input driver specified, ignoring this device.
[     6.072] (II) This device may have been added with another device file.
[     6.072] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event20)
[     6.072] (II) No input driver specified, ignoring this device.
[     6.072] (II) This device may have been added with another device file.
[     6.072] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:02.0/drm/card1
[     6.072] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[     6.073] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event4)
[     6.073] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[     6.073] (II) Using input driver 'evdev' for 'HID 046a:0023'
[     6.073] (**) HID 046a:0023: always reports core events
[     6.073] (**) evdev: HID 046a:0023: Device: "/dev/input/event4"
[     6.073] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[     6.073] (--) evdev: HID 046a:0023: Found keys
[     6.073] (II) evdev: HID 046a:0023: Configuring as keyboard
[     6.073] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input4/event4"
[     6.073] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 10)
[     6.073] (**) Option "xkb_rules" "evdev"
[     6.073] (**) Option "xkb_model" "pc105"
[     6.073] (**) Option "xkb_layout" "de"
[     6.073] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event5)
[     6.073] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[     6.073] (II) Using input driver 'evdev' for 'HID 046a:0023'
[     6.073] (**) HID 046a:0023: always reports core events
[     6.073] (**) evdev: HID 046a:0023: Device: "/dev/input/event5"
[     6.073] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[     6.073] (--) evdev: HID 046a:0023: Found 1 mouse buttons
[     6.073] (--) evdev: HID 046a:0023: Found scroll wheel(s)
[     6.073] (--) evdev: HID 046a:0023: Found relative axes
[     6.073] (II) evdev: HID 046a:0023: Forcing relative x/y axes to exist.
[     6.073] (--) evdev: HID 046a:0023: Found absolute axes
[     6.073] (II) evdev: HID 046a:0023: Forcing absolute x/y axes to exist.
[     6.073] (--) evdev: HID 046a:0023: Found keys
[     6.073] (II) evdev: HID 046a:0023: Configuring as mouse
[     6.073] (II) evdev: HID 046a:0023: Configuring as keyboard
[     6.073] (II) evdev: HID 046a:0023: Adding scrollwheel support
[     6.073] (**) evdev: HID 046a:0023: YAxisMapping: buttons 4 and 5
[     6.073] (**) evdev: HID 046a:0023: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.073] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/input/input5/event5"
[     6.073] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 11)
[     6.073] (**) Option "xkb_rules" "evdev"
[     6.073] (**) Option "xkb_model" "pc105"
[     6.073] (**) Option "xkb_layout" "de"
[     6.073] (II) evdev: HID 046a:0023: initialized for relative axes.
[     6.074] (WW) evdev: HID 046a:0023: ignoring absolute axes.
[     6.074] (**) HID 046a:0023: (accel) keeping acceleration scheme 1
[     6.074] (**) HID 046a:0023: (accel) acceleration profile 0
[     6.074] (**) HID 046a:0023: (accel) acceleration factor: 2.000
[     6.074] (**) HID 046a:0023: (accel) acceleration threshold: 4
[     6.074] (II) config/udev: Adding input device Logitech G9 Laser Mouse (/dev/input/event6)
[     6.074] (**) Logitech G9 Laser Mouse: Applying InputClass "evdev pointer catchall"
[     6.074] (II) Using input driver 'evdev' for 'Logitech G9 Laser Mouse'
[     6.074] (**) Logitech G9 Laser Mouse: always reports core events
[     6.074] (**) evdev: Logitech G9 Laser Mouse: Device: "/dev/input/event6"
[     6.074] (--) evdev: Logitech G9 Laser Mouse: Vendor 0x46d Product 0xc048
[     6.074] (--) evdev: Logitech G9 Laser Mouse: Found 20 mouse buttons
[     6.074] (--) evdev: Logitech G9 Laser Mouse: Found scroll wheel(s)
[     6.074] (--) evdev: Logitech G9 Laser Mouse: Found relative axes
[     6.074] (--) evdev: Logitech G9 Laser Mouse: Found x and y relative axes
[     6.074] (II) evdev: Logitech G9 Laser Mouse: Configuring as mouse
[     6.074] (II) evdev: Logitech G9 Laser Mouse: Adding scrollwheel support
[     6.074] (**) evdev: Logitech G9 Laser Mouse: YAxisMapping: buttons 4 and 5
[     6.074] (**) evdev: Logitech G9 Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.074] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input6/event6"
[     6.074] (II) XINPUT: Adding extended input device "Logitech G9 Laser Mouse" (type: MOUSE, id 12)
[     6.074] (II) evdev: Logitech G9 Laser Mouse: initialized for relative axes.
[     6.074] (**) Logitech G9 Laser Mouse: (accel) keeping acceleration scheme 1
[     6.074] (**) Logitech G9 Laser Mouse: (accel) acceleration profile 0
[     6.074] (**) Logitech G9 Laser Mouse: (accel) acceleration factor: 2.000
[     6.074] (**) Logitech G9 Laser Mouse: (accel) acceleration threshold: 4
[     6.074] (II) config/udev: Adding input device Logitech G9 Laser Mouse (/dev/input/mouse0)
[     6.074] (II) No input driver specified, ignoring this device.
[     6.074] (II) This device may have been added with another device file.
[     6.075] (II) config/udev: Adding input device Logitech G9 Laser Mouse (/dev/input/event7)
[     6.075] (**) Logitech G9 Laser Mouse: Applying InputClass "evdev keyboard catchall"
[     6.075] (II) Using input driver 'evdev' for 'Logitech G9 Laser Mouse'
[     6.075] (**) Logitech G9 Laser Mouse: always reports core events
[     6.075] (**) evdev: Logitech G9 Laser Mouse: Device: "/dev/input/event7"
[     6.075] (--) evdev: Logitech G9 Laser Mouse: Vendor 0x46d Product 0xc048
[     6.075] (--) evdev: Logitech G9 Laser Mouse: Found 1 mouse buttons
[     6.075] (--) evdev: Logitech G9 Laser Mouse: Found scroll wheel(s)
[     6.075] (--) evdev: Logitech G9 Laser Mouse: Found relative axes
[     6.075] (II) evdev: Logitech G9 Laser Mouse: Forcing relative x/y axes to exist.
[     6.075] (--) evdev: Logitech G9 Laser Mouse: Found absolute axes
[     6.075] (II) evdev: Logitech G9 Laser Mouse: Forcing absolute x/y axes to exist.
[     6.075] (--) evdev: Logitech G9 Laser Mouse: Found keys
[     6.075] (II) evdev: Logitech G9 Laser Mouse: Configuring as mouse
[     6.075] (II) evdev: Logitech G9 Laser Mouse: Configuring as keyboard
[     6.075] (II) evdev: Logitech G9 Laser Mouse: Adding scrollwheel support
[     6.075] (**) evdev: Logitech G9 Laser Mouse: YAxisMapping: buttons 4 and 5
[     6.075] (**) evdev: Logitech G9 Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.075] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.1/input/input7/event7"
[     6.075] (II) XINPUT: Adding extended input device "Logitech G9 Laser Mouse" (type: KEYBOARD, id 13)
[     6.075] (**) Option "xkb_rules" "evdev"
[     6.075] (**) Option "xkb_model" "pc105"
[     6.075] (**) Option "xkb_layout" "de"
[     6.075] (II) evdev: Logitech G9 Laser Mouse: initialized for relative axes.
[     6.075] (WW) evdev: Logitech G9 Laser Mouse: ignoring absolute axes.
[     6.075] (**) Logitech G9 Laser Mouse: (accel) keeping acceleration scheme 1
[     6.075] (**) Logitech G9 Laser Mouse: (accel) acceleration profile 0
[     6.075] (**) Logitech G9 Laser Mouse: (accel) acceleration factor: 2.000
[     6.075] (**) Logitech G9 Laser Mouse: (accel) acceleration threshold: 4
[     6.075] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[     6.075] (II) No input driver specified, ignoring this device.
[     6.075] (II) This device may have been added with another device file.
[     6.075] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[     6.075] (II) No input driver specified, ignoring this device.
[     6.075] (II) This device may have been added with another device file.
[     6.075] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event13)
[     6.075] (II) No input driver specified, ignoring this device.
[     6.075] (II) This device may have been added with another device file.
[     6.076] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event14)
[     6.076] (II) No input driver specified, ignoring this device.
[     6.076] (II) This device may have been added with another device file.
[     6.076] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event15)
[     6.076] (II) No input driver specified, ignoring this device.
[     6.076] (II) This device may have been added with another device file.
[     6.076] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     6.076] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     6.076] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     6.076] (**) AT Translated Set 2 keyboard: always reports core events
[     6.076] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     6.076] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     6.076] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     6.076] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     6.076] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     6.076] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[     6.076] (**) Option "xkb_rules" "evdev"
[     6.076] (**) Option "xkb_model" "pc105"
[     6.076] (**) Option "xkb_layout" "de"
[     6.076] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event16)
[     6.076] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     6.076] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     6.076] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     6.076] (II) LoadModule: "synaptics"
[     6.076] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.077] (II) Module synaptics: vendor="X.Org Foundation"
[     6.077]     compiled for 1.13.1.901, module version = 1.6.2
[     6.077]     Module class: X.Org XInput Driver
[     6.077]     ABI class: X.Org XInput driver, version 18.0
[     6.077] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     6.077] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.077] (**) Option "Device" "/dev/input/event16"
[     6.144] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[     6.144] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[     6.144] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[     6.144] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     6.144] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     6.144] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     6.144] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     6.144] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.144] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.180] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input16/event16"
[     6.180] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 15)
[     6.180] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     6.180] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[     6.180] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[     6.180] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     6.180] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     6.180] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     6.180] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     6.180] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.180] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[     6.180] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     6.182] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event8)
[     6.182] (**) MSI WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     6.182] (II) Using input driver 'evdev' for 'MSI WMI hotkeys'
[     6.182] (**) MSI WMI hotkeys: always reports core events
[     6.182] (**) evdev: MSI WMI hotkeys: Device: "/dev/input/event8"
[     6.182] (--) evdev: MSI WMI hotkeys: Vendor 0 Product 0
[     6.182] (--) evdev: MSI WMI hotkeys: Found keys
[     6.182] (II) evdev: MSI WMI hotkeys: Configuring as keyboard
[     6.182] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[     6.182] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 16)
[     6.182] (**) Option "xkb_rules" "evdev"
[     6.182] (**) Option "xkb_model" "pc105"
[     6.182] (**) Option "xkb_layout" "de"


```

maybe if got the wrong xorg-server version? i have read that the optimus function only works with xorg-server 1.14.1 and randr 1.4, isnt that right?

---

### Post by Scofa on 2013-07-06
And Here is the output from xorg log 2 :

```
[  1364.458] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[  1364.458] X Protocol Version 11, Revision 0
[  1364.458] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  1364.458] Current Operating System: Linux Cru-Z 3.10.0-2-generic #10-Ubuntu SMP Fri Jul 5 18:03:52 UTC 2013 x86_64
[  1364.458] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.10.0-2-generic root=UUID=a27b04f3-c658-4aa6-bb13-7098a3308a0c ro quiet splash
[  1364.458] Build Date: 17 June 2013  12:30:59PM
[  1364.458] xorg-server 2:1.13.3-0ubuntu13 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1364.458] Current version of pixman: 0.28.2
[  1364.458]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[  1364.458] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1364.459] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Jul  6 13:26:10 2013
[  1364.459] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1364.459] (==) No Layout section.  Using the first Screen section.
[  1364.459] (==) No screen section available. Using defaults.
[  1364.459] (**) |-->Screen "Default Screen Section" (0)
[  1364.459] (**) |   |-->Monitor "<default monitor>"
[  1364.459] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1364.459] (==) Automatically adding devices
[  1364.459] (==) Automatically enabling devices
[  1364.459] (==) Automatically adding GPU devices
[  1364.459] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1364.459]     Entry deleted from font path.
[  1364.459] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1364.459]     Entry deleted from font path.
[  1364.459] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1364.459]     Entry deleted from font path.
[  1364.459] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1364.459]     Entry deleted from font path.
[  1364.459] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1364.459]     Entry deleted from font path.
[  1364.459] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  1364.459]     Entry deleted from font path.
[  1364.459] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1364.459] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1364.459] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1364.459] (II) Loader magic: 0x7f30206b2d20
[  1364.459] (II) Module ABI versions:
[  1364.459]     X.Org ANSI C Emulation: 0.4
[  1364.459]     X.Org Video Driver: 13.1
[  1364.459]     X.Org XInput driver : 18.0
[  1364.459]     X.Org Server Extension : 7.0
[  1364.459] (II) config/udev: Adding drm device (/dev/dri/card0)
[  1364.459] (II) config/udev: Adding drm device (/dev/dri/card1)
[  1364.460] (--) PCI:*(0:0:2:0) 8086:0166:1462:10d9 rev 9, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[  1364.460] (--) PCI: (0:1:0:0) 10de:11a7:1462:10d9 rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[  1364.460] (II) Open ACPI successful (/var/run/acpid.socket)
[  1364.460] Initializing built-in extension Generic Event Extension
[  1364.460] Initializing built-in extension SHAPE
[  1364.460] Initializing built-in extension MIT-SHM
[  1364.461] Initializing built-in extension XInputExtension
[  1364.461] Initializing built-in extension XTEST
[  1364.461] Initializing built-in extension BIG-REQUESTS
[  1364.461] Initializing built-in extension SYNC
[  1364.461] Initializing built-in extension XKEYBOARD
[  1364.461] Initializing built-in extension XC-MISC
[  1364.461] Initializing built-in extension SECURITY
[  1364.461] Initializing built-in extension XINERAMA
[  1364.461] Initializing built-in extension XFIXES
[  1364.461] Initializing built-in extension RENDER
[  1364.461] Initializing built-in extension RANDR
[  1364.461] Initializing built-in extension COMPOSITE
[  1364.461] Initializing built-in extension DAMAGE
[  1364.461] Initializing built-in extension MIT-SCREEN-SAVER
[  1364.462] Initializing built-in extension DOUBLE-BUFFER
[  1364.462] Initializing built-in extension RECORD
[  1364.463] Initializing built-in extension DPMS
[  1364.463] Initializing built-in extension X-Resource
[  1364.464] Initializing built-in extension XVideo
[  1364.465] Initializing built-in extension XVideo-MotionCompensation
[  1364.465] Initializing built-in extension SELinux
[  1364.466] Initializing built-in extension XFree86-VidModeExtension
[  1364.467] Initializing built-in extension XFree86-DGA
[  1364.467] Initializing built-in extension XFree86-DRI
[  1364.468] Initializing built-in extension DRI2
[  1364.468] (II) LoadModule: "glx"
[  1364.468] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[  1364.476] (II) Module glx: vendor="NVIDIA Corporation"
[  1364.476]     compiled for 4.0.2, module version = 1.0.0
[  1364.476]     Module class: X.Org Server Extension
[  1364.476] (II) NVIDIA GLX Module  325.08  Wed Jun 26 17:51:26 PDT 2013
[  1364.476] Loading extension GLX
[  1364.476] (==) Matched intel as autoconfigured driver 0
[  1364.476] (==) Matched nvidia as autoconfigured driver 1
[  1364.476] (==) Matched nouveau as autoconfigured driver 2
[  1364.476] (==) Matched intel as autoconfigured driver 3
[  1364.476] (==) Matched vesa as autoconfigured driver 4
[  1364.476] (==) Matched modesetting as autoconfigured driver 5
[  1364.476] (==) Matched fbdev as autoconfigured driver 6
[  1364.476] (==) Assigned the driver to the xf86ConfigLayout
[  1364.476] (II) LoadModule: "intel"
[  1364.477] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1364.477] (II) Module intel: vendor="X.Org Foundation"
[  1364.477]     compiled for 1.13.3, module version = 2.21.9
[  1364.477]     Module class: X.Org Video Driver
[  1364.477]     ABI class: X.Org Video Driver, version 13.1
[  1364.477] (II) LoadModule: "nvidia"
[  1364.477] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1364.477] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1364.477]     compiled for 4.0.2, module version = 1.0.0
[  1364.477]     Module class: X.Org Video Driver
[  1364.477] (II) LoadModule: "nouveau"
[  1364.477] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1364.477] (II) Module nouveau: vendor="X.Org Foundation"
[  1364.477]     compiled for 1.13.3, module version = 1.0.8
[  1364.477]     Module class: X.Org Video Driver
[  1364.477]     ABI class: X.Org Video Driver, version 13.1
[  1364.477] (II) LoadModule: "vesa"
[  1364.478] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1364.478] (II) Module vesa: vendor="X.Org Foundation"
[  1364.478]     compiled for 1.12.99.902, module version = 2.3.2
[  1364.478]     Module class: X.Org Video Driver
[  1364.478]     ABI class: X.Org Video Driver, version 13.0
[  1364.478] (II) LoadModule: "modesetting"
[  1364.478] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1364.478] (II) Module modesetting: vendor="X.Org Foundation"
[  1364.478]     compiled for 1.13.3, module version = 0.8.0
[  1364.478]     Module class: X.Org Video Driver
[  1364.478]     ABI class: X.Org Video Driver, version 13.1
[  1364.478] (II) LoadModule: "fbdev"
[  1364.478] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1364.478] (II) Module fbdev: vendor="X.Org Foundation"
[  1364.478]     compiled for 1.12.99.902, module version = 0.4.3
[  1364.478]     Module class: X.Org Video Driver
[  1364.478]     ABI class: X.Org Video Driver, version 13.0
[  1364.478] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), HD Graphics, HD Graphics 4600,
    Haswell Desktop (GT3), HD Graphics, HD Graphics 4600,
    Haswell Mobile (GT3), HD Graphics, HD Graphics P4600/P4700,
    Haswell Server (GT3), Haswell (GT1), Haswell (GT2), Haswell (GT3),
    HD Graphics, Haswell (GT2), Haswell (GT3), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT3),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT3), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4400,
    HD Graphics 5000, Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Iris(TM) Graphics 5100, Haswell ULT (GT1), Haswell ULT (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4200,
    Iris(TM) Graphics 5100, Haswell CRW Desktop (GT1), HD Graphics 4600,
    Iris(TM) Pro Graphics 5200, Haswell CRW Mobile (GT1),
    HD Graphics 4600, Iris(TM) Pro Graphics 5200,
    Haswell CRW Server (GT1), Haswell CRW Server (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, ValleyView PO board
[  1364.479] (II) NVIDIA dlloader X Driver  325.08  Wed Jun 26 17:32:32 PDT 2013
[  1364.479] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1364.479] (II) NOUVEAU driver Date:   Wed Jun 12 10:46:39 2013 +0200
[  1364.479] (II) NOUVEAU driver for NVIDIA chipset families :
[  1364.479]     RIVA TNT        (NV04)
[  1364.479]     RIVA TNT2       (NV05)
[  1364.479]     GeForce 256     (NV10)
[  1364.479]     GeForce 2       (NV11, NV15)
[  1364.479]     GeForce 4MX     (NV17, NV18)
[  1364.479]     GeForce 3       (NV20)
[  1364.479]     GeForce 4Ti     (NV25, NV28)
[  1364.479]     GeForce FX      (NV3x)
[  1364.479]     GeForce 6       (NV4x)
[  1364.479]     GeForce 7       (G7x)
[  1364.479]     GeForce 8       (G8x)
[  1364.479]     GeForce GTX 200 (NVA0)
[  1364.479]     GeForce GTX 400 (NVC0)
[  1364.479] (II) VESA: driver for VESA chipsets: vesa
[  1364.479] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1364.479] (II) FBDEV: driver for framebuffer: fbdev
[  1364.479] (--) using VT number 8

[  1364.483] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.9-0ubuntu2 (Timo Aaltonen <tjaalton@ubuntu.com>)
[  1364.483] (EE) [drm] KMS not enabled
[  1364.483] (WW) Falling back to old probe method for vesa
[  1364.483] (WW) Falling back to old probe method for modesetting
[  1364.483] (WW) Falling back to old probe method for fbdev
[  1364.483] (II) Loading sub module "fbdevhw"
[  1364.483] (II) LoadModule: "fbdevhw"
[  1364.483] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1364.483] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1364.483]     compiled for 1.13.3, module version = 0.0.2
[  1364.483]     ABI class: X.Org Video Driver, version 13.1
[  1364.484] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1364.484] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  1364.484] (==) intel(0): RGB weight 888
[  1364.484] (==) intel(0): Default visual is TrueColor
[  1364.484] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[  1364.484] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[  1364.484] (**) intel(0): Framebuffer tiled
[  1364.484] (**) intel(0): Pixmaps tiled
[  1364.484] (**) intel(0): "Tear free" disabled
[  1364.484] (**) intel(0): Forcing per-crtc-pixmaps? no
[  1364.484] (II) intel(0): Output LVDS1 has no monitor section
[  1364.487] (--) intel(0): found backlight control interface acpi_video1 (type 'firmware')
[  1364.488] (II) intel(0): Output VGA1 has no monitor section
[  1364.539] (II) intel(0): Output HDMI1 has no monitor section
[  1364.588] (II) intel(0): Output DP1 has no monitor section
[  1364.588] (II) intel(0): EDID for output LVDS1
[  1364.588] (II) intel(0): Manufacturer: CMO  Model: 1720  Serial#: 0
[  1364.588] (II) intel(0): Year: 2011  Week: 2
[  1364.588] (II) intel(0): EDID Version: 1.3
[  1364.588] (II) intel(0): Digital Display Input
[  1364.588] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[  1364.588] (II) intel(0): Gamma: 2.20
[  1364.588] (II) intel(0): No DPMS capabilities specified
[  1364.588] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  1364.588] (II) intel(0): First detailed timing is preferred mode
[  1364.588] (II) intel(0): redX: 0.640 redY: 0.333   greenX: 0.303 greenY: 0.613
[  1364.588] (II) intel(0): blueX: 0.154 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[  1364.588] (II) intel(0): Manufacturer's mask: 0
[  1364.588] (II) intel(0): Supported detailed timing:
[  1364.588] (II) intel(0): clock: 138.7 MHz   Image Size:  382 x 215 mm
[  1364.588] (II) intel(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[  1364.588] (II) intel(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[  1364.588] (II) intel(0):  N173HGE-L11
[  1364.588] (II) intel(0):  CMO
[  1364.588] (II) intel(0):  N173HGE-L11
[  1364.588] (II) intel(0): EDID (in hex):
[  1364.588] (II) intel(0):     00ffffffffffff000daf201700000000
[  1364.588] (II) intel(0):     02150103802615780ad895a3554d9d27
[  1364.588] (II) intel(0):     0f505400000001010101010101010101
[  1364.588] (II) intel(0):     0101010101012e3680a070381f403020
[  1364.588] (II) intel(0):     35007ed710000018000000fe004e3137
[  1364.588] (II) intel(0):     334847452d4c31310a20000000fe0043
[  1364.588] (II) intel(0):     4d4f0a202020202020202020000000fe
[  1364.588] (II) intel(0):     004e3137334847452d4c31310a20006e
[  1364.588] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[  1364.588] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[  1364.588] (II) intel(0): Printing probed modes for output LVDS1
[  1364.588] (II) intel(0): Modeline "1920x1080"x60.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[  1364.588] (II) intel(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[  1364.588] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[  1364.588] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[  1364.588] (II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[  1364.588] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[  1364.588] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[  1364.588] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[  1364.588] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[  1364.588] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[  1364.588] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[  1364.588] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[  1364.588] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[  1364.588] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[  1364.588] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[  1364.588] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[  1364.589] (II) intel(0): EDID for output VGA1
[  1364.639] (II) intel(0): EDID for output HDMI1
[  1364.639] (II) intel(0): Manufacturer: ACR  Model: ea  Serial#: 1086601
[  1364.639] (II) intel(0): Year: 2010  Week: 1
[  1364.639] (II) intel(0): EDID Version: 1.3
[  1364.639] (II) intel(0): Digital Display Input
[  1364.639] (II) intel(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[  1364.639] (II) intel(0): Gamma: 2.20
[  1364.639] (II) intel(0): DPMS capabilities: Off
[  1364.639] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  1364.639] (II) intel(0): First detailed timing is preferred mode
[  1364.639] (II) intel(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[  1364.639] (II) intel(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[  1364.639] (II) intel(0): Supported established timings:
[  1364.639] (II) intel(0): 720x400@70Hz
[  1364.639] (II) intel(0): 640x480@60Hz
[  1364.639] (II) intel(0): 640x480@67Hz
[  1364.639] (II) intel(0): 800x600@56Hz
[  1364.639] (II) intel(0): 800x600@60Hz
[  1364.639] (II) intel(0): 1024x768@60Hz
[  1364.639] (II) intel(0): 1024x768@70Hz
[  1364.639] (II) intel(0): Manufacturer's mask: 0
[  1364.639] (II) intel(0): Supported standard timings:
[  1364.639] (II) intel(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  1364.639] (II) intel(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[  1364.639] (II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  1364.639] (II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[  1364.639] (II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[  1364.639] (II) intel(0): #5: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[  1364.639] (II) intel(0): Supported detailed timing:
[  1364.639] (II) intel(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[  1364.639] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[  1364.639] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[  1364.639] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[  1364.639] (II) intel(0): Monitor name: Acer P225HQ
[  1364.639] (II) intel(0): Serial No: LHJ0W0124311
[  1364.639] (II) intel(0): Supported detailed timing:
[  1364.639] (II) intel(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[  1364.639] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[  1364.639] (II) intel(0): v_active: 1080  v_sync: 1089  v_sync_end 1095 v_blanking: 1125 v_border: 0
[  1364.639] (II) intel(0): Supported detailed timing:
[  1364.640] (II) intel(0): clock: 74.2 MHz   Image Size:  477 x 268 mm
[  1364.640] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[  1364.640] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[  1364.640] (II) intel(0): Supported detailed timing:
[  1364.640] (II) intel(0): clock: 74.2 MHz   Image Size:  477 x 268 mm
[  1364.640] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[  1364.640] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[  1364.640] (II) intel(0): Supported detailed timing:
[  1364.640] (II) intel(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[  1364.640] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[  1364.640] (II) intel(0): v_active: 1080  v_sync: 1082  v_sync_end 1087 v_blanking: 1125 v_border: 0
[  1364.640] (II) intel(0): Number of EDID sections to follow: 1
[  1364.640] (II) intel(0): EDID (in hex):
[  1364.640] (II) intel(0):     00ffffffffffff000472ea0089941000
[  1364.640] (II) intel(0):     0114010380301b782a3585a656489a24
[  1364.640] (II) intel(0):     125054b30c00714f810081809500b300
[  1364.640] (II) intel(0):     d1c001010101023a801871382d40582c
[  1364.640] (II) intel(0):     4500dd0c1100001e000000fd00384b1e
[  1364.640] (II) intel(0):     5311000a202020202020000000fc0041
[  1364.640] (II) intel(0):     636572205032323548510a20000000ff
[  1364.640] (II) intel(0):     004c484a3057303132343331310a01fe
[  1364.640] (II) intel(0):     020321324f010203040590111213149f
[  1364.640] (II) intel(0):     060715166c030c001000b8a5c0000000
[  1364.640] (II) intel(0):     00023a80d072382d40102c9680dd0c11
[  1364.640] (II) intel(0):     000018011d8018711c1620582c2500dd
[  1364.640] (II) intel(0):     0c1100009e011d80d0721c1620102c25
[  1364.640] (II) intel(0):     80dd0c1100009e023a80d072382d4010
[  1364.640] (II) intel(0):     2c2580dd0c1100001e00000000000000
[  1364.640] (II) intel(0):     000000000000000000000000000000e9
[  1364.640] (II) intel(0): Printing probed modes for output HDMI1
[  1364.640] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1364.640] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[  1364.640] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1082 1087 1125 +hsync +vsync (56.2 kHz e)
[  1364.640] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1089 1095 1125 -hsync -vsync (56.2 kHz e)
[  1364.640] (II) intel(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[  1364.640] (II) intel(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[  1364.640] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1364.640] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1364.640] (II) intel(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1364.640] (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1364.640] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1364.640] (II) intel(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[  1364.640] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1364.640] (II) intel(0): Modeline "1440x576i"x50.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[  1364.640] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1364.640] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1364.640] (II) intel(0): Modeline "1440x480i"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[  1364.640] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1364.640] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1364.640] (II) intel(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[  1364.640] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1364.640] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1364.640] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1364.640] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1364.640] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1364.688] (II) intel(0): EDID for output DP1
[  1364.688] (II) intel(0): Output LVDS1 connected
[  1364.688] (II) intel(0): Output VGA1 disconnected
[  1364.688] (II) intel(0): Output HDMI1 connected
[  1364.688] (II) intel(0): Output DP1 disconnected
[  1364.688] (II) intel(0): Using exact sizes for initial modes
[  1364.688] (II) intel(0): Output LVDS1 using initial mode 1920x1080
[  1364.688] (II) intel(0): Output HDMI1 using initial mode 1920x1080i
[  1364.688] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1364.688] (==) intel(0): DPI set to (96, 96)
[  1364.688] (II) Loading sub module "dri2"
[  1364.688] (II) LoadModule: "dri2"
[  1364.688] (II) Module "dri2" already built-in
[  1364.688] (II) UnloadModule: "nvidia"
[  1364.688] (II) Unloading nvidia
[  1364.688] (II) UnloadModule: "vesa"
[  1364.688] (II) Unloading vesa
[  1364.688] (II) UnloadModule: "fbdev"
[  1364.688] (II) Unloading fbdev
[  1364.688] (II) UnloadSubModule: "fbdevhw"
[  1364.688] (II) Unloading fbdevhw
[  1364.688] (==) Depth 24 pixmap format is 32 bpp
[  1364.688] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[  1364.688] (==) intel(0): Backing store disabled
[  1364.688] (==) intel(0): Silken mouse enabled
[  1364.688] (II) intel(0): HW Cursor enabled
[  1364.688] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1364.695] (==) intel(0): DPMS enabled
[  1364.695] (II) intel(0): [DRI2] Setup complete
[  1364.695] (II) intel(0): [DRI2]   DRI driver: i965
[  1364.695] (II) intel(0): direct rendering: DRI2 Enabled
[  1364.695] (==) intel(0): hotplug detection: "enabled"
[  1364.695] (--) RandR disabled
[  1364.700] (II) SELinux: Disabled on system
[  1364.701] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[  1364.701] (II) intel(0): switch to mode 1920x1080 on pipe 0 using LVDS1
[  1364.764] (II) intel(0): switch to mode 1920x1080 on pipe 1 using HDMI1
[  1364.980] (II) intel(0): Setting screen physical size to 508 x 285
[  1364.986] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1364.988] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  1364.988] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1364.988] (II) LoadModule: "evdev"
[  1364.988] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1364.989] (II) Module evdev: vendor="X.Org Foundation"
[  1364.989]     compiled for 1.13.3, module version = 2.7.3
[  1364.989]     Module class: X.Org XInput Driver
[  1364.989]     ABI class: X.Org XInput driver, version 18.0
[  1364.989] (II) Using input driver 'evdev' for 'Power Button'
[  1364.989] (**) Power Button: always reports core events
[  1364.989] (**) evdev: Power Button: Device: "/dev/input/event2"
[  1364.989] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1364.989] (--) evdev: Power Button: Found keys
[  1364.989] (II) evdev: Power Button: Configuring as keyboard
[  1364.989] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  1364.989] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1364.989] (**) Option "xkb_rules" "evdev"
[  1364.989] (**) Option "xkb_model" "pc105"
[  1364.989] (**) Option "xkb_layout" "de"
[  1364.991] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[  1364.991] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[  1364.991] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1364.991] (II) Using input driver 'evdev' for 'Video Bus'
[  1364.991] (**) Video Bus: always reports core events
[  1364.991] (**) evdev: Video Bus: Device: "/dev/input/event10"
[  1364.991] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  1364.991] (--) evdev: Video Bus: Found keys
[  1364.991] (II) evdev: Video Bus: Configuring as keyboard
[  1364.991] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10/event10"
[  1364.992] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  1364.992] (**) Option "xkb_rules" "evdev"
[  1364.992] (**) Option "xkb_model" "pc105"
[  1364.992] (**) Option "xkb_layout" "de"
[  1364.992] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  1364.992] (II) No input driver specified, ignoring this device.
[  1364.992] (II) This device may have been added with another device file.
[  1364.992] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[  1364.992] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1364.992] (II) Using input driver 'evdev' for 'Video Bus'
[  1364.992] (**) Video Bus: always reports core events
[  1364.992] (**) evdev: Video Bus: Device: "/dev/input/event9"
[  1364.992] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  1364.992] (--) evdev: Video Bus: Found keys
[  1364.992] (II) evdev: Video Bus: Configuring as keyboard
[  1364.992] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a/LNXVIDEO:00/input/input9/event9"
[  1364.992] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[  1364.992] (**) Option "xkb_rules" "evdev"
[  1364.992] (**) Option "xkb_model" "pc105"
[  1364.992] (**) Option "xkb_layout" "de"
[  1364.993] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1364.993] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1364.993] (II) Using input driver 'evdev' for 'Power Button'
[  1364.993] (**) Power Button: always reports core events
[  1364.993] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1364.993] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1364.993] (--) evdev: Power Button: Found keys
[  1364.993] (II) evdev: Power Button: Configuring as keyboard
[  1364.993] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[  1364.993] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[  1364.993] (**) Option "xkb_rules" "evdev"
[  1364.993] (**) Option "xkb_model" "pc105"
[  1364.993] (**) Option "xkb_layout" "de"
[  1364.993] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[  1364.993] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[  1364.993] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event17)
[  1364.993] (II) No input driver specified, ignoring this device.
[  1364.993] (II) This device may have been added with another device file.
[  1364.993] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event18)
[  1364.993] (II) No input driver specified, ignoring this device.
[  1364.993] (II) This device may have been added with another device file.
[  1364.994] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event19)
[  1364.994] (II) No input driver specified, ignoring this device.
[  1364.994] (II) This device may have been added with another device file.
[  1364.994] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event20)
[  1364.994] (II) No input driver specified, ignoring this device.
[  1364.994] (II) This device may have been added with another device file.
[  1364.994] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:02.0/drm/card1
[  1364.994] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[  1364.994] (II) config/udev: Adding input device Logitech G9 Laser Mouse (/dev/input/event4)
[  1364.994] (**) Logitech G9 Laser Mouse: Applying InputClass "evdev pointer catchall"
[  1364.994] (II) Using input driver 'evdev' for 'Logitech G9 Laser Mouse'
[  1364.994] (**) Logitech G9 Laser Mouse: always reports core events
[  1364.994] (**) evdev: Logitech G9 Laser Mouse: Device: "/dev/input/event4"
[  1364.994] (--) evdev: Logitech G9 Laser Mouse: Vendor 0x46d Product 0xc048
[  1364.994] (--) evdev: Logitech G9 Laser Mouse: Found 20 mouse buttons
[  1364.994] (--) evdev: Logitech G9 Laser Mouse: Found scroll wheel(s)
[  1364.994] (--) evdev: Logitech G9 Laser Mouse: Found relative axes
[  1364.994] (--) evdev: Logitech G9 Laser Mouse: Found x and y relative axes
[  1364.994] (II) evdev: Logitech G9 Laser Mouse: Configuring as mouse
[  1364.994] (II) evdev: Logitech G9 Laser Mouse: Adding scrollwheel support
[  1364.994] (**) evdev: Logitech G9 Laser Mouse: YAxisMapping: buttons 4 and 5
[  1364.994] (**) evdev: Logitech G9 Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1364.994] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input4/event4"
[  1364.994] (II) XINPUT: Adding extended input device "Logitech G9 Laser Mouse" (type: MOUSE, id 10)
[  1364.994] (II) evdev: Logitech G9 Laser Mouse: initialized for relative axes.
[  1364.995] (**) Logitech G9 Laser Mouse: (accel) keeping acceleration scheme 1
[  1364.995] (**) Logitech G9 Laser Mouse: (accel) acceleration profile 0
[  1364.995] (**) Logitech G9 Laser Mouse: (accel) acceleration factor: 2.000
[  1364.995] (**) Logitech G9 Laser Mouse: (accel) acceleration threshold: 4
[  1364.995] (II) config/udev: Adding input device Logitech G9 Laser Mouse (/dev/input/mouse0)
[  1364.995] (II) No input driver specified, ignoring this device.
[  1364.995] (II) This device may have been added with another device file.
[  1364.995] (II) config/udev: Adding input device Logitech G9 Laser Mouse (/dev/input/event5)
[  1364.995] (**) Logitech G9 Laser Mouse: Applying InputClass "evdev keyboard catchall"
[  1364.995] (II) Using input driver 'evdev' for 'Logitech G9 Laser Mouse'
[  1364.995] (**) Logitech G9 Laser Mouse: always reports core events
[  1364.995] (**) evdev: Logitech G9 Laser Mouse: Device: "/dev/input/event5"
[  1364.995] (--) evdev: Logitech G9 Laser Mouse: Vendor 0x46d Product 0xc048
[  1364.995] (--) evdev: Logitech G9 Laser Mouse: Found 1 mouse buttons
[  1364.995] (--) evdev: Logitech G9 Laser Mouse: Found scroll wheel(s)
[  1364.995] (--) evdev: Logitech G9 Laser Mouse: Found relative axes
[  1364.995] (II) evdev: Logitech G9 Laser Mouse: Forcing relative x/y axes to exist.
[  1364.995] (--) evdev: Logitech G9 Laser Mouse: Found absolute axes
[  1364.995] (II) evdev: Logitech G9 Laser Mouse: Forcing absolute x/y axes to exist.
[  1364.995] (--) evdev: Logitech G9 Laser Mouse: Found keys
[  1364.995] (II) evdev: Logitech G9 Laser Mouse: Configuring as mouse
[  1364.995] (II) evdev: Logitech G9 Laser Mouse: Configuring as keyboard
[  1364.995] (II) evdev: Logitech G9 Laser Mouse: Adding scrollwheel support
[  1364.995] (**) evdev: Logitech G9 Laser Mouse: YAxisMapping: buttons 4 and 5
[  1364.995] (**) evdev: Logitech G9 Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1364.995] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input5/event5"
[  1364.995] (II) XINPUT: Adding extended input device "Logitech G9 Laser Mouse" (type: KEYBOARD, id 11)
[  1364.995] (**) Option "xkb_rules" "evdev"
[  1364.995] (**) Option "xkb_model" "pc105"
[  1364.995] (**) Option "xkb_layout" "de"
[  1364.996] (II) evdev: Logitech G9 Laser Mouse: initialized for relative axes.
[  1364.996] (WW) evdev: Logitech G9 Laser Mouse: ignoring absolute axes.
[  1364.996] (**) Logitech G9 Laser Mouse: (accel) keeping acceleration scheme 1
[  1364.996] (**) Logitech G9 Laser Mouse: (accel) acceleration profile 0
[  1364.996] (**) Logitech G9 Laser Mouse: (accel) acceleration factor: 2.000
[  1364.996] (**) Logitech G9 Laser Mouse: (accel) acceleration threshold: 4
[  1364.996] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event6)
[  1364.996] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[  1364.996] (II) Using input driver 'evdev' for 'HID 046a:0023'
[  1364.996] (**) HID 046a:0023: always reports core events
[  1364.996] (**) evdev: HID 046a:0023: Device: "/dev/input/event6"
[  1364.996] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[  1364.996] (--) evdev: HID 046a:0023: Found keys
[  1364.996] (II) evdev: HID 046a:0023: Configuring as keyboard
[  1364.996] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input21/event6"
[  1364.996] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 12)
[  1364.996] (**) Option "xkb_rules" "evdev"
[  1364.996] (**) Option "xkb_model" "pc105"
[  1364.996] (**) Option "xkb_layout" "de"
[  1364.997] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event7)
[  1364.997] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[  1364.997] (II) Using input driver 'evdev' for 'HID 046a:0023'
[  1364.997] (**) HID 046a:0023: always reports core events
[  1364.997] (**) evdev: HID 046a:0023: Device: "/dev/input/event7"
[  1364.997] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[  1364.997] (--) evdev: HID 046a:0023: Found 1 mouse buttons
[  1364.997] (--) evdev: HID 046a:0023: Found scroll wheel(s)
[  1364.997] (--) evdev: HID 046a:0023: Found relative axes
[  1364.997] (II) evdev: HID 046a:0023: Forcing relative x/y axes to exist.
[  1364.997] (--) evdev: HID 046a:0023: Found absolute axes
[  1364.997] (II) evdev: HID 046a:0023: Forcing absolute x/y axes to exist.
[  1364.997] (--) evdev: HID 046a:0023: Found keys
[  1364.997] (II) evdev: HID 046a:0023: Configuring as mouse
[  1364.997] (II) evdev: HID 046a:0023: Configuring as keyboard
[  1364.997] (II) evdev: HID 046a:0023: Adding scrollwheel support
[  1364.997] (**) evdev: HID 046a:0023: YAxisMapping: buttons 4 and 5
[  1364.997] (**) evdev: HID 046a:0023: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1364.997] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/input/input22/event7"
[  1364.997] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 13)
[  1364.997] (**) Option "xkb_rules" "evdev"
[  1364.997] (**) Option "xkb_model" "pc105"
[  1364.997] (**) Option "xkb_layout" "de"
[  1364.997] (II) evdev: HID 046a:0023: initialized for relative axes.
[  1364.997] (WW) evdev: HID 046a:0023: ignoring absolute axes.
[  1364.997] (**) HID 046a:0023: (accel) keeping acceleration scheme 1
[  1364.997] (**) HID 046a:0023: (accel) acceleration profile 0
[  1364.997] (**) HID 046a:0023: (accel) acceleration factor: 2.000
[  1364.997] (**) HID 046a:0023: (accel) acceleration threshold: 4
[  1364.997] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[  1364.997] (II) No input driver specified, ignoring this device.
[  1364.997] (II) This device may have been added with another device file.
[  1364.998] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[  1364.998] (II) No input driver specified, ignoring this device.
[  1364.998] (II) This device may have been added with another device file.
[  1364.998] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event13)
[  1364.998] (II) No input driver specified, ignoring this device.
[  1364.998] (II) This device may have been added with another device file.
[  1364.998] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event14)
[  1364.998] (II) No input driver specified, ignoring this device.
[  1364.998] (II) This device may have been added with another device file.
[  1364.998] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event15)
[  1364.998] (II) No input driver specified, ignoring this device.
[  1364.998] (II) This device may have been added with another device file.
[  1364.998] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  1364.998] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1364.998] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1364.998] (**) AT Translated Set 2 keyboard: always reports core events
[  1364.998] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  1364.998] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  1364.998] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  1364.998] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  1364.998] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  1364.998] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[  1364.998] (**) Option "xkb_rules" "evdev"
[  1364.999] (**) Option "xkb_model" "pc105"
[  1364.999] (**) Option "xkb_layout" "de"
[  1364.999] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event16)
[  1364.999] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  1364.999] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  1364.999] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[  1364.999] (II) LoadModule: "synaptics"
[  1364.999] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1364.999] (II) Module synaptics: vendor="X.Org Foundation"
[  1364.999]     compiled for 1.13.1.901, module version = 1.6.2
[  1364.999]     Module class: X.Org XInput Driver
[  1364.999]     ABI class: X.Org XInput driver, version 18.0
[  1364.999] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  1364.999] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1364.999] (**) Option "Device" "/dev/input/event16"
[  1365.052] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[  1365.052] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[  1365.052] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[  1365.052] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  1365.052] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  1365.052] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  1365.052] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[  1365.052] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1365.052] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1365.088] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input16/event16"
[  1365.088] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 15)
[  1365.088] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  1365.088] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  1365.088] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[  1365.088] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  1365.088] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  1365.088] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  1365.088] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  1365.088] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1365.088] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[  1365.088] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[  1365.090] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event8)
[  1365.090] (**) MSI WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  1365.090] (II) Using input driver 'evdev' for 'MSI WMI hotkeys'
[  1365.090] (**) MSI WMI hotkeys: always reports core events
[  1365.090] (**) evdev: MSI WMI hotkeys: Device: "/dev/input/event8"
[  1365.090] (--) evdev: MSI WMI hotkeys: Vendor 0 Product 0
[  1365.090] (--) evdev: MSI WMI hotkeys: Found keys
[  1365.090] (II) evdev: MSI WMI hotkeys: Configuring as keyboard
[  1365.090] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[  1365.090] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 16)
[  1365.090] (**) Option "xkb_rules" "evdev"
[  1365.090] (**) Option "xkb_model" "pc105"
[  1365.090] (**) Option "xkb_layout" "de"
[  1382.348] (II) evdev: MSI WMI hotkeys: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) UnloadModule: "synaptics"
[  1382.348] (II) evdev: AT Translated Set 2 keyboard: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) evdev: HID 046a:0023: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) evdev: HID 046a:0023: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) evdev: Logitech G9 Laser Mouse: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) evdev: Logitech G9 Laser Mouse: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) evdev: Power Button: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) evdev: Video Bus: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) evdev: Video Bus: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.348] (II) evdev: Power Button: Close
[  1382.348] (II) UnloadModule: "evdev"
[  1382.350] Server terminated successfully (0). Closing log file.


```

---

### Post by Scofa on 2013-07-06
And here is my xorg.cfg

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" RightOf "Screen2"
    Screen      4  "Screen4" RightOf "Screen3"
    Screen      5  "Screen5" RightOf "Screen4"
    Screen      6  "Screen6" RightOf "Screen5"
    Screen      7  "Screen7" RightOf "Screen6"
    Screen      8  "Screen8" RightOf "Screen7"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor3"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor4"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor5"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor6"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor7"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor8"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapLimit"              # <i>
        #Option     "AsyncUTSDFS"            # [<bool>]
    Identifier  "Card1"
    Driver      "nouveau"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier  "Card2"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card3"
    Driver      "modesetting"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card4"
    Driver      "modesetting"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card5"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card6"
    Driver      "fbdev"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card7"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card8"
    Driver      "vesa"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen3"
    Device     "Card3"
    Monitor    "Monitor3"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen4"
    Device     "Card4"
    Monitor    "Monitor4"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen5"
    Device     "Card5"
    Monitor    "Monitor5"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen6"
    Device     "Card6"
    Monitor    "Monitor6"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen7"
    Device     "Card7"
    Monitor    "Monitor7"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen8"
    Device     "Card8"
    Monitor    "Monitor8"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

---

### Post by wojox on 2013-07-06
I found in your second x log file:
```
[ 1364.701] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

---

### Post by Scofa on 2013-07-06
Ok, so the xserver dosnt find my Nvidia driver.... 
do you know how to configure it? :-)

---

### Post by wojox on 2013-07-06
> **Scofa said:**
> 
Then i tryed to install the Nvidia  325.08 driver

What procedure did you follow for this?

---

### Post by Scofa on 2013-07-06
I dontloaded the driver ( .run )
then i closed the xserver with ctlr+alt+F1
i loged in as root
stoped the gdm service
startet the driver, on the first time it toled me to blacklist nouveau driver
reboot
started the driver installation again and it installed the driver with comiling the kernel, and now im here :P

---

### Post by Scofa on 2013-07-06
My question is, why the xorg-server, cant load my nvidia driver.... does somebody knows where i have to confiure it?

---

### Post by tista on 2013-07-06
@Scofa,

I have some questions about it:

#1. Does this laptop have "Hybrid-Graphics" system truthly?

#2. If you want to get something like failsafe, did you aleady tried blacklisting nvidia driver?

Regards,
Tista

---

### Post by Scofa on 2013-07-06
Jeah the Laptop jave the Optimus system
1 intel HD4000 Graphic
2 Nvidia GTX675MX

And i dont tried to blacklist nvidia driver, i blacklist the nouveau driver

---

### Post by tista on 2013-07-06
OK..
So if you did blacklisting both "intel" and "nouveau" driver, could nvidia driver take you to the desktop properly?

Regards,
Tista

---

### Post by Scofa on 2013-07-06
i didnt blacklist intel driver, just the nouveau, and jeah the nouveau driver take me back to the desktop, but it lags, i need the nvidia driver not the nouveau....

---

### Post by Scofa on 2013-07-07
OK guys, i solved the problem with GLX, it was the wrong path in the xorg.cfg for the modules.
But now i get an new error :

> 
(EE) Failed to load module "fbdev" (module does not exist, 0)


---

### Post by Scofa on 2013-07-07
I googled and found out, that i need the xf86-video-fbdev module, i downloaded it and tryed to install, and now he sayes i need the xorg-server first.... i though i have the xorg-server allready....

---

### Post by Scofa on 2013-07-07
Solved this one too, i get raged and reinstalled my whole system, followed by this commends:

apt-get update
apt-get upgrade
apt-get dist-upgrade
reboot
added this to the packetmanager

> 
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) saucy main  
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) saucy main


apt-get update
apt-get upgrade
apt-get install synaptic

then i installed nvidia-325 nvidia-settings-325 and in case i need it the fbdev

followed by reboot.
loged in
nvidia-xconfig
then i changed the module path in xorg-conf
reboot
And now i get this error:

> (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0
[    57.138] (EE) NVIDIA(0): Failing initialization of X screen 0
[    57.138] (II) UnloadModule: "nvidia"
[    57.138] (II) UnloadSubModule: "shadow"
[    57.138] (II) UnloadSubModule: "wfb"
[    57.138] (II) UnloadSubModule: "fb"
[    57.138] (EE) Screen(s) found, but none have a usable configuration.
[    57.138] 
Fatal server error:
[    57.138] no screens found

---

### Post by Scofa on 2013-07-07
And here is my new xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 325.08  (buildmeister@swio-display-x64-rhel04-12)  Wed Jun 26 18:41:44 PDT 2013


Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" RightOf "Screen2"
    Screen      4  "Screen4" RightOf "Screen3"
    Screen      5  "Screen5" RightOf "Screen4"
    Screen      6  "Screen6" RightOf "Screen5"
    Screen      7  "Screen7" RightOf "Screen6"
    Screen      8  "Screen8" RightOf "Screen7"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath      "/usr/lib/x86_64-linux-gnu/xorg/extra-modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "built-ins"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor3"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor4"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor5"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor6"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor7"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

Section "Monitor"
    Identifier     "Monitor8"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection


Section "Device"
   Identifier          "Device0"
   Driver              "nvidia"
   VendorName         "NVIDIA Corporation"
   Option             "ConnectedMonitor"   "DFP-0"
   Option             "CustomEDID"          "DFP-0:/etc/X11/edid.bin"
EndSection


Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapLimit"              # <i>
        #Option     "AsyncUTSDFS"            # [<bool>]
    Identifier     "Card0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier     "Card1"
    Driver         "nvidia"
    BusID          "PCI:0:2:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier     "Card2"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "Backlight"              # <str>
        #Option     "DRI"                    # <str>
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "TearFree"               # [<bool>]
        #Option     "PerCrtcPixmaps"         # [<bool>]
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "BufferCache"            # [<bool>]
    Identifier     "Card3"
    Driver         "nvidia"
    BusID          "PCI:0:2:0"
EndSection

Section "Device"
    Identifier     "Card4"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier     "Card5"
    Driver         "nvidia"
    BusID          "PCI:0:2:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier     "Card6"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier     "Card7"
    Driver         "nvidia"
    BusID          "PCI:0:2:0"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier     "Card8"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Card1"
    Monitor        "Monitor1"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Card2"
    Monitor        "Monitor2"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen3"
    Device         "Card3"
    Monitor        "Monitor3"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen4"
    Device         "Card4"
    Monitor        "Monitor4"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen5"
    Device         "Card5"
    Monitor        "Monitor5"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen6"
    Device         "Card6"
    Monitor        "Monitor6"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen7"
    Device         "Card7"
    Monitor        "Monitor7"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen8"
    Device         "Card8"
    Monitor        "Monitor8"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection


```

---

### Post by uRock on 2013-07-07
Please use code tags, instead of quote tags. Highlight the text, then click the # in the toolbar.

Thanks

---

### Post by Scofa on 2013-07-07
Im sry uRock, i checked it, but u have changed it allready :-)

So who can help me with my problem?

---

### Post by cariboo on 2013-07-07
A couple of things I've noticed in this thread, if you are stating X from a prompt, startx should take you directly to the desktop, so ignore any references to lightdm or GDM.

Why are you trying to use the latest nvidia driver, when there would be far less problems using one of the nvidia drivers from the repositories. 

xorg.conf is no longer being used, so either delete it, or rename it.

You also may want to have a look at [this wiki page]("https://wiki.ubuntu.com/Bumblebee"), as it should help with your graphics problem

---

### Post by Scofa on 2013-07-08
I thougt i dont need bumble anymore if i used the nvidia-319+ driver with kernel 3.10 isnt that right?

---

### Post by Scofa on 2013-07-10
I installed bumblebee now, and it works all fine

---

