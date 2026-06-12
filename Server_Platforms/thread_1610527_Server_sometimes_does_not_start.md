---
title: "Server sometimes does not start"
date: 2010-10-31
forum: Server Platforms
---

### Post by MickSulley on 2010-10-31
Running Ubuntu Server 10.04 32 bit.  Sometimes when I reboot it does not start up, It seems to be going through the boot process but then just hangs.  I have had a look at the log files and can't see anything, but I'm not really sure what I am looking for.

Can anyone tell me how to track down the cause of the problem?

Thanks

---

### Post by brettg on 2010-10-31
More info is required:

Does it only happen when booting from cold? 

Where does the bootup process halt?

You should start with ```
dmesg
```

---

### Post by MickSulley on 2010-11-01
It has happened on reboot and also on a power cycle.  

I assume that the dmesg needed is the one from when the failure occurred, unfortunately I can't be sure which one that is as I rebooted several times.  Just looking at them, are the numbers on the left the boot level?  I see that in one of them it only gets to 8.723134, does that mean that it did not complete the boot sequence?

That one is - 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-25-generic-pae (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 21:01:33 UTC 2010 (Ubuntu 2.6.32-25.45-generic-pae 2.6.32.21+drm33.7)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f740000 (usable)
[    0.000000]  BIOS-e820: 000000003f740000 - 000000003f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f750000 - 000000003f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3f740 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f740000 (usable)
[    0.000000]  modified: 000000003f740000 - 000000003f750000 (ACPI data)
[    0.000000]  modified: 000000003f750000 - 000000003f800000 (ACPI NVS)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 10000-16000
[    0.000000] RAMDISK: 2f165000 - 2f9af8e5
[    0.000000] ACPI: RSDP 000fa550 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3f740000 00030 (v01 A M I  OEMRSDT  05000616 MSFT 00000097)
[    0.000000] ACPI: FACP 3f740200 00081 (v02 A M I  OEMFACP  05000616 MSFT 00000097)
[    0.000000] ACPI: DSDT 3f740370 03B3B (v01  P4i6G P4i6G101 00000101 INTL 02002026)
[    0.000000] ACPI: FACS 3f750000 00040
[    0.000000] ACPI: APIC 3f740300 0006C (v01 A M I  OEMAPIC  05000616 MSFT 00000097)
[    0.000000] ACPI: OEMB 3f750040 0003F (v01 A M I  OEMBIOS  05000616 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 125MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00012000 - 00018f40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 0000935818]    TEXT DATA BSS ==> [0000100000 - 0000935818]
[    0.000000]   #4 [002f165000 - 002f9af8e5]          RAMDISK ==> [002f165000 - 002f9af8e5]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000936000 - 000093d091]              BRK ==> [0000936000 - 000093d091]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x0003f740
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f740
[    0.000000] On node 0 totalpages: 259791
[    0.000000] free_area_init_node: node 0, pgdat c07d8d60, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 251 pages used for memmap
[    0.000000]   HighMem zone: 31815 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1800000 s39480 r0 d21960 u524288
[    0.000000] pcpu-alloc: s39480 r0 d21960 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257760
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-25-generic-pae root=/dev/mapper/Solar-root ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5197760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:0003f740)
[    0.000000] Memory: 1007248k/1039616k available (4833k kernel code, 31216k reserved, 2220k data, 672k init, 128264k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e4000 - 0xc088c000   ( 672 kB)
[    0.000000]       .data : 0xc05b87af - 0xc07e37c8   (2220 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b87af   (4833 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3200.991 MHz processor.
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 6401.98 BogoMIPS (lpj=12803964)
[    0.004048] Security Framework initialized
[    0.004092] AppArmor: AppArmor initialized
[    0.004111] Mount-cache hash table entries: 512
[    0.004374] Initializing cgroup subsys ns
[    0.004380] Initializing cgroup subsys cpuacct
[    0.004394] Initializing cgroup subsys memory
[    0.004404] Initializing cgroup subsys devices
[    0.004407] Initializing cgroup subsys freezer
[    0.004410] Initializing cgroup subsys net_cls
[    0.004462] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004467] CPU: L2 cache: 1024K
[    0.004470] CPU: Physical Processor ID: 0
[    0.004472] CPU: Processor Core ID: 0
[    0.004486] mce: CPU supports 4 MCE banks
[    0.004501] CPU0: Thermal monitoring enabled (TM1)
[    0.004517] using mwait in idle threads.
[    0.004527] Performance Events: no PMU driver, software events only.
[    0.004535] Checking 'hlt' instruction... OK.
[    0.025691] ACPI: Core revision 20090903
[    0.039324] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.039331] ftrace: allocating 22420 entries in 44 pages
[    0.040128] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040506] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081166] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.008000] CPU: L2 cache: 1024K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.168131] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[    0.168147] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172039] Brought up 2 CPUs
[    0.172044] Total of 2 processors activated (12803.13 BogoMIPS).
[    0.172473] CPU0 attaching sched-domain:
[    0.172488]  domain 0: span 0-1 level SIBLING
[    0.172492]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.172499]   domain 1: span 0-1 level MC
[    0.172503]    groups: 0-1 (cpu_power = 1178)
[    0.172521] CPU1 attaching sched-domain:
[    0.172523]  domain 0: span 0-1 level SIBLING
[    0.172526]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.172533]   domain 1: span 0-1 level MC
[    0.172536]    groups: 0-1 (cpu_power = 1178)
[    0.172768] devtmpfs: initialized
[    0.172768] regulator: core version 0.5
[    0.172768] Time: 23:12:30  Date: 10/31/10
[    0.172768] NET: Registered protocol family 16
[    0.172768] Trying to unpack rootfs image as initramfs...
[    0.172768] EISA bus registered
[    0.172768] ACPI: bus type pci registered
[    0.172768] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.172768] PCI: Using configuration type 1 for base access
[    0.177504] bio: create slab <bio-0> at 0
[    0.179087] ACPI: EC: Look up EC in DSDT
[    0.185563] ACPI: Executed 1 blocks of module-level executable AML code
[    0.194142] ACPI: Interpreter enabled
[    0.194160] ACPI: (supports S0 S1 S4 S5)
[    0.194221] ACPI: Using IOAPIC for interrupt routing
[    0.209129] ACPI Warning: Incorrect checksum in table [OEMB] - 8C, should be 7F (20090903/tbutils-314)
[    0.209358] ACPI: No dock devices found.
[    0.209645] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.209739] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.209763] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xfe800000-0xfebfffff]
[    0.209875] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.209893] pci 0000:00:02.0: reg 14 32bit mmio: [0xff280000-0xff2fffff]
[    0.209903] pci 0000:00:02.0: reg 18 io port: [0xec00-0xec07]
[    0.209993] pci 0000:00:06.0: reg 10 32bit mmio: [0xfecf0000-0xfecf0fff]
[    0.210160] pci 0000:00:1d.0: reg 20 io port: [0xdc00-0xdc1f]
[    0.210254] pci 0000:00:1d.1: reg 20 io port: [0xe000-0xe01f]
[    0.210347] pci 0000:00:1d.2: reg 20 io port: [0xe400-0xe41f]
[    0.210439] pci 0000:00:1d.3: reg 20 io port: [0xe800-0xe81f]
[    0.210541] pci 0000:00:1d.7: reg 10 32bit mmio: [0xff27fc00-0xff27ffff]
[    0.210646] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.210654] pci 0000:00:1d.7: PME# disabled
[    0.210817] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.210836] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.210843] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.210884] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.210903] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.210913] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.210931] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.210941] pci 0000:00:1f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.210951] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.211009] pci 0000:00:1f.2: reg 10 io port: [0xd000-0xd007]
[    0.211027] pci 0000:00:1f.2: reg 14 io port: [0xcc00-0xcc03]
[    0.211036] pci 0000:00:1f.2: reg 18 io port: [0xc800-0xc807]
[    0.211045] pci 0000:00:1f.2: reg 1c io port: [0xc400-0xc403]
[    0.211064] pci 0000:00:1f.2: reg 20 io port: [0xc000-0xc00f]
[    0.211155] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.211236] pci 0000:00:1f.5: reg 10 io port: [0xd800-0xd8ff]
[    0.211255] pci 0000:00:1f.5: reg 14 io port: [0xd400-0xd43f]
[    0.211264] pci 0000:00:1f.5: reg 18 32bit mmio: [0xff27f800-0xff27f9ff]
[    0.211283] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xff27f400-0xff27f4ff]
[    0.211330] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.211345] pci 0000:00:1f.5: PME# disabled
[    0.211411] pci 0000:01:01.0: reg 10 io port: [0xbc00-0xbc07]
[    0.211423] pci 0000:01:01.0: reg 14 io port: [0xb800-0xb807]
[    0.211445] pci 0000:01:01.0: reg 18 io port: [0xb400-0xb407]
[    0.211455] pci 0000:01:01.0: reg 1c io port: [0xb000-0xb007]
[    0.211473] pci 0000:01:01.0: reg 20 io port: [0xac00-0xac07]
[    0.211483] pci 0000:01:01.0: reg 24 io port: [0xa800-0xa80f]
[    0.211564] pci 0000:01:05.0: reg 10 io port: [0xa400-0xa4ff]
[    0.211574] pci 0000:01:05.0: reg 14 32bit mmio: [0xff0ffc00-0xff0ffcff]
[    0.211640] pci 0000:01:05.0: supports D1 D2
[    0.211644] pci 0000:01:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.211660] pci 0000:01:05.0: PME# disabled
[    0.211724] pci 0000:00:1e.0: transparent bridge
[    0.211731] pci 0000:00:1e.0: bridge io port: [0xa000-0xbfff]
[    0.211738] pci 0000:00:1e.0: bridge 32bit mmio: [0xff000000-0xff0fffff]
[    0.211762] pci_bus 0000:00: on NUMA node 0
[    0.211771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.212023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.218148] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.218381] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.218619] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.218852] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.219079] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.219325] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.219555] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.219792] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.220125] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.220157] vgaarb: loaded
[    0.220468] SCSI subsystem initialized
[    0.220721] libata version 3.00 loaded.
[    0.220920] usbcore: registered new interface driver usbfs
[    0.220954] usbcore: registered new interface driver hub
[    0.221021] usbcore: registered new device driver usb
[    0.221380] ACPI: WMI: Mapper loaded
[    0.221385] PCI: Using ACPI for IRQ routing
[    0.221759] NetLabel: Initializing
[    0.221763] NetLabel:  domain hash size = 128
[    0.221766] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.221799] NetLabel:  unlabeled traffic allowed by default
[    0.221980] hpet clockevent registered
[    0.221986] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.221994] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.222013] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.228066] Switching to clocksource tsc
[    0.233072] AppArmor: AppArmor Filesystem Enabled
[    0.233122] pnp: PnP ACPI init
[    0.233163] ACPI: bus type pnp registered
[    0.244539] pnp: PnP ACPI: found 14 devices
[    0.244555] ACPI: ACPI bus type pnp unregistered
[    0.244566] PnPBIOS: Disabled by ACPI PNP
[    0.244615] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.244622] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.244628] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.244635] system 00:07: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.244650] system 00:07: iomem range 0xff380000-0xffefffff has been reserved
[    0.244662] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.244677] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.244691] system 00:0c: ioport range 0x680-0x6ff has been reserved
[    0.244697] system 00:0c: ioport range 0x295-0x296 has been reserved
[    0.244718] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.244724] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[    0.244730] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.244744] system 00:0d: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.244750] system 00:0d: iomem range 0xfff00000-0xffffffff has been reserved
[    0.279801] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.279818] pci 0000:00:1e.0:   IO window: 0xa000-0xbfff
[    0.279826] pci 0000:00:1e.0:   MEM window: 0xff000000-0xff0fffff
[    0.279833] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.279865] pci 0000:00:1e.0: setting latency timer to 64
[    0.279882] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.279887] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.279894] pci_bus 0000:01: resource 0 io:  [0xa000-0xbfff]
[    0.279899] pci_bus 0000:01: resource 1 mem: [0xff000000-0xff0fffff]
[    0.279913] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.279918] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.280014] NET: Registered protocol family 2
[    0.280301] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.281192] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.282302] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.283083] TCP: Hash tables configured (established 131072 bind 65536)
[    0.283098] TCP reno registered
[    0.283397] NET: Registered protocol family 1
[    0.283455] pci 0000:00:02.0: Boot video device
[    0.284127] cpufreq-nforce2: No nForce2 chipset.
[    0.284206] Scanning for low memory corruption every 60 seconds
[    0.284475] audit: initializing netlink socket (disabled)
[    0.284519] type=2000 audit(1288566750.282:1): initialized
[    0.301477] highmem bounce pool size: 64 pages
[    0.301488] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.305463] VFS: Disk quotas dquot_6.5.2
[    0.305653] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.307315] fuse init (API version 7.13)
[    0.307558] msgmni has been set to 1718
[    0.308155] alg: No test for stdrng (krng)
[    0.308301] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.308316] io scheduler noop registered
[    0.308320] io scheduler anticipatory registered
[    0.308324] io scheduler deadline registered
[    0.308440] io scheduler cfq registered (default)
[    0.308744] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.308822] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.309078] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.309085] ACPI: Power Button [PWRB]
[    0.309212] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.309217] ACPI: Power Button [PWRF]
[    0.310112] processor LNXCPU:00: registered as cooling_device0
[    0.310373] processor LNXCPU:01: registered as cooling_device1
[    0.320584] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.320763] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.321657] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.323304] isapnp: Scanning for PnP cards...
[    0.324467] brd: module loaded
[    0.325651] loop: module loaded
[    0.325895] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.326201] ata_piix 0000:00:1f.1: version 2.13
[    0.326236]   alloc irq_desc for 18 on node -1
[    0.326241]   alloc kstat_irqs on node -1
[    0.326262] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.326341] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.326503] scsi0 : ata_piix
[    0.326673] scsi1 : ata_piix
[    0.329920] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.329934] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.329972] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.329979] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.330061] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.330157] scsi2 : ata_piix
[    0.330271] scsi3 : ata_piix
[    0.330356] ata3: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc000 irq 18
[    0.330361] ata4: SATA max UDMA/133 cmd 0xc800 ctl 0xc400 bmdma 0xc008 irq 18
[    0.331217] Fixed MDIO Bus: probed
[    0.331305] PPP generic driver version 2.4.2
[    0.331411] tun: Universal TUN/TAP device driver, 1.6
[    0.331415] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.331634] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.331670]   alloc irq_desc for 23 on node -1
[    0.331683]   alloc kstat_irqs on node -1
[    0.331691] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.331724] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.331730] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.331809] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.331857] ehci_hcd 0000:00:1d.7: debug port 1
[    0.335752] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.335780] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff27fc00
[    0.355085] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.355357] usb usb1: configuration #1 chosen from 1 choice
[    0.355429] hub 1-0:1.0: USB hub found
[    0.355455] hub 1-0:1.0: 8 ports detected
[    0.355601] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.355649] uhci_hcd: USB Universal Host Controller Interface driver
[    0.355742]   alloc irq_desc for 16 on node -1
[    0.355746]   alloc kstat_irqs on node -1
[    0.355757] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.355779] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.355785] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.355873] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.355926] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000dc00
[    0.356128] usb usb2: configuration #1 chosen from 1 choice
[    0.356190] hub 2-0:1.0: USB hub found
[    0.356210] hub 2-0:1.0: 2 ports detected
[    0.356305]   alloc irq_desc for 19 on node -1
[    0.356308]   alloc kstat_irqs on node -1
[    0.356316] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.356324] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.356338] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.356407] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.356446] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e000
[    0.356654] usb usb3: configuration #1 chosen from 1 choice
[    0.356716] hub 3-0:1.0: USB hub found
[    0.356728] hub 3-0:1.0: 2 ports detected
[    0.356823] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.356840] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.356845] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.356914] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.356944] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    0.357146] usb usb4: configuration #1 chosen from 1 choice
[    0.357208] hub 4-0:1.0: USB hub found
[    0.357228] hub 4-0:1.0: 2 ports detected
[    0.357320] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.357328] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.357333] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.357410] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.357444] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e800
[    0.357641] usb usb5: configuration #1 chosen from 1 choice
[    0.357702] hub 5-0:1.0: USB hub found
[    0.357712] hub 5-0:1.0: 2 ports detected
[    0.357932] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.374631] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.374663] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.374999] mice: PS/2 mouse device common for all mice
[    0.375294] rtc_cmos 00:02: RTC can wake from S4
[    0.375390] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.375428] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.403634] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.420155] device-mapper: uevent: version 1.0.3
[    0.464816] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.496368] ata2.00: ATAPI: OPTORITEDVD RW DD1205, 120e, max UDMA/33
[    0.504748] ata3.00: ATA-8: WDC WD20EADS-00R6B0, 01.00A01, max UDMA/133
[    0.504754] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.504911] ata4.00: ATA-8: WDC WD20EARS-00S8B1, 80.00A80, max UDMA/133
[    0.504916] ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.511652] ata2.00: configured for UDMA/33
[    0.519904] ata3.00: configured for UDMA/133
[    0.519994] ata4.00: configured for UDMA/133
[    0.597843] device-mapper: multipath: version 1.1.0 loaded
[    0.597855] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.642594] EISA: Probing bus 0 at eisa.0
[    0.642661] EISA: Detected 0 cards.
[    0.643996] Freeing initrd memory: 8490k freed
[    0.655615] cpuidle: using governor ladder
[    0.655620] cpuidle: using governor menu
[    0.656832] TCP cubic registered
[    0.657165] NET: Registered protocol family 10
[    0.658397] lo: Disabled Privacy Extensions
[    0.659294] NET: Registered protocol family 17
[    0.659428] Using IPI No-Shortcut mode
[    0.659669] PM: Resume from disk failed.
[    0.659698] registered taskstats version 1
[    0.660106]   Magic number: 14:962:252
[    0.660185] uhci_hcd 0000:00:1d.0: hash matches
[    0.660253] rtc_cmos 00:02: setting system clock to 2010-10-31 23:12:31 UTC (1288566751)
[    0.660268] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.660271] EDD information not available.
[    0.687192] isapnp: No Plug & Play device found
[    0.688025] scsi 1:0:0:0: CD-ROM            OPTORITE DVD RW DD1205    120e PQ: 0 ANSI: 5
[    0.690679] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    0.690684] Uniform CD-ROM driver Revision: 3.20
[    0.690882] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.690979] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    0.691222] scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EADS-00R 01.0 PQ: 0 ANSI: 5
[    0.691454] sd 2:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    0.691477] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.691581] sd 2:0:0:0: [sda] Write Protect is off
[    0.691596] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.691662] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.691756] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EARS-00S 80.0 PQ: 0 ANSI: 5
[    0.692004]  sda:
[    0.692065] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    0.692230] sd 3:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    0.692325] sd 3:0:0:0: [sdb] Write Protect is off
[    0.692329] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.692381] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.692616]  sdb: unknown partition table
[    0.711344] sd 3:0:0:0: [sdb] Attached SCSI disk
[    0.746487]  sda1 sda2 sda3
[    0.747025] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.747057] Freeing unused kernel memory: 672k freed
[    0.748019] Write protecting the kernel text: 4836k
[    0.748162] Write protecting the kernel read-only data: 1880k
[    0.785863] udev: starting version 151
[    1.089622] Floppy drive(s): fd0 is 1.44M
[    1.111954] FDC 0 is a post-1991 82077
[    1.119697] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.119760] 8139cp 0000:01:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.130089] 8139too Fast Ethernet driver 0.9.28
[    1.130215]   alloc irq_desc for 22 on node -1
[    1.130229]   alloc kstat_irqs on node -1
[    1.130243] 8139too 0000:01:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.133636] eth0: RealTek RTL8139 at 0xa400, 00:13:8f:b8:cd:f4, IRQ 22
[    1.455717] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    1.455724] EXT4-fs (dm-0): write access will be enabled during recovery
[    1.911272] EXT4-fs (dm-0): recovery complete
[    1.918524] EXT4-fs (dm-0): mounted filesystem with ordered data mode
[    2.506692] type=1505 audit(1288566753.344:2):  operation="profile_load" pid=288 name="/sbin/dhclient3"
[    2.507671] type=1505 audit(1288566753.344:3):  operation="profile_load" pid=288 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    2.508233] type=1505 audit(1288566753.347:4):  operation="profile_load" pid=288 name="/usr/lib/connman/scripts/dhclient-script"
[    2.536105] type=1505 audit(1288566753.375:5):  operation="profile_load" pid=289 name="/usr/sbin/mysqld"
[    2.564437] type=1505 audit(1288566753.403:6):  operation="profile_load" pid=290 name="/usr/sbin/ntpd"
[    2.568445] type=1505 audit(1288566753.407:7):  operation="profile_load" pid=291 name="/usr/sbin/tcpdump"
[    3.966268] Adding 3002360k swap on /dev/mapper/Solar-swap_1.  Priority:-1 extents:1 across:3002360k 
[    4.210502] udev: starting version 151
[    4.684539] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.863948] intel_rng: FWH not detected
[    4.884784] Linux agpgart interface v0.103
[    4.898095] psmouse serio1: ID: 00 00 3c
[    5.149488] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    5.150315] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[    5.153869] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    5.421678] parport_pc 00:06: reported by Plug and Play ACPI
[    5.421836] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    5.438467] lp: driver loaded but no devices found
[    5.509587] lp0: using parport0 (interrupt-driven).
[    5.516674] parport_serial 0000:01:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.516717] parport1: PC-style at 0xb400 [PCSPP,TRISTATE,EPP]
[    5.524191] ppdev: user-space parallel port driver
[    5.607128] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[    5.613211] lp1: using parport1 (polling).
[    5.613522] 0000:01:01.0: ttyS1 at I/O 0xbc00 (irq = 22) is a 16550A
[    5.613817] 0000:01:01.0: ttyS2 at I/O 0xb800 (irq = 22) is a 16550A
[    5.801656] [drm] Initialized drm 1.1.0 20060810
[    5.849907]   alloc irq_desc for 17 on node -1
[    5.849912]   alloc kstat_irqs on node -1
[    5.849932] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.850000] Intel ICH 0000:00:1f.5: setting latency timer to 64
[    6.172537] intel8x0_measure_ac97_clock: measured 55301 usecs (2666 samples)
[    6.172552] intel8x0: clocking to 48000
[    6.174707] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.174716] i915 0000:00:02.0: setting latency timer to 64
[    6.179696] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.183802] [drm] set up 7M of stolen space
[    6.218187] [drm] initialized overlay support
[    6.345249] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[    6.737762] fb0: inteldrmfb frame buffer device
[    6.737769] registered panic notifier
[    6.737798] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.905229] vga16fb: initializing
[    6.905236] vga16fb: mapped to 0xc00a0000
[    6.905244] vga16fb: not registering due to another framebuffer present
[    7.145162] Console: switching to colour frame buffer device 128x48
[    8.706057] type=1505 audit(1288566759.427:8):  operation="profile_replace" pid=791 name="/sbin/dhclient3"
[    8.707207] type=1505 audit(1288566759.427:9):  operation="profile_replace" pid=791 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.707856] type=1505 audit(1288566759.427:10):  operation="profile_replace" pid=791 name="/usr/lib/connman/scripts/dhclient-script"
[    8.712825] type=1505 audit(1288566759.435:11):  operation="profile_replace" pid=792 name="/usr/sbin/mysqld"
[    8.718002] type=1505 audit(1288566759.439:12):  operation="profile_replace" pid=793 name="/usr/sbin/ntpd"
[    8.723134] type=1505 audit(1288566759.443:13):  operation="profile_replace" pid=794 name="/usr/sbin/tcpdump"
```

---

