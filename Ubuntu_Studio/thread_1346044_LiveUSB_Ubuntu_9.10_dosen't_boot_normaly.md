---
title: "LiveUSB Ubuntu 9.10 dosen't boot normaly"
date: 2009-12-04
forum: Ubuntu Studio
---

### Post by mihail.costea on 2009-12-04
A few days ago i made a LiveUSB. I used GRUB2 because it can use ISO. It boots right Slax, Grml, but i have problems with Ubuntu 9.10 and Karmic Netbook Remix. After i select ubuntu in grub it gets until login but it stops at a black screen and it shows me the mouse and nothing more. I was able to enter in terminal with CTRL-ALT-F1-6 and i run dmesg. The stick is FAT32, but i used EXT3 too and i get same error.

Output dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004f7d3800 (usable)
[    0.000000]  BIOS-e820: 000000004f7d3800 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x4f7d3 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FF0000000 write-back
[    0.000000]   2 base 04F800000 mask FFF800000 uncachable
[    0.000000]   3 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000004f7d3800 (usable)
[    0.000000]  modified: 000000004f7d3800 - 0000000050000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37a72000 - 37fef098
[    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
[    0.000000] Move RAMDISK from 0000000037a72000 - 0000000037fef097 to 008ad000 - 00e2a097
[    0.000000] ACPI: RSDP 000fc9b0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 4f7d4425 00038 (v01 DELL    CPi R   27D5031F ASL  00000061)
[    0.000000] ACPI: FACP 4f7d4c00 00074 (v01 DELL    CPi R   27D5031F ASL  00000061)
[    0.000000] ACPI: DSDT 4f7d5800 02D96 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 4f7e4000 00040
[    0.000000] ACPI: APIC 4f7d5400 00068 (v01 DELL    CPi R   27D5031F ASL  00000047)
[    0.000000] ACPI: MCFG 4f7d53c0 0003E (v16 DELL    CPi R   27D5031F ASL  00000061)
[    0.000000] ACPI: SSDT 4f7d4658 001D8 (v01  PmRef  Cpu0Cst 00003001 INTL 20030522)
[    0.000000] ACPI: SSDT 4f7d445d 001FB (v01  PmRef    CpuPm 00003000 INTL 20030522)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac188]              BRK ==> [00008a9000 - 00008ac188]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0004f7d3
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004f7d3
[    0.000000] On node 0 totalpages: 325486
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 768 pages used for memmap
[    0.000000]   HighMem zone: 97493 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 50000000:90000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c19f5000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 322942
[    0.000000] Kernel command line: BOOT_IMAGE=(loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-desktop-i386.iso noeject noprompt --
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6511740 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0004f7d3)
[    0.000000] Memory: 1270060k/1302348k available (4565k kernel code, 30972k reserved, 2143k data, 540k init, 393044k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1296.915 MHz processor.
[    0.002044] Console: colour VGA+ 80x25
[    0.002050] console [tty0] enabled
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 2593.83 BogoMIPS (lpj=5187660)
[    0.004191] Security Framework initialized
[    0.004291] AppArmor: AppArmor initialized
[    0.004367] Mount-cache hash table entries: 512
[    0.004657] Initializing cgroup subsys ns
[    0.004728] Initializing cgroup subsys cpuacct
[    0.004798] Initializing cgroup subsys memory
[    0.004872] Initializing cgroup subsys freezer
[    0.004939] Initializing cgroup subsys net_cls
[    0.005026] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.005125] CPU: L2 cache: 1024K
[    0.005192] mce: CPU supports 5 MCE banks
[    0.005270] CPU0: Thermal monitoring enabled (TM1)
[    0.005351] Performance Counters: p6 PMU driver.
[    0.005460] ... version:                 0
[    0.005526] ... bit width:               32
[    0.005591] ... generic counters:        2
[    0.005657] ... value mask:              00000000ffffffff
[    0.005727] ... max period:              000000007fffffff
[    0.005796] ... fixed-purpose counters:  0
[    0.005861] ... counter mask:            0000000000000003
[    0.005934] Checking 'hlt' instruction... OK.
[    0.021178] SMP alternatives: switching to UP code
[    0.028010] ACPI: Core revision 20090521
[    0.040325] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080103] CPU0: Intel(R) Celeron(R) M processor         1.30GHz stepping 06
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (2593.83 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] Booting paravirtualized kernel on bare hardware
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 12:13:39  Date: 12/03/09
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.084001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.084001] PCI: MCFG area at e0000000 reserved in E820
[    0.084001] PCI: Using MMCONFIG for extended config space
[    0.084001] PCI: Using configuration type 1 for base access
[    0.084001] bio: create slab <bio-0> at 0
[    0.084442] ACPI: EC: Look up EC in DSDT
[    0.090848] ACPI: Interpreter enabled
[    0.090921] ACPI: (supports S0 S3 S4 S5)
[    0.091148] ACPI: Using IOAPIC for interrupt routing
[    0.101526] ACPI: No dock devices found.
[    0.118250] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.118439] pci 0000:00:02.0: reg 10 32bit mmio: [0xdff00000-0xdff7ffff]
[    0.118447] pci 0000:00:02.0: reg 14 io port: [0xec38-0xec3f]
[    0.118454] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
[    0.118461] pci 0000:00:02.0: reg 1c 32bit mmio: [0xdfec0000-0xdfefffff]
[    0.118504] pci 0000:00:02.1: reg 10 32bit mmio: [0xdff80000-0xdfffffff]
[    0.118632] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.118703] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[    0.118773] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[    0.118844] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[    0.118918] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[    0.118987] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.119063] pci 0000:00:1d.7: PME# disabled
[    0.119246] pci 0000:00:1e.2: reg 10 io port: [0xed00-0xedff]
[    0.119256] pci 0000:00:1e.2: reg 14 io port: [0xec40-0xec7f]
[    0.119267] pci 0000:00:1e.2: reg 18 32bit mmio: [0xdfebfe00-0xdfebffff]
[    0.119277] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xdfebfd00-0xdfebfdff]
[    0.119321] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.119396] pci 0000:00:1e.2: PME# disabled
[    0.119503] pci 0000:00:1e.3: reg 10 io port: [0xee00-0xeeff]
[    0.119513] pci 0000:00:1e.3: reg 14 io port: [0xec80-0xecff]
[    0.119568] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.119642] pci 0000:00:1e.3: PME# disabled
[    0.119804] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.119816] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.120006] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.120082] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0900-097f
[    0.120187] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.120197] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.120207] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.120217] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.120227] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.120317] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.120411] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.120442] pci 0000:02:01.0: supports D1 D2
[    0.120446] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120523] pci 0000:02:01.0: PME# disabled
[    0.120622] pci 0000:02:03.0: reg 10 32bit mmio: [0xdfdfe000-0xdfdfffff]
[    0.120718] pci 0000:02:08.0: reg 10 32bit mmio: [0xdfdfd000-0xdfdfdfff]
[    0.120729] pci 0000:02:08.0: reg 14 io port: [0xdf40-0xdf7f]
[    0.120787] pci 0000:02:08.0: supports D1 D2
[    0.120790] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120866] pci 0000:02:08.0: PME# disabled
[    0.120984] pci 0000:00:1e.0: transparent bridge
[    0.121055] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.121062] pci 0000:00:1e.0: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
[    0.121104] pci_bus 0000:00: on NUMA node 0
[    0.121111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.121513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.136074] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.136476] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.136865] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.137255] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.137716] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[    0.138379] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.139113] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.140005] SCSI subsystem initialized
[    0.140146] libata version 3.00 loaded.
[    0.140261] usbcore: registered new interface driver usbfs
[    0.140355] usbcore: registered new interface driver hub
[    0.140460] usbcore: registered new device driver usb
[    0.140722] ACPI: WMI: Mapper loaded
[    0.140788] PCI: Using ACPI for IRQ routing
[    0.141064] Bluetooth: Core ver 2.15
[    0.141169] NET: Registered protocol family 31
[    0.141237] Bluetooth: HCI device and connection manager initialized
[    0.141310] Bluetooth: HCI socket layer initialized
[    0.141378] NetLabel: Initializing
[    0.141441] NetLabel:  domain hash size = 128
[    0.141508] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.141592] NetLabel:  unlabeled traffic allowed by default
[    0.141876] hpet clockevent registered
[    0.141881] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.141961] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.142167] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.150630] pnp: PnP ACPI init
[    0.150735] ACPI: bus type pnp registered
[    0.187765] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.187872] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.188077] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.188184] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.188287] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.190045] pnp 00:0b: io resource (0xd3b0-0xd3bb) overlaps 0000:00:1e.0 BAR 13 (0xd000-0xdfff), disabling
[    0.190150] pnp 00:0b: io resource (0xd3c0-0xd3df) overlaps 0000:00:1e.0 BAR 13 (0xd000-0xdfff), disabling
[    0.190254] pnp 00:0b: io resource (0xd7b0-0xd7bb) overlaps 0000:00:1e.0 BAR 13 (0xd000-0xdfff), disabling
[    0.190357] pnp 00:0b: io resource (0xd7c0-0xd7df) overlaps 0000:00:1e.0 BAR 13 (0xd000-0xdfff), disabling
[    0.190462] pnp 00:0b: io resource (0xdbb0-0xdbbb) overlaps 0000:00:1e.0 BAR 13 (0xd000-0xdfff), disabling
[    0.190565] pnp 00:0b: io resource (0xdbc0-0xdbdf) overlaps 0000:00:1e.0 BAR 13 (0xd000-0xdfff), disabling
[    0.190668] pnp 00:0b: io resource (0xdfb0-0xdfbb) overlaps 0000:00:1e.0 BAR 13 (0xd000-0xdfff), disabling
[    0.190772] pnp 00:0b: io resource (0xdfc0-0xdfdf) overlaps 0000:00:1e.0 BAR 13 (0xd000-0xdfff), disabling
[    0.191470] pnp: PnP ACPI: found 12 devices
[    0.191537] ACPI: ACPI bus type pnp unregistered
[    0.191607] PnPBIOS: Disabled by ACPI PNP
[    0.191686] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.191763] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.191839] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.191914] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.192000] system 00:00: iomem range 0x100000-0x4f7d37ff could not be reserved
[    0.192096] system 00:00: iomem range 0x4f7d3800-0x4f7fffff has been reserved
[    0.192172] system 00:00: iomem range 0x4f800000-0x4fffffff has been reserved
[    0.192248] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.192323] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.192400] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.192497] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.192573] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.192649] system 00:00: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.192725] system 00:00: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.192801] system 00:00: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.192877] system 00:00: iomem range 0xf0006000-0xf0006fff has been reserved
[    0.192952] system 00:00: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.193028] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.193109] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.193187] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.193261] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.193336] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.193410] system 00:03: ioport range 0x10e0-0x10ff has been reserved
[    0.193489] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.193563] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.193636] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.193710] system 00:08: ioport range 0x930-0x93f has been reserved
[    0.193783] system 00:08: ioport range 0x940-0x97f has been reserved
[    0.193862] system 00:0b: ioport range 0x7b0-0x7bb has been reserved
[    0.193935] system 00:0b: ioport range 0x7c0-0x7df has been reserved
[    0.194008] system 00:0b: ioport range 0xbb0-0xbbb has been reserved
[    0.194082] system 00:0b: ioport range 0xbc0-0xbdf has been reserved
[    0.194156] system 00:0b: ioport range 0xfb0-0xfbb has been reserved
[    0.194229] system 00:0b: ioport range 0xfc0-0xfdf has been reserved
[    0.194302] system 00:0b: ioport range 0x13b0-0x13bb has been reserved
[    0.194377] system 00:0b: ioport range 0x13c0-0x13df has been reserved
[    0.194451] system 00:0b: ioport range 0x17b0-0x17bb has been reserved
[    0.194525] system 00:0b: ioport range 0x17c0-0x17df has been reserved
[    0.194599] system 00:0b: ioport range 0x1bb0-0x1bbb has been reserved
[    0.194674] system 00:0b: ioport range 0x1bc0-0x1bdf has been reserved
[    0.194748] system 00:0b: ioport range 0x1fb0-0x1fbb has been reserved
[    0.194822] system 00:0b: ioport range 0x1fc0-0x1fdf has been reserved
[    0.194896] system 00:0b: ioport range 0x23b0-0x23bb has been reserved
[    0.194970] system 00:0b: ioport range 0x23c0-0x23df has been reserved
[    0.195046] system 00:0b: ioport range 0x27b0-0x27bb has been reserved
[    0.195120] system 00:0b: ioport range 0x27c0-0x27df has been reserved
[    0.195194] system 00:0b: ioport range 0x2bb0-0x2bbb has been reserved
[    0.195268] system 00:0b: ioport range 0x2bc0-0x2bdf has been reserved
[    0.195343] system 00:0b: ioport range 0x2fb0-0x2fbb has been reserved
[    0.195417] system 00:0b: ioport range 0x2fc0-0x2fdf has been reserved
[    0.195491] system 00:0b: ioport range 0x33b0-0x33bb has been reserved
[    0.195566] system 00:0b: ioport range 0x33c0-0x33df has been reserved
[    0.195641] system 00:0b: ioport range 0x37b0-0x37bb has been reserved
[    0.195715] system 00:0b: ioport range 0x37c0-0x37df has been reserved
[    0.195789] system 00:0b: ioport range 0x3bb0-0x3bbb has been reserved
[    0.195863] system 00:0b: ioport range 0x3bc0-0x3bdf has been reserved
[    0.195937] system 00:0b: ioport range 0x3fb0-0x3fbb has been reserved
[    0.196017] system 00:0b: ioport range 0x3fc0-0x3fdf has been reserved
[    0.196092] system 00:0b: ioport range 0x43b0-0x43bb has been reserved
[    0.196166] system 00:0b: ioport range 0x43c0-0x43df has been reserved
[    0.196241] system 00:0b: ioport range 0x47b0-0x47bb has been reserved
[    0.196315] system 00:0b: ioport range 0x47c0-0x47df has been reserved
[    0.196389] system 00:0b: ioport range 0x4bb0-0x4bbb has been reserved
[    0.196463] system 00:0b: ioport range 0x4bc0-0x4bdf has been reserved
[    0.196537] system 00:0b: ioport range 0x4fb0-0x4fbb has been reserved
[    0.196611] system 00:0b: ioport range 0x4fc0-0x4fdf has been reserved
[    0.196686] system 00:0b: ioport range 0x53b0-0x53bb has been reserved
[    0.196761] system 00:0b: ioport range 0x53c0-0x53df has been reserved
[    0.196835] system 00:0b: ioport range 0x57b0-0x57bb has been reserved
[    0.196908] system 00:0b: ioport range 0x57c0-0x57df has been reserved
[    0.196983] system 00:0b: ioport range 0x5bb0-0x5bbb has been reserved
[    0.197058] system 00:0b: ioport range 0x5bc0-0x5bdf has been reserved
[    0.197132] system 00:0b: ioport range 0x5fb0-0x5fbb has been reserved
[    0.197206] system 00:0b: ioport range 0x5fc0-0x5fdf has been reserved
[    0.197281] system 00:0b: ioport range 0x63b0-0x63bb has been reserved
[    0.197355] system 00:0b: ioport range 0x63c0-0x63df has been reserved
[    0.197430] system 00:0b: ioport range 0x67b0-0x67bb has been reserved
[    0.197505] system 00:0b: ioport range 0x67c0-0x67df has been reserved
[    0.197579] system 00:0b: ioport range 0x6bb0-0x6bbb has been reserved
[    0.197654] system 00:0b: ioport range 0x6bc0-0x6bdf has been reserved
[    0.197729] system 00:0b: ioport range 0x6fb0-0x6fbb has been reserved
[    0.197803] system 00:0b: ioport range 0x6fc0-0x6fdf has been reserved
[    0.197879] system 00:0b: ioport range 0x73b0-0x73bb has been reserved
[    0.197954] system 00:0b: ioport range 0x73c0-0x73df has been reserved
[    0.198029] system 00:0b: ioport range 0x77b0-0x77bb has been reserved
[    0.198103] system 00:0b: ioport range 0x77c0-0x77df has been reserved
[    0.198178] system 00:0b: ioport range 0x7bb0-0x7bbb has been reserved
[    0.198252] system 00:0b: ioport range 0x7bc0-0x7bdf has been reserved
[    0.198327] system 00:0b: ioport range 0x7fb0-0x7fbb has been reserved
[    0.198402] system 00:0b: ioport range 0x7fc0-0x7fdf has been reserved
[    0.198476] system 00:0b: ioport range 0x83b0-0x83bb has been reserved
[    0.198550] system 00:0b: ioport range 0x83c0-0x83df has been reserved
[    0.198625] system 00:0b: ioport range 0x87b0-0x87bb has been reserved
[    0.198700] system 00:0b: ioport range 0x87c0-0x87df has been reserved
[    0.198774] system 00:0b: ioport range 0x8bb0-0x8bbb has been reserved
[    0.198848] system 00:0b: ioport range 0x8bc0-0x8bdf has been reserved
[    0.198923] system 00:0b: ioport range 0x8fb0-0x8fbb has been reserved
[    0.198997] system 00:0b: ioport range 0x8fc0-0x8fdf has been reserved
[    0.199071] system 00:0b: ioport range 0x93b0-0x93bb has been reserved
[    0.199146] system 00:0b: ioport range 0x93c0-0x93df has been reserved
[    0.199220] system 00:0b: ioport range 0x97b0-0x97bb has been reserved
[    0.199294] system 00:0b: ioport range 0x97c0-0x97df has been reserved
[    0.199369] system 00:0b: ioport range 0x9bb0-0x9bbb has been reserved
[    0.199444] system 00:0b: ioport range 0x9bc0-0x9bdf has been reserved
[    0.199518] system 00:0b: ioport range 0x9fb0-0x9fbb has been reserved
[    0.199593] system 00:0b: ioport range 0x9fc0-0x9fdf has been reserved
[    0.199667] system 00:0b: ioport range 0xa3b0-0xa3bb has been reserved
[    0.199742] system 00:0b: ioport range 0xa3c0-0xa3df has been reserved
[    0.199817] system 00:0b: ioport range 0xa7b0-0xa7bb has been reserved
[    0.199892] system 00:0b: ioport range 0xa7c0-0xa7df has been reserved
[    0.199966] system 00:0b: ioport range 0xabb0-0xabbb has been reserved
[    0.200046] system 00:0b: ioport range 0xabc0-0xabdf has been reserved
[    0.200121] system 00:0b: ioport range 0xafb0-0xafbb has been reserved
[    0.201376] system 00:0b: ioport range 0xafc0-0xafdf has been reserved
[    0.201451] system 00:0b: ioport range 0xb3b0-0xb3bb has been reserved
[    0.201526] system 00:0b: ioport range 0xb3c0-0xb3df has been reserved
[    0.201601] system 00:0b: ioport range 0xb7b0-0xb7bb has been reserved
[    0.201675] system 00:0b: ioport range 0xb7c0-0xb7df has been reserved
[    0.201750] system 00:0b: ioport range 0xbbb0-0xbbbb has been reserved
[    0.201825] system 00:0b: ioport range 0xbbc0-0xbbdf has been reserved
[    0.201900] system 00:0b: ioport range 0xbfb0-0xbfbb has been reserved
[    0.201983] system 00:0b: ioport range 0xbfc0-0xbfdf has been reserved
[    0.202058] system 00:0b: ioport range 0xc3b0-0xc3bb has been reserved
[    0.202133] system 00:0b: ioport range 0xc3c0-0xc3df has been reserved
[    0.202208] system 00:0b: ioport range 0xc7b0-0xc7bb has been reserved
[    0.202283] system 00:0b: ioport range 0xc7c0-0xc7df has been reserved
[    0.202357] system 00:0b: ioport range 0xcbb0-0xcbbb has been reserved
[    0.202432] system 00:0b: ioport range 0xcbc0-0xcbdf has been reserved
[    0.202507] system 00:0b: ioport range 0xcfb0-0xcfbb has been reserved
[    0.202581] system 00:0b: ioport range 0xcfc0-0xcfdf has been reserved
[    0.202660] system 00:0b: ioport range 0xe3b0-0xe3bb has been reserved
[    0.202736] system 00:0b: ioport range 0xe3c0-0xe3df has been reserved
[    0.202811] system 00:0b: ioport range 0xe7b0-0xe7bb has been reserved
[    0.202885] system 00:0b: ioport range 0xe7c0-0xe7df has been reserved
[    0.202962] system 00:0b: ioport range 0xebb0-0xebbb has been reserved
[    0.203037] system 00:0b: ioport range 0xebc0-0xebdf has been reserved
[    0.203112] system 00:0b: ioport range 0xefb0-0xefbb has been reserved
[    0.203187] system 00:0b: ioport range 0xefc0-0xefdf has been reserved
[    0.203262] system 00:0b: ioport range 0xf3b0-0xf3bb has been reserved
[    0.203337] system 00:0b: ioport range 0xf3c0-0xf3df has been reserved
[    0.203412] system 00:0b: ioport range 0xf7b0-0xf7bb has been reserved
[    0.203486] system 00:0b: ioport range 0xf7c0-0xf7df has been reserved
[    0.203563] system 00:0b: ioport range 0xfbb0-0xfbbb has been reserved
[    0.203638] system 00:0b: ioport range 0xfbc0-0xfbdf has been reserved
[    0.203713] system 00:0b: ioport range 0xffb0-0xffbb has been reserved
[    0.203788] system 00:0b: ioport range 0xffc0-0xffdf has been reserved
[    0.238632] AppArmor: AppArmor Filesystem Enabled
[    0.238749] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.238823] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.238897] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.238972] pci 0000:02:01.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.239050] pci 0000:02:01.0:   MEM window: 0x54000000-0x57ffffff
[    0.239126] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.239199] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.239274] pci 0000:00:1e.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.239350] pci 0000:00:1e.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.239437] pci 0000:00:1e.0: setting latency timer to 64
[    0.239449] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.239526]   alloc irq_desc for 16 on node -1
[    0.239530]   alloc kstat_irqs on node -1
[    0.239539] pci 0000:02:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.239621] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.239626] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.239630] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.239635] pci_bus 0000:02: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.239639] pci_bus 0000:02: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.239643] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.239648] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.239652] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.239656] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.239661] pci_bus 0000:03: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.239665] pci_bus 0000:03: resource 3 mem: [0x54000000-0x57ffffff]
[    0.239722] NET: Registered protocol family 2
[    0.239928] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.240480] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.241974] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.242918] TCP: Hash tables configured (established 131072 bind 65536)
[    0.242995] TCP reno registered
[    0.243261] NET: Registered protocol family 1
[    0.243437] Trying to unpack rootfs image as initramfs...
[    0.643960] Switched to high resolution mode on CPU 0
[    2.611732] Freeing initrd memory: 5620k freed
[    2.618185] cpufreq-nforce2: No nForce2 chipset.
[    2.618309] Scanning for low memory corruption every 60 seconds
[    2.618565] audit: initializing netlink socket (disabled)
[    2.618661] type=2000 audit(1259842421.616:1): initialized
[    2.632349] highmem bounce pool size: 64 pages
[    2.632425] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.634688] VFS: Disk quotas dquot_6.5.2
[    2.634838] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.635736] fuse init (API version 7.12)
[    2.635920] msgmni has been set to 1725
[    2.636287] alg: No test for stdrng (krng)
[    2.636370] io scheduler noop registered
[    2.636436] io scheduler anticipatory registered
[    2.636503] io scheduler deadline registered
[    2.636633] io scheduler cfq registered (default)
[    2.636720] pci 0000:00:02.0: Boot video device
[    2.636846] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    2.637051] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.637156] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.637928] ACPI: AC Adapter [AC] (on-line)
[    2.638138] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    2.638784] ACPI: Lid Switch [LID]
[    2.638919] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.639021] ACPI: Power Button [PBTN]
[    2.639148] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.639246] ACPI: Sleep Button [SBTN]
[    2.639868] Marking TSC unstable due to TSC halts in idle
[    2.639964] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.640222] processor LNXCPU:00: registered as cooling_device0
[    2.640295] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.647268] thermal LNXTHERM:01: registered as thermal_zone0
[    2.647349] ACPI: Thermal Zone [THM] (65 C)
[    2.647485] isapnp: Scanning for PnP cards...
[    2.946776] ACPI: Battery Slot [BAT0] (battery present)
[    3.033943] isapnp: No Plug & Play device found
[    3.035615] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.036245]   alloc irq_desc for 17 on node -1
[    3.036249]   alloc kstat_irqs on node -1
[    3.036260] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.036341] serial 0000:00:1e.3: PCI INT B disabled
[    3.037795] brd: module loaded
[    3.038535] loop: module loaded
[    3.038708] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    3.038962] ata_piix 0000:00:1f.1: version 2.13
[    3.038975] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.039102] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.039303] scsi0 : ata_piix
[    3.039485] scsi1 : ata_piix
[    3.040392] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    3.040470] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    3.041779] Fixed MDIO Bus: probed
[    3.041896] PPP generic driver version 2.4.2
[    3.042098] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.042196] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.042289] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.042296] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.042435] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.046437] ehci_hcd 0000:00:1d.7: debug port 1
[    3.046510] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.047050] ata2: port disabled. ignoring.
[    3.047087] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    3.060023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.060214] usb usb1: configuration #1 chosen from 1 choice
[    3.060332] hub 1-0:1.0: USB hub found
[    3.060408] hub 1-0:1.0: 8 ports detected
[    3.060567] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.060663] uhci_hcd: USB Universal Host Controller Interface driver
[    3.060774] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.060855] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.060860] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.060979] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.061101] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    3.061293] usb usb2: configuration #1 chosen from 1 choice
[    3.061399] hub 2-0:1.0: USB hub found
[    3.061471] hub 2-0:1.0: 2 ports detected
[    3.061595] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.061677] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.061682] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.061795] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.061931] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    3.062112] usb usb3: configuration #1 chosen from 1 choice
[    3.062220] hub 3-0:1.0: USB hub found
[    3.062293] hub 3-0:1.0: 2 ports detected
[    3.062418]   alloc irq_desc for 18 on node -1
[    3.062422]   alloc kstat_irqs on node -1
[    3.062431] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.062511] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.062516] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.062636] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.062767] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    3.062949] usb usb4: configuration #1 chosen from 1 choice
[    3.063055] hub 4-0:1.0: USB hub found
[    3.063126] hub 4-0:1.0: 2 ports detected
[    3.063253]   alloc irq_desc for 19 on node -1
[    3.063256]   alloc kstat_irqs on node -1
[    3.063263] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.063347] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.063352] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.063464] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.063595] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    3.063767] usb usb5: configuration #1 chosen from 1 choice
[    3.063873] hub 5-0:1.0: USB hub found
[    3.063945] hub 5-0:1.0: 2 ports detected
[    3.064170] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.069076] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.069151] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.069304] mice: PS/2 mouse device common for all mice
[    3.069584] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.069689] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.069927] device-mapper: uevent: version 1.0.3
[    3.070128] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    3.070333] device-mapper: multipath: version 1.1.0 loaded
[    3.070404] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.070658] EISA: Probing bus 0 at eisa.0
[    3.070743] Cannot allocate resource for EISA slot 1
[    3.070847] EISA: Detected 0 cards.
[    3.071030] cpuidle: using governor ladder
[    3.071184] cpuidle: using governor menu
[    3.071959] TCP cubic registered
[    3.072273] NET: Registered protocol family 10
[    3.072969] lo: Disabled Privacy Extensions
[    3.073474] NET: Registered protocol family 17
[    3.073564] Bluetooth: L2CAP ver 2.13
[    3.073629] Bluetooth: L2CAP socket layer initialized
[    3.073698] Bluetooth: SCO (Voice Link) ver 0.6
[    3.073764] Bluetooth: SCO socket layer initialized
[    3.073883] Bluetooth: RFCOMM TTY layer initialized
[    3.073952] Bluetooth: RFCOMM socket layer initialized
[    3.074021] Bluetooth: RFCOMM ver 1.11
[    3.075367] Using IPI No-Shortcut mode
[    3.075522] PM: Resume from disk failed.
[    3.075539] registered taskstats version 1
[    3.075759]   Magic number: 5:700:227
[    3.075893] acpi PNP0200:00: hash matches
[    3.076028] rtc_cmos 00:06: setting system clock to 2009-12-03 12:13:42 UTC (1259842422)
[    3.076127] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.076199] EDD information not available.
[    3.078042] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.216737] ata1.00: ATA-7: HITACHI HTS541680J9AT00, SB2IA79H, max UDMA/100
[    3.216814] ata1.00: 156301488 sectors, multi 8: LBA 
[    3.216942] ata1.01: ATAPI: Optiarc DVD+/-RW AD-5540A, 102C, max UDMA/33
[    3.232688] ata1.00: configured for UDMA/100
[    3.248428] ata1.01: configured for UDMA/33
[    3.249000] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54168 SB2I PQ: 0 ANSI: 5
[    3.249275] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.250508] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    3.250673] sd 0:0:0:0: [sda] Write Protect is off
[    3.250742] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.250781] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.251067]  sda:
[    3.251245] scsi 0:0:1:0: CD-ROM            Optiarc  DVD+-RW AD-5540A 102C PQ: 0 ANSI: 5
[    3.271497]  sda1 sda2 sda3 < sda5 sda6 > sda4
[    3.308032] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.308695] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.308770] Uniform CD-ROM driver Revision: 3.20
[    3.308939] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    3.309006] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    3.309108] Freeing unused kernel memory: 540k freed
[    3.309616] Write protecting the kernel text: 4568k
[    3.309739] Write protecting the kernel read-only data: 1836k
[    3.432365] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    3.555766] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/input/input5
[    3.555935] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.556140] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    3.556423] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/input/input6
[    3.556580] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    3.575883] usb 1-3: configuration #1 chosen from 1 choice
[    3.624837] Linux agpgart interface v0.103
[    3.640041] Clocksource tsc unstable (delta = -73053232 ns)
[    3.691670] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    3.692324] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    3.695819] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    3.742152] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    3.742237] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.742372]   alloc irq_desc for 20 on node -1
[    3.742377]   alloc kstat_irqs on node -1
[    3.742388] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.769732] e100 0000:02:08.0: PME# disabled
[    3.816458] e100: eth0: e100_probe: addr 0xdfdfd000, irq 20, MAC addr 00:11:43:56:2b:1b
[    3.816629] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.820670] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    3.821340] [drm] Initialized drm 1.1.0 20060810
[    3.825523] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.844089] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.844173] i915 0000:00:02.0: setting latency timer to 64
[    3.974137] Initializing USB Mass Storage driver...
[    3.974368] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.974562] usbcore: registered new interface driver usb-storage
[    3.974636] USB Mass Storage support registered.
[    3.979865] usb-storage: device found at 3
[    3.979872] usb-storage: waiting for device to settle before scanning
[    4.472160] [drm] DAC-6: set mode 640x480 0
[    4.697903] [drm] TV-14: set mode NTSC 480i 0
[    4.825947] [drm] fb0: inteldrmfb frame buffer device
[    4.826032] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.826469] usb 2-1: configuration #1 chosen from 1 choice
[    4.893638] usbcore: registered new interface driver hiddev
[    4.895244] render error detected, EIR: 0x00000010
[    4.895248] page table error
[    4.895251]   PGTBL_ER: 0x00000100
[    4.895255] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    4.895265] render error detected, EIR: 0x00000010
[    4.895268] page table error
[    4.895270]   PGTBL_ER: 0x00000100
[    4.914039] [drm] LVDS-8: set mode 1024x768 17
[    5.315013] Console: switching to colour frame buffer device 128x48
[    5.315719] input: HID 04b3:310b as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input7
[    5.315846] generic-usb 0003:04B3:310B.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:1d.0-1/input0
[    5.315873] usbcore: registered new interface driver usbhid
[    5.315878] usbhid: v2.6:USB HID core driver
[    5.545878] xor: automatically using best checksumming function: pIII_sse
[    5.564009]    pIII_sse  :  3368.000 MB/sec
[    5.564060] xor: using function: pIII_sse (3368.000 MB/sec)
[    5.569180] device-mapper: dm-raid45: initialized v0.2594b
[    5.951222] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[    5.953631] SGI XFS Quota Management subsystem
[    5.964717] JFS: nTxBlock = 8192, nTxLock = 65536
[    6.104482] kjournald starting.  Commit interval 5 seconds
[    6.106369] EXT3 FS on sda1, internal journal
[    6.108049] EXT3-fs: mounted filesystem with writeback data mode.
[    6.173226] kjournald starting.  Commit interval 5 seconds
[    6.174988] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[    6.177073] EXT3 FS on sda2, internal journal
[    6.178941] EXT3-fs: mounted filesystem with writeback data mode.
[    6.251118] kjournald starting.  Commit interval 5 seconds
[    6.253390] EXT3 FS on sda4, internal journal
[    6.255413] EXT3-fs: mounted filesystem with writeback data mode.
[    6.389789] EXT4-fs (sda5): barriers enabled
[    6.403023] kjournald2 starting: pid 495, dev sda5:8, commit interval 5 seconds
[    6.405505] EXT4-fs (sda5): internal journal on sda5:8
[    6.407741] EXT4-fs (sda5): delayed allocation enabled
[    6.410026] EXT4-fs: file extents enabled
[    6.415251] EXT4-fs: mballoc enabled
[    6.417588] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.455232] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[    6.457681] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[    6.460199] EXT4-fs: mballoc: 0 generated and it took 0
[    6.462722] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[    8.976269] usb-storage: device scan complete
[    8.976761] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[    8.979905] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    8.984606] sd 2:0:0:0: [sdb] 15654848 512-byte logical blocks: (8.01 GB/7.46 GiB)
[    8.987723] sd 2:0:0:0: [sdb] Write Protect is off
[    8.990362] sd 2:0:0:0: [sdb] Mode Sense: 16 07 09 51
[    8.990367] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.995342] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.997872]  sdb: sdb1
[    9.007480] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.010000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    9.637432] kjournald starting.  Commit interval 5 seconds
[    9.640156] EXT3 FS on sda1, internal journal
[    9.642573] EXT3-fs: mounted filesystem with writeback data mode.
[    9.728409] kjournald starting.  Commit interval 5 seconds
[    9.730869] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[    9.733561] EXT3 FS on sda2, internal journal
[    9.736056] EXT3-fs: mounted filesystem with writeback data mode.
[    9.817397] kjournald starting.  Commit interval 5 seconds
[    9.820280] EXT3 FS on sda4, internal journal
[    9.822737] EXT3-fs: mounted filesystem with writeback data mode.
[    9.956094] EXT4-fs (sda5): barriers enabled
[    9.969308] kjournald2 starting: pid 580, dev sda5:8, commit interval 5 seconds
[    9.972041] EXT4-fs (sda5): internal journal on sda5:8
[    9.974517] EXT4-fs (sda5): delayed allocation enabled
[    9.976984] EXT4-fs: file extents enabled
[    9.982359] EXT4-fs: mballoc enabled
[    9.984751] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   10.021528] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[   10.023913] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[   10.026354] EXT4-fs: mballoc: 0 generated and it took 0
[   10.028767] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[   11.147924] ISO 9660 Extensions: Microsoft Joliet Level 3
[   11.147986] ISO 9660 Extensions: RRIP_1991A
[   11.160917] aufs 2-standalone.tree-30-20090727
[   11.185004] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   43.975985] Adding 1276916k swap on /dev/sda6.  Priority:-1 extents:1 across:1276916k 
[   44.433647] udev: starting version 147
[   45.566116] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   45.601769] intel_rng: FWH not detected
[   45.921952] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:01a5]
[   45.921984] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   45.921988] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   45.921996] yenta_cardbus 0000:02:01.0: TI: mfunc 0x00001002, devctl 0x64
[   46.026283] cfg80211: Calling CRDA to update world regulatory domain
[   46.032633] dell-wmi: No known WMI GUID found
[   46.153467] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   46.153475] yenta_cardbus 0000:02:01.0: Socket status: 30000007
[   46.153481] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   46.153494] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   46.153499] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xdfff: clean.
[   46.154199] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[   46.154204] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   46.420248] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   46.423933] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.840992] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x8fa0b1, caps: 0xa04713/0x200000
[   46.886362] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   46.934495] cfg80211: World regulatory domain updated:
[   46.934505]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   46.934510]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   46.934515]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   46.934519]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   46.934523]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   46.934528]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.026072] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.063484] phy0: Selected rate control algorithm 'minstrel'
[   47.064544] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   47.306410] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   47.308286] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   47.309048] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   47.309685] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   47.310540] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   47.564164] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   47.787388] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   47.797074] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   47.802084] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   47.804686] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   47.853459] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   47.917230] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   47.945112] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   47.947803] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   47.950499] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   48.011972] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   48.012070] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   48.816172] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   48.820615] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   48.840910] intel8x0_measure_ac97_clock: measured 53299 usecs (2568 samples)
[   48.840917] intel8x0: clocking to 48000
[   50.734823] [drm] DAC-6: set mode 640x480 0
[   51.274033] [drm] DAC-6: set mode 640x480 0
[   51.370659] lp: driver loaded but no devices found
[   51.659811] ppdev: user-space parallel port driver
[   51.765349] [drm] TV-14: set mode NTSC 480i 0
[   51.906606] [drm] TV-14: set mode NTSC 480i 0
[   52.066846] [drm] DAC-6: set mode 640x480 0
[   52.270473] [drm] DAC-6: set mode 640x480 0
[   52.512865] [drm] TV-14: set mode NTSC 480i 0
[   52.653354] [drm] TV-14: set mode NTSC 480i 0
[   56.440348] sd 2:0:0:0: [sdb] Media Changed
[   56.440357] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   56.440363] sd 2:0:0:0: [sdb] Sense Key : Unit Attention [current] 
[   56.440370] Info fld=0x0
[   56.440373] sd 2:0:0:0: [sdb] Add. Sense: Not ready to ready change, medium may have changed
[   56.440384] end_request: I/O error, dev sdb, sector 285357
[   56.445558] Buffer I/O error on device loop0, logical block 63168
[   56.445586] Buffer I/O error on device loop0, logical block 63169
[   56.445605] Buffer I/O error on device loop0, logical block 63170
[   56.445623] Buffer I/O error on device loop0, logical block 63171
[   56.445641] Buffer I/O error on device loop0, logical block 63172
[   56.445659] Buffer I/O error on device loop0, logical block 63173
[   56.445677] Buffer I/O error on device loop0, logical block 63174
[   56.445695] Buffer I/O error on device loop0, logical block 63175
[   56.445713] Buffer I/O error on device loop0, logical block 63176
[   56.445731] Buffer I/O error on device loop0, logical block 63177
[   56.532491] SQUASHFS error: squashfs_read_data failed to read block 0x21a8afcc
[   56.532501] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532505] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.532515] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532519] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.532525] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532529] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.532539] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532543] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.532549] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532553] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.814690] SQUASHFS error: squashfs_read_data failed to read block 0x25b75b75
[   56.814700] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814704] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.814713] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814716] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.814723] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814727] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.814733] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814737] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.814743] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814747] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.954914] SQUASHFS error: squashfs_read_data failed to read block 0x31599fe
[   56.954924] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   56.954929] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   56.954939] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   56.954942] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.002056] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.002065] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.009387] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.009396] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.025542] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.025550] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.028183] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.028190] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.523797] SQUASHFS error: squashfs_read_data failed to read block 0x31599fe
[   57.523807] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.523812] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.588324] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   58.952034] eth0: no IPv6 routers present
```Output dmesg | grep "error"
```
[    4.895244] render error detected, EIR: 0x00000010
[    4.895248] page table error
[    4.895255] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    4.895265] render error detected, EIR: 0x00000010
[    4.895268] page table error
[   56.440384] end_request: I/O error, dev sdb, sector 285357
[   56.445558] Buffer I/O error on device loop0, logical block 63168
[   56.445586] Buffer I/O error on device loop0, logical block 63169
[   56.445605] Buffer I/O error on device loop0, logical block 63170
[   56.445623] Buffer I/O error on device loop0, logical block 63171
[   56.445641] Buffer I/O error on device loop0, logical block 63172
[   56.445659] Buffer I/O error on device loop0, logical block 63173
[   56.445677] Buffer I/O error on device loop0, logical block 63174
[   56.445695] Buffer I/O error on device loop0, logical block 63175
[   56.445713] Buffer I/O error on device loop0, logical block 63176
[   56.445731] Buffer I/O error on device loop0, logical block 63177
[   56.532491] SQUASHFS error: squashfs_read_data failed to read block 0x21a8afcc
[   56.532501] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532505] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.532515] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532519] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.532525] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532529] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.532539] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532543] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.532549] SQUASHFS error: Unable to read fragment cache entry [21a8afcc]
[   56.532553] SQUASHFS error: Unable to read page, block 21a8afcc, size 6742
[   56.814690] SQUASHFS error: squashfs_read_data failed to read block 0x25b75b75
[   56.814700] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814704] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.814713] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814716] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.814723] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814727] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.814733] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814737] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.814743] SQUASHFS error: Unable to read fragment cache entry [25b75b75]
[   56.814747] SQUASHFS error: Unable to read page, block 25b75b75, size a809
[   56.954914] SQUASHFS error: squashfs_read_data failed to read block 0x31599fe
[   56.954924] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   56.954929] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   56.954939] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   56.954942] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.002056] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.002065] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.009387] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.009396] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.025542] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.025550] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.028183] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.028190] SQUASHFS error: Unable to read page, block 31599fe, size 5110
[   57.523797] SQUASHFS error: squashfs_read_data failed to read block 0x31599fe
[   57.523807] SQUASHFS error: Unable to read fragment cache entry [31599fe]
[   57.523812] SQUASHFS error: Unable to read page, block 31599fe, size 5110
```This is grub.cfg

```
### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 3E9C-5D00
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 3E9C-5D00
insmod tga
if background_image /boot/images/Hortensia-1.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN LiveUSB

