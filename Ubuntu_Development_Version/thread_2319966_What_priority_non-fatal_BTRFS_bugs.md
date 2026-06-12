---
title: "What priority non-fatal BTRFS bugs?"
date: 2016-04-09
forum: Ubuntu Development Version
---

### Post by bcschmerker on 2016-04-09
I noticed during boot that SystemD issues a series of warnings specific to the B-Tree File System, which I use for /var and /home on my rig; they involve primary partitions for 500GiB Toshiba® SATA 2.6 drives on two specific ports of the Gigabyte® GA-MA78GM-S2HP.  I have both consistent "failed to find root 8" errors on startup and hit-and-miss unmounts of /var and /home during shutdown; the attached DMesg from startup 8 April 2016 is a typical boot my rig and also includes some errors irrelevant to the BTrFS issue.  Which bugs, if any, are applicable to the warnings in said DMesg; and which, if any, need upstream attention?

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-18-generic (buildd@lcy01-05) (gcc version 5.3.1 20160405 (Ubuntu 5.3.1-13ubuntu4) ) #34-Ubuntu SMP Wed Apr 6 14:01:02 UTC 2016 (Ubuntu 4.4.0-18.34-generic 4.4.6)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.4.0-18-generic root=UUID=7e8f5247-d70e-4084-b1cd-6cf9227030ba ro debug
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] tseg: 00afe00000
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000afddffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000afde0000-0x00000000afde2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000afde3000-0x00000000afdeffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000afdf0000-0x00000000afdfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000012fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-MA78GM-S2HP/GA-MA78GM-S2HP, BIOS F3 12/16/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00AFE00000 mask FFFFE00000 uncachable
[    0.000000]   4 base 0100000000 mask FFE0000000 write-back
[    0.000000]   5 base 0120000000 mask FFF0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2814MB, range: 2MB, type UC
[    0.000000] reg 4, base: 4GB, range: 512MB, type WB
[    0.000000] reg 5, base: 4608MB, range: 256MB, type WB
[    0.000000] total RAM covered: 2814M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 4M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2814MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xafe00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xafde0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f57d0-0x000f57df] mapped at [ffff8800000f57d0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] BRK [0x021fe000, 0x021fefff] PGTABLE
[    0.000000] BRK [0x021ff000, 0x021fffff] PGTABLE
[    0.000000] BRK [0x02200000, 0x02200fff] PGTABLE
[    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33a78000-0x35d33fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F7150 000014 (v00 GBT   )
[    0.000000] ACPI: RSDT 0x00000000AFDE3000 000030 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 0x00000000AFDE3040 000074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 0x00000000AFDE30C0 006467 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 0x00000000AFDE0000 000040
[    0.000000] ACPI: MCFG 0x00000000AFDE9640 00003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 0x00000000AFDE9540 000084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000012fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x12fff8000-0x12fffcfff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000012fffffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000afddffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000012fffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000012fffffff]
[    0.000000] On node 0 totalpages: 916862
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11192 pages used for memmap
[    0.000000]   DMA32 zone: 716256 pages, LIFO batch:31
[    0.000000]   Normal zone: 3072 pages used for memmap
[    0.000000]   Normal zone: 196608 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafde0000-0xafde2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xafde3000-0xafdeffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafdf0000-0xafdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafe00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
[    0.000000] e820: [mem 0xafe00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88012fc00000 s98008 r8192 d28968 u524288
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 902513
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-4.4.0-18-generic root=UUID=7e8f5247-d70e-4084-b1cd-6cf9227030ba ro debug
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] AGP: Node 0: aperture [bus addr 0xa4000000-0xa5ffffff] (32MB)
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
[    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
[    0.000000] AGP: This costs you 64MB of RAM
[    0.000000] AGP: Mapping aperture over RAM [mem 0xa4000000-0xa7ffffff] (65536KB)
[    0.000000] PM: Registered nosave memory: [mem 0xa4000000-0xa7ffffff]
[    0.000000] Memory: 3423608K/3667448K available (8355K kernel code, 1278K rwdata, 3920K rodata, 1476K init, 1292K bss, 243840K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2812.243 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.008048] Calibrating delay loop (skipped), value calculated using timer frequency.. 5624.48 BogoMIPS (lpj=11248972)
[    0.009110] pid_max: default: 32768 minimum: 301
[    0.012007] ACPI: Core revision 20150930
[    0.015068] ACPI: 1 ACPI AML tables successfully acquired and loaded
[    0.015194] Security Framework initialized
[    0.015228] Yama: becoming mindful.
[    0.015282] AppArmor: AppArmor initialized
[    0.015729] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.018269] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.019668] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.019710] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.020104] Initializing cgroup subsys io
[    0.020143] Initializing cgroup subsys memory
[    0.020186] Initializing cgroup subsys devices
[    0.020223] Initializing cgroup subsys freezer
[    0.020260] Initializing cgroup subsys net_cls
[    0.020296] Initializing cgroup subsys perf_event
[    0.020332] Initializing cgroup subsys net_prio
[    0.020369] Initializing cgroup subsys hugetlb
[    0.020407] Initializing cgroup subsys pids
[    0.020459] CPU: Physical Processor ID: 0
[    0.020493] CPU: Processor Core ID: 0
[    0.020528] mce: CPU supports 5 MCE banks
[    0.020569] LVT offset 0 assigned for vector 0xf9
[    0.020606] process: using AMD E400 aware idle routine
[    0.020640] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.020675] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4, 1GB 0
[    0.020957] Freeing SMP alternatives memory: 28K (ffffffff820b2000 - ffffffff820b9000)
[    0.024017] ftrace: allocating 31877 entries in 125 pages
[    0.036163] smpboot: Max logical packages: 2
[    0.040203] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080000] smpboot: CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (family: 0xf, model: 0x6b, stepping: 0x2)
[    0.080000] Performance Events: AMD PMU driver.
[    0.080000] ... version:                0
[    0.080000] ... bit width:              48
[    0.080000] ... generic registers:      4
[    0.080000] ... value mask:             0000ffffffffffff
[    0.080000] ... max period:             00007fffffffffff
[    0.080000] ... fixed-purpose events:   0
[    0.080000] ... event mask:             000000000000000f
[    0.080000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080000] x86: Booting SMP configuration:
[    0.080000] .... node  #0, CPUs:      #1
[    0.156037] x86: Booted up 1 node, 2 CPUs
[    0.156102] smpboot: Total of 2 processors activated (11249.14 BogoMIPS)
[    0.156641] devtmpfs: initialized
[    0.160902] evm: security.selinux
[    0.160937] evm: security.SMACK64
[    0.160972] evm: security.SMACK64EXEC
[    0.161006] evm: security.SMACK64TRANSMUTE
[    0.161040] evm: security.SMACK64MMAP
[    0.161074] evm: security.ima
[    0.161109] evm: security.capability
[    0.161197] PM: Registering ACPI NVS region [mem 0xafde0000-0xafde2fff] (12288 bytes)
[    0.161197] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.161197] pinctrl core: initialized pinctrl subsystem
[    0.161197] RTC time:  4:36:53, date: 04/09/16
[    0.161197] NET: Registered protocol family 16
[    0.172007] cpuidle: using governor ladder
[    0.180003] cpuidle: using governor menu
[    0.180040] PCCT header not found.
[    0.180077] node 0 link 0: io port [b000, ffff]
[    0.180112] TOM: 00000000d0000000 aka 3328M
[    0.180147] node 0 link 0: mmio [a0000, bffff]
[    0.180212] node 0 link 0: mmio [d0000000, dfffffff]
[    0.180275] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.180339] node 0 link 0: mmio [e0000000, e05fffff]
[    0.180401] TOM2: 0000000130000000 aka 4864M
[    0.180435] bus: [bus 00-05] on node 0 link 0
[    0.180469] bus: 00 [io  0x0000-0xffff]
[    0.180502] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.180536] bus: 00 [mem 0xd0000000-0xefffffff]
[    0.180570] bus: 00 [mem 0xf0000000-0xffffffff]
[    0.180604] bus: 00 [mem 0x130000000-0xfcffffffff]
[    0.180690] ACPI: bus type PCI registered
[    0.180725] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.180838] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.180877] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.180926] PCI: Using configuration type 1 for base access
[    0.188119] ACPI: Added _OSI(Module Device)
[    0.188159] ACPI: Added _OSI(Processor Device)
[    0.188193] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.188227] ACPI: Added _OSI(Processor Aggregator Device)
[    0.192190] ACPI: Interpreter enabled
[    0.192234] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.192333] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.192440] ACPI: (supports S0 S3 S4 S5)
[    0.192474] ACPI: Using IOAPIC for interrupt routing
[    0.192575] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.197311] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.197357] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.197398] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.197688] PCI host bridge to bus 0000:00
[    0.197724] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.197759] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.197794] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.197831] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.197869] pci_bus 0000:00: root bus resource [mem 0xcff00000-0xfebfffff window]
[    0.197907] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.197951] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
[    0.198003] pci 0000:00:00.0: [Firmware Bug]: reg 0x1c: invalid BAR (can't size)
[    0.198141] pci 0000:00:01.0: [1022:9602] type 01 class 0x060400
[    0.198281] pci 0000:00:04.0: [1022:9604] type 01 class 0x060400
[    0.198355] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.198437] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.198519] pci 0000:00:0a.0: [1022:9609] type 01 class 0x060400
[    0.198593] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.198672] pci 0000:00:0a.0: System wakeup disabled by ACPI
[    0.198763] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.198824] pci 0000:00:11.0: reg 0x10: [io  0xff00-0xff07]
[    0.198867] pci 0000:00:11.0: reg 0x14: [io  0xfe00-0xfe03]
[    0.198911] pci 0000:00:11.0: reg 0x18: [io  0xfd00-0xfd07]
[    0.198953] pci 0000:00:11.0: reg 0x1c: [io  0xfc00-0xfc03]
[    0.198998] pci 0000:00:11.0: reg 0x20: [io  0xfb00-0xfb0f]
[    0.199041] pci 0000:00:11.0: reg 0x24: [mem 0xfe02f000-0xfe02f3ff]
[    0.199188] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.199239] pci 0000:00:12.0: reg 0x10: [mem 0xfe02e000-0xfe02efff]
[    0.199373] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.199449] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.199499] pci 0000:00:12.1: reg 0x10: [mem 0xfe02d000-0xfe02dfff]
[    0.199633] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.199714] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.199775] pci 0000:00:12.2: reg 0x10: [mem 0xfe02c000-0xfe02c0ff]
[    0.199884] pci 0000:00:12.2: supports D1 D2
[    0.199918] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.200010] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.200096] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.200146] pci 0000:00:13.0: reg 0x10: [mem 0xfe02b000-0xfe02bfff]
[    0.200280] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.200357] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.200407] pci 0000:00:13.1: reg 0x10: [mem 0xfe02a000-0xfe02afff]
[    0.200541] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.200623] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.200684] pci 0000:00:13.2: reg 0x10: [mem 0xfe029000-0xfe0290ff]
[    0.200793] pci 0000:00:13.2: supports D1 D2
[    0.200828] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.200909] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.200996] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.201199] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.201259] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.201302] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.201345] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.201388] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.201431] pci 0000:00:14.1: reg 0x20: [io  0xfa00-0xfa0f]
[    0.201486] pci 0000:00:14.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.201521] pci 0000:00:14.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.201557] pci 0000:00:14.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.201592] pci 0000:00:14.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.201722] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.201907] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.202021] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.202098] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.202148] pci 0000:00:14.5: reg 0x10: [mem 0xfe028000-0xfe028fff]
[    0.202283] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.202363] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.202476] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.202586] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.202695] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.202856] pci 0000:01:05.0: [1002:9610] type 00 class 0x030000
[    0.202902] pci 0000:01:05.0: reg 0x10: [mem 0xd0000000-0xdfffffff pref]
[    0.202939] pci 0000:01:05.0: reg 0x14: [io  0xee00-0xeeff]
[    0.202977] pci 0000:01:05.0: reg 0x18: [mem 0xfdde0000-0xfddeffff]
[    0.203020] pci 0000:01:05.0: reg 0x24: [mem 0xfdc00000-0xfdcfffff]
[    0.203071] pci 0000:01:05.0: supports D1 D2
[    0.203144] pci 0000:01:05.1: [1002:960f] type 00 class 0x040300
[    0.204013] pci 0000:01:05.1: reg 0x10: [mem 0xfddfc000-0xfddfffff]
[    0.204077] pci 0000:01:05.1: supports D1 D2
[    0.204180] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.204216] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.204253] pci 0000:00:01.0:   bridge window [mem 0xfdc00000-0xfddfffff]
[    0.204289] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.204385] pci 0000:02:00.0: [10b5:8112] type 01 class 0x060400
[    0.204592] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.204639] pci 0000:00:04.0: PCI bridge to [bus 02-03]
[    0.204676] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.204712] pci 0000:00:04.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.204748] pci 0000:00:04.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.204860] pci 0000:03:04.0: [13f6:8788] type 00 class 0x040100
[    0.204933] pci 0000:03:04.0: reg 0x10: [io  0xde00-0xdeff]
[    0.205090] pci 0000:03:04.0: supports D1 D2
[    0.205215] pci 0000:02:00.0: PCI bridge to [bus 03]
[    0.205254] pci 0000:02:00.0:   bridge window [io  0xd000-0xdfff]
[    0.205293] pci 0000:02:00.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.205332] pci 0000:02:00.0:   bridge window [mem 0xfd800000-0xfd8fffff pref]
[    0.205428] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    0.205492] pci 0000:04:00.0: reg 0x10: [io  0xce00-0xceff]
[    0.205548] pci 0000:04:00.0: reg 0x18: [mem 0xfdeff000-0xfdefffff 64bit pref]
[    0.205597] pci 0000:04:00.0: reg 0x20: [mem 0xfdee0000-0xfdeeffff 64bit pref]
[    0.205644] pci 0000:04:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.205726] pci 0000:04:00.0: supports D1 D2
[    0.205761] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212021] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.212059] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    0.212097] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.212134] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.212239] pci 0000:05:0e.0: [104c:8024] type 00 class 0x0c0010
[    0.212306] pci 0000:05:0e.0: reg 0x10: [mem 0xfdaff000-0xfdaff7ff]
[    0.212354] pci 0000:05:0e.0: reg 0x14: [mem 0xfdaf8000-0xfdafbfff]
[    0.212479] pci 0000:05:0e.0: supports D1 D2
[    0.212515] pci 0000:05:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.212624] pci 0000:00:14.4: PCI bridge to [bus 05] (subtractive decode)
[    0.212663] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.212702] pci 0000:00:14.4:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.212741] pci 0000:00:14.4:   bridge window [mem 0xfd900000-0xfd9fffff pref]
[    0.212781] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.212822] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.212863] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.212903] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff window] (subtractive decode)
[    0.212943] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xfebfffff window] (subtractive decode)
[    0.213241] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.213651] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.214061] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.214469] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.214878] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.215288] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.215694] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.216080] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.217108] vgaarb: setting as boot device: PCI:0000:01:05.0
[    0.217108] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.217108] vgaarb: loaded
[    0.217108] vgaarb: bridge control possible 0000:01:05.0
[    0.217108] SCSI subsystem initialized
[    0.217108] libata version 3.00 loaded.
[    0.217108] ACPI: bus type USB registered
[    0.217108] usbcore: registered new interface driver usbfs
[    0.217108] usbcore: registered new interface driver hub
[    0.217108] usbcore: registered new device driver usb
[    0.217108] PCI: Using ACPI for IRQ routing
[    0.227399] PCI: pci_cache_line_size set to 64 bytes
[    0.227510] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.227546] e820: reserve RAM buffer [mem 0xafde0000-0xafffffff]
[    0.227743] NetLabel: Initializing
[    0.227779] NetLabel:  domain hash size = 128
[    0.227814] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.227862] NetLabel:  unlabeled traffic allowed by default
[    0.228025] clocksource: Switched to clocksource refined-jiffies
[    0.237574] AppArmor: AppArmor Filesystem Enabled
[    0.237699] pnp: PnP ACPI init
[    0.237870] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.237907] system 00:00: [io  0x0220-0x0225] has been reserved
[    0.237941] system 00:00: [io  0x0290-0x0294] has been reserved
[    0.237980] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.238266] pnp 00:01: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:04:00.0 BAR 6 [mem 0x00000000-0x0000ffff pref]
[    0.238333] system 00:01: [io  0x4100-0x411f] has been reserved
[    0.238369] system 00:01: [io  0x0228-0x022f] has been reserved
[    0.238404] system 00:01: [io  0x0238-0x023f] has been reserved
[    0.238438] system 00:01: [io  0x040b] has been reserved
[    0.238473] system 00:01: [io  0x04d6] has been reserved
[    0.238507] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.238541] system 00:01: [io  0x0c14] has been reserved
[    0.238576] system 00:01: [io  0x0c50-0x0c52] has been reserved
[    0.238612] system 00:01: [io  0x0c6c-0x0c6d] has been reserved
[    0.238646] system 00:01: [io  0x0c6f] has been reserved
[    0.238681] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
[    0.238716] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
[    0.238751] system 00:01: [io  0x0cd4-0x0cdf] has been reserved
[    0.238786] system 00:01: [io  0x4000-0x40fe] could not be reserved
[    0.238820] system 00:01: [io  0x4210-0x4217] has been reserved
[    0.238855] system 00:01: [io  0x0b00-0x0b0f] has been reserved
[    0.238890] system 00:01: [io  0x0b10-0x0b1f] has been reserved
[    0.238925] system 00:01: [io  0x0b20-0x0b3f] has been reserved
[    0.238961] system 00:01: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.238999] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.239202] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.239377] pnp 00:03: [dma 2]
[    0.239445] pnp 00:03: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.239679] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.239924] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.240093] pnp 00:06: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.240174] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.240276] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.240313] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.240519] system 00:09: [mem 0x000d1a00-0x000d3fff] has been reserved
[    0.240558] system 00:09: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.240593] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.240628] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.240664] system 00:09: [mem 0xafde0000-0xafdfffff] could not be reserved
[    0.240700] system 00:09: [mem 0xffff0000-0xffffffff] has been reserved
[    0.240735] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.240770] system 00:09: [mem 0x00100000-0xafddffff] could not be reserved
[    0.240806] system 00:09: [mem 0xafef0000-0xcfeeffff] could not be reserved
[    0.240841] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.240876] system 00:09: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.240911] system 00:09: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.240947] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.241001] pnp: PnP ACPI: found 10 devices
[    0.247564] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.247620] clocksource: Switched to clocksource acpi_pm
[    0.247692] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.247727] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.247763] pci 0000:00:01.0:   bridge window [mem 0xfdc00000-0xfddfffff]
[    0.247799] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.247840] pci 0000:02:00.0: PCI bridge to [bus 03]
[    0.247876] pci 0000:02:00.0:   bridge window [io  0xd000-0xdfff]
[    0.247917] pci 0000:02:00.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.247956] pci 0000:02:00.0:   bridge window [mem 0xfd800000-0xfd8fffff pref]
[    0.247956] pci 0000:00:04.0: PCI bridge to [bus 02-03]
[    0.247956] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.247956] pci 0000:00:04.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.247956] pci 0000:00:04.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.247956] pci 0000:04:00.0: BAR 6: assigned [mem 0xfdf00000-0xfdf0ffff pref]
[    0.247956] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.247956] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    0.247956] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.247956] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.247956] pci 0000:00:14.4: PCI bridge to [bus 05]
[    0.247956] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.247956] pci 0000:00:14.4:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.247956] pci 0000:00:14.4:   bridge window [mem 0xfd900000-0xfd9fffff pref]
[    0.247956] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.247956] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.247956] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.247956] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.247956] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xfebfffff window]
[    0.247956] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.247956] pci_bus 0000:01: resource 1 [mem 0xfdc00000-0xfddfffff]
[    0.247956] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.247956] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.247956] pci_bus 0000:02: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.247956] pci_bus 0000:02: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.247956] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.247956] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.247956] pci_bus 0000:03: resource 2 [mem 0xfd800000-0xfd8fffff pref]
[    0.247956] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.247956] pci_bus 0000:04: resource 1 [mem 0xfdf00000-0xfdffffff]
[    0.247956] pci_bus 0000:04: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.247956] pci_bus 0000:05: resource 0 [io  0xb000-0xbfff]
[    0.247956] pci_bus 0000:05: resource 1 [mem 0xfda00000-0xfdafffff]
[    0.247956] pci_bus 0000:05: resource 2 [mem 0xfd900000-0xfd9fffff pref]
[    0.247956] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7 window]
[    0.247956] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff window]
[    0.247956] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.247956] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.247956] pci_bus 0000:05: resource 8 [mem 0xcff00000-0xfebfffff window]
[    0.247956] NET: Registered protocol family 2
[    0.247956] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.247956] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.247956] TCP: Hash tables configured (established 32768 bind 32768)
[    0.247956] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.247956] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.247956] NET: Registered protocol family 1
[    0.247969] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.620040] pci 0000:01:05.0: Video device with shadowed ROM
[    0.620091] PCI: CLS 4 bytes, default 64
[    0.620195] Trying to unpack rootfs image as initramfs...
[    1.259516] Freeing initrd memory: 35568K (ffff880033a78000 - ffff880035d34000)
[    1.262016] PCI-DMA: Disabling AGP.
[    1.262128] PCI-DMA: aperture base @ a4000000 size 65536 KB
[    1.262162] PCI-DMA: using GART IOMMU.
[    1.262197] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.265973] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x28896e7ed69, max_idle_ns: 440795272431 ns
[    1.266097] Scanning for low memory corruption every 60 seconds
[    1.266545] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    1.266619] audit: initializing netlink subsys (disabled)
[    1.266676] audit: type=2000 audit(1460176614.263:1): initialized
[    1.267034] Initialise system trusted keyring
[    1.267223] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.269196] zbud: loaded
[    1.269514] VFS: Disk quotas dquot_6.6.0
[    1.269594] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.270385] fuse init (API version 7.23)
[    1.270608] Key type big_key registered
[    1.271376] Key type asymmetric registered
[    1.271415] Asymmetric key parser 'x509' registered
[    1.271501] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.271586] io scheduler noop registered
[    1.271622] io scheduler deadline registered (default)
[    1.271697] io scheduler cfq registered
[    1.272517] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.272559] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.272721] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.272764] ACPI: Power Button [PWRB]
[    1.272852] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.272892] ACPI: Power Button [PWRF]
[    1.273123] GHES: HEST is not enabled!
[    1.273301] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.293877] 00:04: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.296059] Linux agpgart interface v0.103
[    1.299730] brd: module loaded
[    1.301610] loop: module loaded
[    1.302199] libphy: Fixed MDIO Bus: probed
[    1.302236] tun: Universal TUN/TAP device driver, 1.6
[    1.302269] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.302368] PPP generic driver version 2.4.2
[    1.302484] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.302534] ehci-pci: EHCI PCI platform driver
[    1.302677] QUIRK: Enable AMD PLL fix
[    1.302739] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.302782] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.302823] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.302860] ehci-pci 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.302910] ehci-pci 0000:00:12.2: debug port 1
[    1.302999] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.312054] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.312168] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.312204] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.312241] usb usb1: Product: EHCI Host Controller
[    1.312276] usb usb1: Manufacturer: Linux 4.4.0-18-generic ehci_hcd
[    1.312310] usb usb1: SerialNumber: 0000:00:12.2
[    1.312516] hub 1-0:1.0: USB hub found
[    1.312557] hub 1-0:1.0: 6 ports detected
[    1.312978] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.313019] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.313060] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.313098] ehci-pci 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.313147] ehci-pci 0000:00:13.2: debug port 1
[    1.313235] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.324029] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.324126] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.324163] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.324203] usb usb2: Product: EHCI Host Controller
[    1.324238] usb usb2: Manufacturer: Linux 4.4.0-18-generic ehci_hcd
[    1.324274] usb usb2: SerialNumber: 0000:00:13.2
[    1.324449] hub 2-0:1.0: USB hub found
[    1.324490] hub 2-0:1.0: 6 ports detected
[    1.324722] ehci-platform: EHCI generic platform driver
[    1.324779] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.324819] ohci-pci: OHCI PCI platform driver
[    1.324992] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.325035] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.325112] ohci-pci 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.384067] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.384103] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.384140] usb usb3: Product: OHCI PCI host controller
[    1.384175] usb usb3: Manufacturer: Linux 4.4.0-18-generic ohci_hcd
[    1.384209] usb usb3: SerialNumber: 0000:00:12.0
[    1.384373] hub 3-0:1.0: USB hub found
[    1.384417] hub 3-0:1.0: 3 ports detected
[    1.384683] ohci-pci 0000:00:12.1: OHCI PCI host controller
[    1.384723] ohci-pci 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.384778] ohci-pci 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.444057] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.444093] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.444130] usb usb4: Product: OHCI PCI host controller
[    1.444165] usb usb4: Manufacturer: Linux 4.4.0-18-generic ohci_hcd
[    1.444199] usb usb4: SerialNumber: 0000:00:12.1
[    1.444364] hub 4-0:1.0: USB hub found
[    1.444406] hub 4-0:1.0: 3 ports detected
[    1.444669] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.444708] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.444778] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.504061] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.504097] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.504135] usb usb5: Product: OHCI PCI host controller
[    1.504169] usb usb5: Manufacturer: Linux 4.4.0-18-generic ohci_hcd
[    1.504203] usb usb5: SerialNumber: 0000:00:13.0
[    1.504369] hub 5-0:1.0: USB hub found
[    1.504411] hub 5-0:1.0: 3 ports detected
[    1.504670] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.504710] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.504766] ohci-pci 0000:00:13.1: irq 18, io mem 0xfe02a000
[    1.564057] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.564092] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.564129] usb usb6: Product: OHCI PCI host controller
[    1.564164] usb usb6: Manufacturer: Linux 4.4.0-18-generic ohci_hcd
[    1.564198] usb usb6: SerialNumber: 0000:00:13.1
[    1.564359] hub 6-0:1.0: USB hub found
[    1.564400] hub 6-0:1.0: 3 ports detected
[    1.564678] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.564718] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.564784] ohci-pci 0000:00:14.5: irq 18, io mem 0xfe028000
[    1.624038] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.624112] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.624148] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.624185] usb usb7: Product: OHCI PCI host controller
[    1.624220] usb usb7: Manufacturer: Linux 4.4.0-18-generic ohci_hcd
[    1.625249] usb usb7: SerialNumber: 0000:00:14.5
[    1.625414] hub 7-0:1.0: USB hub found
[    1.625457] hub 7-0:1.0: 2 ports detected
[    1.625626] ohci-platform: OHCI generic platform driver
[    1.625678] uhci_hcd: USB Universal Host Controller Interface driver
[    1.625806] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.626304] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.626341] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.626549] mousedev: PS/2 mouse device common for all mice
[    1.626775] rtc_cmos 00:02: RTC can wake from S4
[    1.626947] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.627013] rtc_cmos 00:02: alarms up to one month, 242 bytes nvram
[    1.627055] i2c /dev entries driver
[    1.627159] device-mapper: uevent: version 1.0.3
[    1.627285] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    1.627340] ledtrig-cpu: registered to indicate activity on CPUs
[    1.627862] NET: Registered protocol family 10
[    1.628165] NET: Registered protocol family 17
[    1.628213] Key type dns_resolver registered
[    1.628455] microcode: AMD CPU family 0xf not supported
[    1.628696] registered taskstats version 1
[    1.628746] Loading compiled-in X.509 certificates
[    1.629807] Loaded X.509 cert 'Build time autogenerated kernel key: 46aac491f1b0fe5a07252157966e4fbbb99d02a4'
[    1.629864] zswap: loaded using pool lzo/zbud
[    1.632501] Key type trusted registered
[    1.636045] usb 2-3: new high-speed USB device number 2 using ehci-pci
[    1.637709] Key type encrypted registered
[    1.637759] AppArmor: AppArmor sha1 policy hashing enabled
[    1.637796] ima: No TPM chip found, activating TPM-bypass!
[    1.637858] evm: HMAC attrs: 0x1
[    1.638235]   Magic number: 12:664:615
[    1.638293] misc tun: hash matches
[    1.638451] rtc_cmos 00:02: setting system clock to 2016-04-09 04:36:55 UTC (1460176615)
[    1.638593] powernow_k8: [Firmware Bug]: No compatible ACPI _PSS objects found.
               [Firmware Bug]: First, make sure Cool'N'Quiet is enabled in the BIOS.
               [Firmware Bug]: If that doesn't help, try upgrading your BIOS.
