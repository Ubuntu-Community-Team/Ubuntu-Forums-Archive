---
title: "Jack audio server runs only as root"
date: 2009-01-05
forum: Ubuntu Studio
---

### Post by jorgose on 2009-01-05
Hello, I' don't know what is wrong with jack or my rt-hardy kernel because I can' start jackd as non root user. It was working normally this morning but now I can only start it with sudo. I've just checked the /usr/security/limits.conf file and it is fine:
@audio -rtprio 99
@audio -nice -19
@audio -memlock unlimited

I'm also in the audio group.

Here is the message log:

01:01:23.835 Patchbay deactivated.
01:01:24.125 Statistics reset.
01:01:29.279 Startup script...
01:01:29.280 artsshell -q terminate
01:01:29.707 Startup script terminated with exit status=256.
01:01:29.708 JACK is starting...
01:01:29.708 /usr/bin/jackd -R -dalsa -r44100 -p256 -n2 -D -Chw:1 -Phw:1
01:01:29.713 JACK was started with PID=7215.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -67930400, from thread -67930400] (1: Operation not permitted)
cannot create engine
01:01:29.727 JACK was stopped successfully.
01:01:29.727 Post-shutdown script...
01:01:29.728 killall jackd
jackd: no process killed
01:01:30.137 Post-shutdown script terminated with exit status=256.
01:01:31.922 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

does someone have an idea what could be going on?
I should also mention that I have uninstalled pd to install pd-extended 0.40.3; the removal required that I also remove the meta-package ubuntustudio-audio (but all applications in there remained). when I try to install ubuntustudio-audio synaptic wants to install pd too.
I think ubuntustudio audio is just a collection of programs, so I don't really need it...(if I already have the programs that I want).
I'd appreciate any hint.
thanks
Jorgos

---

### Post by Stochastic on 2009-01-06
could you run ```
sudo nano /etc/udev/rules.d/40-permissions.rules
```
then look for the lines that look like ```
KERNEL=="raw1394",                      GROUP="audio"
KERNEL=="dv1394*",                      GROUP="audio"
```
and make sure they look like that (i.e. with the audio group).  If you do make a change here, then reboot your compy to reload the udev rules.

---

### Post by thorgal on 2009-01-06
could also be you have an already running jackd instance but defunct. Make sure no such process hangs :
```

pgrep jack

```

if nothing comes up, you're fine.

second thing: you know you can avoid the -Phw:1 and -Chw:1 options by simply saying
```

jackd -R -dalsa -dhw:1 -r44100 -p256 -n2

```

third: what does dmesg say ?

---

### Post by jorgose on 2009-01-06
I tried the modifications in the 40-permission.rules file("audio" instead of "video") but it din't change anything, I use a USB Soundcard(ESI U46 se) not firewire... so I put that back to "video". 
pgrep jack doesn't give any output, so i think it's fine.

