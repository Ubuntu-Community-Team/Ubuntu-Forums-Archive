---
title: "usb no longer working"
date: 2009-02-05
forum: Server Platforms
---

### Post by ethridgt on 2009-02-05
I have a box running 8.04 server edition.  It is headless.  I use it for samba, nfs, and cups.  I share one usb printer with it.  It has been working for several months now and suddenly it stopped working.  

In /var/log/messages I have tons of messages like this:
```
Feb  5 23:05:37 fs1 kernel: [  778.374077] printk: 1 messages suppressed.
Feb  5 23:05:44 fs1 kernel: [  785.556435] printk: 2 messages suppressed.
Feb  5 23:05:49 fs1 kernel: [  790.344672] printk: 1 messages suppressed.
Feb  5 23:05:54 fs1 kernel: [  795.132911] printk: 1 messages suppressed.
Feb  5 23:05:58 fs1 kernel: [  799.921149] printk: 1 messages suppressed.
Feb  5 23:06:03 fs1 kernel: [  804.709387] printk: 1 messages suppressed.
Feb  5 23:06:08 fs1 kernel: [  809.497625] printk: 1 messages suppressed.
Feb  5 23:06:13 fs1 kernel: [  814.285865] printk: 1 messages suppressed.
Feb  5 23:06:18 fs1 kernel: [  819.074105] printk: 1 messages suppressed.
```

I have disconnected all usb devices attached to the box.  I've shutdown samba, nfs, & cups.  I still keep getting these messages.  When I try to run "lsusb" the terminal window hangs.  I have to kill the terminal and log back in.  

I'm at a loss as to how I should continue to trouble-shoot this issue.  Can somebody help figure out this problem?

