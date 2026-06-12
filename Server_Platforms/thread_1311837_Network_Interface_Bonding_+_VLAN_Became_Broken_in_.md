---
title: "Network Interface Bonding + VLAN Became Broken in Ubuntu Server 9.10 (Karmic)"
date: 2009-11-02
forum: Server Platforms
---

### Post by jwindle on 2009-11-02
Problem: Networking does not work until I login locally to the server and restart networking by running /etc/init.d/networking restart. The configuration below works in Ubuntu Server 9.04 (Jaunty).

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto bond0
iface bond0 inet manual
slaves eth0 eth1
bond-mode 4
mond-miimon 100

auto vlan32
iface vlan32 inet dhcp
mtu 1500
vlan_raw_device bond0

```/etc/modprobe.d/bonding.conf
```

alias bond0 bonding

```Packages Installed: ifenslave, vlan

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-server (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 (Ubuntu 2.6.31-14.48-server)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=/dev/mapper/mybcclb1-root ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dffe0000 (usable)
[    0.000000]  BIOS-e820: 00000000dffe0000 - 00000000dffef000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dffef000 - 00000000dfffdc00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfffdc00 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec86000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000220000000 (usable)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x220000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   1 base 000000000 mask E00000000 write-back
[    0.000000]   2 base 200000000 mask FE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdffe0 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000dffe0000 (usable)
[    0.000000]  modified: 00000000dffe0000 - 00000000dffef000 (ACPI data)
[    0.000000]  modified: 00000000dffef000 - 00000000dfffdc00 (ACPI NVS)
[    0.000000]  modified: 00000000dfffdc00 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec86000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000220000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000dffe0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dffe0000 page 4k
[    0.000000] kernel direct mapping tables up to dffe0000 @ 8000-e000
[    0.000000] init_memory_mapping: 0000000100000000-0000000220000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0220000000 page 2M
[    0.000000] kernel direct mapping tables up to 220000000 @ c000-16000
[    0.000000] RAMDISK: 378db000 - 37fef99b
[    0.000000] ACPI: RSDP 00000000000f8500 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000dffe0000 00038 (v01 A M I  7520JR23 09000629 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000dffe0200 00084 (v02 A M I  OEMFACP  09000629 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000dffe04f0 04950 (v01  SJR2A SJR2A092 00000092 INTL 02002026)
[    0.000000] ACPI: FACS 00000000dffef000 00040
[    0.000000] ACPI: APIC 00000000dffe0390 000B0 (v01 A M I  OEMAPIC  09000629 MSFT 00000097)
[    0.000000] ACPI: SPCR 00000000dffe0460 00050 (v01 A M I  OEMSPCR  09000629 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000dffe04b0 0003C (v01 A M I  OEMMCFG  09000629 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000dffef040 00040 (v01 A M I  AMI_OEM  09000629 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000220000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000220000000
[    0.000000]   NODE_DATA [0000000000011000 - 0000000000015fff]
[    0.000000]   bootmap [0000000000016000 -  0000000000059fff] pages 44
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0220000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e0ccc]    TEXT DATA BSS ==> [0001000000 - 00019e0ccc]
[    0.000000]   #3 [00378db000 - 0037fef99b]          RAMDISK ==> [00378db000 - 0037fef99b]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e1000 - 00019e1314]              BRK ==> [00019e1000 - 00019e1314]
[    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #7 [000000c000 - 0000011000]          PGTABLE ==> [000000c000 - 0000011000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880028600000-ffff88002f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00220000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dffe0
[    0.000000]     0: 0x00100000 -> 0x00220000
[    0.000000] On node 0 totalpages: 2097018
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 108 pages reserved
[    0.000000]   DMA zone: 3830 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 899096 pages, LIFO batch:31
[    0.000000]   Normal zone: 16128 pages used for memmap
[    0.000000]   Normal zone: 1163520 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec80000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 32, address 0xfec80000, GSI 24-47
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec80400] gsi_base[48])
[    0.000000] IOAPIC[2]: apic_id 4, version 32, address 0xfec80400, GSI 48-71
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 72
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dffe0000 - 00000000dffef000
[    0.000000] PM: Registered nosave memory: 00000000dffef000 - 00000000dfffd000
[    0.000000] PM: Registered nosave memory: 00000000dfffd000 - 00000000dfffe000
[    0.000000] PM: Registered nosave memory: 00000000dfffe000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec86000
[    0.000000] PM: Registered nosave memory: 00000000fec86000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028034000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2066446
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=/dev/mapper/mybcclb1-root ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 8186712k/8912896k available (5303k kernel code, 524824k absent, 201360k reserved, 3013k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:1288
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3391.668 MHz processor.
[    0.001602] Console: colour VGA+ 80x25
[    0.001607] console [tty0] enabled
[    0.010000] allocated 83886080 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010011] Calibrating delay loop (skipped), value calculated using timer frequency.. 6783.33 BogoMIPS (lpj=33916680)
[    0.010051] Security Framework initialized
[    0.010085] AppArmor: AppArmor initialized
[    0.011267] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.017435] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.020312] Mount-cache hash table entries: 256
[    0.020563] Initializing cgroup subsys ns
[    0.020569] Initializing cgroup subsys cpuacct
[    0.020575] Initializing cgroup subsys memory
[    0.020587] Initializing cgroup subsys freezer
[    0.020590] Initializing cgroup subsys net_cls
[    0.020614] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.020617] CPU: L2 cache: 2048K
[    0.020622] CPU 0/0x0 -> Node 0
[    0.020625] CPU: Physical Processor ID: 0
[    0.020627] CPU: Processor Core ID: 0
[    0.020631] mce: CPU supports 4 MCE banks
[    0.020644] CPU0: Thermal monitoring enabled (TM1)
[    0.020650] using mwait in idle threads.
[    0.020652] Performance Counters: no PMU driver, software counters only.
[    0.023563] ACPI: Core revision 20090521
[    0.039798] Setting APIC routing to flat
[    0.040260] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.140283] CPU0: Intel(R) Xeon(TM) CPU 3.40GHz stepping 0a
[    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6783.17 BogoMIPS (lpj=33915880)
[    0.010000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 4 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM1)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.301087] CPU1: Intel(R) Xeon(TM) CPU 3.40GHz stepping 0a
[    0.301105] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.310063] Brought up 2 CPUs
[    0.310067] Total of 2 processors activated (13566.51 BogoMIPS).
[    0.310125] CPU0 attaching sched-domain:
[    0.310129]  domain 0: span 0-1 level SIBLING
[    0.310133]   groups: 0 1
[    0.310140] CPU1 attaching sched-domain:
[    0.310142]  domain 0: span 0-1 level SIBLING
[    0.310145]   groups: 1 0
[    0.310269] Booting paravirtualized kernel on bare hardware
[    0.310269] regulator: core version 0.5
[    0.310269] Time: 22:48:09  Date: 11/02/09
[    0.310269] NET: Registered protocol family 16
[    0.310308] ACPI: bus type pci registered
[    0.310379] PCI: Found Intel Corporation E7520 Memory Controller Hub with MMCONFIG support.
[    0.310388] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.310391] PCI: Not using MMCONFIG.
[    0.310394] PCI: Using configuration type 1 for base access
[    0.311464] bio: create slab <bio-0> at 0
[    0.311464] ACPI: EC: Look up EC in DSDT
[    0.323424] ACPI: Interpreter enabled
[    0.323430] ACPI: (supports S0 S1 S4 S5)
[    0.323456] ACPI: Using IOAPIC for interrupt routing
[    0.331362] ACPI: No dock devices found.
[    0.331512] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.331700] pci 0000:00:01.0: reg 10 32bit mmio: [0xfcbff000-0xfcbfffff]
[    0.331791] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.331796] pci 0000:00:02.0: PME# disabled
[    0.331858] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.331863] pci 0000:00:06.0: PME# disabled
[    0.331935] pci 0000:00:1d.0: reg 20 io port: [0xb880-0xb89f]
[    0.331991] pci 0000:00:1d.1: reg 20 io port: [0xbc00-0xbc1f]
[    0.332046] pci 0000:00:1d.2: reg 20 io port: [0xbc80-0xbc9f]
[    0.332113] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfcbfec00-0xfcbfefff]
[    0.332171] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.332176] pci 0000:00:1d.7: PME# disabled
[    0.332265] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.332271] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.332275] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO
[    0.332300] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.332307] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.332314] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.332321] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.332328] pci 0000:00:1f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.332335] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.332366] pci 0000:00:1f.2: reg 10 io port: [0xb800-0xb807]
[    0.332373] pci 0000:00:1f.2: reg 14 io port: [0xb480-0xb483]
[    0.332379] pci 0000:00:1f.2: reg 18 io port: [0xb400-0xb407]
[    0.332385] pci 0000:00:1f.2: reg 1c io port: [0xb080-0xb083]
[    0.332392] pci 0000:00:1f.2: reg 20 io port: [0xb000-0xb00f]
[    0.332444] pci 0000:00:1f.3: reg 20 io port: [0x540-0x55f]
[    0.332501] pci 0000:01:00.0: PXH quirk detected; SHPC device MSI disabled
[    0.332533] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.332537] pci 0000:01:00.0: PME# disabled
[    0.332574] pci 0000:01:00.2: PXH quirk detected; SHPC device MSI disabled
[    0.332606] pci 0000:01:00.2: PME# supported from D0 D3hot D3cold
[    0.332610] pci 0000:01:00.2: PME# disabled
[    0.332665] pci 0000:00:02.0: bridge io port: [0xc000-0xdfff]
[    0.332669] pci 0000:00:02.0: bridge 32bit mmio: [0xfcc00000-0xfcffffff]
[    0.332722] pci 0000:02:05.0: reg 10 io port: [0xc800-0xc8ff]
[    0.332733] pci 0000:02:05.0: reg 14 64bit mmio: [0xfced0000-0xfcedffff]
[    0.332744] pci 0000:02:05.0: reg 1c 64bit mmio: [0xfcec0000-0xfcecffff]
[    0.332755] pci 0000:02:05.0: reg 30 32bit mmio: [0xfcc00000-0xfccfffff]
[    0.332779] pci 0000:02:05.0: supports D1 D2
[    0.332825] pci 0000:02:05.1: reg 10 io port: [0xcc00-0xccff]
[    0.332836] pci 0000:02:05.1: reg 14 64bit mmio: [0xfcef0000-0xfcefffff]
[    0.332847] pci 0000:02:05.1: reg 1c 64bit mmio: [0xfcee0000-0xfceeffff]
[    0.332858] pci 0000:02:05.1: reg 30 32bit mmio: [0xfcd00000-0xfcdfffff]
[    0.332882] pci 0000:02:05.1: supports D1 D2
[    0.332931] pci 0000:01:00.0: bridge io port: [0xc000-0xcfff]
[    0.332935] pci 0000:01:00.0: bridge 32bit mmio: [0xfcc00000-0xfcefffff]
[    0.332990] pci 0000:03:04.0: reg 10 64bit mmio: [0xfcfa0000-0xfcfbffff]
[    0.333005] pci 0000:03:04.0: reg 20 io port: [0xdc00-0xdc3f]
[    0.333036] pci 0000:03:04.0: PME# supported from D0 D3hot D3cold
[    0.333040] pci 0000:03:04.0: PME# disabled
[    0.333089] pci 0000:03:04.1: reg 10 64bit mmio: [0xfcfe0000-0xfcffffff]
[    0.333104] pci 0000:03:04.1: reg 20 io port: [0xdc80-0xdcbf]
[    0.333134] pci 0000:03:04.1: PME# supported from D0 D3hot D3cold
[    0.333139] pci 0000:03:04.1: PME# disabled
[    0.333189] pci 0000:01:00.2: bridge io port: [0xd000-0xdfff]
[    0.333193] pci 0000:01:00.2: bridge 32bit mmio: [0xfcf00000-0xfcffffff]
[    0.333307] pci 0000:05:0c.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.333314] pci 0000:05:0c.0: reg 14 io port: [0xec00-0xecff]
[    0.333322] pci 0000:05:0c.0: reg 18 32bit mmio: [0xfebff000-0xfebfffff]
[    0.333342] pci 0000:05:0c.0: reg 30 32bit mmio: [0xfebc0000-0xfebdffff]
[    0.333361] pci 0000:05:0c.0: supports D1 D2
[    0.333391] pci 0000:00:1e.0: transparent bridge
[    0.333396] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.333400] pci 0000:00:1e.0: bridge 32bit mmio: [0xfd000000-0xfebfffff]
[    0.333422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.333655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EPA0._PRT]
[    0.333723] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EPA0.PXHA._PRT]
[    0.333905] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EPA0.PXHB._PRT]
[    0.334030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EPC0._PRT]
[    0.334373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.337166] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 7 *10 11 12 14 15)
[    0.337363] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 7 10 *11 12 14 15)
[    0.337557] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *7 10 11 12 14 15)
[    0.337750] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 7 *10 11 12 14 15)
[    0.337942] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 7 10 11 12 14 15) *0, disabled.
[    0.338135] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 7 10 11 12 14 15) *0, disabled.
[    0.338336] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 7 10 11 12 14 15) *0, disabled.
[    0.338531] ACPI: PCI Interrupt Link [LNKH] (IRQs *5)
[    0.338789] SCSI subsystem initialized
[    0.338825] libata version 3.00 loaded.
[    0.338825] usbcore: registered new interface driver usbfs
[    0.338825] usbcore: registered new interface driver hub
[    0.338825] usbcore: registered new device driver usb
[    0.338825] ACPI: WMI: Mapper loaded
[    0.338825] PCI: Using ACPI for IRQ routing
[    0.370013] Bluetooth: Core ver 2.15
[    0.370041] NET: Registered protocol family 31
[    0.370041] Bluetooth: HCI device and connection manager initialized
[    0.370041] Bluetooth: HCI socket layer initialized
[    0.370041] NetLabel: Initializing
[    0.370041] NetLabel:  domain hash size = 128
[    0.370041] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.370062] NetLabel:  unlabeled traffic allowed by default
[    0.370198] hpet clockevent registered
[    0.370203] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.370208] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.370214] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.410015] pnp: PnP ACPI init
[    0.410035] ACPI: bus type pnp registered
[    0.415592] pnp: PnP ACPI: found 15 devices
[    0.415595] ACPI: ACPI bus type pnp unregistered
[    0.415617] system 00:09: ioport range 0x680-0x69f has been reserved
[    0.415620] system 00:09: ioport range 0x640-0x65f has been reserved
[    0.415623] system 00:09: ioport range 0x600-0x60f has been reserved
[    0.415626] system 00:09: ioport range 0x6c0-0x6df has been reserved
[    0.415629] system 00:09: ioport range 0x700-0x71f has been reserved
[    0.415632] system 00:09: ioport range 0x720-0x73f has been reserved
[    0.415635] system 00:09: ioport range 0x740-0x74f has been reserved
[    0.415638] system 00:09: ioport range 0x6ae-0x6ae has been reserved
[    0.415641] system 00:09: ioport range 0x6af-0x6af has been reserved
[    0.415647] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.415650] system 00:0a: ioport range 0x400-0x47f has been reserved
[    0.415653] system 00:0a: ioport range 0x500-0x53f has been reserved
[    0.415656] system 00:0a: ioport range 0xca4-0xca5 has been reserved
[    0.415659] system 00:0a: ioport range 0x900-0x90f has been reserved
[    0.415662] system 00:0a: ioport range 0x910-0x91f has been reserved
[    0.415666] system 00:0a: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.415672] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.415676] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.415681] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.415688] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.415690] system 00:0e: iomem range 0xc0000-0xdffff has been reserved
[    0.415693] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.415696] system 00:0e: iomem range 0x100000-0xdfffffff could not be reserved
[    0.415699] system 00:0e: iomem range 0xffc00000-0xffffffff has been reserved
[    0.420427] AppArmor: AppArmor Filesystem Enabled
[    0.420450] pci 0000:05:0c.0: BAR 6: address space collision on of device [0xfebc0000-0xfebdffff]
[    0.420495] pci 0000:01:00.0: PCI bridge, secondary bus 0000:02
[    0.420499] pci 0000:01:00.0:   IO window: 0xc000-0xcfff
[    0.420504] pci 0000:01:00.0:   MEM window: 0xfcc00000-0xfcefffff
[    0.420508] pci 0000:01:00.0:   PREFETCH window: disabled
[    0.420513] pci 0000:01:00.2: PCI bridge, secondary bus 0000:03
[    0.420516] pci 0000:01:00.2:   IO window: 0xd000-0xdfff
[    0.420521] pci 0000:01:00.2:   MEM window: 0xfcf00000-0xfcffffff
[    0.420524] pci 0000:01:00.2:   PREFETCH window: disabled
[    0.420528] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.420532] pci 0000:00:02.0:   IO window: 0xc000-0xdfff
[    0.420536] pci 0000:00:02.0:   MEM window: 0xfcc00000-0xfcffffff
[    0.420540] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.420544] pci 0000:00:06.0: PCI bridge, secondary bus 0000:04
[    0.420546] pci 0000:00:06.0:   IO window: disabled
[    0.420551] pci 0000:00:06.0:   MEM window: disabled
[    0.420554] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.420559] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.420563] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.420568] pci 0000:00:1e.0:   MEM window: 0xfd000000-0xfebfffff
[    0.420573] pci 0000:00:1e.0:   PREFETCH window: 0xf0000000-0xf00fffff
[    0.420588]   alloc irq_desc for 16 on node 0
[    0.420591]   alloc kstat_irqs on node 0
[    0.420598] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.420604] pci 0000:00:02.0: setting latency timer to 64
[    0.420613] pci 0000:01:00.0: setting latency timer to 64
[    0.420620] pci 0000:01:00.2: setting latency timer to 64
[    0.420630] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.420634] pci 0000:00:06.0: setting latency timer to 64
[    0.420642] pci 0000:00:1e.0: setting latency timer to 64
[    0.420648] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.420650] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.420653] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.420656] pci_bus 0000:01: resource 1 mem: [0xfcc00000-0xfcffffff]
[    0.420659] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.420661] pci_bus 0000:02: resource 1 mem: [0xfcc00000-0xfcefffff]
[    0.420664] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.420666] pci_bus 0000:03: resource 1 mem: [0xfcf00000-0xfcffffff]
[    0.420669] pci_bus 0000:05: resource 0 io:  [0xe000-0xefff]
[    0.420672] pci_bus 0000:05: resource 1 mem: [0xfd000000-0xfebfffff]
[    0.420674] pci_bus 0000:05: resource 2 pref mem [0xf0000000-0xf00fffff]
[    0.420677] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.420679] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.420728] NET: Registered protocol family 2
[    0.421146] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.424058] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.429772] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.430546] TCP: Hash tables configured (established 524288 bind 65536)
[    0.430551] TCP reno registered
[    0.430756] NET: Registered protocol family 1
[    0.430855] Trying to unpack rootfs image as initramfs...
[    0.634613] Freeing initrd memory: 7250k freed
[    0.640953] Scanning for low memory corruption every 60 seconds
[    0.641144] audit: initializing netlink socket (disabled)
[    0.641167] type=2000 audit(1257202089.639:1): initialized
[    0.650355] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.652156] VFS: Disk quotas dquot_6.5.2
[    0.652233] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.653046] fuse init (API version 7.12)
[    0.653145] msgmni has been set to 16003
[    0.653458] alg: No test for stdrng (krng)
[    0.653479] io scheduler noop registered
[    0.653482] io scheduler anticipatory registered
[    0.653484] io scheduler deadline registered (default)
[    0.653539] io scheduler cfq registered
[    0.653655] PCI quirk: reroute interrupts for 0x8086:0x0329
[    0.653660] PCI quirk: reroute interrupts for 0x8086:0x032a
[    0.653674] pci 0000:05:0c.0: Boot video device
[    0.653823] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.653947] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    0.654186] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.654222] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.654383] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.654388] ACPI: Power Button [PWRF]
[    0.654460] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.654464] ACPI: Power Button [PWRB]
[    0.655702] ACPI: SSDT 00000000dffe4e40 002E4 (v01    AMI   CPU1PM 00000001 INTL 02002026)
[    0.656028] processor LNXCPU:00: registered as cooling_device0
[    0.656033] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.656361] ACPI: SSDT 00000000dffe5130 002E4 (v01    AMI   CPU2PM 00000001 INTL 02002026)
[    0.656659] processor LNXCPU:01: registered as cooling_device1
[    0.656664] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.660476] Linux agpgart interface v0.103
[    0.660490] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.660604] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.660699] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.661005] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.661138] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.662445] brd: module loaded
[    0.662991] loop: module loaded
[    0.663076] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.663260] ata_piix 0000:00:1f.1: version 2.13
[    0.663281]   alloc irq_desc for 18 on node 0
[    0.663284]   alloc kstat_irqs on node 0
[    0.663294] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.663353] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.663493] scsi0 : ata_piix
[    0.663612] scsi1 : ata_piix
[    0.665326] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.665330] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.665414] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.665422] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.665492] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.665666] scsi2 : ata_piix
[    0.665738] scsi3 : ata_piix
[    0.665779] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb000 irq 18
[    0.665783] ata4: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xb008 irq 18
[    0.666807] Fixed MDIO Bus: probed
[    0.666851] PPP generic driver version 2.4.2
[    0.666958] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.667028]   alloc irq_desc for 23 on node 0
[    0.667031]   alloc kstat_irqs on node 0
[    0.667037] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.667061] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.667066] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.667132] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.671048] ehci_hcd 0000:00:1d.7: debug port 1
[    0.671055] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.671069] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfcbfec00
[    0.690033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.690147] usb usb1: configuration #1 chosen from 1 choice
[    0.690192] hub 1-0:1.0: USB hub found
[    0.690204] hub 1-0:1.0: 6 ports detected
[    0.690313] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.690338] uhci_hcd: USB Universal Host Controller Interface driver
[    0.690443] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.690452] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.690456] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.690493] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.690528] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000b880
[    0.690625] usb usb2: configuration #1 chosen from 1 choice
[    0.690659] hub 2-0:1.0: USB hub found
[    0.690669] hub 2-0:1.0: 2 ports detected
[    0.690767]   alloc irq_desc for 19 on node 0
[    0.690770]   alloc kstat_irqs on node 0
[    0.690776] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.690783] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.690786] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.690826] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.690855] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bc00
[    0.690947] usb usb3: configuration #1 chosen from 1 choice
[    0.690977] hub 3-0:1.0: USB hub found
[    0.690987] hub 3-0:1.0: 2 ports detected
[    0.691086] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.691094] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.691098] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.691134] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.691156] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bc80
[    0.691254] usb usb4: configuration #1 chosen from 1 choice
[    0.691285] hub 4-0:1.0: USB hub found
[    0.691294] hub 4-0:1.0: 2 ports detected
[    0.691426] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.694218] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.694227] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.694332] mice: PS/2 mouse device common for all mice
[    0.694443] rtc_cmos 00:02: RTC can wake from S4
[    0.694491] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.694515] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.694641] device-mapper: uevent: version 1.0.3
[    0.694746] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.694841] device-mapper: multipath: version 1.1.0 loaded
[    0.694845] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.695086] cpuidle: using governor ladder
[    0.695089] cpuidle: using governor menu
[    0.695601] TCP cubic registered
[    0.695754] NET: Registered protocol family 10
[    0.696352] lo: Disabled Privacy Extensions
[    0.696682] NET: Registered protocol family 17
[    0.696707] Bluetooth: L2CAP ver 2.13
[    0.696709] Bluetooth: L2CAP socket layer initialized
[    0.696712] Bluetooth: SCO (Voice Link) ver 0.6
[    0.696714] Bluetooth: SCO socket layer initialized
[    0.696760] Bluetooth: RFCOMM TTY layer initialized
[    0.696764] Bluetooth: RFCOMM socket layer initialized
[    0.696766] Bluetooth: RFCOMM ver 1.11
[    0.698981] PM: Resume from disk failed.
[    0.698999] registered taskstats version 1
[    0.699201]   Magic number: 1:303:855
[    0.699302] rtc_cmos 00:02: setting system clock to 2009-11-02 22:48:10 UTC (1257202090)
[    0.699306] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.699308] EDD information not available.
[    0.726450] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.841552] ata1.00: ATAPI: Slimtype COMBO SSC-2485K, 5GK1, max UDMA/33
[    0.861735] ata3.00: ATA-6: ST340014AS, 3.00, max UDMA/133
[    0.861739] ata3.00: 78165360 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.871229] Switched to high resolution mode on CPU 1
[    0.880058] Switched to high resolution mode on CPU 0
[    0.880941] ata1.00: configured for UDMA/33
[    0.900423] ata3.00: configured for UDMA/133
[    0.901130] scsi 0:0:0:0: CD-ROM            Slimtype COMBO SSC-2485K  5GK1 PQ: 0 ANSI: 5
[    0.903878] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    0.903884] Uniform CD-ROM driver Revision: 3.20
[    0.904006] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.904063] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.904154] scsi 2:0:0:0: Direct-Access     ATA      ST340014AS       3.00 PQ: 0 ANSI: 5
[    0.904294] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.904340] sd 2:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.904403] sd 2:0:0:0: [sda] Write Protect is off
[    0.904406] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.904439] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.904594]  sda: sda1 sda2 < sda5 >
[    0.940972] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.940994] Freeing unused kernel memory: 660k freed
[    0.941562] Write protecting the kernel read-only data: 7572k
[    1.233196] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    1.233204] Copyright (c) 1999-2006 Intel Corporation.
[    1.233414]   alloc irq_desc for 54 on node 0
[    1.233420]   alloc kstat_irqs on node 0
[    1.233436] e1000 0000:03:04.0: PCI INT A -> GSI 54 (level, low) -> IRQ 54
[    1.251616] Fusion MPT base driver 3.04.10
[    1.251623] Copyright (c) 1999-2008 LSI Corporation
[    1.268389] Fusion MPT SPI Host driver 3.04.10
[    1.519163] e1000: 0000:03:04.0: e1000_probe: (PCI-X:100MHz:64-bit) 00:04:23:d1:b0:12
[    1.519208]   alloc irq_desc for 26 on node 0
[    1.519212]   alloc kstat_irqs on node 0
[    1.519223] mptspi 0000:02:05.0: PCI INT A -> GSI 26 (level, low) -> IRQ 26
[    1.519414] mptbase: ioc0: Initiating bringup
[    1.567908] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    1.568050]   alloc irq_desc for 55 on node 0
[    1.568055]   alloc kstat_irqs on node 0
[    1.568070] e1000 0000:03:04.1: PCI INT B -> GSI 55 (level, low) -> IRQ 55
[    1.849289] e1000: 0000:03:04.1: e1000_probe: (PCI-X:100MHz:64-bit) 00:04:23:d1:b0:13
[    1.890241] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.150010] ioc0: LSI53C1030 C0: Capabilities={Initiator}
[    5.283231] scsi4 : ioc0: LSI53C1030 C0, FwRev=01032700h, Ports=1, MaxQ=222, IRQ=26
[    5.892894]   alloc irq_desc for 25 on node 0
[    5.892898]   alloc kstat_irqs on node 0
[    5.892908] mptspi 0000:02:05.1: PCI INT B -> GSI 25 (level, low) -> IRQ 25
[    5.893062] mptbase: ioc1: Initiating bringup
[    8.430023] ioc1: LSI53C1030 C0: Capabilities={Initiator}
[   10.623210] scsi5 : ioc1: LSI53C1030 C0, FwRev=01032700h, Ports=1, MaxQ=222, IRQ=25
[   11.338120] PM: Starting manual resume from disk
[   11.338126] PM: Resume from partition 252:1
[   11.338128] PM: Checking hibernation image.
[   11.338302] PM: Resume from disk failed.
[   11.370340] EXT4-fs (dm-0): barriers enabled
[   11.388230] kjournald2 starting: pid 405, dev dm-0:8, commit interval 5 seconds
[   11.388281] EXT4-fs (dm-0): delayed allocation enabled
[   11.388286] EXT4-fs: file extents enabled
[   11.391636] EXT4-fs: mballoc enabled
[   11.391657] EXT4-fs (dm-0): mounted filesystem with ordered data mode
[   12.203556] type=1505 audit(1257202102.001:2): operation="profile_load" pid=426 name=/sbin/dhclient3
[   12.204195] type=1505 audit(1257202102.001:3): operation="profile_load" pid=426 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.204539] type=1505 audit(1257202102.001:4): operation="profile_load" pid=426 name=/usr/lib/connman/scripts/dhclient-script
[   12.219453] type=1505 audit(1257202102.011:5): operation="profile_load" pid=427 name=/usr/sbin/tcpdump
[   12.981216] Adding 1642488k swap on /dev/mapper/mybcclb1-swap_1.  Priority:-1 extents:1 across:1642488k 
[   14.072498] EXT4-fs (dm-0): internal journal on dm-0:8
[   14.128197] udev: starting version 147
[   16.334691] EDAC MC: Ver: 2.1.0 Oct 16 2009
[   16.349061] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.543366] EDAC e752x: tolm = e0000, remapbase = 200000, remaplimit = 21c000
[   16.543431] EDAC MC0: Giving out device to 'e752x_edac' 'E7520': DEV 0000:00:00.0
[   16.543514] EDAC PCI0: Giving out device to module 'e752x_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
[   16.627844] intel_rng: FWH not detected
[   16.633380] lp: driver loaded but no devices found
[   16.894456] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.953377] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   17.313920] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   17.314259] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   17.314262] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   17.314264] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   18.483700] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   18.642153] type=1505 audit(1257202108.440:6): operation="profile_replace" pid=827 name=/sbin/dhclient3
[   18.642793] type=1505 audit(1257202108.440:7): operation="profile_replace" pid=827 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.643143] type=1505 audit(1257202108.440:8): operation="profile_replace" pid=827 name=/usr/lib/connman/scripts/dhclient-script
[   18.645787] type=1505 audit(1257202108.440:9): operation="profile_replace" pid=828 name=/usr/sbin/tcpdump
[   21.288835] Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)
[   21.288840] bonding: Warning: either miimon or arp_interval and arp_ip_target module parameters must be specified, otherwise bonding will not detect link failures! see bonding.txt for details.
[   21.358722] bonding: bond0: doing slave updates when interface is down.
[   21.358731] bonding: bond0: Adding slave eth0.
[   21.358734] bonding bond0: master_dev is not up in bond_enslave
[   21.407852] bonding: bond0: enslaving eth0 as an active interface with an up link.
[   21.411201] bonding: bond0: doing slave updates when interface is down.
[   21.411211] bonding: bond0: Adding slave eth1.
[   21.411217] bonding bond0: master_dev is not up in bond_enslave
[   21.420389] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   21.456062] bonding: bond0: enslaving eth1 as an active interface with an up link.
[   21.456262] bonding: bond0: setting mode to 802.3ad (4).
[   21.470388] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   21.681331] 802.1Q VLAN Support v1.8 Ben Greear <greearb@candelatech.com>
[   21.681335] All bugs added by David S. Miller <davem@redhat.com>
[   21.690998] bonding: bond0: Warning: bond's first port is uninitialized
[   21.790663] bonding: bond0: Warning: Found an uninitialized port
[   21.890642] bonding: bond0: Warning: Found an uninitialized port
[   21.990644] bonding: bond0: Warning: Found an uninitialized port
[   22.090662] bonding: bond0: Warning: Found an uninitialized port
[   22.190652] bonding: bond0: Warning: Found an uninitialized port
[   22.290641] bonding: bond0: Warning: Found an uninitialized port
[   22.390652] bonding: bond0: Warning: Found an uninitialized port
[   22.490018] bonding: bond0: Warning: Found an uninitialized port
[   22.590014] bonding: bond0: Warning: Found an uninitialized port
[   22.690012] bonding: bond0: Warning: Found an uninitialized port
[   22.790012] bonding: bond0: Warning: Found an uninitialized port
[   22.890011] bonding: bond0: Warning: Found an uninitialized port
[   22.990012] bonding: bond0: Warning: Found an uninitialized port
[   23.090021] bonding: bond0: Warning: Found an uninitialized port
[   23.190012] bonding: bond0: Warning: Found an uninitialized port
[   23.290653] bonding: bond0: Warning: Found an uninitialized port
[   23.390011] bonding: bond0: Warning: Found an uninitialized port
[   23.490013] bonding: bond0: Warning: Found an uninitialized port
[   23.590013] bonding: bond0: Warning: Found an uninitialized port
[   23.690012] bonding: bond0: Warning: Found an uninitialized port
[   23.790011] bonding: bond0: Warning: Found an uninitialized port
[   23.890010] bonding: bond0: Warning: Found an uninitialized port
[   23.990011] bonding: bond0: Warning: Found an uninitialized port
[   24.090029] bonding: bond0: Warning: Found an uninitialized port
[   24.190012] bonding: bond0: Warning: Found an uninitialized port
[   24.290014] bonding: bond0: Warning: Found an uninitialized port
[   24.390009] bonding: bond0: Warning: Found an uninitialized port
[   24.490011] bonding: bond0: Warning: Found an uninitialized port
[   24.590013] bonding: bond0: Warning: Found an uninitialized port
[   24.690012] bonding: bond0: Warning: Found an uninitialized port
[   24.790667] bonding: bond0: Warning: Found an uninitialized port
[   24.890014] bonding: bond0: Warning: Found an uninitialized port
[   24.990014] bonding: bond0: Warning: Found an uninitialized port
[   25.090642] bonding: bond0: Warning: Found an uninitialized port
[   25.190013] bonding: bond0: Warning: Found an uninitialized port
[   25.290637] bonding: bond0: Warning: Found an uninitialized port
[   25.390008] bonding: bond0: Warning: Found an uninitialized port
[   25.490011] bonding: bond0: Warning: Found an uninitialized port
[   25.590010] bonding: bond0: Warning: Found an uninitialized port
[   25.690635] bonding: bond0: Warning: Found an uninitialized port
[   25.790013] bonding: bond0: Warning: Found an uninitialized port
[   25.890009] bonding: bond0: Warning: Found an uninitialized port
[   25.990009] bonding: bond0: Warning: Found an uninitialized port
[   26.090026] bonding: bond0: Warning: Found an uninitialized port
[   26.190011] bonding: bond0: Warning: Found an uninitialized port
[   26.290634] bonding: bond0: Warning: Found an uninitialized port
[   26.390650] bonding: bond0: Warning: Found an uninitialized port
[   26.490640] bonding: bond0: Warning: Found an uninitialized port
[   26.590014] bonding: bond0: Warning: Found an uninitialized port
[   26.690012] bonding: bond0: Warning: Found an uninitialized port
[   26.790012] bonding: bond0: Warning: Found an uninitialized port
[   26.890010] bonding: bond0: Warning: Found an uninitialized port
[   26.990013] bonding: bond0: Warning: Found an uninitialized port
[   27.090018] bonding: bond0: Warning: Found an uninitialized port
[   27.190011] bonding: bond0: Warning: Found an uninitialized port
[   27.203408] bonding: bond0: Error: bond_3ad_get_active_agg_info failed
[   27.290009] bonding: bond0: Warning: Found an uninitialized port
[   27.390009] bonding: bond0: Warning: Found an uninitialized port
[   27.490009] bonding: bond0: Warning: Found an uninitialized port
[   27.590009] bonding: bond0: Warning: Found an uninitialized port
[   27.690009] bonding: bond0: Warning: Found an uninitialized port
[   27.790013] bonding: bond0: Warning: Found an uninitialized port
[   27.890009] bonding: bond0: Warning: Found an uninitialized port
[   27.990009] bonding: bond0: Warning: Found an uninitialized port
[   28.090014] bonding: bond0: Warning: Found an uninitialized port
[   28.190635] bonding: bond0: Warning: Found an uninitialized port
[   28.290017] bonding: bond0: Warning: Found an uninitialized port
[   28.390008] bonding: bond0: Warning: Found an uninitialized port
[   28.490013] bonding: bond0: Warning: Found an uninitialized port
[   28.590009] bonding: bond0: Warning: Found an uninitialized port
[   28.690013] bonding: bond0: Warning: Found an uninitialized port
[   28.790009] bonding: bond0: Warning: Found an uninitialized port
[   28.890009] bonding: bond0: Warning: Found an uninitialized port
[   28.990009] bonding: bond0: Warning: Found an uninitialized port
[   29.090017] bonding: bond0: Warning: Found an uninitialized port
[   29.190008] bonding: bond0: Warning: Found an uninitialized port
[   29.290014] bonding: bond0: Warning: Found an uninitialized port
[   29.390635] bonding: bond0: Warning: Found an uninitialized port
[   29.490013] bonding: bond0: Warning: Found an uninitialized port
[   29.590649] bonding: bond0: Warning: Found an uninitialized port
[   29.690654] bonding: bond0: Warning: Found an uninitialized port
[   29.790639] bonding: bond0: Warning: Found an uninitialized port
[   29.890655] bonding: bond0: Warning: Found an uninitialized port
[   29.990680] bonding: bond0: Warning: Found an uninitialized port
[   30.090656] bonding: bond0: Warning: Found an uninitialized port
[   30.190652] bonding: bond0: Warning: Found an uninitialized port
[   30.290661] bonding: bond0: Warning: Found an uninitialized port
[   30.390656] bonding: bond0: Warning: Found an uninitialized port
[   30.490665] bonding: bond0: Warning: Found an uninitialized port
[   30.590674] bonding: bond0: Warning: Found an uninitialized port
[   30.690649] bonding: bond0: Warning: Found an uninitialized port
[   30.790662] bonding: bond0: Warning: Found an uninitialized port
[   30.890661] bonding: bond0: Warning: Found an uninitialized port
[   30.990665] bonding: bond0: Warning: Found an uninitialized port
[   31.090664] bonding: bond0: Warning: Found an uninitialized port
[   31.190694] bonding: bond0: Warning: Found an uninitialized port
[   31.290655] bonding: bond0: Warning: Found an uninitialized port
[   31.390655] bonding: bond0: Warning: Found an uninitialized port
[   31.490676] bonding: bond0: Warning: Found an uninitialized port
[   31.590680] bonding: bond0: Warning: Found an uninitialized port
[   31.690675] bonding: bond0: Warning: Found an uninitialized port
[   31.790665] bonding: bond0: Warning: Found an uninitialized port
[   31.880027] bond0: no IPv6 routers present
[   31.890685] bonding: bond0: Warning: Found an uninitialized port
[   31.990654] bonding: bond0: Warning: Found an uninitialized port
[   32.090702] bonding: bond0: Warning: Found an uninitialized port
[   32.190662] bonding: bond0: Warning: Found an uninitialized port
[   32.220661] vlan32: no IPv6 routers present
[   32.290675] bonding: bond0: Warning: Found an uninitialized port
[   32.390657] bonding: bond0: Warning: Found an uninitialized port
[   32.490655] bonding: bond0: Warning: Found an uninitialized port
[   32.590664] bonding: bond0: Warning: Found an uninitialized port
[   32.690695] bonding: bond0: Warning: Found an uninitialized port
[   32.790660] bonding: bond0: Warning: Found an uninitialized port
[   32.890671] bonding: bond0: Warning: Found an uninitialized port
[   32.990789] bonding: bond0: Warning: Found an uninitialized port
[   33.090696] bonding: bond0: Warning: Found an uninitialized port
[   33.190655] bonding: bond0: Warning: Found an uninitialized port
[   33.290658] bonding: bond0: Warning: Found an uninitialized port
[   33.390651] bonding: bond0: Warning: Found an uninitialized port
[   33.490646] bonding: bond0: Warning: Found an uninitialized port
[   33.590697] bonding: bond0: Warning: Found an uninitialized port
[   33.690013] bonding: bond0: Warning: Found an uninitialized port
[   33.790015] bonding: bond0: Warning: Found an uninitialized port
[   33.890010] bonding: bond0: Warning: Found an uninitialized port
[   33.990012] bonding: bond0: Warning: Found an uninitialized port
[   34.090025] bonding: bond0: Warning: Found an uninitialized port
[   34.190010] bonding: bond0: Warning: Found an uninitialized port
[   34.206420] bonding: bond0: Error: bond_3ad_get_active_agg_info failed
[   34.290009] bonding: bond0: Warning: Found an uninitialized port
[   34.390009] bonding: bond0: Warning: Found an uninitialized port
[   34.490011] bonding: bond0: Warning: Found an uninitialized port
[   34.590011] bonding: bond0: Warning: Found an uninitialized port
[   34.690010] bonding: bond0: Warning: Found an uninitialized port
[   34.790008] bonding: bond0: Warning: Found an uninitialized port
[   34.890011] bonding: bond0: Warning: Found an uninitialized port
[   34.990012] bonding: bond0: Warning: Found an uninitialized port
[   35.090017] bonding: bond0: Warning: Found an uninitialized port
[   35.190009] bonding: bond0: Warning: Found an uninitialized port
[   35.290641] bonding: bond0: Warning: Found an uninitialized port
[   35.390010] bonding: bond0: Warning: Found an uninitialized port
[   35.490012] bonding: bond0: Warning: Found an uninitialized port
[   35.590013] bonding: bond0: Warning: Found an uninitialized port
[   35.690012] bonding: bond0: Warning: Found an uninitialized port
[   35.790011] bonding: bond0: Warning: Found an uninitialized port
[   35.890009] bonding: bond0: Warning: Found an uninitialized port
[   35.990013] bonding: bond0: Warning: Found an uninitialized port
[   36.090024] bonding: bond0: Warning: Found an uninitialized port
[   36.190014] bonding: bond0: Warning: Found an uninitialized port
[   36.290017] bonding: bond0: Warning: Found an uninitialized port
[   36.390012] bonding: bond0: Warning: Found an uninitialized port
[   36.490011] bonding: bond0: Warning: Found an uninitialized port
[   36.590013] bonding: bond0: Warning: Found an uninitialized port
[   36.690011] bonding: bond0: Warning: Found an uninitialized port
[   36.790012] bonding: bond0: Warning: Found an uninitialized port
[   36.890009] bonding: bond0: Warning: Found an uninitialized port
[   36.990014] bonding: bond0: Warning: Found an uninitialized port
[   37.090014] bonding: bond0: Warning: Found an uninitialized port
[   37.190011] bonding: bond0: Warning: Found an uninitialized port
[   37.290017] bonding: bond0: Warning: Found an uninitialized port
[   37.390009] bonding: bond0: Warning: Found an uninitialized port
[   37.490012] bonding: bond0: Warning: Found an uninitialized port
[   37.590013] bonding: bond0: Warning: Found an uninitialized port
[   37.690011] bonding: bond0: Warning: Found an uninitialized port
[   37.790012] bonding: bond0: Warning: Found an uninitialized port
[   37.890009] bonding: bond0: Warning: Found an uninitialized port
[   37.990014] bonding: bond0: Warning: Found an uninitialized port
[   38.090014] bonding: bond0: Warning: Found an uninitialized port
[   38.190014] bonding: bond0: Warning: Found an uninitialized port
[   38.290014] bonding: bond0: Warning: Found an uninitialized port
[   38.390646] bonding: bond0: Warning: Found an uninitialized port
[   38.490010] bonding: bond0: Warning: Found an uninitialized port
[   38.590022] bonding: bond0: Warning: Found an uninitialized port
[   38.690011] bonding: bond0: Warning: Found an uninitialized port
[   38.790646] bonding: bond0: Warning: Found an uninitialized port
[   38.890633] bonding: bond0: Warning: Found an uninitialized port
[   38.990011] bonding: bond0: Warning: Found an uninitialized port
[   39.090028] bonding: bond0: Warning: Found an uninitialized port
[   39.190016] bonding: bond0: Warning: Found an uninitialized port
[   39.290639] bonding: bond0: Warning: Found an uninitialized port
[   39.390009] bonding: bond0: Warning: Found an uninitialized port
[   39.490011] bonding: bond0: Warning: Found an uninitialized port
[   39.590011] bonding: bond0: Warning: Found an uninitialized port
[   39.690010] bonding: bond0: Warning: Found an uninitialized port
[   39.790641] bonding: bond0: Warning: Found an uninitialized port
[   39.890010] bonding: bond0: Warning: Found an uninitialized port
[   39.990012] bonding: bond0: Warning: Found an uninitialized port
[   40.090019] bonding: bond0: Warning: Found an uninitialized port
[   40.190632] bonding: bond0: Warning: Found an uninitialized port
[   40.290010] bonding: bond0: Warning: Found an uninitialized port
[   40.390008] bonding: bond0: Warning: Found an uninitialized port
[   40.490640] bonding: bond0: Warning: Found an uninitialized port
[   40.590010] bonding: bond0: Warning: Found an uninitialized port
[   40.690012] bonding: bond0: Warning: Found an uninitialized port
[   40.790012] bonding: bond0: Warning: Found an uninitialized port
[   40.890009] bonding: bond0: Warning: Found an uninitialized port
[   40.990010] bonding: bond0: Warning: Found an uninitialized port
[   41.090018] bonding: bond0: Warning: Found an uninitialized port
[   41.190012] bonding: bond0: Warning: Found an uninitialized port
[   41.290017] bonding: bond0: Warning: Found an uninitialized port
[   41.390009] bonding: bond0: Warning: Found an uninitialized port
[   41.490022] bonding: bond0: Warning: Found an uninitialized port
[   41.590011] bonding: bond0: Warning: Found an uninitialized port
[   41.690009] bonding: bond0: Warning: Found an uninitialized port
[   41.790009] bonding: bond0: Warning: Found an uninitialized port
[   41.890010] bonding: bond0: Warning: Found an uninitialized port
[   41.990019] bonding: bond0: Warning: Found an uninitialized port
[   42.090017] bonding: bond0: Warning: Found an uninitialized port
[   42.190017] bonding: bond0: Warning: Found an uninitialized port
[   42.290014] bonding: bond0: Warning: Found an uninitialized port
[   42.390635] bonding: bond0: Warning: Found an uninitialized port
[   42.490643] bonding: bond0: Warning: Found an uninitialized port
[   42.590013] bonding: bond0: Warning: Found an uninitialized port
[   42.690012] bonding: bond0: Warning: Found an uninitialized port
[   42.790014] bonding: bond0: Warning: Found an uninitialized port
[   42.890009] bonding: bond0: Warning: Found an uninitialized port
[   42.990009] bonding: bond0: Warning: Found an uninitialized port
[   43.090027] bonding: bond0: Warning: Found an uninitialized port
[   43.190012] bonding: bond0: Warning: Found an uninitialized port
[   43.290018] bonding: bond0: Warning: Found an uninitialized port
[   43.390010] bonding: bond0: Warning: Found an uninitialized port
[   43.490008] bonding: bond0: Warning: Found an uninitialized port
[   43.590008] bonding: bond0: Warning: Found an uninitialized port
[   43.690009] bonding: bond0: Warning: Found an uninitialized port
[   43.790008] bonding: bond0: Warning: Found an uninitialized port
[   43.890008] bonding: bond0: Warning: Found an uninitialized port
[   43.990011] bonding: bond0: Warning: Found an uninitialized port
[   44.090013] bonding: bond0: Warning: Found an uninitialized port
[   44.190009] bonding: bond0: Warning: Found an uninitialized port
[   44.290014] bonding: bond0: Warning: Found an uninitialized port
[   44.390010] bonding: bond0: Warning: Found an uninitialized port
[   44.490009] bonding: bond0: Warning: Found an uninitialized port
[   44.590008] bonding: bond0: Warning: Found an uninitialized port
[   44.690008] bonding: bond0: Warning: Found an uninitialized port
[   44.790008] bonding: bond0: Warning: Found an uninitialized port
[   44.890009] bonding: bond0: Warning: Found an uninitialized port
[   44.990009] bonding: bond0: Warning: Found an uninitialized port
[   45.090008] bonding: bond0: Warning: Found an uninitialized port
[   45.190011] bonding: bond0: Warning: Found an uninitialized port
[   45.290017] bonding: bond0: Warning: Found an uninitialized port
[   45.390009] bonding: bond0: Warning: Found an uninitialized port
[   45.490008] bonding: bond0: Warning: Found an uninitialized port
[   45.590009] bonding: bond0: Warning: Found an uninitialized port
[   45.690017] bonding: bond0: Warning: Found an uninitialized port
[   45.775226] bonding: bond0: Removing slave eth0
[   45.775234] bonding: bond0: Warning: the permanent HWaddr of eth0 - 00:04:23:d1:b0:12 - is still in use by bond0. Set the HWaddr of eth0 to a different address to avoid conflicts.
[   45.775239] bonding: Warning: bond0: Trying to unbind an uninitialized port on eth0
[   45.775242] bonding: bond0: releasing active interface eth0
[   45.775253] bonding: bond0: now running without any active interface !
[   45.800021] bonding: bond0: Warning: Found an uninitialized port
[   45.890013] bonding: bond0: Warning: Found an uninitialized port
[   45.975594] bonding: bond0: Removing slave eth1
[   45.975603] bonding: Warning: bond0: Trying to unbind an uninitialized port on eth1
[   45.975608] bonding: bond0: releasing active interface eth1
[   45.975614] bonding: bond0: Warning: clearing HW address of bond0 while it still has VLANs.
[   45.975618] bonding: bond0: When re-adding slaves, make sure the bond's HW address matches its VLANs'.
[   47.080323] bonding: bond0: Adding slave eth0.
[   47.125683] bonding: bond0: Warning: failed to get speed and duplex from eth0, assumed to be 100Mb/sec and Full.
[   47.125692] bonding: bond0: Warning: Operation of 802.3ad mode requires ETHTOOL support in base driver for proper aggregator selection.
[   47.125720] bonding: bond0: enslaving eth0 as a backup interface with an up link.
[   47.127812] bonding: bond0: Adding slave eth1.
[   47.175865] bonding: bond0: Warning: failed to get speed and duplex from eth1, assumed to be 100Mb/sec and Full.
[   47.175873] bonding: bond0: Warning: Operation of 802.3ad mode requires ETHTOOL support in base driver for proper aggregator selection.
[   47.175902] bonding: bond0: enslaving eth1 as a backup interface with an up link.
[   47.176074] bonding: unable to update mode of bond0 because interface is up.
[   48.840370] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   49.100371] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   57.520007] vlan32: no IPv6 routers present

```Starting at "bonding: bond0: Removing slave eth0" is when I run the network restart script.