This comes up with dmesg:
jorgose@ubuntulaptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.24-22-rt (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP PREEMPT RT Mon Nov 24 21:01:16 UTC 2008 (Ubuntu 2.6.24-4.6-generic)
[    0.000000] Command line: root=UUID=8ccb11cd-7974-4830-bee4-e86e93a9778c ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006ff50000 (usable)
[    0.000000]  BIOS-e820: 000000006ff50000 - 000000006ff65000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006ff65000 - 000000006ff66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006ff66000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 458576) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7CA0 checksum 0
[    0.000000] ACPI: RSDP 000F7CA0, 0024 (r2 ACRSYS)
[    0.000000] ACPI: XSDT 6FF5E351, 005C (r1 ACRSYS ACRPRDCT  6040000  LTP        0)
[    0.000000] ACPI: SLIC 6FF64ACE, 0176 (r1 ACRSYS ACRPRDCT  6040000 LOHR        0)
[    0.000000] ACPI: FACP 6FF64C44, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 6FF5E3AD, 66AD (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 6FF65FC0, 0040
[    0.000000] ACPI: SSDT 6FF64D38, 01C4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 6FF64EFC, 003C (r1 Nvidia NVDAACPI  6040000 NVDA        0)
[    0.000000] ACPI: HPET 6FF64F38, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 6FF64F70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 6FF64FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000006ff50000
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 458576) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000006ff50000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      158
[    0.000000]     0:      256 ->   458576
[    0.000000] On node 0 totalpages: 458478
[    0.000000]   DMA zone: 96 pages used for memmap
[    0.000000]   DMA zone: 1290 pages reserved
[    0.000000]   DMA zone: 2612 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10651 pages used for memmap
[    0.000000]   DMA32 zone: 443829 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 33000 bytes of per cpu data
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 446441
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=8ccb11cd-7974-4830-bee4-e86e93a9778c ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   16.228323] Marking TSC unstable due to TSCs unsynchronized
[   16.228326] time.c: Detected 1800.238 MHz processor.
[   16.232161] Console: colour VGA+ 80x25
[   16.232164] console [tty0] enabled
[   16.232182] Checking aperture...
[   16.232185] CPU 0: aperture @ 3b0000000 size 32 MB
[   16.232187] Aperture too small (32 MB)
[   16.238420] No AGP bridge found
[   16.261121] Memory: 1777568k/1834304k available (2563k kernel code, 56344k reserved, 1366k data, 348k init)
[   16.321170] Calibrating delay using timer specific routine.. 3603.18 BogoMIPS (lpj=1801593)
[   16.321222] Security Framework initialized
[   16.321229] SELinux:  Disabled at boot.
[   16.321238] AppArmor: AppArmor initialized
[   16.321241] Failure registering capabilities with primary security module.
[   16.321449] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   16.322633] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.323225] Mount-cache hash table entries: 256
[   16.323403] Initializing cgroup subsys ns
[   16.323407] Initializing cgroup subsys cpuacct
[   16.323419] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.323422] CPU: L2 Cache: 512K (64 bytes/line)
[   16.323424] CPU 0/0 -> Node 0
[   16.323426] CPU: Physical Processor ID: 0
[   16.323428] CPU: Processor Core ID: 0
[   16.323452] SMP alternatives: switching to UP code
[   16.324018] Early unpacking initramfs... done
[   16.680652] ACPI: Core revision 20070126
[   16.680744] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.102891] Using local APIC timer interrupts.
[   17.158369] APIC timer calibration result 12501658
[   17.158371] Detected 12.501 MHz APIC timer.
[   17.159013] SMP alternatives: switching to SMP code
[   17.159486] Booting processor 1/2 APIC 0x1
[   17.169706] Initializing CPU#1
[   17.230406] Calibrating delay using timer specific routine.. 3600.35 BogoMIPS (lpj=1800179)
[   17.230412] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.230415] CPU: L2 Cache: 512K (64 bytes/line)
[   17.230417] CPU 1/1 -> Node 0
[   17.230419] CPU: Physical Processor ID: 0
[   17.230421] CPU: Processor Core ID: 1
[   17.230509] AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   17.230525] AMD C1E detected late. Force timer broadcast.
[   17.230444] Brought up 2 CPUs
[   17.230562] CPU0 attaching sched-domain:
[   17.230565]  domain 0: span 03
[   17.230567]   groups: 01 02
[   17.230571]   domain 1: span 03
[   17.230572]    groups: 03
[   17.230576] CPU1 attaching sched-domain:
[   17.230578]  domain 0: span 03
[   17.230579]   groups: 02 01
[   17.230582]   domain 1: span 03
[   17.230584]    groups: 03
[   17.230915] net_namespace: 144 bytes
[   17.231427] Time: 14:12:12  Date: 01/06/09
[   17.231478] NET: Registered protocol family 16
[   17.231752] ACPI: bus type pci registered
[   17.231849] PCI: Using configuration type 1
[   17.233462] ACPI: EC: Look up EC in DSDT
[   17.237073] ACPI: Interpreter enabled
[   17.237076] ACPI: (supports S0 S3 S4 S5)
[   17.237094] ACPI: Using IOAPIC for interrupt routing
[   17.242437] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.318026] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   17.318030] ACPI: EC: driver started in interrupt mode
[   17.318098] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.319038] PCI: Transparent bridge - 0000:00:08.0
[   17.319235] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.319361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   17.319386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   17.319425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   17.359789] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 11) *10
[   17.360056] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *11)
[   17.360316] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 11) *0, disabled.
[   17.360593] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 11) *0, disabled.
[   17.360858] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   17.361119] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   17.361392] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   17.361654] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[   17.361915] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[   17.362176] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22 23) *11
[   17.362447] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22 23) *7
[   17.362713] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[   17.362981] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[   17.363241] ACPI: PCI Interrupt Link [LGPU] (IRQs 17) *10
[   17.363511] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22 23) *0, disabled.
[   17.363772] ACPI: PCI Interrupt Link [LSI0] (IRQs 20 21 22 23) *5
[   17.364037] ACPI: PCI Interrupt Link [Z00N] (IRQs 20 21 22 23) *10
[   17.364301] ACPI: PCI Interrupt Link [Z00O] (IRQs 20 21 22 23) *11
[   17.364577] ACPI: PCI Interrupt Link [LPMU] (IRQs 18) *11
[   17.364769] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.364809] pnp: PnP ACPI init
[   17.364821] ACPI: bus type pnp registered
[   17.401757] pnp: PnP ACPI: found 13 devices
[   17.401760] ACPI: ACPI bus type pnp unregistered
[   17.402074] PCI: Using ACPI for IRQ routing
[   17.402078] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.409289] NET: Registered protocol family 8
[   17.409292] NET: Registered protocol family 20
[   17.409429] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   17.409435] hpet0: 3 32-bit timers, 25000000 Hz
[   17.410533] AppArmor: AppArmor Filesystem Enabled
[   17.411280] Clockevents: could not switch to one-shot mode:<6>Clockevents: could not switch to one-shot mode: lapic is not functional.
[   17.411154]  lapic is not functional.
[   17.411157] Could not switch to high resolution mode on CPU 0
[   17.411294] Could not switch to high resolution mode on CPU 1
[   17.418329] system 00:01: ioport range 0x360-0x361 has been reserved
[   17.418333] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   17.418347] system 00:07: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.418355] system 00:0a: ioport range 0x1000-0x107f has been reserved
[   17.418358] system 00:0a: ioport range 0x1080-0x10ff has been reserved
[   17.418361] system 00:0a: ioport range 0x1400-0x147f has been reserved
[   17.418364] system 00:0a: ioport range 0x1480-0x14ff has been reserved
[   17.418367] system 00:0a: ioport range 0x1800-0x187f has been reserved
[   17.418370] system 00:0a: ioport range 0x1880-0x18ff has been reserved
[   17.418378] system 00:0c: iomem range 0xffc00000-0xffffffff could not be reserved
[   17.418382] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   17.418385] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
[   17.418388] system 00:0c: iomem range 0xfed00000-0xfed00fff has been reserved
[   17.418391] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   17.418394] system 00:0c: iomem range 0xfef00000-0xfef00fff has been reserved
[   17.418931] PCI: Bridge: 0000:00:08.0
[   17.418934]   IO window: disabled.
[   17.418937]   MEM window: d0500000-d05fffff
[   17.418940]   PREFETCH window: disabled.
[   17.418943] PCI: Bridge: 0000:00:0c.0
[   17.418945]   IO window: 4000-4fff
[   17.418947]   MEM window: d0200000-d03fffff
[   17.418950]   PREFETCH window: d0000000-d01fffff
[   17.418952] PCI: Bridge: 0000:00:0d.0
[   17.418954]   IO window: disabled.
[   17.418956]   MEM window: d0400000-d04fffff
[   17.418958]   PREFETCH window: disabled.
[   17.418969] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   17.418980] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   17.418988] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   17.419084] NET: Registered protocol family 2
[   17.454371] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   17.455502] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   17.458210] TCP bind hash table entries: 65536 (order: 10, 4194304 bytes)
[   17.460210] TCP: Hash tables configured (established 262144 bind 65536)
[   17.460214] TCP reno registered
[   17.472398] checking if image is initramfs... it is
[   18.196620] Freeing initrd memory: 7892k freed
[   18.201928] Simple Boot Flag at 0x36 set to 0x1
[   18.203056] audit: initializing netlink socket (disabled)
[   18.203078] audit(1231251132.515:1): initialized
[   18.203208] krcupreemptd setsched 0
[   18.203210]   prio = 98
[   18.203387] VFS: Disk quotas dquot_6.5.1
[   18.203415] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   18.203515] io scheduler noop registered
[   18.203517] io scheduler anticipatory registered
[   18.203520] io scheduler deadline registered
[   18.203535] io scheduler cfq registered (default)
[   18.203564] pci 0000:00:00.0: Enabling HT MSI Mapping
[   18.204742] pci 0000:00:07.0: Enabling HT MSI Mapping
[   18.204762] pci 0000:00:08.0: Enabling HT MSI Mapping
[   18.204777] pci 0000:00:09.0: Enabling HT MSI Mapping
[   18.204793] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   18.204807] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   18.204821] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   18.204835] Boot video device is 0000:00:12.0
[   18.205099] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.205123] assign_interrupt_mode Found MSI capability
[   18.205145] Allocate Port Service[0000:00:0c.0:pcie00]
[   18.205225] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.205248] assign_interrupt_mode Found MSI capability
[   18.205264] Allocate Port Service[0000:00:0d.0:pcie00]
[   18.241739] Real Time Clock Driver v1.12ac
[   18.242032] hpet_resources: 0xfed00000 is busy
[   18.242068] Linux agpgart interface v0.102
[   18.242071] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.243608] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.243694] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.243813] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[   18.282148] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.282205] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.294064] mice: PS/2 mouse device common for all mice
[   18.294116] cpuidle: using governor ladder
[   18.294193] NET: Registered protocol family 1
[   18.294280] registered taskstats version 1
[   18.294446]   Magic number: 9:71:232
[   18.294478]   hash matches device ttyv2
[   18.294578] /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   18.294582] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.294584] EDD information not available.
[   18.294593] Freeing unused kernel memory: 348k freed
[   18.331803] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.535809] fuse init (API version 7.9)
[   19.548066] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.548077] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.548135] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.548148] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   19.617912] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   19.646147] ACPI: Thermal Zone [THRM] (60 C)
[   20.028546] usbcore: registered new interface driver usbfs
[   20.028573] usbcore: registered new interface driver hub
[   20.028608] usbcore: registered new device driver usb
[   20.029724] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.030205] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   20.030228] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 23 (level, low) -> IRQ 23
[   20.030408] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   20.030422] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   20.030850] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   20.030951] ohci_hcd 0000:00:02.0: irq 23, io mem 0xd0886000
[   20.056978] SCSI subsystem initialized
[   20.082407] libata version 3.00 loaded.
[   20.083328] usb usb1: configuration #1 chosen from 1 choice
[   20.083357] hub 1-0:1.0: USB hub found
[   20.083368] hub 1-0:1.0: 5 ports detected
[   20.184693] ACPI: PCI Interrupt Link [Z00N] enabled at IRQ 22
[   20.184708] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z00N] -> GSI 22 (level, low) -> IRQ 22
[   20.184882] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   20.184891] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   20.184965] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[   20.191904] ohci_hcd 0000:00:04.0: irq 22, io mem 0xd0887000
[   20.245209] usb usb2: configuration #1 chosen from 1 choice
[   20.245245] hub 2-0:1.0: USB hub found
[   20.245256] hub 2-0:1.0: 5 ports detected
[   20.346440] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[   20.346454] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 21 (level, low) -> IRQ 21
[   20.346615] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   20.346624] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   20.346689] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[   20.346731] ehci_hcd 0000:00:02.1: debug port 1
[   20.346735] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   20.352104] ehci_hcd 0000:00:02.1: irq 21, io mem 0xd0889000
[   20.444654] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   20.450786] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.450971] usb usb3: configuration #1 chosen from 1 choice
[   20.451006] hub 3-0:1.0: USB hub found
[   20.451018] hub 3-0:1.0: 5 ports detected
[   20.552393] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 20
[   20.552407] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z00O] -> GSI 20 (level, low) -> IRQ 20
[   20.552651] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   20.552659] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   20.552740] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[   20.552778] ehci_hcd 0000:00:04.1: debug port 1
[   20.552782] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   20.552991] ehci_hcd 0000:00:04.1: irq 20, io mem 0xd0889400
[   20.559571] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.559760] usb usb4: configuration #1 chosen from 1 choice
[   20.559796] hub 4-0:1.0: USB hub found
[   20.559805] hub 4-0:1.0: 5 ports detected
[   20.660658] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   20.661146] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[   20.661150] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 23 (level, low) -> IRQ 23
[   20.661157] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.126607] usb 3-3: new high speed USB device using ehci_hcd and address 3
[   21.173434] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:38:22:f1:e5
[   21.173441] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   21.178156] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   21.178171] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   21.234759] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   21.240277] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[d0500000-d05007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   21.245217] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 22
[   21.245224] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 22 (level, low) -> IRQ 22
[   21.245266] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   21.245278] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[   21.249957] ahci 0000:00:09.0: version 3.0
[   21.249973] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 22 (level, low) -> IRQ 22
[   21.538577] usb 3-3: configuration #1 chosen from 1 choice
[   21.845684] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   22.045473] usb 1-2: configuration #1 chosen from 1 choice
[   22.096529] usbcore: registered new interface driver hiddev
[   22.106406] hiddev96hidraw0: USB HID v1.00 Device [ESI U46  ] on usb-0000:00:02.0-2
[   22.106431] usbcore: registered new interface driver usbhid
[   22.106435] /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   22.249096] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   22.249103] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[   22.249108] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.249458] scsi0 : ahci
[   22.249849] scsi1 : ahci
[   22.250066] scsi2 : ahci
[   22.250298] scsi3 : ahci
[   22.250420] ata1: SATA max UDMA/133 abar m8192@0xd0884000 port 0xd0884100 irq 509
[   22.250423] ata2: SATA max UDMA/133 abar m8192@0xd0884000 port 0xd0884180 irq 509
[   22.250426] ata3: SATA max UDMA/133 abar m8192@0xd0884000 port 0xd0884200 irq 509
[   22.250429] ata4: SATA max UDMA/133 abar m8192@0xd0884000 port 0xd0884280 irq 509
[   22.500887] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f77ba4061bb]
[   22.858195] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.911967] ata1.00: ATA-7: WDC WD1600BEVS-00RST0, 04.01G04, max UDMA/133
[   22.911972] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   22.912774] ata1.00: configured for UDMA/133
[   23.216669] ata2: SATA link down (SStatus 0 SControl 300)
[   23.521219] ata3: SATA link down (SStatus 0 SControl 300)
[   23.825780] ata4: SATA link down (SStatus 0 SControl 300)
[   23.825926] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 04.0 PQ: 0 ANSI: 5
[   23.826794] pata_amd 0000:00:06.0: version 0.3.10
[   23.826848] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   23.831815] scsi4 : pata_amd
[   23.832590] scsi5 : pata_amd
[   23.833236] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   23.833239] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   23.837025] Driver 'sd' needs updating - please use bus_type methods
[   23.837139] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   23.837155] sd 0:0:0:0: [sda] Write Protect is off
[   23.837158] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.837183] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.837247] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   23.837261] sd 0:0:0:0: [sda] Write Protect is off
[   23.837263] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.837286] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.837293]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[   23.927708] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.932291] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.137592] ata5.00: ATAPI: Optiarc DVD RW AD-7560A, DX06, max UDMA/33
[   24.294301] ata5.00: configured for UDMA/33
[   24.294340] ata6: port disabled. ignoring.
[   24.295224] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560A  DX06 PQ: 0 ANSI: 5
[   24.295321] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   24.303210] Driver 'sr' needs updating - please use bus_type methods
[   24.311257] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.311264] Uniform CD-ROM driver Revision: 3.20
[   24.311335] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   24.578288] Attempting manual resume
[   24.578293] swsusp: Resume From Partition 8:6
[   24.578295] PM: Checking swsusp image.
[   24.578488] PM: Resume from disk failed.
[   24.608997] kjournald starting.  Commit interval 5 seconds
[   24.609029] EXT3-fs: mounted filesystem with ordered data mode.
[   34.424270] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   34.826430] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.996398] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.060413] ACPI: WMI-Acer: Mapper loaded
[   35.101779] input: Power Button (FF) as /devices/virtual/input/input3
[   35.117708] ACPI: Power Button (FF) [PWRF]
[   35.117799] input: Lid Switch as /devices/virtual/input/input4
[   35.163408] ACPI: Lid Switch [LID]
[   35.163518] input: Sleep Button (CM) as /devices/virtual/input/input5
[   35.181188] ACPI: Sleep Button (CM) [SLPB]
[   35.181334] input: Power Button (CM) as /devices/virtual/input/input6
[   35.196050] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   35.196060] acer_acpi: Detected Acer WMID interface
[   35.199089] ACPI: Power Button (CM) [PWRB]
[   35.313698] nvidia: module license 'NVIDIA' taints kernel.
[   35.804073] ACPI: AC Adapter [ACAD] (on-line)
[   35.876216] eth0: no link during initialization.
[   36.093961] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04713/0x204000
[   36.188880] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 17
[   36.188894] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 17 (level, low) -> IRQ 17
[   36.188903] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   36.189105] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   36.202171] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   36.540787] ACPI: Battery Slot [BAT1] (battery present)
[   36.570823] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
[   37.256350] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   37.256366] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[   37.256376] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   37.377812] sdhci: Secure Digital Host Controller Interface driver
[   37.377818] sdhci: Copyright(c) Pierre Ossman
[   37.443823] Linux video capture interface: v2.00
[   37.608554] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (5986:0102)
[   37.652194] NET: Registered protocol family 10
[   37.652492] lo: Disabled Privacy Extensions
[   37.653046] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.688619] usbcore: registered new interface driver snd-usb-audio
[   37.689321] usbcore: registered new interface driver uvcvideo
[   37.689326] USB Video Class driver (v0.1.0)
[   37.855800] MadWifi: ath_attach: Switching rfkill capability off.
[   37.904988] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[   37.963712] ath_pci: wifi0: Atheros 5424/2424: mem=0xd0400000, irq=19
[   37.963934] sdhci: SDHCI controller found at 0000:01:04.1 [1180:0822] (rev 22)
[   37.964414] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   37.964418] ACPI: PCI Interrupt 0000:01:04.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   37.964609] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   37.964707] mmc0: SDHCI at 0xd0500800 irq 11 DMA
[   37.965346] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   37.965350] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   37.965525] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   38.597533] loop: module loaded
[   38.649051] lp: driver loaded but no devices found
[   38.851794] Adding 1020088k swap on /dev/sda6.  Priority:-1 extents:1 across:1020088k
[   39.426623] EXT3 FS on sda5, internal journal
[   40.750927] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.068329] PPP generic driver version 2.4.2
[   41.082796] NET: Registered protocol family 17
[   41.280172] NET: Registered protocol family 24
[   41.865447] No dock devices found.
[   42.282858] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[   42.282910] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   42.282918] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   42.282920] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   43.387372] ppdev: user-space parallel port driver
[   43.522810] audit(1231247559.053:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5438 profile="/usr/sbin/cupsd" namespace="default"
[   43.929133] Clocksource tsc unstable (delta = -219902095 ns)
[   44.859648] Bluetooth: Core ver 2.11
[   44.861557] NET: Registered protocol family 31
[   44.861564] Bluetooth: HCI device and connection manager initialized
[   44.861595] Bluetooth: HCI socket layer initialized
[   44.876333] Bluetooth: L2CAP ver 2.9
[   44.876340] Bluetooth: L2CAP socket layer initialized
[   44.905863] Bluetooth: RFCOMM socket layer initialized
[   44.905888] Bluetooth: RFCOMM TTY layer initialized
[   44.905890] Bluetooth: RFCOMM ver 1.8
[   45.767803] ath0: no IPv6 routers present
[   54.202032] CPU0 attaching NULL sched-domain.
[   54.202040] CPU1 attaching NULL sched-domain.
[   54.202086] CPU0 attaching sched-domain:
[   54.202089]  domain 0: span 03
[   54.202091]   groups: 01 02
[   54.202095]   domain 1: span 03
[   54.202097]    groups: 03
[   54.202099] CPU1 attaching sched-domain:
[   54.202101]  domain 0: span 03
[   54.202102]   groups: 02 01
[   54.202105]   domain 1: span 03
[   54.202106]    groups: 03 

I don't know how to interpret that...
thanks

---

### Post by thorgal on 2009-01-06
thanks for the dmesg output.

I don't see anything related to ALSA in the dmesg output. 

So can you post the result of 

```

lsmod | grep snd

```

after you have booted and logged it ?

---

### Post by jorgose on 2009-01-06
here it is:
jorgose@ubuntulaptop:~$ lsmod | grep snd
snd_rtctimer            5344  1 
snd_usb_audio         100640  0 
snd_usb_lib            21248  1 snd_usb_audio
snd_hda_intel         440920  0 
snd_pcm_oss            48032  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                93320  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12680  2 snd_usb_audio,snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            39424  0 
snd_seq_midi           10688  0 
snd_rawmidi            30240  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                64256  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              28424  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71880  15 snd_rtctimer,snd_usb_audio,snd_usb_lib,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11040  1 snd
usbcore               172208  7 uvcvideo,snd_usb_audio,snd_usb_lib,usbhid,ohci_hcd,ehci_hcd

---

### Post by thorgal on 2009-01-06
OK, you seem to have two devices:

1- onboard Intel HDA
2- USB audio device

So you have to be specific about which device. It could be that hw:1 is sometimes the intel chip and after some rebooting ends up being your USB device. Have you had any issue like this ? This would be typical.

You have to force the ALSA device index if you have problems like this. In my linux DAW, I have created a file called /etc/modprobe.d/sound in which I have put :

```

alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hdsp
options snd-hda-intel index=0
options snd-hdsp index=1

```

you should replace snd-hdsp by the ALSA USB module 'snd-usb-audio'

Then, if I understand from owners of such USB devices, you probably need to have some firmware flashed at boot time to make your USB card work. YMMV ...

---

### Post by jorgose on 2009-01-06
thanks for the quick reply! I don't think the usb device is the problem, Jack always works when i start it with sudo and it also picks the right device. it works the same with sudo qjackctl where the default settings say hw1 is the alsa driver for 'U46' my usb soundcard. Jack only doesn't get the permission to start as non root. Is there a way to give jack permanent permission to start?

---

### Post by thorgal on 2009-01-06
ah, but then, it could well be a udev rule, as Stochastic mentioned, but for USB audio device, I would have no clue what shape these rules have. Just google 'udev rule USB audio ALSA' and you may find something relevant. 

By the way, of course you belong to the 'audio' group, etc, don't you ?

just post the ouput of 

```

id

```

---

### Post by jorgose on 2009-01-06
Thanks for the tip, I'm going to look right now.
here the output of id:
jorgose@ubuntulaptop:~$ id
uid=1000(jorgose) gid=1000(jorgose) groups=4(adm),20(dialout),24(cdrom),25(floppy),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(jorgose),1001(audio)

---

### Post by thorgal on 2009-01-06
ha! gotcha :)

