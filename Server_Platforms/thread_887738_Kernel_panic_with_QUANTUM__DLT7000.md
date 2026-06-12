---
title: "Kernel panic with QUANTUM  DLT7000"
date: 2008-08-12
forum: Server Platforms
---

### Post by windependence on 2008-08-12
I really want to use Ubuntu server for my new quad core VMware box but I am having stability problems I think due to the drivers for my QUANTUM  DLT7000 tape drive. It loads and works fine for a day or two and then pukes with a kernel panic referencing the megaraid device. The tape drive runs on a DELL (LSI) Perc3 SCSI controller, and it is the only device on the controller. Below is my dmesg and as you can see it is complaining about several things including the osst and st drivers for the tape drive. I have googled that and I have not found a solution. Any ideas?


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-server (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:44:47 UTC 2008 (Ubuntu 2.6.24-19.34-server)
[    0.000000] Command line: root=UUID=faf9d1a6-0177-4e08-ae65-add01620e862 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7fb0000 (usable)
[    0.000000]  BIOS-e820: 00000000d7fbe000 - 00000000d7fc0000 (usable)
[    0.000000]  BIOS-e820: 00000000d7fc0000 - 00000000d7fce000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d7fce000 - 00000000d8000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000328000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 884656) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 884670, 884672) 2 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 3309568) 3 entries of 3200 used
[    0.000000] end_pfn_map = 3309568
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F8E80 checksum 0
[    0.000000] ACPI: RSDP 000F8E80, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT D7FC0000, 0048 (r1 S M C  OEMRSDT   3000822 MSFT       97)
[    0.000000] ACPI: FACP D7FC0200, 0084 (r2 S M C  OEMFACP   3000822 MSFT       97)
[    0.000000] ACPI: DSDT D7FC0480, 4E4D (r1  H8DM8 H8DM8000        0 INTL 20051117)
[    0.000000] ACPI: FACS D7FCE000, 0040
[    0.000000] ACPI: APIC D7FC0390, 00A6 (r1 S M C  OEMAPIC   3000822 MSFT       97)
[    0.000000] ACPI: OEMB D7FCE040, 00A6 (r1 S M C  SMC_OEM   3000822 MSFT       97)
[    0.000000] ACPI: SRAT D7FC52D0, 0150 (r1 AMD    HAMMER          1 AMD         1)
[    0.000000] ACPI: EINJ D7FC5420, 0130 (r1  AMIER AMI_EINJ  3000822 MSFT       97)
[    0.000000] ACPI: BERT D7FC55B0, 0030 (r1  AMIER AMI_BERT  3000822 MSFT       97)
[    0.000000] ACPI: ERST D7FC55E0, 01B0 (r1  AMIER AMI_ERST  3000822 MSFT       97)
[    0.000000] ACPI: HEST D7FC5790, 00A8 (r1  AMIER AMI_HEST  3000822 MSFT       97)
[    0.000000] ACPI: SSDT D7FC5840, 143C (r1 S M C  POWERNOW        1 AMD         1)
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 2 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 3 -> Node 0
[    0.000000] SRAT: PXM 1 -> APIC 4 -> Node 1
[    0.000000] SRAT: PXM 1 -> APIC 5 -> Node 1
[    0.000000] SRAT: PXM 1 -> APIC 6 -> Node 1
[    0.000000] SRAT: PXM 1 -> APIC 7 -> Node 1
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] SRAT: Node 0 PXM 0 0-d8000000
[    0.000000] Entering add_active_range(0, 0, 159) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 884656) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 884670, 884672) 2 entries of 3200 used
[    0.000000] SRAT: Node 0 PXM 0 0-1a8000000
[    0.000000] Entering add_active_range(0, 0, 159) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 884656) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 884670, 884672) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1736704) 3 entries of 3200 used
[    0.000000] SRAT: Node 1 PXM 1 1a8000000-328000000
[    0.000000] Entering add_active_range(1, 1736704, 3309568) 4 entries of 3200 used
[    0.000000] NUMA: Allocated memnodemap from 16000 - 160e5
[    0.000000] NUMA: Using 27 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-00000001a8000000
[    0.000000] Bootmem setup node 1 00000001a8000000-0000000328000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  3309568
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   884656
[    0.000000]     0:   884670 ->   884672
[    0.000000]     0:  1048576 ->  1736704
[    0.000000]     1:  1736704 ->  3309568
[    0.000000] On node 0 totalpages: 1572689
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1333 pages reserved
[    0.000000]   DMA zone: 2610 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 866282 pages, LIFO batch:31
[    0.000000]   Normal zone: 9408 pages used for memmap
[    0.000000]   Normal zone: 678720 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] On node 1 totalpages: 1572864
[    0.000000]   DMA zone: 0 pages used for memmap
[    0.000000]   DMA32 zone: 0 pages used for memmap
[    0.000000]   Normal zone: 21504 pages used for memmap
[    0.000000]   Normal zone: 1551360 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x2008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] Processor #4
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] Processor #5
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] Processor #6
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] Processor #7
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000d7fb0000 - 00000000d7fbe000
[    0.000000] swsusp: Registered nosave memory region: 00000000d7fc0000 - 00000000d7fce000
[    0.000000] swsusp: Registered nosave memory region: 00000000d7fce000 - 00000000d8000000
[    0.000000] swsusp: Registered nosave memory region: 00000000d8000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec01000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fef00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fef00000 - 00000000ff700000
[    0.000000] swsusp: Registered nosave memory region: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at dc000000 (gap: d8000000:26c00000)
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 41952 bytes of per cpu data
[    0.000000] Built 2 zonelists in Zone order, mobility grouping on.  Total pages: 3098972
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=faf9d1a6-0177-4e08-ae65-add01620e862 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   73.590988] Marking TSC unstable due to TSCs unsynchronized
[   73.590990] time.c: Detected 2110.804 MHz processor.
[   73.592979] Console: colour VGA+ 80x25
[   73.592995] console [tty0] enabled
[   73.593024] Checking aperture...
[   73.593027] CPU 0: aperture @ 5730000000 size 32 MB
[   73.593028] Aperture too small (32 MB)
[   73.598020] No AGP bridge found
[   73.598039] Your BIOS doesn't leave a aperture memory hole
[   73.598040] Please enable the IOMMU option in the BIOS setup
[   73.598041] This costs you 64 MB of RAM
[   73.620356] Mapping aperture over 65536 KB of RAM @ 4000000
[   73.620360] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000
[   73.731315] Memory: 12322244k/13238272k available (2523k kernel code, 259968k reserved, 1331k data, 328k init)
[   73.731353] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=8, Nodes=2
[   73.880891] Calibrating delay using timer specific routine.. 4225.97 BogoMIPS (lpj=21129895)
[   73.880924] Security Framework initialized
[   73.880930] SELinux:  Disabled at boot.
[   73.880942] AppArmor: AppArmor initialized
[   73.880946] Failure registering capabilities with primary security module.
[   73.883623] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[   73.892095] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[   73.895956] Mount-cache hash table entries: 256
[   73.896194] Initializing cgroup subsys ns
[   73.896197] Initializing cgroup subsys cpuacct
[   73.896214] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   73.896216] CPU: L2 Cache: 512K (64 bytes/line)
[   73.896219] CPU 0/0 -> Node 0
[   73.896221] CPU: Physical Processor ID: 0
[   73.896222] CPU: Processor Core ID: 0
[   73.896243] SMP alternatives: switching to UP code
[   73.896828] Early unpacking initramfs... done
[   74.166126] ACPI: Core revision 20070126
[   74.166184] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   74.269460] Using local APIC timer interrupts.
[   74.316837] APIC timer calibration result 12564295
[   74.316839] Detected 12.564 MHz APIC timer.
[   74.316946] SMP alternatives: switching to SMP code
[   74.317459] Booting processor 1/8 APIC 0x1
[   74.327750] Initializing CPU#1
[   74.476841] Calibrating delay using timer specific routine.. 4225.63 BogoMIPS (lpj=21128180)
[   74.476847] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   74.476849] CPU: L2 Cache: 512K (64 bytes/line)
[   74.476852] CPU 1/1 -> Node 0
[   74.476853] CPU: Physical Processor ID: 0
[   74.476855] CPU: Processor Core ID: 1
[   74.477152] Quad-Core AMD Opteron(tm) Processor 2352 stepping 03
[   74.477293] SMP alternatives: switching to SMP code
[   74.477665] Booting processor 2/8 APIC 0x2
[   74.487954] Initializing CPU#2
[   74.636800] Calibrating delay using timer specific routine.. 4221.75 BogoMIPS (lpj=21108751)
[   74.636806] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   74.636808] CPU: L2 Cache: 512K (64 bytes/line)
[   74.636810] CPU 2/2 -> Node 0
[   74.636812] CPU: Physical Processor ID: 0
[   74.636813] CPU: Processor Core ID: 2
[   74.637112] Quad-Core AMD Opteron(tm) Processor 2352 stepping 03
[   74.637233] SMP alternatives: switching to SMP code
[   74.637607] Booting processor 3/8 APIC 0x3
[   74.647897] Initializing CPU#3
[   74.796758] Calibrating delay using timer specific routine.. 4221.75 BogoMIPS (lpj=21108750)
[   74.796765] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   74.796767] CPU: L2 Cache: 512K (64 bytes/line)
[   74.796769] CPU 3/3 -> Node 0
[   74.796771] CPU: Physical Processor ID: 0
[   74.796772] CPU: Processor Core ID: 3
[   74.797070] Quad-Core AMD Opteron(tm) Processor 2352 stepping 03
[   74.797220] SMP alternatives: switching to SMP code
[   74.797614] Booting processor 4/8 APIC 0x4
[   74.807900] Initializing CPU#4
[   74.956711] Calibrating delay using timer specific routine.. 4221.65 BogoMIPS (lpj=21108282)
[   74.956718] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   74.956720] CPU: L2 Cache: 512K (64 bytes/line)
[   74.956722] CPU 4/4 -> Node 1
[   74.956725] CPU: Physical Processor ID: 1
[   74.956726] CPU: Processor Core ID: 0
[   74.957030] Quad-Core AMD Opteron(tm) Processor 2352 stepping 03
[   74.957117] SMP alternatives: switching to SMP code
[   74.957488] Booting processor 5/8 APIC 0x5
[   74.967776] Initializing CPU#5
[   75.116670] Calibrating delay using timer specific routine.. 4221.65 BogoMIPS (lpj=21108265)
[   75.116677] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   75.116679] CPU: L2 Cache: 512K (64 bytes/line)
[   75.116681] CPU 5/5 -> Node 1
[   75.116683] CPU: Physical Processor ID: 1
[   75.116684] CPU: Processor Core ID: 1
[   75.116987] Quad-Core AMD Opteron(tm) Processor 2352 stepping 03
[   75.117078] SMP alternatives: switching to SMP code
[   75.117448] Booting processor 6/8 APIC 0x6
[   75.127736] Initializing CPU#6
[   75.276628] Calibrating delay using timer specific routine.. 4221.66 BogoMIPS (lpj=21108341)
[   75.276635] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   75.276637] CPU: L2 Cache: 512K (64 bytes/line)
[   75.276639] CPU 6/6 -> Node 1
[   75.276642] CPU: Physical Processor ID: 1
[   75.276643] CPU: Processor Core ID: 2
[   75.276945] Quad-Core AMD Opteron(tm) Processor 2352 stepping 03
[   75.277062] SMP alternatives: switching to SMP code
[   75.277442] Booting processor 7/8 APIC 0x7
[   75.287729] Initializing CPU#7
[   75.436587] Calibrating delay using timer specific routine.. 4221.65 BogoMIPS (lpj=21108272)
[   75.436594] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   75.436596] CPU: L2 Cache: 512K (64 bytes/line)
[   75.436598] CPU 7/7 -> Node 1
[   75.436601] CPU: Physical Processor ID: 1
[   75.436602] CPU: Processor Core ID: 3
[   75.436904] Quad-Core AMD Opteron(tm) Processor 2352 stepping 03
[   75.437004] Brought up 8 CPUs
[   75.437229] CPU0 attaching sched-domain:
[   75.437232]  domain 0: span 00000000,0000000f
[   75.437234]   groups: 00000000,00000001 00000000,00000002 00000000,00000004 00000000,00000008
[   75.437239]   domain 1: span 00000000,000000ff
[   75.437240]    groups: 00000000,0000000f 00000000,000000f0
[   75.437243] CPU1 attaching sched-domain:
[   75.437245]  domain 0: span 00000000,0000000f
[   75.437246]   groups: 00000000,00000002 00000000,00000004 00000000,00000008 00000000,00000001
[   75.437250]   domain 1: span 00000000,000000ff
[   75.437252]    groups: 00000000,0000000f 00000000,000000f0
[   75.437254] CPU2 attaching sched-domain:
[   75.437256]  domain 0: span 00000000,0000000f
[   75.437257]   groups: 00000000,00000004 00000000,00000008 00000000,00000001 00000000,00000002
[   75.437261]   domain 1: span 00000000,000000ff
[   75.437263]    groups: 00000000,0000000f 00000000,000000f0
[   75.437265] CPU3 attaching sched-domain:
[   75.437267]  domain 0: span 00000000,0000000f
[   75.437268]   groups: 00000000,00000008 00000000,00000001 00000000,00000002 00000000,00000004
[   75.437272]   domain 1: span 00000000,000000ff
[   75.437273]    groups: 00000000,0000000f 00000000,000000f0
[   75.437276] CPU4 attaching sched-domain:
[   75.437277]  domain 0: span 00000000,000000f0
[   75.437279]   groups: 00000000,00000010 00000000,00000020 00000000,00000040 00000000,00000080
[   75.437283]   domain 1: span 00000000,000000ff
[   75.437284]    groups: 00000000,000000f0 00000000,0000000f
[   75.437287] CPU5 attaching sched-domain:
[   75.437288]  domain 0: span 00000000,000000f0
[   75.437289]   groups: 00000000,00000020 00000000,00000040 00000000,00000080 00000000,00000010
[   75.437293]   domain 1: span 00000000,000000ff
[   75.437295]    groups: 00000000,000000f0 00000000,0000000f
[   75.437297] CPU6 attaching sched-domain:
[   75.437299]  domain 0: span 00000000,000000f0
[   75.437300]   groups: 00000000,00000040 00000000,00000080 00000000,00000010 00000000,00000020
[   75.437304]   domain 1: span 00000000,000000ff
[   75.437305]    groups: 00000000,000000f0 00000000,0000000f
[   75.437308] CPU7 attaching sched-domain:
[   75.437309]  domain 0: span 00000000,000000f0
[   75.437311]   groups: 00000000,00000080 00000000,00000010 00000000,00000020 00000000,00000040
[   75.437315]   domain 1: span 00000000,000000ff
[   75.437316]    groups: 00000000,000000f0 00000000,0000000f
[   75.437895] net_namespace: 120 bytes
[   75.438403] Time: 17:03:35  Date: 08/11/08
[   75.438439] NET: Registered protocol family 16
[   75.438647] ACPI: bus type pci registered
[   75.438721] PCI: Using configuration type 1
[   75.442970] ACPI: EC: Look up EC in DSDT
[   75.449565] ACPI: Interpreter enabled
[   75.449567] ACPI: (supports S0 S1 S4 S5)
[   75.449578] ACPI: Using IOAPIC for interrupt routing
[   75.458410] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   75.459622] PCI: Transparent bridge - 0000:00:06.0
[   75.460648] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   75.460898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   75.460976] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[   75.461073] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[   75.461161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[   75.461240] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR15.BR30._PRT]
[   75.461354] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR15.BR31._PRT]
[   75.470186] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *10
[   75.470392] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[   75.470581] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   75.470788] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[   75.470963] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[   75.471136] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   75.471310] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *11
[   75.471483] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *10
[   75.471666] ACPI: PCI Interrupt Link [LUB0] (IRQs 21 22 23) *14
[   75.471849] ACPI: PCI Interrupt Link [LMAD] (IRQs 20) *14
[   75.472022] ACPI: PCI Interrupt Link [LUB2] (IRQs 21 22 23) *7
[   75.472196] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *5
[   75.472369] ACPI: PCI Interrupt Link [LAZA] (IRQs 21 22 23) *0, disabled.
[   75.472552] ACPI: PCI Interrupt Link [LSMB] (IRQs 21 22 23) *11
[   75.472725] ACPI: PCI Interrupt Link [LPMU] (IRQs 21 22 23) *5
[   75.472889] ACPI: PCI Interrupt Link [LSA0] (IRQs 21 22 23) *10
[   75.473106] ACPI: PCI Interrupt Link [LSA1] (IRQs 21 22 23) *11
[   75.473306] ACPI: PCI Interrupt Link [LATA] (IRQs 21 22 23) *0, disabled.
[   75.473490] ACPI: PCI Interrupt Link [LSA2] (IRQs 21 22 23) *0, disabled.
[   75.473629] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  FF, should be F4 [20070126]
[   75.473653] Linux Plug and Play Support v0.97 (c) Adam Belay
[   75.473684] pnp: PnP ACPI init
[   75.473690] ACPI: bus type pnp registered
[   75.478166] pnp: PnP ACPI: found 15 devices
[   75.478168] ACPI: ACPI bus type pnp unregistered
[   75.478439] PCI: Using ACPI for IRQ routing
[   75.478442] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   75.526588] NET: Registered protocol family 8
[   75.526589] NET: Registered protocol family 20
[   75.526652] NetLabel: Initializing
[   75.526653] NetLabel:  domain hash size = 128
[   75.526654] NetLabel:  protocols = UNLABELED CIPSOv4
[   75.526667] NetLabel:  unlabeled traffic allowed by default
[   75.526733] PCI-DMA: Disabling AGP.
[   75.528345] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   75.528349] PCI-DMA: using GART IOMMU.
[   75.528357] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   75.530303] AppArmor: AppArmor Filesystem Enabled
[   75.566702] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   75.566705] system 00:08: ioport range 0x800-0x80f has been reserved
[   75.566708] system 00:08: ioport range 0x2000-0x207f has been reserved
[   75.566710] system 00:08: ioport range 0x2080-0x20ff has been reserved
[   75.566712] system 00:08: ioport range 0x2400-0x247f has been reserved
[   75.566714] system 00:08: ioport range 0x2480-0x24ff has been reserved
[   75.566717] system 00:08: ioport range 0x2800-0x287f has been reserved
[   75.566719] system 00:08: ioport range 0x2880-0x28ff has been reserved
[   75.566721] system 00:08: ioport range 0x2c00-0x2c7f has been reserved
[   75.566723] system 00:08: ioport range 0x2c80-0x2cff has been reserved
[   75.566728] system 00:08: iomem range 0xfe8c0000-0xfe8fffff has been reserved
[   75.566730] system 00:08: iomem range 0xfee01000-0xfeefffff has been reserved
[   75.566738] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   75.566741] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   75.566748] system 00:0c: ioport range 0x290-0x29f has been reserved
[   75.566756] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   75.566762] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   75.566764] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[   75.566767] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   75.566769] system 00:0e: iomem range 0x100000-0xd7ffffff could not be reserved
[   75.566771] system 00:0e: iomem range 0xfec00000-0xffffffff could not be reserved
[   75.567377] PCI: Bridge: 0000:00:06.0
[   75.567379]   IO window: d000-dfff
[   75.567382]   MEM window: fe900000-fe9fffff
[   75.567383]   PREFETCH window: d8000000-dfffffff
[   75.567388] PCI: Bridge: 0000:04:00.0
[   75.567389]   IO window: disabled.
[   75.567393]   MEM window: feb00000-febfffff
[   75.567400]   PREFETCH window: f0000000-f7ffffff
[   75.567405] PCI: Bridge: 0000:03:04.0
[   75.567407]   IO window: e000-efff
[   75.567411]   MEM window: fea00000-febfffff
[   75.567417]   PREFETCH window: f0000000-f7ffffff
[   75.567421] PCI: Bridge: 0000:02:00.0
[   75.567423]   IO window: e000-efff
[   75.567427]   MEM window: fea00000-febfffff
[   75.567433]   PREFETCH window: f0000000-f7ffffff
[   75.567437] PCI: Bridge: 0000:02:00.1
[   75.567438]   IO window: disabled.
[   75.567442]   MEM window: disabled.
[   75.567444]   PREFETCH window: disabled.
[   75.567448] PCI: Bridge: 0000:00:0a.0
[   75.567449]   IO window: e000-efff
[   75.567451]   MEM window: fea00000-febfffff
[   75.567453]   PREFETCH window: f0000000-fdffffff
[   75.567455] PCI: Bridge: 0000:00:0d.0
[   75.567456]   IO window: disabled.
[   75.567458]   MEM window: disabled.
[   75.567460]   PREFETCH window: disabled.
[   75.567462] PCI: Bridge: 0000:00:0e.0
[   75.567463]   IO window: disabled.
[   75.567464]   MEM window: disabled.
[   75.567466]   PREFETCH window: disabled.
[   75.567468] PCI: Bridge: 0000:00:0f.0
[   75.567469]   IO window: disabled.
[   75.567471]   MEM window: disabled.
[   75.567472]   PREFETCH window: disabled.
[   75.567481] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   75.567492] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   75.567511] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   75.567557] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   75.567564] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   75.567570] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   75.567576] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   75.567585] NET: Registered protocol family 2
[   75.576560] Time: acpi_pm clocksource has been installed.
[   75.576577] Switched to high resolution mode on CPU 0
[   75.576940] Switched to high resolution mode on CPU 1
[   75.576973] Switched to high resolution mode on CPU 6
[   75.576979] Switched to high resolution mode on CPU 4
[   75.577012] Switched to high resolution mode on CPU 7
[   75.577038] Switched to high resolution mode on CPU 3
[   75.577046] Switched to high resolution mode on CPU 5
[   75.577053] Switched to high resolution mode on CPU 2
[   75.657554] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   75.660938] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   75.664939] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   75.665401] TCP: Hash tables configured (established 524288 bind 65536)
[   75.665403] TCP reno registered
[   75.686752] checking if image is initramfs... it is
[   76.212682] Freeing initrd memory: 7333k freed
[   76.219283] audit: initializing netlink socket (disabled)
[   76.219303] audit(1218474216.600:1): initialized
[   76.220575] Total HugeTLB memory allocated, 0
[   76.223027] VFS: Disk quotas dquot_6.5.1
[   76.223104] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   76.223315] io scheduler noop registered
[   76.223317] io scheduler anticipatory registered
[   76.223319] io scheduler deadline registered (default)
[   76.223435] io scheduler cfq registered
[   76.223493] pci 0000:00:00.0: Enabling HT MSI Mapping
[   76.250818] pci 0000:00:05.0: Enabling HT MSI Mapping
[   76.250855] pci 0000:00:05.1: Enabling HT MSI Mapping
[   76.250883] pci 0000:00:06.0: Enabling HT MSI Mapping
[   76.250913] pci 0000:00:08.0: Enabling HT MSI Mapping
[   76.250942] pci 0000:00:09.0: Enabling HT MSI Mapping
[   76.250971] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   76.251001] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   76.251031] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   76.251061] pci 0000:00:0f.0: Enabling HT MSI Mapping
[   76.251074] Boot video device is 0000:01:05.0
[   76.251309] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   76.251334] assign_interrupt_mode Found MSI capability
[   76.251357] Allocate Port Service[0000:00:0a.0:pcie00]
[   76.251441] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   76.251463] assign_interrupt_mode Found MSI capability
[   76.251503] Allocate Port Service[0000:00:0d.0:pcie00]
[   76.251594] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   76.251616] assign_interrupt_mode Found MSI capability
[   76.251656] Allocate Port Service[0000:00:0e.0:pcie00]
[   76.251741] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   76.251762] assign_interrupt_mode Found MSI capability
[   76.251802] Allocate Port Service[0000:00:0f.0:pcie00]
[   76.279492] Real Time Clock Driver v1.12ac
[   76.279613] Linux agpgart interface v0.102
[   76.279616] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   76.279759] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   76.279901] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   76.280404] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   76.280658] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   76.281764] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   76.281834] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   76.281930] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   76.284151] serio: i8042 KBD port at 0x60,0x64 irq 1
[   76.284162] serio: i8042 AUX port at 0x60,0x64 irq 12
[   76.320854] mice: PS/2 mouse device common for all mice
[   76.320918] cpuidle: using governor ladder
[   76.320919] cpuidle: using governor menu
[   76.321109] NET: Registered protocol family 1
[   76.321255] registered taskstats version 1
[   76.321433]   Magic number: 4:155:87
[   76.321537]   hash matches device LNXPWRBN:00
[   76.321541] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   76.321544] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   76.321899] Freeing unused kernel memory: 328k freed
[   76.341831] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   76.466060] fuse init (API version 7.9)
[   76.638925] SCSI subsystem initialized
[   76.643426] libata version 3.00 loaded.
[   76.648316] usbcore: registered new interface driver usbfs
[   76.648335] usbcore: registered new interface driver hub
[   76.655548] sata_nv 0000:00:05.0: version 3.5
[   76.655852] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[   76.655860] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LSA0] -> GSI 23 (level, low) -> IRQ 23
[   76.656603] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   76.657105] usbcore: registered new device driver usb
[   76.657128] scsi0 : sata_nv
[   76.657180] scsi1 : sata_nv
[   76.657320] ata1: SATA max UDMA/133 cmd 0xc480 ctl 0xc400 bmdma 0xbc00 irq 23
[   76.657322] ata2: SATA max UDMA/133 cmd 0xc080 ctl 0xc000 bmdma 0xbc08 irq 23
[   76.658384] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   76.715110] Floppy drive(s): fd0 is 1.44M
[   76.720811] megaraid cmm: 2.20.2.7 (Release Date: Sun Jul 16 00:01:03 EST 2006)
[   76.722009] megaraid: 2.20.5.1 (Release Date: Thu Nov 16 15:32:35 EST 2006)
[   76.731435] FDC 0 is a post-1991 82077
[   77.146174] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   77.166481] ata1.00: ATA-8: WDC WD5000AAKS-00A7B0, 01.03B01, max UDMA/133
[   77.166487] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (not used)
[   77.211543] ata1.00: configured for UDMA/133
[   77.696025] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   77.716743] ata2.00: ATA-8: WDC WD5000AAKS-00A7B0, 01.03B01, max UDMA/133
[   77.716746] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (not used)
[   77.740780] ata2.00: configured for UDMA/133
[   77.740923] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
[   77.741029] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
[   77.741405] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[   77.741412] ACPI: PCI Interrupt 0000:00:05.1[B] -> Link [LSA1] -> GSI 22 (level, low) -> IRQ 22
[   77.742240] PCI: Setting latency timer of device 0000:00:05.1 to 64
[   77.742325] scsi2 : sata_nv
[   77.742389] scsi3 : sata_nv
[   77.742528] ata3: SATA max UDMA/133 cmd 0xb880 ctl 0xb800 bmdma 0xb080 irq 22
[   77.742530] ata4: SATA max UDMA/133 cmd 0xb480 ctl 0xb400 bmdma 0xb088 irq 22
[   78.225894] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   78.247053] ata3.00: ATA-8: WDC WD5000AAKS-00A7B0, 01.03B01, max UDMA/133
[   78.247058] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (not used)
[   78.271052] ata3.00: configured for UDMA/133
[   78.755747] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   78.945800] ata4.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L08, max UDMA/100
[   79.135781] ata4.00: configured for UDMA/100
[   79.135878] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
[   79.137114] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L08 PQ: 0 ANSI: 5
[   79.137553] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[   79.137560] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 21 (level, low) -> IRQ 21
[   79.138196] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   79.138203] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   79.138488] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   79.138508] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe8bf000
[   79.197736] usb usb1: configuration #1 chosen from 1 choice
[   79.197757] hub 1-0:1.0: USB hub found
[   79.197765] hub 1-0:1.0: 10 ports detected
[   79.315896] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   79.316206] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   79.316213] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 20
[   79.316218] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   79.316728] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 2, addr 00:30:48:c0:35:1c
[   79.316731] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   79.317011] ACPI: PCI Interrupt Link [LMAD] enabled at IRQ 20
[   79.317013] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LMAD] -> GSI 20 (level, low) -> IRQ 20
[   79.317017] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   79.317514] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 3, addr 00:30:48:c0:35:1d
[   79.317516] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   79.318001] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[   79.318008] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 23 (level, low) -> IRQ 23
[   79.318655] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   79.318664] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   79.318734] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   79.318768] ehci_hcd 0000:00:02.1: debug port 1
[   79.318772] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   79.318781] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfe8bec00
[   79.339330] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   79.339441] usb usb2: configuration #1 chosen from 1 choice
[   79.339471] hub 2-0:1.0: USB hub found
[   79.339478] hub 2-0:1.0: 10 ports detected
[   79.445654] qla1280: Skipping AMI SubSys Vendor ID Chip
[   79.445729] megaraid: probe new device 0x101e:0x1960:0x1028:0x0493: bus 5:slot 0:func 0
[   79.446087] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 19
[   79.446097] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LNEC] -> GSI 19 (level, low) -> IRQ 19
[   79.585559] megaraid: fw version:[1.74] bios version:[3.27]
[   79.685650] scsi4 : LSI Logic MegaRAID driver
[   79.685905] scsi[4]: scanning scsi channel 0 [Phy 0] for non-raid devices
[   79.694867] Driver 'sd' needs updating - please use bus_type methods
[   79.694968] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   79.694978] sd 0:0:0:0: [sda] Write Protect is off
[   79.694980] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   79.694991] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.695043] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   79.695053] sd 0:0:0:0: [sda] Write Protect is off
[   79.695055] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   79.695068] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.695071]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   79.698911]  sda2 < sda5 sda6 sda7 sda8 >
[   79.725082] sd 0:0:0:0: [sda] Attached SCSI disk
[   79.725128] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   79.725137] sd 1:0:0:0: [sdb] Write Protect is off
[   79.725139] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   79.725150] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.725182] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   79.725191] sd 1:0:0:0: [sdb] Write Protect is off
[   79.725193] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   79.725203] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.725210]  sdb: sdb1
[   79.729204] sd 1:0:0:0: [sdb] Attached SCSI disk
[   79.729238] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   79.729244] sd 2:0:0:0: [sdc] Write Protect is off
[   79.729246] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   79.729256] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.729279] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   79.729285] sd 2:0:0:0: [sdc] Write Protect is off
[   79.729287] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   79.729297] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   79.729300]  sdc: sdc1
[   79.736769] sd 2:0:0:0: [sdc] Attached SCSI disk
[   79.740133] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   79.740157] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   79.740176] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   79.740194] sr 3:0:0:0: Attached scsi generic sg3 type 5
[   79.744945] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   79.744948] Uniform CD-ROM driver Revision: 3.20
[   79.744980] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   80.226572] Attempting manual resume
[   80.226575] swsusp: Resume From Partition 8:5
[   80.226577] PM: Checking swsusp image.
[   80.226760] PM: Resume from disk failed.
[   80.236141] EXT3-fs: INFO: recovery required on readonly filesystem.
[   80.236143] EXT3-fs: write access will be enabled during recovery.
[   80.562456] kjournald starting.  Commit interval 5 seconds
[   80.562472] EXT3-fs: sda6: orphan cleanup on readonly fs
[   80.573636] ext3_orphan_cleanup: deleting unreferenced inode 1060810
[   80.598849] ext3_orphan_cleanup: deleting unreferenced inode 1060809
[   80.624169] ext3_orphan_cleanup: deleting unreferenced inode 973363
[   80.624176] EXT3-fs: sda6: 3 orphan inodes deleted
[   80.624177] EXT3-fs: recovery complete.
[   80.627280] EXT3-fs: mounted filesystem with ordered data mode.
[   82.116435] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   82.275132] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2d00
[   82.275148] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2e00
[   82.310693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   82.312521] shpchp: Unknown symbol acpi_run_oshp
[   82.312576] shpchp: Unknown symbol pci_hp_change_slot_info
[   82.312641] shpchp: Unknown symbol pci_hp_register
[   82.312801] shpchp: Unknown symbol pci_hp_deregister
[   82.312928] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   82.327706] input: Power Button (FF) as /devices/virtual/input/input3
[   82.349501] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   82.686022] ACPI: Power Button (FF) [PWRF]
[   82.686113] input: Power Button (CM) as /devices/virtual/input/input4
[   82.845942] ACPI: Power Button (CM) [PWRB]
[   83.366355] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   84.479627] NET: Registered protocol family 17
[   84.624935] loop: module loaded
[   84.662298] lp: driver loaded but no devices found
[   84.874304] Adding 19800072k swap on /dev/sda5.  Priority:-1 extents:1 across:19800072k
[   85.188277] EXT3 FS on sda6, internal journal
[   85.194045] megaraid: aborting-1 cmd=12 <c=0 t=0 l=0>
[   85.194050] megaraid abort: 1:0[0:0], fw owner
[   85.194060] megaraid: 1 outstanding commands. Max wait 300 sec
[   85.194064] megaraid mbox: Wait for 1 commands to complete:300
[   86.291977] NET: Registered protocol family 10
[   86.292241] lo: Disabled Privacy Extensions
[   88.156427] kjournald starting.  Commit interval 5 seconds
[   88.156696] EXT3 FS on sda8, internal journal
[   88.156703] EXT3-fs: mounted filesystem with ordered data mode.
[   88.184805] kjournald starting.  Commit interval 5 seconds
[   88.185041] EXT3 FS on sda7, internal journal
[   88.185046] EXT3-fs: mounted filesystem with ordered data mode.
[   88.203461] kjournald starting.  Commit interval 5 seconds
[   88.203739] EXT3 FS on sdb1, internal journal
[   88.203743] EXT3-fs: mounted filesystem with ordered data mode.
[   88.208594] kjournald starting.  Commit interval 5 seconds
[   88.208877] EXT3 FS on sdc1, internal journal
[   88.208880] EXT3-fs: mounted filesystem with ordered data mode.
[   88.614099] ip_tables: (C) 2000-2006 Netfilter Core Team
[   90.012421] vmmon: module license 'unspecified' taints kernel.
[   90.013487] /dev/vmmon[5121]: Module vmmon: registered with major=10 minor=165
[   90.013502] /dev/vmmon[5121]: Module vmmon: initialized
[   90.232722] megaraid mbox: Wait for 1 commands to complete:295
[   90.375850] /dev/vmnet: open called by PID 5162 (vmnet-bridge)
[   90.375861] /dev/vmnet: hub 0 does not exist, allocating memory.
[   90.375871] /dev/vmnet: port on hub 0 successfully opened
[   90.375885] bridge-eth0: enabling the bridge
[   90.375890] bridge-eth0: up
[   90.375893] bridge-eth0: already up
[   90.375895] bridge-eth0: attached
[   90.384874] /dev/vmnet: open called by PID 5172 (vmnet-bridge)
[   90.384888] /dev/vmnet: hub 2 does not exist, allocating memory.
[   90.384899] /dev/vmnet: port on hub 2 successfully opened
[   90.384918] bridge-eth1: peer interface eth1 not found, will wait for it to come up
[   90.384922] bridge-eth1: attached
[   90.426042] /dev/vmnet: open called by PID 5181 (vmnet-natd)
[   90.426056] /dev/vmnet: hub 8 does not exist, allocating memory.
[   90.426067] /dev/vmnet: port on hub 8 successfully opened
[   95.281390] megaraid mbox: Wait for 1 commands to complete:290
[   96.471066] eth0: no IPv6 routers present
[  100.330061] megaraid mbox: Wait for 1 commands to complete:285
[  105.378732] megaraid mbox: Wait for 1 commands to complete:280
[  110.427403] megaraid mbox: Wait for 1 commands to complete:275
[  115.476074] megaraid mbox: Wait for 1 commands to complete:270
[  120.524746] megaraid mbox: Wait for 1 commands to complete:265
[  125.573418] megaraid mbox: Wait for 1 commands to complete:260
[  130.622089] megaraid mbox: Wait for 1 commands to complete:255
[  135.670755] megaraid mbox: Wait for 1 commands to complete:250
[  140.719431] megaraid mbox: Wait for 1 commands to complete:245
[  145.768100] megaraid mbox: Wait for 1 commands to complete:240
[  150.816774] megaraid mbox: Wait for 1 commands to complete:235
[  155.865448] megaraid mbox: Wait for 1 commands to complete:230
[  160.914116] megaraid mbox: Wait for 1 commands to complete:225
[  165.962788] megaraid mbox: Wait for 1 commands to complete:220
[  171.011459] megaraid mbox: Wait for 1 commands to complete:215
[  176.060127] megaraid mbox: Wait for 1 commands to complete:210
[  181.108798] megaraid mbox: Wait for 1 commands to complete:205
[  186.157469] megaraid mbox: Wait for 1 commands to complete:200
[  191.206140] megaraid mbox: Wait for 1 commands to complete:195
[  196.254811] megaraid mbox: Wait for 1 commands to complete:190
[  201.303477] megaraid mbox: Wait for 1 commands to complete:185
[  206.352148] megaraid mbox: Wait for 1 commands to complete:180
[  211.400821] megaraid mbox: Wait for 1 commands to complete:175
[  216.449491] megaraid mbox: Wait for 1 commands to complete:170
[  221.498162] megaraid mbox: Wait for 1 commands to complete:165
[  226.546834] megaraid mbox: Wait for 1 commands to complete:160
[  231.595511] megaraid mbox: Wait for 1 commands to complete:155
[  236.644171] megaraid mbox: Wait for 1 commands to complete:150
[  241.692847] megaraid mbox: Wait for 1 commands to complete:145
[  246.741514] megaraid mbox: Wait for 1 commands to complete:140
[  251.790191] megaraid mbox: Wait for 1 commands to complete:135
[  256.838856] megaraid mbox: Wait for 1 commands to complete:130
[  261.887527] megaraid mbox: Wait for 1 commands to complete:125
[  266.936199] megaraid mbox: Wait for 1 commands to complete:120
[  271.984870] megaraid mbox: Wait for 1 commands to complete:115
[  277.033537] megaraid mbox: Wait for 1 commands to complete:110
[  282.082208] megaraid mbox: Wait for 1 commands to complete:105
[  287.130879] megaraid mbox: Wait for 1 commands to complete:100
[  292.179551] megaraid mbox: Wait for 1 commands to complete:95
[  297.228222] megaraid mbox: Wait for 1 commands to complete:90
[  302.276893] megaraid mbox: Wait for 1 commands to complete:85
[  307.325565] megaraid mbox: Wait for 1 commands to complete:80
[  312.374236] megaraid mbox: Wait for 1 commands to complete:75
[  317.422907] megaraid mbox: Wait for 1 commands to complete:70
[  322.471579] megaraid mbox: Wait for 1 commands to complete:65
[  327.520251] megaraid mbox: Wait for 1 commands to complete:60
[  332.568916] megaraid mbox: Wait for 1 commands to complete:55
[  337.617588] megaraid mbox: Wait for 1 commands to complete:50
[  342.666264] megaraid mbox: Wait for 1 commands to complete:45
[  347.714929] megaraid mbox: Wait for 1 commands to complete:40
[  352.763607] megaraid mbox: Wait for 1 commands to complete:35
[  357.812269] megaraid mbox: Wait for 1 commands to complete:30
[  362.860949] megaraid mbox: Wait for 1 commands to complete:25
[  367.909615] megaraid mbox: Wait for 1 commands to complete:20
[  372.958287] megaraid mbox: Wait for 1 commands to complete:15
[  378.006953] megaraid mbox: Wait for 1 commands to complete:10
[  383.055625] megaraid mbox: Wait for 1 commands to complete:5
[  388.104295] megaraid mbox: critical hardware error!
[  388.104305] megaraid: hw error, cannot reset
[  388.104306] megaraid: hw error, cannot reset
[  388.104310] scsi 4:0:0:0: Device offlined - not ready after error recovery
[  393.602849] megaraid: aborting-2 cmd=12 <c=0 t=1 l=0>
[  393.602853] megaraid: hw error, not aborting
[  393.602856] megaraid: hw error, cannot reset
[  393.602857] megaraid: hw error, cannot reset
[  393.602859] megaraid: hw error, cannot reset
[  393.602860] scsi 4:0:1:0: Device offlined - not ready after error recovery
[  399.101402] megaraid: aborting-3 cmd=12 <c=0 t=2 l=0>
[  399.101406] megaraid: hw error, not aborting
[  399.101408] megaraid: hw error, cannot reset
[  399.101409] megaraid: hw error, cannot reset
[  399.101410] megaraid: hw error, cannot reset
[  399.101412] scsi 4:0:2:0: Device offlined - not ready after error recovery
[  404.599953] megaraid: aborting-4 cmd=12 <c=0 t=3 l=0>
[  404.599957] megaraid: hw error, not aborting
[  404.599958] megaraid: hw error, cannot reset
[  404.599960] megaraid: hw error, cannot reset
[  404.599961] megaraid: hw error, cannot reset
[  404.599962] scsi 4:0:3:0: Device offlined - not ready after error recovery
[  410.098504] megaraid: aborting-5 cmd=12 <c=0 t=4 l=0>
[  410.098508] megaraid: hw error, not aborting
[  410.098510] megaraid: hw error, cannot reset
[  410.098511] megaraid: hw error, cannot reset
[  410.098512] megaraid: hw error, cannot reset
[  410.098514] scsi 4:0:4:0: Device offlined - not ready after error recovery
[  415.597058] megaraid: aborting-6 cmd=12 <c=0 t=5 l=0>
[  415.597062] megaraid: hw error, not aborting
[  415.597064] megaraid: hw error, cannot reset
[  415.597065] megaraid: hw error, cannot reset
[  415.597068] megaraid: hw error, cannot reset
[  415.597070] scsi 4:0:5:0: Device offlined - not ready after error recovery
[  421.095609] megaraid: aborting-7 cmd=12 <c=0 t=6 l=0>
[  421.095613] megaraid: hw error, not aborting
[  421.095615] megaraid: hw error, cannot reset
[  421.095616] megaraid: hw error, cannot reset
[  421.095617] megaraid: hw error, cannot reset
[  421.095619] scsi 4:0:6:0: Device offlined - not ready after error recovery
[  426.594162] megaraid: aborting-8 cmd=12 <c=0 t=8 l=0>
[  426.594165] megaraid: hw error, not aborting
[  426.594167] megaraid: hw error, cannot reset
[  426.594168] megaraid: hw error, cannot reset
[  426.594169] megaraid: hw error, cannot reset
[  426.594171] scsi 4:0:8:0: Device offlined - not ready after error recovery
[  432.092714] megaraid: aborting-9 cmd=12 <c=0 t=9 l=0>
[  432.092718] megaraid: hw error, not aborting
[  432.092719] megaraid: hw error, cannot reset
[  432.092721] megaraid: hw error, cannot reset
[  432.092722] megaraid: hw error, cannot reset
[  432.092723] scsi 4:0:9:0: Device offlined - not ready after error recovery
[  437.591267] megaraid: aborting-10 cmd=12 <c=0 t=10 l=0>
[  437.591271] megaraid: hw error, not aborting
[  437.591272] megaraid: hw error, cannot reset
[  437.591274] megaraid: hw error, cannot reset
[  437.591275] megaraid: hw error, cannot reset
[  437.591276] scsi 4:0:10:0: Device offlined - not ready after error recovery
[  443.089819] megaraid: aborting-11 cmd=12 <c=0 t=11 l=0>
[  443.089823] megaraid: hw error, not aborting
[  443.089824] megaraid: hw error, cannot reset
[  443.089826] megaraid: hw error, cannot reset
[  443.089827] megaraid: hw error, cannot reset
[  443.089829] scsi 4:0:11:0: Device offlined - not ready after error recovery
[  448.588373] megaraid: aborting-12 cmd=12 <c=0 t=12 l=0>
[  448.588377] megaraid: hw error, not aborting
[  448.588380] megaraid: hw error, cannot reset
[  448.588382] megaraid: hw error, cannot reset
[  448.588383] megaraid: hw error, cannot reset
[  448.588385] scsi 4:0:12:0: Device offlined - not ready after error recovery
[  454.086926] megaraid: aborting-13 cmd=12 <c=0 t=13 l=0>
[  454.086930] megaraid: hw error, not aborting
[  454.086932] megaraid: hw error, cannot reset
[  454.086933] megaraid: hw error, cannot reset
[  454.086934] megaraid: hw error, cannot reset
[  454.086936] scsi 4:0:13:0: Device offlined - not ready after error recovery
[  459.585476] megaraid: aborting-14 cmd=12 <c=0 t=14 l=0>
[  459.585480] megaraid: hw error, not aborting
[  459.585482] megaraid: hw error, cannot reset
[  459.585483] megaraid: hw error, cannot reset
[  459.585484] megaraid: hw error, cannot reset
[  459.585486] scsi 4:0:14:0: Device offlined - not ready after error recovery
[  465.084028] megaraid: aborting-15 cmd=12 <c=0 t=15 l=0>
[  465.084032] megaraid: hw error, not aborting
[  465.084034] megaraid: hw error, cannot reset
[  465.084035] megaraid: hw error, cannot reset
[  465.084037] megaraid: hw error, cannot reset
[  465.084038] scsi 4:0:15:0: Device offlined - not ready after error recovery
[  465.084964] scsi[4]: scanning scsi channel 1 [Phy 1] for non-raid devices
[  466.394560] scsi 4:1:5:0: Sequential-Access QUANTUM  DLT7000          2150 PQ: 0 ANSI: 2
[  468.730278] scsi[4]: scanning scsi channel 2 [virtual] for logical drives
[  469.014968] scsi 4:1:5:0: Attached scsi generic sg4 type 1
[  469.079057] osst :I: Tape driver with OnStream support version 0.99.4
[  469.079059] osst :I: $Id: osst.c,v 1.73 2005/01/01 21:13:34 wriede Exp $
[  469.079078] Driver 'osst' needs updating - please use bus_type methods
[  469.093414] st: Version 20070203, fixed bufsize 32768, s/g segs 256
[  469.093428] Driver 'st' needs updating - please use bus_type methods
[  469.093555] st 4:1:5:0: Attached scsi tape st0
[  469.093557] st 4:1:5:0: st0: try direct i/o: yes (alignment 512 B)
[  469.132917] st0: Block limits 2 - 16777214 bytes.
root@jefe:~# 
```

Thanks,

-Tim

---

### Post by windependence on 2008-08-12
Bump. Hey I know this is a tough one. :)

-Tim

---