---

### Post by layback on 2009-11-10
I'm seeing the same issue.  The bonded interface is broken on boot, but is fine when I do a /etc/init.d/networking restart.

I get heaps of these errors:

> Warning: Found an uninitialized port

And it also complains that:
> 
Warning: either miimon or arp_interval and arp_ip_target module parameters must be specified, otherwise bonding will not detect link failures! see bonding.txt for details.

even though miimon is specified in /etc/network/interfaces.  See attached /etc/network/interfaces and dmesg output for more detail.

This issue appeared after an otherwise successful dist-upgrade from jaunty.

Ideas anyone?

---

### Post by jgoris on 2009-11-10
I have experienced the same problems. One is an i386 machine that was upgraded from 9.04 server and the other is an am64 machine with a fresh install of 9.10 server. Here are the relevant lines from /etc/network/interfaces:

```
auto bond0
    iface bond0 inet static
    address 172.16.0.3
    netmask 255.255.255.248
    network 172.16.0.0
    broadcast 172.16.0.7
    mtu 9216
    slaves slave0 slave1
    bond_miimon 100
    bond_mode 802.3ad
```

After either machine boots, the bond0 interface appears to come up. I can successfully ping the bond0 interface address, but pinging any other IP address on the subnet fails. After executing[INDENT]sudo ifdown bond0
sudo ifup bond0
[/INDENT]On the affected host, it all works fine.

