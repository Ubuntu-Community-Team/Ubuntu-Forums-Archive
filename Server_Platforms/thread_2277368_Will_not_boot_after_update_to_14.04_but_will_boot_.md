---
title: "Will not boot after update to 14.04 but will boot recovery"
date: 2015-05-08
forum: Server Platforms
---

### Post by bigmonmulgrew on 2015-05-08
So today I decided to take the plunge and upgrade to the next LTS. I've been putting it off for far too long. Oh how I wish I had not gone ahead.

I've had a host of issues. One of which was apaches site files requiring .conf at the end now. Got that sorted
My server will now no longer boot. I'll try and get a screen grab of the exact error message. 

But I'm also noticing some other error messages that fly past too fast to see. One is with vsftp and fail2ban.

I can get the server to boot if I launch recovery mode and then immediately select resume normal boot.

The server is running a Raid 1. 

So heres some of the recent logs with the failed reboots

```
May  8 15:09:40 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpuset
May  8 15:09:40 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpu
May  8 15:09:40 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpuacct
May  8 15:09:40 MEwebServer kernel: [    0.000000] Linux version 3.13.0-52-generic (buildd@comet) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #86-Ubuntu SMP Mon May 4 04:32:59 UTC 2015 (Ubuntu 3.13.0-52.86-generic 3.13.11-ckt18)
May  8 15:09:40 MEwebServer kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic root=UUID=bf21290d-7a02-4713-aaad-c45f755eec04 ro recovery nomodeset
May  8 15:09:40 MEwebServer kernel: [    0.000000] KERNEL supported cpus:
May  8 15:09:40 MEwebServer kernel: [    0.000000]   Intel GenuineIntel
May  8 15:09:40 MEwebServer kernel: [    0.000000]   AMD AuthenticAMD
May  8 15:09:40 MEwebServer kernel: [    0.000000]   Centaur CentaurHauls
May  8 15:09:40 MEwebServer kernel: [    0.000000] e820: BIOS-provided physical RAM map:
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000ddfeffff] usable
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000ddff0000-0x00000000ddff2fff] ACPI NVS
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000ddff3000-0x00000000ddffffff] ACPI data
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000de000000-0x00000000dfffffff] reserved
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
May  8 15:09:40 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
May  8 15:09:40 MEwebServer kernel: [    0.000000] NX (Execute Disable) protection: active
May  8 15:09:40 MEwebServer kernel: [    0.000000] SMBIOS 2.4 present.
May  8 15:09:40 MEwebServer kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. M61PME-S2P/M61PME-S2P, BIOS F2 12/30/2008
May  8 15:09:40 MEwebServer kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
May  8 15:09:40 MEwebServer kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
May  8 15:09:40 MEwebServer kernel: [    0.000000] No AGP bridge found
May  8 15:09:40 MEwebServer kernel: [    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x400000000
May  8 15:09:40 MEwebServer kernel: [    0.000000] MTRR default type: uncachable
May  8 15:09:40 MEwebServer kernel: [    0.000000] MTRR fixed ranges enabled:
May  8 15:09:40 MEwebServer kernel: [    0.000000]   00000-9FFFF write-back
May  8 15:09:40 MEwebServer kernel: [    0.000000]   A0000-BFFFF uncachable
May  8 15:09:40 MEwebServer kernel: [    0.000000]   C0000-C7FFF write-protect
May  8 15:09:40 MEwebServer kernel: [    0.000000]   C8000-EFFFF uncachable
May  8 15:09:40 MEwebServer kernel: [    0.000000]   F0000-FFFFF write-through
May  8 15:09:40 MEwebServer kernel: [    0.000000] MTRR variable ranges enabled:
May  8 15:09:40 MEwebServer kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
May  8 15:09:40 MEwebServer kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
May  8 15:09:40 MEwebServer kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
May  8 15:09:40 MEwebServer kernel: [    0.000000]   3 base 0000DE000000 mask FFFFFE000000 uncachable
May  8 15:09:40 MEwebServer kernel: [    0.000000]   4 base 000100000000 mask FFFFE0000000 write-back
May  8 15:09:40 MEwebServer kernel: [    0.000000]   5 disabled
May  8 15:09:40 MEwebServer kernel: [    0.000000]   6 disabled
May  8 15:09:40 MEwebServer kernel: [    0.000000]   7 disabled
May  8 15:09:40 MEwebServer kernel: [    0.000000] TOM2: 0000000120000000 aka 4608M
May  8 15:09:40 MEwebServer kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  8 15:09:40 MEwebServer kernel: [    0.000000] original variable MTRRs
May  8 15:09:40 MEwebServer kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
May  8 15:09:40 MEwebServer kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
May  8 15:09:40 MEwebServer kernel: [    0.000000] reg 2, base: 3GB, range: 512MB, type WB
May  8 15:09:40 MEwebServer kernel: [    0.000000] reg 3, base: 3552MB, range: 32MB, type UC
May  8 15:09:40 MEwebServer kernel: [    0.000000] reg 4, base: 4GB, range: 512MB, type WB
May  8 15:09:40 MEwebServer kernel: [    0.000000] total RAM covered: 3552M
May  8 15:09:40 MEwebServer kernel: [    0.000000] Found optimal setting for mtrr clean up
May  8 15:09:40 MEwebServer kernel: [    0.000000]  gran_size: 64K 	chunk_size: 1G 	num_reg: 3  	lose cover RAM: 0G
May  8 15:09:40 MEwebServer kernel: [    0.000000] New variable MTRRs
May  8 15:09:40 MEwebServer kernel: [    0.000000] reg 0, base: 0GB, range: 4GB, type WB
May  8 15:09:40 MEwebServer kernel: [    0.000000] reg 1, base: 3552MB, range: 32MB, type UC
May  8 15:09:40 MEwebServer kernel: [    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
May  8 15:09:40 MEwebServer kernel: [    0.000000] e820: update [mem 0xde000000-0xffffffff] usable ==> reserved
May  8 15:09:40 MEwebServer kernel: [    0.000000] e820: last_pfn = 0xddff0 max_arch_pfn = 0x400000000
May  8 15:09:40 MEwebServer kernel: [    0.000000] found SMP MP-table at [mem 0x000f4a90-0x000f4a9f] mapped at [ffff8800000f4a90]
May  8 15:09:40 MEwebServer kernel: [    0.000000] Scanning 1 areas for low memory corruption
May  8 15:09:40 MEwebServer kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
May  8 15:09:40 MEwebServer kernel: [    0.000000] Using GB pages for direct mapping
May  8 15:09:40 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
May  8 15:09:40 MEwebServer kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
May  8 15:09:40 MEwebServer kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
May  8 15:09:40 MEwebServer kernel: [    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
May  8 15:09:40 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x11fe00000-0x11fffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0x11fe00000-0x11fffffff] page 2M
May  8 15:09:40 MEwebServer kernel: [    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
May  8 15:09:40 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x11c000000-0x11fdfffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0x11c000000-0x11fdfffff] page 2M
May  8 15:09:40 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11bffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0x100000000-0x11bffffff] page 2M
May  8 15:09:40 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xddfeffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0xc0000000-0xdddfffff] page 2M
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [mem 0xdde00000-0xddfeffff] page 4k
May  8 15:09:40 MEwebServer kernel: [    0.000000] RAMDISK: [mem 0x35a4c000-0x36d1dfff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: RSDP 00000000000f6460 000014 (v00 GBT   )
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: RSDT 00000000ddff3000 000038 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: FACP 00000000ddff3040 000074 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: DSDT 00000000ddff30c0 0043ED (v01 GBT    NVDAACPI 00001000 MSFT 03000000)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: FACS 00000000ddff0000 000040
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: SSDT 00000000ddff7580 00095E (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: HPET 00000000ddff7f00 000038 (v01 GBT    NVDAACPI 42302E31 NVDA 00000098)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: MCFG 00000000ddff7f40 00003C (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: APIC 00000000ddff74c0 000098 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  8 15:09:40 MEwebServer kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
May  8 15:09:40 MEwebServer kernel: [    0.000000] No NUMA configuration found
May  8 15:09:40 MEwebServer kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011fffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x11fffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]   NODE_DATA [mem 0x11fff9000-0x11fffdfff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011b600000-ffff88011f5fffff] on node 0
May  8 15:09:40 MEwebServer kernel: [    0.000000] Zone ranges:
May  8 15:09:40 MEwebServer kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]   Normal   [mem 0x100000000-0x11fffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] Movable zone start for each node
May  8 15:09:40 MEwebServer kernel: [    0.000000] Early memory node ranges
May  8 15:09:40 MEwebServer kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009efff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]   node   0: [mem 0x00100000-0xddfeffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000]   node   0: [mem 0x100000000-0x11fffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] On node 0 totalpages: 1040270
May  8 15:09:40 MEwebServer kernel: [    0.000000]   DMA zone: 64 pages used for memmap
May  8 15:09:40 MEwebServer kernel: [    0.000000]   DMA zone: 21 pages reserved
May  8 15:09:40 MEwebServer kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
May  8 15:09:40 MEwebServer kernel: [    0.000000]   DMA32 zone: 14144 pages used for memmap
May  8 15:09:40 MEwebServer kernel: [    0.000000]   DMA32 zone: 905200 pages, LIFO batch:31
May  8 15:09:40 MEwebServer kernel: [    0.000000]   Normal zone: 2048 pages used for memmap
May  8 15:09:40 MEwebServer kernel: [    0.000000]   Normal zone: 131072 pages, LIFO batch:31
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  8 15:09:40 MEwebServer kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: IRQ0 used by override.
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: IRQ2 used by override.
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: IRQ9 used by override.
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: IRQ14 used by override.
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: IRQ15 used by override.
May  8 15:09:40 MEwebServer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  8 15:09:40 MEwebServer kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
May  8 15:09:40 MEwebServer kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
May  8 15:09:40 MEwebServer kernel: [    0.000000] nr_irqs_gsi: 40
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xddff0000-0xddff2fff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xddff3000-0xddffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xde000000-0xdfffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] e820: [mem 0xe0000000-0xefffffff] available for PCI devices
May  8 15:09:40 MEwebServer kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  8 15:09:40 MEwebServer kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
May  8 15:09:40 MEwebServer kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88011fc00000 s81536 r8192 d20864 u524288
May  8 15:09:40 MEwebServer kernel: [    0.000000] pcpu-alloc: s81536 r8192 d20864 u524288 alloc=1*2097152
May  8 15:09:40 MEwebServer kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
May  8 15:09:40 MEwebServer kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1023993
May  8 15:09:40 MEwebServer kernel: [    0.000000] Policy zone: Normal
May  8 15:09:40 MEwebServer kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic root=UUID=bf21290d-7a02-4713-aaad-c45f755eec04 ro recovery nomodeset
May  8 15:09:40 MEwebServer kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.000000] Checking aperture...
May  8 15:09:40 MEwebServer kernel: [    0.000000] No AGP bridge found
May  8 15:09:40 MEwebServer kernel: [    0.000000] Node 0: aperture @ d4000000 size 32 MB
May  8 15:09:40 MEwebServer kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
May  8 15:09:40 MEwebServer kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
May  8 15:09:40 MEwebServer kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
May  8 15:09:40 MEwebServer kernel: [    0.000000] This costs you 64 MB of RAM
May  8 15:09:40 MEwebServer kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ d4000000
May  8 15:09:40 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd4000000-0xd7ffffff]
May  8 15:09:40 MEwebServer kernel: [    0.000000] Memory: 3927608K/4161080K available (7389K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 233472K reserved)
May  8 15:09:40 MEwebServer kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May  8 15:09:40 MEwebServer kernel: [    0.000000] Hierarchical RCU implementation.
May  8 15:09:40 MEwebServer kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
May  8 15:09:40 MEwebServer kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
May  8 15:09:40 MEwebServer kernel: [    0.000000] 	Offload RCU callbacks from all CPUs
May  8 15:09:40 MEwebServer kernel: [    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
May  8 15:09:40 MEwebServer kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
May  8 15:09:40 MEwebServer kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
May  8 15:09:40 MEwebServer kernel: [    0.000000] Console: colour VGA+ 80x25
May  8 15:09:40 MEwebServer kernel: [    0.000000] console [tty0] enabled
May  8 15:09:40 MEwebServer kernel: [    0.000000] allocated 16777216 bytes of page_cgroup
May  8 15:09:40 MEwebServer kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  8 15:09:40 MEwebServer kernel: [    0.000000] hpet clockevent registered
May  8 15:09:40 MEwebServer kernel: [    0.000000] tsc: Fast TSC calibration using PIT
May  8 15:09:40 MEwebServer kernel: [    0.004000] tsc: Detected 2812.575 MHz processor
May  8 15:09:40 MEwebServer kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5625.15 BogoMIPS (lpj=11250300)
May  8 15:09:40 MEwebServer kernel: [    0.000122] pid_max: default: 32768 minimum: 301
May  8 15:09:40 MEwebServer kernel: [    0.000207] Security Framework initialized
May  8 15:09:40 MEwebServer kernel: [    0.000282] AppArmor: AppArmor initialized
May  8 15:09:40 MEwebServer kernel: [    0.000340] Yama: becoming mindful.
May  8 15:09:40 MEwebServer kernel: [    0.000680] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.002135] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.002813] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.002880] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.003164] Initializing cgroup subsys memory
May  8 15:09:40 MEwebServer kernel: [    0.003228] Initializing cgroup subsys devices
May  8 15:09:40 MEwebServer kernel: [    0.003286] Initializing cgroup subsys freezer
May  8 15:09:40 MEwebServer kernel: [    0.003344] Initializing cgroup subsys blkio
May  8 15:09:40 MEwebServer kernel: [    0.003402] Initializing cgroup subsys perf_event
May  8 15:09:40 MEwebServer kernel: [    0.003462] Initializing cgroup subsys hugetlb
May  8 15:09:40 MEwebServer kernel: [    0.003537] tseg: 0000000000
May  8 15:09:40 MEwebServer kernel: [    0.003544] CPU: Physical Processor ID: 0
May  8 15:09:40 MEwebServer kernel: [    0.003601] CPU: Processor Core ID: 0
May  8 15:09:40 MEwebServer kernel: [    0.003659] mce: CPU supports 6 MCE banks
May  8 15:09:40 MEwebServer kernel: [    0.003720] LVT offset 0 assigned for vector 0xf9
May  8 15:09:40 MEwebServer kernel: [    0.003781] process: using AMD E400 aware idle routine
May  8 15:09:40 MEwebServer kernel: [    0.003841] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
May  8 15:09:40 MEwebServer kernel: [    0.003841] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
May  8 15:09:40 MEwebServer kernel: [    0.003841] tlb_flushall_shift: 4
May  8 15:09:40 MEwebServer kernel: [    0.004021] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
May  8 15:09:40 MEwebServer kernel: [    0.004840] ACPI: Core revision 20131115
May  8 15:09:40 MEwebServer kernel: [    0.006661] ACPI: All ACPI Tables successfully acquired
May  8 15:09:40 MEwebServer kernel: [    0.008182] ftrace: allocating 28576 entries in 112 pages
May  8 15:09:40 MEwebServer kernel: [    0.020122] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  8 15:09:40 MEwebServer kernel: [    0.059861] smpboot: CPU0: AMD Athlon(tm) X2 240e Processor (fam: 10, model: 06, stepping: 02)
May  8 15:09:40 MEwebServer kernel: [    0.165664] Performance Events: AMD PMU driver.
May  8 15:09:40 MEwebServer kernel: [    0.165768] ... version:                0
May  8 15:09:40 MEwebServer kernel: [    0.165825] ... bit width:              48
May  8 15:09:40 MEwebServer kernel: [    0.165882] ... generic registers:      4
May  8 15:09:40 MEwebServer kernel: [    0.165939] ... value mask:             0000ffffffffffff
May  8 15:09:40 MEwebServer kernel: [    0.165997] ... max period:             00007fffffffffff
May  8 15:09:40 MEwebServer kernel: [    0.166055] ... fixed-purpose events:   0
May  8 15:09:40 MEwebServer kernel: [    0.166112] ... event mask:             000000000000000f
May  8 15:09:40 MEwebServer kernel: [    0.167632] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
May  8 15:09:40 MEwebServer kernel: [    0.167781] x86: Booting SMP configuration:
May  8 15:09:40 MEwebServer kernel: [    0.167839] .... node  #0, CPUs:      #1
May  8 15:09:40 MEwebServer kernel: [    0.181020] x86: Booted up 1 node, 2 CPUs
May  8 15:09:40 MEwebServer kernel: [    0.181130] smpboot: Total of 2 processors activated (11250.30 BogoMIPS)
May  8 15:09:40 MEwebServer kernel: [    0.181888] devtmpfs: initialized
May  8 15:09:40 MEwebServer kernel: [    0.185145] EVM: security.selinux
May  8 15:09:40 MEwebServer kernel: [    0.185201] EVM: security.SMACK64
May  8 15:09:40 MEwebServer kernel: [    0.185258] EVM: security.ima
May  8 15:09:40 MEwebServer kernel: [    0.185313] EVM: security.capability
May  8 15:09:40 MEwebServer kernel: [    0.185438] PM: Registering ACPI NVS region [mem 0xddff0000-0xddff2fff] (12288 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.186443] pinctrl core: initialized pinctrl subsystem
May  8 15:09:40 MEwebServer kernel: [    0.186572] regulator-dummy: no parameters
May  8 15:09:40 MEwebServer kernel: [    0.186663] RTC time: 14:09:07, date: 05/08/15
May  8 15:09:40 MEwebServer kernel: [    0.186762] NET: Registered protocol family 16
May  8 15:09:40 MEwebServer kernel: [    0.186914] cpuidle: using governor ladder
May  8 15:09:40 MEwebServer kernel: [    0.186972] cpuidle: using governor menu
May  8 15:09:40 MEwebServer kernel: [    0.187033] node 0 link 0: io port [1000, fffff]
May  8 15:09:40 MEwebServer kernel: [    0.187035] TOM: 00000000e0000000 aka 3584M
May  8 15:09:40 MEwebServer kernel: [    0.187093] Fam 10h mmconf [mem 0xf0000000-0xf00fffff]
May  8 15:09:40 MEwebServer kernel: [    0.187095] node 0 link 0: mmio [f0000000, f7ffffff] ==> [f0100000, f7ffffff]
May  8 15:09:40 MEwebServer kernel: [    0.187098] node 0 link 0: mmio [f8000000, ffb7ffff]
May  8 15:09:40 MEwebServer kernel: [    0.187100] node 0 link 0: mmio [a0000, bffff]
May  8 15:09:40 MEwebServer kernel: [    0.187101] node 0 link 0: mmio [e0000000, efffffff]
May  8 15:09:40 MEwebServer kernel: [    0.187103] TOM2: 0000000120000000 aka 4608M
May  8 15:09:40 MEwebServer kernel: [    0.187161] bus: [bus 00-ff] on node 0 link 0
May  8 15:09:40 MEwebServer kernel: [    0.187162] bus: 00 [io  0x0000-0xffff]
May  8 15:09:40 MEwebServer kernel: [    0.187163] bus: 00 [mem 0xf0100000-0xffffffff]
May  8 15:09:40 MEwebServer kernel: [    0.187164] bus: 00 [mem 0x000a0000-0x000bffff]
May  8 15:09:40 MEwebServer kernel: [    0.187165] bus: 00 [mem 0xe0000000-0xefffffff]
May  8 15:09:40 MEwebServer kernel: [    0.187167] bus: 00 [mem 0x120000000-0xfcffffffff]
May  8 15:09:40 MEwebServer kernel: [    0.187210] ACPI: bus type PCI registered
May  8 15:09:40 MEwebServer kernel: [    0.187268] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
May  8 15:09:40 MEwebServer kernel: [    0.187382] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
May  8 15:09:40 MEwebServer kernel: [    0.187456] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
May  8 15:09:40 MEwebServer kernel: [    0.193991] PCI: Using configuration type 1 for base access
May  8 15:09:40 MEwebServer kernel: [    0.194930] bio: create slab <bio-0> at 0
May  8 15:09:40 MEwebServer kernel: [    0.195163] ACPI: Added _OSI(Module Device)
May  8 15:09:40 MEwebServer kernel: [    0.195221] ACPI: Added _OSI(Processor Device)
May  8 15:09:40 MEwebServer kernel: [    0.195281] ACPI: Added _OSI(3.0 _SCP Extensions)
May  8 15:09:40 MEwebServer kernel: [    0.195338] ACPI: Added _OSI(Processor Aggregator Device)
May  8 15:09:40 MEwebServer kernel: [    0.199045] ACPI: Interpreter enabled
May  8 15:09:40 MEwebServer kernel: [    0.199108] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
May  8 15:09:40 MEwebServer kernel: [    0.199268] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
May  8 15:09:40 MEwebServer kernel: [    0.199434] ACPI: (supports S0 S3 S4 S5)
May  8 15:09:40 MEwebServer kernel: [    0.199492] ACPI: Using IOAPIC for interrupt routing
May  8 15:09:40 MEwebServer kernel: [    0.199568] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
May  8 15:09:40 MEwebServer kernel: [    0.199732] ACPI: No dock devices found.
May  8 15:09:40 MEwebServer kernel: [    0.204598] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
May  8 15:09:40 MEwebServer kernel: [    0.204663] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
May  8 15:09:40 MEwebServer kernel: [    0.204737] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
May  8 15:09:40 MEwebServer kernel: [    0.204845] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
May  8 15:09:40 MEwebServer kernel: [    0.205047] PCI host bridge to bus 0000:00
May  8 15:09:40 MEwebServer kernel: [    0.205106] pci_bus 0000:00: root bus resource [bus 00-ff]
May  8 15:09:40 MEwebServer kernel: [    0.205166] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
May  8 15:09:40 MEwebServer kernel: [    0.205226] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
May  8 15:09:40 MEwebServer kernel: [    0.205286] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
May  8 15:09:40 MEwebServer kernel: [    0.205347] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
May  8 15:09:40 MEwebServer kernel: [    0.205408] pci_bus 0000:00: root bus resource [mem 0xde000000-0xfebfffff]
May  8 15:09:40 MEwebServer kernel: [    0.205488] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
May  8 15:09:40 MEwebServer kernel: [    0.205703] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
May  8 15:09:40 MEwebServer kernel: [    0.205786] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
May  8 15:09:40 MEwebServer kernel: [    0.205797] pci 0000:00:01.1: reg 0x10: [io  0xc000-0xc03f]
May  8 15:09:40 MEwebServer kernel: [    0.205811] pci 0000:00:01.1: reg 0x20: [io  0x1c00-0x1c3f]
May  8 15:09:40 MEwebServer kernel: [    0.205815] pci 0000:00:01.1: reg 0x24: [io  0xc800-0xc83f]
May  8 15:09:40 MEwebServer kernel: [    0.205841] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  8 15:09:40 MEwebServer kernel: [    0.205907] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
May  8 15:09:40 MEwebServer kernel: [    0.205986] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
May  8 15:09:40 MEwebServer kernel: [    0.206051] pci 0000:00:04.0: System wakeup disabled by ACPI
May  8 15:09:40 MEwebServer kernel: [    0.206133] pci 0000:00:06.0: [10de:03ec] type 00 class 0x01018a
May  8 15:09:40 MEwebServer kernel: [    0.206152] pci 0000:00:06.0: reg 0x20: [io  0xf000-0xf00f]
May  8 15:09:40 MEwebServer kernel: [    0.206227] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
May  8 15:09:40 MEwebServer kernel: [    0.206236] pci 0000:00:07.0: reg 0x10: [mem 0xfb000000-0xfb000fff]
May  8 15:09:40 MEwebServer kernel: [    0.206240] pci 0000:00:07.0: reg 0x14: [io  0xcc00-0xcc07]
May  8 15:09:40 MEwebServer kernel: [    0.206270] pci 0000:00:07.0: supports D1 D2
May  8 15:09:40 MEwebServer kernel: [    0.206272] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
May  8 15:09:40 MEwebServer kernel: [    0.206317] pci 0000:00:07.0: System wakeup disabled by ACPI
May  8 15:09:40 MEwebServer kernel: [    0.206398] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
May  8 15:09:40 MEwebServer kernel: [    0.206405] pci 0000:00:08.0: reg 0x10: [io  0x09f0-0x09f7]
May  8 15:09:40 MEwebServer kernel: [    0.206409] pci 0000:00:08.0: reg 0x14: [io  0x0bf0-0x0bf3]
May  8 15:09:40 MEwebServer kernel: [    0.206412] pci 0000:00:08.0: reg 0x18: [io  0x0970-0x0977]
May  8 15:09:40 MEwebServer kernel: [    0.206416] pci 0000:00:08.0: reg 0x1c: [io  0x0b70-0x0b73]
May  8 15:09:40 MEwebServer kernel: [    0.206419] pci 0000:00:08.0: reg 0x20: [io  0xe000-0xe00f]
May  8 15:09:40 MEwebServer kernel: [    0.206423] pci 0000:00:08.0: reg 0x24: [mem 0xfb001000-0xfb001fff]
May  8 15:09:40 MEwebServer kernel: [    0.206501] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
May  8 15:09:40 MEwebServer kernel: [    0.206507] pci 0000:00:0d.0: reg 0x10: [mem 0xf8000000-0xf8ffffff]
May  8 15:09:40 MEwebServer kernel: [    0.206512] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
May  8 15:09:40 MEwebServer kernel: [    0.206516] pci 0000:00:0d.0: reg 0x1c: [mem 0xf9000000-0xf9ffffff 64bit]
May  8 15:09:40 MEwebServer kernel: [    0.206521] pci 0000:00:0d.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
May  8 15:09:40 MEwebServer kernel: [    0.206591] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
May  8 15:09:40 MEwebServer kernel: [    0.206653] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
May  8 15:09:40 MEwebServer kernel: [    0.206710] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
May  8 15:09:40 MEwebServer kernel: [    0.206766] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
May  8 15:09:40 MEwebServer kernel: [    0.206827] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
May  8 15:09:40 MEwebServer kernel: [    0.206933] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
May  8 15:09:40 MEwebServer kernel: [    0.206996] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
May  8 15:09:40 MEwebServer kernel: [    0.206999] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
May  8 15:09:40 MEwebServer kernel: [    0.207001] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May  8 15:09:40 MEwebServer kernel: [    0.207002] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May  8 15:09:40 MEwebServer kernel: [    0.207004] pci 0000:00:04.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
May  8 15:09:40 MEwebServer kernel: [    0.207006] pci 0000:00:04.0:   bridge window [mem 0xde000000-0xfebfffff] (subtractive decode)
May  8 15:09:40 MEwebServer kernel: [    0.207381] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.207953] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.208523] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.209095] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.209664] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.210234] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.210803] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.211373] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.211944] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
May  8 15:09:40 MEwebServer kernel: [    0.212425] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.212996] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 *7 9 10 11 14 15)
May  8 15:09:40 MEwebServer kernel: [    0.213477] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
May  8 15:09:40 MEwebServer kernel: [    0.213956] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.214526] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.215097] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
May  8 15:09:40 MEwebServer kernel: [    0.215571] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.216141] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.216711] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
May  8 15:09:40 MEwebServer kernel: [    0.217191] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.217789] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.218116] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.218443] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.218768] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.219094] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.219419] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.219745] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.220070] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.220396] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
May  8 15:09:40 MEwebServer kernel: [    0.220807] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
May  8 15:09:40 MEwebServer kernel: [    0.221220] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
May  8 15:09:40 MEwebServer kernel: [    0.221630] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.222085] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.222539] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
May  8 15:09:40 MEwebServer kernel: [    0.222949] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.223404] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.223858] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.224312] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
May  8 15:09:40 MEwebServer kernel: [    0.224723] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
May  8 15:09:40 MEwebServer kernel: [    0.225206] ACPI: \_SB_.PCI0: notify handler is installed
May  8 15:09:40 MEwebServer kernel: [    0.225236] Found 1 acpi root devices
May  8 15:09:40 MEwebServer kernel: [    0.225358] vgaarb: setting as boot device: PCI:0000:00:0d.0
May  8 15:09:40 MEwebServer kernel: [    0.225418] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
May  8 15:09:40 MEwebServer kernel: [    0.225490] vgaarb: loaded
May  8 15:09:40 MEwebServer kernel: [    0.225545] vgaarb: bridge control possible 0000:00:0d.0
May  8 15:09:40 MEwebServer kernel: [    0.225761] SCSI subsystem initialized
May  8 15:09:40 MEwebServer kernel: [    0.225901] libata version 3.00 loaded.
May  8 15:09:40 MEwebServer kernel: [    0.225928] ACPI: bus type USB registered
May  8 15:09:40 MEwebServer kernel: [    0.226005] usbcore: registered new interface driver usbfs
May  8 15:09:40 MEwebServer kernel: [    0.226071] usbcore: registered new interface driver hub
May  8 15:09:40 MEwebServer kernel: [    0.226171] usbcore: registered new device driver usb
May  8 15:09:40 MEwebServer kernel: [    0.226339] PCI: Using ACPI for IRQ routing
May  8 15:09:40 MEwebServer kernel: [    0.229331] PCI: pci_cache_line_size set to 64 bytes
May  8 15:09:40 MEwebServer kernel: [    0.229354] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
May  8 15:09:40 MEwebServer kernel: [    0.229357] e820: reserve RAM buffer [mem 0xddff0000-0xdfffffff]
May  8 15:09:40 MEwebServer kernel: [    0.229448] NetLabel: Initializing
May  8 15:09:40 MEwebServer kernel: [    0.229505] NetLabel:  domain hash size = 128
May  8 15:09:40 MEwebServer kernel: [    0.229562] NetLabel:  protocols = UNLABELED CIPSOv4
May  8 15:09:40 MEwebServer kernel: [    0.229630] NetLabel:  unlabeled traffic allowed by default
May  8 15:09:40 MEwebServer kernel: [    0.229792] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May  8 15:09:40 MEwebServer kernel: [    0.229857] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
May  8 15:09:40 MEwebServer kernel: [    0.230087] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
May  8 15:09:40 MEwebServer kernel: [    0.232288] Switched to clocksource hpet
May  8 15:09:40 MEwebServer kernel: [    0.236805] AppArmor: AppArmor Filesystem Enabled
May  8 15:09:40 MEwebServer kernel: [    0.236896] pnp: PnP ACPI init
May  8 15:09:40 MEwebServer kernel: [    0.236966] ACPI: bus type PNP registered
May  8 15:09:40 MEwebServer kernel: [    0.237178] system 00:00: [io  0x1000-0x107f] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237239] system 00:00: [io  0x1080-0x10ff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237300] system 00:00: [io  0x1400-0x147f] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237360] system 00:00: [io  0x1480-0x14ff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237420] system 00:00: [io  0x1800-0x187f] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237480] system 00:00: [io  0x1880-0x18ff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237540] system 00:00: [mem 0xfefe0000-0xfefe01ff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237602] system 00:00: [mem 0xfefe1000-0xfefe10ff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237662] system 00:00: [mem 0xde000000-0xdfffffff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237725] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:09:40 MEwebServer kernel: [    0.237790] system 00:01: [io  0x04d0-0x04d1] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237851] system 00:01: [io  0x0800-0x087f] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237911] system 00:01: [io  0x0295-0x0296] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.237971] system 00:01: [io  0x0290-0x0294] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.238031] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:09:40 MEwebServer kernel: [    0.238041] pnp 00:02: [dma 4]
May  8 15:09:40 MEwebServer kernel: [    0.238058] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
May  8 15:09:40 MEwebServer kernel: [    0.238115] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
May  8 15:09:40 MEwebServer kernel: [    0.238147] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
May  8 15:09:40 MEwebServer kernel: [    0.238167] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
May  8 15:09:40 MEwebServer kernel: [    0.238189] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
May  8 15:09:40 MEwebServer kernel: [    0.238456] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
May  8 15:09:40 MEwebServer kernel: [    0.238867] system 00:08: [mem 0xf0000000-0xf7ffffff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.238929] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:09:40 MEwebServer kernel: [    0.239039] system 00:09: [mem 0x000cec00-0x000cffff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.239101] system 00:09: [mem 0x000f0000-0x000f7fff] could not be reserved
May  8 15:09:40 MEwebServer kernel: [    0.239163] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
May  8 15:09:40 MEwebServer kernel: [    0.239224] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
May  8 15:09:40 MEwebServer kernel: [    0.239285] system 00:09: [mem 0xddff0000-0xddffffff] could not be reserved
May  8 15:09:40 MEwebServer kernel: [    0.239346] system 00:09: [mem 0xffff0000-0xffffffff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.239408] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
May  8 15:09:40 MEwebServer kernel: [    0.239469] system 00:09: [mem 0x00100000-0xddfeffff] could not be reserved
May  8 15:09:40 MEwebServer kernel: [    0.239530] system 00:09: [mem 0xde000000-0xdfffffff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.239591] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
May  8 15:09:40 MEwebServer kernel: [    0.239653] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
May  8 15:09:40 MEwebServer kernel: [    0.239714] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
May  8 15:09:40 MEwebServer kernel: [    0.239726] pnp: PnP ACPI: found 10 devices
May  8 15:09:40 MEwebServer kernel: [    0.239783] ACPI: bus type PNP unregistered
May  8 15:09:40 MEwebServer kernel: [    0.246044] pci 0000:00:0d.0: BAR 6: assigned [mem 0xfa000000-0xfa01ffff pref]
May  8 15:09:40 MEwebServer kernel: [    0.246116] pci 0000:00:04.0: PCI bridge to [bus 01]
May  8 15:09:40 MEwebServer kernel: [    0.246176] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
May  8 15:09:40 MEwebServer kernel: [    0.246241] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
May  8 15:09:40 MEwebServer kernel: [    0.246243] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
May  8 15:09:40 MEwebServer kernel: [    0.246245] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
May  8 15:09:40 MEwebServer kernel: [    0.246246] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
May  8 15:09:40 MEwebServer kernel: [    0.246248] pci_bus 0000:00: resource 8 [mem 0xde000000-0xfebfffff]
May  8 15:09:40 MEwebServer kernel: [    0.246250] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
May  8 15:09:40 MEwebServer kernel: [    0.246251] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
May  8 15:09:40 MEwebServer kernel: [    0.246253] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
May  8 15:09:40 MEwebServer kernel: [    0.246254] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
May  8 15:09:40 MEwebServer kernel: [    0.246256] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
May  8 15:09:40 MEwebServer kernel: [    0.246258] pci_bus 0000:01: resource 8 [mem 0xde000000-0xfebfffff]
May  8 15:09:40 MEwebServer kernel: [    0.246289] NET: Registered protocol family 2
May  8 15:09:40 MEwebServer kernel: [    0.246530] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.246708] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.246924] TCP: Hash tables configured (established 32768 bind 32768)
May  8 15:09:40 MEwebServer kernel: [    0.247026] TCP: reno registered
May  8 15:09:40 MEwebServer kernel: [    0.247090] UDP hash table entries: 2048 (order: 4, 65536 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.247176] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.247324] NET: Registered protocol family 1
May  8 15:09:40 MEwebServer kernel: [    0.247462] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:09:40 MEwebServer kernel: [    0.247567] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:09:40 MEwebServer kernel: [    0.247670] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:09:40 MEwebServer kernel: [    0.247733] pci 0000:00:0d.0: Video device with shadowed ROM
May  8 15:09:40 MEwebServer kernel: [    0.247743] PCI: CLS 0 bytes, default 64
May  8 15:09:40 MEwebServer kernel: [    0.247824] Trying to unpack rootfs image as initramfs...
May  8 15:09:40 MEwebServer kernel: [    0.542777] Freeing initrd memory: 19272K (ffff880035a4c000 - ffff880036d1e000)
May  8 15:09:40 MEwebServer kernel: [    0.543021] PCI-DMA: Disabling AGP.
May  8 15:09:40 MEwebServer kernel: [    0.543145] PCI-DMA: aperture base @ d4000000 size 65536 KB
May  8 15:09:40 MEwebServer kernel: [    0.543205] PCI-DMA: using GART IOMMU.
May  8 15:09:40 MEwebServer kernel: [    0.543264] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
May  8 15:09:40 MEwebServer kernel: [    0.546127] LVT offset 1 assigned for vector 0x400
May  8 15:09:40 MEwebServer kernel: [    0.546196] IBS: LVT offset 1 assigned
May  8 15:09:40 MEwebServer kernel: [    0.546276] perf: AMD IBS detected (0x0000001f)
May  8 15:09:40 MEwebServer kernel: [    0.546379] microcode: CPU0: patch_level=0x00000000
May  8 15:09:40 MEwebServer kernel: [    0.546445] microcode: CPU1: patch_level=0x00000000
May  8 15:09:40 MEwebServer kernel: [    0.546570] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
May  8 15:09:40 MEwebServer kernel: [    0.546643] Scanning for low memory corruption every 60 seconds
May  8 15:09:40 MEwebServer kernel: [    0.546907] Initialise system trusted keyring
May  8 15:09:40 MEwebServer kernel: [    0.547009] audit: initializing netlink socket (disabled)
May  8 15:09:40 MEwebServer kernel: [    0.547081] type=2000 audit(1431094147.440:1): initialized
May  8 15:09:40 MEwebServer kernel: [    0.573135] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  8 15:09:40 MEwebServer kernel: [    0.574320] zbud: loaded
May  8 15:09:40 MEwebServer kernel: [    0.574545] VFS: Disk quotas dquot_6.5.2
May  8 15:09:40 MEwebServer kernel: [    0.574658] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May  8 15:09:40 MEwebServer kernel: [    0.575210] fuse init (API version 7.22)
May  8 15:09:40 MEwebServer kernel: [    0.575352] msgmni has been set to 7837
May  8 15:09:40 MEwebServer kernel: [    0.575471] Key type big_key registered
May  8 15:09:40 MEwebServer kernel: [    0.575854] Key type asymmetric registered
May  8 15:09:40 MEwebServer kernel: [    0.575913] Asymmetric key parser 'x509' registered
May  8 15:09:40 MEwebServer kernel: [    0.575997] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
May  8 15:09:40 MEwebServer kernel: [    0.576093] io scheduler noop registered
May  8 15:09:40 MEwebServer kernel: [    0.576151] io scheduler deadline registered (default)
May  8 15:09:40 MEwebServer kernel: [    0.578602] io scheduler cfq registered
May  8 15:09:40 MEwebServer kernel: [    0.578727] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  8 15:09:40 MEwebServer kernel: [    0.578799] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  8 15:09:40 MEwebServer kernel: [    0.578896] ipmi message handler version 39.2
May  8 15:09:40 MEwebServer kernel: [    0.579013] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
May  8 15:09:40 MEwebServer kernel: [    0.579086] ACPI: Power Button [PWRB]
May  8 15:09:40 MEwebServer kernel: [    0.579178] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  8 15:09:40 MEwebServer kernel: [    0.579249] ACPI: Power Button [PWRF]
May  8 15:09:40 MEwebServer kernel: [    0.579392] GHES: HEST is not enabled!
May  8 15:09:40 MEwebServer kernel: [    0.579532] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May  8 15:09:40 MEwebServer kernel: [    0.580725] Linux agpgart interface v0.103
May  8 15:09:40 MEwebServer kernel: [    0.581935] brd: module loaded
May  8 15:09:40 MEwebServer kernel: [    0.582578] loop: module loaded
May  8 15:09:40 MEwebServer kernel: [    0.582949] libphy: Fixed MDIO Bus: probed
May  8 15:09:40 MEwebServer kernel: [    0.583079] tun: Universal TUN/TAP device driver, 1.6
May  8 15:09:40 MEwebServer kernel: [    0.583138] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  8 15:09:40 MEwebServer kernel: [    0.583277] PPP generic driver version 2.4.2
May  8 15:09:40 MEwebServer kernel: [    0.583369] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  8 15:09:40 MEwebServer kernel: [    0.583431] ehci-pci: EHCI PCI platform driver
May  8 15:09:40 MEwebServer kernel: [    0.583497] ehci-platform: EHCI generic platform driver
May  8 15:09:40 MEwebServer kernel: [    0.583559] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  8 15:09:40 MEwebServer kernel: [    0.583619] ohci-pci: OHCI PCI platform driver
May  8 15:09:40 MEwebServer kernel: [    0.583682] ohci-platform: OHCI generic platform driver
May  8 15:09:40 MEwebServer kernel: [    0.583744] uhci_hcd: USB Universal Host Controller Interface driver
May  8 15:09:40 MEwebServer kernel: [    0.583844] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  8 15:09:40 MEwebServer kernel: [    0.583905] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  8 15:09:40 MEwebServer kernel: [    0.584124] serio: i8042 KBD port at 0x60,0x64 irq 1
May  8 15:09:40 MEwebServer kernel: [    0.584313] mousedev: PS/2 mouse device common for all mice
May  8 15:09:40 MEwebServer kernel: [    0.584479] rtc_cmos 00:04: RTC can wake from S4
May  8 15:09:40 MEwebServer kernel: [    0.584677] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
May  8 15:09:40 MEwebServer kernel: [    0.584768] rtc_cmos 00:04: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
May  8 15:09:40 MEwebServer kernel: [    0.584891] device-mapper: uevent: version 1.0.3
May  8 15:09:40 MEwebServer kernel: [    0.584999] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
May  8 15:09:40 MEwebServer kernel: [    0.585076] ledtrig-cpu: registered to indicate activity on CPUs
May  8 15:09:40 MEwebServer kernel: [    0.585233] TCP: cubic registered
May  8 15:09:40 MEwebServer kernel: [    0.585356] NET: Registered protocol family 10
May  8 15:09:40 MEwebServer kernel: [    0.585557] NET: Registered protocol family 17
May  8 15:09:40 MEwebServer kernel: [    0.585624] Key type dns_resolver registered
May  8 15:09:40 MEwebServer kernel: [    0.585888] Loading compiled-in X.509 certificates
May  8 15:09:40 MEwebServer kernel: [    0.586915] Loaded X.509 cert 'Magrathea: Glacier signing key: 1981bc916ffc00599231ec5630e666e0256fd6f1'
May  8 15:09:40 MEwebServer kernel: [    0.587005] registered taskstats version 1
May  8 15:09:40 MEwebServer kernel: [    0.589182] Key type trusted registered
May  8 15:09:40 MEwebServer kernel: [    0.592164] Key type encrypted registered
May  8 15:09:40 MEwebServer kernel: [    0.592230] AppArmor: AppArmor sha1 policy hashing enabled
May  8 15:09:40 MEwebServer kernel: [    0.592305] IMA: No TPM chip found, activating TPM-bypass!
May  8 15:09:40 MEwebServer kernel: [    0.592493] regulator-dummy: disabling
May  8 15:09:40 MEwebServer kernel: [    0.592587]   Magic number: 15:693:181
May  8 15:09:40 MEwebServer kernel: [    0.592740] rtc_cmos 00:04: setting system clock to 2015-05-08 14:09:08 UTC (1431094148)
May  8 15:09:40 MEwebServer kernel: [    0.592889] acpi-cpufreq: overriding BIOS provided _PSD data
May  8 15:09:40 MEwebServer kernel: [    0.592999] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  8 15:09:40 MEwebServer kernel: [    0.593058] EDD information not available.
May  8 15:09:40 MEwebServer kernel: [    0.593140] PM: Hibernation image not present or could not be loaded.
May  8 15:09:40 MEwebServer kernel: [    0.594533] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
May  8 15:09:40 MEwebServer kernel: [    0.594610] Write protecting the kernel read-only data: 12288k
May  8 15:09:40 MEwebServer kernel: [    0.596851] Freeing unused kernel memory: 792K (ffff88000173a000 - ffff880001800000)
May  8 15:09:40 MEwebServer kernel: [    0.598752] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
May  8 15:09:40 MEwebServer kernel: [    0.606199] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
May  8 15:09:40 MEwebServer kernel: [    0.628044] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
May  8 15:09:40 MEwebServer kernel: [    0.633573] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
May  8 15:09:40 MEwebServer kernel: [    0.636383] md: linear personality registered for level -1
May  8 15:09:40 MEwebServer kernel: [    0.641020] md: multipath personality registered for level -4
May  8 15:09:40 MEwebServer kernel: [    0.644262] md: raid0 personality registered for level 0
May  8 15:09:40 MEwebServer kernel: [    0.647681] md: raid1 personality registered for level 1
May  8 15:09:40 MEwebServer kernel: [    0.716245] raid6: sse2x1    3771 MB/s
May  8 15:09:40 MEwebServer kernel: [    0.784230] raid6: sse2x2    5836 MB/s
May  8 15:09:40 MEwebServer kernel: [    0.852221] raid6: sse2x4    6750 MB/s
May  8 15:09:40 MEwebServer kernel: [    0.852278] raid6: using algorithm sse2x4 (6750 MB/s)
May  8 15:09:40 MEwebServer kernel: [    0.852337] raid6: using intx1 recovery algorithm
May  8 15:09:40 MEwebServer kernel: [    0.853598] xor: measuring software checksum speed
May  8 15:09:40 MEwebServer kernel: [    0.892202]    prefetch64-sse: 11515.000 MB/sec
May  8 15:09:40 MEwebServer kernel: [    0.932196]    generic_sse: 10879.000 MB/sec
May  8 15:09:40 MEwebServer kernel: [    0.932254] xor: using function: prefetch64-sse (11515.000 MB/sec)
May  8 15:09:40 MEwebServer kernel: [    0.933566] async_tx: api initialized (async)
May  8 15:09:40 MEwebServer kernel: [    0.940383] md: raid6 personality registered for level 6
May  8 15:09:40 MEwebServer kernel: [    0.940447] md: raid5 personality registered for level 5
May  8 15:09:40 MEwebServer kernel: [    0.940507] md: raid4 personality registered for level 4
May  8 15:09:40 MEwebServer kernel: [    0.946090] md: raid10 personality registered for level 10
May  8 15:09:40 MEwebServer kernel: [    1.156940] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:24:1d:66:65:be
May  8 15:09:40 MEwebServer kernel: [    1.157017] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
May  8 15:09:40 MEwebServer kernel: [    1.157117] pata_amd 0000:00:06.0: version 0.4.1
May  8 15:09:40 MEwebServer kernel: [    1.157670] scsi0 : pata_amd
May  8 15:09:40 MEwebServer kernel: [    1.157791] scsi1 : pata_amd
May  8 15:09:40 MEwebServer kernel: [    1.157873] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  8 15:09:40 MEwebServer kernel: [    1.157934] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  8 15:09:40 MEwebServer kernel: [    1.158026] sata_nv 0000:00:08.0: version 3.5
May  8 15:09:40 MEwebServer kernel: [    1.158175] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
May  8 15:09:40 MEwebServer kernel: [    1.158436] scsi2 : sata_nv
May  8 15:09:40 MEwebServer kernel: [    1.158539] scsi3 : sata_nv
May  8 15:09:40 MEwebServer kernel: [    1.158620] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 22
May  8 15:09:40 MEwebServer kernel: [    1.158681] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 22
May  8 15:09:40 MEwebServer kernel: [    1.312361] ata1.01: NODEV after polling detection
May  8 15:09:40 MEwebServer kernel: [    1.320733] ata1.00: ATAPI: PHILIPS DVDR1628P1, Q1.1, max UDMA/33
May  8 15:09:40 MEwebServer kernel: [    1.320803] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
May  8 15:09:40 MEwebServer kernel: [    1.336659] ata1.00: configured for UDMA/33
May  8 15:09:40 MEwebServer kernel: [    1.339681] scsi 0:0:0:0: CD-ROM            PHILIPS  DVDR1628P1       Q1.1 PQ: 0 ANSI: 5
May  8 15:09:40 MEwebServer kernel: [    1.343476] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May  8 15:09:40 MEwebServer kernel: [    1.343542] cdrom: Uniform CD-ROM driver Revision: 3.20
May  8 15:09:40 MEwebServer kernel: [    1.343737] sr 0:0:0:0: Attached scsi CD-ROM sr0
May  8 15:09:40 MEwebServer kernel: [    1.343792] sr 0:0:0:0: Attached scsi generic sg0 type 5
May  8 15:09:40 MEwebServer kernel: [    1.344013] ata2: port disabled--ignoring
May  8 15:09:40 MEwebServer kernel: [    1.544155] tsc: Refined TSC clocksource calibration: 2812.791 MHz
May  8 15:09:40 MEwebServer kernel: [    1.624164] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  8 15:09:40 MEwebServer kernel: [    1.632371] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
May  8 15:09:40 MEwebServer kernel: [    1.632437] ata3.00: 488397168 sectors, multi 16: LBA48 
May  8 15:09:40 MEwebServer kernel: [    1.640370] ata3.00: configured for UDMA/133
May  8 15:09:40 MEwebServer kernel: [    1.640570] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
May  8 15:09:40 MEwebServer kernel: [    1.640807] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
May  8 15:09:40 MEwebServer kernel: [    1.640901] sd 2:0:0:0: Attached scsi generic sg1 type 0
May  8 15:09:40 MEwebServer kernel: [    1.640944] sd 2:0:0:0: [sda] Write Protect is off
May  8 15:09:40 MEwebServer kernel: [    1.640946] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  8 15:09:40 MEwebServer kernel: [    1.640963] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 15:09:40 MEwebServer kernel: [    1.679707]  sda: sda1 sda2 < sda5 >
May  8 15:09:40 MEwebServer kernel: [    1.680115] sd 2:0:0:0: [sda] Attached SCSI disk
May  8 15:09:40 MEwebServer kernel: [    2.108096] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  8 15:09:40 MEwebServer kernel: [    2.117184] ata4.00: HPA detected: current 488395055, native 488397168
May  8 15:09:40 MEwebServer kernel: [    2.117252] ata4.00: ATA-8: WDC WD2500AAJS-00VTA0, 01.01B01, max UDMA/133
May  8 15:09:40 MEwebServer kernel: [    2.117313] ata4.00: 488395055 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  8 15:09:40 MEwebServer kernel: [    2.133215] ata4.00: configured for UDMA/133
May  8 15:09:40 MEwebServer kernel: [    2.133445] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500AAJS-0 01.0 PQ: 0 ANSI: 5
May  8 15:09:40 MEwebServer kernel: [    2.133669] sd 3:0:0:0: Attached scsi generic sg2 type 0
May  8 15:09:40 MEwebServer kernel: [    2.133723] sd 3:0:0:0: [sdb] 488395055 512-byte logical blocks: (250 GB/232 GiB)
May  8 15:09:40 MEwebServer kernel: [    2.133748] sd 3:0:0:0: [sdb] Write Protect is off
May  8 15:09:40 MEwebServer kernel: [    2.133749] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  8 15:09:40 MEwebServer kernel: [    2.133760] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 15:09:40 MEwebServer kernel: [    2.188478]  sdb: sdb1 sdb2 < sdb5 >
May  8 15:09:40 MEwebServer kernel: [    2.188832] sd 3:0:0:0: [sdb] Attached SCSI disk
May  8 15:09:40 MEwebServer kernel: [    2.336499] md: bind<sda1>
May  8 15:09:40 MEwebServer kernel: [    2.338005] md/raid1:md0: active with 1 out of 2 mirrors
May  8 15:09:40 MEwebServer kernel: [    2.338087] md0: detected capacity change from 0 to 245662285824
May  8 15:09:40 MEwebServer kernel: [    2.364294]  md0: unknown partition table
May  8 15:09:40 MEwebServer kernel: [    2.544029] Switched to clocksource tsc
May  8 15:09:40 MEwebServer kernel: [    2.575478] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
May  8 15:09:40 MEwebServer kernel: [    5.218234] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:09:40 MEwebServer kernel: [    5.218309] ata4.00: BMDMA stat 0x24
May  8 15:09:40 MEwebServer kernel: [    5.218367] ata4.00: failed command: READ DMA
May  8 15:09:40 MEwebServer kernel: [    5.218428] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:09:40 MEwebServer kernel: [    5.218428]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:09:40 MEwebServer kernel: [    5.218526] ata4.00: status: { DRDY ERR }
May  8 15:09:40 MEwebServer kernel: [    5.218583] ata4.00: error: { UNC }
May  8 15:09:40 MEwebServer kernel: [    5.232063] ata4.00: configured for UDMA/133
May  8 15:09:40 MEwebServer kernel: [    5.232144] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:09:40 MEwebServer kernel: [    5.232202] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [    5.232258] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:09:40 MEwebServer kernel: [    5.232318] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [    5.232374] Sense Key : Medium Error [current] [descriptor]
May  8 15:09:40 MEwebServer kernel: [    5.232561] Descriptor sense data with sense descriptors (in hex):
May  8 15:09:40 MEwebServer kernel: [    5.232662]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:09:40 MEwebServer kernel: [    5.233443]         00 00 01 97 
May  8 15:09:40 MEwebServer kernel: [    5.233711] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [    5.233768] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:09:40 MEwebServer kernel: [    5.233871] sd 3:0:0:0: [sdb] CDB: 
May  8 15:09:40 MEwebServer kernel: [    5.233927] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:09:40 MEwebServer kernel: [    5.234496] end_request: I/O error, dev sdb, sector 407
May  8 15:09:40 MEwebServer kernel: [    5.234556] Buffer I/O error on device sdb, logical block 407
May  8 15:09:40 MEwebServer kernel: [    5.234634] ata4: EH complete
May  8 15:09:40 MEwebServer kernel: [    8.168004] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:09:40 MEwebServer kernel: [    8.168070] ata4.00: BMDMA stat 0x24
May  8 15:09:40 MEwebServer kernel: [    8.170465] ata4.00: failed command: READ DMA
May  8 15:09:40 MEwebServer kernel: [    8.170525] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:09:40 MEwebServer kernel: [    8.170525]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:09:40 MEwebServer kernel: [    8.170615] ata4.00: status: { DRDY ERR }
May  8 15:09:40 MEwebServer kernel: [    8.170672] ata4.00: error: { UNC }
May  8 15:09:40 MEwebServer kernel: [    8.191877] ata4.00: configured for UDMA/133
May  8 15:09:40 MEwebServer kernel: [    8.191953] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:09:40 MEwebServer kernel: [    8.192012] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [    8.192068] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:09:40 MEwebServer kernel: [    8.192127] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [    8.192183] Sense Key : Medium Error [current] [descriptor]
May  8 15:09:40 MEwebServer kernel: [    8.192370] Descriptor sense data with sense descriptors (in hex):
May  8 15:09:40 MEwebServer kernel: [    8.192471]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:09:40 MEwebServer kernel: [    8.193252]         00 00 01 97 
May  8 15:09:40 MEwebServer kernel: [    8.193520] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [    8.193577] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:09:40 MEwebServer kernel: [    8.193680] sd 3:0:0:0: [sdb] CDB: 
May  8 15:09:40 MEwebServer kernel: [    8.193736] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:09:40 MEwebServer kernel: [    8.194304] end_request: I/O error, dev sdb, sector 407
May  8 15:09:40 MEwebServer kernel: [    8.194364] Buffer I/O error on device sdb, logical block 407
May  8 15:09:40 MEwebServer kernel: [    8.194445] ata4: EH complete
May  8 15:09:40 MEwebServer kernel: [    8.613579] random: nonblocking pool is initialized
May  8 15:09:40 MEwebServer kernel: [   12.164373] MCE: In-kernel MCE decoding enabled.
May  8 15:09:40 MEwebServer kernel: [   12.204720] EDAC MC: Ver: 3.0.0
May  8 15:09:40 MEwebServer kernel: [   12.290090] AMD64 EDAC driver v3.4.0
May  8 15:09:40 MEwebServer kernel: [   12.290178] EDAC amd64: DRAM ECC disabled.
May  8 15:09:40 MEwebServer kernel: [   12.290241] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May  8 15:09:40 MEwebServer kernel: [   12.290241]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May  8 15:09:40 MEwebServer kernel: [   12.290241]  (Note that use of the override may cause unknown side effects.)
May  8 15:09:40 MEwebServer kernel: [   12.397954] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
May  8 15:09:40 MEwebServer kernel: [   12.398033] i2c i2c-1: nForce2 SMBus adapter at 0xc800
May  8 15:09:40 MEwebServer kernel: [   12.868348] kvm: Nested Virtualization enabled
May  8 15:09:40 MEwebServer kernel: [   12.868596] kvm: Nested Paging enabled
May  8 15:09:40 MEwebServer kernel: [   13.100233] [drm] Initialized drm 1.1.0 20060810
May  8 15:09:40 MEwebServer kernel: [   13.393304] wmi: Mapper loaded
May  8 15:09:40 MEwebServer kernel: [   14.025455] ip_tables: (C) 2000-2006 Netfilter Core Team
May  8 15:09:40 MEwebServer kernel: [   14.061797] forcedeth 0000:00:07.0: irq 40 for MSI/MSI-X
May  8 15:09:40 MEwebServer kernel: [   14.061827] forcedeth 0000:00:07.0 eth0: MSI enabled
May  8 15:09:40 MEwebServer kernel: [   14.119926] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
May  8 15:09:40 MEwebServer kernel: [   14.484911] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  8 15:09:40 MEwebServer kernel: [   15.244646] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:09:40 MEwebServer kernel: [   15.244713] ata4.00: BMDMA stat 0x24
May  8 15:09:40 MEwebServer kernel: [   15.244771] ata4.00: failed command: READ DMA
May  8 15:09:40 MEwebServer kernel: [   15.244832] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:09:40 MEwebServer kernel: [   15.244832]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:09:40 MEwebServer kernel: [   15.244931] ata4.00: status: { DRDY ERR }
May  8 15:09:40 MEwebServer kernel: [   15.244988] ata4.00: error: { UNC }
May  8 15:09:40 MEwebServer kernel: [   15.266525] ata4.00: configured for UDMA/133
May  8 15:09:40 MEwebServer kernel: [   15.266606] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:09:40 MEwebServer kernel: [   15.266664] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   15.266720] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:09:40 MEwebServer kernel: [   15.266779] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   15.266836] Sense Key : Medium Error [current] [descriptor]
May  8 15:09:40 MEwebServer kernel: [   15.267023] Descriptor sense data with sense descriptors (in hex):
May  8 15:09:40 MEwebServer kernel: [   15.267124]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:09:40 MEwebServer kernel: [   15.267905]         00 00 01 97 
May  8 15:09:40 MEwebServer kernel: [   15.268174] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   15.268230] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:09:40 MEwebServer kernel: [   15.268333] sd 3:0:0:0: [sdb] CDB: 
May  8 15:09:40 MEwebServer kernel: [   15.268389] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:09:40 MEwebServer kernel: [   15.268958] end_request: I/O error, dev sdb, sector 407
May  8 15:09:40 MEwebServer kernel: [   15.269018] Buffer I/O error on device sdb, logical block 407
May  8 15:09:40 MEwebServer kernel: [   15.269096] ata4: EH complete
May  8 15:09:40 MEwebServer kernel: [   18.200428] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:09:40 MEwebServer kernel: [   18.200494] ata4.00: BMDMA stat 0x24
May  8 15:09:40 MEwebServer kernel: [   18.200553] ata4.00: failed command: READ DMA
May  8 15:09:40 MEwebServer kernel: [   18.200614] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:09:40 MEwebServer kernel: [   18.200614]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:09:40 MEwebServer kernel: [   18.200703] ata4.00: status: { DRDY ERR }
May  8 15:09:40 MEwebServer kernel: [   18.200760] ata4.00: error: { UNC }
May  8 15:09:40 MEwebServer kernel: [   18.222291] ata4.00: configured for UDMA/133
May  8 15:09:40 MEwebServer kernel: [   18.222310] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:09:40 MEwebServer kernel: [   18.222311] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   18.222313] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:09:40 MEwebServer kernel: [   18.222314] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   18.222316] Sense Key : Medium Error [current] [descriptor]
May  8 15:09:40 MEwebServer kernel: [   18.222318] Descriptor sense data with sense descriptors (in hex):
May  8 15:09:40 MEwebServer kernel: [   18.222319]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:09:40 MEwebServer kernel: [   18.222324]         00 00 01 97 
May  8 15:09:40 MEwebServer kernel: [   18.222326] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   18.222328] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:09:40 MEwebServer kernel: [   18.222330] sd 3:0:0:0: [sdb] CDB: 
May  8 15:09:40 MEwebServer kernel: [   18.222331] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:09:40 MEwebServer kernel: [   18.222336] end_request: I/O error, dev sdb, sector 407
May  8 15:09:40 MEwebServer kernel: [   18.222398] Buffer I/O error on device sdb, logical block 407
May  8 15:09:40 MEwebServer kernel: [   18.222480] ata4: EH complete
May  8 15:09:40 MEwebServer kernel: [   19.168452] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
May  8 15:09:40 MEwebServer kernel: [   22.129042] AMD64 EDAC driver v3.4.0
May  8 15:09:40 MEwebServer kernel: [   22.129072] EDAC amd64: DRAM ECC disabled.
May  8 15:09:40 MEwebServer kernel: [   22.129077] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May  8 15:09:40 MEwebServer kernel: [   22.129077]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May  8 15:09:40 MEwebServer kernel: [   22.129077]  (Note that use of the override may cause unknown side effects.)
May  8 15:09:40 MEwebServer kernel: [   22.321472] lp: driver loaded but no devices found
May  8 15:09:40 MEwebServer kernel: [   25.157955] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:09:40 MEwebServer kernel: [   25.157960] ata4.00: BMDMA stat 0x24
May  8 15:09:40 MEwebServer kernel: [   25.157963] ata4.00: failed command: READ DMA
May  8 15:09:40 MEwebServer kernel: [   25.157968] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:09:40 MEwebServer kernel: [   25.157968]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:09:40 MEwebServer kernel: [   25.157970] ata4.00: status: { DRDY ERR }
May  8 15:09:40 MEwebServer kernel: [   25.157972] ata4.00: error: { UNC }
May  8 15:09:40 MEwebServer kernel: [   25.181855] ata4.00: configured for UDMA/133
May  8 15:09:40 MEwebServer kernel: [   25.181880] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:09:40 MEwebServer kernel: [   25.181882] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   25.181884] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:09:40 MEwebServer kernel: [   25.181885] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   25.181887] Sense Key : Medium Error [current] [descriptor]
May  8 15:09:40 MEwebServer kernel: [   25.181889] Descriptor sense data with sense descriptors (in hex):
May  8 15:09:40 MEwebServer kernel: [   25.181890]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:09:40 MEwebServer kernel: [   25.181895]         00 00 01 97 
May  8 15:09:40 MEwebServer kernel: [   25.181897] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   25.181900] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:09:40 MEwebServer kernel: [   25.181901] sd 3:0:0:0: [sdb] CDB: 
May  8 15:09:40 MEwebServer kernel: [   25.181902] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:09:40 MEwebServer kernel: [   25.181907] end_request: I/O error, dev sdb, sector 407
May  8 15:09:40 MEwebServer kernel: [   25.181909] Buffer I/O error on device sdb, logical block 407
May  8 15:09:40 MEwebServer kernel: [   25.181933] ata4: EH complete
May  8 15:09:40 MEwebServer kernel: [   28.115733] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:09:40 MEwebServer kernel: [   28.115738] ata4.00: BMDMA stat 0x24
May  8 15:09:40 MEwebServer kernel: [   28.115741] ata4.00: failed command: READ DMA
May  8 15:09:40 MEwebServer kernel: [   28.115746] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:09:40 MEwebServer kernel: [   28.115746]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:09:40 MEwebServer kernel: [   28.115748] ata4.00: status: { DRDY ERR }
May  8 15:09:40 MEwebServer kernel: [   28.115749] ata4.00: error: { UNC }
May  8 15:09:40 MEwebServer kernel: [   28.137644] ata4.00: configured for UDMA/133
May  8 15:09:40 MEwebServer kernel: [   28.137662] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:09:40 MEwebServer kernel: [   28.137664] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   28.137665] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:09:40 MEwebServer kernel: [   28.137667] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   28.137668] Sense Key : Medium Error [current] [descriptor]
May  8 15:09:40 MEwebServer kernel: [   28.137671] Descriptor sense data with sense descriptors (in hex):
May  8 15:09:40 MEwebServer kernel: [   28.137671]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:09:40 MEwebServer kernel: [   28.137676]         00 00 01 97 
May  8 15:09:40 MEwebServer kernel: [   28.137678] sd 3:0:0:0: [sdb]  
May  8 15:09:40 MEwebServer kernel: [   28.137680] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:09:40 MEwebServer kernel: [   28.137682] sd 3:0:0:0: [sdb] CDB: 
May  8 15:09:40 MEwebServer kernel: [   28.137683] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:09:40 MEwebServer kernel: [   28.137688] end_request: I/O error, dev sdb, sector 407
May  8 15:09:40 MEwebServer kernel: [   28.137690] Buffer I/O error on device sdb, logical block 407
May  8 15:09:40 MEwebServer kernel: [   28.137714] ata4: EH complete
May  8 15:09:40 MEwebServer kernel: [   31.530763] Adding 4159484k swap on /dev/sda5.  Priority:-1 extents:1 across:4159484k FS
May  8 15:09:40 MEwebServer kernel: [   31.533963] Adding 4159484k swap on /dev/sdb5.  Priority:-2 extents:1 across:4159484k FS
May  8 15:09:40 MEwebServer kernel: [   32.142692] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro
May  8 15:09:40 MEwebServer kernel: [   32.706927] type=1400 audit(1431094180.179:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=1152 comm="apparmor_parser"
May  8 15:09:40 MEwebServer kernel: [   32.709905] type=1400 audit(1431094180.183:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1151 comm="apparmor_parser"
May  8 15:09:40 MEwebServer kernel: [   32.709914] type=1400 audit(1431094180.183:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1151 comm="apparmor_parser"
May  8 15:09:40 MEwebServer kernel: [   32.709918] type=1400 audit(1431094180.183:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1151 comm="apparmor_parser"
May  8 15:09:40 MEwebServer kernel: [   32.710360] type=1400 audit(1431094180.183:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1151 comm="apparmor_parser"
May  8 15:09:40 MEwebServer kernel: [   32.710365] type=1400 audit(1431094180.183:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1151 comm="apparmor_parser"
May  8 15:09:40 MEwebServer kernel: [   32.710601] type=1400 audit(1431094180.183:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1151 comm="apparmor_parser"
May  8 15:09:40 MEwebServer kernel: [   32.712949] type=1400 audit(1431094180.187:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1154 comm="apparmor_parser"
May  8 15:09:45 MEwebServer kernel: [   38.340393] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=50732 DF PROTO=TCP SPT=1024 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:46 MEwebServer kernel: [   39.310158] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40207 DF PROTO=TCP SPT=1025 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:46 MEwebServer kernel: [   39.339635] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=50733 DF PROTO=TCP SPT=1024 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:46 MEwebServer kernel: [   39.390123] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=32332 DF PROTO=TCP SPT=1026 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:47 MEwebServer kernel: [   39.860092] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=26040 DF PROTO=TCP SPT=1027 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:47 MEwebServer kernel: [   40.150048] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=29942 DF PROTO=TCP SPT=1028 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:47 MEwebServer kernel: [   40.309647] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40208 DF PROTO=TCP SPT=1025 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:47 MEwebServer kernel: [   40.389532] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=32333 DF PROTO=TCP SPT=1026 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:48 MEwebServer kernel: [   40.849502] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=26041 DF PROTO=TCP SPT=1027 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:09:48 MEwebServer kernel: [   41.149429] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.133.216.151 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=29943 DF PROTO=TCP SPT=1028 DPT=25 WINDOW=29200 RES=0x00 SYN URGP=0 
May  8 15:10:53 MEwebServer kernel: [  105.873181] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:f2:01:0c:bb:a6:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  8 15:12:58 MEwebServer kernel: [  230.859988] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:f2:01:0c:bb:a6:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  8 15:13:23 MEwebServer kernel: [  255.628235] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=91.93.199.54 DST=192.168.0.200 LEN=60 TOS=0x18 PREC=0x60 TTL=39 ID=43020 DF PROTO=TCP SPT=39493 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
May  8 15:13:26 MEwebServer kernel: [  258.554630] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=91.93.199.54 DST=192.168.0.200 LEN=60 TOS=0x18 PREC=0x60 TTL=39 ID=43021 DF PROTO=TCP SPT=39493 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
May  8 15:13:30 MEwebServer kernel: [  263.312162] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:40:f2:01:0c:bb:a6:08:00 SRC=81.214.132.137 DST=192.168.0.200 LEN=60 TOS=0x18 PREC=0x60 TTL=45 ID=26426 DF PROTO=TCP SPT=46712 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
May  8 15:15:03 MEwebServer kernel: [  355.846809] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:f2:01:0c:bb:a6:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  8 15:17:50 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpuset
May  8 15:17:50 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpu
May  8 15:17:50 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpuacct
May  8 15:17:50 MEwebServer kernel: [    0.000000] Linux version 3.13.0-52-generic (buildd@comet) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #86-Ubuntu SMP Mon May 4 04:32:59 UTC 2015 (Ubuntu 3.13.0-52.86-generic 3.13.11-ckt18)
May  8 15:17:50 MEwebServer kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic root=UUID=bf21290d-7a02-4713-aaad-c45f755eec04 ro recovery nomodeset
May  8 15:17:50 MEwebServer kernel: [    0.000000] KERNEL supported cpus:
May  8 15:17:50 MEwebServer kernel: [    0.000000]   Intel GenuineIntel
May  8 15:17:50 MEwebServer kernel: [    0.000000]   AMD AuthenticAMD
May  8 15:17:50 MEwebServer kernel: [    0.000000]   Centaur CentaurHauls
May  8 15:17:50 MEwebServer kernel: [    0.000000] e820: BIOS-provided physical RAM map:
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000ddfeffff] usable
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000ddff0000-0x00000000ddff2fff] ACPI NVS
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000ddff3000-0x00000000ddffffff] ACPI data
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000de000000-0x00000000dfffffff] reserved
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
May  8 15:17:50 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
May  8 15:17:50 MEwebServer kernel: [    0.000000] NX (Execute Disable) protection: active
May  8 15:17:50 MEwebServer kernel: [    0.000000] SMBIOS 2.4 present.
May  8 15:17:50 MEwebServer kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. M61PME-S2P/M61PME-S2P, BIOS F2 12/30/2008
May  8 15:17:50 MEwebServer kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
May  8 15:17:50 MEwebServer kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
May  8 15:17:50 MEwebServer kernel: [    0.000000] No AGP bridge found
May  8 15:17:50 MEwebServer kernel: [    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x400000000
May  8 15:17:50 MEwebServer kernel: [    0.000000] MTRR default type: uncachable
May  8 15:17:50 MEwebServer kernel: [    0.000000] MTRR fixed ranges enabled:
May  8 15:17:50 MEwebServer kernel: [    0.000000]   00000-9FFFF write-back
May  8 15:17:50 MEwebServer kernel: [    0.000000]   A0000-BFFFF uncachable
May  8 15:17:50 MEwebServer kernel: [    0.000000]   C0000-C7FFF write-protect
May  8 15:17:50 MEwebServer kernel: [    0.000000]   C8000-EFFFF uncachable
May  8 15:17:50 MEwebServer kernel: [    0.000000]   F0000-FFFFF write-through
May  8 15:17:50 MEwebServer kernel: [    0.000000] MTRR variable ranges enabled:
May  8 15:17:50 MEwebServer kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
May  8 15:17:50 MEwebServer kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
May  8 15:17:50 MEwebServer kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
May  8 15:17:50 MEwebServer kernel: [    0.000000]   3 base 0000DE000000 mask FFFFFE000000 uncachable
May  8 15:17:50 MEwebServer kernel: [    0.000000]   4 base 000100000000 mask FFFFE0000000 write-back
May  8 15:17:50 MEwebServer kernel: [    0.000000]   5 disabled
May  8 15:17:50 MEwebServer kernel: [    0.000000]   6 disabled
May  8 15:17:50 MEwebServer kernel: [    0.000000]   7 disabled
May  8 15:17:50 MEwebServer kernel: [    0.000000] TOM2: 0000000120000000 aka 4608M
May  8 15:17:50 MEwebServer kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  8 15:17:50 MEwebServer kernel: [    0.000000] original variable MTRRs
May  8 15:17:50 MEwebServer kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
May  8 15:17:50 MEwebServer kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
May  8 15:17:50 MEwebServer kernel: [    0.000000] reg 2, base: 3GB, range: 512MB, type WB
May  8 15:17:50 MEwebServer kernel: [    0.000000] reg 3, base: 3552MB, range: 32MB, type UC
May  8 15:17:50 MEwebServer kernel: [    0.000000] reg 4, base: 4GB, range: 512MB, type WB
May  8 15:17:50 MEwebServer kernel: [    0.000000] total RAM covered: 3552M
May  8 15:17:50 MEwebServer kernel: [    0.000000] Found optimal setting for mtrr clean up
May  8 15:17:50 MEwebServer kernel: [    0.000000]  gran_size: 64K 	chunk_size: 1G 	num_reg: 3  	lose cover RAM: 0G
May  8 15:17:50 MEwebServer kernel: [    0.000000] New variable MTRRs
May  8 15:17:50 MEwebServer kernel: [    0.000000] reg 0, base: 0GB, range: 4GB, type WB
May  8 15:17:50 MEwebServer kernel: [    0.000000] reg 1, base: 3552MB, range: 32MB, type UC
May  8 15:17:50 MEwebServer kernel: [    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
May  8 15:17:50 MEwebServer kernel: [    0.000000] e820: update [mem 0xde000000-0xffffffff] usable ==> reserved
May  8 15:17:50 MEwebServer kernel: [    0.000000] e820: last_pfn = 0xddff0 max_arch_pfn = 0x400000000
May  8 15:17:50 MEwebServer kernel: [    0.000000] found SMP MP-table at [mem 0x000f4a90-0x000f4a9f] mapped at [ffff8800000f4a90]
May  8 15:17:50 MEwebServer kernel: [    0.000000] Scanning 1 areas for low memory corruption
May  8 15:17:50 MEwebServer kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
May  8 15:17:50 MEwebServer kernel: [    0.000000] Using GB pages for direct mapping
May  8 15:17:50 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
May  8 15:17:50 MEwebServer kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
May  8 15:17:50 MEwebServer kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
May  8 15:17:50 MEwebServer kernel: [    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
May  8 15:17:50 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x11fe00000-0x11fffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0x11fe00000-0x11fffffff] page 2M
May  8 15:17:50 MEwebServer kernel: [    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
May  8 15:17:50 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x11c000000-0x11fdfffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0x11c000000-0x11fdfffff] page 2M
May  8 15:17:50 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11bffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0x100000000-0x11bffffff] page 2M
May  8 15:17:50 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xddfeffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0xc0000000-0xdddfffff] page 2M
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [mem 0xdde00000-0xddfeffff] page 4k
May  8 15:17:50 MEwebServer kernel: [    0.000000] RAMDISK: [mem 0x35a4c000-0x36d1dfff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: RSDP 00000000000f6460 000014 (v00 GBT   )
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: RSDT 00000000ddff3000 000038 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: FACP 00000000ddff3040 000074 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: DSDT 00000000ddff30c0 0043ED (v01 GBT    NVDAACPI 00001000 MSFT 03000000)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: FACS 00000000ddff0000 000040
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: SSDT 00000000ddff7580 00095E (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: HPET 00000000ddff7f00 000038 (v01 GBT    NVDAACPI 42302E31 NVDA 00000098)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: MCFG 00000000ddff7f40 00003C (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: APIC 00000000ddff74c0 000098 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  8 15:17:50 MEwebServer kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
May  8 15:17:50 MEwebServer kernel: [    0.000000] No NUMA configuration found
May  8 15:17:50 MEwebServer kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011fffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x11fffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]   NODE_DATA [mem 0x11fff9000-0x11fffdfff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011b600000-ffff88011f5fffff] on node 0
May  8 15:17:50 MEwebServer kernel: [    0.000000] Zone ranges:
May  8 15:17:50 MEwebServer kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]   Normal   [mem 0x100000000-0x11fffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] Movable zone start for each node
May  8 15:17:50 MEwebServer kernel: [    0.000000] Early memory node ranges
May  8 15:17:50 MEwebServer kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009efff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]   node   0: [mem 0x00100000-0xddfeffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000]   node   0: [mem 0x100000000-0x11fffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] On node 0 totalpages: 1040270
May  8 15:17:50 MEwebServer kernel: [    0.000000]   DMA zone: 64 pages used for memmap
May  8 15:17:50 MEwebServer kernel: [    0.000000]   DMA zone: 21 pages reserved
May  8 15:17:50 MEwebServer kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
May  8 15:17:50 MEwebServer kernel: [    0.000000]   DMA32 zone: 14144 pages used for memmap
May  8 15:17:50 MEwebServer kernel: [    0.000000]   DMA32 zone: 905200 pages, LIFO batch:31
May  8 15:17:50 MEwebServer kernel: [    0.000000]   Normal zone: 2048 pages used for memmap
May  8 15:17:50 MEwebServer kernel: [    0.000000]   Normal zone: 131072 pages, LIFO batch:31
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  8 15:17:50 MEwebServer kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: IRQ0 used by override.
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: IRQ2 used by override.
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: IRQ9 used by override.
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: IRQ14 used by override.
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: IRQ15 used by override.
May  8 15:17:50 MEwebServer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  8 15:17:50 MEwebServer kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
May  8 15:17:50 MEwebServer kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
May  8 15:17:50 MEwebServer kernel: [    0.000000] nr_irqs_gsi: 40
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xddff0000-0xddff2fff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xddff3000-0xddffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xde000000-0xdfffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] e820: [mem 0xe0000000-0xefffffff] available for PCI devices
May  8 15:17:50 MEwebServer kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  8 15:17:50 MEwebServer kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
May  8 15:17:50 MEwebServer kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88011fc00000 s81536 r8192 d20864 u524288
May  8 15:17:50 MEwebServer kernel: [    0.000000] pcpu-alloc: s81536 r8192 d20864 u524288 alloc=1*2097152
May  8 15:17:50 MEwebServer kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
May  8 15:17:50 MEwebServer kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1023993
May  8 15:17:50 MEwebServer kernel: [    0.000000] Policy zone: Normal
May  8 15:17:50 MEwebServer kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic root=UUID=bf21290d-7a02-4713-aaad-c45f755eec04 ro recovery nomodeset
May  8 15:17:50 MEwebServer kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.000000] Checking aperture...
May  8 15:17:50 MEwebServer kernel: [    0.000000] No AGP bridge found
May  8 15:17:50 MEwebServer kernel: [    0.000000] Node 0: aperture @ d4000000 size 32 MB
May  8 15:17:50 MEwebServer kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
May  8 15:17:50 MEwebServer kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
May  8 15:17:50 MEwebServer kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
May  8 15:17:50 MEwebServer kernel: [    0.000000] This costs you 64 MB of RAM
May  8 15:17:50 MEwebServer kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ d4000000
May  8 15:17:50 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd4000000-0xd7ffffff]
May  8 15:17:50 MEwebServer kernel: [    0.000000] Memory: 3927608K/4161080K available (7389K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 233472K reserved)
May  8 15:17:50 MEwebServer kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May  8 15:17:50 MEwebServer kernel: [    0.000000] Hierarchical RCU implementation.
May  8 15:17:50 MEwebServer kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
May  8 15:17:50 MEwebServer kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
May  8 15:17:50 MEwebServer kernel: [    0.000000] 	Offload RCU callbacks from all CPUs
May  8 15:17:50 MEwebServer kernel: [    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
May  8 15:17:50 MEwebServer kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
May  8 15:17:50 MEwebServer kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
May  8 15:17:50 MEwebServer kernel: [    0.000000] Console: colour VGA+ 80x25
May  8 15:17:50 MEwebServer kernel: [    0.000000] console [tty0] enabled
May  8 15:17:50 MEwebServer kernel: [    0.000000] allocated 16777216 bytes of page_cgroup
May  8 15:17:50 MEwebServer kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  8 15:17:50 MEwebServer kernel: [    0.000000] hpet clockevent registered
May  8 15:17:50 MEwebServer kernel: [    0.000000] tsc: Fast TSC calibration using PIT
May  8 15:17:50 MEwebServer kernel: [    0.004000] tsc: Detected 2812.740 MHz processor
May  8 15:17:50 MEwebServer kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5625.48 BogoMIPS (lpj=11250960)
May  8 15:17:50 MEwebServer kernel: [    0.000122] pid_max: default: 32768 minimum: 301
May  8 15:17:50 MEwebServer kernel: [    0.000207] Security Framework initialized
May  8 15:17:50 MEwebServer kernel: [    0.000282] AppArmor: AppArmor initialized
May  8 15:17:50 MEwebServer kernel: [    0.000339] Yama: becoming mindful.
May  8 15:17:50 MEwebServer kernel: [    0.000679] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.002116] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.002798] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.002866] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.003150] Initializing cgroup subsys memory
May  8 15:17:50 MEwebServer kernel: [    0.003214] Initializing cgroup subsys devices
May  8 15:17:50 MEwebServer kernel: [    0.003272] Initializing cgroup subsys freezer
May  8 15:17:50 MEwebServer kernel: [    0.003330] Initializing cgroup subsys blkio
May  8 15:17:50 MEwebServer kernel: [    0.003388] Initializing cgroup subsys perf_event
May  8 15:17:50 MEwebServer kernel: [    0.003447] Initializing cgroup subsys hugetlb
May  8 15:17:50 MEwebServer kernel: [    0.003523] tseg: 0000000000
May  8 15:17:50 MEwebServer kernel: [    0.003530] CPU: Physical Processor ID: 0
May  8 15:17:50 MEwebServer kernel: [    0.003587] CPU: Processor Core ID: 0
May  8 15:17:50 MEwebServer kernel: [    0.003644] mce: CPU supports 6 MCE banks
May  8 15:17:50 MEwebServer kernel: [    0.003706] LVT offset 0 assigned for vector 0xf9
May  8 15:17:50 MEwebServer kernel: [    0.003767] process: using AMD E400 aware idle routine
May  8 15:17:50 MEwebServer kernel: [    0.003827] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
May  8 15:17:50 MEwebServer kernel: [    0.003827] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
May  8 15:17:50 MEwebServer kernel: [    0.003827] tlb_flushall_shift: 4
May  8 15:17:50 MEwebServer kernel: [    0.004007] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
May  8 15:17:50 MEwebServer kernel: [    0.004823] ACPI: Core revision 20131115
May  8 15:17:50 MEwebServer kernel: [    0.006642] ACPI: All ACPI Tables successfully acquired
May  8 15:17:50 MEwebServer kernel: [    0.008157] ftrace: allocating 28576 entries in 112 pages
May  8 15:17:50 MEwebServer kernel: [    0.020081] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  8 15:17:50 MEwebServer kernel: [    0.059821] smpboot: CPU0: AMD Athlon(tm) X2 240e Processor (fam: 10, model: 06, stepping: 02)
May  8 15:17:50 MEwebServer kernel: [    0.165877] Performance Events: AMD PMU driver.
May  8 15:17:50 MEwebServer kernel: [    0.165981] ... version:                0
May  8 15:17:50 MEwebServer kernel: [    0.166038] ... bit width:              48
May  8 15:17:50 MEwebServer kernel: [    0.166094] ... generic registers:      4
May  8 15:17:50 MEwebServer kernel: [    0.166151] ... value mask:             0000ffffffffffff
May  8 15:17:50 MEwebServer kernel: [    0.166210] ... max period:             00007fffffffffff
May  8 15:17:50 MEwebServer kernel: [    0.166268] ... fixed-purpose events:   0
May  8 15:17:50 MEwebServer kernel: [    0.166325] ... event mask:             000000000000000f
May  8 15:17:50 MEwebServer kernel: [    0.167844] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
May  8 15:17:50 MEwebServer kernel: [    0.167991] x86: Booting SMP configuration:
May  8 15:17:50 MEwebServer kernel: [    0.168049] .... node  #0, CPUs:      #1
May  8 15:17:50 MEwebServer kernel: [    0.181230] x86: Booted up 1 node, 2 CPUs
May  8 15:17:50 MEwebServer kernel: [    0.181340] smpboot: Total of 2 processors activated (11250.96 BogoMIPS)
May  8 15:17:50 MEwebServer kernel: [    0.182095] devtmpfs: initialized
May  8 15:17:50 MEwebServer kernel: [    0.185348] EVM: security.selinux
May  8 15:17:50 MEwebServer kernel: [    0.185405] EVM: security.SMACK64
May  8 15:17:50 MEwebServer kernel: [    0.185461] EVM: security.ima
May  8 15:17:50 MEwebServer kernel: [    0.185517] EVM: security.capability
May  8 15:17:50 MEwebServer kernel: [    0.185640] PM: Registering ACPI NVS region [mem 0xddff0000-0xddff2fff] (12288 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.186641] pinctrl core: initialized pinctrl subsystem
May  8 15:17:50 MEwebServer kernel: [    0.186769] regulator-dummy: no parameters
May  8 15:17:50 MEwebServer kernel: [    0.186860] RTC time: 14:17:17, date: 05/08/15
May  8 15:17:50 MEwebServer kernel: [    0.186959] NET: Registered protocol family 16
May  8 15:17:50 MEwebServer kernel: [    0.187112] cpuidle: using governor ladder
May  8 15:17:50 MEwebServer kernel: [    0.187170] cpuidle: using governor menu
May  8 15:17:50 MEwebServer kernel: [    0.187231] node 0 link 0: io port [1000, fffff]
May  8 15:17:50 MEwebServer kernel: [    0.187233] TOM: 00000000e0000000 aka 3584M
May  8 15:17:50 MEwebServer kernel: [    0.187291] Fam 10h mmconf [mem 0xf0000000-0xf00fffff]
May  8 15:17:50 MEwebServer kernel: [    0.187293] node 0 link 0: mmio [f0000000, f7ffffff] ==> [f0100000, f7ffffff]
May  8 15:17:50 MEwebServer kernel: [    0.187296] node 0 link 0: mmio [f8000000, ffb7ffff]
May  8 15:17:50 MEwebServer kernel: [    0.187298] node 0 link 0: mmio [a0000, bffff]
May  8 15:17:50 MEwebServer kernel: [    0.187299] node 0 link 0: mmio [e0000000, efffffff]
May  8 15:17:50 MEwebServer kernel: [    0.187300] TOM2: 0000000120000000 aka 4608M
May  8 15:17:50 MEwebServer kernel: [    0.187358] bus: [bus 00-ff] on node 0 link 0
May  8 15:17:50 MEwebServer kernel: [    0.187360] bus: 00 [io  0x0000-0xffff]
May  8 15:17:50 MEwebServer kernel: [    0.187361] bus: 00 [mem 0xf0100000-0xffffffff]
May  8 15:17:50 MEwebServer kernel: [    0.187362] bus: 00 [mem 0x000a0000-0x000bffff]
May  8 15:17:50 MEwebServer kernel: [    0.187363] bus: 00 [mem 0xe0000000-0xefffffff]
May  8 15:17:50 MEwebServer kernel: [    0.187364] bus: 00 [mem 0x120000000-0xfcffffffff]
May  8 15:17:50 MEwebServer kernel: [    0.187407] ACPI: bus type PCI registered
May  8 15:17:50 MEwebServer kernel: [    0.187465] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
May  8 15:17:50 MEwebServer kernel: [    0.187579] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
May  8 15:17:50 MEwebServer kernel: [    0.187653] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
May  8 15:17:50 MEwebServer kernel: [    0.194147] PCI: Using configuration type 1 for base access
May  8 15:17:50 MEwebServer kernel: [    0.195084] bio: create slab <bio-0> at 0
May  8 15:17:50 MEwebServer kernel: [    0.195317] ACPI: Added _OSI(Module Device)
May  8 15:17:50 MEwebServer kernel: [    0.195375] ACPI: Added _OSI(Processor Device)
May  8 15:17:50 MEwebServer kernel: [    0.195432] ACPI: Added _OSI(3.0 _SCP Extensions)
May  8 15:17:50 MEwebServer kernel: [    0.195490] ACPI: Added _OSI(Processor Aggregator Device)
May  8 15:17:50 MEwebServer kernel: [    0.199185] ACPI: Interpreter enabled
May  8 15:17:50 MEwebServer kernel: [    0.199248] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
May  8 15:17:50 MEwebServer kernel: [    0.199407] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
May  8 15:17:50 MEwebServer kernel: [    0.199574] ACPI: (supports S0 S3 S4 S5)
May  8 15:17:50 MEwebServer kernel: [    0.199631] ACPI: Using IOAPIC for interrupt routing
May  8 15:17:50 MEwebServer kernel: [    0.199707] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
May  8 15:17:50 MEwebServer kernel: [    0.199873] ACPI: No dock devices found.
May  8 15:17:50 MEwebServer kernel: [    0.204742] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
May  8 15:17:50 MEwebServer kernel: [    0.204806] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
May  8 15:17:50 MEwebServer kernel: [    0.204880] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
May  8 15:17:50 MEwebServer kernel: [    0.204988] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
May  8 15:17:50 MEwebServer kernel: [    0.205189] PCI host bridge to bus 0000:00
May  8 15:17:50 MEwebServer kernel: [    0.205249] pci_bus 0000:00: root bus resource [bus 00-ff]
May  8 15:17:50 MEwebServer kernel: [    0.205309] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
May  8 15:17:50 MEwebServer kernel: [    0.205369] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
May  8 15:17:50 MEwebServer kernel: [    0.205429] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
May  8 15:17:50 MEwebServer kernel: [    0.205490] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
May  8 15:17:50 MEwebServer kernel: [    0.205551] pci_bus 0000:00: root bus resource [mem 0xde000000-0xfebfffff]
May  8 15:17:50 MEwebServer kernel: [    0.205631] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
May  8 15:17:50 MEwebServer kernel: [    0.205845] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
May  8 15:17:50 MEwebServer kernel: [    0.205928] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
May  8 15:17:50 MEwebServer kernel: [    0.205938] pci 0000:00:01.1: reg 0x10: [io  0xc000-0xc03f]
May  8 15:17:50 MEwebServer kernel: [    0.205952] pci 0000:00:01.1: reg 0x20: [io  0x1c00-0x1c3f]
May  8 15:17:50 MEwebServer kernel: [    0.205956] pci 0000:00:01.1: reg 0x24: [io  0xc800-0xc83f]
May  8 15:17:50 MEwebServer kernel: [    0.205982] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  8 15:17:50 MEwebServer kernel: [    0.206048] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
May  8 15:17:50 MEwebServer kernel: [    0.206127] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
May  8 15:17:50 MEwebServer kernel: [    0.206192] pci 0000:00:04.0: System wakeup disabled by ACPI
May  8 15:17:50 MEwebServer kernel: [    0.206274] pci 0000:00:06.0: [10de:03ec] type 00 class 0x01018a
May  8 15:17:50 MEwebServer kernel: [    0.206293] pci 0000:00:06.0: reg 0x20: [io  0xf000-0xf00f]
May  8 15:17:50 MEwebServer kernel: [    0.206368] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
May  8 15:17:50 MEwebServer kernel: [    0.206377] pci 0000:00:07.0: reg 0x10: [mem 0xfb000000-0xfb000fff]
May  8 15:17:50 MEwebServer kernel: [    0.206381] pci 0000:00:07.0: reg 0x14: [io  0xcc00-0xcc07]
May  8 15:17:50 MEwebServer kernel: [    0.206411] pci 0000:00:07.0: supports D1 D2
May  8 15:17:50 MEwebServer kernel: [    0.206413] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
May  8 15:17:50 MEwebServer kernel: [    0.206457] pci 0000:00:07.0: System wakeup disabled by ACPI
May  8 15:17:50 MEwebServer kernel: [    0.206539] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
May  8 15:17:50 MEwebServer kernel: [    0.206546] pci 0000:00:08.0: reg 0x10: [io  0x09f0-0x09f7]
May  8 15:17:50 MEwebServer kernel: [    0.206549] pci 0000:00:08.0: reg 0x14: [io  0x0bf0-0x0bf3]
May  8 15:17:50 MEwebServer kernel: [    0.206553] pci 0000:00:08.0: reg 0x18: [io  0x0970-0x0977]
May  8 15:17:50 MEwebServer kernel: [    0.206556] pci 0000:00:08.0: reg 0x1c: [io  0x0b70-0x0b73]
May  8 15:17:50 MEwebServer kernel: [    0.206560] pci 0000:00:08.0: reg 0x20: [io  0xe000-0xe00f]
May  8 15:17:50 MEwebServer kernel: [    0.206564] pci 0000:00:08.0: reg 0x24: [mem 0xfb001000-0xfb001fff]
May  8 15:17:50 MEwebServer kernel: [    0.206642] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
May  8 15:17:50 MEwebServer kernel: [    0.206648] pci 0000:00:0d.0: reg 0x10: [mem 0xf8000000-0xf8ffffff]
May  8 15:17:50 MEwebServer kernel: [    0.206653] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
May  8 15:17:50 MEwebServer kernel: [    0.206657] pci 0000:00:0d.0: reg 0x1c: [mem 0xf9000000-0xf9ffffff 64bit]
May  8 15:17:50 MEwebServer kernel: [    0.206662] pci 0000:00:0d.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
May  8 15:17:50 MEwebServer kernel: [    0.206732] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
May  8 15:17:50 MEwebServer kernel: [    0.206793] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
May  8 15:17:50 MEwebServer kernel: [    0.206849] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
May  8 15:17:50 MEwebServer kernel: [    0.206906] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
May  8 15:17:50 MEwebServer kernel: [    0.206967] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
May  8 15:17:50 MEwebServer kernel: [    0.207074] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
May  8 15:17:50 MEwebServer kernel: [    0.207136] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
May  8 15:17:50 MEwebServer kernel: [    0.207139] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
May  8 15:17:50 MEwebServer kernel: [    0.207141] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May  8 15:17:50 MEwebServer kernel: [    0.207143] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May  8 15:17:50 MEwebServer kernel: [    0.207144] pci 0000:00:04.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
May  8 15:17:50 MEwebServer kernel: [    0.207146] pci 0000:00:04.0:   bridge window [mem 0xde000000-0xfebfffff] (subtractive decode)
May  8 15:17:50 MEwebServer kernel: [    0.207520] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.208092] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.208662] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.209233] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.209802] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.210371] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.210940] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.211509] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.212079] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
May  8 15:17:50 MEwebServer kernel: [    0.212559] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.213129] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 *7 9 10 11 14 15)
May  8 15:17:50 MEwebServer kernel: [    0.213610] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
May  8 15:17:50 MEwebServer kernel: [    0.214088] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.214657] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.215227] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
May  8 15:17:50 MEwebServer kernel: [    0.215702] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.216271] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.216840] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
May  8 15:17:50 MEwebServer kernel: [    0.217320] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.217917] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.218244] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.218570] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.218895] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.219221] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.219546] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.219871] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.220197] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.220522] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
May  8 15:17:50 MEwebServer kernel: [    0.220932] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
May  8 15:17:50 MEwebServer kernel: [    0.221345] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
May  8 15:17:50 MEwebServer kernel: [    0.221755] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.222209] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.222663] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
May  8 15:17:50 MEwebServer kernel: [    0.223073] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.223526] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.223981] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.224435] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
May  8 15:17:50 MEwebServer kernel: [    0.224846] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
May  8 15:17:50 MEwebServer kernel: [    0.225329] ACPI: \_SB_.PCI0: notify handler is installed
May  8 15:17:50 MEwebServer kernel: [    0.225359] Found 1 acpi root devices
May  8 15:17:50 MEwebServer kernel: [    0.225481] vgaarb: setting as boot device: PCI:0000:00:0d.0
May  8 15:17:50 MEwebServer kernel: [    0.225541] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
May  8 15:17:50 MEwebServer kernel: [    0.225612] vgaarb: loaded
May  8 15:17:50 MEwebServer kernel: [    0.225668] vgaarb: bridge control possible 0000:00:0d.0
May  8 15:17:50 MEwebServer kernel: [    0.225885] SCSI subsystem initialized
May  8 15:17:50 MEwebServer kernel: [    0.226022] libata version 3.00 loaded.
May  8 15:17:50 MEwebServer kernel: [    0.226049] ACPI: bus type USB registered
May  8 15:17:50 MEwebServer kernel: [    0.226126] usbcore: registered new interface driver usbfs
May  8 15:17:50 MEwebServer kernel: [    0.226192] usbcore: registered new interface driver hub
May  8 15:17:50 MEwebServer kernel: [    0.226291] usbcore: registered new device driver usb
May  8 15:17:50 MEwebServer kernel: [    0.226458] PCI: Using ACPI for IRQ routing
May  8 15:17:50 MEwebServer kernel: [    0.229452] PCI: pci_cache_line_size set to 64 bytes
May  8 15:17:50 MEwebServer kernel: [    0.229475] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
May  8 15:17:50 MEwebServer kernel: [    0.229477] e820: reserve RAM buffer [mem 0xddff0000-0xdfffffff]
May  8 15:17:50 MEwebServer kernel: [    0.229569] NetLabel: Initializing
May  8 15:17:50 MEwebServer kernel: [    0.229625] NetLabel:  domain hash size = 128
May  8 15:17:50 MEwebServer kernel: [    0.229682] NetLabel:  protocols = UNLABELED CIPSOv4
May  8 15:17:50 MEwebServer kernel: [    0.229750] NetLabel:  unlabeled traffic allowed by default
May  8 15:17:50 MEwebServer kernel: [    0.229904] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May  8 15:17:50 MEwebServer kernel: [    0.229969] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
May  8 15:17:50 MEwebServer kernel: [    0.230199] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
May  8 15:17:50 MEwebServer kernel: [    0.232398] Switched to clocksource hpet
May  8 15:17:50 MEwebServer kernel: [    0.236976] AppArmor: AppArmor Filesystem Enabled
May  8 15:17:50 MEwebServer kernel: [    0.237068] pnp: PnP ACPI init
May  8 15:17:50 MEwebServer kernel: [    0.237137] ACPI: bus type PNP registered
May  8 15:17:50 MEwebServer kernel: [    0.237348] system 00:00: [io  0x1000-0x107f] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237409] system 00:00: [io  0x1080-0x10ff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237469] system 00:00: [io  0x1400-0x147f] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237529] system 00:00: [io  0x1480-0x14ff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237589] system 00:00: [io  0x1800-0x187f] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237649] system 00:00: [io  0x1880-0x18ff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237710] system 00:00: [mem 0xfefe0000-0xfefe01ff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237770] system 00:00: [mem 0xfefe1000-0xfefe10ff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237831] system 00:00: [mem 0xde000000-0xdfffffff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.237894] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:17:50 MEwebServer kernel: [    0.237959] system 00:01: [io  0x04d0-0x04d1] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.238020] system 00:01: [io  0x0800-0x087f] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.238080] system 00:01: [io  0x0295-0x0296] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.238140] system 00:01: [io  0x0290-0x0294] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.238200] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:17:50 MEwebServer kernel: [    0.238209] pnp 00:02: [dma 4]
May  8 15:17:50 MEwebServer kernel: [    0.238227] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
May  8 15:17:50 MEwebServer kernel: [    0.238283] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
May  8 15:17:50 MEwebServer kernel: [    0.238314] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
May  8 15:17:50 MEwebServer kernel: [    0.238334] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
May  8 15:17:50 MEwebServer kernel: [    0.238357] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
May  8 15:17:50 MEwebServer kernel: [    0.238624] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
May  8 15:17:50 MEwebServer kernel: [    0.239037] system 00:08: [mem 0xf0000000-0xf7ffffff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.239098] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:17:50 MEwebServer kernel: [    0.239210] system 00:09: [mem 0x000cec00-0x000cffff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.239271] system 00:09: [mem 0x000f0000-0x000f7fff] could not be reserved
May  8 15:17:50 MEwebServer kernel: [    0.239333] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
May  8 15:17:50 MEwebServer kernel: [    0.239394] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
May  8 15:17:50 MEwebServer kernel: [    0.239455] system 00:09: [mem 0xddff0000-0xddffffff] could not be reserved
May  8 15:17:50 MEwebServer kernel: [    0.239517] system 00:09: [mem 0xffff0000-0xffffffff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.239578] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
May  8 15:17:50 MEwebServer kernel: [    0.239639] system 00:09: [mem 0x00100000-0xddfeffff] could not be reserved
May  8 15:17:50 MEwebServer kernel: [    0.239701] system 00:09: [mem 0xde000000-0xdfffffff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.239761] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
May  8 15:17:50 MEwebServer kernel: [    0.239823] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
May  8 15:17:50 MEwebServer kernel: [    0.239884] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
May  8 15:17:50 MEwebServer kernel: [    0.239896] pnp: PnP ACPI: found 10 devices
May  8 15:17:50 MEwebServer kernel: [    0.239953] ACPI: bus type PNP unregistered
May  8 15:17:50 MEwebServer kernel: [    0.246215] pci 0000:00:0d.0: BAR 6: assigned [mem 0xfa000000-0xfa01ffff pref]
May  8 15:17:50 MEwebServer kernel: [    0.246287] pci 0000:00:04.0: PCI bridge to [bus 01]
May  8 15:17:50 MEwebServer kernel: [    0.246346] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
May  8 15:17:50 MEwebServer kernel: [    0.246412] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
May  8 15:17:50 MEwebServer kernel: [    0.246413] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
May  8 15:17:50 MEwebServer kernel: [    0.246415] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
May  8 15:17:50 MEwebServer kernel: [    0.246417] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
May  8 15:17:50 MEwebServer kernel: [    0.246418] pci_bus 0000:00: resource 8 [mem 0xde000000-0xfebfffff]
May  8 15:17:50 MEwebServer kernel: [    0.246420] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
May  8 15:17:50 MEwebServer kernel: [    0.246422] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
May  8 15:17:50 MEwebServer kernel: [    0.246423] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
May  8 15:17:50 MEwebServer kernel: [    0.246425] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
May  8 15:17:50 MEwebServer kernel: [    0.246426] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
May  8 15:17:50 MEwebServer kernel: [    0.246428] pci_bus 0000:01: resource 8 [mem 0xde000000-0xfebfffff]
May  8 15:17:50 MEwebServer kernel: [    0.246459] NET: Registered protocol family 2
May  8 15:17:50 MEwebServer kernel: [    0.246701] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.246879] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.247094] TCP: Hash tables configured (established 32768 bind 32768)
May  8 15:17:50 MEwebServer kernel: [    0.247196] TCP: reno registered
May  8 15:17:50 MEwebServer kernel: [    0.247260] UDP hash table entries: 2048 (order: 4, 65536 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.247345] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.247492] NET: Registered protocol family 1
May  8 15:17:50 MEwebServer kernel: [    0.247630] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:17:50 MEwebServer kernel: [    0.247735] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:17:50 MEwebServer kernel: [    0.247838] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:17:50 MEwebServer kernel: [    0.247901] pci 0000:00:0d.0: Video device with shadowed ROM
May  8 15:17:50 MEwebServer kernel: [    0.247911] PCI: CLS 0 bytes, default 64
May  8 15:17:50 MEwebServer kernel: [    0.247990] Trying to unpack rootfs image as initramfs...
May  8 15:17:50 MEwebServer kernel: [    0.542804] Freeing initrd memory: 19272K (ffff880035a4c000 - ffff880036d1e000)
May  8 15:17:50 MEwebServer kernel: [    0.543044] PCI-DMA: Disabling AGP.
May  8 15:17:50 MEwebServer kernel: [    0.543169] PCI-DMA: aperture base @ d4000000 size 65536 KB
May  8 15:17:50 MEwebServer kernel: [    0.543228] PCI-DMA: using GART IOMMU.
May  8 15:17:50 MEwebServer kernel: [    0.543286] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
May  8 15:17:50 MEwebServer kernel: [    0.546140] LVT offset 1 assigned for vector 0x400
May  8 15:17:50 MEwebServer kernel: [    0.546209] IBS: LVT offset 1 assigned
May  8 15:17:50 MEwebServer kernel: [    0.546287] perf: AMD IBS detected (0x0000001f)
May  8 15:17:50 MEwebServer kernel: [    0.546390] microcode: CPU0: patch_level=0x00000000
May  8 15:17:50 MEwebServer kernel: [    0.546455] microcode: CPU1: patch_level=0x00000000
May  8 15:17:50 MEwebServer kernel: [    0.546580] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
May  8 15:17:50 MEwebServer kernel: [    0.546652] Scanning for low memory corruption every 60 seconds
May  8 15:17:50 MEwebServer kernel: [    0.546918] Initialise system trusted keyring
May  8 15:17:50 MEwebServer kernel: [    0.547019] audit: initializing netlink socket (disabled)
May  8 15:17:50 MEwebServer kernel: [    0.547089] type=2000 audit(1431094637.440:1): initialized
May  8 15:17:50 MEwebServer kernel: [    0.573122] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  8 15:17:50 MEwebServer kernel: [    0.574291] zbud: loaded
May  8 15:17:50 MEwebServer kernel: [    0.574514] VFS: Disk quotas dquot_6.5.2
May  8 15:17:50 MEwebServer kernel: [    0.574628] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May  8 15:17:50 MEwebServer kernel: [    0.575178] fuse init (API version 7.22)
May  8 15:17:50 MEwebServer kernel: [    0.575320] msgmni has been set to 7837
May  8 15:17:50 MEwebServer kernel: [    0.575438] Key type big_key registered
May  8 15:17:50 MEwebServer kernel: [    0.575818] Key type asymmetric registered
May  8 15:17:50 MEwebServer kernel: [    0.575877] Asymmetric key parser 'x509' registered
May  8 15:17:50 MEwebServer kernel: [    0.575961] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
May  8 15:17:50 MEwebServer kernel: [    0.576058] io scheduler noop registered
May  8 15:17:50 MEwebServer kernel: [    0.576116] io scheduler deadline registered (default)
May  8 15:17:50 MEwebServer kernel: [    0.578526] io scheduler cfq registered
May  8 15:17:50 MEwebServer kernel: [    0.578651] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  8 15:17:50 MEwebServer kernel: [    0.578723] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  8 15:17:50 MEwebServer kernel: [    0.578820] ipmi message handler version 39.2
May  8 15:17:50 MEwebServer kernel: [    0.578936] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
May  8 15:17:50 MEwebServer kernel: [    0.579009] ACPI: Power Button [PWRB]
May  8 15:17:50 MEwebServer kernel: [    0.579100] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  8 15:17:50 MEwebServer kernel: [    0.579171] ACPI: Power Button [PWRF]
May  8 15:17:50 MEwebServer kernel: [    0.579314] GHES: HEST is not enabled!
May  8 15:17:50 MEwebServer kernel: [    0.579447] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May  8 15:17:50 MEwebServer kernel: [    0.580640] Linux agpgart interface v0.103
May  8 15:17:50 MEwebServer kernel: [    0.581843] brd: module loaded
May  8 15:17:50 MEwebServer kernel: [    0.582485] loop: module loaded
May  8 15:17:50 MEwebServer kernel: [    0.582853] libphy: Fixed MDIO Bus: probed
May  8 15:17:50 MEwebServer kernel: [    0.582983] tun: Universal TUN/TAP device driver, 1.6
May  8 15:17:50 MEwebServer kernel: [    0.583041] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  8 15:17:50 MEwebServer kernel: [    0.583179] PPP generic driver version 2.4.2
May  8 15:17:50 MEwebServer kernel: [    0.583270] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  8 15:17:50 MEwebServer kernel: [    0.583332] ehci-pci: EHCI PCI platform driver
May  8 15:17:50 MEwebServer kernel: [    0.583398] ehci-platform: EHCI generic platform driver
May  8 15:17:50 MEwebServer kernel: [    0.583460] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  8 15:17:50 MEwebServer kernel: [    0.583520] ohci-pci: OHCI PCI platform driver
May  8 15:17:50 MEwebServer kernel: [    0.583583] ohci-platform: OHCI generic platform driver
May  8 15:17:50 MEwebServer kernel: [    0.583645] uhci_hcd: USB Universal Host Controller Interface driver
May  8 15:17:50 MEwebServer kernel: [    0.583745] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  8 15:17:50 MEwebServer kernel: [    0.583806] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  8 15:17:50 MEwebServer kernel: [    0.584022] serio: i8042 KBD port at 0x60,0x64 irq 1
May  8 15:17:50 MEwebServer kernel: [    0.584191] mousedev: PS/2 mouse device common for all mice
May  8 15:17:50 MEwebServer kernel: [    0.584372] rtc_cmos 00:04: RTC can wake from S4
May  8 15:17:50 MEwebServer kernel: [    0.584580] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
May  8 15:17:50 MEwebServer kernel: [    0.584671] rtc_cmos 00:04: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
May  8 15:17:50 MEwebServer kernel: [    0.584795] device-mapper: uevent: version 1.0.3
May  8 15:17:50 MEwebServer kernel: [    0.584902] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
May  8 15:17:50 MEwebServer kernel: [    0.584980] ledtrig-cpu: registered to indicate activity on CPUs
May  8 15:17:50 MEwebServer kernel: [    0.585135] TCP: cubic registered
May  8 15:17:50 MEwebServer kernel: [    0.585259] NET: Registered protocol family 10
May  8 15:17:50 MEwebServer kernel: [    0.585459] NET: Registered protocol family 17
May  8 15:17:50 MEwebServer kernel: [    0.585525] Key type dns_resolver registered
May  8 15:17:50 MEwebServer kernel: [    0.585790] Loading compiled-in X.509 certificates
May  8 15:17:50 MEwebServer kernel: [    0.586816] Loaded X.509 cert 'Magrathea: Glacier signing key: 1981bc916ffc00599231ec5630e666e0256fd6f1'
May  8 15:17:50 MEwebServer kernel: [    0.586912] registered taskstats version 1
May  8 15:17:50 MEwebServer kernel: [    0.588799] Key type trusted registered
May  8 15:17:50 MEwebServer kernel: [    0.591741] Key type encrypted registered
May  8 15:17:50 MEwebServer kernel: [    0.591803] AppArmor: AppArmor sha1 policy hashing enabled
May  8 15:17:50 MEwebServer kernel: [    0.591863] IMA: No TPM chip found, activating TPM-bypass!
May  8 15:17:50 MEwebServer kernel: [    0.592040] regulator-dummy: disabling
May  8 15:17:50 MEwebServer kernel: [    0.592137]   Magic number: 15:796:282
May  8 15:17:50 MEwebServer kernel: [    0.592226] tty tty19: hash matches
May  8 15:17:50 MEwebServer kernel: [    0.592364] rtc_cmos 00:04: setting system clock to 2015-05-08 14:17:18 UTC (1431094638)
May  8 15:17:50 MEwebServer kernel: [    0.592524] acpi-cpufreq: overriding BIOS provided _PSD data
May  8 15:17:50 MEwebServer kernel: [    0.592643] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  8 15:17:50 MEwebServer kernel: [    0.592703] EDD information not available.
May  8 15:17:50 MEwebServer kernel: [    0.592784] PM: Hibernation image not present or could not be loaded.
May  8 15:17:50 MEwebServer kernel: [    0.594161] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
May  8 15:17:50 MEwebServer kernel: [    0.594238] Write protecting the kernel read-only data: 12288k
May  8 15:17:50 MEwebServer kernel: [    0.596470] Freeing unused kernel memory: 792K (ffff88000173a000 - ffff880001800000)
May  8 15:17:50 MEwebServer kernel: [    0.598328] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
May  8 15:17:50 MEwebServer kernel: [    0.609038] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
May  8 15:17:50 MEwebServer kernel: [    0.621846] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
May  8 15:17:50 MEwebServer kernel: [    0.622121] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
May  8 15:17:50 MEwebServer kernel: [    0.625883] md: linear personality registered for level -1
May  8 15:17:50 MEwebServer kernel: [    0.628198] md: multipath personality registered for level -4
May  8 15:17:50 MEwebServer kernel: [    0.630683] md: raid0 personality registered for level 0
May  8 15:17:50 MEwebServer kernel: [    0.633377] md: raid1 personality registered for level 1
May  8 15:17:50 MEwebServer kernel: [    0.700358] raid6: sse2x1    3826 MB/s
May  8 15:17:50 MEwebServer kernel: [    0.768338] raid6: sse2x2    5620 MB/s
May  8 15:17:50 MEwebServer kernel: [    0.836330] raid6: sse2x4    6666 MB/s
May  8 15:17:50 MEwebServer kernel: [    0.836388] raid6: using algorithm sse2x4 (6666 MB/s)
May  8 15:17:50 MEwebServer kernel: [    0.836446] raid6: using intx1 recovery algorithm
May  8 15:17:50 MEwebServer kernel: [    0.837684] xor: measuring software checksum speed
May  8 15:17:50 MEwebServer kernel: [    0.876319]    prefetch64-sse: 11517.000 MB/sec
May  8 15:17:50 MEwebServer kernel: [    0.916314]    generic_sse: 10881.000 MB/sec
May  8 15:17:50 MEwebServer kernel: [    0.916372] xor: using function: prefetch64-sse (11517.000 MB/sec)
May  8 15:17:50 MEwebServer kernel: [    0.917525] async_tx: api initialized (async)
May  8 15:17:50 MEwebServer kernel: [    0.924335] md: raid6 personality registered for level 6
May  8 15:17:50 MEwebServer kernel: [    0.924396] md: raid5 personality registered for level 5
May  8 15:17:50 MEwebServer kernel: [    0.924455] md: raid4 personality registered for level 4
May  8 15:17:50 MEwebServer kernel: [    0.930050] md: raid10 personality registered for level 10
May  8 15:17:50 MEwebServer kernel: [    1.145055] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:24:1d:66:65:be
May  8 15:17:50 MEwebServer kernel: [    1.145133] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
May  8 15:17:50 MEwebServer kernel: [    1.145230] pata_amd 0000:00:06.0: version 0.4.1
May  8 15:17:50 MEwebServer kernel: [    1.145767] scsi0 : pata_amd
May  8 15:17:50 MEwebServer kernel: [    1.145888] scsi1 : pata_amd
May  8 15:17:50 MEwebServer kernel: [    1.145974] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  8 15:17:50 MEwebServer kernel: [    1.146035] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  8 15:17:50 MEwebServer kernel: [    1.146125] sata_nv 0000:00:08.0: version 3.5
May  8 15:17:50 MEwebServer kernel: [    1.146275] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
May  8 15:17:50 MEwebServer kernel: [    1.146539] scsi2 : sata_nv
May  8 15:17:50 MEwebServer kernel: [    1.146641] scsi3 : sata_nv
May  8 15:17:50 MEwebServer kernel: [    1.146726] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 22
May  8 15:17:50 MEwebServer kernel: [    1.146788] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 22
May  8 15:17:50 MEwebServer kernel: [    1.300474] ata1.01: NODEV after polling detection
May  8 15:17:50 MEwebServer kernel: [    1.308840] ata1.00: ATAPI: PHILIPS DVDR1628P1, Q1.1, max UDMA/33
May  8 15:17:50 MEwebServer kernel: [    1.308911] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
May  8 15:17:50 MEwebServer kernel: [    1.324768] ata1.00: configured for UDMA/33
May  8 15:17:50 MEwebServer kernel: [    1.327751] scsi 0:0:0:0: CD-ROM            PHILIPS  DVDR1628P1       Q1.1 PQ: 0 ANSI: 5
May  8 15:17:50 MEwebServer kernel: [    1.331534] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May  8 15:17:50 MEwebServer kernel: [    1.331600] cdrom: Uniform CD-ROM driver Revision: 3.20
May  8 15:17:50 MEwebServer kernel: [    1.331791] sr 0:0:0:0: Attached scsi CD-ROM sr0
May  8 15:17:50 MEwebServer kernel: [    1.331844] sr 0:0:0:0: Attached scsi generic sg0 type 5
May  8 15:17:50 MEwebServer kernel: [    1.332125] ata2: port disabled--ignoring
May  8 15:17:50 MEwebServer kernel: [    1.544263] tsc: Refined TSC clocksource calibration: 2812.791 MHz
May  8 15:17:50 MEwebServer kernel: [    1.612276] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  8 15:17:50 MEwebServer kernel: [    1.620481] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
May  8 15:17:50 MEwebServer kernel: [    1.620546] ata3.00: 488397168 sectors, multi 16: LBA48 
May  8 15:17:50 MEwebServer kernel: [    1.628484] ata3.00: configured for UDMA/133
May  8 15:17:50 MEwebServer kernel: [    1.628685] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
May  8 15:17:50 MEwebServer kernel: [    1.628926] sd 2:0:0:0: Attached scsi generic sg1 type 0
May  8 15:17:50 MEwebServer kernel: [    1.628932] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
May  8 15:17:50 MEwebServer kernel: [    1.628977] sd 2:0:0:0: [sda] Write Protect is off
May  8 15:17:50 MEwebServer kernel: [    1.628979] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  8 15:17:50 MEwebServer kernel: [    1.628996] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 15:17:50 MEwebServer kernel: [    1.667549]  sda: sda1 sda2 < sda5 >
May  8 15:17:50 MEwebServer kernel: [    1.668006] sd 2:0:0:0: [sda] Attached SCSI disk
May  8 15:17:50 MEwebServer kernel: [    2.096208] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  8 15:17:50 MEwebServer kernel: [    2.104608] ata4.00: HPA detected: current 488395055, native 488397168
May  8 15:17:50 MEwebServer kernel: [    2.104676] ata4.00: ATA-8: WDC WD2500AAJS-00VTA0, 01.01B01, max UDMA/133
May  8 15:17:50 MEwebServer kernel: [    2.104737] ata4.00: 488395055 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  8 15:17:50 MEwebServer kernel: [    2.120618] ata4.00: configured for UDMA/133
May  8 15:17:50 MEwebServer kernel: [    2.120818] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500AAJS-0 01.0 PQ: 0 ANSI: 5
May  8 15:17:50 MEwebServer kernel: [    2.121061] sd 3:0:0:0: [sdb] 488395055 512-byte logical blocks: (250 GB/232 GiB)
May  8 15:17:50 MEwebServer kernel: [    2.121072] sd 3:0:0:0: Attached scsi generic sg2 type 0
May  8 15:17:50 MEwebServer kernel: [    2.121277] sd 3:0:0:0: [sdb] Write Protect is off
May  8 15:17:50 MEwebServer kernel: [    2.121337] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  8 15:17:50 MEwebServer kernel: [    2.121372] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 15:17:50 MEwebServer kernel: [    2.173934]  sdb: sdb1 sdb2 < sdb5 >
May  8 15:17:50 MEwebServer kernel: [    2.174350] sd 3:0:0:0: [sdb] Attached SCSI disk
May  8 15:17:50 MEwebServer kernel: [    2.323698] md: bind<sda1>
May  8 15:17:50 MEwebServer kernel: [    2.325234] md/raid1:md0: active with 1 out of 2 mirrors
May  8 15:17:50 MEwebServer kernel: [    2.325316] md0: detected capacity change from 0 to 245662285824
May  8 15:17:50 MEwebServer kernel: [    2.352208]  md0: unknown partition table
May  8 15:17:50 MEwebServer kernel: [    2.544189] Switched to clocksource tsc
May  8 15:17:50 MEwebServer kernel: [    2.563261] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
May  8 15:17:50 MEwebServer kernel: [    5.203690] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:17:50 MEwebServer kernel: [    5.203784] ata4.00: BMDMA stat 0x24
May  8 15:17:50 MEwebServer kernel: [    5.203843] ata4.00: failed command: READ DMA
May  8 15:17:50 MEwebServer kernel: [    5.203904] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:17:50 MEwebServer kernel: [    5.203904]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:17:50 MEwebServer kernel: [    5.204002] ata4.00: status: { DRDY ERR }
May  8 15:17:50 MEwebServer kernel: [    5.204059] ata4.00: error: { UNC }
May  8 15:17:50 MEwebServer kernel: [    5.220562] ata4.00: configured for UDMA/133
May  8 15:17:50 MEwebServer kernel: [    5.220642] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:17:50 MEwebServer kernel: [    5.220701] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [    5.220757] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:17:50 MEwebServer kernel: [    5.220816] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [    5.220872] Sense Key : Medium Error [current] [descriptor]
May  8 15:17:50 MEwebServer kernel: [    5.221059] Descriptor sense data with sense descriptors (in hex):
May  8 15:17:50 MEwebServer kernel: [    5.221160]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:17:50 MEwebServer kernel: [    5.221941]         00 00 01 97 
May  8 15:17:50 MEwebServer kernel: [    5.222210] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [    5.222266] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:17:50 MEwebServer kernel: [    5.222369] sd 3:0:0:0: [sdb] CDB: 
May  8 15:17:50 MEwebServer kernel: [    5.222426] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:17:50 MEwebServer kernel: [    5.222994] end_request: I/O error, dev sdb, sector 407
May  8 15:17:50 MEwebServer kernel: [    5.223053] Buffer I/O error on device sdb, logical block 407
May  8 15:17:50 MEwebServer kernel: [    5.223133] ata4: EH complete
May  8 15:17:50 MEwebServer kernel: [    8.153441] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:17:50 MEwebServer kernel: [    8.153506] ata4.00: BMDMA stat 0x24
May  8 15:17:50 MEwebServer kernel: [    8.153564] ata4.00: failed command: READ DMA
May  8 15:17:50 MEwebServer kernel: [    8.153624] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:17:50 MEwebServer kernel: [    8.153624]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:17:50 MEwebServer kernel: [    8.153713] ata4.00: status: { DRDY ERR }
May  8 15:17:50 MEwebServer kernel: [    8.153770] ata4.00: error: { UNC }
May  8 15:17:50 MEwebServer kernel: [    8.176344] ata4.00: configured for UDMA/133
May  8 15:17:50 MEwebServer kernel: [    8.176420] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:17:50 MEwebServer kernel: [    8.176478] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [    8.176534] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:17:50 MEwebServer kernel: [    8.176594] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [    8.176649] Sense Key : Medium Error [current] [descriptor]
May  8 15:17:50 MEwebServer kernel: [    8.176836] Descriptor sense data with sense descriptors (in hex):
May  8 15:17:50 MEwebServer kernel: [    8.176937]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:17:50 MEwebServer kernel: [    8.177717]         00 00 01 97 
May  8 15:17:50 MEwebServer kernel: [    8.177985] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [    8.178042] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:17:50 MEwebServer kernel: [    8.178145] sd 3:0:0:0: [sdb] CDB: 
May  8 15:17:50 MEwebServer kernel: [    8.178201] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:17:50 MEwebServer kernel: [    8.178768] end_request: I/O error, dev sdb, sector 407
May  8 15:17:50 MEwebServer kernel: [    8.178828] Buffer I/O error on device sdb, logical block 407
May  8 15:17:50 MEwebServer kernel: [    8.178909] ata4: EH complete
May  8 15:17:50 MEwebServer kernel: [    8.660112] random: nonblocking pool is initialized
May  8 15:17:50 MEwebServer kernel: [   12.085557] MCE: In-kernel MCE decoding enabled.
May  8 15:17:50 MEwebServer kernel: [   12.117650] EDAC MC: Ver: 3.0.0
May  8 15:17:50 MEwebServer kernel: [   12.178529] AMD64 EDAC driver v3.4.0
May  8 15:17:50 MEwebServer kernel: [   12.178620] EDAC amd64: DRAM ECC disabled.
May  8 15:17:50 MEwebServer kernel: [   12.178681] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May  8 15:17:50 MEwebServer kernel: [   12.178681]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May  8 15:17:50 MEwebServer kernel: [   12.178681]  (Note that use of the override may cause unknown side effects.)
May  8 15:17:50 MEwebServer kernel: [   12.310829] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
May  8 15:17:50 MEwebServer kernel: [   12.310909] i2c i2c-1: nForce2 SMBus adapter at 0xc800
May  8 15:17:50 MEwebServer kernel: [   12.772842] kvm: Nested Virtualization enabled
May  8 15:17:50 MEwebServer kernel: [   12.773091] kvm: Nested Paging enabled
May  8 15:17:50 MEwebServer kernel: [   13.054802] [drm] Initialized drm 1.1.0 20060810
May  8 15:17:50 MEwebServer kernel: [   13.364442] wmi: Mapper loaded
May  8 15:17:50 MEwebServer kernel: [   13.974704] forcedeth 0000:00:07.0: irq 40 for MSI/MSI-X
May  8 15:17:50 MEwebServer kernel: [   13.974734] forcedeth 0000:00:07.0 eth0: MSI enabled
May  8 15:17:50 MEwebServer kernel: [   14.029983] ip_tables: (C) 2000-2006 Netfilter Core Team
May  8 15:17:50 MEwebServer kernel: [   14.116099] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
May  8 15:17:50 MEwebServer kernel: [   14.497806] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  8 15:17:50 MEwebServer kernel: [   15.144023] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:17:50 MEwebServer kernel: [   15.144089] ata4.00: BMDMA stat 0x24
May  8 15:17:50 MEwebServer kernel: [   15.144147] ata4.00: failed command: READ DMA
May  8 15:17:50 MEwebServer kernel: [   15.144208] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:17:50 MEwebServer kernel: [   15.144208]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:17:50 MEwebServer kernel: [   15.144307] ata4.00: status: { DRDY ERR }
May  8 15:17:50 MEwebServer kernel: [   15.144364] ata4.00: error: { UNC }
May  8 15:17:50 MEwebServer kernel: [   15.166879] ata4.00: configured for UDMA/133
May  8 15:17:50 MEwebServer kernel: [   15.166959] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:17:50 MEwebServer kernel: [   15.167018] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   15.167074] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:17:50 MEwebServer kernel: [   15.167133] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   15.167189] Sense Key : Medium Error [current] [descriptor]
May  8 15:17:50 MEwebServer kernel: [   15.167376] Descriptor sense data with sense descriptors (in hex):
May  8 15:17:50 MEwebServer kernel: [   15.167477]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:17:50 MEwebServer kernel: [   15.168258]         00 00 01 97 
May  8 15:17:50 MEwebServer kernel: [   15.168526] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   15.168583] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:17:50 MEwebServer kernel: [   15.168686] sd 3:0:0:0: [sdb] CDB: 
May  8 15:17:50 MEwebServer kernel: [   15.168742] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:17:50 MEwebServer kernel: [   15.169310] end_request: I/O error, dev sdb, sector 407
May  8 15:17:50 MEwebServer kernel: [   15.169370] Buffer I/O error on device sdb, logical block 407
May  8 15:17:50 MEwebServer kernel: [   15.169449] ata4: EH complete
May  8 15:17:50 MEwebServer kernel: [   17.043615] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
May  8 15:17:50 MEwebServer kernel: [   18.101804] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:17:50 MEwebServer kernel: [   18.101870] ata4.00: BMDMA stat 0x24
May  8 15:17:50 MEwebServer kernel: [   18.101947] ata4.00: failed command: READ DMA
May  8 15:17:50 MEwebServer kernel: [   18.102008] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:17:50 MEwebServer kernel: [   18.102008]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:17:50 MEwebServer kernel: [   18.102097] ata4.00: status: { DRDY ERR }
May  8 15:17:50 MEwebServer kernel: [   18.102154] ata4.00: error: { UNC }
May  8 15:17:50 MEwebServer kernel: [   18.126736] ata4.00: configured for UDMA/133
May  8 15:17:50 MEwebServer kernel: [   18.126754] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:17:50 MEwebServer kernel: [   18.126756] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   18.126757] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:17:50 MEwebServer kernel: [   18.126759] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   18.126760] Sense Key : Medium Error [current] [descriptor]
May  8 15:17:50 MEwebServer kernel: [   18.126763] Descriptor sense data with sense descriptors (in hex):
May  8 15:17:50 MEwebServer kernel: [   18.126764]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:17:50 MEwebServer kernel: [   18.126768]         00 00 01 97 
May  8 15:17:50 MEwebServer kernel: [   18.126771] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   18.126773] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:17:50 MEwebServer kernel: [   18.126774] sd 3:0:0:0: [sdb] CDB: 
May  8 15:17:50 MEwebServer kernel: [   18.126775] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:17:50 MEwebServer kernel: [   18.126780] end_request: I/O error, dev sdb, sector 407
May  8 15:17:50 MEwebServer kernel: [   18.126842] Buffer I/O error on device sdb, logical block 407
May  8 15:17:50 MEwebServer kernel: [   18.126924] ata4: EH complete
May  8 15:17:50 MEwebServer kernel: [   22.330477] AMD64 EDAC driver v3.4.0
May  8 15:17:50 MEwebServer kernel: [   22.330507] EDAC amd64: DRAM ECC disabled.
May  8 15:17:50 MEwebServer kernel: [   22.330512] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May  8 15:17:50 MEwebServer kernel: [   22.330512]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May  8 15:17:50 MEwebServer kernel: [   22.330512]  (Note that use of the override may cause unknown side effects.)
May  8 15:17:50 MEwebServer kernel: [   22.489649] lp: driver loaded but no devices found
May  8 15:17:50 MEwebServer kernel: [   25.334590] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:17:50 MEwebServer kernel: [   25.334595] ata4.00: BMDMA stat 0x24
May  8 15:17:50 MEwebServer kernel: [   25.334598] ata4.00: failed command: READ DMA
May  8 15:17:50 MEwebServer kernel: [   25.334602] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:17:50 MEwebServer kernel: [   25.334602]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:17:50 MEwebServer kernel: [   25.334605] ata4.00: status: { DRDY ERR }
May  8 15:17:50 MEwebServer kernel: [   25.334606] ata4.00: error: { UNC }
May  8 15:17:50 MEwebServer kernel: [   25.357469] ata4.00: configured for UDMA/133
May  8 15:17:50 MEwebServer kernel: [   25.357492] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:17:50 MEwebServer kernel: [   25.357493] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   25.357495] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:17:50 MEwebServer kernel: [   25.357496] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   25.357498] Sense Key : Medium Error [current] [descriptor]
May  8 15:17:50 MEwebServer kernel: [   25.357500] Descriptor sense data with sense descriptors (in hex):
May  8 15:17:50 MEwebServer kernel: [   25.357501]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:17:50 MEwebServer kernel: [   25.357506]         00 00 01 97 
May  8 15:17:50 MEwebServer kernel: [   25.357508] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   25.357510] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:17:50 MEwebServer kernel: [   25.357512] sd 3:0:0:0: [sdb] CDB: 
May  8 15:17:50 MEwebServer kernel: [   25.357513] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:17:50 MEwebServer kernel: [   25.357518] end_request: I/O error, dev sdb, sector 407
May  8 15:17:50 MEwebServer kernel: [   25.357519] Buffer I/O error on device sdb, logical block 407
May  8 15:17:50 MEwebServer kernel: [   25.357542] ata4: EH complete
May  8 15:17:50 MEwebServer kernel: [   28.284343] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:17:50 MEwebServer kernel: [   28.284347] ata4.00: BMDMA stat 0x24
May  8 15:17:50 MEwebServer kernel: [   28.284350] ata4.00: failed command: READ DMA
May  8 15:17:50 MEwebServer kernel: [   28.284355] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:17:50 MEwebServer kernel: [   28.284355]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:17:50 MEwebServer kernel: [   28.284357] ata4.00: status: { DRDY ERR }
May  8 15:17:50 MEwebServer kernel: [   28.284358] ata4.00: error: { UNC }
May  8 15:17:50 MEwebServer kernel: [   28.309297] ata4.00: configured for UDMA/133
May  8 15:17:50 MEwebServer kernel: [   28.309315] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:17:50 MEwebServer kernel: [   28.309316] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   28.309318] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:17:50 MEwebServer kernel: [   28.309319] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   28.309320] Sense Key : Medium Error [current] [descriptor]
May  8 15:17:50 MEwebServer kernel: [   28.309323] Descriptor sense data with sense descriptors (in hex):
May  8 15:17:50 MEwebServer kernel: [   28.309323]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:17:50 MEwebServer kernel: [   28.309328]         00 00 01 97 
May  8 15:17:50 MEwebServer kernel: [   28.309330] sd 3:0:0:0: [sdb]  
May  8 15:17:50 MEwebServer kernel: [   28.309332] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:17:50 MEwebServer kernel: [   28.309334] sd 3:0:0:0: [sdb] CDB: 
May  8 15:17:50 MEwebServer kernel: [   28.309335] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:17:50 MEwebServer kernel: [   28.309340] end_request: I/O error, dev sdb, sector 407
May  8 15:17:50 MEwebServer kernel: [   28.309342] Buffer I/O error on device sdb, logical block 407
May  8 15:17:50 MEwebServer kernel: [   28.309367] ata4: EH complete
May  8 15:17:50 MEwebServer kernel: [   31.693484] Adding 4159484k swap on /dev/sda5.  Priority:-1 extents:1 across:4159484k FS
May  8 15:17:50 MEwebServer kernel: [   31.696073] Adding 4159484k swap on /dev/sdb5.  Priority:-2 extents:1 across:4159484k FS
May  8 15:17:50 MEwebServer kernel: [   32.338776] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro
May  8 15:17:50 MEwebServer kernel: [   33.094642] type=1400 audit(1431094670.531:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=1155 comm="apparmor_parser"
May  8 15:17:50 MEwebServer kernel: [   33.097585] type=1400 audit(1431094670.535:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1154 comm="apparmor_parser"
May  8 15:17:50 MEwebServer kernel: [   33.097593] type=1400 audit(1431094670.535:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1154 comm="apparmor_parser"
May  8 15:17:50 MEwebServer kernel: [   33.097597] type=1400 audit(1431094670.535:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1154 comm="apparmor_parser"
May  8 15:17:50 MEwebServer kernel: [   33.098033] type=1400 audit(1431094670.535:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1154 comm="apparmor_parser"
May  8 15:17:50 MEwebServer kernel: [   33.098038] type=1400 audit(1431094670.535:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1154 comm="apparmor_parser"
May  8 15:17:50 MEwebServer kernel: [   33.098272] type=1400 audit(1431094670.535:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1154 comm="apparmor_parser"
May  8 15:17:50 MEwebServer kernel: [   33.100670] type=1400 audit(1431094670.539:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1157 comm="apparmor_parser"
May  8 15:17:50 MEwebServer kernel: [   33.400195] type=1400 audit(1431094670.839:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=1270 comm="apparmor_parser"
May  8 15:19:13 MEwebServer kernel: [  115.897640] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:f2:01:0c:bb:a6:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  8 15:20:47 MEwebServer kernel: [  209.760396] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
May  8 15:20:47 MEwebServer kernel: [  209.822559] JFS: nTxBlock = 8192, nTxLock = 65536
May  8 15:20:47 MEwebServer kernel: [  209.897372] NTFS driver 2.1.30 [Flags: R/O MODULE].
May  8 15:20:47 MEwebServer kernel: [  209.978541] QNX4 filesystem 0.2.3 registered.
May  8 15:20:47 MEwebServer kernel: [  210.176595] bio: create slab <bio-1> at 1
May  8 15:20:47 MEwebServer kernel: [  210.177360] Btrfs loaded
May  8 15:21:18 MEwebServer kernel: [  240.884478] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:f2:01:0c:bb:a6:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
May  8 15:23:51 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpuset
May  8 15:23:51 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpu
May  8 15:23:51 MEwebServer kernel: [    0.000000] Initializing cgroup subsys cpuacct
May  8 15:23:51 MEwebServer kernel: [    0.000000] Linux version 3.13.0-52-generic (buildd@comet) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #86-Ubuntu SMP Mon May 4 04:32:59 UTC 2015 (Ubuntu 3.13.0-52.86-generic 3.13.11-ckt18)
May  8 15:23:51 MEwebServer kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic root=UUID=bf21290d-7a02-4713-aaad-c45f755eec04 ro recovery nomodeset
May  8 15:23:51 MEwebServer kernel: [    0.000000] KERNEL supported cpus:
May  8 15:23:51 MEwebServer kernel: [    0.000000]   Intel GenuineIntel
May  8 15:23:51 MEwebServer kernel: [    0.000000]   AMD AuthenticAMD
May  8 15:23:51 MEwebServer kernel: [    0.000000]   Centaur CentaurHauls
May  8 15:23:51 MEwebServer kernel: [    0.000000] e820: BIOS-provided physical RAM map:
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000ddfeffff] usable
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000ddff0000-0x00000000ddff2fff] ACPI NVS
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000ddff3000-0x00000000ddffffff] ACPI data
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000de000000-0x00000000dfffffff] reserved
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
May  8 15:23:51 MEwebServer kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
May  8 15:23:51 MEwebServer kernel: [    0.000000] NX (Execute Disable) protection: active
May  8 15:23:51 MEwebServer kernel: [    0.000000] SMBIOS 2.4 present.
May  8 15:23:51 MEwebServer kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. M61PME-S2P/M61PME-S2P, BIOS F2 12/30/2008
May  8 15:23:51 MEwebServer kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
May  8 15:23:51 MEwebServer kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
May  8 15:23:51 MEwebServer kernel: [    0.000000] No AGP bridge found
May  8 15:23:51 MEwebServer kernel: [    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x400000000
May  8 15:23:51 MEwebServer kernel: [    0.000000] MTRR default type: uncachable
May  8 15:23:51 MEwebServer kernel: [    0.000000] MTRR fixed ranges enabled:
May  8 15:23:51 MEwebServer kernel: [    0.000000]   00000-9FFFF write-back
May  8 15:23:51 MEwebServer kernel: [    0.000000]   A0000-BFFFF uncachable
May  8 15:23:51 MEwebServer kernel: [    0.000000]   C0000-C7FFF write-protect
May  8 15:23:51 MEwebServer kernel: [    0.000000]   C8000-EFFFF uncachable
May  8 15:23:51 MEwebServer kernel: [    0.000000]   F0000-FFFFF write-through
May  8 15:23:51 MEwebServer kernel: [    0.000000] MTRR variable ranges enabled:
May  8 15:23:51 MEwebServer kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
May  8 15:23:51 MEwebServer kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
May  8 15:23:51 MEwebServer kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
May  8 15:23:51 MEwebServer kernel: [    0.000000]   3 base 0000DE000000 mask FFFFFE000000 uncachable
May  8 15:23:51 MEwebServer kernel: [    0.000000]   4 base 000100000000 mask FFFFE0000000 write-back
May  8 15:23:51 MEwebServer kernel: [    0.000000]   5 disabled
May  8 15:23:51 MEwebServer kernel: [    0.000000]   6 disabled
May  8 15:23:51 MEwebServer kernel: [    0.000000]   7 disabled
May  8 15:23:51 MEwebServer kernel: [    0.000000] TOM2: 0000000120000000 aka 4608M
May  8 15:23:51 MEwebServer kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May  8 15:23:51 MEwebServer kernel: [    0.000000] original variable MTRRs
May  8 15:23:51 MEwebServer kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
May  8 15:23:51 MEwebServer kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
May  8 15:23:51 MEwebServer kernel: [    0.000000] reg 2, base: 3GB, range: 512MB, type WB
May  8 15:23:51 MEwebServer kernel: [    0.000000] reg 3, base: 3552MB, range: 32MB, type UC
May  8 15:23:51 MEwebServer kernel: [    0.000000] reg 4, base: 4GB, range: 512MB, type WB
May  8 15:23:51 MEwebServer kernel: [    0.000000] total RAM covered: 3552M
May  8 15:23:51 MEwebServer kernel: [    0.000000] Found optimal setting for mtrr clean up
May  8 15:23:51 MEwebServer kernel: [    0.000000]  gran_size: 64K 	chunk_size: 1G 	num_reg: 3  	lose cover RAM: 0G
May  8 15:23:51 MEwebServer kernel: [    0.000000] New variable MTRRs
May  8 15:23:51 MEwebServer kernel: [    0.000000] reg 0, base: 0GB, range: 4GB, type WB
May  8 15:23:51 MEwebServer kernel: [    0.000000] reg 1, base: 3552MB, range: 32MB, type UC
May  8 15:23:51 MEwebServer kernel: [    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
May  8 15:23:51 MEwebServer kernel: [    0.000000] e820: update [mem 0xde000000-0xffffffff] usable ==> reserved
May  8 15:23:51 MEwebServer kernel: [    0.000000] e820: last_pfn = 0xddff0 max_arch_pfn = 0x400000000
May  8 15:23:51 MEwebServer kernel: [    0.000000] found SMP MP-table at [mem 0x000f4a90-0x000f4a9f] mapped at [ffff8800000f4a90]
May  8 15:23:51 MEwebServer kernel: [    0.000000] Scanning 1 areas for low memory corruption
May  8 15:23:51 MEwebServer kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
May  8 15:23:51 MEwebServer kernel: [    0.000000] Using GB pages for direct mapping
May  8 15:23:51 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
May  8 15:23:51 MEwebServer kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
May  8 15:23:51 MEwebServer kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
May  8 15:23:51 MEwebServer kernel: [    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
May  8 15:23:51 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x11fe00000-0x11fffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0x11fe00000-0x11fffffff] page 2M
May  8 15:23:51 MEwebServer kernel: [    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
May  8 15:23:51 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x11c000000-0x11fdfffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0x11c000000-0x11fdfffff] page 2M
May  8 15:23:51 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x11bffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0x100000000-0x11bffffff] page 2M
May  8 15:23:51 MEwebServer kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xddfeffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0xc0000000-0xdddfffff] page 2M
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [mem 0xdde00000-0xddfeffff] page 4k
May  8 15:23:51 MEwebServer kernel: [    0.000000] RAMDISK: [mem 0x35a4c000-0x36d1dfff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: RSDP 00000000000f6460 000014 (v00 GBT   )
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: RSDT 00000000ddff3000 000038 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: FACP 00000000ddff3040 000074 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: DSDT 00000000ddff30c0 0043ED (v01 GBT    NVDAACPI 00001000 MSFT 03000000)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: FACS 00000000ddff0000 000040
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: SSDT 00000000ddff7580 00095E (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: HPET 00000000ddff7f00 000038 (v01 GBT    NVDAACPI 42302E31 NVDA 00000098)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: MCFG 00000000ddff7f40 00003C (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: APIC 00000000ddff74c0 000098 (v01 GBT    NVDAACPI 42302E31 NVDA 01010101)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  8 15:23:51 MEwebServer kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
May  8 15:23:51 MEwebServer kernel: [    0.000000] No NUMA configuration found
May  8 15:23:51 MEwebServer kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011fffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x11fffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]   NODE_DATA [mem 0x11fff9000-0x11fffdfff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011b600000-ffff88011f5fffff] on node 0
May  8 15:23:51 MEwebServer kernel: [    0.000000] Zone ranges:
May  8 15:23:51 MEwebServer kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]   Normal   [mem 0x100000000-0x11fffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] Movable zone start for each node
May  8 15:23:51 MEwebServer kernel: [    0.000000] Early memory node ranges
May  8 15:23:51 MEwebServer kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009efff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]   node   0: [mem 0x00100000-0xddfeffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000]   node   0: [mem 0x100000000-0x11fffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] On node 0 totalpages: 1040270
May  8 15:23:51 MEwebServer kernel: [    0.000000]   DMA zone: 64 pages used for memmap
May  8 15:23:51 MEwebServer kernel: [    0.000000]   DMA zone: 21 pages reserved
May  8 15:23:51 MEwebServer kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
May  8 15:23:51 MEwebServer kernel: [    0.000000]   DMA32 zone: 14144 pages used for memmap
May  8 15:23:51 MEwebServer kernel: [    0.000000]   DMA32 zone: 905200 pages, LIFO batch:31
May  8 15:23:51 MEwebServer kernel: [    0.000000]   Normal zone: 2048 pages used for memmap
May  8 15:23:51 MEwebServer kernel: [    0.000000]   Normal zone: 131072 pages, LIFO batch:31
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  8 15:23:51 MEwebServer kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: IRQ0 used by override.
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: IRQ2 used by override.
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: IRQ9 used by override.
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: IRQ14 used by override.
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: IRQ15 used by override.
May  8 15:23:51 MEwebServer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  8 15:23:51 MEwebServer kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
May  8 15:23:51 MEwebServer kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
May  8 15:23:51 MEwebServer kernel: [    0.000000] nr_irqs_gsi: 40
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xddff0000-0xddff2fff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xddff3000-0xddffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xde000000-0xdfffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] e820: [mem 0xe0000000-0xefffffff] available for PCI devices
May  8 15:23:51 MEwebServer kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May  8 15:23:51 MEwebServer kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
May  8 15:23:51 MEwebServer kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88011fc00000 s81536 r8192 d20864 u524288
May  8 15:23:51 MEwebServer kernel: [    0.000000] pcpu-alloc: s81536 r8192 d20864 u524288 alloc=1*2097152
May  8 15:23:51 MEwebServer kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
May  8 15:23:51 MEwebServer kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1023993
May  8 15:23:51 MEwebServer kernel: [    0.000000] Policy zone: Normal
May  8 15:23:51 MEwebServer kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic root=UUID=bf21290d-7a02-4713-aaad-c45f755eec04 ro recovery nomodeset
May  8 15:23:51 MEwebServer kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.000000] Checking aperture...
May  8 15:23:51 MEwebServer kernel: [    0.000000] No AGP bridge found
May  8 15:23:51 MEwebServer kernel: [    0.000000] Node 0: aperture @ d4000000 size 32 MB
May  8 15:23:51 MEwebServer kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
May  8 15:23:51 MEwebServer kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
May  8 15:23:51 MEwebServer kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
May  8 15:23:51 MEwebServer kernel: [    0.000000] This costs you 64 MB of RAM
May  8 15:23:51 MEwebServer kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ d4000000
May  8 15:23:51 MEwebServer kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd4000000-0xd7ffffff]
May  8 15:23:51 MEwebServer kernel: [    0.000000] Memory: 3927608K/4161080K available (7389K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 233472K reserved)
May  8 15:23:51 MEwebServer kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May  8 15:23:51 MEwebServer kernel: [    0.000000] Hierarchical RCU implementation.
May  8 15:23:51 MEwebServer kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
May  8 15:23:51 MEwebServer kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
May  8 15:23:51 MEwebServer kernel: [    0.000000] 	Offload RCU callbacks from all CPUs
May  8 15:23:51 MEwebServer kernel: [    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
May  8 15:23:51 MEwebServer kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
May  8 15:23:51 MEwebServer kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
May  8 15:23:51 MEwebServer kernel: [    0.000000] Console: colour VGA+ 80x25
May  8 15:23:51 MEwebServer kernel: [    0.000000] console [tty0] enabled
May  8 15:23:51 MEwebServer kernel: [    0.000000] allocated 16777216 bytes of page_cgroup
May  8 15:23:51 MEwebServer kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May  8 15:23:51 MEwebServer kernel: [    0.000000] hpet clockevent registered
May  8 15:23:51 MEwebServer kernel: [    0.000000] tsc: Fast TSC calibration using PIT
May  8 15:23:51 MEwebServer kernel: [    0.004000] tsc: Detected 2812.598 MHz processor
May  8 15:23:51 MEwebServer kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5625.19 BogoMIPS (lpj=11250392)
May  8 15:23:51 MEwebServer kernel: [    0.000121] pid_max: default: 32768 minimum: 301
May  8 15:23:51 MEwebServer kernel: [    0.000206] Security Framework initialized
May  8 15:23:51 MEwebServer kernel: [    0.000281] AppArmor: AppArmor initialized
May  8 15:23:51 MEwebServer kernel: [    0.000338] Yama: becoming mindful.
May  8 15:23:51 MEwebServer kernel: [    0.000679] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.002132] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.002816] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.002883] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.003168] Initializing cgroup subsys memory
May  8 15:23:51 MEwebServer kernel: [    0.003231] Initializing cgroup subsys devices
May  8 15:23:51 MEwebServer kernel: [    0.003289] Initializing cgroup subsys freezer
May  8 15:23:51 MEwebServer kernel: [    0.003347] Initializing cgroup subsys blkio
May  8 15:23:51 MEwebServer kernel: [    0.003405] Initializing cgroup subsys perf_event
May  8 15:23:51 MEwebServer kernel: [    0.003464] Initializing cgroup subsys hugetlb
May  8 15:23:51 MEwebServer kernel: [    0.003539] tseg: 0000000000
May  8 15:23:51 MEwebServer kernel: [    0.003546] CPU: Physical Processor ID: 0
May  8 15:23:51 MEwebServer kernel: [    0.003603] CPU: Processor Core ID: 0
May  8 15:23:51 MEwebServer kernel: [    0.003661] mce: CPU supports 6 MCE banks
May  8 15:23:51 MEwebServer kernel: [    0.003722] LVT offset 0 assigned for vector 0xf9
May  8 15:23:51 MEwebServer kernel: [    0.003783] process: using AMD E400 aware idle routine
May  8 15:23:51 MEwebServer kernel: [    0.003842] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
May  8 15:23:51 MEwebServer kernel: [    0.003842] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
May  8 15:23:51 MEwebServer kernel: [    0.003842] tlb_flushall_shift: 4
May  8 15:23:51 MEwebServer kernel: [    0.004022] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
May  8 15:23:51 MEwebServer kernel: [    0.004840] ACPI: Core revision 20131115
May  8 15:23:51 MEwebServer kernel: [    0.006660] ACPI: All ACPI Tables successfully acquired
May  8 15:23:51 MEwebServer kernel: [    0.008179] ftrace: allocating 28576 entries in 112 pages
May  8 15:23:51 MEwebServer kernel: [    0.020128] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  8 15:23:51 MEwebServer kernel: [    0.059867] smpboot: CPU0: AMD Athlon(tm) X2 240e Processor (fam: 10, model: 06, stepping: 02)
May  8 15:23:51 MEwebServer kernel: [    0.165664] Performance Events: AMD PMU driver.
May  8 15:23:51 MEwebServer kernel: [    0.165768] ... version:                0
May  8 15:23:51 MEwebServer kernel: [    0.165825] ... bit width:              48
May  8 15:23:51 MEwebServer kernel: [    0.165882] ... generic registers:      4
May  8 15:23:51 MEwebServer kernel: [    0.165938] ... value mask:             0000ffffffffffff
May  8 15:23:51 MEwebServer kernel: [    0.165997] ... max period:             00007fffffffffff
May  8 15:23:51 MEwebServer kernel: [    0.166055] ... fixed-purpose events:   0
May  8 15:23:51 MEwebServer kernel: [    0.166111] ... event mask:             000000000000000f
May  8 15:23:51 MEwebServer kernel: [    0.167633] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
May  8 15:23:51 MEwebServer kernel: [    0.167781] x86: Booting SMP configuration:
May  8 15:23:51 MEwebServer kernel: [    0.167839] .... node  #0, CPUs:      #1
May  8 15:23:51 MEwebServer kernel: [    0.181017] x86: Booted up 1 node, 2 CPUs
May  8 15:23:51 MEwebServer kernel: [    0.181126] smpboot: Total of 2 processors activated (11250.39 BogoMIPS)
May  8 15:23:51 MEwebServer kernel: [    0.181885] devtmpfs: initialized
May  8 15:23:51 MEwebServer kernel: [    0.185137] EVM: security.selinux
May  8 15:23:51 MEwebServer kernel: [    0.185193] EVM: security.SMACK64
May  8 15:23:51 MEwebServer kernel: [    0.185249] EVM: security.ima
May  8 15:23:51 MEwebServer kernel: [    0.185305] EVM: security.capability
May  8 15:23:51 MEwebServer kernel: [    0.185429] PM: Registering ACPI NVS region [mem 0xddff0000-0xddff2fff] (12288 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.186432] pinctrl core: initialized pinctrl subsystem
May  8 15:23:51 MEwebServer kernel: [    0.186559] regulator-dummy: no parameters
May  8 15:23:51 MEwebServer kernel: [    0.186651] RTC time: 14:23:15, date: 05/08/15
May  8 15:23:51 MEwebServer kernel: [    0.186749] NET: Registered protocol family 16
May  8 15:23:51 MEwebServer kernel: [    0.186903] cpuidle: using governor ladder
May  8 15:23:51 MEwebServer kernel: [    0.186960] cpuidle: using governor menu
May  8 15:23:51 MEwebServer kernel: [    0.187021] node 0 link 0: io port [1000, fffff]
May  8 15:23:51 MEwebServer kernel: [    0.187024] TOM: 00000000e0000000 aka 3584M
May  8 15:23:51 MEwebServer kernel: [    0.187082] Fam 10h mmconf [mem 0xf0000000-0xf00fffff]
May  8 15:23:51 MEwebServer kernel: [    0.187084] node 0 link 0: mmio [f0000000, f7ffffff] ==> [f0100000, f7ffffff]
May  8 15:23:51 MEwebServer kernel: [    0.187087] node 0 link 0: mmio [f8000000, ffb7ffff]
May  8 15:23:51 MEwebServer kernel: [    0.187089] node 0 link 0: mmio [a0000, bffff]
May  8 15:23:51 MEwebServer kernel: [    0.187090] node 0 link 0: mmio [e0000000, efffffff]
May  8 15:23:51 MEwebServer kernel: [    0.187091] TOM2: 0000000120000000 aka 4608M
May  8 15:23:51 MEwebServer kernel: [    0.187149] bus: [bus 00-ff] on node 0 link 0
May  8 15:23:51 MEwebServer kernel: [    0.187151] bus: 00 [io  0x0000-0xffff]
May  8 15:23:51 MEwebServer kernel: [    0.187152] bus: 00 [mem 0xf0100000-0xffffffff]
May  8 15:23:51 MEwebServer kernel: [    0.187153] bus: 00 [mem 0x000a0000-0x000bffff]
May  8 15:23:51 MEwebServer kernel: [    0.187154] bus: 00 [mem 0xe0000000-0xefffffff]
May  8 15:23:51 MEwebServer kernel: [    0.187155] bus: 00 [mem 0x120000000-0xfcffffffff]
May  8 15:23:51 MEwebServer kernel: [    0.187198] ACPI: bus type PCI registered
May  8 15:23:51 MEwebServer kernel: [    0.187256] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
May  8 15:23:51 MEwebServer kernel: [    0.187369] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
May  8 15:23:51 MEwebServer kernel: [    0.187443] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
May  8 15:23:51 MEwebServer kernel: [    0.193974] PCI: Using configuration type 1 for base access
May  8 15:23:51 MEwebServer kernel: [    0.194910] bio: create slab <bio-0> at 0
May  8 15:23:51 MEwebServer kernel: [    0.195143] ACPI: Added _OSI(Module Device)
May  8 15:23:51 MEwebServer kernel: [    0.195201] ACPI: Added _OSI(Processor Device)
May  8 15:23:51 MEwebServer kernel: [    0.195258] ACPI: Added _OSI(3.0 _SCP Extensions)
May  8 15:23:51 MEwebServer kernel: [    0.195316] ACPI: Added _OSI(Processor Aggregator Device)
May  8 15:23:51 MEwebServer kernel: [    0.199017] ACPI: Interpreter enabled
May  8 15:23:51 MEwebServer kernel: [    0.199080] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
May  8 15:23:51 MEwebServer kernel: [    0.199240] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
May  8 15:23:51 MEwebServer kernel: [    0.199405] ACPI: (supports S0 S3 S4 S5)
May  8 15:23:51 MEwebServer kernel: [    0.199463] ACPI: Using IOAPIC for interrupt routing
May  8 15:23:51 MEwebServer kernel: [    0.199539] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
May  8 15:23:51 MEwebServer kernel: [    0.199704] ACPI: No dock devices found.
May  8 15:23:51 MEwebServer kernel: [    0.204573] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
May  8 15:23:51 MEwebServer kernel: [    0.204637] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
May  8 15:23:51 MEwebServer kernel: [    0.204711] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
May  8 15:23:51 MEwebServer kernel: [    0.204819] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
May  8 15:23:51 MEwebServer kernel: [    0.205023] PCI host bridge to bus 0000:00
May  8 15:23:51 MEwebServer kernel: [    0.205081] pci_bus 0000:00: root bus resource [bus 00-ff]
May  8 15:23:51 MEwebServer kernel: [    0.205141] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
May  8 15:23:51 MEwebServer kernel: [    0.205201] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
May  8 15:23:51 MEwebServer kernel: [    0.205261] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
May  8 15:23:51 MEwebServer kernel: [    0.205322] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
May  8 15:23:51 MEwebServer kernel: [    0.205383] pci_bus 0000:00: root bus resource [mem 0xde000000-0xfebfffff]
May  8 15:23:51 MEwebServer kernel: [    0.205462] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
May  8 15:23:51 MEwebServer kernel: [    0.205677] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
May  8 15:23:51 MEwebServer kernel: [    0.205760] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
May  8 15:23:51 MEwebServer kernel: [    0.205771] pci 0000:00:01.1: reg 0x10: [io  0xc000-0xc03f]
May  8 15:23:51 MEwebServer kernel: [    0.205784] pci 0000:00:01.1: reg 0x20: [io  0x1c00-0x1c3f]
May  8 15:23:51 MEwebServer kernel: [    0.205789] pci 0000:00:01.1: reg 0x24: [io  0xc800-0xc83f]
May  8 15:23:51 MEwebServer kernel: [    0.205815] pci 0000:00:01.1: PME# supported from D3hot D3cold
May  8 15:23:51 MEwebServer kernel: [    0.205881] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
May  8 15:23:51 MEwebServer kernel: [    0.205960] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
May  8 15:23:51 MEwebServer kernel: [    0.206025] pci 0000:00:04.0: System wakeup disabled by ACPI
May  8 15:23:51 MEwebServer kernel: [    0.206108] pci 0000:00:06.0: [10de:03ec] type 00 class 0x01018a
May  8 15:23:51 MEwebServer kernel: [    0.206127] pci 0000:00:06.0: reg 0x20: [io  0xf000-0xf00f]
May  8 15:23:51 MEwebServer kernel: [    0.206202] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
May  8 15:23:51 MEwebServer kernel: [    0.206210] pci 0000:00:07.0: reg 0x10: [mem 0xfb000000-0xfb000fff]
May  8 15:23:51 MEwebServer kernel: [    0.206214] pci 0000:00:07.0: reg 0x14: [io  0xcc00-0xcc07]
May  8 15:23:51 MEwebServer kernel: [    0.206244] pci 0000:00:07.0: supports D1 D2
May  8 15:23:51 MEwebServer kernel: [    0.206246] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
May  8 15:23:51 MEwebServer kernel: [    0.206291] pci 0000:00:07.0: System wakeup disabled by ACPI
May  8 15:23:51 MEwebServer kernel: [    0.206372] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
May  8 15:23:51 MEwebServer kernel: [    0.206379] pci 0000:00:08.0: reg 0x10: [io  0x09f0-0x09f7]
May  8 15:23:51 MEwebServer kernel: [    0.206383] pci 0000:00:08.0: reg 0x14: [io  0x0bf0-0x0bf3]
May  8 15:23:51 MEwebServer kernel: [    0.206386] pci 0000:00:08.0: reg 0x18: [io  0x0970-0x0977]
May  8 15:23:51 MEwebServer kernel: [    0.206390] pci 0000:00:08.0: reg 0x1c: [io  0x0b70-0x0b73]
May  8 15:23:51 MEwebServer kernel: [    0.206393] pci 0000:00:08.0: reg 0x20: [io  0xe000-0xe00f]
May  8 15:23:51 MEwebServer kernel: [    0.206397] pci 0000:00:08.0: reg 0x24: [mem 0xfb001000-0xfb001fff]
May  8 15:23:51 MEwebServer kernel: [    0.206475] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
May  8 15:23:51 MEwebServer kernel: [    0.206481] pci 0000:00:0d.0: reg 0x10: [mem 0xf8000000-0xf8ffffff]
May  8 15:23:51 MEwebServer kernel: [    0.206485] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
May  8 15:23:51 MEwebServer kernel: [    0.206490] pci 0000:00:0d.0: reg 0x1c: [mem 0xf9000000-0xf9ffffff 64bit]
May  8 15:23:51 MEwebServer kernel: [    0.206495] pci 0000:00:0d.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
May  8 15:23:51 MEwebServer kernel: [    0.206565] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
May  8 15:23:51 MEwebServer kernel: [    0.206627] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
May  8 15:23:51 MEwebServer kernel: [    0.206684] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
May  8 15:23:51 MEwebServer kernel: [    0.206740] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
May  8 15:23:51 MEwebServer kernel: [    0.206801] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
May  8 15:23:51 MEwebServer kernel: [    0.206908] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
May  8 15:23:51 MEwebServer kernel: [    0.206970] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
May  8 15:23:51 MEwebServer kernel: [    0.206974] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
May  8 15:23:51 MEwebServer kernel: [    0.206975] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
May  8 15:23:51 MEwebServer kernel: [    0.206977] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
May  8 15:23:51 MEwebServer kernel: [    0.206979] pci 0000:00:04.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
May  8 15:23:51 MEwebServer kernel: [    0.206980] pci 0000:00:04.0:   bridge window [mem 0xde000000-0xfebfffff] (subtractive decode)
May  8 15:23:51 MEwebServer kernel: [    0.207355] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.207926] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.208495] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.209065] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.209633] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.210201] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.210770] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.211338] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.211908] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
May  8 15:23:51 MEwebServer kernel: [    0.212388] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.212957] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 *7 9 10 11 14 15)
May  8 15:23:51 MEwebServer kernel: [    0.213437] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
May  8 15:23:51 MEwebServer kernel: [    0.213914] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.214481] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.215050] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
May  8 15:23:51 MEwebServer kernel: [    0.215523] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.216091] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.216660] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
May  8 15:23:51 MEwebServer kernel: [    0.217139] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.217735] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.218061] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.218387] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.218712] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.219037] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.219362] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.219687] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.220012] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.220337] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
May  8 15:23:51 MEwebServer kernel: [    0.220746] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
May  8 15:23:51 MEwebServer kernel: [    0.221158] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
May  8 15:23:51 MEwebServer kernel: [    0.221568] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.222020] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.222474] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
May  8 15:23:51 MEwebServer kernel: [    0.222883] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.223336] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.223789] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.224242] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
May  8 15:23:51 MEwebServer kernel: [    0.224652] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
May  8 15:23:51 MEwebServer kernel: [    0.225135] ACPI: \_SB_.PCI0: notify handler is installed
May  8 15:23:51 MEwebServer kernel: [    0.225165] Found 1 acpi root devices
May  8 15:23:51 MEwebServer kernel: [    0.225288] vgaarb: setting as boot device: PCI:0000:00:0d.0
May  8 15:23:51 MEwebServer kernel: [    0.225347] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
May  8 15:23:51 MEwebServer kernel: [    0.225419] vgaarb: loaded
May  8 15:23:51 MEwebServer kernel: [    0.225474] vgaarb: bridge control possible 0000:00:0d.0
May  8 15:23:51 MEwebServer kernel: [    0.225692] SCSI subsystem initialized
May  8 15:23:51 MEwebServer kernel: [    0.225829] libata version 3.00 loaded.
May  8 15:23:51 MEwebServer kernel: [    0.225856] ACPI: bus type USB registered
May  8 15:23:51 MEwebServer kernel: [    0.225932] usbcore: registered new interface driver usbfs
May  8 15:23:51 MEwebServer kernel: [    0.225998] usbcore: registered new interface driver hub
May  8 15:23:51 MEwebServer kernel: [    0.226097] usbcore: registered new device driver usb
May  8 15:23:51 MEwebServer kernel: [    0.226265] PCI: Using ACPI for IRQ routing
May  8 15:23:51 MEwebServer kernel: [    0.229264] PCI: pci_cache_line_size set to 64 bytes
May  8 15:23:51 MEwebServer kernel: [    0.229287] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
May  8 15:23:51 MEwebServer kernel: [    0.229289] e820: reserve RAM buffer [mem 0xddff0000-0xdfffffff]
May  8 15:23:51 MEwebServer kernel: [    0.229381] NetLabel: Initializing
May  8 15:23:51 MEwebServer kernel: [    0.229437] NetLabel:  domain hash size = 128
May  8 15:23:51 MEwebServer kernel: [    0.229495] NetLabel:  protocols = UNLABELED CIPSOv4
May  8 15:23:51 MEwebServer kernel: [    0.229562] NetLabel:  unlabeled traffic allowed by default
May  8 15:23:51 MEwebServer kernel: [    0.229718] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May  8 15:23:51 MEwebServer kernel: [    0.229783] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
May  8 15:23:51 MEwebServer kernel: [    0.230012] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
May  8 15:23:51 MEwebServer kernel: [    0.232211] Switched to clocksource hpet
May  8 15:23:51 MEwebServer kernel: [    0.236772] AppArmor: AppArmor Filesystem Enabled
May  8 15:23:51 MEwebServer kernel: [    0.236863] pnp: PnP ACPI init
May  8 15:23:51 MEwebServer kernel: [    0.236932] ACPI: bus type PNP registered
May  8 15:23:51 MEwebServer kernel: [    0.237143] system 00:00: [io  0x1000-0x107f] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237204] system 00:00: [io  0x1080-0x10ff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237264] system 00:00: [io  0x1400-0x147f] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237324] system 00:00: [io  0x1480-0x14ff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237384] system 00:00: [io  0x1800-0x187f] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237444] system 00:00: [io  0x1880-0x18ff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237504] system 00:00: [mem 0xfefe0000-0xfefe01ff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237565] system 00:00: [mem 0xfefe1000-0xfefe10ff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237626] system 00:00: [mem 0xde000000-0xdfffffff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237688] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:23:51 MEwebServer kernel: [    0.237754] system 00:01: [io  0x04d0-0x04d1] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237814] system 00:01: [io  0x0800-0x087f] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237874] system 00:01: [io  0x0295-0x0296] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237934] system 00:01: [io  0x0290-0x0294] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.237994] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:23:51 MEwebServer kernel: [    0.238004] pnp 00:02: [dma 4]
May  8 15:23:51 MEwebServer kernel: [    0.238021] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
May  8 15:23:51 MEwebServer kernel: [    0.238078] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
May  8 15:23:51 MEwebServer kernel: [    0.238108] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
May  8 15:23:51 MEwebServer kernel: [    0.238128] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
May  8 15:23:51 MEwebServer kernel: [    0.238151] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
May  8 15:23:51 MEwebServer kernel: [    0.238418] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
May  8 15:23:51 MEwebServer kernel: [    0.238833] system 00:08: [mem 0xf0000000-0xf7ffffff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.238894] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
May  8 15:23:51 MEwebServer kernel: [    0.239006] system 00:09: [mem 0x000cec00-0x000cffff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.239068] system 00:09: [mem 0x000f0000-0x000f7fff] could not be reserved
May  8 15:23:51 MEwebServer kernel: [    0.239129] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
May  8 15:23:51 MEwebServer kernel: [    0.239190] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
May  8 15:23:51 MEwebServer kernel: [    0.239251] system 00:09: [mem 0xddff0000-0xddffffff] could not be reserved
May  8 15:23:51 MEwebServer kernel: [    0.239313] system 00:09: [mem 0xffff0000-0xffffffff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.239374] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
May  8 15:23:51 MEwebServer kernel: [    0.239435] system 00:09: [mem 0x00100000-0xddfeffff] could not be reserved
May  8 15:23:51 MEwebServer kernel: [    0.239496] system 00:09: [mem 0xde000000-0xdfffffff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.239557] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
May  8 15:23:51 MEwebServer kernel: [    0.239618] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
May  8 15:23:51 MEwebServer kernel: [    0.239679] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
May  8 15:23:51 MEwebServer kernel: [    0.239692] pnp: PnP ACPI: found 10 devices
May  8 15:23:51 MEwebServer kernel: [    0.239749] ACPI: bus type PNP unregistered
May  8 15:23:51 MEwebServer kernel: [    0.246008] pci 0000:00:0d.0: BAR 6: assigned [mem 0xfa000000-0xfa01ffff pref]
May  8 15:23:51 MEwebServer kernel: [    0.246080] pci 0000:00:04.0: PCI bridge to [bus 01]
May  8 15:23:51 MEwebServer kernel: [    0.246140] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
May  8 15:23:51 MEwebServer kernel: [    0.246205] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
May  8 15:23:51 MEwebServer kernel: [    0.246206] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
May  8 15:23:51 MEwebServer kernel: [    0.246208] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
May  8 15:23:51 MEwebServer kernel: [    0.246210] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
May  8 15:23:51 MEwebServer kernel: [    0.246211] pci_bus 0000:00: resource 8 [mem 0xde000000-0xfebfffff]
May  8 15:23:51 MEwebServer kernel: [    0.246213] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
May  8 15:23:51 MEwebServer kernel: [    0.246215] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
May  8 15:23:51 MEwebServer kernel: [    0.246216] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
May  8 15:23:51 MEwebServer kernel: [    0.246218] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
May  8 15:23:51 MEwebServer kernel: [    0.246219] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
May  8 15:23:51 MEwebServer kernel: [    0.246221] pci_bus 0000:01: resource 8 [mem 0xde000000-0xfebfffff]
May  8 15:23:51 MEwebServer kernel: [    0.246252] NET: Registered protocol family 2
May  8 15:23:51 MEwebServer kernel: [    0.246495] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.246674] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.246889] TCP: Hash tables configured (established 32768 bind 32768)
May  8 15:23:51 MEwebServer kernel: [    0.246991] TCP: reno registered
May  8 15:23:51 MEwebServer kernel: [    0.247055] UDP hash table entries: 2048 (order: 4, 65536 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.247142] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.247288] NET: Registered protocol family 1
May  8 15:23:51 MEwebServer kernel: [    0.247425] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:23:51 MEwebServer kernel: [    0.247530] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:23:51 MEwebServer kernel: [    0.247632] pci 0000:00:00.0: Found enabled HT MSI Mapping
May  8 15:23:51 MEwebServer kernel: [    0.247695] pci 0000:00:0d.0: Video device with shadowed ROM
May  8 15:23:51 MEwebServer kernel: [    0.247705] PCI: CLS 0 bytes, default 64
May  8 15:23:51 MEwebServer kernel: [    0.247785] Trying to unpack rootfs image as initramfs...
May  8 15:23:51 MEwebServer kernel: [    0.542668] Freeing initrd memory: 19272K (ffff880035a4c000 - ffff880036d1e000)
May  8 15:23:51 MEwebServer kernel: [    0.542910] PCI-DMA: Disabling AGP.
May  8 15:23:51 MEwebServer kernel: [    0.543035] PCI-DMA: aperture base @ d4000000 size 65536 KB
May  8 15:23:51 MEwebServer kernel: [    0.543094] PCI-DMA: using GART IOMMU.
May  8 15:23:51 MEwebServer kernel: [    0.543153] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
May  8 15:23:51 MEwebServer kernel: [    0.546016] LVT offset 1 assigned for vector 0x400
May  8 15:23:51 MEwebServer kernel: [    0.546085] IBS: LVT offset 1 assigned
May  8 15:23:51 MEwebServer kernel: [    0.546164] perf: AMD IBS detected (0x0000001f)
May  8 15:23:51 MEwebServer kernel: [    0.546266] microcode: CPU0: patch_level=0x00000000
May  8 15:23:51 MEwebServer kernel: [    0.546331] microcode: CPU1: patch_level=0x00000000
May  8 15:23:51 MEwebServer kernel: [    0.546457] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
May  8 15:23:51 MEwebServer kernel: [    0.546530] Scanning for low memory corruption every 60 seconds
May  8 15:23:51 MEwebServer kernel: [    0.546794] Initialise system trusted keyring
May  8 15:23:51 MEwebServer kernel: [    0.546897] audit: initializing netlink socket (disabled)
May  8 15:23:51 MEwebServer kernel: [    0.546968] type=2000 audit(1431094995.440:1): initialized
May  8 15:23:51 MEwebServer kernel: [    0.573008] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May  8 15:23:51 MEwebServer kernel: [    0.574184] zbud: loaded
May  8 15:23:51 MEwebServer kernel: [    0.574408] VFS: Disk quotas dquot_6.5.2
May  8 15:23:51 MEwebServer kernel: [    0.574521] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May  8 15:23:51 MEwebServer kernel: [    0.575070] fuse init (API version 7.22)
May  8 15:23:51 MEwebServer kernel: [    0.575213] msgmni has been set to 7837
May  8 15:23:51 MEwebServer kernel: [    0.575330] Key type big_key registered
May  8 15:23:51 MEwebServer kernel: [    0.575712] Key type asymmetric registered
May  8 15:23:51 MEwebServer kernel: [    0.575771] Asymmetric key parser 'x509' registered
May  8 15:23:51 MEwebServer kernel: [    0.575855] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
May  8 15:23:51 MEwebServer kernel: [    0.575951] io scheduler noop registered
May  8 15:23:51 MEwebServer kernel: [    0.576010] io scheduler deadline registered (default)
May  8 15:23:51 MEwebServer kernel: [    0.578458] io scheduler cfq registered
May  8 15:23:51 MEwebServer kernel: [    0.578583] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  8 15:23:51 MEwebServer kernel: [    0.578654] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  8 15:23:51 MEwebServer kernel: [    0.578752] ipmi message handler version 39.2
May  8 15:23:51 MEwebServer kernel: [    0.578867] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
May  8 15:23:51 MEwebServer kernel: [    0.578941] ACPI: Power Button [PWRB]
May  8 15:23:51 MEwebServer kernel: [    0.579032] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May  8 15:23:51 MEwebServer kernel: [    0.579103] ACPI: Power Button [PWRF]
May  8 15:23:51 MEwebServer kernel: [    0.579247] GHES: HEST is not enabled!
May  8 15:23:51 MEwebServer kernel: [    0.579379] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May  8 15:23:51 MEwebServer kernel: [    0.580565] Linux agpgart interface v0.103
May  8 15:23:51 MEwebServer kernel: [    0.581770] brd: module loaded
May  8 15:23:51 MEwebServer kernel: [    0.582411] loop: module loaded
May  8 15:23:51 MEwebServer kernel: [    0.582777] libphy: Fixed MDIO Bus: probed
May  8 15:23:51 MEwebServer kernel: [    0.582907] tun: Universal TUN/TAP device driver, 1.6
May  8 15:23:51 MEwebServer kernel: [    0.582966] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May  8 15:23:51 MEwebServer kernel: [    0.583103] PPP generic driver version 2.4.2
May  8 15:23:51 MEwebServer kernel: [    0.583194] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  8 15:23:51 MEwebServer kernel: [    0.583256] ehci-pci: EHCI PCI platform driver
May  8 15:23:51 MEwebServer kernel: [    0.583322] ehci-platform: EHCI generic platform driver
May  8 15:23:51 MEwebServer kernel: [    0.583384] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  8 15:23:51 MEwebServer kernel: [    0.583444] ohci-pci: OHCI PCI platform driver
May  8 15:23:51 MEwebServer kernel: [    0.583507] ohci-platform: OHCI generic platform driver
May  8 15:23:51 MEwebServer kernel: [    0.583569] uhci_hcd: USB Universal Host Controller Interface driver
May  8 15:23:51 MEwebServer kernel: [    0.583668] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May  8 15:23:51 MEwebServer kernel: [    0.583729] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May  8 15:23:51 MEwebServer kernel: [    0.583945] serio: i8042 KBD port at 0x60,0x64 irq 1
May  8 15:23:51 MEwebServer kernel: [    0.584115] mousedev: PS/2 mouse device common for all mice
May  8 15:23:51 MEwebServer kernel: [    0.584314] rtc_cmos 00:04: RTC can wake from S4
May  8 15:23:51 MEwebServer kernel: [    0.584512] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
May  8 15:23:51 MEwebServer kernel: [    0.584603] rtc_cmos 00:04: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
May  8 15:23:51 MEwebServer kernel: [    0.584726] device-mapper: uevent: version 1.0.3
May  8 15:23:51 MEwebServer kernel: [    0.584835] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
May  8 15:23:51 MEwebServer kernel: [    0.584911] ledtrig-cpu: registered to indicate activity on CPUs
May  8 15:23:51 MEwebServer kernel: [    0.585067] TCP: cubic registered
May  8 15:23:51 MEwebServer kernel: [    0.585190] NET: Registered protocol family 10
May  8 15:23:51 MEwebServer kernel: [    0.585391] NET: Registered protocol family 17
May  8 15:23:51 MEwebServer kernel: [    0.585457] Key type dns_resolver registered
May  8 15:23:51 MEwebServer kernel: [    0.585720] Loading compiled-in X.509 certificates
May  8 15:23:51 MEwebServer kernel: [    0.586749] Loaded X.509 cert 'Magrathea: Glacier signing key: 1981bc916ffc00599231ec5630e666e0256fd6f1'
May  8 15:23:51 MEwebServer kernel: [    0.586839] registered taskstats version 1
May  8 15:23:51 MEwebServer kernel: [    0.588821] Key type trusted registered
May  8 15:23:51 MEwebServer kernel: [    0.591757] Key type encrypted registered
May  8 15:23:51 MEwebServer kernel: [    0.591819] AppArmor: AppArmor sha1 policy hashing enabled
May  8 15:23:51 MEwebServer kernel: [    0.591878] IMA: No TPM chip found, activating TPM-bypass!
May  8 15:23:51 MEwebServer kernel: [    0.592057] regulator-dummy: disabling
May  8 15:23:51 MEwebServer kernel: [    0.592156]   Magic number: 15:899:383
May  8 15:23:51 MEwebServer kernel: [    0.592328] rtc_cmos 00:04: setting system clock to 2015-05-08 14:23:15 UTC (1431094995)
May  8 15:23:51 MEwebServer kernel: [    0.592490] acpi-cpufreq: overriding BIOS provided _PSD data
May  8 15:23:51 MEwebServer kernel: [    0.592608] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  8 15:23:51 MEwebServer kernel: [    0.592668] EDD information not available.
May  8 15:23:51 MEwebServer kernel: [    0.592749] PM: Hibernation image not present or could not be loaded.
May  8 15:23:51 MEwebServer kernel: [    0.594129] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
May  8 15:23:51 MEwebServer kernel: [    0.594205] Write protecting the kernel read-only data: 12288k
May  8 15:23:51 MEwebServer kernel: [    0.596439] Freeing unused kernel memory: 792K (ffff88000173a000 - ffff880001800000)
May  8 15:23:51 MEwebServer kernel: [    0.598293] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
May  8 15:23:51 MEwebServer kernel: [    0.608969] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
May  8 15:23:51 MEwebServer kernel: [    0.622175] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
May  8 15:23:51 MEwebServer kernel: [    0.622451] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
May  8 15:23:51 MEwebServer kernel: [    0.626205] md: linear personality registered for level -1
May  8 15:23:51 MEwebServer kernel: [    0.628615] md: multipath personality registered for level -4
May  8 15:23:51 MEwebServer kernel: [    0.630997] md: raid0 personality registered for level 0
May  8 15:23:51 MEwebServer kernel: [    0.633679] md: raid1 personality registered for level 1
May  8 15:23:51 MEwebServer kernel: [    0.704176] raid6: sse2x1    3806 MB/s
May  8 15:23:51 MEwebServer kernel: [    0.772156] raid6: sse2x2    5916 MB/s
May  8 15:23:51 MEwebServer kernel: [    0.840144] raid6: sse2x4    6681 MB/s
May  8 15:23:51 MEwebServer kernel: [    0.840201] raid6: using algorithm sse2x4 (6681 MB/s)
May  8 15:23:51 MEwebServer kernel: [    0.840259] raid6: using intx1 recovery algorithm
May  8 15:23:51 MEwebServer kernel: [    0.841501] xor: measuring software checksum speed
May  8 15:23:51 MEwebServer kernel: [    0.880132]    prefetch64-sse: 11516.000 MB/sec
May  8 15:23:51 MEwebServer kernel: [    0.920126]    generic_sse: 10880.000 MB/sec
May  8 15:23:51 MEwebServer kernel: [    0.920184] xor: using function: prefetch64-sse (11516.000 MB/sec)
May  8 15:23:51 MEwebServer kernel: [    0.921338] async_tx: api initialized (async)
May  8 15:23:51 MEwebServer kernel: [    0.928154] md: raid6 personality registered for level 6
May  8 15:23:51 MEwebServer kernel: [    0.928215] md: raid5 personality registered for level 5
May  8 15:23:51 MEwebServer kernel: [    0.928273] md: raid4 personality registered for level 4
May  8 15:23:51 MEwebServer kernel: [    0.933822] md: raid10 personality registered for level 10
May  8 15:23:51 MEwebServer kernel: [    1.144863] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:24:1d:66:65:be
May  8 15:23:51 MEwebServer kernel: [    1.144940] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
May  8 15:23:51 MEwebServer kernel: [    1.145038] pata_amd 0000:00:06.0: version 0.4.1
May  8 15:23:51 MEwebServer kernel: [    1.145572] scsi0 : pata_amd
May  8 15:23:51 MEwebServer kernel: [    1.145696] scsi1 : pata_amd
May  8 15:23:51 MEwebServer kernel: [    1.145780] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
May  8 15:23:51 MEwebServer kernel: [    1.145841] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
May  8 15:23:51 MEwebServer kernel: [    1.145931] sata_nv 0000:00:08.0: version 3.5
May  8 15:23:51 MEwebServer kernel: [    1.146081] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
May  8 15:23:51 MEwebServer kernel: [    1.146343] scsi2 : sata_nv
May  8 15:23:51 MEwebServer kernel: [    1.146443] scsi3 : sata_nv
May  8 15:23:51 MEwebServer kernel: [    1.146527] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 22
May  8 15:23:51 MEwebServer kernel: [    1.146588] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 22
May  8 15:23:51 MEwebServer kernel: [    1.300286] ata1.01: NODEV after polling detection
May  8 15:23:51 MEwebServer kernel: [    1.308653] ata1.00: ATAPI: PHILIPS DVDR1628P1, Q1.1, max UDMA/33
May  8 15:23:51 MEwebServer kernel: [    1.308723] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
May  8 15:23:51 MEwebServer kernel: [    1.324581] ata1.00: configured for UDMA/33
May  8 15:23:51 MEwebServer kernel: [    1.327405] scsi 0:0:0:0: CD-ROM            PHILIPS  DVDR1628P1       Q1.1 PQ: 0 ANSI: 5
May  8 15:23:51 MEwebServer kernel: [    1.331266] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May  8 15:23:51 MEwebServer kernel: [    1.331332] cdrom: Uniform CD-ROM driver Revision: 3.20
May  8 15:23:51 MEwebServer kernel: [    1.331530] sr 0:0:0:0: Attached scsi CD-ROM sr0
May  8 15:23:51 MEwebServer kernel: [    1.331579] sr 0:0:0:0: Attached scsi generic sg0 type 5
May  8 15:23:51 MEwebServer kernel: [    1.331865] ata2: port disabled--ignoring
May  8 15:23:51 MEwebServer kernel: [    1.544075] tsc: Refined TSC clocksource calibration: 2812.792 MHz
May  8 15:23:51 MEwebServer kernel: [    1.612088] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  8 15:23:51 MEwebServer kernel: [    1.620289] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
May  8 15:23:51 MEwebServer kernel: [    1.620354] ata3.00: 488397168 sectors, multi 16: LBA48 
May  8 15:23:51 MEwebServer kernel: [    1.628290] ata3.00: configured for UDMA/133
May  8 15:23:51 MEwebServer kernel: [    1.628498] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
May  8 15:23:51 MEwebServer kernel: [    1.628733] sd 2:0:0:0: Attached scsi generic sg1 type 0
May  8 15:23:51 MEwebServer kernel: [    1.628744] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
May  8 15:23:51 MEwebServer kernel: [    1.628815] sd 2:0:0:0: [sda] Write Protect is off
May  8 15:23:51 MEwebServer kernel: [    1.628817] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May  8 15:23:51 MEwebServer kernel: [    1.628841] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 15:23:51 MEwebServer kernel: [    1.670913]  sda: sda1 sda2 < sda5 >
May  8 15:23:51 MEwebServer kernel: [    1.671345] sd 2:0:0:0: [sda] Attached SCSI disk
May  8 15:23:51 MEwebServer kernel: [    2.096021] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May  8 15:23:51 MEwebServer kernel: [    2.105077] ata4.00: HPA detected: current 488395055, native 488397168
May  8 15:23:51 MEwebServer kernel: [    2.105144] ata4.00: ATA-8: WDC WD2500AAJS-00VTA0, 01.01B01, max UDMA/133
May  8 15:23:51 MEwebServer kernel: [    2.105205] ata4.00: 488395055 sectors, multi 16: LBA48 NCQ (depth 0/32)
May  8 15:23:51 MEwebServer kernel: [    2.121078] ata4.00: configured for UDMA/133
May  8 15:23:51 MEwebServer kernel: [    2.121308] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500AAJS-0 01.0 PQ: 0 ANSI: 5
May  8 15:23:51 MEwebServer kernel: [    2.121538] sd 3:0:0:0: Attached scsi generic sg2 type 0
May  8 15:23:51 MEwebServer kernel: [    2.121567] sd 3:0:0:0: [sdb] 488395055 512-byte logical blocks: (250 GB/232 GiB)
May  8 15:23:51 MEwebServer kernel: [    2.121610] sd 3:0:0:0: [sdb] Write Protect is off
May  8 15:23:51 MEwebServer kernel: [    2.121611] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May  8 15:23:51 MEwebServer kernel: [    2.121632] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  8 15:23:51 MEwebServer kernel: [    2.176406]  sdb: sdb1 sdb2 < sdb5 >
May  8 15:23:51 MEwebServer kernel: [    2.176877] sd 3:0:0:0: [sdb] Attached SCSI disk
May  8 15:23:51 MEwebServer kernel: [    2.327656] md: bind<sda1>
May  8 15:23:51 MEwebServer kernel: [    2.329292] md/raid1:md0: active with 1 out of 2 mirrors
May  8 15:23:51 MEwebServer kernel: [    2.329372] md0: detected capacity change from 0 to 245662285824
May  8 15:23:51 MEwebServer kernel: [    2.355503]  md0: unknown partition table
May  8 15:23:51 MEwebServer kernel: [    2.544035] Switched to clocksource tsc
May  8 15:23:51 MEwebServer kernel: [    2.566690] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
May  8 15:23:51 MEwebServer kernel: [    5.389286] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:23:51 MEwebServer kernel: [    5.389362] ata4.00: BMDMA stat 0x24
May  8 15:23:51 MEwebServer kernel: [    5.389420] ata4.00: failed command: READ DMA
May  8 15:23:51 MEwebServer kernel: [    5.389481] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:23:51 MEwebServer kernel: [    5.389481]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:23:51 MEwebServer kernel: [    5.389579] ata4.00: status: { DRDY ERR }
May  8 15:23:51 MEwebServer kernel: [    5.389636] ata4.00: error: { UNC }
May  8 15:23:51 MEwebServer kernel: [    5.404190] ata4.00: configured for UDMA/133
May  8 15:23:51 MEwebServer kernel: [    5.404270] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:23:51 MEwebServer kernel: [    5.404328] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [    5.404384] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:23:51 MEwebServer kernel: [    5.404444] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [    5.404500] Sense Key : Medium Error [current] [descriptor]
May  8 15:23:51 MEwebServer kernel: [    5.404686] Descriptor sense data with sense descriptors (in hex):
May  8 15:23:51 MEwebServer kernel: [    5.404788]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:23:51 MEwebServer kernel: [    5.405566]         00 00 01 97 
May  8 15:23:51 MEwebServer kernel: [    5.405834] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [    5.405891] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:23:51 MEwebServer kernel: [    5.405993] sd 3:0:0:0: [sdb] CDB: 
May  8 15:23:51 MEwebServer kernel: [    5.406050] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:23:51 MEwebServer kernel: [    5.406617] end_request: I/O error, dev sdb, sector 407
May  8 15:23:51 MEwebServer kernel: [    5.406676] Buffer I/O error on device sdb, logical block 407
May  8 15:23:51 MEwebServer kernel: [    5.406759] ata4: EH complete
May  8 15:23:51 MEwebServer kernel: [    8.525218] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:23:51 MEwebServer kernel: [    8.527632] ata4.00: BMDMA stat 0x24
May  8 15:23:51 MEwebServer kernel: [    8.527690] ata4.00: failed command: READ DMA
May  8 15:23:51 MEwebServer kernel: [    8.527750] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:23:51 MEwebServer kernel: [    8.527750]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:23:51 MEwebServer kernel: [    8.527839] ata4.00: status: { DRDY ERR }
May  8 15:23:51 MEwebServer kernel: [    8.527896] ata4.00: error: { UNC }
May  8 15:23:51 MEwebServer kernel: [    8.552116] ata4.00: configured for UDMA/133
May  8 15:23:51 MEwebServer kernel: [    8.552191] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:23:51 MEwebServer kernel: [    8.552250] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [    8.552306] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:23:51 MEwebServer kernel: [    8.552365] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [    8.552421] Sense Key : Medium Error [current] [descriptor]
May  8 15:23:51 MEwebServer kernel: [    8.552607] Descriptor sense data with sense descriptors (in hex):
May  8 15:23:51 MEwebServer kernel: [    8.552708]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:23:51 MEwebServer kernel: [    8.553487]         00 00 01 97 
May  8 15:23:51 MEwebServer kernel: [    8.553754] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [    8.553811] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:23:51 MEwebServer kernel: [    8.553914] sd 3:0:0:0: [sdb] CDB: 
May  8 15:23:51 MEwebServer kernel: [    8.553970] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:23:51 MEwebServer kernel: [    8.554536] end_request: I/O error, dev sdb, sector 407
May  8 15:23:51 MEwebServer kernel: [    8.554596] Buffer I/O error on device sdb, logical block 407
May  8 15:23:51 MEwebServer kernel: [    8.554677] ata4: EH complete
May  8 15:23:51 MEwebServer kernel: [    9.054700] random: nonblocking pool is initialized
May  8 15:23:51 MEwebServer kernel: [   12.721768] MCE: In-kernel MCE decoding enabled.
May  8 15:23:51 MEwebServer kernel: [   12.797244] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
May  8 15:23:51 MEwebServer kernel: [   12.797324] i2c i2c-1: nForce2 SMBus adapter at 0xc800
May  8 15:23:51 MEwebServer kernel: [   12.828913] EDAC MC: Ver: 3.0.0
May  8 15:23:51 MEwebServer kernel: [   12.880948] AMD64 EDAC driver v3.4.0
May  8 15:23:51 MEwebServer kernel: [   12.881048] EDAC amd64: DRAM ECC disabled.
May  8 15:23:51 MEwebServer kernel: [   12.881109] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May  8 15:23:51 MEwebServer kernel: [   12.881109]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May  8 15:23:51 MEwebServer kernel: [   12.881109]  (Note that use of the override may cause unknown side effects.)
May  8 15:23:51 MEwebServer kernel: [   13.151045] kvm: Nested Virtualization enabled
May  8 15:23:51 MEwebServer kernel: [   13.151287] kvm: Nested Paging enabled
May  8 15:23:51 MEwebServer kernel: [   13.416252] [drm] Initialized drm 1.1.0 20060810
May  8 15:23:51 MEwebServer kernel: [   13.734222] wmi: Mapper loaded
May  8 15:23:51 MEwebServer kernel: [   14.286186] forcedeth 0000:00:07.0: irq 40 for MSI/MSI-X
May  8 15:23:51 MEwebServer kernel: [   14.286215] forcedeth 0000:00:07.0 eth0: MSI enabled
May  8 15:23:51 MEwebServer kernel: [   14.416339] ip_tables: (C) 2000-2006 Netfilter Core Team
May  8 15:23:51 MEwebServer kernel: [   14.494193] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
May  8 15:23:51 MEwebServer kernel: [   14.859231] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  8 15:23:51 MEwebServer kernel: [   15.285563] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
May  8 15:23:51 MEwebServer kernel: [   15.855120] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:23:51 MEwebServer kernel: [   15.855187] ata4.00: BMDMA stat 0x24
May  8 15:23:51 MEwebServer kernel: [   15.855246] ata4.00: failed command: READ DMA
May  8 15:23:51 MEwebServer kernel: [   15.855307] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:23:51 MEwebServer kernel: [   15.855307]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:23:51 MEwebServer kernel: [   15.855405] ata4.00: status: { DRDY ERR }
May  8 15:23:51 MEwebServer kernel: [   15.855463] ata4.00: error: { UNC }
May  8 15:23:51 MEwebServer kernel: [   15.879001] ata4.00: configured for UDMA/133
May  8 15:23:51 MEwebServer kernel: [   15.879083] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:23:51 MEwebServer kernel: [   15.879142] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   15.879198] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:23:51 MEwebServer kernel: [   15.879257] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   15.879313] Sense Key : Medium Error [current] [descriptor]
May  8 15:23:51 MEwebServer kernel: [   15.879499] Descriptor sense data with sense descriptors (in hex):
May  8 15:23:51 MEwebServer kernel: [   15.879601]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:23:51 MEwebServer kernel: [   15.880380]         00 00 01 97 
May  8 15:23:51 MEwebServer kernel: [   15.880648] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   15.880705] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:23:51 MEwebServer kernel: [   15.880807] sd 3:0:0:0: [sdb] CDB: 
May  8 15:23:51 MEwebServer kernel: [   15.880863] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:23:51 MEwebServer kernel: [   15.881430] end_request: I/O error, dev sdb, sector 407
May  8 15:23:51 MEwebServer kernel: [   15.881490] Buffer I/O error on device sdb, logical block 407
May  8 15:23:51 MEwebServer kernel: [   15.881574] ata4: EH complete
May  8 15:23:51 MEwebServer kernel: [   18.812900] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:23:51 MEwebServer kernel: [   18.812966] ata4.00: BMDMA stat 0x24
May  8 15:23:51 MEwebServer kernel: [   18.813024] ata4.00: failed command: READ DMA
May  8 15:23:51 MEwebServer kernel: [   18.813085] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:23:51 MEwebServer kernel: [   18.813085]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:23:51 MEwebServer kernel: [   18.813174] ata4.00: status: { DRDY ERR }
May  8 15:23:51 MEwebServer kernel: [   18.813231] ata4.00: error: { UNC }
May  8 15:23:51 MEwebServer kernel: [   18.834782] ata4.00: configured for UDMA/133
May  8 15:23:51 MEwebServer kernel: [   18.834801] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:23:51 MEwebServer kernel: [   18.834803] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   18.834804] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:23:51 MEwebServer kernel: [   18.834805] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   18.834807] Sense Key : Medium Error [current] [descriptor]
May  8 15:23:51 MEwebServer kernel: [   18.834809] Descriptor sense data with sense descriptors (in hex):
May  8 15:23:51 MEwebServer kernel: [   18.834810]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:23:51 MEwebServer kernel: [   18.834815]         00 00 01 97 
May  8 15:23:51 MEwebServer kernel: [   18.834817] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   18.834819] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:23:51 MEwebServer kernel: [   18.834821] sd 3:0:0:0: [sdb] CDB: 
May  8 15:23:51 MEwebServer kernel: [   18.834822] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:23:51 MEwebServer kernel: [   18.834827] end_request: I/O error, dev sdb, sector 407
May  8 15:23:51 MEwebServer kernel: [   18.834889] Buffer I/O error on device sdb, logical block 407
May  8 15:23:51 MEwebServer kernel: [   18.834971] ata4: EH complete
May  8 15:23:51 MEwebServer kernel: [   25.025229] AMD64 EDAC driver v3.4.0
May  8 15:23:51 MEwebServer kernel: [   25.025259] EDAC amd64: DRAM ECC disabled.
May  8 15:23:51 MEwebServer kernel: [   25.025263] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May  8 15:23:51 MEwebServer kernel: [   25.025263]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May  8 15:23:51 MEwebServer kernel: [   25.025263]  (Note that use of the override may cause unknown side effects.)
May  8 15:23:51 MEwebServer kernel: [   25.215425] lp: driver loaded but no devices found
May  8 15:23:51 MEwebServer kernel: [   28.028546] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:23:51 MEwebServer kernel: [   28.028551] ata4.00: BMDMA stat 0x24
May  8 15:23:51 MEwebServer kernel: [   28.028555] ata4.00: failed command: READ DMA
May  8 15:23:51 MEwebServer kernel: [   28.028559] ata4.00: cmd c8/00:08:90:01:00/00:00:00:00:00/e0 tag 0 dma 4096 in
May  8 15:23:51 MEwebServer kernel: [   28.028559]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:23:51 MEwebServer kernel: [   28.028561] ata4.00: status: { DRDY ERR }
May  8 15:23:51 MEwebServer kernel: [   28.028563] ata4.00: error: { UNC }
May  8 15:23:51 MEwebServer kernel: [   28.053462] ata4.00: configured for UDMA/133
May  8 15:23:51 MEwebServer kernel: [   28.053480] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:23:51 MEwebServer kernel: [   28.053482] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   28.053484] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:23:51 MEwebServer kernel: [   28.053485] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   28.053487] Sense Key : Medium Error [current] [descriptor]
May  8 15:23:51 MEwebServer kernel: [   28.053489] Descriptor sense data with sense descriptors (in hex):
May  8 15:23:51 MEwebServer kernel: [   28.053490]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:23:51 MEwebServer kernel: [   28.053495]         00 00 01 97 
May  8 15:23:51 MEwebServer kernel: [   28.053497] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   28.053499] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:23:51 MEwebServer kernel: [   28.053501] sd 3:0:0:0: [sdb] CDB: 
May  8 15:23:51 MEwebServer kernel: [   28.053502] Read(10): 28 00 00 00 01 90 00 00 08 00
May  8 15:23:51 MEwebServer kernel: [   28.053507] end_request: I/O error, dev sdb, sector 407
May  8 15:23:51 MEwebServer kernel: [   28.053509] Buffer I/O error on device sdb, logical block 407
May  8 15:23:51 MEwebServer kernel: [   28.053519] ata4: EH complete
May  8 15:23:51 MEwebServer kernel: [   31.173501] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May  8 15:23:51 MEwebServer kernel: [   31.173505] ata4.00: BMDMA stat 0x24
May  8 15:23:51 MEwebServer kernel: [   31.173508] ata4.00: failed command: READ DMA
May  8 15:23:51 MEwebServer kernel: [   31.173513] ata4.00: cmd c8/00:01:97:01:00/00:00:00:00:00/e0 tag 0 dma 512 in
May  8 15:23:51 MEwebServer kernel: [   31.173513]          res 51/40:00:97:01:00/00:00:00:00:00/e0 Emask 0x9 (media error)
May  8 15:23:51 MEwebServer kernel: [   31.173515] ata4.00: status: { DRDY ERR }
May  8 15:23:51 MEwebServer kernel: [   31.173516] ata4.00: error: { UNC }
May  8 15:23:51 MEwebServer kernel: [   31.196384] ata4.00: configured for UDMA/133
May  8 15:23:51 MEwebServer kernel: [   31.196468] sd 3:0:0:0: [sdb] Unhandled sense code
May  8 15:23:51 MEwebServer kernel: [   31.196470] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   31.196472] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May  8 15:23:51 MEwebServer kernel: [   31.196473] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   31.196474] Sense Key : Medium Error [current] [descriptor]
May  8 15:23:51 MEwebServer kernel: [   31.196477] Descriptor sense data with sense descriptors (in hex):
May  8 15:23:51 MEwebServer kernel: [   31.196478]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May  8 15:23:51 MEwebServer kernel: [   31.196483]         00 00 01 97 
May  8 15:23:51 MEwebServer kernel: [   31.196485] sd 3:0:0:0: [sdb]  
May  8 15:23:51 MEwebServer kernel: [   31.196487] Add. Sense: Unrecovered read error - auto reallocate failed
May  8 15:23:51 MEwebServer kernel: [   31.196489] sd 3:0:0:0: [sdb] CDB: 
May  8 15:23:51 MEwebServer kernel: [   31.196490] Read(10): 28 00 00 00 01 97 00 00 01 00
May  8 15:23:51 MEwebServer kernel: [   31.196495] end_request: I/O error, dev sdb, sector 407
May  8 15:23:51 MEwebServer kernel: [   31.196497] Buffer I/O error on device sdb, logical block 407
May  8 15:23:51 MEwebServer kernel: [   31.196517] ata4: EH complete
May  8 15:23:51 MEwebServer kernel: [   34.410978] Adding 4159484k swap on /dev/sda5.  Priority:-1 extents:1 across:4159484k FS
May  8 15:23:51 MEwebServer kernel: [   34.413691] Adding 4159484k swap on /dev/sdb5.  Priority:-2 extents:1 across:4159484k FS
May  8 15:23:51 MEwebServer kernel: [   35.140298] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro
May  8 15:23:51 MEwebServer kernel: [   36.041474] type=1400 audit(1431095031.316:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=1150 comm="apparmor_parser"
May  8 15:23:51 MEwebServer kernel: [   36.044382] type=1400 audit(1431095031.320:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1149 comm="apparmor_parser"
May  8 15:23:51 MEwebServer kernel: [   36.044391] type=1400 audit(1431095031.320:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1149 comm="apparmor_parser"
May  8 15:23:51 MEwebServer kernel: [   36.044395] type=1400 audit(1431095031.320:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1149 comm="apparmor_parser"
May  8 15:23:51 MEwebServer kernel: [   36.044837] type=1400 audit(1431095031.320:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1149 comm="apparmor_parser"
May  8 15:23:51 MEwebServer kernel: [   36.044842] type=1400 audit(1431095031.320:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1149 comm="apparmor_parser"
May  8 15:23:51 MEwebServer kernel: [   36.045075] type=1400 audit(1431095031.320:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1149 comm="apparmor_parser"
May  8 15:23:51 MEwebServer kernel: [   36.047387] type=1400 audit(1431095031.324:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1152 comm="apparmor_parser"
May  8 15:23:51 MEwebServer kernel: [   36.340986] type=1400 audit(1431095031.616:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=1276 comm="apparmor_parser"
May  8 15:25:28 MEwebServer kernel: [  133.049332] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:40:f2:01:0c:bb:a6:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 

```