the audio group shall have a low ID to be able to have RT access. Something like 29 (most debian based systems use 29). A groupd ID of 1001 has no chance to have RT access, it's even further from root than your own ID (which is 1000) :lol:

---

### Post by Stochastic on 2009-01-06
I don't think that's the issue here (at least that's what my gut says), I've always operated with an audio group id of 1001 and had no troubles, though it is a good tip to change that to lower.

Can you start jack as a regular user without the realtime option enabled?
This seems to be related to [http://ubuntuforums.org/showthread.php?t=743470](http://ubuntuforums.org/showthread.php?t=743470)

My gut tells me this is a group permissions problem, maybe changing the audio group to 29 is the key, maybe a deletion of the audio group and re-creation would clear things up.

It shouldn't be a udev issue, that was me assuming it was a firewire device earlier.

---

### Post by jorgose on 2009-01-07
I wasn't able to change the group number to 29, when i try to do it the group disapears. Now i set it to 102 (it seems too that I can't asign a group number under 100). Anyway the change didn't helped. Jack do run as non user when I don't use realtime but with xruns

---

### Post by jorgose on 2009-01-07
recreating the group didn't helped too.
I also used synaptic to completely remove jackd and qjackctl, then reinstalled it, but nothing the problem persists.

---

### Post by thorgal on 2009-01-07
jorgose, could you post the following :

```

cat /etc/group

```

```

cat /etc/security/limits.conf

```

```

uname -r

```

```

cat /proc/asound/cards

```

```

ls -l /dev/snd

```

and again:
```

id

```

---

### Post by jorgose on 2009-01-08
here are the outputs:
```

jorgose@ubuntulaptop:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:jorgose
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:jorgose
fax:x:21:
voice:x:22:
cdrom:x:24:jorgose
floppy:x:25:jorgose
tape:x:26:
sudo:x:27:
dip:x:30:jorgose
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:jorgose
sasl:x:45:
plugdev:x:46:jorgose
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
dhcp:x:102:
syslog:x:103:
klog:x:104:
scanner:x:105:hplip
nvram:x:106:
fuse:x:107:jorgose
ssl-cert:x:108:
lpadmin:x:109:jorgose
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:jorgose
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
jorgose:x:1000:jorgose
audio:x:129:jorgose
jorgose@ubuntulaptop:~$ cat /etc/security/limits.conf
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4


@audio -rtprio 99
@audio -nice -10
@audio -memlock unlimited


# End of file
jorgose@ubuntulaptop:~$ uname -r
2.6.24-22-rt
jorgose@ubuntulaptop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd0880000 irq 21
 1 [default        ]: USB-Audio - U46  
                      ESI U46   at usb-0000:00:02.0-2, full speed
jorgose@ubuntulaptop:~$ ls -l /dev/snd
total 0
crw-rw----+ 1 root audio 116,  0 2009-01-08 09:25 controlC0
crw-rw----+ 1 root audio 116, 32 2009-01-08 09:25 controlC1
crw-rw----+ 1 root audio 116,  4 2009-01-08 09:25 hwC0D0
crw-rw----+ 1 root audio 116,  5 2009-01-08 09:25 hwC0D1
crw-rw----+ 1 root audio 116, 24 2009-01-08 09:25 pcmC0D0c
crw-rw----+ 1 root audio 116, 16 2009-01-08 09:25 pcmC0D0p
crw-rw----+ 1 root audio 116, 56 2009-01-08 09:25 pcmC1D0c
crw-rw----+ 1 root audio 116, 48 2009-01-08 09:25 pcmC1D0p
crw-rw----+ 1 root audio 116,  1 2009-01-08 09:25 seq
crw-rw----+ 1 root audio 116, 33 2009-01-08 09:25 timer
jorgose@ubuntulaptop:~$ id
uid=1000(jorgose) gid=1000(jorgose) groups=4(adm),20(dialout),24(cdrom),25(floppy),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),129(audio),1000(jorgose)
jorgose@ubuntulaptop:~$ 

```

---

### Post by thorgal on 2009-01-08
things look fine. The only difference I can see when I check my system is that root also belongs to the audio group. It does not seem to be the case in your configuration since you only added yourself in this group. But again, I cannot see why that would be relevant for your issue, the /dev/snd/* are read-write for the audio group. mmmmm, that's a tricky one ... I don't know ... try to add root in the audio group 

```

sudo adduser root audio

```

check /etc/group again, see if root is added next to your username at audio, and reboot. I don't expect anything to happen but who knows ? ...

---

### Post by Stochastic on 2009-01-08
Can you post the output of ```
apt-cache policy jackd
```

Also, are you able to start jack, without sudo, with the realtime flag if you use your internal card (hw:0)?

Also, can you post the output of ```
cat /etc/udev/rules.d/40-basic-permissions.rules
```
and also for good measure what's this output ```
cat /etc/udev/rules.d/40-permissions.rules | grep USB
```

---

### Post by jorgose on 2009-01-08
adding root to the audio group made no difference, in fact it was already there but I took it out to see if I still could run Jack as root and yes jack runs in realtime with sudo even if root does not belong to the audio group.
As a normal user I cannot start jack in realtime with any soundcard. Without realtime with both.
As root i can run jack in realtime with both souncards.
here are the new outputs:
```

jorgose@ubuntulaptop:~$ apt-cache policy jackd
jackd:
  Installed: 0.109.2-1ubuntu1
  Candidate: 0.109.2-1ubuntu1
  Version table:
 *** 0.109.2-1ubuntu1 0
        500 http://de.archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status
jorgose@ubuntulaptop:~$ cat /etc/udev/rules.d/40-basic-permissions.rules
# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",		MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",			MODE="0600"
KERNEL=="ptmx",				MODE="0666"
KERNEL=="tty",				MODE="0666"
LABEL="vc_end"

# Miscellaneous devices
KERNEL=="null",				MODE="0666"
KERNEL=="zero",				MODE="0666"
KERNEL=="full",				MODE="0666"
KERNEL=="random",			MODE="0666"
KERNEL=="urandom",			MODE="0666"
KERNEL=="inotify",			MODE="0666"
jorgose@ubuntulaptop:~$ cat /etc/udev/rules.d/40-basic-permissions.rules |grep USB
# USB devices (usbfs replacement)

```
thanks guys

---

### Post by thorgal on 2009-01-08
now it's turning into a bad episode of the Twighlight Zone :lol:
OK, let's see ... did you ever compile jack and install it under /usr/local ? Did you ever install more than one version of jack ?
Have you considered an upgrade to version 0.116.1 ?

I am running out of ideas ...

---

### Post by jorgose on 2009-01-08
for a couple of months i installed jackdmp over jackd (bad idea) so neither jackd or jackdmp were able to run. So i make uninstalled jackdmp and 'completely remove' jackd with synaptic (ardour, etc had to go to). Then I installed jackd again with all the programs that come along ubuntustudio-audio and I had no problems until this week, after the installation of the ia32libs and pd-extended(with many 32bit libs). 
Yesterday i also uninstalled jackd and try to compile jackdmp again. But this time I had errors in the building about paths that couldn't be found(the first time there were no issues)..So i installed jackd again and it still works realtime only for root.
I'm going to give the compilation of jackdmp another try...

---

### Post by thorgal on 2009-01-08
OK. You have a 64bit system ... I did not know.
Try jackd 0.116.1, it's been fixed for running 32bit client with a 64bit server and vice-versa, if I don't say BS. I never really got interested in this aspect of things because all my systems are 32bit.

From the jack website:
> 

JACK 0.116.1 released (netjack bugfix)
Submitted by paul on Sat, 2008-12-06 10:54.

JACK 0.116.1 is now released. It contains a critical bugfix for the netjack driver discovered last night. There are no other changes between this and 0.116.0. Apologies to any distribution packagers who jumped on the 0.116.0 release (but thanks also for your attention).
JACK 0.116.0 released
Submitted by paul on Fri, 2008-12-05 17:13.

On behalf of the JACK development community, I am happy to announce the release of JACK 0.116.0. This is an important release, because it fixes all the problems reported with 0.115.6 and now makes 0.109.2 completely obsolete. Nobody should be using 0.109.2 within a few weeks, and even that is only to allow for distributions to update.

As usual, upgrading to this new version does not require clients to be rebuilt or relinked. Packagers should note that there really are manpages for most of the "tools" clients now (unlike the claim in 0.115.6). These manpages will improve as we get closer to 1.0, as will netjack which remains a hotbed of development activity thanks to Torben.
Changes since 0.115.6

(in rough order of importance)

    * compile on OS X
    * fixed deadlock in jack when handling multiple vanishing clients
    * netjack now supports CELT codec to allow use over DSL/WAN
    * many fixes and redesign for netjack code
    * add missing changes for mixed 32/64-bit server/client support
    * make dynamic SIMD work on OS X
    * man pages for most toolkit clients
    * transport control client added to toolkit clients
    * build system notably cleaned up and stabilized 

JACK 0.115.6 released
Submitted by paul on Fri, 2008-11-28 14:10.

On behalf of all those work on JACK, I am happy to announce the release of JACK 0.115.6.
[http://jackaudio.org/downloads/jack-audio-connection-kit-0.115.6.tar.gz](http://jackaudio.org/downloads/jack-audio-connection-kit-0.115.6.tar.gz)

(corresponding to svn rev 3132)

Qualitatively speaking, this is the best and most stable version of JACK ever released. It fixes many problems with the 0.109.2 release (which in truth should probably never have been allowed out of the door), as well as improving many areas of JACK. The list of changes below summarizes the changes over the last 10 months. 


So you not only have fixes for 64bit / 32bit combinations of clients / server but also a big fat advice that 0.109.2 shall not be used at all because it's too buggy.

---

### Post by jorgose on 2009-01-08
great! thanks, i'll search for the code right now

---

### Post by jorgose on 2009-01-08
I become the same errors as when I try to compile jackdmp!!
```

cc1: error: /usr/local/include/x86_64-linux-gnu: Not a directory
cc1: error: /usr/local/include: not a directory

```
here is the complete log:
```

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = ubuntulaptop
uname -m = x86_64
uname -r = 2.6.24-22-rt
uname -s = Linux
uname -v = #1 SMP PREEMPT RT Mon Nov 24 21:01:16 UTC 2008

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2116: checking build system type
configure:2134: result: x86_64-unknown-linux-gnu
configure:2156: checking host system type
configure:2171: result: x86_64-unknown-linux-gnu
configure:2193: checking target system type
configure:2208: result: x86_64-unknown-linux-gnu
configure:2286: checking for a BSD-compatible install
configure:2342: result: /usr/bin/install -c
configure:2353: checking whether build environment is sane
configure:2396: result: yes
configure:2424: checking for a thread-safe mkdir -p
configure:2463: result: /bin/mkdir -p
configure:2476: checking for gawk
configure:2506: result: no
configure:2476: checking for mawk
configure:2492: found /usr/bin/mawk
configure:2503: result: mawk
configure:2514: checking whether make sets $(MAKE)
configure:2535: result: yes
configure:2723: checking whether to enable maintainer-specific portions of Makefiles
configure:2732: result: no
configure:2847: checking for gcc
configure:2863: found /usr/bin/gcc
configure:2874: result: gcc
configure:3112: checking for C compiler version
configure:3119: gcc --version >&5
gcc (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3122: $? = 0
configure:3129: gcc -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
configure:3132: $? = 0
configure:3139: gcc -V >&5
gcc: '-V' option must have argument
configure:3142: $? = 1
configure:3165: checking for C compiler default output file name
configure:3192: gcc    conftest.c  >&5
cc1: error: /usr/local/include/x86_64-linux-gnu: Not a directory
cc1: error: /usr/local/include: not a directory
configure:3195: $? = 1
configure:3233: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PROTOCOL_VERSION "24"
| #define PACKAGE "jack-audio-connection-kit"
| #define VERSION "0.116.1"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3240: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=x86_64-unknown-linux-gnu
ac_cv_env_ALSA_CFLAGS_set=
ac_cv_env_ALSA_CFLAGS_value=
ac_cv_env_ALSA_LIBS_set=
ac_cv_env_ALSA_LIBS_value=
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CELT_CFLAGS_set=
ac_cv_env_CELT_CFLAGS_value=
ac_cv_env_CELT_LIBS_set=
ac_cv_env_CELT_LIBS_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBFFADO_CFLAGS_set=
ac_cv_env_LIBFFADO_CFLAGS_value=
ac_cv_env_LIBFFADO_LIBS_set=
ac_cv_env_LIBFFADO_LIBS_value=
ac_cv_env_LIBFREEBOB_CFLAGS_set=
ac_cv_env_LIBFREEBOB_CFLAGS_value=
ac_cv_env_LIBFREEBOB_LIBS_set=
ac_cv_env_LIBFREEBOB_LIBS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_SAMPLERATE_CFLAGS_set=
ac_cv_env_SAMPLERATE_CFLAGS_value=
ac_cv_env_SAMPLERATE_LIBS_set=
ac_cv_env_SAMPLERATE_LIBS_value=
ac_cv_env_SNDFILE_CFLAGS_set=
ac_cv_env_SNDFILE_CFLAGS_value=
ac_cv_env_SNDFILE_LIBS_set=
ac_cv_env_SNDFILE_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=x86_64-unknown-linux-gnu
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes
ac_cv_target=x86_64-unknown-linux-gnu

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/jorgose/sources/jack-audio-connection-kit-0.116.1/config/missing --run aclocal-1.10'
ADDON_DIR=''
ALSA_CFLAGS=''
ALSA_LIBS=''
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/jorgose/sources/jack-audio-connection-kit-0.116.1/config/missing --run tar'
AR=''
AUTOCONF='${SHELL} /home/jorgose/sources/jack-audio-connection-kit-0.116.1/config/missing --run autoconf'
AUTOHEADER='${SHELL} /home/jorgose/sources/jack-audio-connection-kit-0.116.1/config/missing --run autoheader'
AUTOMAKE='${SHELL} /home/jorgose/sources/jack-audio-connection-kit-0.116.1/config/missing --run automake-1.10'
AWK='mawk'
CC='gcc'
CCDEPMODE=''
CELT_CFLAGS=''
CELT_LIBS=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CXX=''
CXXCPP=''
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFAULT_TMP_DIR=''
DEFS=''
DEPDIR=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
F77=''
FFLAGS=''
GREP=''
HAVE_ALSA_FALSE=''
HAVE_ALSA_MIDI_FALSE=''
HAVE_ALSA_MIDI_TRUE=''
HAVE_ALSA_TRUE=''
HAVE_CAPABILITIES=''
HAVE_CELT_FALSE=''
HAVE_CELT_TRUE=''
HAVE_COREAUDIO_FALSE=''
HAVE_COREAUDIO_TRUE=''
HAVE_DOXYGEN=''
HAVE_DOXYGEN_FALSE=''
HAVE_DOXYGEN_TRUE=''
HAVE_FIREWIRE_FALSE=''
HAVE_FIREWIRE_TRUE=''
HAVE_FREEBOB_FALSE=''
HAVE_FREEBOB_TRUE=''
HAVE_OSS_FALSE=''
HAVE_OSS_TRUE=''
HAVE_PA_FALSE=''
HAVE_PA_TRUE=''
HAVE_PPOLL_FALSE=''
HAVE_PPOLL_TRUE=''
HAVE_READLINE_FALSE=''
HAVE_READLINE_TRUE=''
HAVE_SAMPLERATE_FALSE=''
HAVE_SAMPLERATE_TRUE=''
HAVE_SNDFILE_FALSE=''
HAVE_SNDFILE_TRUE=''
HAVE_SUN_FALSE=''
HAVE_SUN_TRUE=''
HTML_DIR=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
JACK_API_MAJOR_VERSION=''
JACK_API_MICRO_VERSION=''
JACK_API_MINOR_VERSION=''
JACK_CFLAGS=''
JACK_CORE_CFLAGS=''
JACK_MAJOR_VERSION='0'
JACK_MICRO_VERSION='1'
JACK_MINOR_VERSION='116'
JACK_PROTOCOL_VERSION='24'
JACK_RELEASE='0-116-1'
JACK_SEMAPHORE_KEY=''
JACK_SO_VERSION='0:28:0'
JACK_VERSION='0.116.1'
LDFLAGS=''
LIBFFADO_CFLAGS=''
LIBFFADO_LIBS=''
LIBFREEBOB_CFLAGS=''
LIBFREEBOB_LIBS=''
LIBOBJS=''
LIBS=''
LIBTOOL=''
LN_S=''
LTLIBOBJS=''
MAINT='#'
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAKEINFO='${SHELL} /home/jorgose/sources/jack-audio-connection-kit-0.116.1/config/missing --run makeinfo'
OBJEXT=''
OS_LDFLAGS=''
PACKAGE='jack-audio-connection-kit'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PA_LIBS=''
PKG_CONFIG=''
RANLIB=''
READLINE_DEPS=''
SAMPLERATE_CFLAGS=''
SAMPLERATE_LIBS=''
SED=''
SET_MAKE=''
SHELL='/bin/bash'
SIMD_CFLAGS=''
SNDFILE_CFLAGS=''
SNDFILE_LIBS=''
STRIP=''
STRIPPED_JACKD_FALSE=''
STRIPPED_JACKD_TRUE=''
USE_CAPABILITIES_FALSE=''
USE_CAPABILITIES_TRUE=''
USE_POSIX_SHM_FALSE=''
USE_POSIX_SHM_TRUE=''
VERSION='0.116.1'
ac_ct_CC='gcc'
ac_ct_CXX=''
ac_ct_F77=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE=''
am__fastdepCXX_TRUE=''
am__include=''
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='x86_64-unknown-linux-gnu'
build_alias=''
build_cpu='x86_64'
build_os='linux-gnu'
build_vendor='unknown'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
host='x86_64-unknown-linux-gnu'
host_alias=''
host_cpu='x86_64'
host_os='linux-gnu'
host_vendor='unknown'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /home/jorgose/sources/jack-audio-connection-kit-0.116.1/config/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target='x86_64-unknown-linux-gnu'
target_alias=''
target_cpu='x86_64'
target_os='linux-gnu'
target_vendor='unknown'

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""
#define PROTOCOL_VERSION "24"
#define PACKAGE "jack-audio-connection-kit"
#define VERSION "0.116.1"

configure: exit 77

```
i also had this problem when i was trying to compile OSCx last week, that's why i ended up compiling pd-extended to get OSC.

---

### Post by jorgose on 2009-01-19
finally works!!!! It was a very stupid thing. There **MUST** be a blank space between the minus sign and the rtprio 99. in the /etc/security/limits.conf file
this is wrong:
```

@audio -rtprio 99
@audio -nice -19
@audio -memlock unlimited

```
this is correct:
```

@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited

```
Thanks thorgal and stochastic for your help!!

---

