---
title: "computer crashes when viewing page from local host"
date: 2009-09-29
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-09-29
i'm hosting a web site on my pc running ubuntu 9.

when I open a certain page on the localhost, the screen turns black, some text flashes, and i have to log-in. (all processes are killed)

this problem was happening (seemingly) random, but now this one particular page causes the crash every time i view it. The page has a lot of java applets. I don't know if that has anything to do with it.

the page works fine when viewing it from another computer, via LAN or WWW. the problem is only when i view it form the localhost.

I don't even know how to begin solving this problem.

please help

---

### Post by undecim on 2009-09-29
Sounds like it's killing your X server. Post the output of /var/log/Xorg.0.old (after a crash)

---

### Post by rhythmiccycle on 2009-09-30
i went to the page to cause the crash
then opened the file you said with cat
this is the output:
```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 30 00:37:20 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0xd0200000/524288, 0xc0000000/268435456, 0xd0280000/262144, I/O @ 0x0000e400/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xD0200000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): Output VGA connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA using initial mode 1152x864
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000000 to 0x00000203
(WW) intel(0): PIPEASTAT before: status:
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
(WW) intel(0): DRI2 requires UXA
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xd0200000
(II) intel(0): [dri] visual configs initialized
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 33423360 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0e015000 (pgoffset 57365)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x00009fff: HW cursors (40 kB, 0x000000003f800000 physical
)
(II) intel(0): 0x0000a000-0x0000afff: overlay registers (4 kB, 0x000000003f80a000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x0e014fff: DRI memory manager (221528 kB)
(II) intel(0): 0x0e015000-0x0fff4fff: exa offscreen (32640 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x007bf000:            start of memory manager
(II) intel(0): 0x01000000-0x01ffffff: depth buffer (16384 kB) X tiled
(II) intel(0): 0x02000000-0x02ffffff: back buffer (16384 kB) X tiled
(II) intel(0): 0x03000000-0x03ffffff: front buffer (16384 kB) X tiled
(II) intel(0): 0x0e015000:            end of memory manager
(WW) intel(0): ESR is 0x00000001, instruction error
(WW) intel(0): Existing errors found in hardware state.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] mapped front buffer at 0xc3000000, handle = 0xc3000000
(II) intel(0): [drm] mapped back buffer at 0xc2000000, handle = 0xc2000000
(II) intel(0): [drm] mapped depth buffer at 0xc1000000, handle = 0xc1000000
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: XF86DRI Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 304 x 228
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device GenPS/2 Genius Mouse
(**) GenPS/2 Genius Mouse: always reports core events
(**) GenPS/2 Genius Mouse: Device: "/dev/input/event5"
(II) GenPS/2 Genius Mouse: Found 5 mouse buttons
(II) GenPS/2 Genius Mouse: Found x and y relative axes
(II) GenPS/2 Genius Mouse: Configuring as mouse
(**) GenPS/2 Genius Mouse: YAxisMapping: buttons 4 and 5
(**) GenPS/2 Genius Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "GenPS/2 Genius Mouse" (type: MOUSE)
(**) GenPS/2 Genius Mouse: (accel) keeping acceleration scheme 1
(**) GenPS/2 Genius Mouse: (accel) filter chain progression: 2.00
(**) GenPS/2 Genius Mouse: (accel) filter stage 0: 20.00 ms
(**) GenPS/2 Genius Mouse: (accel) set acceleration profile 0
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_D" initialized.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_D:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_D:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_D:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_D" removed.
(II) intel(0): I2C bus "CRTDDC_E" initialized.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_E:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_E:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_E:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_E" removed.

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb80b2400]
3: /usr/lib/xorg/modules//libfb.so(fbBltStip+0x73) [0xb7859583]
4: /usr/lib/xorg/modules//libfb.so(fbGetImage+0x228) [0xb785e868]
5: /usr/lib/xorg/modules//libexa.so(exaGetImage+0x152) [0xb783e7f2]
6: /usr/X11R6/bin/X [0x81248e5]
7: /usr/X11R6/bin/X(ProcGetImage+0x56b) [0x808b45b]
8: /usr/X11R6/bin/X(Dispatch+0x33f) [0x808d57f]
9: /usr/X11R6/bin/X(main+0x3bd) [0x80722ed]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c84775]
11: /usr/X11R6/bin/X [0x80717a1]
Saw signal 11.  Server aborting.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) GenPS/2 Genius Mouse: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
 ddxSigGiveUp: Closing log


```

btw: i went to the same page (again, after crashing it 3 times in a row), and it didn't crash this time. 9 out of 10 times the page made it crash.

---

### Post by hessiess on 2009-09-30
What exactly is the page doing, does it contain javascript?

---

### Post by rhythmiccycle on 2009-09-30
here is a link to the page (with the log-in stuff removed):
[http://maliszesky.dyndns.org/Classes/Geo/javaExample.php](http://maliszesky.dyndns.org/Classes/Geo/javaExample.php)

the page just has a 7 java applets, that create images.
php makes random numbers that go into the applet, that adds variations to the images.

they are posted with <applet> tags,

and I made the applets in processing 1.0

The computer has crashed before i even made that page, Maybe it crashes when i'm doing too much at once, and that page has a lot of applets, over loading the cpu. but it doesn't over load other computers when i view the page online.

---

### Post by rhythmiccycle on 2009-10-01
is there anything else i can do to narrow down to cause of the problem?

---

