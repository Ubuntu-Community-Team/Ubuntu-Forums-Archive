---
title: "No window decorator, and ATI driver trouble, after a fresh install"
date: 2013-03-30
forum: Ubuntu Development Version
---

### Post by gioby on 2013-03-30
I've just installed the lastest Raring daily snapshot (28/3/2013), but I have problems related to windows decorator and ATI drivers
My computer is a HP Pavilion dv3 laptop, and my video card is an ATI Mobility Radeon HD 5400 Series.
I was able to fix a problem related to the fglrx drivers, but I am not able to have window decorators in Unity.

**Problem 1: Could not find fglrx driver after first boot**

The installation went well, fast and without errors. However, after the first boot, Xorg could not load, and I was faced with a black screen and a window saying that the Video driver could not be configured automatically.
Unfortunately, the error window didn't respond to my keyboard, so I wasn't even able to use the Recovery mode.
So, I switched to another tty, and noticed that the Xorg log file was complaining about not being able to load the fglrx module.

Output of /var/log/Xorg.1.log: 

```
[   203.537] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[   203.543] X Protocol Version 11, Revision 0
[   203.545] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[   203.547] Current Operating System: Linux trellos 3.8.0-15-generic #25-Ubuntu SMP Wed Mar 27 19:19:30 UTC 2013 x86_64
[   203.547] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-15-generic root=UUID=f62eaf4f-df31-4a72-bc20-c71d52a98f2a ro quiet splash vt.handoff=7
[   203.551] Build Date: 26 March 2013  03:26:34PM
[   203.553] xorg-server 2:1.13.3-0ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[   203.555] Current version of pixman: 0.28.2
[   203.558]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   203.558] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   203.566] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Mar 30 11:49:50 2013
[   203.568] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   203.569] (==) No Layout section.  Using the first Screen section.
[   203.569] (==) No screen section available. Using defaults.
[   203.569] (**) |-->Screen "Default Screen Section" (0)
[   203.569] (**) |   |-->Monitor "<default monitor>"
[   203.569] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   203.569] (==) Automatically adding devices
[   203.569] (==) Automatically enabling devices
[   203.569] (==) Automatically adding GPU devices
[   203.569] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   203.569]     Entry deleted from font path.
[   203.569] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   203.569]     Entry deleted from font path.
[   203.569] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   203.569]     Entry deleted from font path.
[   203.569] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   203.569]     Entry deleted from font path.
[   203.569] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   203.569]     Entry deleted from font path.
[   203.569] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   203.569]     Entry deleted from font path.
[   203.569] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   203.569] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   203.569] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   203.569] (II) Loader magic: 0x7fbacd0fad00
[   203.569] (II) Module ABI versions:
[   203.569]     X.Org ANSI C Emulation: 0.4
[   203.569]     X.Org Video Driver: 13.1
[   203.569]     X.Org XInput driver : 18.0
[   203.569]     X.Org Server Extension : 7.0
[   203.569] (II) config/udev: Adding drm device (/dev/dri/card0)
[   203.570] (II) config/udev: Adding drm device (/dev/dri/card1)
[   203.572] (--) PCI:*(0:0:2:0) 8086:0046:103c:1433 rev 2, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00004050/8
[   203.572] (--) PCI: (0:1:0:0) 1002:68e0:103c:1433 rev 0, Mem @ 0xa0000000/268435456, 0xc4400000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[   203.572] (II) Open ACPI successful (/var/run/acpid.socket)
[   203.574] Initializing built-in extension Generic Event Extension
[   203.576] Initializing built-in extension SHAPE
[   203.578] Initializing built-in extension MIT-SHM
[   203.580] Initializing built-in extension XInputExtension
[   203.581] Initializing built-in extension XTEST
[   203.583] Initializing built-in extension BIG-REQUESTS
[   203.585] Initializing built-in extension SYNC
[   203.587] Initializing built-in extension XKEYBOARD
[   203.588] Initializing built-in extension XC-MISC
[   203.590] Initializing built-in extension SECURITY
[   203.592] Initializing built-in extension XINERAMA
[   203.593] Initializing built-in extension XFIXES
[   203.595] Initializing built-in extension RENDER
[   203.596] Initializing built-in extension RANDR
[   203.598] Initializing built-in extension COMPOSITE
[   203.600] Initializing built-in extension DAMAGE
[   203.601] Initializing built-in extension MIT-SCREEN-SAVER
[   203.602] Initializing built-in extension DOUBLE-BUFFER
[   203.604] Initializing built-in extension RECORD
[   203.605] Initializing built-in extension DPMS
[   203.606] Initializing built-in extension X-Resource
[   203.608] Initializing built-in extension XVideo
[   203.609] Initializing built-in extension XVideo-MotionCompensation
[   203.610] Initializing built-in extension SELinux
[   203.611] Initializing built-in extension XFree86-VidModeExtension
[   203.612] Initializing built-in extension XFree86-DGA
[   203.613] Initializing built-in extension XFree86-DRI
[   203.614] Initializing built-in extension DRI2
[   203.615] (II) LoadModule: "glx"
[   203.615] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   203.615] (II) Module glx: vendor="X.Org Foundation"
[   203.615]     compiled for 1.13.3, module version = 1.0.0
[   203.615]     ABI class: X.Org Server Extension, version 7.0
[   203.615] (==) AIGLX enabled
[   203.616] Loading extension GLX
[   203.616] (==) Matched intel as autoconfigured driver 0
[   203.616] (==) Matched fglrx as autoconfigured driver 1
[   203.616] (==) Matched ati as autoconfigured driver 2
[   203.616] (==) Matched intel as autoconfigured driver 3
[   203.616] (==) Matched vesa as autoconfigured driver 4
[   203.616] (==) Matched modesetting as autoconfigured driver 5
[   203.616] (==) Matched fbdev as autoconfigured driver 6
[   203.616] (==) Assigned the driver to the xf86ConfigLayout
[   203.616] (II) LoadModule: "intel"
[   203.617] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   203.617] (II) Module intel: vendor="X.Org Foundation"
[   203.617]     compiled for 1.13.3, module version = 2.21.5
[   203.617]     Module class: X.Org Video Driver
[   203.617]     ABI class: X.Org Video Driver, version 13.1
[   203.617] (II) LoadModule: "fglrx"
[   203.617] (WW) Warning, couldn't open module fglrx
[   203.617] (II) UnloadModule: "fglrx"
[   203.617] (II) Unloading fglrx
[   203.617] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   203.617] (II) LoadModule: "ati"
[   203.618] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   203.618] (II) Module ati: vendor="X.Org Foundation"
[   203.618]     compiled for 1.13.3, module version = 7.1.0
[   203.618]     Module class: X.Org Video Driver
[   203.618]     ABI class: X.Org Video Driver, version 13.1
[   203.618] (II) LoadModule: "radeon"
[   203.618] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   203.618] (II) Module radeon: vendor="X.Org Foundation"
[   203.618]     compiled for 1.13.3, module version = 7.1.0
[   203.618]     Module class: X.Org Video Driver
[   203.618]     ABI class: X.Org Video Driver, version 13.1
[   203.618] (II) LoadModule: "vesa"
[   203.619] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   203.619] (II) Module vesa: vendor="X.Org Foundation"
[   203.619]     compiled for 1.12.99.902, module version = 2.3.2
[   203.619]     Module class: X.Org Video Driver
[   203.619]     ABI class: X.Org Video Driver, version 13.0
[   203.619] (II) LoadModule: "modesetting"
[   203.619] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   203.619] (II) Module modesetting: vendor="X.Org Foundation"
[   203.619]     compiled for 1.13.3, module version = 0.7.0
[   203.619]     Module class: X.Org Video Driver
[   203.619]     ABI class: X.Org Video Driver, version 13.1
[   203.619] (II) LoadModule: "fbdev"
[   203.619] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   203.620] (II) Module fbdev: vendor="X.Org Foundation"
[   203.620]     compiled for 1.12.99.902, module version = 0.4.3
[   203.620]     Module class: X.Org Video Driver
[   203.620]     ABI class: X.Org Video Driver, version 13.0
[   203.620] (==) Matched intel as autoconfigured driver 0
[   203.620] (==) Matched fglrx as autoconfigured driver 1
[   203.620] (==) Matched ati as autoconfigured driver 2
[   203.620] (==) Matched intel as autoconfigured driver 3
[   203.620] (==) Matched vesa as autoconfigured driver 4
[   203.620] (==) Matched modesetting as autoconfigured driver 5
[   203.620] (==) Matched fbdev as autoconfigured driver 6
[   203.620] (==) Assigned the driver to the xf86ConfigLayout
[   203.620] (II) LoadModule: "intel"
[   203.620] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   203.620] (II) Module intel: vendor="X.Org Foundation"
[   203.620]     compiled for 1.13.3, module version = 2.21.5
[   203.620]     Module class: X.Org Video Driver
[   203.620]     ABI class: X.Org Video Driver, version 13.1
[   203.620] (II) UnloadModule: "intel"
[   203.620] (II) Unloading intel
[   203.620] (II) Failed to load module "intel" (already loaded, 32698)
[   203.620] (II) LoadModule: "fglrx"
[   203.620] (WW) Warning, couldn't open module fglrx
[   203.620] (II) UnloadModule: "fglrx"
[   203.620] (II) Unloading fglrx
[   203.620] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   203.620] (II) LoadModule: "ati"
[   203.621] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   203.621] (II) Module ati: vendor="X.Org Foundation"
[   203.621]     compiled for 1.13.3, module version = 7.1.0
[   203.621]     Module class: X.Org Video Driver
[   203.621]     ABI class: X.Org Video Driver, version 13.1
[   203.621] (II) LoadModule: "vesa"
[   203.621] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   203.621] (II) Module vesa: vendor="X.Org Foundation"
[   203.621]     compiled for 1.12.99.902, module version = 2.3.2
[   203.621]     Module class: X.Org Video Driver
[   203.621]     ABI class: X.Org Video Driver, version 13.0
[   203.621] (II) UnloadModule: "vesa"
[   203.621] (II) Unloading vesa
[   203.621] (II) Failed to load module "vesa" (already loaded, 0)
[   203.621] (II) LoadModule: "modesetting"
[   203.621] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   203.621] (II) Module modesetting: vendor="X.Org Foundation"
[   203.621]     compiled for 1.13.3, module version = 0.7.0
[   203.621]     Module class: X.Org Video Driver
[   203.621]     ABI class: X.Org Video Driver, version 13.1
[   203.621] (II) UnloadModule: "modesetting"
[   203.621] (II) Unloading modesetting
[   203.621] (II) Failed to load module "modesetting" (already loaded, 0)
[   203.621] (II) LoadModule: "fbdev"
[   203.622] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   203.622] (II) Module fbdev: vendor="X.Org Foundation"
[   203.622]     compiled for 1.12.99.902, module version = 0.4.3
[   203.622]     Module class: X.Org Video Driver
[   203.622]     ABI class: X.Org Video Driver, version 13.0
[   203.622] (II) UnloadModule: "fbdev"
[   203.622] (II) Unloading fbdev
[   203.622] (II) Failed to load module "fbdev" (already loaded, 0)
[   203.622] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[   203.623] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[   203.628] (II) VESA: driver for VESA chipsets: vesa
[   203.628] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   203.628] (II) FBDEV: driver for framebuffer: fbdev
[   203.628] (--) using VT number 7

[   203.633] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.5-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[   203.633] (II) [KMS] Kernel modesetting enabled.
[   203.633] (WW) Falling back to old probe method for vesa
[   203.633] (WW) Falling back to old probe method for modesetting
[   203.633] (WW) Falling back to old probe method for fbdev
[   203.633] (II) Loading sub module "fbdevhw"
[   203.633] (II) LoadModule: "fbdevhw"
[   203.634] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   203.634] (II) Module fbdevhw: vendor="X.Org Foundation"
[   203.634]     compiled for 1.13.3, module version = 0.0.2
[   203.634]     ABI class: X.Org Video Driver, version 13.1
[   203.634] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   203.634] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   203.634] (==) intel(0): RGB weight 888
[   203.634] (==) intel(0): Default visual is TrueColor
[   203.634] (--) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[   203.635] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[   203.635] (**) intel(0): Framebuffer tiled
[   203.635] (**) intel(0): Pixmaps tiled
[   203.635] (**) intel(0): "Tear free" disabled
[   203.635] (**) intel(0): Forcing per-crtc-pixmaps? no
[   203.635] (II) intel(0): Output LVDS2 has no monitor section
[   203.635] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[   203.788] (II) intel(0): Output VGA2 has no monitor section
[   203.788] (II) intel(0): EDID for output LVDS2
[   203.788] (II) intel(0): Manufacturer: LGD  Model: 22c  Serial#: 0
[   203.788] (II) intel(0): Year: 2009  Week: 0
[   203.788] (II) intel(0): EDID Version: 1.3
[   203.788] (II) intel(0): Digital Display Input
[   203.788] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 17
[   203.788] (II) intel(0): Gamma: 2.20
[   203.788] (II) intel(0): No DPMS capabilities specified
[   203.788] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   203.788] (II) intel(0): First detailed timing is preferred mode
[   203.788] (II) intel(0): redX: 0.589 redY: 0.349   greenX: 0.337 greenY: 0.548
[   203.788] (II) intel(0): blueX: 0.155 blueY: 0.122   whiteX: 0.313 whiteY: 0.329
[   203.788] (II) intel(0): Manufacturer's mask: 0
[   203.788] (II) intel(0): Supported detailed timing:
[   203.788] (II) intel(0): clock: 69.3 MHz   Image Size:  294 x 166 mm
[   203.788] (II) intel(0): h_active: 1366  h_sync: 1398  h_sync_end 1446 h_blank_end 1462 h_border: 0
[   203.788] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 790 v_border: 0
[   203.788] (II) intel(0):  LG Display
[   203.788] (II) intel(0):  LP133WH1-TLA2
[   203.788] (II) intel(0): EDID (in hex):
[   203.788] (II) intel(0):     00ffffffffffff0030e42c0200000000
[   203.788] (II) intel(0):     00130103801d11780ad5d59659568c27
[   203.788] (II) intel(0):     1f505400000001010101010101010101
[   203.789] (II) intel(0):     010101010101121b5660500016302030
[   203.789] (II) intel(0):     360026a6100000190000000000000000
[   203.789] (II) intel(0):     00000000000000000000000000fe004c
[   203.789] (II) intel(0):     4720446973706c61790a2020000000fe
[   203.789] (II) intel(0):     004c503133335748312d544c41320002
[   203.789] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   203.789] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   203.790] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   203.790] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   203.790] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   203.790] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   203.790] (II) intel(0): Printing probed modes for output LVDS2
[   203.790] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1398 1446 1462  768 771 777 790 -hsync -vsync (47.4 kHz eP)
[   203.790] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[   203.790] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[   203.790] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[   203.790] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[   203.790] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[   203.790] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[   203.940] (II) intel(0): EDID for output VGA2
[   203.940] (II) intel(0): Manufacturer: GSM  Model: 57a3  Serial#: 25589
[   203.940] (II) intel(0): Year: 2010  Week: 4
[   203.940] (II) intel(0): EDID Version: 1.3
[   203.940] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[   203.940] (II) intel(0): Sync:  Separate  Composite
[   203.940] (II) intel(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[   203.940] (II) intel(0): Gamma: 2.20
[   203.940] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   203.940] (II) intel(0): First detailed timing is preferred mode
[   203.940] (II) intel(0): redX: 0.631 redY: 0.349   greenX: 0.341 greenY: 0.622
[   203.940] (II) intel(0): blueX: 0.152 blueY: 0.058   whiteX: 0.313 whiteY: 0.329
[   203.940] (II) intel(0): Supported established timings:
[   203.940] (II) intel(0): 720x400@70Hz
[   203.940] (II) intel(0): 640x480@60Hz
[   203.940] (II) intel(0): 640x480@75Hz
[   203.940] (II) intel(0): 800x600@60Hz
[   203.940] (II) intel(0): 800x600@75Hz
[   203.940] (II) intel(0): 1024x768@60Hz
[   203.940] (II) intel(0): 1024x768@75Hz
[   203.940] (II) intel(0): 1280x1024@75Hz
[   203.940] (II) intel(0): Manufacturer's mask: 0
[   203.940] (II) intel(0): Supported standard timings:
[   203.940] (II) intel(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   203.940] (II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   203.940] (II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[   203.940] (II) intel(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   203.940] (II) intel(0): Supported detailed timing:
[   203.940] (II) intel(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[   203.940] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   203.940] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   203.940] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 155 MHz
[   203.941] (II) intel(0): Monitor name: E2240
[   203.941] (II) intel(0): Serial No: 004TPZK0R589
[   203.941] (II) intel(0): EDID (in hex):
[   203.941] (II) intel(0):     00ffffffffffff001e6da357f5630000
[   203.941] (II) intel(0):     041401036c301b78ea9535a159579f27
[   203.941] (II) intel(0):     0e5054a54b00b3008180818f714f0101
[   203.941] (II) intel(0):     010101010101023a801871382d40582c
[   203.941] (II) intel(0):     4500dd0c1100001a000000fd00384b1e
[   203.941] (II) intel(0):     530f000a202020202020000000fc0045
[   203.941] (II) intel(0):     323234300a20202020202020000000ff
[   203.941] (II) intel(0):     0030303454505a4b30523538390a0053
[   203.941] (II) intel(0): Printing probed modes for output VGA2
[   203.941] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync -vsync (67.5 kHz eP)
[   203.941] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   203.941] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   203.941] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   203.941] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   203.941] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   203.941] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   203.941] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   203.941] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   203.941] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   203.941] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   203.941] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   203.941] (II) intel(0): Output LVDS2 connected
[   203.941] (II) intel(0): Output VGA2 connected
[   203.941] (II) intel(0): Using fuzzy aspect match for initial modes
[   203.941] (II) intel(0): Output LVDS2 using initial mode 1024x768
[   203.941] (II) intel(0): Output VGA2 using initial mode 1024x768
[   203.942] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   203.942] (==) intel(0): DPI set to (96, 96)
[   203.942] (II) Loading sub module "dri2"
[   203.942] (II) LoadModule: "dri2"
[   203.942] (II) Module "dri2" already built-in
[   203.942] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[   203.942] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   203.942] (==) RADEON(G0): Default visual is TrueColor
[   203.942] (==) RADEON(G0): RGB weight 888
[   203.942] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[   203.942] (--) RADEON(G0): Chipset: "ATI Mobility Radeon HD 5000 Series" (ChipID = 0x68e0)
[   203.942] (II) Loading sub module "dri2"
[   203.942] (II) LoadModule: "dri2"
[   203.942] (II) Module "dri2" already built-in
[   203.942] (II) Loading sub module "exa"
[   203.942] (II) LoadModule: "exa"
[   203.943] (II) Loading /usr/lib/xorg/modules/libexa.so
[   203.943] (II) Module exa: vendor="X.Org Foundation"
[   203.943]     compiled for 1.13.3, module version = 2.6.0
[   203.943]     ABI class: X.Org Video Driver, version 13.1
[   203.943] (II) RADEON(G0): KMS Color Tiling: enabled
[   203.943] (II) RADEON(G0): KMS Color Tiling 2D: enabled
[   203.943] (II) RADEON(G0): KMS Pageflipping: enabled
[   203.943] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[   203.946] (II) RADEON(G0): Output LVDS has no monitor section
[   203.949] (II) RADEON(G0): Output HDMI-0 has no monitor section
[   203.972] (II) RADEON(G0): Output VGA-0 has no monitor section
[   203.975] (II) RADEON(G0): EDID for output LVDS
[   203.975] (II) RADEON(G0): Printing probed modes for output LVDS
[   203.975] (II) RADEON(G0): Modeline "1366x768"x60.0   69.30  1366 1398 1446 1462  768 771 777 790 -hsync -vsync (47.4 kHz eP)
[   203.975] (II) RADEON(G0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[   203.975] (II) RADEON(G0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[   203.975] (II) RADEON(G0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   203.975] (II) RADEON(G0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   203.975] (II) RADEON(G0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[   203.975] (II) RADEON(G0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[   203.975] (II) RADEON(G0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   203.978] (II) RADEON(G0): EDID for output HDMI-0
[   204.004] (II) RADEON(G0): EDID for output VGA-0
[   204.004] (II) RADEON(G0): Output LVDS connected
[   204.004] (II) RADEON(G0): Output HDMI-0 disconnected
[   204.004] (II) RADEON(G0): Output VGA-0 disconnected
[   204.004] (II) RADEON(G0): Using exact sizes for initial modes
[   204.004] (II) RADEON(G0): Output LVDS using initial mode 1366x768
[   204.004] (II) RADEON(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   204.004] (II) RADEON(G0): mem size init: gart size :1fdef000 vram size: s:20000000 visible:1fba0000
[   204.004] (II) RADEON(G0): EXA: Driver will allow EXA pixmaps in VRAM
[   204.004] (==) RADEON(G0): DPI set to (96, 96)
[   204.004] (II) Loading sub module "fb"
[   204.004] (II) LoadModule: "fb"
[   204.005] (II) Loading /usr/lib/xorg/modules/libfb.so
[   204.005] (II) Module fb: vendor="X.Org Foundation"
[   204.005]     compiled for 1.13.3, module version = 1.0.0
[   204.005]     ABI class: X.Org ANSI C Emulation, version 0.4
[   204.005] (II) Loading sub module "ramdac"
[   204.005] (II) LoadModule: "ramdac"
[   204.005] (II) Module "ramdac" already built-in
[   204.005] (II) UnloadModule: "vesa"
[   204.005] (II) Unloading vesa
[   204.005] (II) UnloadModule: "modesetting"
[   204.005] (II) Unloading modesetting
[   204.005] (II) UnloadModule: "fbdev"
[   204.005] (II) Unloading fbdev
[   204.006] (II) UnloadSubModule: "fbdevhw"
[   204.006] (II) Unloading fbdevhw
[   204.006] (==) Depth 24 pixmap format is 32 bpp
[   204.006] (II) RADEON(G0): [DRI2] Setup complete
[   204.006] (II) RADEON(G0): [DRI2]   DRI driver: r600
[   204.006] (II) RADEON(G0): [DRI2]   VDPAU driver: r600
[   204.006] (II) RADEON(G0): Front buffer size: 4128K
[   204.006] (II) RADEON(G0): VRAM usage limit set to 464054K
[   204.006] (==) RADEON(G0): Backing store disabled
[   204.007] (II) RADEON(G0): Direct rendering enabled
[   204.007] (II) EXA(256): Driver allocated offscreen pixmaps
[   204.007] (II) EXA(256): Driver registered support for the following operations:
[   204.007] (II)         Solid
[   204.007] (II)         Copy
[   204.007] (II)         Composite (RENDER acceleration)
[   204.007] (II)         UploadToScreen
[   204.007] (II)         DownloadFromScreen
[   204.007] (II) RADEON(G0): Acceleration enabled
[   204.007] (==) RADEON(G0): DPMS enabled
[   204.007] (==) RADEON(G0): Silken mouse enabled
[   204.007] (II) RADEON(G0): Set up textured video
[   204.007] (II) RADEON(G0): [XvMC] Associated with Radeon Textured Video.
[   204.007] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[   204.007] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   204.009] (II) intel(0): SNA initialized with Ironlake backend
[   204.009] (==) intel(0): Backing store disabled
[   204.009] (==) intel(0): Silken mouse enabled
[   204.009] (II) intel(0): HW Cursor enabled
[   204.009] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   204.010] (==) intel(0): DPMS enabled
[   204.010] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   204.010] (II) intel(0): [DRI2] Setup complete
[   204.010] (II) intel(0): [DRI2]   DRI driver: i965
[   204.010] (II) intel(0): direct rendering: DRI2 Enabled
[   204.010] (==) intel(0): hotplug detection: "enabled"
[   204.011] (--) RandR disabled
[   204.023] (II) SELinux: Disabled on system
[   204.030] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   204.030] (II) AIGLX: enabled GLX_INTEL_swap_event
[   204.030] (II) AIGLX: enabled GLX_ARB_create_context
[   204.030] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   204.030] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   204.030] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   204.030] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   204.030] (II) AIGLX: Loaded and initialized i965
[   204.030] (II) GLX: Initialized DRI2 GL provider for screen 0
[   204.031] (II) RADEON(G0): Setting screen physical size to 361 x 203
[   204.031] (II) intel(0): switch to mode 1024x768 on crtc 3 (pipe 0)
[   204.920] (II) intel(0): switch to mode 1024x768 on crtc 5 (pipe 1)
[   205.112] (II) intel(0): Setting screen physical size to 270 x 203
[   205.129] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   205.178] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   205.178] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   205.178] (II) LoadModule: "evdev"
[   205.178] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   205.179] (II) Module evdev: vendor="X.Org Foundation"
[   205.179]     compiled for 1.13.3, module version = 2.7.3
[   205.179]     Module class: X.Org XInput Driver
[   205.179]     ABI class: X.Org XInput driver, version 18.0
[   205.179] (II) Using input driver 'evdev' for 'Power Button'
[   205.179] (**) Power Button: always reports core events
[   205.179] (**) evdev: Power Button: Device: "/dev/input/event2"
[   205.179] (--) evdev: Power Button: Vendor 0 Product 0x1
[   205.179] (--) evdev: Power Button: Found keys
[   205.179] (II) evdev: Power Button: Configuring as keyboard
[   205.179] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   205.179] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   205.179] (**) Option "xkb_rules" "evdev"
[   205.179] (**) Option "xkb_model" "pc105"
[   205.179] (**) Option "xkb_layout" "es"
[   205.182] (II) XKB: generating xkmfile /tmp/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[   205.206] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[   205.206] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   205.206] (II) Using input driver 'evdev' for 'Video Bus'
[   205.206] (**) Video Bus: always reports core events
[   205.206] (**) evdev: Video Bus: Device: "/dev/input/event9"
[   205.206] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   205.206] (--) evdev: Video Bus: Found keys
[   205.206] (II) evdev: Video Bus: Configuring as keyboard
[   205.206] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9/event9"
[   205.207] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   205.207] (**) Option "xkb_rules" "evdev"
[   205.207] (**) Option "xkb_model" "pc105"
[   205.207] (**) Option "xkb_layout" "es"
[   205.207] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[   205.207] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   205.207] (II) Using input driver 'evdev' for 'Video Bus'
[   205.207] (**) Video Bus: always reports core events
[   205.207] (**) evdev: Video Bus: Device: "/dev/input/event10"
[   205.207] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   205.207] (--) evdev: Video Bus: Found keys
[   205.207] (II) evdev: Video Bus: Configuring as keyboard
[   205.207] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/LNXVIDEO:01/input/input10/event10"
[   205.207] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[   205.207] (**) Option "xkb_rules" "evdev"
[   205.207] (**) Option "xkb_model" "pc105"
[   205.207] (**) Option "xkb_layout" "es"
[   205.208] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   205.208] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   205.208] (II) Using input driver 'evdev' for 'Power Button'
[   205.209] (**) Power Button: always reports core events
[   205.209] (**) evdev: Power Button: Device: "/dev/input/event1"
[   205.209] (--) evdev: Power Button: Vendor 0 Product 0x1
[   205.209] (--) evdev: Power Button: Found keys
[   205.209] (II) evdev: Power Button: Configuring as keyboard
[   205.209] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[   205.209] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[   205.209] (**) Option "xkb_rules" "evdev"
[   205.209] (**) Option "xkb_model" "pc105"
[   205.209] (**) Option "xkb_layout" "es"
[   205.209] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   205.209] (II) No input driver specified, ignoring this device.
[   205.209] (II) This device may have been added with another device file.
[   205.210] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[   205.210] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   205.210] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event13)
[   205.210] (II) No input driver specified, ignoring this device.
[   205.210] (II) This device may have been added with another device file.
[   205.210] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:02.0/drm/card1
[   205.210] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[   205.211] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event11)
[   205.211] (II) No input driver specified, ignoring this device.
[   205.211] (II) This device may have been added with another device file.
[   205.211] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event12)
[   205.211] (II) No input driver specified, ignoring this device.
[   205.211] (II) This device may have been added with another device file.
[   205.211] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101b (/dev/input/event4)
[   205.211] (**) Logitech Unifying Device. Wireless PID:101b: Applying InputClass "evdev pointer catchall"
[   205.211] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101b'
[   205.211] (**) Logitech Unifying Device. Wireless PID:101b: always reports core events
[   205.211] (**) evdev: Logitech Unifying Device. Wireless PID:101b: Device: "/dev/input/event4"
[   205.211] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Vendor 0x46d Product 0xc52b
[   205.211] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found 20 mouse buttons
[   205.212] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found scroll wheel(s)
[   205.212] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found relative axes
[   205.212] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found x and y relative axes
[   205.212] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Configuring as mouse
[   205.212] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Adding scrollwheel support
[   205.212] (**) evdev: Logitech Unifying Device. Wireless PID:101b: YAxisMapping: buttons 4 and 5
[   205.212] (**) evdev: Logitech Unifying Device. Wireless PID:101b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   205.212] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:046D:C52B.0003/input/input4/event4"
[   205.212] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101b" (type: MOUSE, id 10)
[   205.212] (II) evdev: Logitech Unifying Device. Wireless PID:101b: initialized for relative axes.
[   205.212] (**) Logitech Unifying Device. Wireless PID:101b: (accel) keeping acceleration scheme 1
[   205.212] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration profile 0
[   205.212] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration factor: 2.000
[   205.212] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration threshold: 4
[   205.213] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101b (/dev/input/mouse0)
[   205.213] (II) No input driver specified, ignoring this device.
[   205.213] (II) This device may have been added with another device file.
[   205.213] (II) config/udev: Adding input device HP Webcam (/dev/input/event5)
[   205.213] (**) HP Webcam: Applying InputClass "evdev keyboard catchall"
[   205.213] (II) Using input driver 'evdev' for 'HP Webcam'
[   205.213] (**) HP Webcam: always reports core events
[   205.213] (**) evdev: HP Webcam: Device: "/dev/input/event5"
[   205.213] (--) evdev: HP Webcam: Vendor 0x10f1 Product 0x1a16
[   205.213] (--) evdev: HP Webcam: Found keys
[   205.213] (II) evdev: HP Webcam: Configuring as keyboard
[   205.213] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input5/event5"
[   205.213] (II) XINPUT: Adding extended input device "HP Webcam" (type: KEYBOARD, id 11)
[   205.213] (**) Option "xkb_rules" "evdev"
[   205.213] (**) Option "xkb_model" "pc105"
[   205.213] (**) Option "xkb_layout" "es"
[   205.214] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   205.214] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   205.214] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   205.214] (**) AT Translated Set 2 keyboard: always reports core events
[   205.214] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   205.214] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   205.214] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   205.214] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   205.214] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   205.214] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[   205.214] (**) Option "xkb_rules" "evdev"
[   205.214] (**) Option "xkb_model" "pc105"
[   205.214] (**) Option "xkb_layout" "es"
[   205.215] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[   205.215] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   205.215] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   205.215] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   205.215] (II) LoadModule: "synaptics"
[   205.215] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   205.215] (II) Module synaptics: vendor="X.Org Foundation"
[   205.215]     compiled for 1.13.1.901, module version = 1.6.2
[   205.215]     Module class: X.Org XInput Driver
[   205.215]     ABI class: X.Org XInput driver, version 18.0
[   205.215] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   205.215] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   205.215] (**) Option "Device" "/dev/input/event7"
[   205.236] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[   205.236] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[   205.236] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5516
[   205.236] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4544
[   205.236] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   205.236] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   205.236] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[   205.236] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   205.236] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[   205.236] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   205.236] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   205.244] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input7/event7"
[   205.244] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[   205.244] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   205.244] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   205.244] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.039
[   205.245] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   205.245] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   205.245] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   205.245] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   205.245] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   205.245] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[   205.246] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   205.246] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[   205.246] (II) No input driver specified, ignoring this device.
[   205.246] (II) This device may have been added with another device file.
[   205.247] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[   205.247] (II) No input driver specified, ignoring this device.
[   205.247] (II) This device may have been added with another device file.
[   205.253] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event8)
[   205.253] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   205.253] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[   205.253] (**) HP WMI hotkeys: always reports core events
[   205.253] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event8"
[   205.253] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[   205.253] (--) evdev: HP WMI hotkeys: Found keys
[   205.253] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[   205.254] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[   205.254] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 14)
[   205.254] (**) Option "xkb_rules" "evdev"
[   205.254] (**) Option "xkb_model" "pc105"
[   205.254] (**) Option "xkb_layout" "es"
[   205.260] (EE) 
[   205.260] (EE) Backtrace:
[   205.261] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7fbacce851c6]
[   205.261] (EE) 1: /usr/bin/X (0x7fbacccd5000+0x1b4009) [0x7fbacce89009]
[   205.261] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fbacbdd8000+0xfbd0) [0x7fbacbde7bd0]
[   205.261] (EE) 3: /usr/bin/X (DamageRegister+0x20) [0x7fbacce0d1a0]
[   205.261] (EE) 4: /usr/bin/X (0x7fbacccd5000+0xda761) [0x7fbaccdaf761]
[   205.261] (EE) 5: /usr/bin/X (BlockHandler+0x77) [0x7fbaccd31b27]
[   205.261] (EE) 6: /usr/bin/X (WaitForSomething+0x114) [0x7fbacce82544]
[   205.261] (EE) 7: /usr/bin/X (0x7fbacccd5000+0x58771) [0x7fbaccd2d771]
[   205.261] (EE) 8: /usr/bin/X (0x7fbacccd5000+0x474da) [0x7fbaccd1c4da]
[   205.261] (EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7fbacaa25ea5]
[   205.261] (EE) 10: /usr/bin/X (0x7fbacccd5000+0x47821) [0x7fbaccd1c821]
[   205.261] (EE) 
[   205.261] (EE) Segmentation fault at address 0x10
[   205.261] 
Fatal server error:
[   205.261] Caught signal 11 (Segmentation fault). Server aborting
[   205.261] 
[   205.261] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   205.261] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   205.262] (EE) 
[   205.264] (II) evdev: Power Button: Close
[   205.264] (II) UnloadModule: "evdev"
[   205.268] (II) evdev: Video Bus: Close
[   205.268] (II) UnloadModule: "evdev"
[   205.276] (II) evdev: Video Bus: Close
[   205.276] (II) UnloadModule: "evdev"
[   205.284] (II) evdev: Power Button: Close
[   205.284] (II) UnloadModule: "evdev"
[   205.292] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Close
[   205.292] (II) UnloadModule: "evdev"
[   205.300] (II) evdev: HP Webcam: Close
[   205.300] (II) UnloadModule: "evdev"
[   205.308] (II) evdev: AT Translated Set 2 keyboard: Close
[   205.308] (II) UnloadModule: "evdev"
[   205.320] (II) UnloadModule: "synaptics"
[   205.324] (II) evdev: HP WMI hotkeys: Close
[   205.324] (II) UnloadModule: "evdev"
[   205.324] (II) AIGLX: Suspending AIGLX clients for VT switch
[   206.402] Server terminated with error (1). Closing log file.
```