```
 * Stopping load modules from /etc/modules[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
 * Starting set console font[74G[ OK ]
 * Stopping set console font[74G[ OK ]
 * Starting userspace bootsplash[74G[ OK ]
 * Starting Send an event to indicate plymouth is up[74G[ OK ]
 * Stopping Send an event to indicate plymouth is up[74G[ OK ]
 * Stopping userspace bootsplash[74G[ OK ]
 * Stopping Read required files in advance[74G[ OK ]
 * Starting Mount filesystems on boot[74G[ OK ]
 * Stopping Track if upstart is running in a container[74G[ OK ]
 * Starting set console keymap[74G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[74G[ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted[74G[ OK ]
 * Stopping set console keymap[74G[ OK ]
 * Starting Signal sysvinit that the rootfs is mounted[74G[ OK ]
 * Starting Clean /tmp directory[74G[ OK ]
 * Stopping Clean /tmp directory[74G[ OK ]
 * Starting Signal sysvinit that local filesystems are mounted[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Stopping Mount filesystems on boot[74G[ OK ]
 * Starting flush early job output to logs[74G[ OK ]
 * Stopping Failsafe Boot Delay[74G[ OK ]
 * Starting D-Bus system message bus[74G[ OK ]
 * Starting System V initialisation compatibility[74G[ OK ]
 * Starting SystemD login management service[74G[ OK ]
 * Stopping flush early job output to logs[74G[ OK ]
 * Starting configure virtual network devices[74G[ OK ]
 * Starting system logging daemon[74G[ OK ]
 * Starting Bridge file events into upstart[74G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting dovecot - pop3/imap mail server[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Stopping save kernel messages[74G[ OK ]
 * Starting automatic crash report generation[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Starting OpenSSH server[74G[ OK ]
 * Starting Postfix Mail Transport Agent postfix       [80G 
[74G[ OK ]
 * Starting MD monitoring service mdadm --monitor       [80G 
[74G[ OK ]
 * Restoring resolver state...       [80G 
[74G[ OK ]
 * Starting crash report submission daemon[74G[ OK ]
 * 
ERROR  No file(s) found for glob /var/log/vsftpd.log
ERROR  Failed during configuration: Have not found any log file for vsftpd jail
 * Starting authentication failure monitor fail2ban       [80G 
[74G[[31mfail[39;49m]
 * Starting MySQL Server[74G[ OK ]
 * Stopping System V runlevel compatibility[74G[ OK ]

```

I appreciate your gonna need a lot more info I just want sure where to start so guys please let me know what yo uneed ot know and I'll respond asap

---

### Post by cariboo on 2015-05-09
It looks like /dev/sdb is failing.

---

### Post by bigmonmulgrew on 2015-05-10
OK so assuming for a moment this is a hardware fault its a mirror. Surely it should still run with 1 good drive.

---

### Post by darkod on 2015-05-10
When you were configuring mdadm did you select to boot degraded or not? If you selected No it will not boot with any members failed even if the raid itself is good and can run.

---

### Post by bigmonmulgrew on 2015-05-10
It was a while ago so I don't recall but the whole point of the raid was to run degraded. I vaguely recall testing it would run degraded.

Perhaps this is something changed in the upgrade.

---

### Post by bigmonmulgrew on 2015-05-10
I've checked and it is set to boot degraded

---

