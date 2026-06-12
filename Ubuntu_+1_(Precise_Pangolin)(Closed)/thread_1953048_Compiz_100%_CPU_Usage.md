---
title: "Compiz 100% CPU Usage"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jeffsf on 2012-04-05
I built an AMD A8-3870 system last week and fresh-installed Precise Beta on it (and have kept it current with apt-get). 

The compiz process periodically gets to the point where it is consuming  100% of the CPU, even though there is no one at the console (I am ssh-ed  in remotely).

I believe I am running the fglrx-update drivers (though Jockey still crashes when trying to enable them, apparently a known issue).

Previously there was a way to disable effects, but I do not see a similar option with Precise.

kill -9 on the compiz process usually temporarily resolves the issue, but it tends to reoccur later in the day. 
Here, top output, a few minutes after a kill:
```
[FONT=Courier New]top - 10:01:09 up 20:16,  3 users,  load average: 6.24, 6.45, 6.90
Tasks: 256 total,   2 running, 251 sleeping,   0 stopped,   3 zombie
Cpu(s):  4.2%us, 22.8%sy,  0.0%ni,  5.9%id, 67.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   7659620k total,  7422672k used,   236948k free,      260k buffers
Swap:  7860220k total,  3942372k used,  3917848k free,    69952k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                       
15853 jeff      20   0 1278m  55m  11m R  100  0.7  11:20.41 compiz                                                                                                         
10224 vnc       20   0  602m 7388 2804 S    2  0.1  25:33.59 psensor                                                                                                        
10858 vnc       20   0 9499m 5.9g   20 D    1 80.7  58:41.38 chromium-browse     [/FONT]
```
Any suggestions on how to resolve this?

Thanks!

