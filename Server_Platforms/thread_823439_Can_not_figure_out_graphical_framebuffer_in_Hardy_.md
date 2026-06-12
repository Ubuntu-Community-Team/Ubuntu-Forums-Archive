---
title: "Can not figure out graphical framebuffer in Hardy as Xen domU"
date: 2008-06-09
forum: Server Platforms
---

### Post by letsbangout on 2008-06-09
Hi all.  I'm trying to get my console text (and a getty) sent to the graphical framebuffer so I can view my domU's console over VNC.  Before anyone suggests using 'xm console', there is a specific reason I want VNC.  I do not need to run X, only to have the text console output to VNC.

The Xen dom0 and the domU kernel are hooking up fine; the VNC window I get from the dom0 (which is CentOS 5.1 with Xen 3.2.1 compiled from source) appears to be sized to 640x480.  I get /dev/fb0 installed by udev.  I've tried this with a standard Hardy image which I made with debootstrap.  I also tried it after installing xorg and xserver-xorg-video-fbdev with apt-get.

All relevant info/configs below; can anyone advise?

---
domU config:

bootloader = '/usr/bin/pygrub'
memory = 256
name = "hardy"
vif = ['mac=00:16:3e:58:70:45, vifname=np, script=vif-np']
disk = [ 'tap:aio:/home/hardy.img,xvda1,w' ]
vfb = [ 'type=vnc,vnclisten=0.0.0.0,vncdisplay=2,vncpasswd=lolz' ]

xorg.conf:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection



dmesg output:

