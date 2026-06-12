---
title: "ATI DRI not seen by Wine"
date: 2010-12-20
forum: Wine
---

### Post by lucabu on 2010-12-20
Hello all,

I installed Ubuntu 10.10 64 bit on my DELL Studio XPS 1645 notebook, graphic card is a ATI Mobility Radeon HD 4670. I installed also proprietary ati drivers using Ubuntu administration applet, along with Wine 1.2 from package manager. All seems to work properly.

This is fglrxinfo output:

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4670
OpenGL version string: 1.4 (3.3.10237 Compatibility Profile Context FireGL)

fgl_glxgears works too:
$ fgl_glxgears 
Using GLX_SGIX_pbuffer
6863 frames in 5.0 seconds = 1372.600 FPS
9275 frames in 5.0 seconds = 1855.000 FPS
10074 frames in 5.0 seconds = 2014.800 FPS

If I try to run a 3D program on wine (Wow client) i get following error code:

err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly

I tried to reinstall proprietary drivers, and I also tried to switch to Wine 1.0 with no luck. In a previous installation (on the same machine) all worked immediately.

I enclose Xorg.0.log output too.

Thanks all for help.

Luca.

############## Xorg.0.log ##############

[    19.122] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    19.122] X Protocol Version 11, Revision 0
[    19.122] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    19.122] Current Operating System: Linux leonidas 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64
[    19.122] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-23-generic root=UUID=3c80168d-d8be-4815-ba32-ea35953133bf ro quiet splash video=nomodeset uvesafb:mode_option=1280x800-24, mtrr=3,scroll=ywrap
[    19.122] Build Date: 16 September 2010  06:18:41PM
[    19.122] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    19.122] Current version of pixman: 0.18.4
[    19.122]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
   to make sure that you have the latest version.
[    19.122] Markers: (--) probed, (**) from config file, (==) default setting,
   (++) from command line, (!!) notice, (II) informational,
   (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.122] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 20 09:44:24 2010
[    19.122] (==) Using config file: "/etc/X11/xorg.conf"
[    19.122] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.122] (==) No Layout section.  Using the first Screen section.
[    19.122] (**) |-->Screen "Default Screen" (0)
[    19.122] (**) |   |-->Monitor "<default monitor>"
[    19.123] (==) No device specified for screen "Default Screen".
   Using the first device section listed.
[    19.123] (**) |   |-->Device "Default Device"
[    19.123] (==) No monitor specified for screen "Default Screen".
   Using a default monitor configuration.
[    19.123] (==) Automatically adding devices
[    19.123] (==) Automatically enabling devices
[    19.123] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.123]    Entry deleted from font path.
[    19.123] (==) FontPath set to:
   /usr/share/fonts/X11/misc,
   /usr/share/fonts/X11/100dpi/:unscaled,
   /usr/share/fonts/X11/75dpi/:unscaled,
   /usr/share/fonts/X11/Type1,
   /usr/share/fonts/X11/100dpi,
   /usr/share/fonts/X11/75dpi,
   /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
   built-ins
[    19.123] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.123] (II) The server relies on udev to provide the list of input devices.
   If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.123] (II) Loader magic: 0x7d0200
