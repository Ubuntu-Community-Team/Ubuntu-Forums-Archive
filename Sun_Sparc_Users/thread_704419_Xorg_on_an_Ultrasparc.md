---
title: "Xorg on an Ultrasparc"
date: 2008-02-22
forum: Sun Sparc Users
---

### Post by smroszczak on 2008-02-22
Hello all,

I just got Ubuntu server working on an old UltraSparc and it went remarkably smooth.  Deciding to push my luck, i thought I would try installing "ubuntu-desktop" and see if the window manager would work.

It finished the install, and after rebooting, I heard the Ubuntu "drums" announcing that the GDM had started, but I get a "mode not supported" on my LCD monitor.  I fixed the xorg.conf file with the correct vsync and hsync options, but no dice.  I suspect there is a problem with the graphics card instead, but I am not sure if that is correct.  My Xorg.log file is below, followed by my xorg.conf.  Is there a clue in there to why it is not working?
```

> 
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux sunserver 2.6.22-14-sparc64 #1 Tue Feb 12 03:18:52 UTC 2008 sparc64
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 22 09:19:22 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "-e ATI Technologies 3D Rage Pro or similar (ATY,RageXL)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x1d2ad4
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 108e,a001 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:03:0: chip 10b9,7101 card 0000,0000 rev 00 class 00,00,00 hdr 00
(II) PCI: 00:05:0: chip 1011,0024 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 10b9,1533 card 10b9,1533 rev 00 class 06,01,00 hdr 00
(II) PCI: 00:08:0: chip 10b9,5451 card 10b9,5451 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:0c:0: chip 108e,1100 card 0000,0000 rev 01 class 06,80,00 hdr 80
(II) PCI: 00:0c:1: chip 108e,1101 card 0000,0000 rev 01 class 02,00,00 hdr 80
(II) PCI: 00:0c:2: chip 108e,1102 card 0000,0000 rev 01 class 0c,00,10 hdr 80
(II) PCI: 00:0c:3: chip 108e,1103 card 0000,0000 rev 01 class 0c,03,10 hdr 80
(II) PCI: 00:0d:0: chip 10b9,5229 card 0000,0000 rev c3 class 01,01,ff hdr 00
(II) PCI: 00:13:0: chip 1002,4752 card 0000,0000 rev 27 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	1	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	1	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	1	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:5:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:19:0) ATI Technologies Inc Rage XL rev 39, Mem @ 0x03000000/24, 0x00426000/13, I/O @ 0x0b00/8, BIOS @ 0x00440000/17
(II) Addressable bus resource ranges are
	[0] -1	1	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	1	0x00000000 - 0x00ffffff (0x1000000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[5] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Active PCI resource ranges:
	[0] -1	1	0x02000000 - 0x02ffffff (0x1000000) MX[B]
	[1] -1	1	0x00422000 - 0x00423fff (0x2000) MX[B]
	[2] -1	1	0x00420000 - 0x00421fff (0x2000) MX[B]
	[3] -1	1	0x00400000 - 0x0041ffff (0x20000) MX[B]
	[4] -1	1	0xf1000000 - 0xf1000000 (0x1) MX[B]
	[5] -1	1	0xf0000000 - 0xf0000000 (0x1) MX[B]
	[6] -1	1	0x00424000 - 0x00425fff (0x2000) MX[B]
	[7] -1	1	0x00440000 - 0x0045ffff (0x20000) MX[B](B)
	[8] -1	1	0x00426000 - 0x00427fff (0x2000) MX[B](B)
	[9] -1	1	0x03000000 - 0x03ffffff (0x1000000) MX[B](B)
	[10] -1	1	0x00000a20 - 0x00000a2f (0x10) IX[B]
	[11] -1	1	0x00000a08 - 0x00000a0f (0x8) IX[B]
	[12] -1	1	0x00000a10 - 0x00000a17 (0x8) IX[B]
	[13] -1	1	0x00000a18 - 0x00000a1f (0x8) IX[B]
	[14] -1	1	0x00000a00 - 0x00000a07 (0x8) IX[B]
	[15] -1	1	0x00000900 - 0x000009ff (0x100) IX[B]
	[16] -1	1	0x00000b00 - 0x00000bff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	1	0x02000000 - 0x02ffffff (0x1000000) MX[B]
	[1] -1	1	0x00422000 - 0x00423fff (0x2000) MX[B]
	[2] -1	1	0x00420000 - 0x00421fff (0x2000) MX[B]
	[3] -1	1	0x00400000 - 0x0041ffff (0x20000) MX[B]
	[4] -1	1	0xf1000000 - 0xf1000000 (0x1) MX[B]
	[5] -1	1	0xf0000000 - 0xf0000000 (0x1) MX[B]
	[6] -1	1	0x00424000 - 0x00425fff (0x2000) MX[B]
	[7] -1	1	0x00440000 - 0x0045ffff (0x20000) MX[B](B)
	[8] -1	1	0x00426000 - 0x00427fff (0x2000) MX[B](B)
	[9] -1	1	0x03000000 - 0x03ffffff (0x1000000) MX[B](B)
	[10] -1	1	0x00000a20 - 0x00000a2f (0x10) IX[B]
	[11] -1	1	0x00000a08 - 0x00000a0f (0x8) IX[B]
	[12] -1	1	0x00000a10 - 0x00000a17 (0x8) IX[B]
	[13] -1	1	0x00000a18 - 0x00000a1f (0x8) IX[B]
	[14] -1	1	0x00000a00 - 0x00000a07 (0x8) IX[B]
	[15] -1	1	0x00000900 - 0x000009ff (0x100) IX[B]
	[16] -1	1	0x00000b00 - 0x00000bff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[5] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
(II) All system resource ranges:
	[0] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x02000000 - 0x02ffffff (0x1000000) MX[B]
	[5] -1	1	0x00422000 - 0x00423fff (0x2000) MX[B]
	[6] -1	1	0x00420000 - 0x00421fff (0x2000) MX[B]
	[7] -1	1	0x00400000 - 0x0041ffff (0x20000) MX[B]
	[8] -1	1	0xf1000000 - 0xf1000000 (0x1) MX[B]
	[9] -1	1	0xf0000000 - 0xf0000000 (0x1) MX[B]
	[10] -1	1	0x00424000 - 0x00425fff (0x2000) MX[B]
	[11] -1	1	0x00440000 - 0x0045ffff (0x20000) MX[B](B)
	[12] -1	1	0x00426000 - 0x00427fff (0x2000) MX[B](B)
	[13] -1	1	0x03000000 - 0x03ffffff (0x1000000) MX[B](B)
	[14] -1	1	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	1	0x00000a20 - 0x00000a2f (0x10) IX[B]
	[17] -1	1	0x00000a08 - 0x00000a0f (0x8) IX[B]
	[18] -1	1	0x00000a10 - 0x00000a17 (0x8) IX[B]
	[19] -1	1	0x00000a18 - 0x00000a1f (0x8) IX[B]
	[20] -1	1	0x00000a00 - 0x00000a07 (0x8) IX[B]
	[21] -1	1	0x00000900 - 0x000009ff (0x100) IX[B]
	[22] -1	1	0x00000b00 - 0x00000bff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 00:13:0
(II) Loading sub module "atimisc"
(II) LoadModule: "atimisc"
(II) Loading /usr/lib/xorg/modules/drivers//atimisc_drv.so
(II) Module atimisc: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) ATI: Driver for ATI Mach64 chipsets
(--) Chipset ATI 3D Rage XL or XC found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x02000000 - 0x02ffffff (0x1000000) MX[B]
	[5] -1	1	0x00422000 - 0x00423fff (0x2000) MX[B]
	[6] -1	1	0x00420000 - 0x00421fff (0x2000) MX[B]
	[7] -1	1	0x00400000 - 0x0041ffff (0x20000) MX[B]
	[8] -1	1	0xf1000000 - 0xf1000000 (0x1) MX[B]
	[9] -1	1	0xf0000000 - 0xf0000000 (0x1) MX[B]
	[10] -1	1	0x00424000 - 0x00425fff (0x2000) MX[B]
	[11] -1	1	0x00440000 - 0x0045ffff (0x20000) MX[B](B)
	[12] -1	1	0x00426000 - 0x00427fff (0x2000) MX[B](B)
	[13] -1	1	0x03000000 - 0x03ffffff (0x1000000) MX[B](B)
	[14] -1	1	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	1	0x00000a20 - 0x00000a2f (0x10) IX[B]
	[17] -1	1	0x00000a08 - 0x00000a0f (0x8) IX[B]
	[18] -1	1	0x00000a10 - 0x00000a17 (0x8) IX[B]
	[19] -1	1	0x00000a18 - 0x00000a1f (0x8) IX[B]
	[20] -1	1	0x00000a00 - 0x00000a07 (0x8) IX[B]
	[21] -1	1	0x00000900 - 0x000009ff (0x100) IX[B]
	[22] -1	1	0x00000b00 - 0x00000bff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0x02000000 - 0x02ffffff (0x1000000) MX[B]
	[5] -1	1	0x00422000 - 0x00423fff (0x2000) MX[B]
	[6] -1	1	0x00420000 - 0x00421fff (0x2000) MX[B]
	[7] -1	1	0x00400000 - 0x0041ffff (0x20000) MX[B]
	[8] -1	1	0xf1000000 - 0xf1000000 (0x1) MX[B]
	[9] -1	1	0xf0000000 - 0xf0000000 (0x1) MX[B]
	[10] -1	1	0x00424000 - 0x00425fff (0x2000) MX[B]
	[11] -1	1	0x00440000 - 0x0045ffff (0x20000) MX[B](B)
	[12] -1	1	0x00426000 - 0x00427fff (0x2000) MX[B](B)
	[13] -1	1	0x03000000 - 0x03ffffff (0x1000000) MX[B](B)
	[14] 0	1	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	1	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	1	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	1	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[18] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	1	0x00000a20 - 0x00000a2f (0x10) IX[B]
	[20] -1	1	0x00000a08 - 0x00000a0f (0x8) IX[B]
	[21] -1	1	0x00000a10 - 0x00000a17 (0x8) IX[B]
	[22] -1	1	0x00000a18 - 0x00000a1f (0x8) IX[B]
	[23] -1	1	0x00000a00 - 0x00000a07 (0x8) IX[B]
	[24] -1	1	0x00000900 - 0x000009ff (0x100) IX[B]
	[25] -1	1	0x00000b00 - 0x00000bff (0x100) IX[B](B)
	[26] 0	1	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	1	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) ATI(0): Depth 24, (--) framebuffer bpp 32
(==) ATI(0): Using XAA acceleration architecture
(II) ATI: Shared PCI/AGP Mach64 in slot 0:19:0 detected.
(II) ATI(0): BIOS Data:  BIOSSize=0x0000, ROMTable=0x0000.
(II) ATI(0): BIOS Data:  ClockTable=0x0000, FrequencyTable=0x0000.
(II) ATI(0): BIOS Data:  LCDTable=0x0000, LCDPanelInfo=0x0000.
(II) ATI(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x0000.
(II) ATI(0): BIOS Data:  I2CType=0x00, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) ATI(0): ATI 3D Rage XL or XC graphics controller detected.
(--) ATI(0): Chip type 4752 "GR", version 7, foundry TSMC, class 0, revision 0x00.
(--) ATI(0): PCI bus interface detected.
(--) ATI(0): ATI Mach64 adapter detected.
(!!) ATI(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) ATI(0): Internal RAMDAC (subtype 1) detected.
(==) ATI(0): RGB weight 888
(==) ATI(0): Default visual is TrueColor
(==) ATI(0): Using gamma correction (1.0, 1.0, 1.0)
(II) ATI(0): Using Mach64 accelerator CRTC.
(II) ATI(0): Storing hardware cursor image at 0x037FFC00.
(II) ATI(0): Using 8 MB linear aperture at 0x03800000.
(!!) ATI(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) ATI(0): Using Block 0 MMIO aperture at 0x00426400.
(II) ATI(0): Using Block 1 MMIO aperture at 0x00426000.
(II) ATI(0): MMIO write caching enabled.
(--) ATI(0): 8192 kB of SDRAM (1:1) detected (using 8191 kB).
(WW) ATI(0): Cannot shadow an accelerated frame buffer.
(II) ATI(0): Engine XCLK 30.399 MHz;  Refresh rate code 1.
(--) ATI(0): Internal programmable clock generator detected.
(--) ATI(0): Reference clock 157.5/11 (14.318) MHz.
(II) ATI(0): Generic Monitor: Using hsync range of 30.00-81.00 kHz
(II) ATI(0): Generic Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) ATI(0): Maximum clock:  60.00 MHz
(II) ATI(0): Not using default mode "640x350" (vrefresh out of range)
(II) ATI(0): Not using default mode "320x175" (vrefresh out of range)
(II) ATI(0): Not using default mode "640x400" (vrefresh out of range)
(II) ATI(0): Not using default mode "320x200" (vrefresh out of range)
(II) ATI(0): Not using default mode "720x400" (vrefresh out of range)
(II) ATI(0): Not using default mode "360x200" (vrefresh out of range)
(II) ATI(0): Not using default mode "640x480" (vrefresh out of range)
(II) ATI(0): Not using default mode "320x240" (vrefresh out of range)
(II) ATI(0): Not using default mode "800x600" (vrefresh out of range)
(II) ATI(0): Not using default mode "400x300" (vrefresh out of range)
(II) ATI(0): Not using default mode "1024x768" (vrefresh out of range)
(II) ATI(0): Not using default mode "512x384" (vrefresh out of range)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "512x384" (vrefresh out of range)
(II) ATI(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ATI(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ATI(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ATI(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ATI(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "576x384" (vrefresh out of range)
(II) ATI(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using mode "1280x1024" (no mode of this name)
(II) ATI(0): Not using mode "1024x768" (no mode of this name)
(II) ATI(0): Not using default mode "832x624" (width too large for virtual size)
(--) ATI(0): Virtual size is 800x600 (pitch 800)
(**) ATI(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) ATI(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) ATI(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) ATI(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) ATI(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) ATI(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) ATI(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) ATI(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) ATI(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) ATI(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) ATI(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) ATI(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) ATI(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) ATI(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) ATI(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) ATI(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) ATI(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) ATI(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) ATI(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) ATI(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) ATI(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) ATI(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) ATI(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) ATI(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) ATI(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) ATI(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) ATI(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) ATI(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) ATI(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) ATI(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) ATI(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) ATI(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) ATI(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) ATI(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) ATI(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) ATI(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(==) ATI(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) ATI(0): I2C bus "Mach64" initialized.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	1	0x00426000 - 0x00427fff (0x2000) MS[B]
	[1] 0	1	0x03000000 - 0x03ffffff (0x1000000) MS[B]
	[2] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[3] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	1	0x02000000 - 0x02ffffff (0x1000000) MX[B]
	[7] -1	1	0x00422000 - 0x00423fff (0x2000) MX[B]
	[8] -1	1	0x00420000 - 0x00421fff (0x2000) MX[B]
	[9] -1	1	0x00400000 - 0x0041ffff (0x20000) MX[B]
	[10] -1	1	0xf1000000 - 0xf1000000 (0x1) MX[B]
	[11] -1	1	0xf0000000 - 0xf0000000 (0x1) MX[B]
	[12] -1	1	0x00424000 - 0x00425fff (0x2000) MX[B]
	[13] -1	1	0x00440000 - 0x0045ffff (0x20000) MX[B](B)
	[14] -1	1	0x00426000 - 0x00427fff (0x2000) MX[B](B)
	[15] -1	1	0x03000000 - 0x03ffffff (0x1000000) MX[B](B)
	[16] 0	1	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	1	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	1	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] 0	1	0x00000b00 - 0x00000bff (0x100) IS[B]
	[20] -1	1	0x00ffffff - 0x00ffffff (0x1) IX[B]
	[21] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	1	0x00000a20 - 0x00000a2f (0x10) IX[B]
	[23] -1	1	0x00000a08 - 0x00000a0f (0x8) IX[B]
	[24] -1	1	0x00000a10 - 0x00000a17 (0x8) IX[B]
	[25] -1	1	0x00000a18 - 0x00000a1f (0x8) IX[B]
	[26] -1	1	0x00000a00 - 0x00000a07 (0x8) IX[B]
	[27] -1	1	0x00000900 - 0x000009ff (0x100) IX[B]
	[28] -1	1	0x00000b00 - 0x00000bff (0x100) IX[B](B)
	[29] 0	1	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	1	0x000003c0 - 0x000003df (0x20) IS[B]
(II) ATI(0): [drm] SAREA 2200+1208: 3408
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
[drm] failed to load kernel module "mach64"
(II) ATI(0): [drm] drmOpen failed
(EE) ATI(0): [dri] DRIScreenInit Failed
(II) ATI(0): Largest offscreen areas (with overlaps):
(II) ATI(0): 	800 x 2021 rectangle at 0,600
(II) ATI(0): 	96 x 2022 rectangle at 0,600
(II) ATI(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		14 256x256 slots
(==) ATI(0): Backing store disabled
(==) ATI(0): Silken mouse enabled
(**) Option "dpms"
(**) ATI(0): DPMS enabled
(WW) ATI(0): Option "UseFBDev" is not used
(II) ATI(0): Direct rendering disabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded



> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"-e ATI Technologies 3D Rage Pro or similar (ATY,RageXL)"
	Driver		"ati"
	BusID		"PCI:0:19:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"-e ATI Technologies 3D Rage Pro or similar (ATY,RageXL)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600"
#		Modes		"1280x1024" "800x600"

	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection






```