Some info on the box:
```

$ uname -a
Linux fs1 2.6.24-23-server #1 SMP Mon Jan 26 00:55:21 UTC 2009 i686 GNU/Linux

$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


$ cat /var/log/dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-server (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:55:21 UTC 2009 (Ubuntu 2.6.24-23.48-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7f0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f7f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f3000 - 000000003f800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4e90
[    0.000000] Entering add_active_range(0, 0, 260080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   260080
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   260080
[    0.000000] On node 0 totalpages: 260080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30465 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F67F0 checksum 0
[    0.000000] ACPI: RSDP 000F67F0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 3F7F3040, 0030 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 3F7F30C0, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 3F7F3180, 3983 (r1 GBT    AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3F7F0000, 0040
[    0.000000] ACPI: MCFG 3F7F6C40, 003C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: APIC 3F7F6B80, 0068 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:b0800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 258049
[    0.000000] Kernel command line: auto BOOT_IMAGE=Linux ro root=/dev/sda1
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2660.272 MHz processor.
[   24.390181] Console: colour VGA+ 80x25
[   24.390187] console [tty0] enabled
[   24.393155] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.393589] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.422107] Memory: 1019304k/1040320k available (2258k kernel code, 20416k reserved, 1037k data, 384k init, 122816k highmem)
[   24.422182] virtual kernel memory layout:
[   24.422183]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[   24.422184]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   24.422185]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   24.422186]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.422187]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
[   24.422188]       .data : 0xc03349d9 - 0xc0437fe4   (1037 kB)
[   24.422189]       .text : 0xc0100000 - 0xc03349d9   (2258 kB)
[   24.422539] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.422664] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   24.572384] Calibrating delay using timer specific routine.. 5324.71 BogoMIPS (lpj=26623574)
[   24.572500] Security Framework initialized
[   24.572546] SELinux:  Disabled at boot.
[   24.572605] AppArmor: AppArmor initialized
[   24.572651] Failure registering capabilities with primary security module.
[   24.572705] Mount-cache hash table entries: 512
[   24.572892] Initializing cgroup subsys ns
[   24.572939] Initializing cgroup subsys cpuacct
[   24.572995] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001 00000000
[   24.573006] monitor/mwait feature present.
[   24.573050] using mwait in idle threads.
[   24.573098] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   24.573169] CPU: L2 cache: 1024K
[   24.573212] CPU: Physical Processor ID: 0
[   24.573255] CPU: Processor Core ID: 0
[   24.573298] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043180 0000651d 00000000 00000001 00000000
[   24.573309] Compat vDSO mapped to ffffe000.
[   24.573370] Checking 'hlt' instruction... OK.
[   24.612882] SMP alternatives: switching to UP code
[   24.615092] Early unpacking initramfs... done
[   24.926237] ACPI: Core revision 20070126
[   24.926332] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.928832] CPU0: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[   24.928946] SMP alternatives: switching to SMP code
[   24.929929] Booting processor 1/1 eip 3000
[   24.940252] Initializing CPU#1
[   25.081148] Calibrating delay using timer specific routine.. 5320.57 BogoMIPS (lpj=26602882)
[   25.081158] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001 00000000
[   25.081166] monitor/mwait feature present.
[   25.081172] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   25.081174] CPU: L2 cache: 1024K
[   25.081176] CPU: Physical Processor ID: 0
[   25.081178] CPU: Processor Core ID: 1
[   25.081179] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043180 0000651d 00000000 00000001 00000000
[   25.081551] CPU1: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[   25.081985] Total of 2 processors activated (10645.29 BogoMIPS).
[   25.082185] ENABLING IO-APIC IRQs
[   25.082408] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   25.300733] checking TSC synchronization [CPU#0 -> CPU#1]:
[   25.320760] Measured 20 cycles TSC warp between CPUs, turning off TSC clock.
[   25.320809] Marking TSC unstable due to: check_tsc_sync_source failed.
[   25.320877] Brought up 2 CPUs
[   25.320946] CPU0 attaching sched-domain:
[   25.320950]  domain 0: span 03
[   25.320952]   groups: 01 02
[   25.320957] CPU1 attaching sched-domain:
[   25.320959]  domain 0: span 03
[   25.320961]   groups: 02 01
[   25.321214] net_namespace: 64 bytes
[   25.321263] Booting paravirtualized kernel on bare hardware
[   25.321972] Time:  4:06:59  Date: 02/06/09
[   25.322043] NET: Registered protocol family 16
[   25.322351] EISA bus registered
[   25.322398] ACPI: bus type pci registered
[   25.329513] PCI: PCI BIOS revision 3.00 entry at 0xfac80, last bus=2
[   25.329561] PCI: Using configuration type 1
[   25.329609] Setting up standard PCI resources
[   25.338123] ACPI: EC: Look up EC in DSDT
[   25.342509] ACPI: Interpreter enabled
[   25.342555] ACPI: (supports S0 S1 S4 S5)
[   25.342714] ACPI: Using IOAPIC for interrupt routing
[   25.348258] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.349004] Force enabled HPET at base address 0xfed00000
[   25.349011] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   25.349060] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   25.349626] PCI: Transparent bridge - 0000:00:1e.0
[   25.349700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.349877] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   25.349966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   25.359484] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   25.359979] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.360531] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.361024] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.361515] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   25.362009] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.362554] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.363104] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   25.363643] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.363732] pnp: PnP ACPI init
[   25.363782] ACPI: bus type pnp registered
[   25.366952] pnpacpi: exceeded the max number of mem resources: 12
[   25.367177] pnp: PnP ACPI: found 14 devices
[   25.367222] ACPI: ACPI bus type pnp unregistered
[   25.367270] PnPBIOS: Disabled by ACPI PNP
[   25.367613] PCI: Using ACPI for IRQ routing
[   25.367659] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.410376] NET: Registered protocol family 8
[   25.410422] NET: Registered protocol family 20
[   25.410503] NetLabel: Initializing
[   25.410547] NetLabel:  domain hash size = 128
[   25.410590] NetLabel:  protocols = UNLABELED CIPSOv4
[   25.410648] NetLabel:  unlabeled traffic allowed by default
[   25.410780] hpet clockevent registered
[   25.410786] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   25.410935] hpet0: 3 64-bit timers, 14318180 Hz
[   25.412023] AppArmor: AppArmor Filesystem Enabled
[   25.420339] Time: hpet clocksource has been installed.
[   25.420395] Switched to high resolution mode on CPU 0
[   25.420631] Switched to high resolution mode on CPU 1
[   25.440342] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   25.440391] system 00:01: ioport range 0x290-0x29f has been reserved
[   25.441187] system 00:01: ioport range 0x800-0x87f has been reserved
[   25.441235] system 00:01: ioport range 0x880-0x88f has been reserved
[   25.441292] system 00:0a: ioport range 0x400-0x4bf could not be reserved
[   25.441345] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   25.441411] system 00:0c: iomem range 0xcc000-0xd3fff has been reserved
[   25.441460] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   25.441509] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   25.441558] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   25.441606] system 00:0c: iomem range 0x3f7f0000-0x3f7fffff could not be reserved
[   25.441666] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   25.441714] system 00:0c: iomem range 0x100000-0x3f7effff could not be reserved
[   25.441774] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   25.441834] system 00:0c: iomem range 0xfed13000-0xfed1dfff could not be reserved
[   25.441894] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   25.441954] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   25.442014] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved
[   25.472562] PCI: Bridge: 0000:00:1c.0
[   25.472608]   IO window: 9000-9fff
[   25.472655]   MEM window: disabled.
[   25.472699]   PREFETCH window: disabled.
[   25.472753] PCI: Bridge: 0000:00:1e.0
[   25.472798]   IO window: a000-afff
[   25.472844]   MEM window: e0000000-e1ffffff
[   25.472889]   PREFETCH window: disabled.
[   25.472963] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.473052] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   25.473067] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.473079] NET: Registered protocol family 2
[   25.570063] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.570455] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   25.571184] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.571590] TCP: Hash tables configured (established 131072 bind 65536)
[   25.571637] TCP reno registered
[   25.600082] checking if image is initramfs... it is
[   26.213154] Freeing initrd memory: 7147k freed
[   26.214248] audit: initializing netlink socket (disabled)
[   26.214313] audit(1233893219.670:1): initialized
[   26.214620] highmem bounce pool size: 64 pages
[   26.214667] Total HugeTLB memory allocated, 0
[   26.217473] VFS: Disk quotas dquot_6.5.1
[   26.217615] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.217900] io scheduler noop registered
[   26.217944] io scheduler anticipatory registered
[   26.217989] io scheduler deadline registered (default)
[   26.218045] io scheduler cfq registered
[   26.218098] Boot video device is 0000:00:02.0
[   26.218324] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.218376] assign_interrupt_mode Found MSI capability
[   26.218471] Allocate Port Service[0000:00:1c.0:pcie00]
[   26.218526] Allocate Port Service[0000:00:1c.0:pcie02]
[   26.218888] isapnp: Scanning for PnP cards...
[   26.572611] isapnp: No Plug & Play device found
[   26.614155] Real Time Clock Driver v1.12ac
[   26.614334] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.614532] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.614735] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.615540] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.615907] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.617066] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.617223] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.617499] PNP: No PS/2 controller found. Probing ports directly.
[   26.620416] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.620474] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.647646] mice: PS/2 mouse device common for all mice
[   26.647855] EISA: Probing bus 0 at eisa.0
[   26.647934] EISA: Detected 0 cards.
[   26.647979] cpuidle: using governor ladder
[   26.648022] cpuidle: using governor menu
[   26.648158] NET: Registered protocol family 1
[   26.648241] Using IPI No-Shortcut mode
[   26.648318] registered taskstats version 1
[   26.648465]   Magic number: 13:908:109
[   26.648656] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   26.649264] Freeing unused kernel memory: 384k freed
[   26.649359] Write protecting the kernel read-only data: 828k
[   26.853368] fuse init (API version 7.9)
[   26.878950] ACPI: Processor [CPU0] (supports 2 throttling states)
[   26.879113] ACPI: Processor [CPU1] (supports 2 throttling states)
[   27.173485] usbcore: registered new interface driver usbfs
[   27.173566] usbcore: registered new interface driver hub
[   27.173645] usbcore: registered new device driver usb
[   27.175279] USB Universal Host Controller Interface driver v3.0
[   27.175384] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   27.175481] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   27.175486] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   27.176194] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   27.176284] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000b000
[   27.176496] usb usb1: configuration #1 chosen from 1 choice
[   27.176571] hub 1-0:1.0: USB hub found
[   27.176620] hub 1-0:1.0: 2 ports detected
[   27.260613] SCSI subsystem initialized
[   27.284603] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[   27.284607]   originally by Donald Becker <becker@scyld.com>
[   27.284608]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[   27.285947] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   27.286050] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   27.286054] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   27.286127] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   27.286218] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000b400
[   27.286408] usb usb2: configuration #1 chosen from 1 choice
[   27.286484] hub 2-0:1.0: USB hub found
[   27.286534] hub 2-0:1.0: 2 ports detected
[   27.290050] libata version 3.00 loaded.
[   27.294694] Floppy drive(s): fd0 is 1.44M
[   27.309444] FDC 0 is a post-1991 82077
[   27.395648] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   27.395756] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   27.395760] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   27.395837] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   27.395930] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000b800
[   27.396118] usb usb3: configuration #1 chosen from 1 choice
[   27.396197] hub 3-0:1.0: USB hub found
[   27.396247] hub 3-0:1.0: 2 ports detected
[   27.505329] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   27.505428] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   27.505433] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   27.505510] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   27.505601] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000bc00
[   27.505778] usb usb4: configuration #1 chosen from 1 choice
[   27.505855] hub 4-0:1.0: USB hub found
[   27.505904] hub 4-0:1.0: 2 ports detected
[   27.615121] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[   27.615248] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.615253] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.615351] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   27.619328] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.619337] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xe20c4000
[   27.637459] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.637669] usb usb5: configuration #1 chosen from 1 choice
[   27.637747] hub 5-0:1.0: USB hub found
[   27.637797] hub 5-0:1.0: 8 ports detected
[   27.747455] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[   27.749618] natsemi eth0: NatSemi DP8381[56] at 0xe1005000 (0000:02:00.0), 00:02:e3:0b:e7:8f, IRQ 20, port TP.
[   27.749748] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 23 (level, low) -> IRQ 17
[   27.799865] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[e1004000-e10047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   27.802731] ata_piix 0000:00:1f.1: version 2.12
[   27.802763] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   27.802916] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.803287] scsi0 : ata_piix
[   27.803407] scsi1 : ata_piix
[   27.804112] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   27.804162] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   28.136537] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-4040B, A300, max UDMA/33
[   28.335983] ata1.00: configured for UDMA/33
[   28.508143] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4040B A300 PQ: 0 ANSI: 5
[   28.508301] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   28.508510] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   28.508636] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.508977] scsi2 : ata_piix
[   28.509182] scsi3 : ata_piix
[   28.509966] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd800 bmdma 0xe400 irq 18
[   28.510016] ata4: SATA max UDMA/133 cmd 0xdc00 ctl 0xe000 bmdma 0xe408 irq 18
[   28.892033] ata3.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[   28.892089] ata3.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
[   28.892876] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.907487] ata3.01: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
[   28.907535] ata3.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
[   28.984640] ata3.00: configured for UDMA/133
[   29.021900] ata3.01: configured for UDMA/133
[   29.111457] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0014850000c74120]
[   29.201666] ata4.00: ATA-7: ST3500320AS, SD04, max UDMA/133
[   29.201719] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   29.241565] ata4.00: configured for UDMA/133
[   29.241744] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   29.242250] scsi 2:0:1:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
[   29.242700] scsi 3:0:0:0: Direct-Access     ATA      ST3500320AS      SD04 PQ: 0 ANSI: 5
[   29.254250] Driver 'sr' needs updating - please use bus_type methods
[   29.259632] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[   29.259700] Uniform CD-ROM driver Revision: 3.20
[   29.259805] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   29.264885] Driver 'sd' needs updating - please use bus_type methods
[   29.265061] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   29.265131] sd 2:0:0:0: [sda] Write Protect is off
[   29.265183] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.265210] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.265343] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   29.265526] sd 2:0:0:0: [sda] Write Protect is off
[   29.265575] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.265602] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.265673]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   29.270256] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   29.270324] scsi 2:0:1:0: Attached scsi generic sg2 type 0
[   29.270397] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[   29.281853]  sda1 sda2 < sda5 > sda3
[   29.302472] sd 2:0:0:0: [sda] Attached SCSI disk
[   29.303426] sd 2:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   29.303492] sd 2:0:1:0: [sdb] Write Protect is off
[   29.303538] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.303564] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.303682] sd 2:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   29.303743] sd 2:0:1:0: [sdb] Write Protect is off
[   29.303788] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.303813] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.303877]  sdb: sdb1
[   29.306513] sd 2:0:1:0: [sdb] Attached SCSI disk
[   29.307057] sd 3:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   29.307122] sd 3:0:0:0: [sdc] Write Protect is off
[   29.307170] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   29.307196] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.307317] sd 3:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   29.307378] sd 3:0:0:0: [sdc] Write Protect is off
[   29.307424] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   29.307449] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.307515]  sdc: sdc1
[   29.312925] sd 3:0:0:0: [sdc] Attached SCSI disk
[   30.138771] hub 5-0:1.0: connect-debounce failed, port 1 disabled
[   31.931275] Attempting manual resume
[   31.931321] swsusp: Resume From Partition 8:5
[   31.931323] PM: Checking swsusp image.
[   31.931476] PM: Resume from disk failed.
[   31.943950] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   31.947011] SGI XFS Quota Management subsystem
[   31.958049] XFS mounting filesystem sda1
[   32.018687] Ending clean XFS mount for filesystem: sda1
[   32.532892] hub 5-0:1.0: connect-debounce failed, port 2 disabled
[   34.139142] input: PC Speaker as /devices/platform/pcspkr/input/input1
[   34.179176] parport_pc 00:09: reported by Plug and Play ACPI
[   34.179278] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   34.793919] iTCO_vendor_support: vendor-support=0
[   34.836372] Linux agpgart interface v0.102
[   34.864277] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.895660] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.937030] hub 5-0:1.0: connect-debounce failed, port 3 disabled
[   35.050066] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   35.050243] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   35.050347] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.097915] agpgart: Detected an Intel 945G Chipset.
[   35.098794] agpgart: Detected 7932K stolen memory.
[   35.118088] agpgart: AGP aperture is 256M @ 0xd0000000
[   35.135926] input: Power Button (FF) as /devices/virtual/input/input2
[   35.229064] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.229190] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.268731] ACPI: Power Button (FF) [PWRF]
[   35.268860] input: Power Button (CM) as /devices/virtual/input/input3
[   35.298678] intel_rng: FWH not detected
[   35.312671] eth0: DSPCFG accepted after 0 usec.
[   35.312729] eth0: link up.
[   35.312783] eth0: Setting full-duplex based on negotiated link capability.
[   35.327995] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   35.428393] ACPI: Power Button (CM) [PWRB]
[   36.042983] NET: Registered protocol family 10
[   36.043380] lo: Disabled Privacy Extensions
[   36.463337] loop: module loaded
[   36.490755] lp0: using parport0 (interrupt-driven).
[   36.743071] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   37.261932] XFS mounting filesystem sda3
[   37.331099] hub 5-0:1.0: connect-debounce failed, port 4 disabled
[   37.356822] Ending clean XFS mount for filesystem: sda3
[   37.382709] XFS mounting filesystem sdb1
[   37.469785] Ending clean XFS mount for filesystem: sdb1
[   37.500972] XFS mounting filesystem sdc1
[   37.587700] Ending clean XFS mount for filesystem: sdc1
[   38.389353] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.710782] RPC: Registered udp transport module.
[   39.710786] RPC: Registered tcp transport module.

```

---

