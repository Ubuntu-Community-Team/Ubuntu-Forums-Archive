---
title: "Ultra 60 Elite 3D xorg problem"
date: 2007-03-13
forum: Sun Sparc Users
---

### Post by jcastill on 2007-03-13
Hi, we just got some Ultra 60 machines and wanted to try ubuntu on them, as this model does not have CD-ROM I tried using the netinstall which worked "great".

I read the forums and the advice to Load cfb and cfb32; as well as using sunffb as driver; yet I cannot get to start xorg... Aparently there's nothing on Xorg.0.log and xorg.conf seems to be ok (below you can find copies)

Anybody knows what's my error? I've been all day trying to fix it without results.

Thanks!

Xorg.0.log
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-26-sparc64 sparc
Current Operating System: Linux lattecoco 2.6.15-28-sparc64-smp #1 SMP Thu Feb 1 16:49:08 UTC 2007 sparc64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 13 16:49:52 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Sun Creator3D"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 80:00:0: chip 108e,8000 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 128: bridge is at (128:0:0), (128,128,128), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 128 I/O range:
	[0] -1	1	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 128 non-prefetchable memory range:
	[0] -1	1	0x00000000 - 0x7fffffff (0x80000000) MX[B]
(II) Bus 128 prefetchable memory range:
	[0] -1	1	0x00000000 - 0x7fffffff (0x80000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(--) SBUS:(0xf006e270) Sun Elite3D at /SUNW,afb@1e,0
(II) Addressable bus resource ranges are
	[0] -1	1	0x00000000 - 0x7fffffff (0x80000000) MX[B]
	[1] -1	1	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	1	0x7fffffff - 0x7fffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	1	0x7fffffff - 0x7fffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
(II) All system resource ranges:
	[0] -1	1	0x7fffffff - 0x7fffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "cfb"
(II) Loading /usr/lib/xorg/modules/libcfb.so
(II) Module cfb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "mfb"
(II) LoadModule: "mfb"
(II) Loading /usr/lib/xorg/modules/libmfb.so
(II) Module mfb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) LoadModule: "cfb32"
(II) Loading /usr/lib/xorg/modules/libcfb32.so
(II) Module cfb32: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "cfb"
(II) LoadModule: "cfb"
(II) Reloading /usr/lib/xorg/modules/libcfb.so
(II) Loading sub module "mfb"
(II) LoadModule: "mfb"
(II) Reloading /usr/lib/xorg/modules/libmfb.so
(II) LoadModule: "sunffb"
(II) Loading /usr/lib/xorg/modules/drivers/sunffb_drv.so
(II) Module sunffb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) SUNFFB: driver for Creator, Creator 3D and Elite 3D
(--) Assigning device section with no busID to SBUS:/SUNW,afb@1e,0
(II) resource ranges after probing:
	[0] -1	1	0x7fffffff - 0x7fffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
