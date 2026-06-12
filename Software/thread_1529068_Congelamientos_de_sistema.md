---
title: "Congelamientos de sistema"
date: 2010-07-11
forum: Software
---

### Post by leonardomdq on 2010-07-11
Hola gente, estoy teniendo como lo indica el titulo de thread congelamientos de sistema, varias veces al dia y la verdad que es muy molesto.
Dejo las salidas  de algunos logs  para ver que puede ser lo que produce.
Si alguno me puede ayudar le estare agradecido.

Muchas gracias de antemano.


/var/log/messages
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux ubuntu-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=3d66cdf6-9da5-4918-b098-d88b6d937353 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 11 18:54:57 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0640:1682:400a nVidia Corporation G96 [GeForce 9500 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.35  Wed Jun 16 19:21:24 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.35  Wed Jun 16 18:59:34 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1600x900 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Jul 11 18:54:57 NVIDIA(0): Enabling RENDER acceleration
(II) Jul 11 18:54:57 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jul 11 18:54:57 NVIDIA(0):     enabled.
(II) Jul 11 18:54:59 NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
(--) Jul 11 18:54:59 NVIDIA(0): Memory: 1048576 kBytes
(--) Jul 11 18:54:59 NVIDIA(0): VideoBIOS: 62.94.4b.00.70
(II) Jul 11 18:54:59 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jul 11 18:54:59 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jul 11 18:54:59 NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0:
(--) Jul 11 18:54:59 NVIDIA(0):     LG Electronics W2043 (CRT-0)
(--) Jul 11 18:54:59 NVIDIA(0): LG Electronics W2043 (CRT-0): 400.0 MHz maximum pixel clock
(II) Jul 11 18:54:59 NVIDIA(0): Assigned Display Device: CRT-0
(II) Jul 11 18:54:59 NVIDIA(0): Validated modes:
(II) Jul 11 18:54:59 NVIDIA(0):     "1600x900+0+0"
(II) Jul 11 18:54:59 NVIDIA(0): Virtual screen size determined to be 1600 x 900
(--) Jul 11 18:54:59 NVIDIA(0): DPI set to (90, 91); computed from "UseEdidDpi" X config
(--) Jul 11 18:54:59 NVIDIA(0):     option
(==) Jul 11 18:54:59 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jul 11 18:54:59 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Jul 11 18:54:59 NVIDIA(0): Initialized GPU GART.
(II) Jul 11 18:54:59 NVIDIA(0): Setting mode "1600x900+0+0"
(II) Loading extension NV-GLX
(II) Jul 11 18:54:59 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jul 11 18:54:59 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
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
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) XKB: reuse xkmfile /var/lib/xkb/server-188C20793BE00CBD61865C180F610EC4A3A6D8CD.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event4)
(**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Genius Optical Mouse: always reports core events
(**) Genius Optical Mouse: Device: "/dev/input/event4"
(II) Genius Optical Mouse: Found 3 mouse buttons
(II) Genius Optical Mouse: Found scroll wheel(s)
(II) Genius Optical Mouse: Found relative axes
(II) Genius Optical Mouse: Found x and y relative axes
(II) Genius Optical Mouse: Configuring as mouse
(**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
(II) Genius Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```/var/log/messages
```

Jul 11 00:36:59 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="853" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 11 09:26:12 ubuntu-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 11 09:26:12 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="854" x-info="http://www.rsyslog.com"] (re)start
Jul 11 09:26:12 ubuntu-desktop rsyslogd: rsyslogd's groupid changed to 103
Jul 11 09:26:13 ubuntu-desktop rsyslogd: rsyslogd's userid changed to 101
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] KERNEL supported cpus:
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   Intel GenuineIntel
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   NSC Geode by NSC
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] DMI 2.4 present.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] modified physical RAM map:
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] RAMDISK: 37858000 - 37fef3be
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Allocated new RAMDISK: 008e0000 - 010773be
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fef3bd to 008e0000 - 010773bd
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: RSDP 000f70e0 00014 (v00 GBT   )
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: RSDT 7fee3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: FACP 7fee3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: DSDT 7fee30c0 042A8 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: FACS 7fee0000 00040
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: SSDT 7fee7440 007BA (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: HPET 7fee7c00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: MCFG 7fee7c40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: APIC 7fee7380 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] 1158MB HIGHMEM available.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] 887MB LOWMEM available.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #5 [00008dc000 - 00008df0fe]              BRK ==> [00008dc000 - 00008df0fe]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #7 [00008e0000 - 00010773be]      NEW RAMDISK ==> [00008e0000 - 00010773be]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] found SMP MP-table at [c00f56f0] f56f0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007fee0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Using APIC driver default
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:60100000)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519805
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=3d66cdf6-9da5-4918-b098-d88b6d937353 ro quiet splash
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Initializing CPU#0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] allocated 10480000 bytes of page_cgroup
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Memory: 2050904k/2096000k available (4679k kernel code, 43552k reserved, 2116k data, 660k init, 1186696k highmem)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] virtual kernel memory layout:
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] console [tty0] enabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.000000] Detected 2719.249 MHz processor.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5438.49 BogoMIPS (lpj=10876996)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004018] Security Framework initialized
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004034] AppArmor: AppArmor initialized
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004039] Mount-cache hash table entries: 512
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004132] Initializing cgroup subsys ns
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004135] Initializing cgroup subsys cpuacct
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004138] Initializing cgroup subsys memory
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004143] Initializing cgroup subsys devices
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004145] Initializing cgroup subsys freezer
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004147] Initializing cgroup subsys net_cls
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004160] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004163] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004165] CPU: Physical Processor ID: 0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004166] CPU: Processor Core ID: 0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004168] mce: CPU supports 6 MCE banks
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004177] using C1E aware idle routine
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004181] Performance Events: AMD PMU driver.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004186] ... version:                0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004188] ... bit width:              48
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004189] ... generic registers:      4
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004190] ... value mask:             0000ffffffffffff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004192] ... max period:             00007fffffffffff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004194] ... fixed-purpose events:   0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004195] ... event mask:             000000000000000f
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.004198] Checking 'hlt' instruction... OK.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.021769] ACPI: Core revision 20090903
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.028026] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.028034] ftrace: allocating 21780 entries in 43 pages
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.032059] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.032566] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.072703] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.008000] Initializing CPU#1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.008000] CPU: Physical Processor ID: 0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.008000] CPU: Processor Core ID: 1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.160104] CPU1: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.160114] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164011] Brought up 2 CPUs
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164013] Total of 2 processors activated (10876.74 BogoMIPS).
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] devtmpfs: initialized
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] regulator: core version 0.5
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] Time:  9:25:35  Date: 07/11/10
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] NET: Registered protocol family 16
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] EISA bus registered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] Trying to unpack rootfs image as initramfs...
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] ACPI: bus type pci registered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] PCI: MCFG area at e0000000 reserved in E820
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] PCI: Using MMCONFIG for extended config space
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.164477] PCI: Using configuration type 1 for base access
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.168073] bio: create slab <bio-0> at 0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.174425] ACPI: Interpreter enabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.174437] ACPI: (supports S0 S3 S4 S5)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.174458] ACPI: Using IOAPIC for interrupt routing
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.177794] ACPI: No dock devices found.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.177891] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.177957] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.177960] pci 0000:00:02.0: PME# disabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.177992] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.177994] pci 0000:00:06.0: PME# disabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.178097] pci 0000:00:11.0: set SATA to AHCI mode
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.178315] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.178319] pci 0000:00:12.2: PME# disabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.178525] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.178529] pci 0000:00:13.2: PME# disabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.178771] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.178775] pci 0000:00:14.2: PME# disabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.179200] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.179204] pci 0000:02:00.0: PME# disabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.179424] pci 0000:00:14.4: transparent bridge
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196065] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196136] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196204] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196272] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196339] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196408] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196475] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196543] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196635] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196638] vgaarb: loaded
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196726] SCSI subsystem initialized
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196853] usbcore: registered new interface driver usbfs
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196862] usbcore: registered new interface driver hub
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196880] usbcore: registered new device driver usb
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196968] ACPI: WMI: Mapper loaded
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.196969] PCI: Using ACPI for IRQ routing
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.197099] NetLabel: Initializing
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.197101] NetLabel:  domain hash size = 128
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.197102] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.197113] NetLabel:  unlabeled traffic allowed by default
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.197140] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.197144] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199173] Switching to clocksource tsc
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199268] AppArmor: AppArmor Filesystem Enabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199268] pnp: PnP ACPI init
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199268] ACPI: bus type pnp registered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199379] pnp: PnP ACPI: found 13 devices
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199381] ACPI: ACPI bus type pnp unregistered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199384] PnPBIOS: Disabled by ACPI PNP
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199393] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199395] system 00:01: ioport range 0x220-0x225 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199397] system 00:01: ioport range 0x290-0x294 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199401] system 00:02: ioport range 0x4100-0x411f has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199403] system 00:02: ioport range 0x228-0x22f has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199405] system 00:02: ioport range 0x238-0x23f has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199407] system 00:02: ioport range 0x40b-0x40b has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199409] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199411] system 00:02: ioport range 0xc00-0xc01 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199413] system 00:02: ioport range 0xc14-0xc14 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199415] system 00:02: ioport range 0xc50-0xc52 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199417] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199419] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199421] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199423] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199425] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199427] system 00:02: ioport range 0x4000-0x40fe has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199429] system 00:02: ioport range 0x4210-0x4217 has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199431] system 00:02: ioport range 0xb00-0xb0f has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199433] system 00:02: ioport range 0xb10-0xb1f has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199435] system 00:02: ioport range 0xb20-0xb3f has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199441] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199445] system 00:0c: iomem range 0xce000-0xcffff has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199447] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199450] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199452] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199454] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199456] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199459] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199461] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199463] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199465] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.199468] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234114] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234117] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234120] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234123] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234127] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234129] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234132] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234134] pci 0000:00:06.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234138] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234140] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234145] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234149] pci 0000:00:14.4:   PREFETCH window: 0xfdd00000-0xfddfffff
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234229] NET: Registered protocol family 2
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234305] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.234560] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.235104] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.235369] TCP: Hash tables configured (established 131072 bind 65536)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.235371] TCP reno registered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.235438] NET: Registered protocol family 1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.372969] cpufreq-nforce2: No nForce2 chipset.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.372991] Scanning for low memory corruption every 60 seconds
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.373077] audit: initializing netlink socket (disabled)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.373088] type=2000 audit(1278840335.372:1): initialized
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.379737] highmem bounce pool size: 64 pages
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.379741] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.380795] VFS: Disk quotas dquot_6.5.2
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.380840] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381255] fuse init (API version 7.13)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381313] msgmni has been set to 1690
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381482] alg: No test for stdrng (krng)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381525] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381527] io scheduler noop registered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381529] io scheduler anticipatory registered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381531] io scheduler deadline registered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381560] io scheduler cfq registered (default)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381765] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381783] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381855] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381859] ACPI: Power Button [PWRB]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381899] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.381901] ACPI: Power Button [PWRF]
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.382128] processor LNXCPU:00: registered as cooling_device0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.382156] processor LNXCPU:01: registered as cooling_device1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.382420] Freeing initrd memory: 7772k freed
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.384802] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.384918] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.385202] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.385831] isapnp: Scanning for PnP cards...
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.385954] brd: module loaded
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386252] loop: module loaded
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386310] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386429] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386668] Fixed MDIO Bus: probed
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386691] PPP generic driver version 2.4.2
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386716] tun: Universal TUN/TAP device driver, 1.6
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386717] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386770] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386793] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386804] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386825] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386846] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386860] ehci_hcd 0000:00:12.2: debug port 1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.386891] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396755] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396818] usb usb1: configuration #1 chosen from 1 choice
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396839] hub 1-0:1.0: USB hub found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396845] hub 1-0:1.0: 6 ports detected
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396900] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396908] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396929] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396946] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396958] ehci_hcd 0000:00:13.2: debug port 1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.396984] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408751] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408796] usb usb2: configuration #1 chosen from 1 choice
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408813] hub 2-0:1.0: USB hub found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408817] hub 2-0:1.0: 6 ports detected
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408862] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408871] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408879] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408901] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.408930] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.468775] usb usb3: configuration #1 chosen from 1 choice
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.468792] hub 3-0:1.0: USB hub found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.468799] hub 3-0:1.0: 3 ports detected
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.468834] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.468841] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.468860] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.468875] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.528770] usb usb4: configuration #1 chosen from 1 choice
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.528786] hub 4-0:1.0: USB hub found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.528793] hub 4-0:1.0: 3 ports detected
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.528836] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.528844] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.528862] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.528887] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.588764] usb usb5: configuration #1 chosen from 1 choice
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.588782] hub 5-0:1.0: USB hub found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.588789] hub 5-0:1.0: 3 ports detected
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.588823] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.588830] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.588849] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.588863] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.648761] usb usb6: configuration #1 chosen from 1 choice
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.648779] hub 6-0:1.0: USB hub found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.648786] hub 6-0:1.0: 3 ports detected
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.648820] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.648827] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.648850] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.648864] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.708764] usb usb7: configuration #1 chosen from 1 choice
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.708780] hub 7-0:1.0: USB hub found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.708787] hub 7-0:1.0: 2 ports detected
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.708820] uhci_hcd: USB Universal Host Controller Interface driver
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.708866] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.708868] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709002] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709065] mice: PS/2 mouse device common for all mice
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709144] rtc_cmos 00:05: RTC can wake from S4
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709173] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709206] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709277] device-mapper: uevent: version 1.0.3
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709361] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709409] device-mapper: multipath: version 1.1.0 loaded
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709412] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709488] EISA: Probing bus 0 at eisa.0
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709504] Cannot allocate resource for EISA slot 4
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709520] EISA: Detected 0 cards.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709572] cpuidle: using governor ladder
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709573] cpuidle: using governor menu
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709877] TCP cubic registered
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.709982] NET: Registered protocol family 10
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.710327] lo: Disabled Privacy Extensions
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.710564] NET: Registered protocol family 17
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.710586] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.710612] powernow-k8:    0 : pstate 0 (2700 MHz)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.710614] powernow-k8:    1 : pstate 1 (1350 MHz)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.739632] isapnp: No Plug & Play device found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.739670] Using IPI No-Shortcut mode
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.739759] registered taskstats version 1
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.740036]   Magic number: 2:160:424
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.740097] rtc_cmos 00:05: setting system clock to 2010-07-11 09:25:35 UTC (1278840335)
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.740100] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.740102] EDD information not available.
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.740144] Freeing unused kernel memory: 660k freed
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.740455] Write protecting the kernel text: 4680k
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.740483] Write protecting the kernel read-only data: 1840k
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.742294] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.752349] udev: starting version 151
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.807249] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.807267] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.807820] eth0: RTL8168c/8111c at 0xf808e000, 00:24:1d:2a:40:65, XID 1c4000c0 IRQ 27
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.822825] scsi0 : pata_atiixp
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.832102] scsi1 : pata_atiixp
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.832970] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.832973] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.833035] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.833151] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.833155] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.836204] scsi2 : ahci
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.836305] scsi3 : ahci
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.836368] scsi4 : ahci
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.836428] scsi5 : ahci
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.836520] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.836523] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.836527] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.836530] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Jul 11 09:26:13 ubuntu-desktop kernel: [    0.944730] usb 3-2: new low speed USB device using ohci_hcd and address 2
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.083295] usb 3-2: configuration #1 chosen from 1 choice
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.160047] ata6: SATA link down (SStatus 0 SControl 300)
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.160074] ata4: SATA link down (SStatus 0 SControl 300)
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.276013] ata3: applying SB600 PMP SRST workaround and retrying
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.324011] ata5: applying SB600 PMP SRST workaround and retrying
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.440019] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.441685] ata3.00: HPA unlocked: 976771055 -> 976773168, native 976773168
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.441784] ata3.00: ATA-8: WDC WD5000AAKS-22A7B2, 01.03B01, max UDMA/133
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.441786] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.442840] ata3.00: configured for UDMA/133
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.456095] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 01.0 PQ: 0 ANSI: 5
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.456216] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.456231] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.456301] sd 2:0:0:0: [sda] Write Protect is off
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.456320] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.456426]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.477735] sd 2:0:0:0: [sda] Attached SCSI disk
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.488024] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.492108] ata5.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100, ATAPI AN
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.496411] ata5.00: configured for UDMA/100
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.519348] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.540250] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.540253] Uniform CD-ROM driver Revision: 3.20
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.540354] sr 4:0:0:0: Attached scsi generic sg1 type 5
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.543388] usbcore: registered new interface driver hiddev
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.547214] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.547281] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:12.0-2/input0
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.547299] usbcore: registered new interface driver usbhid
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.547302] usbhid: v2.6:USB HID core driver
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.865103] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
Jul 11 09:26:13 ubuntu-desktop kernel: [    1.865108] EXT4-fs (sda3): write access will be enabled during recovery
Jul 11 09:26:13 ubuntu-desktop kernel: [    2.233378] EXT4-fs (sda3): recovery complete
Jul 11 09:26:13 ubuntu-desktop kernel: [    2.233771] EXT4-fs (sda3): mounted filesystem with ordered data mode
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.761334] udev: starting version 151
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.792218] vga16fb: mapped to 0xc00a0000
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.792307] fb0: VGA16 VGA frame buffer device
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.833123] Adding 1952760k swap on /dev/sda5.  Priority:-1 extents:1 across:1952760k 
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.864013] Linux agpgart interface v0.103
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.867324] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.932938] lp: driver loaded but no devices found
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.960907] nvidia: module license 'NVIDIA' taints kernel.
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.960911] Disabling lock debugging due to kernel taint
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.971666] type=1505 audit(1278851145.728:2):  operation="profile_load" pid=684 name="/sbin/dhclient3"
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.971879] type=1505 audit(1278851145.728:3):  operation="profile_load" pid=684 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 11 09:26:13 ubuntu-desktop kernel: [   10.971993] type=1505 audit(1278851145.728:4):  operation="profile_load" pid=684 name="/usr/lib/connman/scripts/dhclient-script"
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.846538] parport_pc 00:09: reported by Plug and Play ACPI
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.846606] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.849284] cfg80211: Calling CRDA to update world regulatory domain
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.864078] cfg80211: World regulatory domain updated:
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.864082]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.864085]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.864087]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.864089]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.864091]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.864093]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.868652] ath5k 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jul 11 09:26:13 ubuntu-desktop kernel: [   11.868685] ath5k 0000:03:06.0: registered as 'phy0'
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.233128] ppdev: user-space parallel port driver
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.294952] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.346632] lp0: using parport0 (interrupt-driven).
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.360539] Console: switching to colour frame buffer device 80x30
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.366897] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.366910] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.367482] NVRM: loading NVIDIA UNIX x86 Kernel Module  256.35  Wed Jun 16 18:57:17 PDT 2010
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.439921] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.474012] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.474118] cfg80211: Calling CRDA for country: CN
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.476400] cfg80211: Regulatory domain changed to country: CN
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.476402]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.476405]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jul 11 09:26:13 ubuntu-desktop kernel: [   12.476407]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
Jul 11 09:26:13 ubuntu-desktop kernel: [   36.530609] kjournald starting.  Commit interval 5 seconds
Jul 11 09:26:13 ubuntu-desktop kernel: [   36.530884] EXT3 FS on sda6, internal journal
Jul 11 09:26:13 ubuntu-desktop kernel: [   36.530891] EXT3-fs: mounted filesystem with ordered data mode.
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.255551] type=1505 audit(1278851173.011:5):  operation="profile_load" pid=892 name="/usr/share/gdm/guest-session/Xsession"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.256658] type=1505 audit(1278851173.015:6):  operation="profile_replace" pid=893 name="/sbin/dhclient3"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.256874] type=1505 audit(1278851173.015:7):  operation="profile_replace" pid=893 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.256993] type=1505 audit(1278851173.015:8):  operation="profile_replace" pid=893 name="/usr/lib/connman/scripts/dhclient-script"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.259111] type=1505 audit(1278851173.015:9):  operation="profile_load" pid=894 name="/usr/bin/evince"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.261734] type=1505 audit(1278851173.019:10):  operation="profile_load" pid=894 name="/usr/bin/evince-previewer"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.263346] type=1505 audit(1278851173.019:11):  operation="profile_load" pid=894 name="/usr/bin/evince-thumbnailer"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.266932] type=1505 audit(1278851173.023:12):  operation="profile_load" pid=896 name="/usr/lib/cups/backend/cups-pdf"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.267188] type=1505 audit(1278851173.023:13):  operation="profile_load" pid=896 name="/usr/sbin/cupsd"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.268377] type=1505 audit(1278851173.027:14):  operation="profile_load" pid=897 name="/usr/sbin/tcpdump"
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.293137] r8169: eth0: link down
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.293316] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 11 09:26:13 ubuntu-desktop kernel: [   38.370971] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 11 09:26:23 ubuntu-desktop kernel: Kernel logging (proc) stopped.
Jul 11 09:26:23 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="854" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul 11 09:27:10 ubuntu-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 11 09:27:10 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="851" x-info="http://www.rsyslog.com"] (re)start
Jul 11 09:27:10 ubuntu-desktop rsyslogd: rsyslogd's groupid changed to 103
Jul 11 09:27:10 ubuntu-desktop rsyslogd: rsyslogd's userid changed to 101
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] KERNEL supported cpus:
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   Intel GenuineIntel
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   NSC Geode by NSC
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] DMI 2.4 present.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] modified physical RAM map:
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] RAMDISK: 37858000 - 37fef3be
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Allocated new RAMDISK: 008e0000 - 010773be
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fef3bd to 008e0000 - 010773bd
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: RSDP 000f70e0 00014 (v00 GBT   )
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: RSDT 7fee3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: FACP 7fee3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: DSDT 7fee30c0 042A8 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: FACS 7fee0000 00040
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: SSDT 7fee7440 007BA (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: HPET 7fee7c00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: MCFG 7fee7c40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: APIC 7fee7380 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] 1158MB HIGHMEM available.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] 887MB LOWMEM available.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #5 [00008dc000 - 00008df0fe]              BRK ==> [00008dc000 - 00008df0fe]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #7 [00008e0000 - 00010773be]      NEW RAMDISK ==> [00008e0000 - 00010773be]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] found SMP MP-table at [c00f56f0] f56f0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007fee0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Using APIC driver default
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:60100000)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519805
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=3d66cdf6-9da5-4918-b098-d88b6d937353 ro quiet splash
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Initializing CPU#0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] allocated 10480000 bytes of page_cgroup
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Memory: 2050904k/2096000k available (4679k kernel code, 43552k reserved, 2116k data, 660k init, 1186696k highmem)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] virtual kernel memory layout:
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] console [tty0] enabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.000000] Detected 2719.044 MHz processor.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5438.08 BogoMIPS (lpj=10876176)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008019] Security Framework initialized
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008034] AppArmor: AppArmor initialized
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008040] Mount-cache hash table entries: 512
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008132] Initializing cgroup subsys ns
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008135] Initializing cgroup subsys cpuacct
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008138] Initializing cgroup subsys memory
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008144] Initializing cgroup subsys devices
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008146] Initializing cgroup subsys freezer
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008148] Initializing cgroup subsys net_cls
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008161] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008163] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008165] CPU: Physical Processor ID: 0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008167] CPU: Processor Core ID: 0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008169] mce: CPU supports 6 MCE banks
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008177] using C1E aware idle routine
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008182] Performance Events: AMD PMU driver.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008187] ... version:                0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008188] ... bit width:              48
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008190] ... generic registers:      4
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008191] ... value mask:             0000ffffffffffff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008193] ... max period:             00007fffffffffff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008194] ... fixed-purpose events:   0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008196] ... event mask:             000000000000000f
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.008199] Checking 'hlt' instruction... OK.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.025770] ACPI: Core revision 20090903
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.032026] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.032037] ftrace: allocating 21780 entries in 43 pages
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.036059] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.036566] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.076675] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.012000] Initializing CPU#1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.012000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.012000] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.012000] CPU: Physical Processor ID: 0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.012000] CPU: Processor Core ID: 1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.164088] CPU1: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.164097] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168012] Brought up 2 CPUs
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168013] Total of 2 processors activated (10876.35 BogoMIPS).
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] devtmpfs: initialized
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] regulator: core version 0.5
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] Time:  9:26:58  Date: 07/11/10
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] NET: Registered protocol family 16
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] EISA bus registered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] Trying to unpack rootfs image as initramfs...
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] ACPI: bus type pci registered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] PCI: MCFG area at e0000000 reserved in E820
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] PCI: Using MMCONFIG for extended config space
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.168482] PCI: Using configuration type 1 for base access
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.172073] bio: create slab <bio-0> at 0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.178427] ACPI: Interpreter enabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.178439] ACPI: (supports S0 S3 S4 S5)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.178460] ACPI: Using IOAPIC for interrupt routing
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.181798] ACPI: No dock devices found.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.181894] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.181961] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.181964] pci 0000:00:02.0: PME# disabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.181996] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.181998] pci 0000:00:06.0: PME# disabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.182102] pci 0000:00:11.0: set SATA to AHCI mode
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.182321] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.182325] pci 0000:00:12.2: PME# disabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.182530] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.182534] pci 0000:00:13.2: PME# disabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.182778] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.182781] pci 0000:00:14.2: PME# disabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.183212] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.183216] pci 0000:02:00.0: PME# disabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.183437] pci 0000:00:14.4: transparent bridge
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.199969] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200049] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200117] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200185] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200252] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200319] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200387] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200455] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200546] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200549] vgaarb: loaded
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200637] SCSI subsystem initialized
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200769] usbcore: registered new interface driver usbfs
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200778] usbcore: registered new interface driver hub
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200796] usbcore: registered new device driver usb
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200880] ACPI: WMI: Mapper loaded
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.200881] PCI: Using ACPI for IRQ routing
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.201014] NetLabel: Initializing
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.201015] NetLabel:  domain hash size = 128
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.201017] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.201027] NetLabel:  unlabeled traffic allowed by default
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.201054] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.201058] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203087] Switching to clocksource tsc
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203293] AppArmor: AppArmor Filesystem Enabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203293] pnp: PnP ACPI init
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203293] ACPI: bus type pnp registered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203399] pnp: PnP ACPI: found 13 devices
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203401] ACPI: ACPI bus type pnp unregistered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203404] PnPBIOS: Disabled by ACPI PNP
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203413] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203415] system 00:01: ioport range 0x220-0x225 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203417] system 00:01: ioport range 0x290-0x294 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203421] system 00:02: ioport range 0x4100-0x411f has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203423] system 00:02: ioport range 0x228-0x22f has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203426] system 00:02: ioport range 0x238-0x23f has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203428] system 00:02: ioport range 0x40b-0x40b has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203430] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203432] system 00:02: ioport range 0xc00-0xc01 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203434] system 00:02: ioport range 0xc14-0xc14 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203436] system 00:02: ioport range 0xc50-0xc52 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203438] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203440] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203442] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203444] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203446] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203448] system 00:02: ioport range 0x4000-0x40fe has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203451] system 00:02: ioport range 0x4210-0x4217 has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203453] system 00:02: ioport range 0xb00-0xb0f has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203455] system 00:02: ioport range 0xb10-0xb1f has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203457] system 00:02: ioport range 0xb20-0xb3f has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203462] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203467] system 00:0c: iomem range 0xce000-0xcffff has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203469] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203471] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203473] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203476] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203478] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203480] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203483] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203485] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203487] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.203490] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238137] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238139] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238142] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238145] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238149] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238152] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238154] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238157] pci 0000:00:06.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238160] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238163] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238168] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238172] pci 0000:00:14.4:   PREFETCH window: 0xfdd00000-0xfddfffff
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238252] NET: Registered protocol family 2
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238329] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.238590] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.239132] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.239394] TCP: Hash tables configured (established 131072 bind 65536)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.239397] TCP reno registered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.239464] NET: Registered protocol family 1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.376961] cpufreq-nforce2: No nForce2 chipset.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.376984] Scanning for low memory corruption every 60 seconds
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.377070] audit: initializing netlink socket (disabled)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.377081] type=2000 audit(1278840418.376:1): initialized
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.383730] highmem bounce pool size: 64 pages
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.383734] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.384790] VFS: Disk quotas dquot_6.5.2
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.384834] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385249] fuse init (API version 7.13)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385307] msgmni has been set to 1690
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385475] alg: No test for stdrng (krng)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385518] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385521] io scheduler noop registered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385522] io scheduler anticipatory registered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385524] io scheduler deadline registered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385553] io scheduler cfq registered (default)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385759] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385776] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385848] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385852] ACPI: Power Button [PWRB]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385893] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.385895] ACPI: Power Button [PWRF]
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.386122] processor LNXCPU:00: registered as cooling_device0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.386149] processor LNXCPU:01: registered as cooling_device1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.386421] Freeing initrd memory: 7772k freed
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.388801] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.388916] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.389204] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.389732] isapnp: Scanning for PnP cards...
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.389954] brd: module loaded
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390251] loop: module loaded
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390308] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390425] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390667] Fixed MDIO Bus: probed
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390690] PPP generic driver version 2.4.2
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390713] tun: Universal TUN/TAP device driver, 1.6
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390714] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390766] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390788] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390799] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390820] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390840] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390854] ehci_hcd 0000:00:12.2: debug port 1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.390886] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400743] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400806] usb usb1: configuration #1 chosen from 1 choice
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400827] hub 1-0:1.0: USB hub found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400833] hub 1-0:1.0: 6 ports detected
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400889] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400896] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400916] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400934] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400946] ehci_hcd 0000:00:13.2: debug port 1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.400971] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412741] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412787] usb usb2: configuration #1 chosen from 1 choice
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412804] hub 2-0:1.0: USB hub found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412808] hub 2-0:1.0: 6 ports detected
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412854] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412864] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412871] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412894] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.412920] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.472768] usb usb3: configuration #1 chosen from 1 choice
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.472785] hub 3-0:1.0: USB hub found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.472792] hub 3-0:1.0: 3 ports detected
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.472826] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.472834] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.472853] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.472866] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.532769] usb usb4: configuration #1 chosen from 1 choice
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.532785] hub 4-0:1.0: USB hub found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.532791] hub 4-0:1.0: 3 ports detected
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.532835] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.532842] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.532861] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.532887] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.592768] usb usb5: configuration #1 chosen from 1 choice
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.592786] hub 5-0:1.0: USB hub found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.592793] hub 5-0:1.0: 3 ports detected
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.592827] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.592835] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.592854] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.592868] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.652770] usb usb6: configuration #1 chosen from 1 choice
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.652787] hub 6-0:1.0: USB hub found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.652794] hub 6-0:1.0: 3 ports detected
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.652828] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.652836] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.652859] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.652873] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.712775] usb usb7: configuration #1 chosen from 1 choice
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.712791] hub 7-0:1.0: USB hub found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.712799] hub 7-0:1.0: 2 ports detected
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.712831] uhci_hcd: USB Universal Host Controller Interface driver
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.712877] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.712879] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713012] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713076] mice: PS/2 mouse device common for all mice
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713155] rtc_cmos 00:05: RTC can wake from S4
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713184] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713218] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713288] device-mapper: uevent: version 1.0.3
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713372] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713420] device-mapper: multipath: version 1.1.0 loaded
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713423] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713499] EISA: Probing bus 0 at eisa.0
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713516] Cannot allocate resource for EISA slot 4
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713531] EISA: Detected 0 cards.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713581] cpuidle: using governor ladder
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713582] cpuidle: using governor menu
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713886] TCP cubic registered
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.713992] NET: Registered protocol family 10
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.714333] lo: Disabled Privacy Extensions
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.714570] NET: Registered protocol family 17
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.714591] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.714617] powernow-k8:    0 : pstate 0 (2700 MHz)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.714619] powernow-k8:    1 : pstate 1 (1350 MHz)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.743682] isapnp: No Plug & Play device found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.743721] Using IPI No-Shortcut mode
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.743807] registered taskstats version 1
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.744082]   Magic number: 2:160:424
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.744144] rtc_cmos 00:05: setting system clock to 2010-07-11 09:26:59 UTC (1278840419)
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.744147] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.744149] EDD information not available.
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.744191] Freeing unused kernel memory: 660k freed
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.744498] Write protecting the kernel text: 4680k
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.744525] Write protecting the kernel read-only data: 1840k
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.748889] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.756362] udev: starting version 151
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.807886] scsi0 : pata_atiixp
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.808606] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.808622] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.809047] scsi1 : pata_atiixp
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.809862] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.809864] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.809941] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.810076] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.810079] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.810630] eth0: RTL8168c/8111c at 0xf808e000, 00:24:1d:2a:40:65, XID 1c4000c0 IRQ 27
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.836924] scsi2 : ahci
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.840987] scsi3 : ahci
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.841051] scsi4 : ahci
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.841096] scsi5 : ahci
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.841196] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.841200] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.841203] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.841206] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Jul 11 09:27:10 ubuntu-desktop kernel: [    0.952759] usb 3-2: new low speed USB device using ohci_hcd and address 2
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.143188] usb 3-2: configuration #1 chosen from 1 choice
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.164031] ata6: SATA link down (SStatus 0 SControl 300)
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.164099] ata4: SATA link down (SStatus 0 SControl 300)
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.328013] ata5: applying SB600 PMP SRST workaround and retrying
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.328030] ata3: applying SB600 PMP SRST workaround and retrying
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.492018] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.492038] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.493684] ata3.00: HPA unlocked: 976771055 -> 976773168, native 976773168
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.493786] ata3.00: ATA-8: WDC WD5000AAKS-22A7B2, 01.03B01, max UDMA/133
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.493788] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.494810] ata3.00: configured for UDMA/133
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.496121] ata5.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100, ATAPI AN
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.500423] ata5.00: configured for UDMA/100
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.508098] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 01.0 PQ: 0 ANSI: 5
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.508213] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.508232] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.508317] sd 2:0:0:0: [sda] Write Protect is off
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.508338] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.508442]  sda: sda1 sda2 sda3 sda4 <
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.523338] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.531304]  sda5 sda6 >
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.531562] sd 2:0:0:0: [sda] Attached SCSI disk
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.544240] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.544243] Uniform CD-ROM driver Revision: 3.20
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.544337] sr 4:0:0:0: Attached scsi generic sg1 type 5
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.547886] usbcore: registered new interface driver hiddev
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.552289] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.552368] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:12.0-2/input0
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.552388] usbcore: registered new interface driver usbhid
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.552391] usbhid: v2.6:USB HID core driver
Jul 11 09:27:10 ubuntu-desktop kernel: [    1.866502] EXT4-fs (sda3): mounted filesystem with ordered data mode
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.271116] udev: starting version 151
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.318702] Linux agpgart interface v0.103
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.323336] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.388563] vga16fb: mapped to 0xc00a0000
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.388617] fb0: VGA16 VGA frame buffer device
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.405993] Adding 1952760k swap on /dev/sda5.  Priority:-1 extents:1 across:1952760k 
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.428741] type=1505 audit(1278851228.184:2):  operation="profile_load" pid=628 name="/sbin/dhclient3"
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.428948] type=1505 audit(1278851228.184:3):  operation="profile_load" pid=628 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.429066] type=1505 audit(1278851228.184:4):  operation="profile_load" pid=628 name="/usr/lib/connman/scripts/dhclient-script"
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.467546] nvidia: module license 'NVIDIA' taints kernel.
Jul 11 09:27:10 ubuntu-desktop kernel: [    9.467551] Disabling lock debugging due to kernel taint
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.117244] kjournald starting.  Commit interval 5 seconds
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.117487] EXT3 FS on sda6, internal journal
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.117492] EXT3-fs: mounted filesystem with ordered data mode.
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.351618] lp: driver loaded but no devices found
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.354920] cfg80211: Calling CRDA to update world regulatory domain
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.369254] cfg80211: World regulatory domain updated:
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.369257]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.369260]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.369262]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.369264]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.369266]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.369268]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.374139] ath5k 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.374172] ath5k 0000:03:06.0: registered as 'phy0'
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.601835] parport_pc 00:09: reported by Plug and Play ACPI
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.601896] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.665037] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.665114] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.665126] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.665245] NVRM: loading NVIDIA UNIX x86 Kernel Module  256.35  Wed Jun 16 18:57:17 PDT 2010
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.816408] lp0: using parport0 (interrupt-driven).
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.881642] Console: switching to colour frame buffer device 80x30
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.895433] ppdev: user-space parallel port driver
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.944640] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.986368] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.986524] cfg80211: Calling CRDA for country: CN
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.988308] cfg80211: Regulatory domain changed to country: CN
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.988310]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.988313]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jul 11 09:27:10 ubuntu-desktop kernel: [   10.988315]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.819081] type=1505 audit(1278851230.571:5):  operation="profile_load" pid=889 name="/usr/share/gdm/guest-session/Xsession"
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.820150] type=1505 audit(1278851230.575:6):  operation="profile_replace" pid=890 name="/sbin/dhclient3"
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.820363] type=1505 audit(1278851230.575:7):  operation="profile_replace" pid=890 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.820480] type=1505 audit(1278851230.575:8):  operation="profile_replace" pid=890 name="/usr/lib/connman/scripts/dhclient-script"
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.822578] type=1505 audit(1278851230.575:9):  operation="profile_load" pid=891 name="/usr/bin/evince"
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.825200] type=1505 audit(1278851230.579:10):  operation="profile_load" pid=891 name="/usr/bin/evince-previewer"
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.826825] type=1505 audit(1278851230.579:11):  operation="profile_load" pid=891 name="/usr/bin/evince-thumbnailer"
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.907986] r8169: eth0: link down
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.908157] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 11 09:27:10 ubuntu-desktop kernel: [   11.975926] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 11 09:27:38 ubuntu-desktop kernel: [   39.639685] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 11 09:27:42 ubuntu-desktop kernel: [   43.457616] padlock: VIA PadLock not detected.
Jul 11 18:34:39 ubuntu-desktop kernel: [32859.159673] ath5k phy0: unsupported jumbo
Jul 11 18:53:22 ubuntu-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 11 18:53:22 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="849" x-info="http://www.rsyslog.com"] (re)start
Jul 11 18:53:22 ubuntu-desktop rsyslogd: rsyslogd's groupid changed to 103
Jul 11 18:53:22 ubuntu-desktop rsyslogd: rsyslogd's userid changed to 101
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] KERNEL supported cpus:
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   Intel GenuineIntel
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   NSC Geode by NSC
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] DMI 2.4 present.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] modified physical RAM map:
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] RAMDISK: 37858000 - 37fef3be
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Allocated new RAMDISK: 008e0000 - 010773be
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fef3bd to 008e0000 - 010773bd
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: RSDP 000f70e0 00014 (v00 GBT   )
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: RSDT 7fee3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: FACP 7fee3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: DSDT 7fee30c0 042A8 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: FACS 7fee0000 00040
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: SSDT 7fee7440 007BA (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: HPET 7fee7c00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: MCFG 7fee7c40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: APIC 7fee7380 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] 1158MB HIGHMEM available.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] 887MB LOWMEM available.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #5 [00008dc000 - 00008df0fe]              BRK ==> [00008dc000 - 00008df0fe]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #7 [00008e0000 - 00010773be]      NEW RAMDISK ==> [00008e0000 - 00010773be]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] found SMP MP-table at [c00f56f0] f56f0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007fee0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Using APIC driver default
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:60100000)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519805
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=3d66cdf6-9da5-4918-b098-d88b6d937353 ro quiet splash
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Initializing CPU#0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] allocated 10480000 bytes of page_cgroup
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Memory: 2050904k/2096000k available (4679k kernel code, 43552k reserved, 2116k data, 660k init, 1186696k highmem)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] virtual kernel memory layout:
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] console [tty0] enabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.000000] Detected 2719.282 MHz processor.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5438.56 BogoMIPS (lpj=10877128)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004018] Security Framework initialized
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004034] AppArmor: AppArmor initialized
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004040] Mount-cache hash table entries: 512
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004131] Initializing cgroup subsys ns
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004133] Initializing cgroup subsys cpuacct
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004137] Initializing cgroup subsys memory
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004142] Initializing cgroup subsys devices
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004144] Initializing cgroup subsys freezer
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004146] Initializing cgroup subsys net_cls
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004159] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004162] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004164] CPU: Physical Processor ID: 0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004165] CPU: Processor Core ID: 0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004168] mce: CPU supports 6 MCE banks
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004176] using C1E aware idle routine
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004180] Performance Events: AMD PMU driver.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004185] ... version:                0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004186] ... bit width:              48
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004188] ... generic registers:      4
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004189] ... value mask:             0000ffffffffffff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004191] ... max period:             00007fffffffffff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004192] ... fixed-purpose events:   0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004194] ... event mask:             000000000000000f
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.004197] Checking 'hlt' instruction... OK.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.021770] ACPI: Core revision 20090903
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.028025] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.028034] ftrace: allocating 21780 entries in 43 pages
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.032059] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.032566] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.072678] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.008000] Initializing CPU#1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.008000] CPU: Physical Processor ID: 0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.008000] CPU: Processor Core ID: 1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.160105] CPU1: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.160114] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164012] Brought up 2 CPUs
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164014] Total of 2 processors activated (10876.82 BogoMIPS).
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] devtmpfs: initialized
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] regulator: core version 0.5
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] Time: 18:52:45  Date: 07/11/10
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] NET: Registered protocol family 16
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] EISA bus registered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] Trying to unpack rootfs image as initramfs...
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] ACPI: bus type pci registered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] PCI: MCFG area at e0000000 reserved in E820
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] PCI: Using MMCONFIG for extended config space
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.164484] PCI: Using configuration type 1 for base access
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.168073] bio: create slab <bio-0> at 0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.174428] ACPI: Interpreter enabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.174440] ACPI: (supports S0 S3 S4 S5)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.174461] ACPI: Using IOAPIC for interrupt routing
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.177801] ACPI: No dock devices found.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.177897] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.177963] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.177966] pci 0000:00:02.0: PME# disabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.177998] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.178000] pci 0000:00:06.0: PME# disabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.178103] pci 0000:00:11.0: set SATA to AHCI mode
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.178322] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.178326] pci 0000:00:12.2: PME# disabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.178531] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.178535] pci 0000:00:13.2: PME# disabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.178778] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.178782] pci 0000:00:14.2: PME# disabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.179211] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.179215] pci 0000:02:00.0: PME# disabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.179437] pci 0000:00:14.4: transparent bridge
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196100] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196172] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196240] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196308] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196375] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196444] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196512] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196579] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196671] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196674] vgaarb: loaded
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196764] SCSI subsystem initialized
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196891] usbcore: registered new interface driver usbfs
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196900] usbcore: registered new interface driver hub
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.196918] usbcore: registered new device driver usb
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.197006] ACPI: WMI: Mapper loaded
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.197008] PCI: Using ACPI for IRQ routing
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.197138] NetLabel: Initializing
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.197139] NetLabel:  domain hash size = 128
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.197141] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.197152] NetLabel:  unlabeled traffic allowed by default
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.197178] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.197182] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199212] Switching to clocksource tsc
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199297] AppArmor: AppArmor Filesystem Enabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199297] pnp: PnP ACPI init
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199297] ACPI: bus type pnp registered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199387] pnp: PnP ACPI: found 13 devices
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199389] ACPI: ACPI bus type pnp unregistered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199392] PnPBIOS: Disabled by ACPI PNP
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199400] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199402] system 00:01: ioport range 0x220-0x225 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199405] system 00:01: ioport range 0x290-0x294 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199409] system 00:02: ioport range 0x4100-0x411f has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199411] system 00:02: ioport range 0x228-0x22f has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199413] system 00:02: ioport range 0x238-0x23f has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199415] system 00:02: ioport range 0x40b-0x40b has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199417] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199419] system 00:02: ioport range 0xc00-0xc01 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199421] system 00:02: ioport range 0xc14-0xc14 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199423] system 00:02: ioport range 0xc50-0xc52 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199425] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199427] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199429] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199432] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199434] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199436] system 00:02: ioport range 0x4000-0x40fe has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199438] system 00:02: ioport range 0x4210-0x4217 has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199440] system 00:02: ioport range 0xb00-0xb0f has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199442] system 00:02: ioport range 0xb10-0xb1f has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199444] system 00:02: ioport range 0xb20-0xb3f has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199450] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199454] system 00:0c: iomem range 0xce000-0xcffff has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199456] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199459] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199461] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199463] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199465] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199468] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199470] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199472] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199475] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.199477] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234122] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234125] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234128] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234131] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234135] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234137] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234140] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234142] pci 0000:00:06.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234145] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234148] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234153] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234157] pci 0000:00:14.4:   PREFETCH window: 0xfdd00000-0xfddfffff
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234238] NET: Registered protocol family 2
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234314] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.234570] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.235114] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.235379] TCP: Hash tables configured (established 131072 bind 65536)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.235381] TCP reno registered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.235450] NET: Registered protocol family 1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.372935] cpufreq-nforce2: No nForce2 chipset.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.372957] Scanning for low memory corruption every 60 seconds
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.373042] audit: initializing netlink socket (disabled)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.373053] type=2000 audit(1278874364.372:1): initialized
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.379701] highmem bounce pool size: 64 pages
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.379705] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.380760] VFS: Disk quotas dquot_6.5.2
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.380804] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381218] fuse init (API version 7.13)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381276] msgmni has been set to 1690
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381445] alg: No test for stdrng (krng)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381486] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381489] io scheduler noop registered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381491] io scheduler anticipatory registered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381492] io scheduler deadline registered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381522] io scheduler cfq registered (default)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381730] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381747] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381821] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381825] ACPI: Power Button [PWRB]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381866] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.381868] ACPI: Power Button [PWRF]
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.382096] processor LNXCPU:00: registered as cooling_device0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.382123] processor LNXCPU:01: registered as cooling_device1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.382452] Freeing initrd memory: 7772k freed
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.384764] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.384880] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.385169] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.385768] isapnp: Scanning for PnP cards...
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.385925] brd: module loaded
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386223] loop: module loaded
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386279] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386399] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386641] Fixed MDIO Bus: probed
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386664] PPP generic driver version 2.4.2
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386687] tun: Universal TUN/TAP device driver, 1.6
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386689] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386740] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386762] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386773] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386794] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386814] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386828] ehci_hcd 0000:00:12.2: debug port 1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.386859] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396721] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396784] usb usb1: configuration #1 chosen from 1 choice
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396805] hub 1-0:1.0: USB hub found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396812] hub 1-0:1.0: 6 ports detected
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396868] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396875] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396895] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396912] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396925] ehci_hcd 0000:00:13.2: debug port 1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.396949] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408717] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408764] usb usb2: configuration #1 chosen from 1 choice
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408781] hub 2-0:1.0: USB hub found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408785] hub 2-0:1.0: 6 ports detected
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408832] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408842] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408849] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408872] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.408898] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.468740] usb usb3: configuration #1 chosen from 1 choice
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.468757] hub 3-0:1.0: USB hub found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.468764] hub 3-0:1.0: 3 ports detected
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.468798] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.468806] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.468825] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.468838] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.528736] usb usb4: configuration #1 chosen from 1 choice
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.528752] hub 4-0:1.0: USB hub found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.528758] hub 4-0:1.0: 3 ports detected
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.528802] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.528809] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.528828] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.528854] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.588730] usb usb5: configuration #1 chosen from 1 choice
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.588747] hub 5-0:1.0: USB hub found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.588755] hub 5-0:1.0: 3 ports detected
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.588789] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.588796] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.588816] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.588830] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.648726] usb usb6: configuration #1 chosen from 1 choice
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.648744] hub 6-0:1.0: USB hub found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.648751] hub 6-0:1.0: 3 ports detected
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.648784] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.648792] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.648815] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.648830] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.708726] usb usb7: configuration #1 chosen from 1 choice
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.708742] hub 7-0:1.0: USB hub found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.708750] hub 7-0:1.0: 2 ports detected
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.708783] uhci_hcd: USB Universal Host Controller Interface driver
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.708828] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.708830] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.708964] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709028] mice: PS/2 mouse device common for all mice
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709107] rtc_cmos 00:05: RTC can wake from S4
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709136] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709169] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709238] device-mapper: uevent: version 1.0.3
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709324] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709372] device-mapper: multipath: version 1.1.0 loaded
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709374] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709451] EISA: Probing bus 0 at eisa.0
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709467] Cannot allocate resource for EISA slot 4
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709483] EISA: Detected 0 cards.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709532] cpuidle: using governor ladder
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709534] cpuidle: using governor menu
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709838] TCP cubic registered
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.709944] NET: Registered protocol family 10
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.710285] lo: Disabled Privacy Extensions
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.710521] NET: Registered protocol family 17
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.710543] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.710569] powernow-k8:    0 : pstate 0 (2700 MHz)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.710570] powernow-k8:    1 : pstate 1 (1350 MHz)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.739679] isapnp: No Plug & Play device found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.739718] Using IPI No-Shortcut mode
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.739805] registered taskstats version 1
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.740080]   Magic number: 2:82:898
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.740142] rtc_cmos 00:05: setting system clock to 2010-07-11 18:52:45 UTC (1278874365)
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.740145] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.740147] EDD information not available.
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.740189] Freeing unused kernel memory: 660k freed
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.740496] Write protecting the kernel text: 4680k
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.740524] Write protecting the kernel read-only data: 1840k
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.745097] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.752320] udev: starting version 151
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.801658] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.801767] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.801770] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.806204] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.806222] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.806761] eth0: RTL8168c/8111c at 0xf8092000, 00:24:1d:2a:40:65, XID 1c4000c0 IRQ 27
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.809503] scsi0 : ahci
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.828874] scsi1 : ahci
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.834782] scsi2 : ahci
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.834889] scsi3 : ahci
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.834988] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.834992] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.834995] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.834998] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.836953] scsi4 : pata_atiixp
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.837050] scsi5 : pata_atiixp
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.837856] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.837859] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Jul 11 18:53:22 ubuntu-desktop kernel: [    0.944690] usb 3-2: new low speed USB device using ohci_hcd and address 2
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.083247] usb 3-2: configuration #1 chosen from 1 choice
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.112031] ata4: SATA link down (SStatus 0 SControl 300)
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.112059] ata2: SATA link down (SStatus 0 SControl 300)
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.276017] ata1: applying SB600 PMP SRST workaround and retrying
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.276034] ata3: applying SB600 PMP SRST workaround and retrying
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.440020] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.440041] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.441619] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.441712] ata1.00: ATA-8: WDC WD5000AAKS-22A7B2, 01.03B01, max UDMA/133
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.441714] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.442668] ata1.00: configured for UDMA/133
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.444127] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100, ATAPI AN
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.448428] ata3.00: configured for UDMA/100
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.456099] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 01.0 PQ: 0 ANSI: 5
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.456227] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.456264] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.456312] sd 0:0:0:0: [sda] Write Protect is off
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.456330] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.456427]  sda: sda1 sda2 sda3 sda4 <
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.475356] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.485411]  sda5 sda6 >
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.485649] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.496284] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.496287] Uniform CD-ROM driver Revision: 3.20
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.496385] sr 2:0:0:0: Attached scsi generic sg1 type 5
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.666473] usbcore: registered new interface driver hiddev
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.671845] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.671920] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:12.0-2/input0
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.671945] usbcore: registered new interface driver usbhid
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.671947] usbhid: v2.6:USB HID core driver
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.972785] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
Jul 11 18:53:22 ubuntu-desktop kernel: [    1.972790] EXT4-fs (sda3): write access will be enabled during recovery
Jul 11 18:53:22 ubuntu-desktop kernel: [    2.862758] EXT4-fs (sda3): recovery complete
Jul 11 18:53:22 ubuntu-desktop kernel: [    2.863096] EXT4-fs (sda3): mounted filesystem with ordered data mode
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.245567] udev: starting version 151
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.295469] Adding 1952760k swap on /dev/sda5.  Priority:-1 extents:1 across:1952760k 
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.364638] vga16fb: mapped to 0xc00a0000
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.364687] fb0: VGA16 VGA frame buffer device
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.391878] Linux agpgart interface v0.103
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.438196] nvidia: module license 'NVIDIA' taints kernel.
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.438200] Disabling lock debugging due to kernel taint
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.447513] type=1505 audit(1278885175.204:2):  operation="profile_load" pid=678 name="/sbin/dhclient3"
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.447720] type=1505 audit(1278885175.204:3):  operation="profile_load" pid=678 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 11 18:53:22 ubuntu-desktop kernel: [   10.447834] type=1505 audit(1278885175.204:4):  operation="profile_load" pid=678 name="/usr/lib/connman/scripts/dhclient-script"
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.312226] parport_pc 00:09: reported by Plug and Play ACPI
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.312281] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.329802] cfg80211: Calling CRDA to update world regulatory domain
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.345767] cfg80211: World regulatory domain updated:
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.345771]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.345774]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.345776]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.345779]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.345780]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.345782]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.350336] ath5k 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.350369] ath5k 0000:03:06.0: registered as 'phy0'
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.562863] ppdev: user-space parallel port driver
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.590336] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.590385] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.590515] NVRM: loading NVIDIA UNIX x86 Kernel Module  256.35  Wed Jun 16 18:57:17 PDT 2010
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.625534] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.842103] Console: switching to colour frame buffer device 80x30
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.849322] lp0: using parport0 (interrupt-driven).
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.947728] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.955729] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.956028] cfg80211: Calling CRDA for country: CN
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.958189] cfg80211: Regulatory domain changed to country: CN
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.958192]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.958194]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.958196]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
Jul 11 18:53:22 ubuntu-desktop kernel: [   11.962997] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Jul 11 18:53:22 ubuntu-desktop kernel: [   36.363579] kjournald starting.  Commit interval 5 seconds
Jul 11 18:53:22 ubuntu-desktop kernel: [   36.363852] EXT3 FS on sda6, internal journal
Jul 11 18:53:22 ubuntu-desktop kernel: [   36.363858] EXT3-fs: mounted filesystem with ordered data mode.
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.096526] type=1505 audit(1278885202.855:5):  operation="profile_load" pid=886 name="/usr/share/gdm/guest-session/Xsession"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.097619] type=1505 audit(1278885202.855:6):  operation="profile_replace" pid=887 name="/sbin/dhclient3"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.097836] type=1505 audit(1278885202.855:7):  operation="profile_replace" pid=887 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.097958] type=1505 audit(1278885202.855:8):  operation="profile_replace" pid=887 name="/usr/lib/connman/scripts/dhclient-script"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.100112] type=1505 audit(1278885202.859:9):  operation="profile_load" pid=888 name="/usr/bin/evince"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.102791] type=1505 audit(1278885202.859:10):  operation="profile_load" pid=888 name="/usr/bin/evince-previewer"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.104441] type=1505 audit(1278885202.863:11):  operation="profile_load" pid=888 name="/usr/bin/evince-thumbnailer"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.107960] type=1505 audit(1278885202.863:12):  operation="profile_load" pid=890 name="/usr/lib/cups/backend/cups-pdf"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.108218] type=1505 audit(1278885202.867:13):  operation="profile_load" pid=890 name="/usr/sbin/cupsd"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.109426] type=1505 audit(1278885202.867:14):  operation="profile_load" pid=891 name="/usr/sbin/tcpdump"
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.152076] r8169: eth0: link down
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.152243] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 11 18:53:22 ubuntu-desktop kernel: [   38.222289] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 11 18:53:24 ubuntu-desktop pulseaudio[1100]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.Spawn.ExecFailed: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
Jul 11 18:53:38 ubuntu-desktop kernel: [   54.128044] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 11 18:53:42 ubuntu-desktop kernel: [   57.469454] padlock: VIA PadLock not detected.
Jul 11 18:54:08 ubuntu-desktop kernel: [   80.910452] nautilus[1435]: segfault at 4 ip 009b3189 sp bf88acf0 error 4 in libgobject-2.0.so.0.2400.1[989000+3d000]
Jul 11 18:54:08 ubuntu-desktop kernel: Kernel logging (proc) stopped.
Jul 11 18:54:56 ubuntu-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 11 18:54:56 ubuntu-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="852" x-info="http://www.rsyslog.com"] (re)start
Jul 11 18:54:56 ubuntu-desktop rsyslogd: rsyslogd's groupid changed to 103
Jul 11 18:54:56 ubuntu-desktop rsyslogd: rsyslogd's userid changed to 101
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] KERNEL supported cpus:
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   Intel GenuineIntel
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   NSC Geode by NSC
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] DMI 2.4 present.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] modified physical RAM map:
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] RAMDISK: 37858000 - 37fef3be
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Allocated new RAMDISK: 008e0000 - 010773be
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fef3bd to 008e0000 - 010773bd
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: RSDP 000f70e0 00014 (v00 GBT   )
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: RSDT 7fee3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: FACP 7fee3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: DSDT 7fee30c0 042A8 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: FACS 7fee0000 00040
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: SSDT 7fee7440 007BA (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: HPET 7fee7c00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: MCFG 7fee7c40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: APIC 7fee7380 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] 1158MB HIGHMEM available.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] 887MB LOWMEM available.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #5 [00008dc000 - 00008df0fe]              BRK ==> [00008dc000 - 00008df0fe]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #7 [00008e0000 - 00010773be]      NEW RAMDISK ==> [00008e0000 - 00010773be]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] found SMP MP-table at [c00f56f0] f56f0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007fee0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Using APIC driver default
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:60100000)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519805
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=3d66cdf6-9da5-4918-b098-d88b6d937353 ro quiet splash
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Initializing CPU#0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] allocated 10480000 bytes of page_cgroup
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Memory: 2050904k/2096000k available (4679k kernel code, 43552k reserved, 2116k data, 660k init, 1186696k highmem)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] virtual kernel memory layout:
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] console [tty0] enabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.000000] Detected 2719.634 MHz processor.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5439.26 BogoMIPS (lpj=10878536)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004018] Security Framework initialized
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004034] AppArmor: AppArmor initialized
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004040] Mount-cache hash table entries: 512
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004131] Initializing cgroup subsys ns
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004134] Initializing cgroup subsys cpuacct
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004137] Initializing cgroup subsys memory
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004143] Initializing cgroup subsys devices
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004145] Initializing cgroup subsys freezer
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004146] Initializing cgroup subsys net_cls
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004160] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004162] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004164] CPU: Physical Processor ID: 0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004165] CPU: Processor Core ID: 0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004168] mce: CPU supports 6 MCE banks
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004176] using C1E aware idle routine
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004181] Performance Events: AMD PMU driver.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004186] ... version:                0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004187] ... bit width:              48
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004188] ... generic registers:      4
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004190] ... value mask:             0000ffffffffffff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004192] ... max period:             00007fffffffffff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004193] ... fixed-purpose events:   0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004195] ... event mask:             000000000000000f
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.004198] Checking 'hlt' instruction... OK.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.021775] ACPI: Core revision 20090903
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.028025] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.028033] ftrace: allocating 21780 entries in 43 pages
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.032059] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.032566] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.072758] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.008000] Initializing CPU#1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.008000] CPU: Physical Processor ID: 0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.008000] CPU: Processor Core ID: 1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.160101] CPU1: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.160111] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164011] Brought up 2 CPUs
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164013] Total of 2 processors activated (10877.53 BogoMIPS).
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] devtmpfs: initialized
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] regulator: core version 0.5
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] Time: 18:54:44  Date: 07/11/10
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] NET: Registered protocol family 16
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] EISA bus registered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] Trying to unpack rootfs image as initramfs...
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] ACPI: bus type pci registered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] PCI: MCFG area at e0000000 reserved in E820
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] PCI: Using MMCONFIG for extended config space
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.164482] PCI: Using configuration type 1 for base access
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.168073] bio: create slab <bio-0> at 0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.174441] ACPI: Interpreter enabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.174453] ACPI: (supports S0 S3 S4 S5)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.174474] ACPI: Using IOAPIC for interrupt routing
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.177819] ACPI: No dock devices found.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.177916] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.177983] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.177986] pci 0000:00:02.0: PME# disabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178018] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178020] pci 0000:00:06.0: PME# disabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178124] pci 0000:00:11.0: set SATA to AHCI mode
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178344] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178348] pci 0000:00:12.2: PME# disabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178553] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178557] pci 0000:00:13.2: PME# disabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178800] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.178804] pci 0000:00:14.2: PME# disabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.179230] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.179234] pci 0000:02:00.0: PME# disabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.179454] pci 0000:00:14.4: transparent bridge
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196004] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196075] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196144] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196212] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196280] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196347] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196416] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196484] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196575] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196577] vgaarb: loaded
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196667] SCSI subsystem initialized
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196796] usbcore: registered new interface driver usbfs
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196805] usbcore: registered new interface driver hub
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196823] usbcore: registered new device driver usb
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196906] ACPI: WMI: Mapper loaded
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.196908] PCI: Using ACPI for IRQ routing
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.197039] NetLabel: Initializing
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.197040] NetLabel:  domain hash size = 128
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.197042] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.197052] NetLabel:  unlabeled traffic allowed by default
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.197079] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.197083] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199113] Switching to clocksource tsc
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199293] AppArmor: AppArmor Filesystem Enabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199293] pnp: PnP ACPI init
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199293] ACPI: bus type pnp registered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199391] pnp: PnP ACPI: found 13 devices
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199393] ACPI: ACPI bus type pnp unregistered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199396] PnPBIOS: Disabled by ACPI PNP
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199405] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199407] system 00:01: ioport range 0x220-0x225 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199409] system 00:01: ioport range 0x290-0x294 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199413] system 00:02: ioport range 0x4100-0x411f has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199415] system 00:02: ioport range 0x228-0x22f has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199417] system 00:02: ioport range 0x238-0x23f has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199420] system 00:02: ioport range 0x40b-0x40b has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199422] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199424] system 00:02: ioport range 0xc00-0xc01 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199426] system 00:02: ioport range 0xc14-0xc14 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199428] system 00:02: ioport range 0xc50-0xc52 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199430] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199432] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199434] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199436] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199438] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199440] system 00:02: ioport range 0x4000-0x40fe has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199442] system 00:02: ioport range 0x4210-0x4217 has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199445] system 00:02: ioport range 0xb00-0xb0f has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199447] system 00:02: ioport range 0xb10-0xb1f has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199449] system 00:02: ioport range 0xb20-0xb3f has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199454] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199459] system 00:0c: iomem range 0xce000-0xcffff has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199461] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199463] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199465] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199468] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199470] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199472] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199475] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199477] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199480] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.199482] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234123] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234126] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234129] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234132] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234136] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234138] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234141] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234144] pci 0000:00:06.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234147] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234150] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234155] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234159] pci 0000:00:14.4:   PREFETCH window: 0xfdd00000-0xfddfffff
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234239] NET: Registered protocol family 2
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234315] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.234572] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.235113] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.235379] TCP: Hash tables configured (established 131072 bind 65536)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.235381] TCP reno registered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.235448] NET: Registered protocol family 1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.372918] cpufreq-nforce2: No nForce2 chipset.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.372940] Scanning for low memory corruption every 60 seconds
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.373024] audit: initializing netlink socket (disabled)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.373035] type=2000 audit(1278874484.372:1): initialized
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.379683] highmem bounce pool size: 64 pages
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.379687] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.380744] VFS: Disk quotas dquot_6.5.2
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.380787] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381202] fuse init (API version 7.13)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381259] msgmni has been set to 1690
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381430] alg: No test for stdrng (krng)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381471] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381474] io scheduler noop registered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381475] io scheduler anticipatory registered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381477] io scheduler deadline registered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381506] io scheduler cfq registered (default)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381712] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381730] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381800] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381804] ACPI: Power Button [PWRB]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381844] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.381846] ACPI: Power Button [PWRF]
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.382074] processor LNXCPU:00: registered as cooling_device0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.382101] processor LNXCPU:01: registered as cooling_device1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.382509] Freeing initrd memory: 7772k freed
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.384739] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.384855] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.385145] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.385820] isapnp: Scanning for PnP cards...
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.385908] brd: module loaded
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386207] loop: module loaded
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386264] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386384] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386629] Fixed MDIO Bus: probed
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386652] PPP generic driver version 2.4.2
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386675] tun: Universal TUN/TAP device driver, 1.6
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386676] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386727] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386750] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386761] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386781] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386802] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386815] ehci_hcd 0000:00:12.2: debug port 1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.386846] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396699] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396763] usb usb1: configuration #1 chosen from 1 choice
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396784] hub 1-0:1.0: USB hub found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396791] hub 1-0:1.0: 6 ports detected
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396847] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396854] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396875] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396892] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396905] ehci_hcd 0000:00:13.2: debug port 1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.396929] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408694] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408740] usb usb2: configuration #1 chosen from 1 choice
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408757] hub 2-0:1.0: USB hub found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408762] hub 2-0:1.0: 6 ports detected
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408809] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408819] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408826] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408849] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.408875] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.468709] usb usb3: configuration #1 chosen from 1 choice
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.468726] hub 3-0:1.0: USB hub found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.468733] hub 3-0:1.0: 3 ports detected
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.468767] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.468775] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.468794] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.468808] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.528697] usb usb4: configuration #1 chosen from 1 choice
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.528713] hub 4-0:1.0: USB hub found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.528720] hub 4-0:1.0: 3 ports detected
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.528762] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.528770] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.528789] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.528815] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.588683] usb usb5: configuration #1 chosen from 1 choice
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.588701] hub 5-0:1.0: USB hub found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.588708] hub 5-0:1.0: 3 ports detected
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.588742] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.588749] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.588769] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.588783] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.648670] usb usb6: configuration #1 chosen from 1 choice
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.648688] hub 6-0:1.0: USB hub found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.648695] hub 6-0:1.0: 3 ports detected
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.648731] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.648740] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.648763] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.648777] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.708664] usb usb7: configuration #1 chosen from 1 choice
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.708680] hub 7-0:1.0: USB hub found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.708689] hub 7-0:1.0: 2 ports detected
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.708722] uhci_hcd: USB Universal Host Controller Interface driver
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.708766] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.708768] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.708901] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.708965] mice: PS/2 mouse device common for all mice
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709044] rtc_cmos 00:05: RTC can wake from S4
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709074] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709106] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709176] device-mapper: uevent: version 1.0.3
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709261] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709309] device-mapper: multipath: version 1.1.0 loaded
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709311] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709388] EISA: Probing bus 0 at eisa.0
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709405] Cannot allocate resource for EISA slot 4
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709420] EISA: Detected 0 cards.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709470] cpuidle: using governor ladder
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709472] cpuidle: using governor menu
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709776] TCP cubic registered
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.709882] NET: Registered protocol family 10
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.710223] lo: Disabled Privacy Extensions
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.710472] NET: Registered protocol family 17
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.710493] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.710518] powernow-k8:    0 : pstate 0 (2700 MHz)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.710520] powernow-k8:    1 : pstate 1 (1350 MHz)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.739688] isapnp: No Plug & Play device found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.739729] Using IPI No-Shortcut mode
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.739815] registered taskstats version 1
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.740091]   Magic number: 2:632:948
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.740105] tty tty5: hash matches
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.740152] rtc_cmos 00:05: setting system clock to 2010-07-11 18:54:45 UTC (1278874485)
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.740155] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.740157] EDD information not available.
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.740196] Freeing unused kernel memory: 660k freed
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.740501] Write protecting the kernel text: 4680k
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.740529] Write protecting the kernel read-only data: 1840k
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.744821] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.752364] udev: starting version 151
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.780695] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.802681] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.802686] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.808345] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.808362] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.809045] eth0: RTL8168c/8111c at 0xf8092000, 00:24:1d:2a:40:65, XID 1c4000c0 IRQ 27
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.811866] scsi0 : ahci
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.827880] scsi1 : ahci
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.833972] scsi2 : ahci
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.835472] scsi3 : ahci
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.835587] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.835591] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.835594] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.835598] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.835801] scsi4 : pata_atiixp
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.835880] scsi5 : pata_atiixp
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.836707] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.836710] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Jul 11 18:54:56 ubuntu-desktop kernel: [    0.944596] usb 3-2: new low speed USB device using ohci_hcd and address 2
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.083135] usb 3-2: configuration #1 chosen from 1 choice
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.112069] ata2: SATA link down (SStatus 0 SControl 300)
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.160021] ata4: SATA link down (SStatus 0 SControl 300)
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.276014] ata1: applying SB600 PMP SRST workaround and retrying
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.276032] ata3: applying SB600 PMP SRST workaround and retrying
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.440021] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.440042] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.441627] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.441730] ata1.00: ATA-8: WDC WD5000AAKS-22A7B2, 01.03B01, max UDMA/133
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.441733] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.442687] ata1.00: configured for UDMA/133
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.444126] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100, ATAPI AN
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.448429] ata3.00: configured for UDMA/100
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.456099] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 01.0 PQ: 0 ANSI: 5
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.456224] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.456307] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.456338] sd 0:0:0:0: [sda] Write Protect is off
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.456354] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.456451]  sda: sda1 sda2 sda3 sda4 <
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.475350] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.484737]  sda5 sda6 >
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.484973] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.496272] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.496275] Uniform CD-ROM driver Revision: 3.20
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.496374] sr 2:0:0:0: Attached scsi generic sg1 type 5
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.667400] usbcore: registered new interface driver hiddev
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.671665] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.671736] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:12.0-2/input0
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.671759] usbcore: registered new interface driver usbhid
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.671761] usbhid: v2.6:USB HID core driver
Jul 11 18:54:56 ubuntu-desktop kernel: [    1.994399] EXT4-fs (sda3): mounted filesystem with ordered data mode
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.362765] udev: starting version 151
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.428758] Adding 1952760k swap on /dev/sda5.  Priority:-1 extents:1 across:1952760k 
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.443056] Linux agpgart interface v0.103
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.448256] vga16fb: mapped to 0xc00a0000
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.448307] fb0: VGA16 VGA frame buffer device
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.507893] type=1505 audit(1278885294.264:2):  operation="profile_load" pid=597 name="/sbin/dhclient3"
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.508100] type=1505 audit(1278885294.264:3):  operation="profile_load" pid=597 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.508215] type=1505 audit(1278885294.264:4):  operation="profile_load" pid=597 name="/usr/lib/connman/scripts/dhclient-script"
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.554767] nvidia: module license 'NVIDIA' taints kernel.
Jul 11 18:54:56 ubuntu-desktop kernel: [    9.554771] Disabling lock debugging due to kernel taint
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.243434] kjournald starting.  Commit interval 5 seconds
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.243679] EXT3 FS on sda6, internal journal
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.243683] EXT3-fs: mounted filesystem with ordered data mode.
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.426730] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.438336] lp: driver loaded but no devices found
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.487074] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.516731] parport_pc 00:09: reported by Plug and Play ACPI
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.516785] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.677221] cfg80211: Calling CRDA to update world regulatory domain
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.697680] ath5k 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.697713] ath5k 0000:03:06.0: registered as 'phy0'
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.709371] Console: switching to colour frame buffer device 80x30
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.718044] ppdev: user-space parallel port driver
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.718599] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.718612] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.719308] NVRM: loading NVIDIA UNIX x86 Kernel Module  256.35  Wed Jun 16 18:57:17 PDT 2010
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.725359] cfg80211: World regulatory domain updated:
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.725361]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.725364]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.725367]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.725369]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.725371]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.725373]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.740216] lp0: using parport0 (interrupt-driven).
Jul 11 18:54:56 ubuntu-desktop kernel: [   10.772800] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.303719] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.303811] cfg80211: Calling CRDA for country: CN
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.306216] cfg80211: Regulatory domain changed to country: CN
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.306219]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.306222]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.306224]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.870144] type=1505 audit(1278885296.627:5):  operation="profile_load" pid=890 name="/usr/share/gdm/guest-session/Xsession"
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.871243] type=1505 audit(1278885296.627:6):  operation="profile_replace" pid=891 name="/sbin/dhclient3"
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.871460] type=1505 audit(1278885296.627:7):  operation="profile_replace" pid=891 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.871582] type=1505 audit(1278885296.627:8):  operation="profile_replace" pid=891 name="/usr/lib/connman/scripts/dhclient-script"
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.873739] type=1505 audit(1278885296.631:9):  operation="profile_load" pid=892 name="/usr/bin/evince"
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.876364] type=1505 audit(1278885296.635:10):  operation="profile_load" pid=892 name="/usr/bin/evince-previewer"
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.878014] type=1505 audit(1278885296.635:11):  operation="profile_load" pid=892 name="/usr/bin/evince-thumbnailer"
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.947328] r8169: eth0: link down
Jul 11 18:54:56 ubuntu-desktop kernel: [   11.947506] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 11 18:54:56 ubuntu-desktop kernel: [   12.054294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 11 18:55:08 ubuntu-desktop kernel: [   24.136337] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 11 18:55:12 ubuntu-desktop kernel: [   27.947854] padlock: VIA PadLock not detected.

```

/var/log/dmesg 
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 (Ubuntu 2.6.32-24.38-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 00007FF00000 mask FFFFFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37858000 - 37fef3be
[    0.000000] Allocated new RAMDISK: 008e0000 - 010773be
[    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fef3bd to 008e0000 - 010773bd
[    0.000000] ACPI: RSDP 000f70e0 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 7fee3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 7fee3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 7fee30c0 042A8 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 7fee0000 00040
[    0.000000] ACPI: SSDT 7fee7440 007BA (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 7fee7c00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 7fee7c40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 7fee7380 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df0fe]              BRK ==> [00008dc000 - 00008df0fe]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e0000 - 00010773be]      NEW RAMDISK ==> [00008e0000 - 00010773be]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f56f0] f56f0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523899
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c1079000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294356 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:60100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519805
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=3d66cdf6-9da5-4918-b098-d88b6d937353 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10480000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
[    0.000000] Memory: 2050904k/2096000k available (4679k kernel code, 43552k reserved, 2116k data, 660k init, 1186696k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d23 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d23   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2719.634 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5439.26 BogoMIPS (lpj=10878536)
[    0.004018] Security Framework initialized
[    0.004034] AppArmor: AppArmor initialized
[    0.004040] Mount-cache hash table entries: 512
[    0.004131] Initializing cgroup subsys ns
[    0.004134] Initializing cgroup subsys cpuacct
[    0.004137] Initializing cgroup subsys memory
[    0.004143] Initializing cgroup subsys devices
[    0.004145] Initializing cgroup subsys freezer
[    0.004146] Initializing cgroup subsys net_cls
[    0.004160] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004162] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004164] CPU: Physical Processor ID: 0
[    0.004165] CPU: Processor Core ID: 0
[    0.004168] mce: CPU supports 6 MCE banks
[    0.004176] using C1E aware idle routine
[    0.004181] Performance Events: AMD PMU driver.
[    0.004186] ... version:                0
[    0.004187] ... bit width:              48
[    0.004188] ... generic registers:      4
[    0.004190] ... value mask:             0000ffffffffffff
[    0.004192] ... max period:             00007fffffffffff
[    0.004193] ... fixed-purpose events:   0
[    0.004195] ... event mask:             000000000000000f
[    0.004198] Checking 'hlt' instruction... OK.
[    0.021775] ACPI: Core revision 20090903
[    0.028025] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028033] ftrace: allocating 21780 entries in 43 pages
[    0.032059] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032566] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072758] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.160101] CPU1: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.160111] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164011] Brought up 2 CPUs
[    0.164013] Total of 2 processors activated (10877.53 BogoMIPS).
[    0.164408] CPU0 attaching sched-domain:
[    0.164410]  domain 0: span 0-1 level MC
[    0.164412]   groups: 0 1
[    0.164417] CPU1 attaching sched-domain:
[    0.164419]  domain 0: span 0-1 level MC
[    0.164420]   groups: 1 0
[    0.164482] devtmpfs: initialized
[    0.164482] regulator: core version 0.5
[    0.164482] Time: 18:54:44  Date: 07/11/10
[    0.164482] NET: Registered protocol family 16
[    0.164482] EISA bus registered
[    0.164482] Trying to unpack rootfs image as initramfs...
[    0.164482] ACPI: bus type pci registered
[    0.164482] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164482] PCI: MCFG area at e0000000 reserved in E820
[    0.164482] PCI: Using MMCONFIG for extended config space
[    0.164482] PCI: Using configuration type 1 for base access
[    0.168073] bio: create slab <bio-0> at 0
[    0.168494] ACPI: EC: Look up EC in DSDT
[    0.174441] ACPI: Interpreter enabled
[    0.174453] ACPI: (supports S0 S3 S4 S5)
[    0.174474] ACPI: Using IOAPIC for interrupt routing
[    0.177819] ACPI: No dock devices found.
[    0.177916] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.177983] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.177986] pci 0000:00:02.0: PME# disabled
[    0.178018] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.178020] pci 0000:00:06.0: PME# disabled
[    0.178073] pci 0000:00:11.0: reg 10 io port: [0xff00-0xff07]
[    0.178080] pci 0000:00:11.0: reg 14 io port: [0xfe00-0xfe03]
[    0.178086] pci 0000:00:11.0: reg 18 io port: [0xfd00-0xfd07]
[    0.178093] pci 0000:00:11.0: reg 1c io port: [0xfc00-0xfc03]
[    0.178100] pci 0000:00:11.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.178106] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f3ff]
[    0.178124] pci 0000:00:11.0: set SATA to AHCI mode
[    0.178168] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.178221] pci 0000:00:12.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.178291] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe02c000-0xfe02c0ff]
[    0.178342] pci 0000:00:12.2: supports D1 D2
[    0.178344] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.178348] pci 0000:00:12.2: PME# disabled
[    0.178378] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.178431] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02a000-0xfe02afff]
[    0.178501] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe029000-0xfe0290ff]
[    0.178552] pci 0000:00:13.2: supports D1 D2
[    0.178553] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.178557] pci 0000:00:13.2: PME# disabled
[    0.178670] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.178677] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.178683] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.178689] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.178695] pci 0000:00:14.1: reg 20 io port: [0xfa00-0xfa0f]
[    0.178759] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe024000-0xfe027fff]
[    0.178800] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.178804] pci 0000:00:14.2: PME# disabled
[    0.178906] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe028000-0xfe028fff]
[    0.179035] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.179043] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.179051] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.179056] pci 0000:01:00.0: reg 24 io port: [0xef00-0xef7f]
[    0.179061] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
[    0.179131] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.179134] pci 0000:00:02.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    0.179137] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.179170] pci 0000:02:00.0: reg 10 io port: [0xde00-0xdeff]
[    0.179184] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfdfff000-0xfdffffff]
[    0.179194] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdfe0000-0xfdfeffff]
[    0.179201] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.179228] pci 0000:02:00.0: supports D1 D2
[    0.179230] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.179234] pci 0000:02:00.0: PME# disabled
[    0.179291] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
[    0.179293] pci 0000:00:06.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.179297] pci 0000:00:06.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.179348] pci 0000:03:06.0: reg 10 32bit mmio: [0xfdef0000-0xfdefffff]
[    0.179454] pci 0000:00:14.4: transparent bridge
[    0.179458] pci 0000:00:14.4: bridge io port: [0xc000-0xcfff]
[    0.179462] pci 0000:00:14.4: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.179466] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.179477] pci_bus 0000:00: on NUMA node 0
[    0.179480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.179660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.179713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.179758] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.196004] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.196075] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.196144] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.196212] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.196280] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.196347] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.196416] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.196484] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.196575] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.196577] vgaarb: loaded
[    0.196667] SCSI subsystem initialized
[    0.196749] libata version 3.00 loaded.
[    0.196796] usbcore: registered new interface driver usbfs
[    0.196805] usbcore: registered new interface driver hub
[    0.196823] usbcore: registered new device driver usb
[    0.196906] ACPI: WMI: Mapper loaded
[    0.196908] PCI: Using ACPI for IRQ routing
[    0.197039] NetLabel: Initializing
[    0.197040] NetLabel:  domain hash size = 128
[    0.197042] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.197052] NetLabel:  unlabeled traffic allowed by default
[    0.197079] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.197083] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.199113] Switching to clocksource tsc
[    0.199293] AppArmor: AppArmor Filesystem Enabled
[    0.199293] pnp: PnP ACPI init
[    0.199293] ACPI: bus type pnp registered
[    0.199391] pnp: PnP ACPI: found 13 devices
[    0.199393] ACPI: ACPI bus type pnp unregistered
[    0.199396] PnPBIOS: Disabled by ACPI PNP
[    0.199405] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.199407] system 00:01: ioport range 0x220-0x225 has been reserved
[    0.199409] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.199413] system 00:02: ioport range 0x4100-0x411f has been reserved
[    0.199415] system 00:02: ioport range 0x228-0x22f has been reserved
[    0.199417] system 00:02: ioport range 0x238-0x23f has been reserved
[    0.199420] system 00:02: ioport range 0x40b-0x40b has been reserved
[    0.199422] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.199424] system 00:02: ioport range 0xc00-0xc01 has been reserved
[    0.199426] system 00:02: ioport range 0xc14-0xc14 has been reserved
[    0.199428] system 00:02: ioport range 0xc50-0xc52 has been reserved
[    0.199430] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[    0.199432] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[    0.199434] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[    0.199436] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[    0.199438] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[    0.199440] system 00:02: ioport range 0x4000-0x40fe has been reserved
[    0.199442] system 00:02: ioport range 0x4210-0x4217 has been reserved
[    0.199445] system 00:02: ioport range 0xb00-0xb0f has been reserved
[    0.199447] system 00:02: ioport range 0xb10-0xb1f has been reserved
[    0.199449] system 00:02: ioport range 0xb20-0xb3f has been reserved
[    0.199454] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.199459] system 00:0c: iomem range 0xce000-0xcffff has been reserved
[    0.199461] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.199463] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.199465] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.199468] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.199470] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.199472] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.199475] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
[    0.199477] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.199480] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.199482] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.234123] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.234126] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.234129] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
[    0.234132] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.234136] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.234138] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
[    0.234141] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.234144] pci 0000:00:06.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.234147] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.234150] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.234155] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
[    0.234159] pci 0000:00:14.4:   PREFETCH window: 0xfdd00000-0xfddfffff
[    0.234172] pci 0000:00:02.0: setting latency timer to 64
[    0.234176] pci 0000:00:06.0: setting latency timer to 64
[    0.234184] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.234186] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.234188] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.234190] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbffffff]
[    0.234192] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.234195] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.234197] pci_bus 0000:02: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.234199] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.234201] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.234203] pci_bus 0000:03: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.234204] pci_bus 0000:03: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.234206] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.234208] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.234239] NET: Registered protocol family 2
[    0.234315] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.234572] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.235113] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.235379] TCP: Hash tables configured (established 131072 bind 65536)
[    0.235381] TCP reno registered
[    0.235448] NET: Registered protocol family 1
[    0.372734] pci 0000:01:00.0: Boot video device
[    0.372918] cpufreq-nforce2: No nForce2 chipset.
[    0.372940] Scanning for low memory corruption every 60 seconds
[    0.373024] audit: initializing netlink socket (disabled)
[    0.373035] type=2000 audit(1278874484.372:1): initialized
[    0.379683] highmem bounce pool size: 64 pages
[    0.379687] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.380744] VFS: Disk quotas dquot_6.5.2
[    0.380787] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.381202] fuse init (API version 7.13)
[    0.381259] msgmni has been set to 1690
[    0.381430] alg: No test for stdrng (krng)
[    0.381471] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.381474] io scheduler noop registered
[    0.381475] io scheduler anticipatory registered
[    0.381477] io scheduler deadline registered
[    0.381506] io scheduler cfq registered (default)
[    0.381605]   alloc irq_desc for 25 on node -1
[    0.381607]   alloc kstat_irqs on node -1
[    0.381614] pcieport 0000:00:02.0: irq 25 for MSI/MSI-X
[    0.381620] pcieport 0000:00:02.0: setting latency timer to 64
[    0.381668]   alloc irq_desc for 26 on node -1
[    0.381670]   alloc kstat_irqs on node -1
[    0.381673] pcieport 0000:00:06.0: irq 26 for MSI/MSI-X
[    0.381677] pcieport 0000:00:06.0: setting latency timer to 64
[    0.381712] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.381730] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.381800] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.381804] ACPI: Power Button [PWRB]
[    0.381844] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.381846] ACPI: Power Button [PWRF]
[    0.382074] processor LNXCPU:00: registered as cooling_device0
[    0.382101] processor LNXCPU:01: registered as cooling_device1
[    0.382509] Freeing initrd memory: 7772k freed
[    0.384739] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.384855] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.385145] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.385820] isapnp: Scanning for PnP cards...
[    0.385908] brd: module loaded
[    0.386207] loop: module loaded
[    0.386264] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.386372]   alloc irq_desc for 16 on node -1
[    0.386374]   alloc kstat_irqs on node -1
[    0.386384] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.386629] Fixed MDIO Bus: probed
[    0.386652] PPP generic driver version 2.4.2
[    0.386675] tun: Universal TUN/TAP device driver, 1.6
[    0.386676] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.386727] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.386742]   alloc irq_desc for 17 on node -1
[    0.386743]   alloc kstat_irqs on node -1
[    0.386750] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.386761] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.386781] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.386802] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    0.386815] ehci_hcd 0000:00:12.2: debug port 1
[    0.386846] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    0.396699] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.396763] usb usb1: configuration #1 chosen from 1 choice
[    0.396784] hub 1-0:1.0: USB hub found
[    0.396791] hub 1-0:1.0: 6 ports detected
[    0.396839]   alloc irq_desc for 19 on node -1
[    0.396840]   alloc kstat_irqs on node -1
[    0.396847] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.396854] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.396875] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.396892] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    0.396905] ehci_hcd 0000:00:13.2: debug port 1
[    0.396929] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    0.408694] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.408740] usb usb2: configuration #1 chosen from 1 choice
[    0.408757] hub 2-0:1.0: USB hub found
[    0.408762] hub 2-0:1.0: 6 ports detected
[    0.408809] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.408819] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.408826] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.408849] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.408875] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    0.468709] usb usb3: configuration #1 chosen from 1 choice
[    0.468726] hub 3-0:1.0: USB hub found
[    0.468733] hub 3-0:1.0: 3 ports detected
[    0.468767] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.468775] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.468794] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.468808] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    0.528697] usb usb4: configuration #1 chosen from 1 choice
[    0.528713] hub 4-0:1.0: USB hub found
[    0.528720] hub 4-0:1.0: 3 ports detected
[    0.528754]   alloc irq_desc for 18 on node -1
[    0.528756]   alloc kstat_irqs on node -1
[    0.528762] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.528770] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.528789] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.528815] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    0.588683] usb usb5: configuration #1 chosen from 1 choice
[    0.588701] hub 5-0:1.0: USB hub found
[    0.588708] hub 5-0:1.0: 3 ports detected
[    0.588742] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.588749] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.588769] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.588783] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    0.648670] usb usb6: configuration #1 chosen from 1 choice
[    0.648688] hub 6-0:1.0: USB hub found
[    0.648695] hub 6-0:1.0: 3 ports detected
[    0.648731] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.648740] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    0.648763] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    0.648777] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    0.708664] usb usb7: configuration #1 chosen from 1 choice
[    0.708680] hub 7-0:1.0: USB hub found
[    0.708689] hub 7-0:1.0: 2 ports detected
[    0.708722] uhci_hcd: USB Universal Host Controller Interface driver
[    0.708766] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.708768] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.708901] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.708965] mice: PS/2 mouse device common for all mice
[    0.709044] rtc_cmos 00:05: RTC can wake from S4
[    0.709074] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.709106] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.709176] device-mapper: uevent: version 1.0.3
[    0.709261] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.709309] device-mapper: multipath: version 1.1.0 loaded
[    0.709311] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.709388] EISA: Probing bus 0 at eisa.0
[    0.709405] Cannot allocate resource for EISA slot 4
[    0.709420] EISA: Detected 0 cards.
[    0.709470] cpuidle: using governor ladder
[    0.709472] cpuidle: using governor menu
[    0.709776] TCP cubic registered
[    0.709882] NET: Registered protocol family 10
[    0.710223] lo: Disabled Privacy Extensions
[    0.710472] NET: Registered protocol family 17
[    0.710493] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
[    0.710518] powernow-k8:    0 : pstate 0 (2700 MHz)
[    0.710520] powernow-k8:    1 : pstate 1 (1350 MHz)
[    0.739688] isapnp: No Plug & Play device found
[    0.739729] Using IPI No-Shortcut mode
[    0.739804] PM: Resume from disk failed.
[    0.739815] registered taskstats version 1
[    0.740091]   Magic number: 2:632:948
[    0.740105] tty tty5: hash matches
[    0.740152] rtc_cmos 00:05: setting system clock to 2010-07-11 18:54:45 UTC (1278874485)
[    0.740155] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.740157] EDD information not available.
[    0.740196] Freeing unused kernel memory: 660k freed
[    0.740501] Write protecting the kernel text: 4680k
[    0.740529] Write protecting the kernel read-only data: 1840k
[    0.744821] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.752364] udev: starting version 151
[    0.780663] ahci 0000:00:11.0: version 3.0
[    0.780682]   alloc irq_desc for 22 on node -1
[    0.780684]   alloc kstat_irqs on node -1
[    0.780695] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.802681] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.802686] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.808345] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.808362] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.808398] r8169 0000:02:00.0: setting latency timer to 64
[    0.808431]   alloc irq_desc for 27 on node -1
[    0.808432]   alloc kstat_irqs on node -1
[    0.808444] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    0.809045] eth0: RTL8168c/8111c at 0xf8092000, 00:24:1d:2a:40:65, XID 1c4000c0 IRQ 27
[    0.811866] scsi0 : ahci
[    0.827880] scsi1 : ahci
[    0.833972] scsi2 : ahci
[    0.835472] scsi3 : ahci
[    0.835587] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    0.835591] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    0.835594] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    0.835598] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    0.835801] scsi4 : pata_atiixp
[    0.835880] scsi5 : pata_atiixp
[    0.836707] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    0.836710] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    0.944596] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.083135] usb 3-2: configuration #1 chosen from 1 choice
[    1.112069] ata2: SATA link down (SStatus 0 SControl 300)
[    1.160021] ata4: SATA link down (SStatus 0 SControl 300)
[    1.276012] ata1: softreset failed (device not ready)
[    1.276014] ata1: applying SB600 PMP SRST workaround and retrying
[    1.276030] ata3: softreset failed (device not ready)
[    1.276032] ata3: applying SB600 PMP SRST workaround and retrying
[    1.440021] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.440042] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.441627] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.441730] ata1.00: ATA-8: WDC WD5000AAKS-22A7B2, 01.03B01, max UDMA/133
[    1.441733] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.442687] ata1.00: configured for UDMA/133
[    1.444126] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100, ATAPI AN
[    1.448429] ata3.00: configured for UDMA/100
[    1.456099] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 01.0 PQ: 0 ANSI: 5
[    1.456224] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.456307] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.456338] sd 0:0:0:0: [sda] Write Protect is off
[    1.456340] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.456354] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.456451]  sda: sda1 sda2 sda3 sda4 <
[    1.475350] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
[    1.484737]  sda5 sda6 >
[    1.484973] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.496272] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.496275] Uniform CD-ROM driver Revision: 3.20
[    1.496333] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.496374] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.667400] usbcore: registered new interface driver hiddev
[    1.671665] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4
[    1.671736] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:12.0-2/input0
[    1.671759] usbcore: registered new interface driver usbhid
[    1.671761] usbhid: v2.6:USB HID core driver
[    1.994399] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    9.362765] udev: starting version 151
[    9.428758] Adding 1952760k swap on /dev/sda5.  Priority:-1 extents:1 across:1952760k 
[    9.443056] Linux agpgart interface v0.103
[    9.448252] vga16fb: initializing
[    9.448256] vga16fb: mapped to 0xc00a0000
[    9.448307] fb0: VGA16 VGA frame buffer device
[    9.507893] type=1505 audit(1278885294.264:2):  operation="profile_load" pid=597 name="/sbin/dhclient3"
[    9.508100] type=1505 audit(1278885294.264:3):  operation="profile_load" pid=597 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.508215] type=1505 audit(1278885294.264:4):  operation="profile_load" pid=597 name="/usr/lib/connman/scripts/dhclient-script"
[    9.554767] nvidia: module license 'NVIDIA' taints kernel.
[    9.554771] Disabling lock debugging due to kernel taint
[   10.243434] kjournald starting.  Commit interval 5 seconds
[   10.243679] EXT3 FS on sda6, internal journal
[   10.243683] EXT3-fs: mounted filesystem with ordered data mode.
[   10.426730] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   10.438336] lp: driver loaded but no devices found
[   10.487074] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.516731] parport_pc 00:09: reported by Plug and Play ACPI
[   10.516785] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.677221] cfg80211: Calling CRDA to update world regulatory domain
[   10.697668]   alloc irq_desc for 20 on node -1
[   10.697670]   alloc kstat_irqs on node -1
[   10.697680] ath5k 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   10.697713] ath5k 0000:03:06.0: registered as 'phy0'
[   10.709371] Console: switching to colour frame buffer device 80x30
[   10.718044] ppdev: user-space parallel port driver
[   10.718599] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.718607] nvidia 0000:01:00.0: setting latency timer to 64
[   10.718612] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   10.719308] NVRM: loading NVIDIA UNIX x86 Kernel Module  256.35  Wed Jun 16 18:57:17 PDT 2010
[   10.725359] cfg80211: World regulatory domain updated:
[   10.725361]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.725364]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.725367]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.725369]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.725371]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.725373]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.740216] lp0: using parport0 (interrupt-driven).
[   10.772800] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[   11.298577] ath: EEPROM regdomain: 0x809c
[   11.298580] ath: EEPROM indicates we should expect a country code
[   11.298582] ath: doing EEPROM country->regdmn map search
[   11.298584] ath: country maps to regdmn code: 0x52
[   11.298586] ath: Country alpha2 being used: CN
[   11.298587] ath: Regpair used: 0x52
[   11.303134] phy0: Selected rate control algorithm 'minstrel'
[   11.303719] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   11.303811] cfg80211: Calling CRDA for country: CN
[   11.306216] cfg80211: Regulatory domain changed to country: CN
[   11.306219]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.306222]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   11.306224]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[   11.870144] type=1505 audit(1278885296.627:5):  operation="profile_load" pid=890 name="/usr/share/gdm/guest-session/Xsession"
[   11.871243] type=1505 audit(1278885296.627:6):  operation="profile_replace" pid=891 name="/sbin/dhclient3"
[   11.871460] type=1505 audit(1278885296.627:7):  operation="profile_replace" pid=891 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.871582] type=1505 audit(1278885296.627:8):  operation="profile_replace" pid=891 name="/usr/lib/connman/scripts/dhclient-script"
[   11.873739] type=1505 audit(1278885296.631:9):  operation="profile_load" pid=892 name="/usr/bin/evince"
[   11.876364] type=1505 audit(1278885296.635:10):  operation="profile_load" pid=892 name="/usr/bin/evince-previewer"
[   11.878014] type=1505 audit(1278885296.635:11):  operation="profile_load" pid=892 name="/usr/bin/evince-thumbnailer"
[   11.947328] r8169: eth0: link down
[   11.947506] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.054294] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