```
[FONT=Courier New]jeff@port7:~$ uname -a
Linux port7 3.2.0-21-generic #34-Ubuntu SMP Fri Mar 30 04:25:35 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux[/FONT]
```
(excerpts from /var/log/dmesg)```

[FONT=Courier New][    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-A75M-D2H/GA-A75M-D2H, BIOS F1 06/09/2011

[    0.057137] CPU0: AMD A8-3870 APU with Radeon(tm) HD Graphics stepping 00[/FONT]
```
(excerpts from /var/log/Xorg.0.log)
```
[FONT=Courier New][    25.646] (II) LoadModule: "fglrx"
[    25.646] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    27.423] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    27.668]    compiled for 1.4.99.906, module version = 8.96.4
[    27.668]    Module class: X.Org Video Driver
[    27.708] (II) Loading sub module "fglrxdrm"
[    27.708] (II) LoadModule: "fglrxdrm"
[    27.708] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    28.357] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    28.357]    compiled for 1.4.99.906, module version = 8.96.4
[    28.384] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    28.384] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[    28.384] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:50
[    28.384] (++) using VT number 7
[    28.384] (WW) Falling back to old probe method for fglrx
[    28.641] (II) Loading PCS database from /etc/ati/amdpcsdb
[    28.677] (--) Chipset Supported AMD Graphics Processor (0x9640) found
[    28.685] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[    28.687] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    28.688] (II) AMD Video driver is signed
[    28.688] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    28.688] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    28.688] (II) fglrx(0): pEnt->device->identifier=0x7fa671863d10
[    28.688] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    28.688] (II) Loading sub module "vgahw"
[    28.688] (II) LoadModule: "vgahw"
[    28.688] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    28.707] (II) Module vgahw: vendor="X.Org Foundation"
[    28.707]    compiled for 1.11.3, module version = 0.1.0
[    28.707]    ABI class: X.Org Video Driver, version 11.0
[    28.707] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    28.707] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    28.707] (==) fglrx(0): Default visual is TrueColor
[    28.707] (**) fglrx(0): Option "DPMS" "true"
[    28.707] (==) fglrx(0): RGB weight 888
[    28.707] (II) fglrx(0): Using 8 bits per RGB 
[    28.707] (==) fglrx(0): Buffer Tiling is ON
[    28.708] (II) Loading sub module "fglrxdrm"
[    28.708] (II) LoadModule: "fglrxdrm"
[    28.708] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    28.708] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    28.708]    compiled for 1.4.99.906, module version = 8.96.4
[    28.744] ukiDynamicMajor: found major device number 250
[    28.744] ukiDynamicMajor: found major device number 250
[    28.744] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    28.744] ukiOpenDevice: node name is /dev/ati/card0
[    28.744] ukiOpenDevice: open result is 12, (OK)
[    28.744] ukiOpenByBusid: ukiOpenMinor returns 12
[    28.745] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    28.745] (**) fglrx(0): NoAccel = NO
[    28.745] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    28.745] (--) fglrx(0): Chipset: "AMD Radeon HD 6550D" (Chipset = 0x9640)
[    28.745] (--) fglrx(0): (PciSubVendor = 0x1458, PciSubDevice = 0xd000)
[    28.745] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    28.745] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    28.745] (--) fglrx(0): MMIO registers at 0xfdfc0000
[    28.745] (--) fglrx(0): I/O port at 0x0000f800
[    28.745] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    29.088] (II) fglrx(0): AC Adapter is used
[    29.152] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    29.171] (II) Loading sub module "vbe"
[    29.171] (II) LoadModule: "vbe"
[    29.196] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    29.208] (II) Module vbe: vendor="X.Org Foundation"
[    29.208]    compiled for 1.11.3, module version = 1.1.0
[    29.208]    ABI class: X.Org Video Driver, version 11.0
[    29.208] (II) fglrx(0): VESA BIOS detected
[    29.208] (II) fglrx(0): VESA VBE Version 3.0
[    29.208] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    29.208] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    29.208] (II) fglrx(0): VESA VBE OEM Software Rev: 12.43
[    29.208] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    29.208] (II) fglrx(0): VESA VBE OEM Product: SUMO
[    29.208] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    29.214] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    29.214] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
[    29.214] (II) fglrx(0): PCIE card detected
[    29.214] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    29.214] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    29.219] (II) fglrx(0): Using adapter: 0:1.0.
[    29.613] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    29.654] (II) fglrx(0): Interrupt handler installed at IRQ 53.
[    29.654] (II) fglrx(0): RandR 1.2 support is enabled!
[    29.654] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    29.654] (==) fglrx(0): Center Mode is disabled 
[    29.654] (II) Loading sub module "fb"
[    29.654] (II) LoadModule: "fb"
[    29.655] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.866] (II) Module fb: vendor="X.Org Foundation"
[    29.866]    compiled for 1.11.3, module version = 1.0.0
[    29.866]    ABI class: X.Org ANSI C Emulation, version 0.4
[    29.866] (II) Loading sub module "ddc"
[    29.866] (II) LoadModule: "ddc"
[    29.866] (II) Module "ddc" already built-in
[    30.334] (II) fglrx(0): Finished Initialize PPLIB!
[    30.352] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    30.352] (II) fglrx(0): Output CRT1 has no monitor section
[    30.352] (II) Loading sub module "ddc"
[    30.352] (II) LoadModule: "ddc"
[    30.352] (II) Module "ddc" already built-in
[    30.352] (II) fglrx(0): Connected Display0: DFP1[/FONT]
```Monitor is a Samsung running 1920x1280 through DVI

---

### Post by cariboo on 2012-04-05
Have you tried Unity 2D?

---

### Post by jeffsf on 2012-04-06
Using the 2D variant does seem to resolve the issue.

I'll next see what the behavior is with fglrx (base), as well as without the proprietary drivers and add to / file a bug as appropriate.

Thanks

---

### Post by dino99 on 2012-04-06
you might test the compiz plugins one by one to know which one to blame.

---

