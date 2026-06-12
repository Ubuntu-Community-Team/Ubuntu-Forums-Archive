---
title: "Starling SD Card Reader Doesn't Work"
date: 2009-12-31
forum: System76 Support
---

### Post by Ian505 on 2009-12-31
I got my Starling about midway through December, but haven't been able to get the SD card reader to work. I am suspecting that a few messages that I get each time I boot, just before the ubuntu splash screen appears, would lend some clue as to what's going on. Below is my syslog for today, and bolded are the messages like the ones I get during boot. (They are only there for about a second, and therefore I don't know exactly which ones appear for not all of the bolded below do. However, I do know that they are along the lines of those highlighted.)

```
Dec 31 09:58:49 system76-netbook syslogd 1.5.0#5ubuntu3: restart.
Dec 31 09:58:49 system76-netbook kernel: Inspecting /boot/System.map-2.6.28-17-generic
Dec 31 09:58:49 system76-netbook kernel: Cannot find map file.
Dec 31 09:58:49 system76-netbook kernel: Loaded 53694 symbols from 48 modules.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Linux version 2.6.28-17-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 (Ubuntu 2.6.28-17.58-generic)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] KERNEL supported cpus:
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Intel GenuineIntel
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   AMD AuthenticAMD
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   NSC Geode by NSC
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Cyrix CyrixInstead
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Centaur CentaurHauls
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   UMC UMC UMC UMC
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f376000 (usable)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 000000007f376000 - 000000007f3bf000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 000000007f3bf000 - 000000007f46d000 (ACPI data)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 000000007f46d000 - 000000007f4bf000 (ACPI NVS)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 000000007f4bf000 - 000000007f500000 (ACPI data)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 000000007f500000 - 0000000080000000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] DMI 2.4 present.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] last_pfn = 0x7f376 max_arch_pfn = 0x100000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Scanning 2 areas for low memory corruption
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] modified physical RAM map:
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 0000000000100000 - 000000007f376000 (usable)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 000000007f376000 - 000000007f3bf000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 000000007f3bf000 - 000000007f46d000 (ACPI data)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 000000007f46d000 - 000000007f4bf000 (ACPI NVS)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 000000007f4bf000 - 000000007f500000 (ACPI data)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 000000007f500000 - 0000000080000000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] RAMDISK: 378bc000 - 37fef4d0
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Allocated new RAMDISK: 0087d000 - 00fb04d0
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Move RAMDISK from 00000000378bc000 - 0000000037fef4cf to 0087d000 - 00fb04cf
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: RSDP 000FE020, 0024 (r2  haier)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: XSDT 7F4FE120, 0064 (r1  haier computer        1       1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: FACP 7F4FC000, 00F4 (r4  haier computer        1 MSFT  1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: DSDT 7F4F1000, 6209 (r1  haier computer        1 MSFT  1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: FACS 7F488000, 0040
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: SSDT 7F4FD000, 04C4 (r2  PmRef    CpuPm     3000 INTL 20060317)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: HPET 7F4FB000, 0038 (r1  haier computer        1 MSFT  1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: APIC 7F4FA000, 0068 (r2  haier computer        1 MSFT  1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: MCFG 7F4F9000, 003C (r1  haier computer        1 MSFT  1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: ASF! 7F4F8000, 00A5 (r32  haier computer        1 MSFT  1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: SLIC 7F4F0000, 0180 (r1  haier computer        1 MSFT  1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: BOOT 7F4EF000, 0028 (r1  haier computer        1 MSFT  1000013)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] 1151MB HIGHMEM available.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] 883MB LOWMEM available.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   low ram: 00000000 - 373fe000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   bootmap 00012000 - 00018e80
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #7 [000087d000 - 0000fb04d0]      NEW RAMDISK ==> [000087d000 - 0000fb04d0]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Zone PFN ranges:
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   HighMem  0x000373fe -> 0x0007f376
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Movable zone start PFN for each node
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] early_node_map[4] active PFN ranges
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]     0: 0x00000006 -> 0x00000007
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]     0: 0x00000010 -> 0x00000092
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]     0: 0x00000100 -> 0x0007f376
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] On node 0 totalpages: 520955
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   DMA zone: 3941 pages, LIFO batch:0
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Normal zone: 1736 pages used for memmap
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Normal zone: 220470 pages, LIFO batch:31
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   HighMem zone: 2303 pages used for memmap
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   HighMem zone: 292473 pages, LIFO batch:31
Dec 31 09:58:49 system76-netbook kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 516884
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Kernel command line: root=UUID=9fdd20be-ce71-4f01-9861-14fcfe916c81 ro quiet splash pciehp.pciehp_force=1 
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Initializing CPU#0
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Fast TSC calibration using PIT
Dec 31 09:58:49 system76-netbook kernel: [    0.000000] Detected 1596.138 MHz processor.
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Console: colour VGA+ 80x25
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] console [tty0] enabled
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] allocated 10421560 bytes of page_cgroup
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Memory: 2040492k/2084312k available (4116k kernel code, 42468k reserved, 2199k data, 532k init, 1179104k highmem)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] virtual kernel memory layout:
Dec 31 09:58:49 system76-netbook kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000]       .data : 0xc050525d - 0xc072ae60   (2199 kB)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000]       .text : 0xc0100000 - 0xc050525d   (4116 kB)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] hpet clockevent registered
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.27 BogoMIPS (lpj=6384552)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Security Framework initialized
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] SELinux:  Disabled at boot.
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] AppArmor: AppArmor initialized
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Mount-cache hash table entries: 512
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Initializing cgroup subsys ns
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Initializing cgroup subsys cpuacct
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Initializing cgroup subsys memory
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Initializing cgroup subsys freezer
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] CPU: L2 cache: 512K
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] CPU: Physical Processor ID: 0
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] CPU: Processor Core ID: 0
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] using mwait in idle threads.
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Checking 'hlt' instruction... OK.
Dec 31 09:58:49 system76-netbook kernel: [    0.019761] ACPI: Core revision 20080926
Dec 31 09:58:49 system76-netbook kernel: [    0.022496] ACPI: Checking initramfs for custom DSDT
Dec 31 09:58:49 system76-netbook kernel: [    0.500631] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 31 09:58:49 system76-netbook kernel: [    0.540677] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Dec 31 09:58:49 system76-netbook kernel: [    0.544002] Booting processor 1 APIC 0x1 ip 0x6000
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Initializing CPU#1
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] Calibrating delay using timer specific routine.. 3191.93 BogoMIPS (lpj=6383878)
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] CPU: L2 cache: 512K
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] CPU: Physical Processor ID: 0
Dec 31 09:58:49 system76-netbook kernel: [    0.004000] CPU: Processor Core ID: 0
Dec 31 09:58:49 system76-netbook kernel: [    0.628227] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Dec 31 09:58:49 system76-netbook kernel: [    0.628265] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 31 09:58:49 system76-netbook kernel: [    0.632067] Brought up 2 CPUs
Dec 31 09:58:49 system76-netbook kernel: [    0.632074] Total of 2 processors activated (6384.21 BogoMIPS).
Dec 31 09:58:49 system76-netbook kernel: [    0.632148] CPU0 attaching sched-domain:
Dec 31 09:58:49 system76-netbook kernel: [    0.632153]  domain 0: span 0-1 level SIBLING
Dec 31 09:58:49 system76-netbook kernel: [    0.632158]   groups: 0 1
Dec 31 09:58:49 system76-netbook kernel: [    0.632169] CPU1 attaching sched-domain:
Dec 31 09:58:49 system76-netbook kernel: [    0.632173]  domain 0: span 0-1 level SIBLING
Dec 31 09:58:49 system76-netbook kernel: [    0.632177]   groups: 1 0
Dec 31 09:58:49 system76-netbook kernel: [    0.632313] net_namespace: 776 bytes
Dec 31 09:58:49 system76-netbook kernel: [    0.632313] Booting paravirtualized kernel on bare hardware
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] Time: 14:58:32  Date: 12/31/09
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] regulator: core version 0.5
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] NET: Registered protocol family 16
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] EISA bus registered
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] ACPI: bus type pci registered
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] PCI: MCFG area at e0000000 reserved in E820
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] PCI: Using MMCONFIG for extended config space
Dec 31 09:58:49 system76-netbook kernel: [    0.632691] PCI: Using configuration type 1 for base access
Dec 31 09:58:49 system76-netbook kernel: [    0.637622] ACPI: EC: Look up EC in DSDT
Dec 31 09:58:49 system76-netbook kernel: [    0.644277] ACPI: BIOS _OSI(Linux) query ignored
Dec 31 09:58:49 system76-netbook kernel: [    0.645529] ACPI: EC: non-query interrupt received, switching to interrupt mode
Dec 31 09:58:49 system76-netbook kernel: [    1.144015] ACPI: EC: missing confirmations, switch off interrupt mode.
Dec 31 09:58:49 system76-netbook kernel: [    1.149345] ACPI: Interpreter enabled
Dec 31 09:58:49 system76-netbook kernel: [    1.149352] ACPI: (supports S0 S3 S4 S5)
Dec 31 09:58:49 system76-netbook kernel: [    1.149391] ACPI: Using IOAPIC for interrupt routing
Dec 31 09:58:49 system76-netbook kernel: [    1.159691] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 31 09:58:49 system76-netbook kernel: [    1.159697] ACPI: EC: driver started in poll mode
Dec 31 09:58:49 system76-netbook kernel: [    1.160071] ACPI: No dock devices found.
Dec 31 09:58:49 system76-netbook kernel: [    1.160097] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 31 09:58:49 system76-netbook kernel: [    1.160224] pci 0000:00:02.0: reg 10 32bit mmio: [0x94280000-0x942fffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.160233] pci 0000:00:02.0: reg 14 io port: [0x40c0-0x40c7]
Dec 31 09:58:49 system76-netbook kernel: [    1.160241] pci 0000:00:02.0: reg 18 32bit mmio: [0x80000000-0x8fffffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.160250] pci 0000:00:02.0: reg 1c 32bit mmio: [0x94300000-0x9433ffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.160291] pci 0000:00:02.1: reg 10 32bit mmio: [0x94200000-0x9427ffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.160423] pci 0000:00:1b.0: reg 10 64bit mmio: [0x94340000-0x94343fff]
Dec 31 09:58:49 system76-netbook kernel: [    1.160472] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 31 09:58:49 system76-netbook kernel: [    1.160480] pci 0000:00:1b.0: PME# disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.160556] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 31 09:58:49 system76-netbook kernel: [    1.160564] pci 0000:00:1c.0: PME# disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.160641] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Dec 31 09:58:49 system76-netbook kernel: [    1.160649] pci 0000:00:1c.1: PME# disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.160725] pci 0000:00:1d.0: reg 20 io port: [0x4080-0x409f]
Dec 31 09:58:49 system76-netbook kernel: [    1.160796] pci 0000:00:1d.1: reg 20 io port: [0x4060-0x407f]
Dec 31 09:58:49 system76-netbook kernel: [    1.160867] pci 0000:00:1d.2: reg 20 io port: [0x4040-0x405f]
Dec 31 09:58:49 system76-netbook kernel: [    1.160938] pci 0000:00:1d.3: reg 20 io port: [0x4020-0x403f]
Dec 31 09:58:49 system76-netbook kernel: [    1.161013] pci 0000:00:1d.7: reg 10 32bit mmio: [0x94344400-0x943447ff]
Dec 31 09:58:49 system76-netbook kernel: [    1.161067] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Dec 31 09:58:49 system76-netbook kernel: [    1.161076] pci 0000:00:1d.7: PME# disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.161252] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Dec 31 09:58:49 system76-netbook kernel: [    1.161260] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
Dec 31 09:58:49 system76-netbook kernel: [    1.161324] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
Dec 31 09:58:49 system76-netbook kernel: [    1.161335] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
Dec 31 09:58:49 system76-netbook kernel: [    1.161346] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
Dec 31 09:58:49 system76-netbook kernel: [    1.161357] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
Dec 31 09:58:49 system76-netbook kernel: [    1.161369] pci 0000:00:1f.2: reg 20 io port: [0x40a0-0x40af]
Dec 31 09:58:49 system76-netbook kernel: [    1.161399] pci 0000:00:1f.2: PME# supported from D3hot
Dec 31 09:58:49 system76-netbook kernel: [    1.161406] pci 0000:00:1f.2: PME# disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.161476] pci 0000:00:1f.3: reg 20 io port: [0x4000-0x401f]
Dec 31 09:58:49 system76-netbook kernel: [    1.161575] pci 0000:01:00.0: reg 10 32bit mmio: [0x93100300-0x931003ff]
Dec 31 09:58:49 system76-netbook kernel: [    1.161640] pci 0000:01:00.0: reg 30 32bit mmio: [0xffff8000-0xffffffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.161740] pci 0000:01:00.2: reg 10 32bit mmio: [0x93100200-0x931002ff]
Dec 31 09:58:49 system76-netbook kernel: [    1.161894] pci 0000:01:00.3: reg 10 32bit mmio: [0x93100100-0x931001ff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162047] pci 0000:01:00.4: reg 10 32bit mmio: [0x93100000-0x931000ff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162208] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162217] pci 0000:00:1c.0: bridge 32bit mmio: [0x93100000-0x941fffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162229] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x90000000-0x90ffffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162301] pci 0000:02:00.0: reg 10 io port: [0x1000-0x10ff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162333] pci 0000:02:00.0: reg 18 64bit mmio: [0x91010000-0x91010fff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162356] pci 0000:02:00.0: reg 20 64bit mmio: [0x91000000-0x9100ffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162371] pci 0000:02:00.0: reg 30 32bit mmio: [0xffff0000-0xffffffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162390] pci 0000:02:00.0: supports D1 D2
Dec 31 09:58:49 system76-netbook kernel: [    1.162394] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 31 09:58:49 system76-netbook kernel: [    1.162403] pci 0000:02:00.0: PME# disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.162491] pci 0000:00:1c.1: bridge io port: [0x1000-0x2fff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162500] pci 0000:00:1c.1: bridge 32bit mmio: [0x92100000-0x930fffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162511] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x91000000-0x920fffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.162584] pci 0000:00:1e.0: transparent bridge
Dec 31 09:58:49 system76-netbook kernel: [    1.162622] bus 00 -> node 0
Dec 31 09:58:49 system76-netbook kernel: [    1.162639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 31 09:58:49 system76-netbook kernel: [    1.163270] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
Dec 31 09:58:49 system76-netbook kernel: [    1.163734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Dec 31 09:58:49 system76-netbook kernel: [    1.164058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Dec 31 09:58:49 system76-netbook kernel: [    1.177198] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Dec 31 09:58:49 system76-netbook kernel: [    1.177463] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Dec 31 09:58:49 system76-netbook kernel: [    1.177725] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Dec 31 09:58:49 system76-netbook kernel: [    1.177985] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Dec 31 09:58:49 system76-netbook kernel: [    1.178244] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Dec 31 09:58:49 system76-netbook kernel: [    1.178505] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Dec 31 09:58:49 system76-netbook kernel: [    1.178766] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Dec 31 09:58:49 system76-netbook kernel: [    1.179027] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Dec 31 09:58:49 system76-netbook kernel: [    1.179498] ACPI: WMI: Mapper loaded
Dec 31 09:58:49 system76-netbook kernel: [    1.179623] SCSI subsystem initialized
Dec 31 09:58:49 system76-netbook kernel: [    1.180023] libata version 3.00 loaded.
Dec 31 09:58:49 system76-netbook kernel: [    1.180082] usbcore: registered new interface driver usbfs
Dec 31 09:58:49 system76-netbook kernel: [    1.180120] usbcore: registered new interface driver hub
Dec 31 09:58:49 system76-netbook kernel: [    1.180156] usbcore: registered new device driver usb
Dec 31 09:58:49 system76-netbook kernel: [    1.180156] PCI: Using ACPI for IRQ routing
Dec 31 09:58:49 system76-netbook kernel: [    1.188021] Bluetooth: Core ver 2.13
Dec 31 09:58:49 system76-netbook kernel: [    1.188059] NET: Registered protocol family 31
Dec 31 09:58:49 system76-netbook kernel: [    1.188059] Bluetooth: HCI device and connection manager initialized
Dec 31 09:58:49 system76-netbook kernel: [    1.188059] Bluetooth: HCI socket layer initialized
Dec 31 09:58:49 system76-netbook kernel: [    1.188059] NET: Registered protocol family 8
Dec 31 09:58:49 system76-netbook kernel: [    1.188059] NET: Registered protocol family 20
Dec 31 09:58:49 system76-netbook kernel: [    1.188076] NetLabel: Initializing
Dec 31 09:58:49 system76-netbook kernel: [    1.188080] NetLabel:  domain hash size = 128
Dec 31 09:58:49 system76-netbook kernel: [    1.188083] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 31 09:58:49 system76-netbook kernel: [    1.188107] NetLabel:  unlabeled traffic allowed by default
Dec 31 09:58:49 system76-netbook kernel: [    1.188138] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 31 09:58:49 system76-netbook kernel: [    1.188147] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Dec 31 09:58:49 system76-netbook kernel: [    1.192122] AppArmor: AppArmor Filesystem Enabled
Dec 31 09:58:49 system76-netbook kernel: [    1.196023] Switched to high resolution mode on CPU 0
Dec 31 09:58:49 system76-netbook kernel: [    1.196338] Switched to high resolution mode on CPU 1
Dec 31 09:58:49 system76-netbook kernel: [    1.200024] pnp: PnP ACPI init
Dec 31 09:58:49 system76-netbook kernel: [    1.200048] ACPI: bus type pnp registered
Dec 31 09:58:49 system76-netbook kernel: [    1.203617] pnp: PnP ACPI: found 9 devices
Dec 31 09:58:49 system76-netbook kernel: [    1.203623] ACPI: ACPI bus type pnp unregistered
Dec 31 09:58:49 system76-netbook kernel: [    1.203629] PnPBIOS: Disabled by ACPI PNP
Dec 31 09:58:49 system76-netbook kernel: [    1.203652] system 00:01: ioport range 0x200-0x20f has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203659] system 00:01: ioport range 0x600-0x60f has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203665] system 00:01: ioport range 0x610-0x610 has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203670] system 00:01: ioport range 0x800-0x80f has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203676] system 00:01: ioport range 0x400-0x47f has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203682] system 00:01: ioport range 0x500-0x53f has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203689] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203696] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203702] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203708] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203715] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203721] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.203728] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Dec 31 09:58:49 system76-netbook kernel: [    1.238671] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Dec 31 09:58:49 system76-netbook kernel: [    1.238679] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
Dec 31 09:58:49 system76-netbook kernel: [    1.238690] pci 0000:00:1c.0:   MEM window: 0x93100000-0x941fffff
Dec 31 09:58:49 system76-netbook kernel: [    1.238698] pci 0000:00:1c.0:   PREFETCH window: 0x00000090000000-0x00000090ffffff
Dec 31 09:58:49 system76-netbook kernel: [    1.238711] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
Dec 31 09:58:49 system76-netbook kernel: [    1.238718] pci 0000:00:1c.1:   IO window: 0x1000-0x2fff
Dec 31 09:58:49 system76-netbook kernel: [    1.238727] pci 0000:00:1c.1:   MEM window: 0x92100000-0x930fffff
Dec 31 09:58:49 system76-netbook kernel: [    1.238735] pci 0000:00:1c.1:   PREFETCH window: 0x00000091000000-0x000000920fffff
Dec 31 09:58:49 system76-netbook kernel: [    1.238746] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Dec 31 09:58:49 system76-netbook kernel: [    1.238750] pci 0000:00:1e.0:   IO window: disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.238759] pci 0000:00:1e.0:   MEM window: disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.238766] pci 0000:00:1e.0:   PREFETCH window: disabled
Dec 31 09:58:49 system76-netbook kernel: [    1.238795] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 09:58:49 system76-netbook kernel: [    1.238804] pci 0000:00:1c.0: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    1.238819] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 31 09:58:49 system76-netbook kernel: [    1.238828] pci 0000:00:1c.1: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    1.238840] pci 0000:00:1e.0: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    1.238847] bus: 00 index 0 io port: [0x00-0xffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238852] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238857] bus: 01 index 0 io port: [0x3000-0x3fff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238862] bus: 01 index 1 mmio: [0x93100000-0x941fffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238867] bus: 01 index 2 mmio: [0x90000000-0x90ffffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238871] bus: 01 index 3 mmio: [0x0-0x0]
Dec 31 09:58:49 system76-netbook kernel: [    1.238876] bus: 02 index 0 io port: [0x1000-0x2fff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238881] bus: 02 index 1 mmio: [0x92100000-0x930fffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238886] bus: 02 index 2 mmio: [0x91000000-0x920fffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238890] bus: 02 index 3 mmio: [0x0-0x0]
Dec 31 09:58:49 system76-netbook kernel: [    1.238894] bus: 03 index 0 mmio: [0x0-0x0]
Dec 31 09:58:49 system76-netbook kernel: [    1.238898] bus: 03 index 1 mmio: [0x0-0x0]
Dec 31 09:58:49 system76-netbook kernel: [    1.238902] bus: 03 index 2 mmio: [0x0-0x0]
Dec 31 09:58:49 system76-netbook kernel: [    1.238906] bus: 03 index 3 io port: [0x00-0xffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238911] bus: 03 index 4 mmio: [0x000000-0xffffffff]
Dec 31 09:58:49 system76-netbook kernel: [    1.238933] NET: Registered protocol family 2
Dec 31 09:58:49 system76-netbook kernel: [    1.252127] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 31 09:58:49 system76-netbook kernel: [    1.252653] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 31 09:58:49 system76-netbook kernel: [    1.253517] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 31 09:58:49 system76-netbook kernel: [    1.253956] TCP: Hash tables configured (established 131072 bind 65536)
Dec 31 09:58:49 system76-netbook kernel: [    1.253963] TCP reno registered
Dec 31 09:58:49 system76-netbook kernel: [    1.260191] NET: Registered protocol family 1
Dec 31 09:58:49 system76-netbook kernel: [    1.260419] checking if image is initramfs... it is
Dec 31 09:58:49 system76-netbook kernel: [    2.238699] Freeing initrd memory: 7373k freed
Dec 31 09:58:49 system76-netbook kernel: [    2.238769] Simple Boot Flag at 0x44 set to 0x1
Dec 31 09:58:49 system76-netbook kernel: [    2.239112] cpufreq: No nForce2 chipset.
Dec 31 09:58:49 system76-netbook kernel: [    2.239370] audit: initializing netlink socket (disabled)
Dec 31 09:58:49 system76-netbook kernel: [    2.239409] type=2000 audit(1262271513.236:1): initialized
Dec 31 09:58:49 system76-netbook kernel: [    2.253846] highmem bounce pool size: 64 pages
Dec 31 09:58:49 system76-netbook kernel: [    2.253858] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec 31 09:58:49 system76-netbook kernel: [    2.256619] VFS: Disk quotas dquot_6.5.1
Dec 31 09:58:49 system76-netbook kernel: [    2.256743] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 31 09:58:49 system76-netbook kernel: [    2.258068] fuse init (API version 7.10)
Dec 31 09:58:49 system76-netbook kernel: [    2.258256] msgmni has been set to 1698
Dec 31 09:58:49 system76-netbook kernel: [    2.258610] alg: No test for stdrng (krng)
Dec 31 09:58:49 system76-netbook kernel: [    2.258642] io scheduler noop registered
Dec 31 09:58:49 system76-netbook kernel: [    2.258647] io scheduler anticipatory registered
Dec 31 09:58:49 system76-netbook kernel: [    2.258651] io scheduler deadline registered
Dec 31 09:58:49 system76-netbook kernel: [    2.258690] io scheduler cfq registered (default)
Dec 31 09:58:49 system76-netbook kernel: [    2.258713] pci 0000:00:02.0: Boot video device
Dec 31 09:58:49 system76-netbook kernel: [    2.259312] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Dec 31 09:58:49 system76-netbook kernel: [    2.259327] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14dc8), AE_ALREADY_EXISTS
Dec 31 09:58:49 system76-netbook kernel: [    2.259343] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Dec 31 09:58:49 system76-netbook kernel: [    2.261071] ACPI Error (dsfield-0139): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
Dec 31 09:58:49 system76-netbook kernel: [    2.261084] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f6c14dc8), AE_ALREADY_EXISTS
Dec 31 09:58:49 system76-netbook kernel: [    2.262657] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    2.262717] pcieport-driver 0000:00:1c.0: found MSI capability
Dec 31 09:58:49 system76-netbook kernel: [    2.262763] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
Dec 31 09:58:49 system76-netbook kernel: [    2.262783] pci_express 0000:00:1c.0:pcie00: allocate port service
Dec 31 09:58:49 system76-netbook kernel: [    2.262822] pci_express 0000:00:1c.0:pcie02: allocate port service
Dec 31 09:58:49 system76-netbook kernel: [    2.262850] pci_express 0000:00:1c.0:pcie03: allocate port service
Dec 31 09:58:49 system76-netbook kernel: [    2.262947] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    2.263002] pcieport-driver 0000:00:1c.1: found MSI capability
Dec 31 09:58:49 system76-netbook kernel: [    2.263043] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
Dec 31 09:58:49 system76-netbook kernel: [    2.263063] pci_express 0000:00:1c.1:pcie00: allocate port service
Dec 31 09:58:49 system76-netbook kernel: [    2.263091] pci_express 0000:00:1c.1:pcie02: allocate port service
Dec 31 09:58:49 system76-netbook kernel: [    2.263118] pci_express 0000:00:1c.1:pcie03: allocate port service
[B]Dec 31 09:58:49 system76-netbook kernel: [    2.263243] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 31 09:58:49 system76-netbook kernel: [    2.263256] pciehp 0000:00:1c.0:pcie02: Bypassing BIOS check for pciehp use on 0000:00:1c.0
Dec 31 09:58:49 system76-netbook kernel: [    2.263351] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
Dec 31 09:58:49 system76-netbook kernel: [    2.364025] pciehp 0000:00:1c.0:pcie02: Device 0000:01:00.0 already exists at 0000:01:00, cannot hot-add
Dec 31 09:58:49 system76-netbook kernel: [    2.364092] pciehp 0000:00:1c.0:pcie02: Cannot add device at 0000:01:00
Dec 31 09:58:49 system76-netbook kernel: [    3.368040] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
Dec 31 09:58:49 system76-netbook kernel: [    3.368058] pciehp 0000:00:1c.1:pcie02: Bypassing BIOS check for pciehp use on 0000:00:1c.1
Dec 31 09:58:49 system76-netbook kernel: [    3.368082] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
Dec 31 09:58:49 system76-netbook kernel: [    3.472024] pciehp 0000:00:1c.1:pcie02: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add
Dec 31 09:58:49 system76-netbook kernel: [    3.472085] pciehp 0000:00:1c.1:pcie02: Cannot add device at 0000:02:00
Dec 31 09:58:49 system76-netbook kernel: [    4.476036] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
Dec 31 09:58:49 system76-netbook kernel: [    4.476060] pciehp: PCI Express Hot Plug Controller Driver version: 0.4[/B]
Dec 31 09:58:49 system76-netbook kernel: [    4.477606] ACPI: AC Adapter [ACAD] (on-line)
Dec 31 09:58:49 system76-netbook kernel: [    4.501683] ACPI: Battery Slot [BAT1] (battery present)
Dec 31 09:58:49 system76-netbook kernel: [    4.501838] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Dec 31 09:58:49 system76-netbook kernel: [    4.501844] ACPI: Power Button (FF) [PWRF]
Dec 31 09:58:49 system76-netbook kernel: [    4.501933] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Dec 31 09:58:49 system76-netbook kernel: [    4.501939] ACPI: Power Button (CM) [PWRB]
Dec 31 09:58:49 system76-netbook kernel: [    4.502026] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
Dec 31 09:58:49 system76-netbook kernel: [    4.503178] ACPI: Lid Switch [LID0]
Dec 31 09:58:49 system76-netbook kernel: [    4.503271] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
Dec 31 09:58:49 system76-netbook kernel: [    4.503277] ACPI: Sleep Button (CM) [SLPB]
Dec 31 09:58:49 system76-netbook kernel: [    4.504380] ACPI: SSDT 7F380C90, 0239 (r2  PmRef  Cpu0Ist     3000 INTL 20060317)
Dec 31 09:58:49 system76-netbook kernel: [    4.505082] ACPI: SSDT 7F37FE10, 01C7 (r2  PmRef  Cpu0Cst     3001 INTL 20060317)
Dec 31 09:58:49 system76-netbook kernel: [    4.505902] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 31 09:58:49 system76-netbook kernel: [    4.505955] processor ACPI_CPU:00: registered as cooling_device0
Dec 31 09:58:49 system76-netbook kernel: [    4.505964] ACPI: Processor [CPU0] (supports 8 throttling states)
Dec 31 09:58:49 system76-netbook kernel: [    4.506662] ACPI: SSDT 7F380F10, 00D0 (r2  PmRef  Cpu1Ist     3000 INTL 20060317)
Dec 31 09:58:49 system76-netbook kernel: [    4.507316] ACPI: SSDT 7F37EF10, 0083 (r2  PmRef  Cpu1Cst     3000 INTL 20060317)
Dec 31 09:58:49 system76-netbook kernel: [    4.508189] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 31 09:58:49 system76-netbook kernel: [    4.508232] processor ACPI_CPU:01: registered as cooling_device1
Dec 31 09:58:49 system76-netbook kernel: [    4.508241] ACPI: Processor [CPU1] (supports 8 throttling states)
Dec 31 09:58:49 system76-netbook kernel: [    4.515185] thermal LNXTHERM:01: registered as thermal_zone0
Dec 31 09:58:49 system76-netbook kernel: [    4.517399] ACPI: Thermal Zone [THRM] (25 C)
Dec 31 09:58:49 system76-netbook kernel: [    4.517511] isapnp: Scanning for PnP cards...
Dec 31 09:58:49 system76-netbook kernel: [    4.871295] isapnp: No Plug & Play device found
Dec 31 09:58:49 system76-netbook kernel: [    4.885533] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Dec 31 09:58:49 system76-netbook kernel: [    4.887429] brd: module loaded
Dec 31 09:58:49 system76-netbook kernel: [    4.888096] loop: module loaded
Dec 31 09:58:49 system76-netbook kernel: [    4.888258] Fixed MDIO Bus: probed
Dec 31 09:58:49 system76-netbook kernel: [    4.888270] PPP generic driver version 2.4.2
Dec 31 09:58:49 system76-netbook kernel: [    4.888412] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Dec 31 09:58:49 system76-netbook kernel: [    4.888476] Driver 'sd' needs updating - please use bus_type methods
Dec 31 09:58:49 system76-netbook kernel: [    4.888502] Driver 'sr' needs updating - please use bus_type methods
Dec 31 09:58:49 system76-netbook kernel: [    4.888649] ata_piix 0000:00:1f.2: version 2.12
Dec 31 09:58:49 system76-netbook kernel: [    4.888675] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 31 09:58:49 system76-netbook kernel: [    4.888682] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Dec 31 09:58:49 system76-netbook kernel: [    4.888747] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    4.888925] scsi0 : ata_piix
Dec 31 09:58:49 system76-netbook kernel: [    4.889141] scsi1 : ata_piix
Dec 31 09:58:49 system76-netbook kernel: [    4.891276] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x40a0 irq 14
Dec 31 09:58:49 system76-netbook kernel: [    4.891283] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x40a8 irq 15
Dec 31 09:58:49 system76-netbook kernel: [    5.091713] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
Dec 31 09:58:49 system76-netbook kernel: [    5.091720] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 31 09:58:49 system76-netbook kernel: [    5.105063] ata1.00: configured for UDMA/133
Dec 31 09:58:49 system76-netbook kernel: [    5.260294] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
Dec 31 09:58:49 system76-netbook kernel: [    5.260516] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Dec 31 09:58:49 system76-netbook kernel: [    5.260558] sd 0:0:0:0: [sda] Write Protect is off
Dec 31 09:58:49 system76-netbook kernel: [    5.260564] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 31 09:58:49 system76-netbook kernel: [    5.260634] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 31 09:58:49 system76-netbook kernel: [    5.260781] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Dec 31 09:58:49 system76-netbook kernel: [    5.260821] sd 0:0:0:0: [sda] Write Protect is off
Dec 31 09:58:49 system76-netbook kernel: [    5.260827] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 31 09:58:49 system76-netbook kernel: [    5.260896] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 31 09:58:49 system76-netbook kernel: [    5.260906]  sda: sda1 sda2 sda3
Dec 31 09:58:49 system76-netbook kernel: [    5.267037] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 31 09:58:49 system76-netbook kernel: [    5.267140] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 31 09:58:49 system76-netbook kernel: [    5.268626] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 31 09:58:49 system76-netbook kernel: [    5.268669] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 09:58:49 system76-netbook kernel: [    5.268703] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    5.268710] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 31 09:58:49 system76-netbook kernel: [    5.268819] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Dec 31 09:58:49 system76-netbook kernel: [    5.272752] ehci_hcd 0000:00:1d.7: debug port 1
Dec 31 09:58:49 system76-netbook kernel: [    5.272762] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Dec 31 09:58:49 system76-netbook kernel: [    5.272794] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x94344400
Dec 31 09:58:49 system76-netbook kernel: [    5.288020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec 31 09:58:49 system76-netbook kernel: [    5.288171] usb usb1: configuration #1 chosen from 1 choice
Dec 31 09:58:49 system76-netbook kernel: [    5.288228] hub 1-0:1.0: USB hub found
Dec 31 09:58:49 system76-netbook kernel: [    5.288244] hub 1-0:1.0: 8 ports detected
Dec 31 09:58:49 system76-netbook kernel: [    5.288463] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 31 09:58:49 system76-netbook kernel: [    5.288502] uhci_hcd: USB Universal Host Controller Interface driver
Dec 31 09:58:49 system76-netbook kernel: [    5.288570] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 09:58:49 system76-netbook kernel: [    5.288583] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    5.288589] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 31 09:58:49 system76-netbook kernel: [    5.288685] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec 31 09:58:49 system76-netbook kernel: [    5.288722] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00004080
Dec 31 09:58:49 system76-netbook kernel: [    5.288879] usb usb2: configuration #1 chosen from 1 choice
Dec 31 09:58:49 system76-netbook kernel: [    5.288933] hub 2-0:1.0: USB hub found
Dec 31 09:58:49 system76-netbook kernel: [    5.288947] hub 2-0:1.0: 2 ports detected
Dec 31 09:58:49 system76-netbook kernel: [    5.289112] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 31 09:58:49 system76-netbook kernel: [    5.289123] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    5.289129] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 31 09:58:49 system76-netbook kernel: [    5.289214] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Dec 31 09:58:49 system76-netbook kernel: [    5.289263] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00004060
Dec 31 09:58:49 system76-netbook kernel: [    5.289414] usb usb3: configuration #1 chosen from 1 choice
Dec 31 09:58:49 system76-netbook kernel: [    5.289467] hub 3-0:1.0: USB hub found
Dec 31 09:58:49 system76-netbook kernel: [    5.289481] hub 3-0:1.0: 2 ports detected
Dec 31 09:58:49 system76-netbook kernel: [    5.289661] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 31 09:58:49 system76-netbook kernel: [    5.289674] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    5.289680] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 31 09:58:49 system76-netbook kernel: [    5.289772] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Dec 31 09:58:49 system76-netbook kernel: [    5.289818] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004040
Dec 31 09:58:49 system76-netbook kernel: [    5.289977] usb usb4: configuration #1 chosen from 1 choice
Dec 31 09:58:49 system76-netbook kernel: [    5.290032] hub 4-0:1.0: USB hub found
Dec 31 09:58:49 system76-netbook kernel: [    5.290046] hub 4-0:1.0: 2 ports detected
Dec 31 09:58:49 system76-netbook kernel: [    5.290213] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec 31 09:58:49 system76-netbook kernel: [    5.290224] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    5.290230] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Dec 31 09:58:49 system76-netbook kernel: [    5.290315] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Dec 31 09:58:49 system76-netbook kernel: [    5.290363] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00004020
Dec 31 09:58:49 system76-netbook kernel: [    5.290514] usb usb5: configuration #1 chosen from 1 choice
Dec 31 09:58:49 system76-netbook kernel: [    5.290567] hub 5-0:1.0: USB hub found
Dec 31 09:58:49 system76-netbook kernel: [    5.290581] hub 5-0:1.0: 2 ports detected
Dec 31 09:58:49 system76-netbook kernel: [    5.290847] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
Dec 31 09:58:49 system76-netbook kernel: [    5.291194] i8042.c: Warning: Keylock active.
Dec 31 09:58:49 system76-netbook kernel: [    5.299946] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 31 09:58:49 system76-netbook kernel: [    5.305122] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 31 09:58:49 system76-netbook kernel: [    5.305136] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 31 09:58:49 system76-netbook kernel: [    5.305143] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 31 09:58:49 system76-netbook kernel: [    5.305150] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 31 09:58:49 system76-netbook kernel: [    5.305157] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 31 09:58:49 system76-netbook kernel: [    5.308093] mice: PS/2 mouse device common for all mice
Dec 31 09:58:49 system76-netbook kernel: [    5.328130] rtc_cmos 00:03: RTC can wake from S4
Dec 31 09:58:49 system76-netbook kernel: [    5.328205] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec 31 09:58:49 system76-netbook kernel: [    5.328249] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Dec 31 09:58:49 system76-netbook kernel: [    5.328401] device-mapper: uevent: version 1.0.3
Dec 31 09:58:49 system76-netbook kernel: [    5.328618] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Dec 31 09:58:49 system76-netbook kernel: [    5.328790] device-mapper: multipath: version 1.0.5 loaded
Dec 31 09:58:49 system76-netbook kernel: [    5.328798] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 31 09:58:49 system76-netbook kernel: [    5.328986] EISA: Probing bus 0 at eisa.0
Dec 31 09:58:49 system76-netbook kernel: [    5.328998] Cannot allocate resource for EISA slot 1
Dec 31 09:58:49 system76-netbook kernel: [    5.329005] Cannot allocate resource for EISA slot 2
Dec 31 09:58:49 system76-netbook kernel: [    5.329012] Cannot allocate resource for EISA slot 3
Dec 31 09:58:49 system76-netbook kernel: [    5.329018] Cannot allocate resource for EISA slot 4
Dec 31 09:58:49 system76-netbook kernel: [    5.329044] EISA: Detected 0 cards.
Dec 31 09:58:49 system76-netbook kernel: [    5.329294] cpuidle: using governor ladder
Dec 31 09:58:49 system76-netbook kernel: [    5.329522] cpuidle: using governor menu
Dec 31 09:58:49 system76-netbook kernel: [    5.330578] TCP cubic registered
Dec 31 09:58:49 system76-netbook kernel: [    5.330803] NET: Registered protocol family 10
Dec 31 09:58:49 system76-netbook kernel: [    5.331696] lo: Disabled Privacy Extensions
Dec 31 09:58:49 system76-netbook kernel: [    5.332369] NET: Registered protocol family 17
Dec 31 09:58:49 system76-netbook kernel: [    5.332413] Bluetooth: L2CAP ver 2.11
Dec 31 09:58:49 system76-netbook kernel: [    5.332417] Bluetooth: L2CAP socket layer initialized
Dec 31 09:58:49 system76-netbook kernel: [    5.332422] Bluetooth: SCO (Voice Link) ver 0.6
Dec 31 09:58:49 system76-netbook kernel: [    5.332425] Bluetooth: SCO socket layer initialized
Dec 31 09:58:49 system76-netbook kernel: [    5.332512] Bluetooth: RFCOMM socket layer initialized
Dec 31 09:58:49 system76-netbook kernel: [    5.332528] Marking TSC unstable due to TSC halts in idle
Dec 31 09:58:49 system76-netbook kernel: [    5.332532] Bluetooth: RFCOMM TTY layer initialized
Dec 31 09:58:49 system76-netbook kernel: [    5.332536] Bluetooth: RFCOMM ver 1.10
Dec 31 09:58:49 system76-netbook kernel: [    5.333648] Using IPI No-Shortcut mode
Dec 31 09:58:49 system76-netbook kernel: [    5.333821] registered taskstats version 1
Dec 31 09:58:49 system76-netbook kernel: [    5.334053]   Magic number: 5:295:992
Dec 31 09:58:49 system76-netbook kernel: [    5.334198] rtc_cmos 00:03: setting system clock to 2009-12-31 14:58:37 UTC (1262271517)
Dec 31 09:58:49 system76-netbook kernel: [    5.334206] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 31 09:58:49 system76-netbook kernel: [    5.334211] EDD information not available.
Dec 31 09:58:49 system76-netbook kernel: [    5.334633] Freeing unused kernel memory: 532k freed
Dec 31 09:58:49 system76-netbook kernel: [    5.334951] Write protecting the kernel text: 4120k
Dec 31 09:58:49 system76-netbook kernel: [    5.335066] Write protecting the kernel read-only data: 1524k
Dec 31 09:58:49 system76-netbook kernel: [    5.351450] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Dec 31 09:58:49 system76-netbook kernel: [    5.601074] usb 1-5: new high speed USB device using ehci_hcd and address 2
Dec 31 09:58:49 system76-netbook kernel: [    5.814439] usb 1-5: configuration #1 chosen from 1 choice
Dec 31 09:58:49 system76-netbook kernel: [    5.919260] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 31 09:58:49 system76-netbook kernel: [    5.919300] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 31 09:58:49 system76-netbook kernel: [    5.919338] r8169 0000:02:00.0: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [    5.919518] r8169 0000:02:00.0: irq 2301 for MSI/MSI-X
Dec 31 09:58:49 system76-netbook kernel: [    5.921323] eth0: RTL8102e at 0xf7c5e000, 00:26:9e:01:43:66, XID 24a00000 IRQ 2301
Dec 31 09:58:49 system76-netbook kernel: [    5.930186] usb 1-7: new high speed USB device using ehci_hcd and address 3
Dec 31 09:58:49 system76-netbook kernel: [    6.072558] usb 1-7: configuration #1 chosen from 1 choice
Dec 31 09:58:49 system76-netbook kernel: [    6.506130] PM: Starting manual resume from disk
Dec 31 09:58:49 system76-netbook kernel: [    6.506138] PM: Resume from partition 8:2
Dec 31 09:58:49 system76-netbook kernel: [    6.506142] PM: Checking hibernation image.
Dec 31 09:58:49 system76-netbook kernel: [    6.506506] PM: Resume from disk failed.
Dec 31 09:58:49 system76-netbook kernel: [    6.537045] kjournald starting.  Commit interval 5 seconds
Dec 31 09:58:49 system76-netbook kernel: [    6.537109] EXT3-fs: mounted filesystem with ordered data mode.
Dec 31 09:58:49 system76-netbook kernel: [   11.340547] udev: starting version 141
Dec 31 09:58:49 system76-netbook kernel: [   11.535194] Linux agpgart interface v0.103
Dec 31 09:58:49 system76-netbook kernel: [   11.584496] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29/input/input6
Dec 31 09:58:49 system76-netbook kernel: [   11.595203] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Dec 31 09:58:49 system76-netbook kernel: [   11.595671] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Dec 31 09:58:49 system76-netbook kernel: [   11.598689] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
Dec 31 09:58:49 system76-netbook kernel: [   11.616486] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
Dec 31 09:58:49 system76-netbook kernel: [   11.892184] sdhci: Secure Digital Host Controller Interface driver
Dec 31 09:58:49 system76-netbook kernel: [   11.892193] sdhci: Copyright(c) Pierre Ossman
Dec 31 09:58:49 system76-netbook kernel: [   11.904534] sdhci-pci 0000:01:00.0: SDHCI controller found [197b:2382] (rev 0)
Dec 31 09:58:49 system76-netbook kernel: [   11.904573] sdhci-pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 09:58:49 system76-netbook kernel: [   11.904721] sdhci-pci 0000:01:00.0: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [   11.904844] mmc0: SDHCI controller on PCI [0000:01:00.0] using ADMA
Dec 31 09:58:49 system76-netbook kernel: [   11.904871] sdhci-pci 0000:01:00.2: SDHCI controller found [197b:2381] (rev 0)
Dec 31 09:58:49 system76-netbook kernel: [   11.904901] sdhci-pci 0000:01:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 09:58:49 system76-netbook kernel: [   11.904917] sdhci-pci 0000:01:00.2: Refusing to bind to secondary interface.
Dec 31 09:58:49 system76-netbook kernel: [   11.904931] sdhci-pci 0000:01:00.2: PCI INT A disabled
Dec 31 09:58:49 system76-netbook kernel: [   11.918520] intel_rng: FWH not detected
Dec 31 09:58:49 system76-netbook kernel: [   11.932772] ieee80211_crypt: registered algorithm 'NULL'
Dec 31 09:58:49 system76-netbook kernel: [   11.936281] ieee80211_crypt: registered algorithm 'CCMP'
Dec 31 09:58:49 system76-netbook kernel: [   11.939819] ieee80211_crypt: registered algorithm 'WEP'
Dec 31 09:58:49 system76-netbook kernel: [   11.944611] ieee80211_crypt: registered algorithm 'TKIP'
Dec 31 09:58:49 system76-netbook kernel: [   12.013367] input: PC Speaker as /devices/platform/pcspkr/input/input7
Dec 31 09:58:49 system76-netbook kernel: [   12.250870] mmc0: error -84 whilst initialising SD card
Dec 31 09:58:49 system76-netbook kernel: [   12.278052] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Dec 31 09:58:49 system76-netbook kernel: [   12.334708] 
Dec 31 09:58:49 system76-netbook kernel: [   12.334711] Linux kernel driver for RTL8187/RTL8187B based WLAN cards
Dec 31 09:58:49 system76-netbook kernel: [   12.334718] Copyright (c) 2004-2008, Realsil Wlan
Dec 31 09:58:49 system76-netbook kernel: [   12.334723] rtl8187: Initializing module
Dec 31 09:58:49 system76-netbook kernel: [   12.334728] rtl8187: Wireless extensions version 22
Dec 31 09:58:49 system76-netbook kernel: [   12.334733] rtl8187: Initializing proc filesystem
Dec 31 09:58:49 system76-netbook kernel: [   12.383613] rtl8187: idProduct:0x8189, bcdDevice:0x200
Dec 31 09:58:49 system76-netbook kernel: [   12.385418] Linux video capture interface: v2.00
Dec 31 09:58:49 system76-netbook kernel: [   12.410196] iTCO_vendor_support: vendor-support=0
Dec 31 09:58:49 system76-netbook kernel: [   12.414362] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Dec 31 09:58:49 system76-netbook kernel: [   12.414827] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x0460)
Dec 31 09:58:49 system76-netbook kernel: [   12.415076] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 31 09:58:49 system76-netbook kernel: [   12.427983] rtl8187: Channel plan is 0 
Dec 31 09:58:49 system76-netbook kernel: [   12.428473] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
Dec 31 09:58:49 system76-netbook kernel: [   12.462402] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:a127)
Dec 31 09:58:49 system76-netbook kernel: [   12.464536] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
Dec 31 09:58:49 system76-netbook kernel: [   12.465383] usbcore: registered new interface driver uvcvideo
Dec 31 09:58:49 system76-netbook kernel: [   12.465537] USB Video Class driver (v0.1.0)
Dec 31 09:58:49 system76-netbook kernel: [   12.652516] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 09:58:49 system76-netbook kernel: [   12.652650] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 31 09:58:49 system76-netbook kernel: [   12.721617] rtl8187: Card MAC address is 00:17:c4:91:ba:4f
Dec 31 09:58:49 system76-netbook kernel: [   13.100270] rtl8187: EEPROM Customer ID: 00
Dec 31 09:58:49 system76-netbook kernel: [   13.101959] rtl8187: Driver probe completed
Dec 31 09:58:49 system76-netbook kernel: [   13.102014] usbcore: registered new interface driver rtl8187
Dec 31 09:58:49 system76-netbook kernel: [   13.218608] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
Dec 31 09:58:49 system76-netbook kernel: [   13.272798] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
Dec 31 09:58:49 system76-netbook kernel: [   13.387688] lp: driver loaded but no devices found
Dec 31 09:58:49 system76-netbook kernel: [   13.548139] Adding 1954092k swap on /dev/sda2.  Priority:-1 extents:1 across:1954092k
Dec 31 09:58:49 system76-netbook kernel: [   14.171873] EXT3 FS on sda1, internal journal
Dec 31 09:58:49 system76-netbook kernel: [   15.150406] kjournald starting.  Commit interval 5 seconds
Dec 31 09:58:49 system76-netbook kernel: [   15.150894] EXT3 FS on sda3, internal journal
Dec 31 09:58:49 system76-netbook kernel: [   15.150911] EXT3-fs: mounted filesystem with ordered data mode.
Dec 31 09:58:49 system76-netbook kernel: [   15.637548] type=1505 audit(1262271527.801:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1984
Dec 31 09:58:49 system76-netbook kernel: [   15.637818] type=1505 audit(1262271527.801:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1984
Dec 31 09:58:49 system76-netbook kernel: [   15.637935] type=1505 audit(1262271527.801:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1984
Dec 31 09:58:49 system76-netbook kernel: [   15.638039] type=1505 audit(1262271527.801:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1984
Dec 31 09:58:49 system76-netbook kernel: [   15.956270] type=1505 audit(1262271528.121:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1989
Dec 31 09:58:49 system76-netbook kernel: [   15.956675] type=1505 audit(1262271528.121:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1989
Dec 31 09:58:49 system76-netbook kernel: [   16.021764] type=1505 audit(1262271528.185:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1993
Dec 31 09:58:51 system76-netbook acpid: client connected from 2475[111:120] 
Dec 31 09:58:51 system76-netbook bluetoothd[2493]: Bluetooth daemon
Dec 31 09:58:51 system76-netbook bluetoothd[2493]: Starting SDP server
Dec 31 09:58:51 system76-netbook bluetoothd[2493]: Registered interface org.bluez.Service on path /org/bluez/2493/any
Dec 31 09:58:51 system76-netbook bluetoothd[2493]: Starting experimental netlink support
Dec 31 09:58:51 system76-netbook bluetoothd[2493]: Failed to find Bluetooth netlink family
Dec 31 09:58:51 system76-netbook kernel: [   19.188057] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 31 09:58:51 system76-netbook kernel: [   19.188066] Bluetooth: BNEP filters: protocol multicast
Dec 31 09:58:51 system76-netbook bluetoothd[2493]: bridge pan0 created
Dec 31 09:58:51 system76-netbook kernel: [   19.217408] Bridge firewalling registered
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  starting... 
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169') 
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_26_9e_01_43_66 
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rtl8187') 
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_17_c4_91_ba_4f 
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  Trying to start the supplicant... 
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  Trying to start the system settings daemon... 
Dec 31 09:58:52 system76-netbook nm-system-settings:    SCPlugin-Ifupdown: init!
Dec 31 09:58:52 system76-netbook nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Dec 31 09:58:52 system76-netbook nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Dec 31 09:58:52 system76-netbook nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_26_9e_01_43_66, iface: eth0): not well known
Dec 31 09:58:52 system76-netbook nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_17_c4_91_ba_4f, iface: wlan0): not well known
Dec 31 09:58:52 system76-netbook nm-system-settings:    SCPlugin-Ifupdown: end _init.
Dec 31 09:58:52 system76-netbook nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 31 09:58:52 system76-netbook nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 31 09:58:52 system76-netbook nm-system-settings:    SCPlugin-Ifupdown: (136963896) ... get_connections.
Dec 31 09:58:52 system76-netbook nm-system-settings:    SCPlugin-Ifupdown: (136963896) ... get_connections (managed=false): return empty list.
Dec 31 09:58:52 system76-netbook NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: Successfully dropped root privileges.
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: avahi-daemon 0.6.23 starting up.
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: Successfully called chroot().
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: Successfully dropped remaining capabilities.
Dec 31 09:58:52 system76-netbook nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Dec 31 09:58:52 system76-netbook acpid: client connected from 2538[0:0] 
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: No service file found in /etc/avahi/services.
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: Network interface enumeration completed.
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 31 09:58:52 system76-netbook avahi-daemon[2583]: Server startup complete. Host name is system76-netbook.local. Local service cookie is 4218557185.
Dec 31 09:58:52 system76-netbook kernel: [   20.456882] ppdev: user-space parallel port driver
Dec 31 09:58:53 system76-netbook anacron[2698]: Anacron 2.3 started on 2009-12-31
Dec 31 09:58:53 system76-netbook anacron[2698]: Will run job `cron.daily' in 5 min.
Dec 31 09:58:53 system76-netbook anacron[2698]: Will run job `cron.weekly' in 10 min.
Dec 31 09:58:53 system76-netbook anacron[2698]: Jobs will be executed sequentially
Dec 31 09:58:53 system76-netbook /usr/sbin/cron[2741]: (CRON) INFO (pidfile fd = 3)
Dec 31 09:58:53 system76-netbook /usr/sbin/cron[2742]: (CRON) STARTUP (fork ok)
Dec 31 09:58:53 system76-netbook /usr/sbin/cron[2742]: (CRON) INFO (Running @reboot jobs)
Dec 31 09:58:54 system76-netbook kernel: [   22.033647] [drm] Initialized drm 1.1.0 20060810
Dec 31 09:58:54 system76-netbook kernel: [   22.046620] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 09:58:54 system76-netbook kernel: [   22.046630] pci 0000:00:02.0: setting latency timer to 64
Dec 31 09:58:54 system76-netbook kernel: [   22.046939] [drm] Initialized i915 1.6.0 20080730 on minor 0
Dec 31 09:58:54 system76-netbook kernel: [   22.051477] [drm:i915_setparam] *ERROR* unknown parameter 4
Dec 31 09:58:54 system76-netbook kernel: [   22.051532] [drm:i915_getparam] *ERROR* Unknown parameter 6
Dec 31 09:58:55 system76-netbook kernel: [   23.191824] [drm:i915_getparam] *ERROR* Unknown parameter 6
Dec 31 09:58:56 system76-netbook console-kit-daemon[2344]: WARNING: Couldn't read /proc/2343/environ: Failed to open file '/proc/2343/environ': No such file or directory 
Dec 31 09:58:56 system76-netbook NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Dec 31 09:58:56 system76-netbook NetworkManager: <info>  (eth0): bringing up device. 
Dec 31 09:58:57 system76-netbook NetworkManager: <info>  (eth0): preparing device. 
Dec 31 09:58:57 system76-netbook NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Dec 31 09:58:57 system76-netbook NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Dec 31 09:58:57 system76-netbook NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Dec 31 09:58:57 system76-netbook NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Dec 31 09:58:57 system76-netbook NetworkManager: <info>  (wlan0): bringing up device. 
Dec 31 09:58:57 system76-netbook kernel: [   24.836204] r8169: eth0: link down
Dec 31 09:58:57 system76-netbook kernel: [   24.836747] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 09:58:57 system76-netbook kernel: [   24.839223] rtl8187: rtl8187_open process 
Dec 31 09:58:57 system76-netbook nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_26_9e_01_43_66
Dec 31 09:58:57 system76-netbook kernel: [   24.843015] rtl8187: Now Radio ON!
Dec 31 09:58:57 system76-netbook kernel: [   24.853516] rtl8187: Card successfully reset
Dec 31 09:59:01 system76-netbook kernel: [   28.867159] rtl8187: DIG is enabled, set default initial gain index to 4
Dec 31 09:59:01 system76-netbook kernel: [   28.869204] rtl8187: RTL8187 + 8225 Initial Gain State 4: -74 dBm 
Dec 31 09:59:01 system76-netbook kernel: [   28.875270] rtl8187: WIRELESS_MODE_G
Dec 31 09:59:01 system76-netbook kernel: [   28.920829] rtl8187: rtl8187_open process complete
Dec 31 09:59:01 system76-netbook NetworkManager: <info>  (wlan0): preparing device. 
Dec 31 09:59:01 system76-netbook kernel: [   28.921298] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 31 09:59:01 system76-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Dec 31 09:59:01 system76-netbook kernel: [   28.986003] rtl8187: Setting SW wep key
Dec 31 09:59:01 system76-netbook NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Dec 31 09:59:01 system76-netbook NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Dec 31 09:59:05 system76-netbook kernel: [   32.920064] rtl8187: IPSEnter(): Turn off RF.
Dec 31 09:59:05 system76-netbook kernel: [   32.921105] rtl8187: Now Radio OFF!
Dec 31 09:59:07 system76-netbook kernel: [   35.526489] [drm:i915_getparam] *ERROR* Unknown parameter 6
Dec 31 09:59:09 system76-netbook kernel: [   36.898662] [drm:i915_getparam] *ERROR* Unknown parameter 6
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Activation (wlan0) starting connection 'Auto CedarBrookPlace' 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto CedarBrookPlace' requires no security.  No secrets needed. 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Config: added 'ssid' value 'CedarBrookPlace' 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  Config: set interface ap_scan to 1 
Dec 31 09:59:10 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Dec 31 09:59:13 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Dec 31 09:59:13 system76-netbook kernel: [   41.625282] rtl8187: ISLeave(): Turn on RF.
Dec 31 09:59:13 system76-netbook kernel: [   41.627671] rtl8187: Now Radio ON!
Dec 31 09:59:15 system76-netbook kernel: [   42.920142] rtl8187: IPSEnter(): Turn off RF.
Dec 31 09:59:15 system76-netbook kernel: [   42.921394] rtl8187: Now Radio OFF!
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Dec 31 09:59:20 system76-netbook kernel: [   47.972215] Linking with CedarBrookPlace, channel:4
Dec 31 09:59:20 system76-netbook kernel: [   47.972311] rtl8187: ISLeave(): Turn on RF.
Dec 31 09:59:20 system76-netbook kernel: [   47.973646] rtl8187: Now Radio ON!
Dec 31 09:59:20 system76-netbook kernel: [   48.018572] Linking with CedarBrookPlace, channel:4
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Dec 31 09:59:20 system76-netbook kernel: [   48.059024] Associated successfully
Dec 31 09:59:20 system76-netbook kernel: [   48.059037] Using G rates
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'CedarBrookPlace'. 
Dec 31 09:59:20 system76-netbook kernel: [   48.078329] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Dec 31 09:59:20 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Dec 31 09:59:20 system76-netbook avahi-daemon[2583]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.40.
Dec 31 09:59:20 system76-netbook avahi-daemon[2583]: New relevant interface wlan0.IPv4 for mDNS.
Dec 31 09:59:20 system76-netbook avahi-daemon[2583]: Registering new address record for 192.168.1.40 on wlan0.IPv4.
Dec 31 09:59:21 system76-netbook NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Dec 31 09:59:21 system76-netbook NetworkManager: <info>  Policy set 'Auto CedarBrookPlace' (wlan0) as default for routing and DNS. 
Dec 31 09:59:21 system76-netbook NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Dec 31 09:59:21 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 31 09:59:22 system76-netbook avahi-daemon[2583]: Registering new address record for fe80::217:c4ff:fe91:ba4f on wlan0.*.
Dec 31 09:59:31 system76-netbook kernel: [   59.072068] wlan0: no IPv6 routers present
Dec 31 09:59:35 system76-netbook ntpdate[3213]: step time server 91.189.94.4 offset 3.750109 sec
Dec 31 09:59:44 system76-netbook kernel: [   68.921452] rtl8187: RTL8187 + 8225 Initial Gain State 3: -78 dBm 
Dec 31 10:00:05 system76-netbook /USR/SBIN/CRON[3237]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 31 10:00:05 system76-netbook /USR/SBIN/CRON[3239]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Dec 31 10:00:24 system76-netbook kernel: [  108.920584] rtl8187: RTL8187 + 8225 Initial Gain State 2: -78 dBm 
Dec 31 10:03:56 system76-netbook anacron[2698]: Job `cron.daily' started

```

I really have no idea how to go about troubleshooting this, so it's up to ya'll now. :) Thanks in advance.

-Ian

---

### Post by thomasaaron on 2009-12-31
First, run your System76 driver (Administration > System76 Driver > Install tab > Install button), and then reboot.

THEN, open a terminal and run...

tail -f /var/log/syslog

THEN, insert your SD card. A few seconds after inserting it, some messages should pop up in the terminal. Please copy and paste them here, and I'll have a look.

Also, have you tried with any other SD cards?

---

### Post by Ian505 on 2010-01-09
Sorry for the delayed reply.

I did as you asked. Here is the results of "tail -f /var/log/syslog" with what appeared following the insertion of the SD card in bold.

```
ian@system76-netbook:~$ tail -f /var/log/syslog
Jan  9 19:22:24 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Jan  9 19:22:24 system76-netbook avahi-daemon[2506]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.47.
Jan  9 19:22:24 system76-netbook avahi-daemon[2506]: New relevant interface wlan0.IPv4 for mDNS.
Jan  9 19:22:24 system76-netbook avahi-daemon[2506]: Registering new address record for 192.168.1.47 on wlan0.IPv4.
Jan  9 19:22:25 system76-netbook NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Jan  9 19:22:25 system76-netbook NetworkManager: <info>  Policy set 'Auto CedarBrookPlace' (wlan0) as default for routing and DNS. 
Jan  9 19:22:25 system76-netbook NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jan  9 19:22:25 system76-netbook NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan  9 19:22:26 system76-netbook ntpdate[3157]: adjust time server 91.189.94.4 offset 0.049431 sec
Jan  9 19:22:29 system76-netbook kernel: [   57.896075] wlan0: no IPv6 routers present
Jan  9 19:22:43 system76-netbook kernel: [   71.896420] rtl8187: RTL8187 + 8225 Initial Gain State 3: -78 dBm 
[B]Jan  9 19:23:09 system76-netbook kernel: [   98.020252] pciehp 0000:00:1c.0:pcie02: Card present on Slot(0)
Jan  9 19:23:09 system76-netbook kernel: [   98.140119] pci 0000:01:00.0: reg 10 32bit mmio: [0x000000-0x0000ff]
Jan  9 19:23:09 system76-netbook kernel: [   98.140188] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
Jan  9 19:23:09 system76-netbook kernel: [   98.140292] pci 0000:01:00.2: reg 10 32bit mmio: [0x000000-0x0000ff]
Jan  9 19:23:09 system76-netbook kernel: [   98.140447] pci 0000:01:00.3: reg 10 32bit mmio: [0x000000-0x0000ff]
Jan  9 19:23:09 system76-netbook kernel: [   98.140601] pci 0000:01:00.4: reg 10 32bit mmio: [0x000000-0x0000ff]
Jan  9 19:23:09 system76-netbook kernel: [   98.140773] pciehp: Could not get hotplug parameters
Jan  9 19:23:09 system76-netbook kernel: [   98.140819] pciehp: Could not get hotplug parameters
Jan  9 19:23:09 system76-netbook kernel: [   98.140863] pciehp: Could not get hotplug parameters
Jan  9 19:23:09 system76-netbook kernel: [   98.140907] pciehp: Could not get hotplug parameters
Jan  9 19:23:09 system76-netbook kernel: [   98.214102] sdhci: Secure Digital Host Controller Interface driver
Jan  9 19:23:09 system76-netbook kernel: [   98.214111] sdhci: Copyright(c) Pierre Ossman
Jan  9 19:23:09 system76-netbook kernel: [   98.221404] sdhci-pci 0000:01:00.0: SDHCI controller found [197b:2382] (rev 0)
Jan  9 19:23:09 system76-netbook kernel: [   98.221439] sdhci-pci 0000:01:00.0: enabling device (0000 -> 0002)
Jan  9 19:23:09 system76-netbook kernel: [   98.221459] sdhci-pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  9 19:23:09 system76-netbook kernel: [   98.221838] sdhci-pci 0000:01:00.0: setting latency timer to 64
Jan  9 19:23:09 system76-netbook kernel: [   98.221986] mmc0: SDHCI controller on PCI [0000:01:00.0] using ADMA
Jan  9 19:23:09 system76-netbook kernel: [   98.222018] sdhci-pci 0000:01:00.2: SDHCI controller found [197b:2381] (rev 0)
Jan  9 19:23:09 system76-netbook kernel: [   98.222049] sdhci-pci 0000:01:00.2: enabling device (0000 -> 0002)
Jan  9 19:23:09 system76-netbook kernel: [   98.222067] sdhci-pci 0000:01:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  9 19:23:09 system76-netbook kernel: [   98.222087] sdhci-pci 0000:01:00.2: Refusing to bind to secondary interface.
Jan  9 19:23:09 system76-netbook kernel: [   98.222099] sdhci-pci 0000:01:00.2: PCI INT A disabled
Jan  9 19:23:09 system76-netbook kernel: [   98.558398] mmc0: error -84 whilst initialising SD card
Jan  9 19:23:13 system76-netbook kernel: [  101.896425] rtl8187: RTL8187 + 8225 Initial Gain State 2: -78 dBm [/B]

```

---

### Post by Ian505 on 2010-01-09
Embarrassingly enough, I just tried another SD card and it mounted without a hitch.

Is the card reader SDHC compatible? The one I was trying was 8GB, while the one I just tried was 1GB.

-Ian

---

### Post by Tart on 2010-01-09
> **Ian505 said:**
> 
Is the card reader SDHC compatible? The one I was trying was 8GB, while the one I just tried was 1GB.


I don't think so. My Starling doesn't like any of the SDHC card, regular SD 1 or 2GB that I have work like a charm. I have to use separate usb cardreader for my SDHC cards

Can this be resolved with driver update? Probably not, right?

---

### Post by Ian505 on 2010-01-10
Well that's a big disappointment. I guess I will have to stick to the smaller cards from now on...

And to my knowledge, if the reader was designed for the SD 1.0 or 1.1 specifications, it will not be compatible with the SDHC cards due to hardware differences.

-Ian

---

### Post by waterdragon687 on 2010-03-13
I just got a Starling this week (very nice, by the by) and I too was having problems with the built-in card reader at first. I don't have the full logs to hand but it was giving a "-84" error when I tried to insert a 4GB SDHC card, yet it would mount and read the exact same card with no problems using a SanDisk MobileMate USB reader, so I knew it wasn't a problem with the card itself. And it seemed impossible that System76 would be installing card-readers that weren't SDHC compatible--even the reader in my old Asus EEE 900 that I bought a couple of years ago would handle SDHC cards without issue. 

So, after some searching both here and on Google, I came across a reference to someone having a similar issue that was solved by using a different version of the kernel, at which point it occurred to me that I hadn't yet used the Update Manager to bring everything on the system up to the latest versions.  (Oops. :oops: ) Well, sure enough, when I brought it up and checked, the kernel was listed among the stuff to be updated, so I ran that through and rebooted--and, lo and behold, the card reader now accepts the 4GB card just as it should. So I thought I would post that as something to try, anyway, if you haven't already done so... it's not the exact same problem that Ian505 is having, but maybe it will help some other new Starling owner...

---

