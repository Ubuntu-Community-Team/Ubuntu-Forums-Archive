---
title: "Re: Steam crash the machine"
date: 2016-02-15
forum: Ubuntu Development Version
---

### Post by valereguerin on 2016-02-15
Hello, everything is good but in steam at one moment in game ; game freeze just put reset button option ! (sorry if you don't understand, i'm french)
i try to put Steam in a window on the desk, it's the same  Maybe a problem with pulseaudio because the sound crash first

[pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files

Where can i find information about crash ???

```
freeman@Sniper-one:~$ inxi -b  
System:    Host: Sniper-one Kernel: 4.3.0-5-generic x86_64 (64 bit) Desktop: Gnome 3.18.2
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2798 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.17.3 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.6.2) GLX Version: 3.0 Mesa 11.0.7
Network:   Card: D-Link System DGE-528T Gigabit Ethernet Adapter driver: r8169
Drives:    HDD Total Size: 5815.3GB (23.1% used)
Info:      Processes: 336 Uptime: 59 min Memory: 2268.9/7853.2MB Client: Shell (bash) inxi: 2.2.28 


log.xserveur

[  1601.762] _XSERVTransMakeAllCOTSServerListeners: server already running
[  1601.762] 
X.Org X Server 1.17.3
Release Date: 2015-10-26
[  1601.762] X Protocol Version 11, Revision 0
[  1601.762] Build Operating System: Linux 3.19.0-33-generic x86_64 Ubuntu
[  1601.762] Current Operating System: Linux Sniper-one 4.3.0-5-generic #16-Ubuntu SMP Wed Dec 16 23:33:25 UTC 2015 x86_64
[  1601.762] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-5-generic root=UUID=xxxxx-xxxxxx-xxxxxxx-xxxxx ro persistent quiet splash crashkernel=384M-:128M
[  1601.762] Build Date: 25 November 2015  04:17:13PM
[  1601.762] xorg-server 2:1.17.3-2ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1601.762] Current version of pixman: 0.33.4
[  1601.762]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[  1601.762] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1601.762] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 24 13:54:25 2015
[  1601.762] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1601.762] (==) No Layout section.  Using the first Screen section.
[  1601.762] (==) No screen section available. Using defaults.
[  1601.762] (**) |-->Screen "Default Screen Section" (0)
[  1601.763] (**) |   |-->Monitor "<default monitor>"
[  1601.763] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  1601.763] (==) Automatically adding devices
[  1601.763] (==) Automatically enabling devices
[  1601.763] (==) Automatically adding GPU devices
[  1601.763] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1601.763]     Entry deleted from font path.
[  1601.763] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1601.763]     Entry deleted from font path.
[  1601.763] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1601.763]     Entry deleted from font path.
[  1601.763] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1601.763]     Entry deleted from font path.
[  1601.763] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1601.763]     Entry deleted from font path.
[  1601.763] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1601.763] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1601.763] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1601.763] (II) Loader magic: 0x556bc5e72da0
[  1601.763] (II) Module ABI versions:
[  1601.763]     X.Org ANSI C Emulation: 0.4
[  1601.763]     X.Org Video Driver: 19.0
[  1601.763]     X.Org XInput driver : 21.0
[  1601.763]     X.Org Server Extension : 9.0
[  1601.765] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_311
[  1601.765] (II) xfree86: Adding drm device (/dev/dri/card0)
[  1601.766] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 10 paused 0
[  1601.768] (--) PCI:*(0:3:0:0) 1002:679a:174b:a003 rev 0, Mem @ 0xe0000000/268435456, 0xfbb80000/262144, I/O @ 0x0000ce00/256, BIOS @ 0x????????/131072
[  1601.768] (II) LoadModule: "glx"
[  1601.768] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1601.769] (II) Module glx: vendor="X.Org Foundation"
[  1601.769]     compiled for 1.17.3, module version = 1.0.0
[  1601.769]     ABI class: X.Org Server Extension, version 9.0
[  1601.769] (==) AIGLX enabled
[  1601.769] (==) Matched fglrx as autoconfigured driver 0
[  1601.769] (==) Matched ati as autoconfigured driver 1
[  1601.769] (==) Matched fglrx as autoconfigured driver 2
[  1601.769] (==) Matched ati as autoconfigured driver 3
[  1601.769] (==) Matched modesetting as autoconfigured driver 4
[  1601.769] (==) Matched fbdev as autoconfigured driver 5
[  1601.769] (==) Matched vesa as autoconfigured driver 6
[  1601.769] (==) Assigned the driver to the xf86ConfigLayout
[  1601.769] (II) LoadModule: "fglrx"
[  1601.769] (WW) Warning, couldn't open module fglrx
[  1601.769] (II) UnloadModule: "fglrx"
[  1601.769] (II) Unloading fglrx
[  1601.769] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  1601.769] (II) LoadModule: "ati"
[  1601.769] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  1601.769] (II) Module ati: vendor="X.Org Foundation"
[  1601.769]     compiled for 1.17.3, module version = 7.6.1
[  1601.769]     Module class: X.Org Video Driver
[  1601.769]     ABI class: X.Org Video Driver, version 19.0
[  1601.769] (II) LoadModule: "radeon"
[  1601.769] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  1601.769] (II) Module radeon: vendor="X.Org Foundation"
[  1601.769]     compiled for 1.17.3, module version = 7.6.1
[  1601.769]     Module class: X.Org Video Driver
[  1601.769]     ABI class: X.Org Video Driver, version 19.0
[  1601.769] (II) LoadModule: "modesetting"
[  1601.770] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1601.770] (II) Module modesetting: vendor="X.Org Foundation"
[  1601.770]     compiled for 1.17.3, module version = 1.17.3
[  1601.770]     Module class: X.Org Video Driver
[  1601.770]     ABI class: X.Org Video Driver, version 19.0
[  1601.770] (II) LoadModule: "fbdev"
[  1601.770] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1601.770] (II) Module fbdev: vendor="X.Org Foundation"
[  1601.770]     compiled for 1.17.1, module version = 0.4.4
[  1601.770]     Module class: X.Org Video Driver
[  1601.770]     ABI class: X.Org Video Driver, version 19.0
[  1601.770] (II) LoadModule: "vesa"
[  1601.770] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1601.770] (II) Module vesa: vendor="X.Org Foundation"
[  1601.770]     compiled for 1.17.1, module version = 2.3.4
[  1601.770]     Module class: X.Org Video Driver
[  1601.770]     ABI class: X.Org Video Driver, version 19.0
[  1601.770] (==) Matched fglrx as autoconfigured driver 0
[  1601.770] (==) Matched ati as autoconfigured driver 1
[  1601.770] (==) Matched fglrx as autoconfigured driver 2
[  1601.770] (==) Matched ati as autoconfigured driver 3
[  1601.770] (==) Matched modesetting as autoconfigured driver 4
[  1601.770] (==) Matched fbdev as autoconfigured driver 5
[  1601.770] (==) Matched vesa as autoconfigured driver 6
[  1601.770] (==) Assigned the driver to the xf86ConfigLayout
[  1601.770] (II) LoadModule: "fglrx"
[  1601.770] (WW) Warning, couldn't open module fglrx
[  1601.770] (II) UnloadModule: "fglrx"
[  1601.770] (II) Unloading fglrx
[  1601.770] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  1601.770] (II) LoadModule: "ati"
[  1601.770] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  1601.770] (II) Module ati: vendor="X.Org Foundation"
[  1601.770]     compiled for 1.17.3, module version = 7.6.1
[  1601.770]     Module class: X.Org Video Driver
[  1601.770]     ABI class: X.Org Video Driver, version 19.0
[  1601.770] (II) LoadModule: "modesetting"
[  1601.770] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1601.770] (II) Module modesetting: vendor="X.Org Foundation"
[  1601.770]     compiled for 1.17.3, module version = 1.17.3
[  1601.770]     Module class: X.Org Video Driver
[  1601.770]     ABI class: X.Org Video Driver, version 19.0
[  1601.771] (II) UnloadModule: "modesetting"
[  1601.771] (II) Unloading modesetting
[  1601.771] (II) Failed to load module "modesetting" (already loaded, 0)
[  1601.771] (II) LoadModule: "fbdev"
[  1601.771] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1601.771] (II) Module fbdev: vendor="X.Org Foundation"
[  1601.771]     compiled for 1.17.1, module version = 0.4.4
[  1601.771]     Module class: X.Org Video Driver
[  1601.771]     ABI class: X.Org Video Driver, version 19.0
[  1601.771] (II) UnloadModule: "fbdev"
[  1601.771] (II) Unloading fbdev
[  1601.771] (II) Failed to load module "fbdev" (already loaded, 0)
[  1601.771] (II) LoadModule: "vesa"
[  1601.771] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1601.771] (II) Module vesa: vendor="X.Org Foundation"
[  1601.771]     compiled for 1.17.1, module version = 2.3.4
[  1601.771]     Module class: X.Org Video Driver
[  1601.771]     ABI class: X.Org Video Driver, version 19.0
[  1601.771] (II) UnloadModule: "vesa"
[  1601.771] (II) Unloading vesa
[  1601.771] (II) Failed to load module "vesa" (already loaded, 0)
[  1601.771] (II) RADEON: Driver for ATI Radeon chipsets:
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
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
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
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[  1601.818] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1601.818] (II) FBDEV: driver for framebuffer: fbdev
[  1601.818] (II) VESA: driver for VESA chipsets: vesa
[  1601.818] (++) using VT number 2

[  1601.818] (II) [KMS] Kernel modesetting enabled.
[  1601.819] (WW) Falling back to old probe method for modesetting
[  1601.819] (WW) Falling back to old probe method for fbdev
[  1601.819] (II) Loading sub module "fbdevhw"
[  1601.819] (II) LoadModule: "fbdevhw"
[  1601.819] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1601.819] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1601.819]     compiled for 1.17.3, module version = 0.0.2
[  1601.819]     ABI class: X.Org Video Driver, version 19.0
[  1601.819] (WW) Falling back to old probe method for vesa
[  1601.819] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  1601.819] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  1601.819] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  1601.819] (==) RADEON(0): Default visual is TrueColor
[  1601.819] (==) RADEON(0): RGB weight 888
[  1601.819] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  1601.819] (--) RADEON(0): Chipset: "TAHITI" (ChipID = 0x679a)
[  1601.819] (II) Loading sub module "dri2"
[  1601.819] (II) LoadModule: "dri2"
[  1601.819] (II) Module "dri2" already built-in
[  1601.819] (II) Loading sub module "glamoregl"
[  1601.819] (II) LoadModule: "glamoregl"
[  1601.819] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  1601.822] (II) Module glamoregl: vendor="X.Org Foundation"
[  1601.822]     compiled for 1.17.3, module version = 1.0.0
[  1601.822]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1601.822] (II) glamor: OpenGL accelerated X.org driver based.
[  1601.834] (II) glamor: EGL version 1.4 (DRI2):
[  1601.835] (II) RADEON(0): glamor detected, initialising EGL layer.
[  1601.835] (II) RADEON(0): KMS Color Tiling: enabled
[  1601.835] (II) RADEON(0): KMS Color Tiling 2D: enabled
[  1601.835] (II) RADEON(0): KMS Pageflipping: enabled
[  1601.835] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  1601.840] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[  1601.899] (II) RADEON(0): Output HDMI-0 has no monitor section
[  1601.901] (II) RADEON(0): Output DVI-0 has no monitor section
[  1601.912] (II) RADEON(0): Output DVI-1 has no monitor section
[  1601.920] (II) RADEON(0): EDID for output DisplayPort-0
[  1601.979] (II) RADEON(0): EDID for output HDMI-0
[  1601.979] (II) RADEON(0): Manufacturer: SAM  Model: b67  Serial#: 808662579
[  1601.979] (II) RADEON(0): Year: 2014  Week: 43
[  1601.979] (II) RADEON(0): EDID Version: 1.3
[  1601.979] (II) RADEON(0): Digital Display Input
[  1601.979] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[  1601.979] (II) RADEON(0): Gamma: 2.20
[  1601.979] (II) RADEON(0): DPMS capabilities: Off
[  1601.979] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  1601.979] (II) RADEON(0): First detailed timing is preferred mode
[  1601.979] (II) RADEON(0): redX: 0.646 redY: 0.337   greenX: 0.329 greenY: 0.616
[  1601.979] (II) RADEON(0): blueX: 0.146 blueY: 0.056   whiteX: 0.312 whiteY: 0.329
[  1601.979] (II) RADEON(0): Supported established timings:
[  1601.979] (II) RADEON(0): 720x400@70Hz
[  1601.979] (II) RADEON(0): 640x480@60Hz
[  1601.979] (II) RADEON(0): 640x480@67Hz
[  1601.979] (II) RADEON(0): 640x480@72Hz
[  1601.979] (II) RADEON(0): 640x480@75Hz
[  1601.979] (II) RADEON(0): 800x600@56Hz
[  1601.979] (II) RADEON(0): 800x600@60Hz
[  1601.979] (II) RADEON(0): 800x600@72Hz
[  1601.979] (II) RADEON(0): 800x600@75Hz
[  1601.979] (II) RADEON(0): 832x624@75Hz
[  1601.980] (II) RADEON(0): 1024x768@60Hz
[  1601.980] (II) RADEON(0): 1024x768@70Hz
[  1601.980] (II) RADEON(0): 1024x768@75Hz
[  1601.980] (II) RADEON(0): 1280x1024@75Hz
[  1601.980] (II) RADEON(0): 1152x864@75Hz
[  1601.980] (II) RADEON(0): Manufacturer's mask: 0
[  1601.980] (II) RADEON(0): Supported standard timings:
[  1601.980] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  1601.980] (II) RADEON(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[  1601.980] (II) RADEON(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[  1601.980] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  1601.980] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[  1601.980] (II) RADEON(0): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[  1601.980] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[  1601.980] (II) RADEON(0): Supported detailed timing:
[  1601.980] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[  1601.980] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[  1601.980] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[  1601.980] (II) RADEON(0): Supported detailed timing:
[  1601.980] (II) RADEON(0): clock: 74.2 MHz   Image Size:  598 x 336 mm
[  1601.980] (II) RADEON(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[  1601.980] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[  1601.980] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[  1601.980] (II) RADEON(0): Monitor name: S27D390
[  1601.980] (II) RADEON(0): Supported detailed timing:
[  1601.980] (II) RADEON(0): clock: 74.2 MHz   Image Size:  598 x 336 mm
[  1601.980] (II) RADEON(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[  1601.980] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[  1601.980] (II) RADEON(0): Supported detailed timing:
[  1601.980] (II) RADEON(0): clock: 27.0 MHz   Image Size:  598 x 336 mm
[  1601.980] (II) RADEON(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[  1601.980] (II) RADEON(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[  1601.980] (II) RADEON(0): Supported detailed timing:
[  1601.980] (II) RADEON(0): clock: 27.0 MHz   Image Size:  598 x 336 mm
[  1601.980] (II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[  1601.980] (II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[  1601.980] (II) RADEON(0): Number of EDID sections to follow: 1
[  1601.980] (II) RADEON(0): EDID (in hex):
[  1601.980] (II) RADEON(0):     00ffffffffffff004c2d670b33363330
[  1601.980] (II) RADEON(0):     2b180103803c22782a9791a556549d25
[  1601.980] (II) RADEON(0):     0e5054bfef80714f81c0810081809500
[  1601.980] (II) RADEON(0):     a9c0b3000101023a801871382d40582c
[  1601.980] (II) RADEON(0):     450056502100001e011d007251d01e20
[  1601.980] (II) RADEON(0):     6e28550056502100001e000000fd0032
[  1601.980] (II) RADEON(0):     4b1e5111000a202020202020000000fc
[  1601.980] (II) RADEON(0):     00533237443339300a202020202001db
[  1601.980] (II) RADEON(0):     02031af14690041f1303122309070783
[  1601.980] (II) RADEON(0):     01000066030c00100080011d00bc52d0
[  1601.980] (II) RADEON(0):     1e20b828554056502100001e8c0ad090
[  1601.980] (II) RADEON(0):     204031200c4055005650210000188c0a
[  1601.980] (II) RADEON(0):     d08a20e02d10103e9600565021000018
[  1601.980] (II) RADEON(0):     00000000000000000000000000000000
[  1601.980] (II) RADEON(0):     00000000000000000000000000000000
[  1601.980] (II) RADEON(0):     00000000000000000000000000000061
[  1601.980] (II) RADEON(0): Printing probed modes for output HDMI-0
[  1601.980] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1601.980] (II) RADEON(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1601.980] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1601.980] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1601.980] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1601.980] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1601.980] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1601.980] (II) RADEON(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[  1601.980] (II) RADEON(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[  1601.980] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1601.980] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1601.980] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1601.981] (II) RADEON(0): EDID for output DVI-0
[  1601.992] (II) RADEON(0): EDID for output DVI-1
[  1601.992] (II) RADEON(0): Output DisplayPort-0 disconnected
[  1601.992] (II) RADEON(0): Output HDMI-0 connected
[  1601.992] (II) RADEON(0): Output DVI-0 disconnected
[  1601.992] (II) RADEON(0): Output DVI-1 disconnected
[  1601.992] (II) RADEON(0): Using exact sizes for initial modes
[  1601.992] (II) RADEON(0): Output HDMI-0 using initial mode 1920x1080
[  1601.992] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1601.992] (II) RADEON(0): mem size init: gart size :7fbcc000 vram size: s:c0000000 visible:be8bd000
[  1601.992] (==) RADEON(0): DPI set to (96, 96)
[  1601.992] (II) Loading sub module "fb"
[  1601.992] (II) LoadModule: "fb"
[  1601.992] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1601.992] (II) Module fb: vendor="X.Org Foundation"
[  1601.992]     compiled for 1.17.3, module version = 1.0.0
[  1601.992]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1601.992] (II) Loading sub module "ramdac"
[  1601.992] (II) LoadModule: "ramdac"
[  1601.992] (II) Module "ramdac" already built-in
[  1601.992] (II) UnloadModule: "modesetting"
[  1601.992] (II) Unloading modesetting
[  1601.992] (II) UnloadModule: "fbdev"
[  1601.992] (II) Unloading fbdev
[  1601.992] (II) UnloadSubModule: "fbdevhw"
[  1601.992] (II) Unloading fbdevhw
[  1601.992] (II) UnloadModule: "vesa"
[  1601.992] (II) Unloading vesa
[  1601.992] (--) Depth 24 pixmap format is 32 bpp
[  1601.992] (II) RADEON(0): [DRI2] Setup complete
[  1601.992] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[  1601.992] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[  1601.993] (II) RADEON(0): Front buffer size: 8640K
[  1601.993] (II) RADEON(0): VRAM usage limit set to 2801854K
[  1601.993] (==) RADEON(0): DRI3 disabled
[  1601.993] (==) RADEON(0): Backing store enabled
[  1601.993] (II) RADEON(0): Direct rendering enabled
[  1602.037] (II) RADEON(0): Use GLAMOR acceleration.
[  1602.037] (II) RADEON(0): Acceleration enabled
[  1602.037] (==) RADEON(0): DPMS enabled
[  1602.037] (==) RADEON(0): Silken mouse enabled
[  1602.037] (II) RADEON(0): Set up textured video (glamor)
[  1602.037] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[  1602.037] (II) RADEON(0): [XvMC] Extension initialized.
[  1602.037] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1602.037] (--) RandR disabled
[  1602.041] (II) SELinux: Disabled on system
[  1602.042] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  1602.042] (II) AIGLX: enabled GLX_ARB_create_context
[  1602.042] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  1602.042] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[  1602.042] (II) AIGLX: enabled GLX_INTEL_swap_event
[  1602.042] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  1602.042] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[  1602.042] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[  1602.042] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  1602.042] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[  1602.043] (II) AIGLX: Loaded and initialized radeonsi
[  1602.043] (II) GLX: Initialized DRI2 GL provider for screen 0
[  1602.050] (II) RADEON(0): Setting screen physical size to 508 x 285
[  1602.065] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1602.087] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1602.087] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1602.087] (II) LoadModule: "evdev"
[  1602.088] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1602.088] (II) Module evdev: vendor="X.Org Foundation"
[  1602.088]     compiled for 1.17.1, module version = 2.9.2
[  1602.088]     Module class: X.Org XInput Driver
[  1602.088]     ABI class: X.Org XInput driver, version 21.0
[  1602.088] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 18 paused 0
[  1602.088] (II) Using input driver 'evdev' for 'Power Button'
[  1602.088] (**) Power Button: always reports core events
[  1602.088] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1602.088] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1602.089] (--) evdev: Power Button: Found keys
[  1602.089] (II) evdev: Power Button: Configuring as keyboard
[  1602.089] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1602.089] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1602.089] (**) Option "xkb_rules" "evdev"
[  1602.089] (**) Option "xkb_model" "pc105"
[  1602.089] (**) Option "xkb_layout" "fr"
[  1602.089] (**) Option "xkb_variant" "latin9"
[  1602.091] (II) XKB: generating xkmfile /tmp/server-816A055A5FF7D63897839A4BDEDC3908551E49DA.xkm
[  1602.105] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1602.105] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1602.106] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 19 paused 0
[  1602.106] (II) Using input driver 'evdev' for 'Power Button'
[  1602.106] (**) Power Button: always reports core events
[  1602.106] (**) evdev: Power Button: Device: "/dev/input/event0"
[  1602.106] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1602.106] (--) evdev: Power Button: Found keys
[  1602.106] (II) evdev: Power Button: Configuring as keyboard
[  1602.106] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[  1602.106] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  1602.106] (**) Option "xkb_rules" "evdev"
[  1602.106] (**) Option "xkb_model" "pc105"
[  1602.106] (**) Option "xkb_layout" "fr"
[  1602.106] (**) Option "xkb_variant" "latin9"
[  1602.107] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event7)
[  1602.107] (II) No input driver specified, ignoring this device.
[  1602.107] (II) This device may have been added with another device file.
[  1602.107] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event8)
[  1602.107] (II) No input driver specified, ignoring this device.
[  1602.107] (II) This device may have been added with another device file.
[  1602.107] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event9)
[  1602.107] (II) No input driver specified, ignoring this device.
[  1602.107] (II) This device may have been added with another device file.
[  1602.107] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[  1602.107] (II) No input driver specified, ignoring this device.
[  1602.107] (II) This device may have been added with another device file.
[  1602.108] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event5)
[  1602.108] (II) No input driver specified, ignoring this device.
[  1602.108] (II) This device may have been added with another device file.
[  1602.108] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event6)
[  1602.108] (II) No input driver specified, ignoring this device.
[  1602.108] (II) This device may have been added with another device file.
[  1602.108] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[  1602.108] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[  1602.109] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 20 paused 0
[  1602.109] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[  1602.109] (**) Dell Dell USB Keyboard: always reports core events
[  1602.109] (**) evdev: Dell Dell USB Keyboard: Device: "/dev/input/event2"
[  1602.109] (--) evdev: Dell Dell USB Keyboard: Vendor 0x413c Product 0x2105
[  1602.109] (--) evdev: Dell Dell USB Keyboard: Found keys
[  1602.109] (II) evdev: Dell Dell USB Keyboard: Configuring as keyboard
[  1602.109] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb6/6-1/6-1:1.0/0003:413C:2105.0001/input/input5/event2"
[  1602.109] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD, id 8)
[  1602.109] (**) Option "xkb_rules" "evdev"
[  1602.109] (**) Option "xkb_model" "pc105"
[  1602.109] (**) Option "xkb_layout" "fr"
[  1602.109] (**) Option "xkb_variant" "latin9"
[  1602.109] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[  1602.109] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[  1602.109] (**) USB Optical Mouse: Applying InputClass "Avago Technologies mouse quirks (LP: #746639)"
[  1602.110] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 21 paused 0
[  1602.110] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[  1602.110] (**) USB Optical Mouse: always reports core events
[  1602.110] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[  1602.110] (--) evdev: USB Optical Mouse: Vendor 0x192f Product 0x416
[  1602.110] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[  1602.110] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[  1602.110] (--) evdev: USB Optical Mouse: Found relative axes
[  1602.110] (--) evdev: USB Optical Mouse: Found x and y relative axes
[  1602.110] (II) evdev: USB Optical Mouse: Configuring as mouse
[  1602.110] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[  1602.110] (**) Option "Emulate3Buttons" "True"
[  1602.110] (**) Option "Emulate3Timeout" "50"
[  1602.110] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[  1602.110] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1602.110] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb7/7-1/7-1:1.0/0003:192F:0416.0002/input/input6/event3"
[  1602.110] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 9)
[  1602.110] (II) evdev: USB Optical Mouse: initialized for relative axes.
[  1602.110] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[  1602.110] (**) USB Optical Mouse: (accel) acceleration profile 0
[  1602.110] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[  1602.110] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[  1602.111] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[  1602.111] (II) No input driver specified, ignoring this device.
[  1602.111] (II) This device may have been added with another device file.
[  1602.196] (II) XKB: generating xkmfile /tmp/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[  1603.355] (II) RADEON(0): EDID vendor "SAM", prod id 2919
[  1603.355] (II) RADEON(0): Using EDID range info for horizontal sync
[  1603.355] (II) RADEON(0): Using EDID range info for vertical refresh
[  1603.355] (II) RADEON(0): Printing DDC gathered Modelines:
[  1603.355] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1603.355] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[  1603.355] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[  1603.355] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1603.355] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1603.355] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1603.355] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1603.355] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1603.355] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1603.355] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1603.355] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1603.355] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1603.355] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1603.355] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[  1603.355] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[  1603.897] (II) XKB: generating xkmfile /tmp/server-A117E8C2B34CD5FF754CF1E73D033279089234B3.xkm
[  1603.988] (II) XKB: generating xkmfile /tmp/server-B4DE02F174E1811E593C0401E2AA50C11B795B92.xkm
[  1604.540] (II) RADEON(0): EDID vendor "SAM", prod id 2919
[  1604.541] (II) RADEON(0): Using hsync ranges from config file
[  1604.541] (II) RADEON(0): Using vrefresh ranges from config file
[  1604.541] (II) RADEON(0): Printing DDC gathered Modelines:
[  1604.541] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1604.541] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[  1604.541] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[  1604.541] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1604.541] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1604.541] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1604.541] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1604.541] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1604.541] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1604.541] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1604.541] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1604.541] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1604.541] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1604.541] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[  1604.541] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[  1604.699] (II) RADEON(0): EDID vendor "SAM", prod id 2919
[  1604.699] (II) RADEON(0): Using hsync ranges from config file
[  1604.699] (II) RADEON(0): Using vrefresh ranges from config file
[  1604.699] (II) RADEON(0): Printing DDC gathered Modelines:
[  1604.699] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1604.699] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[  1604.699] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[  1604.699] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1604.699] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1604.699] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1604.699] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1604.699] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1604.699] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1604.699] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1604.699] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1604.699] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1604.699] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1604.699] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[  1604.699] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[  1604.949] (II) XKB: generating xkmfile /tmp/server-A117E8C2B34CD5FF754CF1E73D033279089234B3.xkm
[  1605.021] (II) XKB: generating xkmfile /tmp/server-88AD5CA040F76AF9F761C0BBE9FA5C12439E3C76.xkm
[  1605.048] (II) XKB: generating xkmfile /tmp/server-88AD5CA040F76AF9F761C0BBE9FA5C12439E3C76.xkm
[  1605.233] (II) RADEON(0): EDID vendor "SAM", prod id 2919
[  1605.233] (II) RADEON(0): Using hsync ranges from config file
[  1605.233] (II) RADEON(0): Using vrefresh ranges from config file
[  1605.233] (II) RADEON(0): Printing DDC gathered Modelines:
[  1605.233] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1605.233] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[  1605.233] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[  1605.233] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1605.233] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1605.233] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1605.233] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1605.233] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1605.233] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1605.233] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1605.233] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1605.233] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1605.233] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1605.233] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1605.233] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1605.234] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[  1605.234] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1605.234] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[  1605.234] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[  1605.234] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[  1606.246] (II) XKB: generating xkmfile /tmp/server-88AD5CA040F76AF9F761C0BBE9FA5C12439E3C76.xkm
[  1608.347] (II) RADEON(0): EDID vendor "SAM", prod id 2919
[  1608.347] (II) RADEON(0): Using hsync ranges from config file
[  1608.347] (II) RADEON(0): Using vrefresh ranges from config file
[  1608.347] (II) RADEON(0): Printing DDC gathered Modelines:
[  1608.347] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1608.347] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1608.347] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[  1608.347] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[  1608.347] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1608.347] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1608.347] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1608.347] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1608.347] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1608.347] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1608.347] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1608.347] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1608.347] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1608.347] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1608.347] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1608.347] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1608.347] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1608.347] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1608.347] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1608.347] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1608.347] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1608.347] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1608.348] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1608.348] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1608.348] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[  1608.348] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1608.348] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[  1608.348] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[  1608.348] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[  1608.427] (II) RADEON(0): EDID vendor "SAM", prod id 2919
[  1608.427] (II) RADEON(0): Using hsync ranges from config file
[  1608.427] (II) RADEON(0): Using vrefresh ranges from config file
[  1608.427] (II) RADEON(0): Printing DDC gathered Modelines:
[  1608.427] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1608.427] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[  1608.427] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[  1608.427] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[  1608.427] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[  1608.427] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1608.427] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1608.427] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1608.427] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1608.427] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1608.427] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1608.427] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1608.427] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1608.427] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1608.427] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1608.427] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1608.427] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1608.427] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1608.427] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1608.427] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1608.427] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1608.428] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1608.428] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1608.428] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1608.428] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[  1608.428] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1608.428] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[  1608.428] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[  1608.428] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)



freeman@Sniper-one:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:10.0 PIC: Intel Corporation 7500/5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 7500/5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:11.0 PIC: Intel Corporation 7500/5520/5500 Physical and Link Layer Registers Port 1 (rev 13)
00:11.1 PIC: Intel Corporation 7500/5520/5500 Routing & Protocol Layer Register Port 1 (rev 13)
00:13.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:15.0 PIC: Intel Corporation 7500/5520/5500/X58 Trusted Execution Technology Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation SATA Controller [RAID mode]
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 SATA controller: Marvell Technology Group Ltd. Device 9182 (rev 10)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]
05:00.0 Audio device: Creative Labs EMU20k2 [X-Fi Titanium Series] (rev 03)
06:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
07:00.0 Power PC: Freescale Semiconductor Inc MPC8308 (rev 10)
08:00.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
3f:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
3f:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
3f:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
3f:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
3f:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
3f:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
3f:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
3f:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
3f:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
3f:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
3f:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
3f:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
3f:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
3f:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
3f:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
3f:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
freeman@Sniper-one:~$ uname -r
4.3.0-5-generic
freeman@Sniper-one:~$ lsusb
Bus 004 Device 002: ID 059f:105e LaCie, Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 2109:3431 VIA Labs, Inc. Hub
Bus 003 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 2109:0810 VIA Labs, Inc. VL81x Hub
Bus 002 Device 002: ID 2109:0810 VIA Labs, Inc. VL81x Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

i tried to put graphic setting in low-mode (radeon R9 !) everywhere, it's the same thing, first the audio crash sometimes i can "ctrl echap"; sometimes no, nothing is possible just put 4s start power and reboot

I USE  :  the experimental version ! but it's the same thing in normal version

thanks for regards,

do i install proprio-driver Radéon ?

update is better now i crash less and i can't need to reboot, but i crash again one time in 10 hours of game

NEW !  ```
freeman@Sniper-one:~$ steam Running Steam on ubuntu 16.04 64-bit STEAM_RUNTIME is enabled automatically Installing breakpad exception handler for appid(steam)/version(0) libGL error: unable to load driver: radeonsi_dri.so libGL error: driver pointer missing libGL error: failed to load driver: radeonsi libGL error: unable to load driver: swrast_dri.so libGL error: failed to load driver: swrast
```

and don't want start  with unity too, on AMDphenom1055t 6850Radeon 8GRam SSD samsung 840 Xenial : ```
freeman@freeman-II:~$ inxi -b System:    Host: freeman-II Kernel: 4.4.0-8-generic x86_64 (64 bit) Desktop: Unity 7.4.0            Distro: Ubuntu 16.04 xenial Machine:   Mobo: ASUSTeK model: M5A97 LE R2.0 v: Rev 1.xx Bios: American Megatrends v: 1903 date: 07/11/2013 CPU:       Hexa core AMD Phenom II X6 1055T (-MCP-) speed/max: 800/2800 MHz Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts PRO [Radeon HD 6850]            Display Server: X.Org 1.17.3 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1280x1024@60.02hz            GLX Renderer: Gallium 0.4 on AMD BARTS (DRM 2.43.0, LLVM 3.8.0) GLX Version: 3.0 Mesa 11.1.2 Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169            Card-2: Ralink RT5370 Wireless Adapter driver: rt2800usb Drives:    HDD Total Size: 2500.5GB (32.2% used) Info:      Processes: 292 Uptime: 2:58 Memory: 1869.5/7966.0MB Client: Shell (bash) inxi: 2.2.33   freeman@freeman-II:~$ steam Running Steam on ubuntu 16.04 64-bit STEAM_RUNTIME is enabled automatically [2016-02-28 05:12:45] Startup - updater built Feb  4 2016 12:22:08 SteamUpdateUI: An X Error occurred X Error of failed request:  BadValue (integer parameter out of range for operation)
```

But works fine on my second config  after install fglrx and the today update to steam !

```
freeman@freeman-II:~$ inxi -b
**System:    Host: freeman-II Kernel: 4.4.0-8-generic x86_64 (64 bit)** Desktop: Unity Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: M5A97 LE R2.0 v: Rev 1.xx Bios: American Megatrends v: 1903 date: 07/11/2013
CPU:       Hexa core AMD Phenom II X6 1055T (-MCP-) speed/max: 800/2800 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts PRO [Radeon HD 6850]
           Display Server: X.Org 1.17.3 drivers: ati,fglrx (unloaded: fbdev,vesa,radeon)
           Resolution: 1280x1024@60.02hz
           GLX Renderer: AMD Radeon HD 6800 Series GLX Version: 4.5.13399 - CPC 15.201.1151
```

under Cairo-dock session (yes i shoot Unity and install Gnome Desktop, just fine !)

---

### Post by valereguerin on 2016-02-28
nobody ?

---

### Post by valereguerin on 2016-03-17
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc

---

### Post by valereguerin on 2016-04-09
[URL="https://wirejungle.wordpress.com/2015/01/09/how-to-fix-broken-steam-linux-client-with-radeon-graphics-driver-workaround/"]https://wirejungle.wordpress.com/2015/01/09/how-to-fix-broken-steam-linux-client-with-radeon-graphics-driver-workaround/



for me : 

```
LD_PRELOAD='/usr/$LIB/libstdc++.so.6' DIAPLAY=:0 steam
```


:(:(:(i put this command-line in the terminal after [COLOR=#ff0000]every[/COLOR] update/upgrade.........
[/URL]

---

### Post by valereguerin on 2016-04-09
thanks ....for.....support......

---

### Post by valereguerin on 2016-04-21
```
No cached sticky mapping in GetActionSetHandle. Native Steam Controller support won't work.
```


but i can play....

---

### Post by valereguerin on 2016-05-09
[URL="https://wirejungle.wordpress.com/2015/01/09/how-to-fix-broken-steam-linux-client-with-radeon-graphics-driver-workaround/"] 	Code:
 	LD_PRELOAD='/usr/$LIB/libstdc++.so.6' DIAPLAY=:0 steam 

:sad::sad::sad:i put this command-line in the terminal after [SIZE=6][COLOR=#ff0000]every[/COLOR][/SIZE] update/upgrade.........[/URL]

and now the steam window not appear on my desktop i must looking for it on another desktop !. ????

---

### Post by cariboo on 2016-05-09
Again, this thread is about problems with Xenial. We are now testing Yakkety. Time to move on, thread closed.

---

