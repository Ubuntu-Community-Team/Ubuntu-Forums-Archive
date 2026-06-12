---
title: "*ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384"
date: 2012-01-29
forum: Server Platforms
---

### Post by slparker09 on 2012-01-29
I receive quite of few of these errors in DMESG. Is there anything I can do to fix this issue?

So far, it hasn't caused any problems that I know of but I would rather not take a chance.

I considered just unloading and removing the Radeon module, but wasn't sure that would be a good idea.

This is nothing more than a headless server connected to via SSH only.

I've done a lot of Googling and can't find much on this particular error.

Any thoughts appreciated.

I tried attaching the DMESG output but it was too large for a text file. Here is the output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-server (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #26-Ubuntu SMP Fri Jan 20 19:07:39 UTC 2012 (Ubuntu 3.0.0-15.26-server 3.0.13)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-15-server root=UUID=87e2f5ec-a7cf-4c03-91e3-10545fef0e16 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff8e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000220000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M3A78-CM, BIOS 2801    08/23/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x220000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff80000 page 4k
[    0.000000] kernel direct mapping tables up to cff80000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000220000000
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 0220000000 page 2M
[    0.000000] kernel direct mapping tables up to 220000000 @ cff7e000-cff80000
[    0.000000] RAMDISK: 36542000 - 37299000
[    0.000000] ACPI: RSDP 00000000000fb520 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff80000 00040 (v01 082310 RSDT1625 20100823 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff80200 00084 (v01 082310 FACP1625 20100823 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff805d0 0733E (v01  A0901 A0901001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff8e000 00040
[    0.000000] ACPI: APIC 00000000cff80390 0007C (v01 082310 APIC1625 20100823 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff80410 0003C (v01 082310 OEMMCFG  20100823 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff8e040 00071 (v01 082310 OEMB1625 20100823 MSFT 00000097)
[    0.000000] ACPI: SRAT 00000000cff87910 000E8 (v03 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 00000000cff87a00 00038 (v01 082310 OEMHPET  20100823 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff87a40 00544 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
[    0.000000] SRAT: Node 0 PXM 0 100000000-230000000
[    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
[    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,220000000) -> [0,220000000)
[    0.000000] Initmem setup node 0 0000000000000000-0000000220000000
[    0.000000]   NODE_DATA [000000021fffb000 - 000000021fffffff]
[    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880217a00000-ffff88021e7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00220000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff80
[    0.000000]     0: 0x00100000 -> 0x00220000
[    0.000000] On node 0 totalpages: 2031374
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833464 pages, LIFO batch:31
[    0.000000]   Normal zone: 16128 pages used for memmap
[    0.000000]   Normal zone: 1163520 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff8e000
[    0.000000] PM: Registered nosave memory: 00000000cff8e000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021fc00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2000905
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-15-server root=UUID=87e2f5ec-a7cf-4c03-91e3-10545fef0e16 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 7851228k/8912896k available (6218k kernel code, 787400k absent, 274268k reserved, 6906k data, 904k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:728 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 65011712 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2305.358 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4610.71 BogoMIPS (lpj=9221432)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004058] AppArmor: AppArmor initialized
[    0.004061] Yama: becoming mindful.
[    0.008170] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012110] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013858] Mount-cache hash table entries: 256
[    0.014001] Initializing cgroup subsys cpuacct
[    0.014009] Initializing cgroup subsys memory
[    0.014020] Initializing cgroup subsys devices
[    0.014024] Initializing cgroup subsys freezer
[    0.014027] Initializing cgroup subsys net_cls
[    0.014031] Initializing cgroup subsys blkio
[    0.014040] Initializing cgroup subsys perf_event
[    0.014071] tseg: 0000000000
[    0.014091] CPU: Physical Processor ID: 0
[    0.014094] CPU: Processor Core ID: 0
[    0.014098] mce: CPU supports 6 MCE banks
[    0.015645] ACPI: Core revision 20110413
[    0.018923] ftrace: allocating 26077 entries in 103 pages
[    0.020450] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062501] CPU0: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.064003] Performance Events: AMD PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      4
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000000f
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 99000
[    0.152081]  #2
[    0.152083] smpboot cpu 2: start_ip = 99000
[    0.244083]  #3
[    0.244085] smpboot cpu 3: start_ip = 99000
[    0.336026] Brought up 4 CPUs
[    0.336030] Total of 4 processors activated (18441.74 BogoMIPS).
[    0.337515] devtmpfs: initialized
[    0.337515] PM: Registering ACPI NVS region at cff8e000 (270336 bytes)
[    0.340658] print_constraints: dummy: 
[    0.340700] Time:  3:36:32  Date: 01/30/12
[    0.340740] NET: Registered protocol family 16
[    0.340848] node 0 link 0: io port [1000, ffffff]
[    0.340851] TOM: 00000000d0000000 aka 3328M
[    0.340855] Fam 10h mmconf [e0000000, efffffff]
[    0.340857] node 0 link 0: mmio [a0000, bffff]
[    0.340860] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.340864] node 0 link 0: mmio [f0000000, fbcfffff]
[    0.340866] node 0 link 0: mmio [fbd00000, fbdfffff]
[    0.340868] node 0 link 0: mmio [fbe00000, ffefffff]
[    0.340870] TOM2: 0000000230000000 aka 8960M
[    0.340874] bus: [00, 07] on node 0 link 0
[    0.340877] bus: 00 index 0 [io  0x0000-0xffff]
[    0.340879] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.340881] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.340883] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.340885] bus: 00 index 4 [mem 0x230000000-0xfcffffffff]
[    0.340905] Extended Config Space enabled on 1 nodes
[    0.340753] Trying to unpack rootfs image as initramfs...
[    0.340933] ACPI: bus type pci registered
[    0.341007] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.341013] PCI: not using MMCONFIG
[    0.341016] PCI: Using configuration type 1 for base access
[    0.341019] PCI: Using configuration type 1 for extended access
[    0.341198] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.341202] mtrr: probably your BIOS does not setup all CPUs.
[    0.341205] mtrr: corrected configuration.
[    0.341836] bio: create slab <bio-0> at 0
[    0.341836] ACPI: EC: Look up EC in DSDT
[    0.344314] ACPI: Executed 2 blocks of module-level executable AML code
[    0.368607] ACPI: Interpreter enabled
[    0.368613] ACPI: (supports S0 S1 S3 S4 S5)
[    0.368636] ACPI: Using IOAPIC for interrupt routing
[    0.368661] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.370240] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.398572] ACPI: No dock devices found.
[    0.398578] HEST: Table not found.
[    0.398583] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.398667] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.398837] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.398842] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.398846] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.398850] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.398855] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.398859] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfed44fff]
[    0.398877] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    0.398923] pci 0000:00:01.0: [1043:9602] type 1 class 0x000604
[    0.398959] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
[    0.398987] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.398990] pci 0000:00:06.0: PME# disabled
[    0.399031] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.399050] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.399060] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.399070] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.399080] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.399090] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.399100] pci 0000:00:11.0: reg 24: [mem 0xfbcff800-0xfbcffbff]
[    0.399145] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.399159] pci 0000:00:12.0: reg 10: [mem 0xfbcfe000-0xfbcfefff]
[    0.399224] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.399237] pci 0000:00:12.1: reg 10: [mem 0xfbcfd000-0xfbcfdfff]
[    0.399307] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.399327] pci 0000:00:12.2: reg 10: [mem 0xfbcff000-0xfbcff0ff]
[    0.399397] pci 0000:00:12.2: supports D1 D2
[    0.399399] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.399403] pci 0000:00:12.2: PME# disabled
[    0.399425] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.399439] pci 0000:00:13.0: reg 10: [mem 0xfbcfc000-0xfbcfcfff]
[    0.399505] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.399519] pci 0000:00:13.1: reg 10: [mem 0xfbcfb000-0xfbcfbfff]
[    0.399588] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.399608] pci 0000:00:13.2: reg 10: [mem 0xfbcfa800-0xfbcfa8ff]
[    0.399678] pci 0000:00:13.2: supports D1 D2
[    0.399680] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.399684] pci 0000:00:13.2: PME# disabled
[    0.399709] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.399802] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.399819] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.399829] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.399838] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.399848] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.399858] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.399905] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.399981] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.400028] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.400042] pci 0000:00:14.5: reg 10: [mem 0xfbcf9000-0xfbcf9fff]
[    0.400109] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.400127] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.400141] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.400155] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.400171] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.400217] pci 0000:01:05.0: [1002:9611] type 0 class 0x000300
[    0.400226] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.400231] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
[    0.400236] pci 0000:01:05.0: reg 18: [mem 0xfbef0000-0xfbefffff]
[    0.400247] pci 0000:01:05.0: reg 24: [mem 0xfbd00000-0xfbdfffff]
[    0.400260] pci 0000:01:05.0: supports D1 D2
[    0.400299] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.400305] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.400308] pci 0000:00:01.0:   bridge window [mem 0xfbd00000-0xfbefffff]
[    0.400312] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.400348] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.400361] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.400382] pci 0000:02:00.0: reg 18: [mem 0xfbfff000-0xfbffffff 64bit]
[    0.400396] pci 0000:02:00.0: reg 20: [mem 0xfaff0000-0xfaffffff 64bit pref]
[    0.400405] pci 0000:02:00.0: reg 30: [mem 0xfbfc0000-0xfbfdffff pref]
[    0.400434] pci 0000:02:00.0: supports D1 D2
[    0.400436] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.400440] pci 0000:02:00.0: PME# disabled
[    0.408041] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.408046] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    0.408049] pci 0000:00:06.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.408053] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.408114] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.408120] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.408125] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.408129] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.408132] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.408135] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.408137] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.408140] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.408142] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.408145] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfed44fff] (subtractive decode)
[    0.408157] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.408335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.408368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.408414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.408471]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.408476]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.408480] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.412571] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.412612] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.412649] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.412686] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.412722] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.412761] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.412798] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 *11 12 14 15)
[    0.412834] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.412944] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.412949] vgaarb: loaded
[    0.412952] vgaarb: bridge control possible 0000:01:05.0
[    0.413136] SCSI subsystem initialized
[    0.413154] libata version 3.00 loaded.
[    0.413154] usbcore: registered new interface driver usbfs
[    0.413154] usbcore: registered new interface driver hub
[    0.413154] usbcore: registered new device driver usb
[    0.413154] PCI: Using ACPI for IRQ routing
[    0.421989] PCI: pci_cache_line_size set to 64 bytes
[    0.422061] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.422063] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
[    0.422165] NetLabel: Initializing
[    0.422168] NetLabel:  domain hash size = 128
[    0.422171] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.422185] NetLabel:  unlabeled traffic allowed by default
[    0.422229] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.422235] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.424053] Switching to clocksource hpet
[    0.427706] Switched to NOHz mode on CPU #0
[    0.427793] Switched to NOHz mode on CPU #2
[    0.427839] Switched to NOHz mode on CPU #1
[    0.427847] Switched to NOHz mode on CPU #3
[    0.430213] AppArmor: AppArmor Filesystem Enabled
[    0.430256] pnp: PnP ACPI init
[    0.430276] ACPI: bus type pnp registered
[    0.430416] pnp 00:00: [bus 00-ff]
[    0.430419] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.430421] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.430423] pnp 00:00: [io  0x0d00-0xffff window]
[    0.430426] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.430428] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.430430] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
[    0.430432] pnp 00:00: [mem 0xf0000000-0xfed44fff window]
[    0.430495] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.430571] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.430574] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.430628] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.430665] pnp 00:02: [dma 4]
[    0.430667] pnp 00:02: [io  0x0000-0x000f]
[    0.430669] pnp 00:02: [io  0x0081-0x0083]
[    0.430671] pnp 00:02: [io  0x0087]
[    0.430672] pnp 00:02: [io  0x0089-0x008b]
[    0.430674] pnp 00:02: [io  0x008f]
[    0.430676] pnp 00:02: [io  0x00c0-0x00df]
[    0.430698] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.430707] pnp 00:03: [io  0x0070-0x0071]
[    0.430720] pnp 00:03: [irq 8]
[    0.430742] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.430749] pnp 00:04: [io  0x0061]
[    0.430773] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.430780] pnp 00:05: [io  0x00f0-0x00ff]
[    0.430788] pnp 00:05: [irq 13]
[    0.430809] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.431642] pnp 00:06: [io  0x0378-0x037f]
[    0.431647] pnp 00:06: [irq 7]
[    0.431649] pnp 00:06: [dma 0 disabled]
[    0.431871] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.431901] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.431926] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.432413] pnp 00:08: [io  0x03f8-0x03ff]
[    0.432418] pnp 00:08: [irq 4]
[    0.432420] pnp 00:08: [dma 0 disabled]
[    0.432500] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.432566] pnp 00:09: [io  0x0060]
[    0.432567] pnp 00:09: [io  0x0064]
[    0.432569] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.432571] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.432616] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.432621] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.432626] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.432697] pnp 00:0a: [io  0x0010-0x001f]
[    0.432699] pnp 00:0a: [io  0x0022-0x003f]
[    0.432701] pnp 00:0a: [io  0x0062-0x0063]
[    0.432703] pnp 00:0a: [io  0x0065-0x006f]
[    0.432704] pnp 00:0a: [io  0x0072-0x007f]
[    0.432706] pnp 00:0a: [io  0x0080]
[    0.432707] pnp 00:0a: [io  0x0084-0x0086]
[    0.432709] pnp 00:0a: [io  0x0088]
[    0.432710] pnp 00:0a: [io  0x008c-0x008e]
[    0.432712] pnp 00:0a: [io  0x0090-0x009f]
[    0.432714] pnp 00:0a: [io  0x00a2-0x00bf]
[    0.432715] pnp 00:0a: [io  0x00b1]
[    0.432717] pnp 00:0a: [io  0x00e0-0x00ef]
[    0.432719] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.432720] pnp 00:0a: [io  0x040b]
[    0.432722] pnp 00:0a: [io  0x04d6]
[    0.432723] pnp 00:0a: [io  0x0c00-0x0c01]
[    0.432725] pnp 00:0a: [io  0x0c14]
[    0.432726] pnp 00:0a: [io  0x0c50-0x0c51]
[    0.432728] pnp 00:0a: [io  0x0c52]
[    0.432733] pnp 00:0a: [io  0x0c6c]
[    0.432734] pnp 00:0a: [io  0x0c6f]
[    0.432736] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    0.432738] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    0.432739] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    0.432741] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    0.432742] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    0.432744] pnp 00:0a: [io  0x0b00-0x0b3f]
[    0.432746] pnp 00:0a: [io  0x0800-0x089f]
[    0.432747] pnp 00:0a: [io  0x0b20-0x0b2f]
[    0.432749] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.432751] pnp 00:0a: [io  0x0900-0x090f]
[    0.432753] pnp 00:0a: [io  0x0910-0x091f]
[    0.432754] pnp 00:0a: [io  0xfe00-0xfefe]
[    0.432756] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.432758] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
[    0.432760] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.432830] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.432835] system 00:0a: [io  0x040b] has been reserved
[    0.432838] system 00:0a: [io  0x04d6] has been reserved
[    0.432842] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.432846] system 00:0a: [io  0x0c14] has been reserved
[    0.432850] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.432854] system 00:0a: [io  0x0c52] has been reserved
[    0.432858] system 00:0a: [io  0x0c6c] has been reserved
[    0.432861] system 00:0a: [io  0x0c6f] has been reserved
[    0.432865] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.432869] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.432873] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.432877] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.432881] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.432885] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    0.432889] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.432895] system 00:0a: [io  0x0b20-0x0b2f] has been reserved
[    0.432899] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.432903] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.432908] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.432912] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.432916] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.432921] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.432925] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.433063] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    0.433065] pnp 00:0b: [io  0x0230-0x023f]
[    0.433067] pnp 00:0b: [io  0x0290-0x029f]
[    0.433069] pnp 00:0b: [io  0x0300-0x030f]
[    0.433070] pnp 00:0b: [io  0x0a30-0x0a3f]
[    0.433117] system 00:0b: [io  0x0230-0x023f] has been reserved
[    0.433121] system 00:0b: [io  0x0290-0x029f] has been reserved
[    0.433127] system 00:0b: [io  0x0300-0x030f] has been reserved
[    0.433131] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    0.433136] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.433175] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.433214] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.433220] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.433331] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.433333] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.433335] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.433337] pnp 00:0d: [mem 0x00100000-0xcfffffff]
[    0.433338] pnp 00:0d: [mem 0xfed45000-0xffffffff]
[    0.433383] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.433388] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.433392] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.433396] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.433401] system 00:0d: [mem 0xfed45000-0xffffffff] could not be reserved
[    0.433406] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.433496] pnp: PnP ACPI: found 14 devices
[    0.433499] ACPI: ACPI bus type pnp unregistered
[    0.439414] PCI: max bus depth: 1 pci_try_num: 2
[    0.439432] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.439438] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.439443] pci 0000:00:01.0:   bridge window [mem 0xfbd00000-0xfbefffff]
[    0.439448] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.439454] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.439458] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    0.439463] pci 0000:00:06.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.439468] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.439474] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.439477] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.439487] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.439492] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.439518] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.439523] pci 0000:00:06.0: setting latency timer to 64
[    0.439531] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.439534] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.439536] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.439538] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.439540] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.439543] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.439545] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.439547] pci_bus 0000:01: resource 1 [mem 0xfbd00000-0xfbefffff]
[    0.439549] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.439552] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.439554] pci_bus 0000:02: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.439556] pci_bus 0000:02: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.439559] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.439561] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.439563] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.439565] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.439567] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.439570] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.439613] NET: Registered protocol family 2
[    0.439865] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.441601] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.445498] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.445984] TCP: Hash tables configured (established 524288 bind 65536)
[    0.445989] TCP reno registered
[    0.446011] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.446096] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.446294] NET: Registered protocol family 1
[    0.446309] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.564039] pci 0000:01:05.0: Boot video device
[    0.564044] PCI: CLS 64 bytes, default 64
[    0.581043] PCI-DMA: Disabling AGP.
[    0.581175] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.581179] PCI-DMA: using GART IOMMU.
[    0.581184] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.585184] audit: initializing netlink socket (disabled)
[    0.585202] type=2000 audit(1327894591.580:1): initialized
[    0.626746] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.671992] VFS: Disk quotas dquot_6.5.2
[    0.672090] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.672681] fuse init (API version 7.16)
[    0.672762] msgmni has been set to 15463
[    0.673223] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.673267] io scheduler noop registered
[    0.673271] io scheduler deadline registered (default)
[    0.673314] io scheduler cfq registered
[    0.673534] pcieport 0000:00:06.0: setting latency timer to 64
[    0.673568] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
[    0.673665] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.673695] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.673830] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.673839] ACPI: Power Button [PWRB]
[    0.673881] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.673887] ACPI: Power Button [PWRF]
[    0.673915] ACPI: acpi_idle registered with cpuidle
[    0.676380] ERST: Table is not found!
[    0.676466] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.696954] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.718323] Freeing initrd memory: 13660k freed
[    0.916590] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.916916] Linux agpgart interface v0.103
[    0.917938] brd: module loaded
[    0.918395] loop: module loaded
[    0.918689] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.918725] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.919045] Fixed MDIO Bus: probed
[    0.919069] PPP generic driver version 2.4.2
[    0.919103] tun: Universal TUN/TAP device driver, 1.6
[    0.919107] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.919186] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.919241] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.919281] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.919330] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.919351] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.919382] QUIRK: Enable AMD PLL fix
[    0.919385] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    0.919401] ehci_hcd 0000:00:12.2: debug port 1
[    0.919428] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbcff000
[    0.932030] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.932138] hub 1-0:1.0: USB hub found
[    0.932144] hub 1-0:1.0: 6 ports detected
[    0.932280] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.932293] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.932328] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.932349] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.932371] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    0.932386] ehci_hcd 0000:00:13.2: debug port 1
[    0.932410] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbcfa800
[    0.944033] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.944118] hub 2-0:1.0: USB hub found
[    0.944122] hub 2-0:1.0: 6 ports detected
[    0.944202] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.944249] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.944263] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.944296] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.944336] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbcfe000
[    1.004103] hub 3-0:1.0: USB hub found
[    1.004115] hub 3-0:1.0: 3 ports detected
[    1.004227] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.004242] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.004283] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.004306] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbcfd000
[    1.064106] hub 4-0:1.0: USB hub found
[    1.064121] hub 4-0:1.0: 3 ports detected
[    1.064234] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.064247] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.064281] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.064324] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbcfc000
[    1.124095] hub 5-0:1.0: USB hub found
[    1.124106] hub 5-0:1.0: 3 ports detected
[    1.124219] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.124232] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.124265] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.124299] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbcfb000
[    1.184103] hub 6-0:1.0: USB hub found
[    1.184114] hub 6-0:1.0: 3 ports detected
[    1.184229] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.184242] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.184279] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.184310] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbcf9000
[    1.244029] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.244100] hub 7-0:1.0: USB hub found
[    1.244109] hub 7-0:1.0: 2 ports detected
[    1.244179] uhci_hcd: USB Universal Host Controller Interface driver
[    1.244260] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.244638] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.244647] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.244756] mousedev: PS/2 mouse device common for all mice
[    1.244860] rtc_cmos 00:03: RTC can wake from S4
[    1.244952] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.244979] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.245100] device-mapper: uevent: version 1.0.3
[    1.245164] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.245180] cpuidle: using governor ladder
[    1.245183] cpuidle: using governor menu
[    1.245186] EFI Variables Facility v0.08 2004-May-17
[    1.245425] TCP cubic registered
[    1.245538] NET: Registered protocol family 10
[    1.246021] NET: Registered protocol family 17
[    1.246041] Registering the dns_resolver key type
[    1.246136] PM: Hibernation image not present or could not be loaded.
[    1.246150] registered taskstats version 1
[    1.275511]   Magic number: 12:120:615
[    1.275525] misc tun: hash matches
[    1.275628] rtc_cmos 00:03: setting system clock to 2012-01-30 03:36:33 UTC (1327894593)
[    1.275648] powernow-k8: Found 1 AMD Phenom(tm) 9600 Quad-Core Processor (4 cpu cores) (version 2.20.00)
[    1.275685] powernow-k8:    0 : pstate 0 (2300 MHz)
[    1.275688] powernow-k8:    1 : pstate 1 (1150 MHz)
[    1.276307] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.276311] EDD information not available.
[    1.277865] Freeing unused kernel memory: 904k freed
[    1.278227] Write protecting the kernel read-only data: 12288k
[    1.284850] Freeing unused kernel memory: 1956k freed
[    1.290223] Freeing unused kernel memory: 1364k freed
[    1.315217] udevd[120]: starting version 173
[    1.321837] md: linear personality registered for level -1
[    1.325878] md: multipath personality registered for level -4
[    1.328796] md: raid0 personality registered for level 0
[    1.332266] md: raid1 personality registered for level 1
[    1.335928] async_tx: api initialized (async)
[    1.361024] scsi0 : pata_atiixp
[    1.362979] scsi1 : pata_atiixp
[    1.363606] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.363612] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.365998] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.366033] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.366083] r8169 0000:02:00.0: setting latency timer to 64
[    1.366130] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
[    1.366556] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc90000c0e000, 00:22:15:d0:f0:ea, XID 1c4000c0 IRQ 41
[    1.366620] ahci 0000:00:11.0: version 3.0
[    1.366638] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.366789] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.366795] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.367809] scsi2 : ahci
[    1.367896] scsi3 : ahci
[    1.367978] scsi4 : ahci
[    1.368082] scsi5 : ahci
[    1.368156] scsi6 : ahci
[    1.368223] scsi7 : ahci
[    1.368275] ata3: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcff900 irq 22
[    1.368281] ata4: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcff980 irq 22
[    1.368286] ata5: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffa00 irq 22
[    1.368292] ata6: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffa80 irq 22
[    1.368297] ata7: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffb00 irq 22
[    1.368303] ata8: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffb80 irq 22
[    1.404025] raid6: int64x1   1946 MB/s
[    1.418006] usbcore: registered new interface driver uas
[    1.472035] raid6: int64x2   2644 MB/s
[    1.540036] raid6: int64x4   1968 MB/s
[    1.608028] raid6: int64x8   1797 MB/s
[    1.676030] raid6: sse2x1    3158 MB/s
[    1.688051] ata6: SATA link down (SStatus 0 SControl 300)
[    1.688095] ata7: SATA link down (SStatus 0 SControl 300)
[    1.688159] ata8: SATA link down (SStatus 0 SControl 300)
[    1.744027] raid6: sse2x2    5384 MB/s
[    1.812019] raid6: sse2x4    5791 MB/s
[    1.812022] raid6: using algorithm sse2x4 (5791 MB/s)
[    1.812045] Refined TSC clocksource calibration: 2305.234 MHz.
[    1.812054] Switching to clocksource tsc
[    1.860021] ata3: softreset failed (device not ready)
[    1.860029] ata3: applying SB600 PMP SRST workaround and retrying
[    1.860053] ata4: softreset failed (device not ready)
[    1.860061] ata4: applying SB600 PMP SRST workaround and retrying
[    1.860080] ata5: softreset failed (device not ready)
[    1.860087] ata5: applying SB600 PMP SRST workaround and retrying
[    2.032024] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.036024] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.036053] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.036183] ata4.00: ATAPI: hp      DVD-RAM GH60L, RD01, max UDMA/100
[    2.038252] ata3.00: ATA-8: ST95005620AS, SD26, max UDMA/133
[    2.038256] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.038576] ata5.00: ATA-8: ST95005620AS, SD25, max UDMA/133
[    2.038580] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.040559] ata3.00: configured for UDMA/133
[    2.040722] scsi 2:0:0:0: Direct-Access     ATA      ST95005620AS     SD26 PQ: 0 ANSI: 5
[    2.040922] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.040945] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.041043] sd 2:0:0:0: [sda] Write Protect is off
[    2.041050] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.041085] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.041098] ata4.00: configured for UDMA/100
[    2.041541] ata5.00: configured for UDMA/133
[    2.041699]  sda: sda1 sda2 sda3
[    2.042021] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.049601] scsi 3:0:0:0: CD-ROM            hp       DVD-RAM GH60L    RD01 PQ: 0 ANSI: 5
[    2.057959] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.057965] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.058063] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.058136] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.058291] scsi 4:0:0:0: Direct-Access     ATA      ST95005620AS     SD25 PQ: 0 ANSI: 5
[    2.058438] sd 4:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.058472] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.058540] sd 4:0:0:0: [sdb] Write Protect is off
[    2.058547] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.058589] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.058979]  sdb: sdb1 sdb2 sdb3
[    2.059247] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.060366] xor: automatically using best checksumming function: generic_sse
[    2.064420] Initializing USB Mass Storage driver...
[    2.066309] scsi8 : usb-storage 1-1:1.0
[    2.066419] usbcore: registered new interface driver usb-storage
[    2.066423] USB Mass Storage support registered.
[    2.080007]    generic_sse:  9380.000 MB/sec
[    2.080013] xor: using function: generic_sse (9380.000 MB/sec)
[    2.081371] md: raid6 personality registered for level 6
[    2.081377] md: raid5 personality registered for level 5
[    2.081380] md: raid4 personality registered for level 4
[    2.088383] md: raid10 personality registered for level 10
[    2.114824] md: bind<sda3>
[    2.117142] md: bind<sda1>
[    2.119291] md: bind<sda2>
[    2.143298] md: bind<sdb2>
[    2.145394] bio: create slab <bio-1> at 1
[    2.145490] md/raid1:md1: active with 2 out of 2 mirrors
[    2.145518] md1: detected capacity change from 0 to 8099188736
[    2.147294] md: bind<sdb3>
[    2.148396]  md1: unknown partition table
[    2.149618] md/raid1:md2: active with 2 out of 2 mirrors
[    2.149646] md2: detected capacity change from 0 to 490005716992
[    2.151487] md: bind<sdb1>
[    2.153290]  md2: unknown partition table
[    2.153806] md/raid1:md0: active with 2 out of 2 mirrors
[    2.153835] md0: detected capacity change from 0 to 1997524992
[    2.157263]  md0: unknown partition table
[    2.532729] EXT4-fs (md2): mounted filesystem with ordered data mode. Opts: (null)
[    3.064595] scsi 8:0:0:0: Direct-Access     Corsair  Survivor GTR     0.00 PQ: 0 ANSI: 2
[    3.065119] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    3.066335] sd 8:0:0:0: [sdc] 126746624 512-byte logical blocks: (64.8 GB/60.4 GiB)
[    3.066829] sd 8:0:0:0: [sdc] Write Protect is off
[    3.066834] sd 8:0:0:0: [sdc] Mode Sense: 00 00 00 00
[    3.067327] sd 8:0:0:0: [sdc] Asking for cache data failed
[    3.067331] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    3.069704] sd 8:0:0:0: [sdc] Asking for cache data failed
[    3.069709] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    3.070463]  sdc: sdc1
[    3.072578] sd 8:0:0:0: [sdc] Asking for cache data failed
[    3.072582] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    3.072589] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[    3.461387] udevd[391]: starting version 173
[    3.567011] Adding 7909304k swap on /dev/md1.  Priority:-1 extents:1 across:7909304k 
[    3.630384] lp: driver loaded but no devices found
[    3.711414] parport_pc 00:06: reported by Plug and Play ACPI
[    3.711478] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    3.731022] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.808190] lp0: using parport0 (interrupt-driven).
[    3.826213] MCE: In-kernel MCE decoding enabled.
[    3.831373] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    3.839244] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
[    3.839863] ppdev: user-space parallel port driver
[    3.849568] EDAC MC: Ver: 2.1.0
[    3.886603] AMD64 EDAC driver v3.4.0
[    3.886748] EDAC amd64: DRAM ECC disabled.
[    3.886761] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    3.886763]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    3.886764]  (Note that use of the override may cause unknown side effects.)
[    3.975496] EXT4-fs (md2): re-mounted. Opts: errors=remount-ro
[    4.086649] [drm] Initialized drm 1.1.0 20060810
[    4.113147] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    4.113287] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[    4.213418] [drm] radeon defaulting to kernel modesetting.
[    4.213422] [drm] radeon kernel modesetting enabled.
[    4.213700] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.213707] radeon 0000:01:05.0: setting latency timer to 64
[    4.214003] [drm] initializing kernel modesetting (RS780 0x1002:0x9611 0x1043:0x82EE).
[    4.214048] [drm] register mmio base: 0xFBEF0000
[    4.214050] [drm] register mmio size: 65536
[    4.214739] ATOM BIOS: B27722_RS780C
[    4.214766] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    4.214769] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    4.215975] [drm] Detected VRAM RAM=256M, BAR=256M
[    4.215980] [drm] RAM width 32bits DDR
[    4.216128] [TTM] Zone  kernel: Available graphics memory: 3967532 kiB.
[    4.216130] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    4.216132] [TTM] Initializing pool allocator.
[    4.216176] [drm] radeon: 256M of VRAM memory ready
[    4.216178] [drm] radeon: 512M of GTT memory ready.
[    4.216208] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.216210] [drm] Driver supports precise vblank timestamp query.
[    4.216238] [drm] radeon: irq initialized.
[    4.216246] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    4.217118] [drm] Loading RS780 Microcode
[    4.251484] radeon 0000:01:05.0: WB enabled
[    4.282573] [drm] ring test succeeded in 1 usecs
[    4.282734] [drm] radeon: ib pool ready.
[    4.282811] [drm] ib test succeeded in 0 usecs
[    4.282822] failed to evaluate ATIF got AE_BAD_PARAMETER
[    4.283605] [drm] Radeon Display Connectors
[    4.283607] [drm] Connector 0:
[    4.283608] [drm]   VGA
[    4.283611] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    4.283612] [drm]   Encoders:
[    4.283614] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    4.283615] [drm] Connector 1:
[    4.283616] [drm]   DVI-D
[    4.283617] [drm]   HPD1
[    4.283619] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    4.283621] [drm]   Encoders:
[    4.283622] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
[    4.283624] [drm] Connector 2:
[    4.283625] [drm]   DisplayPort
[    4.283626] [drm]   HPD2
[    4.283628] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[    4.283629] [drm]   Encoders:
[    4.283630] [drm]     DFP2: INTERNAL_UNIPHY
[    4.293322] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[    4.302953] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
[    4.330744] type=1400 audit(1327894596.551:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=610 comm="apparmor_parser"
[    4.330764] type=1400 audit(1327894596.551:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=609 comm="apparmor_parser"
[    4.331216] type=1400 audit(1327894596.551:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=610 comm="apparmor_parser"
[    4.331241] type=1400 audit(1327894596.551:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=609 comm="apparmor_parser"
[    4.331513] type=1400 audit(1327894596.551:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=610 comm="apparmor_parser"
[    4.331547] type=1400 audit(1327894596.551:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=609 comm="apparmor_parser"
[    4.382273] type=1400 audit(1327894596.603:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=673 comm="apparmor_parser"
[    4.382291] type=1400 audit(1327894596.603:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=674 comm="apparmor_parser"
[    4.478017] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
[    4.618291] r8169 0000:02:00.0: eth0: link down
[    4.618303] r8169 0000:02:00.0: eth0: link down
[    4.619585] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.646582] init: failsafe main process (710) killed by TERM signal
[    4.780035] [drm] Radeon display connector DP-1: No monitor connected or invalid EDID
[    4.780369] [drm] radeon: power management initialized
[    4.808022] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808032] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808038] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808043] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808049] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808054] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808060] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808065] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808069] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808126] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808133] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808138] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808142] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808148] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808154] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808159] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808164] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808169] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808222] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808235] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808240] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808244] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808250] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808255] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808261] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808266] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808271] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808323] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808336] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808341] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808346] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808351] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.808357] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808362] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808367] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808372] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.808429] No connectors reported connected with modes
[    4.808433] [drm] Cannot find any crtc or sizes - going 1024x768
[    4.816107] [drm] fb mappable at 0xD0141000
[    4.816109] [drm] vram apper at 0xD0000000
[    4.816110] [drm] size 3145728
[    4.816111] [drm] fb depth is 24
[    4.816113] [drm]    pitch is 4096
[    4.816267] fbcon: radeondrmfb (fb0) is primary device
[    4.816384] Console: switching to colour frame buffer device 128x48
[    4.823813] fb0: radeondrmfb frame buffer device
[    4.823815] drm: registered panic notifier
[    4.823828] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[    4.948038] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.948191] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.948325] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.948458] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.948592] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.948725] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.948858] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.948990] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.949122] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.949302] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.949435] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.949567] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.949699] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.949831] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.949965] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.950099] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.950231] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.950363] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.950553] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.950686] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.950818] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.950949] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.951081] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.951214] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.954188] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.956973] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.959662] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.962315] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.964924] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.967379] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.969757] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.972048] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.974252] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.976408] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.978533] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.980524] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    4.992019] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.993821] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.995499] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.997104] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    4.998637] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.000078] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.001442] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.002694] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.003846] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.005002] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.006006] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.006919] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.007741] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.008579] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.009384] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.010203] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.011018] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.011848] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.012725] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.013543] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.014360] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.015163] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.016053] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.016869] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.017706] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.018535] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.019363] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.020247] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.021097] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.021938] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.022777] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.023619] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245184 vs. 16384
[    5.024485] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.025319] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.026159] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.027022] [drm:atom_get_src_int] *ERROR* ATOM: fb read beyond scratch region: 1245188 vs. 16384
[    5.076822] type=1400 audit(1327894597.299:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=825 comm="apparmor_parser"
[    5.310142] init: apport pre-start process (860) terminated with status 1
[    5.313977] init: apport post-stop process (878) terminated with status 1


```

---

### Post by david3d on 2013-02-03
No solution for you but I'm also seeing this.  I'd classify it as more than a few.  After 1 hour and 20 minutes of uptime since my last reboot my /var/log/syslog is already 2.5M and has 17172 lines that match this message.

---

### Post by Arlor on 2013-02-18
I have the same problem too. The error appears 10 times a second. I am not able to read my logs any more. From what I read [here]("http://www.linuxquestions.org/questions/linux-server-73/memory-leaks-in-centos-6-2-a-947037-print/"), it is harmless. But how exactly can I get rid of it?

---

