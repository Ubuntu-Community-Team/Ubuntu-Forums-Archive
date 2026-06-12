---
title: "Not able to run instance in UEC"
date: 2010-10-25
forum: Ubuntu Cloud and Juju
---

### Post by deviprasad_k on 2010-10-25
Hi,
 
I had installed UEC 10.04.
I had downloaded Cent OS image (euca-centos-5.3-i386.tar.gz).
When i try creating an instance using this image, i get the AUTHORIZED_KEYS as blank. Find below the console output. Any idea as to why this is happening and how to resolve it?
 
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-server ([EMAIL="buildd@palmer"]buildd@palmer[/EMAIL]) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 (Ubuntu 2.6.28-11.42-server)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bffb000 (usable)
[    0.000000]  BIOS-e820: 000000000bffb000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffbc000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbffb max_arch_pfn = 0x1000000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000bffb000 (usable)
[    0.000000]  modified: 000000000bffb000 - 000000000c000000 (reserved)
[    0.000000]  modified: 00000000fffbc000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] RAMDISK: 0b8d6000 - 0bfef1b5
[    0.000000] ACPI: RSDP 000F8940, 0014 (r0 BOCHS )
[    0.000000] ACPI: RSDT 0BFFDE30, 0034 (r1 BOCHS  BXPCRSDT        1 BXPC        1)
[    0.000000] ACPI: FACP 0BFFFE70, 0074 (r1 BOCHS  BXPCFACP        1 BXPC        1)
[    0.000000] ACPI: DSDT 0BFFDFD0, 1E22 (r1   BXPC   BXDSDT        1 INTL 20090123)
[    0.000000] ACPI: FACS 0BFFFE00, 0040
[    0.000000] ACPI: SSDT 0BFFDF90, 0037 (r1 BOCHS  BXPCSSDT        1 BXPC        1)
[    0.000000] ACPI: APIC 0BFFDEB0, 0072 (r1 BOCHS  BXPCAPIC        1 BXPC        1)
[    0.000000] ACPI: HPET 0BFFDE70, 0038 (r1 BOCHS  BXPCHPET        1 BXPC        1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 191MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0bffb000
[    0.000000]   low ram: 00000000 - 0bffb000
[    0.000000]   bootmap 00013000 - 00014800
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bffb000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008aae2c]    TEXT DATA BSS ==> [0000100000 - 00008aae2c]
[    0.000000]   #4 [000b8d6000 - 000bfef1b5]          RAMDISK ==> [000b8d6000 - 000bfef1b5]
[    0.000000]   #5 [00008ab000 - 00008b4000]    INIT_PG_TABLE ==> [00008ab000 - 00008b4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #8 [0000013000 - 0000015000]          BOOTMAP ==> [0000013000 - 0000015000]
[    0.000000] found SMP MP-table at [c00f8990] 000f8990
[    0.000000] kvm-clock: cpu 0, msr 0:7d9281, boot clock
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000bffb
[    0.000000]   HighMem  0x0000bffb -> 0x0000bffb
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0000bffb
[    0.000000] ACPI: PM-Timer IO Port: 0xb008
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 high level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: c000000:f3fbc000)
[    0.000000] PERCPU: Allocating 49152 bytes of per cpu data
[    0.000000] kvm-clock: cpu 0, msr 0:118b281, primary cpu clock
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48640
[    0.000000] Kernel command line: root=/dev/sda1 console=ttyS0
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 23274.660 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [ttyS0] enabled
[    0.010000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.010000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.010000] allocated 982940 bytes of page_cgroup
[    0.010000] please try cgroup_disable=memory option if you don't want
[    0.010000] Scanning for low memory corruption every 60 seconds
[    0.010000] Memory: 177972k/196588k available (4180k kernel code, 17956k reserved, 2255k data, 548k init, 0k highmem)
[    0.010000] virtual kernel memory layout:
[    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
[    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
[    0.010000]     vmalloc : 0xcc7fb000 - 0xff7fe000   ( 816 MB)
[    0.010000]     lowmem  : 0xc0000000 - 0xcbffb000   ( 191 MB)
[    0.010000]       .init : 0xc0751000 - 0xc07da000   ( 548 kB)
[    0.010000]       .data : 0xc0515003 - 0xc0748fc0   (2255 kB)
[    0.010000]       .text : 0xc0100000 - 0xc0515003   (4180 kB)
[    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.040018] Calibrating delay loop (skipped) preset value.. 4654.93 BogoMIPS (lpj=23274660)
[    0.041525] Security Framework initialized
[    0.042285] SELinux:  Disabled at boot.
[    0.043021] AppArmor: AppArmor initialized
[    0.043749] Mount-cache hash table entries: 512
[    0.044867] Initializing cgroup subsys ns
[    0.045521] Initializing cgroup subsys cpuacct
[    0.046352] Initializing cgroup subsys memory
[    0.047174] Initializing cgroup subsys freezer
[    0.048037] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.050006] CPU: L2 cache: 4096K
[    0.056726] SMP alternatives: switching to UP code
[    0.170701] Freeing SMP alternatives: 18k freed
[    0.171474] ACPI: Core revision 20080926
[    0.172293] ACPI: Checking initramfs for custom DSDT
[    0.433003] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.534133] CPU0: Intel QEMU Virtual CPU version 0.12.3 stepping 03
[    0.540000] Brought up 1 CPUs
[    0.540000] Total of 1 processors activated (4654.93 BogoMIPS).
[    0.540000] net_namespace: 776 bytes
[    0.540000] Booting paravirtualized kernel on KVM
[    0.540000] Time: 11:58:27  Date: 10/25/10
[    0.540000] regulator: core version 0.5
[    0.540000] NET: Registered protocol family 16
[    0.540000] EISA bus registered
[    0.540000] ACPI: bus type pci registered
[    0.540000] PCI: PCI BIOS revision 2.10 entry at 0xffe77, last bus=0
[    0.540004] PCI: Using configuration type 1 for base access
[    0.544017] ACPI: Interpreter enabled
[    0.544656] ACPI: (supports S0 S3 S4 S5)
[    0.545465] ACPI: Using IOAPIC for interrupt routing
[    0.548388] ACPI: No dock devices found.
[    0.549172] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.551782] pci 0000:00:01.3: quirk: region b000-b03f claimed by PIIX4 ACPI
[    0.553142] pci 0000:00:01.3: quirk: region b100-b10f claimed by PIIX4 SMB
[    0.563254] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10 11)
[    0.564544] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    0.565768] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10 *11)
[    0.566997] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[    0.568347] ACPI: WMI: Mapper loaded
[    0.569593] SCSI subsystem initialized
[    0.570220] usbcore: registered new interface driver usbfs
[    0.571294] usbcore: registered new interface driver hub
[    0.572356] usbcore: registered new device driver usb
[    0.573510] PCI: Using ACPI for IRQ routing
[    0.574578] Bluetooth: Core ver 2.13
[    0.574578] NET: Registered protocol family 31
[    0.574578] Bluetooth: HCI device and connection manager initialized
[    0.574578] Bluetooth: HCI socket layer initialized
[    0.574578] NET: Registered protocol family 8
[    0.574661] NET: Registered protocol family 20
[    0.580013] NetLabel: Initializing
[    0.580640] NetLabel:  domain hash size = 128
[    0.581452] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.582461] NetLabel:  unlabeled traffic allowed by default
[    0.583564] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.584589] hpet0: 3 comparators, 64-bit 100.000000 MHz counter
[    0.590360] AppArmor: AppArmor Filesystem Enabled
[    0.591295] pnp: PnP ACPI init
[    0.591295] ACPI: bus type pnp registered
[    0.592003] pnp: PnP ACPI: found 7 devices
[    0.592810] ACPI: ACPI bus type pnp unregistered
[    0.593657] PnPBIOS: Disabled
[    0.630410] bus: 00 index 0 io port: [0x00-0xffff]
[    0.631344] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.632476] NET: Registered protocol family 2
[    0.633461] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.635026] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.636423] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.637716] TCP: Hash tables configured (established 8192 bind 8192)
[    0.638941] TCP reno registered
[    0.639627] NET: Registered protocol family 1
[    0.640712] checking if image is initramfs... it is
[    1.000032] Clocksource tsc unstable (delta = -558073355 ns)
[    1.184233] Freeing initrd memory: 7268k freed
[    1.185240] cpufreq: No nForce2 chipset.
[    1.186198] audit: initializing netlink socket (disabled)
[    1.187231] type=2000 audit(1288007909.180:1): initialized
[    1.195031] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.197180] VFS: Disk quotas dquot_6.5.1
[    1.198036] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.199864] fuse init (API version 7.10)
[    1.200710] msgmni has been set to 362
[    1.201652] alg: No test for stdrng (krng)
[    1.202410] io scheduler noop registered
[    1.203208] io scheduler anticipatory registered
[    1.204108] io scheduler deadline registered (default)
[    1.205147] io scheduler cfq registered
[    1.205958] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    1.207104] pci 0000:00:01.0: PIIX3: Enabling Passive Release
[    1.208197] pci 0000:00:01.0: Activating ISA DMA hang workarounds
[    1.210142] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.211070] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.212320] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.213681] ACPI: Power Button (FF) [PWRF]
[    1.214694] processor ACPI_CPU:00: registered as cooling_device0
[    1.216295] isapnp: Scanning for PnP cards...
[    1.578098] isapnp: No Plug & Play device found
[    1.579769] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.581074] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.582560] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.584142] brd: module loaded
[    1.584915] loop: module loaded
[    1.585511] Fixed MDIO Bus: probed
[    1.586084] PPP generic driver version 2.4.2
[    1.586851] input: Macintosh mouse button emulation as /devices/virtual/input/input1
[    1.588154] Driver 'sd' needs updating - please use bus_type methods
[    1.589223] Driver 'sr' needs updating - please use bus_type methods
[    1.590721] scsi0 : ata_piix
[    1.591310] scsi1 : ata_piix
[    1.591833] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc000 irq 14
[    1.592972] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc008 irq 15
[    1.910708] ata2.00: ATAPI: QEMU DVD-ROM, 0.12.3, max UDMA/100
[    1.912148] ata2.00: configured for MWDMA2
[    1.913588] scsi 1:0:0:0: CD-ROM            QEMU     QEMU DVD-ROM     0.12 PQ: 0 ANSI: 5
[    1.916618] sr0: scsi3-mmc drive: 4x/4x xa/form2 tray
[    1.917470] Uniform CD-ROM driver Revision: 3.20
[    1.918336] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.919712] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.920833] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.921860] uhci_hcd: USB Universal Host Controller Interface driver
[    1.923115] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    1.924090] uhci_hcd 0000:00:01.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, high) -> IRQ 11
[    1.925508] uhci_hcd 0000:00:01.2: UHCI Host Controller
[    1.926557] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    1.927897] uhci_hcd 0000:00:01.2: irq 11, io base 0x0000c020
[    1.928995] usb usb1: configuration #1 chosen from 1 choice
[    1.930090] hub 1-0:1.0: USB hub found
[    1.930869] hub 1-0:1.0: 2 ports detected
[    1.931803] usbcore: registered new interface driver libusual
[    1.932926] usbcore: registered new interface driver usbserial
[    1.934043] USB Serial support registered for generic
[    1.935017] usbcore: registered new interface driver usbserial_generic
[    1.936227] usbserial: USB Serial Driver core
[    1.937129] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.939256] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.940226] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.941298] mice: PS/2 mouse device common for all mice
[    1.942448] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.943762] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.945163] device-mapper: uevent: version 1.0.3
[    1.946421] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.948144] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.949781] device-mapper: multipath: version 1.0.5 loaded
[    1.950838] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.952223] EISA: Probing bus 0 at eisa.0
[    1.953091] EISA: Detected 0 cards.
[    1.953745] cpuidle: using governor ladder
[    1.954557] cpuidle: using governor menu
[    1.955710] TCP cubic registered
[    1.956486] NET: Registered protocol family 10
[    1.957732] lo: Disabled Privacy Extensions
[    1.958799] NET: Registered protocol family 17
[    1.959687] Bluetooth: L2CAP ver 2.11
[    1.960430] Bluetooth: L2CAP socket layer initialized
[    1.961393] Bluetooth: SCO (Voice Link) ver 0.6
[    1.962224] Bluetooth: SCO socket layer initialized
[    1.963195] Bluetooth: RFCOMM socket layer initialized
[    1.964200] Bluetooth: RFCOMM TTY layer initialized
[    1.965125] Bluetooth: RFCOMM ver 1.10
[    1.965921] Using IPI No-Shortcut mode
[    1.966761] registered taskstats version 1
[    1.967622]   Magic number: 14:511:985
[    1.968413] rtc_cmos 00:01: setting system clock to 2010-10-25 11:58:29 UTC (1288007909)
[    1.969946] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.971094] EDD information not available.
[    1.972490] Freeing unused kernel memory: 548k freed
[    1.973834] Write protecting the kernel text: 4184k
[    1.974977] Write protecting the kernel read-only data: 1552k
Loading, please wait...
Couldnt get a file descriptor referring to the console
Begin: Loading essential drivers... ...
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
Begin: Waiting for root file system... ...
[    2.430446] FDC 0 is a S82078B
[    2.480067] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    2.481298] Copyright (c) 1999-2006 Intel Corporation.
[    2.482634] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    2.483805] e1000 0000:00:03.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, high) -> IRQ 10
[    2.801438] e1000: 0000:00:03.0: e1000_probe: (PCI:33MHz:32-bit) d0:0d:47:47:08:b2
[    2.863975] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.865306] sym53c8xx 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, high) -> IRQ 11
[    2.868593] sym0: <895a> rev 0x0 at pci 0000:00:04.0 irq 11
[    2.885910] sym0: No NVRAM, ID 7, Fast-40, LVD, parity checking
[    2.890013] sym0: SCSI BUS has been reset.
[    2.902060] scsi2 : sym-2.2.3
[    5.910220] scsi 2:0:0:0: Direct-Access     QEMU     QEMU HARDDISK    0.12 PQ: 0 ANSI: 3
[    5.911585] scsi target2:0:0: tagged command queuing enabled, command queue depth 16.
[    5.912916] scsi target2:0:0: Beginning Domain Validation
[    5.914270] scsi target2:0:0: Domain Validation skipping write tests
[    5.915328] scsi target2:0:0: Ending Domain Validation
[    5.919014] sd 2:0:0:0: [sda] 4225024 512-byte hardware sectors: (2.16 GB/2.01 GiB)
[    5.920508] sd 2:0:0:0: [sda] Write Protect is off
[    5.921427] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    5.923212] sd 2:0:0:0: [sda] 4225024 512-byte hardware sectors: (2.16 GB/2.01 GiB)
[    5.924549] sd 2:0:0:0: [sda] Write Protect is off
[    5.925472] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    5.926969]  sda: sda1 sda2 sda3
[    5.929275] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.930125] sd 2:0:0:0: Attached scsi generic sg1 type 0
Done.
Begin: Running /scripts/local-premount ...
Begin: Waiting for resume device... ...
Done.
Done.
[   11.113824] kjournald starting.  Commit interval 5 seconds
[   11.114767] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
INIT: version 2.86 booting
  Welcome to  CentOS release 5.3 (Final)
  Press 'I' to enter interactive startup.