[    19.123] (II) Module ABI versions:
[    19.123]    X.Org ANSI C Emulation: 0.4
[    19.123]    X.Org Video Driver: 8.0
[    19.123]    X.Org XInput driver : 11.0
[    19.123]    X.Org Server Extension : 4.0
[    19.125] (--) PCI:*(0:2:0:0) 1002:9488:1028:02fe rev 0, Mem @ 0xd0000000/268435456, 0xcfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x??/131072
[    19.125] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.125] (II) "extmod" will be loaded by default.
[    19.125] (II) "dbe" will be loaded by default.
[    19.125] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    19.125] (II) "record" will be loaded by default.
[    19.125] (II) "dri" will be loaded by default.
[    19.125] (II) "dri2" will be loaded by default.
[    19.125] (II) LoadModule: "glx"
[    19.126] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    19.126] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    19.126]    compiled for 7.6.0, module version = 1.0.0
[    19.126] (II) Loading extension GLX
[    19.126] (II) LoadModule: "extmod"
[    19.144] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.144] (II) Module extmod: vendor="X.Org Foundation"
[    19.144]    compiled for 1.9.0, module version = 1.0.0
[    19.144]    Module class: X.Org Server Extension
[    19.144]    ABI class: X.Org Server Extension, version 4.0
[    19.144] (II) Loading extension MIT-SCREEN-SAVER
[    19.144] (II) Loading extension XFree86-VidModeExtension
[    19.144] (II) Loading extension XFree86-DGA
[    19.144] (II) Loading extension DPMS
[    19.144] (II) Loading extension XVideo
[    19.144] (II) Loading extension XVideo-MotionCompensation
[    19.144] (II) Loading extension X-Resource
[    19.144] (II) LoadModule: "dbe"
[    19.144] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.144] (II) Module dbe: vendor="X.Org Foundation"
[    19.144]    compiled for 1.9.0, module version = 1.0.0
[    19.144]    Module class: X.Org Server Extension
[    19.144]    ABI class: X.Org Server Extension, version 4.0
[    19.144] (II) Loading extension DOUBLE-BUFFER
[    19.144] (II) LoadModule: "record"
[    19.145] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.145] (II) Module record: vendor="X.Org Foundation"
[    19.145]    compiled for 1.9.0, module version = 1.13.0
[    19.145]    Module class: X.Org Server Extension
[    19.145]    ABI class: X.Org Server Extension, version 4.0
[    19.145] (II) Loading extension RECORD
[    19.145] (II) LoadModule: "dri"
[    19.145] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.145] (II) Module dri: vendor="X.Org Foundation"
[    19.145]    compiled for 1.9.0, module version = 1.0.0
[    19.145]    ABI class: X.Org Server Extension, version 4.0
[    19.145] (II) Loading extension XFree86-DRI
[    19.145] (II) LoadModule: "dri2"
[    19.145] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.145] (II) Module dri2: vendor="X.Org Foundation"
[    19.145]    compiled for 1.9.0, module version = 1.2.0
[    19.145]    ABI class: X.Org Server Extension, version 4.0
[    19.145] (II) Loading extension DRI2
[    19.145] (II) LoadModule: "fglrx"
[    19.146] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    19.157] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    19.157]    compiled for 1.4.99.906, module version = 8.78.30
[    19.157]    Module class: X.Org Video Driver
[    19.157] (II) Loading sub module "fglrxdrm"
[    19.157] (II) LoadModule: "fglrxdrm"
[    19.157] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    19.157] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    19.157]    compiled for 1.8.99.905, module version = 8.78.30
[    19.157] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    19.157] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    19.157] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:31:08
[    19.157] (++) using VT number 7

[    19.157] (WW) Falling back to old probe method for fglrx
[    19.160] (II) Loading PCS database from /etc/ati/amdpcsdb
[    19.160] (--) Assigning device section with no busID to primary device
[    19.160] (--) Chipset Supported AMD Graphics Processor (0x9488) found
[    19.160] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    19.160] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    19.160] (II) AMD Video driver is signed
[    19.161] (II) fglrx(0): pEnt->device->identifier=0x25a23e0
[    19.161] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    19.161] (II) Loading sub module "vgahw"
[    19.161] (II) LoadModule: "vgahw"
[    19.161] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    19.161] (II) Module vgahw: vendor="X.Org Foundation"
[    19.161]    compiled for 1.9.0, module version = 0.1.0
[    19.161]    ABI class: X.Org Video Driver, version 8.0
[    19.161] (II) fglrx(0): Creating default Display subsection in Screen section
   "Default Screen" for depth/fbbpp 24/32