[    1.638649] powernow_k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (2 cpu cores) (version 2.20.00)
[    1.638693] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.638726] EDD information not available.
[    1.638822] PM: Hibernation image not present or could not be loaded.
[    1.640984] Freeing unused kernel memory: 1476K (ffffffff81f41000 - ffffffff820b2000)
[    1.641032] Write protecting the kernel read-only data: 14336k
[    1.642341] Freeing unused kernel memory: 1872K (ffff88000182c000 - ffff880001a00000)
[    1.642908] Freeing unused kernel memory: 176K (ffff880001dd4000 - ffff880001e00000)
[    1.650084] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.661424] systemd-udevd[119]: starting version 229
[    1.662487] random: systemd-udevd urandom read with 2 bits of entropy available
[    1.712653] wmi: Mapper loaded
[    1.715154] ahci 0000:00:11.0: version 3.0
[    1.715324] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.715364] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.719343] [drm] Initialized drm 1.1.0 20060810
[    1.719809] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.719862] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.720693] r8169 0000:04:00.0 eth0: RTL8168c/8111c at 0xffffc9000073c000, 00:1f:d0:d1:98:15, XID 1c4000c0 IRQ 26
[    1.720738] r8169 0000:04:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.725484] scsi host0: ahci
[    1.732773] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.735407] scsi host1: ahci
[    1.739064] scsi host2: ahci
[    1.742643] scsi host3: ahci
[    1.742800] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.742839] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.742878] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.742917] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    1.754066] Floppy drive(s): fd0 is 1.44M
[    1.756544] scsi host4: pata_atiixp
[    1.769621] usb 2-3: config index 0 descriptor too short (expected 32, got 9)
[    1.769664] usb 2-3: config 1 has 0 interfaces, different from the descriptor's value: 1
[    1.772619] usb 2-3: New USB device found, idVendor=07cc, idProduct=0301
[    1.772661] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.772698] usb 2-3: Product: Winter Ver1.3   
[    1.772733] usb 2-3: Manufacturer:         Ltd
[    1.772768] usb 2-3: SerialNumber: 392673724128
[    1.776423] scsi host5: pata_atiixp
[    1.776559] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.776595] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.783941] [drm] radeon kernel modesetting enabled.
[    1.784037] FDC 0 is a post-1991 82077
[    1.786908] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.786950] AMD IOMMUv2 functionality not available on this system
[    1.790819] CRAT table not found
[    1.790861] Finished initializing topology ret=0
[    1.790958] kfd kfd: Initialized module
[    1.791679] [drm] initializing kernel modesetting (RS780 0x1002:0x9610 0x1458:0xD000).
[    1.791739] [drm] register mmio base: 0xFDDE0000
[    1.791778] [drm] register mmio size: 65536
[    1.792168] ATOM BIOS: B27722
[    1.792227] radeon 0000:01:05.0: VRAM: 512M 0x00000000C0000000 - 0x00000000DFFFFFFF (512M used)
[    1.792265] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    1.792306] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.792340] [drm] RAM width 32bits DDR
[    1.792442] [TTM] Zone  kernel: Available graphics memory: 1764340 kiB
[    1.792477] [TTM] Initializing pool allocator
[    1.792515] [TTM] Initializing DMA pool allocator
[    1.792584] [drm] radeon: 512M of VRAM memory ready
[    1.792618] [drm] radeon: 512M of GTT memory ready.
[    1.792666] [drm] Loading RS780 Microcode
[    1.792800] [drm] radeon: power management initialized
[    1.792961] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.807383] [drm] PCIE GART of 512M enabled (table at 0x00000000C0258000).
[    1.807745] radeon 0000:01:05.0: WB enabled
[    1.807783] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff8800af720c00
[    1.808699] radeon 0000:01:05.0: fence driver on ring 5 use gpu addr 0x00000000c0056038 and cpu addr 0xffffc90000816038
[    1.808902] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.808939] [drm] Driver supports precise vblank timestamp query.
[    1.808974] radeon 0000:01:05.0: radeon: MSI limited to 32-bit
[    1.809022] [drm] radeon: irq initialized.
[    1.821360] r8169 0000:04:00.0 enp4s0: renamed from eth0
[    1.829152] firewire_ohci 0000:05:0e.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    1.840115] [drm] ring test on 0 succeeded in 1 usecs
[    1.952492] ata5.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB04, max UDMA/33
[    1.988195] ata5.01: HPA detected: current 156299375, native 156301488
[    1.988231] ata5.01: ATA-7: ST380215A, 3.AAC, max UDMA/100
[    1.988266] ata5.01: 156299375 sectors, multi 16: LBA48 
[    2.004425] ata5.00: configured for UDMA/33
[    2.014794] [drm] ring test on 5 succeeded in 1 usecs
[    2.014832] [drm] UVD initialized successfully.
[    2.014994] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.071369] ata5.01: configured for UDMA/100
[    2.232019] ata1: softreset failed (device not ready)
[    2.232055] ata1: applying PMP SRST workaround and retrying
[    2.236021] ata2: softreset failed (device not ready)
[    2.236056] ata2: applying PMP SRST workaround and retrying
[    2.236107] ata3: softreset failed (device not ready)
[    2.236143] ata3: applying PMP SRST workaround and retrying
[    2.240024] ata4: softreset failed (device not ready)
[    2.240059] ata4: applying PMP SRST workaround and retrying
[    2.268088] usb 1-1: New USB device found, idVendor=045e, idProduct=0294
[    2.268124] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.268159] usb 1-1: Product: Video Camera           
[    2.268193] usb 1-1: Manufacturer: Microsoft      
[    2.268227] usb 1-1: SerialNumber: 000F330020417701
[    2.276963] input: PS2++ Logitech TrackMan as /devices/platform/i8042/serio1/input/input4
[    2.328117] firewire_core 0000:05:0e.0: created device fw0: GUID 007eb83000001fd0, S400
[    2.404042] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.404680] ata1.00: ATA-7: WDC WD1600JS-55NCB1, 10.02E01, max UDMA/133
[    2.404715] ata1.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.405412] ata1.00: configured for UDMA/133
[    2.405670] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JS-55N 2E01 PQ: 0 ANSI: 5
[    2.405956] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.406030] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.406068] sd 0:0:0:0: [sda] Write Protect is off
[    2.406070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.406096] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.408040] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.408102] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.412050] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.430613] ata2.00: ATA-8: TOSHIBA MQ01ABD050, AX001A, max UDMA/100
[    2.430656] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.430701] ata3.00: ATA-8: TOSHIBA MQ01ABD050, AX001A, max UDMA/100
[    2.430737] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.432348] ata2.00: configured for UDMA/100
[    2.432430] ata3.00: configured for UDMA/100
[    2.432567] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD0 1A   PQ: 0 ANSI: 5
[    2.432865] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    2.432911] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    2.433004] sd 1:0:0:0: [sdb] Write Protect is off
[    2.433040] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.433096] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.433196] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.433340] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD0 1A   PQ: 0 ANSI: 5
[    2.433577] sd 2:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    2.433616] sd 2:0:0:0: [sdc] 4096-byte physical blocks
[    2.433712] sd 2:0:0:0: [sdc] Write Protect is off
[    2.433749] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.433814] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.433894] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.441567] ata4.00: ATA-8: TOSHIBA MQ01ABD050, AX001A, max UDMA/100
[    2.441604] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.443294] ata4.00: configured for UDMA/100
[    2.443499] scsi 3:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD0 1A   PQ: 0 ANSI: 5
[    2.443792] sd 3:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    2.443841] sd 3:0:0:0: [sdd] 4096-byte physical blocks
[    2.443939] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.443978] sd 3:0:0:0: [sdd] Write Protect is off
[    2.443980] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.444034] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.445044]  sda: sda1 sda2 sda3 < sda5 >
[    2.445215] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB04 PQ: 0 ANSI: 5
[    2.445679] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.464677] sr 4:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.464715] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.464889] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.464992] sr 4:0:0:0: Attached scsi generic sg4 type 5
[    2.465187] scsi 4:0:1:0: Direct-Access     ATA      ST380215A        C    PQ: 0 ANSI: 5
[    2.465423] sd 4:0:1:0: Attached scsi generic sg5 type 0
[    2.466510] sd 4:0:1:0: [sde] 156299375 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.466608] sd 4:0:1:0: [sde] Write Protect is off
[    2.466644] sd 4:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    2.466732] sd 4:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.510488]  sde: sde1 sde2 < sde5 >
[    2.510882] sd 4:0:1:0: [sde] Attached SCSI disk
[    2.545393]  sdc: sdc1 sdc2 < sdc5 >
[    2.545804] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.559965]  sdd: sdd1 sdd2 < sdd5 >
[    2.560330] sd 3:0:0:0: [sdd] Attached SCSI disk
[    2.575477]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    2.575916] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.652028] usb 4-1: new full-speed USB device number 2 using ohci-pci
[    2.660048] [drm] ib test on ring 5 succeeded
[    2.661118] [drm] Radeon Display Connectors
[    2.661156] [drm] Connector 0:
[    2.661189] [drm]   VGA-1
[    2.661232] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.661275] [drm]   Encoders:
[    2.661309] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.661348] [drm] Connector 1:
[    2.661381] [drm]   DVI-D-1
[    2.661414] [drm]   HPD1
[    2.661447] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.661483] [drm]   Encoders:
[    2.661516] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[    2.704607] [drm] fb mappable at 0xD0359000
[    2.704647] [drm] vram apper at 0xD0000000
[    2.704681] [drm] size 5787648
[    2.704714] [drm] fb depth is 24
[    2.704746] [drm]    pitch is 6400
[    2.704892] fbcon: radeondrmfb (fb0) is primary device
[    2.718104] random: nonblocking pool is initialized
[    2.733505] Console: switching to colour frame buffer device 200x56
[    2.738932] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[    2.752075] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:05.0 on minor 0
[    2.821072] usb 4-1: New USB device found, idVendor=03f0, idProduct=3402
[    2.821123] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.821166] usb 4-1: Product: photosmart 1115
[    2.821193] usb 4-1: Manufacturer: hp
[    2.821216] usb 4-1: SerialNumber: MX1AU1Y12Y0V
[    3.796019] raid6: sse2x1   gen()  3749 MB/s
[    3.864019] raid6: sse2x1   xor()  3218 MB/s
[    3.932017] raid6: sse2x2   gen()  5089 MB/s
[    4.000021] raid6: sse2x2   xor()  3609 MB/s
[    4.068024] raid6: sse2x4   gen()  5232 MB/s
[    4.136023] raid6: sse2x4   xor()  2500 MB/s
[    4.136051] raid6: using algorithm sse2x4 gen() 5232 MB/s
[    4.136084] raid6: .... xor() 2500 MB/s, rmw enabled
[    4.136116] raid6: using intx1 recovery algorithm
[    4.137642] xor: measuring software checksum speed
[    4.176013]    prefetch64-sse:  7986.000 MB/sec
[    4.216012]    generic_sse:  7592.000 MB/sec
[    4.216041] xor: using function: prefetch64-sse (7986.000 MB/sec)
[    4.234791] Btrfs loaded
[    4.336041] blk_update_request: I/O error, dev fd0, sector 0
[    4.336090] floppy: error -5 while reading block 0
[    5.625500] BTRFS: device fsid c81619ed-43dc-4ed2-912a-a331569c8e82 devid 1 transid 7191 /dev/sdd1
[    5.625689] BTRFS: device fsid 70a74a90-e612-49c9-95fe-f22e4d48db0d devid 1 transid 5597 /dev/sdc1
[   10.776476] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   11.160872] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   12.564762] systemd[1]: Mounting cgroup to /sys/fs/cgroup/cpu,cpuacct of type cgroup with options cpu,cpuacct.
[   12.564936] systemd[1]: Mounting cgroup to /sys/fs/cgroup/pids of type cgroup with options pids.
[   12.566302] systemd[1]: Mounting cgroup to /sys/fs/cgroup/hugetlb of type cgroup with options hugetlb.
[   12.567657] systemd[1]: Mounting cgroup to /sys/fs/cgroup/net_cls,net_prio of type cgroup with options net_cls,net_prio.
[   12.569075] systemd[1]: Mounting cgroup to /sys/fs/cgroup/memory of type cgroup with options memory.
[   12.570612] systemd[1]: Mounting cgroup to /sys/fs/cgroup/blkio of type cgroup with options blkio.
[   12.572132] systemd[1]: Mounting cgroup to /sys/fs/cgroup/perf_event of type cgroup with options perf_event.
[   12.573436] systemd[1]: Mounting cgroup to /sys/fs/cgroup/cpuset of type cgroup with options cpuset.
[   12.574974] systemd[1]: Mounting cgroup to /sys/fs/cgroup/freezer of type cgroup with options freezer.
[   12.576394] systemd[1]: Mounting cgroup to /sys/fs/cgroup/devices of type cgroup with options devices.
[   12.577779] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[   12.580773] systemd[1]: Detected architecture x86-64.
[   12.594511] systemd[1]: Set hostname to <hotrodgpc-desktop>.
[   12.635330] systemd[1]: Using cgroup controller name=systemd. File system hierarchy is at /sys/fs/cgroup/systemd.
[   12.636930] systemd[1]: Installed release agent.
[   12.661152] systemd[1]: Controller 'cpu' supported: no
[   12.662659] systemd[1]: Controller 'cpuacct' supported: yes
[   12.664181] systemd[1]: Controller 'blkio' supported: yes
[   12.665668] systemd[1]: Controller 'memory' supported: yes
[   12.667160] systemd[1]: Controller 'devices' supported: yes
[   12.668671] systemd[1]: Controller 'pids' supported: yes
[   12.670190] systemd[1]: Set up TFD_TIMER_CANCEL_ON_SET timerfd.
[   12.692418] systemd[1]: Enabling showing of status.
[   12.731285] systemd[285]: Spawned /lib/systemd/system-generators/systemd-dbus1-generator as 286.
[   12.733128] systemd[285]: Spawned /lib/systemd/system-generators/systemd-system-update-generator as 287.
[   12.734897] systemd[285]: Spawned /lib/systemd/system-generators/systemd-fstab-generator as 288.
[   12.736706] systemd[285]: Spawned /lib/systemd/system-generators/systemd-rc-local-generator as 289.
[   12.738466] systemd[285]: Spawned /lib/systemd/system-generators/systemd-insserv-generator as 290.
[   12.740188] systemd[285]: Spawned /lib/systemd/system-generators/systemd-hibernate-resume-generator as 291.
[   12.741970] systemd[285]: Spawned /lib/systemd/system-generators/systemd-sysv-generator as 292.
[   12.743754] systemd[285]: Spawned /lib/systemd/system-generators/systemd-getty-generator as 293.
[   12.745573] systemd[285]: Spawned /lib/systemd/system-generators/systemd-cryptsetup-generator as 294.
[   12.747329] systemd[285]: Spawned /lib/systemd/system-generators/systemd-debug-generator as 295.
[   12.749170] systemd[285]: Spawned /lib/systemd/system-generators/systemd-gpt-auto-generator as 296.
[   12.844493] systemd-fstab-generator[288]: Parsing /etc/fstab
[   12.844640] systemd-rc-local-generator[289]: Automatically adding rc-local.service.
[   12.847582] systemd-fstab-generator[288]: Found entry what=/dev/disk/by-uuid/7e8f5247-d70e-4084-b1cd-6cf9227030ba where=/ type=ext4 nofail=no noauto=no
[   12.851756] systemd[285]: /lib/systemd/system-generators/systemd-dbus1-generator succeeded.
[   12.882190] systemd-fstab-generator[288]: Found entry what=/dev/disk/by-uuid/01c37fd7-5f37-47f5-ad5b-5f6429042682 where=/boot type=ext4 nofail=no noauto=no
[   12.884069] systemd-fstab-generator[288]: Found entry what=/dev/disk/by-uuid/c81619ed-43dc-4ed2-912a-a331569c8e82 where=/home type=btrfs nofail=no noauto=no
[   12.884242] systemd-sysv-generator[292]: Looking for unit files in (higher priority first):
[   12.884245] systemd-sysv-generator[292]: 	/etc/systemd/system
[   12.884246] systemd-sysv-generator[292]: 	/run/systemd/system
[   12.884248] systemd-sysv-generator[292]: 	/usr/local/lib/systemd/system
[   12.884249] systemd-sysv-generator[292]: 	/lib/systemd/system
[   12.884251] systemd-sysv-generator[292]: 	/usr/lib/systemd/system
[   12.884266] systemd-sysv-generator[292]: Looking for SysV init scripts in:
[   12.884268] systemd-sysv-generator[292]: 	/etc/init.d
[   12.884270] systemd-sysv-generator[292]: Looking for SysV rcN.d links in:
[   12.884271] systemd-sysv-generator[292]: 	/etc
[   12.906637] systemd-gpt-auto-generator[296]: /dev/sda2: root device /dev/sda.
[   12.985758] systemd-fstab-generator[288]: Found entry what=/dev/disk/by-uuid/ed87e847-54db-4191-8466-c160276cb192 where=/opt type=ext4 nofail=no noauto=no
[   12.987557] systemd-fstab-generator[288]: Found entry what=/dev/disk/by-uuid/167b6271-5439-4784-be27-26ce9db7b50e where=/srv type=ext4 nofail=no noauto=no
[   12.989299] systemd-fstab-generator[288]: Found entry what=/dev/disk/by-uuid/75a16d97-3671-4adb-b23e-a4c282d40fb5 where=/tmp type=ext4 nofail=no noauto=no
[   12.990983] systemd-fstab-generator[288]: Found entry what=/dev/disk/by-uuid/3e23d151-f0d0-4b0c-9581-7066156eafde where=/usr type=ext4 nofail=no noauto=no
[   12.992712] systemd-fstab-generator[288]: Found entry what=/dev/disk/by-uuid/70a74a90-e612-49c9-95fe-f22e4d48db0d where=/var type=btrfs nofail=no noauto=no
[   12.994442] systemd-fstab-generator[288]: Found entry what=/dev/fd0 where=/media/floppy0 type=auto nofail=yes noauto=no
[   12.996173] systemd-fstab-generator[288]: Found entry what=/dev/mapper/cryptswap1 where=none type=swap nofail=no noauto=no
[   12.997905] systemd-fstab-generator[288]: Found entry what=/dev/mapper/cryptswap2 where=none type=swap nofail=no noauto=no
[   12.999610] systemd-fstab-generator[288]: Found entry what=/dev/mapper/cryptswap3 where=none type=swap nofail=no noauto=no
[   13.001309] systemd-fstab-generator[288]: Found entry what=/dev/mapper/cryptswap4 where=none type=swap nofail=no noauto=no
[   13.002988] systemd-fstab-generator[288]: Found entry what=/dev/mapper/cryptswap5 where=none type=swap nofail=no noauto=no
[   13.004850] systemd[285]: /lib/systemd/system-generators/systemd-fstab-generator succeeded.
[   13.006367] systemd[285]: /lib/systemd/system-generators/systemd-getty-generator succeeded.
[   13.007826] systemd[285]: /lib/systemd/system-generators/systemd-system-update-generator succeeded.
[   13.009335] systemd[285]: /lib/systemd/system-generators/systemd-debug-generator succeeded.
[   13.139768] systemd-sysv-generator[292]: Native unit for cups-browsed.service already exists, skipping.
[   13.204703] systemd-sysv-generator[292]: Native unit for procps.service already exists, skipping.
[   13.298374] systemd-sysv-generator[292]: Native unit for whoopsie.service already exists, skipping.
[   13.348527] systemd-sysv-generator[292]: Native unit for checkfs.service already exists, skipping.
[   13.350030] systemd-sysv-generator[292]: Native unit for hostname.service already exists, skipping.
[   13.351543] systemd-sysv-generator[292]: Native unit for bootmisc.service already exists, skipping.
[   13.353068] systemd-sysv-generator[292]: Native unit for x11-common.service already exists, skipping.
[   13.389224] systemd-sysv-generator[292]: Native unit for rsync.service already exists, skipping.
[   13.438903] systemd-sysv-generator[292]: Native unit for cups.service already exists, skipping.
[   13.488487] systemd-sysv-generator[292]: Native unit for avahi-daemon.service already exists, skipping.
[   13.489988] systemd-sysv-generator[292]: Native unit for mountall-bootclean.service already exists, skipping.
[   13.491507] systemd-sysv-generator[292]: Native unit for hwclock.service already exists, skipping.
[   13.540465] systemd-sysv-generator[292]: Native unit for dns-clean.service already exists, skipping.
[   13.593527] systemd-sysv-generator[292]: Native unit for cron.service already exists, skipping.
[   13.595129] systemd-sysv-generator[292]: Native unit for cryptdisks.service already exists, skipping.
[   13.624389] systemd-sysv-generator[292]: Native unit for rc.local.service already exists, skipping.
[   13.625996] systemd-sysv-generator[292]: Native unit for rc.service already exists, skipping.
[   13.627557] systemd-sysv-generator[292]: Native unit for killprocs.service already exists, skipping.
[   13.629145] systemd-sysv-generator[292]: Native unit for umountfs.service already exists, skipping.
[   13.669753] systemd-sysv-generator[292]: Native unit for networking.service already exists, skipping.
[   13.671404] systemd-sysv-generator[292]: Native unit for umountroot.service already exists, skipping.
[   13.718334] systemd-sysv-generator[292]: Native unit for kerneloops.service already exists, skipping.
[   13.719970] systemd-sysv-generator[292]: Native unit for saned.service already exists, skipping.
[   13.721582] systemd-sysv-generator[292]: Native unit for mountall.service already exists, skipping.
[   13.723108] systemd-sysv-generator[292]: Native unit for mountnfs-bootclean.service already exists, skipping.
[   13.763909] systemd-sysv-generator[292]: Native unit for unattended-upgrades.service already exists, skipping.
[   13.765519] systemd-sysv-generator[292]: Native unit for halt.service already exists, skipping.
[   13.766993] systemd-sysv-generator[292]: Native unit for umountnfs.service already exists, skipping.
[   13.813732] systemd-sysv-generator[292]: Native unit for ufw.service already exists, skipping.
[   13.854103] systemd-sysv-generator[292]: Native unit for plymouth.service already exists, skipping.
[   13.913055] systemd-sysv-generator[292]: Native unit for anacron.service already exists, skipping.
[   13.936507] systemd-gpt-auto-generator[296]: /dev/sda: not a GPT partition table, ignoring.
[   13.938285] systemd[285]: /lib/systemd/system-generators/systemd-gpt-auto-generator succeeded.
[   13.939723] systemd[285]: /lib/systemd/system-generators/systemd-cryptsetup-generator succeeded.
[   13.962424] systemd-sysv-generator[292]: Native unit for network-manager.service already exists, skipping.
[   13.989893] systemd-sysv-generator[292]: Native unit for uuidd.service already exists, skipping.
[   13.991345] systemd-sysv-generator[292]: Native unit for alsa-utils.service already exists, skipping.
[   13.992997] systemd-sysv-generator[292]: Native unit for kmod.service already exists, skipping.
[   14.022073] systemd-sysv-generator[292]: Native unit for resolvconf.service already exists, skipping.
[   14.023532] systemd-sysv-generator[292]: Native unit for reboot.service already exists, skipping.
[   14.046967] systemd-sysv-generator[292]: Native unit for dbus.service already exists, skipping.
[   14.048576] systemd-sysv-generator[292]: Native unit for plymouth-log.service already exists, skipping.
[   14.077288] systemd-sysv-generator[292]: Native unit for lm-sensors.service already exists, skipping.
[   14.078878] systemd-sysv-generator[292]: Native unit for brltty.service already exists, skipping.
[   14.088079] systemd-sysv-generator[292]: Native unit for thermald.service already exists, skipping.
[   14.135919] systemd-sysv-generator[292]: Native unit for smartmontools.service already exists, skipping.
[   14.142402] systemd-sysv-generator[292]: Native unit for udev.service already exists, skipping.
[   14.146038] systemd-sysv-generator[292]: Native unit for console-setup.service already exists, skipping.
[   14.147553] systemd-sysv-generator[292]: Native unit for rcS.service already exists, skipping.
[   14.171686] systemd-sysv-generator[292]: Native unit for bluetooth.service already exists, skipping.
[   14.173303] systemd-sysv-generator[292]: Native unit for urandom.service already exists, skipping.
[   14.179467] systemd-sysv-generator[292]: Native unit for pppd-dns.service already exists, skipping.
[   14.180997] systemd-sysv-generator[292]: Native unit for cryptdisks-early.service already exists, skipping.
[   14.182529] systemd-sysv-generator[292]: Native unit for mountdevsubfs.service already exists, skipping.
[   14.184062] systemd-sysv-generator[292]: Native unit for single.service already exists, skipping.
[   14.185573] systemd-sysv-generator[292]: Native unit for sendsigs.service already exists, skipping.
[   14.187070] systemd-sysv-generator[292]: Native unit for mountkernfs.service already exists, skipping.
[   14.212393] systemd-sysv-generator[292]: Native unit for lightdm.service already exists, skipping.
[   14.216141] systemd-sysv-generator[292]: Native unit for acpid.service already exists, skipping.
[   14.217640] systemd-sysv-generator[292]: Native unit for mountnfs.service already exists, skipping.
[   14.219148] systemd-sysv-generator[292]: Native unit for checkroot.service already exists, skipping.
[   14.220812] systemd-sysv-generator[292]: Native unit for rsyslog.service already exists, skipping.
[   14.222331] systemd-sysv-generator[292]: Native unit for checkroot-bootclean.service already exists, skipping.
[   14.223941] systemd-sysv-generator[292]: Ignoring S14bootmisc.sh symlink in rcS.d, not generating bootmisc.service.
[   14.225467] systemd-sysv-generator[292]: Ignoring S02hostname.sh symlink in rcS.d, not generating hostname.service.
[   14.226973] systemd-sysv-generator[292]: Ignoring S08kmod symlink in rcS.d, not generating kmod.service.
[   14.228490] systemd-sysv-generator[292]: Ignoring S04resolvconf symlink in rcS.d, not generating resolvconf.service.
[   14.230002] systemd-sysv-generator[292]: Ignoring S11networking symlink in rcS.d, not generating networking.service.
[   14.231509] systemd-sysv-generator[292]: Ignoring S08checkroot-bootclean.sh symlink in rcS.d, not generating checkroot-bootclean.service.
[   14.233060] systemd-sysv-generator[292]: Ignoring S02dns-clean symlink in rcS.d, not generating dns-clean.service.
[   14.234600] systemd-sysv-generator[292]: Ignoring S06checkroot.sh symlink in rcS.d, not generating checkroot.service.
[   14.236167] systemd-sysv-generator[292]: Ignoring S10checkfs.sh symlink in rcS.d, not generating checkfs.service.
[   14.237730] systemd-sysv-generator[292]: Ignoring S02alsa-utils symlink in rcS.d, not generating alsa-utils.service.
[   14.239281] systemd-sysv-generator[292]: Ignoring S02ufw symlink in rcS.d, not generating ufw.service.
[   14.240785] systemd-sysv-generator[292]: Ignoring S01console-setup symlink in rcS.d, not generating console-setup.service.
[   14.242375] systemd-sysv-generator[292]: Ignoring S02mountkernfs.sh symlink in rcS.d, not generating mountkernfs.service.
[   14.243987] systemd-sysv-generator[292]: Ignoring S04mountdevsubfs.sh symlink in rcS.d, not generating mountdevsubfs.service.
[   14.245634] systemd-sysv-generator[292]: Ignoring S12mountall-bootclean.sh symlink in rcS.d, not generating mountall-bootclean.service.
[   14.247296] systemd-sysv-generator[292]: Ignoring S02pppd-dns symlink in rcS.d, not generating pppd-dns.service.
[   14.248975] systemd-sysv-generator[292]: Ignoring S02lm-sensors symlink in rcS.d, not generating lm-sensors.service.
[   14.250655] systemd-sysv-generator[292]: Ignoring S08urandom symlink in rcS.d, not generating urandom.service.
[   14.252343] systemd-sysv-generator[292]: Ignoring S04brltty symlink in rcS.d, not generating brltty.service.
[   14.254030] systemd-sysv-generator[292]: Ignoring S13mountnfs-bootclean.sh symlink in rcS.d, not generating mountnfs-bootclean.service.
[   14.255742] systemd-sysv-generator[292]: Ignoring S11mountall.sh symlink in rcS.d, not generating mountall.service.
[   14.257401] systemd-sysv-generator[292]: Ignoring S12mountnfs.sh symlink in rcS.d, not generating mountnfs.service.
[   14.259106] systemd-sysv-generator[292]: Ignoring S02x11-common symlink in rcS.d, not generating x11-common.service.
[   14.260833] systemd-sysv-generator[292]: Ignoring S07cryptdisks-early symlink in rcS.d, not generating cryptdisks-early.service.
[   14.262556] systemd-sysv-generator[292]: Ignoring S05hwclock.sh symlink in rcS.d, not generating hwclock.service.
[   14.264282] systemd-sysv-generator[292]: Ignoring S03udev symlink in rcS.d, not generating udev.service.
[   14.266006] systemd-sysv-generator[292]: Ignoring S09cryptdisks symlink in rcS.d, not generating cryptdisks.service.
[   14.267723] systemd-sysv-generator[292]: Ignoring S02plymouth-log symlink in rcS.d, not generating plymouth-log.service.
[   14.269468] systemd-sysv-generator[292]: Ignoring S04procps symlink in rcS.d, not generating procps.service.
[   14.271332] systemd-sysv-generator[292]: Ignoring S01killprocs symlink in rc1.d, not generating killprocs.service.
[   14.273072] systemd-sysv-generator[292]: Ignoring K01alsa-utils symlink in rc1.d, not generating alsa-utils.service.
[   14.274783] systemd-sysv-generator[292]: Ignoring K01cups-browsed symlink in rc1.d, not generating cups-browsed.service.
[   14.276563] systemd-sysv-generator[292]: Ignoring K02avahi-daemon symlink in rc1.d, not generating avahi-daemon.service.
[   14.278326] systemd-sysv-generator[292]: Ignoring K01uuidd symlink in rc1.d, not generating uuidd.service.
[   14.280106] systemd-sysv-generator[292]: Ignoring K01saned symlink in rc1.d, not generating saned.service.
[   14.281854] systemd-sysv-generator[292]: Ignoring K01smartmontools symlink in rc1.d, not generating smartmontools.service.
[   14.283622] systemd-sysv-generator[292]: Ignoring K04rsyslog symlink in rc1.d, not generating rsyslog.service.
[   14.285406] systemd-sysv-generator[292]: Ignoring K01bluetooth symlink in rc1.d, not generating bluetooth.service.
[   14.287191] systemd-sysv-generator[292]: Ignoring K01thermald symlink in rc1.d, not generating thermald.service.
[   14.288997] systemd-sysv-generator[292]: Ignoring S02single symlink in rc1.d, not generating single.service.
[   14.290716] systemd-sysv-generator[292]: Ignoring K01kerneloops symlink in rc1.d, not generating kerneloops.service.
[   14.292533] systemd-sysv-generator[292]: Ignoring K01lightdm symlink in rc1.d, not generating lightdm.service.
[   14.294341] systemd-sysv-generator[292]: Ignoring K01whoopsie symlink in rc1.d, not generating whoopsie.service.
[   14.296173] systemd-sysv-generator[292]: Ignoring K01cups symlink in rc1.d, not generating cups.service.
[   14.297994] systemd-sysv-generator[292]: Ignoring K01ufw symlink in rc1.d, not generating ufw.service.
[   14.299960] systemd-sysv-generator[292]: Ignoring S02acpid symlink in rc2.d, not generating acpid.service.
[   14.301808] systemd-sysv-generator[292]: Ignoring S05plymouth symlink in rc2.d, not generating plymouth.service.
[   14.303651] systemd-sysv-generator[292]: Ignoring S04cups-browsed symlink in rc2.d, not generating cups-browsed.service.
[   14.305523] systemd-sysv-generator[292]: Ignoring S04saned symlink in rc2.d, not generating saned.service.
[   14.307311] systemd-sysv-generator[292]: Ignoring S02thermald symlink in rc2.d, not generating thermald.service.
[   14.309190] systemd-sysv-generator[292]: Ignoring S01uuidd symlink in rc2.d, not generating uuidd.service.
[   14.311069] systemd-sysv-generator[292]: Ignoring S02dbus symlink in rc2.d, not generating dbus.service.
[   14.312966] systemd-sysv-generator[292]: Ignoring S02smartmontools symlink in rc2.d, not generating smartmontools.service.
[   14.314866] systemd-sysv-generator[292]: Ignoring S03lightdm symlink in rc2.d, not generating lightdm.service.
[   14.316782] systemd-sysv-generator[292]: Ignoring S02rsync symlink in rc2.d, not generating rsync.service.
[   14.318698] systemd-sysv-generator[292]: Ignoring S04cups symlink in rc2.d, not generating cups.service.
[   14.320605] systemd-sysv-generator[292]: Ignoring S03bluetooth symlink in rc2.d, not generating bluetooth.service.
[   14.322528] systemd-sysv-generator[292]: Ignoring S02kerneloops symlink in rc2.d, not generating kerneloops.service.
[   14.324391] systemd-sysv-generator[292]: Ignoring S02whoopsie symlink in rc2.d, not generating whoopsie.service.
[   14.326317] systemd-sysv-generator[292]: Ignoring S02cron symlink in rc2.d, not generating cron.service.
[   14.328266] systemd-sysv-generator[292]: Ignoring S03avahi-daemon symlink in rc2.d, not generating avahi-daemon.service.
[   14.330200] systemd-sysv-generator[292]: Ignoring S01rsyslog symlink in rc2.d, not generating rsyslog.service.
[   14.332140] systemd-sysv-generator[292]: Ignoring S05rc.local symlink in rc2.d, not generating rc.local.service.
[   14.334059] systemd-sysv-generator[292]: Ignoring S02anacron symlink in rc2.d, not generating anacron.service.
[   14.336104] systemd-sysv-generator[292]: Ignoring S02acpid symlink in rc3.d, not generating acpid.service.
[   14.338029] systemd-sysv-generator[292]: Ignoring S05plymouth symlink in rc3.d, not generating plymouth.service.
[   14.339924] systemd-sysv-generator[292]: Ignoring S04cups-browsed symlink in rc3.d, not generating cups-browsed.service.
[   14.341832] systemd-sysv-generator[292]: Ignoring S04saned symlink in rc3.d, not generating saned.service.
[   14.343762] systemd-sysv-generator[292]: Ignoring S02thermald symlink in rc3.d, not generating thermald.service.
[   14.345698] systemd-sysv-generator[292]: Ignoring S01uuidd symlink in rc3.d, not generating uuidd.service.
[   14.347608] systemd-sysv-generator[292]: Ignoring S02dbus symlink in rc3.d, not generating dbus.service.
[   14.349514] systemd-sysv-generator[292]: Ignoring S02smartmontools symlink in rc3.d, not generating smartmontools.service.
[   14.351428] systemd-sysv-generator[292]: Ignoring S03lightdm symlink in rc3.d, not generating lightdm.service.
[   14.353345] systemd-sysv-generator[292]: Ignoring S02rsync symlink in rc3.d, not generating rsync.service.
[   14.355254] systemd-sysv-generator[292]: Ignoring S04cups symlink in rc3.d, not generating cups.service.
[   14.357093] systemd-sysv-generator[292]: Ignoring S03bluetooth symlink in rc3.d, not generating bluetooth.service.
[   14.358965] systemd-sysv-generator[292]: Ignoring S02kerneloops symlink in rc3.d, not generating kerneloops.service.
[   14.360884] systemd-sysv-generator[292]: Ignoring S02whoopsie symlink in rc3.d, not generating whoopsie.service.
[   14.362799] systemd-sysv-generator[292]: Ignoring S02cron symlink in rc3.d, not generating cron.service.
[   14.364710] systemd-sysv-generator[292]: Ignoring S03avahi-daemon symlink in rc3.d, not generating avahi-daemon.service.
[   14.366607] systemd-sysv-generator[292]: Ignoring S01rsyslog symlink in rc3.d, not generating rsyslog.service.
[   14.368520] systemd-sysv-generator[292]: Ignoring S05rc.local symlink in rc3.d, not generating rc.local.service.
[   14.370416] systemd-sysv-generator[292]: Ignoring S02anacron symlink in rc3.d, not generating anacron.service.
[   14.372465] systemd-sysv-generator[292]: Ignoring S02acpid symlink in rc4.d, not generating acpid.service.
[   14.374279] systemd-sysv-generator[292]: Ignoring S05plymouth symlink in rc4.d, not generating plymouth.service.
[   14.376178] systemd-sysv-generator[292]: Ignoring S04cups-browsed symlink in rc4.d, not generating cups-browsed.service.
[   14.378074] systemd-sysv-generator[292]: Ignoring S04saned symlink in rc4.d, not generating saned.service.
[   14.379968] systemd-sysv-generator[292]: Ignoring S02thermald symlink in rc4.d, not generating thermald.service.
[   14.381884] systemd-sysv-generator[292]: Ignoring S01uuidd symlink in rc4.d, not generating uuidd.service.
[   14.383783] systemd-sysv-generator[292]: Ignoring S02dbus symlink in rc4.d, not generating dbus.service.
[   14.385714] systemd-sysv-generator[292]: Ignoring S02smartmontools symlink in rc4.d, not generating smartmontools.service.
[   14.387643] systemd-sysv-generator[292]: Ignoring S03lightdm symlink in rc4.d, not generating lightdm.service.
[   14.389561] systemd-sysv-generator[292]: Ignoring S02rsync symlink in rc4.d, not generating rsync.service.
[   14.391426] systemd-sysv-generator[292]: Ignoring S04cups symlink in rc4.d, not generating cups.service.
[   14.393350] systemd-sysv-generator[292]: Ignoring S03bluetooth symlink in rc4.d, not generating bluetooth.service.
[   14.395276] systemd-sysv-generator[292]: Ignoring S02kerneloops symlink in rc4.d, not generating kerneloops.service.
[   14.397214] systemd-sysv-generator[292]: Ignoring S02whoopsie symlink in rc4.d, not generating whoopsie.service.
[   14.399141] systemd-sysv-generator[292]: Ignoring S02cron symlink in rc4.d, not generating cron.service.
[   14.401071] systemd-sysv-generator[292]: Ignoring S03avahi-daemon symlink in rc4.d, not generating avahi-daemon.service.
[   14.403006] systemd-sysv-generator[292]: Ignoring S01rsyslog symlink in rc4.d, not generating rsyslog.service.
[   14.404961] systemd-sysv-generator[292]: Ignoring S05rc.local symlink in rc4.d, not generating rc.local.service.
[   14.406849] systemd-sysv-generator[292]: Ignoring S02anacron symlink in rc4.d, not generating anacron.service.
[   14.408890] systemd-sysv-generator[292]: Ignoring S02acpid symlink in rc5.d, not generating acpid.service.
[   14.410811] systemd-sysv-generator[292]: Ignoring S05plymouth symlink in rc5.d, not generating plymouth.service.
[   14.412748] systemd-sysv-generator[292]: Ignoring S04cups-browsed symlink in rc5.d, not generating cups-browsed.service.
[   14.414679] systemd-sysv-generator[292]: Ignoring S04saned symlink in rc5.d, not generating saned.service.
[   14.416625] systemd-sysv-generator[292]: Ignoring S02thermald symlink in rc5.d, not generating thermald.service.
[   14.418554] systemd-sysv-generator[292]: Ignoring S01uuidd symlink in rc5.d, not generating uuidd.service.
[   14.420494] systemd-sysv-generator[292]: Ignoring S02dbus symlink in rc5.d, not generating dbus.service.
[   14.422411] systemd-sysv-generator[292]: Ignoring S02smartmontools symlink in rc5.d, not generating smartmontools.service.
[   14.424277] systemd-sysv-generator[292]: Ignoring S03lightdm symlink in rc5.d, not generating lightdm.service.
[   14.426216] systemd-sysv-generator[292]: Ignoring S02rsync symlink in rc5.d, not generating rsync.service.
[   14.428165] systemd-sysv-generator[292]: Ignoring S04cups symlink in rc5.d, not generating cups.service.
[   14.430085] systemd-sysv-generator[292]: Ignoring S03bluetooth symlink in rc5.d, not generating bluetooth.service.
[   14.432027] systemd-sysv-generator[292]: Ignoring S02kerneloops symlink in rc5.d, not generating kerneloops.service.
[   14.433957] systemd-sysv-generator[292]: Ignoring S02whoopsie symlink in rc5.d, not generating whoopsie.service.
[   14.435880] systemd-sysv-generator[292]: Ignoring S02cron symlink in rc5.d, not generating cron.service.
[   14.437817] systemd-sysv-generator[292]: Ignoring S03avahi-daemon symlink in rc5.d, not generating avahi-daemon.service.
[   14.439721] systemd-sysv-generator[292]: Ignoring S01rsyslog symlink in rc5.d, not generating rsyslog.service.
[   14.441609] systemd-sysv-generator[292]: Ignoring S05rc.local symlink in rc5.d, not generating rc.local.service.
[   14.443542] systemd-sysv-generator[292]: Ignoring S02anacron symlink in rc5.d, not generating anacron.service.
[   14.445607] systemd-sysv-generator[292]: Ignoring K01alsa-utils symlink in rc0.d, not generating alsa-utils.service.
[   14.447549] systemd-sysv-generator[292]: Ignoring K01cups-browsed symlink in rc0.d, not generating cups-browsed.service.
[   14.449498] systemd-sysv-generator[292]: Ignoring K02avahi-daemon symlink in rc0.d, not generating avahi-daemon.service.
[   14.451414] systemd-sysv-generator[292]: Ignoring K01uuidd symlink in rc0.d, not generating uuidd.service.
[   14.453344] systemd-sysv-generator[292]: Ignoring K05umountnfs.sh symlink in rc0.d, not generating umountnfs.service.
[   14.455272] systemd-sysv-generator[292]: Ignoring K01urandom symlink in rc0.d, not generating urandom.service.
[   14.457140] systemd-sysv-generator[292]: Ignoring K07umountfs symlink in rc0.d, not generating umountfs.service.
[   14.459042] systemd-sysv-generator[292]: Ignoring K04rsyslog symlink in rc0.d, not generating rsyslog.service.
[   14.460966] systemd-sysv-generator[292]: Ignoring K09cryptdisks-early symlink in rc0.d, not generating cryptdisks-early.service.
[   14.462903] systemd-sysv-generator[292]: Ignoring K01bluetooth symlink in rc0.d, not generating bluetooth.service.
[   14.464846] systemd-sysv-generator[292]: Ignoring K01thermald symlink in rc0.d, not generating thermald.service.
[   14.466791] systemd-sysv-generator[292]: Ignoring K05hwclock.sh symlink in rc0.d, not generating hwclock.service.
[   14.468735] systemd-sysv-generator[292]: Ignoring K01resolvconf symlink in rc0.d, not generating resolvconf.service.
[   14.470656] systemd-sysv-generator[292]: Ignoring K10umountroot symlink in rc0.d, not generating umountroot.service.
[   14.472563] systemd-sysv-generator[292]: Ignoring K01kerneloops symlink in rc0.d, not generating kerneloops.service.
[   14.474368] systemd-sysv-generator[292]: Ignoring K01lightdm symlink in rc0.d, not generating lightdm.service.
[   14.476253] systemd-sysv-generator[292]: Ignoring K01plymouth symlink in rc0.d, not generating plymouth.service.
[   14.478132] systemd-sysv-generator[292]: Ignoring K11halt symlink in rc0.d, not generating halt.service.
[   14.480025] systemd-sysv-generator[292]: Ignoring K08cryptdisks symlink in rc0.d, not generating cryptdisks.service.
[   14.481912] systemd-sysv-generator[292]: Ignoring K06networking symlink in rc0.d, not generating networking.service.
[   14.483780] systemd-sysv-generator[292]: Ignoring K01unattended-upgrades symlink in rc0.d, not generating unattended-upgrades.service.
[   14.485673] systemd-sysv-generator[292]: Ignoring K03sendsigs symlink in rc0.d, not generating sendsigs.service.
[   14.487689] systemd-sysv-generator[292]: Ignoring K01alsa-utils symlink in rc6.d, not generating alsa-utils.service.
[   14.489567] systemd-sysv-generator[292]: Ignoring K01cups-browsed symlink in rc6.d, not generating cups-browsed.service.
[   14.491399] systemd-sysv-generator[292]: Ignoring K02avahi-daemon symlink in rc6.d, not generating avahi-daemon.service.
[   14.493274] systemd-sysv-generator[292]: Ignoring K01uuidd symlink in rc6.d, not generating uuidd.service.
[   14.495134] systemd-sysv-generator[292]: Ignoring K05umountnfs.sh symlink in rc6.d, not generating umountnfs.service.
[   14.497012] systemd-sysv-generator[292]: Ignoring K01urandom symlink in rc6.d, not generating urandom.service.
[   14.498885] systemd-sysv-generator[292]: Ignoring K07umountfs symlink in rc6.d, not generating umountfs.service.
[   14.500773] systemd-sysv-generator[292]: Ignoring K04rsyslog symlink in rc6.d, not generating rsyslog.service.
[   14.502640] systemd-sysv-generator[292]: Ignoring K09cryptdisks-early symlink in rc6.d, not generating cryptdisks-early.service.
[   14.504528] systemd-sysv-generator[292]: Ignoring K01bluetooth symlink in rc6.d, not generating bluetooth.service.
[   14.506388] systemd-sysv-generator[292]: Ignoring K01thermald symlink in rc6.d, not generating thermald.service.
[   14.508227] systemd-sysv-generator[292]: Ignoring K05hwclock.sh symlink in rc6.d, not generating hwclock.service.
[   14.510109] systemd-sysv-generator[292]: Ignoring K11reboot symlink in rc6.d, not generating reboot.service.
[   14.511982] systemd-sysv-generator[292]: Ignoring K01resolvconf symlink in rc6.d, not generating resolvconf.service.
[   14.513865] systemd-sysv-generator[292]: Ignoring K10umountroot symlink in rc6.d, not generating umountroot.service.
[   14.515732] systemd-sysv-generator[292]: Ignoring K01kerneloops symlink in rc6.d, not generating kerneloops.service.
[   14.517588] systemd-sysv-generator[292]: Ignoring K01lightdm symlink in rc6.d, not generating lightdm.service.
[   14.519430] systemd-sysv-generator[292]: Ignoring K01plymouth symlink in rc6.d, not generating plymouth.service.
[   14.521284] systemd-sysv-generator[292]: Ignoring K08cryptdisks symlink in rc6.d, not generating cryptdisks.service.
[   14.523095] systemd-sysv-generator[292]: Ignoring K06networking symlink in rc6.d, not generating networking.service.
[   14.524883] systemd-sysv-generator[292]: Ignoring K01unattended-upgrades symlink in rc6.d, not generating unattended-upgrades.service.
[   14.526738] systemd-sysv-generator[292]: Ignoring K03sendsigs symlink in rc6.d, not generating sendsigs.service.
[   14.528619] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/grub-common
[   14.538087] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/hdparm
[   14.540239] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/sensord
[   14.580180] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/apport
[   14.587028] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/apparmor
[   14.588970] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/irqbalance
[   14.590757] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/ld10k1
[   14.618622] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/ondemand
[   14.620443] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/speech-dispatcher
[   14.622230] systemd-sysv-generator[292]: Loading SysV script /etc/init.d/hddtemp
[   14.651610] systemd[285]: /lib/systemd/system-generators/systemd-sysv-generator succeeded.
[   14.653275] systemd[285]: /lib/systemd/system-generators/systemd-hibernate-resume-generator succeeded.
[   14.654896] systemd[285]: /lib/systemd/system-generators/systemd-insserv-generator succeeded.
[   14.656484] systemd[285]: /lib/systemd/system-generators/systemd-rc-local-generator succeeded.
[   14.658294] systemd[1]: system-generators succeeded.
[   14.660032] systemd[1]: Looking for unit files in (higher priority first):
[   14.661621] systemd[1]: 	/etc/systemd/system
[   14.663181] systemd[1]: 	/run/systemd/system
[   14.664741] systemd[1]: 	/run/systemd/generator
[   14.666256] systemd[1]: 	/usr/local/lib/systemd/system
[   14.667748] systemd[1]: 	/lib/systemd/system
[   14.669230] systemd[1]: 	/usr/lib/systemd/system
[   14.670674] systemd[1]: 	/run/systemd/generator.late
[   14.672123] systemd[1]: Looking for SysV init scripts in:
[   14.673515] systemd[1]: 	/etc/init.d
[   14.674919] systemd[1]: Looking for SysV rcN.d links in:
[   14.676376] systemd[1]: 	/etc
[   14.678864] systemd[1]: Unit type .busname is not supported on this system.
[   14.748204] systemd[1]: run-systemd-journal-socket.mount: Failed to load configuration: No such file or directory
[   14.749711] systemd[1]: run.mount: Failed to load configuration: No such file or directory
[   14.751179] systemd[1]: run-systemd.mount: Failed to load configuration: No such file or directory
[   14.752690] systemd[1]: run-systemd-journal.mount: Failed to load configuration: No such file or directory
[   14.754185] systemd[1]: run-systemd-journal-stdout.mount: Failed to load configuration: No such file or directory
[   14.789574] systemd[1]: systemd-sysusers.service: Failed to load configuration: No such file or directory
[   14.791482] systemd[1]: run-udev.mount: Failed to load configuration: No such file or directory
[   14.793017] systemd[1]: run-udev-control.mount: Failed to load configuration: No such file or directory
[   14.798892] systemd[1]: keyboard-setup.service: Failed to load configuration: No such file or directory
[   14.800637] systemd[1]: run-systemd-ask\x2dpassword.mount: Failed to load configuration: No such file or directory
[   14.812315] systemd[1]: var-tmp.mount: Failed to load configuration: No such file or directory
[   14.837404] systemd[1]: etc.mount: Failed to load configuration: No such file or directory
[   14.838945] systemd[1]: etc-acpi.mount: Failed to load configuration: No such file or directory
[   14.840439] systemd[1]: etc-acpi-events.mount: Failed to load configuration: No such file or directory
[   14.842277] systemd[1]: run-acpid.socket.mount: Failed to load configuration: No such file or directory
[   14.859459] systemd[1]: var-lib.mount: Failed to load configuration: No such file or directory
[   14.861057] systemd[1]: var-lib-systemd.mount: Failed to load configuration: No such file or directory
[   14.862605] systemd[1]: var-lib-systemd-timers.mount: Failed to load configuration: No such file or directory
[   14.864581] systemd[1]: var-lib-systemd-random\x2dseed.mount: Failed to load configuration: No such file or directory
[   14.866423] systemd[1]: var-log.mount: Failed to load configuration: No such file or directory
[   14.868022] systemd[1]: var-log-wtmp.mount: Failed to load configuration: No such file or directory
[   14.869626] systemd[1]: auditd.service: Failed to load configuration: No such file or directory
[   14.871455] systemd[1]: dev.mount: Failed to load configuration: No such file or directory
[   14.873293] systemd[1]: sys.mount: Failed to load configuration: No such file or directory
[   14.874818] systemd[1]: sys-fs.mount: Failed to load configuration: No such file or directory
[   14.876436] systemd[1]: sys-fs-fuse.mount: Failed to load configuration: No such file or directory
[   14.878268] systemd[1]: systemd-update-done.service: Failed to load configuration: No such file or directory
[   14.882291] systemd[1]: proc.mount: Failed to load configuration: No such file or directory
[   14.883914] systemd[1]: proc-sys.mount: Failed to load configuration: No such file or directory
[   14.885566] systemd[1]: proc-sys-fs.mount: Failed to load configuration: No such file or directory
[   14.891165] systemd[1]: systemd-vconsole-setup.service: Failed to load configuration: No such file or directory
[   14.893554] systemd[1]: sys-kernel.mount: Failed to load configuration: No such file or directory
[   14.896447] systemd[1]: var-log-journal.mount: Failed to load configuration: No such file or directory
[   14.899440] systemd[1]: var-lib-brltty.mount: Failed to load configuration: No such file or directory
[   14.921922] systemd[1]: run-systemd-netif.mount: Failed to load configuration: No such file or directory
[   14.923705] systemd[1]: run-systemd-netif-state.mount: Failed to load configuration: No such file or directory
[   14.963218] systemd[1]: var-run.mount: Failed to load configuration: No such file or directory
[   14.965136] systemd[1]: var-run-dbus.mount: Failed to load configuration: No such file or directory
[   14.967015] systemd[1]: var-run-dbus-system_bus_socket.mount: Failed to load configuration: No such file or directory
[   14.990347] systemd[1]: root.mount: Failed to load configuration: No such file or directory
[   14.992866] systemd[1]: var-lib-systemd-clock.mount: Failed to load configuration: No such file or directory
[   14.995222] systemd[1]: dev-mapper.mount: Failed to load configuration: No such file or directory
[   14.997199] systemd[1]: dev-mapper-cryptswap1.mount: Failed to load configuration: No such file or directory
[   14.999298] systemd[1]: dev-mapper-cryptswap2.mount: Failed to load configuration: No such file or directory
[   15.001380] systemd[1]: dev-mapper-cryptswap3.mount: Failed to load configuration: No such file or directory
[   15.003431] systemd[1]: dev-mapper-cryptswap4.mount: Failed to load configuration: No such file or directory
[   15.005502] systemd[1]: dev-mapper-cryptswap5.mount: Failed to load configuration: No such file or directory
[   15.008102] systemd[1]: run-systemd-journal-syslog.mount: Failed to load configuration: No such file or directory
[   15.010638] systemd[1]: run-systemd-journal-dev\x2dlog.mount: Failed to load configuration: No such file or directory
[   15.022414] systemd[1]: run-systemd-initctl.mount: Failed to load configuration: No such file or directory
[   15.024369] systemd[1]: run-systemd-initctl-fifo.mount: Failed to load configuration: No such file or directory
[   15.050260] systemd[1]: run-apport.socket.mount: Failed to load configuration: No such file or directory
[   15.079734] systemd[1]: var-run-cups.mount: Failed to load configuration: No such file or directory
[   15.081820] systemd[1]: var-run-cups-cups.sock.mount: Failed to load configuration: No such file or directory
[   15.084286] systemd[1]: var-run-avahi\x2ddaemon.mount: Failed to load configuration: No such file or directory
[   15.086398] systemd[1]: var-run-avahi\x2ddaemon-socket.mount: Failed to load configuration: No such file or directory
[   15.088903] systemd[1]: run-uuidd.mount: Failed to load configuration: No such file or directory
[   15.090923] systemd[1]: run-uuidd-request.mount: Failed to load configuration: No such file or directory
[   15.093316] systemd[1]: dev-disk.mount: Failed to load configuration: No such file or directory
[   15.095407] systemd[1]: dev-disk-by\x2duuid.mount: Failed to load configuration: No such file or directory
[   15.097530] systemd[1]: dev-disk-by\x2duuid-01c37fd7\x2d5f37\x2d47f5\x2dad5b\x2d5f6429042682.mount: Failed to load configuration: No such file or directory
[   15.100459] systemd[1]: run-systemd-fsck.progress.mount: Failed to load configuration: No such file or directory
[   15.103017] systemd[1]: dev-disk-by\x2duuid-c81619ed\x2d43dc\x2d4ed2\x2d912a\x2da331569c8e82.mount: Failed to load configuration: No such file or directory
[   15.105649] systemd[1]: dev-disk-by\x2duuid-ed87e847\x2d54db\x2d4191\x2d8466\x2dc160276cb192.mount: Failed to load configuration: No such file or directory
[   15.108207] systemd[1]: dev-disk-by\x2duuid-167b6271\x2d5439\x2d4784\x2dbe27\x2d26ce9db7b50e.mount: Failed to load configuration: No such file or directory
[   15.110801] systemd[1]: dev-disk-by\x2duuid-75a16d97\x2d3671\x2d4adb\x2db23e\x2da4c282d40fb5.mount: Failed to load configuration: No such file or directory
[   15.113323] systemd[1]: dev-disk-by\x2duuid-3e23d151\x2df0d0\x2d4b0c\x2d9581\x2d7066156eafde.mount: Failed to load configuration: No such file or directory
[   15.115704] systemd[1]: dev-disk-by\x2duuid-70a74a90\x2de612\x2d49c9\x2d95fe\x2df22e4d48db0d.mount: Failed to load configuration: No such file or directory
[   15.205012] systemd[1]: festival.service: Failed to load configuration: No such file or directory
[   15.211211] systemd[1]: syslog.target: Failed to load configuration: No such file or directory
[   15.221259] systemd[1]: var-cache.mount: Failed to load configuration: No such file or directory
[   15.223330] systemd[1]: var-cache-cups.mount: Failed to load configuration: No such file or directory
[   15.225408] systemd[1]: var-cache-cups-org.cups.cupsd.mount: Failed to load configuration: No such file or directory
[   15.389111] systemd[1]: dev-disk-by\x2duuid-7e8f5247\x2dd70e\x2d4084\x2db1cd\x2d6cf9227030ba.mount: Failed to load configuration: No such file or directory
[   15.391259] systemd[1]: Using notification socket /run/systemd/notify
[   15.393504] systemd[1]: Successfully created private D-Bus server.
[   15.395642] systemd[1]: dev-sda2.device: Changed dead -> tentative
[   15.397783] systemd[1]: dev-sdb1.device: Changed dead -> tentative
[   15.399887] systemd[1]: -.mount: Changed dead -> mounted
[   15.402023] systemd[1]: usr.mount: Changed dead -> mounted
[   15.404137] systemd[1]: usr.mount: Unit is bound to inactive unit dev-disk-by\x2duuid-3e23d151\x2df0d0\x2d4b0c\x2d9581\x2d7066156eafde.device. Stopping, too.
[   15.406275] systemd[1]: usr.mount: Trying to enqueue job usr.mount/stop/fail
[   15.408364] systemd[1]: usr.mount: Installed new job usr.mount/stop as 1
[   15.410485] systemd[1]: usr.mount: Enqueued job usr.mount/stop as 1
[   15.412602] systemd[1]: -.slice changed dead -> active
[   15.414686] systemd[1]: init.scope changed dead -> running
[   15.416770] systemd[1]: Activating default unit: default.target
[   15.421792] systemd[1]: var-lib-ureadahead.mount: Failed to load configuration: No such file or directory
[   15.424259] systemd[1]: graphical.target: Trying to enqueue job graphical.target/start/isolate
[   15.427039] systemd[1]: plymouth-quit.service: Looking at job plymouth-quit.service/stop conflicted_by=yes
[   15.429143] systemd[1]: plymouth-quit.service: Looking at job plymouth-quit.service/start conflicted_by=no
[   15.431183] systemd[1]: plymouth-quit.service: Fixing conflicting jobs plymouth-quit.service/stop,plymouth-quit.service/start by deleting job plymouth-quit.service/start
[   15.433289] systemd[1]: lightdm.service: Looking at job lightdm.service/start conflicted_by=no
[   15.435381] systemd[1]: lightdm.service: Looking at job lightdm.service/stop conflicted_by=no
[   15.437443] systemd[1]: lightdm.service: Fixing conflicting jobs lightdm.service/start,lightdm.service/stop by deleting job lightdm.service/stop
[   15.439656] systemd[1]: systemd-ask-password-wall.path: Installed new job systemd-ask-password-wall.path/start as 151
[   15.441691] systemd[1]: dev-disk-by\x2duuid-0708bffe\x2dc8fb\x2d483f\x2daa21\x2d522f49bfa760.device: Installed new job dev-disk-by\x2duuid-0708bffe\x2dc8fb\x2d483f\x2daa21\x2d522f49bfa760.device/start as 91
[   15.446002] systemd[1]: alsa-restore.service: Installed new job alsa-restore.service/start as 120
[   15.448233] systemd[1]: dev-mapper-cryptswap1.swap: Installed new job dev-mapper-cryptswap1.swap/start as 84
[   15.450495] systemd[1]: systemd-udevd-kernel.socket: Installed new job systemd-udevd-kernel.socket/start as 35
[   15.452811] systemd[1]: whoopsie.service: Installed new job whoopsie.service/start as 150
[   15.455149] systemd[1]: dev-mapper-cryptswap2.swap: Installed new job dev-mapper-cryptswap2.swap/start as 75
[   15.457441] systemd[1]: accounts-daemon.service: Installed new job accounts-daemon.service/start as 177
[   15.459772] systemd[1]: multi-user.target: Installed new job multi-user.target/start as 5
[   15.462122] systemd[1]: sys-kernel-debug.mount: Installed new job sys-kernel-debug.mount/start as 96
[   15.464483] systemd[1]: sys-kernel-config.mount: Installed new job sys-kernel-config.mount/start as 57
[   15.466821] systemd[1]: systemd-cryptsetup@cryptswap2.service: Installed new job systemd-cryptsetup@cryptswap2.service/start as 77
[   15.469208] systemd[1]: systemd-sysctl.service: Installed new job systemd-sysctl.service/start as 56
[   15.471561] systemd[1]: systemd-cryptsetup@cryptswap4.service: Installed new job systemd-cryptsetup@cryptswap4.service/start as 82
[   15.473904] systemd[1]: systemd-tmpfiles-clean.timer: Installed new job systemd-tmpfiles-clean.timer/start as 107
[   15.476278] systemd[1]: pppd-dns.service: Installed new job pppd-dns.service/start as 153
[   15.478654] systemd[1]: console-setup.service: Installed new job console-setup.service/start as 160
[   15.481055] systemd[1]: getty@tty1.service: Installed new job getty@tty1.service/start as 146
[   15.483435] systemd[1]: dev-disk-by\x2duuid-0728bba8\x2d6a01\x2d459a\x2dbf5d\x2dd124e51232cb.device: Installed new job dev-disk-by\x2duuid-0728bba8\x2d6a01\x2d459a\x2dbf5d\x2dd124e51232cb.device/start as 87
[   15.488336] systemd[1]: cups.service: Installed new job cups.service/start as 162
[   15.490703] systemd[1]: systemd-ask-password-plymouth.path: Installed new job systemd-ask-password-plymouth.path/start as 98
[   15.493135] systemd[1]: systemd-tmpfiles-setup-dev.service: Installed new job systemd-tmpfiles-setup-dev.service/start as 30
[   15.495581] systemd[1]: network-online.target: Installed new job network-online.target/start as 164
[   15.498067] systemd[1]: brltty.service: Installed new job brltty.service/start as 69
[   15.500561] systemd[1]: thermald.service: Installed new job thermald.service/start as 168
[   15.503064] systemd[1]: systemd-cryptsetup@cryptswap1.service: Installed new job systemd-cryptsetup@cryptswap1.service/start as 86
[   15.505628] systemd[1]: systemd-tmpfiles-setup.service: Installed new job systemd-tmpfiles-setup.service/start as 70
[   15.508099] systemd[1]: boot.mount: Installed new job boot.mount/start as 46
[   15.510620] systemd[1]: systemd-timesyncd.service: Installed new job systemd-timesyncd.service/start as 19
[   15.513177] systemd[1]: acpid.path: Installed new job acpid.path/start as 118
[   15.515716] systemd[1]: var.mount: Installed new job var.mount/start as 20
[   15.518252] systemd[1]: getty-static.service: Installed new job getty-static.service/start as 148
[   15.520768] systemd[1]: dev-mapper-cryptswap5.device: Installed new job dev-mapper-cryptswap5.device/start as 93
[   15.523235] systemd[1]: systemd-udev-trigger.service: Installed new job systemd-udev-trigger.service/start as 33
[   15.525696] systemd[1]: systemd-fsck@dev-disk-by\x2duuid-75a16d97\x2d3671\x2d4adb\x2db23e\x2da4c282d40fb5.service: Installed new job systemd-fsck@dev-disk-by\x2duuid-75a16d97\x2d3671\x2d4adb\x2db23e\x2da4c282d40fb5.service/start as 27
[   15.530885] systemd[1]: apport.service: Installed new job apport.service/start as 122
[   15.533545] systemd[1]: systemd-machine-id-commit.service: Installed new job systemd-machine-id-commit.service/start as 67
[   15.536257] systemd[1]: srv.mount: Installed new job srv.mount/start as 41
[   15.538920] systemd[1]: kmod-static-nodes.service: Installed new job kmod-static-nodes.service/start as 73
[   15.541513] systemd[1]: dev-mapper-cryptswap4.device: Installed new job dev-mapper-cryptswap4.device/start as 81
[   15.544205] systemd[1]: dev-disk-by\x2duuid-75a16d97\x2d3671\x2d4adb\x2db23e\x2da4c282d40fb5.device: Installed new job dev-disk-by\x2duuid-75a16d97\x2d3671\x2d4adb\x2db23e\x2da4c282d40fb5.device/start as 28
[   15.549752] systemd[1]: paths.target: Installed new job paths.target/start as 117
[   15.552590] systemd[1]: systemd-cryptsetup@cryptswap3.service: Installed new job systemd-cryptsetup@cryptswap3.service/start as 90
[   15.555464] systemd[1]: apt-daily.timer: Installed new job apt-daily.timer/start as 106
[   15.558265] systemd[1]: dev-mapper-cryptswap3.device: Installed new job dev-mapper-cryptswap3.device/start as 89
[   15.561159] systemd[1]: systemd-hwdb-update.service: Installed new job systemd-hwdb-update.service/start as 71
[   15.564056] systemd[1]: dev-mqueue.mount: Installed new job dev-mqueue.mount/start as 66
[   15.566957] systemd[1]: dev-mapper-cryptswap4.swap: Installed new job dev-mapper-cryptswap4.swap/start as 80
[   15.569869] systemd[1]: systemd-journald-dev-log.socket: Installed new job systemd-journald-dev-log.socket/start as 63
[   15.572749] systemd[1]: irqbalance.service: Installed new job irqbalance.service/start as 129
[   15.575570] systemd[1]: ondemand.service: Installed new job ondemand.service/start as 155
[   15.578468] systemd[1]: systemd-journald-audit.socket: Installed new job systemd-journald-audit.socket/start as 62
[   15.581361] systemd[1]: sysinit.target: Installed new job sysinit.target/start as 7
[   15.584192] systemd[1]: uuidd.socket: Installed new job uuidd.socket/start as 115
[   15.586956] systemd[1]: dev-mapper-cryptswap1.device: Installed new job dev-mapper-cryptswap1.device/start as 85
[   15.589723] systemd[1]: remote-fs.target: Installed new job remote-fs.target/start as 157
[   15.592435] systemd[1]: acpid.socket: Installed new job acpid.socket/start as 116
[   15.595186] systemd[1]: rc-local.service: Installed new job rc-local.service/start as 125
[   15.597929] systemd[1]: network.target: Installed new job network.target/start as 134
[   15.600666] systemd[1]: apport-forward.socket: Installed new job apport-forward.socket/start as 114
[   15.603404] systemd[1]: resolvconf.service: Installed new job resolvconf.service/start as 64
[   15.606148] systemd[1]: systemd-fsck@dev-disk-by\x2duuid-01c37fd7\x2d5f37\x2d47f5\x2dad5b\x2d5f6429042682.service: Installed new job systemd-fsck@dev-disk-by\x2duuid-01c37fd7\x2d5f37\x2d47f5\x2dad5b\x2d5f6429042682.service/start as 47
[   15.606153] systemd[1]: friendly-recovery.service: Installed new job friendly-recovery.service/start as 68
[   15.606159] systemd[1]: dev-disk-by\x2duuid-c81619ed\x2d43dc\x2d4ed2\x2d912a\x2da331569c8e82.device: Installed new job dev-disk-by\x2duuid-c81619ed\x2d43dc\x2d4ed2\x2d912a\x2da331569c8e82.device/start as 51
[   15.606165] systemd[1]: sockets.target: Installed new job sockets.target/start as 109
[   15.606169] systemd[1]: rsyslog.service: Installed new job rsyslog.service/start as 143
[   15.606174] systemd[1]: nss-user-lookup.target: Installed new job nss-user-lookup.target/start as 178
[   15.606179] systemd[1]: ureadahead-stop.timer: Installed new job ureadahead-stop.timer/start as 180
[   15.606184] systemd[1]: systemd-initctl.socket: Installed new job systemd-initctl.socket/start as 110
[   15.606188] systemd[1]: cron.service: Installed new job cron.service/start as 132
[   15.606193] systemd[1]: opt.mount: Installed new job opt.mount/start as 38
[   15.606199] systemd[1]: usr.mount: Job usr.mount/stop finished, result=canceled
[   15.606206] systemd[1]: usr.mount: Installed new job usr.mount/start as 44
[   15.606210] systemd[1]: avahi-daemon.socket: Installed new job avahi-daemon.socket/start as 112
[   15.606215] systemd[1]: systemd-remount-fs.service: Installed new job systemd-remount-fs.service/start as 52
[   15.606220] systemd[1]: dbus.service: Installed new job dbus.service/start as 126
[   15.606226] systemd[1]: dev-disk-by\x2duuid-deecc37e\x2d5c73\x2d4d39\x2d964d\x2dbdc1f8bae554.device: Installed new job dev-disk-by\x2duuid-deecc37e\x2d5c73\x2d4d39\x2d964d\x2dbdc1f8bae554.device/start as 95
[   15.606231] systemd[1]: cups-browsed.service: Installed new job cups-browsed.service/start as 161
[   15.606236] systemd[1]: getty.target: Installed new job getty.target/start as 145
[   15.606241] systemd[1]: systemd-fsck-root.service: Installed new job systemd-fsck-root.service/start as 54
[   15.606246] systemd[1]: dev-mapper-cryptswap3.swap: Installed new job dev-mapper-cryptswap3.swap/start as 88
[   15.606251] systemd[1]: system-systemd\x2dfsck.slice: Installed new job system-systemd\x2dfsck.slice/start as 22
[   15.606256] systemd[1]: apparmor.service: Installed new job apparmor.service/start as 8
[   15.606261] systemd[1]: dev-disk-by\x2duuid-ed87e847\x2d54db\x2d4191\x2d8466\x2dc160276cb192.device: Installed new job dev-disk-by\x2duuid-ed87e847\x2d54db\x2d4191\x2d8466\x2dc160276cb192.device/start as 40
[   15.606266] systemd[1]: dev-mapper-cryptswap2.device: Installed new job dev-mapper-cryptswap2.device/start as 76
[   15.606271] systemd[1]: alsa-state.service: Installed new job alsa-state.service/start as 119
[   15.606276] systemd[1]: dev-disk-by\x2duuid-6721b1f0\x2d012a\x2d4f7b\x2d9c14\x2d2613560d0cc7.device: Installed new job dev-disk-by\x2duuid-6721b1f0\x2d012a\x2d4f7b\x2d9c14\x2d2613560d0cc7.device/start as 79
[   15.606282] systemd[1]: smartd.service: Installed new job smartd.service/start as 137
[   15.606287] systemd[1]: dev-disk-by\x2duuid-d6854cca\x2d5c25\x2d4b3c\x2d86d0\x2d261384b3361e.device: Installed new job dev-disk-by\x2duuid-d6854cca\x2d5c25\x2d4b3c\x2d86d0\x2d261384b3361e.device/start as 83
[   15.606292] systemd[1]: systemd-fsckd.socket: Installed new job systemd-fsckd.socket/start as 24
[   15.606297] systemd[1]: ModemManager.service: Installed new job ModemManager.service/start as 167
[   15.606302] systemd[1]: systemd-journal-flush.service: Installed new job systemd-journal-flush.service/start as 59
[   15.606307] systemd[1]: sensord.service: Installed new job sensord.service/start as 131
[   15.606312] systemd[1]: system-systemd\x2dcryptsetup.slice: Installed new job system-systemd\x2dcryptsetup.slice/start as 78
[   15.606317] systemd[1]: speech-dispatcher.service: Installed new job speech-dispatcher.service/start as 152
[   15.606322] systemd[1]: cryptsetup.target: Installed new job cryptsetup.target/start as 99
[   15.606327] systemd[1]: systemd-update-utmp.service: Installed new job systemd-update-utmp.service/start as 128
[   15.606333] systemd[1]: systemd-fsck@dev-disk-by\x2duuid-ed87e847\x2d54db\x2d4191\x2d8466\x2dc160276cb192.service: Installed new job systemd-fsck@dev-disk-by\x2duuid-ed87e847\x2d54db\x2d4191\x2d8466\x2dc160276cb192.service/start as 39
[   15.606337] systemd[1]: timers.target: Installed new job timers.target/start as 105
[   15.606342] systemd[1]: avahi-daemon.service: Installed new job avahi-daemon.service/start as 141
[   15.606347] systemd[1]: ld10k1.service: Installed new job ld10k1.service/start as 149
[   15.606351] systemd[1]: plymouth-read-write.service: Installed new job plymouth-read-write.service/start as 31
[   15.606357] systemd[1]: dev-disk-by\x2duuid-01c37fd7\x2d5f37\x2d47f5\x2dad5b\x2d5f6429042682.device: Installed new job dev-disk-by\x2duuid-01c37fd7\x2d5f37\x2d47f5\x2dad5b\x2d5f6429042682.device/start as 48
[   15.606362] systemd[1]: plymouth-start.service: Installed new job plymouth-start.service/start as 97
[   15.606367] systemd[1]: dev-disk-by\x2duuid-3e23d151\x2df0d0\x2d4b0c\x2d9581\x2d7066156eafde.device: Installed new job dev-disk-by\x2duuid-3e23d151\x2df0d0\x2d4b0c\x2d9581\x2d7066156eafde.device/start as 45
[   15.606372] systemd[1]: lm-sensors.service: Installed new job lm-sensors.service/start as 130
[   15.606377] systemd[1]: local-fs-pre.target: Installed new job local-fs-pre.target/start as 53
[   15.606382] systemd[1]: systemd-logind.service: Installed new job systemd-logind.service/start as 135
[   15.606387] systemd[1]: systemd-user-sessions.service: Installed new job systemd-user-sessions.service/start as 159
[   15.606392] systemd[1]: systemd-fsck@dev-disk-by\x2duuid-70a74a90\x2de612\x2d49c9\x2d95fe\x2df22e4d48db0d.service: Installed new job systemd-fsck@dev-disk-by\x2duuid-70a74a90\x2de612\x2d49c9\x2d95fe\x2df22e4d48db0d.service/start as 21
[   15.606397] systemd[1]: systemd-networkd-resolvconf-update.path: Installed new job systemd-networkd-resolvconf-update.path/start as 65
[   15.606402] systemd[1]: ureadahead.service: Installed new job ureadahead.service/start as 179
[   15.606406] systemd[1]: systemd-modules-load.service: Installed new job systemd-modules-load.service/start as 32
[   15.606411] systemd[1]: systemd-udevd-control.socket: Installed new job systemd-udevd-control.socket/start as 36
[   15.606416] systemd[1]: graphical.target: Installed new job graphical.target/start as 4
[   15.606421] systemd[1]: systemd-journald.service: Installed new job systemd-journald.service/start as 60
[   15.606426] systemd[1]: dev-hugepages.mount: Installed new job dev-hugepages.mount/start as 55
[   15.606431] systemd[1]: NetworkManager.service: Installed new job NetworkManager.service/start as 166
[   15.606436] systemd[1]: systemd-fsck@dev-disk-by\x2duuid-167b6271\x2d5439\x2d4784\x2dbe27\x2d26ce9db7b50e.service: Installed new job systemd-fsck@dev-disk-by\x2duuid-167b6271\x2d5439\x2d4784\x2dbe27\x2d26ce9db7b50e.service/start as 42
[   15.606441] systemd[1]: remote-fs-pre.target: Installed new job remote-fs-pre.target/start as 158
[   15.606446] systemd[1]: slices.target: Installed new job slices.target/start as 108
[   15.606450] systemd[1]: sys-fs-fuse-connections.mount: Installed new job sys-fs-fuse-connections.mount/start as 102
[   15.606455] systemd[1]: local-fs.target: Installed new job local-fs.target/start as 37
[   15.606460] systemd[1]: grub-common.service: Installed new job grub-common.service/start as 123
[   15.606464] systemd[1]: user.slice: Installed new job user.slice/start as 136
[   15.606469] systemd[1]: system-getty.slice: Installed new job system-getty.slice/start as 147
[   15.606474] systemd[1]: NetworkManager-wait-online.service: Installed new job NetworkManager-wait-online.service/start as 165
[   15.606478] systemd[1]: dns-clean.service: Installed new job dns-clean.service/start as 154
[   15.606484] systemd[1]: system.slice: Installed new job system.slice/start as 9
[   15.606488] systemd[1]: systemd-ask-password-console.path: Installed new job systemd-ask-password-console.path/start as 101
[   15.606493] systemd[1]: cups.socket: Installed new job cups.socket/start as 113
[   15.606497] systemd[1]: swap.target: Installed new job swap.target/start as 74
[   15.606502] systemd[1]: anacron.service: Installed new job anacron.service/start as 121
[   15.606507] systemd[1]: gpu-manager.service: Installed new job gpu-manager.service/start as 172
[   15.606512] systemd[1]: plymouth-quit-wait.service: Installed new job plymouth-quit-wait.service/start as 124
[   15.606517] systemd[1]: systemd-random-seed.service: Installed new job systemd-random-seed.service/start as 58
[   15.606522] systemd[1]: dev-disk-by\x2duuid-167b6271\x2d5439\x2d4784\x2dbe27\x2d26ce9db7b50e.device: Installed new job dev-disk-by\x2duuid-167b6271\x2d5439\x2d4784\x2dbe27\x2d26ce9db7b50e.device/start as 43
[   15.606527] systemd[1]: syslog.socket: Installed new job syslog.socket/start as 144
[   15.606532] systemd[1]: systemd-binfmt.service: Installed new job systemd-binfmt.service/start as 13
[   15.606537] systemd[1]: dev-disk-by\x2duuid-70a74a90\x2de612\x2d49c9\x2d95fe\x2df22e4d48db0d.device: Installed new job dev-disk-by\x2duuid-70a74a90\x2de612\x2d49c9\x2d95fe\x2df22e4d48db0d.device/start as 23
[   15.606542] systemd[1]: home.mount: Installed new job home.mount/start as 49
[   15.606546] systemd[1]: systemd-journald.socket: Installed new job systemd-journald.socket/start as 61
[   15.606551] systemd[1]: time-sync.target: Installed new job time-sync.target/start as 29
[   15.606557] systemd[1]: systemd-cryptsetup@cryptswap5.service: Installed new job systemd-cryptsetup@cryptswap5.service/start as 94
[   15.606561] systemd[1]: tmp.mount: Installed new job tmp.mount/start as 26
[   15.606566] systemd[1]: networking.service: Installed new job networking.service/start as 133
[   15.606571] systemd[1]: ufw.service: Installed new job ufw.service/start as 138
[   15.606575] systemd[1]: hddtemp.service: Installed new job hddtemp.service/start as 163
[   15.606580] systemd[1]: dev-mapper-cryptswap5.swap: Installed new job dev-mapper-cryptswap5.swap/start as 92
[   15.606585] systemd[1]: hdparm.service: Installed new job hdparm.service/start as 72
[   15.606589] systemd[1]: dbus.socket: Installed new job dbus.socket/start as 111
[   15.606595] systemd[1]: systemd-fsck@dev-disk-by\x2duuid-c81619ed\x2d43dc\x2d4ed2\x2d912a\x2da331569c8e82.service: Installed new job systemd-fsck@dev-disk-by\x2duuid-c81619ed\x2d43dc\x2d4ed2\x2d912a\x2da331569c8e82.service/start as 50
[   15.606600] systemd[1]: systemd-update-utmp-runlevel.service: Installed new job systemd-update-utmp-runlevel.service/start as 127
[   15.606604] systemd[1]: cups.path: Installed new job cups.path/start as 156
[   15.606608] systemd[1]: basic.target: Installed new job basic.target/start as 6
[   15.606613] systemd[1]: proc-sys-fs-binfmt_misc.automount: Installed new job proc-sys-fs-binfmt_misc.automount/start as 11
[   15.606617] systemd[1]: systemd-udevd.service: Installed new job systemd-udevd.service/start as 34
[   15.606622] systemd[1]: lightdm.service: Installed new job lightdm.service/start as 171
[   15.606626] systemd[1]: graphical.target: Enqueued job graphical.target/start as 4
[   15.606636] systemd[1]: Loaded units and determined initial transaction in 2.9s.
[   15.606678] systemd[1]: var-lib-ureadahead.mount: Collecting.
[   15.606681] systemd[1]: dev-disk-by\x2duuid-7e8f5247\x2dd70e\x2d4084\x2db1cd\x2d6cf9227030ba.mount: Collecting.
[   15.606696] systemd[1]: var-cache.mount: Collecting.
[   15.606698] systemd[1]: var-cache-cups.mount: Collecting.
[   15.606701] systemd[1]: var-cache-cups-org.cups.cupsd.mount: Collecting.
[   15.606717] systemd[1]: dev-disk-by\x2duuid-70a74a90\x2de612\x2d49c9\x2d95fe\x2df22e4d48db0d.mount: Collecting.
[   15.606720] systemd[1]: dev-disk-by\x2duuid-3e23d151\x2df0d0\x2d4b0c\x2d9581\x2d7066156eafde.mount: Collecting.
[   15.606723] systemd[1]: dev-disk-by\x2duuid-75a16d97\x2d3671\x2d4adb\x2db23e\x2da4c282d40fb5.mount: Collecting.
[   15.606726] systemd[1]: dev-disk-by\x2duuid-167b6271\x2d5439\x2d4784\x2dbe27\x2d26ce9db7b50e.mount: Collecting.
[   15.606728] systemd[1]: dev-disk-by\x2duuid-ed87e847\x2d54db\x2d4191\x2d8466\x2dc160276cb192.mount: Collecting.
[   15.606731] systemd[1]: dev-disk-by\x2duuid-c81619ed\x2d43dc\x2d4ed2\x2d912a\x2da331569c8e82.mount: Collecting.
[   15.606734] systemd[1]: run-systemd-fsck.progress.mount: Collecting.
[   15.606736] systemd[1]: dev-disk.mount: Collecting.
[   15.606738] systemd[1]: dev-disk-by\x2duuid.mount: Collecting.
[   15.606741] systemd[1]: dev-disk-by\x2duuid-01c37fd7\x2d5f37\x2d47f5\x2dad5b\x2d5f6429042682.mount: Collecting.
[   15.606743] systemd[1]: run-uuidd.mount: Collecting.
[   15.606745] systemd[1]: run-uuidd-request.mount: Collecting.
[   15.606747] systemd[1]: var-run-avahi\x2ddaemon.mount: Collecting.
[   15.606750] systemd[1]: var-run-avahi\x2ddaemon-socket.mount: Collecting.
[   15.606752] systemd[1]: var-run-cups.mount: Collecting.
[   15.606754] systemd[1]: var-run-cups-cups.sock.mount: Collecting.
[   15.606756] systemd[1]: run-apport.socket.mount: Collecting.
[   15.606758] systemd[1]: run-systemd-initctl.mount: Collecting.
[   15.606760] systemd[1]: run-systemd-initctl-fifo.mount: Collecting.
[   15.606764] systemd[1]: run-systemd-journal-dev\x2dlog.mount: Collecting.
[   15.606766] systemd[1]: run-systemd-journal-syslog.mount: Collecting.
[   15.606769] systemd[1]: dev-mapper-cryptswap5.mount: Collecting.
[   15.606771] systemd[1]: dev-mapper-cryptswap4.mount: Collecting.
[   15.606773] systemd[1]: dev-mapper-cryptswap3.mount: Collecting.
[   15.606776] systemd[1]: dev-mapper-cryptswap2.mount: Collecting.
[   15.606778] systemd[1]: dev-mapper.mount: Collecting.
[   15.606780] systemd[1]: dev-mapper-cryptswap1.mount: Collecting.
[   15.606783] systemd[1]: var-lib-systemd-clock.mount: Collecting.
[   15.606786] systemd[1]: root.mount: Collecting.
[   15.606788] systemd[1]: var-run.mount: Collecting.
[   15.606790] systemd[1]: var-run-dbus.mount: Collecting.
[   15.606793] systemd[1]: var-run-dbus-system_bus_socket.mount: Collecting.
[   15.606797] systemd[1]: run-systemd-netif.mount: Collecting.
[   15.606799] systemd[1]: run-systemd-netif-state.mount: Collecting.
[   15.606802] systemd[1]: var-lib-brltty.mount: Collecting.
[   15.606805] systemd[1]: var-log-journal.mount: Collecting.
[   15.606807] systemd[1]: sys-kernel.mount: Collecting.
[   15.606811] systemd[1]: proc.mount: Collecting.
[   15.606813] systemd[1]: proc-sys.mount: Collecting.
[   15.606816] systemd[1]: proc-sys-fs.mount: Collecting.
[   15.606823] systemd[1]: sys.mount: Collecting.
[   15.606825] systemd[1]: sys-fs.mount: Collecting.
[   15.606828] systemd[1]: sys-fs-fuse.mount: Collecting.
[   15.606830] systemd[1]: dev.mount: Collecting.
[   15.606832] systemd[1]: var-log.mount: Collecting.
[   15.606835] systemd[1]: var-log-wtmp.mount: Collecting.
[   15.606838] systemd[1]: var-lib-systemd-random\x2dseed.mount: Collecting.
[   15.606840] systemd[1]: var-lib.mount: Collecting.
[   15.606842] systemd[1]: var-lib-systemd.mount: Collecting.
[   15.606844] systemd[1]: var-lib-systemd-timers.mount: Collecting.
[   15.606848] systemd[1]: run-acpid.socket.mount: Collecting.
[   15.606850] systemd[1]: etc.mount: Collecting.
[   15.606852] systemd[1]: etc-acpi.mount: Collecting.
[   15.606854] systemd[1]: etc-acpi-events.mount: Collecting.
[   15.606856] systemd[1]: var-tmp.mount: Collecting.
[   15.606859] systemd[1]: run-systemd-ask\x2dpassword.mount: Collecting.
[   15.606862] systemd[1]: run-udev.mount: Collecting.
[   15.606865] systemd[1]: run-udev-control.mount: Collecting.
[   15.606874] systemd[1]: run-systemd-journal-socket.mount: Collecting.
[   15.606876] systemd[1]: run.mount: Collecting.
[   15.606878] systemd[1]: run-systemd.mount: Collecting.
[   15.606880] systemd[1]: run-systemd-journal.mount: Collecting.
[   15.606882] systemd[1]: run-systemd-journal-stdout.mount: Collecting.
[   15.607180] systemd[1]: Received SIGCHLD from PID 285 (n/a).
[   15.607213] systemd[1]: proc-sys-fs-binfmt_misc.automount: ConditionPathIsReadWrite=/proc/sys/ succeeded.
[   15.607227] systemd[1]: proc-sys-fs-binfmt_misc.automount: ConditionPathExists=/proc/sys/fs/binfmt_misc/ succeeded.
[   15.607403] systemd[1]: Autofs kernel version 1.0
[   15.607483] systemd[1]: Autofs protocol version 5.2
[   15.607493] systemd[1]: proc-sys-fs-binfmt_misc.automount: Changed dead -> waiting
[   15.607502] systemd[1]: proc-sys-fs-binfmt_misc.automount: Job proc-sys-fs-binfmt_misc.automount/start finished, result=done
[   15.607514] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   16.073247] systemd[1]: systemd-journald.socket: Changed dead -> listening
[   16.074391] systemd[1]: systemd-journald.socket: Job systemd-journald.socket/start finished, result=done
[   16.075616] systemd[1]: Listening on Journal Socket.
[   16.078194] systemd[1]: syslog.socket: Changed dead -> listening
[   16.079443] systemd[1]: syslog.socket: Job syslog.socket/start finished, result=done
[   16.080739] systemd[1]: Listening on Syslog Socket.
[   16.083582] systemd[1]: system.slice changed dead -> active
[   16.084929] systemd[1]: system.slice: Job system.slice/start finished, result=done
[   16.086277] systemd[1]: Created slice System Slice.
[   16.089336] systemd[1]: ufw.service: About to execute: /lib/ufw/ufw-init start quiet
[   16.090939] systemd[1]: ufw.service: Forked /lib/ufw/ufw-init as 297
[   16.104244] systemd[1]: ufw.service: Changed dead -> start
[   16.105692] systemd[1]: Starting Uncomplicated firewall...
[   16.108603] systemd[1]: systemd-binfmt.service: ConditionDirectoryNotEmpty=|/run/binfmt.d failed.
[   16.148821] systemd[1]: systemd-binfmt.service: ConditionDirectoryNotEmpty=|/etc/binfmt.d failed.
[   16.150327] systemd[1]: systemd-binfmt.service: ConditionDirectoryNotEmpty=|/usr/local/lib/binfmt.d failed.
[   16.151903] systemd[1]: systemd-binfmt.service: ConditionDirectoryNotEmpty=|/usr/lib/binfmt.d failed.
[   16.153368] systemd[1]: systemd-binfmt.service: ConditionDirectoryNotEmpty=|/lib/binfmt.d failed.
[   16.154822] systemd[1]: systemd-binfmt.service: ConditionPathIsReadWrite=/proc/sys/ succeeded.
[   16.156282] systemd[1]: systemd-binfmt.service: Starting requested but condition failed. Not starting unit.
[   16.157676] systemd[1]: systemd-binfmt.service: Job systemd-binfmt.service/start finished, result=done
[   16.159401] systemd[1]: system-getty.slice changed dead -> active
[   16.160926] systemd[1]: system-getty.slice: Job system-getty.slice/start finished, result=done
[   16.162444] systemd[1]: Created slice system-getty.slice.
[   16.165746] systemd[1]: user.slice changed dead -> active
[   16.167302] systemd[1]: user.slice: Job user.slice/start finished, result=done
[   16.168880] systemd[1]: Created slice User and Session Slice.
[   16.172190] systemd[1]: slices.target changed dead -> active
[   16.173740] systemd[1]: slices.target: Job slices.target/start finished, result=done
[   16.175315] systemd[1]: Reached target Slices.
[   16.178640] systemd[1]: remote-fs-pre.target changed dead -> active
[   16.180299] systemd[1]: remote-fs-pre.target: Job remote-fs-pre.target/start finished, result=done
[   16.181969] systemd[1]: Reached target Remote File Systems (Pre).
[   16.185474] systemd[1]: dev-hugepages.mount: ConditionCapability=CAP_SYS_ADMIN succeeded.
[   16.187207] systemd[1]: dev-hugepages.mount: ConditionPathExists=/sys/kernel/mm/hugepages succeeded.
[   16.188961] systemd[1]: dev-hugepages.mount: Failed to check symlink /dev/hugepages, ignoring: No such file or directory
[   16.191001] systemd[1]: dev-hugepages.mount: About to execute: /bin/mount hugetlbfs /dev/hugepages -t hugetlbfs
[   16.193092] systemd[1]: dev-hugepages.mount: Forked /bin/mount as 299
[   16.204342] systemd[1]: dev-hugepages.mount: Changed dead -> mounting
[   16.206314] systemd[1]: Mounting Huge Pages File System...
[   16.209936] systemd[1]: systemd-udevd-control.socket: ConditionPathIsReadWrite=/sys succeeded.
[   16.211791] systemd[1]: systemd-udevd-control.socket: Changed dead -> listening
[   16.213589] systemd[1]: systemd-udevd-control.socket: Job systemd-udevd-control.socket/start finished, result=done
[   16.215860] systemd[1]: Listening on udev Control Socket.
[   16.219879] systemd[1]: systemd-modules-load.service: ConditionKernelCommandLine=|rd.modules-load failed.
[   16.221711] systemd[1]: systemd-modules-load.service: ConditionKernelCommandLine=|modules-load failed.
[   16.223438] systemd[1]: systemd-modules-load.service: ConditionDirectoryNotEmpty=|/run/modules-load.d failed.
[   16.243791] systemd[1]: systemd-modules-load.service: ConditionDirectoryNotEmpty=|/etc/modules-load.d succeeded.
[   16.245577] systemd[1]: systemd-modules-load.service: ConditionDirectoryNotEmpty=|/usr/local/lib/modules-load.d failed.
[   16.247465] systemd[1]: systemd-modules-load.service: ConditionDirectoryNotEmpty=|/usr/lib/modules-load.d failed.
[   16.249193] systemd[1]: systemd-modules-load.service: ConditionDirectoryNotEmpty=|/lib/modules-load.d failed.
[   16.250950] systemd[1]: systemd-modules-load.service: ConditionCapability=CAP_SYS_MODULE succeeded.
[   16.253017] systemd[1]: systemd-modules-load.service: About to execute: /lib/systemd/systemd-modules-load
[   16.255468] systemd[1]: systemd-modules-load.service: Forked /lib/systemd/systemd-modules-load as 302
[   16.268280] systemd[1]: systemd-modules-load.service: Changed dead -> start
[   16.270076] systemd[1]: Starting Load Kernel Modules...
[   16.273827] systemd[1]: system-systemd\x2dcryptsetup.slice changed dead -> active
[   16.275487] systemd[1]: system-systemd\x2dcryptsetup.slice: Job system-systemd\x2dcryptsetup.slice/start finished, result=done
[   16.277208] systemd[1]: Created slice system-systemd\x2dcryptsetup.slice.
[   16.280858] systemd[1]: systemd-fsckd.socket: Changed dead -> listening
[   16.282596] systemd[1]: systemd-fsckd.socket: Job systemd-fsckd.socket/start finished, result=done
[   16.284342] systemd[1]: Listening on fsck to fsckd communication Socket.
[   16.288170] systemd[1]: system-systemd\x2dfsck.slice changed dead -> active
[   16.289949] systemd[1]: system-systemd\x2dfsck.slice: Job system-systemd\x2dfsck.slice/start finished, result=done
[   16.291709] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[   16.295524] systemd[1]: systemd-initctl.socket: Changed dead -> listening
[   16.297387] systemd[1]: systemd-initctl.socket: Job systemd-initctl.socket/start finished, result=done
[   16.299230] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   16.303001] systemd[1]: nss-user-lookup.target changed dead -> active
[   16.304860] systemd[1]: nss-user-lookup.target: Job nss-user-lookup.target/start finished, result=done
[   16.306695] systemd[1]: Reached target User and Group Name Lookups.
[   16.310451] systemd[1]: remote-fs.target changed dead -> active
[   16.312325] systemd[1]: remote-fs.target: Job remote-fs.target/start finished, result=done
[   16.314196] systemd[1]: Reached target Remote File Systems.
[   16.318067] systemd[1]: systemd-journald-audit.socket: ConditionCapability=CAP_AUDIT_READ succeeded.
[   16.319995] systemd[1]: systemd-journald-audit.socket: ConditionSecurity=audit succeeded.
[   16.321929] systemd[1]: systemd-journald-audit.socket: Changed dead -> listening
[   16.323768] systemd[1]: systemd-journald-audit.socket: Job systemd-journald-audit.socket/start finished, result=done
[   16.325635] systemd[1]: Listening on Journal Audit Socket.
[   16.329467] systemd[1]: systemd-journald-dev-log.socket: Changed dead -> listening
[   16.331364] systemd[1]: systemd-journald-dev-log.socket: Job systemd-journald-dev-log.socket/start finished, result=done
[   16.333282] systemd[1]: Listening on Journal Socket (/dev/log).
[   16.337438] systemd[1]: systemd-journald.service: About to execute: /lib/systemd/systemd-journald
[   16.339639] systemd[1]: systemd-journald.service: Forked /lib/systemd/systemd-journald as 306
[   16.348281] systemd[1]: systemd-journald.service: Changed dead -> start
[   16.350239] systemd[1]: Starting Journal Service...
[   16.354215] systemd[1]: dev-mqueue.mount: ConditionCapability=CAP_SYS_ADMIN succeeded.
[   16.356163] systemd[1]: dev-mqueue.mount: ConditionPathExists=/proc/sys/fs/mqueue succeeded.
[   16.357989] systemd[1]: dev-mqueue.mount: Failed to check symlink /dev/mqueue, ignoring: No such file or directory
[   16.360310] systemd[1]: dev-mqueue.mount: About to execute: /bin/mount mqueue /dev/mqueue -t mqueue
[   16.362542] systemd[1]: dev-mqueue.mount: Forked /bin/mount as 308
[   16.364544] systemd[1]: dev-mqueue.mount: Changed dead -> mounting
[   16.366427] systemd[1]: Mounting POSIX Message Queue File System...
[   16.370422] systemd[1]: kmod-static-nodes.service: ConditionFileNotEmpty=/lib/modules/4.4.0-18-generic/modules.devname succeeded.
[   16.372486] systemd[1]: kmod-static-nodes.service: ConditionCapability=CAP_SYS_MODULE succeeded.
[   16.374747] systemd[1]: kmod-static-nodes.service: About to execute: /bin/kmod static-nodes --format=tmpfiles --output=/run/tmpfiles.d/kmod.conf
[   16.377051] systemd[1]: kmod-static-nodes.service: Forked /bin/kmod as 311
[   16.379368] systemd[1]: kmod-static-nodes.service: Changed dead -> start
[   16.381425] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   16.385808] systemd[1]: sys-kernel-debug.mount: ConditionCapability=CAP_SYS_RAWIO succeeded.
[   16.387888] systemd[1]: sys-kernel-debug.mount: ConditionPathExists=/sys/kernel/debug succeeded.
[   16.390330] systemd[1]: sys-kernel-debug.mount: About to execute: /bin/mount debugfs /sys/kernel/debug -t debugfs
[   16.392639] systemd[1]: sys-kernel-debug.mount: Forked /bin/mount as 313
[   16.394756] systemd[1]: sys-kernel-debug.mount: Changed dead -> mounting
[   16.396772] systemd[1]: Mounting Debug File System...
[   16.400868] systemd[1]: systemd-udevd-kernel.socket: ConditionPathIsReadWrite=/sys succeeded.
[   16.402921] systemd[1]: systemd-udevd-kernel.socket: Changed dead -> listening
[   16.405003] systemd[1]: systemd-udevd-kernel.socket: Job systemd-udevd-kernel.socket/start finished, result=done
[   16.407031] systemd[1]: Listening on udev Kernel Socket.
[   16.411143] systemd[1]: systemd-ask-password-wall.path: Changed dead -> waiting
[   16.413146] systemd[1]: systemd-ask-password-wall.path: Job systemd-ask-password-wall.path/start finished, result=done
[   16.415128] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   16.420543] systemd[1]: libmount event [rescan: yes]
[   16.423509] systemd[1]: dev-hugepages.mount: Changed mounting -> mounting-done
[   16.425494] systemd[1]: dev-hugepages.mount: Job dev-hugepages.mount/start finished, result=done
[   16.427469] systemd[1]: Mounted Huge Pages File System.
[   16.431581] systemd[1]: dev-mqueue.mount: Changed mounting -> mounting-done
[   16.433575] systemd[1]: dev-mqueue.mount: Job dev-mqueue.mount/start finished, result=done
[   16.435550] systemd[1]: Mounted POSIX Message Queue File System.
[   16.439564] systemd[1]: sys-kernel-debug.mount: Changed mounting -> mounting-done
[   16.441465] systemd[1]: sys-kernel-debug.mount: Job sys-kernel-debug.mount/start finished, result=done
[   16.443472] systemd[1]: Mounted Debug File System.
[   16.447599] systemd[1]: Received SIGCHLD from PID 297 (ufw-init).
[   16.449606] systemd[1]: Child 297 (ufw-init) died (code=exited, status=0/SUCCESS)
[   16.451602] systemd[1]: ufw.service: Child 297 belongs to ufw.service
[   16.453589] systemd[1]: ufw.service: Main process exited, code=exited, status=0/SUCCESS
[   16.455723] systemd[1]: ufw.service: Changed start -> exited
[   16.457598] systemd[1]: ufw.service: Job ufw.service/start finished, result=done
[   16.459513] systemd[1]: Started Uncomplicated firewall.
[   16.463680] systemd[1]: ufw.service: cgroup is empty
[   16.465732] systemd[1]: Child 299 (mount) died (code=exited, status=0/SUCCESS)
[   16.467675] systemd[1]: dev-hugepages.mount: Child 299 belongs to dev-hugepages.mount
[   16.469625] systemd[1]: dev-hugepages.mount: Mount process exited, code=exited status=0
[   16.471519] systemd[1]: dev-hugepages.mount: Changed mounting-done -> mounted
[   16.473456] systemd[1]: Child 308 (mount) died (code=exited, status=0/SUCCESS)
[   16.475305] systemd[1]: dev-mqueue.mount: Child 308 belongs to dev-mqueue.mount
[   16.477204] systemd[1]: dev-mqueue.mount: Mount process exited, code=exited status=0
[   16.479085] systemd[1]: dev-mqueue.mount: Changed mounting-done -> mounted
[   16.481046] systemd[1]: Child 313 (mount) died (code=exited, status=0/SUCCESS)
[   16.482952] systemd[1]: sys-kernel-debug.mount: Child 313 belongs to sys-kernel-debug.mount
[   16.484863] systemd[1]: sys-kernel-debug.mount: Mount process exited, code=exited status=0
[   16.486718] systemd[1]: sys-kernel-debug.mount: Changed mounting-done -> mounted
[   16.489980] systemd[1]: Accepted new private connection.
[   16.491763] systemd[1]: systemd-journald.socket: Incoming traffic
[   16.493581] systemd[1]: systemd-journald.socket: Changed listening -> running
[   16.496780] systemd[1]: Accepted new private connection.
[   16.500299] systemd[1]: Accepted new private connection.
[   16.503435] systemd[1]: Accepted new private connection.
[   16.505238] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.510197] systemd[1]: Accepted new private connection.
[   16.512095] systemd[1]: Got disconnect on private connection.
[   16.515769] systemd[1]: Accepted new private connection.
[   16.517642] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.521637] systemd[1]: Got disconnect on private connection.
[   16.524064] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.529576] systemd[1]: Accepted new private connection.
[   16.531698] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.537412] systemd[1]: Accepted new private connection.
[   16.539622] systemd[1]: Got disconnect on private connection.
[   16.542190] systemd[1]: Got disconnect on private connection.
[   16.546098] systemd[1]: Accepted new private connection.
[   16.548267] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.552741] systemd[1]: Got disconnect on private connection.
[   16.555423] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.561333] systemd[1]: Accepted new private connection.
[   16.563699] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.569804] systemd[1]: Accepted new private connection.
[   16.572313] systemd[1]: Got disconnect on private connection.
[   16.575127] systemd[1]: Got disconnect on private connection.
[   16.579356] systemd[1]: Accepted new private connection.
[   16.581757] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.586816] systemd[1]: Got disconnect on private connection.
[   16.589776] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.596237] systemd[1]: Accepted new private connection.
[   16.598904] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.604476] systemd[1]: Got disconnect on private connection.
[   16.607635] systemd[1]: Got disconnect on private connection.
[   16.610867] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.616637] systemd[1]: systemd-udevd-kernel.socket: Incoming traffic
[   16.619463] systemd[1]: systemd-udevd-kernel.socket: Changed listening -> running
[   16.622404] systemd[1]: systemd-udevd-kernel.socket: Failed to send unit change signal for systemd-udevd-kernel.socket: Connection reset by peer
[   16.625249] systemd[1]: Got disconnect on private connection.
[   16.628673] systemd[1]: Got disconnect on private connection.
[   16.632059] systemd[1]: Got disconnect on private connection.
[   16.653104] systemd[1]: Received SIGCHLD from PID 311 (kmod).
[   16.655931] systemd[1]: Child 311 (kmod) died (code=exited, status=0/SUCCESS)
[   16.658716] systemd[1]: kmod-static-nodes.service: Child 311 belongs to kmod-static-nodes.service
[   16.661577] systemd[1]: kmod-static-nodes.service: Main process exited, code=exited, status=0/SUCCESS
[   16.664596] systemd[1]: kmod-static-nodes.service: Changed start -> exited
[   16.667440] systemd[1]: kmod-static-nodes.service: Job kmod-static-nodes.service/start finished, result=done
[   16.670311] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   16.676275] systemd[1]: kmod-static-nodes.service: cgroup is empty
[   16.680539] systemd[1]: Accepted new private connection.
[   16.683488] systemd[1]: systemd-tmpfiles-setup-dev.service: ConditionCapability=CAP_SYS_MODULE succeeded.
[   16.686683] systemd[1]: systemd-tmpfiles-setup-dev.service: About to execute: /bin/systemd-tmpfiles --prefix=/dev --create --boot
[   16.689832] systemd[1]: systemd-tmpfiles-setup-dev.service: Forked /bin/systemd-tmpfiles as 319
[   16.704284] systemd[1]: systemd-tmpfiles-setup-dev.service: Changed dead -> start
[   16.707079] systemd[1]: Starting Create Static Device Nodes in /dev...
[   16.714953] systemd[1]: Accepted new private connection.
[   16.717818] systemd[1]: Got disconnect on private connection.
[   16.721141] systemd[1]: Got message type=signal sender=n/a destination=n/a object=/org/freedesktop/systemd1/agent interface=org.freedesktop.systemd1.Agent member=Released cookie=1 reply_cookie=0 error=n/a
[   16.726640] systemd[1]: Got disconnect on private connection.
[   16.921040] lp: driver loaded but no devices found
[   16.952157] ppdev: user-space parallel port driver
[   17.023298] parport_pc 00:05: reported by Plug and Play ACPI
[   17.025978] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   17.045685] systemd-journald[306]: Fixed min_use=1.0M max_use=34.4M max_size=4.3M min_size=512.0K keep_free=51.6M n_max_files=100
[   17.049098] systemd-journald[306]: Reserving 7843 entries in hash table.
[   17.052212] systemd-journald[306]: Vacuuming...
[   17.054777] systemd-journald[306]: Vacuuming done, freed 0B of archived journals on disk.
[   17.076798] systemd-journald[306]: Flushing /dev/kmsg...
[   17.124159] lp0: using parport0 (interrupt-driven).
[   17.147571] systemd-journald[306]: systemd-journald running as pid 306
[   17.150230] systemd-journald[306]: Sent READY=1 notification.
[   17.150365] systemd[1]: systemd-journald.service: Got notification message from PID 306 (READY=1, STATUS=Processing requests...)
[   17.150383] systemd[1]: systemd-journald.service: Changed start -> running
[   17.150391] systemd[1]: systemd-journald.service: Job systemd-journald.service/start finished, result=done
[   17.150408] systemd[1]: Started Journal Service.
[   17.162076] systemd-journald[306]: Sent WATCHDOG=1 notification.
[   17.166637] systemd[1]: systemd-journald-audit.socket: Changed listening -> running
[   17.265667] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.268236] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.270767] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.273257] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.275530] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.277842] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.279957] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.285257] it87: Found IT8718F chip at 0x228, revision 5
[   17.287156] it87: Beeping is supported
[   17.312832] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.318517] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   17.380891] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   18.370898] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   18.378152] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   18.448424] EXT4-fs (sdb1): re-mounted. Opts: (null)
[   18.502302] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   18.529323] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   18.681550] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   18.763053] systemd-journald[306]: Data hash table of /run/log/journal/a71e895d394f4d5ba219556bb216a175/system.journal has a fill level at 75.0 (5884 of 7843 items, 4517888 file size, 767 bytes per hash table item), suggesting rotation.
[   18.763061] systemd-journald[306]: /run/log/journal/a71e895d394f4d5ba219556bb216a175/system.journal: Journal header limits reached or header out-of-date, rotating.
[   18.763065] systemd-journald[306]: Rotating...
[   18.763856] systemd-journald[306]: Reserving 7843 entries in hash table.
[   18.764145] systemd-journald[306]: Vacuuming...
[   18.764226] systemd-journald[306]: Vacuuming done, freed 0B of archived journals on disk.
[   19.127605] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.545670] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B0F (\SOR1) (20150930/utaddress-254)
[   19.545679] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.456831] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   20.482084] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   20.485928] media: Linux media interface: v0.10
[   20.545225] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:05.1/sound/card1/input5
[   20.686554] Linux video capture interface: v2.00
[   20.720681] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   20.768578] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   20.849348] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   20.865534] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   21.223110] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   21.405904] EDAC MC: Ver: 3.0.0
[   21.600912] MCE: In-kernel MCE decoding enabled.
[   21.656477] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   21.666320] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   21.667063] BTRFS info (device sdd1): disk space caching is enabled
[   21.667070] BTRFS: has skinny extents
[   21.670741] BTRFS info (device sdc1): disk space caching is enabled
[   21.670746] BTRFS: has skinny extents
[   21.821200] uvcvideo: Found UVC 1.00 device Video Camera            (045e:0294)
[   21.847649] AMD64 EDAC driver v3.4.0
[   21.847693] EDAC amd64: DRAM ECC disabled.
[   21.847701] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[   21.848852] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   21.853353] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   21.865889] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   21.879537] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   22.183290] usbcore: registered new interface driver uvcvideo
[   22.183294] USB Video Class driver (1.1.1)
[   22.280573] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   22.286716] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   22.293061] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   22.295688] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   22.827886] systemd-journald[306]: Received request to flush runtime journal from PID 1
[   22.827959] systemd-journald[306]: Vacuuming...
[   22.828090] systemd-journald[306]: Vacuuming done, freed 0B of archived journals on disk.
[   23.060760] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   23.301605] kvm: disabled by bios
[   23.336648] kvm: disabled by bios
[   23.343217] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   23.350800] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   23.443382] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
[   23.828938] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.264849] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.331605] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[   24.375169] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.375312] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.466633] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.472388] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.517586] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.521252] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.624381] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   24.721327] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   24.729409] Adding 7904764k swap on /dev/mapper/cryptswap4.  Priority:-1 extents:1 across:7904764k FS
[   24.738470] Adding 7904764k swap on /dev/mapper/cryptswap3.  Priority:-2 extents:1 across:7904764k FS
[   24.751973] Adding 7904764k swap on /dev/mapper/cryptswap5.  Priority:-3 extents:1 across:7904764k FS
[   24.956446] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.015008] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[   25.064349] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.069409] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.071580] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.078180] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.081280] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.082831] BTRFS error (device sdc1): could not find root 8
[   25.112626] BTRFS error (device sdd1): could not find root 8
[   25.114002] BTRFS error (device sdd1): could not find root 8
[   25.196866] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.291284] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.301934] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.356934] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.357070] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.372968] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.496768] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.854133] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   25.973500] Adding 7905788k swap on /dev/mapper/cryptswap1.  Priority:-4 extents:1 across:7905788k FS
[   26.222446] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   26.242960] Adding 7904764k swap on /dev/mapper/cryptswap2.  Priority:-5 extents:1 across:7904764k FS
[   26.975622] audit: type=1400 audit(1460176640.831:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=856 comm="apparmor_parser"
[   26.975635] audit: type=1400 audit(1460176640.831:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=856 comm="apparmor_parser"
[   26.998616] audit: type=1400 audit(1460176640.855:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=856 comm="apparmor_parser"
[   26.998629] audit: type=1400 audit(1460176640.855:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=856 comm="apparmor_parser"
[   26.998634] audit: type=1400 audit(1460176640.855:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=856 comm="apparmor_parser"
[   26.998639] audit: type=1400 audit(1460176640.855:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=856 comm="apparmor_parser"
[   27.074791] audit: type=1400 audit(1460176640.931:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=856 comm="apparmor_parser"
[   27.074805] audit: type=1400 audit(1460176640.931:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince//sanitized_helper" pid=856 comm="apparmor_parser"
[   27.074810] audit: type=1400 audit(1460176640.931:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=856 comm="apparmor_parser"
[   27.074816] audit: type=1400 audit(1460176640.931:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer//sanitized_helper" pid=856 comm="apparmor_parser"
[   27.421684] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.476586] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.487909] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.491419] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.494982] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.498702] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.502872] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.506195] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.515969] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.525378] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.525720] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.530155] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.537327] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.566882] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.567034] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.572819] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.574641] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.577141] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.583203] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.588256] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.591638] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   27.600459] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.105161] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.109983] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.121414] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.127191] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.294420] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.578683] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.587471] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.627312] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   30.758152] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   31.283839] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   32.344119] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   32.353343] r8169 0000:04:00.0 enp4s0: link down
[   32.353348] r8169 0000:04:00.0 enp4s0: link down
[   32.353392] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   32.444635] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   32.537289] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   33.848928] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   33.861219] usblp 4-1:1.0: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x3402
[   33.861891] usbcore: registered new interface driver usblp
[   34.737728] r8169 0000:04:00.0 enp4s0: link up
[   34.737741] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready
[   36.571349] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   37.324634] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   37.438247] systemd-journald[306]: Data hash table of /run/log/journal/a71e895d394f4d5ba219556bb216a175/system.journal has a fill level at 75.0 (5883 of 7843 items, 4517888 file size, 767 bytes per hash table item), suggesting rotation.
[   37.438254] systemd-journald[306]: /run/log/journal/a71e895d394f4d5ba219556bb216a175/system.journal: Journal header limits reached or header out-of-date, rotating.
[   37.438258] systemd-journald[306]: Rotating...
[   37.439057] systemd-journald[306]: Reserving 7843 entries in hash table.
[   37.439306] systemd-journald[306]: Vacuuming...
[   37.439419] systemd-journald[306]: Vacuuming done, freed 0B of archived journals on disk.
[   38.736521] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   38.736658] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   38.924561] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   38.924634] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   39.240923] usblp0: removed
[   39.254428] usblp 4-1:1.0: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x3402
[   39.604587] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   39.604709] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   40.022260] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   40.025939] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   40.047233] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   40.059459] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   40.067659] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   43.382372] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   45.844386] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   52.025637] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   54.449045] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   54.450009] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   54.727536] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   54.727609] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   54.751306] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   54.751382] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   54.763493] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   54.763566] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   55.755511] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   56.047292] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   56.047363] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   56.306883] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   56.306962] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   56.664357] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   56.665915] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   56.881002] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   57.800317] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   57.800392] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   57.956669] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   57.956745] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.005577] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.255620] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.255694] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.310065] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.310843] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.392641] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.392714] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.409152] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   58.409964] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   61.405447] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   61.405518] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   62.789823] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   62.789896] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   77.497831] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   77.497899] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   77.878908] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   77.878979] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[   85.532878] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[  151.521058] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  158.077237] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[  211.521078] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  321.521037] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  380.609228] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  380.680553] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[  380.752239] JFS: nTxBlock = 8192, nTxLock = 65536
[  380.873711] ntfs: driver 2.1.32 [Flags: R/O MODULE].
[  380.879266] systemd-journald[306]: Data hash table of /run/log/journal/a71e895d394f4d5ba219556bb216a175/system.journal has a fill level at 75.0 (5884 of 7843 items, 4517888 file size, 767 bytes per hash table item), suggesting rotation.
[  380.879274] systemd-journald[306]: /run/log/journal/a71e895d394f4d5ba219556bb216a175/system.journal: Journal header limits reached or header out-of-date, rotating.
[  380.879277] systemd-journald[306]: Rotating...
[  380.880434] systemd-journald[306]: Reserving 7843 entries in hash table.
[  380.880730] systemd-journald[306]: Vacuuming...
[  380.880846] systemd-journald[306]: Vacuuming done, freed 0B of archived journals on disk.
[  380.996154] QNX4 filesystem 0.2.3 registered.
[  480.225990] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  571.521044] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  691.521049] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  751.521071] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  823.751281] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[  823.751380] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[  840.621072] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  931.521064] systemd-journald[306]: Sent WATCHDOG=1 notification.
[  931.544696] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[ 1049.271263] systemd-journald[306]: Sent WATCHDOG=1 notification.
[ 1111.521047] systemd-journald[306]: Sent WATCHDOG=1 notification.
[ 1231.521046] systemd-journald[306]: Sent WATCHDOG=1 notification.
[ 1291.521159] systemd-journald[306]: Sent WATCHDOG=1 notification.
[ 1385.019630] systemd-journald[306]: Sent WATCHDOG=1 notification.
[ 1385.019840] systemd-journald[306]: Successfully sent stream file descriptor to service manager.
[ 1385.019900] systemd-journald[306]: Successfully sent stream file descriptor to service manager.

```

---