[    0.000000] Linux version 2.6.24-19-xen (hiranotaka@noto) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #2 SMP Fri May 23 03:11:08 JST 2008 (Ubuntu 2.6.24-4.6-generic)
[    0.000000] Reserving virtual address space above 0xf5800000
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  Xen: 0000000000000000 - 0000000010800000 (usable)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 264MB LOWMEM available.
[    0.000000] NX (Execute Disable) protection: active
[1110286.193744] Entering add_active_range(0, 0, 67584) 0 entries of 256 used
[1110286.193750] Zone PFN ranges:
[1110286.193752]   DMA             0 ->     4096
[1110286.193755]   Normal       4096 ->    67584
[1110286.193757]   HighMem     67584 ->    67584
[1110286.193759] Movable zone start PFN for each node
[1110286.193761] early_node_map[1] active PFN ranges
[1110286.193763]     0:        0 ->    67584
[1110286.193767] On node 0 totalpages: 67584
[1110286.194794]   DMA zone: 32 pages used for memmap
[1110286.194797]   DMA zone: 0 pages reserved
[1110286.194801]   DMA zone: 4064 pages, LIFO batch:0
[1110286.195023]   Normal zone: 496 pages used for memmap
[1110286.195026]   Normal zone: 62992 pages, LIFO batch:15
[1110286.198373]   HighMem zone: 0 pages used for memmap
[1110286.198377]   Movable zone: 0 pages used for memmap
[1110286.198687] ACPI in unprivileged domain disabled
[1110286.198694] Allocating PCI resources starting at 20000000 (gap: 10800000:ef800000)
[1110286.198741] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 67056
[1110286.198746] Kernel command line: root=/dev/xvda1 ro console=xvc0
[1110286.198962] Enabling fast FPU save and restore... done.
[1110286.198970] Enabling unmasked SIMD FPU exception support... done.
[1110286.198974] Initializing CPU#0
[1110286.199154] PID hash table entries: 2048 (order: 11, 8192 bytes)
[1110286.199195] Xen reported: 1595.999 MHz processor.
[    0.149633] console [xvc0] enabled
[    0.149692] Console: colour dummy device 80x25
[    0.149879] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.150060] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.150117] Software IO TLB disabled
[    0.150123] vmalloc area: d1000000-f53fe000, maxmem 2d800000
[    0.152514] Memory: 239360k/270336k available (2225k kernel code, 22648k reserved, 1014k data, 212k init, 0k highmem)
[    0.152526] virtual kernel memory layout:
[    0.152527]     fixmap  : 0xf568d000 - 0xf57ff000   (1480 kB)
[    0.152528]     pkmap   : 0xf5400000 - 0xf5600000   (2048 kB)
[    0.152529]     vmalloc : 0xd1000000 - 0xf53fe000   ( 579 MB)
[    0.152530]     lowmem  : 0xc0000000 - 0xd0800000   ( 264 MB)
[    0.152531]       .init : 0xc042f000 - 0xc0464000   ( 212 kB)
[    0.152533]       .data : 0xc032c4a1 - 0xc0429d04   (1014 kB)
[    0.152534]       .text : 0xc0100000 - 0xc032c4a1   (2225 kB)
[    0.152549] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.217645] Calibrating delay using timer specific routine.. 3195.76 BogoMIPS (lpj=6391524)
[    0.217704] Security Framework initialized
[    0.217715] SELinux:  Disabled at boot.
[    0.217724] AppArmor: AppArmor initialized
[    0.217730] Failure registering capabilities with primary security module.
[    0.217749] Mount-cache hash table entries: 512
[    0.217899] CPU: After generic identify, caps: 1fc98375 00100000 00000000 00000000 00000201 00000000 00000000 00000000
[    0.217913] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.217920] CPU: L2 cache: 4096K
[    0.217925] CPU: After all inits, caps: 1fc98375 00100000 00000000 00000140 00000201 00000000 00000000 00000000
[    0.217934] Compat vDSO mapped to f57fe000.
[    0.217945] Checking 'hlt' instruction... OK.
[    0.218535] SMP alternatives: switching to UP code
[    0.219495] Freeing SMP alternatives: 11k freed
[    0.219606] Early unpacking initramfs... done
[    0.237224] Brought up 1 CPUs
[    0.237233] CPU0 attaching NULL sched-domain.
[    0.238106] net_namespace: 64 bytes
[    0.238114] failed to set up cpufreq notifier
[    0.257682] Time: 165:165:165  Date: 165/165/65
[    0.257720] NET: Registered protocol family 16
[    0.259301] Brought up 1 CPUs
[    0.259315] PCI: Fatal: No config space access function found
[    0.259319] PCI: setting up Xen PCI frontend stub
[    0.259978] ACPI: Interpreter disabled.
[    0.259986] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.260019] pnp: PnP ACPI: disabled
[    0.260311] xen_mem: Initialising balloon driver.
[    0.262670] Setting mem allocation to 262144 kiB
[    0.262878] PCI: System does not support PCI
[    0.262883] PCI: System does not support PCI
[    0.268426] NET: Registered protocol family 8
[    0.268432] NET: Registered protocol family 20
[    0.268521] AppArmor: AppArmor Filesystem Enabled
[    0.269014] NET: Registered protocol family 2
[    0.272368] Time: xen clocksource has been installed.
[    0.304379] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.304591] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.304666] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.304740] TCP: Hash tables configured (established 16384 bind 16384)
[    0.304745] TCP reno registered
[    0.316450] checking if image is initramfs... it is
[    0.344487] Freeing initrd memory: 15148k freed
[    0.345067] audit: initializing netlink socket (disabled)
[    0.345085] audit(1212324877.394:1): initialized
[    0.345254] VFS: Disk quotas dquot_6.5.1
[    0.345282] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.345390] io scheduler noop registered
[    0.345396] io scheduler anticipatory registered
[    0.345399] io scheduler deadline registered
[    0.345409] io scheduler cfq registered (default)
[    0.345663] Xen virtual console successfully installed as xvc0
[    0.345711] Event-channel device installed.
[    0.354870] Successfully initialized TPM backend driver.
[    0.357673] netfront: Initialising virtual ethernet driver.
[    0.366893] input: Xen Virtual Keyboard as /devices/virtual/input/input0
[    0.366960] input: Xen Virtual Pointer as /devices/virtual/input/input1
[    0.370452] xen-vbd: registered block device major 202
[    0.402371] rtc: IRQ 8 is not free.
[    0.403068] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.403144] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.403289] PNP: No PS/2 controller found. Probing ports directly.
[    0.404118] i8042.c: No controller found.
[    0.415885] mice: PS/2 mouse device common for all mice
[    0.415935] cpuidle: using governor ladder
[    0.416025] NET: Registered protocol family 1
[    0.416055] Using IPI No-Shortcut mode
[    0.416096] registered taskstats version 1
[    0.416111] XENBUS: Device with no driver: device/console/0
[    0.416133]   Magic number: 1:252:3141
[    0.416327] Freeing unused kernel memory: 212k freed
[    0.667989] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    1.032390] kjournald starting.  Commit interval 5 seconds
[    1.032407] EXT3-fs: mounted filesystem with ordered data mode.
[    6.253003] NET: Registered protocol family 10
[    6.253201] lo: Disabled Privacy Extensions
[    8.617060] EXT3 FS on xvda1, internal journal
[   17.077950] eth0: no IPv6 routers present

---

### Post by letsbangout on 2008-06-09
It's also worth mentioning that I've done all of the logical things at this point - various "console=" and "xencons=" kernel parameters, and echoes to various devices like /dev/tty1, /dev/xvc0, /dev/console, etc.  This seems to Just Work(tm) under CentOS 5.x when I don't specify a console= to the kernel, along with the creation of a new getty in /etc/inittab.  Please understand that I've really "been around the block" with this, having devoted several hours a day to googling for an entire week, both under 7.04, 8.10, and all sorts of Debian variants.

---

### Post by letsbangout on 2008-06-15
I'm not big on bumping threads, but it seems I'm not the only one trying to accomplish this:

[http://lists.xensource.com/archives/html/xen-users/2008-06/msg00707.html](http://lists.xensource.com/archives/html/xen-users/2008-06/msg00707.html)

Maybe it's time to approach the developers (of Ubuntu) directly?

---