---

### Post by smroszczak on 2008-02-25
Bump.

---

### Post by jcastill on 2008-02-27
I heard that UltraSPARC ATI GPU's got a problem with the newest X11 servers. Did you try using dapper?

---

### Post by smroszczak on 2008-02-27
No, I haven't I went right to the latest.  

I just had another thought, is it possible to use an older version of X11 without rolling back the whole distribution?  I am used to Gentoo Linux, and there you could "emerge" (install) older versions of applications that were still in the portage tree.  It would be nice to just roll back the window manager, but keep all the backend server stuff at the latest versions.  Is that possible?



-Steve

---

### Post by fufutos610 on 2008-02-28
From [http://www.gentoo.ro/doc/en/gentoo-sparc-faq.xml#doc_chap4](http://www.gentoo.ro/doc/en/gentoo-sparc-faq.xml#doc_chap4)

add the following option in the Device section of xorg.conf:

Option      "reference_clock"   "28.636 MHz"

some models may do better with "29.5MHz"

---

### Post by smroszczak on 2008-02-28
Ah, the good old Gentoo forums... The 28.636 MHz option worked for me, thank you very much!

-Steve

---

### Post by Spark19 on 2008-07-24
Guys,

Could someone specify where in the xorg.conf do we provide the reference clock and whats the exact format that worked for you?

If possible please post the xorg.conf.

Thanks.

---