I had no problems with the same setup on jaunty.

---

### Post by jwindle on 2009-11-10
I have a feeling this has something to do with the switch to upstart scripts for networking in karmic (9.10).

I think it's trying to initiate the bonding interface to early in the boot process before the kernel is fully ready for it.

/etc/init/network-interface.conf or /etc/init/networking.conf probably need editing so they wait for whatever is needed so the bonding module can work properly.

That is just my hunch anyway.

---

### Post by btmspox on 2009-11-13
Is anyone using a driver other than bnx2?

---

### Post by jwindle on 2009-11-13
> Is anyone using a driver other than bnx2?

Yes my cards are Intel and using the e1000 driver.

---

### Post by btmspox on 2009-11-13
This should only be happening on bond_mode 4 (802.3ad).

Please confirm if anyone is having issues with bonding working on startup using another bond_mode.

---

### Post by btmspox on 2009-11-13
Start a bug report: [https://bugs.launchpad.net/ubuntu/+bug/482419](https://bugs.launchpad.net/ubuntu/+bug/482419)

Please chime in with any additional specifics.

---

### Post by jwindle on 2009-11-13
> Start a bug report: [https://bugs.launchpad.net/ubuntu/+bug/482419](https://bugs.launchpad.net/ubuntu/+bug/482419)

Please chime in with any additional specifics.

Thank's for getting this rolling the report looks good to me.

I think I will also try to verify for myself that mode 0 does work. I'll post my findings here.

Thanks again.

---

### Post by barthnim on 2009-11-23
Hi
Had the same error going from 8.04 to 9.10. Bond0 not starting in mode 4 with the bnx2 driver.
Found a temporary workaround until problem is resolved. By restarting the /etc/init.d/networking in /etc/rc.local. It took some time after boot before the network became fully working.

Hope that can help someone until a fix comes out.

Cheers

---

### Post by fede_rico on 2009-11-25
Hi ,

it happens me too.

I have on x64 9.10 upgrade from 9.04 (it was working) and one x64 fresh 9.10.

Changing to mode 0 resolve the issue. But who needs mode 4????

Ciao,

Federico

 

> **jgoris said:**
> I have experienced the same problems. One is an i386 machine that was upgraded from 9.04 server and the other is an am64 machine with a fresh install of 9.10 server. Here are the relevant lines from /etc/network/interfaces:

```
auto bond0
    iface bond0 inet static
    address 172.16.0.3
    netmask 255.255.255.248
    network 172.16.0.0
    broadcast 172.16.0.7
    mtu 9216
    slaves slave0 slave1
    bond_miimon 100
    bond_mode 802.3ad
```After either machine boots, the bond0 interface appears to come up. I can successfully ping the bond0 interface address, but pinging any other IP address on the subnet fails. After executing[INDENT]sudo ifdown bond0
sudo ifup bond0
[/INDENT]On the affected host, it all works fine.

I had no problems with the same setup on jaunty.

---

### Post by claudiob on 2009-12-08
Same happening to me after a release upgrade from 9.04 server to 9.10 server.

---

### Post by nutznboltz on 2010-01-28
This issue may have already been fixed in Debian Sid.

I notified Bhavani Shankar about it and he took ownership of [https://bugs.launchpad.net/ubuntu/+bug/482419](https://bugs.launchpad.net/ubuntu/+bug/482419)

---

### Post by nutznboltz on 2010-01-29
Patch can be found in the bug report now.

[https://bugs.launchpad.net/ubuntu/+bug/482419](https://bugs.launchpad.net/ubuntu/+bug/482419)

---

### Post by NullHead on 2010-01-29
Mine works fine on ubuntu 9.10.

---

### Post by nutznboltz on 2010-01-29
> **NullHead said:**
> Mine works fine on ubuntu 9.10.

Did you need the patch to get bonding to work on Karmic?

---

### Post by NullHead on 2010-01-29
Nope. Works fine without. I use an Nvidia MCP55 chip for my server. 

In reality, it has a desktop hardware base, but I use it as a server. It is really stable as far as I'm concerned too.

---

### Post by hopo on 2011-01-17
Just thought I'd tell everyone that I have the same problem in 10.04 Lucid on an x86_64 server, fresh install, all updates today (Jan 17, 2011). I made a workaround script that is called from /etc/rc.local, which basically waits a couple of minutes, takes bond0 down, waits 5 seconds and brings it up again, in that order (ifdown, sleep X, ifup).

On a sidenote, the earlier mentioned "bonding: bond0: Warning: Found an uninitialized port" message appears 1789 times, spread out neatly with one message every 100 milliseconds, on every reboot (!), and the reason that the number isn't higher, is because at that point my workaround script finally kicks in.

---

### Post by taylorc on 2011-03-15
Same story - Clean install 10.04.2 x64 server, all updates applied.

Log full of entries:

bond0: Warning: Found an uninitialized port

I followed the hotplug guidelines and here is my interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 10.0.0.2
        netmask 255.255.255.0
        gateway 10.0.0.1

auto bond0
iface bond0 inet static
        address 10.0.1.2
        netmask 255.255.255.0
        bond-slaves none
        bond-mode 802.3ad
        bond-miimon 100

auto eth1
iface eth1 inet manual
        bond-master bond0
        bond-primary eth1 eth3

auto eth3
iface eth3 inet manual
        bond-master bond0
        bond-primary eth1 eth3


What an I doing wrong??

---

### Post by rokabear on 2011-04-21
We had some issues with modes other than 1 or 5.  Some of the modes require a special switch configuration to work properly.  Try switching to 1 or 5 and see if that helps for a bit.

In mode 5 I often see it take a while after boot.  We solved this by turning off spanning tree to the switch ports the servers are connected to, then it only takes at most about 12 seconds for the switch to figure out which port has the shared mac address.

In one of the modes I had a problem where it would work for a while and then bounce to the other nic card for now reason.  This resulted in random periods of connectivity loss for 10 to 30 seconds at a time.  Once we switched to mode 1 or 5, we have not had the issue since.

I have had this work well on intel and broadcom nics.

---

### Post by bhecla on 2011-10-21
I am running 11.10 and seem to be having the same issues described by a few users here. I reboot and the output from the cat /proc/net/bonding/bond0 is showing 

bond bond0 has no active aggregator

at this point there is no network connectivity
after a quick ifdown and ifup  for the bond0 interface everything seems to work. :( has anyone had luck with this issue, I have tried putting a script in rc.local but have had no luck. Any suggestions would be awesome!

---

### Post by ventzpetkov on 2011-11-23
Same problem here in 11.10.

I found this:
[http://web.archiveorange.com/archive/v/mK9nVqUyrtxx5YdJqhyt](http://web.archiveorange.com/archive/v/mK9nVqUyrtxx5YdJqhyt)

But the solution doesn't work for me.

Eventually, I resorted to just having a sleep in /etc/rc.local and issuing a /etc/init.d/networking restart

This works well, but it's a "crappy" way to solve the problem. This really needs to be fixed. (and maybe it is already in debian ifenslave?)

---

### Post by yanaek on 2012-02-01
same problem here (Ubuntu 11.10 x86_64)

SOLVED:

[http://www.3spoken.co.uk/2010/11/how-to-do-ethernet-bonding-on-ubuntu.html](http://www.3spoken.co.uk/2010/11/how-to-do-ethernet-bonding-on-ubuntu.html)

we have to update Community HowTo for bonding

slaves setting has to be removed from 'bondX' config and this must go to 

bond-master bondX in ethX, so

```

auto eth0
iface eth0 inet manual
    bond-master bond0

auto eth1
iface eth1 inet manual
    bond-master bond0

auto bond0
iface bond0 inet static
    address ...
    bond_mode 802.3ad
    bond_miimon 100
    bond_lacp_rate 1

```

---

### Post by bLaCkMeTaLL on 2012-05-01
what about CARP?
Has anyone tried throwing ucarp into vlan & bonding? :popcorn:

---

