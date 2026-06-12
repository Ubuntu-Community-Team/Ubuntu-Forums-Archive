---
title: "Upgrade to 4.4.0.6.7 'kills' monitor (HDMI)"
date: 2016-02-27
forum: Ubuntu Development Version
---

### Post by fantab on 2016-02-27
**HDMI** connected Monitor does not receive any signal from **kernel 4.4.0.6.7** [Ubuntu 4.4.0-6.21-generic 4.4.1]
Monitor complains of "No Signal" and goes to standby. 
I can hear the 'desktop ready' sound; also when I just type password to login I can hear the sound of a successful login. However the Monitor stays in standby/sleep mode.

I am currently booting the previous kernel:
```
$ uname -r
4.3.0-7-generic
```

The previously released Kernel 4.3 boots fine. 

My graphics are from Intel G45/G43 and so is the Mobo... no UEFI , its a legacy board.
```
$ lspci 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection
```

There is nothing in the ***journalctl -b ***that is of help. [https://paste.ubuntu.com/15214111/](https://paste.ubuntu.com/15214111/)
 The ***xorg.log*** too has nothing striking. [https://paste.ubuntu.com/15214133/](https://paste.ubuntu.com/15214133/)

I hope the forum can take a look at the above file and help me understand the issue.
I can share more files and info if needed.

Thanks for the time.

Regards

---

### Post by rockorequin on 2016-03-03
I have the same problem. Kernels 4.2 and 4.5-rc6 work fine, but 4.4 doesn't detect anything on HDMI. It seems it might be a known problem - see [http://www.gossamer-threads.com/lists/linux/kernel/2349389](http://www.gossamer-threads.com/lists/linux/kernel/2349389) and [https://lkml.org/lkml/2016/2/8/123](https://lkml.org/lkml/2016/2/8/123), although it's surprising there's still no patch as of 4th of March.

---

### Post by fantab on 2016-03-03
And the problem/bug seems to be kernel related (probably an upstream issue) as the same bug haunts me on Archlinux. Here too I had to downgrade the kernel.

---

### Post by valereguerin on 2016-03-11
4.4.0.6 after upgrade black screen or sometimes white screen with mouse only
i tape my password for enter into my session, 
you see always nothing just mouse !
ctrl+alt+T (console) (i see always nothing on screen...) 
my login, enter
my password, enter

sudo apt-get update && sudo apt-get upgrade, enter, password, enter ; wait 10 minutes because you don't see always anything ! (forget screen just do like habit , like you haven't eyes)

and 

sudo reboot now

At reboot i have console 1,2...6 and i can see  my screen now !
But gdm3 don't want initialised....

i have solved the problem : sudo apt-get remove fglrx-core....sudo reboot now

Everything is perfect now

advanced option in grub like upstart (do nothing more) and recovery mode don't want accept my root password... for root console ....after network open in the recovery mode options....

---

### Post by fantab on 2016-03-11
> **valereguerin said:**
> ...But gdm don't want initialised....

i have solved the problem : sudo apt-get remove fglrx-core....sudo reboot now

Everything is perfect now

GDM or LightDM? what flavor of Ubuntu you are on? Gnome?
What Graphics do you have? The issue appears to bug only certain Intels... AFAIK...

---

### Post by valereguerin on 2016-03-11
Gdm3 !

```
freeman@Sniper-one:~$ inxi -b
System:    Host: Sniper-one Kernel: 4.4.0-6-generic x86_64 (64 bit) Desktop: Gnome 3.18.4
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2860 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.18.1 drivers: ati (unloaded: fbdev,vesa,radeon) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.8.0) GLX Version: 3.0 Mesa 11.1.2
Network:   Card-1: D-Link System DGE-528T Gigabit Ethernet Adapter driver: r8169
           Card-2: Realtek RTL8187 Wireless Adapter driver: rtl8187
Drives:    HDD Total Size: 5815.3GB (5.7% used)
Info:      Processes: 321 Uptime: 28 min Memory: 2483.1/7853.0MB Client: Shell (bash) inxi: 2.2.35 

```

i had Unity but crash, i shoot unity and install Gnome desktop with gdm but GDM3 !
everything works fine and arrive update with 4.4.6 and at reboot black/white screen with mouse only.

```
 

[   114.211] (--) Log file renamed from "/var/log/Xorg.pid-9460.log" to "/var/log/Xorg.0.log"
[   114.212] 
X.Org X Server 1.18.1
Release Date: 2016-02-08
[   114.212] X Protocol Version 11, Revision 0
[   114.212] Build Operating System: Linux 3.13.0-79-generic x86_64 Ubuntu
[   114.212] Current Operating System: Linux Sniper-one 4.4.0-6-generic #21-Ubuntu SMP Tue Feb 16 20:32:27 UTC 2016 x86_64
[   114.212] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-6-generic root=UUID=xxxxxx-xxxx-xxxxx-xxxxx-xxxx106 ro persistent quiet splash crashkernel=384M-:128M crashkernel=384M-:128M crashkernel=384M-:128M crashkernel=384M-:128M crashkernel=384M-:128M
[   114.212] Build Date: 03 March 2016  10:01:47AM
[   114.212] xorg-server 2:1.18.1-1ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[   114.212] Current version of pixman: 0.33.6
[   114.212]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   114.212] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   114.212] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 11 12:54:26 2016
[   114.212] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   114.212] (==) No Layout section.  Using the first Screen section.
[   114.212] (==) No screen section available. Using defaults.
[   114.212] (**) |-->Screen "Default Screen Section" (0)
[   114.212] (**) |   |-->Monitor "<default monitor>"
[   114.212] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   114.213] (==) Automatically adding devices
[   114.213] (==) Automatically enabling devices
[   114.213] (==) Automatically adding GPU devices
[   114.213] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   114.213] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   114.213]     Entry deleted from font path.
[   114.213] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[   114.213] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   114.213] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   114.213] (II) Loader magic: 0x563feadf5dc0
[   114.213] (II) Module ABI versions:
[   114.213]     X.Org ANSI C Emulation: 0.4
[   114.213]     X.Org Video Driver: 20.0
[   114.213]     X.Org XInput driver : 22.1
[   114.213]     X.Org Server Extension : 9.0
[   114.213] (++) using VT number 7

[   114.215] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c25
[   114.216] (--) PCI:*(0:3:0:0) 1002:679a:174b:a003 rev 0, Mem @ 0xe0000000/268435456, 0xfba80000/262144, I/O @ 0x0000be00/256, BIOS @ 0x????????/131072
[   114.217] (II) LoadModule: "glx"
[   114.217] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   114.217] (II) Module glx: vendor="X.Org Foundation"
[   114.217]     compiled for 1.18.1, module version = 1.0.0
[   114.217]     ABI class: X.Org Server Extension, version 9.0
[   114.217] (==) AIGLX enabled
[   114.217] (==) Matched fglrx as autoconfigured driver 0
[   114.217] (==) Matched ati as autoconfigured driver 1
[   114.217] (==) Matched modesetting as autoconfigured driver 2
[   114.217] (==) Matched fbdev as autoconfigured driver 3
[   114.217] (==) Matched vesa as autoconfigured driver 4
[   114.217] (==) Assigned the driver to the xf86ConfigLayout
[   114.217] (II) LoadModule: "fglrx"
[   114.218] (WW) Warning, couldn't open module fglrx
[   114.218] (II) UnloadModule: "fglrx"
[   114.218] (II) Unloading fglrx
[   114.218] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   114.218] (II) LoadModule: "ati"
[   114.218] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   114.218] (II) Module ati: vendor="X.Org Foundation"
[   114.218]     compiled for 1.18.1, module version = 7.6.1
[   114.218]     Module class: X.Org Video Driver
[   114.218]     ABI class: X.Org Video Driver, version 20.0
[   114.218] (II) LoadModule: "radeon"
[   114.218] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   114.218] (II) Module radeon: vendor="X.Org Foundation"
[   114.218]     compiled for 1.18.1, module version = 7.6.1
[   114.218]     Module class: X.Org Video Driver
[   114.218]     ABI class: X.Org Video Driver, version 20.0
[   114.218] (II) LoadModule: "modesetting"
[   114.218] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   114.218] (II) Module modesetting: vendor="X.Org Foundation"
[   114.218]     compiled for 1.18.1, module version = 1.18.1
[   114.218]     Module class: X.Org Video Driver
[   114.218]     ABI class: X.Org Video Driver, version 20.0
[   114.218] (II) LoadModule: "fbdev"
[   114.218] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   114.218] (II) Module fbdev: vendor="X.Org Foundation"
[   114.218]     compiled for 1.18.1, module version = 0.4.4
[   114.218]     Module class: X.Org Video Driver
[   114.218]     ABI class: X.Org Video Driver, version 20.0
[   114.218] (II) LoadModule: "vesa"
[   114.219] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   114.219] (II) Module vesa: vendor="X.Org Foundation"
[   114.219]     compiled for 1.18.1, module version = 2.3.4
[   114.219]     Module class: X.Org Video Driver
[   114.219]     ABI class: X.Org Video Driver, version 20.0
[   114.219] (==) Matched fglrx as autoconfigured driver 0
[   114.219] (==) Matched ati as autoconfigured driver 1
[   114.219] (==) Matched modesetting as autoconfigured driver 2
[   114.219] (==) Matched fbdev as autoconfigured driver 3
[   114.219] (==) Matched vesa as autoconfigured driver 4
[   114.219] (==) Assigned the driver to the xf86ConfigLayout
[   114.219] (II) LoadModule: "fglrx"
[   114.219] (WW) Warning, couldn't open module fglrx
[   114.219] (II) UnloadModule: "fglrx"
[   114.219] (II) Unloading fglrx
[   114.219] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   114.219] (II) LoadModule: "ati"
[   114.219] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   114.219] (II) Module ati: vendor="X.Org Foundation"
[   114.219]     compiled for 1.18.1, module version = 7.6.1
[   114.219]     Module class: X.Org Video Driver
[   114.219]     ABI class: X.Org Video Driver, version 20.0
[   114.219] (II) LoadModule: "modesetting"
[   114.219] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   114.219] (II) Module modesetting: vendor="X.Org Foundation"
[   114.219]     compiled for 1.18.1, module version = 1.18.1
[   114.219]     Module class: X.Org Video Driver
[   114.219]     ABI class: X.Org Video Driver, version 20.0
[   114.219] (II) UnloadModule: "modesetting"
[   114.219] (II) Unloading modesetting
[   114.219] (II) Failed to load module "modesetting" (already loaded, 0)
[   114.219] (II) LoadModule: "fbdev"
[   114.219] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   114.219] (II) Module fbdev: vendor="X.Org Foundation"
[   114.219]     compiled for 1.18.1, module version = 0.4.4
[   114.219]     Module class: X.Org Video Driver
[   114.219]     ABI class: X.Org Video Driver, version 20.0
[   114.219] (II) UnloadModule: "fbdev"
[   114.219] (II) Unloading fbdev
[   114.219] (II) Failed to load module "fbdev" (already loaded, 0)
[   114.219] (II) LoadModule: "vesa"
[   114.220] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   114.220] (II) Module vesa: vendor="X.Org Foundation"
[   114.220]     compiled for 1.18.1, module version = 2.3.4
[   114.220]     Module class: X.Org Video Driver
[   114.220]     ABI class: X.Org Video Driver, version 20.0
[   114.220] (II) UnloadModule: "vesa"
[   114.220] (II) Unloading vesa
[   114.220] (II) Failed to load module "vesa" (already loaded, 0)
[   114.220] (II) RADEON: Driver for ATI Radeon chipsets:
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
[   114.228] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   114.228] (II) FBDEV: driver for framebuffer: fbdev
[   114.228] (II) VESA: driver for VESA chipsets: vesa
[   114.228] (II) [KMS] drm report modesetting isn't supported.
[   114.228] (EE) open /dev/dri/card0: No such file or directory
[   114.228] (EE) open /dev/dri/card0: No such file or directory
[   114.228] (WW) Falling back to old probe method for modesetting
[   114.228] (EE) open /dev/dri/card0: No such file or directory
[   114.228] (EE) open /dev/dri/card0: No such file or directory
[   114.228] (II) Loading sub module "fbdevhw"
[   114.228] (II) LoadModule: "fbdevhw"
[   114.228] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   114.228] (II) Module fbdevhw: vendor="X.Org Foundation"
[   114.228]     compiled for 1.18.1, module version = 0.0.2
[   114.228]     ABI class: X.Org Video Driver, version 20.0
[   114.228] (EE) open /dev/fb0: No such file or directory
[   114.228] (II) Loading sub module "fbdevhw"
[   114.228] (II) LoadModule: "fbdevhw"
[   114.228] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   114.228] (II) Module fbdevhw: vendor="X.Org Foundation"
[   114.228]     compiled for 1.18.1, module version = 0.0.2
[   114.228]     ABI class: X.Org Video Driver, version 20.0
[   114.228] (EE) open /dev/fb0: No such file or directory
[   114.229] (WW) Falling back to old probe method for fbdev
[   114.229] (II) Loading sub module "fbdevhw"
[   114.229] (II) LoadModule: "fbdevhw"
[   114.229] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   114.229] (II) Module fbdevhw: vendor="X.Org Foundation"
[   114.229]     compiled for 1.18.1, module version = 0.0.2
[   114.229]     ABI class: X.Org Video Driver, version 20.0
[   114.229] (EE) open /dev/fb0: No such file or directory
[   114.229] (EE) open /dev/fb0: No such file or directory
[   114.229] vesa: Ignoring device with a bound kernel driver
[   114.229] (WW) Falling back to old probe method for vesa
[   114.229] (EE) Screen 0 deleted because of no matching config section.
[   114.229] (II) UnloadModule: "radeon"
[   114.229] (EE) Screen 0 deleted because of no matching config section.
[   114.229] (II) UnloadModule: "modesetting"
[   114.229] (EE) Screen 0 deleted because of no matching config section.
[   114.229] (II) UnloadModule: "modesetting"
[   114.229] (EE) Screen 0 deleted because of no matching config section.
[   114.229] (II) UnloadModule: "fbdev"
[   114.229] (II) UnloadSubModule: "fbdevhw"
[   114.229] (EE) Screen 0 deleted because of no matching config section.
[   114.229] (II) UnloadModule: "fbdev"
[   114.229] (II) UnloadSubModule: "fbdevhw"
[   114.229] (II) UnloadSubModule: "fbdevhw"
[   114.229] (EE) Screen 0 deleted because of no matching config section.
[   114.229] (II) UnloadModule: "vesa"
[   114.229] (EE) Device(s) detected, but none match those in the config file.
[   114.229] (EE) 
Fatal server error:
[   114.229] (EE) no screens found(EE) 
[   114.229] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   114.229] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   114.229] (EE) 
[   114.230] (EE) Server terminated with error (1). Closing log file.
```

dpkg.log
```


2016-03-11 12:23:59 startup archives unpack
2016-03-11 12:24:09 upgrade bsdmainutils:amd64 9.0.6ubuntu2 9.0.6ubuntu3
2016-03-11 12:24:09 status half-configured bsdmainutils:amd64 9.0.6ubuntu2
2016-03-11 12:24:09 status unpacked bsdmainutils:amd64 9.0.6ubuntu2
2016-03-11 12:24:09 status half-installed bsdmainutils:amd64 9.0.6ubuntu2
2016-03-11 12:24:09 status triggers-pending man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:24:09 status half-installed bsdmainutils:amd64 9.0.6ubuntu2
2016-03-11 12:24:09 status unpacked bsdmainutils:amd64 9.0.6ubuntu3
2016-03-11 12:24:09 status unpacked bsdmainutils:amd64 9.0.6ubuntu3
2016-03-11 12:24:10 upgrade bsdutils:amd64 1:2.27.1-3ubuntu1 1:2.27.1-4ubuntu1
2016-03-11 12:24:10 status half-configured bsdutils:amd64 1:2.27.1-3ubuntu1
2016-03-11 12:24:10 status unpacked bsdutils:amd64 1:2.27.1-3ubuntu1
2016-03-11 12:24:10 status half-installed bsdutils:amd64 1:2.27.1-3ubuntu1
2016-03-11 12:24:10 status half-installed bsdutils:amd64 1:2.27.1-3ubuntu1
2016-03-11 12:24:10 status unpacked bsdutils:amd64 1:2.27.1-4ubuntu1
2016-03-11 12:24:10 status unpacked bsdutils:amd64 1:2.27.1-4ubuntu1
2016-03-11 12:24:10 startup packages configure
2016-03-11 12:24:10 configure bsdutils:amd64 1:2.27.1-4ubuntu1 <aucune>
2016-03-11 12:24:10 status unpacked bsdutils:amd64 1:2.27.1-4ubuntu1
2016-03-11 12:24:10 status half-configured bsdutils:amd64 1:2.27.1-4ubuntu1
2016-03-11 12:24:11 status installed bsdutils:amd64 1:2.27.1-4ubuntu1
2016-03-11 12:24:11 startup archives unpack
2016-03-11 12:24:11 upgrade libperl5.22:amd64 5.22.1-7 5.22.1-8
2016-03-11 12:24:11 status half-configured libperl5.22:amd64 5.22.1-7
2016-03-11 12:24:11 status unpacked libperl5.22:amd64 5.22.1-7
2016-03-11 12:24:11 status half-installed libperl5.22:amd64 5.22.1-7
2016-03-11 12:24:13 status half-installed libperl5.22:amd64 5.22.1-7
2016-03-11 12:24:14 status unpacked libperl5.22:amd64 5.22.1-8
2016-03-11 12:24:14 status unpacked libperl5.22:amd64 5.22.1-8
2016-03-11 12:24:14 upgrade perl:amd64 5.22.1-7 5.22.1-8
2016-03-11 12:24:14 status half-configured perl:amd64 5.22.1-7
2016-03-11 12:24:14 status unpacked perl:amd64 5.22.1-7
2016-03-11 12:24:14 status half-installed perl:amd64 5.22.1-7
2016-03-11 12:24:14 status half-installed perl:amd64 5.22.1-7
2016-03-11 12:24:14 status unpacked perl:amd64 5.22.1-8
2016-03-11 12:24:14 status unpacked perl:amd64 5.22.1-8
2016-03-11 12:24:15 upgrade perl-base:amd64 5.22.1-7 5.22.1-8
2016-03-11 12:24:15 status half-configured perl-base:amd64 5.22.1-7
2016-03-11 12:24:15 status unpacked perl-base:amd64 5.22.1-7
2016-03-11 12:24:15 status half-installed perl-base:amd64 5.22.1-7
2016-03-11 12:24:15 status half-installed perl-base:amd64 5.22.1-7
2016-03-11 12:24:16 status unpacked perl-base:amd64 5.22.1-8
2016-03-11 12:24:16 status unpacked perl-base:amd64 5.22.1-8
2016-03-11 12:24:16 startup packages configure
2016-03-11 12:24:16 configure perl-base:amd64 5.22.1-8 <aucune>
2016-03-11 12:24:16 status unpacked perl-base:amd64 5.22.1-8
2016-03-11 12:24:16 status half-configured perl-base:amd64 5.22.1-8
2016-03-11 12:24:16 status installed perl-base:amd64 5.22.1-8
2016-03-11 12:24:16 startup archives unpack
2016-03-11 12:24:16 upgrade perl-modules-5.22:all 5.22.1-7 5.22.1-8
2016-03-11 12:24:16 status half-configured perl-modules-5.22:all 5.22.1-7
2016-03-11 12:24:17 status unpacked perl-modules-5.22:all 5.22.1-7
2016-03-11 12:24:17 status half-installed perl-modules-5.22:all 5.22.1-7
2016-03-11 12:24:18 status half-installed perl-modules-5.22:all 5.22.1-7
2016-03-11 12:24:19 status unpacked perl-modules-5.22:all 5.22.1-8
2016-03-11 12:24:19 status unpacked perl-modules-5.22:all 5.22.1-8
2016-03-11 12:24:19 upgrade init-system-helpers:all 1.28ubuntu2 1.29ubuntu1
2016-03-11 12:24:19 status half-configured init-system-helpers:all 1.28ubuntu2
2016-03-11 12:24:19 status unpacked init-system-helpers:all 1.28ubuntu2
2016-03-11 12:24:19 status half-installed init-system-helpers:all 1.28ubuntu2
2016-03-11 12:24:19 status half-installed init-system-helpers:all 1.28ubuntu2
2016-03-11 12:24:19 status unpacked init-system-helpers:all 1.29ubuntu1
2016-03-11 12:24:19 status unpacked init-system-helpers:all 1.29ubuntu1
2016-03-11 12:24:20 startup packages configure
2016-03-11 12:24:20 configure init-system-helpers:all 1.29ubuntu1 <aucune>
2016-03-11 12:24:20 status unpacked init-system-helpers:all 1.29ubuntu1
2016-03-11 12:24:20 status half-configured init-system-helpers:all 1.29ubuntu1
2016-03-11 12:24:20 status installed init-system-helpers:all 1.29ubuntu1
2016-03-11 12:24:20 startup archives unpack
2016-03-11 12:24:20 upgrade init:amd64 1.28ubuntu2 1.29ubuntu1
2016-03-11 12:24:20 status half-configured init:amd64 1.28ubuntu2
2016-03-11 12:24:20 status unpacked init:amd64 1.28ubuntu2
2016-03-11 12:24:20 status half-installed init:amd64 1.28ubuntu2
2016-03-11 12:24:20 status half-installed init:amd64 1.28ubuntu2
2016-03-11 12:24:21 status unpacked init:amd64 1.29ubuntu1
2016-03-11 12:24:21 status unpacked init:amd64 1.29ubuntu1
2016-03-11 12:24:21 startup packages configure
2016-03-11 12:24:21 configure init:amd64 1.29ubuntu1 <aucune>
2016-03-11 12:24:21 status unpacked init:amd64 1.29ubuntu1
2016-03-11 12:24:21 status half-configured init:amd64 1.29ubuntu1
2016-03-11 12:24:21 status installed init:amd64 1.29ubuntu1
2016-03-11 12:24:21 startup archives unpack
2016-03-11 12:24:22 upgrade login:amd64 1:4.2-3.1ubuntu3 1:4.2-3.1ubuntu4
2016-03-11 12:24:22 status half-configured login:amd64 1:4.2-3.1ubuntu3
2016-03-11 12:24:22 status unpacked login:amd64 1:4.2-3.1ubuntu3
2016-03-11 12:24:22 status half-installed login:amd64 1:4.2-3.1ubuntu3
2016-03-11 12:24:22 status half-installed login:amd64 1:4.2-3.1ubuntu3
2016-03-11 12:24:22 status unpacked login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:22 status unpacked login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:22 startup packages configure
2016-03-11 12:24:22 configure login:amd64 1:4.2-3.1ubuntu4 <aucune>
2016-03-11 12:24:22 status unpacked login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:22 status unpacked login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:22 status unpacked login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:23 status unpacked login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:23 status unpacked login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:23 status half-configured login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:23 status installed login:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:23 startup archives unpack
2016-03-11 12:24:23 upgrade util-linux:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:24:23 status half-configured util-linux:amd64 2.27.1-3ubuntu1
2016-03-11 12:24:23 status unpacked util-linux:amd64 2.27.1-3ubuntu1
2016-03-11 12:24:23 status half-installed util-linux:amd64 2.27.1-3ubuntu1
2016-03-11 12:24:24 status triggers-pending systemd:amd64 229-2ubuntu1
2016-03-11 12:24:24 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:24:24 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:24:24 status triggers-pending mime-support:all 3.59ubuntu1
2016-03-11 12:24:24 status half-installed util-linux:amd64 2.27.1-3ubuntu1
2016-03-11 12:24:25 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:25 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:25 trigproc ureadahead:amd64 0.100.0-19build~pie.1 <aucune>
2016-03-11 12:24:25 status half-configured ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:24:25 status installed ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:24:25 trigproc mime-support:all 3.59ubuntu1 <aucune>
2016-03-11 12:24:25 status half-configured mime-support:all 3.59ubuntu1
2016-03-11 12:24:26 status installed mime-support:all 3.59ubuntu1
2016-03-11 12:24:27 startup packages configure
2016-03-11 12:24:27 configure util-linux:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:24:27 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:28 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:28 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:28 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:28 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:28 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:28 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:28 status unpacked util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:28 status half-configured util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:30 status installed util-linux:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:30 trigproc systemd:amd64 229-2ubuntu1 <aucune>
2016-03-11 12:24:30 status half-configured systemd:amd64 229-2ubuntu1
2016-03-11 12:24:30 status installed systemd:amd64 229-2ubuntu1
2016-03-11 12:24:30 startup archives unpack
2016-03-11 12:24:30 upgrade mount:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:24:30 status half-configured mount:amd64 2.27.1-3ubuntu1
2016-03-11 12:24:31 status unpacked mount:amd64 2.27.1-3ubuntu1
2016-03-11 12:24:31 status half-installed mount:amd64 2.27.1-3ubuntu1
2016-03-11 12:24:31 status half-installed mount:amd64 2.27.1-3ubuntu1
2016-03-11 12:24:31 status unpacked mount:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:31 status unpacked mount:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:31 startup packages configure
2016-03-11 12:24:31 configure mount:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:24:31 status unpacked mount:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:31 status half-configured mount:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:31 status installed mount:amd64 2.27.1-4ubuntu1
2016-03-11 12:24:32 startup archives unpack
2016-03-11 12:24:32 upgrade libapt-pkg-dev:amd64 1.2.3 1.2.4
2016-03-11 12:24:32 status half-configured libapt-pkg-dev:amd64 1.2.3
2016-03-11 12:24:32 status unpacked libapt-pkg-dev:amd64 1.2.3
2016-03-11 12:24:32 status half-installed libapt-pkg-dev:amd64 1.2.3
2016-03-11 12:24:32 status half-installed libapt-pkg-dev:amd64 1.2.3
2016-03-11 12:24:32 status unpacked libapt-pkg-dev:amd64 1.2.4
2016-03-11 12:24:32 status unpacked libapt-pkg-dev:amd64 1.2.4
2016-03-11 12:24:33 upgrade libapt-inst2.0:amd64 1.2.3 1.2.4
2016-03-11 12:24:33 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:33 status half-configured libapt-inst2.0:amd64 1.2.3
2016-03-11 12:24:33 status unpacked libapt-inst2.0:amd64 1.2.3
2016-03-11 12:24:33 status half-installed libapt-inst2.0:amd64 1.2.3
2016-03-11 12:24:33 status half-installed libapt-inst2.0:amd64 1.2.3
2016-03-11 12:24:33 status unpacked libapt-inst2.0:amd64 1.2.4
2016-03-11 12:24:33 status unpacked libapt-inst2.0:amd64 1.2.4
2016-03-11 12:24:34 upgrade libapt-pkg5.0:amd64 1.2.3 1.2.4
2016-03-11 12:24:34 status half-configured libapt-pkg5.0:amd64 1.2.3
2016-03-11 12:24:34 status unpacked libapt-pkg5.0:amd64 1.2.3
2016-03-11 12:24:34 status half-installed libapt-pkg5.0:amd64 1.2.3
2016-03-11 12:24:34 status half-installed libapt-pkg5.0:amd64 1.2.3
2016-03-11 12:24:34 status unpacked libapt-pkg5.0:amd64 1.2.4
2016-03-11 12:24:34 status unpacked libapt-pkg5.0:amd64 1.2.4
2016-03-11 12:24:34 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:24:34 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:35 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:35 startup packages configure
2016-03-11 12:24:35 configure libapt-pkg5.0:amd64 1.2.4 <aucune>
2016-03-11 12:24:35 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:35 status unpacked libapt-pkg5.0:amd64 1.2.4
2016-03-11 12:24:35 status half-configured libapt-pkg5.0:amd64 1.2.4
2016-03-11 12:24:35 status installed libapt-pkg5.0:amd64 1.2.4
2016-03-11 12:24:35 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:24:35 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:35 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:36 startup archives unpack
2016-03-11 12:24:36 upgrade apt:amd64 1.2.3 1.2.4
2016-03-11 12:24:36 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:36 status half-configured apt:amd64 1.2.3
2016-03-11 12:24:36 status unpacked apt:amd64 1.2.3
2016-03-11 12:24:36 status half-installed apt:amd64 1.2.3
2016-03-11 12:24:37 status half-installed apt:amd64 1.2.3
2016-03-11 12:24:37 status unpacked apt:amd64 1.2.4
2016-03-11 12:24:37 status unpacked apt:amd64 1.2.4
2016-03-11 12:24:37 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:24:37 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:37 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:38 startup packages configure
2016-03-11 12:24:38 configure apt:amd64 1.2.4 <aucune>
2016-03-11 12:24:38 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:38 status unpacked apt:amd64 1.2.4
2016-03-11 12:24:38 status unpacked apt:amd64 1.2.4
2016-03-11 12:24:38 status unpacked apt:amd64 1.2.4
2016-03-11 12:24:38 status unpacked apt:amd64 1.2.4
2016-03-11 12:24:38 status unpacked apt:amd64 1.2.4
2016-03-11 12:24:38 status unpacked apt:amd64 1.2.4
2016-03-11 12:24:38 status half-configured apt:amd64 1.2.4
2016-03-11 12:24:38 status installed apt:amd64 1.2.4
2016-03-11 12:24:38 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:24:38 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:38 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:38 startup archives unpack
2016-03-11 12:24:39 upgrade apt-utils:amd64 1.2.3 1.2.4
2016-03-11 12:24:39 status half-configured apt-utils:amd64 1.2.3
2016-03-11 12:24:39 status unpacked apt-utils:amd64 1.2.3
2016-03-11 12:24:39 status half-installed apt-utils:amd64 1.2.3
2016-03-11 12:24:39 status half-installed apt-utils:amd64 1.2.3
2016-03-11 12:24:39 status unpacked apt-utils:amd64 1.2.4
2016-03-11 12:24:39 status unpacked apt-utils:amd64 1.2.4
2016-03-11 12:24:39 upgrade libgtk-3-common:all 3.18.8-1ubuntu1 3.18.8-1ubuntu2
2016-03-11 12:24:39 status half-configured libgtk-3-common:all 3.18.8-1ubuntu1
2016-03-11 12:24:40 status unpacked libgtk-3-common:all 3.18.8-1ubuntu1
2016-03-11 12:24:40 status half-installed libgtk-3-common:all 3.18.8-1ubuntu1
2016-03-11 12:24:40 status triggers-pending libglib2.0-0:i386 2.47.6-1
2016-03-11 12:24:40 status half-installed libgtk-3-common:all 3.18.8-1ubuntu1
2016-03-11 12:24:40 status triggers-pending libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:24:40 status half-installed libgtk-3-common:all 3.18.8-1ubuntu1
2016-03-11 12:24:40 status half-installed libgtk-3-common:all 3.18.8-1ubuntu1
2016-03-11 12:24:40 status unpacked libgtk-3-common:all 3.18.8-1ubuntu2
2016-03-11 12:24:40 status unpacked libgtk-3-common:all 3.18.8-1ubuntu2
2016-03-11 12:24:41 upgrade libgtk-3-0-dbg:amd64 3.18.8-1ubuntu1 3.18.8-1ubuntu2
2016-03-11 12:24:41 status half-configured libgtk-3-0-dbg:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:41 status unpacked libgtk-3-0-dbg:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:41 status half-installed libgtk-3-0-dbg:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:41 status half-installed libgtk-3-0-dbg:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:42 status unpacked libgtk-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:42 status unpacked libgtk-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:42 upgrade libgail-3-0-dbg:amd64 3.18.8-1ubuntu1 3.18.8-1ubuntu2
2016-03-11 12:24:42 status half-configured libgail-3-0-dbg:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:42 status unpacked libgail-3-0-dbg:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:42 status half-installed libgail-3-0-dbg:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:42 status half-installed libgail-3-0-dbg:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:42 status unpacked libgail-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:42 status unpacked libgail-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:43 upgrade libgail-3-0:amd64 3.18.8-1ubuntu1 3.18.8-1ubuntu2
2016-03-11 12:24:43 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:43 status half-configured libgail-3-0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:43 status unpacked libgail-3-0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:43 status half-installed libgail-3-0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:43 status half-installed libgail-3-0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:43 status unpacked libgail-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:43 status unpacked libgail-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:43 upgrade libfontconfig1:i386 2.11.1-0ubuntu7 2.11.1-0ubuntu8
2016-03-11 12:24:43 status half-configured libfontconfig1:i386 2.11.1-0ubuntu7
2016-03-11 12:24:43 status unpacked libfontconfig1:i386 2.11.1-0ubuntu7
2016-03-11 12:24:43 status half-configured libfontconfig1:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:43 status half-installed libfontconfig1:i386 2.11.1-0ubuntu7
2016-03-11 12:24:44 status half-installed libfontconfig1:i386 2.11.1-0ubuntu7
2016-03-11 12:24:44 status unpacked libfontconfig1:i386 2.11.1-0ubuntu8
2016-03-11 12:24:44 status unpacked libfontconfig1:i386 2.11.1-0ubuntu8
2016-03-11 12:24:44 upgrade libfontconfig1:amd64 2.11.1-0ubuntu7 2.11.1-0ubuntu8
2016-03-11 12:24:44 status half-configured libfontconfig1:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:44 status unpacked libfontconfig1:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:44 status half-installed libfontconfig1:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:44 status half-installed libfontconfig1:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:44 status unpacked libfontconfig1:amd64 2.11.1-0ubuntu8
2016-03-11 12:24:44 status unpacked libfontconfig1:amd64 2.11.1-0ubuntu8
2016-03-11 12:24:44 upgrade libfontconfig1-dev:amd64 2.11.1-0ubuntu7 2.11.1-0ubuntu8
2016-03-11 12:24:44 status half-configured libfontconfig1-dev:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:45 status unpacked libfontconfig1-dev:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:45 status half-installed libfontconfig1-dev:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:45 status triggers-pending doc-base:all 0.10.7
2016-03-11 12:24:45 status half-installed libfontconfig1-dev:amd64 2.11.1-0ubuntu7
2016-03-11 12:24:45 status unpacked libfontconfig1-dev:amd64 2.11.1-0ubuntu8
2016-03-11 12:24:45 status unpacked libfontconfig1-dev:amd64 2.11.1-0ubuntu8
2016-03-11 12:24:46 upgrade fontconfig-config:all 2.11.1-0ubuntu7 2.11.1-0ubuntu8
2016-03-11 12:24:46 status half-configured fontconfig-config:all 2.11.1-0ubuntu7
2016-03-11 12:24:46 status unpacked fontconfig-config:all 2.11.1-0ubuntu7
2016-03-11 12:24:46 status half-installed fontconfig-config:all 2.11.1-0ubuntu7
2016-03-11 12:24:46 status half-installed fontconfig-config:all 2.11.1-0ubuntu7
2016-03-11 12:24:46 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:24:46 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:24:46 upgrade libjson-glib-dev:amd64 1.0.4-2build~pie.1 1.1.2-0ubuntu1
2016-03-11 12:24:46 status half-configured libjson-glib-dev:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:47 status unpacked libjson-glib-dev:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:47 status half-installed libjson-glib-dev:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:47 status half-installed libjson-glib-dev:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:47 status unpacked libjson-glib-dev:amd64 1.1.2-0ubuntu1
2016-03-11 12:24:47 status unpacked libjson-glib-dev:amd64 1.1.2-0ubuntu1
2016-03-11 12:24:47 upgrade gir1.2-json-1.0:amd64 1.0.4-2build~pie.1 1.1.2-0ubuntu1
2016-03-11 12:24:47 status half-configured gir1.2-json-1.0:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:47 status unpacked gir1.2-json-1.0:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:47 status half-installed gir1.2-json-1.0:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:47 status half-installed gir1.2-json-1.0:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:47 status unpacked gir1.2-json-1.0:amd64 1.1.2-0ubuntu1
2016-03-11 12:24:48 status unpacked gir1.2-json-1.0:amd64 1.1.2-0ubuntu1
2016-03-11 12:24:48 upgrade libjson-glib-1.0-common:all 1.0.4-2build~pie.1 1.1.2-0ubuntu1
2016-03-11 12:24:48 status half-configured libjson-glib-1.0-common:all 1.0.4-2build~pie.1
2016-03-11 12:24:48 status unpacked libjson-glib-1.0-common:all 1.0.4-2build~pie.1
2016-03-11 12:24:48 status half-installed libjson-glib-1.0-common:all 1.0.4-2build~pie.1
2016-03-11 12:24:48 status half-installed libjson-glib-1.0-common:all 1.0.4-2build~pie.1
2016-03-11 12:24:48 status unpacked libjson-glib-1.0-common:all 1.1.2-0ubuntu1
2016-03-11 12:24:48 status unpacked libjson-glib-1.0-common:all 1.1.2-0ubuntu1
2016-03-11 12:24:48 upgrade libjson-glib-1.0-0:amd64 1.0.4-2build~pie.1 1.1.2-0ubuntu1
2016-03-11 12:24:48 status half-configured libjson-glib-1.0-0:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:48 status unpacked libjson-glib-1.0-0:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:49 status half-installed libjson-glib-1.0-0:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:49 status half-installed libjson-glib-1.0-0:amd64 1.0.4-2build~pie.1
2016-03-11 12:24:49 status unpacked libjson-glib-1.0-0:amd64 1.1.2-0ubuntu1
2016-03-11 12:24:49 status unpacked libjson-glib-1.0-0:amd64 1.1.2-0ubuntu1
2016-03-11 12:24:49 upgrade libgtk-3-dev:amd64 3.18.8-1ubuntu1 3.18.8-1ubuntu2
2016-03-11 12:24:49 status half-configured libgtk-3-dev:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:49 status unpacked libgtk-3-dev:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:49 status half-installed libgtk-3-dev:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:49 status half-installed libgtk-3-dev:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:50 status half-installed libgtk-3-dev:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:50 status half-installed libgtk-3-dev:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:50 status unpacked libgtk-3-dev:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:50 status unpacked libgtk-3-dev:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:50 upgrade libgtk-3-0:amd64 3.18.8-1ubuntu1 3.18.8-1ubuntu2
2016-03-11 12:24:50 status half-configured libgtk-3-0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:51 status unpacked libgtk-3-0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:51 status half-installed libgtk-3-0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:51 status half-installed libgtk-3-0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:51 status unpacked libgtk-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:51 status unpacked libgtk-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:51 upgrade gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu1 3.18.8-1ubuntu2
2016-03-11 12:24:51 status half-configured gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:51 status unpacked gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:51 status half-installed gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:52 status half-installed gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu1
2016-03-11 12:24:52 status unpacked gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:52 status unpacked gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu2
2016-03-11 12:24:52 upgrade language-selector-gnome:all 0.157 0.158
2016-03-11 12:24:52 status half-configured language-selector-gnome:all 0.157
2016-03-11 12:24:52 status unpacked language-selector-gnome:all 0.157
2016-03-11 12:24:52 status half-installed language-selector-gnome:all 0.157
2016-03-11 12:24:52 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:24:52 status half-installed language-selector-gnome:all 0.157
2016-03-11 12:24:52 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:24:53 status triggers-pending mime-support:all 3.59ubuntu1
2016-03-11 12:24:53 status half-installed language-selector-gnome:all 0.157
2016-03-11 12:24:53 status unpacked language-selector-gnome:all 0.158
2016-03-11 12:24:53 status unpacked language-selector-gnome:all 0.158
2016-03-11 12:24:53 upgrade language-selector-common:all 0.157 0.158
2016-03-11 12:24:53 status half-configured language-selector-common:all 0.157
2016-03-11 12:24:53 status unpacked language-selector-common:all 0.157
2016-03-11 12:24:53 status half-installed language-selector-common:all 0.157
2016-03-11 12:24:54 status triggers-pending dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:24:54 status triggers-pending dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:24:54 status half-installed language-selector-common:all 0.157
2016-03-11 12:24:54 status unpacked language-selector-common:all 0.158
2016-03-11 12:24:54 status unpacked language-selector-common:all 0.158
2016-03-11 12:24:55 upgrade passwd:amd64 1:4.2-3.1ubuntu3 1:4.2-3.1ubuntu4
2016-03-11 12:24:55 status half-configured passwd:amd64 1:4.2-3.1ubuntu3
2016-03-11 12:24:55 status unpacked passwd:amd64 1:4.2-3.1ubuntu3
2016-03-11 12:24:55 status half-installed passwd:amd64 1:4.2-3.1ubuntu3
2016-03-11 12:24:55 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:24:55 status half-installed passwd:amd64 1:4.2-3.1ubuntu3
2016-03-11 12:24:55 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:55 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:55 trigproc libglib2.0-0:i386 2.47.6-1 <aucune>
2016-03-11 12:24:55 status half-configured libglib2.0-0:i386 2.47.6-1
2016-03-11 12:24:57 status installed libglib2.0-0:i386 2.47.6-1
2016-03-11 12:24:57 trigproc libglib2.0-0:amd64 2.47.6-1 <aucune>
2016-03-11 12:24:57 status half-configured libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:24:57 status installed libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:24:57 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:24:57 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:57 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:24:57 trigproc doc-base:all 0.10.7 <aucune>
2016-03-11 12:24:57 status half-configured doc-base:all 0.10.7
2016-03-11 12:24:58 status installed doc-base:all 0.10.7
2016-03-11 12:24:58 trigproc desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1 <aucune>
2016-03-11 12:24:58 status half-configured desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:24:58 status installed desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:24:58 trigproc gnome-menus:amd64 3.13.3-6ubuntu3 <aucune>
2016-03-11 12:24:58 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:24:58 status installed gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:24:58 trigproc mime-support:all 3.59ubuntu1 <aucune>
2016-03-11 12:24:58 status half-configured mime-support:all 3.59ubuntu1
2016-03-11 12:24:58 status installed mime-support:all 3.59ubuntu1
2016-03-11 12:24:58 trigproc dbus:amd64 1.10.6-1ubuntu2 <aucune>
2016-03-11 12:24:58 status half-configured dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:24:59 status installed dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:24:59 trigproc ureadahead:amd64 0.100.0-19build~pie.1 <aucune>
2016-03-11 12:24:59 status half-configured ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:24:59 status installed ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:24:59 startup packages configure
2016-03-11 12:24:59 configure passwd:amd64 1:4.2-3.1ubuntu4 <aucune>
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status unpacked passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:24:59 status half-configured passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:25:00 status installed passwd:amd64 1:4.2-3.1ubuntu4
2016-03-11 12:25:00 startup archives unpack
2016-03-11 12:25:00 upgrade uuid-runtime:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:00 status half-configured uuid-runtime:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:00 status unpacked uuid-runtime:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:00 status half-installed uuid-runtime:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:00 status triggers-pending systemd:amd64 229-2ubuntu1
2016-03-11 12:25:00 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:01 status half-installed uuid-runtime:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:01 status unpacked uuid-runtime:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:01 status unpacked uuid-runtime:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:01 upgrade fontconfig:amd64 2.11.1-0ubuntu7 2.11.1-0ubuntu8
2016-03-11 12:25:01 status half-configured fontconfig:amd64 2.11.1-0ubuntu7
2016-03-11 12:25:01 status unpacked fontconfig:amd64 2.11.1-0ubuntu7
2016-03-11 12:25:02 status half-installed fontconfig:amd64 2.11.1-0ubuntu7
2016-03-11 12:25:03 status triggers-pending doc-base:all 0.10.7
2016-03-11 12:25:03 status half-installed fontconfig:amd64 2.11.1-0ubuntu7
2016-03-11 12:25:03 status unpacked fontconfig:amd64 2.11.1-0ubuntu8
2016-03-11 12:25:03 status unpacked fontconfig:amd64 2.11.1-0ubuntu8
2016-03-11 12:25:04 upgrade imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:04 status half-configured imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:04 status unpacked imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:04 status half-installed imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:05 status half-installed imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:05 status unpacked imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:05 status unpacked imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:05 upgrade libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:05 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:05 status half-configured libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:05 status unpacked libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:05 status half-installed libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:06 status half-installed libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:06 status unpacked libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:06 status unpacked libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:06 upgrade libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:06 status half-configured libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:06 status unpacked libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:06 status half-installed libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:07 status half-installed libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:07 status unpacked libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:07 status unpacked libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:07 upgrade imagemagick-common:all 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:07 status half-configured imagemagick-common:all 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:07 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:07 status half-installed imagemagick-common:all 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:08 status half-installed imagemagick-common:all 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:08 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:08 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:08 upgrade imagemagick:amd64 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:08 status half-configured imagemagick:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:08 status unpacked imagemagick:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:08 status half-installed imagemagick:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:08 status triggers-pending mime-support:all 3.59ubuntu1
2016-03-11 12:25:08 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:25:08 status half-installed imagemagick:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:08 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:25:08 status triggers-pending mime-support:all 3.59ubuntu1
2016-03-11 12:25:08 status triggers-pending menu:amd64 2.1.47ubuntu1
2016-03-11 12:25:09 status half-installed imagemagick:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:09 status half-installed imagemagick:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:09 status triggers-awaited menu:amd64 2.1.47ubuntu1
2016-03-11 12:25:09 status unpacked imagemagick:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:09 status unpacked imagemagick:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:09 upgrade imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:09 status half-configured imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:09 status unpacked imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:09 status half-installed imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:09 status half-installed imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:09 status triggers-pending hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:25:09 status half-installed imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:10 status half-installed imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:10 status unpacked imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:10 status unpacked imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:10 upgrade libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:10 status half-configured libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:10 status unpacked libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:10 status half-installed libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:10 status half-installed libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:10 status unpacked libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:10 status unpacked libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:11 upgrade libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:11 status half-configured libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:11 status unpacked libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:11 status half-installed libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:11 status half-installed libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:11 status unpacked libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:11 status unpacked libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:11 upgrade libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu1 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:11 status half-configured libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:11 status unpacked libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:11 status half-installed libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:12 status half-installed libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu1
2016-03-11 12:25:12 status unpacked libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:12 status unpacked libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:25:12 upgrade language-pack-en:all 1:16.04+20160228 1:16.04+20160306
2016-03-11 12:25:12 status half-configured language-pack-en:all 1:16.04+20160228
2016-03-11 12:25:12 status unpacked language-pack-en:all 1:16.04+20160228
2016-03-11 12:25:12 status half-installed language-pack-en:all 1:16.04+20160228
2016-03-11 12:25:12 status triggers-pending software-center:all 16.01+16.04.20160217
2016-03-11 12:25:12 status half-installed language-pack-en:all 1:16.04+20160228
2016-03-11 12:25:13 status unpacked language-pack-en:all 1:16.04+20160306
2016-03-11 12:25:13 status unpacked language-pack-en:all 1:16.04+20160306
2016-03-11 12:25:13 upgrade language-pack-fr:all 1:16.04+20160228 1:16.04+20160306
2016-03-11 12:25:13 status half-configured language-pack-fr:all 1:16.04+20160228
2016-03-11 12:25:13 status unpacked language-pack-fr:all 1:16.04+20160228
2016-03-11 12:25:13 status half-installed language-pack-fr:all 1:16.04+20160228
2016-03-11 12:25:13 status half-installed language-pack-fr:all 1:16.04+20160228
2016-03-11 12:25:13 status unpacked language-pack-fr:all 1:16.04+20160306
2016-03-11 12:25:13 status unpacked language-pack-fr:all 1:16.04+20160306
2016-03-11 12:25:13 upgrade language-pack-gnome-en:all 1:16.04+20160228 1:16.04+20160306
2016-03-11 12:25:13 status half-configured language-pack-gnome-en:all 1:16.04+20160228
2016-03-11 12:25:14 status unpacked language-pack-gnome-en:all 1:16.04+20160228
2016-03-11 12:25:14 status half-installed language-pack-gnome-en:all 1:16.04+20160228
2016-03-11 12:25:14 status half-installed language-pack-gnome-en:all 1:16.04+20160228
2016-03-11 12:25:14 status unpacked language-pack-gnome-en:all 1:16.04+20160306
2016-03-11 12:25:14 status unpacked language-pack-gnome-en:all 1:16.04+20160306
2016-03-11 12:25:14 upgrade language-pack-gnome-fr:all 1:16.04+20160228 1:16.04+20160306
2016-03-11 12:25:14 status half-configured language-pack-gnome-fr:all 1:16.04+20160228
2016-03-11 12:25:14 status unpacked language-pack-gnome-fr:all 1:16.04+20160228
2016-03-11 12:25:14 status half-installed language-pack-gnome-fr:all 1:16.04+20160228
2016-03-11 12:25:15 status half-installed language-pack-gnome-fr:all 1:16.04+20160228
2016-03-11 12:25:15 status unpacked language-pack-gnome-fr:all 1:16.04+20160306
2016-03-11 12:25:15 status unpacked language-pack-gnome-fr:all 1:16.04+20160306
2016-03-11 12:25:15 upgrade python-pymysql:all 0.6.2-2 0.7.2-1
2016-03-11 12:25:15 status half-configured python-pymysql:all 0.6.2-2
2016-03-11 12:25:15 status unpacked python-pymysql:all 0.6.2-2
2016-03-11 12:25:15 status half-installed python-pymysql:all 0.6.2-2
2016-03-11 12:25:15 status half-installed python-pymysql:all 0.6.2-2
2016-03-11 12:25:16 status unpacked python-pymysql:all 0.7.2-1
2016-03-11 12:25:16 status unpacked python-pymysql:all 0.7.2-1
2016-03-11 12:25:16 upgrade python3-pymysql:all 0.6.2-2 0.7.2-1
2016-03-11 12:25:16 status half-configured python3-pymysql:all 0.6.2-2
2016-03-11 12:25:16 status unpacked python3-pymysql:all 0.6.2-2
2016-03-11 12:25:16 status half-installed python3-pymysql:all 0.6.2-2
2016-03-11 12:25:16 status half-installed python3-pymysql:all 0.6.2-2
2016-03-11 12:25:17 status unpacked python3-pymysql:all 0.7.2-1
2016-03-11 12:25:17 status unpacked python3-pymysql:all 0.7.2-1
2016-03-11 12:25:17 upgrade kmod:amd64 22-1ubuntu1 22-1ubuntu3
2016-03-11 12:25:17 status half-configured kmod:amd64 22-1ubuntu1
2016-03-11 12:25:17 status unpacked kmod:amd64 22-1ubuntu1
2016-03-11 12:25:17 status half-installed kmod:amd64 22-1ubuntu1
2016-03-11 12:25:17 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:17 status half-installed kmod:amd64 22-1ubuntu1
2016-03-11 12:25:17 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:25:18 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:25:18 upgrade libkmod2:amd64 22-1ubuntu1 22-1ubuntu3
2016-03-11 12:25:18 status half-configured libkmod2:amd64 22-1ubuntu1
2016-03-11 12:25:18 status unpacked libkmod2:amd64 22-1ubuntu1
2016-03-11 12:25:18 status half-installed libkmod2:amd64 22-1ubuntu1
2016-03-11 12:25:18 status half-installed libkmod2:amd64 22-1ubuntu1
2016-03-11 12:25:18 status unpacked libkmod2:amd64 22-1ubuntu3
2016-03-11 12:25:18 status unpacked libkmod2:amd64 22-1ubuntu3
2016-03-11 12:25:18 trigproc ureadahead:amd64 0.100.0-19build~pie.1 <aucune>
2016-03-11 12:25:18 status half-configured ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:18 status installed ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:19 trigproc doc-base:all 0.10.7 <aucune>
2016-03-11 12:25:19 status half-configured doc-base:all 0.10.7
2016-03-11 12:25:19 status installed doc-base:all 0.10.7
2016-03-11 12:25:19 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:19 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:19 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:19 trigproc mime-support:all 3.59ubuntu1 <aucune>
2016-03-11 12:25:19 status half-configured mime-support:all 3.59ubuntu1
2016-03-11 12:25:19 status installed mime-support:all 3.59ubuntu1
2016-03-11 12:25:19 trigproc desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1 <aucune>
2016-03-11 12:25:19 status half-configured desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:25:20 status installed desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:25:20 trigproc gnome-menus:amd64 3.13.3-6ubuntu3 <aucune>
2016-03-11 12:25:20 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:25:20 status installed gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:25:20 trigproc menu:amd64 2.1.47ubuntu1 <aucune>
2016-03-11 12:25:20 status half-configured menu:amd64 2.1.47ubuntu1
2016-03-11 12:25:21 status installed menu:amd64 2.1.47ubuntu1
2016-03-11 12:25:21 trigproc hicolor-icon-theme:all 0.15-0ubuntu1 <aucune>
2016-03-11 12:25:21 status half-configured hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:25:21 status installed hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:25:21 startup packages configure
2016-03-11 12:25:21 configure libkmod2:amd64 22-1ubuntu3 <aucune>
2016-03-11 12:25:21 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:21 status unpacked libkmod2:amd64 22-1ubuntu3
2016-03-11 12:25:21 status half-configured libkmod2:amd64 22-1ubuntu3
2016-03-11 12:25:21 status installed libkmod2:amd64 22-1ubuntu3
2016-03-11 12:25:22 trigproc systemd:amd64 229-2ubuntu1 <aucune>
2016-03-11 12:25:22 status half-configured systemd:amd64 229-2ubuntu1
2016-03-11 12:25:22 status installed systemd:amd64 229-2ubuntu1
2016-03-11 12:25:22 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:22 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:22 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:22 startup archives unpack
2016-03-11 12:25:23 upgrade ubuntu-drivers-common:amd64 1:0.4.15 1:0.4.16
2016-03-11 12:25:23 status half-configured ubuntu-drivers-common:amd64 1:0.4.15
2016-03-11 12:25:23 status unpacked ubuntu-drivers-common:amd64 1:0.4.15
2016-03-11 12:25:23 status half-installed ubuntu-drivers-common:amd64 1:0.4.15
2016-03-11 12:25:23 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:23 status half-installed ubuntu-drivers-common:amd64 1:0.4.15
2016-03-11 12:25:23 status unpacked ubuntu-drivers-common:amd64 1:0.4.16
2016-03-11 12:25:24 status unpacked ubuntu-drivers-common:amd64 1:0.4.16
2016-03-11 12:25:24 upgrade uuid-dev:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:24 status half-configured uuid-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:24 status unpacked uuid-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:24 status half-installed uuid-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:24 status half-installed uuid-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:24 status unpacked uuid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:24 status unpacked uuid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:24 upgrade libuuid1:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:24 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:25 status half-configured libuuid1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:25 status unpacked libuuid1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:25 status half-configured libuuid1:i386 2.27.1-3ubuntu1
2016-03-11 12:25:25 status half-installed libuuid1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:25 status half-installed libuuid1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:25 status unpacked libuuid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:25 status unpacked libuuid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:25 upgrade libuuid1:i386 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:25 status half-configured libuuid1:i386 2.27.1-3ubuntu1
2016-03-11 12:25:25 status unpacked libuuid1:i386 2.27.1-3ubuntu1
2016-03-11 12:25:25 status half-installed libuuid1:i386 2.27.1-3ubuntu1
2016-03-11 12:25:25 status half-installed libuuid1:i386 2.27.1-3ubuntu1
2016-03-11 12:25:26 status unpacked libuuid1:i386 2.27.1-4ubuntu1
2016-03-11 12:25:26 status unpacked libuuid1:i386 2.27.1-4ubuntu1
2016-03-11 12:25:26 upgrade libblkid-dev:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:26 status half-configured libblkid-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:26 status unpacked libblkid-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:26 status half-installed libblkid-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:26 status half-installed libblkid-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:26 status unpacked libblkid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:26 status unpacked libblkid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:27 upgrade libblkid1:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:27 status half-configured libblkid1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:27 status unpacked libblkid1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:27 status half-installed libblkid1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:27 status half-installed libblkid1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:27 status unpacked libblkid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:27 status unpacked libblkid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:27 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:27 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:27 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:28 startup packages configure
2016-03-11 12:25:28 configure libuuid1:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:25:28 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:28 status unpacked libuuid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:28 status half-configured libuuid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:28 status installed libuuid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:28 configure libuuid1:i386 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:25:28 status unpacked libuuid1:i386 2.27.1-4ubuntu1
2016-03-11 12:25:28 status half-configured libuuid1:i386 2.27.1-4ubuntu1
2016-03-11 12:25:28 status installed libuuid1:i386 2.27.1-4ubuntu1
2016-03-11 12:25:28 configure libblkid1:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:25:28 status unpacked libblkid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:28 status half-configured libblkid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:28 status installed libblkid1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:28 trigproc ureadahead:amd64 0.100.0-19build~pie.1 <aucune>
2016-03-11 12:25:28 status half-configured ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:29 status installed ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:29 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:29 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:29 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:29 startup archives unpack
2016-03-11 12:25:29 upgrade libfdisk-dev:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:29 status half-configured libfdisk-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:29 status unpacked libfdisk-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:29 status half-installed libfdisk-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:30 status half-installed libfdisk-dev:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:30 status unpacked libfdisk-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:30 status unpacked libfdisk-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:30 upgrade libfdisk1:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:30 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:30 status half-configured libfdisk1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:30 status unpacked libfdisk1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:30 status half-installed libfdisk1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:30 status half-installed libfdisk1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:30 status unpacked libfdisk1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:31 status unpacked libfdisk1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:31 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:31 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:31 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:31 startup packages configure
2016-03-11 12:25:31 configure libfdisk1:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:25:31 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:31 status unpacked libfdisk1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:31 status half-configured libfdisk1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:31 status installed libfdisk1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:31 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:31 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:31 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:32 startup archives unpack
2016-03-11 12:25:32 upgrade libmount1:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:32 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:32 status half-configured libmount1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:32 status unpacked libmount1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:32 status half-installed libmount1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:32 status half-installed libmount1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:32 status unpacked libmount1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:32 status unpacked libmount1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:33 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:33 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:33 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:34 startup packages configure
2016-03-11 12:25:34 configure libmount1:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:25:34 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:34 status unpacked libmount1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:35 status half-configured libmount1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:35 status installed libmount1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:35 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:35 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:35 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:35 startup archives unpack
2016-03-11 12:25:35 upgrade libsmartcols1:amd64 2.27.1-3ubuntu1 2.27.1-4ubuntu1
2016-03-11 12:25:35 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:35 status half-configured libsmartcols1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:35 status unpacked libsmartcols1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:36 status half-installed libsmartcols1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:36 status half-installed libsmartcols1:amd64 2.27.1-3ubuntu1
2016-03-11 12:25:36 status unpacked libsmartcols1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:36 status unpacked libsmartcols1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:36 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:36 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:36 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:36 startup packages configure
2016-03-11 12:25:36 configure libsmartcols1:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:25:36 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:36 status unpacked libsmartcols1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:36 status half-configured libsmartcols1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:36 status installed libsmartcols1:amd64 2.27.1-4ubuntu1
2016-03-11 12:25:37 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:37 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:37 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:37 startup archives unpack
2016-03-11 12:25:37 upgrade libkrb5support0:amd64 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:25:37 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:37 status half-configured libkrb5support0:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:37 status unpacked libkrb5support0:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:37 status half-configured libkrb5support0:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:38 status half-installed libkrb5support0:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:38 status half-installed libkrb5support0:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:38 status unpacked libkrb5support0:amd64 1.13.2+dfsg-5
2016-03-11 12:25:38 status unpacked libkrb5support0:amd64 1.13.2+dfsg-5
2016-03-11 12:25:38 upgrade libkrb5support0:i386 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:25:38 status half-configured libkrb5support0:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:38 status unpacked libkrb5support0:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:38 status half-installed libkrb5support0:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:38 status half-installed libkrb5support0:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:38 status unpacked libkrb5support0:i386 1.13.2+dfsg-5
2016-03-11 12:25:38 status unpacked libkrb5support0:i386 1.13.2+dfsg-5
2016-03-11 12:25:39 upgrade libkrb5-3:amd64 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:25:39 status half-configured libkrb5-3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:39 status unpacked libkrb5-3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:39 status half-configured libkrb5-3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:39 status half-installed libkrb5-3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:39 status half-installed libkrb5-3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:39 status unpacked libkrb5-3:amd64 1.13.2+dfsg-5
2016-03-11 12:25:39 status unpacked libkrb5-3:amd64 1.13.2+dfsg-5
2016-03-11 12:25:40 upgrade libkrb5-3:i386 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:25:40 status half-configured libkrb5-3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:40 status unpacked libkrb5-3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:40 status half-installed libkrb5-3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:40 status half-installed libkrb5-3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:40 status unpacked libkrb5-3:i386 1.13.2+dfsg-5
2016-03-11 12:25:40 status unpacked libkrb5-3:i386 1.13.2+dfsg-5
2016-03-11 12:25:40 upgrade libgssapi-krb5-2:amd64 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:25:40 status half-configured libgssapi-krb5-2:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:40 status unpacked libgssapi-krb5-2:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:40 status half-configured libgssapi-krb5-2:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:41 status half-installed libgssapi-krb5-2:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:41 status half-installed libgssapi-krb5-2:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:41 status unpacked libgssapi-krb5-2:amd64 1.13.2+dfsg-5
2016-03-11 12:25:41 status unpacked libgssapi-krb5-2:amd64 1.13.2+dfsg-5
2016-03-11 12:25:41 upgrade libgssapi-krb5-2:i386 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:25:41 status half-configured libgssapi-krb5-2:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:41 status unpacked libgssapi-krb5-2:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:41 status half-installed libgssapi-krb5-2:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:41 status half-installed libgssapi-krb5-2:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:42 status unpacked libgssapi-krb5-2:i386 1.13.2+dfsg-5
2016-03-11 12:25:42 status unpacked libgssapi-krb5-2:i386 1.13.2+dfsg-5
2016-03-11 12:25:42 upgrade libk5crypto3:i386 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:25:42 status half-configured libk5crypto3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:42 status unpacked libk5crypto3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:42 status half-configured libk5crypto3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:42 status half-installed libk5crypto3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:42 status half-installed libk5crypto3:i386 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:42 status unpacked libk5crypto3:i386 1.13.2+dfsg-5
2016-03-11 12:25:42 status unpacked libk5crypto3:i386 1.13.2+dfsg-5
2016-03-11 12:25:43 upgrade libk5crypto3:amd64 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:25:43 status half-configured libk5crypto3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:43 status unpacked libk5crypto3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:43 status half-installed libk5crypto3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:43 status half-installed libk5crypto3:amd64 1.13.2+dfsg-4build~pie.1
2016-03-11 12:25:43 status unpacked libk5crypto3:amd64 1.13.2+dfsg-5
2016-03-11 12:25:43 status unpacked libk5crypto3:amd64 1.13.2+dfsg-5
2016-03-11 12:25:43 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:43 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:43 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:43 startup packages configure
2016-03-11 12:25:43 configure libkrb5support0:amd64 1.13.2+dfsg-5 <aucune>
2016-03-11 12:25:43 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:43 status unpacked libkrb5support0:amd64 1.13.2+dfsg-5
2016-03-11 12:25:44 status half-configured libkrb5support0:amd64 1.13.2+dfsg-5
2016-03-11 12:25:44 status installed libkrb5support0:amd64 1.13.2+dfsg-5
2016-03-11 12:25:44 configure libkrb5support0:i386 1.13.2+dfsg-5 <aucune>
2016-03-11 12:25:44 status unpacked libkrb5support0:i386 1.13.2+dfsg-5
2016-03-11 12:25:44 status half-configured libkrb5support0:i386 1.13.2+dfsg-5
2016-03-11 12:25:44 status installed libkrb5support0:i386 1.13.2+dfsg-5
2016-03-11 12:25:44 configure libk5crypto3:amd64 1.13.2+dfsg-5 <aucune>
2016-03-11 12:25:44 status unpacked libk5crypto3:amd64 1.13.2+dfsg-5
2016-03-11 12:25:44 status half-configured libk5crypto3:amd64 1.13.2+dfsg-5
2016-03-11 12:25:44 status installed libk5crypto3:amd64 1.13.2+dfsg-5
2016-03-11 12:25:44 configure libk5crypto3:i386 1.13.2+dfsg-5 <aucune>
2016-03-11 12:25:44 status unpacked libk5crypto3:i386 1.13.2+dfsg-5
2016-03-11 12:25:44 status half-configured libk5crypto3:i386 1.13.2+dfsg-5
2016-03-11 12:25:44 status installed libk5crypto3:i386 1.13.2+dfsg-5
2016-03-11 12:25:44 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:25:44 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:44 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:45 startup archives unpack
2016-03-11 12:25:45 upgrade console-setup-linux:all 1.108ubuntu10 1.108ubuntu11
2016-03-11 12:25:45 status half-configured console-setup-linux:all 1.108ubuntu10
2016-03-11 12:25:45 status unpacked console-setup-linux:all 1.108ubuntu10
2016-03-11 12:25:45 status half-installed console-setup-linux:all 1.108ubuntu10
2016-03-11 12:25:45 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:45 status half-installed console-setup-linux:all 1.108ubuntu10
2016-03-11 12:25:46 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:25:46 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:25:46 upgrade initramfs-tools-core:all 0.122ubuntu4 0.122ubuntu6
2016-03-11 12:25:46 status half-configured initramfs-tools-core:all 0.122ubuntu4
2016-03-11 12:25:46 status unpacked initramfs-tools-core:all 0.122ubuntu4
2016-03-11 12:25:46 status half-installed initramfs-tools-core:all 0.122ubuntu4
2016-03-11 12:25:46 status triggers-pending doc-base:all 0.10.7
2016-03-11 12:25:46 status half-installed initramfs-tools-core:all 0.122ubuntu4
2016-03-11 12:25:47 status unpacked initramfs-tools-core:all 0.122ubuntu6
2016-03-11 12:25:47 status unpacked initramfs-tools-core:all 0.122ubuntu6
2016-03-11 12:25:47 upgrade initramfs-tools:all 0.122ubuntu4 0.122ubuntu6
2016-03-11 12:25:47 status half-configured initramfs-tools:all 0.122ubuntu4
2016-03-11 12:25:47 status unpacked initramfs-tools:all 0.122ubuntu4
2016-03-11 12:25:47 status half-installed initramfs-tools:all 0.122ubuntu4
2016-03-11 12:25:47 status half-installed initramfs-tools:all 0.122ubuntu4
2016-03-11 12:25:47 status unpacked initramfs-tools:all 0.122ubuntu6
2016-03-11 12:25:47 status unpacked initramfs-tools:all 0.122ubuntu6
2016-03-11 12:25:48 upgrade console-setup:all 1.108ubuntu10 1.108ubuntu11
2016-03-11 12:25:48 status half-configured console-setup:all 1.108ubuntu10
2016-03-11 12:25:48 status unpacked console-setup:all 1.108ubuntu10
2016-03-11 12:25:48 status half-installed console-setup:all 1.108ubuntu10
2016-03-11 12:25:48 status half-installed console-setup:all 1.108ubuntu10
2016-03-11 12:25:48 status unpacked console-setup:all 1.108ubuntu11
2016-03-11 12:25:48 status unpacked console-setup:all 1.108ubuntu11
2016-03-11 12:25:49 upgrade keyboard-configuration:all 1.108ubuntu10 1.108ubuntu11
2016-03-11 12:25:49 status half-configured keyboard-configuration:all 1.108ubuntu10
2016-03-11 12:25:49 status unpacked keyboard-configuration:all 1.108ubuntu10
2016-03-11 12:25:49 status half-installed keyboard-configuration:all 1.108ubuntu10
2016-03-11 12:25:49 status triggers-pending systemd:amd64 229-2ubuntu1
2016-03-11 12:25:49 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:25:49 status half-installed keyboard-configuration:all 1.108ubuntu10
2016-03-11 12:25:49 status unpacked keyboard-configuration:all 1.108ubuntu11
2016-03-11 12:25:49 status unpacked keyboard-configuration:all 1.108ubuntu11
2016-03-11 12:25:50 upgrade initramfs-tools-bin:amd64 0.122ubuntu4 0.122ubuntu6
2016-03-11 12:25:50 status half-configured initramfs-tools-bin:amd64 0.122ubuntu4
2016-03-11 12:25:50 status unpacked initramfs-tools-bin:amd64 0.122ubuntu4
2016-03-11 12:25:50 status half-installed initramfs-tools-bin:amd64 0.122ubuntu4
2016-03-11 12:25:50 status half-installed initramfs-tools-bin:amd64 0.122ubuntu4
2016-03-11 12:25:50 status unpacked initramfs-tools-bin:amd64 0.122ubuntu6
2016-03-11 12:25:50 status unpacked initramfs-tools-bin:amd64 0.122ubuntu6
2016-03-11 12:25:50 upgrade bind9-host:amd64 1:9.10.3.dfsg.P2-4 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:50 status half-configured bind9-host:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:50 status unpacked bind9-host:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:50 status half-installed bind9-host:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:51 status half-installed bind9-host:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:51 status unpacked bind9-host:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:51 status unpacked bind9-host:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:51 upgrade dnsutils:amd64 1:9.10.3.dfsg.P2-4 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:51 status half-configured dnsutils:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:51 status unpacked dnsutils:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:51 status half-installed dnsutils:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:51 status half-installed dnsutils:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:51 status unpacked dnsutils:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:51 status unpacked dnsutils:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:52 upgrade libisc160:amd64 1:9.10.3.dfsg.P2-4 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:52 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:25:52 status half-configured libisc160:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:52 status unpacked libisc160:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:52 status half-installed libisc160:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:52 status half-installed libisc160:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:52 status unpacked libisc160:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:52 status unpacked libisc160:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:52 upgrade libisccc140:amd64 1:9.10.3.dfsg.P2-4 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:52 status half-configured libisccc140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:52 status unpacked libisccc140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:52 status half-installed libisccc140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:52 status half-installed libisccc140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:53 status unpacked libisccc140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:53 status unpacked libisccc140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:53 upgrade libisccfg140:amd64 1:9.10.3.dfsg.P2-4 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:53 status half-configured libisccfg140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:53 status unpacked libisccfg140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:53 status half-installed libisccfg140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:53 status half-installed libisccfg140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:53 status unpacked libisccfg140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:53 status unpacked libisccfg140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:54 upgrade liblwres141:amd64 1:9.10.3.dfsg.P2-4 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:54 status half-configured liblwres141:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:54 status unpacked liblwres141:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:54 status half-installed liblwres141:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:54 status half-installed liblwres141:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:54 status unpacked liblwres141:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:54 status unpacked liblwres141:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:54 upgrade libbind9-140:amd64 1:9.10.3.dfsg.P2-4 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:54 status half-configured libbind9-140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:54 status unpacked libbind9-140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:54 status half-installed libbind9-140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:54 status half-installed libbind9-140:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:54 status unpacked libbind9-140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:55 status unpacked libbind9-140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:55 upgrade libssl1.0.0:amd64 1.0.2f-2ubuntu1 1.0.2g-1ubuntu2
2016-03-11 12:25:55 status half-configured libssl1.0.0:amd64 1.0.2f-2ubuntu1
2016-03-11 12:25:55 status unpacked libssl1.0.0:amd64 1.0.2f-2ubuntu1
2016-03-11 12:25:55 status half-configured libssl1.0.0:i386 1.0.2f-2ubuntu1
2016-03-11 12:25:55 status half-installed libssl1.0.0:amd64 1.0.2f-2ubuntu1
2016-03-11 12:25:55 status half-installed libssl1.0.0:amd64 1.0.2f-2ubuntu1
2016-03-11 12:25:55 status unpacked libssl1.0.0:amd64 1.0.2g-1ubuntu2
2016-03-11 12:25:56 status unpacked libssl1.0.0:amd64 1.0.2g-1ubuntu2
2016-03-11 12:25:56 upgrade libssl1.0.0:i386 1.0.2f-2ubuntu1 1.0.2g-1ubuntu2
2016-03-11 12:25:56 status half-configured libssl1.0.0:i386 1.0.2f-2ubuntu1
2016-03-11 12:25:56 status unpacked libssl1.0.0:i386 1.0.2f-2ubuntu1
2016-03-11 12:25:56 status half-installed libssl1.0.0:i386 1.0.2f-2ubuntu1
2016-03-11 12:25:56 status half-installed libssl1.0.0:i386 1.0.2f-2ubuntu1
2016-03-11 12:25:56 status unpacked libssl1.0.0:i386 1.0.2g-1ubuntu2
2016-03-11 12:25:57 status unpacked libssl1.0.0:i386 1.0.2g-1ubuntu2
2016-03-11 12:25:57 upgrade libdns162:amd64 1:9.10.3.dfsg.P2-4 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:57 status half-configured libdns162:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:57 status unpacked libdns162:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:57 status half-installed libdns162:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:57 status half-installed libdns162:amd64 1:9.10.3.dfsg.P2-4
2016-03-11 12:25:57 status unpacked libdns162:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:57 status unpacked libdns162:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:25:58 upgrade isc-dhcp-client:amd64 4.3.3-5ubuntu8 4.3.3-5ubuntu9
2016-03-11 12:25:58 status half-configured isc-dhcp-client:amd64 4.3.3-5ubuntu8
2016-03-11 12:25:58 status unpacked isc-dhcp-client:amd64 4.3.3-5ubuntu8
2016-03-11 12:25:58 status half-installed isc-dhcp-client:amd64 4.3.3-5ubuntu8
2016-03-11 12:25:58 status half-installed isc-dhcp-client:amd64 4.3.3-5ubuntu8
2016-03-11 12:25:58 status unpacked isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:25:58 status unpacked isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:25:58 upgrade isc-dhcp-common:amd64 4.3.3-5ubuntu8 4.3.3-5ubuntu9
2016-03-11 12:25:58 status half-configured isc-dhcp-common:amd64 4.3.3-5ubuntu8
2016-03-11 12:25:58 status unpacked isc-dhcp-common:amd64 4.3.3-5ubuntu8
2016-03-11 12:25:58 status half-installed isc-dhcp-common:amd64 4.3.3-5ubuntu8
2016-03-11 12:25:58 status half-installed isc-dhcp-common:amd64 4.3.3-5ubuntu8
2016-03-11 12:25:59 status unpacked isc-dhcp-common:amd64 4.3.3-5ubuntu9
2016-03-11 12:25:59 status unpacked isc-dhcp-common:amd64 4.3.3-5ubuntu9
2016-03-11 12:25:59 upgrade ubuntu-minimal:amd64 1.348 1.349
2016-03-11 12:25:59 status half-configured ubuntu-minimal:amd64 1.348
2016-03-11 12:25:59 status unpacked ubuntu-minimal:amd64 1.348
2016-03-11 12:25:59 status half-installed ubuntu-minimal:amd64 1.348
2016-03-11 12:25:59 status half-installed ubuntu-minimal:amd64 1.348
2016-03-11 12:25:59 status unpacked ubuntu-minimal:amd64 1.349
2016-03-11 12:25:59 status unpacked ubuntu-minimal:amd64 1.349
2016-03-11 12:25:59 upgrade apt-transport-https:amd64 1.2.3 1.2.4
2016-03-11 12:25:59 status half-configured apt-transport-https:amd64 1.2.3
2016-03-11 12:25:59 status unpacked apt-transport-https:amd64 1.2.3
2016-03-11 12:25:59 status half-installed apt-transport-https:amd64 1.2.3
2016-03-11 12:26:00 status half-installed apt-transport-https:amd64 1.2.3
2016-03-11 12:26:00 status unpacked apt-transport-https:amd64 1.2.4
2016-03-11 12:26:00 status unpacked apt-transport-https:amd64 1.2.4
2016-03-11 12:26:00 upgrade krb5-locales:all 1.13.2+dfsg-4build~pie.1 1.13.2+dfsg-5
2016-03-11 12:26:00 status half-configured krb5-locales:all 1.13.2+dfsg-4build~pie.1
2016-03-11 12:26:00 status unpacked krb5-locales:all 1.13.2+dfsg-4build~pie.1
2016-03-11 12:26:00 status half-installed krb5-locales:all 1.13.2+dfsg-4build~pie.1
2016-03-11 12:26:00 status half-installed krb5-locales:all 1.13.2+dfsg-4build~pie.1
2016-03-11 12:26:00 status unpacked krb5-locales:all 1.13.2+dfsg-5
2016-03-11 12:26:00 status unpacked krb5-locales:all 1.13.2+dfsg-5
2016-03-11 12:26:01 upgrade ltrace:amd64 0.7.3-5.1ubuntu2 0.7.3-5.1ubuntu3
2016-03-11 12:26:01 status half-configured ltrace:amd64 0.7.3-5.1ubuntu2
2016-03-11 12:26:01 status unpacked ltrace:amd64 0.7.3-5.1ubuntu2
2016-03-11 12:26:01 status half-installed ltrace:amd64 0.7.3-5.1ubuntu2
2016-03-11 12:26:01 status half-installed ltrace:amd64 0.7.3-5.1ubuntu2
2016-03-11 12:26:01 status unpacked ltrace:amd64 0.7.3-5.1ubuntu3
2016-03-11 12:26:01 status unpacked ltrace:amd64 0.7.3-5.1ubuntu3
2016-03-11 12:26:01 upgrade openssh-sftp-server:amd64 1:7.1p2-2build0pie.3 1:7.2p1-1
2016-03-11 12:26:01 status half-configured openssh-sftp-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:01 status unpacked openssh-sftp-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:01 status half-installed openssh-sftp-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:01 status half-installed openssh-sftp-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:02 status unpacked openssh-sftp-server:amd64 1:7.2p1-1
2016-03-11 12:26:02 status unpacked openssh-sftp-server:amd64 1:7.2p1-1
2016-03-11 12:26:02 upgrade openssh-server:amd64 1:7.1p2-2build0pie.3 1:7.2p1-1
2016-03-11 12:26:02 status half-configured openssh-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:02 status unpacked openssh-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:02 status half-installed openssh-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:02 status triggers-pending ufw:all 0.35-0ubuntu1
2016-03-11 12:26:02 status half-installed openssh-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:02 status half-installed openssh-server:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:03 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:26:03 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:26:03 upgrade openssh-client:amd64 1:7.1p2-2build0pie.3 1:7.2p1-1
2016-03-11 12:26:03 status half-configured openssh-client:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:03 status unpacked openssh-client:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:03 status half-installed openssh-client:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:03 status half-installed openssh-client:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:26:04 status unpacked openssh-client:amd64 1:7.2p1-1
2016-03-11 12:26:04 status unpacked openssh-client:amd64 1:7.2p1-1
2016-03-11 12:26:04 upgrade openssl:amd64 1.0.2f-2ubuntu1 1.0.2g-1ubuntu2
2016-03-11 12:26:04 status half-configured openssl:amd64 1.0.2f-2ubuntu1
2016-03-11 12:26:04 status unpacked openssl:amd64 1.0.2f-2ubuntu1
2016-03-11 12:26:04 status half-installed openssl:amd64 1.0.2f-2ubuntu1
2016-03-11 12:26:04 status half-installed openssl:amd64 1.0.2f-2ubuntu1
2016-03-11 12:26:05 status unpacked openssl:amd64 1.0.2g-1ubuntu2
2016-03-11 12:26:05 status unpacked openssl:amd64 1.0.2g-1ubuntu2
2016-03-11 12:26:06 upgrade ubuntu-release-upgrader-gtk:all 1:16.04.7 1:16.04.8
2016-03-11 12:26:06 status half-configured ubuntu-release-upgrader-gtk:all 1:16.04.7
2016-03-11 12:26:06 status unpacked ubuntu-release-upgrader-gtk:all 1:16.04.7
2016-03-11 12:26:06 status half-installed ubuntu-release-upgrader-gtk:all 1:16.04.7
2016-03-11 12:26:06 status half-installed ubuntu-release-upgrader-gtk:all 1:16.04.7
2016-03-11 12:26:06 status unpacked ubuntu-release-upgrader-gtk:all 1:16.04.8
2016-03-11 12:26:06 status unpacked ubuntu-release-upgrader-gtk:all 1:16.04.8
2016-03-11 12:26:06 upgrade ubuntu-release-upgrader-core:all 1:16.04.7 1:16.04.8
2016-03-11 12:26:06 status half-configured ubuntu-release-upgrader-core:all 1:16.04.7
2016-03-11 12:26:06 status unpacked ubuntu-release-upgrader-core:all 1:16.04.7
2016-03-11 12:26:06 status half-installed ubuntu-release-upgrader-core:all 1:16.04.7
2016-03-11 12:26:07 status half-installed ubuntu-release-upgrader-core:all 1:16.04.7
2016-03-11 12:26:07 status unpacked ubuntu-release-upgrader-core:all 1:16.04.8
2016-03-11 12:26:07 status unpacked ubuntu-release-upgrader-core:all 1:16.04.8
2016-03-11 12:26:07 upgrade python3-distupgrade:all 1:16.04.7 1:16.04.8
2016-03-11 12:26:07 status half-configured python3-distupgrade:all 1:16.04.7
2016-03-11 12:26:07 status unpacked python3-distupgrade:all 1:16.04.7
2016-03-11 12:26:07 status half-installed python3-distupgrade:all 1:16.04.7
2016-03-11 12:26:07 status half-installed python3-distupgrade:all 1:16.04.7
2016-03-11 12:26:08 status unpacked python3-distupgrade:all 1:16.04.8
2016-03-11 12:26:08 status unpacked python3-distupgrade:all 1:16.04.8
2016-03-11 12:26:08 upgrade ubuntu-standard:amd64 1.348 1.349
2016-03-11 12:26:08 status half-configured ubuntu-standard:amd64 1.348
2016-03-11 12:26:08 status unpacked ubuntu-standard:amd64 1.348
2016-03-11 12:26:08 status half-installed ubuntu-standard:amd64 1.348
2016-03-11 12:26:08 status half-installed ubuntu-standard:amd64 1.348
2016-03-11 12:26:08 status unpacked ubuntu-standard:amd64 1.349
2016-03-11 12:26:08 status unpacked ubuntu-standard:amd64 1.349
2016-03-11 12:26:08 upgrade mcp-account-manager-goa:amd64 3.12.11-0ubuntu2 3.12.11-0ubuntu3
2016-03-11 12:26:08 status half-configured mcp-account-manager-goa:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:08 status unpacked mcp-account-manager-goa:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:08 status half-installed mcp-account-manager-goa:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:09 status half-installed mcp-account-manager-goa:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:09 status unpacked mcp-account-manager-goa:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:09 status unpacked mcp-account-manager-goa:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:09 upgrade mcp-account-manager-uoa:amd64 3.12.11-0ubuntu2 3.12.11-0ubuntu3
2016-03-11 12:26:09 status half-configured mcp-account-manager-uoa:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:09 status unpacked mcp-account-manager-uoa:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:09 status half-installed mcp-account-manager-uoa:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:09 status half-installed mcp-account-manager-uoa:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:09 status unpacked mcp-account-manager-uoa:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:09 status unpacked mcp-account-manager-uoa:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:10 upgrade account-plugin-jabber:amd64 3.12.11-0ubuntu2 3.12.11-0ubuntu3
2016-03-11 12:26:10 status half-configured account-plugin-jabber:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:10 status unpacked account-plugin-jabber:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:10 status half-installed account-plugin-jabber:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:10 status half-installed account-plugin-jabber:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:10 status unpacked account-plugin-jabber:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:10 status unpacked account-plugin-jabber:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:10 upgrade account-plugin-salut:amd64 3.12.11-0ubuntu2 3.12.11-0ubuntu3
2016-03-11 12:26:10 status half-configured account-plugin-salut:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:10 status unpacked account-plugin-salut:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:10 status half-installed account-plugin-salut:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:10 status half-installed account-plugin-salut:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:11 status unpacked account-plugin-salut:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:11 status unpacked account-plugin-salut:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:11 upgrade libgstreamer1.0-dev:amd64 1.7.2-1 1.7.90-1
2016-03-11 12:26:11 status half-configured libgstreamer1.0-dev:amd64 1.7.2-1
2016-03-11 12:26:11 status unpacked libgstreamer1.0-dev:amd64 1.7.2-1
2016-03-11 12:26:11 status half-installed libgstreamer1.0-dev:amd64 1.7.2-1
2016-03-11 12:26:11 status half-installed libgstreamer1.0-dev:amd64 1.7.2-1
2016-03-11 12:26:12 status unpacked libgstreamer1.0-dev:amd64 1.7.90-1
2016-03-11 12:26:12 status unpacked libgstreamer1.0-dev:amd64 1.7.90-1
2016-03-11 12:26:12 upgrade gir1.2-gstreamer-1.0:amd64 1.7.2-1 1.7.90-1
2016-03-11 12:26:12 status half-configured gir1.2-gstreamer-1.0:amd64 1.7.2-1
2016-03-11 12:26:12 status unpacked gir1.2-gstreamer-1.0:amd64 1.7.2-1
2016-03-11 12:26:12 status half-installed gir1.2-gstreamer-1.0:amd64 1.7.2-1
2016-03-11 12:26:12 status half-installed gir1.2-gstreamer-1.0:amd64 1.7.2-1
2016-03-11 12:26:12 status unpacked gir1.2-gstreamer-1.0:amd64 1.7.90-1
2016-03-11 12:26:12 status unpacked gir1.2-gstreamer-1.0:amd64 1.7.90-1
2016-03-11 12:26:12 upgrade libgstreamer1.0-0-dbg:amd64 1.7.2-1 1.7.90-1
2016-03-11 12:26:12 status half-configured libgstreamer1.0-0-dbg:amd64 1.7.2-1
2016-03-11 12:26:12 status unpacked libgstreamer1.0-0-dbg:amd64 1.7.2-1
2016-03-11 12:26:13 status half-installed libgstreamer1.0-0-dbg:amd64 1.7.2-1
2016-03-11 12:26:13 status half-installed libgstreamer1.0-0-dbg:amd64 1.7.2-1
2016-03-11 12:26:13 status unpacked libgstreamer1.0-0-dbg:amd64 1.7.90-1
2016-03-11 12:26:13 status unpacked libgstreamer1.0-0-dbg:amd64 1.7.90-1
2016-03-11 12:26:13 upgrade libgstreamer1.0-0:amd64 1.7.2-1 1.7.90-1
2016-03-11 12:26:13 status half-configured libgstreamer1.0-0:amd64 1.7.2-1
2016-03-11 12:26:13 status unpacked libgstreamer1.0-0:amd64 1.7.2-1
2016-03-11 12:26:13 status half-installed libgstreamer1.0-0:amd64 1.7.2-1
2016-03-11 12:26:14 status half-installed libgstreamer1.0-0:amd64 1.7.2-1
2016-03-11 12:26:14 status unpacked libgstreamer1.0-0:amd64 1.7.90-1
2016-03-11 12:26:14 status unpacked libgstreamer1.0-0:amd64 1.7.90-1
2016-03-11 12:26:14 upgrade gstreamer1.0-plugins-base-dbg:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:14 status half-configured gstreamer1.0-plugins-base-dbg:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:14 status unpacked gstreamer1.0-plugins-base-dbg:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:14 status half-installed gstreamer1.0-plugins-base-dbg:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:14 status half-installed gstreamer1.0-plugins-base-dbg:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:15 status unpacked gstreamer1.0-plugins-base-dbg:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:15 status unpacked gstreamer1.0-plugins-base-dbg:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:15 upgrade gstreamer1.0-alsa:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:15 status half-configured gstreamer1.0-alsa:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:15 status unpacked gstreamer1.0-alsa:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:15 status half-installed gstreamer1.0-alsa:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:15 status half-installed gstreamer1.0-alsa:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:15 status unpacked gstreamer1.0-alsa:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:15 status unpacked gstreamer1.0-alsa:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:15 upgrade gstreamer1.0-plugins-ugly-amr:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:15 status half-configured gstreamer1.0-plugins-ugly-amr:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:16 status unpacked gstreamer1.0-plugins-ugly-amr:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:16 status half-installed gstreamer1.0-plugins-ugly-amr:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:16 status half-installed gstreamer1.0-plugins-ugly-amr:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:16 status unpacked gstreamer1.0-plugins-ugly-amr:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:16 status unpacked gstreamer1.0-plugins-ugly-amr:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:16 upgrade gstreamer1.0-plugins-ugly:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:16 status half-configured gstreamer1.0-plugins-ugly:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:16 status unpacked gstreamer1.0-plugins-ugly:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:16 status half-installed gstreamer1.0-plugins-ugly:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:16 status half-installed gstreamer1.0-plugins-ugly:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:17 status unpacked gstreamer1.0-plugins-ugly:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:17 status unpacked gstreamer1.0-plugins-ugly:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:17 upgrade gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu2
2016-03-11 12:26:17 status half-configured gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:17 status unpacked gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:17 status half-installed gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:17 status half-installed gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:17 status unpacked gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.90-1ubuntu2
2016-03-11 12:26:17 status unpacked gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.90-1ubuntu2
2016-03-11 12:26:17 upgrade gstreamer1.0-plugins-bad-faad:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu2
2016-03-11 12:26:17 status half-configured gstreamer1.0-plugins-bad-faad:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:17 status unpacked gstreamer1.0-plugins-bad-faad:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:17 status half-installed gstreamer1.0-plugins-bad-faad:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:18 status half-installed gstreamer1.0-plugins-bad-faad:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:18 status unpacked gstreamer1.0-plugins-bad-faad:amd64 1.7.90-1ubuntu2
2016-03-11 12:26:18 status unpacked gstreamer1.0-plugins-bad-faad:amd64 1.7.90-1ubuntu2
2016-03-11 12:26:18 upgrade libgstreamer-plugins-base1.0-0:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:18 status half-configured libgstreamer-plugins-base1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:18 status unpacked libgstreamer-plugins-base1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:18 status half-installed libgstreamer-plugins-base1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:18 status half-installed libgstreamer-plugins-base1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:18 status unpacked libgstreamer-plugins-base1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:19 status unpacked libgstreamer-plugins-base1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:19 upgrade gstreamer1.0-plugins-bad:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu2
2016-03-11 12:26:19 status half-configured gstreamer1.0-plugins-bad:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:19 status unpacked gstreamer1.0-plugins-bad:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:19 status half-installed gstreamer1.0-plugins-bad:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:19 status half-installed gstreamer1.0-plugins-bad:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:19 status unpacked gstreamer1.0-plugins-bad:amd64 1.7.90-1ubuntu2
2016-03-11 12:26:19 status unpacked gstreamer1.0-plugins-bad:amd64 1.7.90-1ubuntu2
2016-03-11 12:26:20 upgrade gstreamer1.0-plugins-good:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:20 status half-configured gstreamer1.0-plugins-good:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:20 status unpacked gstreamer1.0-plugins-good:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:20 status half-installed gstreamer1.0-plugins-good:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:20 status half-installed gstreamer1.0-plugins-good:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:20 status unpacked gstreamer1.0-plugins-good:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:20 status unpacked gstreamer1.0-plugins-good:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:20 upgrade libgstreamer-plugins-good1.0-0:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:20 status half-configured libgstreamer-plugins-good1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:20 status unpacked libgstreamer-plugins-good1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:21 status half-installed libgstreamer-plugins-good1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:21 status half-installed libgstreamer-plugins-good1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:21 status unpacked libgstreamer-plugins-good1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:21 status unpacked libgstreamer-plugins-good1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:21 upgrade libgstreamer-plugins-bad1.0-0:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu2
2016-03-11 12:26:21 status half-configured libgstreamer-plugins-bad1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:21 status unpacked libgstreamer-plugins-bad1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:21 status half-installed libgstreamer-plugins-bad1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:21 status half-installed libgstreamer-plugins-bad1.0-0:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:21 status unpacked libgstreamer-plugins-bad1.0-0:amd64 1.7.90-1ubuntu2
2016-03-11 12:26:22 status unpacked libgstreamer-plugins-bad1.0-0:amd64 1.7.90-1ubuntu2
2016-03-11 12:26:22 upgrade gstreamer1.0-plugins-base:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:22 status half-configured gstreamer1.0-plugins-base:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:22 status unpacked gstreamer1.0-plugins-base:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:22 status half-installed gstreamer1.0-plugins-base:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:22 status half-installed gstreamer1.0-plugins-base:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:22 status unpacked gstreamer1.0-plugins-base:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:22 status unpacked gstreamer1.0-plugins-base:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:22 upgrade gstreamer1.0-x:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:22 status half-configured gstreamer1.0-x:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:22 status unpacked gstreamer1.0-x:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:22 status half-installed gstreamer1.0-x:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:23 status half-installed gstreamer1.0-x:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:23 status unpacked gstreamer1.0-x:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:23 status unpacked gstreamer1.0-x:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:23 upgrade account-plugin-aim:amd64 3.12.11-0ubuntu2 3.12.11-0ubuntu3
2016-03-11 12:26:23 status half-configured account-plugin-aim:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:23 status unpacked account-plugin-aim:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:23 status half-installed account-plugin-aim:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:23 status half-installed account-plugin-aim:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:23 status unpacked account-plugin-aim:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:23 status unpacked account-plugin-aim:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:23 upgrade empathy:amd64 3.12.11-0ubuntu2 3.12.11-0ubuntu3
2016-03-11 12:26:23 status half-configured empathy:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:24 status unpacked empathy:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:24 status half-installed empathy:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:24 status triggers-pending libglib2.0-0:i386 2.47.6-1
2016-03-11 12:26:24 status half-installed empathy:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:24 status triggers-pending libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:26:24 status half-installed empathy:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:24 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:26:24 status half-installed empathy:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:24 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:26:24 status triggers-pending mime-support:all 3.59ubuntu1
2016-03-11 12:26:24 status triggers-pending gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:26:24 status half-installed empathy:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:24 status half-installed empathy:amd64 3.12.11-0ubuntu2
2016-03-11 12:26:25 status unpacked empathy:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:25 status unpacked empathy:amd64 3.12.11-0ubuntu3
2016-03-11 12:26:25 upgrade empathy-common:all 3.12.11-0ubuntu2 3.12.11-0ubuntu3
2016-03-11 12:26:25 status half-configured empathy-common:all 3.12.11-0ubuntu2
2016-03-11 12:26:25 status unpacked empathy-common:all 3.12.11-0ubuntu2
2016-03-11 12:26:25 status half-installed empathy-common:all 3.12.11-0ubuntu2
2016-03-11 12:26:26 status triggers-pending hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:26:26 status half-installed empathy-common:all 3.12.11-0ubuntu2
2016-03-11 12:26:27 status half-installed empathy-common:all 3.12.11-0ubuntu2
2016-03-11 12:26:27 status unpacked empathy-common:all 3.12.11-0ubuntu3
2016-03-11 12:26:27 status unpacked empathy-common:all 3.12.11-0ubuntu3
2016-03-11 12:26:27 upgrade gstreamer1.0-pulseaudio:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:26:27 status half-configured gstreamer1.0-pulseaudio:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:27 status unpacked gstreamer1.0-pulseaudio:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:27 status half-installed gstreamer1.0-pulseaudio:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:27 status half-installed gstreamer1.0-pulseaudio:amd64 1.7.2-1ubuntu1
2016-03-11 12:26:27 status unpacked gstreamer1.0-pulseaudio:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:28 status unpacked gstreamer1.0-pulseaudio:amd64 1.7.90-1ubuntu1
2016-03-11 12:26:28 upgrade libaccount-plugin-generic-oauth:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:28 status half-configured libaccount-plugin-generic-oauth:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:28 status unpacked libaccount-plugin-generic-oauth:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:28 status half-installed libaccount-plugin-generic-oauth:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:28 status half-installed libaccount-plugin-generic-oauth:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:28 status unpacked libaccount-plugin-generic-oauth:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:28 status unpacked libaccount-plugin-generic-oauth:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:28 upgrade account-plugin-facebook:all 0.12+15.10.20150914-0ubuntu1build~pie.1 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:28 status half-configured account-plugin-facebook:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:28 status unpacked account-plugin-facebook:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:28 status half-installed account-plugin-facebook:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:29 status half-installed account-plugin-facebook:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:29 status unpacked account-plugin-facebook:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:29 status unpacked account-plugin-facebook:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:29 upgrade account-plugin-flickr:all 0.12+15.10.20150914-0ubuntu1build~pie.1 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:29 status half-configured account-plugin-flickr:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:29 status unpacked account-plugin-flickr:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:29 status half-installed account-plugin-flickr:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:29 status half-installed account-plugin-flickr:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:29 status unpacked account-plugin-flickr:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:29 status unpacked account-plugin-flickr:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:30 upgrade libaccount-plugin-google:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:30 status half-configured libaccount-plugin-google:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:30 status unpacked libaccount-plugin-google:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:30 status half-installed libaccount-plugin-google:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:30 status half-installed libaccount-plugin-google:amd64 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:30 status unpacked libaccount-plugin-google:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:30 status unpacked libaccount-plugin-google:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:30 upgrade account-plugin-google:all 0.12+15.10.20150914-0ubuntu1build~pie.1 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:30 status half-configured account-plugin-google:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:30 status unpacked account-plugin-google:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:30 status half-installed account-plugin-google:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:31 status half-installed account-plugin-google:all 0.12+15.10.20150914-0ubuntu1build~pie.1
2016-03-11 12:26:31 status unpacked account-plugin-google:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:31 status unpacked account-plugin-google:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:26:31 upgrade libappstream-glib8:amd64 0.5.10-0ubuntu3 0.5.10-0ubuntu4
2016-03-11 12:26:31 status half-configured libappstream-glib8:amd64 0.5.10-0ubuntu3
2016-03-11 12:26:31 status unpacked libappstream-glib8:amd64 0.5.10-0ubuntu3
2016-03-11 12:26:31 status half-installed libappstream-glib8:amd64 0.5.10-0ubuntu3
2016-03-11 12:26:31 status half-installed libappstream-glib8:amd64 0.5.10-0ubuntu3
2016-03-11 12:26:31 status unpacked libappstream-glib8:amd64 0.5.10-0ubuntu4
2016-03-11 12:26:31 status unpacked libappstream-glib8:amd64 0.5.10-0ubuntu4
2016-03-11 12:26:32 upgrade appstream-util:amd64 0.5.10-0ubuntu3 0.5.10-0ubuntu4
2016-03-11 12:26:32 status half-configured appstream-util:amd64 0.5.10-0ubuntu3
2016-03-11 12:26:32 status unpacked appstream-util:amd64 0.5.10-0ubuntu3
2016-03-11 12:26:32 status half-installed appstream-util:amd64 0.5.10-0ubuntu3
2016-03-11 12:26:32 status half-installed appstream-util:amd64 0.5.10-0ubuntu3
2016-03-11 12:26:32 status unpacked appstream-util:amd64 0.5.10-0ubuntu4
2016-03-11 12:26:32 status unpacked appstream-util:amd64 0.5.10-0ubuntu4
2016-03-11 12:26:32 upgrade apt-doc:all 1.2.3 1.2.4
2016-03-11 12:26:32 status half-configured apt-doc:all 1.2.3
2016-03-11 12:26:32 status unpacked apt-doc:all 1.2.3
2016-03-11 12:26:32 status half-installed apt-doc:all 1.2.3
2016-03-11 12:26:33 status half-installed apt-doc:all 1.2.3
2016-03-11 12:26:33 status unpacked apt-doc:all 1.2.4
2016-03-11 12:26:33 status unpacked apt-doc:all 1.2.4
2016-03-11 12:26:33 upgrade archdetect-deb:amd64 1.114ubuntu2 1.114ubuntu3
2016-03-11 12:26:33 status half-configured archdetect-deb:amd64 1.114ubuntu2
2016-03-11 12:26:33 status unpacked archdetect-deb:amd64 1.114ubuntu2
2016-03-11 12:26:33 status half-installed archdetect-deb:amd64 1.114ubuntu2
2016-03-11 12:26:33 status half-installed archdetect-deb:amd64 1.114ubuntu2
2016-03-11 12:26:33 status unpacked archdetect-deb:amd64 1.114ubuntu3
2016-03-11 12:26:33 status unpacked archdetect-deb:amd64 1.114ubuntu3
2016-03-11 12:26:33 upgrade binutils-multiarch-dev:amd64 2.26-5ubuntu1 2.26-6ubuntu1
2016-03-11 12:26:33 status half-configured binutils-multiarch-dev:amd64 2.26-5ubuntu1
2016-03-11 12:26:34 status unpacked binutils-multiarch-dev:amd64 2.26-5ubuntu1
2016-03-11 12:26:34 status half-installed binutils-multiarch-dev:amd64 2.26-5ubuntu1
2016-03-11 12:26:34 status half-installed binutils-multiarch-dev:amd64 2.26-5ubuntu1
2016-03-11 12:26:34 status unpacked binutils-multiarch-dev:amd64 2.26-6ubuntu1
2016-03-11 12:26:34 status unpacked binutils-multiarch-dev:amd64 2.26-6ubuntu1
2016-03-11 12:26:34 upgrade binutils-multiarch:amd64 2.26-5ubuntu1 2.26-6ubuntu1
2016-03-11 12:26:34 status half-configured binutils-multiarch:amd64 2.26-5ubuntu1
2016-03-11 12:26:39 status unpacked binutils-multiarch:amd64 2.26-5ubuntu1
2016-03-11 12:26:39 status half-installed binutils-multiarch:amd64 2.26-5ubuntu1
2016-03-11 12:26:39 status half-installed binutils-multiarch:amd64 2.26-5ubuntu1
2016-03-11 12:26:39 status unpacked binutils-multiarch:amd64 2.26-6ubuntu1
2016-03-11 12:26:39 status unpacked binutils-multiarch:amd64 2.26-6ubuntu1
2016-03-11 12:26:39 upgrade binutils-dev:amd64 2.26-5ubuntu1 2.26-6ubuntu1
2016-03-11 12:26:39 status half-configured binutils-dev:amd64 2.26-5ubuntu1
2016-03-11 12:26:39 status unpacked binutils-dev:amd64 2.26-5ubuntu1
2016-03-11 12:26:39 status half-installed binutils-dev:amd64 2.26-5ubuntu1
2016-03-11 12:26:40 status half-installed binutils-dev:amd64 2.26-5ubuntu1
2016-03-11 12:26:40 status unpacked binutils-dev:amd64 2.26-6ubuntu1
2016-03-11 12:26:40 status unpacked binutils-dev:amd64 2.26-6ubuntu1
2016-03-11 12:26:40 upgrade binutils:amd64 2.26-5ubuntu1 2.26-6ubuntu1
2016-03-11 12:26:40 status half-configured binutils:amd64 2.26-5ubuntu1
2016-03-11 12:26:40 status unpacked binutils:amd64 2.26-5ubuntu1
2016-03-11 12:26:41 status half-installed binutils:amd64 2.26-5ubuntu1
2016-03-11 12:26:41 status half-installed binutils:amd64 2.26-5ubuntu1
2016-03-11 12:26:41 status unpacked binutils:amd64 2.26-6ubuntu1
2016-03-11 12:26:41 status unpacked binutils:amd64 2.26-6ubuntu1
2016-03-11 12:26:41 upgrade binutils-source:all 2.26-5ubuntu1 2.26-6ubuntu1
2016-03-11 12:26:41 status half-configured binutils-source:all 2.26-5ubuntu1
2016-03-11 12:26:42 status unpacked binutils-source:all 2.26-5ubuntu1
2016-03-11 12:26:42 status half-installed binutils-source:all 2.26-5ubuntu1
2016-03-11 12:26:42 status half-installed binutils-source:all 2.26-5ubuntu1
2016-03-11 12:26:42 status unpacked binutils-source:all 2.26-6ubuntu1
2016-03-11 12:26:42 status unpacked binutils-source:all 2.26-6ubuntu1
2016-03-11 12:26:42 upgrade libbluetooth-dev:amd64 5.36-0ubuntu1build~pie.1 5.37-0ubuntu5
2016-03-11 12:26:42 status half-configured libbluetooth-dev:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:42 status unpacked libbluetooth-dev:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:42 status half-installed libbluetooth-dev:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:43 status half-installed libbluetooth-dev:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:43 status unpacked libbluetooth-dev:amd64 5.37-0ubuntu5
2016-03-11 12:26:43 status unpacked libbluetooth-dev:amd64 5.37-0ubuntu5
2016-03-11 12:26:43 upgrade bluez-dbg:amd64 5.36-0ubuntu1build~pie.1 5.37-0ubuntu5
2016-03-11 12:26:43 status half-configured bluez-dbg:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:43 status unpacked bluez-dbg:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:43 status half-installed bluez-dbg:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:44 status half-installed bluez-dbg:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:44 status unpacked bluez-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:26:44 status unpacked bluez-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:26:44 upgrade libbluetooth3-dbg:amd64 5.36-0ubuntu1build~pie.1 5.37-0ubuntu5
2016-03-11 12:26:44 status half-configured libbluetooth3-dbg:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:44 status unpacked libbluetooth3-dbg:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:44 status half-installed libbluetooth3-dbg:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:44 status half-installed libbluetooth3-dbg:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:44 status unpacked libbluetooth3-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:26:44 status unpacked libbluetooth3-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:26:45 upgrade libbluetooth3:amd64 5.36-0ubuntu1build~pie.1 5.37-0ubuntu5
2016-03-11 12:26:45 status half-configured libbluetooth3:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:45 status unpacked libbluetooth3:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:45 status half-installed libbluetooth3:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:45 status half-installed libbluetooth3:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:45 status unpacked libbluetooth3:amd64 5.37-0ubuntu5
2016-03-11 12:26:45 status unpacked libbluetooth3:amd64 5.37-0ubuntu5
2016-03-11 12:26:46 upgrade bluez:amd64 5.36-0ubuntu1build~pie.1 5.37-0ubuntu5
2016-03-11 12:26:46 status half-configured bluez:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:46 status unpacked bluez:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:46 status half-installed bluez:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:46 status triggers-pending dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:26:46 status triggers-pending dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:26:46 status half-installed bluez:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:46 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:26:46 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:26:47 upgrade bluez-cups:amd64 5.36-0ubuntu1build~pie.1 5.37-0ubuntu5
2016-03-11 12:26:47 status half-configured bluez-cups:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:47 status unpacked bluez-cups:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:47 status half-installed bluez-cups:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:47 status half-installed bluez-cups:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:47 status unpacked bluez-cups:amd64 5.37-0ubuntu5
2016-03-11 12:26:47 status unpacked bluez-cups:amd64 5.37-0ubuntu5
2016-03-11 12:26:47 upgrade bluez-obexd:amd64 5.36-0ubuntu1build~pie.1 5.37-0ubuntu5
2016-03-11 12:26:47 status half-configured bluez-obexd:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:47 status unpacked bluez-obexd:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:47 status half-installed bluez-obexd:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:47 status half-installed bluez-obexd:amd64 5.36-0ubuntu1build~pie.1
2016-03-11 12:26:47 status unpacked bluez-obexd:amd64 5.37-0ubuntu5
2016-03-11 12:26:47 status unpacked bluez-obexd:amd64 5.37-0ubuntu5
2016-03-11 12:26:48 upgrade crash:amd64 7.1.4-1ubuntu1 7.1.4-1ubuntu2
2016-03-11 12:26:48 status half-configured crash:amd64 7.1.4-1ubuntu1
2016-03-11 12:26:48 status unpacked crash:amd64 7.1.4-1ubuntu1
2016-03-11 12:26:48 status half-installed crash:amd64 7.1.4-1ubuntu1
2016-03-11 12:26:48 status half-installed crash:amd64 7.1.4-1ubuntu1
2016-03-11 12:26:48 status unpacked crash:amd64 7.1.4-1ubuntu2
2016-03-11 12:26:48 status unpacked crash:amd64 7.1.4-1ubuntu2
2016-03-11 12:26:49 upgrade deja-dup:amd64 34.1-1ubuntu2 34.1-1ubuntu3
2016-03-11 12:26:49 status half-configured deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:49 status unpacked deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:49 status half-installed deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:49 status half-installed deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:49 status half-installed deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:49 status half-installed deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:49 status half-installed deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:49 status half-installed deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:50 status half-installed deja-dup:amd64 34.1-1ubuntu2
2016-03-11 12:26:50 status unpacked deja-dup:amd64 34.1-1ubuntu3
2016-03-11 12:26:50 status unpacked deja-dup:amd64 34.1-1ubuntu3
2016-03-11 12:26:50 upgrade deja-dup-backend-cloudfiles:all 34.1-1ubuntu2 34.1-1ubuntu3
2016-03-11 12:26:50 status half-configured deja-dup-backend-cloudfiles:all 34.1-1ubuntu2
2016-03-11 12:26:50 status unpacked deja-dup-backend-cloudfiles:all 34.1-1ubuntu2
2016-03-11 12:26:50 status half-installed deja-dup-backend-cloudfiles:all 34.1-1ubuntu2
2016-03-11 12:26:50 status half-installed deja-dup-backend-cloudfiles:all 34.1-1ubuntu2
2016-03-11 12:26:51 status unpacked deja-dup-backend-cloudfiles:all 34.1-1ubuntu3
2016-03-11 12:26:51 status unpacked deja-dup-backend-cloudfiles:all 34.1-1ubuntu3
2016-03-11 12:26:51 upgrade deja-dup-backend-gvfs:all 34.1-1ubuntu2 34.1-1ubuntu3
2016-03-11 12:26:51 status half-configured deja-dup-backend-gvfs:all 34.1-1ubuntu2
2016-03-11 12:26:51 status unpacked deja-dup-backend-gvfs:all 34.1-1ubuntu2
2016-03-11 12:26:51 status half-installed deja-dup-backend-gvfs:all 34.1-1ubuntu2
2016-03-11 12:26:51 status half-installed deja-dup-backend-gvfs:all 34.1-1ubuntu2
2016-03-11 12:26:51 status unpacked deja-dup-backend-gvfs:all 34.1-1ubuntu3
2016-03-11 12:26:51 status unpacked deja-dup-backend-gvfs:all 34.1-1ubuntu3
2016-03-11 12:26:51 upgrade deja-dup-backend-s3:all 34.1-1ubuntu2 34.1-1ubuntu3
2016-03-11 12:26:51 status half-configured deja-dup-backend-s3:all 34.1-1ubuntu2
2016-03-11 12:26:52 status unpacked deja-dup-backend-s3:all 34.1-1ubuntu2
2016-03-11 12:26:52 status half-installed deja-dup-backend-s3:all 34.1-1ubuntu2
2016-03-11 12:26:52 status half-installed deja-dup-backend-s3:all 34.1-1ubuntu2
2016-03-11 12:26:52 status unpacked deja-dup-backend-s3:all 34.1-1ubuntu3
2016-03-11 12:26:52 status unpacked deja-dup-backend-s3:all 34.1-1ubuntu3
2016-03-11 12:26:52 upgrade eog:amd64 3.18.2-1 3.18.2-1ubuntu1
2016-03-11 12:26:52 status half-configured eog:amd64 3.18.2-1
2016-03-11 12:26:52 status unpacked eog:amd64 3.18.2-1
2016-03-11 12:26:52 status half-installed eog:amd64 3.18.2-1
2016-03-11 12:26:52 status half-installed eog:amd64 3.18.2-1
2016-03-11 12:26:52 status half-installed eog:amd64 3.18.2-1
2016-03-11 12:26:53 status half-installed eog:amd64 3.18.2-1
2016-03-11 12:26:53 status half-installed eog:amd64 3.18.2-1
2016-03-11 12:26:53 status half-installed eog:amd64 3.18.2-1
2016-03-11 12:26:53 status half-installed eog:amd64 3.18.2-1
2016-03-11 12:26:53 status unpacked eog:amd64 3.18.2-1ubuntu1
2016-03-11 12:26:53 status unpacked eog:amd64 3.18.2-1ubuntu1
2016-03-11 12:26:54 upgrade evince-common:all 3.18.2-1ubuntu3 3.18.2-1ubuntu4
2016-03-11 12:26:54 status half-configured evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:54 status unpacked evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:54 status half-installed evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:54 status half-installed evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:54 status half-installed evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:54 status half-installed evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:54 status half-installed evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:54 status half-installed evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:54 status half-installed evince-common:all 3.18.2-1ubuntu3
2016-03-11 12:26:55 status unpacked evince-common:all 3.18.2-1ubuntu4
2016-03-11 12:26:55 status unpacked evince-common:all 3.18.2-1ubuntu4
2016-03-11 12:26:55 upgrade evince:amd64 3.18.2-1ubuntu3 3.18.2-1ubuntu4
2016-03-11 12:26:55 status half-configured evince:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:55 status unpacked evince:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:55 status half-installed evince:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:55 status triggers-pending mime-support:all 3.59ubuntu1
2016-03-11 12:26:55 status half-installed evince:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:55 status half-installed evince:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:55 status unpacked evince:amd64 3.18.2-1ubuntu4
2016-03-11 12:26:55 status unpacked evince:amd64 3.18.2-1ubuntu4
2016-03-11 12:26:56 upgrade libevdocument3-4:amd64 3.18.2-1ubuntu3 3.18.2-1ubuntu4
2016-03-11 12:26:56 status half-configured libevdocument3-4:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:56 status unpacked libevdocument3-4:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:56 status half-installed libevdocument3-4:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:56 status half-installed libevdocument3-4:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:56 status unpacked libevdocument3-4:amd64 3.18.2-1ubuntu4
2016-03-11 12:26:56 status unpacked libevdocument3-4:amd64 3.18.2-1ubuntu4
2016-03-11 12:26:57 upgrade libevview3-3:amd64 3.18.2-1ubuntu3 3.18.2-1ubuntu4
2016-03-11 12:26:57 status half-configured libevview3-3:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:57 status unpacked libevview3-3:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:57 status half-installed libevview3-3:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:57 status half-installed libevview3-3:amd64 3.18.2-1ubuntu3
2016-03-11 12:26:57 status unpacked libevview3-3:amd64 3.18.2-1ubuntu4
2016-03-11 12:26:57 status unpacked libevview3-3:amd64 3.18.2-1ubuntu4
2016-03-11 12:26:57 upgrade extra-cmake-modules:amd64 5.16.0-1build0pie.1 5.18.0-0ubuntu1
2016-03-11 12:26:57 status half-configured extra-cmake-modules:amd64 5.16.0-1build0pie.1
2016-03-11 12:26:57 status unpacked extra-cmake-modules:amd64 5.16.0-1build0pie.1
2016-03-11 12:26:57 status half-installed extra-cmake-modules:amd64 5.16.0-1build0pie.1
2016-03-11 12:26:57 status half-installed extra-cmake-modules:amd64 5.16.0-1build0pie.1
2016-03-11 12:26:58 status unpacked extra-cmake-modules:amd64 5.18.0-0ubuntu1
2016-03-11 12:26:58 status unpacked extra-cmake-modules:amd64 5.18.0-0ubuntu1
2016-03-11 12:26:58 upgrade firefox-dbg:amd64 44.0.2+build1-0ubuntu1 45.0+build2-0ubuntu1
2016-03-11 12:26:58 status half-configured firefox-dbg:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:26:58 status unpacked firefox-dbg:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:26:58 status half-installed firefox-dbg:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:20 status half-installed firefox-dbg:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:20 status unpacked firefox-dbg:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:20 status unpacked firefox-dbg:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:21 upgrade firefox-dev:amd64 44.0.2+build1-0ubuntu1 45.0+build2-0ubuntu1
2016-03-11 12:27:21 status half-configured firefox-dev:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:21 status unpacked firefox-dev:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:21 status half-installed firefox-dev:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:21 status half-installed firefox-dev:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:21 status unpacked firefox-dev:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:21 status unpacked firefox-dev:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:21 upgrade libgtk2.0-common:all 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:21 status half-configured libgtk2.0-common:all 2.24.29-1ubuntu2
2016-03-11 12:27:21 status unpacked libgtk2.0-common:all 2.24.29-1ubuntu2
2016-03-11 12:27:21 status half-installed libgtk2.0-common:all 2.24.29-1ubuntu2
2016-03-11 12:27:21 status half-installed libgtk2.0-common:all 2.24.29-1ubuntu2
2016-03-11 12:27:22 status unpacked libgtk2.0-common:all 2.24.30-1ubuntu1
2016-03-11 12:27:22 status unpacked libgtk2.0-common:all 2.24.30-1ubuntu1
2016-03-11 12:27:22 upgrade libgtk2.0-bin:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:22 status half-configured libgtk2.0-bin:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:22 status unpacked libgtk2.0-bin:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:22 status half-installed libgtk2.0-bin:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:22 status half-installed libgtk2.0-bin:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:22 status unpacked libgtk2.0-bin:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:22 status unpacked libgtk2.0-bin:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:22 upgrade gtk2-engines-pixbuf:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:22 status half-configured gtk2-engines-pixbuf:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:23 status unpacked gtk2-engines-pixbuf:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:23 status half-installed gtk2-engines-pixbuf:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:23 status half-installed gtk2-engines-pixbuf:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:23 status unpacked gtk2-engines-pixbuf:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:23 status unpacked gtk2-engines-pixbuf:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:23 upgrade libgtk2.0-0-dbg:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:23 status half-configured libgtk2.0-0-dbg:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:23 status unpacked libgtk2.0-0-dbg:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:23 status half-installed libgtk2.0-0-dbg:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:24 status half-installed libgtk2.0-0-dbg:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:24 status unpacked libgtk2.0-0-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:24 status unpacked libgtk2.0-0-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:24 upgrade libgail-dbg:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:24 status half-configured libgail-dbg:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:24 status unpacked libgail-dbg:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:24 status half-installed libgail-dbg:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:25 status half-installed libgail-dbg:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:25 status unpacked libgail-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:25 status unpacked libgail-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:25 upgrade libgail-dev:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:25 status half-configured libgail-dev:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:25 status unpacked libgail-dev:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:25 status half-installed libgail-dev:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:25 status half-installed libgail-dev:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:25 status unpacked libgail-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:25 status unpacked libgail-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:26 upgrade libgail-common:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:26 status half-configured libgail-common:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:26 status unpacked libgail-common:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:26 status half-installed libgail-common:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:26 status half-installed libgail-common:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:26 status unpacked libgail-common:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:26 status unpacked libgail-common:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:26 upgrade libgail18:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:26 status half-configured libgail18:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:26 status unpacked libgail18:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:26 status half-installed libgail18:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:27 status half-installed libgail18:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:27 status unpacked libgail18:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:27 status unpacked libgail18:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:27 upgrade libgtk2.0-dev:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:27 status half-configured libgtk2.0-dev:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:27 status unpacked libgtk2.0-dev:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:27 status half-installed libgtk2.0-dev:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:28 status half-installed libgtk2.0-dev:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:28 status unpacked libgtk2.0-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:28 status unpacked libgtk2.0-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:28 upgrade gir1.2-gtk-2.0:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:28 status half-configured gir1.2-gtk-2.0:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:28 status unpacked gir1.2-gtk-2.0:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:28 status half-installed gir1.2-gtk-2.0:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:28 status half-installed gir1.2-gtk-2.0:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:28 status unpacked gir1.2-gtk-2.0:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:29 status unpacked gir1.2-gtk-2.0:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:29 upgrade libgtk2.0-0:amd64 2.24.29-1ubuntu2 2.24.30-1ubuntu1
2016-03-11 12:27:29 status half-configured libgtk2.0-0:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:29 status unpacked libgtk2.0-0:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:29 status half-installed libgtk2.0-0:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:29 status half-installed libgtk2.0-0:amd64 2.24.29-1ubuntu2
2016-03-11 12:27:30 status unpacked libgtk2.0-0:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:30 status unpacked libgtk2.0-0:amd64 2.24.30-1ubuntu1
2016-03-11 12:27:30 upgrade firefox:amd64 44.0.2+build1-0ubuntu1 45.0+build2-0ubuntu1
2016-03-11 12:27:30 status half-configured firefox:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:30 status unpacked firefox:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:30 status half-installed firefox:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:34 status half-installed firefox:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:34 status half-installed firefox:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:34 status unpacked firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:34 status unpacked firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:34 upgrade firefox-locale-en:amd64 44.0.2+build1-0ubuntu1 45.0+build2-0ubuntu1
2016-03-11 12:27:34 status half-configured firefox-locale-en:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:34 status unpacked firefox-locale-en:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:34 status half-installed firefox-locale-en:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:35 status half-installed firefox-locale-en:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:35 status unpacked firefox-locale-en:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:35 status unpacked firefox-locale-en:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:35 upgrade firefox-locale-fr:amd64 44.0.2+build1-0ubuntu1 45.0+build2-0ubuntu1
2016-03-11 12:27:35 status half-configured firefox-locale-fr:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:35 status unpacked firefox-locale-fr:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:35 status half-installed firefox-locale-fr:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:35 status half-installed firefox-locale-fr:amd64 44.0.2+build1-0ubuntu1
2016-03-11 12:27:35 status unpacked firefox-locale-fr:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:35 status unpacked firefox-locale-fr:amd64 45.0+build2-0ubuntu1
2016-03-11 12:27:36 upgrade libnss3-nssdb:all 2:3.21-1ubuntu3 2:3.21-1ubuntu4
2016-03-11 12:27:36 status half-configured libnss3-nssdb:all 2:3.21-1ubuntu3
2016-03-11 12:27:36 status unpacked libnss3-nssdb:all 2:3.21-1ubuntu3
2016-03-11 12:27:36 status half-installed libnss3-nssdb:all 2:3.21-1ubuntu3
2016-03-11 12:27:36 status half-installed libnss3-nssdb:all 2:3.21-1ubuntu3
2016-03-11 12:27:36 status unpacked libnss3-nssdb:all 2:3.21-1ubuntu4
2016-03-11 12:27:36 status unpacked libnss3-nssdb:all 2:3.21-1ubuntu4
2016-03-11 12:27:36 trigproc ureadahead:amd64 0.100.0-19build~pie.1 <aucune>
2016-03-11 12:27:36 status half-configured ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:27:36 status installed ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:27:36 trigproc doc-base:all 0.10.7 <aucune>
2016-03-11 12:27:36 status half-configured doc-base:all 0.10.7
2016-03-11 12:27:36 status installed doc-base:all 0.10.7
2016-03-11 12:27:37 trigproc systemd:amd64 229-2ubuntu1 <aucune>
2016-03-11 12:27:37 status half-configured systemd:amd64 229-2ubuntu1
2016-03-11 12:27:37 status installed systemd:amd64 229-2ubuntu1
2016-03-11 12:27:37 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:27:37 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:27:37 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:27:37 trigproc ufw:all 0.35-0ubuntu1 <aucune>
2016-03-11 12:27:37 status half-configured ufw:all 0.35-0ubuntu1
2016-03-11 12:27:37 status installed ufw:all 0.35-0ubuntu1
2016-03-11 12:27:37 trigproc libglib2.0-0:i386 2.47.6-1 <aucune>
2016-03-11 12:27:37 status half-configured libglib2.0-0:i386 2.47.6-1
2016-03-11 12:27:37 status installed libglib2.0-0:i386 2.47.6-1
2016-03-11 12:27:37 trigproc libglib2.0-0:amd64 2.47.6-1 <aucune>
2016-03-11 12:27:37 status half-configured libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:27:38 status installed libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:27:38 trigproc desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1 <aucune>
2016-03-11 12:27:38 status half-configured desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:27:38 status installed desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:27:38 trigproc gnome-menus:amd64 3.13.3-6ubuntu3 <aucune>
2016-03-11 12:27:38 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:27:38 status installed gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:27:38 trigproc mime-support:all 3.59ubuntu1 <aucune>
2016-03-11 12:27:38 status half-configured mime-support:all 3.59ubuntu1
2016-03-11 12:27:38 status installed mime-support:all 3.59ubuntu1
2016-03-11 12:27:38 trigproc gconf2:amd64 3.2.6-3ubuntu6build0pie.1 <aucune>
2016-03-11 12:27:38 status half-configured gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:27:39 status installed gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:27:39 trigproc hicolor-icon-theme:all 0.15-0ubuntu1 <aucune>
2016-03-11 12:27:39 status half-configured hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:27:39 status installed hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:27:39 trigproc dbus:amd64 1.10.6-1ubuntu2 <aucune>
2016-03-11 12:27:39 status half-configured dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:27:39 status installed dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:27:39 startup packages remove
2016-03-11 12:27:39 status installed libnss3-dbg:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:39 remove libnss3-dbg:amd64 2:3.21-1ubuntu3 <aucune>
2016-03-11 12:27:39 status half-configured libnss3-dbg:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:39 status half-installed libnss3-dbg:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:40 status config-files libnss3-dbg:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:40 status config-files libnss3-dbg:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:40 status config-files libnss3-dbg:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:40 status not-installed libnss3-dbg:amd64 <aucune>
2016-03-11 12:27:40 startup archives unpack
2016-03-11 12:27:40 upgrade libnss3:amd64 2:3.21-1ubuntu3 2:3.21-1ubuntu4
2016-03-11 12:27:40 status half-configured libnss3:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:40 status unpacked libnss3:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:40 status half-installed libnss3:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:41 status half-installed libnss3:amd64 2:3.21-1ubuntu3
2016-03-11 12:27:41 status unpacked libnss3:amd64 2:3.21-1ubuntu4
2016-03-11 12:27:41 status unpacked libnss3:amd64 2:3.21-1ubuntu4
2016-03-11 12:27:41 install libnss3-dbg:amd64 <aucune> 2:3.21-1ubuntu4
2016-03-11 12:27:41 status half-installed libnss3-dbg:amd64 2:3.21-1ubuntu4
2016-03-11 12:27:42 status unpacked libnss3-dbg:amd64 2:3.21-1ubuntu4
2016-03-11 12:27:42 status unpacked libnss3-dbg:amd64 2:3.21-1ubuntu4
2016-03-11 12:27:42 upgrade flashplugin-installer:amd64 11.2.202.569ubuntu1 11.2.202.577ubuntu1
2016-03-11 12:27:42 status half-configured flashplugin-installer:amd64 11.2.202.569ubuntu1
2016-03-11 12:27:42 status unpacked flashplugin-installer:amd64 11.2.202.569ubuntu1
2016-03-11 12:27:42 status half-installed flashplugin-installer:amd64 11.2.202.569ubuntu1
2016-03-11 12:27:42 status triggers-pending update-notifier-common:all 3.166
2016-03-11 12:27:42 status half-installed flashplugin-installer:amd64 11.2.202.569ubuntu1
2016-03-11 12:27:43 status half-installed flashplugin-installer:amd64 11.2.202.569ubuntu1
2016-03-11 12:27:43 status unpacked flashplugin-installer:amd64 11.2.202.577ubuntu1
2016-03-11 12:27:43 status unpacked flashplugin-installer:amd64 11.2.202.577ubuntu1
2016-03-11 12:27:43 upgrade gedit-common:all 3.18.3-0ubuntu3 3.18.3-0ubuntu4
2016-03-11 12:27:43 status half-configured gedit-common:all 3.18.3-0ubuntu3
2016-03-11 12:27:43 status unpacked gedit-common:all 3.18.3-0ubuntu3
2016-03-11 12:27:43 status half-installed gedit-common:all 3.18.3-0ubuntu3
2016-03-11 12:27:43 status triggers-pending gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:27:43 status half-installed gedit-common:all 3.18.3-0ubuntu3
2016-03-11 12:27:44 status triggers-pending libglib2.0-0:i386 2.47.6-1
2016-03-11 12:27:44 status half-installed gedit-common:all 3.18.3-0ubuntu3
2016-03-11 12:27:44 status triggers-pending libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:27:44 status half-installed gedit-common:all 3.18.3-0ubuntu3
2016-03-11 12:27:44 status half-installed gedit-common:all 3.18.3-0ubuntu3
2016-03-11 12:27:44 status unpacked gedit-common:all 3.18.3-0ubuntu4
2016-03-11 12:27:44 status unpacked gedit-common:all 3.18.3-0ubuntu4
2016-03-11 12:27:45 upgrade gedit:amd64 3.18.3-0ubuntu3 3.18.3-0ubuntu4
2016-03-11 12:27:45 status half-configured gedit:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:45 status unpacked gedit:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:45 status half-installed gedit:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:45 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:27:45 status half-installed gedit:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:45 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:27:45 status triggers-pending mime-support:all 3.59ubuntu1
2016-03-11 12:27:45 status half-installed gedit:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:45 status unpacked gedit:amd64 3.18.3-0ubuntu4
2016-03-11 12:27:46 status unpacked gedit:amd64 3.18.3-0ubuntu4
2016-03-11 12:27:46 upgrade gedit-dev:amd64 3.18.3-0ubuntu3 3.18.3-0ubuntu4
2016-03-11 12:27:46 status half-configured gedit-dev:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:46 status unpacked gedit-dev:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:46 status half-installed gedit-dev:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:46 status half-installed gedit-dev:amd64 3.18.3-0ubuntu3
2016-03-11 12:27:46 status unpacked gedit-dev:amd64 3.18.3-0ubuntu4
2016-03-11 12:27:46 status unpacked gedit-dev:amd64 3.18.3-0ubuntu4
2016-03-11 12:27:46 upgrade gir1.2-evince-3.0:amd64 3.18.2-1ubuntu3 3.18.2-1ubuntu4
2016-03-11 12:27:46 status half-configured gir1.2-evince-3.0:amd64 3.18.2-1ubuntu3
2016-03-11 12:27:46 status unpacked gir1.2-evince-3.0:amd64 3.18.2-1ubuntu3
2016-03-11 12:27:46 status half-installed gir1.2-evince-3.0:amd64 3.18.2-1ubuntu3
2016-03-11 12:27:47 status half-installed gir1.2-evince-3.0:amd64 3.18.2-1ubuntu3
2016-03-11 12:27:47 status unpacked gir1.2-evince-3.0:amd64 3.18.2-1ubuntu4
2016-03-11 12:27:47 status unpacked gir1.2-evince-3.0:amd64 3.18.2-1ubuntu4
2016-03-11 12:27:47 upgrade gir1.2-gst-plugins-base-1.0:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:27:47 status half-configured gir1.2-gst-plugins-base-1.0:amd64 1.7.2-1ubuntu1
2016-03-11 12:27:47 status unpacked gir1.2-gst-plugins-base-1.0:amd64 1.7.2-1ubuntu1
2016-03-11 12:27:47 status half-installed gir1.2-gst-plugins-base-1.0:amd64 1.7.2-1ubuntu1
2016-03-11 12:27:47 status half-installed gir1.2-gst-plugins-base-1.0:amd64 1.7.2-1ubuntu1
2016-03-11 12:27:47 status unpacked gir1.2-gst-plugins-base-1.0:amd64 1.7.90-1ubuntu1
2016-03-11 12:27:47 status unpacked gir1.2-gst-plugins-base-1.0:amd64 1.7.90-1ubuntu1
2016-03-11 12:27:48 upgrade mutter:amd64 3.18.2-0ubuntu1 3.18.3-0ubuntu1
2016-03-11 12:27:48 status half-configured mutter:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:48 status unpacked mutter:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:48 status half-installed mutter:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:48 status half-installed mutter:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:48 status half-installed mutter:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:48 status unpacked mutter:amd64 3.18.3-0ubuntu1
2016-03-11 12:27:48 status unpacked mutter:amd64 3.18.3-0ubuntu1
2016-03-11 12:27:48 upgrade gir1.2-mutter-3.0:amd64 3.18.2-0ubuntu1 3.18.3-0ubuntu1
2016-03-11 12:27:48 status half-configured gir1.2-mutter-3.0:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:48 status unpacked gir1.2-mutter-3.0:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:48 status half-installed gir1.2-mutter-3.0:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:48 status half-installed gir1.2-mutter-3.0:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:49 status unpacked gir1.2-mutter-3.0:amd64 3.18.3-0ubuntu1
2016-03-11 12:27:49 status unpacked gir1.2-mutter-3.0:amd64 3.18.3-0ubuntu1
2016-03-11 12:27:49 upgrade libmutter0g:amd64 3.18.2-0ubuntu1 3.18.3-0ubuntu1
2016-03-11 12:27:49 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:27:49 status half-configured libmutter0g:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:49 status unpacked libmutter0g:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:49 status half-installed libmutter0g:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:49 status half-installed libmutter0g:amd64 3.18.2-0ubuntu1
2016-03-11 12:27:49 status unpacked libmutter0g:amd64 3.18.3-0ubuntu1
2016-03-11 12:27:49 status unpacked libmutter0g:amd64 3.18.3-0ubuntu1
2016-03-11 12:27:50 upgrade mutter-common:all 3.18.2-0ubuntu1 3.18.3-0ubuntu1
2016-03-11 12:27:50 status half-configured mutter-common:all 3.18.2-0ubuntu1
2016-03-11 12:27:50 status unpacked mutter-common:all 3.18.2-0ubuntu1
2016-03-11 12:27:50 status half-installed mutter-common:all 3.18.2-0ubuntu1
2016-03-11 12:27:50 status half-installed mutter-common:all 3.18.2-0ubuntu1
2016-03-11 12:27:50 status half-installed mutter-common:all 3.18.2-0ubuntu1
2016-03-11 12:27:50 status half-installed mutter-common:all 3.18.2-0ubuntu1
2016-03-11 12:27:50 status half-installed mutter-common:all 3.18.2-0ubuntu1
2016-03-11 12:27:52 status unpacked mutter-common:all 3.18.3-0ubuntu1
2016-03-11 12:27:52 status unpacked mutter-common:all 3.18.3-0ubuntu1
2016-03-11 12:27:52 upgrade libtotem0:amd64 3.18.1-1ubuntu3 3.18.1-1ubuntu4
2016-03-11 12:27:52 status half-configured libtotem0:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:52 status unpacked libtotem0:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:52 status half-installed libtotem0:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:53 status half-installed libtotem0:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:53 status unpacked libtotem0:amd64 3.18.1-1ubuntu4
2016-03-11 12:27:53 status unpacked libtotem0:amd64 3.18.1-1ubuntu4
2016-03-11 12:27:53 upgrade totem-plugins:amd64 3.18.1-1ubuntu3 3.18.1-1ubuntu4
2016-03-11 12:27:53 status half-configured totem-plugins:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:53 status unpacked totem-plugins:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:53 status half-installed totem-plugins:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:53 status half-installed totem-plugins:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:54 status unpacked totem-plugins:amd64 3.18.1-1ubuntu4
2016-03-11 12:27:54 status unpacked totem-plugins:amd64 3.18.1-1ubuntu4
2016-03-11 12:27:54 upgrade totem:amd64 3.18.1-1ubuntu3 3.18.1-1ubuntu4
2016-03-11 12:27:54 status half-configured totem:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:54 status unpacked totem:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:54 status half-installed totem:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:54 status half-installed totem:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:54 status half-installed totem:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:54 status unpacked totem:amd64 3.18.1-1ubuntu4
2016-03-11 12:27:54 status unpacked totem:amd64 3.18.1-1ubuntu4
2016-03-11 12:27:54 upgrade totem-common:all 3.18.1-1ubuntu3 3.18.1-1ubuntu4
2016-03-11 12:27:54 status half-configured totem-common:all 3.18.1-1ubuntu3
2016-03-11 12:27:54 status unpacked totem-common:all 3.18.1-1ubuntu3
2016-03-11 12:27:55 status half-installed totem-common:all 3.18.1-1ubuntu3
2016-03-11 12:27:55 status half-installed totem-common:all 3.18.1-1ubuntu3
2016-03-11 12:27:55 status triggers-pending hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:27:55 status half-installed totem-common:all 3.18.1-1ubuntu3
2016-03-11 12:27:55 status half-installed totem-common:all 3.18.1-1ubuntu3
2016-03-11 12:27:55 status half-installed totem-common:all 3.18.1-1ubuntu3
2016-03-11 12:27:55 status half-installed totem-common:all 3.18.1-1ubuntu3
2016-03-11 12:27:55 status unpacked totem-common:all 3.18.1-1ubuntu4
2016-03-11 12:27:55 status unpacked totem-common:all 3.18.1-1ubuntu4
2016-03-11 12:27:56 upgrade gir1.2-totem-1.0:amd64 3.18.1-1ubuntu3 3.18.1-1ubuntu4
2016-03-11 12:27:56 status half-configured gir1.2-totem-1.0:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:56 status unpacked gir1.2-totem-1.0:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:56 status half-installed gir1.2-totem-1.0:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:56 status half-installed gir1.2-totem-1.0:amd64 3.18.1-1ubuntu3
2016-03-11 12:27:56 status unpacked gir1.2-totem-1.0:amd64 3.18.1-1ubuntu4
2016-03-11 12:27:56 status unpacked gir1.2-totem-1.0:amd64 3.18.1-1ubuntu4
2016-03-11 12:27:56 upgrade libudisks2-0:amd64 2.1.6-2+git1build~pie.1 2.1.7-1
2016-03-11 12:27:56 status half-configured libudisks2-0:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:27:56 status unpacked libudisks2-0:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:27:56 status half-installed libudisks2-0:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:27:56 status half-installed libudisks2-0:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:27:57 status unpacked libudisks2-0:amd64 2.1.7-1
2016-03-11 12:27:57 status unpacked libudisks2-0:amd64 2.1.7-1
2016-03-11 12:27:57 upgrade gir1.2-udisks-2.0:amd64 2.1.6-2+git1build~pie.1 2.1.7-1
2016-03-11 12:27:57 status half-configured gir1.2-udisks-2.0:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:27:57 status unpacked gir1.2-udisks-2.0:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:27:57 status half-installed gir1.2-udisks-2.0:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:27:57 status half-installed gir1.2-udisks-2.0:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:27:57 status unpacked gir1.2-udisks-2.0:amd64 2.1.7-1
2016-03-11 12:27:57 status unpacked gir1.2-udisks-2.0:amd64 2.1.7-1
2016-03-11 12:27:57 upgrade gnome-calendar:amd64 3.18.2.1-2 3.19.91-0ubuntu3
2016-03-11 12:27:57 status half-configured gnome-calendar:amd64 3.18.2.1-2
2016-03-11 12:27:57 status unpacked gnome-calendar:amd64 3.18.2.1-2
2016-03-11 12:27:58 status half-installed gnome-calendar:amd64 3.18.2.1-2
2016-03-11 12:27:58 status half-installed gnome-calendar:amd64 3.18.2.1-2
2016-03-11 12:27:58 status half-installed gnome-calendar:amd64 3.18.2.1-2
2016-03-11 12:27:58 status half-installed gnome-calendar:amd64 3.18.2.1-2
2016-03-11 12:27:58 status half-installed gnome-calendar:amd64 3.18.2.1-2
2016-03-11 12:27:58 status half-installed gnome-calendar:amd64 3.18.2.1-2
2016-03-11 12:27:58 status unpacked gnome-calendar:amd64 3.19.91-0ubuntu3
2016-03-11 12:27:58 status unpacked gnome-calendar:amd64 3.19.91-0ubuntu3
2016-03-11 12:27:58 upgrade gnome-control-center-data:all 1:3.18.2-1ubuntu4 1:3.18.2-1ubuntu5
2016-03-11 12:27:58 status half-configured gnome-control-center-data:all 1:3.18.2-1ubuntu4
2016-03-11 12:27:59 status unpacked gnome-control-center-data:all 1:3.18.2-1ubuntu4
2016-03-11 12:27:59 status half-installed gnome-control-center-data:all 1:3.18.2-1ubuntu4
2016-03-11 12:27:59 status half-installed gnome-control-center-data:all 1:3.18.2-1ubuntu4
2016-03-11 12:27:59 status half-installed gnome-control-center-data:all 1:3.18.2-1ubuntu4
2016-03-11 12:28:00 status unpacked gnome-control-center-data:all 1:3.18.2-1ubuntu5
2016-03-11 12:28:00 status unpacked gnome-control-center-data:all 1:3.18.2-1ubuntu5
2016-03-11 12:28:00 upgrade gnome-control-center:amd64 1:3.18.2-1ubuntu4 1:3.18.2-1ubuntu5
2016-03-11 12:28:00 status half-configured gnome-control-center:amd64 1:3.18.2-1ubuntu4
2016-03-11 12:28:00 status unpacked gnome-control-center:amd64 1:3.18.2-1ubuntu4
2016-03-11 12:28:00 status half-installed gnome-control-center:amd64 1:3.18.2-1ubuntu4
2016-03-11 12:28:00 status half-installed gnome-control-center:amd64 1:3.18.2-1ubuntu4
2016-03-11 12:28:00 status triggers-pending menu:amd64 2.1.47ubuntu1
2016-03-11 12:28:00 status half-installed gnome-control-center:amd64 1:3.18.2-1ubuntu4
2016-03-11 12:28:01 status half-installed gnome-control-center:amd64 1:3.18.2-1ubuntu4
2016-03-11 12:28:01 status triggers-awaited menu:amd64 2.1.47ubuntu1
2016-03-11 12:28:01 status unpacked gnome-control-center:amd64 1:3.18.2-1ubuntu5
2016-03-11 12:28:01 status unpacked gnome-control-center:amd64 1:3.18.2-1ubuntu5
2016-03-11 12:28:01 upgrade gnome-control-center-dev:all 1:3.18.2-1ubuntu4 1:3.18.2-1ubuntu5
2016-03-11 12:28:01 status half-configured gnome-control-center-dev:all 1:3.18.2-1ubuntu4
2016-03-11 12:28:01 status unpacked gnome-control-center-dev:all 1:3.18.2-1ubuntu4
2016-03-11 12:28:01 status half-installed gnome-control-center-dev:all 1:3.18.2-1ubuntu4
2016-03-11 12:28:01 status half-installed gnome-control-center-dev:all 1:3.18.2-1ubuntu4
2016-03-11 12:28:01 status unpacked gnome-control-center-dev:all 1:3.18.2-1ubuntu5
2016-03-11 12:28:01 status unpacked gnome-control-center-dev:all 1:3.18.2-1ubuntu5
2016-03-11 12:28:02 upgrade gnome-shell:amd64 3.18.3-3ubuntu1 3.18.4-0ubuntu1
2016-03-11 12:28:02 status half-configured gnome-shell:amd64 3.18.3-3ubuntu1
2016-03-11 12:28:02 status unpacked gnome-shell:amd64 3.18.3-3ubuntu1
2016-03-11 12:28:02 status half-installed gnome-shell:amd64 3.18.3-3ubuntu1
2016-03-11 12:28:02 status half-installed gnome-shell:amd64 3.18.3-3ubuntu1
2016-03-11 12:28:02 status half-installed gnome-shell:amd64 3.18.3-3ubuntu1
2016-03-11 12:28:02 status half-installed gnome-shell:amd64 3.18.3-3ubuntu1
2016-03-11 12:28:02 status half-installed gnome-shell:amd64 3.18.3-3ubuntu1
2016-03-11 12:28:02 status unpacked gnome-shell:amd64 3.18.4-0ubuntu1
2016-03-11 12:28:02 status unpacked gnome-shell:amd64 3.18.4-0ubuntu1
2016-03-11 12:28:03 upgrade gnome-shell-common:all 3.18.3-3ubuntu1 3.18.4-0ubuntu1
2016-03-11 12:28:03 status half-configured gnome-shell-common:all 3.18.3-3ubuntu1
2016-03-11 12:28:03 status unpacked gnome-shell-common:all 3.18.3-3ubuntu1
2016-03-11 12:28:03 status half-installed gnome-shell-common:all 3.18.3-3ubuntu1
2016-03-11 12:28:03 status half-installed gnome-shell-common:all 3.18.3-3ubuntu1
2016-03-11 12:28:03 status half-installed gnome-shell-common:all 3.18.3-3ubuntu1
2016-03-11 12:28:03 status half-installed gnome-shell-common:all 3.18.3-3ubuntu1
2016-03-11 12:28:03 status half-installed gnome-shell-common:all 3.18.3-3ubuntu1
2016-03-11 12:28:03 status unpacked gnome-shell-common:all 3.18.4-0ubuntu1
2016-03-11 12:28:03 status unpacked gnome-shell-common:all 3.18.4-0ubuntu1
2016-03-11 12:28:04 upgrade gnome-software:amd64 3.19.91~git20160229.ceb6b9d-0ubuntu1 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:28:04 status half-configured gnome-software:amd64 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:04 status unpacked gnome-software:amd64 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:04 status half-installed gnome-software:amd64 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:04 status half-installed gnome-software:amd64 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:04 status half-installed gnome-software:amd64 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:04 status half-installed gnome-software:amd64 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:04 status half-installed gnome-software:amd64 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:04 status unpacked gnome-software:amd64 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:28:04 status unpacked gnome-software:amd64 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:28:04 upgrade gnome-software-common:all 3.19.91~git20160229.ceb6b9d-0ubuntu1 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:28:04 status half-configured gnome-software-common:all 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:05 status unpacked gnome-software-common:all 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:05 status half-installed gnome-software-common:all 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:05 status half-installed gnome-software-common:all 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:05 status half-installed gnome-software-common:all 3.19.91~git20160229.ceb6b9d-0ubuntu1
2016-03-11 12:28:05 status unpacked gnome-software-common:all 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:28:05 status unpacked gnome-software-common:all 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:28:05 upgrade libqt5core5a:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:05 status half-configured libqt5core5a:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:05 status unpacked libqt5core5a:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:05 status half-installed libqt5core5a:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:06 status half-installed libqt5core5a:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:06 status unpacked libqt5core5a:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:06 status unpacked libqt5core5a:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:06 upgrade libqt5dbus5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:06 status half-configured libqt5dbus5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:06 status unpacked libqt5dbus5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:06 status half-installed libqt5dbus5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:07 status half-installed libqt5dbus5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:07 status unpacked libqt5dbus5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:07 status unpacked libqt5dbus5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:07 upgrade libqt5network5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:07 status half-configured libqt5network5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:07 status unpacked libqt5network5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:07 status half-installed libqt5network5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:07 status half-installed libqt5network5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:07 status unpacked libqt5network5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:07 status unpacked libqt5network5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:08 upgrade libqt5gui5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:08 status half-configured libqt5gui5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:08 status unpacked libqt5gui5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:08 status half-installed libqt5gui5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:08 status half-installed libqt5gui5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:08 status unpacked libqt5gui5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:08 status unpacked libqt5gui5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:09 upgrade libqt5widgets5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:09 status half-configured libqt5widgets5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:09 status unpacked libqt5widgets5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:09 status half-installed libqt5widgets5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:09 status half-installed libqt5widgets5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:09 status unpacked libqt5widgets5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:09 status unpacked libqt5widgets5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:10 upgrade libqt5printsupport5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:10 status half-configured libqt5printsupport5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:10 status unpacked libqt5printsupport5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:10 status half-installed libqt5printsupport5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:10 status half-installed libqt5printsupport5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:10 status unpacked libqt5printsupport5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:10 status unpacked libqt5printsupport5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:10 upgrade gnuplot5-qt:amd64 5.0.3+dfsg1-2 5.0.3+dfsg2-1
2016-03-11 12:28:10 status half-configured gnuplot5-qt:amd64 5.0.3+dfsg1-2
2016-03-11 12:28:10 status unpacked gnuplot5-qt:amd64 5.0.3+dfsg1-2
2016-03-11 12:28:11 status half-installed gnuplot5-qt:amd64 5.0.3+dfsg1-2
2016-03-11 12:28:11 status half-installed gnuplot5-qt:amd64 5.0.3+dfsg1-2
2016-03-11 12:28:11 status half-installed gnuplot5-qt:amd64 5.0.3+dfsg1-2
2016-03-11 12:28:11 status unpacked gnuplot5-qt:amd64 5.0.3+dfsg2-1
2016-03-11 12:28:11 status unpacked gnuplot5-qt:amd64 5.0.3+dfsg2-1
2016-03-11 12:28:11 upgrade gnuplot5-data:all 5.0.3+dfsg1-2 5.0.3+dfsg2-1
2016-03-11 12:28:11 status half-configured gnuplot5-data:all 5.0.3+dfsg1-2
2016-03-11 12:28:11 status unpacked gnuplot5-data:all 5.0.3+dfsg1-2
2016-03-11 12:28:11 status half-installed gnuplot5-data:all 5.0.3+dfsg1-2
2016-03-11 12:28:11 status half-installed gnuplot5-data:all 5.0.3+dfsg1-2
2016-03-11 12:28:12 status unpacked gnuplot5-data:all 5.0.3+dfsg2-1
2016-03-11 12:28:12 status unpacked gnuplot5-data:all 5.0.3+dfsg2-1
2016-03-11 12:28:12 upgrade gstreamer1.0-libav:amd64 1.7.2-1 1.7.90-1
2016-03-11 12:28:12 status half-configured gstreamer1.0-libav:amd64 1.7.2-1
2016-03-11 12:28:12 status unpacked gstreamer1.0-libav:amd64 1.7.2-1
2016-03-11 12:28:12 status half-installed gstreamer1.0-libav:amd64 1.7.2-1
2016-03-11 12:28:12 status half-installed gstreamer1.0-libav:amd64 1.7.2-1
2016-03-11 12:28:12 status unpacked gstreamer1.0-libav:amd64 1.7.90-1
2016-03-11 12:28:12 status unpacked gstreamer1.0-libav:amd64 1.7.90-1
2016-03-11 12:28:13 upgrade gstreamer1.0-tools:amd64 1.7.2-1 1.7.90-1
2016-03-11 12:28:13 status half-configured gstreamer1.0-tools:amd64 1.7.2-1
2016-03-11 12:28:13 status unpacked gstreamer1.0-tools:amd64 1.7.2-1
2016-03-11 12:28:13 status half-installed gstreamer1.0-tools:amd64 1.7.2-1
2016-03-11 12:28:13 status half-installed gstreamer1.0-tools:amd64 1.7.2-1
2016-03-11 12:28:13 status unpacked gstreamer1.0-tools:amd64 1.7.90-1
2016-03-11 12:28:13 status unpacked gstreamer1.0-tools:amd64 1.7.90-1
2016-03-11 12:28:13 upgrade gstreamer1.0-plugins-base-apps:amd64 1.7.2-1ubuntu1 1.7.90-1ubuntu1
2016-03-11 12:28:13 status half-configured gstreamer1.0-plugins-base-apps:amd64 1.7.2-1ubuntu1
2016-03-11 12:28:13 status unpacked gstreamer1.0-plugins-base-apps:amd64 1.7.2-1ubuntu1
2016-03-11 12:28:13 status half-installed gstreamer1.0-plugins-base-apps:amd64 1.7.2-1ubuntu1
2016-03-11 12:28:13 status half-installed gstreamer1.0-plugins-base-apps:amd64 1.7.2-1ubuntu1
2016-03-11 12:28:14 status unpacked gstreamer1.0-plugins-base-apps:amd64 1.7.90-1ubuntu1
2016-03-11 12:28:14 status unpacked gstreamer1.0-plugins-base-apps:amd64 1.7.90-1ubuntu1
2016-03-11 12:28:14 upgrade hunspell-en-ca:all 1:4.2.1-0ubuntu3 1:5.1.0-1ubuntu1
2016-03-11 12:28:14 status half-configured hunspell-en-ca:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:14 status unpacked hunspell-en-ca:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:14 status half-installed hunspell-en-ca:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:14 status triggers-pending postgresql-common:all 172
2016-03-11 12:28:14 status half-installed hunspell-en-ca:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:14 status half-installed hunspell-en-ca:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:14 status triggers-pending postgresql-common:all 172
2016-03-11 12:28:14 status unpacked hunspell-en-ca:all 1:5.1.0-1ubuntu1
2016-03-11 12:28:14 status unpacked hunspell-en-ca:all 1:5.1.0-1ubuntu1
2016-03-11 12:28:15 upgrade hunspell-en-us:all 20070829-6ubuntu2 20070829-6ubuntu3
2016-03-11 12:28:15 status half-configured hunspell-en-us:all 20070829-6ubuntu2
2016-03-11 12:28:15 status unpacked hunspell-en-us:all 20070829-6ubuntu2
2016-03-11 12:28:15 status half-installed hunspell-en-us:all 20070829-6ubuntu2
2016-03-11 12:28:15 status half-installed hunspell-en-us:all 20070829-6ubuntu2
2016-03-11 12:28:15 status half-installed hunspell-en-us:all 20070829-6ubuntu2
2016-03-11 12:28:15 status unpacked hunspell-en-us:all 20070829-6ubuntu3
2016-03-11 12:28:15 status unpacked hunspell-en-us:all 20070829-6ubuntu3
2016-03-11 12:28:15 upgrade hyphen-fr:all 1:4.2.1-0ubuntu3 1:5.1.0-1ubuntu1
2016-03-11 12:28:15 status half-configured hyphen-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:15 status unpacked hyphen-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:15 status half-installed hyphen-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:15 status half-installed hyphen-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:15 status half-installed hyphen-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:28:16 status unpacked hyphen-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:28:16 status unpacked hyphen-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:28:16 upgrade systemd-shim:amd64 9-1bzr4 9-1bzr4ubuntu1
2016-03-11 12:28:16 status half-configured systemd-shim:amd64 9-1bzr4
2016-03-11 12:28:16 status unpacked systemd-shim:amd64 9-1bzr4
2016-03-11 12:28:16 status half-installed systemd-shim:amd64 9-1bzr4
2016-03-11 12:28:16 status triggers-pending dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:28:16 status half-installed systemd-shim:amd64 9-1bzr4
2016-03-11 12:28:17 status unpacked systemd-shim:amd64 9-1bzr4ubuntu1
2016-03-11 12:28:17 status unpacked systemd-shim:amd64 9-1bzr4ubuntu1
2016-03-11 12:28:17 upgrade indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu1 15.10+16.04.20160129-0ubuntu2
2016-03-11 12:28:17 status half-configured indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu1
2016-03-11 12:28:17 status unpacked indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu1
2016-03-11 12:28:17 status half-installed indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu1
2016-03-11 12:28:17 status half-installed indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu1
2016-03-11 12:28:17 status half-installed indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu1
2016-03-11 12:28:18 status half-installed indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu1
2016-03-11 12:28:18 status unpacked indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu2
2016-03-11 12:28:18 status unpacked indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu2
2016-03-11 12:28:18 upgrade junit4:all 4.12-2ubuntu1 4.12-4ubuntu1
2016-03-11 12:28:18 status half-configured junit4:all 4.12-2ubuntu1
2016-03-11 12:28:18 status unpacked junit4:all 4.12-2ubuntu1
2016-03-11 12:28:18 status half-installed junit4:all 4.12-2ubuntu1
2016-03-11 12:28:18 status half-installed junit4:all 4.12-2ubuntu1
2016-03-11 12:28:18 status unpacked junit4:all 4.12-4ubuntu1
2016-03-11 12:28:18 status unpacked junit4:all 4.12-4ubuntu1
2016-03-11 12:28:19 upgrade libqt5sql5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:19 status half-configured libqt5sql5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:19 status unpacked libqt5sql5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:19 status half-installed libqt5sql5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:19 status half-installed libqt5sql5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:19 status unpacked libqt5sql5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:19 status unpacked libqt5sql5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:19 upgrade libqt5sql5-sqlite:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:19 status half-configured libqt5sql5-sqlite:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:19 status unpacked libqt5sql5-sqlite:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:19 status half-installed libqt5sql5-sqlite:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:19 status half-installed libqt5sql5-sqlite:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:20 status unpacked libqt5sql5-sqlite:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:20 status unpacked libqt5sql5-sqlite:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:20 upgrade qml-module-org-kde-activities:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:20 status half-configured qml-module-org-kde-activities:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:20 status unpacked qml-module-org-kde-activities:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:20 status half-installed qml-module-org-kde-activities:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:20 status half-installed qml-module-org-kde-activities:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:20 status unpacked qml-module-org-kde-activities:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:20 status unpacked qml-module-org-kde-activities:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:21 upgrade libkf5activities5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:21 status half-configured libkf5activities5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:21 status unpacked libkf5activities5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:21 status half-installed libkf5activities5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:21 status half-installed libkf5activities5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:21 status unpacked libkf5activities5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:21 status unpacked libkf5activities5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:21 upgrade libkf5dbusaddons5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:21 status half-configured libkf5dbusaddons5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:21 status unpacked libkf5dbusaddons5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:21 status half-installed libkf5dbusaddons5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:22 status half-installed libkf5dbusaddons5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:22 status unpacked libkf5dbusaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:22 status unpacked libkf5dbusaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:22 upgrade libkf5dbusaddons-data:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:22 status half-configured libkf5dbusaddons-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:22 status unpacked libkf5dbusaddons-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:23 status half-installed libkf5dbusaddons-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:24 status half-installed libkf5dbusaddons-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:24 status unpacked libkf5dbusaddons-data:all 5.18.0-0ubuntu1
2016-03-11 12:28:24 status unpacked libkf5dbusaddons-data:all 5.18.0-0ubuntu1
2016-03-11 12:28:24 upgrade libkf5windowsystem5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:24 status half-configured libkf5windowsystem5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:24 status unpacked libkf5windowsystem5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:24 status half-installed libkf5windowsystem5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:24 status half-installed libkf5windowsystem5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:24 status unpacked libkf5windowsystem5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:25 status unpacked libkf5windowsystem5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:25 upgrade libkf5windowsystem-data:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:25 status half-configured libkf5windowsystem-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:25 status unpacked libkf5windowsystem-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:25 status half-installed libkf5windowsystem-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:25 status half-installed libkf5windowsystem-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:25 status unpacked libkf5windowsystem-data:all 5.18.0-0ubuntu1
2016-03-11 12:28:25 status unpacked libkf5windowsystem-data:all 5.18.0-0ubuntu1
2016-03-11 12:28:25 upgrade kactivities:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:25 status half-configured kactivities:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:25 status unpacked kactivities:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:25 status half-installed kactivities:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:26 status half-installed kactivities:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:26 status unpacked kactivities:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:26 status unpacked kactivities:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:26 upgrade kamera:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:26 status half-configured kamera:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:26 status unpacked kamera:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:26 status half-installed kamera:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:26 status half-installed kamera:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:27 status unpacked kamera:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:27 status unpacked kamera:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:27 upgrade libqt5xml5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:27 status half-configured libqt5xml5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:27 status unpacked libqt5xml5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:27 status half-installed libqt5xml5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:27 status half-installed libqt5xml5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:27 status unpacked libqt5xml5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:27 status unpacked libqt5xml5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:28 upgrade kapman:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:28 status half-configured kapman:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:28 status unpacked kapman:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:28 status half-installed kapman:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:28 status half-installed kapman:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:28 status half-installed kapman:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:28 status half-installed kapman:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:28 status half-installed kapman:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:28 status unpacked kapman:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:29 status unpacked kapman:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:29 upgrade kde-runtime:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:29 status half-configured kde-runtime:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:29 status unpacked kde-runtime:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:29 status half-installed kde-runtime:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:29 status half-installed kde-runtime:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:30 status half-installed kde-runtime:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:30 status unpacked kde-runtime:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:30 status unpacked kde-runtime:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:30 upgrade kde-runtime-data:all 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:30 status half-configured kde-runtime-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:30 status unpacked kde-runtime-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:30 status half-installed kde-runtime-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:31 status triggers-pending shared-mime-info:amd64 1.5-2build~pie.1
2016-03-11 12:28:31 status half-installed kde-runtime-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:32 status half-installed kde-runtime-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:32 status triggers-pending dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:28:32 status half-installed kde-runtime-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:33 status unpacked kde-runtime-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:28:33 status unpacked kde-runtime-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:28:33 upgrade plasma-scriptengine-javascript:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:33 status half-configured plasma-scriptengine-javascript:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:33 status unpacked plasma-scriptengine-javascript:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:33 status half-installed plasma-scriptengine-javascript:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:33 status half-installed plasma-scriptengine-javascript:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:33 status unpacked plasma-scriptengine-javascript:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:33 status unpacked plasma-scriptengine-javascript:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:34 upgrade kerneloops-daemon:amd64 0.12+git20090217-3ubuntu9 0.12+git20140509-2ubuntu1
2016-03-11 12:28:34 status half-configured kerneloops-daemon:amd64 0.12+git20090217-3ubuntu9
2016-03-11 12:28:34 status unpacked kerneloops-daemon:amd64 0.12+git20090217-3ubuntu9
2016-03-11 12:28:34 status half-installed kerneloops-daemon:amd64 0.12+git20090217-3ubuntu9
2016-03-11 12:28:34 status triggers-pending systemd:amd64 229-2ubuntu1
2016-03-11 12:28:34 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:28:34 status half-installed kerneloops-daemon:amd64 0.12+git20090217-3ubuntu9
2016-03-11 12:28:34 status unpacked kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:28:35 status unpacked kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:28:35 upgrade kinit:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:35 status half-configured kinit:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:35 status unpacked kinit:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:35 status half-installed kinit:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:35 status half-installed kinit:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:35 status unpacked kinit:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:35 status unpacked kinit:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:35 upgrade libkompareinterface5:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:35 status half-configured libkompareinterface5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:36 status unpacked libkompareinterface5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:36 status half-installed libkompareinterface5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:36 status half-installed libkompareinterface5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:36 status unpacked libkompareinterface5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:36 status unpacked libkompareinterface5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:36 upgrade libkomparediff2-5:amd64 4:15.08.2-0ubuntu2 4:15.12.1-0ubuntu1
2016-03-11 12:28:36 status half-configured libkomparediff2-5:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:36 status unpacked libkomparediff2-5:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:36 status half-installed libkomparediff2-5:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:36 status half-installed libkomparediff2-5:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:36 status unpacked libkomparediff2-5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:37 status unpacked libkomparediff2-5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:37 upgrade kompare:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:37 status half-configured kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:37 status unpacked kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:37 status half-installed kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:37 status half-installed kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:37 status half-installed kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:37 status unpacked kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:37 status unpacked kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:37 upgrade kpart5-kompare:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:37 status half-configured kpart5-kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:38 status unpacked kpart5-kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:38 status half-installed kpart5-kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:38 status half-installed kpart5-kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:38 status half-installed kpart5-kompare:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:38 status unpacked kpart5-kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:38 status unpacked kpart5-kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:38 upgrade libkf5waylandserver5:amd64 4:5.4.3-0ubuntu1 4:5.5.4-0ubuntu1
2016-03-11 12:28:38 status half-configured libkf5waylandserver5:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:38 status unpacked libkf5waylandserver5:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:38 status half-installed libkf5waylandserver5:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:39 status half-installed libkf5waylandserver5:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:39 status unpacked libkf5waylandserver5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:28:39 status unpacked libkf5waylandserver5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:28:39 upgrade libkf5waylandclient5:amd64 4:5.4.3-0ubuntu1 4:5.5.4-0ubuntu1
2016-03-11 12:28:39 status half-configured libkf5waylandclient5:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:39 status unpacked libkf5waylandclient5:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:39 status half-installed libkf5waylandclient5:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:39 status half-installed libkf5waylandclient5:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:39 status unpacked libkf5waylandclient5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:28:39 status unpacked libkf5waylandclient5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:28:40 upgrade kwayland-data:all 4:5.4.3-0ubuntu1 4:5.5.4-0ubuntu1
2016-03-11 12:28:40 status half-configured kwayland-data:all 4:5.4.3-0ubuntu1
2016-03-11 12:28:40 status unpacked kwayland-data:all 4:5.4.3-0ubuntu1
2016-03-11 12:28:40 status half-installed kwayland-data:all 4:5.4.3-0ubuntu1
2016-03-11 12:28:40 status half-installed kwayland-data:all 4:5.4.3-0ubuntu1
2016-03-11 12:28:40 status unpacked kwayland-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:28:40 status unpacked kwayland-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:28:40 upgrade libkf5idletime5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:40 status half-configured libkf5idletime5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:40 status unpacked libkf5idletime5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:40 status half-installed libkf5idletime5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:41 status half-installed libkf5idletime5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:41 status unpacked libkf5idletime5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:41 status unpacked libkf5idletime5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:41 upgrade kwayland-integration:amd64 4:5.4.3-0ubuntu1 4:5.5.4-0ubuntu1
2016-03-11 12:28:41 status half-configured kwayland-integration:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:41 status unpacked kwayland-integration:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:41 status half-installed kwayland-integration:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:41 status half-installed kwayland-integration:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:28:41 status unpacked kwayland-integration:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:28:41 status unpacked kwayland-integration:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:28:41 upgrade libcommons-cli-java:all 1.3.1-2ubuntu1 1.3.1-3ubuntu1
2016-03-11 12:28:41 status half-configured libcommons-cli-java:all 1.3.1-2ubuntu1
2016-03-11 12:28:41 status unpacked libcommons-cli-java:all 1.3.1-2ubuntu1
2016-03-11 12:28:42 status half-installed libcommons-cli-java:all 1.3.1-2ubuntu1
2016-03-11 12:28:42 status half-installed libcommons-cli-java:all 1.3.1-2ubuntu1
2016-03-11 12:28:42 status unpacked libcommons-cli-java:all 1.3.1-3ubuntu1
2016-03-11 12:28:42 status unpacked libcommons-cli-java:all 1.3.1-3ubuntu1
2016-03-11 12:28:42 upgrade libcommons-lang-java:all 2.6-5ubuntu1 2.6-6ubuntu1
2016-03-11 12:28:42 status half-configured libcommons-lang-java:all 2.6-5ubuntu1
2016-03-11 12:28:42 status unpacked libcommons-lang-java:all 2.6-5ubuntu1
2016-03-11 12:28:42 status half-installed libcommons-lang-java:all 2.6-5ubuntu1
2016-03-11 12:28:42 status half-installed libcommons-lang-java:all 2.6-5ubuntu1
2016-03-11 12:28:42 status unpacked libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:28:43 status unpacked libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:28:43 upgrade libgraphite2-3:amd64 1.3.5-1ubuntu1 1.3.6-1ubuntu1
2016-03-11 12:28:43 status half-configured libgraphite2-3:amd64 1.3.5-1ubuntu1
2016-03-11 12:28:43 status unpacked libgraphite2-3:amd64 1.3.5-1ubuntu1
2016-03-11 12:28:43 status half-installed libgraphite2-3:amd64 1.3.5-1ubuntu1
2016-03-11 12:28:43 status half-installed libgraphite2-3:amd64 1.3.5-1ubuntu1
2016-03-11 12:28:43 status unpacked libgraphite2-3:amd64 1.3.6-1ubuntu1
2016-03-11 12:28:43 status unpacked libgraphite2-3:amd64 1.3.6-1ubuntu1
2016-03-11 12:28:43 upgrade libgtk-3-bin:amd64 3.18.8-1ubuntu1 3.18.8-1ubuntu2
2016-03-11 12:28:43 status half-configured libgtk-3-bin:amd64 3.18.8-1ubuntu1
2016-03-11 12:28:44 status unpacked libgtk-3-bin:amd64 3.18.8-1ubuntu1
2016-03-11 12:28:44 status half-installed libgtk-3-bin:amd64 3.18.8-1ubuntu1
2016-03-11 12:28:44 status half-installed libgtk-3-bin:amd64 3.18.8-1ubuntu1
2016-03-11 12:28:44 status unpacked libgtk-3-bin:amd64 3.18.8-1ubuntu2
2016-03-11 12:28:44 status unpacked libgtk-3-bin:amd64 3.18.8-1ubuntu2
2016-03-11 12:28:44 upgrade libjasper1:amd64 1.900.1-debian1-2.4build~pie.1 1.900.1-debian1-2.4ubuntu1
2016-03-11 12:28:44 status half-configured libjasper1:amd64 1.900.1-debian1-2.4build~pie.1
2016-03-11 12:28:44 status unpacked libjasper1:amd64 1.900.1-debian1-2.4build~pie.1
2016-03-11 12:28:44 status half-installed libjasper1:amd64 1.900.1-debian1-2.4build~pie.1
2016-03-11 12:28:45 status half-installed libjasper1:amd64 1.900.1-debian1-2.4build~pie.1
2016-03-11 12:28:45 status unpacked libjasper1:amd64 1.900.1-debian1-2.4ubuntu1
2016-03-11 12:28:45 status unpacked libjasper1:amd64 1.900.1-debian1-2.4ubuntu1
2016-03-11 12:28:45 upgrade libjs-sphinxdoc:all 1.3.5-1ubuntu3 1.3.6-2ubuntu1
2016-03-11 12:28:45 status half-configured libjs-sphinxdoc:all 1.3.5-1ubuntu3
2016-03-11 12:28:45 status unpacked libjs-sphinxdoc:all 1.3.5-1ubuntu3
2016-03-11 12:28:45 status half-installed libjs-sphinxdoc:all 1.3.5-1ubuntu3
2016-03-11 12:28:45 status half-installed libjs-sphinxdoc:all 1.3.5-1ubuntu3
2016-03-11 12:28:45 status unpacked libjs-sphinxdoc:all 1.3.6-2ubuntu1
2016-03-11 12:28:45 status unpacked libjs-sphinxdoc:all 1.3.6-2ubuntu1
2016-03-11 12:28:46 upgrade libkcompactdisc4:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:46 status half-configured libkcompactdisc4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:46 status unpacked libkcompactdisc4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:46 status half-installed libkcompactdisc4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:46 status half-installed libkcompactdisc4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:46 status unpacked libkcompactdisc4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:46 status unpacked libkcompactdisc4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:46 upgrade libkcddb4:amd64 4:15.08.2-0ubuntu2 4:15.12.1-0ubuntu1
2016-03-11 12:28:46 status half-configured libkcddb4:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:46 status unpacked libkcddb4:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:47 status half-installed libkcddb4:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:47 status half-installed libkcddb4:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:47 status unpacked libkcddb4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:47 status unpacked libkcddb4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:47 upgrade libqt5sql5-mysql:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:47 status half-configured libqt5sql5-mysql:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:47 status unpacked libqt5sql5-mysql:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:47 status half-installed libqt5sql5-mysql:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:47 status half-installed libqt5sql5-mysql:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:28:47 status unpacked libqt5sql5-mysql:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:47 status unpacked libqt5sql5-mysql:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:28:48 upgrade akonadi-server:amd64 4:15.08.2-0ubuntu3 4:15.12.1-0ubuntu2
2016-03-11 12:28:48 status half-configured akonadi-server:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:48 status unpacked akonadi-server:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:48 status half-installed akonadi-server:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:48 status half-installed akonadi-server:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:48 status half-installed akonadi-server:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:48 status unpacked akonadi-server:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:28:48 status unpacked akonadi-server:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:28:48 upgrade akonadi-backend-mysql:all 4:15.08.2-0ubuntu3 4:15.12.1-0ubuntu2
2016-03-11 12:28:48 status half-configured akonadi-backend-mysql:all 4:15.08.2-0ubuntu3
2016-03-11 12:28:49 status unpacked akonadi-backend-mysql:all 4:15.08.2-0ubuntu3
2016-03-11 12:28:49 status half-installed akonadi-backend-mysql:all 4:15.08.2-0ubuntu3
2016-03-11 12:28:49 status half-installed akonadi-backend-mysql:all 4:15.08.2-0ubuntu3
2016-03-11 12:28:49 status unpacked akonadi-backend-mysql:all 4:15.12.1-0ubuntu2
2016-03-11 12:28:49 status unpacked akonadi-backend-mysql:all 4:15.12.1-0ubuntu2
2016-03-11 12:28:49 upgrade libkf5akonadiprivate5:amd64 4:15.08.2-0ubuntu3 4:15.12.1-0ubuntu2
2016-03-11 12:28:49 status half-configured libkf5akonadiprivate5:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:49 status unpacked libkf5akonadiprivate5:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:49 status half-installed libkf5akonadiprivate5:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:49 status half-installed libkf5akonadiprivate5:amd64 4:15.08.2-0ubuntu3
2016-03-11 12:28:50 status unpacked libkf5akonadiprivate5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:28:50 status unpacked libkf5akonadiprivate5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:28:50 upgrade libkf5attica5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:50 status half-configured libkf5attica5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:50 status unpacked libkf5attica5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:50 status half-installed libkf5attica5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:50 status half-installed libkf5attica5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:50 status unpacked libkf5attica5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:50 status unpacked libkf5attica5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:51 upgrade libkf5calendarcore5:amd64 4:15.08.2-0ubuntu2 4:15.12.1-0ubuntu1
2016-03-11 12:28:51 status half-configured libkf5calendarcore5:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:51 status unpacked libkf5calendarcore5:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:51 status half-installed libkf5calendarcore5:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:51 status half-installed libkf5calendarcore5:amd64 4:15.08.2-0ubuntu2
2016-03-11 12:28:51 status unpacked libkf5calendarcore5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:51 status unpacked libkf5calendarcore5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:51 upgrade libkf5calendarutils5:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu2
2016-03-11 12:28:51 status half-configured libkf5calendarutils5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:51 status unpacked libkf5calendarutils5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:51 status half-installed libkf5calendarutils5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:52 status half-installed libkf5calendarutils5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:52 status unpacked libkf5calendarutils5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:28:52 status unpacked libkf5calendarutils5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:28:52 upgrade libkf5contacts5:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:52 status half-configured libkf5contacts5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:52 status unpacked libkf5contacts5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:52 status half-installed libkf5contacts5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:52 status half-installed libkf5contacts5:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:28:52 status unpacked libkf5contacts5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:52 status unpacked libkf5contacts5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:28:53 upgrade libkf5contacts-data:all 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:28:53 status half-configured libkf5contacts-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:53 status unpacked libkf5contacts-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:53 status half-installed libkf5contacts-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:53 status half-installed libkf5contacts-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:28:53 status unpacked libkf5contacts-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:28:53 status unpacked libkf5contacts-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:28:53 upgrade libkf5dbusaddons-bin:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:53 status half-configured libkf5dbusaddons-bin:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:53 status unpacked libkf5dbusaddons-bin:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:53 status half-installed libkf5dbusaddons-bin:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:55 status half-installed libkf5dbusaddons-bin:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:55 status unpacked libkf5dbusaddons-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:55 status unpacked libkf5dbusaddons-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:55 upgrade libkf5dnssd5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:55 status half-configured libkf5dnssd5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:55 status unpacked libkf5dnssd5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:56 status half-installed libkf5dnssd5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:56 status half-installed libkf5dnssd5:amd64 5.15.0-0ubuntu2
2016-03-11 12:28:56 status unpacked libkf5dnssd5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:56 status unpacked libkf5dnssd5:amd64 5.18.0-0ubuntu1
2016-03-11 12:28:56 upgrade libkf5dnssd-data:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:28:56 status half-configured libkf5dnssd-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:56 status unpacked libkf5dnssd-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:56 status half-installed libkf5dnssd-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:56 status half-installed libkf5dnssd-data:all 5.15.0-0ubuntu2
2016-03-11 12:28:56 status unpacked libkf5dnssd-data:all 5.18.0-0ubuntu1
2016-03-11 12:28:56 status unpacked libkf5dnssd-data:all 5.18.0-0ubuntu1
2016-03-11 12:28:57 upgrade libkf5gapicore5:amd64 5.0.0-0ubuntu3 5.1.0-1ubuntu1
2016-03-11 12:28:57 status half-configured libkf5gapicore5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:57 status unpacked libkf5gapicore5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:57 status half-installed libkf5gapicore5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:57 status half-installed libkf5gapicore5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:57 status unpacked libkf5gapicore5:amd64 5.1.0-1ubuntu1
2016-03-11 12:28:57 status unpacked libkf5gapicore5:amd64 5.1.0-1ubuntu1
2016-03-11 12:28:57 upgrade libkf5gapicontacts5:amd64 5.0.0-0ubuntu3 5.1.0-1ubuntu1
2016-03-11 12:28:57 status half-configured libkf5gapicontacts5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:58 status unpacked libkf5gapicontacts5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:58 status half-installed libkf5gapicontacts5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:58 status half-installed libkf5gapicontacts5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:58 status unpacked libkf5gapicontacts5:amd64 5.1.0-1ubuntu1
2016-03-11 12:28:58 status unpacked libkf5gapicontacts5:amd64 5.1.0-1ubuntu1
2016-03-11 12:28:58 upgrade libkf5gapitasks5:amd64 5.0.0-0ubuntu3 5.1.0-1ubuntu1
2016-03-11 12:28:58 status half-configured libkf5gapitasks5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:58 status unpacked libkf5gapitasks5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:58 status half-installed libkf5gapitasks5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:58 status half-installed libkf5gapitasks5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:58 status unpacked libkf5gapitasks5:amd64 5.1.0-1ubuntu1
2016-03-11 12:28:59 status unpacked libkf5gapitasks5:amd64 5.1.0-1ubuntu1
2016-03-11 12:28:59 upgrade libkf5gapicalendar5:amd64 5.0.0-0ubuntu3 5.1.0-1ubuntu1
2016-03-11 12:28:59 status half-configured libkf5gapicalendar5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:59 status unpacked libkf5gapicalendar5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:59 status half-installed libkf5gapicalendar5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:59 status half-installed libkf5gapicalendar5:amd64 5.0.0-0ubuntu3
2016-03-11 12:28:59 status unpacked libkf5gapicalendar5:amd64 5.1.0-1ubuntu1
2016-03-11 12:28:59 status unpacked libkf5gapicalendar5:amd64 5.1.0-1ubuntu1
2016-03-11 12:28:59 upgrade libkf5gapidrive5:amd64 5.0.0-0ubuntu3 5.1.0-1ubuntu1
2016-03-11 12:28:59 status half-configured libkf5gapidrive5:amd64 5.0.0-0ubuntu3
2016-03-11 12:29:00 status unpacked libkf5gapidrive5:amd64 5.0.0-0ubuntu3
2016-03-11 12:29:00 status half-installed libkf5gapidrive5:amd64 5.0.0-0ubuntu3
2016-03-11 12:29:00 status half-installed libkf5gapidrive5:amd64 5.0.0-0ubuntu3
2016-03-11 12:29:00 status unpacked libkf5gapidrive5:amd64 5.1.0-1ubuntu1
2016-03-11 12:29:00 status unpacked libkf5gapidrive5:amd64 5.1.0-1ubuntu1
2016-03-11 12:29:00 upgrade libkf5gapi-data:all 5.0.0-0ubuntu3 5.1.0-1ubuntu1
2016-03-11 12:29:00 status half-configured libkf5gapi-data:all 5.0.0-0ubuntu3
2016-03-11 12:29:00 status unpacked libkf5gapi-data:all 5.0.0-0ubuntu3
2016-03-11 12:29:00 status half-installed libkf5gapi-data:all 5.0.0-0ubuntu3
2016-03-11 12:29:00 status half-installed libkf5gapi-data:all 5.0.0-0ubuntu3
2016-03-11 12:29:01 status unpacked libkf5gapi-data:all 5.1.0-1ubuntu1
2016-03-11 12:29:01 status unpacked libkf5gapi-data:all 5.1.0-1ubuntu1
2016-03-11 12:29:01 upgrade libkf5gpgmepp5:amd64 15.08.2-0ubuntu1 15.12.1-0ubuntu1
2016-03-11 12:29:01 status half-configured libkf5gpgmepp5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:01 status unpacked libkf5gpgmepp5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:01 status half-installed libkf5gpgmepp5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:01 status half-installed libkf5gpgmepp5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:01 status unpacked libkf5gpgmepp5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:01 status unpacked libkf5gpgmepp5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:02 upgrade libkf5guiaddons5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:02 status half-configured libkf5guiaddons5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:02 status unpacked libkf5guiaddons5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:02 status half-installed libkf5guiaddons5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:02 status half-installed libkf5guiaddons5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:02 status unpacked libkf5guiaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:02 status unpacked libkf5guiaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:02 upgrade libkf5holidays5:amd64 15.08.2-0ubuntu1 15.12.1-1ubuntu1
2016-03-11 12:29:02 status half-configured libkf5holidays5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:02 status unpacked libkf5holidays5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:02 status half-installed libkf5holidays5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:02 status half-installed libkf5holidays5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:03 status unpacked libkf5holidays5:amd64 15.12.1-1ubuntu1
2016-03-11 12:29:03 status unpacked libkf5holidays5:amd64 15.12.1-1ubuntu1
2016-03-11 12:29:03 upgrade libkf5holidays-data:all 15.08.2-0ubuntu1 15.12.1-1ubuntu1
2016-03-11 12:29:03 status half-configured libkf5holidays-data:all 15.08.2-0ubuntu1
2016-03-11 12:29:03 status unpacked libkf5holidays-data:all 15.08.2-0ubuntu1
2016-03-11 12:29:03 status half-installed libkf5holidays-data:all 15.08.2-0ubuntu1
2016-03-11 12:29:03 status half-installed libkf5holidays-data:all 15.08.2-0ubuntu1
2016-03-11 12:29:03 status unpacked libkf5holidays-data:all 15.12.1-1ubuntu1
2016-03-11 12:29:03 status unpacked libkf5holidays-data:all 15.12.1-1ubuntu1
2016-03-11 12:29:04 upgrade libkf5mime5:amd64 15.08.2-0ubuntu1 15.12.1-0ubuntu1
2016-03-11 12:29:04 status half-configured libkf5mime5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:04 status unpacked libkf5mime5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:04 status half-installed libkf5mime5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:04 status half-installed libkf5mime5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:04 status unpacked libkf5mime5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:04 status unpacked libkf5mime5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:04 upgrade libkf5imap5:amd64 15.08.2-0ubuntu1 15.12.1-0ubuntu1
2016-03-11 12:29:04 status half-configured libkf5imap5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:04 status unpacked libkf5imap5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:04 status half-installed libkf5imap5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:05 status half-installed libkf5imap5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:05 status unpacked libkf5imap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:05 status unpacked libkf5imap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:05 upgrade libkf5itemmodels5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:05 status half-configured libkf5itemmodels5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:05 status unpacked libkf5itemmodels5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:05 status half-installed libkf5itemmodels5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:05 status half-installed libkf5itemmodels5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:05 status unpacked libkf5itemmodels5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:05 status unpacked libkf5itemmodels5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:06 upgrade libkf5itemviews5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:06 status half-configured libkf5itemviews5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:06 status unpacked libkf5itemviews5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:06 status half-installed libkf5itemviews5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:06 status half-installed libkf5itemviews5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:06 status unpacked libkf5itemviews5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:06 status unpacked libkf5itemviews5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:06 upgrade libkf5itemviews-data:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:06 status half-configured libkf5itemviews-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:06 status unpacked libkf5itemviews-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:06 status half-installed libkf5itemviews-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:07 status half-installed libkf5itemviews-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:07 status unpacked libkf5itemviews-data:all 5.18.0-0ubuntu1
2016-03-11 12:29:07 status unpacked libkf5itemviews-data:all 5.18.0-0ubuntu1
2016-03-11 12:29:07 upgrade libkf5js5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:07 status half-configured libkf5js5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:07 status unpacked libkf5js5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:07 status half-installed libkf5js5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:07 status half-installed libkf5js5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:07 status unpacked libkf5js5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:07 status unpacked libkf5js5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:08 upgrade libkf5kontactinterface5:amd64 15.08.2-0ubuntu1 15.12.1-1ubuntu1
2016-03-11 12:29:08 status half-configured libkf5kontactinterface5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:08 status unpacked libkf5kontactinterface5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:08 status half-installed libkf5kontactinterface5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:08 status half-installed libkf5kontactinterface5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:08 status unpacked libkf5kontactinterface5:amd64 15.12.1-1ubuntu1
2016-03-11 12:29:08 status unpacked libkf5kontactinterface5:amd64 15.12.1-1ubuntu1
2016-03-11 12:29:08 upgrade libkf5kontactinterface-data:all 15.08.2-0ubuntu1 15.12.1-1ubuntu1
2016-03-11 12:29:08 status half-configured libkf5kontactinterface-data:all 15.08.2-0ubuntu1
2016-03-11 12:29:08 status unpacked libkf5kontactinterface-data:all 15.08.2-0ubuntu1
2016-03-11 12:29:08 status half-installed libkf5kontactinterface-data:all 15.08.2-0ubuntu1
2016-03-11 12:29:09 status half-installed libkf5kontactinterface-data:all 15.08.2-0ubuntu1
2016-03-11 12:29:09 status unpacked libkf5kontactinterface-data:all 15.12.1-1ubuntu1
2016-03-11 12:29:09 status unpacked libkf5kontactinterface-data:all 15.12.1-1ubuntu1
2016-03-11 12:29:09 upgrade libkf5ldap5:amd64 15.08.2-0ubuntu1 15.12.1-0ubuntu1
2016-03-11 12:29:09 status half-configured libkf5ldap5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:09 status unpacked libkf5ldap5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:09 status half-installed libkf5ldap5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:09 status half-installed libkf5ldap5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:09 status unpacked libkf5ldap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:09 status unpacked libkf5ldap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:10 upgrade libkf5mbox5:amd64 15.08.2-0ubuntu1 15.12.1-0ubuntu1
2016-03-11 12:29:10 status half-configured libkf5mbox5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:10 status unpacked libkf5mbox5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:10 status half-installed libkf5mbox5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:10 status half-installed libkf5mbox5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:10 status unpacked libkf5mbox5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:10 status unpacked libkf5mbox5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:10 upgrade libkf5solid5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:10 status half-configured libkf5solid5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:10 status unpacked libkf5solid5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:11 status half-installed libkf5solid5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:11 status half-installed libkf5solid5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:11 status unpacked libkf5solid5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:11 status unpacked libkf5solid5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:11 upgrade libkf5solid5-data:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:11 status half-configured libkf5solid5-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:11 status unpacked libkf5solid5-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:11 status half-installed libkf5solid5-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:11 status half-installed libkf5solid5-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:11 status unpacked libkf5solid5-data:all 5.18.0-0ubuntu1
2016-03-11 12:29:11 status unpacked libkf5solid5-data:all 5.18.0-0ubuntu1
2016-03-11 12:29:12 upgrade libkf5syndication5:amd64 15.08.2-0ubuntu1 15.12.1-0ubuntu1
2016-03-11 12:29:12 status half-configured libkf5syndication5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:12 status unpacked libkf5syndication5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:12 status half-installed libkf5syndication5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:12 status half-installed libkf5syndication5:amd64 15.08.2-0ubuntu1
2016-03-11 12:29:12 status unpacked libkf5syndication5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:12 status unpacked libkf5syndication5:amd64 15.12.1-0ubuntu1
2016-03-11 12:29:13 upgrade libkf5threadweaver5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:13 status half-configured libkf5threadweaver5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:13 status unpacked libkf5threadweaver5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:13 status half-installed libkf5threadweaver5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:13 status half-installed libkf5threadweaver5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:13 status unpacked libkf5threadweaver5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:13 status unpacked libkf5threadweaver5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:13 upgrade libkf5webkit5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:13 status half-configured libkf5webkit5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:13 status unpacked libkf5webkit5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:13 status half-installed libkf5webkit5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:13 status half-installed libkf5webkit5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:14 status unpacked libkf5webkit5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:14 status unpacked libkf5webkit5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:14 upgrade libkf5xmlrpcclient5:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:14 status half-configured libkf5xmlrpcclient5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:14 status unpacked libkf5xmlrpcclient5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:14 status half-installed libkf5xmlrpcclient5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:14 status half-installed libkf5xmlrpcclient5:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:14 status unpacked libkf5xmlrpcclient5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:14 status unpacked libkf5xmlrpcclient5:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:15 upgrade libkf5xmlrpcclient-data:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:15 status half-configured libkf5xmlrpcclient-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:15 status unpacked libkf5xmlrpcclient-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:15 status half-installed libkf5xmlrpcclient-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:15 status half-installed libkf5xmlrpcclient-data:all 5.15.0-0ubuntu2
2016-03-11 12:29:15 status unpacked libkf5xmlrpcclient-data:all 5.18.0-0ubuntu1
2016-03-11 12:29:15 status unpacked libkf5xmlrpcclient-data:all 5.18.0-0ubuntu1
2016-03-11 12:29:15 upgrade libkolabxml1v5:amd64 1.1.1-3 1.1.2-0ubuntu2
2016-03-11 12:29:15 status half-configured libkolabxml1v5:amd64 1.1.1-3
2016-03-11 12:29:15 status unpacked libkolabxml1v5:amd64 1.1.1-3
2016-03-11 12:29:16 status half-installed libkolabxml1v5:amd64 1.1.1-3
2016-03-11 12:29:16 status half-installed libkolabxml1v5:amd64 1.1.1-3
2016-03-11 12:29:16 status unpacked libkolabxml1v5:amd64 1.1.2-0ubuntu2
2016-03-11 12:29:16 status unpacked libkolabxml1v5:amd64 1.1.2-0ubuntu2
2016-03-11 12:29:16 upgrade libllvm3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2 1:3.8-2ubuntu1
2016-03-11 12:29:16 status half-configured libllvm3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:16 status unpacked libllvm3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:16 status half-configured libllvm3.8:i386 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:16 status half-installed libllvm3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:18 status half-installed libllvm3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:18 status unpacked libllvm3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:29:18 status unpacked libllvm3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:29:18 upgrade libllvm3.8:i386 1:3.8~+rc2-1~exp1ubuntu2 1:3.8-2ubuntu1
2016-03-11 12:29:18 status half-configured libllvm3.8:i386 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:18 status unpacked libllvm3.8:i386 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:18 status half-installed libllvm3.8:i386 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:20 status half-installed libllvm3.8:i386 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:20 status unpacked libllvm3.8:i386 1:3.8-2ubuntu1
2016-03-11 12:29:20 status unpacked libllvm3.8:i386 1:3.8-2ubuntu1
2016-03-11 12:29:20 upgrade libpurple-bin:all 1:2.10.12-0ubuntu2 1:2.10.12-0ubuntu5
2016-03-11 12:29:20 status half-configured libpurple-bin:all 1:2.10.12-0ubuntu2
2016-03-11 12:29:20 status unpacked libpurple-bin:all 1:2.10.12-0ubuntu2
2016-03-11 12:29:20 status half-installed libpurple-bin:all 1:2.10.12-0ubuntu2
2016-03-11 12:29:20 status half-installed libpurple-bin:all 1:2.10.12-0ubuntu2
2016-03-11 12:29:20 status unpacked libpurple-bin:all 1:2.10.12-0ubuntu5
2016-03-11 12:29:20 status unpacked libpurple-bin:all 1:2.10.12-0ubuntu5
2016-03-11 12:29:21 upgrade libqmobipocket1:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:29:21 status half-configured libqmobipocket1:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:29:21 status unpacked libqmobipocket1:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:29:21 status half-installed libqmobipocket1:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:29:21 status half-installed libqmobipocket1:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:29:21 status unpacked libqmobipocket1:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:29:21 status unpacked libqmobipocket1:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:29:21 upgrade libqt5opengl5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:29:21 status half-configured libqt5opengl5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:29:21 status unpacked libqt5opengl5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:29:21 status half-installed libqt5opengl5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:29:22 status half-installed libqt5opengl5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:29:22 status unpacked libqt5opengl5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:29:22 status unpacked libqt5opengl5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:29:22 upgrade libqt5test5:amd64 5.5.1+dfsg-14ubuntu2 5.5.1+dfsg-15ubuntu1
2016-03-11 12:29:22 status half-configured libqt5test5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:29:22 status unpacked libqt5test5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:29:22 status half-installed libqt5test5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:29:22 status half-installed libqt5test5:amd64 5.5.1+dfsg-14ubuntu2
2016-03-11 12:29:22 status unpacked libqt5test5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:29:23 status unpacked libqt5test5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:29:23 upgrade libvdpau-va-gl1:amd64 0.3.4-3 0.3.6-1
2016-03-11 12:29:23 status half-configured libvdpau-va-gl1:amd64 0.3.4-3
2016-03-11 12:29:23 status unpacked libvdpau-va-gl1:amd64 0.3.4-3
2016-03-11 12:29:23 status half-installed libvdpau-va-gl1:amd64 0.3.4-3
2016-03-11 12:29:23 status half-installed libvdpau-va-gl1:amd64 0.3.4-3
2016-03-11 12:29:23 status unpacked libvdpau-va-gl1:amd64 0.3.6-1
2016-03-11 12:29:23 status unpacked libvdpau-va-gl1:amd64 0.3.6-1
2016-03-11 12:29:23 upgrade yelp:amd64 3.18.1-1ubuntu2 3.18.1-1ubuntu3
2016-03-11 12:29:23 status half-configured yelp:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:23 status unpacked yelp:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:23 status half-installed yelp:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:24 status half-installed yelp:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:24 status half-installed yelp:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:24 status half-installed yelp:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:24 status half-installed yelp:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:24 status unpacked yelp:amd64 3.18.1-1ubuntu3
2016-03-11 12:29:24 status unpacked yelp:amd64 3.18.1-1ubuntu3
2016-03-11 12:29:24 upgrade libyelp0:amd64 3.18.1-1ubuntu2 3.18.1-1ubuntu3
2016-03-11 12:29:25 status half-configured libyelp0:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:25 status unpacked libyelp0:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:26 status half-installed libyelp0:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:26 status half-installed libyelp0:amd64 3.18.1-1ubuntu2
2016-03-11 12:29:26 status unpacked libyelp0:amd64 3.18.1-1ubuntu3
2016-03-11 12:29:26 status unpacked libyelp0:amd64 3.18.1-1ubuntu3
2016-03-11 12:29:26 upgrade linux-crashdump:amd64 4.4.0.8.9 4.4.0.11.12
2016-03-11 12:29:26 status half-configured linux-crashdump:amd64 4.4.0.8.9
2016-03-11 12:29:26 status unpacked linux-crashdump:amd64 4.4.0.8.9
2016-03-11 12:29:26 status half-installed linux-crashdump:amd64 4.4.0.8.9
2016-03-11 12:29:26 status half-installed linux-crashdump:amd64 4.4.0.8.9
2016-03-11 12:29:26 status unpacked linux-crashdump:amd64 4.4.0.11.12
2016-03-11 12:29:26 status unpacked linux-crashdump:amd64 4.4.0.11.12
2016-03-11 12:29:27 upgrade linux-libc-dev:i386 4.4.0-8.23 4.4.0-11.26
2016-03-11 12:29:27 status half-configured linux-libc-dev:i386 4.4.0-8.23
2016-03-11 12:29:27 status unpacked linux-libc-dev:i386 4.4.0-8.23
2016-03-11 12:29:27 status half-configured linux-libc-dev:amd64 4.4.0-8.23
2016-03-11 12:29:27 status half-installed linux-libc-dev:i386 4.4.0-8.23
2016-03-11 12:29:28 status half-installed linux-libc-dev:i386 4.4.0-8.23
2016-03-11 12:29:28 status unpacked linux-libc-dev:i386 4.4.0-11.26
2016-03-11 12:29:28 status unpacked linux-libc-dev:i386 4.4.0-11.26
2016-03-11 12:29:28 upgrade linux-libc-dev:amd64 4.4.0-8.23 4.4.0-11.26
2016-03-11 12:29:28 status half-configured linux-libc-dev:amd64 4.4.0-8.23
2016-03-11 12:29:28 status unpacked linux-libc-dev:amd64 4.4.0-8.23
2016-03-11 12:29:28 status half-installed linux-libc-dev:amd64 4.4.0-8.23
2016-03-11 12:29:28 status half-installed linux-libc-dev:amd64 4.4.0-8.23
2016-03-11 12:29:28 status unpacked linux-libc-dev:amd64 4.4.0-11.26
2016-03-11 12:29:28 status unpacked linux-libc-dev:amd64 4.4.0-11.26
2016-03-11 12:29:29 upgrade llvm-3.8-dev:amd64 1:3.8~+rc2-1~exp1ubuntu2 1:3.8-2ubuntu1
2016-03-11 12:29:29 status half-configured llvm-3.8-dev:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:29 status unpacked llvm-3.8-dev:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:29 status half-installed llvm-3.8-dev:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:32 status half-installed llvm-3.8-dev:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:32 status unpacked llvm-3.8-dev:amd64 1:3.8-2ubuntu1
2016-03-11 12:29:32 status unpacked llvm-3.8-dev:amd64 1:3.8-2ubuntu1
2016-03-11 12:29:32 upgrade llvm-3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2 1:3.8-2ubuntu1
2016-03-11 12:29:32 status half-configured llvm-3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:32 status unpacked llvm-3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:32 status half-installed llvm-3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:33 status half-installed llvm-3.8:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:33 status unpacked llvm-3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:29:33 status unpacked llvm-3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:29:33 upgrade llvm-3.8-runtime:amd64 1:3.8~+rc2-1~exp1ubuntu2 1:3.8-2ubuntu1
2016-03-11 12:29:33 status half-configured llvm-3.8-runtime:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:33 status unpacked llvm-3.8-runtime:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:33 status half-installed llvm-3.8-runtime:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:33 status half-installed llvm-3.8-runtime:amd64 1:3.8~+rc2-1~exp1ubuntu2
2016-03-11 12:29:34 status unpacked llvm-3.8-runtime:amd64 1:3.8-2ubuntu1
2016-03-11 12:29:34 status unpacked llvm-3.8-runtime:amd64 1:3.8-2ubuntu1
2016-03-11 12:29:34 upgrade mythes-en-us:all 1:4.2.1-0ubuntu3 1:5.1.0-1ubuntu1
2016-03-11 12:29:34 status half-configured mythes-en-us:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:34 status unpacked mythes-en-us:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:34 status half-installed mythes-en-us:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:34 status half-installed mythes-en-us:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:35 status half-installed mythes-en-us:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:35 status unpacked mythes-en-us:all 1:5.1.0-1ubuntu1
2016-03-11 12:29:35 status unpacked mythes-en-us:all 1:5.1.0-1ubuntu1
2016-03-11 12:29:35 upgrade mythes-fr:all 1:4.2.1-0ubuntu3 1:5.1.0-1ubuntu1
2016-03-11 12:29:35 status half-configured mythes-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:35 status unpacked mythes-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:35 status half-installed mythes-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:35 status half-installed mythes-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:35 status half-installed mythes-fr:all 1:4.2.1-0ubuntu3
2016-03-11 12:29:35 status unpacked mythes-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:29:36 status unpacked mythes-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:29:36 upgrade openoffice.org-hyphenation:all 0.8 0.9
2016-03-11 12:29:36 status half-configured openoffice.org-hyphenation:all 0.8
2016-03-11 12:29:36 status unpacked openoffice.org-hyphenation:all 0.8
2016-03-11 12:29:36 status half-installed openoffice.org-hyphenation:all 0.8
2016-03-11 12:29:36 status half-installed openoffice.org-hyphenation:all 0.8
2016-03-11 12:29:36 status half-installed openoffice.org-hyphenation:all 0.8
2016-03-11 12:29:36 status unpacked openoffice.org-hyphenation:all 0.9
2016-03-11 12:29:36 status unpacked openoffice.org-hyphenation:all 0.9
2016-03-11 12:29:36 upgrade python-futurist:all 0.9.0-1 0.13.0-0ubuntu1
2016-03-11 12:29:36 status half-configured python-futurist:all 0.9.0-1
2016-03-11 12:29:37 status unpacked python-futurist:all 0.9.0-1
2016-03-11 12:29:37 status half-installed python-futurist:all 0.9.0-1
2016-03-11 12:29:37 status half-installed python-futurist:all 0.9.0-1
2016-03-11 12:29:37 status unpacked python-futurist:all 0.13.0-0ubuntu1
2016-03-11 12:29:37 status unpacked python-futurist:all 0.13.0-0ubuntu1
2016-03-11 12:29:37 upgrade python-kombu:all 3.0.33-1ubuntu1 3.0.33-1ubuntu2
2016-03-11 12:29:37 status half-configured python-kombu:all 3.0.33-1ubuntu1
2016-03-11 12:29:37 status unpacked python-kombu:all 3.0.33-1ubuntu1
2016-03-11 12:29:37 status half-installed python-kombu:all 3.0.33-1ubuntu1
2016-03-11 12:29:38 status half-installed python-kombu:all 3.0.33-1ubuntu1
2016-03-11 12:29:38 status unpacked python-kombu:all 3.0.33-1ubuntu2
2016-03-11 12:29:38 status unpacked python-kombu:all 3.0.33-1ubuntu2
2016-03-11 12:29:38 upgrade python-oslo.config:all 1:3.8.0-0ubuntu1 1:3.9.0-1
2016-03-11 12:29:38 status half-configured python-oslo.config:all 1:3.8.0-0ubuntu1
2016-03-11 12:29:38 status unpacked python-oslo.config:all 1:3.8.0-0ubuntu1
2016-03-11 12:29:38 status half-installed python-oslo.config:all 1:3.8.0-0ubuntu1
2016-03-11 12:29:39 status half-installed python-oslo.config:all 1:3.8.0-0ubuntu1
2016-03-11 12:29:39 status unpacked python-oslo.config:all 1:3.9.0-1
2016-03-11 12:29:39 status unpacked python-oslo.config:all 1:3.9.0-1
2016-03-11 12:29:39 upgrade python-oslo.i18n:all 3.3.0-0ubuntu1 3.4.0-1
2016-03-11 12:29:39 status half-configured python-oslo.i18n:all 3.3.0-0ubuntu1
2016-03-11 12:29:39 status unpacked python-oslo.i18n:all 3.3.0-0ubuntu1
2016-03-11 12:29:39 status half-installed python-oslo.i18n:all 3.3.0-0ubuntu1
2016-03-11 12:29:39 status half-installed python-oslo.i18n:all 3.3.0-0ubuntu1
2016-03-11 12:29:39 status unpacked python-oslo.i18n:all 3.4.0-1
2016-03-11 12:29:39 status unpacked python-oslo.i18n:all 3.4.0-1
2016-03-11 12:29:40 upgrade python-oslo.utils:all 3.4.0-1ubuntu1 3.7.0-0ubuntu1
2016-03-11 12:29:40 status half-configured python-oslo.utils:all 3.4.0-1ubuntu1
2016-03-11 12:29:40 status unpacked python-oslo.utils:all 3.4.0-1ubuntu1
2016-03-11 12:29:40 status half-installed python-oslo.utils:all 3.4.0-1ubuntu1
2016-03-11 12:29:40 status half-installed python-oslo.utils:all 3.4.0-1ubuntu1
2016-03-11 12:29:40 status unpacked python-oslo.utils:all 3.7.0-0ubuntu1
2016-03-11 12:29:40 status unpacked python-oslo.utils:all 3.7.0-0ubuntu1
2016-03-11 12:29:40 upgrade python-oslo.concurrency:all 3.0.0-1ubuntu1 3.6.0-0ubuntu1
2016-03-11 12:29:40 status half-configured python-oslo.concurrency:all 3.0.0-1ubuntu1
2016-03-11 12:29:41 status unpacked python-oslo.concurrency:all 3.0.0-1ubuntu1
2016-03-11 12:29:41 status half-installed python-oslo.concurrency:all 3.0.0-1ubuntu1
2016-03-11 12:29:41 status half-installed python-oslo.concurrency:all 3.0.0-1ubuntu1
2016-03-11 12:29:41 status unpacked python-oslo.concurrency:all 3.6.0-0ubuntu1
2016-03-11 12:29:41 status unpacked python-oslo.concurrency:all 3.6.0-0ubuntu1
2016-03-11 12:29:41 upgrade python-oslo.context:all 2.1.0-0ubuntu1 2.2.0-1
2016-03-11 12:29:41 status half-configured python-oslo.context:all 2.1.0-0ubuntu1
2016-03-11 12:29:41 status unpacked python-oslo.context:all 2.1.0-0ubuntu1
2016-03-11 12:29:41 status half-installed python-oslo.context:all 2.1.0-0ubuntu1
2016-03-11 12:29:42 status half-installed python-oslo.context:all 2.1.0-0ubuntu1
2016-03-11 12:29:42 status unpacked python-oslo.context:all 2.2.0-1
2016-03-11 12:29:42 status unpacked python-oslo.context:all 2.2.0-1
2016-03-11 12:29:42 upgrade python-oslo.db:all 4.3.0-1ubuntu1 4.6.0-1ubuntu1
2016-03-11 12:29:42 status half-configured python-oslo.db:all 4.3.0-1ubuntu1
2016-03-11 12:29:42 status unpacked python-oslo.db:all 4.3.0-1ubuntu1
2016-03-11 12:29:42 status half-installed python-oslo.db:all 4.3.0-1ubuntu1
2016-03-11 12:29:42 status half-installed python-oslo.db:all 4.3.0-1ubuntu1
2016-03-11 12:29:42 status unpacked python-oslo.db:all 4.6.0-1ubuntu1
2016-03-11 12:29:42 status unpacked python-oslo.db:all 4.6.0-1ubuntu1
2016-03-11 12:29:43 upgrade python-oslo.serialization:all 2.3.0-0ubuntu1 2.4.0-1
2016-03-11 12:29:43 status half-configured python-oslo.serialization:all 2.3.0-0ubuntu1
2016-03-11 12:29:43 status unpacked python-oslo.serialization:all 2.3.0-0ubuntu1
2016-03-11 12:29:43 status half-installed python-oslo.serialization:all 2.3.0-0ubuntu1
2016-03-11 12:29:43 status half-installed python-oslo.serialization:all 2.3.0-0ubuntu1
2016-03-11 12:29:43 status unpacked python-oslo.serialization:all 2.4.0-1
2016-03-11 12:29:43 status unpacked python-oslo.serialization:all 2.4.0-1
2016-03-11 12:29:44 upgrade python-oslo.log:all 3.1.0-0ubuntu1 3.2.0-1
2016-03-11 12:29:44 status half-configured python-oslo.log:all 3.1.0-0ubuntu1
2016-03-11 12:29:44 status unpacked python-oslo.log:all 3.1.0-0ubuntu1
2016-03-11 12:29:44 status half-installed python-oslo.log:all 3.1.0-0ubuntu1
2016-03-11 12:29:44 status half-installed python-oslo.log:all 3.1.0-0ubuntu1
2016-03-11 12:29:44 status unpacked python-oslo.log:all 3.2.0-1
2016-03-11 12:29:44 status unpacked python-oslo.log:all 3.2.0-1
2016-03-11 12:29:44 upgrade python-oslo.middleware:all 3.6.0-0ubuntu1 3.7.0-1
2016-03-11 12:29:44 status half-configured python-oslo.middleware:all 3.6.0-0ubuntu1
2016-03-11 12:29:44 status unpacked python-oslo.middleware:all 3.6.0-0ubuntu1
2016-03-11 12:29:44 status half-installed python-oslo.middleware:all 3.6.0-0ubuntu1
2016-03-11 12:29:45 status half-installed python-oslo.middleware:all 3.6.0-0ubuntu1
2016-03-11 12:29:45 status unpacked python-oslo.middleware:all 3.7.0-1
2016-03-11 12:29:45 status unpacked python-oslo.middleware:all 3.7.0-1
2016-03-11 12:29:45 upgrade python-oslo.policy:all 1.0.0-0ubuntu1 1.5.0-0ubuntu1
2016-03-11 12:29:45 status half-configured python-oslo.policy:all 1.0.0-0ubuntu1
2016-03-11 12:29:45 status unpacked python-oslo.policy:all 1.0.0-0ubuntu1
2016-03-11 12:29:45 status half-installed python-oslo.policy:all 1.0.0-0ubuntu1
2016-03-11 12:29:45 status half-installed python-oslo.policy:all 1.0.0-0ubuntu1
2016-03-11 12:29:46 status unpacked python-oslo.policy:all 1.5.0-0ubuntu1
2016-03-11 12:29:46 status unpacked python-oslo.policy:all 1.5.0-0ubuntu1
2016-03-11 12:29:46 upgrade python-oslo.reports:all 1.0.0-1ubuntu1 1.6.0-1
2016-03-11 12:29:46 status half-configured python-oslo.reports:all 1.0.0-1ubuntu1
2016-03-11 12:29:46 status unpacked python-oslo.reports:all 1.0.0-1ubuntu1
2016-03-11 12:29:46 status half-installed python-oslo.reports:all 1.0.0-1ubuntu1
2016-03-11 12:29:46 status half-installed python-oslo.reports:all 1.0.0-1ubuntu1
2016-03-11 12:29:46 status unpacked python-oslo.reports:all 1.6.0-1
2016-03-11 12:29:46 status unpacked python-oslo.reports:all 1.6.0-1
2016-03-11 12:29:47 upgrade python-oslo.rootwrap:all 4.0.0-0ubuntu1 4.1.0-1
2016-03-11 12:29:47 status half-configured python-oslo.rootwrap:all 4.0.0-0ubuntu1
2016-03-11 12:29:47 status unpacked python-oslo.rootwrap:all 4.0.0-0ubuntu1
2016-03-11 12:29:47 status half-installed python-oslo.rootwrap:all 4.0.0-0ubuntu1
2016-03-11 12:29:47 status half-installed python-oslo.rootwrap:all 4.0.0-0ubuntu1
2016-03-11 12:29:47 status unpacked python-oslo.rootwrap:all 4.1.0-1
2016-03-11 12:29:47 status unpacked python-oslo.rootwrap:all 4.1.0-1
2016-03-11 12:29:48 upgrade python-oslo.service:all 1.0.0-1ubuntu2 1.3.0-1ubuntu1
2016-03-11 12:29:48 status half-configured python-oslo.service:all 1.0.0-1ubuntu2
2016-03-11 12:29:48 status unpacked python-oslo.service:all 1.0.0-1ubuntu2
2016-03-11 12:29:48 status half-installed python-oslo.service:all 1.0.0-1ubuntu2
2016-03-11 12:29:48 status half-installed python-oslo.service:all 1.0.0-1ubuntu2
2016-03-11 12:29:48 status unpacked python-oslo.service:all 1.3.0-1ubuntu1
2016-03-11 12:29:48 status unpacked python-oslo.service:all 1.3.0-1ubuntu1
2016-03-11 12:29:48 upgrade python-unittest2:all 1.1.0-5ubuntu1 1.1.0-6.1
2016-03-11 12:29:48 status half-configured python-unittest2:all 1.1.0-5ubuntu1
2016-03-11 12:29:49 status unpacked python-unittest2:all 1.1.0-5ubuntu1
2016-03-11 12:29:49 status half-installed python-unittest2:all 1.1.0-5ubuntu1
2016-03-11 12:29:49 status half-installed python-unittest2:all 1.1.0-5ubuntu1
2016-03-11 12:29:49 status unpacked python-unittest2:all 1.1.0-6.1
2016-03-11 12:29:49 status unpacked python-unittest2:all 1.1.0-6.1
2016-03-11 12:29:49 upgrade python-waitress:all 0.8.9-2ubuntu1 0.8.10-1
2016-03-11 12:29:49 status half-configured python-waitress:all 0.8.9-2ubuntu1
2016-03-11 12:29:49 status unpacked python-waitress:all 0.8.9-2ubuntu1
2016-03-11 12:29:49 status half-installed python-waitress:all 0.8.9-2ubuntu1
2016-03-11 12:29:49 status half-installed python-waitress:all 0.8.9-2ubuntu1
2016-03-11 12:29:50 status unpacked python-waitress:all 0.8.10-1
2016-03-11 12:29:50 status unpacked python-waitress:all 0.8.10-1
2016-03-11 12:29:50 upgrade python3-cupshelpers:all 1.5.7+20160212-0ubuntu1 1.5.7+20160212-0ubuntu2
2016-03-11 12:29:50 status half-configured python3-cupshelpers:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:29:50 status unpacked python3-cupshelpers:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:29:50 status half-installed python3-cupshelpers:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:29:50 status half-installed python3-cupshelpers:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:29:50 status unpacked python3-cupshelpers:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:29:50 status unpacked python3-cupshelpers:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:29:51 upgrade python3-pycurl:amd64 7.21.5-1ubuntu2build0pie.3 7.43.0-1ubuntu1
2016-03-11 12:29:51 status half-configured python3-pycurl:amd64 7.21.5-1ubuntu2build0pie.3
2016-03-11 12:29:51 status unpacked python3-pycurl:amd64 7.21.5-1ubuntu2build0pie.3
2016-03-11 12:29:51 status half-installed python3-pycurl:amd64 7.21.5-1ubuntu2build0pie.3
2016-03-11 12:29:51 status half-installed python3-pycurl:amd64 7.21.5-1ubuntu2build0pie.3
2016-03-11 12:29:51 status unpacked python3-pycurl:amd64 7.43.0-1ubuntu1
2016-03-11 12:29:51 status unpacked python3-pycurl:amd64 7.43.0-1ubuntu1
2016-03-11 12:29:51 upgrade software-properties-common:all 0.96.17 0.96.18
2016-03-11 12:29:51 status half-configured software-properties-common:all 0.96.17
2016-03-11 12:29:52 status unpacked software-properties-common:all 0.96.17
2016-03-11 12:29:52 status half-installed software-properties-common:all 0.96.17
2016-03-11 12:29:52 status half-installed software-properties-common:all 0.96.17
2016-03-11 12:29:52 status unpacked software-properties-common:all 0.96.18
2016-03-11 12:29:52 status unpacked software-properties-common:all 0.96.18
2016-03-11 12:29:52 upgrade software-properties-gtk:all 0.96.17 0.96.18
2016-03-11 12:29:52 status half-configured software-properties-gtk:all 0.96.17
2016-03-11 12:29:53 status unpacked software-properties-gtk:all 0.96.17
2016-03-11 12:29:53 status half-installed software-properties-gtk:all 0.96.17
2016-03-11 12:29:53 status half-installed software-properties-gtk:all 0.96.17
2016-03-11 12:29:53 status half-installed software-properties-gtk:all 0.96.17
2016-03-11 12:29:53 status half-installed software-properties-gtk:all 0.96.17
2016-03-11 12:29:53 status half-installed software-properties-gtk:all 0.96.17
2016-03-11 12:29:53 status unpacked software-properties-gtk:all 0.96.18
2016-03-11 12:29:53 status unpacked software-properties-gtk:all 0.96.18
2016-03-11 12:29:53 upgrade python3-software-properties:all 0.96.17 0.96.18
2016-03-11 12:29:53 status half-configured python3-software-properties:all 0.96.17
2016-03-11 12:29:53 status unpacked python3-software-properties:all 0.96.17
2016-03-11 12:29:54 status half-installed python3-software-properties:all 0.96.17
2016-03-11 12:29:54 status half-installed python3-software-properties:all 0.96.17
2016-03-11 12:29:54 status unpacked python3-software-properties:all 0.96.18
2016-03-11 12:29:54 status unpacked python3-software-properties:all 0.96.18
2016-03-11 12:29:54 upgrade qml-module-org-kde-extensionplugin:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:54 status half-configured qml-module-org-kde-extensionplugin:all 5.15.0-0ubuntu2
2016-03-11 12:29:54 status unpacked qml-module-org-kde-extensionplugin:all 5.15.0-0ubuntu2
2016-03-11 12:29:54 status half-installed qml-module-org-kde-extensionplugin:all 5.15.0-0ubuntu2
2016-03-11 12:29:54 status half-installed qml-module-org-kde-extensionplugin:all 5.15.0-0ubuntu2
2016-03-11 12:29:54 status unpacked qml-module-org-kde-extensionplugin:all 5.18.0-0ubuntu1
2016-03-11 12:29:54 status unpacked qml-module-org-kde-extensionplugin:all 5.18.0-0ubuntu1
2016-03-11 12:29:55 upgrade qml-module-org-kde-solid:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:55 status half-configured qml-module-org-kde-solid:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:55 status unpacked qml-module-org-kde-solid:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:55 status half-installed qml-module-org-kde-solid:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:55 status half-installed qml-module-org-kde-solid:amd64 5.15.0-0ubuntu2
2016-03-11 12:29:55 status unpacked qml-module-org-kde-solid:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:55 status unpacked qml-module-org-kde-solid:amd64 5.18.0-0ubuntu1
2016-03-11 12:29:55 upgrade qtdeclarative5-kf5solid:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:29:55 status half-configured qtdeclarative5-kf5solid:all 5.15.0-0ubuntu2
2016-03-11 12:29:55 status unpacked qtdeclarative5-kf5solid:all 5.15.0-0ubuntu2
2016-03-11 12:29:55 status half-installed qtdeclarative5-kf5solid:all 5.15.0-0ubuntu2
2016-03-11 12:29:55 status half-installed qtdeclarative5-kf5solid:all 5.15.0-0ubuntu2
2016-03-11 12:29:55 status unpacked qtdeclarative5-kf5solid:all 5.18.0-0ubuntu1
2016-03-11 12:29:56 status unpacked qtdeclarative5-kf5solid:all 5.18.0-0ubuntu1
2016-03-11 12:29:56 upgrade liboxideqt-qmlplugin:amd64 1.12.7-0ubuntu1 1.13.6-0ubuntu1
2016-03-11 12:29:56 status half-configured liboxideqt-qmlplugin:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:56 status unpacked liboxideqt-qmlplugin:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:56 status half-installed liboxideqt-qmlplugin:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:56 status half-installed liboxideqt-qmlplugin:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:56 status unpacked liboxideqt-qmlplugin:amd64 1.13.6-0ubuntu1
2016-03-11 12:29:56 status unpacked liboxideqt-qmlplugin:amd64 1.13.6-0ubuntu1
2016-03-11 12:29:56 upgrade liboxideqtquick0:amd64 1.12.7-0ubuntu1 1.13.6-0ubuntu1
2016-03-11 12:29:56 status half-configured liboxideqtquick0:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:56 status unpacked liboxideqtquick0:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:57 status half-installed liboxideqtquick0:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:57 status half-installed liboxideqtquick0:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:57 status unpacked liboxideqtquick0:amd64 1.13.6-0ubuntu1
2016-03-11 12:29:57 status unpacked liboxideqtquick0:amd64 1.13.6-0ubuntu1
2016-03-11 12:29:57 upgrade liboxideqtcore0:amd64 1.12.7-0ubuntu1 1.13.6-0ubuntu1
2016-03-11 12:29:57 status half-configured liboxideqtcore0:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:57 status unpacked liboxideqtcore0:amd64 1.12.7-0ubuntu1
2016-03-11 12:29:57 status half-installed liboxideqtcore0:amd64 1.12.7-0ubuntu1
2016-03-11 12:30:02 status half-installed liboxideqtcore0:amd64 1.12.7-0ubuntu1
2016-03-11 12:30:03 status unpacked liboxideqtcore0:amd64 1.13.6-0ubuntu1
2016-03-11 12:30:03 status unpacked liboxideqtcore0:amd64 1.13.6-0ubuntu1
2016-03-11 12:30:03 upgrade oxideqt-codecs-extra:amd64 1.12.7-0ubuntu1 1.13.6-0ubuntu1
2016-03-11 12:30:03 status half-configured oxideqt-codecs-extra:amd64 1.12.7-0ubuntu1
2016-03-11 12:30:03 status unpacked oxideqt-codecs-extra:amd64 1.12.7-0ubuntu1
2016-03-11 12:30:03 status half-installed oxideqt-codecs-extra:amd64 1.12.7-0ubuntu1
2016-03-11 12:30:03 status half-installed oxideqt-codecs-extra:amd64 1.12.7-0ubuntu1
2016-03-11 12:30:04 status unpacked oxideqt-codecs-extra:amd64 1.13.6-0ubuntu1
2016-03-11 12:30:04 status unpacked oxideqt-codecs-extra:amd64 1.13.6-0ubuntu1
2016-03-11 12:30:04 upgrade webapp-container:amd64 0.23+16.04.20160223-0ubuntu1 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:04 status half-configured webapp-container:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:04 status unpacked webapp-container:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:04 status half-installed webapp-container:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:04 status half-installed webapp-container:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:04 status unpacked webapp-container:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:04 status unpacked webapp-container:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:05 upgrade webbrowser-app:amd64 0.23+16.04.20160223-0ubuntu1 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:05 status half-configured webbrowser-app:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:05 status unpacked webbrowser-app:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:05 status half-installed webbrowser-app:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:05 status half-installed webbrowser-app:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:05 status half-installed webbrowser-app:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:05 status unpacked webbrowser-app:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:05 status unpacked webbrowser-app:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:06 upgrade qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160223-0ubuntu1 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:06 status half-configured qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:06 status unpacked qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:06 status half-installed qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:06 status half-installed qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160223-0ubuntu1
2016-03-11 12:30:06 status unpacked qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:06 status unpacked qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:30:06 upgrade simple-scan:amd64 3.19.4-0ubuntu1 3.19.91-0ubuntu1
2016-03-11 12:30:06 status half-configured simple-scan:amd64 3.19.4-0ubuntu1
2016-03-11 12:30:06 status unpacked simple-scan:amd64 3.19.4-0ubuntu1
2016-03-11 12:30:06 status half-installed simple-scan:amd64 3.19.4-0ubuntu1
2016-03-11 12:30:06 status half-installed simple-scan:amd64 3.19.4-0ubuntu1
2016-03-11 12:30:07 status half-installed simple-scan:amd64 3.19.4-0ubuntu1
2016-03-11 12:30:07 status half-installed simple-scan:amd64 3.19.4-0ubuntu1
2016-03-11 12:30:07 status half-installed simple-scan:amd64 3.19.4-0ubuntu1
2016-03-11 12:30:07 status unpacked simple-scan:amd64 3.19.91-0ubuntu1
2016-03-11 12:30:07 status unpacked simple-scan:amd64 3.19.91-0ubuntu1
2016-03-11 12:30:08 upgrade ssh-askpass-gnome:amd64 1:7.1p2-2build0pie.3 1:7.2p1-1
2016-03-11 12:30:08 status half-configured ssh-askpass-gnome:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:30:08 status unpacked ssh-askpass-gnome:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:30:08 status half-installed ssh-askpass-gnome:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:30:08 status half-installed ssh-askpass-gnome:amd64 1:7.1p2-2build0pie.3
2016-03-11 12:30:08 status unpacked ssh-askpass-gnome:amd64 1:7.2p1-1
2016-03-11 12:30:08 status unpacked ssh-askpass-gnome:amd64 1:7.2p1-1
2016-03-11 12:30:09 upgrade system-config-printer-gnome:all 1.5.7+20160212-0ubuntu1 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:09 status half-configured system-config-printer-gnome:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:09 status unpacked system-config-printer-gnome:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:09 status half-installed system-config-printer-gnome:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:09 status half-installed system-config-printer-gnome:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:09 status half-installed system-config-printer-gnome:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:09 status unpacked system-config-printer-gnome:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:09 status unpacked system-config-printer-gnome:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:10 upgrade system-config-printer-common:all 1.5.7+20160212-0ubuntu1 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:10 status half-configured system-config-printer-common:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:10 status unpacked system-config-printer-common:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:10 status half-installed system-config-printer-common:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:10 status half-installed system-config-printer-common:all 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:10 status unpacked system-config-printer-common:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:10 status unpacked system-config-printer-common:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:10 upgrade system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu1 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:10 status half-configured system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:10 status unpacked system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:11 status half-installed system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:11 status half-installed system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu1
2016-03-11 12:30:11 status unpacked system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:11 status unpacked system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu2
2016-03-11 12:30:11 upgrade thunderbird-locale-fr:amd64 1:38.5.1+build2-0ubuntu1 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:11 status half-configured thunderbird-locale-fr:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:11 status unpacked thunderbird-locale-fr:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:11 status half-installed thunderbird-locale-fr:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:11 status half-installed thunderbird-locale-fr:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:12 status unpacked thunderbird-locale-fr:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:12 status unpacked thunderbird-locale-fr:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:12 upgrade thunderbird-locale-en:amd64 1:38.5.1+build2-0ubuntu1 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:12 status half-configured thunderbird-locale-en:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:12 status unpacked thunderbird-locale-en:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:12 status half-installed thunderbird-locale-en:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:12 status half-installed thunderbird-locale-en:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:12 status unpacked thunderbird-locale-en:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:12 status unpacked thunderbird-locale-en:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:13 upgrade thunderbird:amd64 1:38.5.1+build2-0ubuntu1 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:13 status half-configured thunderbird:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:13 status unpacked thunderbird:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:13 status half-installed thunderbird:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:16 status half-installed thunderbird:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:16 status half-installed thunderbird:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:16 status unpacked thunderbird:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:16 status unpacked thunderbird:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:16 upgrade thunderbird-gnome-support:amd64 1:38.5.1+build2-0ubuntu1 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:16 status half-configured thunderbird-gnome-support:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:16 status unpacked thunderbird-gnome-support:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:16 status half-installed thunderbird-gnome-support:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:17 status half-installed thunderbird-gnome-support:amd64 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:17 status unpacked thunderbird-gnome-support:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:17 status unpacked thunderbird-gnome-support:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:17 upgrade thunderbird-locale-en-gb:all 1:38.5.1+build2-0ubuntu1 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:17 status half-configured thunderbird-locale-en-gb:all 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:17 status unpacked thunderbird-locale-en-gb:all 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:17 status half-installed thunderbird-locale-en-gb:all 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:17 status half-installed thunderbird-locale-en-gb:all 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:17 status unpacked thunderbird-locale-en-gb:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:17 status unpacked thunderbird-locale-en-gb:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:18 upgrade thunderbird-locale-en-us:all 1:38.5.1+build2-0ubuntu1 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:18 status half-configured thunderbird-locale-en-us:all 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:18 status unpacked thunderbird-locale-en-us:all 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:18 status half-installed thunderbird-locale-en-us:all 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:18 status half-installed thunderbird-locale-en-us:all 1:38.5.1+build2-0ubuntu1
2016-03-11 12:30:18 status unpacked thunderbird-locale-en-us:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:18 status unpacked thunderbird-locale-en-us:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:30:18 upgrade ttf-ubuntu-font-family:all 0.84~mono0.83+arabicfontconfig-0ubuntu1 1:0.83-0ubuntu2
2016-03-11 12:30:18 status half-configured ttf-ubuntu-font-family:all 0.84~mono0.83+arabicfontconfig-0ubuntu1
2016-03-11 12:30:18 status unpacked ttf-ubuntu-font-family:all 0.84~mono0.83+arabicfontconfig-0ubuntu1
2016-03-11 12:30:18 status half-installed ttf-ubuntu-font-family:all 0.84~mono0.83+arabicfontconfig-0ubuntu1
2016-03-11 12:30:19 status half-installed ttf-ubuntu-font-family:all 0.84~mono0.83+arabicfontconfig-0ubuntu1
2016-03-11 12:30:19 status unpacked ttf-ubuntu-font-family:all 1:0.83-0ubuntu2
2016-03-11 12:30:19 status unpacked ttf-ubuntu-font-family:all 1:0.83-0ubuntu2
2016-03-11 12:30:19 upgrade ubuntu-gnome-wallpapers-utopic:all 14.10.1 16.04.1
2016-03-11 12:30:19 status half-configured ubuntu-gnome-wallpapers-utopic:all 14.10.1
2016-03-11 12:30:19 status unpacked ubuntu-gnome-wallpapers-utopic:all 14.10.1
2016-03-11 12:30:19 status half-installed ubuntu-gnome-wallpapers-utopic:all 14.10.1
2016-03-11 12:30:20 status half-installed ubuntu-gnome-wallpapers-utopic:all 14.10.1
2016-03-11 12:30:20 status unpacked ubuntu-gnome-wallpapers-utopic:all 16.04.1
2016-03-11 12:30:20 status unpacked ubuntu-gnome-wallpapers-utopic:all 16.04.1
2016-03-11 12:30:20 upgrade ubuntu-restricted-extras:amd64 64 65
2016-03-11 12:30:20 status half-configured ubuntu-restricted-extras:amd64 64
2016-03-11 12:30:20 status unpacked ubuntu-restricted-extras:amd64 64
2016-03-11 12:30:20 status half-installed ubuntu-restricted-extras:amd64 64
2016-03-11 12:30:21 status half-installed ubuntu-restricted-extras:amd64 64
2016-03-11 12:30:21 status unpacked ubuntu-restricted-extras:amd64 65
2016-03-11 12:30:21 status unpacked ubuntu-restricted-extras:amd64 65
2016-03-11 12:30:21 upgrade ubuntu-wallpapers-wily:all 15.10.3-0ubuntu1 16.04.0-0ubuntu1
2016-03-11 12:30:21 status half-configured ubuntu-wallpapers-wily:all 15.10.3-0ubuntu1
2016-03-11 12:30:21 status unpacked ubuntu-wallpapers-wily:all 15.10.3-0ubuntu1
2016-03-11 12:30:21 status half-installed ubuntu-wallpapers-wily:all 15.10.3-0ubuntu1
2016-03-11 12:30:21 status half-installed ubuntu-wallpapers-wily:all 15.10.3-0ubuntu1
2016-03-11 12:30:22 status unpacked ubuntu-wallpapers-wily:all 16.04.0-0ubuntu1
2016-03-11 12:30:22 status unpacked ubuntu-wallpapers-wily:all 16.04.0-0ubuntu1
2016-03-11 12:30:22 upgrade ubuntu-wallpapers:all 15.10.3-0ubuntu1 16.04.0-0ubuntu1
2016-03-11 12:30:22 status half-configured ubuntu-wallpapers:all 15.10.3-0ubuntu1
2016-03-11 12:30:22 status unpacked ubuntu-wallpapers:all 15.10.3-0ubuntu1
2016-03-11 12:30:22 status half-installed ubuntu-wallpapers:all 15.10.3-0ubuntu1
2016-03-11 12:30:22 status half-installed ubuntu-wallpapers:all 15.10.3-0ubuntu1
2016-03-11 12:30:22 status unpacked ubuntu-wallpapers:all 16.04.0-0ubuntu1
2016-03-11 12:30:23 status unpacked ubuntu-wallpapers:all 16.04.0-0ubuntu1
2016-03-11 12:30:23 upgrade udisks2:amd64 2.1.6-2+git1build~pie.1 2.1.7-1
2016-03-11 12:30:23 status half-configured udisks2:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:30:23 status unpacked udisks2:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:30:23 status half-installed udisks2:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:30:23 status half-installed udisks2:amd64 2.1.6-2+git1build~pie.1
2016-03-11 12:30:23 status unpacked udisks2:amd64 2.1.7-1
2016-03-11 12:30:23 status unpacked udisks2:amd64 2.1.7-1
2016-03-11 12:30:24 upgrade virtualbox-qt:amd64 5.0.14-dfsg-2build1 5.0.16-dfsg-2
2016-03-11 12:30:24 status half-configured virtualbox-qt:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:24 status unpacked virtualbox-qt:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:24 status half-installed virtualbox-qt:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:24 status half-installed virtualbox-qt:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:24 status half-installed virtualbox-qt:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:24 status half-installed virtualbox-qt:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:24 status half-installed virtualbox-qt:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:25 status half-installed virtualbox-qt:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:25 status unpacked virtualbox-qt:amd64 5.0.16-dfsg-2
2016-03-11 12:30:25 status unpacked virtualbox-qt:amd64 5.0.16-dfsg-2
2016-03-11 12:30:25 upgrade virtualbox-dbg:amd64 5.0.14-dfsg-2build1 5.0.16-dfsg-2
2016-03-11 12:30:25 status half-configured virtualbox-dbg:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:25 status unpacked virtualbox-dbg:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:25 status half-installed virtualbox-dbg:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:35 status half-installed virtualbox-dbg:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:36 status unpacked virtualbox-dbg:amd64 5.0.16-dfsg-2
2016-03-11 12:30:36 status unpacked virtualbox-dbg:amd64 5.0.16-dfsg-2
2016-03-11 12:30:36 upgrade virtualbox-dkms:all 5.0.14-dfsg-2build1 5.0.16-dfsg-2
2016-03-11 12:30:36 status half-configured virtualbox-dkms:all 5.0.14-dfsg-2build1
2016-03-11 12:30:37 status unpacked virtualbox-dkms:all 5.0.14-dfsg-2build1
2016-03-11 12:30:37 status half-installed virtualbox-dkms:all 5.0.14-dfsg-2build1
2016-03-11 12:30:37 status half-installed virtualbox-dkms:all 5.0.14-dfsg-2build1
2016-03-11 12:30:38 status unpacked virtualbox-dkms:all 5.0.16-dfsg-2
2016-03-11 12:30:38 status unpacked virtualbox-dkms:all 5.0.16-dfsg-2
2016-03-11 12:30:38 upgrade virtualbox:amd64 5.0.14-dfsg-2build1 5.0.16-dfsg-2
2016-03-11 12:30:38 status half-configured virtualbox:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:43 status unpacked virtualbox:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:44 status half-installed virtualbox:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:45 status half-installed virtualbox:amd64 5.0.14-dfsg-2build1
2016-03-11 12:30:46 status unpacked virtualbox:amd64 5.0.16-dfsg-2
2016-03-11 12:30:46 status unpacked virtualbox:amd64 5.0.16-dfsg-2
2016-03-11 12:30:46 upgrade xserver-common:all 2:1.17.3-2ubuntu4 2:1.18.1-1ubuntu3
2016-03-11 12:30:46 status half-configured xserver-common:all 2:1.17.3-2ubuntu4
2016-03-11 12:30:46 status unpacked xserver-common:all 2:1.17.3-2ubuntu4
2016-03-11 12:30:46 status half-installed xserver-common:all 2:1.17.3-2ubuntu4
2016-03-11 12:30:46 status half-installed xserver-common:all 2:1.17.3-2ubuntu4
2016-03-11 12:30:47 status unpacked xserver-common:all 2:1.18.1-1ubuntu3
2016-03-11 12:30:47 status unpacked xserver-common:all 2:1.18.1-1ubuntu3
2016-03-11 12:30:47 upgrade xserver-xorg-legacy:amd64 2:1.17.3-2ubuntu4 2:1.18.1-1ubuntu3
2016-03-11 12:30:47 status half-configured xserver-xorg-legacy:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:30:47 status unpacked xserver-xorg-legacy:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:30:47 status half-installed xserver-xorg-legacy:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:30:47 status half-installed xserver-xorg-legacy:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:30:47 status unpacked xserver-xorg-legacy:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:30:47 status unpacked xserver-xorg-legacy:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:30:48 upgrade x11-common:all 1:7.7+13ubuntu1 1:7.7+13ubuntu3
2016-03-11 12:30:48 status half-configured x11-common:all 1:7.7+13ubuntu1
2016-03-11 12:30:48 status unpacked x11-common:all 1:7.7+13ubuntu1
2016-03-11 12:30:48 status half-installed x11-common:all 1:7.7+13ubuntu1
2016-03-11 12:30:48 status half-installed x11-common:all 1:7.7+13ubuntu1
2016-03-11 12:30:49 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:30:49 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:30:49 upgrade x11proto-core-dev:all 7.0.28-0ubuntu2 7.0.28-2ubuntu1
2016-03-11 12:30:49 status half-configured x11proto-core-dev:all 7.0.28-0ubuntu2
2016-03-11 12:30:49 status unpacked x11proto-core-dev:all 7.0.28-0ubuntu2
2016-03-11 12:30:49 status half-installed x11proto-core-dev:all 7.0.28-0ubuntu2
2016-03-11 12:30:49 status half-installed x11proto-core-dev:all 7.0.28-0ubuntu2
2016-03-11 12:30:49 status unpacked x11proto-core-dev:all 7.0.28-2ubuntu1
2016-03-11 12:30:49 status unpacked x11proto-core-dev:all 7.0.28-2ubuntu1
2016-03-11 12:30:50 upgrade xserver-xorg-input-all:amd64 1:7.7+13ubuntu1 1:7.7+13ubuntu3
2016-03-11 12:30:50 status half-configured xserver-xorg-input-all:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:50 status unpacked xserver-xorg-input-all:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:50 status half-installed xserver-xorg-input-all:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:50 status half-installed xserver-xorg-input-all:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:50 status unpacked xserver-xorg-input-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:30:50 status unpacked xserver-xorg-input-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:30:50 upgrade xserver-xorg:amd64 1:7.7+13ubuntu1 1:7.7+13ubuntu3
2016-03-11 12:30:50 status half-configured xserver-xorg:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:51 status unpacked xserver-xorg:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:51 status half-installed xserver-xorg:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:51 status half-installed xserver-xorg:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:51 status unpacked xserver-xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:30:51 status unpacked xserver-xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:30:51 upgrade xorg-docs-core:all 1:1.7.1-0ubuntu2 1:1.7.1-1ubuntu1
2016-03-11 12:30:51 status half-configured xorg-docs-core:all 1:1.7.1-0ubuntu2
2016-03-11 12:30:51 status unpacked xorg-docs-core:all 1:1.7.1-0ubuntu2
2016-03-11 12:30:51 status half-installed xorg-docs-core:all 1:1.7.1-0ubuntu2
2016-03-11 12:30:52 status half-installed xorg-docs-core:all 1:1.7.1-0ubuntu2
2016-03-11 12:30:52 status unpacked xorg-docs-core:all 1:1.7.1-1ubuntu1
2016-03-11 12:30:52 status unpacked xorg-docs-core:all 1:1.7.1-1ubuntu1
2016-03-11 12:30:52 upgrade xorg:amd64 1:7.7+13ubuntu1 1:7.7+13ubuntu3
2016-03-11 12:30:52 status half-configured xorg:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:52 status unpacked xorg:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:52 status half-installed xorg:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:52 status half-installed xorg:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:53 status unpacked xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:30:53 status unpacked xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:30:53 upgrade xserver-xephyr:amd64 2:1.17.3-2ubuntu4 2:1.18.1-1ubuntu3
2016-03-11 12:30:53 status half-configured xserver-xephyr:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:30:53 status unpacked xserver-xephyr:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:30:53 status half-installed xserver-xephyr:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:30:53 status half-installed xserver-xephyr:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:30:53 status unpacked xserver-xephyr:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:30:53 status unpacked xserver-xephyr:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:30:54 upgrade xserver-xorg-video-all:amd64 1:7.7+13ubuntu1 1:7.7+13ubuntu3
2016-03-11 12:30:54 status half-configured xserver-xorg-video-all:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:54 status unpacked xserver-xorg-video-all:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:54 status half-installed xserver-xorg-video-all:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:54 status half-installed xserver-xorg-video-all:amd64 1:7.7+13ubuntu1
2016-03-11 12:30:54 status unpacked xserver-xorg-video-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:30:54 status unpacked xserver-xorg-video-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:30:54 upgrade dh-systemd:all 1.28ubuntu2 1.29ubuntu1
2016-03-11 12:30:54 status half-configured dh-systemd:all 1.28ubuntu2
2016-03-11 12:30:55 status unpacked dh-systemd:all 1.28ubuntu2
2016-03-11 12:30:55 status half-installed dh-systemd:all 1.28ubuntu2
2016-03-11 12:30:55 status half-installed dh-systemd:all 1.28ubuntu2
2016-03-11 12:30:55 status unpacked dh-systemd:all 1.29ubuntu1
2016-03-11 12:30:55 status unpacked dh-systemd:all 1.29ubuntu1
2016-03-11 12:30:55 upgrade inxi:all 2.2.33-0ubuntu1 2.2.35-0ubuntu1
2016-03-11 12:30:55 status half-configured inxi:all 2.2.33-0ubuntu1
2016-03-11 12:30:56 status unpacked inxi:all 2.2.33-0ubuntu1
2016-03-11 12:30:56 status half-installed inxi:all 2.2.33-0ubuntu1
2016-03-11 12:30:56 status half-installed inxi:all 2.2.33-0ubuntu1
2016-03-11 12:30:56 status unpacked inxi:all 2.2.35-0ubuntu1
2016-03-11 12:30:56 status unpacked inxi:all 2.2.35-0ubuntu1
2016-03-11 12:30:56 upgrade kde-cli-tools:amd64 4:5.4.3-0ubuntu1 4:5.5.4-0ubuntu1
2016-03-11 12:30:56 status half-configured kde-cli-tools:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:30:56 status unpacked kde-cli-tools:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:30:56 status half-installed kde-cli-tools:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:30:56 status half-installed kde-cli-tools:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:30:57 status unpacked kde-cli-tools:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:30:57 status unpacked kde-cli-tools:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:30:57 upgrade kde-cli-tools-data:all 4:5.4.3-0ubuntu1 4:5.5.4-0ubuntu1
2016-03-11 12:30:57 status half-configured kde-cli-tools-data:all 4:5.4.3-0ubuntu1
2016-03-11 12:30:57 status unpacked kde-cli-tools-data:all 4:5.4.3-0ubuntu1
2016-03-11 12:30:57 status half-installed kde-cli-tools-data:all 4:5.4.3-0ubuntu1
2016-03-11 12:30:58 status half-installed kde-cli-tools-data:all 4:5.4.3-0ubuntu1
2016-03-11 12:30:58 status unpacked kde-cli-tools-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:30:58 status unpacked kde-cli-tools-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:30:59 upgrade khelpcenter:amd64 4:5.4.3-0ubuntu1 4:5.5.4-0ubuntu1
2016-03-11 12:30:59 status half-configured khelpcenter:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:30:59 status unpacked khelpcenter:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:30:59 status half-installed khelpcenter:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:30:59 status half-installed khelpcenter:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:00 status half-installed khelpcenter:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:00 status unpacked khelpcenter:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:31:00 status unpacked khelpcenter:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:31:00 upgrade kio-extras:amd64 4:15.08.2-0ubuntu1 4:15.12.1-1ubuntu1
2016-03-11 12:31:00 status half-configured kio-extras:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:00 status unpacked kio-extras:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:00 status half-installed kio-extras:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:00 status half-installed kio-extras:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:01 status unpacked kio-extras:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:31:01 status unpacked kio-extras:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:31:01 upgrade kio-extras-data:all 4:15.08.2-0ubuntu1 4:15.12.1-1ubuntu1
2016-03-11 12:31:01 status half-configured kio-extras-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:31:01 status unpacked kio-extras-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:31:01 status half-installed kio-extras-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:31:01 status half-installed kio-extras-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:31:01 status half-installed kio-extras-data:all 4:15.08.2-0ubuntu1
2016-03-11 12:31:02 status unpacked kio-extras-data:all 4:15.12.1-1ubuntu1
2016-03-11 12:31:02 status unpacked kio-extras-data:all 4:15.12.1-1ubuntu1
2016-03-11 12:31:02 upgrade kolourpaint4:amd64 4:15.08.2-0ubuntu1 4:15.12.1-1ubuntu1
2016-03-11 12:31:02 status half-configured kolourpaint4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:02 status unpacked kolourpaint4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:02 status half-installed kolourpaint4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:02 status half-installed kolourpaint4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:02 status half-installed kolourpaint4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:03 status half-installed kolourpaint4:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:31:03 status unpacked kolourpaint4:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:31:03 status unpacked kolourpaint4:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:31:03 upgrade kpartx:amd64 0.5.0-7ubuntu15 0.5.0-7ubuntu16
2016-03-11 12:31:03 status half-configured kpartx:amd64 0.5.0-7ubuntu15
2016-03-11 12:31:03 status unpacked kpartx:amd64 0.5.0-7ubuntu15
2016-03-11 12:31:03 status half-installed kpartx:amd64 0.5.0-7ubuntu15
2016-03-11 12:31:04 status half-installed kpartx:amd64 0.5.0-7ubuntu15
2016-03-11 12:31:04 status unpacked kpartx:amd64 0.5.0-7ubuntu16
2016-03-11 12:31:04 status unpacked kpartx:amd64 0.5.0-7ubuntu16
2016-03-11 12:31:04 upgrade libbabeltrace1:amd64 1.3.1-1build1build0pie.3 1.3.2-1
2016-03-11 12:31:04 status half-configured libbabeltrace1:amd64 1.3.1-1build1build0pie.3
2016-03-11 12:31:04 status unpacked libbabeltrace1:amd64 1.3.1-1build1build0pie.3
2016-03-11 12:31:04 status half-installed libbabeltrace1:amd64 1.3.1-1build1build0pie.3
2016-03-11 12:31:05 status half-installed libbabeltrace1:amd64 1.3.1-1build1build0pie.3
2016-03-11 12:31:05 status unpacked libbabeltrace1:amd64 1.3.2-1
2016-03-11 12:31:05 status unpacked libbabeltrace1:amd64 1.3.2-1
2016-03-11 12:31:05 upgrade libbabeltrace-ctf1:amd64 1.3.1-1build1build0pie.3 1.3.2-1
2016-03-11 12:31:05 status half-configured libbabeltrace-ctf1:amd64 1.3.1-1build1build0pie.3
2016-03-11 12:31:05 status unpacked libbabeltrace-ctf1:amd64 1.3.1-1build1build0pie.3
2016-03-11 12:31:05 status half-installed libbabeltrace-ctf1:amd64 1.3.1-1build1build0pie.3
2016-03-11 12:31:05 status half-installed libbabeltrace-ctf1:amd64 1.3.1-1build1build0pie.3
2016-03-11 12:31:06 status unpacked libbabeltrace-ctf1:amd64 1.3.2-1
2016-03-11 12:31:06 status unpacked libbabeltrace-ctf1:amd64 1.3.2-1
2016-03-11 12:31:06 upgrade libfreeimage3:amd64 3.17.0+ds1-1.1 3.17.0+ds1-2
2016-03-11 12:31:06 status half-configured libfreeimage3:amd64 3.17.0+ds1-1.1
2016-03-11 12:31:06 status unpacked libfreeimage3:amd64 3.17.0+ds1-1.1
2016-03-11 12:31:06 status half-installed libfreeimage3:amd64 3.17.0+ds1-1.1
2016-03-11 12:31:06 status half-installed libfreeimage3:amd64 3.17.0+ds1-1.1
2016-03-11 12:31:07 status unpacked libfreeimage3:amd64 3.17.0+ds1-2
2016-03-11 12:31:07 status unpacked libfreeimage3:amd64 3.17.0+ds1-2
2016-03-11 12:31:07 upgrade libkf5filemetadata3:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:31:07 status half-configured libkf5filemetadata3:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:07 status unpacked libkf5filemetadata3:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:07 status half-installed libkf5filemetadata3:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:07 status half-installed libkf5filemetadata3:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:07 status unpacked libkf5filemetadata3:amd64 5.18.0-0ubuntu1
2016-03-11 12:31:07 status unpacked libkf5filemetadata3:amd64 5.18.0-0ubuntu1
2016-03-11 12:31:08 upgrade libkf5filemetadata-data:all 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:31:08 status half-configured libkf5filemetadata-data:all 5.15.0-0ubuntu2
2016-03-11 12:31:08 status unpacked libkf5filemetadata-data:all 5.15.0-0ubuntu2
2016-03-11 12:31:08 status half-installed libkf5filemetadata-data:all 5.15.0-0ubuntu2
2016-03-11 12:31:08 status half-installed libkf5filemetadata-data:all 5.15.0-0ubuntu2
2016-03-11 12:31:08 status unpacked libkf5filemetadata-data:all 5.18.0-0ubuntu1
2016-03-11 12:31:08 status unpacked libkf5filemetadata-data:all 5.18.0-0ubuntu1
2016-03-11 12:31:08 upgrade libkf5filemetadata-bin:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:31:08 status half-configured libkf5filemetadata-bin:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:08 status unpacked libkf5filemetadata-bin:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:08 status half-installed libkf5filemetadata-bin:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:09 status half-installed libkf5filemetadata-bin:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:09 status unpacked libkf5filemetadata-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:31:09 status unpacked libkf5filemetadata-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:31:09 upgrade libkf5networkmanagerqt6:amd64 5.15.0-0ubuntu2 5.18.0-0ubuntu1
2016-03-11 12:31:09 status half-configured libkf5networkmanagerqt6:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:09 status unpacked libkf5networkmanagerqt6:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:09 status half-installed libkf5networkmanagerqt6:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:10 status half-installed libkf5networkmanagerqt6:amd64 5.15.0-0ubuntu2
2016-03-11 12:31:10 status unpacked libkf5networkmanagerqt6:amd64 5.18.0-0ubuntu1
2016-03-11 12:31:10 status unpacked libkf5networkmanagerqt6:amd64 5.18.0-0ubuntu1
2016-03-11 12:31:12 upgrade libkf5screen6:amd64 4:5.4.3-0ubuntu1 4:5.5.4-2~ubuntu1
2016-03-11 12:31:12 status half-configured libkf5screen6:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:12 status unpacked libkf5screen6:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:12 status half-installed libkf5screen6:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:12 status half-installed libkf5screen6:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:13 status unpacked libkf5screen6:amd64 4:5.5.4-2~ubuntu1
2016-03-11 12:31:13 status unpacked libkf5screen6:amd64 4:5.5.4-2~ubuntu1
2016-03-11 12:31:13 upgrade milou:amd64 4:5.4.3-0ubuntu1 4:5.5.4-0ubuntu1
2016-03-11 12:31:13 status half-configured milou:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:13 status unpacked milou:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:13 status half-installed milou:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:13 status half-installed milou:amd64 4:5.4.3-0ubuntu1
2016-03-11 12:31:13 status unpacked milou:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:31:13 status unpacked milou:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:31:14 upgrade python-lockfile:all 1:0.10.2-2ubuntu1 1:0.12.2-1
2016-03-11 12:31:14 status half-configured python-lockfile:all 1:0.10.2-2ubuntu1
2016-03-11 12:31:14 status unpacked python-lockfile:all 1:0.10.2-2ubuntu1
2016-03-11 12:31:14 status half-installed python-lockfile:all 1:0.10.2-2ubuntu1
2016-03-11 12:31:14 status half-installed python-lockfile:all 1:0.10.2-2ubuntu1
2016-03-11 12:31:15 status unpacked python-lockfile:all 1:0.12.2-1
2016-03-11 12:31:15 status unpacked python-lockfile:all 1:0.12.2-1
2016-03-11 12:31:15 upgrade python-openvswitch:all 2.5.0~git20160219.522aca6-0ubuntu3 2.5.0-0ubuntu1
2016-03-11 12:31:15 status half-configured python-openvswitch:all 2.5.0~git20160219.522aca6-0ubuntu3
2016-03-11 12:31:15 status unpacked python-openvswitch:all 2.5.0~git20160219.522aca6-0ubuntu3
2016-03-11 12:31:15 status half-installed python-openvswitch:all 2.5.0~git20160219.522aca6-0ubuntu3
2016-03-11 12:31:15 status half-installed python-openvswitch:all 2.5.0~git20160219.522aca6-0ubuntu3
2016-03-11 12:31:16 status unpacked python-openvswitch:all 2.5.0-0ubuntu1
2016-03-11 12:31:16 status unpacked python-openvswitch:all 2.5.0-0ubuntu1
2016-03-11 12:31:16 upgrade selene:amd64 16.2.7~261~ubuntu16.04.1 16.3~264~ubuntu16.04.1
2016-03-11 12:31:16 status half-configured selene:amd64 16.2.7~261~ubuntu16.04.1
2016-03-11 12:31:16 status unpacked selene:amd64 16.2.7~261~ubuntu16.04.1
2016-03-11 12:31:16 status half-installed selene:amd64 16.2.7~261~ubuntu16.04.1
2016-03-11 12:31:16 status half-installed selene:amd64 16.2.7~261~ubuntu16.04.1
2016-03-11 12:31:16 status half-installed selene:amd64 16.2.7~261~ubuntu16.04.1
2016-03-11 12:31:16 status half-installed selene:amd64 16.2.7~261~ubuntu16.04.1
2016-03-11 12:31:17 status half-installed selene:amd64 16.2.7~261~ubuntu16.04.1
2016-03-11 12:31:17 status unpacked selene:amd64 16.3~264~ubuntu16.04.1
2016-03-11 12:31:17 status unpacked selene:amd64 16.3~264~ubuntu16.04.1
2016-03-11 12:31:17 trigproc update-notifier-common:all 3.166 <aucune>
2016-03-11 12:31:17 status half-configured update-notifier-common:all 3.166
2016-03-11 12:31:30 status installed update-notifier-common:all 3.166
2016-03-11 12:31:30 trigproc gconf2:amd64 3.2.6-3ubuntu6build0pie.1 <aucune>
2016-03-11 12:31:30 status half-configured gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:31:30 status installed gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:31:30 trigproc libglib2.0-0:i386 2.47.6-1 <aucune>
2016-03-11 12:31:30 status half-configured libglib2.0-0:i386 2.47.6-1
2016-03-11 12:31:30 status installed libglib2.0-0:i386 2.47.6-1
2016-03-11 12:31:30 trigproc libglib2.0-0:amd64 2.47.6-1 <aucune>
2016-03-11 12:31:30 status half-configured libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:31:30 status installed libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:31:30 trigproc desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1 <aucune>
2016-03-11 12:31:30 status half-configured desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:31:30 status installed desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:31:30 trigproc gnome-menus:amd64 3.13.3-6ubuntu3 <aucune>
2016-03-11 12:31:30 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:31:30 status installed gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:31:31 trigproc mime-support:all 3.59ubuntu1 <aucune>
2016-03-11 12:31:31 status half-configured mime-support:all 3.59ubuntu1
2016-03-11 12:31:31 status installed mime-support:all 3.59ubuntu1
2016-03-11 12:31:31 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:31:31 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:31:31 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:31:31 trigproc hicolor-icon-theme:all 0.15-0ubuntu1 <aucune>
2016-03-11 12:31:31 status half-configured hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:31:32 status installed hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:31:32 trigproc menu:amd64 2.1.47ubuntu1 <aucune>
2016-03-11 12:31:32 status half-configured menu:amd64 2.1.47ubuntu1
2016-03-11 12:31:32 status installed menu:amd64 2.1.47ubuntu1
2016-03-11 12:31:32 trigproc postgresql-common:all 172 <aucune>
2016-03-11 12:31:32 status half-configured postgresql-common:all 172
2016-03-11 12:31:33 status installed postgresql-common:all 172
2016-03-11 12:31:33 trigproc dbus:amd64 1.10.6-1ubuntu2 <aucune>
2016-03-11 12:31:33 status half-configured dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:31:33 status installed dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:31:33 trigproc shared-mime-info:amd64 1.5-2build~pie.1 <aucune>
2016-03-11 12:31:33 status half-configured shared-mime-info:amd64 1.5-2build~pie.1
2016-03-11 12:32:19 status installed shared-mime-info:amd64 1.5-2build~pie.1
2016-03-11 12:32:19 trigproc systemd:amd64 229-2ubuntu1 <aucune>
2016-03-11 12:32:19 status half-configured systemd:amd64 229-2ubuntu1
2016-03-11 12:32:19 status installed systemd:amd64 229-2ubuntu1
2016-03-11 12:32:19 trigproc ureadahead:amd64 0.100.0-19build~pie.1 <aucune>
2016-03-11 12:32:19 status half-configured ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:32:19 status installed ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:32:20 startup packages configure
2016-03-11 12:32:20 configure bsdmainutils:amd64 9.0.6ubuntu3 <aucune>
2016-03-11 12:32:20 status unpacked bsdmainutils:amd64 9.0.6ubuntu3
2016-03-11 12:32:20 status unpacked bsdmainutils:amd64 9.0.6ubuntu3
2016-03-11 12:32:20 status unpacked bsdmainutils:amd64 9.0.6ubuntu3
2016-03-11 12:32:20 status unpacked bsdmainutils:amd64 9.0.6ubuntu3
2016-03-11 12:32:20 status half-configured bsdmainutils:amd64 9.0.6ubuntu3
2016-03-11 12:32:20 status installed bsdmainutils:amd64 9.0.6ubuntu3
2016-03-11 12:32:20 configure perl-modules-5.22:all 5.22.1-8 <aucune>
2016-03-11 12:32:20 status unpacked perl-modules-5.22:all 5.22.1-8
2016-03-11 12:32:20 status half-configured perl-modules-5.22:all 5.22.1-8
2016-03-11 12:32:20 status installed perl-modules-5.22:all 5.22.1-8
2016-03-11 12:32:20 configure libperl5.22:amd64 5.22.1-8 <aucune>
2016-03-11 12:32:20 status unpacked libperl5.22:amd64 5.22.1-8
2016-03-11 12:32:21 status half-configured libperl5.22:amd64 5.22.1-8
2016-03-11 12:32:21 status installed libperl5.22:amd64 5.22.1-8
2016-03-11 12:32:21 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:32:21 configure perl:amd64 5.22.1-8 <aucune>
2016-03-11 12:32:21 status unpacked perl:amd64 5.22.1-8
2016-03-11 12:32:21 status unpacked perl:amd64 5.22.1-8
2016-03-11 12:32:21 status half-configured perl:amd64 5.22.1-8
2016-03-11 12:32:21 status installed perl:amd64 5.22.1-8
2016-03-11 12:32:21 configure libapt-inst2.0:amd64 1.2.4 <aucune>
2016-03-11 12:32:21 status unpacked libapt-inst2.0:amd64 1.2.4
2016-03-11 12:32:21 status half-configured libapt-inst2.0:amd64 1.2.4
2016-03-11 12:32:21 status installed libapt-inst2.0:amd64 1.2.4
2016-03-11 12:32:22 configure libapt-pkg-dev:amd64 1.2.4 <aucune>
2016-03-11 12:32:22 status unpacked libapt-pkg-dev:amd64 1.2.4
2016-03-11 12:32:22 status half-configured libapt-pkg-dev:amd64 1.2.4
2016-03-11 12:32:22 status installed libapt-pkg-dev:amd64 1.2.4
2016-03-11 12:32:22 configure apt-utils:amd64 1.2.4 <aucune>
2016-03-11 12:32:22 status unpacked apt-utils:amd64 1.2.4
2016-03-11 12:32:22 status half-configured apt-utils:amd64 1.2.4
2016-03-11 12:32:22 status installed apt-utils:amd64 1.2.4
2016-03-11 12:32:22 configure libgtk-3-common:all 3.18.8-1ubuntu2 <aucune>
2016-03-11 12:32:22 status unpacked libgtk-3-common:all 3.18.8-1ubuntu2
2016-03-11 12:32:22 status unpacked libgtk-3-common:all 3.18.8-1ubuntu2
2016-03-11 12:32:22 status half-configured libgtk-3-common:all 3.18.8-1ubuntu2
2016-03-11 12:32:22 status installed libgtk-3-common:all 3.18.8-1ubuntu2
2016-03-11 12:32:22 configure fontconfig-config:all 2.11.1-0ubuntu8 <aucune>
2016-03-11 12:32:22 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:22 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:22 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:22 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:23 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:24 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status unpacked fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status half-configured fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 status installed fontconfig-config:all 2.11.1-0ubuntu8
2016-03-11 12:32:25 configure libfontconfig1:amd64 2.11.1-0ubuntu8 <aucune>
2016-03-11 12:32:25 status unpacked libfontconfig1:amd64 2.11.1-0ubuntu8
2016-03-11 12:32:26 status half-configured libfontconfig1:amd64 2.11.1-0ubuntu8
2016-03-11 12:32:26 status installed libfontconfig1:amd64 2.11.1-0ubuntu8
2016-03-11 12:32:26 configure libfontconfig1:i386 2.11.1-0ubuntu8 <aucune>
2016-03-11 12:32:26 status unpacked libfontconfig1:i386 2.11.1-0ubuntu8
2016-03-11 12:32:26 status half-configured libfontconfig1:i386 2.11.1-0ubuntu8
2016-03-11 12:32:26 status installed libfontconfig1:i386 2.11.1-0ubuntu8
2016-03-11 12:32:26 configure libjson-glib-1.0-common:all 1.1.2-0ubuntu1 <aucune>
2016-03-11 12:32:26 status unpacked libjson-glib-1.0-common:all 1.1.2-0ubuntu1
2016-03-11 12:32:26 status half-configured libjson-glib-1.0-common:all 1.1.2-0ubuntu1
2016-03-11 12:32:26 status installed libjson-glib-1.0-common:all 1.1.2-0ubuntu1
2016-03-11 12:32:26 configure libjson-glib-1.0-0:amd64 1.1.2-0ubuntu1 <aucune>
2016-03-11 12:32:26 status unpacked libjson-glib-1.0-0:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:26 status half-configured libjson-glib-1.0-0:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:26 status installed libjson-glib-1.0-0:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:26 configure libgtk-3-0:amd64 3.18.8-1ubuntu2 <aucune>
2016-03-11 12:32:26 status unpacked libgtk-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:26 status unpacked libgtk-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:26 status half-configured libgtk-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 status installed libgtk-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 configure libgtk-3-0-dbg:amd64 3.18.8-1ubuntu2 <aucune>
2016-03-11 12:32:27 status unpacked libgtk-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 status half-configured libgtk-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 status installed libgtk-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 configure libgail-3-0:amd64 3.18.8-1ubuntu2 <aucune>
2016-03-11 12:32:27 status unpacked libgail-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 status half-configured libgail-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 status installed libgail-3-0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 configure libgail-3-0-dbg:amd64 3.18.8-1ubuntu2 <aucune>
2016-03-11 12:32:27 status unpacked libgail-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 status half-configured libgail-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 status installed libgail-3-0-dbg:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:27 configure libfontconfig1-dev:amd64 2.11.1-0ubuntu8 <aucune>
2016-03-11 12:32:27 status unpacked libfontconfig1-dev:amd64 2.11.1-0ubuntu8
2016-03-11 12:32:27 status half-configured libfontconfig1-dev:amd64 2.11.1-0ubuntu8
2016-03-11 12:32:27 status installed libfontconfig1-dev:amd64 2.11.1-0ubuntu8
2016-03-11 12:32:27 configure gir1.2-json-1.0:amd64 1.1.2-0ubuntu1 <aucune>
2016-03-11 12:32:27 status unpacked gir1.2-json-1.0:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:27 status half-configured gir1.2-json-1.0:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:28 status installed gir1.2-json-1.0:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:28 configure libjson-glib-dev:amd64 1.1.2-0ubuntu1 <aucune>
2016-03-11 12:32:28 status unpacked libjson-glib-dev:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:28 status half-configured libjson-glib-dev:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:28 status installed libjson-glib-dev:amd64 1.1.2-0ubuntu1
2016-03-11 12:32:28 configure gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu2 <aucune>
2016-03-11 12:32:28 status unpacked gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:28 status half-configured gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:28 status installed gir1.2-gtk-3.0:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:28 configure libgtk-3-dev:amd64 3.18.8-1ubuntu2 <aucune>
2016-03-11 12:32:28 status unpacked libgtk-3-dev:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:28 status half-configured libgtk-3-dev:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:28 status installed libgtk-3-dev:amd64 3.18.8-1ubuntu2
2016-03-11 12:32:28 configure language-selector-common:all 0.158 <aucune>
2016-03-11 12:32:28 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:28 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:28 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:28 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:28 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:28 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:29 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:29 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:29 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:29 status unpacked language-selector-common:all 0.158
2016-03-11 12:32:29 status half-configured language-selector-common:all 0.158
2016-03-11 12:32:29 status installed language-selector-common:all 0.158
2016-03-11 12:32:29 configure language-selector-gnome:all 0.158 <aucune>
2016-03-11 12:32:29 status unpacked language-selector-gnome:all 0.158
2016-03-11 12:32:29 status half-configured language-selector-gnome:all 0.158
2016-03-11 12:32:29 status installed language-selector-gnome:all 0.158
2016-03-11 12:32:30 configure uuid-runtime:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:32:30 status unpacked uuid-runtime:amd64 2.27.1-4ubuntu1
2016-03-11 12:32:30 status unpacked uuid-runtime:amd64 2.27.1-4ubuntu1
2016-03-11 12:32:30 status half-configured uuid-runtime:amd64 2.27.1-4ubuntu1
2016-03-11 12:32:31 status installed uuid-runtime:amd64 2.27.1-4ubuntu1
2016-03-11 12:32:31 configure fontconfig:amd64 2.11.1-0ubuntu8 <aucune>
2016-03-11 12:32:31 status unpacked fontconfig:amd64 2.11.1-0ubuntu8
2016-03-11 12:32:31 status half-configured fontconfig:amd64 2.11.1-0ubuntu8
2016-03-11 12:33:58 status installed fontconfig:amd64 2.11.1-0ubuntu8
2016-03-11 12:33:58 configure imagemagick-common:all 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:33:58 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:58 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:58 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:58 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:58 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:58 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:58 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:59 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:59 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:59 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:33:59 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status unpacked imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status half-configured imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status installed imagemagick-common:all 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 configure libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:34:00 status unpacked libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status half-configured libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status installed libmagickcore-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 configure libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:34:00 status unpacked libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status half-configured libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status installed libmagickwand-6.q16-2:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 configure imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:34:00 status unpacked imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status half-configured imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status installed imagemagick-6.q16:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 configure libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:34:00 status unpacked libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:00 status half-configured libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 status installed libmagickcore-6.q16-2-extra:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 configure libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:34:01 status unpacked libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 status half-configured libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 status installed libmagick++-6.q16-5v5:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 configure libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:34:01 status unpacked libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 status half-configured libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 status installed libimage-magick-q16-perl:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 configure imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:34:01 status unpacked imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 status half-configured imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 status installed imagemagick-dbg:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 configure imagemagick:amd64 8:6.8.9.9-7ubuntu2 <aucune>
2016-03-11 12:34:01 status unpacked imagemagick:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:01 status half-configured imagemagick:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:02 status installed imagemagick:amd64 8:6.8.9.9-7ubuntu2
2016-03-11 12:34:02 status triggers-pending menu:amd64 2.1.47ubuntu1
2016-03-11 12:34:02 status triggers-awaited menu:amd64 2.1.47ubuntu1
2016-03-11 12:34:02 configure language-pack-en:all 1:16.04+20160306 <aucune>
2016-03-11 12:34:02 status unpacked language-pack-en:all 1:16.04+20160306
2016-03-11 12:34:02 status half-configured language-pack-en:all 1:16.04+20160306
2016-03-11 12:34:02 status installed language-pack-en:all 1:16.04+20160306
2016-03-11 12:34:02 configure language-pack-fr:all 1:16.04+20160306 <aucune>
2016-03-11 12:34:02 status unpacked language-pack-fr:all 1:16.04+20160306
2016-03-11 12:34:02 status half-configured language-pack-fr:all 1:16.04+20160306
2016-03-11 12:34:02 status installed language-pack-fr:all 1:16.04+20160306
2016-03-11 12:34:02 configure language-pack-gnome-en:all 1:16.04+20160306 <aucune>
2016-03-11 12:34:02 status unpacked language-pack-gnome-en:all 1:16.04+20160306
2016-03-11 12:34:02 status half-configured language-pack-gnome-en:all 1:16.04+20160306
2016-03-11 12:34:03 status installed language-pack-gnome-en:all 1:16.04+20160306
2016-03-11 12:34:03 configure language-pack-gnome-fr:all 1:16.04+20160306 <aucune>
2016-03-11 12:34:03 status unpacked language-pack-gnome-fr:all 1:16.04+20160306
2016-03-11 12:34:03 status half-configured language-pack-gnome-fr:all 1:16.04+20160306
2016-03-11 12:34:03 status installed language-pack-gnome-fr:all 1:16.04+20160306
2016-03-11 12:34:03 configure python-pymysql:all 0.7.2-1 <aucune>
2016-03-11 12:34:03 status unpacked python-pymysql:all 0.7.2-1
2016-03-11 12:34:03 status half-configured python-pymysql:all 0.7.2-1
2016-03-11 12:34:03 status installed python-pymysql:all 0.7.2-1
2016-03-11 12:34:03 configure python3-pymysql:all 0.7.2-1 <aucune>
2016-03-11 12:34:03 status unpacked python3-pymysql:all 0.7.2-1
2016-03-11 12:34:03 status half-configured python3-pymysql:all 0.7.2-1
2016-03-11 12:34:04 status installed python3-pymysql:all 0.7.2-1
2016-03-11 12:34:04 configure kmod:amd64 22-1ubuntu3 <aucune>
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:04 status unpacked kmod:amd64 22-1ubuntu3
2016-03-11 12:34:05 status half-configured kmod:amd64 22-1ubuntu3
2016-03-11 12:34:05 status installed kmod:amd64 22-1ubuntu3
2016-03-11 12:34:05 configure ubuntu-drivers-common:amd64 1:0.4.16 <aucune>
2016-03-11 12:34:05 status unpacked ubuntu-drivers-common:amd64 1:0.4.16
2016-03-11 12:34:05 status unpacked ubuntu-drivers-common:amd64 1:0.4.16
2016-03-11 12:34:05 status half-configured ubuntu-drivers-common:amd64 1:0.4.16
2016-03-11 12:34:06 status installed ubuntu-drivers-common:amd64 1:0.4.16
2016-03-11 12:34:06 configure uuid-dev:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:34:06 status unpacked uuid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:06 status half-configured uuid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:06 status installed uuid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:06 configure libblkid-dev:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:34:06 status unpacked libblkid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:06 status half-configured libblkid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:06 status installed libblkid-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:06 configure libfdisk-dev:amd64 2.27.1-4ubuntu1 <aucune>
2016-03-11 12:34:06 status unpacked libfdisk-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:06 status half-configured libfdisk-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:06 status installed libfdisk-dev:amd64 2.27.1-4ubuntu1
2016-03-11 12:34:07 configure libkrb5-3:i386 1.13.2+dfsg-5 <aucune>
2016-03-11 12:34:07 status unpacked libkrb5-3:i386 1.13.2+dfsg-5
2016-03-11 12:34:07 status half-configured libkrb5-3:i386 1.13.2+dfsg-5
2016-03-11 12:34:07 status installed libkrb5-3:i386 1.13.2+dfsg-5
2016-03-11 12:34:07 configure libkrb5-3:amd64 1.13.2+dfsg-5 <aucune>
2016-03-11 12:34:07 status unpacked libkrb5-3:amd64 1.13.2+dfsg-5
2016-03-11 12:34:07 status half-configured libkrb5-3:amd64 1.13.2+dfsg-5
2016-03-11 12:34:07 status installed libkrb5-3:amd64 1.13.2+dfsg-5
2016-03-11 12:34:07 configure libgssapi-krb5-2:i386 1.13.2+dfsg-5 <aucune>
2016-03-11 12:34:07 status unpacked libgssapi-krb5-2:i386 1.13.2+dfsg-5
2016-03-11 12:34:07 status unpacked libgssapi-krb5-2:i386 1.13.2+dfsg-5
2016-03-11 12:34:07 status half-configured libgssapi-krb5-2:i386 1.13.2+dfsg-5
2016-03-11 12:34:07 status installed libgssapi-krb5-2:i386 1.13.2+dfsg-5
2016-03-11 12:34:07 configure libgssapi-krb5-2:amd64 1.13.2+dfsg-5 <aucune>
2016-03-11 12:34:07 status unpacked libgssapi-krb5-2:amd64 1.13.2+dfsg-5
2016-03-11 12:34:07 status unpacked libgssapi-krb5-2:amd64 1.13.2+dfsg-5
2016-03-11 12:34:07 status half-configured libgssapi-krb5-2:amd64 1.13.2+dfsg-5
2016-03-11 12:34:07 status installed libgssapi-krb5-2:amd64 1.13.2+dfsg-5
2016-03-11 12:34:07 configure keyboard-configuration:all 1.108ubuntu11 <aucune>
2016-03-11 12:34:07 status unpacked keyboard-configuration:all 1.108ubuntu11
2016-03-11 12:34:07 status unpacked keyboard-configuration:all 1.108ubuntu11
2016-03-11 12:34:07 status unpacked keyboard-configuration:all 1.108ubuntu11
2016-03-11 12:34:08 status half-configured keyboard-configuration:all 1.108ubuntu11
2016-03-11 12:34:09 status installed keyboard-configuration:all 1.108ubuntu11
2016-03-11 12:34:09 configure console-setup-linux:all 1.108ubuntu11 <aucune>
2016-03-11 12:34:09 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:09 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:09 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:10 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:11 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:12 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:12 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:12 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:12 status unpacked console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:12 status half-configured console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:12 status installed console-setup-linux:all 1.108ubuntu11
2016-03-11 12:34:12 configure initramfs-tools-bin:amd64 0.122ubuntu6 <aucune>
2016-03-11 12:34:12 status unpacked initramfs-tools-bin:amd64 0.122ubuntu6
2016-03-11 12:34:12 status half-configured initramfs-tools-bin:amd64 0.122ubuntu6
2016-03-11 12:34:12 status installed initramfs-tools-bin:amd64 0.122ubuntu6
2016-03-11 12:34:12 configure initramfs-tools-core:all 0.122ubuntu6 <aucune>
2016-03-11 12:34:12 status unpacked initramfs-tools-core:all 0.122ubuntu6
2016-03-11 12:34:12 status unpacked initramfs-tools-core:all 0.122ubuntu6
2016-03-11 12:34:12 status half-configured initramfs-tools-core:all 0.122ubuntu6
2016-03-11 12:34:12 status installed initramfs-tools-core:all 0.122ubuntu6
2016-03-11 12:34:12 configure initramfs-tools:all 0.122ubuntu6 <aucune>
2016-03-11 12:34:12 status unpacked initramfs-tools:all 0.122ubuntu6
2016-03-11 12:34:12 status unpacked initramfs-tools:all 0.122ubuntu6
2016-03-11 12:34:12 status unpacked initramfs-tools:all 0.122ubuntu6
2016-03-11 12:34:13 status unpacked initramfs-tools:all 0.122ubuntu6
2016-03-11 12:34:13 status half-configured initramfs-tools:all 0.122ubuntu6
2016-03-11 12:34:13 status installed initramfs-tools:all 0.122ubuntu6
2016-03-11 12:34:13 status triggers-pending initramfs-tools:all 0.122ubuntu6
2016-03-11 12:34:13 configure console-setup:all 1.108ubuntu11 <aucune>
2016-03-11 12:34:13 status unpacked console-setup:all 1.108ubuntu11
2016-03-11 12:34:13 status unpacked console-setup:all 1.108ubuntu11
2016-03-11 12:34:13 status half-configured console-setup:all 1.108ubuntu11
2016-03-11 12:34:14 status installed console-setup:all 1.108ubuntu11
2016-03-11 12:34:14 configure libisc160:amd64 1:9.10.3.dfsg.P2-5 <aucune>
2016-03-11 12:34:14 status unpacked libisc160:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:14 status half-configured libisc160:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:14 status installed libisc160:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:14 configure libssl1.0.0:amd64 1.0.2g-1ubuntu2 <aucune>
2016-03-11 12:34:14 status unpacked libssl1.0.0:amd64 1.0.2g-1ubuntu2
2016-03-11 12:34:14 status half-configured libssl1.0.0:amd64 1.0.2g-1ubuntu2
2016-03-11 12:34:15 status installed libssl1.0.0:amd64 1.0.2g-1ubuntu2
2016-03-11 12:34:15 configure libssl1.0.0:i386 1.0.2g-1ubuntu2 <aucune>
2016-03-11 12:34:15 status unpacked libssl1.0.0:i386 1.0.2g-1ubuntu2
2016-03-11 12:34:15 status half-configured libssl1.0.0:i386 1.0.2g-1ubuntu2
2016-03-11 12:34:15 status installed libssl1.0.0:i386 1.0.2g-1ubuntu2
2016-03-11 12:34:15 configure libdns162:amd64 1:9.10.3.dfsg.P2-5 <aucune>
2016-03-11 12:34:15 status unpacked libdns162:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:15 status half-configured libdns162:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:15 status installed libdns162:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:15 configure libisccc140:amd64 1:9.10.3.dfsg.P2-5 <aucune>
2016-03-11 12:34:15 status unpacked libisccc140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status half-configured libisccc140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status installed libisccc140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 configure libisccfg140:amd64 1:9.10.3.dfsg.P2-5 <aucune>
2016-03-11 12:34:16 status unpacked libisccfg140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status half-configured libisccfg140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status installed libisccfg140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 configure libbind9-140:amd64 1:9.10.3.dfsg.P2-5 <aucune>
2016-03-11 12:34:16 status unpacked libbind9-140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status half-configured libbind9-140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status installed libbind9-140:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 configure liblwres141:amd64 1:9.10.3.dfsg.P2-5 <aucune>
2016-03-11 12:34:16 status unpacked liblwres141:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status half-configured liblwres141:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status installed liblwres141:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 configure bind9-host:amd64 1:9.10.3.dfsg.P2-5 <aucune>
2016-03-11 12:34:16 status unpacked bind9-host:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status half-configured bind9-host:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 status installed bind9-host:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:16 configure dnsutils:amd64 1:9.10.3.dfsg.P2-5 <aucune>
2016-03-11 12:34:16 status unpacked dnsutils:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:17 status half-configured dnsutils:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:17 status installed dnsutils:amd64 1:9.10.3.dfsg.P2-5
2016-03-11 12:34:17 configure isc-dhcp-client:amd64 4.3.3-5ubuntu9 <aucune>
2016-03-11 12:34:17 status unpacked isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:17 status unpacked isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:17 status unpacked isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:17 status unpacked isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:17 status unpacked isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:17 status half-configured isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:18 status installed isc-dhcp-client:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:18 configure isc-dhcp-common:amd64 4.3.3-5ubuntu9 <aucune>
2016-03-11 12:34:18 status unpacked isc-dhcp-common:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:18 status half-configured isc-dhcp-common:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:18 status installed isc-dhcp-common:amd64 4.3.3-5ubuntu9
2016-03-11 12:34:18 configure ubuntu-minimal:amd64 1.349 <aucune>
2016-03-11 12:34:18 status unpacked ubuntu-minimal:amd64 1.349
2016-03-11 12:34:18 status half-configured ubuntu-minimal:amd64 1.349
2016-03-11 12:34:18 status installed ubuntu-minimal:amd64 1.349
2016-03-11 12:34:18 configure apt-transport-https:amd64 1.2.4 <aucune>
2016-03-11 12:34:18 status unpacked apt-transport-https:amd64 1.2.4
2016-03-11 12:34:18 status half-configured apt-transport-https:amd64 1.2.4
2016-03-11 12:34:18 status installed apt-transport-https:amd64 1.2.4
2016-03-11 12:34:18 configure krb5-locales:all 1.13.2+dfsg-5 <aucune>
2016-03-11 12:34:18 status unpacked krb5-locales:all 1.13.2+dfsg-5
2016-03-11 12:34:18 status half-configured krb5-locales:all 1.13.2+dfsg-5
2016-03-11 12:34:18 status installed krb5-locales:all 1.13.2+dfsg-5
2016-03-11 12:34:18 configure ltrace:amd64 0.7.3-5.1ubuntu3 <aucune>
2016-03-11 12:34:18 status unpacked ltrace:amd64 0.7.3-5.1ubuntu3
2016-03-11 12:34:19 status unpacked ltrace:amd64 0.7.3-5.1ubuntu3
2016-03-11 12:34:19 status half-configured ltrace:amd64 0.7.3-5.1ubuntu3
2016-03-11 12:34:19 status installed ltrace:amd64 0.7.3-5.1ubuntu3
2016-03-11 12:34:19 configure openssh-client:amd64 1:7.2p1-1 <aucune>
2016-03-11 12:34:19 status unpacked openssh-client:amd64 1:7.2p1-1
2016-03-11 12:34:19 status unpacked openssh-client:amd64 1:7.2p1-1
2016-03-11 12:34:19 status unpacked openssh-client:amd64 1:7.2p1-1
2016-03-11 12:34:19 status half-configured openssh-client:amd64 1:7.2p1-1
2016-03-11 12:34:19 status installed openssh-client:amd64 1:7.2p1-1
2016-03-11 12:34:19 configure openssh-sftp-server:amd64 1:7.2p1-1 <aucune>
2016-03-11 12:34:19 status unpacked openssh-sftp-server:amd64 1:7.2p1-1
2016-03-11 12:34:19 status half-configured openssh-sftp-server:amd64 1:7.2p1-1
2016-03-11 12:34:19 status installed openssh-sftp-server:amd64 1:7.2p1-1
2016-03-11 12:34:19 configure openssh-server:amd64 1:7.2p1-1 <aucune>
2016-03-11 12:34:19 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:19 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:19 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:20 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:20 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:20 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:20 status unpacked openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:20 status half-configured openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:21 status installed openssh-server:amd64 1:7.2p1-1
2016-03-11 12:34:21 configure openssl:amd64 1.0.2g-1ubuntu2 <aucune>
2016-03-11 12:34:21 status unpacked openssl:amd64 1.0.2g-1ubuntu2
2016-03-11 12:34:21 status unpacked openssl:amd64 1.0.2g-1ubuntu2
2016-03-11 12:34:21 status half-configured openssl:amd64 1.0.2g-1ubuntu2
2016-03-11 12:34:21 status installed openssl:amd64 1.0.2g-1ubuntu2
2016-03-11 12:34:21 configure python3-distupgrade:all 1:16.04.8 <aucune>
2016-03-11 12:34:21 status unpacked python3-distupgrade:all 1:16.04.8
2016-03-11 12:34:22 status half-configured python3-distupgrade:all 1:16.04.8
2016-03-11 12:34:22 status installed python3-distupgrade:all 1:16.04.8
2016-03-11 12:34:22 configure ubuntu-release-upgrader-core:all 1:16.04.8 <aucune>
2016-03-11 12:34:22 status unpacked ubuntu-release-upgrader-core:all 1:16.04.8
2016-03-11 12:34:22 status unpacked ubuntu-release-upgrader-core:all 1:16.04.8
2016-03-11 12:34:22 status unpacked ubuntu-release-upgrader-core:all 1:16.04.8
2016-03-11 12:34:22 status unpacked ubuntu-release-upgrader-core:all 1:16.04.8
2016-03-11 12:34:22 status half-configured ubuntu-release-upgrader-core:all 1:16.04.8
2016-03-11 12:34:23 status installed ubuntu-release-upgrader-core:all 1:16.04.8
2016-03-11 12:34:23 configure ubuntu-release-upgrader-gtk:all 1:16.04.8 <aucune>
2016-03-11 12:34:23 status unpacked ubuntu-release-upgrader-gtk:all 1:16.04.8
2016-03-11 12:34:23 status half-configured ubuntu-release-upgrader-gtk:all 1:16.04.8
2016-03-11 12:34:23 status installed ubuntu-release-upgrader-gtk:all 1:16.04.8
2016-03-11 12:34:23 configure ubuntu-standard:amd64 1.349 <aucune>
2016-03-11 12:34:23 status unpacked ubuntu-standard:amd64 1.349
2016-03-11 12:34:23 status half-configured ubuntu-standard:amd64 1.349
2016-03-11 12:34:23 status installed ubuntu-standard:amd64 1.349
2016-03-11 12:34:23 configure libgstreamer1.0-0:amd64 1.7.90-1 <aucune>
2016-03-11 12:34:23 status unpacked libgstreamer1.0-0:amd64 1.7.90-1
2016-03-11 12:34:23 status half-configured libgstreamer1.0-0:amd64 1.7.90-1
2016-03-11 12:34:23 status installed libgstreamer1.0-0:amd64 1.7.90-1
2016-03-11 12:34:23 configure libgstreamer-plugins-base1.0-0:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:23 status unpacked libgstreamer-plugins-base1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:23 status half-configured libgstreamer-plugins-base1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:24 status installed libgstreamer-plugins-base1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:24 configure empathy-common:all 3.12.11-0ubuntu3 <aucune>
2016-03-11 12:34:24 status unpacked empathy-common:all 3.12.11-0ubuntu3
2016-03-11 12:34:24 status half-configured empathy-common:all 3.12.11-0ubuntu3
2016-03-11 12:34:24 status installed empathy-common:all 3.12.11-0ubuntu3
2016-03-11 12:34:24 configure gstreamer1.0-pulseaudio:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:24 status unpacked gstreamer1.0-pulseaudio:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:24 status half-configured gstreamer1.0-pulseaudio:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:24 status installed gstreamer1.0-pulseaudio:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:24 configure empathy:amd64 3.12.11-0ubuntu3 <aucune>
2016-03-11 12:34:24 status unpacked empathy:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:24 status half-configured empathy:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:24 status installed empathy:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:24 configure mcp-account-manager-goa:amd64 3.12.11-0ubuntu3 <aucune>
2016-03-11 12:34:24 status unpacked mcp-account-manager-goa:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:24 status half-configured mcp-account-manager-goa:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 status installed mcp-account-manager-goa:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 configure mcp-account-manager-uoa:amd64 3.12.11-0ubuntu3 <aucune>
2016-03-11 12:34:25 status unpacked mcp-account-manager-uoa:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 status half-configured mcp-account-manager-uoa:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 status installed mcp-account-manager-uoa:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 configure account-plugin-jabber:amd64 3.12.11-0ubuntu3 <aucune>
2016-03-11 12:34:25 status unpacked account-plugin-jabber:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 status half-configured account-plugin-jabber:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 status installed account-plugin-jabber:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 configure account-plugin-salut:amd64 3.12.11-0ubuntu3 <aucune>
2016-03-11 12:34:25 status unpacked account-plugin-salut:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 status half-configured account-plugin-salut:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 status installed account-plugin-salut:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:25 configure gir1.2-gstreamer-1.0:amd64 1.7.90-1 <aucune>
2016-03-11 12:34:25 status unpacked gir1.2-gstreamer-1.0:amd64 1.7.90-1
2016-03-11 12:34:25 status half-configured gir1.2-gstreamer-1.0:amd64 1.7.90-1
2016-03-11 12:34:25 status installed gir1.2-gstreamer-1.0:amd64 1.7.90-1
2016-03-11 12:34:25 configure libgstreamer1.0-dev:amd64 1.7.90-1 <aucune>
2016-03-11 12:34:25 status unpacked libgstreamer1.0-dev:amd64 1.7.90-1
2016-03-11 12:34:26 status half-configured libgstreamer1.0-dev:amd64 1.7.90-1
2016-03-11 12:34:26 status installed libgstreamer1.0-dev:amd64 1.7.90-1
2016-03-11 12:34:26 configure libgstreamer1.0-0-dbg:amd64 1.7.90-1 <aucune>
2016-03-11 12:34:26 status unpacked libgstreamer1.0-0-dbg:amd64 1.7.90-1
2016-03-11 12:34:26 status half-configured libgstreamer1.0-0-dbg:amd64 1.7.90-1
2016-03-11 12:34:26 status installed libgstreamer1.0-0-dbg:amd64 1.7.90-1
2016-03-11 12:34:26 configure gstreamer1.0-alsa:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:26 status unpacked gstreamer1.0-alsa:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:26 status half-configured gstreamer1.0-alsa:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:26 status installed gstreamer1.0-alsa:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:26 configure gstreamer1.0-plugins-base:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:26 status unpacked gstreamer1.0-plugins-base:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:26 status half-configured gstreamer1.0-plugins-base:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:26 status installed gstreamer1.0-plugins-base:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 configure gstreamer1.0-x:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:27 status unpacked gstreamer1.0-x:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 status half-configured gstreamer1.0-x:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 status installed gstreamer1.0-x:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 configure gstreamer1.0-plugins-base-dbg:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:27 status unpacked gstreamer1.0-plugins-base-dbg:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 status half-configured gstreamer1.0-plugins-base-dbg:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 status installed gstreamer1.0-plugins-base-dbg:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 configure gstreamer1.0-plugins-ugly-amr:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:27 status unpacked gstreamer1.0-plugins-ugly-amr:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 status half-configured gstreamer1.0-plugins-ugly-amr:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 status installed gstreamer1.0-plugins-ugly-amr:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 configure gstreamer1.0-plugins-ugly:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:27 status unpacked gstreamer1.0-plugins-ugly:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 status half-configured gstreamer1.0-plugins-ugly:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:27 status installed gstreamer1.0-plugins-ugly:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:28 configure libgstreamer-plugins-bad1.0-0:amd64 1.7.90-1ubuntu2 <aucune>
2016-03-11 12:34:28 status unpacked libgstreamer-plugins-bad1.0-0:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 status half-configured libgstreamer-plugins-bad1.0-0:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 status installed libgstreamer-plugins-bad1.0-0:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 configure gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.90-1ubuntu2 <aucune>
2016-03-11 12:34:28 status unpacked gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 status half-configured gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 status installed gstreamer1.0-plugins-bad-videoparsers:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 configure gstreamer1.0-plugins-bad-faad:amd64 1.7.90-1ubuntu2 <aucune>
2016-03-11 12:34:28 status unpacked gstreamer1.0-plugins-bad-faad:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 status half-configured gstreamer1.0-plugins-bad-faad:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 status installed gstreamer1.0-plugins-bad-faad:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 configure libgstreamer-plugins-good1.0-0:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:28 status unpacked libgstreamer-plugins-good1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:28 status half-configured libgstreamer-plugins-good1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:28 status installed libgstreamer-plugins-good1.0-0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:28 configure gstreamer1.0-plugins-bad:amd64 1.7.90-1ubuntu2 <aucune>
2016-03-11 12:34:28 status unpacked gstreamer1.0-plugins-bad:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 status half-configured gstreamer1.0-plugins-bad:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 status installed gstreamer1.0-plugins-bad:amd64 1.7.90-1ubuntu2
2016-03-11 12:34:28 configure gstreamer1.0-plugins-good:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:28 status unpacked gstreamer1.0-plugins-good:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:28 status half-configured gstreamer1.0-plugins-good:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:29 status installed gstreamer1.0-plugins-good:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:29 configure account-plugin-aim:amd64 3.12.11-0ubuntu3 <aucune>
2016-03-11 12:34:29 status unpacked account-plugin-aim:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:29 status half-configured account-plugin-aim:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:30 status installed account-plugin-aim:amd64 3.12.11-0ubuntu3
2016-03-11 12:34:30 configure libaccount-plugin-generic-oauth:amd64 0.12+16.04.20160126-0ubuntu1 <aucune>
2016-03-11 12:34:30 status unpacked libaccount-plugin-generic-oauth:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status half-configured libaccount-plugin-generic-oauth:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status installed libaccount-plugin-generic-oauth:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 configure account-plugin-facebook:all 0.12+16.04.20160126-0ubuntu1 <aucune>
2016-03-11 12:34:30 status unpacked account-plugin-facebook:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status unpacked account-plugin-facebook:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status half-configured account-plugin-facebook:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status installed account-plugin-facebook:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 configure account-plugin-flickr:all 0.12+16.04.20160126-0ubuntu1 <aucune>
2016-03-11 12:34:30 status unpacked account-plugin-flickr:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status unpacked account-plugin-flickr:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status half-configured account-plugin-flickr:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status installed account-plugin-flickr:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 configure libaccount-plugin-google:amd64 0.12+16.04.20160126-0ubuntu1 <aucune>
2016-03-11 12:34:30 status unpacked libaccount-plugin-google:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status half-configured libaccount-plugin-google:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:30 status installed libaccount-plugin-google:amd64 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:31 configure account-plugin-google:all 0.12+16.04.20160126-0ubuntu1 <aucune>
2016-03-11 12:34:31 status unpacked account-plugin-google:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:31 status unpacked account-plugin-google:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:31 status half-configured account-plugin-google:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:31 status installed account-plugin-google:all 0.12+16.04.20160126-0ubuntu1
2016-03-11 12:34:31 configure libappstream-glib8:amd64 0.5.10-0ubuntu4 <aucune>
2016-03-11 12:34:31 status unpacked libappstream-glib8:amd64 0.5.10-0ubuntu4
2016-03-11 12:34:31 status half-configured libappstream-glib8:amd64 0.5.10-0ubuntu4
2016-03-11 12:34:31 status installed libappstream-glib8:amd64 0.5.10-0ubuntu4
2016-03-11 12:34:31 configure appstream-util:amd64 0.5.10-0ubuntu4 <aucune>
2016-03-11 12:34:31 status unpacked appstream-util:amd64 0.5.10-0ubuntu4
2016-03-11 12:34:31 status half-configured appstream-util:amd64 0.5.10-0ubuntu4
2016-03-11 12:34:31 status installed appstream-util:amd64 0.5.10-0ubuntu4
2016-03-11 12:34:31 configure apt-doc:all 1.2.4 <aucune>
2016-03-11 12:34:31 status unpacked apt-doc:all 1.2.4
2016-03-11 12:34:31 status half-configured apt-doc:all 1.2.4
2016-03-11 12:34:32 status installed apt-doc:all 1.2.4
2016-03-11 12:34:32 configure archdetect-deb:amd64 1.114ubuntu3 <aucune>
2016-03-11 12:34:32 status unpacked archdetect-deb:amd64 1.114ubuntu3
2016-03-11 12:34:32 status half-configured archdetect-deb:amd64 1.114ubuntu3
2016-03-11 12:34:32 status installed archdetect-deb:amd64 1.114ubuntu3
2016-03-11 12:34:32 configure binutils:amd64 2.26-6ubuntu1 <aucune>
2016-03-11 12:34:32 status unpacked binutils:amd64 2.26-6ubuntu1
2016-03-11 12:34:32 status half-configured binutils:amd64 2.26-6ubuntu1
2016-03-11 12:34:32 status installed binutils:amd64 2.26-6ubuntu1
2016-03-11 12:34:32 configure binutils-dev:amd64 2.26-6ubuntu1 <aucune>
2016-03-11 12:34:32 status unpacked binutils-dev:amd64 2.26-6ubuntu1
2016-03-11 12:34:32 status half-configured binutils-dev:amd64 2.26-6ubuntu1
2016-03-11 12:34:32 status installed binutils-dev:amd64 2.26-6ubuntu1
2016-03-11 12:34:32 configure binutils-multiarch:amd64 2.26-6ubuntu1 <aucune>
2016-03-11 12:34:32 status unpacked binutils-multiarch:amd64 2.26-6ubuntu1
2016-03-11 12:34:32 status half-configured binutils-multiarch:amd64 2.26-6ubuntu1
2016-03-11 12:34:37 status installed binutils-multiarch:amd64 2.26-6ubuntu1
2016-03-11 12:34:37 configure binutils-multiarch-dev:amd64 2.26-6ubuntu1 <aucune>
2016-03-11 12:34:37 status unpacked binutils-multiarch-dev:amd64 2.26-6ubuntu1
2016-03-11 12:34:37 status half-configured binutils-multiarch-dev:amd64 2.26-6ubuntu1
2016-03-11 12:34:37 status installed binutils-multiarch-dev:amd64 2.26-6ubuntu1
2016-03-11 12:34:37 configure binutils-source:all 2.26-6ubuntu1 <aucune>
2016-03-11 12:34:37 status unpacked binutils-source:all 2.26-6ubuntu1
2016-03-11 12:34:37 status half-configured binutils-source:all 2.26-6ubuntu1
2016-03-11 12:34:38 status installed binutils-source:all 2.26-6ubuntu1
2016-03-11 12:34:38 configure libbluetooth3:amd64 5.37-0ubuntu5 <aucune>
2016-03-11 12:34:38 status unpacked libbluetooth3:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status half-configured libbluetooth3:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status installed libbluetooth3:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 configure libbluetooth-dev:amd64 5.37-0ubuntu5 <aucune>
2016-03-11 12:34:38 status unpacked libbluetooth-dev:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status half-configured libbluetooth-dev:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status installed libbluetooth-dev:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 configure bluez:amd64 5.37-0ubuntu5 <aucune>
2016-03-11 12:34:38 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:38 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:39 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:39 status unpacked bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:39 status half-configured bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 status installed bluez:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 configure libbluetooth3-dbg:amd64 5.37-0ubuntu5 <aucune>
2016-03-11 12:34:40 status unpacked libbluetooth3-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 status half-configured libbluetooth3-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 status installed libbluetooth3-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 configure bluez-dbg:amd64 5.37-0ubuntu5 <aucune>
2016-03-11 12:34:40 status unpacked bluez-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 status half-configured bluez-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 status installed bluez-dbg:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 configure bluez-cups:amd64 5.37-0ubuntu5 <aucune>
2016-03-11 12:34:40 status unpacked bluez-cups:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 status half-configured bluez-cups:amd64 5.37-0ubuntu5
2016-03-11 12:34:40 status installed bluez-cups:amd64 5.37-0ubuntu5
2016-03-11 12:34:41 configure bluez-obexd:amd64 5.37-0ubuntu5 <aucune>
2016-03-11 12:34:41 status unpacked bluez-obexd:amd64 5.37-0ubuntu5
2016-03-11 12:34:41 status half-configured bluez-obexd:amd64 5.37-0ubuntu5
2016-03-11 12:34:41 status installed bluez-obexd:amd64 5.37-0ubuntu5
2016-03-11 12:34:41 configure crash:amd64 7.1.4-1ubuntu2 <aucune>
2016-03-11 12:34:41 status unpacked crash:amd64 7.1.4-1ubuntu2
2016-03-11 12:34:41 status half-configured crash:amd64 7.1.4-1ubuntu2
2016-03-11 12:34:41 status installed crash:amd64 7.1.4-1ubuntu2
2016-03-11 12:34:41 configure deja-dup:amd64 34.1-1ubuntu3 <aucune>
2016-03-11 12:34:41 status unpacked deja-dup:amd64 34.1-1ubuntu3
2016-03-11 12:34:41 status unpacked deja-dup:amd64 34.1-1ubuntu3
2016-03-11 12:34:41 status half-configured deja-dup:amd64 34.1-1ubuntu3
2016-03-11 12:34:41 status installed deja-dup:amd64 34.1-1ubuntu3
2016-03-11 12:34:41 configure deja-dup-backend-cloudfiles:all 34.1-1ubuntu3 <aucune>
2016-03-11 12:34:41 status unpacked deja-dup-backend-cloudfiles:all 34.1-1ubuntu3
2016-03-11 12:34:41 status half-configured deja-dup-backend-cloudfiles:all 34.1-1ubuntu3
2016-03-11 12:34:41 status installed deja-dup-backend-cloudfiles:all 34.1-1ubuntu3
2016-03-11 12:34:41 configure deja-dup-backend-gvfs:all 34.1-1ubuntu3 <aucune>
2016-03-11 12:34:41 status unpacked deja-dup-backend-gvfs:all 34.1-1ubuntu3
2016-03-11 12:34:42 status half-configured deja-dup-backend-gvfs:all 34.1-1ubuntu3
2016-03-11 12:34:42 status installed deja-dup-backend-gvfs:all 34.1-1ubuntu3
2016-03-11 12:34:42 configure deja-dup-backend-s3:all 34.1-1ubuntu3 <aucune>
2016-03-11 12:34:42 status unpacked deja-dup-backend-s3:all 34.1-1ubuntu3
2016-03-11 12:34:42 status half-configured deja-dup-backend-s3:all 34.1-1ubuntu3
2016-03-11 12:34:42 status installed deja-dup-backend-s3:all 34.1-1ubuntu3
2016-03-11 12:34:42 configure eog:amd64 3.18.2-1ubuntu1 <aucune>
2016-03-11 12:34:42 status unpacked eog:amd64 3.18.2-1ubuntu1
2016-03-11 12:34:42 status half-configured eog:amd64 3.18.2-1ubuntu1
2016-03-11 12:34:42 status installed eog:amd64 3.18.2-1ubuntu1
2016-03-11 12:34:42 configure evince-common:all 3.18.2-1ubuntu4 <aucune>
2016-03-11 12:34:42 status unpacked evince-common:all 3.18.2-1ubuntu4
2016-03-11 12:34:42 status unpacked evince-common:all 3.18.2-1ubuntu4
2016-03-11 12:34:42 status unpacked evince-common:all 3.18.2-1ubuntu4
2016-03-11 12:34:42 status half-configured evince-common:all 3.18.2-1ubuntu4
2016-03-11 12:34:45 status installed evince-common:all 3.18.2-1ubuntu4
2016-03-11 12:34:45 configure libevdocument3-4:amd64 3.18.2-1ubuntu4 <aucune>
2016-03-11 12:34:45 status unpacked libevdocument3-4:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:45 status half-configured libevdocument3-4:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:46 status installed libevdocument3-4:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:46 configure libevview3-3:amd64 3.18.2-1ubuntu4 <aucune>
2016-03-11 12:34:46 status unpacked libevview3-3:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:46 status half-configured libevview3-3:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:46 status installed libevview3-3:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:46 configure evince:amd64 3.18.2-1ubuntu4 <aucune>
2016-03-11 12:34:46 status unpacked evince:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:46 status half-configured evince:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:46 status installed evince:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:46 configure extra-cmake-modules:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:34:46 status unpacked extra-cmake-modules:amd64 5.18.0-0ubuntu1
2016-03-11 12:34:46 status half-configured extra-cmake-modules:amd64 5.18.0-0ubuntu1
2016-03-11 12:34:46 status installed extra-cmake-modules:amd64 5.18.0-0ubuntu1
2016-03-11 12:34:46 configure libgtk2.0-common:all 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:46 status unpacked libgtk2.0-common:all 2.24.30-1ubuntu1
2016-03-11 12:34:46 status unpacked libgtk2.0-common:all 2.24.30-1ubuntu1
2016-03-11 12:34:46 status half-configured libgtk2.0-common:all 2.24.30-1ubuntu1
2016-03-11 12:34:46 status installed libgtk2.0-common:all 2.24.30-1ubuntu1
2016-03-11 12:34:46 configure libgtk2.0-0:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:46 status unpacked libgtk2.0-0:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:46 status half-configured libgtk2.0-0:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:47 status installed libgtk2.0-0:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:47 configure firefox:amd64 45.0+build2-0ubuntu1 <aucune>
2016-03-11 12:34:47 status unpacked firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:47 status unpacked firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:47 status unpacked firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:47 status unpacked firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:47 status unpacked firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:47 status half-configured firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:47 status installed firefox:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:47 configure firefox-dbg:amd64 45.0+build2-0ubuntu1 <aucune>
2016-03-11 12:34:47 status unpacked firefox-dbg:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:47 status half-configured firefox-dbg:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:48 status installed firefox-dbg:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:48 configure firefox-dev:amd64 45.0+build2-0ubuntu1 <aucune>
2016-03-11 12:34:48 status unpacked firefox-dev:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:48 status half-configured firefox-dev:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:48 status installed firefox-dev:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:48 configure libgtk2.0-bin:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:48 status unpacked libgtk2.0-bin:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:48 status half-configured libgtk2.0-bin:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:48 status installed libgtk2.0-bin:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:48 configure gtk2-engines-pixbuf:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:48 status unpacked gtk2-engines-pixbuf:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:48 status half-configured gtk2-engines-pixbuf:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:48 status installed gtk2-engines-pixbuf:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:48 configure libgtk2.0-0-dbg:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:48 status unpacked libgtk2.0-0-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:48 status half-configured libgtk2.0-0-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:48 status installed libgtk2.0-0-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 configure libgail18:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:49 status unpacked libgail18:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 status half-configured libgail18:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 status installed libgail18:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 configure libgail-dbg:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:49 status unpacked libgail-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 status half-configured libgail-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 status installed libgail-dbg:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 configure libgail-common:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:49 status unpacked libgail-common:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 status half-configured libgail-common:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 status installed libgail-common:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 configure gir1.2-gtk-2.0:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:49 status unpacked gir1.2-gtk-2.0:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 status half-configured gir1.2-gtk-2.0:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 status installed gir1.2-gtk-2.0:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:49 configure libgtk2.0-dev:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:49 status unpacked libgtk2.0-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:50 status half-configured libgtk2.0-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:50 status installed libgtk2.0-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:50 configure libgail-dev:amd64 2.24.30-1ubuntu1 <aucune>
2016-03-11 12:34:50 status unpacked libgail-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:50 status half-configured libgail-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:50 status installed libgail-dev:amd64 2.24.30-1ubuntu1
2016-03-11 12:34:50 configure firefox-locale-en:amd64 45.0+build2-0ubuntu1 <aucune>
2016-03-11 12:34:50 status unpacked firefox-locale-en:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:50 status half-configured firefox-locale-en:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:50 status installed firefox-locale-en:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:50 configure firefox-locale-fr:amd64 45.0+build2-0ubuntu1 <aucune>
2016-03-11 12:34:50 status unpacked firefox-locale-fr:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:50 status half-configured firefox-locale-fr:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:50 status installed firefox-locale-fr:amd64 45.0+build2-0ubuntu1
2016-03-11 12:34:51 configure gedit-common:all 3.18.3-0ubuntu4 <aucune>
2016-03-11 12:34:51 status unpacked gedit-common:all 3.18.3-0ubuntu4
2016-03-11 12:34:51 status half-configured gedit-common:all 3.18.3-0ubuntu4
2016-03-11 12:34:51 status installed gedit-common:all 3.18.3-0ubuntu4
2016-03-11 12:34:51 configure gedit:amd64 3.18.3-0ubuntu4 <aucune>
2016-03-11 12:34:51 status unpacked gedit:amd64 3.18.3-0ubuntu4
2016-03-11 12:34:51 status half-configured gedit:amd64 3.18.3-0ubuntu4
2016-03-11 12:34:51 status installed gedit:amd64 3.18.3-0ubuntu4
2016-03-11 12:34:51 configure gedit-dev:amd64 3.18.3-0ubuntu4 <aucune>
2016-03-11 12:34:51 status unpacked gedit-dev:amd64 3.18.3-0ubuntu4
2016-03-11 12:34:51 status half-configured gedit-dev:amd64 3.18.3-0ubuntu4
2016-03-11 12:34:51 status installed gedit-dev:amd64 3.18.3-0ubuntu4
2016-03-11 12:34:51 configure gir1.2-evince-3.0:amd64 3.18.2-1ubuntu4 <aucune>
2016-03-11 12:34:51 status unpacked gir1.2-evince-3.0:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:52 status half-configured gir1.2-evince-3.0:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:52 status installed gir1.2-evince-3.0:amd64 3.18.2-1ubuntu4
2016-03-11 12:34:52 configure gir1.2-gst-plugins-base-1.0:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:34:52 status unpacked gir1.2-gst-plugins-base-1.0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:52 status half-configured gir1.2-gst-plugins-base-1.0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:52 status installed gir1.2-gst-plugins-base-1.0:amd64 1.7.90-1ubuntu1
2016-03-11 12:34:52 configure mutter-common:all 3.18.3-0ubuntu1 <aucune>
2016-03-11 12:34:52 status unpacked mutter-common:all 3.18.3-0ubuntu1
2016-03-11 12:34:52 status half-configured mutter-common:all 3.18.3-0ubuntu1
2016-03-11 12:34:52 status installed mutter-common:all 3.18.3-0ubuntu1
2016-03-11 12:34:52 configure libmutter0g:amd64 3.18.3-0ubuntu1 <aucune>
2016-03-11 12:34:52 status unpacked libmutter0g:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:52 status half-configured libmutter0g:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:52 status installed libmutter0g:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:52 configure mutter:amd64 3.18.3-0ubuntu1 <aucune>
2016-03-11 12:34:52 status unpacked mutter:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:52 status half-configured mutter:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:53 status installed mutter:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:53 configure gir1.2-mutter-3.0:amd64 3.18.3-0ubuntu1 <aucune>
2016-03-11 12:34:53 status unpacked gir1.2-mutter-3.0:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:53 status half-configured gir1.2-mutter-3.0:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:53 status installed gir1.2-mutter-3.0:amd64 3.18.3-0ubuntu1
2016-03-11 12:34:53 configure libtotem0:amd64 3.18.1-1ubuntu4 <aucune>
2016-03-11 12:34:53 status unpacked libtotem0:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:53 status half-configured libtotem0:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:53 status installed libtotem0:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:53 configure totem-common:all 3.18.1-1ubuntu4 <aucune>
2016-03-11 12:34:53 status unpacked totem-common:all 3.18.1-1ubuntu4
2016-03-11 12:34:53 status half-configured totem-common:all 3.18.1-1ubuntu4
2016-03-11 12:34:53 status installed totem-common:all 3.18.1-1ubuntu4
2016-03-11 12:34:53 configure totem:amd64 3.18.1-1ubuntu4 <aucune>
2016-03-11 12:34:53 status unpacked totem:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:53 status half-configured totem:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:54 status installed totem:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:54 configure gir1.2-totem-1.0:amd64 3.18.1-1ubuntu4 <aucune>
2016-03-11 12:34:54 status unpacked gir1.2-totem-1.0:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:54 status half-configured gir1.2-totem-1.0:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:54 status installed gir1.2-totem-1.0:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:54 configure totem-plugins:amd64 3.18.1-1ubuntu4 <aucune>
2016-03-11 12:34:54 status unpacked totem-plugins:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:54 status half-configured totem-plugins:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:54 status installed totem-plugins:amd64 3.18.1-1ubuntu4
2016-03-11 12:34:54 configure libudisks2-0:amd64 2.1.7-1 <aucune>
2016-03-11 12:34:54 status unpacked libudisks2-0:amd64 2.1.7-1
2016-03-11 12:34:54 status half-configured libudisks2-0:amd64 2.1.7-1
2016-03-11 12:34:54 status installed libudisks2-0:amd64 2.1.7-1
2016-03-11 12:34:54 configure gir1.2-udisks-2.0:amd64 2.1.7-1 <aucune>
2016-03-11 12:34:54 status unpacked gir1.2-udisks-2.0:amd64 2.1.7-1
2016-03-11 12:34:55 status half-configured gir1.2-udisks-2.0:amd64 2.1.7-1
2016-03-11 12:34:55 status installed gir1.2-udisks-2.0:amd64 2.1.7-1
2016-03-11 12:34:55 configure gnome-calendar:amd64 3.19.91-0ubuntu3 <aucune>
2016-03-11 12:34:55 status unpacked gnome-calendar:amd64 3.19.91-0ubuntu3
2016-03-11 12:34:55 status half-configured gnome-calendar:amd64 3.19.91-0ubuntu3
2016-03-11 12:34:55 status installed gnome-calendar:amd64 3.19.91-0ubuntu3
2016-03-11 12:34:55 configure gnome-control-center-data:all 1:3.18.2-1ubuntu5 <aucune>
2016-03-11 12:34:55 status unpacked gnome-control-center-data:all 1:3.18.2-1ubuntu5
2016-03-11 12:34:55 status half-configured gnome-control-center-data:all 1:3.18.2-1ubuntu5
2016-03-11 12:34:55 status installed gnome-control-center-data:all 1:3.18.2-1ubuntu5
2016-03-11 12:34:55 configure gnome-control-center:amd64 1:3.18.2-1ubuntu5 <aucune>
2016-03-11 12:34:55 status unpacked gnome-control-center:amd64 1:3.18.2-1ubuntu5
2016-03-11 12:34:55 status half-configured gnome-control-center:amd64 1:3.18.2-1ubuntu5
2016-03-11 12:34:55 status installed gnome-control-center:amd64 1:3.18.2-1ubuntu5
2016-03-11 12:34:55 configure gnome-control-center-dev:all 1:3.18.2-1ubuntu5 <aucune>
2016-03-11 12:34:55 status unpacked gnome-control-center-dev:all 1:3.18.2-1ubuntu5
2016-03-11 12:34:56 status half-configured gnome-control-center-dev:all 1:3.18.2-1ubuntu5
2016-03-11 12:34:56 status installed gnome-control-center-dev:all 1:3.18.2-1ubuntu5
2016-03-11 12:34:56 configure gnome-shell-common:all 3.18.4-0ubuntu1 <aucune>
2016-03-11 12:34:56 status unpacked gnome-shell-common:all 3.18.4-0ubuntu1
2016-03-11 12:34:56 status half-configured gnome-shell-common:all 3.18.4-0ubuntu1
2016-03-11 12:34:56 status installed gnome-shell-common:all 3.18.4-0ubuntu1
2016-03-11 12:34:56 configure gnome-shell:amd64 3.18.4-0ubuntu1 <aucune>
2016-03-11 12:34:56 status unpacked gnome-shell:amd64 3.18.4-0ubuntu1
2016-03-11 12:34:56 status half-configured gnome-shell:amd64 3.18.4-0ubuntu1
2016-03-11 12:34:56 status installed gnome-shell:amd64 3.18.4-0ubuntu1
2016-03-11 12:34:56 configure gnome-software-common:all 3.19.92~git20160310.0c17ea0-0ubuntu1 <aucune>
2016-03-11 12:34:56 status unpacked gnome-software-common:all 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:34:56 status half-configured gnome-software-common:all 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:34:56 status installed gnome-software-common:all 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:34:56 configure gnome-software:amd64 3.19.92~git20160310.0c17ea0-0ubuntu1 <aucune>
2016-03-11 12:34:56 status unpacked gnome-software:amd64 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:34:56 status unpacked gnome-software:amd64 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:34:57 status half-configured gnome-software:amd64 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:34:57 status installed gnome-software:amd64 3.19.92~git20160310.0c17ea0-0ubuntu1
2016-03-11 12:34:57 configure libqt5core5a:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:34:57 status unpacked libqt5core5a:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 status half-configured libqt5core5a:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 status installed libqt5core5a:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 configure libqt5dbus5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:34:57 status unpacked libqt5dbus5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 status half-configured libqt5dbus5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 status installed libqt5dbus5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 configure libqt5network5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:34:57 status unpacked libqt5network5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 status half-configured libqt5network5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 status installed libqt5network5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 configure libqt5gui5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:34:57 status unpacked libqt5gui5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 status half-configured libqt5gui5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:57 status installed libqt5gui5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:58 configure libqt5widgets5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:34:58 status unpacked libqt5widgets5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:58 status half-configured libqt5widgets5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:58 status installed libqt5widgets5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:58 configure libqt5printsupport5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:34:58 status unpacked libqt5printsupport5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:58 status half-configured libqt5printsupport5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:58 status installed libqt5printsupport5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:34:58 configure gnuplot5-data:all 5.0.3+dfsg2-1 <aucune>
2016-03-11 12:34:58 status unpacked gnuplot5-data:all 5.0.3+dfsg2-1
2016-03-11 12:34:58 status half-configured gnuplot5-data:all 5.0.3+dfsg2-1
2016-03-11 12:34:58 status installed gnuplot5-data:all 5.0.3+dfsg2-1
2016-03-11 12:34:58 configure gnuplot5-qt:amd64 5.0.3+dfsg2-1 <aucune>
2016-03-11 12:34:58 status unpacked gnuplot5-qt:amd64 5.0.3+dfsg2-1
2016-03-11 12:34:58 status half-configured gnuplot5-qt:amd64 5.0.3+dfsg2-1
2016-03-11 12:34:59 status installed gnuplot5-qt:amd64 5.0.3+dfsg2-1
2016-03-11 12:34:59 configure gstreamer1.0-libav:amd64 1.7.90-1 <aucune>
2016-03-11 12:34:59 status unpacked gstreamer1.0-libav:amd64 1.7.90-1
2016-03-11 12:34:59 status half-configured gstreamer1.0-libav:amd64 1.7.90-1
2016-03-11 12:34:59 status installed gstreamer1.0-libav:amd64 1.7.90-1
2016-03-11 12:34:59 configure gstreamer1.0-tools:amd64 1.7.90-1 <aucune>
2016-03-11 12:34:59 status unpacked gstreamer1.0-tools:amd64 1.7.90-1
2016-03-11 12:35:00 status half-configured gstreamer1.0-tools:amd64 1.7.90-1
2016-03-11 12:35:00 status installed gstreamer1.0-tools:amd64 1.7.90-1
2016-03-11 12:35:00 configure gstreamer1.0-plugins-base-apps:amd64 1.7.90-1ubuntu1 <aucune>
2016-03-11 12:35:00 status unpacked gstreamer1.0-plugins-base-apps:amd64 1.7.90-1ubuntu1
2016-03-11 12:35:00 status half-configured gstreamer1.0-plugins-base-apps:amd64 1.7.90-1ubuntu1
2016-03-11 12:35:01 status installed gstreamer1.0-plugins-base-apps:amd64 1.7.90-1ubuntu1
2016-03-11 12:35:01 configure hunspell-en-ca:all 1:5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:01 status unpacked hunspell-en-ca:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:01 status half-configured hunspell-en-ca:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:01 status installed hunspell-en-ca:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:01 configure hunspell-en-us:all 20070829-6ubuntu3 <aucune>
2016-03-11 12:35:01 status unpacked hunspell-en-us:all 20070829-6ubuntu3
2016-03-11 12:35:01 status half-configured hunspell-en-us:all 20070829-6ubuntu3
2016-03-11 12:35:01 status installed hunspell-en-us:all 20070829-6ubuntu3
2016-03-11 12:35:01 configure hyphen-fr:all 1:5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:01 status unpacked hyphen-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:01 status half-configured hyphen-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:01 status installed hyphen-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:01 configure systemd-shim:amd64 9-1bzr4ubuntu1 <aucune>
2016-03-11 12:35:01 status unpacked systemd-shim:amd64 9-1bzr4ubuntu1
2016-03-11 12:35:01 status half-configured systemd-shim:amd64 9-1bzr4ubuntu1
2016-03-11 12:35:02 status installed systemd-shim:amd64 9-1bzr4ubuntu1
2016-03-11 12:35:02 configure indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu2 <aucune>
2016-03-11 12:35:02 status unpacked indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu2
2016-03-11 12:35:02 status unpacked indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu2
2016-03-11 12:35:02 status half-configured indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu2
2016-03-11 12:35:02 status installed indicator-datetime:amd64 15.10+16.04.20160129-0ubuntu2
2016-03-11 12:35:02 configure junit4:all 4.12-4ubuntu1 <aucune>
2016-03-11 12:35:02 status unpacked junit4:all 4.12-4ubuntu1
2016-03-11 12:35:02 status half-configured junit4:all 4.12-4ubuntu1
2016-03-11 12:35:02 status installed junit4:all 4.12-4ubuntu1
2016-03-11 12:35:02 configure libqt5sql5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:35:02 status unpacked libqt5sql5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:02 status half-configured libqt5sql5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:02 status installed libqt5sql5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:02 configure libqt5sql5-sqlite:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:35:02 status unpacked libqt5sql5-sqlite:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:03 status half-configured libqt5sql5-sqlite:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:03 status installed libqt5sql5-sqlite:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:03 configure libkf5activities5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:03 status unpacked libkf5activities5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:03 status half-configured libkf5activities5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:03 status installed libkf5activities5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:03 configure qml-module-org-kde-activities:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:03 status unpacked qml-module-org-kde-activities:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:03 status half-configured qml-module-org-kde-activities:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:03 status installed qml-module-org-kde-activities:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:03 configure libkf5dbusaddons-data:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:03 status unpacked libkf5dbusaddons-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:03 status half-configured libkf5dbusaddons-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:03 status installed libkf5dbusaddons-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:04 configure libkf5dbusaddons5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:04 status unpacked libkf5dbusaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 status half-configured libkf5dbusaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 status installed libkf5dbusaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 configure libkf5windowsystem-data:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:04 status unpacked libkf5windowsystem-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:04 status half-configured libkf5windowsystem-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:04 status installed libkf5windowsystem-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:04 configure libkf5windowsystem5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:04 status unpacked libkf5windowsystem5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 status half-configured libkf5windowsystem5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 status installed libkf5windowsystem5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 configure kactivities:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:04 status unpacked kactivities:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 status half-configured kactivities:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 status installed kactivities:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:04 configure kamera:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:04 status unpacked kamera:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:04 status half-configured kamera:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:04 status installed kamera:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:04 configure libqt5xml5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:35:04 status unpacked libqt5xml5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:04 status half-configured libqt5xml5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:05 status installed libqt5xml5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:05 configure kapman:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:05 status unpacked kapman:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 status half-configured kapman:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 status installed kapman:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 configure kde-runtime-data:all 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:05 status unpacked kde-runtime-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 status unpacked kde-runtime-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 status unpacked kde-runtime-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 status half-configured kde-runtime-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 status installed kde-runtime-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 configure plasma-scriptengine-javascript:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:05 status unpacked plasma-scriptengine-javascript:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 status half-configured plasma-scriptengine-javascript:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:05 status installed plasma-scriptengine-javascript:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:06 configure kde-runtime:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:06 status unpacked kde-runtime:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:06 status unpacked kde-runtime:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:06 status half-configured kde-runtime:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:06 status installed kde-runtime:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:06 configure kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1 <aucune>
2016-03-11 12:35:06 status unpacked kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:35:06 status unpacked kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:35:06 status unpacked kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:35:06 status triggers-pending systemd:amd64 229-2ubuntu1
2016-03-11 12:35:06 status triggers-pending ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:35:06 status unpacked kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:35:06 status unpacked kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:35:06 status half-configured kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:35:07 status installed kerneloops-daemon:amd64 0.12+git20140509-2ubuntu1
2016-03-11 12:35:07 configure kinit:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:07 status unpacked kinit:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:07 status half-configured kinit:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:07 status installed kinit:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:07 configure libkompareinterface5:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:07 status unpacked libkompareinterface5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:07 status half-configured libkompareinterface5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:07 status installed libkompareinterface5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:07 configure libkomparediff2-5:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:07 status unpacked libkomparediff2-5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:07 status half-configured libkomparediff2-5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:08 status installed libkomparediff2-5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:08 configure kpart5-kompare:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:08 status unpacked kpart5-kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:08 status half-configured kpart5-kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:08 status installed kpart5-kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:08 configure kompare:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:08 status unpacked kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:08 status half-configured kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:08 status installed kompare:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:08 configure kwayland-data:all 4:5.5.4-0ubuntu1 <aucune>
2016-03-11 12:35:08 status unpacked kwayland-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:35:08 status unpacked kwayland-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:35:08 status half-configured kwayland-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:35:08 status installed kwayland-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:35:08 configure libkf5waylandserver5:amd64 4:5.5.4-0ubuntu1 <aucune>
2016-03-11 12:35:08 status unpacked libkf5waylandserver5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:08 status half-configured libkf5waylandserver5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:08 status installed libkf5waylandserver5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:08 configure libkf5waylandclient5:amd64 4:5.5.4-0ubuntu1 <aucune>
2016-03-11 12:35:08 status unpacked libkf5waylandclient5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:08 status half-configured libkf5waylandclient5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:09 status installed libkf5waylandclient5:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:09 configure libkf5idletime5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:09 status unpacked libkf5idletime5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:09 status half-configured libkf5idletime5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:09 status installed libkf5idletime5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:09 configure kwayland-integration:amd64 4:5.5.4-0ubuntu1 <aucune>
2016-03-11 12:35:09 status unpacked kwayland-integration:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:09 status half-configured kwayland-integration:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:09 status installed kwayland-integration:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:09 configure libcommons-cli-java:all 1.3.1-3ubuntu1 <aucune>
2016-03-11 12:35:09 status unpacked libcommons-cli-java:all 1.3.1-3ubuntu1
2016-03-11 12:35:09 status half-configured libcommons-cli-java:all 1.3.1-3ubuntu1
2016-03-11 12:35:09 status installed libcommons-cli-java:all 1.3.1-3ubuntu1
2016-03-11 12:35:09 configure libcommons-lang-java:all 2.6-6ubuntu1 <aucune>
2016-03-11 12:35:09 status unpacked libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:35:09 status half-configured libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:35:09 status installed libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:35:09 configure libgraphite2-3:amd64 1.3.6-1ubuntu1 <aucune>
2016-03-11 12:35:09 status unpacked libgraphite2-3:amd64 1.3.6-1ubuntu1
2016-03-11 12:35:09 status half-configured libgraphite2-3:amd64 1.3.6-1ubuntu1
2016-03-11 12:35:09 status installed libgraphite2-3:amd64 1.3.6-1ubuntu1
2016-03-11 12:35:10 configure libgtk-3-bin:amd64 3.18.8-1ubuntu2 <aucune>
2016-03-11 12:35:10 status unpacked libgtk-3-bin:amd64 3.18.8-1ubuntu2
2016-03-11 12:35:10 status half-configured libgtk-3-bin:amd64 3.18.8-1ubuntu2
2016-03-11 12:35:10 status installed libgtk-3-bin:amd64 3.18.8-1ubuntu2
2016-03-11 12:35:10 configure libjasper1:amd64 1.900.1-debian1-2.4ubuntu1 <aucune>
2016-03-11 12:35:10 status unpacked libjasper1:amd64 1.900.1-debian1-2.4ubuntu1
2016-03-11 12:35:10 status half-configured libjasper1:amd64 1.900.1-debian1-2.4ubuntu1
2016-03-11 12:35:10 status installed libjasper1:amd64 1.900.1-debian1-2.4ubuntu1
2016-03-11 12:35:10 configure libjs-sphinxdoc:all 1.3.6-2ubuntu1 <aucune>
2016-03-11 12:35:10 status unpacked libjs-sphinxdoc:all 1.3.6-2ubuntu1
2016-03-11 12:35:10 status half-configured libjs-sphinxdoc:all 1.3.6-2ubuntu1
2016-03-11 12:35:10 status installed libjs-sphinxdoc:all 1.3.6-2ubuntu1
2016-03-11 12:35:10 configure libkcompactdisc4:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:10 status unpacked libkcompactdisc4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:10 status half-configured libkcompactdisc4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:10 status installed libkcompactdisc4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:10 configure libkcddb4:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:10 status unpacked libkcddb4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:10 status half-configured libkcddb4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:10 status installed libkcddb4:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:10 configure libqt5sql5-mysql:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:35:10 status unpacked libqt5sql5-mysql:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:10 status half-configured libqt5sql5-mysql:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:11 status installed libqt5sql5-mysql:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:11 configure akonadi-backend-mysql:all 4:15.12.1-0ubuntu2 <aucune>
2016-03-11 12:35:11 status unpacked akonadi-backend-mysql:all 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 status unpacked akonadi-backend-mysql:all 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 status unpacked akonadi-backend-mysql:all 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 status unpacked akonadi-backend-mysql:all 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 status half-configured akonadi-backend-mysql:all 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 status installed akonadi-backend-mysql:all 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 configure libkf5akonadiprivate5:amd64 4:15.12.1-0ubuntu2 <aucune>
2016-03-11 12:35:11 status unpacked libkf5akonadiprivate5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 status half-configured libkf5akonadiprivate5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 status installed libkf5akonadiprivate5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:11 configure akonadi-server:amd64 4:15.12.1-0ubuntu2 <aucune>
2016-03-11 12:35:11 status unpacked akonadi-server:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:12 status unpacked akonadi-server:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:12 status half-configured akonadi-server:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:12 status installed akonadi-server:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:12 configure libkf5attica5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:12 status unpacked libkf5attica5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:12 status half-configured libkf5attica5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:12 status installed libkf5attica5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:12 configure libkf5calendarcore5:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:12 status unpacked libkf5calendarcore5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:12 status half-configured libkf5calendarcore5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:12 status installed libkf5calendarcore5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:12 configure libkf5calendarutils5:amd64 4:15.12.1-0ubuntu2 <aucune>
2016-03-11 12:35:12 status unpacked libkf5calendarutils5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:12 status half-configured libkf5calendarutils5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:12 status installed libkf5calendarutils5:amd64 4:15.12.1-0ubuntu2
2016-03-11 12:35:12 configure libkf5contacts-data:all 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:12 status unpacked libkf5contacts-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:35:12 status half-configured libkf5contacts-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:35:12 status installed libkf5contacts-data:all 4:15.12.1-0ubuntu1
2016-03-11 12:35:12 configure libkf5contacts5:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:12 status unpacked libkf5contacts5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:13 status half-configured libkf5contacts5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:13 status installed libkf5contacts5:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:13 configure libkf5dbusaddons-bin:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:13 status unpacked libkf5dbusaddons-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:13 status half-configured libkf5dbusaddons-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:13 status installed libkf5dbusaddons-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:13 configure libkf5dnssd-data:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:13 status unpacked libkf5dnssd-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:13 status half-configured libkf5dnssd-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:13 status installed libkf5dnssd-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:13 configure libkf5dnssd5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:13 status unpacked libkf5dnssd5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:13 status half-configured libkf5dnssd5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:13 status installed libkf5dnssd5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:13 configure libkf5gapi-data:all 5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:13 status unpacked libkf5gapi-data:all 5.1.0-1ubuntu1
2016-03-11 12:35:13 status unpacked libkf5gapi-data:all 5.1.0-1ubuntu1
2016-03-11 12:35:13 status half-configured libkf5gapi-data:all 5.1.0-1ubuntu1
2016-03-11 12:35:13 status installed libkf5gapi-data:all 5.1.0-1ubuntu1
2016-03-11 12:35:14 configure libkf5gapicore5:amd64 5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:14 status unpacked libkf5gapicore5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 status half-configured libkf5gapicore5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 status installed libkf5gapicore5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 configure libkf5gapicontacts5:amd64 5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:14 status unpacked libkf5gapicontacts5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 status half-configured libkf5gapicontacts5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 status installed libkf5gapicontacts5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 configure libkf5gapitasks5:amd64 5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:14 status unpacked libkf5gapitasks5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 status half-configured libkf5gapitasks5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 status installed libkf5gapitasks5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 configure libkf5gapicalendar5:amd64 5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:14 status unpacked libkf5gapicalendar5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:14 status half-configured libkf5gapicalendar5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:15 status installed libkf5gapicalendar5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:15 configure libkf5gapidrive5:amd64 5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:15 status unpacked libkf5gapidrive5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:15 status half-configured libkf5gapidrive5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:15 status installed libkf5gapidrive5:amd64 5.1.0-1ubuntu1
2016-03-11 12:35:15 configure libkf5gpgmepp5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:15 status unpacked libkf5gpgmepp5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:15 status half-configured libkf5gpgmepp5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:15 status installed libkf5gpgmepp5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:15 configure libkf5guiaddons5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:15 status unpacked libkf5guiaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:15 status half-configured libkf5guiaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:15 status installed libkf5guiaddons5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:15 configure libkf5holidays-data:all 15.12.1-1ubuntu1 <aucune>
2016-03-11 12:35:15 status unpacked libkf5holidays-data:all 15.12.1-1ubuntu1
2016-03-11 12:35:15 status half-configured libkf5holidays-data:all 15.12.1-1ubuntu1
2016-03-11 12:35:15 status installed libkf5holidays-data:all 15.12.1-1ubuntu1
2016-03-11 12:35:15 configure libkf5holidays5:amd64 15.12.1-1ubuntu1 <aucune>
2016-03-11 12:35:15 status unpacked libkf5holidays5:amd64 15.12.1-1ubuntu1
2016-03-11 12:35:16 status half-configured libkf5holidays5:amd64 15.12.1-1ubuntu1
2016-03-11 12:35:16 status installed libkf5holidays5:amd64 15.12.1-1ubuntu1
2016-03-11 12:35:16 configure libkf5mime5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:16 status unpacked libkf5mime5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:16 status half-configured libkf5mime5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:16 status installed libkf5mime5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:16 configure libkf5imap5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:16 status unpacked libkf5imap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:16 status half-configured libkf5imap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:16 status installed libkf5imap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:16 configure libkf5itemmodels5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:16 status unpacked libkf5itemmodels5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:16 status half-configured libkf5itemmodels5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:16 status installed libkf5itemmodels5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:16 configure libkf5itemviews-data:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:16 status unpacked libkf5itemviews-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:16 status half-configured libkf5itemviews-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:16 status installed libkf5itemviews-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:16 configure libkf5itemviews5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:16 status unpacked libkf5itemviews5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:17 status half-configured libkf5itemviews5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:17 status installed libkf5itemviews5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:17 configure libkf5js5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:17 status unpacked libkf5js5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:17 status half-configured libkf5js5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:17 status installed libkf5js5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:17 configure libkf5kontactinterface-data:all 15.12.1-1ubuntu1 <aucune>
2016-03-11 12:35:17 status unpacked libkf5kontactinterface-data:all 15.12.1-1ubuntu1
2016-03-11 12:35:17 status half-configured libkf5kontactinterface-data:all 15.12.1-1ubuntu1
2016-03-11 12:35:17 status installed libkf5kontactinterface-data:all 15.12.1-1ubuntu1
2016-03-11 12:35:17 configure libkf5kontactinterface5:amd64 15.12.1-1ubuntu1 <aucune>
2016-03-11 12:35:17 status unpacked libkf5kontactinterface5:amd64 15.12.1-1ubuntu1
2016-03-11 12:35:17 status half-configured libkf5kontactinterface5:amd64 15.12.1-1ubuntu1
2016-03-11 12:35:17 status installed libkf5kontactinterface5:amd64 15.12.1-1ubuntu1
2016-03-11 12:35:17 configure libkf5ldap5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:17 status unpacked libkf5ldap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:17 status half-configured libkf5ldap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:17 status installed libkf5ldap5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:17 configure libkf5mbox5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:17 status unpacked libkf5mbox5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:17 status half-configured libkf5mbox5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:18 status installed libkf5mbox5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:18 configure libkf5solid5-data:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:18 status unpacked libkf5solid5-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:18 status half-configured libkf5solid5-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:18 status installed libkf5solid5-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:18 configure libkf5solid5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:18 status unpacked libkf5solid5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:18 status half-configured libkf5solid5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:18 status installed libkf5solid5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:18 configure libkf5syndication5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:18 status unpacked libkf5syndication5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:18 status half-configured libkf5syndication5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:18 status installed libkf5syndication5:amd64 15.12.1-0ubuntu1
2016-03-11 12:35:18 configure libkf5threadweaver5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:18 status unpacked libkf5threadweaver5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:18 status half-configured libkf5threadweaver5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:18 status installed libkf5threadweaver5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:19 configure libkf5webkit5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:19 status unpacked libkf5webkit5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:19 status half-configured libkf5webkit5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:19 status installed libkf5webkit5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:19 configure libkf5xmlrpcclient-data:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:19 status unpacked libkf5xmlrpcclient-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:19 status half-configured libkf5xmlrpcclient-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:19 status installed libkf5xmlrpcclient-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:19 configure libkf5xmlrpcclient5:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:19 status unpacked libkf5xmlrpcclient5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:19 status half-configured libkf5xmlrpcclient5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:19 status installed libkf5xmlrpcclient5:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:19 configure libkolabxml1v5:amd64 1.1.2-0ubuntu2 <aucune>
2016-03-11 12:35:19 status unpacked libkolabxml1v5:amd64 1.1.2-0ubuntu2
2016-03-11 12:35:19 status half-configured libkolabxml1v5:amd64 1.1.2-0ubuntu2
2016-03-11 12:35:19 status installed libkolabxml1v5:amd64 1.1.2-0ubuntu2
2016-03-11 12:35:19 configure libllvm3.8:i386 1:3.8-2ubuntu1 <aucune>
2016-03-11 12:35:19 status unpacked libllvm3.8:i386 1:3.8-2ubuntu1
2016-03-11 12:35:19 status half-configured libllvm3.8:i386 1:3.8-2ubuntu1
2016-03-11 12:35:19 status installed libllvm3.8:i386 1:3.8-2ubuntu1
2016-03-11 12:35:19 configure libllvm3.8:amd64 1:3.8-2ubuntu1 <aucune>
2016-03-11 12:35:19 status unpacked libllvm3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:19 status half-configured libllvm3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:20 status installed libllvm3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:20 configure libpurple-bin:all 1:2.10.12-0ubuntu5 <aucune>
2016-03-11 12:35:20 status unpacked libpurple-bin:all 1:2.10.12-0ubuntu5
2016-03-11 12:35:20 status half-configured libpurple-bin:all 1:2.10.12-0ubuntu5
2016-03-11 12:35:20 status installed libpurple-bin:all 1:2.10.12-0ubuntu5
2016-03-11 12:35:20 configure libqmobipocket1:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:35:20 status unpacked libqmobipocket1:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:20 status half-configured libqmobipocket1:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:20 status installed libqmobipocket1:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:35:20 configure libqt5opengl5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:35:20 status unpacked libqt5opengl5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:20 status half-configured libqt5opengl5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:20 status installed libqt5opengl5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:20 configure libqt5test5:amd64 5.5.1+dfsg-15ubuntu1 <aucune>
2016-03-11 12:35:20 status unpacked libqt5test5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:20 status half-configured libqt5test5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:20 status installed libqt5test5:amd64 5.5.1+dfsg-15ubuntu1
2016-03-11 12:35:20 configure libvdpau-va-gl1:amd64 0.3.6-1 <aucune>
2016-03-11 12:35:20 status unpacked libvdpau-va-gl1:amd64 0.3.6-1
2016-03-11 12:35:20 status unpacked libvdpau-va-gl1:amd64 0.3.6-1
2016-03-11 12:35:20 status half-configured libvdpau-va-gl1:amd64 0.3.6-1
2016-03-11 12:35:21 status installed libvdpau-va-gl1:amd64 0.3.6-1
2016-03-11 12:35:21 configure libyelp0:amd64 3.18.1-1ubuntu3 <aucune>
2016-03-11 12:35:21 status unpacked libyelp0:amd64 3.18.1-1ubuntu3
2016-03-11 12:35:21 status half-configured libyelp0:amd64 3.18.1-1ubuntu3
2016-03-11 12:35:21 status installed libyelp0:amd64 3.18.1-1ubuntu3
2016-03-11 12:35:21 configure yelp:amd64 3.18.1-1ubuntu3 <aucune>
2016-03-11 12:35:21 status unpacked yelp:amd64 3.18.1-1ubuntu3
2016-03-11 12:35:21 status half-configured yelp:amd64 3.18.1-1ubuntu3
2016-03-11 12:35:21 status installed yelp:amd64 3.18.1-1ubuntu3
2016-03-11 12:35:21 configure linux-crashdump:amd64 4.4.0.11.12 <aucune>
2016-03-11 12:35:21 status unpacked linux-crashdump:amd64 4.4.0.11.12
2016-03-11 12:35:21 status half-configured linux-crashdump:amd64 4.4.0.11.12
2016-03-11 12:35:21 status installed linux-crashdump:amd64 4.4.0.11.12
2016-03-11 12:35:21 configure linux-libc-dev:amd64 4.4.0-11.26 <aucune>
2016-03-11 12:35:21 status unpacked linux-libc-dev:amd64 4.4.0-11.26
2016-03-11 12:35:21 status half-configured linux-libc-dev:amd64 4.4.0-11.26
2016-03-11 12:35:22 status installed linux-libc-dev:amd64 4.4.0-11.26
2016-03-11 12:35:22 configure linux-libc-dev:i386 4.4.0-11.26 <aucune>
2016-03-11 12:35:22 status unpacked linux-libc-dev:i386 4.4.0-11.26
2016-03-11 12:35:22 status half-configured linux-libc-dev:i386 4.4.0-11.26
2016-03-11 12:35:22 status installed linux-libc-dev:i386 4.4.0-11.26
2016-03-11 12:35:22 configure llvm-3.8-runtime:amd64 1:3.8-2ubuntu1 <aucune>
2016-03-11 12:35:22 status unpacked llvm-3.8-runtime:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 status half-configured llvm-3.8-runtime:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 status installed llvm-3.8-runtime:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 configure llvm-3.8:amd64 1:3.8-2ubuntu1 <aucune>
2016-03-11 12:35:22 status unpacked llvm-3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 status half-configured llvm-3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 status installed llvm-3.8:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 configure llvm-3.8-dev:amd64 1:3.8-2ubuntu1 <aucune>
2016-03-11 12:35:22 status unpacked llvm-3.8-dev:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 status half-configured llvm-3.8-dev:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 status installed llvm-3.8-dev:amd64 1:3.8-2ubuntu1
2016-03-11 12:35:22 configure mythes-en-us:all 1:5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:22 status unpacked mythes-en-us:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:23 status half-configured mythes-en-us:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:23 status installed mythes-en-us:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:23 configure mythes-fr:all 1:5.1.0-1ubuntu1 <aucune>
2016-03-11 12:35:23 status unpacked mythes-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:23 status half-configured mythes-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:23 status installed mythes-fr:all 1:5.1.0-1ubuntu1
2016-03-11 12:35:23 configure openoffice.org-hyphenation:all 0.9 <aucune>
2016-03-11 12:35:23 status unpacked openoffice.org-hyphenation:all 0.9
2016-03-11 12:35:23 status half-configured openoffice.org-hyphenation:all 0.9
2016-03-11 12:35:23 status installed openoffice.org-hyphenation:all 0.9
2016-03-11 12:35:23 configure python-futurist:all 0.13.0-0ubuntu1 <aucune>
2016-03-11 12:35:23 status unpacked python-futurist:all 0.13.0-0ubuntu1
2016-03-11 12:35:23 status half-configured python-futurist:all 0.13.0-0ubuntu1
2016-03-11 12:35:23 status installed python-futurist:all 0.13.0-0ubuntu1
2016-03-11 12:35:23 configure python-kombu:all 3.0.33-1ubuntu2 <aucune>
2016-03-11 12:35:23 status unpacked python-kombu:all 3.0.33-1ubuntu2
2016-03-11 12:35:23 status half-configured python-kombu:all 3.0.33-1ubuntu2
2016-03-11 12:35:24 status installed python-kombu:all 3.0.33-1ubuntu2
2016-03-11 12:35:24 configure python-oslo.config:all 1:3.9.0-1 <aucune>
2016-03-11 12:35:24 status unpacked python-oslo.config:all 1:3.9.0-1
2016-03-11 12:35:24 status half-configured python-oslo.config:all 1:3.9.0-1
2016-03-11 12:35:24 status installed python-oslo.config:all 1:3.9.0-1
2016-03-11 12:35:24 configure python-oslo.i18n:all 3.4.0-1 <aucune>
2016-03-11 12:35:24 status unpacked python-oslo.i18n:all 3.4.0-1
2016-03-11 12:35:24 status half-configured python-oslo.i18n:all 3.4.0-1
2016-03-11 12:35:25 status installed python-oslo.i18n:all 3.4.0-1
2016-03-11 12:35:25 configure python-oslo.utils:all 3.7.0-0ubuntu1 <aucune>
2016-03-11 12:35:25 status unpacked python-oslo.utils:all 3.7.0-0ubuntu1
2016-03-11 12:35:25 status half-configured python-oslo.utils:all 3.7.0-0ubuntu1
2016-03-11 12:35:25 status installed python-oslo.utils:all 3.7.0-0ubuntu1
2016-03-11 12:35:25 configure python-oslo.concurrency:all 3.6.0-0ubuntu1 <aucune>
2016-03-11 12:35:25 status unpacked python-oslo.concurrency:all 3.6.0-0ubuntu1
2016-03-11 12:35:25 status half-configured python-oslo.concurrency:all 3.6.0-0ubuntu1
2016-03-11 12:35:25 status installed python-oslo.concurrency:all 3.6.0-0ubuntu1
2016-03-11 12:35:25 configure python-oslo.context:all 2.2.0-1 <aucune>
2016-03-11 12:35:25 status unpacked python-oslo.context:all 2.2.0-1
2016-03-11 12:35:25 status half-configured python-oslo.context:all 2.2.0-1
2016-03-11 12:35:26 status installed python-oslo.context:all 2.2.0-1
2016-03-11 12:35:26 configure python-oslo.db:all 4.6.0-1ubuntu1 <aucune>
2016-03-11 12:35:26 status unpacked python-oslo.db:all 4.6.0-1ubuntu1
2016-03-11 12:35:26 status half-configured python-oslo.db:all 4.6.0-1ubuntu1
2016-03-11 12:35:26 status installed python-oslo.db:all 4.6.0-1ubuntu1
2016-03-11 12:35:26 configure python-oslo.serialization:all 2.4.0-1 <aucune>
2016-03-11 12:35:26 status unpacked python-oslo.serialization:all 2.4.0-1
2016-03-11 12:35:26 status half-configured python-oslo.serialization:all 2.4.0-1
2016-03-11 12:35:26 status installed python-oslo.serialization:all 2.4.0-1
2016-03-11 12:35:26 configure python-oslo.log:all 3.2.0-1 <aucune>
2016-03-11 12:35:26 status unpacked python-oslo.log:all 3.2.0-1
2016-03-11 12:35:26 status half-configured python-oslo.log:all 3.2.0-1
2016-03-11 12:35:26 status installed python-oslo.log:all 3.2.0-1
2016-03-11 12:35:27 configure python-oslo.middleware:all 3.7.0-1 <aucune>
2016-03-11 12:35:27 status unpacked python-oslo.middleware:all 3.7.0-1
2016-03-11 12:35:27 status half-configured python-oslo.middleware:all 3.7.0-1
2016-03-11 12:35:27 status installed python-oslo.middleware:all 3.7.0-1
2016-03-11 12:35:27 configure python-oslo.policy:all 1.5.0-0ubuntu1 <aucune>
2016-03-11 12:35:27 status unpacked python-oslo.policy:all 1.5.0-0ubuntu1
2016-03-11 12:35:27 status half-configured python-oslo.policy:all 1.5.0-0ubuntu1
2016-03-11 12:35:27 status installed python-oslo.policy:all 1.5.0-0ubuntu1
2016-03-11 12:35:27 configure python-oslo.reports:all 1.6.0-1 <aucune>
2016-03-11 12:35:27 status unpacked python-oslo.reports:all 1.6.0-1
2016-03-11 12:35:27 status half-configured python-oslo.reports:all 1.6.0-1
2016-03-11 12:35:27 status installed python-oslo.reports:all 1.6.0-1
2016-03-11 12:35:27 configure python-oslo.rootwrap:all 4.1.0-1 <aucune>
2016-03-11 12:35:27 status unpacked python-oslo.rootwrap:all 4.1.0-1
2016-03-11 12:35:28 status half-configured python-oslo.rootwrap:all 4.1.0-1
2016-03-11 12:35:28 status installed python-oslo.rootwrap:all 4.1.0-1
2016-03-11 12:35:28 configure python-oslo.service:all 1.3.0-1ubuntu1 <aucune>
2016-03-11 12:35:28 status unpacked python-oslo.service:all 1.3.0-1ubuntu1
2016-03-11 12:35:28 status half-configured python-oslo.service:all 1.3.0-1ubuntu1
2016-03-11 12:35:28 status installed python-oslo.service:all 1.3.0-1ubuntu1
2016-03-11 12:35:28 configure python-unittest2:all 1.1.0-6.1 <aucune>
2016-03-11 12:35:28 status unpacked python-unittest2:all 1.1.0-6.1
2016-03-11 12:35:28 status half-configured python-unittest2:all 1.1.0-6.1
2016-03-11 12:35:28 status installed python-unittest2:all 1.1.0-6.1
2016-03-11 12:35:28 configure python-waitress:all 0.8.10-1 <aucune>
2016-03-11 12:35:28 status unpacked python-waitress:all 0.8.10-1
2016-03-11 12:35:29 status half-configured python-waitress:all 0.8.10-1
2016-03-11 12:35:29 status installed python-waitress:all 0.8.10-1
2016-03-11 12:35:29 configure python3-cupshelpers:all 1.5.7+20160212-0ubuntu2 <aucune>
2016-03-11 12:35:29 status unpacked python3-cupshelpers:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:29 status unpacked python3-cupshelpers:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:29 status half-configured python3-cupshelpers:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:29 status installed python3-cupshelpers:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:29 configure python3-pycurl:amd64 7.43.0-1ubuntu1 <aucune>
2016-03-11 12:35:29 status unpacked python3-pycurl:amd64 7.43.0-1ubuntu1
2016-03-11 12:35:29 status half-configured python3-pycurl:amd64 7.43.0-1ubuntu1
2016-03-11 12:35:29 status installed python3-pycurl:amd64 7.43.0-1ubuntu1
2016-03-11 12:35:29 configure python3-software-properties:all 0.96.18 <aucune>
2016-03-11 12:35:29 status unpacked python3-software-properties:all 0.96.18
2016-03-11 12:35:30 status half-configured python3-software-properties:all 0.96.18
2016-03-11 12:35:30 status installed python3-software-properties:all 0.96.18
2016-03-11 12:35:30 configure software-properties-common:all 0.96.18 <aucune>
2016-03-11 12:35:30 status unpacked software-properties-common:all 0.96.18
2016-03-11 12:35:31 status unpacked software-properties-common:all 0.96.18
2016-03-11 12:35:31 status half-configured software-properties-common:all 0.96.18
2016-03-11 12:35:31 status installed software-properties-common:all 0.96.18
2016-03-11 12:35:31 configure software-properties-gtk:all 0.96.18 <aucune>
2016-03-11 12:35:31 status unpacked software-properties-gtk:all 0.96.18
2016-03-11 12:35:31 status half-configured software-properties-gtk:all 0.96.18
2016-03-11 12:35:31 status installed software-properties-gtk:all 0.96.18
2016-03-11 12:35:31 configure qml-module-org-kde-extensionplugin:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:31 status unpacked qml-module-org-kde-extensionplugin:all 5.18.0-0ubuntu1
2016-03-11 12:35:31 status half-configured qml-module-org-kde-extensionplugin:all 5.18.0-0ubuntu1
2016-03-11 12:35:31 status installed qml-module-org-kde-extensionplugin:all 5.18.0-0ubuntu1
2016-03-11 12:35:32 configure qml-module-org-kde-solid:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:32 status unpacked qml-module-org-kde-solid:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:32 status half-configured qml-module-org-kde-solid:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:32 status installed qml-module-org-kde-solid:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:32 configure qtdeclarative5-kf5solid:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:32 status unpacked qtdeclarative5-kf5solid:all 5.18.0-0ubuntu1
2016-03-11 12:35:32 status half-configured qtdeclarative5-kf5solid:all 5.18.0-0ubuntu1
2016-03-11 12:35:32 status installed qtdeclarative5-kf5solid:all 5.18.0-0ubuntu1
2016-03-11 12:35:32 configure oxideqt-codecs-extra:amd64 1.13.6-0ubuntu1 <aucune>
2016-03-11 12:35:32 status unpacked oxideqt-codecs-extra:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:32 status half-configured oxideqt-codecs-extra:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:32 status installed oxideqt-codecs-extra:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:32 configure simple-scan:amd64 3.19.91-0ubuntu1 <aucune>
2016-03-11 12:35:32 status unpacked simple-scan:amd64 3.19.91-0ubuntu1
2016-03-11 12:35:32 status half-configured simple-scan:amd64 3.19.91-0ubuntu1
2016-03-11 12:35:32 status installed simple-scan:amd64 3.19.91-0ubuntu1
2016-03-11 12:35:32 configure ssh-askpass-gnome:amd64 1:7.2p1-1 <aucune>
2016-03-11 12:35:32 status unpacked ssh-askpass-gnome:amd64 1:7.2p1-1
2016-03-11 12:35:32 status half-configured ssh-askpass-gnome:amd64 1:7.2p1-1
2016-03-11 12:35:33 status installed ssh-askpass-gnome:amd64 1:7.2p1-1
2016-03-11 12:35:33 configure system-config-printer-common:all 1.5.7+20160212-0ubuntu2 <aucune>
2016-03-11 12:35:33 status unpacked system-config-printer-common:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status unpacked system-config-printer-common:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status unpacked system-config-printer-common:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status half-configured system-config-printer-common:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status installed system-config-printer-common:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 configure system-config-printer-gnome:all 1.5.7+20160212-0ubuntu2 <aucune>
2016-03-11 12:35:33 status unpacked system-config-printer-gnome:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status unpacked system-config-printer-gnome:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status half-configured system-config-printer-gnome:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status installed system-config-printer-gnome:all 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 configure system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu2 <aucune>
2016-03-11 12:35:33 status unpacked system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status half-configured system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 status installed system-config-printer-udev:amd64 1.5.7+20160212-0ubuntu2
2016-03-11 12:35:33 configure thunderbird:amd64 1:38.6.0+build1-0ubuntu1 <aucune>
2016-03-11 12:35:33 status unpacked thunderbird:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:33 status unpacked thunderbird:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status unpacked thunderbird:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status unpacked thunderbird:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status half-configured thunderbird:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status installed thunderbird:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 configure thunderbird-locale-fr:amd64 1:38.6.0+build1-0ubuntu1 <aucune>
2016-03-11 12:35:34 status unpacked thunderbird-locale-fr:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status half-configured thunderbird-locale-fr:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status installed thunderbird-locale-fr:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 configure thunderbird-locale-en:amd64 1:38.6.0+build1-0ubuntu1 <aucune>
2016-03-11 12:35:34 status unpacked thunderbird-locale-en:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status half-configured thunderbird-locale-en:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status installed thunderbird-locale-en:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 configure thunderbird-gnome-support:amd64 1:38.6.0+build1-0ubuntu1 <aucune>
2016-03-11 12:35:34 status unpacked thunderbird-gnome-support:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status half-configured thunderbird-gnome-support:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status installed thunderbird-gnome-support:amd64 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 configure thunderbird-locale-en-gb:all 1:38.6.0+build1-0ubuntu1 <aucune>
2016-03-11 12:35:34 status unpacked thunderbird-locale-en-gb:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status half-configured thunderbird-locale-en-gb:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status installed thunderbird-locale-en-gb:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 configure thunderbird-locale-en-us:all 1:38.6.0+build1-0ubuntu1 <aucune>
2016-03-11 12:35:34 status unpacked thunderbird-locale-en-us:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status half-configured thunderbird-locale-en-us:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:34 status installed thunderbird-locale-en-us:all 1:38.6.0+build1-0ubuntu1
2016-03-11 12:35:35 configure ttf-ubuntu-font-family:all 1:0.83-0ubuntu2 <aucune>
2016-03-11 12:35:35 status unpacked ttf-ubuntu-font-family:all 1:0.83-0ubuntu2
2016-03-11 12:35:35 status half-configured ttf-ubuntu-font-family:all 1:0.83-0ubuntu2
2016-03-11 12:35:35 status installed ttf-ubuntu-font-family:all 1:0.83-0ubuntu2
2016-03-11 12:35:35 configure ubuntu-gnome-wallpapers-utopic:all 16.04.1 <aucune>
2016-03-11 12:35:35 status unpacked ubuntu-gnome-wallpapers-utopic:all 16.04.1
2016-03-11 12:35:35 status half-configured ubuntu-gnome-wallpapers-utopic:all 16.04.1
2016-03-11 12:35:35 status installed ubuntu-gnome-wallpapers-utopic:all 16.04.1
2016-03-11 12:35:35 configure ubuntu-restricted-extras:amd64 65 <aucune>
2016-03-11 12:35:35 status unpacked ubuntu-restricted-extras:amd64 65
2016-03-11 12:35:35 status half-configured ubuntu-restricted-extras:amd64 65
2016-03-11 12:35:35 status installed ubuntu-restricted-extras:amd64 65
2016-03-11 12:35:35 configure ubuntu-wallpapers-wily:all 16.04.0-0ubuntu1 <aucune>
2016-03-11 12:35:35 status unpacked ubuntu-wallpapers-wily:all 16.04.0-0ubuntu1
2016-03-11 12:35:35 status half-configured ubuntu-wallpapers-wily:all 16.04.0-0ubuntu1
2016-03-11 12:35:35 status installed ubuntu-wallpapers-wily:all 16.04.0-0ubuntu1
2016-03-11 12:35:35 configure ubuntu-wallpapers:all 16.04.0-0ubuntu1 <aucune>
2016-03-11 12:35:35 status unpacked ubuntu-wallpapers:all 16.04.0-0ubuntu1
2016-03-11 12:35:35 status half-configured ubuntu-wallpapers:all 16.04.0-0ubuntu1
2016-03-11 12:35:35 status installed ubuntu-wallpapers:all 16.04.0-0ubuntu1
2016-03-11 12:35:36 configure udisks2:amd64 2.1.7-1 <aucune>
2016-03-11 12:35:36 status unpacked udisks2:amd64 2.1.7-1
2016-03-11 12:35:36 status unpacked udisks2:amd64 2.1.7-1
2016-03-11 12:35:36 status half-configured udisks2:amd64 2.1.7-1
2016-03-11 12:35:36 status installed udisks2:amd64 2.1.7-1
2016-03-11 12:35:36 configure virtualbox-dkms:all 5.0.16-dfsg-2 <aucune>
2016-03-11 12:35:36 status unpacked virtualbox-dkms:all 5.0.16-dfsg-2
2016-03-11 12:35:36 status half-configured virtualbox-dkms:all 5.0.16-dfsg-2
2016-03-11 12:35:44 status installed virtualbox-dkms:all 5.0.16-dfsg-2
2016-03-11 12:35:44 configure virtualbox:amd64 5.0.16-dfsg-2 <aucune>
2016-03-11 12:35:44 status unpacked virtualbox:amd64 5.0.16-dfsg-2
2016-03-11 12:35:44 status unpacked virtualbox:amd64 5.0.16-dfsg-2
2016-03-11 12:35:45 status unpacked virtualbox:amd64 5.0.16-dfsg-2
2016-03-11 12:35:45 status half-configured virtualbox:amd64 5.0.16-dfsg-2
2016-03-11 12:35:46 status installed virtualbox:amd64 5.0.16-dfsg-2
2016-03-11 12:35:46 configure virtualbox-qt:amd64 5.0.16-dfsg-2 <aucune>
2016-03-11 12:35:46 status unpacked virtualbox-qt:amd64 5.0.16-dfsg-2
2016-03-11 12:35:46 status half-configured virtualbox-qt:amd64 5.0.16-dfsg-2
2016-03-11 12:35:46 status installed virtualbox-qt:amd64 5.0.16-dfsg-2
2016-03-11 12:35:46 configure virtualbox-dbg:amd64 5.0.16-dfsg-2 <aucune>
2016-03-11 12:35:46 status unpacked virtualbox-dbg:amd64 5.0.16-dfsg-2
2016-03-11 12:35:46 status half-configured virtualbox-dbg:amd64 5.0.16-dfsg-2
2016-03-11 12:35:47 status installed virtualbox-dbg:amd64 5.0.16-dfsg-2
2016-03-11 12:35:47 configure x11-common:all 1:7.7+13ubuntu3 <aucune>
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:47 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:48 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:48 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:48 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:48 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:48 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:48 status unpacked x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:48 status half-configured x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:49 status installed x11-common:all 1:7.7+13ubuntu3
2016-03-11 12:35:49 configure xserver-common:all 2:1.18.1-1ubuntu3 <aucune>
2016-03-11 12:35:49 status unpacked xserver-common:all 2:1.18.1-1ubuntu3
2016-03-11 12:35:49 status half-configured xserver-common:all 2:1.18.1-1ubuntu3
2016-03-11 12:35:49 status installed xserver-common:all 2:1.18.1-1ubuntu3
2016-03-11 12:35:49 configure xserver-xorg-legacy:amd64 2:1.18.1-1ubuntu3 <aucune>
2016-03-11 12:35:49 status unpacked xserver-xorg-legacy:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:35:49 status half-configured xserver-xorg-legacy:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:35:50 status installed xserver-xorg-legacy:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:35:50 configure x11proto-core-dev:all 7.0.28-2ubuntu1 <aucune>
2016-03-11 12:35:50 status unpacked x11proto-core-dev:all 7.0.28-2ubuntu1
2016-03-11 12:35:50 status half-configured x11proto-core-dev:all 7.0.28-2ubuntu1
2016-03-11 12:35:50 status installed x11proto-core-dev:all 7.0.28-2ubuntu1
2016-03-11 12:35:50 configure xserver-xorg-input-all:amd64 1:7.7+13ubuntu3 <aucune>
2016-03-11 12:35:50 status unpacked xserver-xorg-input-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:51 status half-configured xserver-xorg-input-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:51 status installed xserver-xorg-input-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:51 configure xserver-xorg:amd64 1:7.7+13ubuntu3 <aucune>
2016-03-11 12:35:51 status unpacked xserver-xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:51 status half-configured xserver-xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:51 status installed xserver-xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:51 configure xorg-docs-core:all 1:1.7.1-1ubuntu1 <aucune>
2016-03-11 12:35:51 status unpacked xorg-docs-core:all 1:1.7.1-1ubuntu1
2016-03-11 12:35:51 status half-configured xorg-docs-core:all 1:1.7.1-1ubuntu1
2016-03-11 12:35:51 status installed xorg-docs-core:all 1:1.7.1-1ubuntu1
2016-03-11 12:35:51 configure xorg:amd64 1:7.7+13ubuntu3 <aucune>
2016-03-11 12:35:51 status unpacked xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:51 status half-configured xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:52 status installed xorg:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:52 configure xserver-xephyr:amd64 2:1.18.1-1ubuntu3 <aucune>
2016-03-11 12:35:52 status unpacked xserver-xephyr:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:35:52 status half-configured xserver-xephyr:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:35:52 status installed xserver-xephyr:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:35:52 configure xserver-xorg-video-all:amd64 1:7.7+13ubuntu3 <aucune>
2016-03-11 12:35:52 status unpacked xserver-xorg-video-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:52 status half-configured xserver-xorg-video-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:52 status installed xserver-xorg-video-all:amd64 1:7.7+13ubuntu3
2016-03-11 12:35:52 configure dh-systemd:all 1.29ubuntu1 <aucune>
2016-03-11 12:35:52 status unpacked dh-systemd:all 1.29ubuntu1
2016-03-11 12:35:52 status half-configured dh-systemd:all 1.29ubuntu1
2016-03-11 12:35:52 status installed dh-systemd:all 1.29ubuntu1
2016-03-11 12:35:52 configure inxi:all 2.2.35-0ubuntu1 <aucune>
2016-03-11 12:35:52 status unpacked inxi:all 2.2.35-0ubuntu1
2016-03-11 12:35:52 status unpacked inxi:all 2.2.35-0ubuntu1
2016-03-11 12:35:53 status half-configured inxi:all 2.2.35-0ubuntu1
2016-03-11 12:35:53 status installed inxi:all 2.2.35-0ubuntu1
2016-03-11 12:35:53 configure kde-cli-tools-data:all 4:5.5.4-0ubuntu1 <aucune>
2016-03-11 12:35:53 status unpacked kde-cli-tools-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 status half-configured kde-cli-tools-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 status installed kde-cli-tools-data:all 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 configure kde-cli-tools:amd64 4:5.5.4-0ubuntu1 <aucune>
2016-03-11 12:35:53 status unpacked kde-cli-tools:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 status half-configured kde-cli-tools:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 status installed kde-cli-tools:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 configure khelpcenter:amd64 4:5.5.4-0ubuntu1 <aucune>
2016-03-11 12:35:53 status unpacked khelpcenter:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 status half-configured khelpcenter:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 status installed khelpcenter:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:53 configure kio-extras-data:all 4:15.12.1-1ubuntu1 <aucune>
2016-03-11 12:35:53 status unpacked kio-extras-data:all 4:15.12.1-1ubuntu1
2016-03-11 12:35:53 status half-configured kio-extras-data:all 4:15.12.1-1ubuntu1
2016-03-11 12:35:53 status installed kio-extras-data:all 4:15.12.1-1ubuntu1
2016-03-11 12:35:53 configure kio-extras:amd64 4:15.12.1-1ubuntu1 <aucune>
2016-03-11 12:35:53 status unpacked kio-extras:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:35:53 status half-configured kio-extras:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:35:54 status installed kio-extras:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:35:54 configure kolourpaint4:amd64 4:15.12.1-1ubuntu1 <aucune>
2016-03-11 12:35:54 status unpacked kolourpaint4:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:35:54 status half-configured kolourpaint4:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:35:54 status installed kolourpaint4:amd64 4:15.12.1-1ubuntu1
2016-03-11 12:35:54 configure kpartx:amd64 0.5.0-7ubuntu16 <aucune>
2016-03-11 12:35:54 status unpacked kpartx:amd64 0.5.0-7ubuntu16
2016-03-11 12:35:54 status half-configured kpartx:amd64 0.5.0-7ubuntu16
2016-03-11 12:35:54 status installed kpartx:amd64 0.5.0-7ubuntu16
2016-03-11 12:35:54 configure libbabeltrace1:amd64 1.3.2-1 <aucune>
2016-03-11 12:35:54 status unpacked libbabeltrace1:amd64 1.3.2-1
2016-03-11 12:35:54 status half-configured libbabeltrace1:amd64 1.3.2-1
2016-03-11 12:35:54 status installed libbabeltrace1:amd64 1.3.2-1
2016-03-11 12:35:55 configure libbabeltrace-ctf1:amd64 1.3.2-1 <aucune>
2016-03-11 12:35:55 status unpacked libbabeltrace-ctf1:amd64 1.3.2-1
2016-03-11 12:35:55 status half-configured libbabeltrace-ctf1:amd64 1.3.2-1
2016-03-11 12:35:55 status installed libbabeltrace-ctf1:amd64 1.3.2-1
2016-03-11 12:35:55 configure libfreeimage3:amd64 3.17.0+ds1-2 <aucune>
2016-03-11 12:35:55 status unpacked libfreeimage3:amd64 3.17.0+ds1-2
2016-03-11 12:35:55 status half-configured libfreeimage3:amd64 3.17.0+ds1-2
2016-03-11 12:35:55 status installed libfreeimage3:amd64 3.17.0+ds1-2
2016-03-11 12:35:55 configure libkf5filemetadata-data:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:55 status unpacked libkf5filemetadata-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:55 status half-configured libkf5filemetadata-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:55 status installed libkf5filemetadata-data:all 5.18.0-0ubuntu1
2016-03-11 12:35:55 configure libkf5filemetadata3:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:55 status unpacked libkf5filemetadata3:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:55 status half-configured libkf5filemetadata3:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:55 status installed libkf5filemetadata3:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:55 configure libkf5filemetadata-bin:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:55 status unpacked libkf5filemetadata-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:55 status half-configured libkf5filemetadata-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:56 status installed libkf5filemetadata-bin:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:56 configure libkf5networkmanagerqt6:amd64 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:35:56 status unpacked libkf5networkmanagerqt6:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:56 status half-configured libkf5networkmanagerqt6:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:56 status installed libkf5networkmanagerqt6:amd64 5.18.0-0ubuntu1
2016-03-11 12:35:56 configure libkf5screen6:amd64 4:5.5.4-2~ubuntu1 <aucune>
2016-03-11 12:35:56 status unpacked libkf5screen6:amd64 4:5.5.4-2~ubuntu1
2016-03-11 12:35:56 status half-configured libkf5screen6:amd64 4:5.5.4-2~ubuntu1
2016-03-11 12:35:56 status installed libkf5screen6:amd64 4:5.5.4-2~ubuntu1
2016-03-11 12:35:56 configure milou:amd64 4:5.5.4-0ubuntu1 <aucune>
2016-03-11 12:35:56 status unpacked milou:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:56 status half-configured milou:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:56 status installed milou:amd64 4:5.5.4-0ubuntu1
2016-03-11 12:35:56 configure python-lockfile:all 1:0.12.2-1 <aucune>
2016-03-11 12:35:56 status unpacked python-lockfile:all 1:0.12.2-1
2016-03-11 12:35:56 status half-configured python-lockfile:all 1:0.12.2-1
2016-03-11 12:35:57 status installed python-lockfile:all 1:0.12.2-1
2016-03-11 12:35:57 configure python-openvswitch:all 2.5.0-0ubuntu1 <aucune>
2016-03-11 12:35:57 status unpacked python-openvswitch:all 2.5.0-0ubuntu1
2016-03-11 12:35:57 status half-configured python-openvswitch:all 2.5.0-0ubuntu1
2016-03-11 12:35:57 status installed python-openvswitch:all 2.5.0-0ubuntu1
2016-03-11 12:35:57 configure selene:amd64 16.3~264~ubuntu16.04.1 <aucune>
2016-03-11 12:35:57 status unpacked selene:amd64 16.3~264~ubuntu16.04.1
2016-03-11 12:35:57 status half-configured selene:amd64 16.3~264~ubuntu16.04.1
2016-03-11 12:35:57 status installed selene:amd64 16.3~264~ubuntu16.04.1
2016-03-11 12:35:57 configure libnss3-nssdb:all 2:3.21-1ubuntu4 <aucune>
2016-03-11 12:35:57 status unpacked libnss3-nssdb:all 2:3.21-1ubuntu4
2016-03-11 12:35:58 status half-configured libnss3-nssdb:all 2:3.21-1ubuntu4
2016-03-11 12:35:58 status installed libnss3-nssdb:all 2:3.21-1ubuntu4
2016-03-11 12:35:58 configure libnss3:amd64 2:3.21-1ubuntu4 <aucune>
2016-03-11 12:35:58 status unpacked libnss3:amd64 2:3.21-1ubuntu4
2016-03-11 12:35:58 status half-configured libnss3:amd64 2:3.21-1ubuntu4
2016-03-11 12:35:58 status installed libnss3:amd64 2:3.21-1ubuntu4
2016-03-11 12:35:58 configure libnss3-dbg:amd64 2:3.21-1ubuntu4 <aucune>
2016-03-11 12:35:58 status unpacked libnss3-dbg:amd64 2:3.21-1ubuntu4
2016-03-11 12:35:58 status half-configured libnss3-dbg:amd64 2:3.21-1ubuntu4
2016-03-11 12:35:58 status installed libnss3-dbg:amd64 2:3.21-1ubuntu4
2016-03-11 12:35:58 configure flashplugin-installer:amd64 11.2.202.577ubuntu1 <aucune>
2016-03-11 12:35:58 status unpacked flashplugin-installer:amd64 11.2.202.577ubuntu1
2016-03-11 12:35:58 status half-configured flashplugin-installer:amd64 11.2.202.577ubuntu1
2016-03-11 12:35:59 status installed flashplugin-installer:amd64 11.2.202.577ubuntu1
2016-03-11 12:35:59 configure liboxideqtcore0:amd64 1.13.6-0ubuntu1 <aucune>
2016-03-11 12:35:59 status unpacked liboxideqtcore0:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 status half-configured liboxideqtcore0:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 status installed liboxideqtcore0:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 configure liboxideqtquick0:amd64 1.13.6-0ubuntu1 <aucune>
2016-03-11 12:35:59 status unpacked liboxideqtquick0:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 status half-configured liboxideqtquick0:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 status installed liboxideqtquick0:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 configure liboxideqt-qmlplugin:amd64 1.13.6-0ubuntu1 <aucune>
2016-03-11 12:35:59 status unpacked liboxideqt-qmlplugin:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 status half-configured liboxideqt-qmlplugin:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 status installed liboxideqt-qmlplugin:amd64 1.13.6-0ubuntu1
2016-03-11 12:35:59 configure qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160307-0ubuntu1 <aucune>
2016-03-11 12:35:59 status unpacked qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:00 status half-configured qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:00 status installed qtdeclarative5-ubuntu-web-plugin:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:00 configure webbrowser-app:amd64 0.23+16.04.20160307-0ubuntu1 <aucune>
2016-03-11 12:36:00 status unpacked webbrowser-app:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:00 status unpacked webbrowser-app:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:00 status half-configured webbrowser-app:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:01 status installed webbrowser-app:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:01 configure webapp-container:amd64 0.23+16.04.20160307-0ubuntu1 <aucune>
2016-03-11 12:36:01 status unpacked webapp-container:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:01 status half-configured webapp-container:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:01 status installed webapp-container:amd64 0.23+16.04.20160307-0ubuntu1
2016-03-11 12:36:01 trigproc man-db:amd64 2.7.5-1build~pie.1 <aucune>
2016-03-11 12:36:01 status half-configured man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:36:19 status installed man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:36:19 trigproc software-center:all 16.01+16.04.20160217 <aucune>
2016-03-11 12:36:19 status half-configured software-center:all 16.01+16.04.20160217
2016-03-11 12:36:51 status installed software-center:all 16.01+16.04.20160217
2016-03-11 12:36:51 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:36:51 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:36:51 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:36:51 trigproc menu:amd64 2.1.47ubuntu1 <aucune>
2016-03-11 12:36:51 status half-configured menu:amd64 2.1.47ubuntu1
2016-03-11 12:36:51 status installed menu:amd64 2.1.47ubuntu1
2016-03-11 12:36:51 trigproc initramfs-tools:all 0.122ubuntu6 <aucune>
2016-03-11 12:36:51 status half-configured initramfs-tools:all 0.122ubuntu6
2016-03-11 12:37:04 status installed initramfs-tools:all 0.122ubuntu6
2016-03-11 12:37:04 trigproc systemd:amd64 229-2ubuntu1 <aucune>
2016-03-11 12:37:04 status half-configured systemd:amd64 229-2ubuntu1
2016-03-11 12:37:04 status installed systemd:amd64 229-2ubuntu1
2016-03-11 12:37:04 trigproc ureadahead:amd64 0.100.0-19build~pie.1 <aucune>
2016-03-11 12:37:04 status half-configured ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:37:05 status installed ureadahead:amd64 0.100.0-19build~pie.1
2016-03-11 12:37:05 startup packages configure
2016-03-11 12:39:02 startup packages remove
2016-03-11 12:39:02 status installed kubuntu-debug-installer:amd64 16.04ubuntu2
2016-03-11 12:39:02 remove kubuntu-debug-installer:amd64 16.04ubuntu2 <aucune>
2016-03-11 12:39:02 status half-configured kubuntu-debug-installer:amd64 16.04ubuntu2
2016-03-11 12:39:02 status half-installed kubuntu-debug-installer:amd64 16.04ubuntu2
2016-03-11 12:39:03 status config-files kubuntu-debug-installer:amd64 16.04ubuntu2
2016-03-11 12:39:03 status config-files kubuntu-debug-installer:amd64 16.04ubuntu2
2016-03-11 12:39:03 status config-files kubuntu-debug-installer:amd64 16.04ubuntu2
2016-03-11 12:39:03 status not-installed kubuntu-debug-installer:amd64 <aucune>
2016-03-11 12:39:03 status installed libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:39:03 remove libcommons-lang-java:all 2.6-6ubuntu1 <aucune>
2016-03-11 12:39:03 status half-configured libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:39:03 status half-installed libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:39:03 status config-files libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:39:03 status config-files libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:39:03 status config-files libcommons-lang-java:all 2.6-6ubuntu1
2016-03-11 12:39:03 status not-installed libcommons-lang-java:all <aucune>
2016-03-11 12:39:04 status installed qapt-batch:amd64 3.0.1-1build1
2016-03-11 12:39:04 remove qapt-batch:amd64 3.0.1-1build1 <aucune>
2016-03-11 12:39:04 status half-configured qapt-batch:amd64 3.0.1-1build1
2016-03-11 12:39:04 status half-installed qapt-batch:amd64 3.0.1-1build1
2016-03-11 12:39:04 status config-files qapt-batch:amd64 3.0.1-1build1
2016-03-11 12:39:04 status config-files qapt-batch:amd64 3.0.1-1build1
2016-03-11 12:39:04 status config-files qapt-batch:amd64 3.0.1-1build1
2016-03-11 12:39:04 status not-installed qapt-batch:amd64 <aucune>
2016-03-11 12:39:04 status installed libqapt3-runtime:amd64 3.0.1-1build1
2016-03-11 12:39:04 remove libqapt3-runtime:amd64 3.0.1-1build1 <aucune>
2016-03-11 12:39:04 status half-configured libqapt3-runtime:amd64 3.0.1-1build1
2016-03-11 12:39:04 status half-installed libqapt3-runtime:amd64 3.0.1-1build1
2016-03-11 12:39:04 status triggers-pending dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:39:05 status config-files libqapt3-runtime:amd64 3.0.1-1build1
2016-03-11 12:39:05 status config-files libqapt3-runtime:amd64 3.0.1-1build1
2016-03-11 12:39:05 status installed libqapt3:amd64 3.0.1-1build1
2016-03-11 12:39:05 remove libqapt3:amd64 3.0.1-1build1 <aucune>
2016-03-11 12:39:05 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:39:05 status half-configured libqapt3:amd64 3.0.1-1build1
2016-03-11 12:39:05 status half-installed libqapt3:amd64 3.0.1-1build1
2016-03-11 12:39:05 status config-files libqapt3:amd64 3.0.1-1build1
2016-03-11 12:39:05 status config-files libqapt3:amd64 3.0.1-1build1
2016-03-11 12:39:05 status config-files libqapt3:amd64 3.0.1-1build1
2016-03-11 12:39:06 status not-installed libqapt3:amd64 <aucune>
2016-03-11 12:39:06 trigproc dbus:amd64 1.10.6-1ubuntu2 <aucune>
2016-03-11 12:39:06 status half-configured dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:39:06 status installed dbus:amd64 1.10.6-1ubuntu2
2016-03-11 12:39:06 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:39:06 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:39:06 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:39:06 startup packages configure
2016-03-11 12:40:00 startup packages remove
2016-03-11 12:40:00 status installed fglrx-amdcccle:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:01 remove fglrx-amdcccle:amd64 2:15.201-0ubuntu7 <aucune>
2016-03-11 12:40:01 status half-configured fglrx-amdcccle:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:01 status half-installed fglrx-amdcccle:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:01 status config-files fglrx-amdcccle:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:01 status config-files fglrx-amdcccle:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:01 status config-files fglrx-amdcccle:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:01 status not-installed fglrx-amdcccle:amd64 <aucune>
2016-03-11 12:40:01 status installed fglrx:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:01 remove fglrx:amd64 2:15.201-0ubuntu7 <aucune>
2016-03-11 12:40:01 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:40:01 status half-configured fglrx:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:02 status half-installed fglrx:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:02 status config-files fglrx:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:02 status config-files fglrx:amd64 2:15.201-0ubuntu7
2016-03-11 12:40:02 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:40:02 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:40:03 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:40:03 startup archives unpack
2016-03-11 12:40:03 upgrade xserver-xorg-video-amdgpu:amd64 1.0.0-1 1.0.1-1build2
2016-03-11 12:40:03 status half-configured xserver-xorg-video-amdgpu:amd64 1.0.0-1
2016-03-11 12:40:03 status unpacked xserver-xorg-video-amdgpu:amd64 1.0.0-1
2016-03-11 12:40:03 status half-installed xserver-xorg-video-amdgpu:amd64 1.0.0-1
2016-03-11 12:40:03 status triggers-pending man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:40:03 status half-installed xserver-xorg-video-amdgpu:amd64 1.0.0-1
2016-03-11 12:40:04 status unpacked xserver-xorg-video-amdgpu:amd64 1.0.1-1build2
2016-03-11 12:40:04 status unpacked xserver-xorg-video-amdgpu:amd64 1.0.1-1build2
2016-03-11 12:40:04 upgrade xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1 1:1.0.12-1build2
2016-03-11 12:40:04 status half-configured xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1
2016-03-11 12:40:04 status unpacked xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1
2016-03-11 12:40:04 status half-installed xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1
2016-03-11 12:40:04 status half-installed xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1
2016-03-11 12:40:04 status unpacked xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1build2
2016-03-11 12:40:04 status unpacked xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1build2
2016-03-11 12:40:05 upgrade xserver-xorg-video-nouveau:amd64 1:1.0.12-1 1:1.0.12-1build2
2016-03-11 12:40:05 status half-configured xserver-xorg-video-nouveau:amd64 1:1.0.12-1
2016-03-11 12:40:05 status unpacked xserver-xorg-video-nouveau:amd64 1:1.0.12-1
2016-03-11 12:40:05 status half-installed xserver-xorg-video-nouveau:amd64 1:1.0.12-1
2016-03-11 12:40:05 status half-installed xserver-xorg-video-nouveau:amd64 1:1.0.12-1
2016-03-11 12:40:05 status unpacked xserver-xorg-video-nouveau:amd64 1:1.0.12-1build2
2016-03-11 12:40:05 status unpacked xserver-xorg-video-nouveau:amd64 1:1.0.12-1build2
2016-03-11 12:40:05 upgrade xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu2 2:2.99.917+git20160218-1ubuntu3
2016-03-11 12:40:05 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:40:05 status half-configured xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu2
2016-03-11 12:40:05 status unpacked xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu2
2016-03-11 12:40:06 status half-installed xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu2
2016-03-11 12:40:06 status half-installed xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu2
2016-03-11 12:40:06 status unpacked xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu3
2016-03-11 12:40:06 status unpacked xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu3
2016-03-11 12:40:06 upgrade xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu1build~pie.1 0.1.4-3ubuntu3
2016-03-11 12:40:06 status half-configured xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu1build~pie.1
2016-03-11 12:40:06 status unpacked xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu1build~pie.1
2016-03-11 12:40:06 status half-installed xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu1build~pie.1
2016-03-11 12:40:07 status half-installed xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu1build~pie.1
2016-03-11 12:40:07 status unpacked xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu3
2016-03-11 12:40:07 status unpacked xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu3
2016-03-11 12:40:07 upgrade xserver-xorg-video-radeon:amd64 1:7.6.1-1build0pie.1 1:7.6.1-1ubuntu2
2016-03-11 12:40:07 status half-configured xserver-xorg-video-radeon:amd64 1:7.6.1-1build0pie.1
2016-03-11 12:40:07 status unpacked xserver-xorg-video-radeon:amd64 1:7.6.1-1build0pie.1
2016-03-11 12:40:07 status half-installed xserver-xorg-video-radeon:amd64 1:7.6.1-1build0pie.1
2016-03-11 12:40:07 status half-installed xserver-xorg-video-radeon:amd64 1:7.6.1-1build0pie.1
2016-03-11 12:40:07 status unpacked xserver-xorg-video-radeon:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:40:07 status unpacked xserver-xorg-video-radeon:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:40:08 upgrade xserver-xorg-video-r128:amd64 6.10.0-1build~pie.1 6.10.0-1build2
2016-03-11 12:40:08 status half-configured xserver-xorg-video-r128:amd64 6.10.0-1build~pie.1
2016-03-11 12:40:08 status unpacked xserver-xorg-video-r128:amd64 6.10.0-1build~pie.1
2016-03-11 12:40:08 status half-installed xserver-xorg-video-r128:amd64 6.10.0-1build~pie.1
2016-03-11 12:40:08 status half-installed xserver-xorg-video-r128:amd64 6.10.0-1build~pie.1
2016-03-11 12:40:08 status unpacked xserver-xorg-video-r128:amd64 6.10.0-1build2
2016-03-11 12:40:08 status unpacked xserver-xorg-video-r128:amd64 6.10.0-1build2
2016-03-11 12:40:08 upgrade xserver-xorg-video-mach64:amd64 6.9.5-1build~pie.1 6.9.5-1build2
2016-03-11 12:40:08 status half-configured xserver-xorg-video-mach64:amd64 6.9.5-1build~pie.1
2016-03-11 12:40:08 status unpacked xserver-xorg-video-mach64:amd64 6.9.5-1build~pie.1
2016-03-11 12:40:08 status half-installed xserver-xorg-video-mach64:amd64 6.9.5-1build~pie.1
2016-03-11 12:40:08 status half-installed xserver-xorg-video-mach64:amd64 6.9.5-1build~pie.1
2016-03-11 12:40:09 status unpacked xserver-xorg-video-mach64:amd64 6.9.5-1build2
2016-03-11 12:40:09 status unpacked xserver-xorg-video-mach64:amd64 6.9.5-1build2
2016-03-11 12:40:09 upgrade xserver-xorg-video-ati:amd64 1:7.6.1-1build0pie.1 1:7.6.1-1ubuntu2
2016-03-11 12:40:09 status half-configured xserver-xorg-video-ati:amd64 1:7.6.1-1build0pie.1
2016-03-11 12:40:09 status unpacked xserver-xorg-video-ati:amd64 1:7.6.1-1build0pie.1
2016-03-11 12:40:09 status half-installed xserver-xorg-video-ati:amd64 1:7.6.1-1build0pie.1
2016-03-11 12:40:09 status half-installed xserver-xorg-video-ati:amd64 1:7.6.1-1build0pie.1
2016-03-11 12:40:09 status unpacked xserver-xorg-video-ati:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:40:09 status unpacked xserver-xorg-video-ati:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:40:10 upgrade xserver-xorg-video-fbdev:amd64 1:0.4.4-1build3build~pie.1 1:0.4.4-1build5
2016-03-11 12:40:10 status half-configured xserver-xorg-video-fbdev:amd64 1:0.4.4-1build3build~pie.1
2016-03-11 12:40:10 status unpacked xserver-xorg-video-fbdev:amd64 1:0.4.4-1build3build~pie.1
2016-03-11 12:40:10 status half-installed xserver-xorg-video-fbdev:amd64 1:0.4.4-1build3build~pie.1
2016-03-11 12:40:10 status half-installed xserver-xorg-video-fbdev:amd64 1:0.4.4-1build3build~pie.1
2016-03-11 12:40:10 status unpacked xserver-xorg-video-fbdev:amd64 1:0.4.4-1build5
2016-03-11 12:40:10 status unpacked xserver-xorg-video-fbdev:amd64 1:0.4.4-1build5
2016-03-11 12:40:10 upgrade xserver-xorg-video-vesa:amd64 1:2.3.4-1build0pie.3 1:2.3.4-1build2
2016-03-11 12:40:10 status half-configured xserver-xorg-video-vesa:amd64 1:2.3.4-1build0pie.3
2016-03-11 12:40:10 status unpacked xserver-xorg-video-vesa:amd64 1:2.3.4-1build0pie.3
2016-03-11 12:40:10 status half-installed xserver-xorg-video-vesa:amd64 1:2.3.4-1build0pie.3
2016-03-11 12:40:11 status half-installed xserver-xorg-video-vesa:amd64 1:2.3.4-1build0pie.3
2016-03-11 12:40:11 status unpacked xserver-xorg-video-vesa:amd64 1:2.3.4-1build2
2016-03-11 12:40:11 status unpacked xserver-xorg-video-vesa:amd64 1:2.3.4-1build2
2016-03-11 12:40:11 upgrade xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu1build~pie.1 1:13.1.0-2ubuntu3
2016-03-11 12:40:11 status half-configured xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu1build~pie.1
2016-03-11 12:40:11 status unpacked xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu1build~pie.1
2016-03-11 12:40:11 status half-installed xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu1build~pie.1
2016-03-11 12:40:11 status half-installed xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu1build~pie.1
2016-03-11 12:40:11 status unpacked xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu3
2016-03-11 12:40:11 status unpacked xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu3
2016-03-11 12:40:12 upgrade xserver-xorg-input-vmmouse:amd64 1:13.1.0-0ubuntu1build~pie.1 1:13.1.0-1ubuntu2
2016-03-11 12:40:12 status half-configured xserver-xorg-input-vmmouse:amd64 1:13.1.0-0ubuntu1build~pie.1
2016-03-11 12:40:12 status unpacked xserver-xorg-input-vmmouse:amd64 1:13.1.0-0ubuntu1build~pie.1
2016-03-11 12:40:12 status half-installed xserver-xorg-input-vmmouse:amd64 1:13.1.0-0ubuntu1build~pie.1
2016-03-11 12:40:12 status half-installed xserver-xorg-input-vmmouse:amd64 1:13.1.0-0ubuntu1build~pie.1
2016-03-11 12:40:12 status unpacked xserver-xorg-input-vmmouse:amd64 1:13.1.0-1ubuntu2
2016-03-11 12:40:12 status unpacked xserver-xorg-input-vmmouse:amd64 1:13.1.0-1ubuntu2
2016-03-11 12:40:12 trigproc man-db:amd64 2.7.5-1build~pie.1 <aucune>
2016-03-11 12:40:12 status half-configured man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:40:13 status installed man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:40:13 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:40:13 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:40:13 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:40:13 startup packages remove
2016-03-11 12:40:13 status installed xserver-xorg-input-mouse:amd64 1:1.9.1-1build~pie.1
2016-03-11 12:40:13 remove xserver-xorg-input-mouse:amd64 1:1.9.1-1build~pie.1 <aucune>
2016-03-11 12:40:13 status half-configured xserver-xorg-input-mouse:amd64 1:1.9.1-1build~pie.1
2016-03-11 12:40:13 status half-installed xserver-xorg-input-mouse:amd64 1:1.9.1-1build~pie.1
2016-03-11 12:40:13 status triggers-pending man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:40:14 status config-files xserver-xorg-input-mouse:amd64 1:1.9.1-1build~pie.1
2016-03-11 12:40:14 status config-files xserver-xorg-input-mouse:amd64 1:1.9.1-1build~pie.1
2016-03-11 12:40:14 status config-files xserver-xorg-input-mouse:amd64 1:1.9.1-1build~pie.1
2016-03-11 12:40:14 status not-installed xserver-xorg-input-mouse:amd64 <aucune>
2016-03-11 12:40:14 trigproc man-db:amd64 2.7.5-1build~pie.1 <aucune>
2016-03-11 12:40:14 status half-configured man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:40:14 status installed man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:40:14 startup archives unpack
2016-03-11 12:40:15 upgrade xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu1build~pie.1 1.8.2-1ubuntu3
2016-03-11 12:40:15 status half-configured xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu1build~pie.1
2016-03-11 12:40:15 status unpacked xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu1build~pie.1
2016-03-11 12:40:15 status half-installed xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu1build~pie.1
2016-03-11 12:40:15 status triggers-pending man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:40:15 status half-installed xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu1build~pie.1
2016-03-11 12:40:15 status unpacked xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu3
2016-03-11 12:40:15 status unpacked xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu3
2016-03-11 12:40:15 upgrade xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu1build0pie.3 1:0.32.0-0ubuntu3
2016-03-11 12:40:15 status half-configured xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu1build0pie.3
2016-03-11 12:40:15 status unpacked xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu1build0pie.3
2016-03-11 12:40:15 status half-installed xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu1build0pie.3
2016-03-11 12:40:16 status half-installed xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu1build0pie.3
2016-03-11 12:40:16 status unpacked xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu3
2016-03-11 12:40:16 status unpacked xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu3
2016-03-11 12:40:16 upgrade xserver-xorg-core:amd64 2:1.17.3-2ubuntu4 2:1.18.1-1ubuntu3
2016-03-11 12:40:16 status half-configured xserver-xorg-core:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:40:16 status unpacked xserver-xorg-core:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:40:16 status half-installed xserver-xorg-core:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:40:17 status half-installed xserver-xorg-core:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:40:17 status unpacked xserver-xorg-core:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:40:17 status unpacked xserver-xorg-core:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:40:17 upgrade xserver-xorg-input-evdev:amd64 1:2.9.2-1ubuntu1 1:2.10.1-1ubuntu2
2016-03-11 12:40:17 status half-configured xserver-xorg-input-evdev:amd64 1:2.9.2-1ubuntu1
2016-03-11 12:40:17 status unpacked xserver-xorg-input-evdev:amd64 1:2.9.2-1ubuntu1
2016-03-11 12:40:17 status half-installed xserver-xorg-input-evdev:amd64 1:2.9.2-1ubuntu1
2016-03-11 12:40:17 status half-installed xserver-xorg-input-evdev:amd64 1:2.9.2-1ubuntu1
2016-03-11 12:40:18 status unpacked xserver-xorg-input-evdev:amd64 1:2.10.1-1ubuntu2
2016-03-11 12:40:18 status unpacked xserver-xorg-input-evdev:amd64 1:2.10.1-1ubuntu2
2016-03-11 12:40:18 install seahorse-daemon:amd64 <aucune> 3.12.2-1
2016-03-11 12:40:18 status half-installed seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:40:18 status triggers-pending libglib2.0-0:i386 2.47.6-1
2016-03-11 12:40:18 status half-installed seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:40:18 status triggers-pending libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:40:18 status half-installed seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:40:18 status triggers-pending gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:40:18 status half-installed seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:40:19 status unpacked seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:40:19 status unpacked seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:40:19 install libcryptui0a:amd64 <aucune> 3.12.2-1
2016-03-11 12:40:19 status half-installed libcryptui0a:amd64 3.12.2-1
2016-03-11 12:40:19 status unpacked libcryptui0a:amd64 3.12.2-1
2016-03-11 12:40:19 status unpacked libcryptui0a:amd64 3.12.2-1
2016-03-11 12:40:19 upgrade evolution-plugins:amd64 3.18.5-1ubuntu1 3.18.5.1-1ubuntu1
2016-03-11 12:40:19 status half-configured evolution-plugins:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:19 status unpacked evolution-plugins:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:19 status half-installed evolution-plugins:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:20 status half-installed evolution-plugins:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:20 status unpacked evolution-plugins:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:40:20 status unpacked evolution-plugins:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:40:20 upgrade evolution:amd64 3.18.5-1ubuntu1 3.18.5.1-1ubuntu1
2016-03-11 12:40:20 status half-configured evolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:20 status unpacked evolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:20 status half-installed evolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:20 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:40:20 status half-installed evolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:20 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:40:20 status triggers-pending mime-support:all 3.59ubuntu1
2016-03-11 12:40:21 status half-installed evolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:21 status unpacked evolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:40:21 status unpacked evolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:40:21 upgrade evolution-common:all 3.18.5-1ubuntu1 3.18.5.1-1ubuntu1
2016-03-11 12:40:21 status half-configured evolution-common:all 3.18.5-1ubuntu1
2016-03-11 12:40:21 status unpacked evolution-common:all 3.18.5-1ubuntu1
2016-03-11 12:40:21 status half-installed evolution-common:all 3.18.5-1ubuntu1
2016-03-11 12:40:21 status half-installed evolution-common:all 3.18.5-1ubuntu1
2016-03-11 12:40:24 status triggers-pending hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:40:24 status half-installed evolution-common:all 3.18.5-1ubuntu1
2016-03-11 12:40:24 status half-installed evolution-common:all 3.18.5-1ubuntu1
2016-03-11 12:40:24 status half-installed evolution-common:all 3.18.5-1ubuntu1
2016-03-11 12:40:26 status half-installed evolution-common:all 3.18.5-1ubuntu1
2016-03-11 12:40:26 status unpacked evolution-common:all 3.18.5.1-1ubuntu1
2016-03-11 12:40:26 status unpacked evolution-common:all 3.18.5.1-1ubuntu1
2016-03-11 12:40:26 upgrade libevolution:amd64 3.18.5-1ubuntu1 3.18.5.1-1ubuntu1
2016-03-11 12:40:26 status half-configured libevolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:26 status unpacked libevolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:27 status half-installed libevolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:27 status half-installed libevolution:amd64 3.18.5-1ubuntu1
2016-03-11 12:40:27 status unpacked libevolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:40:27 status unpacked libevolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:40:27 upgrade qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:27 status half-configured qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:27 status unpacked qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:27 status half-installed qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:28 status half-installed qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:28 status unpacked qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:28 status unpacked qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:28 upgrade ubuntu-ui-toolkit-theme:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:28 status half-configured ubuntu-ui-toolkit-theme:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:29 status unpacked ubuntu-ui-toolkit-theme:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:29 status half-installed ubuntu-ui-toolkit-theme:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:29 status half-installed ubuntu-ui-toolkit-theme:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:29 status unpacked ubuntu-ui-toolkit-theme:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:29 status unpacked ubuntu-ui-toolkit-theme:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:30 install libubuntutoolkit5:amd64 <aucune> 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:30 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:40:30 status half-installed libubuntutoolkit5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:30 status unpacked libubuntutoolkit5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:30 status unpacked libubuntutoolkit5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:30 upgrade libubuntugestures5:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:30 status half-configured libubuntugestures5:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:30 status unpacked libubuntugestures5:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:30 status half-installed libubuntugestures5:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:31 status half-installed libubuntugestures5:amd64 1.3.1795+16.04.20160106-0ubuntu1build0pie.3
2016-03-11 12:40:31 status unpacked libubuntugestures5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:31 status unpacked libubuntugestures5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:40:31 install qt5-image-formats-plugins:amd64 <aucune> 5.5.1-2build1
2016-03-11 12:40:31 status half-installed qt5-image-formats-plugins:amd64 5.5.1-2build1
2016-03-11 12:40:32 status unpacked qt5-image-formats-plugins:amd64 5.5.1-2build1
2016-03-11 12:40:32 status unpacked qt5-image-formats-plugins:amd64 5.5.1-2build1
2016-03-11 12:40:32 upgrade audacious-plugins:amd64 3.6.2-2 3.6.2-2build1
2016-03-11 12:40:32 status half-configured audacious-plugins:amd64 3.6.2-2
2016-03-11 12:40:32 status unpacked audacious-plugins:amd64 3.6.2-2
2016-03-11 12:40:32 status half-installed audacious-plugins:amd64 3.6.2-2
2016-03-11 12:40:33 status half-installed audacious-plugins:amd64 3.6.2-2
2016-03-11 12:40:33 status unpacked audacious-plugins:amd64 3.6.2-2build1
2016-03-11 12:40:33 status unpacked audacious-plugins:amd64 3.6.2-2build1
2016-03-11 12:40:33 upgrade audacious-plugins-data:all 3.6.2-2 3.6.2-2build1
2016-03-11 12:40:33 status half-configured audacious-plugins-data:all 3.6.2-2
2016-03-11 12:40:33 status unpacked audacious-plugins-data:all 3.6.2-2
2016-03-11 12:40:33 status half-installed audacious-plugins-data:all 3.6.2-2
2016-03-11 12:40:34 status half-installed audacious-plugins-data:all 3.6.2-2
2016-03-11 12:40:35 status unpacked audacious-plugins-data:all 3.6.2-2build1
2016-03-11 12:40:35 status unpacked audacious-plugins-data:all 3.6.2-2build1
2016-03-11 12:40:37 install libsndio6.1:amd64 <aucune> 1.1.0-2
2016-03-11 12:40:37 status half-installed libsndio6.1:amd64 1.1.0-2
2016-03-11 12:40:38 status unpacked libsndio6.1:amd64 1.1.0-2
2016-03-11 12:40:38 status unpacked libsndio6.1:amd64 1.1.0-2
2016-03-11 12:40:38 upgrade libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu1 2.0.4+dfsg1-2ubuntu2
2016-03-11 12:40:38 status half-configured libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu1
2016-03-11 12:40:38 status unpacked libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu1
2016-03-11 12:40:38 status half-installed libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu1
2016-03-11 12:40:38 status half-installed libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu1
2016-03-11 12:40:39 status unpacked libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu2
2016-03-11 12:40:39 status unpacked libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu2
2016-03-11 12:40:39 install libkf5kdcraw5:amd64 <aucune> 15.12.1-0ubuntu1
2016-03-11 12:40:39 status half-installed libkf5kdcraw5:amd64 15.12.1-0ubuntu1
2016-03-11 12:40:40 status unpacked libkf5kdcraw5:amd64 15.12.1-0ubuntu1
2016-03-11 12:40:40 status unpacked libkf5kdcraw5:amd64 15.12.1-0ubuntu1
2016-03-11 12:40:40 install libkf5kipi-data:all <aucune> 15.12.1-1ubuntu1
2016-03-11 12:40:40 status half-installed libkf5kipi-data:all 15.12.1-1ubuntu1
2016-03-11 12:40:40 status half-installed libkf5kipi-data:all 15.12.1-1ubuntu1
2016-03-11 12:40:40 status unpacked libkf5kipi-data:all 15.12.1-1ubuntu1
2016-03-11 12:40:40 status unpacked libkf5kipi-data:all 15.12.1-1ubuntu1
2016-03-11 12:40:41 install libkf5kipi30.0.0:amd64 <aucune> 15.12.1-1ubuntu1
2016-03-11 12:40:41 status half-installed libkf5kipi30.0.0:amd64 15.12.1-1ubuntu1
2016-03-11 12:40:41 status unpacked libkf5kipi30.0.0:amd64 15.12.1-1ubuntu1
2016-03-11 12:40:41 status unpacked libkf5kipi30.0.0:amd64 15.12.1-1ubuntu1
2016-03-11 12:40:41 upgrade gwenview:amd64 4:15.08.2-0ubuntu1 4:15.12.1-0ubuntu1
2016-03-11 12:40:41 status half-configured gwenview:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:40:42 status unpacked gwenview:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:40:42 status half-installed gwenview:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:40:42 status half-installed gwenview:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:40:42 status half-installed gwenview:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:40:43 status half-installed gwenview:amd64 4:15.08.2-0ubuntu1
2016-03-11 12:40:43 status unpacked gwenview:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:40:43 status unpacked gwenview:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:40:43 upgrade myspell-en-gb:all 1:4.2.1-0ubuntu3 1:5.1.0-1ubuntu1
2016-03-11 12:40:43 status half-configured myspell-en-gb:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:43 status unpacked myspell-en-gb:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:43 status half-installed myspell-en-gb:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:43 status half-installed myspell-en-gb:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:43 status triggers-pending postgresql-common:all 172
2016-03-11 12:40:44 status half-installed myspell-en-gb:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:44 status triggers-pending postgresql-common:all 172
2016-03-11 12:40:44 status unpacked myspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:44 status unpacked myspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:44 install hunspell-en-gb:all <aucune> 1:5.1.0-1ubuntu1
2016-03-11 12:40:44 status half-installed hunspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:44 status half-installed hunspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:45 status unpacked hunspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:45 status unpacked hunspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:45 upgrade myspell-en-za:all 1:4.2.1-0ubuntu3 1:5.1.0-1ubuntu1
2016-03-11 12:40:45 status half-configured myspell-en-za:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:45 status unpacked myspell-en-za:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:45 status half-installed myspell-en-za:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:45 status half-installed myspell-en-za:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:45 status half-installed myspell-en-za:all 1:4.2.1-0ubuntu3
2016-03-11 12:40:45 status unpacked myspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:45 status unpacked myspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:46 install hunspell-en-za:all <aucune> 1:5.1.0-1ubuntu1
2016-03-11 12:40:46 status half-installed hunspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:46 status half-installed hunspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:46 status unpacked hunspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:46 status unpacked hunspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:40:46 install libfontenc-dev:amd64 <aucune> 1:1.1.3-1build~pie.1
2016-03-11 12:40:46 status half-installed libfontenc-dev:amd64 1:1.1.3-1build~pie.1
2016-03-11 12:40:46 status unpacked libfontenc-dev:amd64 1:1.1.3-1build~pie.1
2016-03-11 12:40:46 status unpacked libfontenc-dev:amd64 1:1.1.3-1build~pie.1
2016-03-11 12:40:47 install libkf5gpgmepp-pthread5:amd64 <aucune> 15.12.1-0ubuntu1
2016-03-11 12:40:47 status half-installed libkf5gpgmepp-pthread5:amd64 15.12.1-0ubuntu1
2016-03-11 12:40:47 status unpacked libkf5gpgmepp-pthread5:amd64 15.12.1-0ubuntu1
2016-03-11 12:40:47 status unpacked libkf5gpgmepp-pthread5:amd64 15.12.1-0ubuntu1
2016-03-11 12:40:47 upgrade libkf5qgpgme5:amd64 15.08.2-0ubuntu1 15.12.1-0ubuntu1
2016-03-11 12:40:47 status half-configured libkf5qgpgme5:amd64 15.08.2-0ubuntu1
2016-03-11 12:40:47 status unpacked libkf5qgpgme5:amd64 15.08.2-0ubuntu1
2016-03-11 12:40:47 status half-installed libkf5qgpgme5:amd64 15.08.2-0ubuntu1
2016-03-11 12:40:48 status half-installed libkf5qgpgme5:amd64 15.08.2-0ubuntu1
2016-03-11 12:40:48 status unpacked libkf5qgpgme5:amd64 15.12.1-0ubuntu1
2016-03-11 12:40:48 status unpacked libkf5qgpgme5:amd64 15.12.1-0ubuntu1
2016-03-11 12:40:48 install pidgin-data:all <aucune> 1:2.10.12-0ubuntu5
2016-03-11 12:40:48 status half-installed pidgin-data:all 1:2.10.12-0ubuntu5
2016-03-11 12:40:49 status half-installed pidgin-data:all 1:2.10.12-0ubuntu5
2016-03-11 12:40:49 status unpacked pidgin-data:all 1:2.10.12-0ubuntu5
2016-03-11 12:40:49 status unpacked pidgin-data:all 1:2.10.12-0ubuntu5
2016-03-11 12:40:50 upgrade libpurple0:amd64 1:2.10.12-0ubuntu2 1:2.10.12-0ubuntu5
2016-03-11 12:40:50 status half-configured libpurple0:amd64 1:2.10.12-0ubuntu2
2016-03-11 12:40:50 status unpacked libpurple0:amd64 1:2.10.12-0ubuntu2
2016-03-11 12:40:50 status half-installed libpurple0:amd64 1:2.10.12-0ubuntu2
2016-03-11 12:40:50 status half-installed libpurple0:amd64 1:2.10.12-0ubuntu2
2016-03-11 12:40:51 status unpacked libpurple0:amd64 1:2.10.12-0ubuntu5
2016-03-11 12:40:51 status unpacked libpurple0:amd64 1:2.10.12-0ubuntu5
2016-03-11 12:40:51 install libxfont-dev:amd64 <aucune> 1:1.5.1-1
2016-03-11 12:40:51 status half-installed libxfont-dev:amd64 1:1.5.1-1
2016-03-11 12:40:51 status unpacked libxfont-dev:amd64 1:1.5.1-1
2016-03-11 12:40:51 status unpacked libxfont-dev:amd64 1:1.5.1-1
2016-03-11 12:40:52 upgrade oxygen-icon-theme:all 4:15.04.2-0ubuntu1 5:5.18.0-0ubuntu1
2016-03-11 12:40:52 status half-configured oxygen-icon-theme:all 4:15.04.2-0ubuntu1
2016-03-11 12:40:52 status unpacked oxygen-icon-theme:all 4:15.04.2-0ubuntu1
2016-03-11 12:40:52 status half-installed oxygen-icon-theme:all 4:15.04.2-0ubuntu1
2016-03-11 12:40:52 status half-installed oxygen-icon-theme:all 4:15.04.2-0ubuntu1
2016-03-11 12:40:52 status half-installed oxygen-icon-theme:all 4:15.04.2-0ubuntu1
2016-03-11 12:40:53 status unpacked oxygen-icon-theme:all 5:5.18.0-0ubuntu1
2016-03-11 12:40:53 status unpacked oxygen-icon-theme:all 5:5.18.0-0ubuntu1
2016-03-11 12:40:53 install oxygen5-icon-theme:all <aucune> 5.18.0-0ubuntu1
2016-03-11 12:40:53 status half-installed oxygen5-icon-theme:all 5.18.0-0ubuntu1
2016-03-11 12:40:58 status half-installed oxygen5-icon-theme:all 5.18.0-0ubuntu1
2016-03-11 12:41:02 status unpacked oxygen5-icon-theme:all 5.18.0-0ubuntu1
2016-03-11 12:41:02 status unpacked oxygen5-icon-theme:all 5.18.0-0ubuntu1
2016-03-11 12:41:02 install python-pika:all <aucune> 0.10.0-1
2016-03-11 12:41:02 status half-installed python-pika:all 0.10.0-1
2016-03-11 12:41:02 status unpacked python-pika:all 0.10.0-1
2016-03-11 12:41:02 status unpacked python-pika:all 0.10.0-1
2016-03-11 12:41:03 install python-pika-pool:all <aucune> 0.1.3-1ubuntu1
2016-03-11 12:41:03 status half-installed python-pika-pool:all 0.1.3-1ubuntu1
2016-03-11 12:41:03 status unpacked python-pika-pool:all 0.1.3-1ubuntu1
2016-03-11 12:41:03 status unpacked python-pika-pool:all 0.1.3-1ubuntu1
2016-03-11 12:41:03 upgrade python-oslo.messaging:all 3.0.0-1ubuntu2 4.5.0-1ubuntu1
2016-03-11 12:41:03 status half-configured python-oslo.messaging:all 3.0.0-1ubuntu2
2016-03-11 12:41:04 status unpacked python-oslo.messaging:all 3.0.0-1ubuntu2
2016-03-11 12:41:04 status half-installed python-oslo.messaging:all 3.0.0-1ubuntu2
2016-03-11 12:41:04 status triggers-pending doc-base:all 0.10.7
2016-03-11 12:41:04 status half-installed python-oslo.messaging:all 3.0.0-1ubuntu2
2016-03-11 12:41:04 status unpacked python-oslo.messaging:all 4.5.0-1ubuntu1
2016-03-11 12:41:04 status unpacked python-oslo.messaging:all 4.5.0-1ubuntu1
2016-03-11 12:41:04 upgrade python-oslo.versionedobjects:all 1.0.0-0ubuntu1 1.7.0-0ubuntu1
2016-03-11 12:41:04 status half-configured python-oslo.versionedobjects:all 1.0.0-0ubuntu1
2016-03-11 12:41:05 status unpacked python-oslo.versionedobjects:all 1.0.0-0ubuntu1
2016-03-11 12:41:05 status half-installed python-oslo.versionedobjects:all 1.0.0-0ubuntu1
2016-03-11 12:41:05 status half-installed python-oslo.versionedobjects:all 1.0.0-0ubuntu1
2016-03-11 12:41:05 status unpacked python-oslo.versionedobjects:all 1.7.0-0ubuntu1
2016-03-11 12:41:05 status unpacked python-oslo.versionedobjects:all 1.7.0-0ubuntu1
2016-03-11 12:41:05 install ubuntu-gnome-wallpapers-xenial:all <aucune> 16.04.1
2016-03-11 12:41:05 status half-installed ubuntu-gnome-wallpapers-xenial:all 16.04.1
2016-03-11 12:41:06 status unpacked ubuntu-gnome-wallpapers-xenial:all 16.04.1
2016-03-11 12:41:06 status unpacked ubuntu-gnome-wallpapers-xenial:all 16.04.1
2016-03-11 12:41:06 upgrade ubuntu-gnome-wallpapers:all 14.10.1 16.04.1
2016-03-11 12:41:06 status half-configured ubuntu-gnome-wallpapers:all 14.10.1
2016-03-11 12:41:06 status unpacked ubuntu-gnome-wallpapers:all 14.10.1
2016-03-11 12:41:06 status half-installed ubuntu-gnome-wallpapers:all 14.10.1
2016-03-11 12:41:06 status half-installed ubuntu-gnome-wallpapers:all 14.10.1
2016-03-11 12:41:08 status unpacked ubuntu-gnome-wallpapers:all 16.04.1
2016-03-11 12:41:08 status unpacked ubuntu-gnome-wallpapers:all 16.04.1
2016-03-11 12:41:08 upgrade xserver-xorg-dev:amd64 2:1.17.3-2ubuntu4 2:1.18.1-1ubuntu3
2016-03-11 12:41:08 status half-configured xserver-xorg-dev:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:41:08 status unpacked xserver-xorg-dev:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:41:08 status half-installed xserver-xorg-dev:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:41:09 status half-installed xserver-xorg-dev:amd64 2:1.17.3-2ubuntu4
2016-03-11 12:41:09 status unpacked xserver-xorg-dev:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:41:09 status unpacked xserver-xorg-dev:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:41:09 trigproc man-db:amd64 2.7.5-1build~pie.1 <aucune>
2016-03-11 12:41:09 status half-configured man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:41:10 status installed man-db:amd64 2.7.5-1build~pie.1
2016-03-11 12:41:10 trigproc libglib2.0-0:i386 2.47.6-1 <aucune>
2016-03-11 12:41:10 status half-configured libglib2.0-0:i386 2.47.6-1
2016-03-11 12:41:10 status installed libglib2.0-0:i386 2.47.6-1
2016-03-11 12:41:11 trigproc libglib2.0-0:amd64 2.47.6-1 <aucune>
2016-03-11 12:41:11 status half-configured libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:41:11 status installed libglib2.0-0:amd64 2.47.6-1
2016-03-11 12:41:11 trigproc gconf2:amd64 3.2.6-3ubuntu6build0pie.1 <aucune>
2016-03-11 12:41:11 status half-configured gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:41:11 status installed gconf2:amd64 3.2.6-3ubuntu6build0pie.1
2016-03-11 12:41:11 trigproc desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1 <aucune>
2016-03-11 12:41:11 status half-configured desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:41:11 status installed desktop-file-utils:amd64 0.22-1ubuntu3build~pie.1
2016-03-11 12:41:11 trigproc gnome-menus:amd64 3.13.3-6ubuntu3 <aucune>
2016-03-11 12:41:11 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:41:11 status installed gnome-menus:amd64 3.13.3-6ubuntu3
2016-03-11 12:41:11 trigproc mime-support:all 3.59ubuntu1 <aucune>
2016-03-11 12:41:11 status half-configured mime-support:all 3.59ubuntu1
2016-03-11 12:41:12 status installed mime-support:all 3.59ubuntu1
2016-03-11 12:41:12 trigproc hicolor-icon-theme:all 0.15-0ubuntu1 <aucune>
2016-03-11 12:41:12 status half-configured hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:41:12 status installed hicolor-icon-theme:all 0.15-0ubuntu1
2016-03-11 12:41:12 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:41:12 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:41:12 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:41:12 trigproc postgresql-common:all 172 <aucune>
2016-03-11 12:41:12 status half-configured postgresql-common:all 172
2016-03-11 12:41:13 status installed postgresql-common:all 172
2016-03-11 12:41:13 trigproc doc-base:all 0.10.7 <aucune>
2016-03-11 12:41:13 status half-configured doc-base:all 0.10.7
2016-03-11 12:41:13 status installed doc-base:all 0.10.7
2016-03-11 12:41:14 startup packages configure
2016-03-11 12:41:14 configure xserver-xorg-core:amd64 2:1.18.1-1ubuntu3 <aucune>
2016-03-11 12:41:14 status unpacked xserver-xorg-core:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:41:14 status half-configured xserver-xorg-core:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:41:14 status installed xserver-xorg-core:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:41:14 configure xserver-xorg-video-amdgpu:amd64 1.0.1-1build2 <aucune>
2016-03-11 12:41:14 status unpacked xserver-xorg-video-amdgpu:amd64 1.0.1-1build2
2016-03-11 12:41:14 status half-configured xserver-xorg-video-amdgpu:amd64 1.0.1-1build2
2016-03-11 12:41:14 status installed xserver-xorg-video-amdgpu:amd64 1.0.1-1build2
2016-03-11 12:41:14 configure xserver-xorg-video-nouveau:amd64 1:1.0.12-1build2 <aucune>
2016-03-11 12:41:14 status unpacked xserver-xorg-video-nouveau:amd64 1:1.0.12-1build2
2016-03-11 12:41:14 status half-configured xserver-xorg-video-nouveau:amd64 1:1.0.12-1build2
2016-03-11 12:41:14 status installed xserver-xorg-video-nouveau:amd64 1:1.0.12-1build2
2016-03-11 12:41:14 configure xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1build2 <aucune>
2016-03-11 12:41:14 status unpacked xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1build2
2016-03-11 12:41:14 status half-configured xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1build2
2016-03-11 12:41:14 status installed xserver-xorg-video-nouveau-dbg:amd64 1:1.0.12-1build2
2016-03-11 12:41:14 configure xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu3 <aucune>
2016-03-11 12:41:14 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:41:14 status unpacked xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu3
2016-03-11 12:41:15 status half-configured xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu3
2016-03-11 12:41:15 status installed xserver-xorg-video-intel:amd64 2:2.99.917+git20160218-1ubuntu3
2016-03-11 12:41:15 configure xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu3 <aucune>
2016-03-11 12:41:15 status unpacked xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu3
2016-03-11 12:41:15 status half-configured xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu3
2016-03-11 12:41:15 status installed xserver-xorg-video-qxl:amd64 0.1.4-3ubuntu3
2016-03-11 12:41:15 configure xserver-xorg-video-radeon:amd64 1:7.6.1-1ubuntu2 <aucune>
2016-03-11 12:41:15 status unpacked xserver-xorg-video-radeon:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:41:15 status half-configured xserver-xorg-video-radeon:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:41:15 status installed xserver-xorg-video-radeon:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:41:15 configure xserver-xorg-video-r128:amd64 6.10.0-1build2 <aucune>
2016-03-11 12:41:15 status unpacked xserver-xorg-video-r128:amd64 6.10.0-1build2
2016-03-11 12:41:15 status half-configured xserver-xorg-video-r128:amd64 6.10.0-1build2
2016-03-11 12:41:15 status installed xserver-xorg-video-r128:amd64 6.10.0-1build2
2016-03-11 12:41:15 configure xserver-xorg-video-mach64:amd64 6.9.5-1build2 <aucune>
2016-03-11 12:41:15 status unpacked xserver-xorg-video-mach64:amd64 6.9.5-1build2
2016-03-11 12:41:15 status half-configured xserver-xorg-video-mach64:amd64 6.9.5-1build2
2016-03-11 12:41:15 status installed xserver-xorg-video-mach64:amd64 6.9.5-1build2
2016-03-11 12:41:15 configure xserver-xorg-video-ati:amd64 1:7.6.1-1ubuntu2 <aucune>
2016-03-11 12:41:15 status unpacked xserver-xorg-video-ati:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:41:15 status half-configured xserver-xorg-video-ati:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:41:16 status installed xserver-xorg-video-ati:amd64 1:7.6.1-1ubuntu2
2016-03-11 12:41:16 configure xserver-xorg-video-fbdev:amd64 1:0.4.4-1build5 <aucune>
2016-03-11 12:41:16 status unpacked xserver-xorg-video-fbdev:amd64 1:0.4.4-1build5
2016-03-11 12:41:16 status half-configured xserver-xorg-video-fbdev:amd64 1:0.4.4-1build5
2016-03-11 12:41:16 status installed xserver-xorg-video-fbdev:amd64 1:0.4.4-1build5
2016-03-11 12:41:16 configure xserver-xorg-video-vesa:amd64 1:2.3.4-1build2 <aucune>
2016-03-11 12:41:16 status unpacked xserver-xorg-video-vesa:amd64 1:2.3.4-1build2
2016-03-11 12:41:16 status half-configured xserver-xorg-video-vesa:amd64 1:2.3.4-1build2
2016-03-11 12:41:16 status installed xserver-xorg-video-vesa:amd64 1:2.3.4-1build2
2016-03-11 12:41:16 configure xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu3 <aucune>
2016-03-11 12:41:16 status unpacked xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu3
2016-03-11 12:41:16 status unpacked xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu3
2016-03-11 12:41:16 status half-configured xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu3
2016-03-11 12:41:16 status installed xserver-xorg-video-vmware:amd64 1:13.1.0-2ubuntu3
2016-03-11 12:41:16 configure xserver-xorg-input-vmmouse:amd64 1:13.1.0-1ubuntu2 <aucune>
2016-03-11 12:41:16 status unpacked xserver-xorg-input-vmmouse:amd64 1:13.1.0-1ubuntu2
2016-03-11 12:41:16 status half-configured xserver-xorg-input-vmmouse:amd64 1:13.1.0-1ubuntu2
2016-03-11 12:41:16 status installed xserver-xorg-input-vmmouse:amd64 1:13.1.0-1ubuntu2
2016-03-11 12:41:17 configure xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu3 <aucune>
2016-03-11 12:41:17 status unpacked xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu3
2016-03-11 12:41:17 status half-configured xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu3
2016-03-11 12:41:17 status installed xserver-xorg-input-synaptics:amd64 1.8.2-1ubuntu3
2016-03-11 12:41:17 configure xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu3 <aucune>
2016-03-11 12:41:17 status unpacked xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu3
2016-03-11 12:41:17 status half-configured xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu3
2016-03-11 12:41:17 status installed xserver-xorg-input-wacom:amd64 1:0.32.0-0ubuntu3
2016-03-11 12:41:17 configure xserver-xorg-input-evdev:amd64 1:2.10.1-1ubuntu2 <aucune>
2016-03-11 12:41:17 status unpacked xserver-xorg-input-evdev:amd64 1:2.10.1-1ubuntu2
2016-03-11 12:41:17 status half-configured xserver-xorg-input-evdev:amd64 1:2.10.1-1ubuntu2
2016-03-11 12:41:17 status installed xserver-xorg-input-evdev:amd64 1:2.10.1-1ubuntu2
2016-03-11 12:41:17 configure seahorse-daemon:amd64 3.12.2-1 <aucune>
2016-03-11 12:41:17 status unpacked seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:41:17 status half-configured seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:41:17 status installed seahorse-daemon:amd64 3.12.2-1
2016-03-11 12:41:17 configure libcryptui0a:amd64 3.12.2-1 <aucune>
2016-03-11 12:41:17 status unpacked libcryptui0a:amd64 3.12.2-1
2016-03-11 12:41:17 status half-configured libcryptui0a:amd64 3.12.2-1
2016-03-11 12:41:18 status installed libcryptui0a:amd64 3.12.2-1
2016-03-11 12:41:18 configure evolution-common:all 3.18.5.1-1ubuntu1 <aucune>
2016-03-11 12:41:18 status unpacked evolution-common:all 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status half-configured evolution-common:all 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status installed evolution-common:all 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 configure libevolution:amd64 3.18.5.1-1ubuntu1 <aucune>
2016-03-11 12:41:18 status unpacked libevolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status half-configured libevolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status installed libevolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 configure evolution:amd64 3.18.5.1-1ubuntu1 <aucune>
2016-03-11 12:41:18 status unpacked evolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status unpacked evolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status half-configured evolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status installed evolution:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 configure evolution-plugins:amd64 3.18.5.1-1ubuntu1 <aucune>
2016-03-11 12:41:18 status unpacked evolution-plugins:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status half-configured evolution-plugins:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:18 status installed evolution-plugins:amd64 3.18.5.1-1ubuntu1
2016-03-11 12:41:19 configure ubuntu-ui-toolkit-theme:amd64 1.3.1872+16.04.20160308-0ubuntu1 <aucune>
2016-03-11 12:41:19 status unpacked ubuntu-ui-toolkit-theme:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 status half-configured ubuntu-ui-toolkit-theme:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 status installed ubuntu-ui-toolkit-theme:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 configure libubuntugestures5:amd64 1.3.1872+16.04.20160308-0ubuntu1 <aucune>
2016-03-11 12:41:19 status unpacked libubuntugestures5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 status half-configured libubuntugestures5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 status installed libubuntugestures5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 configure libubuntutoolkit5:amd64 1.3.1872+16.04.20160308-0ubuntu1 <aucune>
2016-03-11 12:41:19 status unpacked libubuntutoolkit5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 status half-configured libubuntutoolkit5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 status installed libubuntutoolkit5:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 configure qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1872+16.04.20160308-0ubuntu1 <aucune>
2016-03-11 12:41:19 status unpacked qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 status half-configured qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 status installed qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 1.3.1872+16.04.20160308-0ubuntu1
2016-03-11 12:41:19 configure qt5-image-formats-plugins:amd64 5.5.1-2build1 <aucune>
2016-03-11 12:41:19 status unpacked qt5-image-formats-plugins:amd64 5.5.1-2build1
2016-03-11 12:41:19 status half-configured qt5-image-formats-plugins:amd64 5.5.1-2build1
2016-03-11 12:41:20 status installed qt5-image-formats-plugins:amd64 5.5.1-2build1
2016-03-11 12:41:20 configure audacious-plugins-data:all 3.6.2-2build1 <aucune>
2016-03-11 12:41:20 status unpacked audacious-plugins-data:all 3.6.2-2build1
2016-03-11 12:41:20 status half-configured audacious-plugins-data:all 3.6.2-2build1
2016-03-11 12:41:20 status installed audacious-plugins-data:all 3.6.2-2build1
2016-03-11 12:41:20 configure libsndio6.1:amd64 1.1.0-2 <aucune>
2016-03-11 12:41:20 status unpacked libsndio6.1:amd64 1.1.0-2
2016-03-11 12:41:20 status half-configured libsndio6.1:amd64 1.1.0-2
2016-03-11 12:41:20 status installed libsndio6.1:amd64 1.1.0-2
2016-03-11 12:41:20 configure libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu2 <aucune>
2016-03-11 12:41:20 status unpacked libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu2
2016-03-11 12:41:20 status half-configured libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu2
2016-03-11 12:41:20 status installed libsdl2-2.0-0:amd64 2.0.4+dfsg1-2ubuntu2
2016-03-11 12:41:20 configure audacious-plugins:amd64 3.6.2-2build1 <aucune>
2016-03-11 12:41:20 status unpacked audacious-plugins:amd64 3.6.2-2build1
2016-03-11 12:41:20 status half-configured audacious-plugins:amd64 3.6.2-2build1
2016-03-11 12:41:20 status installed audacious-plugins:amd64 3.6.2-2build1
2016-03-11 12:41:20 configure libkf5kdcraw5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:41:20 status unpacked libkf5kdcraw5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:20 status half-configured libkf5kdcraw5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:21 status installed libkf5kdcraw5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:21 configure libkf5kipi-data:all 15.12.1-1ubuntu1 <aucune>
2016-03-11 12:41:21 status unpacked libkf5kipi-data:all 15.12.1-1ubuntu1
2016-03-11 12:41:21 status half-configured libkf5kipi-data:all 15.12.1-1ubuntu1
2016-03-11 12:41:21 status installed libkf5kipi-data:all 15.12.1-1ubuntu1
2016-03-11 12:41:21 configure libkf5kipi30.0.0:amd64 15.12.1-1ubuntu1 <aucune>
2016-03-11 12:41:21 status unpacked libkf5kipi30.0.0:amd64 15.12.1-1ubuntu1
2016-03-11 12:41:21 status half-configured libkf5kipi30.0.0:amd64 15.12.1-1ubuntu1
2016-03-11 12:41:21 status installed libkf5kipi30.0.0:amd64 15.12.1-1ubuntu1
2016-03-11 12:41:21 configure gwenview:amd64 4:15.12.1-0ubuntu1 <aucune>
2016-03-11 12:41:21 status unpacked gwenview:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:41:21 status half-configured gwenview:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:41:21 status installed gwenview:amd64 4:15.12.1-0ubuntu1
2016-03-11 12:41:21 configure hunspell-en-gb:all 1:5.1.0-1ubuntu1 <aucune>
2016-03-11 12:41:21 status unpacked hunspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:21 status half-configured hunspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:21 status installed hunspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:21 configure myspell-en-gb:all 1:5.1.0-1ubuntu1 <aucune>
2016-03-11 12:41:21 status unpacked myspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:21 status half-configured myspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:21 status installed myspell-en-gb:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:21 configure hunspell-en-za:all 1:5.1.0-1ubuntu1 <aucune>
2016-03-11 12:41:21 status unpacked hunspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:22 status half-configured hunspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:22 status installed hunspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:22 configure myspell-en-za:all 1:5.1.0-1ubuntu1 <aucune>
2016-03-11 12:41:22 status unpacked myspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:22 status half-configured myspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:22 status installed myspell-en-za:all 1:5.1.0-1ubuntu1
2016-03-11 12:41:22 configure libfontenc-dev:amd64 1:1.1.3-1build~pie.1 <aucune>
2016-03-11 12:41:22 status unpacked libfontenc-dev:amd64 1:1.1.3-1build~pie.1
2016-03-11 12:41:22 status half-configured libfontenc-dev:amd64 1:1.1.3-1build~pie.1
2016-03-11 12:41:22 status installed libfontenc-dev:amd64 1:1.1.3-1build~pie.1
2016-03-11 12:41:22 configure libkf5gpgmepp-pthread5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:41:22 status unpacked libkf5gpgmepp-pthread5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:22 status half-configured libkf5gpgmepp-pthread5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:22 status installed libkf5gpgmepp-pthread5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:22 configure libkf5qgpgme5:amd64 15.12.1-0ubuntu1 <aucune>
2016-03-11 12:41:22 status unpacked libkf5qgpgme5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:22 status half-configured libkf5qgpgme5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:22 status installed libkf5qgpgme5:amd64 15.12.1-0ubuntu1
2016-03-11 12:41:22 configure pidgin-data:all 1:2.10.12-0ubuntu5 <aucune>
2016-03-11 12:41:22 status unpacked pidgin-data:all 1:2.10.12-0ubuntu5
2016-03-11 12:41:22 status unpacked pidgin-data:all 1:2.10.12-0ubuntu5
2016-03-11 12:41:23 status half-configured pidgin-data:all 1:2.10.12-0ubuntu5
2016-03-11 12:41:23 status installed pidgin-data:all 1:2.10.12-0ubuntu5
2016-03-11 12:41:23 configure libpurple0:amd64 1:2.10.12-0ubuntu5 <aucune>
2016-03-11 12:41:23 status unpacked libpurple0:amd64 1:2.10.12-0ubuntu5
2016-03-11 12:41:23 status half-configured libpurple0:amd64 1:2.10.12-0ubuntu5
2016-03-11 12:41:23 status installed libpurple0:amd64 1:2.10.12-0ubuntu5
2016-03-11 12:41:23 configure libxfont-dev:amd64 1:1.5.1-1 <aucune>
2016-03-11 12:41:23 status unpacked libxfont-dev:amd64 1:1.5.1-1
2016-03-11 12:41:23 status half-configured libxfont-dev:amd64 1:1.5.1-1
2016-03-11 12:41:23 status installed libxfont-dev:amd64 1:1.5.1-1
2016-03-11 12:41:23 configure oxygen5-icon-theme:all 5.18.0-0ubuntu1 <aucune>
2016-03-11 12:41:23 status unpacked oxygen5-icon-theme:all 5.18.0-0ubuntu1
2016-03-11 12:41:23 status half-configured oxygen5-icon-theme:all 5.18.0-0ubuntu1
2016-03-11 12:41:23 status installed oxygen5-icon-theme:all 5.18.0-0ubuntu1
2016-03-11 12:41:23 configure oxygen-icon-theme:all 5:5.18.0-0ubuntu1 <aucune>
2016-03-11 12:41:23 status unpacked oxygen-icon-theme:all 5:5.18.0-0ubuntu1
2016-03-11 12:41:23 status half-configured oxygen-icon-theme:all 5:5.18.0-0ubuntu1
2016-03-11 12:41:23 status installed oxygen-icon-theme:all 5:5.18.0-0ubuntu1
2016-03-11 12:41:23 configure python-pika:all 0.10.0-1 <aucune>
2016-03-11 12:41:23 status unpacked python-pika:all 0.10.0-1
2016-03-11 12:41:23 status half-configured python-pika:all 0.10.0-1
2016-03-11 12:41:24 status installed python-pika:all 0.10.0-1
2016-03-11 12:41:24 configure python-pika-pool:all 0.1.3-1ubuntu1 <aucune>
2016-03-11 12:41:24 status unpacked python-pika-pool:all 0.1.3-1ubuntu1
2016-03-11 12:41:24 status half-configured python-pika-pool:all 0.1.3-1ubuntu1
2016-03-11 12:41:24 status installed python-pika-pool:all 0.1.3-1ubuntu1
2016-03-11 12:41:24 configure python-oslo.messaging:all 4.5.0-1ubuntu1 <aucune>
2016-03-11 12:41:24 status unpacked python-oslo.messaging:all 4.5.0-1ubuntu1
2016-03-11 12:41:24 status half-configured python-oslo.messaging:all 4.5.0-1ubuntu1
2016-03-11 12:41:24 status installed python-oslo.messaging:all 4.5.0-1ubuntu1
2016-03-11 12:41:24 configure python-oslo.versionedobjects:all 1.7.0-0ubuntu1 <aucune>
2016-03-11 12:41:24 status unpacked python-oslo.versionedobjects:all 1.7.0-0ubuntu1
2016-03-11 12:41:25 status half-configured python-oslo.versionedobjects:all 1.7.0-0ubuntu1
2016-03-11 12:41:25 status installed python-oslo.versionedobjects:all 1.7.0-0ubuntu1
2016-03-11 12:41:25 configure ubuntu-gnome-wallpapers-xenial:all 16.04.1 <aucune>
2016-03-11 12:41:25 status unpacked ubuntu-gnome-wallpapers-xenial:all 16.04.1
2016-03-11 12:41:25 status half-configured ubuntu-gnome-wallpapers-xenial:all 16.04.1
2016-03-11 12:41:25 status installed ubuntu-gnome-wallpapers-xenial:all 16.04.1
2016-03-11 12:41:25 configure ubuntu-gnome-wallpapers:all 16.04.1 <aucune>
2016-03-11 12:41:25 status unpacked ubuntu-gnome-wallpapers:all 16.04.1
2016-03-11 12:41:25 status half-configured ubuntu-gnome-wallpapers:all 16.04.1
2016-03-11 12:41:25 status installed ubuntu-gnome-wallpapers:all 16.04.1
2016-03-11 12:41:25 configure xserver-xorg-dev:amd64 2:1.18.1-1ubuntu3 <aucune>
2016-03-11 12:41:25 status unpacked xserver-xorg-dev:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:41:25 status half-configured xserver-xorg-dev:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:41:25 status installed xserver-xorg-dev:amd64 2:1.18.1-1ubuntu3
2016-03-11 12:41:25 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:41:25 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:41:25 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:41:26 startup packages configure
2016-03-11 12:42:01 startup packages remove
2016-03-11 12:42:01 status installed libsndio6.0:amd64 1.0.1-2
2016-03-11 12:42:02 remove libsndio6.0:amd64 1.0.1-2 <aucune>
2016-03-11 12:42:02 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:42:02 status half-configured libsndio6.0:amd64 1.0.1-2
2016-03-11 12:42:02 status half-installed libsndio6.0:amd64 1.0.1-2
2016-03-11 12:42:02 status config-files libsndio6.0:amd64 1.0.1-2
2016-03-11 12:42:02 status config-files libsndio6.0:amd64 1.0.1-2
2016-03-11 12:42:02 status config-files libsndio6.0:amd64 1.0.1-2
2016-03-11 12:42:02 status not-installed libsndio6.0:amd64 <aucune>
2016-03-11 12:42:02 status installed qtdeclarative5-qtfeedback-plugin:amd64 5.0~git20130529-0ubuntu12build0pie.4
2016-03-11 12:42:03 remove qtdeclarative5-qtfeedback-plugin:amd64 5.0~git20130529-0ubuntu12build0pie.4 <aucune>
2016-03-11 12:42:03 status half-configured qtdeclarative5-qtfeedback-plugin:amd64 5.0~git20130529-0ubuntu12build0pie.4
2016-03-11 12:42:03 status half-installed qtdeclarative5-qtfeedback-plugin:amd64 5.0~git20130529-0ubuntu12build0pie.4
2016-03-11 12:42:03 status config-files qtdeclarative5-qtfeedback-plugin:amd64 5.0~git20130529-0ubuntu12build0pie.4
2016-03-11 12:42:03 status config-files qtdeclarative5-qtfeedback-plugin:amd64 5.0~git20130529-0ubuntu12build0pie.4
2016-03-11 12:42:03 status config-files qtdeclarative5-qtfeedback-plugin:amd64 5.0~git20130529-0ubuntu12build0pie.4
2016-03-11 12:42:03 status not-installed qtdeclarative5-qtfeedback-plugin:amd64 <aucune>
2016-03-11 12:42:03 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:42:03 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:42:04 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:42:04 startup packages configure
2016-03-11 12:57:04 startup packages remove
2016-03-11 12:57:04 status installed fglrx-core:amd64 2:15.201-0ubuntu7
2016-03-11 12:57:14 remove fglrx-core:amd64 2:15.201-0ubuntu7 <aucune>
2016-03-11 12:57:14 status triggers-pending libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:57:14 status half-configured fglrx-core:amd64 2:15.201-0ubuntu7
2016-03-11 12:57:24 status half-installed fglrx-core:amd64 2:15.201-0ubuntu7
2016-03-11 12:57:24 status triggers-pending initramfs-tools:all 0.122ubuntu6
2016-03-11 12:57:24 status config-files fglrx-core:amd64 2:15.201-0ubuntu7
2016-03-11 12:57:24 status config-files fglrx-core:amd64 2:15.201-0ubuntu7
2016-03-11 12:57:24 trigproc libc-bin:amd64 2.21-0ubuntu7~pie.1 <aucune>
2016-03-11 12:57:24 status half-configured libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:57:25 status installed libc-bin:amd64 2.21-0ubuntu7~pie.1
2016-03-11 12:57:25 trigproc initramfs-tools:all 0.122ubuntu6 <aucune>
2016-03-11 12:57:25 status half-configured initramfs-tools:all 0.122ubuntu6
2016-03-11 12:57:37 status installed initramfs-tools:all 0.122ubuntu6
2016-03-11 12:57:37 startup packages configure
```

```
freeman@Sniper-one:~$ journalctl -b
-- Logs begin at ven. 2016-03-11 12:58:56 CET, end at ven. 2016-03-11 14:55:47 CET. --
mars 11 12:58:56 Sniper-one systemd-journald[319]: Runtime journal (/run/log/journal/) is 8.0M, max 78.5M, 70.5M free.
mars 11 12:58:56 Sniper-one kernel: microcode: CPU0 microcode updated early to revision 0x19, date = 2013-06-21
mars 11 12:58:56 Sniper-one kernel: Initializing cgroup subsys cpuset
mars 11 12:58:56 Sniper-one kernel: Initializing cgroup subsys cpu
mars 11 12:58:56 Sniper-one kernel: Initializing cgroup subsys cpuacct
mars 11 12:58:56 Sniper-one kernel: Linux version 4.4.0-6-generic (buildd@lgw01-21) (gcc version 5.3.1 20160211 (Ubuntu 5.3.1-8ubuntu3) ) #21-Ubuntu SMP Tue Feb 16 20:32:27 UTC 2016 (Ubuntu 
mars 11 12:58:56 Sniper-one kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-6-generic root=UUID=7acfe1ef-c520-4721-8eaf-c0fdf57ca106 ro persistent quiet splash crashkernel=384M-:128M cr
mars 11 12:58:56 Sniper-one kernel: KERNEL supported cpus:
mars 11 12:58:56 Sniper-one kernel:   Intel GenuineIntel
mars 11 12:58:56 Sniper-one kernel:   AMD AuthenticAMD
mars 11 12:58:56 Sniper-one kernel:   Centaur CentaurHauls
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Legacy x87 FPU detected.
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
lines 14-18
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
lines 14-20
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
lines 14-21
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
lines 14-22
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
lines 14-23

mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
lines 14-24
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
lines 14-25
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
lines 14-27

mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
lines 14-28
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
lines 14-29
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
lines 14-30

mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
lines 14-31
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
lines 14-32

mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
lines 14-33
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
lines 14-34
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
lines 14-36

mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
lines 14-37
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
lines 14-38


mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
lines 14-40
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
lines 14-41

mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
mars 11 12:58:56 Sniper-one kernel:   2 base 100000000 mask F00000000 write-back
lines 14-42
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
mars 11 12:58:56 Sniper-one kernel:   2 base 100000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   3 base 200000000 mask FE0000000 write-back
lines 14-43
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
mars 11 12:58:56 Sniper-one kernel:   2 base 100000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   3 base 200000000 mask FE0000000 write-back
mars 11 12:58:56 Sniper-one kernel:   4 disabled
lines 14-44
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
mars 11 12:58:56 Sniper-one kernel:   2 base 100000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   3 base 200000000 mask FE0000000 write-back
mars 11 12:58:56 Sniper-one kernel:   4 disabled
mars 11 12:58:56 Sniper-one kernel:   5 disabled
lines 14-45
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
mars 11 12:58:56 Sniper-one kernel:   2 base 100000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   3 base 200000000 mask FE0000000 write-back
mars 11 12:58:56 Sniper-one kernel:   4 disabled
mars 11 12:58:56 Sniper-one kernel:   5 disabled
mars 11 12:58:56 Sniper-one kernel:   6 disabled
lines 14-46
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
mars 11 12:58:56 Sniper-one kernel:   2 base 100000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   3 base 200000000 mask FE0000000 write-back
mars 11 12:58:56 Sniper-one kernel:   4 disabled
mars 11 12:58:56 Sniper-one kernel:   5 disabled
mars 11 12:58:56 Sniper-one kernel:   6 disabled
mars 11 12:58:56 Sniper-one kernel:   7 disabled
lines 14-47
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
mars 11 12:58:56 Sniper-one kernel:   2 base 100000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   3 base 200000000 mask FE0000000 write-back
mars 11 12:58:56 Sniper-one kernel:   4 disabled
mars 11 12:58:56 Sniper-one kernel:   5 disabled
mars 11 12:58:56 Sniper-one kernel:   6 disabled
mars 11 12:58:56 Sniper-one kernel:   7 disabled
mars 11 12:58:56 Sniper-one kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
lines 14-48
mars 11 12:58:56 Sniper-one kernel: x86/fpu: Using 'lazy' FPU context switches.
mars 11 12:58:56 Sniper-one kernel: e820: BIOS-provided physical RAM map:
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000dfecffff] usable
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed0000-0x00000000dfed0fff] ACPI NVS
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfed1000-0x00000000dfedffff] ACPI data
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000dfee0000-0x00000000dfefffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
mars 11 12:58:56 Sniper-one kernel: BIOS-e820: [mem 0x0000000100000000-0x000000021fffffff] usable
mars 11 12:58:56 Sniper-one kernel: NX (Execute Disable) protection: active
mars 11 12:58:56 Sniper-one kernel: SMBIOS 2.4 present.
mars 11 12:58:56 Sniper-one kernel: DMI: Gigabyte Technology Co., Ltd. G1.Sniper/G1.Sniper, BIOS F1 01/17/2011
mars 11 12:58:56 Sniper-one kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
mars 11 12:58:56 Sniper-one kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
mars 11 12:58:56 Sniper-one kernel: e820: last_pfn = 0x220000 max_arch_pfn = 0x400000000
mars 11 12:58:56 Sniper-one kernel: MTRR default type: uncachable
mars 11 12:58:56 Sniper-one kernel: MTRR fixed ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   00000-9FFFF write-back
mars 11 12:58:56 Sniper-one kernel:   A0000-BFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   C0000-CFFFF write-protect
mars 11 12:58:56 Sniper-one kernel:   D0000-EFFFF uncachable
mars 11 12:58:56 Sniper-one kernel:   F0000-FFFFF write-through
mars 11 12:58:56 Sniper-one kernel: MTRR variable ranges enabled:
mars 11 12:58:56 Sniper-one kernel:   0 base 000000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   1 base 0E0000000 mask FE0000000 uncachable
mars 11 12:58:56 Sniper-one kernel:   2 base 100000000 mask F00000000 write-back
mars 11 12:58:56 Sniper-one kernel:   3 base 200000000 mask FE0000000 write-back
mars 11 12:58:56 Sniper-one kernel:   4 disabled
mars 11 12:58:56 Sniper-one kernel:   5 disabled
mars 11 12:58:56 Sniper-one kernel:   6 disabled
mars 11 12:58:56 Sniper-one kernel:   7 disabled
mars 11 12:58:56 Sniper-one kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
mars 11 12:58:56 Sniper-one kernel: original variable MTRRs
lines 14-49


```

---

### Post by fantab on 2016-03-18
The issue/bug has resolved since kernel 4.4.0.13. 
The kernel boots normally and has upgraded to 4.4.0.14 smoothly.

---