(==) SUNFFB(0): RGB weight 888
(==) SUNFFB(0): Default visual is TrueColor
(==) SUNFFB(0): Using gamma correction (1.0, 1.0, 1.0)
(==) SUNFFB(0): Using HW cursor
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(++) SUNFFB(0): DPI set to (100, 100)
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	1	0x7fffffff - 0x7fffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
(II) /dev/fb0: AFB: Detected Elite3D/M6.
(II) /dev/fb0: BT498 (PAC2) ramdac detected
(II) /dev/fb0: Detected Elite3D M3/M6, checking firmware...
(II) /dev/fb0: ... AFB firmware not loaded
(WW) /dev/fb0: Forcing no acceleration on Elite3D M3/M6
(==) SUNFFB(0): Backing store disabled
(==) SUNFFB(0): Silken mouse enabled
(**) Option "dpms"
(**) SUNFFB(0): DPMS enabled
(**) SUNFFB(0): DPMS enabled
(WW) SUNFFB(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:

Fatal server error:
Caught signal 11.  Server aborting

```

xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"cfb"
	Load	"cfb32"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Sun Creator3D"
	Driver		"sunffb"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Sun Creator3D"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by netztier on 2007-03-14
> **jcastill said:**
> 

```
[COLOR="Red"](II) /dev/fb0: ... AFB firmware not loaded[/COLOR]
```

Anybody knows what's my error? I've been all day trying to fix it without results.


If it really is a Elite3D, you need the AFB Microcode. I don't know all the details, but this here might help as a starting point:

[http://www.ubuntuforums.org/showpost.php?p=1673729&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1673729&postcount=11)

best regards

Marc

---

### Post by jcastill on 2007-03-20
Thanks you Marc.

Sorry for the delay answering, but we finally got xorg working along with sound (we read the "howto" on another post.

Now, as we got like 8 Ultra 60, we are making a little bash script for installing them (just run and forget) And when we got something "cool" I would like to help people and release it; do you know if Sun allows public distribution of the afb.ucode file?

Also, I was wondering what to install in order to be able to reproduce mp3 files and some video. I already have vlc installed but I wish amarok to be able to play them; so far I found no help in which codecs to install.

Thanks for the support you give to sparc users Marc, without you I wouldn't be writing this post from the Ultra60.

Cheers

Jose

---

### Post by netztier on 2007-03-20
> **jcastill said:**
> 
Now, as we got like 8 Ultra 60, we are making a little bash script for installing them (just run and forget) And when we got something "cool" I would like to help people and release it; do you know if Sun allows public distribution of the afb.ucode file?

I am not an expert if it comes to licensing etc., so my advice might be wrong altogether. 

From my intuition, I think if you provide & distribute a script that will download a solaris patch from it's official source location and extracts the afb.ucode file from there, you "might get away with it", so to speak. I think there are similar approaches being used with flashplayer-installer, where Ubuntu or Debian just provide the installer script that will in turn download what's needed from the official source and install it.

> **jcastill said:**
> 
Also, I was wondering what to install in order to be able to reproduce mp3 files and some video. I already have vlc installed but I wish amarok to be able to play them; so far I found no help in which codecs to install.

Well, once you've got sound running, you just need the correct **gstreamer-0.10-plugins-***, where * is for **base**,** good**,** bad**, **bad-multiverse**, **ugly** and **ugly-multiverse**. I can't remember if all of these are available for SPARC, but at least some should. Don't expect full Windows Media Audio/Video support or DVD playback - some might work, most won't. But mp3 and most movie formats should be supported.

If your installation still has gstreamer-0.8, use the -0.8 plugin packages. They are named differently, but I think you'll be able to figure out what you'll need.

I wonder... does (and how good?) OpenGL work on the Elite3D cards? All my Sparcs crash X11 instantly when launching certain OpenGL apps (such as an X.org screensaver). Some apps work, others crash X11 with a Signal 11. :(  This is on both Dapper and Edgy, both with the ati driver (Ultra 5) as on the sunffb driver (Creator in Ultra 2 and Creator3D in Ultra 60).

best regards

Marc

---

### Post by jcastill on 2007-03-20
> **netztier said:**
> I am not an expert if it comes to licensing etc., so my advice might be wrong altogether. 

From my intuition, I think if you provide & distribute a script that will download a solaris patch from it's official source location and extracts the afb.ucode file from there, you "might get away with it", so to speak. I think there are similar approaches being used with flashplayer-installer, where Ubuntu or Debian just provide the installer script that will in turn download what's needed from the official source and install it.


I'll try to implement that before "public" release, as right now I just download the file from the same server the script is. Thanks for your suggestion and hope Sun doesn't bother.


> **netztier said:**
> Well, once you've got sound running, you just need the correct **gstreamer-0.10-plugins-***, where * is for **base**,** good**,** bad**, **bad-multiverse**, **ugly** and **ugly-multiverse**. I can't remember if all of these are available for SPARC, but at least some should. Don't expect full Windows Media Audio/Video support or DVD playback - some might work, most won't. But mp3 and most movie formats should be supported.

If your installation still has gstreamer-0.8, use the -0.8 plugin packages. They are named differently, but I think you'll be able to figure out what you'll need.

I wonder... does (and how good?) OpenGL work on the Elite3D cards? All my Sparcs crash X11 instantly when launching certain OpenGL apps (such as the some screensavers). Some apps work, others crash X11 with a Signal 11. :(  This is on both Dapper and Edgy, both with the ati driver (Ultra 5) as on the sunffb driver (Creator in Ultra 2 and Creator3D in Ultra 60).

best regards

Marc

We have the same problem, if the OpenGL apps work, it slows the computer a lot (just tried screensaver previews, will investigate further) or X11 simply restarts.

Also I have just tried Dapper on this machines (as we started testing on a Sunblade 150 and edgy,feisty didn't get passed the "booting linux" message) I will try to dist-upgrade one Ultra60 right now to edgy and see what happens. I will also reboot the Sunblade150 (with ATI driver) to see if OpenGL works better there.

You have any "non-screensaver" OpenGL apps we can test that crashes with you?

Thanks

Jose

---

### Post by netztier on 2007-03-20
> **jcastill said:**
> 
You have any "non-screensaver" OpenGL apps we can test that crashes with you?


Well, **Blender** from [www.blender.org]("www.blender.org") is one that comes to mind, but I doubt that it's available for SPARC - I'll have to boot one of the Ultras tonight to check.

In general, I launch the small OpenGL screensaver apps from the command line directly; they're all in **/usr/lib/xscreensaver/**. I'll investigate as much as possible tonight and then I think I'll raise a bug on launchpad if there isn't already one.

best regards

Marc.

---

### Post by jcastill on 2007-03-20
> **netztier said:**
> Well, **Blender** from [www.blender.org]("www.blender.org") is one that comes to mind, but I doubt that it's available for SPARC - I'll have to boot one of the Ultras tonight to check.

In general, I launch the small OpenGL screensaver apps from the command line directly; they're all in **/usr/lib/xscreensaver/**. I'll investigate as much as possible tonight and then I think I'll raise a bug on launchpad if there isn't already one.

best regards

Marc.

I tried Bender, it did compile, but I got this error when I tried running it (Special note... I tried to run it on the Ultra60 that has 2 Elite3D cards, don't know if that makes a difference)

```
(**) SUNFFB(1): DPMS enabled
(**) SUNFFB(1): DPMS enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
error opening security policy file /etc/X11/xserver/SecurityPolicy
(II) Configured Mouse: ps2EnableDataReporting: succeeded
AUDIT: Tue Mar 20 10:36:10 2007: 3625 X: client 1 rejected from local host
AUDIT: Tue Mar 20 10:36:10 2007: 3625 X: client 3 rejected from local host

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:

Fatal server error:
Caught signal 10.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

```


Thanks again

Jose

---

### Post by netztier on 2007-03-20
> **jcastill said:**
> 
```

Fatal server error:
Caught signal 10.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

```

Same here. My Blender installation comes from the universe repositories, I didn't bother (re)compiling it. My U 60 also has two (Creator 3D) cards and is running Xinerama. And X.org dies instantly when starting one of the screensaver hacks from /usr/lib/xscreensaver, with the very same error. :-(

best regards

Marc

---

### Post by jcastill on 2007-03-21
Do you know if OpenGl is supported in the SPARC platform? I'm going to try (hopefully later today) in the sunblade150 to see if it works.

Also, a dist-upgrade to edgy worked great on the ultra60 although the sunblade150 won't work. I'm right now dist-upgrading another ultra60 to feisty to see if it works (the sunblade150 also doesn't work on feisty)

By the way; does your ultra60 has cd-rom? or do you use a netinstall? So far I've only seen netinstall for dapper, (I setup apt-proxy on a server to avoid getting the packages over and over again) So any comments on how do you install your ultra60 would rock.

Thanks

Jose

---

### Post by jcastill on 2007-03-22
Same result in the Sunblade150 with the ATI video card.

Does anybody know if OpenGl works at all in the SPARC platform?

Thanks

Jose

---

### Post by netztier on 2007-03-23
> **jcastill said:**
> 
Does anybody know if OpenGl works at all in the SPARC platform?


Well, I think it basically does - and it did - I remember that it ran when I was still compiling kernels and software for days and day... eh running Gentoo on the Ultras. But that was almost two years ago.

The slowness when running a (working) OpenGL Screensaver preview comes from the fact that OpenGL rendering is done via Mesa, i.e. in Software on the CPU, and not with hardware-acceleration on the video card.

I think the problem might be somewhere near MESA library and interfaces - but that's just a guess, might be all wrong here. 

best regards

Marc

---

### Post by jcastill on 2007-03-26
Thanks, I'll try to check why OpenGl doesn't work and if you have any idea on how to fix it or any possible test you would like us to do please say.

Thanks

Jose

---

### Post by Obewizan on 2007-07-22
Hello,

I have recently installed Ubuntu on a Sun Ultra 60, and despite many late nights and a couple thousand forum threads, I still cannot load afbinit and get it to recognize the afb.ucode. My graphics card is an elite 3d, so this has to work in order to launch the GNOME. Have you completed the Batch file you spoke of (just run and forget)? I could use any help that you may be able to offer. I am new to Ubuntu and linux so I need very detailed instructions - most forums and threads do not offer this information so it is difficult to understand exactly what I am doing.

Can anyone please provide very detailed instructions (almost idiotic) that would walk me through the installation of this elite 3d graphics card.


Thanks for the help,
Benjamin

---

### Post by jcastill on 2007-09-05
Sorry, summer came along and that's why it took me so long to answer. Well, The script is right now just made for working out of the box with our Ultra60 machines, I will PM you so you can test the script and maybe help testing it on an outside place.

Netztier, with the update to feisty I can run blender on ubuntu without problem, same for the screensavers; yet I THINK it's software opengl as it's very slow. Got any ideas on how to check if it's hardware or software? Maybe if it's hardware we can make compiz or beryl work (I LOVE TO DREAM =P~)

Also, if you would kindly give me a walk through on how to make the creator3d cards you have on your ultra60 under X.org so I can integrate it to the script for others to use (and ourself)

Thanks and I promise to keep in touch now

---

### Post by netztier on 2007-09-06
> **jcastill said:**
> 
Also, if you would kindly give me a walk through on how to make the creator3d cards you have on your ultra60 under X.org so I can integrate it to the script for others to use (and ourself)


[http://ubuntuforums.org/showthread.php?t=213883&highlight=sunffb+cfb32](http://ubuntuforums.org/showthread.php?t=213883&highlight=sunffb+cfb32) holds almost anything I needed to know to make my Creator3Ds work. "sunffb" and "cfb32" might be the best search keywords 

best regards

Marc

---