You can see that there are some errors complaining that fglrx could not be loaded. I didn't know that Ubuntu installed the ATI driver by default during the installation, but in any case, it didn't work correctly in my case.

Anyway, I was able to solve this problem by installing the fglrx drivers (apt-get install fglrx). Later, I removed fglrx, and used the open source drivers.


**[SIZE=3]Missing window decorators in Unity[/SIZE]**

I am using the open source ATI drivers now, but I am not able to get window decorators in Unity. After logging to Unity, the desktop is completely empty (except for icons), and no panel nor unity bar is present.

I have tried running unity --replace, but it didn't work 

```
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: nessun processo trovato
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/gioby/.compiz/session/10bcd42beb3b53adfd136465872831872500000238440014"
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
```

---

### Post by dino99 on 2013-03-30
often compiz simply crash; so you need to open a terminal and run:

compiz --replace ccp &
setsid unity

---

### Post by gioby on 2013-03-30
Thank you for the reply,
unfortunately, this didn't work. It seems that Unity is not supported in my computer. But then, shouldn't unity work anyway using llvmpipe?


Here is the output:

```
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: nessun processo trovato
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/gioby/.compiz/session/10bcd42beb3b53adfd136465872831872500000238440014"
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
```

---

### Post by gioby on 2013-03-30
I've also tried to reistall unity:

```
sudo apt-get install --reinstall unity
sudo apt-get install --reinstall ubuntu-desktop
```

but no effect :-(

---

### Post by dino99 on 2013-03-30
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available

there is two problem: 
- unity is not supported on that hardware, so try gnome-classic (shell)
- pixmap is buggy (or compiz), so need to wait a few more days to get more fixes. Maybe report against libxpm4

---

### Post by jfernyhough on 2013-03-30
Have you removed the xorg.conf created by the fglrx driver?
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old

Unity/Compiz should work with an AMD chip no matter the graphics driver.

---

### Post by gioby on 2013-03-30
> **dino99 said:**
> compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available

there is two problem: 
- unity is not supported on that hardware, so try gnome-classic (shell)
- pixmap is buggy (or compiz), so need to wait a few more days to get more fixes. Maybe report against libxpm4

Thank you very much for the answer.
Unfortunately Gnome-shell also doesn't work without the proprietary drivers. I am using the gnome fall back session, which looks like gnome 2.6. How silly, I really like Unity and Gnome shell more.





> Have you removed the xorg.conf created by the fglrx driver?
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old

Unity/Compiz should work with an AMD chip no matter the graphics driver.
Thank you. I've tried it, but there is no /etc/X11/xorg.conf file there. In any case, this machine has an Intel processor, but an ATI card.
I've never been able to install the ATI proprietary drivers in this machine. Until now I was using Ubuntu 12.04, and happily using Unity 2D. I was expecting Unity to work now that the former has been removed, but it's not the case.

---

### Post by jemoon on 2013-03-30
Hello,
@gioby after launching X without decorations try to run the terminal (ctrl+alt+t) and then:
> 
sudo mv ~/.config/dconf/user ~/user
sudo reboot


---

### Post by gioby on 2013-03-30
> **jemoon said:**
> Hello,
@gioby after launching X without decorations try to run the terminal (ctrl+alt+t) and then:

Thank you, but no luck, even after trying this :-(

---