Setting clock : Mon Oct 25 11:58:39 EDT 2010 [  OK  ]
Starting udev: udevd-event[900]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:01.1/host0/ioerr_cnt' failed
udevd-event[901]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:01.1/host1/ioerr_cnt' failed
udevd-event[902]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:04.0/host2/ioerr_cnt' failed
udevd-event[1403]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:01.1/host1/target1:0:0/ioerr_cnt' failed
udevd-event[1406]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:04.0/host2/target2:0:0/ioerr_cnt' failed
[  OK  ]
Setting hostname localhost:  [  OK  ]
No devices found
Setting up Logical Volume Management: [  OK  ]
Checking filesystems
Checking all file systems.
[  OK  ]
Remounting root filesystem in read-write mode:  [  OK  ]
Mounting local filesystems:  [  OK  ]
Enabling /etc/fstab swaps:  [  OK  ]
modprobe: FATAL: Could not open 'kernel/fs/binfmt_misc.ko': No such file or directory
INIT: Entering runlevel: 3
Entering non-interactive startup
Bringing up loopback interface:  [  OK  ]
Bringing up interface eth0:  
Determining IP information for eth0...cp: cannot stat `/etc/resolv.conf': No such file or directory
 done.
[  OK  ]
Starting system logger: [  OK  ]
Starting kernel logger: [  OK  ]
Starting sshd: [  OK  ]
[   29.863926] acpiphp_glue: can't get bus number, assuming 0
[   29.864879] decode_hpp: Could not get hotplug parameters. Use defaults
AUTHORIZED_KEYS:
************************
************************
INIT: Id "xvc0" respawning too fast: disabled for 5 minutes

---

### Post by kim0 on 2010-10-25
Hi there,

Did you create your own keys like
euca-add-keypair mykey > ~/.euca/mykey.priv

and did you start your instance with a -k argument like
euca-run-instances $EMI -k mykey -t m1.small

Check out more details at: [https://help.ubuntu.com/community/UEC/CDInstall#STEP](https://help.ubuntu.com/community/UEC/CDInstall#STEP) 7: Run an Image

---

### Post by deviprasad_k on 2010-10-25
Yes, did it as per the instructions given... 
 
If you see the output, it creates the instance, runs it and only think that is not normal 
is that it doesnt generate the AUTHORIZED_KEYS...
 
Any thoughts.

---

### Post by kim0 on 2010-10-26
Well not really sure, if you don't get an answer here, please send to the ubuntu-cloud list
[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-cloud](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-cloud)

---

### Post by Rusty au Lait on 2010-10-26
I just googled the image. I found this:
[https://lists.ubuntu.com/archives/ubuntu-server-bugs/2010-March/032193.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2010-March/032193.html)
Hope it helps.

---