menuentry "Ubuntu Live 9.04 32bit" {
loopback loop /boot/iso/ubuntu-9.10-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-desktop-i386.iso --
initrd (loop)/casper/initrd.lz
}

menuentry "Grml small 2009.10" {
  loopback loop /boot/iso/grml-small_2009.10.iso
  linux (loop)/boot/grmlsmall/linux26 findiso=/boot/iso/grml-small_2009.10.iso apm=power-off lang=us vga=791 boot=live nomce noeject noprompt --
  initrd (loop)/boot/grmlsmall/initrd.gz
}

menuentry "Karmic Netbook Remix" {
 loopback loop /boot/iso/karmic-netbook-remix-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/karmic-netbook-remix-i386.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}

menuentry "Slax" {
    set isofile="/boot/iso/slax-6.1.2.iso"

    loopback loop $isofile 
    linux (loop)/boot/vmlinuz from=$isofile ramdisk_size=6666 root=/dev/ram0 rw
    initrd (loop)/boot/initrd.gz
}

menuentry "Fedora 12" {
 linux /boot/iso/Fedora12/EFI/boot/vmlinuz0 root=/boot/iso/Fedora12/EFI/boot rootfstype=auto ro liveimg quiet  rhgb
 initrd /boot/iso/Fedora12/EFI/boot/initrd0.img 
# loopback loop /boot/iso/Fedora-12-i686-Live.iso
# linux (loop)/EFI/boot/vmlinuz0 boot=EFI/boot iso-scan/filename=/boot/iso/Fedora-12-i686-Live.iso
# initrd (loop)/EFI/boot/initrd0.img
}

menuentry "Memory test (memtest86+)" {
 linux /boot/img/memtest86+.bin
}

menuentry "Grub2 HDD" {
 set root=hd(1)
 chainloader +1
}

### END LiveUSB

menuentry "Restart" {
 reboot
}

menuentry "Shut Down" {
 halt
}
```

---

### Post by kk_furtiva on 2009-12-05
I'm having this problem too.

USB drive is a KINSGTON to install 9.10 on my Samsung NC10.

Anyone?

---

### Post by veiloctane on 2009-12-22
same problem here on ubuntu 9.10 nebtook remix.

i have a kingston datatraveler dti/8gb when i get this problem.

i have used a older OCZ 1GB roadster and a Kingston datatraveler 2gb and it boots fine im thinking it might be the dti/8gb stick.

---

### Post by AutoStatic on 2009-12-22
Hello all, I think you all should try a different forum (Installation & Upgrades).

---

### Post by mihail.costea on 2009-12-25
If i remember i haven't post here first and i think my post was moved in this section. I wasn't able to make ubuntu 9.10 work properly, maybe because is too new, but ubuntu 9.04 works without any problem.

---

