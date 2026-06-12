---
title: "VirtualBox causing &quot;System Program Problem Detected&quot; Warning"
date: 2015-11-03
forum: Virtualisation
---

### Post by chowse on 2015-11-03
Title says it all, but I am curious...
Has anyone ever Solved this particular issue?
Does this warning indicate my system is OK other than VirtualBox?


Thanks, 
Charles

---

### Post by TheFu on 2015-11-03
What do the log files say?  Check dmesg, /var/log/* and where ever  the virtualbox  logs  go for issues.
What OS is the host running? Version?

---

### Post by chowse on 2015-11-03
> **TheFu said:**
> What do the log files say?  Check dmesg, /var/log/* and where ever  the virtualbox  logs  go for issues.
What OS is the host running? Version?

Hi,
All I can provide is a cat of dmesg.  The crash report is binary.
I tried to just upload a text file containing this info, but the forum wouldn't let me.  Sorry about the length.

****
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-16-generic (buildd@lcy01-07) (gcc version 5.2.1 20151003 (Ubuntu 5.2.1-21ubuntu2) ) #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 (Ubuntu 4.2.0-16.19-generic 4.2.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic root=UUID=c8daf783-60b9-4e12-b0ed-908b2d64b98a ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] tseg: 0000000000
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cff8ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cff90000-0x00000000cffa7fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cffa8000-0x00000000cffcffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cffd0000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M4A785-M, BIOS 1006    08/18/2010
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x230000 max_arch_pfn = 0x400000000
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
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff0000, 0x01ff0fff] PGTABLE
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22fe00000-0x22fffffff]
[    0.000000]  [mem 0x22fe00000-0x22fffffff] page 2M
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x22fdfffff]
[    0.000000]  [mem 0x220000000-0x22fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21fffffff]
[    0.000000]  [mem 0x200000000-0x21fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcff8ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcff8ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x33fc2000-0x35fd8fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FB470 000024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 0x00000000CFF90100 00005C (v01 081810 XSDT1703 20100818 MSFT 00000097)
[    0.000000] ACPI: FACP 0x00000000CFF90290 0000F4 (v03 081810 FACP1703 20100818 MSFT 00000097)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20150619/tbfadt-654)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 64/32 (20150619/tbfadt-623)
[    0.000000] ACPI: DSDT 0x00000000CFF90450 00D2FB (v01 A1429  A1429001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 0x00000000CFFA8000 000040
[    0.000000] ACPI: FACS 0x00000000CFFA8000 000040
[    0.000000] ACPI: APIC 0x00000000CFF90390 00007C (v01 081810 APIC1703 20100818 MSFT 00000097)
[    0.000000] ACPI: MCFG 0x00000000CFF90410 00003C (v01 081810 OEMMCFG  20100818 MSFT 00000097)
[    0.000000] ACPI: OEMB 0x00000000CFFA8040 000072 (v01 081810 OEMB1703 20100818 MSFT 00000097)
[    0.000000] ACPI: SRAT 0x00000000CFF9F450 0000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 0x00000000CFF9F540 000038 (v01 081810 OEMHPET  20100818 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x00000000CFF9F580 000544 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff]
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x00100000-0xcfffffff]
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x100000000-0x22fffffff]
[    0.000000] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x00100000-0xcfffffff] -> [mem 0x00000000-0xcfffffff]
[    0.000000] NUMA: Node 0 [mem 0x00000000-0xcfffffff] + [mem 0x100000000-0x22fffffff] -> [mem 0x00000000-0x22fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x22fff9000-0x22fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880227600000-ffff88022f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000022fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000cff8ffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000022fffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000022fffffff]
[    0.000000] On node 0 totalpages: 2096942
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13247 pages used for memmap
[    0.000000]   DMA32 zone: 847760 pages, LIFO batch:31
[    0.000000]   Normal zone: 19456 pages used for memmap
[    0.000000]   Normal zone: 1245184 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcff90000-0xcffa7fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcffa8000-0xcffcffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcffd0000-0xcfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd0000000-0xffefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfff00000-0xffffffff]
[    0.000000] e820: [mem 0xd0000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88022fc00000 s96728 r8192 d30248 u262144
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2064154
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic root=UUID=c8daf783-60b9-4e12-b0ed-908b2d64b98a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] AGP: Node 0: aperture [bus addr 0xc4000000-0xc5ffffff] (32MB)
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
[    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
[    0.000000] AGP: This costs you 64MB of RAM
[    0.000000] AGP: Mapping aperture over RAM [mem 0xc4000000-0xc7ffffff] (65536KB)
[    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
[    0.000000] Memory: 8074752K/8387768K available (8146K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 313016K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=6.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=6
[    0.000000] NR_IRQS:16640 nr_irqs:472 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-5.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484873504 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2511.378 MHz processor
[    0.000028] Calibrating delay loop (skipped), value calculated using timer frequency.. 5022.75 BogoMIPS (lpj=10045512)
[    0.000032] pid_max: default: 32768 minimum: 301
[    0.000039] ACPI: Core revision 20150619
[    0.007565] ACPI: All ACPI Tables successfully acquired
[    0.007589] Security Framework initialized
[    0.007603] AppArmor: AppArmor initialized
[    0.007605] Yama: becoming mindful.
[    0.008261] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.011147] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012467] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.012479] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.012784] Initializing cgroup subsys blkio
[    0.012789] Initializing cgroup subsys memory
[    0.012798] Initializing cgroup subsys devices
[    0.012802] Initializing cgroup subsys freezer
[    0.012805] Initializing cgroup subsys net_cls
[    0.012808] Initializing cgroup subsys perf_event
[    0.012811] Initializing cgroup subsys net_prio
[    0.012814] Initializing cgroup subsys hugetlb
[    0.012837] CPU: Physical Processor ID: 0
[    0.012838] CPU: Processor Core ID: 0
[    0.012840] mce: CPU supports 6 MCE banks
[    0.012846] LVT offset 0 assigned for vector 0xf9
[    0.012851] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.012853] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64, 1GB 0
[    0.012972] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.022324] ftrace: allocating 30905 entries in 121 pages
[    0.036530] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.183259] smpboot: CPU0: AMD Phenom(tm) 9850 Quad-Core Processor (fam: 10, model: 02, stepping: 03)
[    0.183290] Performance Events: AMD PMU driver.
[    0.183295] ... version:                0
[    0.183296] ... bit width:              48
[    0.183297] ... generic registers:      4
[    0.183298] ... value mask:             0000ffffffffffff
[    0.183300] ... max period:             00007fffffffffff
[    0.183301] ... fixed-purpose events:   0
[    0.183302] ... event mask:             000000000000000f
[    0.184088] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.184200] x86: Booting SMP configuration:
[    0.184202] .... node  #0, CPUs:      #1 #2 #3
[    0.193786] x86: Booted up 1 node, 4 CPUs
[    0.193789] smpboot: Total of 4 processors activated (20091.02 BogoMIPS)
[    0.196136] devtmpfs: initialized
[    0.200651] evm: security.selinux
[    0.200653] evm: security.SMACK64
[    0.200654] evm: security.SMACK64EXEC
[    0.200655] evm: security.SMACK64TRANSMUTE
[    0.200656] evm: security.SMACK64MMAP
[    0.200657] evm: security.ima
[    0.200658] evm: security.capability
[    0.200736] PM: Registering ACPI NVS region [mem 0xcffa8000-0xcffcffff] (163840 bytes)
[    0.200826] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.200919] pinctrl core: initialized pinctrl subsystem
[    0.201042] RTC time: 20:28:54, date: 11/03/15
[    0.201168] NET: Registered protocol family 16
[    0.207294] cpuidle: using governor ladder
[    0.211296] cpuidle: using governor menu
[    0.211303] node 0 link 0: io port [1000, ffffff]
[    0.211305] TOM: 00000000d0000000 aka 3328M
[    0.211308] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.211310] node 0 link 0: mmio [a0000, bffff]
[    0.211313] node 0 link 0: mmio [d0000000, dfffffff]
[    0.211315] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.211316] node 0 link 0: mmio [f0000000, ffefffff]
[    0.211318] TOM2: 0000000230000000 aka 8960M
[    0.211320] bus: [bus 00-07] on node 0 link 0
[    0.211321] bus: 00 [io  0x0000-0xffff]
[    0.211323] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.211324] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.211325] bus: 00 [mem 0xf0000000-0xffffffff]
[    0.211326] bus: 00 [mem 0x230000000-0xfcffffffff]
[    0.211410] ACPI: bus type PCI registered
[    0.211412] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.211487] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.211489] PCI: not using MMCONFIG
[    0.211490] PCI: Using configuration type 1 for base access
[    0.211491] PCI: Using configuration type 1 for extended access
[    0.211802] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.211803] mtrr: probably your BIOS does not setup all CPUs.
[    0.211804] mtrr: corrected configuration.
[    0.215716] ACPI: Added _OSI(Module Device)
[    0.215718] ACPI: Added _OSI(Processor Device)
[    0.215719] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.215721] ACPI: Added _OSI(Processor Aggregator Device)
[    0.218284] ACPI: Executed 3 blocks of module-level executable AML code
[    0.287855] ACPI: Interpreter enabled
[    0.287868] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.287884] ACPI: (supports S0 S1 S3 S4 S5)
[    0.287886] ACPI: Using IOAPIC for interrupt routing
[    0.287906] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.289275] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.289304] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.295204] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.295211] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.295218] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.295477] PCI host bridge to bus 0000:00
[    0.295480] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.295483] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.295485] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.295487] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.295489] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
[    0.295491] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xdfffffff window]
[    0.295493] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff window]
[    0.295502] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
[    0.295610] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.295643] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.295687] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.295748] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.295774] pci 0000:00:11.0: reg 0x10: [io  0xc000-0xc007]
[    0.295783] pci 0000:00:11.0: reg 0x14: [io  0xb000-0xb003]
[    0.295793] pci 0000:00:11.0: reg 0x18: [io  0xa000-0xa007]
[    0.295802] pci 0000:00:11.0: reg 0x1c: [io  0x9000-0x9003]
[    0.295812] pci 0000:00:11.0: reg 0x20: [io  0x8000-0x800f]
[    0.295821] pci 0000:00:11.0: reg 0x24: [mem 0xfe9ffc00-0xfe9fffff]
[    0.295920] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.295936] pci 0000:00:12.0: reg 0x10: [mem 0xfe9fe000-0xfe9fefff]
[    0.296026] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.296066] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.296081] pci 0000:00:12.1: reg 0x10: [mem 0xfe9fd000-0xfe9fdfff]
[    0.296173] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.296218] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.296243] pci 0000:00:12.2: reg 0x10: [mem 0xfe9ff800-0xfe9ff8ff]
[    0.296308] pci 0000:00:12.2: supports D1 D2
[    0.296310] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.296354] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.296398] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.296414] pci 0000:00:13.0: reg 0x10: [mem 0xfe9fc000-0xfe9fcfff]
[    0.296510] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.296549] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.296564] pci 0000:00:13.1: reg 0x10: [mem 0xfe9fb000-0xfe9fbfff]
[    0.296655] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.296698] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.296723] pci 0000:00:13.2: reg 0x10: [mem 0xfe9ff400-0xfe9ff4ff]
[    0.296789] pci 0000:00:13.2: supports D1 D2
[    0.296790] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.296833] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.296879] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.297028] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.297051] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.297061] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.297070] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.297079] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.297088] pci 0000:00:14.1: reg 0x20: [io  0xff00-0xff0f]
[    0.297108] pci 0000:00:14.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.297110] pci 0000:00:14.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.297112] pci 0000:00:14.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.297114] pci 0000:00:14.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.297198] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.297224] pci 0000:00:14.2: reg 0x10: [mem 0xfe9f4000-0xfe9f7fff 64bit]
[    0.297280] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.297319] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.297358] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.297493] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.297565] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.297604] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.297619] pci 0000:00:14.5: reg 0x10: [mem 0xfe9fa000-0xfe9fafff]
[    0.297710] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.297751] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.297823] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.297887] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.297958] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.298029] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.298143] pci 0000:01:00.0: [1002:68f9] type 00 class 0x030000
[    0.298165] pci 0000:01:00.0: reg 0x10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.298174] pci 0000:01:00.0: reg 0x18: [mem 0xfeae0000-0xfeafffff 64bit]
[    0.298181] pci 0000:01:00.0: reg 0x20: [io  0xd000-0xd0ff]
[    0.298193] pci 0000:01:00.0: reg 0x30: [mem 0xfeac0000-0xfeadffff pref]
[    0.298212] pci 0000:01:00.0: supports D1 D2
[    0.298254] pci 0000:01:00.1: [1002:aa68] type 00 class 0x040300
[    0.298276] pci 0000:01:00.1: reg 0x10: [mem 0xfeabc000-0xfeabffff 64bit]
[    0.298318] pci 0000:01:00.1: supports D1 D2
[    0.303346] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.303350] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.303353] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.303356] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.303402] pci 0000:02:06.0: [10ec:8169] type 00 class 0x020000
[    0.303432] pci 0000:02:06.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.303444] pci 0000:02:06.0: reg 0x14: [mem 0xfebffc00-0xfebffcff]
[    0.303497] pci 0000:02:06.0: reg 0x30: [mem 0xfebc0000-0xfebdffff pref]
[    0.303520] pci 0000:02:06.0: supports D1 D2
[    0.303522] pci 0000:02:06.0: PME# supported from D1 D2 D3hot D3cold
[    0.303603] pci 0000:00:14.4: PCI bridge to [bus 02] (subtractive decode)
[    0.303607] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.303611] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.303616] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.303618] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.303620] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.303622] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff window] (subtractive decode)
[    0.303624] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff window] (subtractive decode)
[    0.303626] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff window] (subtractive decode)
[    0.303639] pci_bus 0000:00: on NUMA node 0
[    0.304338] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.304384] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.304423] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.304466] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.304516] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.304560] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 *10 11 12 14 15)
[    0.304609] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.304657] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.304738] ACPI: Enabled 2 GPEs in block 00 to 1F
[    0.304858] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.304861] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.304862] vgaarb: loaded
[    0.304864] vgaarb: bridge control possible 0000:01:00.0
[    0.305145] SCSI subsystem initialized
[    0.305193] libata version 3.00 loaded.
[    0.305217] ACPI: bus type USB registered
[    0.305237] usbcore: registered new interface driver usbfs
[    0.305247] usbcore: registered new interface driver hub
[    0.305269] usbcore: registered new device driver usb
[    0.305442] PCI: Using ACPI for IRQ routing
[    0.313839] PCI: pci_cache_line_size set to 64 bytes
[    0.313889] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.313891] e820: reserve RAM buffer [mem 0xcff90000-0xcfffffff]
[    0.314018] NetLabel: Initializing
[    0.314020] NetLabel:  domain hash size = 128
[    0.314021] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.314034] NetLabel:  unlabeled traffic allowed by default
[    0.314115] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.314119] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.316167] clocksource: Switched to clocksource hpet
[    0.323954] AppArmor: AppArmor Filesystem Enabled
[    0.324045] pnp: PnP ACPI init
[    0.324253] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.324312] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.324887] pnp 00:02: [dma 0 disabled]
[    0.325081] pnp 00:02: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.325491] pnp 00:03: [dma 0 disabled]
[    0.325565] pnp 00:03: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.325672] system 00:04: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.325675] system 00:04: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.325678] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.325910] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.325913] system 00:05: [io  0x040b] has been reserved
[    0.325915] system 00:05: [io  0x04d6] has been reserved
[    0.325917] system 00:05: [io  0x0c00-0x0c01] has been reserved
[    0.325920] system 00:05: [io  0x0c14] has been reserved
[    0.325922] system 00:05: [io  0x0c50-0x0c51] has been reserved
[    0.325924] system 00:05: [io  0x0c52] has been reserved
[    0.325926] system 00:05: [io  0x0c6c] has been reserved
[    0.325928] system 00:05: [io  0x0c6f] has been reserved
[    0.325932] system 00:05: [io  0x0cd0-0x0cd1] has been reserved
[    0.325934] system 00:05: [io  0x0cd2-0x0cd3] has been reserved
[    0.325936] system 00:05: [io  0x0cd4-0x0cd5] has been reserved
[    0.325939] system 00:05: [io  0x0cd6-0x0cd7] has been reserved
[    0.325941] system 00:05: [io  0x0cd8-0x0cdf] has been reserved
[    0.325943] system 00:05: [io  0x0b00-0x0b3f] has been reserved
[    0.325945] system 00:05: [io  0x0800-0x089f] could not be reserved
[    0.325947] system 00:05: [io  0x0b00-0x0b0f] has been reserved
[    0.325949] system 00:05: [io  0x0b20-0x0b3f] has been reserved
[    0.325951] system 00:05: [io  0x0900-0x090f] has been reserved
[    0.325953] system 00:05: [io  0x0910-0x091f] has been reserved
[    0.325956] system 00:05: [io  0xfe00-0xfefe] has been reserved
[    0.325958] system 00:05: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.325961] system 00:05: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.325963] system 00:05: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.325966] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.326166] system 00:06: [io  0x0230-0x023f] has been reserved
[    0.326168] system 00:06: [io  0x0290-0x029f] has been reserved
[    0.326171] system 00:06: [io  0x0300-0x030f] has been reserved
[    0.326173] system 00:06: [io  0x0a30-0x0a3f] has been reserved
[    0.326175] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.326238] system 00:07: [mem 0xe0000000-0xefffffff] has been reserved
[    0.326241] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.326394] system 00:08: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.326397] system 00:08: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.326399] system 00:08: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.326401] system 00:08: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.326404] system 00:08: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.326407] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.326498] pnp: PnP ACPI: found 9 devices
[    0.333287] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.333311] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.333315] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.333318] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.333321] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.333325] pci 0000:00:14.4: PCI bridge to [bus 02]
[    0.333327] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.333333] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.333341] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.333344] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.333346] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.333348] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.333350] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff window]
[    0.333352] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff window]
[    0.333354] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.333356] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.333358] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.333361] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.333363] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.333365] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7 window]
[    0.333367] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff window]
[    0.333369] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.333371] pci_bus 0000:02: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.333373] pci_bus 0000:02: resource 8 [mem 0xd0000000-0xdfffffff window]
[    0.333375] pci_bus 0000:02: resource 9 [mem 0xf0000000-0xfebfffff window]
[    0.333415] NET: Registered protocol family 2
[    0.333643] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.333893] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.334214] TCP: Hash tables configured (established 65536 bind 65536)
[    0.334274] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.334334] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.334437] NET: Registered protocol family 1
[    0.756525] pci 0000:01:00.0: Video device with shadowed ROM
[    0.756532] PCI: CLS 64 bytes, default 64
[    0.756606] Trying to unpack rootfs image as initramfs...
[    1.329205] Freeing initrd memory: 32860K (ffff880033fc2000 - ffff880035fd9000)
[    1.329436] PCI-DMA: Disabling AGP.
[    1.329517] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.329518] PCI-DMA: using GART IOMMU.
[    1.329521] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.333310] microcode: CPU0: patch_level=0x01000095
[    1.333326] microcode: CPU1: patch_level=0x01000095
[    1.333338] microcode: CPU2: patch_level=0x01000095
[    1.333351] microcode: CPU3: patch_level=0x01000095
[    1.333424] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.333433] LVT offset 1 assigned for vector 0x400
[    1.333442] IBS: LVT offset 1 assigned
[    1.333462] perf: AMD IBS detected (0x00000007)
[    1.333587] Scanning for low memory corruption every 60 seconds
[    1.333957] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.333987] Initialise system trusted keyring
[    1.334013] audit: initializing netlink subsys (disabled)
[    1.334039] audit: type=2000 audit(1446582535.224:1): initialized
[    1.334369] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    1.334371] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.336103] zpool: loaded
[    1.336105] zbud: loaded
[    1.336313] VFS: Disk quotas dquot_6.6.0
[    1.336352] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.336924] fuse init (API version 7.23)
[    1.337082] Key type big_key registered
[    1.337562] Key type asymmetric registered
[    1.337566] Asymmetric key parser 'x509' registered
[    1.337581] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.337634] io scheduler noop registered
[    1.337637] io scheduler deadline registered (default)
[    1.337672] io scheduler cfq registered
[    1.338008] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.338016] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.338050] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    1.338051] vesafb: scrolling: redraw
[    1.338054] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.338071] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90001000000, using 5824k, total 5824k
[    1.338198] Console: switching to colour frame buffer device 175x65
[    1.338229] fb0: VESA VGA frame buffer device
[    1.338331] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.338336] ACPI: Power Button [PWRB]
[    1.338384] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.338387] ACPI: Power Button [PWRF]
[    1.339451] GHES: HEST is not enabled!
[    1.339564] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.360046] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.361920] Linux agpgart interface v0.103
[    1.364758] brd: module loaded
[    1.365918] loop: module loaded
[    1.366171] libphy: Fixed MDIO Bus: probed
[    1.366174] tun: Universal TUN/TAP device driver, 1.6
[    1.366175] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.366223] PPP generic driver version 2.4.2
[    1.366300] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.366305] ehci-pci: EHCI PCI platform driver
[    1.366489] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.366496] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.366501] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.366512] ehci-pci 0000:00:12.2: debug port 1
[    1.366554] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe9ff800
[    1.376782] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.376823] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.376825] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.376827] usb usb1: Product: EHCI Host Controller
[    1.376829] usb usb1: Manufacturer: Linux 4.2.0-16-generic ehci_hcd
[    1.376830] usb usb1: SerialNumber: 0000:00:12.2
[    1.376950] hub 1-0:1.0: USB hub found
[    1.376958] hub 1-0:1.0: 6 ports detected
[    1.377223] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.377228] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.377232] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.377241] ehci-pci 0000:00:13.2: debug port 1
[    1.377276] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe9ff400
[    1.388782] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.388816] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.388818] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.388820] usb usb2: Product: EHCI Host Controller
[    1.388821] usb usb2: Manufacturer: Linux 4.2.0-16-generic ehci_hcd
[    1.388823] usb usb2: SerialNumber: 0000:00:13.2
[    1.388927] hub 2-0:1.0: USB hub found
[    1.388937] hub 2-0:1.0: 6 ports detected
[    1.389091] ehci-platform: EHCI generic platform driver
[    1.389104] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.389107] ohci-pci: OHCI PCI platform driver
[    1.389227] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.389232] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.389252] ohci-pci 0000:00:12.0: irq 16, io mem 0xfe9fe000
[    1.448841] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.448843] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.448844] usb usb3: Product: OHCI PCI host controller
[    1.448846] usb usb3: Manufacturer: Linux 4.2.0-16-generic ohci_hcd
[    1.448848] usb usb3: SerialNumber: 0000:00:12.0
[    1.448980] hub 3-0:1.0: USB hub found
[    1.448990] hub 3-0:1.0: 3 ports detected
[    1.449245] ohci-pci 0000:00:12.1: OHCI PCI host controller
[    1.449252] ohci-pci 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.449277] ohci-pci 0000:00:12.1: irq 16, io mem 0xfe9fd000
[    1.508878] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.508880] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.508882] usb usb4: Product: OHCI PCI host controller
[    1.508884] usb usb4: Manufacturer: Linux 4.2.0-16-generic ohci_hcd
[    1.508885] usb usb4: SerialNumber: 0000:00:12.1
[    1.509001] hub 4-0:1.0: USB hub found
[    1.509009] hub 4-0:1.0: 3 ports detected
[    1.509206] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.509211] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.509235] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe9fc000
[    1.568905] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.568907] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.568909] usb usb5: Product: OHCI PCI host controller
[    1.568910] usb usb5: Manufacturer: Linux 4.2.0-16-generic ohci_hcd
[    1.568912] usb usb5: SerialNumber: 0000:00:13.0
[    1.569020] hub 5-0:1.0: USB hub found
[    1.569028] hub 5-0:1.0: 3 ports detected
[    1.569220] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.569225] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.569248] ohci-pci 0000:00:13.1: irq 18, io mem 0xfe9fb000
[    1.628944] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.628946] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.628948] usb usb6: Product: OHCI PCI host controller
[    1.628949] usb usb6: Manufacturer: Linux 4.2.0-16-generic ohci_hcd
[    1.628951] usb usb6: SerialNumber: 0000:00:13.1
[    1.629053] hub 6-0:1.0: USB hub found
[    1.629060] hub 6-0:1.0: 3 ports detected
[    1.629258] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.629263] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.629278] ohci-pci 0000:00:14.5: irq 18, io mem 0xfe9fa000
[    1.688938] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    1.688969] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.688972] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.688974] usb usb7: Product: OHCI PCI host controller
[    1.688975] usb usb7: Manufacturer: Linux 4.2.0-16-generic ohci_hcd
[    1.688977] usb usb7: SerialNumber: 0000:00:14.5
[    1.689079] hub 7-0:1.0: USB hub found
[    1.689087] hub 7-0:1.0: 2 ports detected
[    1.689171] ohci-platform: OHCI generic platform driver
[    1.689184] uhci_hcd: USB Universal Host Controller Interface driver
[    1.689246] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.689630] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.689637] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.689844] mousedev: PS/2 mouse device common for all mice
[    1.689988] rtc_cmos 00:01: RTC can wake from S4
[    1.690053] rtc rtc0: invalid alarm value: 2015-11-31 14:22:12
[    1.690096] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.690120] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.690130] i2c /dev entries driver
[    1.690218] device-mapper: uevent: version 1.0.3
[    1.690293] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: [email]dm-devel@redhat.com[/email]
[    1.690313] ledtrig-cpu: registered to indicate activity on CPUs
[    1.690452] PCCT header not found.
[    1.690713] NET: Registered protocol family 10
[    1.690923] NET: Registered protocol family 17
[    1.690936] Key type dns_resolver registered
[    1.691350] Loading compiled-in X.509 certificates
[    1.692507] Loaded X.509 cert 'Build time autogenerated kernel key: 6a1c9c21f04ab86fd1d7ced6ca113540fc8e35b6'
[    1.692524] registered taskstats version 1
[    1.692544] zswap: loading zswap
[    1.692546] zswap: using zbud pool
[    1.692551] zswap: using lzo compressor
[    1.694810] Key type trusted registered
[    1.698896] Key type encrypted registered
[    1.698905] AppArmor: AppArmor sha1 policy hashing enabled
[    1.698910] ima: No TPM chip found, activating TPM-bypass!
[    1.698940] evm: HMAC attrs: 0x1
[    1.699199]   Magic number: 7:304:497
[    1.699318] rtc_cmos 00:01: setting system clock to 2015-11-03 20:28:56 UTC (1446582536)
[    1.699431] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.699882] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.699883] EDD information not available.
[    1.699939] PM: Hibernation image not present or could not be loaded.
[    1.700519] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    1.700522] Write protecting the kernel read-only data: 12288k
[    1.700722] Freeing unused kernel memory: 36K (ffff8800017f7000 - ffff880001800000)
[    1.700873] Freeing unused kernel memory: 296K (ffff880001bb6000 - ffff880001c00000)
[    1.714532] random: systemd-udevd urandom read with 2 bits of entropy available
[    1.758872] wmi: Mapper loaded
[    1.762045] ahci 0000:00:11.0: version 3.0
[    1.762303] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.762307] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.765110] [drm] Initialized drm 1.1.0 20060810
[    1.765994] scsi host0: ahci
[    1.766145] scsi host1: ahci
[    1.766259] scsi host2: ahci
[    1.766416] scsi host3: ahci
[    1.766475] ata1: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd00 irq 22
[    1.766479] ata2: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd80 irq 22
[    1.766483] ata3: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe00 irq 22
[    1.766486] ata4: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe80 irq 22
[    1.767695] scsi host4: pata_atiixp
[    1.767834] scsi host5: pata_atiixp
[    1.767893] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.767895] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.769530] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.769633] r8169 0000:02:06.0 (unnamed net_device) (uninitialized): not PCI Express
[    1.769947] r8169 0000:02:06.0 eth0: RTL8169sb/8110sb at 0xffffc90000e8ac00, 74:ea:3a:b3:81:c2, XID 10000000 IRQ 21
[    1.769949] r8169 0000:02:06.0 eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[    1.796591] r8169 0000:02:06.0 enp2s6: renamed from eth0
[    1.796932] [drm] radeon kernel modesetting enabled.
[    1.799624] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.799627] AMD IOMMUv2 functionality not available on this system
[    1.802948] CRAT table not found
[    1.802950] Finished initializing topology ret=0
[    1.803011] kfd kfd: Initialized module
[    1.803303] checking generic (d0000000 5b0000) vs hw (d0000000 10000000)
[    1.803305] fb: switching to radeondrmfb from VESA VGA
[    1.803344] Console: switching to colour dummy device 80x25
[    1.803736] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68F9 0x1043:0x0374).
[    1.803747] [drm] register mmio base: 0xFEAE0000
[    1.803749] [drm] register mmio size: 131072
[    1.804457] ATOM BIOS: 68F9.12.19.0.2.AS02
[    1.804514] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.804516] radeon 0000:01:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    1.804518] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.804519] [drm] RAM width 64bits DDR
[    1.804584] [TTM] Zone  kernel: Available graphics memory: 4087692 kiB
[    1.804586] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.804587] [TTM] Initializing pool allocator
[    1.804592] [TTM] Initializing DMA pool allocator
[    1.804615] [drm] radeon: 512M of VRAM memory ready
[    1.804617] [drm] radeon: 1024M of GTT memory ready.
[    1.804626] [drm] Loading CEDAR Microcode
[    1.804711] [drm] Internal thermal controller without fan control
[    1.832678] [drm] radeon: dpm initialized
[    1.832799] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.833518] usb 1-2: New USB device found, idVendor=03f0, idProduct=c511
[    1.833522] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.833525] usb 1-2: Product: ENVY 4500 series
[    1.833527] usb 1-2: Manufacturer: HP
[    1.833528] usb 1-2: SerialNumber: CN39O2V26805X4
[    1.834725] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    1.851193] [drm] PCIE GART of 1024M enabled (table at 0x000000000025E000).
[    1.851286] radeon 0000:01:00.0: WB enabled
[    1.851289] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880221fd4c00
[    1.851292] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880221fd4c0c
[    1.852028] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xffffc9000181c418
[    1.852030] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.852031] [drm] Driver supports precise vblank timestamp query.
[    1.852033] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    1.852066] radeon 0000:01:00.0: radeon: using MSI.
[    1.852094] [drm] radeon: irq initialized.
[    1.868224] [drm] ring test on 0 succeeded in 1 usecs
[    1.868229] [drm] ring test on 3 succeeded in 2 usecs
[    1.953428] ata6.01: ATAPI: Optiarc DVD RW AD-7260S, 1.03, max UDMA/100
[    1.969435] ata6.01: configured for UDMA/100
[    2.054094] [drm] ring test on 5 succeeded in 1 usecs
[    2.054100] [drm] UVD initialized successfully.
[    2.054291] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.054329] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.085205] ata2: SATA link down (SStatus 0 SControl 300)
[    2.109175] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    2.242439] usb 1-3: New USB device found, idVendor=05e3, idProduct=0608
[    2.242441] usb 1-3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.242444] usb 1-3: Product: USB2.0 Hub
[    2.242854] hub 1-3:1.0: USB hub found
[    2.243189] hub 1-3:1.0: 4 ports detected
[    2.257275] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.257301] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.257327] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.257504] ata1.00: ATA-9: TOSHIBA THNSNJ128GCSU, JURA0101, max UDMA/100
[    2.257508] ata1.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.258164] ata3.00: ATA-8: WDC WD10EZRX-00A8LB0, 01.01A01, max UDMA/133
[    2.258167] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.258204] ata1.00: configured for UDMA/100
[    2.258350] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA THNSNJ12 0101 PQ: 0 ANSI: 5
[    2.258370] ata4.00: ATA-8: ST31000520AS, CC32, max UDMA/133
[    2.258373] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.258623] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    2.258673] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.258746] sd 0:0:0:0: [sda] Write Protect is off
[    2.258749] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.258798] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.259569]  sda: sda1 sda2 < sda5 >
[    2.259595] ata4.00: configured for UDMA/133
[    2.259892] ata3.00: configured for UDMA/133
[    2.259988] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EZRX-00A 1A01 PQ: 0 ANSI: 5
[    2.260002] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.260168] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.260170] sd 2:0:0:0: [sdb] 4096-byte physical blocks
[    2.260194] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.260254] sd 2:0:0:0: [sdb] Write Protect is off
[    2.260257] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.260295] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.260329] scsi 3:0:0:0: Direct-Access     ATA      ST31000520AS     CC32 PQ: 0 ANSI: 5
[    2.260560] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.260606] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.260683] sd 3:0:0:0: [sdc] Write Protect is off
[    2.260686] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.260727] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.261981] scsi 5:0:1:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.03 PQ: 0 ANSI: 5
[    2.268315]  sdc: sdc1
[    2.268583] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.278901]  sdb: sdb1
[    2.279020] sr 5:0:1:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.279023] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.279143] sr 5:0:1:0: Attached scsi CD-ROM sr0
[    2.279242] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.279303] sr 5:0:1:0: Attached scsi generic sg3 type 5
[    2.333301] tsc: Refined TSC clocksource calibration: 2511.188 MHz
[    2.333307] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x243282a39fc, max_idle_ns: 440795292954 ns
[    2.513402] usb 1-3.1: new full-speed USB device number 4 using ehci-pci
[    2.611473] usb 1-3.1: New USB device found, idVendor=045e, idProduct=0745
[    2.611476] usb 1-3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.611479] usb 1-3.1: Product: Microsoft® 2.4GHz Transceiver v8.0
[    2.611481] usb 1-3.1: Manufacturer: Microsoft
[    2.615675] hidraw: raw HID events driver (C) Jiri Kosina
[    2.631072] usbcore: registered new interface driver usbhid
[    2.631074] usbhid: USB HID core driver
[    2.632982] input: Microsoft Microsoft® 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3.1/1-3.1:1.0/0003:045E:0745.0001/input/input5
[    2.685601] hid-generic 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® 2.4GHz Transceiver v8.0] on usb-0000:00:12.2-3.1/input0
[    2.686183] input: Microsoft Microsoft® 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3.1/1-3.1:1.1/0003:045E:0745.0002/input/input6
[    2.721548] [drm] ib test on ring 5 succeeded
[    2.722452] [drm] Radeon Display Connectors
[    2.722454] [drm] Connector 0:
[    2.722455] [drm]   HDMI-A-1
[    2.722456] [drm]   HPD1
[    2.722458] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    2.722459] [drm]   Encoders:
[    2.722460] [drm]     DFP1: INTERNAL_UNIPHY1
[    2.722461] [drm] Connector 1:
[    2.722462] [drm]   DVI-I-1
[    2.722463] [drm]   HPD4
[    2.722465] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    2.722465] [drm]   Encoders:
[    2.722466] [drm]     DFP2: INTERNAL_UNIPHY
[    2.722468] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.722468] [drm] Connector 2:
[    2.722469] [drm]   VGA-1
[    2.722471] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    2.722472] [drm]   Encoders:
[    2.722473] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    2.741689] hid-generic 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® 2.4GHz Transceiver v8.0] on usb-0000:00:12.2-3.1/input1
[    2.752202] input: Microsoft Microsoft® 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3.1/1-3.1:1.2/0003:045E:0745.0003/input/input7
[    2.805708] hid-generic 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® 2.4GHz Transceiver v8.0] on usb-0000:00:12.2-3.1/input2
[    2.817247] [drm] fb mappable at 0xD045F000
[    2.817250] [drm] vram apper at 0xD0000000
[    2.817251] [drm] size 8294400
[    2.817252] [drm] fb depth is 24
[    2.817254] [drm]    pitch is 7680
[    2.817325] fbcon: radeondrmfb (fb0) is primary device
[    2.817421] Console: switching to colour frame buffer device 240x67
[    2.817457] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.817459] radeon 0000:01:00.0: registered panic notifier
[    2.821671] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 0
[    2.856887] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.938066] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    2.945228] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    2.945425] systemd[1]: Detected architecture x86-64.
[    2.945682] systemd[1]: Set hostname to <MOE>.
[    3.019585] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    3.019625] systemd[1]: Reached target User and Group Name Lookups.
[    3.019670] systemd[1]: Created slice Root Slice.
[    3.019723] systemd[1]: Listening on udev Control Socket.
[    3.019838] systemd[1]: Created slice System Slice.
[    3.019952] systemd[1]: Created slice system-getty.slice.
[    3.020009] systemd[1]: Listening on Journal Socket (/dev/log).
[    3.020044] systemd[1]: Listening on udev Kernel Socket.
[    3.020121] systemd[1]: Created slice User and Session Slice.
[    3.020167] systemd[1]: Listening on Journal Socket.
[    3.020910] systemd[1]: Starting Setup Virtual Console...
[    3.021768] systemd[1]: Mounting POSIX Message Queue File System...
[    3.022738] systemd[1]: Starting udev Coldplug all Devices...
[    3.024294] systemd[1]: Starting Load Kernel Modules...
[    3.025153] systemd[1]: Mounting Huge Pages File System...
[    3.026280] systemd[1]: Started Braille Device Support.
[    3.027571] systemd[1]: Starting Uncomplicated firewall...
[    3.028485] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    3.029304] systemd[1]: Mounting Debug File System...
[    3.030273] systemd[1]: Started Read required files in advance.
[    3.030489] systemd[1]: Listening on Journal Audit Socket.
[    3.030557] systemd[1]: Listening on fsck to fsckd communication Socket.
[    3.030791] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    3.031966] systemd[1]: Reached target Encrypted Volumes.
[    3.034237] systemd[1]: Starting Increase datagram queue length...
[    3.034305] systemd[1]: Reached target Slices.
[    3.034421] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    3.034461] systemd[1]: Reached target Remote File Systems (Pre).
[    3.035756] systemd[1]: Mounted POSIX Message Queue File System.
[    3.035802] systemd[1]: Mounted Huge Pages File System.
[    3.037831] systemd[1]: Started Setup Virtual Console.
[    3.038340] systemd[1]: Started Uncomplicated firewall.
[    3.038563] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    3.040519] systemd[1]: Mounted Debug File System.
[    3.043361] systemd[1]: Started Increase datagram queue length.
[    3.047502] lp: driver loaded but no devices found
[    3.051747] ppdev: user-space parallel port driver
[    3.055101] parport_pc 00:02: reported by Plug and Play ACPI
[    3.055199] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    3.056875] systemd[1]: Listening on Syslog Socket.
[    3.057896] systemd[1]: Starting Journal Service...
[    3.059196] systemd[1]: Starting Create Static Device Nodes in /dev...
[    3.085252] systemd[1]: Started Create Static Device Nodes in /dev.
[    3.086323] systemd[1]: Starting udev Kernel Device Manager...
[    3.091836] systemd[1]: Started udev Coldplug all Devices.
[    3.111061] systemd[1]: Started udev Kernel Device Manager.
[    3.113073] systemd[1]: Starting Show Plymouth Boot Screen...
[    3.114455] systemd[1]: Starting Remount Root and Kernel File Systems...
[    3.120469] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.122733] systemd[1]: Started Remount Root and Kernel File Systems.
[    3.124093] systemd[1]: Starting Load/Save Random Seed...
[    3.124508] systemd[1]: Reached target Local File Systems (Pre).
[    3.124720] systemd[1]: Reached target Local File Systems.
[    3.127427] systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
[    3.128326] systemd[1]: Starting LSB: AppArmor initialization...
[    3.137249] systemd[1]: Starting Clean up any mess left by 0dns-up...
[    3.138860] systemd[1]: Starting Set console keymap...
[    3.138902] systemd[1]: Reached target Remote File Systems.
[    3.143282] systemd[1]: Starting Wait for all "auto" /etc/network/interfaces to be up for network-online.target...
[    3.143908] systemd[1]: Started Journal Service.
[    3.149936] lp0: using parport0 (interrupt-driven).
[    3.223102] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.230350] systemd-journald[254]: Received request to flush runtime journal from PID 1
[    3.251559] random: nonblocking pool is initialized
[    3.273089] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B0F (\SOR1) (20150619/utaddress-254)
[    3.273098] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B2F (\SMRG) (20150619/utaddress-254)
[    3.273104] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B2F (\_SB_.PCI0.SBRG.ASOC.SMRG) (20150619/utaddress-254)
[    3.273109] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.278281] audit: type=1400 audit(1446582538.076:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=411 comm="apparmor_parser"
[    3.278293] audit: type=1400 audit(1446582538.076:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=411 comm="apparmor_parser"
[    3.280531] audit: type=1400 audit(1446582538.076:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=411 comm="apparmor_parser"
[    3.280541] audit: type=1400 audit(1446582538.076:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=411 comm="apparmor_parser"
[    3.280546] audit: type=1400 audit(1446582538.076:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=411 comm="apparmor_parser"
[    3.280551] audit: type=1400 audit(1446582538.076:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=411 comm="apparmor_parser"
[    3.292424] MCE: In-kernel MCE decoding enabled.
[    3.294709] EDAC MC: Ver: 3.0.0
[    3.294761] audit: type=1400 audit(1446582538.092:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=411 comm="apparmor_parser"
[    3.294774] audit: type=1400 audit(1446582538.092:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=411 comm="apparmor_parser"
[    3.294780] audit: type=1400 audit(1446582538.092:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=411 comm="apparmor_parser"
[    3.298104] AMD64 EDAC driver v3.4.0
[    3.298141] EDAC amd64: DRAM ECC disabled.
[    3.298148] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[    3.301031] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
[    3.334221] clocksource: Switched to clocksource tsc
[    3.352673] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    3.364511] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[    3.365264] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input8
[    3.372524] snd_hda_codec_via hdaudioC0D0: autoconfig for VT1708S: line_outs=4 (0x1c/0x19/0x22/0x23/0x0) type:line
[    3.372549] snd_hda_codec_via hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.372552] snd_hda_codec_via hdaudioC0D0:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
[    3.372554] snd_hda_codec_via hdaudioC0D0:    mono: mono_out=0x0
[    3.372563] snd_hda_codec_via hdaudioC0D0:    dig-out=0x20/0x21
[    3.372564] snd_hda_codec_via hdaudioC0D0:    inputs:
[    3.372567] snd_hda_codec_via hdaudioC0D0:      Rear Mic=0x1a
[    3.372569] snd_hda_codec_via hdaudioC0D0:      Front Mic=0x1e
[    3.372571] snd_hda_codec_via hdaudioC0D0:      Line=0x1b
[    3.391108] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[    3.391202] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[    3.391277] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[    3.391408] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[    3.391540] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
[    3.391662] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input14
[    3.391966] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input15
[    3.392116] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input16
[    3.395227] kvm: disabled by bios
[    3.446903] kvm: disabled by bios
[    3.466221] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[    3.574292] Adding 8386556k swap on /dev/sda5.  Priority:-1 extents:1 across:8386556k SSFS
[    3.645104] cgroup: new mount options do not match the existing superblock, will be ignored
[    3.766123] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[    3.841895] IPv6: ADDRCONF(NETDEV_UP): enp2s6: link is not ready
[    3.845861] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[    3.849224] vboxdrv: Found 4 processor cores
[    3.850749] r8169 0000:02:06.0 enp2s6: link down
[    3.850768] r8169 0000:02:06.0 enp2s6: link down
[    3.850795] IPv6: ADDRCONF(NETDEV_UP): enp2s6: link is not ready
[    3.868674] vboxdrv: TSC mode is Invariant, tentative frequency 2511154187 Hz
[    3.868679] vboxdrv: Successfully loaded version 5.0.4_Ubuntu (interface 0x00240000)
[    3.877631] VBoxNetFlt: Successfully started.
[    3.888885] VBoxNetAdp: Successfully started.
[    3.894929] VBoxPciLinuxInit
[    3.900138] vboxpci: IOMMU not found (not registered)
[    3.940246] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0xC511
[    3.940304] usbcore: registered new interface driver usblp
[    4.066272] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[    4.366439] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[    6.998196] r8169 0000:02:06.0 enp2s6: link up
[    6.998209] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s6: link becomes ready
[    8.980152] usblp1: removed
[    8.982045] usblp 1-2:1.1: usblp1: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0xC511

---