[    19.161] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    19.161] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    19.161] (==) fglrx(0): Default visual is TrueColor
[    19.161] (==) fglrx(0): RGB weight 888
[    19.161] (II) fglrx(0): Using 8 bits per RGB 
[    19.161] (==) fglrx(0): Buffer Tiling is ON
[    19.161] (II) Loading sub module "fglrxdrm"
[    19.161] (II) LoadModule: "fglrxdrm"
[    19.161] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    19.163] ukiDynamicMajor: found major device number 249
[    19.163] ukiDynamicMajor: found major device number 249
[    19.163] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    19.163] ukiOpenDevice: node name is /dev/ati/card0
[    19.163] ukiOpenDevice: open result is 11, (OK)
[    19.163] ukiOpenByBusid: ukiOpenMinor returns 11
[    19.163] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    19.163] (==) fglrx(0): NoAccel = NO
[    19.163] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    19.163] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4670" (Chipset = 0x9488)
[    19.163] (--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x02fe)
[    19.163] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    19.163] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    19.163] (--) fglrx(0): MMIO registers at 0xcfef0000
[    19.163] (--) fglrx(0): I/O port at 0x00002000
[    19.163] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    19.262] (II) fglrx(0): ATIF platform detected
[    19.360] (II) fglrx(0): AC Adapter is used
[    19.361] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    19.362] (II) Loading sub module "vbe"
[    19.362] (II) LoadModule: "vbe"
[    19.362] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    19.362] (II) Module vbe: vendor="X.Org Foundation"
[    19.362]    compiled for 1.9.0, module version = 1.1.0
[    19.362]    ABI class: X.Org Video Driver, version 8.0
[    19.362] (II) fglrx(0): VESA BIOS detected
[    19.362] (II) fglrx(0): VESA VBE Version 3.0
[    19.362] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    19.362] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    19.362] (II) fglrx(0): VESA VBE OEM Software Rev: 11.22
[    19.362] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    19.362] (II) fglrx(0): VESA VBE OEM Product: M96
[    19.362] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    19.390] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    19.390] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    19.390] (II) fglrx(0): PCIE card detected
[    19.390] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    19.390] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    19.392] (II) fglrx(0): Using adapter: 2:0.0.
[    19.423] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    19.497] (II) fglrx(0): Interrupt handler installed at IRQ 55.
[    19.497] (II) fglrx(0): RandR 1.2 support is enabled!
[    19.497] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    19.497] (==) fglrx(0): Center Mode is disabled 
[    19.497] (II) Loading sub module "fb"
[    19.497] (II) LoadModule: "fb"
[    19.497] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.497] (II) Module fb: vendor="X.Org Foundation"
[    19.497]    compiled for 1.9.0, module version = 1.0.0
[    19.497]    ABI class: X.Org ANSI C Emulation, version 0.4
[    19.497] (==) fglrx(0): Active stereo disabled
[    19.497] (II) Loading sub module "ddc"
[    19.497] (II) LoadModule: "ddc"
[    19.497] (II) Module "ddc" already built-in
[    20.576] (II) fglrx(0): Finished Initialize PPLIB!
[    20.620] (II) fglrx(0): Output LVDS has no monitor section
[    20.620] (II) fglrx(0): Output DFP1 has no monitor section
[    20.620] (II) fglrx(0): Output DFP2 has no monitor section
[    20.620] (II) fglrx(0): Output CRT1 has no monitor section
[    20.620] (II) Loading sub module "ddc"
[    20.620] (II) LoadModule: "ddc"
[    20.620] (II) Module "ddc" already built-in
[    20.620] (II) fglrx(0): Connected Display0: LVDS
[    20.620] (II) fglrx(0): Display0 EDID data ---------------------------
[    20.620] (II) fglrx(0): Manufacturer: SEC  Model: 5448  Serial#: 0
[    20.620] (II) fglrx(0): Year: 2008  Week: 0
[    20.620] (II) fglrx(0): EDID Version: 1.3
[    20.620] (II) fglrx(0): Digital Display Input
[    20.620] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 20
[    20.620] (II) fglrx(0): Gamma: 2.20
[    20.620] (II) fglrx(0): No DPMS capabilities specified
[    20.620] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.620] (II) fglrx(0): First detailed timing is preferred mode
[    20.620] (II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    20.620] (II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    20.620] (II) fglrx(0): Manufacturer's mask: 0
[    20.620] (II) fglrx(0): Supported detailed timing:
[    20.620] (II) fglrx(0): clock: 153.5 MHz   Image Size:  353 x 198 mm
[    20.620] (II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2280 h_border: 0
[    20.620] (II) fglrx(0): v_active: 1080  v_sync: 1082  v_sync_end 1087 v_blanking: 1122 v_border: 0
[    20.620] (II) fglrx(0): Supported detailed timing:
[    20.620] (II) fglrx(0): clock: 153.5 MHz   Image Size:  353 x 198 mm
[    20.620] (II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2280 h_border: 0
[    20.620] (II) fglrx(0): v_active: 1080  v_sync: 1082  v_sync_end 1087 v_blanking: 1122 v_border: 0
[    20.620] (II) fglrx(0):  M077D€160HT
[    20.620] (II) fglrx(0): Unknown vendor-specific block 0
[    20.620] (II) fglrx(0): EDID (in hex):
[    20.620] (II) fglrx(0):    00ffffffffffff004ca3485400000000
[    20.620] (II) fglrx(0):    00120103902314780a87f594574f8c27
[    20.620] (II) fglrx(0):    27505400000001010101010101010101
[    20.620] (II) fglrx(0):    010101010101f53b806871382a403020
[    20.620] (II) fglrx(0):    250061c61000001af53b806871382a40
[    20.620] (II) fglrx(0):    3020250061c61000001a000000fe004d
[    20.620] (II) fglrx(0):    303737448031363048540a2000000000
[    20.620] (II) fglrx(0):    00000000000000000006010a2020009b
[    20.620] (II) fglrx(0): End of Display0 EDID data --------------------
[    20.996] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    20.996] (II) fglrx(0): Printing DDC gathered Modelines:
[    20.996] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    20.996] (II) fglrx(0): Output LVDS connected
[    20.996] (II) fglrx(0): Output DFP1 disconnected
[    20.996] (II) fglrx(0): Output DFP2 disconnected
[    20.996] (II) fglrx(0): Output CRT1 disconnected
[    20.996] (II) fglrx(0): Using exact sizes for initial modes
[    20.996] (II) fglrx(0): Output LVDS using initial mode 1920x1080
[    20.996] (II) fglrx(0): Display dimensions: (350, 200) mm
[    20.996] (II) fglrx(0): DPI set to (139, 137)
[    20.996] (II) fglrx(0): Adapter ATI Mobility Radeon HD 4670 has 2 configurable heads and 1 displays connected.
[    20.996] (==) fglrx(0):  PseudoColor visuals disabled
[    20.996] (II) Loading sub module "ramdac"
[    20.997] (II) LoadModule: "ramdac"
[    20.997] (II) Module "ramdac" already built-in
[    20.997] (==) fglrx(0): NoDRI = NO
[    20.997] (==) fglrx(0): Capabilities: 0x00000000
[    20.997] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    20.997] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    20.997] (==) fglrx(0): UseFastTLS=0
[    20.997] (==) fglrx(0): BlockSignalsOnLock=1
[    20.997] (--) Depth 24 pixmap format is 32 bpp
[    20.999] (II) Loading extension ATIFGLRXDRI
[    20.999] (II) fglrx(0): doing swlDriScreenInit
[    21.000] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    21.000] ukiDynamicMajor: found major device number 249
[    21.000] ukiDynamicMajor: found major device number 249
[    21.000] ukiDynamicMajor: found major device number 249
[    21.000] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    21.000] ukiOpenDevice: node name is /dev/ati/card0
[    21.000] ukiOpenDevice: open result is 16, (OK)
[    21.000] ukiOpenByBusid: ukiOpenMinor returns 16
[    21.000] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    21.000] (II) fglrx(0): [uki] DRM interface version 1.0
[    21.000] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:2:0:0"
[    21.000] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    21.000] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7fcc49cdb000
[    21.000] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    21.000] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    21.000] (II) fglrx(0): swlDriScreenInit done
[    21.000] (II) fglrx(0): Kernel Module Version Information:
[    21.000] (II) fglrx(0):     Name: fglrx
[    21.000] (II) fglrx(0):     Version: 8.78.30
[    21.000] (II) fglrx(0):     Date: Sep 20 2010
[    21.000] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    21.000] (II) fglrx(0): Kernel Module version matches driver.
[    21.000] (II) fglrx(0): Kernel Module Build Time Information:
[    21.000] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.35-23-generic
[    21.000] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    21.000] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    21.000] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    21.000] (II) fglrx(0): [uki] register handle = 0x00004000
[    21.000] (II) fglrx(0): FIREGL Board Found
[    21.019] (II) fglrx(0): DRI initialization successfull
[    21.019] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x0102c000
[    21.019] (II) fglrx(0): FBMM initialized for area (0,0)-(1920,2208)
[    21.019] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
[    21.019] (II) fglrx(0): Largest offscreen area available: 1920 x 288
[    21.019] (==) fglrx(0): Backing store disabled
[    21.019] (II) Loading extension FGLRXEXTENSION
[    21.020] (==) fglrx(0): DPMS enabled
[    21.020] (II) fglrx(0): Initialized in-driver Xinerama extension
[    21.020] (**) fglrx(0): Textured Video is enabled.
[    21.020] (II) LoadModule: "glesx"
[    21.020] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    21.020] (II) Module glesx: vendor="X.Org Foundation"
[    21.020]    compiled for 1.8.99.905, module version = 1.0.0
[    21.020] (II) Loading extension GLESX
[    21.020] (II) fglrx(0): GLESX enableFlags = 528
[    21.020] (II) fglrx(0): GLESX is enabled
[    21.020] (II) fglrx(0): Acceleration enabled
[    21.020] (II) LoadModule: "amdxmm"
[    21.020] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    21.020] (II) Module amdxmm: vendor="X.Org Foundation"
[    21.021]    compiled for 1.8.99.905, module version = 1.0.0
[    21.021] (II) Loading extension AMDXVOPL
[    21.022] (II) fglrx(0): UVD2 feature is available
[    21.037] (II) fglrx(0): Enable composite support successfully
[    21.037] (II) fglrx(0): X context handle = 0x1
[    21.037] (II) fglrx(0): [DRI] installation complete
[    21.037] (==) fglrx(0): Silken mouse enabled
[    21.038] (==) fglrx(0): Using HW cursor of display infrastructure!
[    21.038] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    21.038] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    21.038] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    22.126] (--) RandR disabled
[    22.126] (II) Initializing built-in extension Generic Event Extension
[    22.126] (II) Initializing built-in extension SHAPE
[    22.126] (II) Initializing built-in extension MIT-SHM
[    22.126] (II) Initializing built-in extension XInputExtension
[    22.126] (II) Initializing built-in extension XTEST
[    22.126] (II) Initializing built-in extension BIG-REQUESTS
[    22.126] (II) Initializing built-in extension SYNC
[    22.126] (II) Initializing built-in extension XKEYBOARD
[    22.126] (II) Initializing built-in extension XC-MISC
[    22.126] (II) Initializing built-in extension SECURITY
[    22.126] (II) Initializing built-in extension XINERAMA
[    22.126] (II) Initializing built-in extension XFIXES
[    22.126] (II) Initializing built-in extension RENDER
[    22.126] (II) Initializing built-in extension RANDR
[    22.126] (II) Initializing built-in extension COMPOSITE
[    22.126] (II) Initializing built-in extension DAMAGE
[    22.126] (II) Initializing built-in extension GESTURE
[    22.136] ukiDynamicMajor: found major device number 249
[    22.136] ukiDynamicMajor: found major device number 249
[    22.136] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    22.136] ukiOpenDevice: node name is /dev/ati/card0
[    22.136] ukiOpenDevice: open result is 17, (OK)
[    22.136] ukiOpenByBusid: ukiOpenMinor returns 17
[    22.136] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    22.179] (II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
[    22.179] (II) GLX: Initialized DRI GL provider for screen 0
[    22.180] (II) fglrx(0): Enable the clock gating!
[    22.180] (II) fglrx(0): Setting screen physical size to 508 x 285
[    22.191] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.196] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    22.196] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.196] (II) LoadModule: "evdev"
[    22.196] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.197] (II) Module evdev: vendor="X.Org Foundation"
[    22.197]    compiled for 1.9.0, module version = 2.3.2
[    22.197]    Module class: X.Org XInput Driver
[    22.197]    ABI class: X.Org XInput driver, version 11.0
[    22.197] (**) Power Button: always reports core events
[    22.197] (**) Power Button: Device: "/dev/input/event3"
[    22.242] (II) Power Button: Found keys
[    22.242] (II) Power Button: Configuring as keyboard
[    22.242] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.242] (**) Option "xkb_rules" "evdev"
[    22.242] (**) Option "xkb_model" "evdev"
[    22.242] (**) Option "xkb_layout" "it"
[    22.243] (II) XKB: reuse xkmfile /var/lib/xkb/server-35DF0DEC488035CD7337E5EF69F018BFAFADCAC5.xkm
[    22.243] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    22.243] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.243] (**) Video Bus: always reports core events
[    22.244] (**) Video Bus: Device: "/dev/input/event5"
[    22.284] (II) Video Bus: Found keys
[    22.284] (II) Video Bus: Configuring as keyboard
[    22.284] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    22.284] (**) Option "xkb_rules" "evdev"
[    22.284] (**) Option "xkb_model" "evdev"
[    22.284] (**) Option "xkb_layout" "it"
[    22.285] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.285] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.285] (**) Power Button: always reports core events
[    22.285] (**) Power Button: Device: "/dev/input/event0"
[    22.314] (II) Power Button: Found keys
[    22.314] (II) Power Button: Configuring as keyboard
[    22.314] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.314] (**) Option "xkb_rules" "evdev"
[    22.314] (**) Option "xkb_model" "evdev"
[    22.314] (**) Option "xkb_layout" "it"
[    22.314] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    22.314] (II) No input driver/identifier specified (ignoring)
[    22.315] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    22.315] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    22.315] (**) Sleep Button: always reports core events
[    22.315] (**) Sleep Button: Device: "/dev/input/event1"
[    22.374] (II) Sleep Button: Found keys
[    22.374] (II) Sleep Button: Configuring as keyboard
[    22.374] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    22.374] (**) Option "xkb_rules" "evdev"
[    22.374] (**) Option "xkb_model" "evdev"
[    22.374] (**) Option "xkb_layout" "it"
[    22.375] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event8)
[    22.375] (**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
[    22.375] (**) Laptop_Integrated_Webcam_2M: always reports core events
[    22.375] (**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event8"
[    22.454] (II) Laptop_Integrated_Webcam_2M: Found keys
[    22.454] (II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
[    22.454] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
[    22.454] (**) Option "xkb_rules" "evdev"
[    22.454] (**) Option "xkb_model" "evdev"
[    22.454] (**) Option "xkb_layout" "it"
[    22.455] (II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event9)
[    22.455] (II) No input driver/identifier specified (ignoring)
[    22.455] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event10)
[    22.455] (II) No input driver/identifier specified (ignoring)
[    22.455] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event11)
[    22.455] (II) No input driver/identifier specified (ignoring)
[    22.456] (II) config/udev: Adding input device HID 413c:8157 (/dev/input/event6)
[    22.456] (**) HID 413c:8157: Applying InputClass "evdev keyboard catchall"
[    22.456] (**) HID 413c:8157: always reports core events
[    22.456] (**) HID 413c:8157: Device: "/dev/input/event6"
[    22.534] (II) HID 413c:8157: Found keys
[    22.534] (II) HID 413c:8157: Configuring as keyboard
[    22.534] (II) XINPUT: Adding extended input device "HID 413c:8157" (type: KEYBOARD)
[    22.534] (**) Option "xkb_rules" "evdev"
[    22.534] (**) Option "xkb_model" "evdev"
[    22.534] (**) Option "xkb_layout" "it"
[    22.536] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    22.536] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.536] (**) AT Translated Set 2 keyboard: always reports core events
[    22.536] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    22.614] (II) AT Translated Set 2 keyboard: Found keys
[    22.614] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    22.614] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    22.614] (**) Option "xkb_rules" "evdev"
[    22.614] (**) Option "xkb_model" "evdev"
[    22.614] (**) Option "xkb_layout" "it"
[    22.614] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
[    22.614] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    22.614] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    22.614] (II) LoadModule: "synaptics"
[    22.615] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.615] (II) Module synaptics: vendor="X.Org Foundation"
[    22.615]    compiled for 1.9.0, module version = 1.2.2
[    22.615]    Module class: X.Org XInput Driver
[    22.615]    ABI class: X.Org XInput driver, version 11.0
[    22.615] (II) Synaptics touchpad driver version 1.2.2
[    22.615] (**) Option "Device" "/dev/input/event12"
[    23.014] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5576
[    23.014] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4684
[    23.014] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.014] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    23.014] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    23.294] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.294] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.454] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    23.454] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    23.454] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    23.454] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    23.454] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    23.694] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.694] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    23.694] (II) No input driver/identifier specified (ignoring)
[    23.696] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[    23.696] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    23.696] (**) Dell WMI hotkeys: always reports core events
[    23.696] (**) Dell WMI hotkeys: Device: "/dev/input/event7"
[    23.774] (II) Dell WMI hotkeys: Found keys
[    23.774] (II) Dell WMI hotkeys: Configuring as keyboard
[    23.774] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    23.774] (**) Option "xkb_rules" "evdev"
[    23.774] (**) Option "xkb_model" "evdev"
[    23.774] (**) Option "xkb_layout" "it"
[    24.272] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    24.480] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    24.480] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.480] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    24.495] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    24.495] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.495] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    24.530] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    24.530] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.530] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    24.544] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    24.544] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.544] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    35.441] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    35.441] (II) fglrx(0): Printing DDC gathered Modelines:
[    35.441] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    35.457] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    35.457] (II) fglrx(0): Printing DDC gathered Modelines:
[    35.457] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    35.471] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    35.471] (II) fglrx(0): Printing DDC gathered Modelines:
[    35.471] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    35.484] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    35.484] (II) fglrx(0): Printing DDC gathered Modelines:
[    35.484] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    35.875] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    35.875] (II) fglrx(0): Printing DDC gathered Modelines:
[    35.875] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[    40.817] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[    40.817] (II) fglrx(0): Printing DDC gathered Modelines:
[    40.817] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1387.039] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1387.039] (II) fglrx(0): Printing DDC gathered Modelines:
[  1387.039] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1481.935] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1481.935] (II) fglrx(0): Printing DDC gathered Modelines:
[  1481.935] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1481.956] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1481.956] (II) fglrx(0): Printing DDC gathered Modelines:
[  1481.956] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1482.439] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1482.439] (II) fglrx(0): Printing DDC gathered Modelines:
[  1482.439] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1482.805] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1482.805] (II) fglrx(0): Printing DDC gathered Modelines:
[  1482.806] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1482.868] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1482.868] (II) fglrx(0): Printing DDC gathered Modelines:
[  1482.868] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1653.300] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1653.300] (II) fglrx(0): Printing DDC gathered Modelines:
[  1653.300] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1653.340] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1653.340] (II) fglrx(0): Printing DDC gathered Modelines:
[  1653.341] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1654.066] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1654.066] (II) fglrx(0): Printing DDC gathered Modelines:
[  1654.066] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1654.147] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1654.147] (II) fglrx(0): Printing DDC gathered Modelines:
[  1654.147] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)
[  1654.168] (II) fglrx(0): EDID vendor "SEC", prod id 21576
[  1654.168] (II) fglrx(0): Printing DDC gathered Modelines:
[  1654.168] (II) fglrx(0): Modeline "1920x1080"x0.0  153.49  1920 1968 2000 2280  1080 1082 1087 1122 +hsync -vsync (67.3 kHz)

---

### Post by Skazzi on 2011-01-24
I have same problem.
any variants of > export LIBGL_DRIVERS_PATH= don't work
**[Wine 1.3.12]("http://www.winehq.org/announce/1.3.12")** and fglrx 8.801
[]("http://www.winehq.org/announce/1.3.12")

---

### Post by lucabu on 2011-01-25
I posted workaround here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/683470](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/683470)

---

