---
title: "Software raid5 - Very low performance"
date: 2010-03-05
forum: Server Platforms
---

### Post by magogo200 on 2010-03-05
[FONT=Courier New]Hello,

I recently installed a new home backup server with Ubuntu 9.10 x86_64 using the alternate CD. I used the CD's installer to partition my disk and created a software RAID 5 array on 4 disks with no spares. The root file system is located outside the raid array.

At first the array performed nicely but as it started to fill up, the io performance dropped significantly to the point where I get a transfer rate of 1-2MB/s when writing!

This is the output of 'mdadm -D /dev/md0': 
```
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jan 25 20:02:57 2010
     Raid Level : raid5
     Array Size : 4366105152 (4163.84 GiB 4470.89 GB)
  Used Dev Size : 1455368384 (1387.95 GiB 1490.30 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Mar  6 01:54:56 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : badd71f5:ea8866e5:5eaaa51e:5a5908a7
         Events : 0.201025

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5
       3       8       53        3      active sync   /dev/sdd5

Also, here's the output of 'for file in `find /sys/block/md0/md -type f | sort`; do echo $file:; cat $file; done':

/sys/block/md0/md/array_size:
default
/sys/block/md0/md/array_state:
clean
/sys/block/md0/md/bitmap_set_bits:
cat: /sys/block/md0/md/bitmap_set_bits: Permission denied
/sys/block/md0/md/chunk_size:
65536
/sys/block/md0/md/component_size:
1455368384
/sys/block/md0/md/degraded:
0
/sys/block/md0/md/dev-sda5/errors:
0
/sys/block/md0/md/dev-sda5/offset:
0
/sys/block/md0/md/dev-sda5/size:
1455368384
/sys/block/md0/md/dev-sda5/slot:
0
/sys/block/md0/md/dev-sda5/state:
in_sync
/sys/block/md0/md/dev-sdb5/errors:
0
/sys/block/md0/md/dev-sdb5/offset:
0
/sys/block/md0/md/dev-sdb5/size:
1455368384
/sys/block/md0/md/dev-sdb5/slot:
1
/sys/block/md0/md/dev-sdb5/state:
in_sync
/sys/block/md0/md/dev-sdc5/errors:
0
/sys/block/md0/md/dev-sdc5/offset:
0
/sys/block/md0/md/dev-sdc5/size:
1455368384
/sys/block/md0/md/dev-sdc5/slot:
2
/sys/block/md0/md/dev-sdc5/state:
in_sync
/sys/block/md0/md/dev-sdd5/errors:
0
/sys/block/md0/md/dev-sdd5/offset:
0
/sys/block/md0/md/dev-sdd5/size:
1455368384
/sys/block/md0/md/dev-sdd5/slot:
3
/sys/block/md0/md/dev-sdd5/state:
in_sync
/sys/block/md0/md/layout:
2
/sys/block/md0/md/level:
raid5
/sys/block/md0/md/metadata_version:
0.90
/sys/block/md0/md/mismatch_cnt:
0
/sys/block/md0/md/new_dev:
cat: /sys/block/md0/md/new_dev: Permission denied
/sys/block/md0/md/preread_bypass_threshold:
1
/sys/block/md0/md/raid_disks:
4
/sys/block/md0/md/reshape_position:
none
/sys/block/md0/md/resync_start:
none
/sys/block/md0/md/safe_mode_delay:
0.210
/sys/block/md0/md/stripe_cache_active:
0
/sys/block/md0/md/stripe_cache_size:
32768
/sys/block/md0/md/suspend_hi:
0
/sys/block/md0/md/suspend_lo:
0
/sys/block/md0/md/sync_action:
idle
/sys/block/md0/md/sync_completed:
none
/sys/block/md0/md/sync_force_parallel:
0
/sys/block/md0/md/sync_max:
max
/sys/block/md0/md/sync_min:
0
/sys/block/md0/md/sync_speed:
none
/sys/block/md0/md/sync_speed_max:
20000000 (system)
/sys/block/md0/md/sync_speed_min:
100000 (system)
```

The most noticeable behaviour is that when I try to copy a large file, the write speed starts at about 30MB/s (that's the read speed of my external USB drive) and after a few seconds it drops to 1-2MB/s. When I suspend the copy process I see that the drive keeps working for 30-40 more seconds. When I resume the copy, the speed goes backup and the scenario repeats. Also, If I let the copy continue, I see that from time to time the speed picks up to about 25MB/s for 1-2 seconds and then drops for a minute or so. 

Even when the system is supposedly Idle, I see the disk is always working even though 'iotop' shows no IO activity!

Can anyone help me track down the cause of this low performance and fix it? 

Thanks!

for reference, here's my dmesg output:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-server (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:59:59 UTC 2010 (Ubuntu 2.6.31-20.57-server)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-server root=UUID=00000000-0000-0000-0001-000000000001 ro nosplash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007b8d5000 (usable)
[    0.000000]  BIOS-e820: 000000007b8d5000 - 000000007b957000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007b957000 - 000000007ba53000 (reserved)
[    0.000000]  BIOS-e820: 000000007ba53000 - 000000007ba56000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ba56000 - 000000007bb56000 (reserved)
[    0.000000]  BIOS-e820: 000000007bb56000 - 000000007bb5e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bb5e000 - 000000007bb68000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bb68000 - 000000007bb8a000 (reserved)
[    0.000000]  BIOS-e820: 000000007bb8a000 - 000000007bb90000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bb90000 - 000000007bd00000 (usable)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7bd00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07BD00000 mask FFFF00000 write-through
[    0.000000]   2 base 07BE00000 mask FFFE00000 uncachable
[    0.000000]   3 base 07C000000 mask FFC000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009d000 (usable)
[    0.000000]  modified: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007b8d5000 (usable)
[    0.000000]  modified: 000000007b8d5000 - 000000007b957000 (ACPI NVS)
[    0.000000]  modified: 000000007b957000 - 000000007ba53000 (reserved)
[    0.000000]  modified: 000000007ba53000 - 000000007ba56000 (ACPI NVS)
[    0.000000]  modified: 000000007ba56000 - 000000007bb56000 (reserved)
[    0.000000]  modified: 000000007bb56000 - 000000007bb5e000 (ACPI data)
[    0.000000]  modified: 000000007bb5e000 - 000000007bb68000 (ACPI NVS)
[    0.000000]  modified: 000000007bb68000 - 000000007bb8a000 (reserved)
[    0.000000]  modified: 000000007bb8a000 - 000000007bb90000 (ACPI NVS)
[    0.000000]  modified: 000000007bb90000 - 000000007bd00000 (usable)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007bd00000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 007bc00000 page 2M
[    0.000000]  007bc00000 - 007bd00000 page 4k
[    0.000000] kernel direct mapping tables up to 7bd00000 @ 8000-c000
[    0.000000] RAMDISK: 377b4000 - 37fef78a
[    0.000000] ACPI: RSDP 00000000000f03c0 00024 (v02  INTEL)
[    0.000000] ACPI: XSDT 000000007bb5ce18 0004C (v01  INTEL   DG43NB 00000063 MSFT 00010013)
[    0.000000] ACPI: FACP 000000007bb5bd98 000F4 (v04  INTEL   DG43NB 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! 20090521 tbfadt-370
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 7BB5FF40/000000007BB64F40, using 32 20090521 tbfadt-487
[    0.000000] ACPI: DSDT 000000007bb56018 04E89 (v01  INTEL   DG43NB 00000063 INTL 20051117)
[    0.000000] ACPI: FACS 000000007bb5ff40 00040
[    0.000000] ACPI: APIC 000000007bb5bf18 0006C (v02  INTEL   DG43NB 00000063 MSFT 00010013)
[    0.000000] ACPI: MCFG 000000007bb66e18 0003C (v01 INTEL  DG43NB   00000063 MSFT 00000097)
[    0.000000] ACPI: ASF! 000000007bb65d18 000A0 (v32 INTEL    DG43NB 00000063 TFSM 000F4240)
[    0.000000] ACPI: HPET 000000007bb66d98 00038 (v01 INTEL  DG43NB   00000063 AMI. 00000003)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007bd00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007bd00000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  000000000001e79f] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007bd00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e6c8c]    TEXT DATA BSS ==> [0001000000 - 00019e6c8c]
[    0.000000]   #3 [00377b4000 - 0037fef78a]          RAMDISK ==> [00377b4000 - 0037fef78a]
[    0.000000]   #4 [000009d000 - 0000100000]    BIOS reserved ==> [000009d000 - 0000100000]
[    0.000000]   #5 [00019e7000 - 00019e71ec]              BRK ==> [00019e7000 - 00019e71ec]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007b8d5
[    0.000000]     0: 0x0007bb90 -> 0x0007bd00
[    0.000000] On node 0 totalpages: 506333
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3832 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6878 pages used for memmap
[    0.000000]   DMA32 zone: 495463 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000007b8d5000 - 000000007b957000
[    0.000000] PM: Registered nosave memory: 000000007b957000 - 000000007ba53000
[    0.000000] PM: Registered nosave memory: 000000007ba53000 - 000000007ba56000
[    0.000000] PM: Registered nosave memory: 000000007ba56000 - 000000007bb56000
[    0.000000] PM: Registered nosave memory: 000000007bb56000 - 000000007bb5e000
[    0.000000] PM: Registered nosave memory: 000000007bb5e000 - 000000007bb68000
[    0.000000] PM: Registered nosave memory: 000000007bb68000 - 000000007bb8a000
[    0.000000] PM: Registered nosave memory: 000000007bb8a000 - 000000007bb90000
[    0.000000] Allocating PCI resources starting at 7bd00000 (gap: 7bd00000:8301c000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f8000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 499295
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-server root=UUID=00000000-0000-0000-0001-000000000001 ro nosplash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1977436k/2028544k available (5318k kernel code, 3212k absent, 47896k reserved, 3015k data, 664k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2593.848 MHz processor.
[    0.001233] Console: colour VGA+ 80x25
[    0.001236] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5187.69 BogoMIPS (lpj=25938480)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.012635] Setting APIC routing to flat
[    0.012999] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.113079] CPU0: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 5186.96 BogoMIPS (lpj=25934828)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.271406] CPU1: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
[    0.272007] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280022] Brought up 2 CPUs
[    0.280671] Total of 2 processors activated (10374.66 BogoMIPS).
[    0.280774] CPU0 attaching sched-domain:
[    0.280777]  domain 0: span 0-1 level MC
[    0.280779]   groups: 0 1
[    0.280783] CPU1 attaching sched-domain:
[    0.280784]  domain 0: span 0-1 level MC
[    0.280786]   groups: 1 0
[    0.280850] Booting paravirtualized kernel on bare hardware
[    0.280850] regulator: core version 0.5
[    0.280850] Time: 22:13:40  Date: 03/05/10
[    0.280850] NET: Registered protocol family 16
[    0.280850] ACPI: bus type pci registered
[    0.280850] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.280850] PCI: Not using MMCONFIG.
[    0.280850] PCI: Using configuration type 1 for base access
[    0.281193] bio: create slab <bio-0> at 0
[    0.281193] ACPI: EC: Look up EC in DSDT
[    0.290308] ACPI: Interpreter enabled
[    0.290354] ACPI: (supports S0 S1 S3 S4 S5)
[    0.290510] ACPI: Using IOAPIC for interrupt routing
[    0.290602] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.290712] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.292335] PCI: Using MMCONFIG at f0000000 - f7ffffff
[    0.292618] ACPI: BIOS _OSI(Linux) query ignored
[    0.297309] ACPI: No dock devices found.
[    0.297549] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.297683] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.297735] pci 0000:00:01.0: PME# disabled
[    0.297800] pci 0000:00:02.0: reg 10 64bit mmio: [0xe0000000-0xe03fffff]
[    0.297806] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.297810] pci 0000:00:02.0: reg 20 io port: [0xf140-0xf147]
[    0.297839] pci 0000:00:02.1: reg 10 64bit mmio: [0xe0400000-0xe04fffff]
[    0.297903] pci 0000:00:03.0: reg 10 64bit mmio: [0xe0726100-0xe072610f]
[    0.297954] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.298006] pci 0000:00:03.0: PME# disabled
[    0.298118] pci 0000:00:19.0: reg 10 32bit mmio: [0xe0700000-0xe071ffff]
[    0.298124] pci 0000:00:19.0: reg 14 32bit mmio: [0xe0724000-0xe0724fff]
[    0.298129] pci 0000:00:19.0: reg 18 io port: [0xf0e0-0xf0ff]
[    0.298165] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.298217] pci 0000:00:19.0: PME# disabled
[    0.298306] pci 0000:00:1a.0: reg 20 io port: [0xf0c0-0xf0df]
[    0.298369] pci 0000:00:1a.1: reg 20 io port: [0xf0a0-0xf0bf]
[    0.298431] pci 0000:00:1a.2: reg 20 io port: [0xf080-0xf09f]
[    0.298498] pci 0000:00:1a.7: reg 10 32bit mmio: [0xe0725c00-0xe0725fff]
[    0.298548] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.298600] pci 0000:00:1a.7: PME# disabled
[    0.298681] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe0720000-0xe0723fff]
[    0.298719] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.298770] pci 0000:00:1b.0: PME# disabled
[    0.298867] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.298918] pci 0000:00:1c.0: PME# disabled
[    0.299018] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.299069] pci 0000:00:1c.3: PME# disabled
[    0.299166] pci 0000:00:1d.0: reg 20 io port: [0xf060-0xf07f]
[    0.299231] pci 0000:00:1d.1: reg 20 io port: [0xf040-0xf05f]
[    0.299294] pci 0000:00:1d.2: reg 20 io port: [0xf020-0xf03f]
[    0.299362] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0725800-0xe0725bff]
[    0.299412] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.299464] pci 0000:00:1d.7: PME# disabled
[    0.299672] pci 0000:00:1f.2: reg 10 io port: [0xf130-0xf137]
[    0.299677] pci 0000:00:1f.2: reg 14 io port: [0xf120-0xf123]
[    0.299683] pci 0000:00:1f.2: reg 18 io port: [0xf110-0xf117]
[    0.299688] pci 0000:00:1f.2: reg 1c io port: [0xf100-0xf103]
[    0.299693] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf01f]
[    0.299698] pci 0000:00:1f.2: reg 24 32bit mmio: [0xe0725000-0xe07257ff]
[    0.299725] pci 0000:00:1f.2: PME# supported from D3hot
[    0.299775] pci 0000:00:1f.2: PME# disabled
[    0.299845] pci 0000:00:1f.3: reg 10 64bit mmio: [0xe0726000-0xe07260ff]
[    0.299857] pci 0000:00:1f.3: reg 20 io port: [0x1180-0x119f]
[    0.300045] pci 0000:03:00.0: reg 10 io port: [0xe040-0xe047]
[    0.300054] pci 0000:03:00.0: reg 14 io port: [0xe030-0xe033]
[    0.300063] pci 0000:03:00.0: reg 18 io port: [0xe020-0xe027]
[    0.300071] pci 0000:03:00.0: reg 1c io port: [0xe010-0xe013]
[    0.300080] pci 0000:03:00.0: reg 20 io port: [0xe000-0xe00f]
[    0.300175] pci 0000:00:1c.3: bridge io port: [0xe000-0xefff]
[    0.300179] pci 0000:00:1c.3: bridge 32bit mmio: [0xe0600000-0xe06fffff]
[    0.300228] pci 0000:04:04.0: reg 10 32bit mmio: [0xe0540000-0xe055ffff]
[    0.300235] pci 0000:04:04.0: reg 14 32bit mmio: [0xe0520000-0xe053ffff]
[    0.300241] pci 0000:04:04.0: reg 18 io port: [0xd000-0xd03f]
[    0.300261] pci 0000:04:04.0: reg 30 32bit mmio: [0xe0500000-0xe051ffff]
[    0.300282] pci 0000:04:04.0: PME# supported from D0 D3hot D3cold
[    0.300335] pci 0000:04:04.0: PME# disabled
[    0.300414] pci 0000:04:06.0: reg 10 32bit mmio: [0xe0560000-0xe0560fff]
[    0.300456] pci 0000:04:06.0: supports D1 D2
[    0.300458] pci 0000:04:06.0: PME# supported from D0 D1 D2 D3hot
[    0.300510] pci 0000:04:06.0: PME# disabled
[    0.300596] pci 0000:00:1e.0: transparent bridge
[    0.300644] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.300648] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0500000-0xe05fffff]
[    0.300668] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.300805] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.300850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.300893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.305549] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.305913] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.306275] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.306620] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.306962] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.307324] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.307686] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.308048] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.308471] SCSI subsystem initialized
[    0.308537] libata version 3.00 loaded.
[    0.308537] usbcore: registered new interface driver usbfs
[    0.308537] usbcore: registered new interface driver hub
[    0.308537] usbcore: registered new device driver usb
[    0.308537] ACPI: WMI: Mapper loaded
[    0.308537] PCI: Using ACPI for IRQ routing
[    0.330010] Bluetooth: Core ver 2.15
[    0.330085] NET: Registered protocol family 31
[    0.330085] Bluetooth: HCI device and connection manager initialized
[    0.330137] Bluetooth: HCI socket layer initialized
[    0.330184] NetLabel: Initializing
[    0.330227] NetLabel:  domain hash size = 128
[    0.330273] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.330332] NetLabel:  unlabeled traffic allowed by default
[    0.330417] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.330564] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.369992] pnp: PnP ACPI init
[    0.370060] ACPI: bus type pnp registered
[    0.371808] pnp: PnP ACPI: found 11 devices
[    0.371854] ACPI: ACPI bus type pnp unregistered
[    0.371908] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.371961] system 00:01: iomem range 0xf0000000-0xf7ffffff has been reserved
[    0.372019] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.372070] system 00:07: ioport range 0x540-0x57f has been reserved
[    0.372122] system 00:07: iomem range 0xffe00000-0xffffffff has been reserved
[    0.372174] system 00:07: iomem range 0xfed30000-0xfed3ffff has been reserved
[    0.372227] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.372282] system 00:09: ioport range 0x400-0x47f has been reserved
[    0.372333] system 00:09: ioport range 0x1180-0x119f has been reserved
[    0.372385] system 00:09: ioport range 0x500-0x57f could not be reserved
[    0.372437] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.372490] system 00:09: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.372559] system 00:09: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.372612] system 00:09: iomem range 0xff000000-0xffffffff could not be reserved
[    0.377314] AppArmor: AppArmor Filesystem Enabled
[    0.377375] pci 0000:04:04.0: BAR 6: address space collision on of device [0xe0500000-0xe051ffff]
[    0.377475] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.377524] pci 0000:00:01.0:   IO window: disabled
[    0.377573] pci 0000:00:01.0:   MEM window: disabled
[    0.377622] pci 0000:00:01.0:   PREFETCH window: disabled
[    0.377672] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.377721] pci 0000:00:1c.0:   IO window: disabled
[    0.377770] pci 0000:00:1c.0:   MEM window: disabled
[    0.377819] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.377869] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.377920] pci 0000:00:1c.3:   IO window: 0xe000-0xefff
[    0.377971] pci 0000:00:1c.3:   MEM window: 0xe0600000-0xe06fffff
[    0.378022] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.378073] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.378124] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.378175] pci 0000:00:1e.0:   MEM window: 0xe0500000-0xe05fffff
[    0.378227] pci 0000:00:1e.0:   PREFETCH window: 0x7c000000-0x7c0fffff
[    0.378285]   alloc irq_desc for 16 on node 0
[    0.378287]   alloc kstat_irqs on node 0
[    0.378291] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.378344] pci 0000:00:01.0: setting latency timer to 64
[    0.378350]   alloc irq_desc for 17 on node 0
[    0.378352]   alloc kstat_irqs on node 0
[    0.378354] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.378407] pci 0000:00:1c.0: setting latency timer to 64
[    0.378413]   alloc irq_desc for 19 on node 0
[    0.378414]   alloc kstat_irqs on node 0
[    0.378417] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.378470] pci 0000:00:1c.3: setting latency timer to 64
[    0.378476] pci 0000:00:1e.0: setting latency timer to 64
[    0.378479] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.378481] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.378484] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.378485] pci_bus 0000:03: resource 1 mem: [0xe0600000-0xe06fffff]
[    0.378487] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    0.378489] pci_bus 0000:04: resource 1 mem: [0xe0500000-0xe05fffff]
[    0.378491] pci_bus 0000:04: resource 2 pref mem [0x7c000000-0x7c0fffff]
[    0.378492] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.378494] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.378522] NET: Registered protocol family 2
[    0.378677] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.379358] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.381557] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.382176] TCP: Hash tables configured (established 262144 bind 65536)
[    0.382228] TCP reno registered
[    0.382390] NET: Registered protocol family 1
[    0.382495] Trying to unpack rootfs image as initramfs...
[    0.502066] Switched to high resolution mode on CPU 1
[    0.509967] Switched to high resolution mode on CPU 0
[    0.538080] Freeing initrd memory: 8429k freed
[    0.542029] Scanning for low memory corruption every 60 seconds
[    0.542213] audit: initializing netlink socket (disabled)
[    0.542277] type=2000 audit(1267827219.540:1): initialized
[    0.549776] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.550930] VFS: Disk quotas dquot_6.5.2
[    0.551023] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.551506] fuse init (API version 7.12)
[    0.551610] msgmni has been set to 3878
[    0.551814] alg: No test for stdrng (krng)
[    0.551869] io scheduler noop registered
[    0.551915] io scheduler anticipatory registered
[    0.551961] io scheduler deadline registered (default)
[    0.552039] io scheduler cfq registered
[    0.552093] pci 0000:00:02.0: Boot video device
[    2.550009] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.550009] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    4.550301]   alloc irq_desc for 24 on node 0
[    4.550302]   alloc kstat_irqs on node 0
[    4.550310] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    4.550315] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    4.550416]   alloc irq_desc for 25 on node 0
[    4.550417]   alloc kstat_irqs on node 0
[    4.550423] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    4.550431] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    4.550544]   alloc irq_desc for 26 on node 0
[    4.550546]   alloc kstat_irqs on node 0
[    4.550552] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    4.550559] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    4.550627] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.550691] Firmware did not grant requested _OSC control
[    4.550716] Firmware did not grant requested _OSC control
[    4.550727] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.550875] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    4.550945] ACPI: Power Button [PWRF]
[    4.551035] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    4.551109] ACPI: Sleep Button [SLPB]
[    4.551188] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    4.551261] ACPI: Power Button [PWRB]
[    4.551668] ACPI: SSDT 000000007bb5fc18 002CC (v01    AMI      IST 00000001 MSFT 03000001)
[    4.552114] Marking TSC unstable due to TSC halts in idle
[    4.552179] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    4.552322] processor LNXCPU:00: registered as cooling_device0
[    4.552566] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    4.552703] processor LNXCPU:01: registered as cooling_device1
[    4.554689] Linux agpgart interface v0.103
[    4.554741] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.554881] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.555141] 00:03: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.555960] brd: module loaded
[    4.556329] loop: module loaded
[    4.556428] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    4.556581] ahci 0000:00:1f.2: version 3.0
[    4.556594] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.556670]   alloc irq_desc for 27 on node 0
[    4.556671]   alloc kstat_irqs on node 0
[    4.556679] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    4.556754] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    4.556825] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ems 
[    4.556896] ahci 0000:00:1f.2: setting latency timer to 64
[    4.650075] scsi0 : ahci
[    4.650238] scsi1 : ahci
[    4.650324] scsi2 : ahci
[    4.650408] scsi3 : ahci
[    4.650495] scsi4 : ahci
[    4.650585] scsi5 : ahci
[    4.650661] ata1: SATA max UDMA/133 abar m2048@0xe0725000 port 0xe0725100 irq 27
[    4.650731] ata2: SATA max UDMA/133 abar m2048@0xe0725000 port 0xe0725180 irq 27
[    4.650800] ata3: SATA max UDMA/133 abar m2048@0xe0725000 port 0xe0725200 irq 27
[    4.650869] ata4: SATA max UDMA/133 abar m2048@0xe0725000 port 0xe0725280 irq 27
[    4.650938] ata5: SATA max UDMA/133 abar m2048@0xe0725000 port 0xe0725300 irq 27
[    4.651616] ata6: SATA max UDMA/133 abar m2048@0xe0725000 port 0xe0725380 irq 27
[    4.652014] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.652110] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    4.652167] scsi6 : pata_jmicron
[    4.652275] scsi7 : pata_jmicron
[    4.652341] ata7: PATA max UDMA/100 cmd 0xe040 ctl 0xe030 bmdma 0xe000 irq 19
[    4.652393] ata8: PATA max UDMA/100 cmd 0xe020 ctl 0xe010 bmdma 0xe008 irq 19
[    4.652830] Fixed MDIO Bus: probed
[    4.652899] PPP generic driver version 2.4.2
[    4.653024] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.653115]   alloc irq_desc for 18 on node 0
[    4.653117]   alloc kstat_irqs on node 0
[    4.653122] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.653185] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.653188] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.653266] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.657226] ehci_hcd 0000:00:1a.7: debug port 1
[    4.657277] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.657286] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe0725c00
[    4.680019] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.680173] usb usb1: configuration #1 chosen from 1 choice
[    4.680255] hub 1-0:1.0: USB hub found
[    4.680305] hub 1-0:1.0: 6 ports detected
[    4.680418]   alloc irq_desc for 23 on node 0
[    4.680419]   alloc kstat_irqs on node 0
[    4.680423] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.680481] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.680484] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.680554] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.684511] ehci_hcd 0000:00:1d.7: debug port 1
[    4.684560] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.684570] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe0725800
[    4.700014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.700189] usb usb2: configuration #1 chosen from 1 choice
[    4.700265] hub 2-0:1.0: USB hub found
[    4.700314] hub 2-0:1.0: 6 ports detected
[    4.700410] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.700470] uhci_hcd: USB Universal Host Controller Interface driver
[    4.700585] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.700641] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.700644] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.700712] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.700808] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000f0c0
[    4.700919] usb usb3: configuration #1 chosen from 1 choice
[    4.700984] hub 3-0:1.0: USB hub found
[    4.701033] hub 3-0:1.0: 2 ports detected
[    4.701134]   alloc irq_desc for 21 on node 0
[    4.701136]   alloc kstat_irqs on node 0
[    4.701139] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.701195] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.701197] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.701276] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.701370] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000f0a0
[    4.701474] usb usb4: configuration #1 chosen from 1 choice
[    4.701544] hub 4-0:1.0: USB hub found
[    4.701593] hub 4-0:1.0: 2 ports detected
[    4.701697] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.701752] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    4.701755] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    4.701822] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    4.701910] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000f080
[    4.702015] usb usb5: configuration #1 chosen from 1 choice
[    4.702080] hub 5-0:1.0: USB hub found
[    4.702129] hub 5-0:1.0: 2 ports detected
[    4.702230] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.702286] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.702288] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.702358] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    4.702446] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000f060
[    4.702547] usb usb6: configuration #1 chosen from 1 choice
[    4.702615] hub 6-0:1.0: USB hub found
[    4.702664] hub 6-0:1.0: 2 ports detected
[    4.702762] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.702818] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.702821] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.702887] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    4.702975] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000f040
[    4.703082] usb usb7: configuration #1 chosen from 1 choice
[    4.703147] hub 7-0:1.0: USB hub found
[    4.703195] hub 7-0:1.0: 2 ports detected
[    4.703297] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.703353] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.703356] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.703422] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    4.703511] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f020
[    4.703620] usb usb8: configuration #1 chosen from 1 choice
[    4.703686] hub 8-0:1.0: USB hub found
[    4.703734] hub 8-0:1.0: 2 ports detected
[    4.703854] PNP: No PS/2 controller found. Probing ports directly.
[    4.706490] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.706544] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.706641] mice: PS/2 mouse device common for all mice
[    4.706770] rtc_cmos 00:05: RTC can wake from S4
[    4.706846] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    4.706918] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.707059] device-mapper: uevent: version 1.0.3
[    4.707180] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    4.707307] device-mapper: multipath: version 1.1.0 loaded
[    4.707359] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.707589] cpuidle: using governor ladder
[    4.707717] cpuidle: using governor menu
[    4.708074] TCP cubic registered
[    4.708213] NET: Registered protocol family 10
[    4.708603] lo: Disabled Privacy Extensions
[    4.708864] NET: Registered protocol family 17
[    4.708924] Bluetooth: L2CAP ver 2.13
[    4.708969] Bluetooth: L2CAP socket layer initialized
[    4.709018] Bluetooth: SCO (Voice Link) ver 0.6
[    4.709064] Bluetooth: SCO socket layer initialized
[    4.709137] Bluetooth: RFCOMM TTY layer initialized
[    4.709185] Bluetooth: RFCOMM socket layer initialized
[    4.709232] Bluetooth: RFCOMM ver 1.11
[    4.709615] PM: Resume from disk failed.
[    4.709626] registered taskstats version 1
[    4.709777]   Magic number: 2:857:248
[    4.709910] rtc_cmos 00:05: setting system clock to 2010-03-05 22:13:44 UTC (1267827224)
[    4.709981] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.710048] EDD information not available.
[    4.840619] ata7.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 2.00, max UDMA/66
[    4.840682] ata7.00: limited to UDMA/33 due to 40-wire cable
[    4.880642] ata7.00: configured for UDMA/33
[    5.000029] Clocksource tsc unstable (delta = -144969703 ns)
[    5.000112] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.000177] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.000240] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.000302] ata5: SATA link down (SStatus 0 SControl 300)
[    5.000374] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.000437] ata6: SATA link down (SStatus 0 SControl 300)
[    5.001872] ata3.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[    5.001925] ata3.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.003410] ata1.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[    5.003439] ata2.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[    5.003441] ata2.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.003551] ata4.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[    5.003553] ata4.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.003623] ata3.00: configured for UDMA/133
[    5.003633] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
[    5.003634] ata3: irq_stat 0x00400040, connection status changed
[    5.003637] ata3: hard resetting link
[    5.003891] ata1.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.007556] ata4.00: configured for UDMA/133
[    5.007608] ata4: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
[    5.007664] ata1.00: configured for UDMA/133
[    5.007732] ata4: irq_stat 0x00400040, connection status changed
[    5.007743] scsi 0:0:0:0: Direct-Access     ATA      WDC WD15EADS-00P 01.0 PQ: 0 ANSI: 5
[    5.007836] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.007867] sd 0:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    5.007901] sd 0:0:0:0: [sda] Write Protect is off
[    5.007902] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.007920] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.008021]  sda:
[    5.008065] ata2.00: configured for UDMA/133
[    5.008074] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
[    5.008075] ata2: irq_stat 0x00400040, connection status changed
[    5.008078] ata2: hard resetting link
[    5.008370] ata4: hard resetting link
[    5.017021]  sda1 sda2 sda3 < sda5 >
[    5.029533] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.300025] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    5.488624] usb 6-2: configuration #1 chosen from 1 choice
[    5.750033] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.757455] ata2.00: configured for UDMA/133
[    5.757503] ata2: EH complete
[    5.757594] scsi 1:0:0:0: Direct-Access     ATA      WDC WD15EADS-00P 01.0 PQ: 0 ANSI: 5
[    5.757740] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    5.757811] sd 1:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    5.757911] sd 1:0:0:0: [sdb] Write Protect is off
[    5.757958] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.757975] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.758126]  sdb:
[    5.760047] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.760147] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.763423] ata3.00: configured for UDMA/133
[    5.763470] ata3: EH complete
[    5.763555] scsi 2:0:0:0: Direct-Access     ATA      WDC WD15EADS-00P 01.0 PQ: 0 ANSI: 5
[    5.763693] sd 2:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    5.763699] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    5.763844] sd 2:0:0:0: [sdc] Write Protect is off
[    5.763891] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.763909] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.764661]  sdc:
[    5.767359] ata4.00: configured for UDMA/133
[    5.767442] ata4: EH complete
[    5.767524] scsi 3:0:0:0: Direct-Access     ATA      WDC WD15EADS-00P 01.0 PQ: 0 ANSI: 5
[    5.767666] sd 3:0:0:0: [sdd] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    5.767667] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    5.767820] sd 3:0:0:0: [sdd] Write Protect is off
[    5.767867] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    5.767884] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.768035]  sdd:
[    5.769301] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 2.00 PQ: 0 ANSI: 5
[    5.770023] usb 8-2: new low speed USB device using uhci_hcd and address 2
[    5.771073] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.771143] Uniform CD-ROM driver Revision: 3.20
[    5.771242] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    5.771277] sr 6:0:0:0: Attached scsi generic sg4 type 5
[    5.771997]  sdb1 sdb2 sdb3 < sdd1 sdd2 sdd3 < sdd5 >
[    5.796049]  sdb5 >
[    5.797688] sd 3:0:0:0: [sdd] Attached SCSI disk
[    5.801113] sd 1:0:0:0: [sdb] Attached SCSI disk
[    5.952638] usb 8-2: configuration #1 chosen from 1 choice
[    6.248602]  sdc1 sdc2 sdc3 < sdc5 >
[    6.271098] sd 2:0:0:0: [sdc] Attached SCSI disk
[    6.271178] Freeing unused kernel memory: 664k freed
[    6.271432] Write protecting the kernel read-only data: 7584k
[    6.349160] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
[    6.349798] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    6.352915] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    6.365216] [drm] Initialized drm 1.1.0 20060810
[    6.369132] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    6.369205] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    6.369393]   alloc irq_desc for 20 on node 0
[    6.369395]   alloc kstat_irqs on node 0
[    6.369404] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.369479] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb
[    6.369577] e1000e 0000:00:19.0: setting latency timer to 64
[    6.369651]   alloc irq_desc for 28 on node 0
[    6.369652]   alloc kstat_irqs on node 0
[    6.369662] e1000e 0000:00:19.0: irq 28 for MSI/MSI-X
[    6.428717] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    6.428782] Copyright (c) 1999-2006 Intel Corporation.
[    6.431697]   alloc irq_desc for 22 on node 0
[    6.431700]   alloc kstat_irqs on node 0
[    6.431707] e1000 0000:04:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.440388] usbcore: registered new interface driver hiddev
[    6.453898] input: Microsoft Microsoft® Digital Media Keyboard     as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input4
[    6.454047] generic-usb 0003:045E:00B4.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Digital Media Keyboard    ] on usb-0000:00:1d.0-2/input0
[    6.531407] input: Microsoft Microsoft® Digital Media Keyboard     as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input5
[    6.531552] generic-usb 0003:045E:00B4.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Microsoft® Digital Media Keyboard    ] on usb-0000:00:1d.0-2/input1
[    6.547844] input: Microsoft  Microsoft Basic Optical Mouse  as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input6
[    6.547995] generic-usb 0003:045E:0084.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse ] on usb-0000:00:1d.2-2/input0
[    6.548095] usbcore: registered new interface driver usbhid
[    6.548146] usbhid: v2.6:USB HID core driver
[    6.589707] md: bind<sda5>
[    6.619905] md: bind<sdc5>
[    6.709823] e1000: 0000:04:04.0: e1000_probe: (PCI:33MHz:32-bit) 00:1b:21:56:97:73
[    6.722445] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:c0:b0:6c:46
[    6.722515] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    6.722590] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: ffffff-0ff
[    6.722790] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.722852] i915 0000:00:02.0: setting latency timer to 64
[    6.729184]   alloc irq_desc for 29 on node 0
[    6.729187]   alloc kstat_irqs on node 0
[    6.729194] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    6.734503] [drm] i2c_init DPDDC-B
[    6.887183] i2c-adapter i2c-1: unable to read EDID block.
[    6.887233] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    6.890478] [drm] fb0: inteldrmfb frame buffer device
[    6.890622] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.955583] [drm] DAC-6: set mode 1024x768 16
[    6.977478] Console: switching to colour frame buffer device 128x48
[    6.992461] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[    6.992659] ohci1394 0000:04:06.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    7.052048] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[23]  MMIO=[e0560000-e05607ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    8.370112] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009027000259fbaa]
[   13.092165] md: bind<sdd5>
[   16.777444] md: bind<sdb5>
[   16.781506] xor: automatically using best checksumming function: generic_sse
[   16.831258]    generic_sse:  9876.400 MB/sec
[   16.831278] xor: using function: generic_sse (9876.400 MB/sec)
[   16.831719] async_tx: api initialized (async)
[   17.001277] raid6: int64x1   2037 MB/s
[   17.171268] raid6: int64x2   2725 MB/s
[   17.341259] raid6: int64x4   1960 MB/s
[   17.511276] raid6: int64x8   1785 MB/s
[   17.681261] raid6: sse2x1    4369 MB/s
[   17.851259] raid6: sse2x2    4508 MB/s
[   18.021260] raid6: sse2x4    7678 MB/s
[   18.021278] raid6: using algorithm sse2x4 (7678 MB/s)
[   18.023355] md: raid6 personality registered for level 6
[   18.023381] md: raid5 personality registered for level 5
[   18.023403] md: raid4 personality registered for level 4
[   18.023631] raid5: device sdb5 operational as raid disk 1
[   18.024134] raid5: device sdd5 operational as raid disk 3
[   18.024625] raid5: device sdc5 operational as raid disk 2
[   18.025123] raid5: device sda5 operational as raid disk 0
[   18.025951] raid5: allocated 4280kB for md0
[   18.026491] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
[   18.027042] RAID5 conf printout:
[   18.027611]  --- rd:4 wd:4
[   18.028190]  disk 0, o:1, dev:sda5
[   18.028794]  disk 1, o:1, dev:sdb5
[   18.029389]  disk 2, o:1, dev:sdc5
[   18.029989]  disk 3, o:1, dev:sdd5
[   18.030619] md0: detected capacity change from 0 to 4470891675648
[   18.032234]  md0: unknown partition table
[   18.683695] md: linear personality registered for level -1
[   18.686198] md: multipath personality registered for level -4
[   18.688447] md: raid0 personality registered for level 0
[   18.691539] md: raid1 personality registered for level 1
[   18.697960] md: raid10 personality registered for level 10
[   18.756270] PM: Starting manual resume from disk
[   18.757067] PM: Resume from partition 8:2
[   18.757068] PM: Checking hibernation image.
[   18.757175] PM: Resume from disk failed.
[   18.789142] EXT4-fs (sda1): barriers enabled
[   18.804608] kjournald2 starting: pid 500, dev sda1:8, commit interval 5 seconds
[   18.805442] EXT4-fs (sda1): delayed allocation enabled
[   18.806239] EXT4-fs: file extents enabled
[   18.807144] EXT4-fs: mballoc enabled
[   18.807912] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   19.170279] type=1505 audit(1267827238.951:2): operation="profile_load" pid=528 name=/usr/share/gdm/guest-session/Xsession
[   19.186366] type=1505 audit(1267827238.971:3): operation="profile_load" pid=529 name=/sbin/dhclient3
[   19.187752] type=1505 audit(1267827238.971:4): operation="profile_load" pid=529 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.189708] type=1505 audit(1267827238.971:5): operation="profile_load" pid=529 name=/usr/lib/connman/scripts/dhclient-script
[   19.221028] type=1505 audit(1267827239.001:6): operation="profile_load" pid=530 name=/usr/bin/evince
[   19.230553] type=1505 audit(1267827239.012:7): operation="profile_load" pid=530 name=/usr/bin/evince-previewer
[   19.236544] type=1505 audit(1267827239.021:8): operation="profile_load" pid=530 name=/usr/bin/evince-thumbnailer
[   19.266906] type=1505 audit(1267827239.051:9): operation="profile_load" pid=532 name=/usr/lib/cups/backend/cups-pdf
[   19.268522] type=1505 audit(1267827239.051:10): operation="profile_load" pid=532 name=/usr/sbin/cupsd
[   19.279956] type=1505 audit(1267827239.061:11): operation="profile_load" pid=533 name=/usr/sbin/dhcpd3
[   20.139284] Adding 1951888k swap on /dev/sda2.  Priority:-1 extents:1 across:1951888k 
[   20.147140] Adding 1951888k swap on /dev/sdb2.  Priority:-2 extents:1 across:1951888k 
[   20.160588] Adding 1951888k swap on /dev/sdc2.  Priority:-3 extents:1 across:1951888k 
[   20.165476] Adding 1951888k swap on /dev/sdd2.  Priority:-4 extents:1 across:1951888k 
[   20.651572] EXT4-fs (sda1): internal journal on sda1:8
[   21.141384] udev: starting version 147
[   21.978529] RPC: Registered udp transport module.
[   21.978532] RPC: Registered tcp transport module.
[   22.000295] heci: module is from the staging directory, the quality is unknown, you have been warned.
[   22.001197] heci: Intel(R) Management Engine Interface - version 5.0.0.31
[   22.001199] heci: Copyright (c) 2003 - 2008 Intel Corporation.
[   22.005579] heci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.005585] heci 0000:00:03.0: setting latency timer to 64
[   22.006934] heci: link layer has been established.
[   22.019531] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   22.125693] heci driver initialization successful.
[   22.227512] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.228606] lp: driver loaded but no devices found
[   22.477181] w83627ehf: Found W83627DHG chip at 0x290
[   23.571427] e1000e 0000:00:19.0: irq 28 for MSI/MSI-X
[   23.631628] e1000e 0000:00:19.0: irq 28 for MSI/MSI-X
[   23.631891] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.642265] coretemp coretemp.0: Using relative temperature scale!
[   23.642305] coretemp coretemp.1: Using relative temperature scale!
[   23.769076] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[   24.107414] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.107443] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.404012] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   24.404193] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   25.200786] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   25.200790] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   25.201007] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.107148] i2c-adapter i2c-1: unable to read EDID block.
[   28.107152] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.111718] i2c-adapter i2c-1: unable to read EDID block.
[   28.111720] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.267405] i2c-adapter i2c-1: unable to read EDID block.
[   28.267409] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.271974] i2c-adapter i2c-1: unable to read EDID block.
[   28.271976] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.440118] [drm] DAC-6: set mode 1280x1024 18
[   33.079120] i2c-adapter i2c-1: unable to read EDID block.
[   33.079124] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.083781] i2c-adapter i2c-1: unable to read EDID block.
[   33.083783] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.228648] i2c-adapter i2c-1: unable to read EDID block.
[   33.228652] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.233532] i2c-adapter i2c-1: unable to read EDID block.
[   33.233535] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.406866] i2c-adapter i2c-1: unable to read EDID block.
[   33.406869] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.411550] i2c-adapter i2c-1: unable to read EDID block.
[   33.411554] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   34.952773] [drm] DAC-6: set mode 1024x768 16
[   35.070624] CPU0 attaching NULL sched-domain.
[   35.070629] CPU1 attaching NULL sched-domain.
[   35.112137] CPU0 attaching sched-domain:
[   35.112141]  domain 0: span 0-1 level MC
[   35.112143]   groups: 0 1
[   35.112148] CPU1 attaching sched-domain:
[   35.112149]  domain 0: span 0-1 level MC
[   35.112151]   groups: 1 0
[   35.125161] EXT4-fs (md0): barriers enabled
[   35.180336] kjournald2 starting: pid 1616, dev md0:8, commit interval 5 seconds
[   36.000020] eth0: no IPv6 routers present
[   36.904688] EXT4-fs (md0): internal journal on md0:8
[   36.904693] EXT4-fs (md0): delayed allocation enabled
[   36.904696] EXT4-fs: file extents enabled
[   37.109480] EXT4-fs: mballoc enabled
[   37.109499] EXT4-fs (md0): mounted filesystem with ordered data mode
[   48.123712] svc: failed to register lockdv1 RPC service (errno 97).
[   48.124338] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   48.144013] NFSD: starting 90-second grace period
[   51.161779] ppdev: user-space parallel port driver
[   53.093714] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   53.093889] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   53.093890] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   53.093892] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   61.231582] [drm] DAC-6: set mode 640x480 1b
[   62.820403] Netfilter messages via NETLINK v0.30.
[   68.178826] i2c-adapter i2c-1: unable to read EDID block.
[   68.178829] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   68.183514] i2c-adapter i2c-1: unable to read EDID block.
[   68.183517] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   68.327813] i2c-adapter i2c-1: unable to read EDID block.
[   68.327817] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   68.332256] i2c-adapter i2c-1: unable to read EDID block.
[   68.332258] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   68.476587] i2c-adapter i2c-1: unable to read EDID block.
[   68.476591] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   68.481035] i2c-adapter i2c-1: unable to read EDID block.
[   68.481037] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   72.903173] UDF-fs: No VRS found
[   72.903177] UDF-fs: No partition found (1)
[   72.954434] ISO 9660 Extensions: Microsoft Joliet Level 3
[   73.079439] ISO 9660 Extensions: RRIP_1991A
[  123.881688] JBD: barrier-based sync failed on md0:8 - disabling barriers
[  200.840102] usb 1-6: new high speed USB device using ehci_hcd and address 2
[  200.991628] usb 1-6: configuration #1 chosen from 1 choice
[  201.040563] Initializing USB Mass Storage driver...
[  201.040751] scsi8 : SCSI emulation for USB Mass Storage devices
[  201.040860] usbcore: registered new interface driver usb-storage
[  201.040865] USB Mass Storage support registered.
[  201.043051] usb-storage: device found at 2
[  201.043055] usb-storage: waiting for device to settle before scanning
[  206.040444] usb-storage: device scan complete
[  206.041410] scsi 8:0:0:0: Direct-Access     WD       My Passport 070A 1030 PQ: 0 ANSI: 4
[  206.042276] scsi 8:0:0:1: CD-ROM            WD       Virtual CD 070A  1030 PQ: 0 ANSI: 4
[  206.043030] scsi 8:0:0:2: Enclosure         WD       SES Device       1030 PQ: 0 ANSI: 4
[  206.043663] sd 8:0:0:0: Attached scsi generic sg5 type 0
[  206.044884] sd 8:0:0:0: [sde] 1463775232 512-byte logical blocks: (749 GB/697 GiB)
[  206.046642] sd 8:0:0:0: [sde] Write Protect is off
[  206.046648] sd 8:0:0:0: [sde] Mode Sense: 23 00 10 00
[  206.046653] sd 8:0:0:0: [sde] Assuming drive cache: write through
[  206.049660] sd 8:0:0:0: [sde] Assuming drive cache: write through
[  206.049669]  sde: sde1
[  206.065909] sr1: scsi3-mmc drive: 51x/51x caddy
[  206.066075] sr 8:0:0:1: Attached scsi CD-ROM sr1
[  206.066173] sr 8:0:0:1: Attached scsi generic sg6 type 5
[  206.066304] scsi 8:0:0:2: Attached scsi generic sg7 type 13
[  206.074980] sd 8:0:0:0: [sde] Assuming drive cache: write through
[  206.074988] sd 8:0:0:0: [sde] Attached SCSI disk
[  206.117532] ses 8:0:0:2: Attached Enclosure device
[  206.916396] UDF-fs: Partition marked readonly; forcing readonly mount
[  206.916885] UDF-fs INFO UDF: Mounting volume 'WD SmartWare', timestamp 2009/10/14 23:49 (1078)
[  555.104302] __ratelimit: 6 callbacks suppressed
```

[/FONT]

---

### Post by Ares Drake on 2010-03-06
Quick-reading your long post I came to the impression you tried only copying files from your USB disk to the raid to check speeds? Maybe the problem is with reading from USB? You can check this simply with


Write on Raid: (will write 20GB, adjust count to your needs)
```
dd if=/dev/zero of=/some/path/on/your/raid/testfile bs=1G count=20
``` 

Read
```
dd if=/some/path/on/your/raid/testfile of=/dev/null
```


Delete testfile afterwards. If that gives you acceptable speed your raid is fine, but USB is the problem.

---

### Post by tgalati4 on 2010-03-06
Sounds quite possible that the USB controller is sharing an interrupt with the disk controllers or there is just a bottleneck in the motherboard/chipset design.

What is the output of:

cat /proc/interrupts

Try running some other benchmarks:

sudo apt-get install phoronix-test-suite

Info available at [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

---

### Post by NullHead on 2010-03-06
You could run a benchmark on each disk in the array to test the cache/buffer speeds. If they're low in comparison to other disks, you should run a s.m.a.r.t self test. ```
sudo hdparm -Tt /dev/sdx
```

And ```
suod smartctl --test=short /dev/sdx
```To read the results of the s.m.a.r.t tests, do ```
sudo smartctl -l selftest /dev/sdx
```

Your raid array will run as slow as your oldest disk, so if you have a single failing disk, the whole array will be slow. 

Correct me if I'm wrong.

---

### Post by ian dobson on 2010-03-06
Hi,

Could it be that your array is still rebuilding? Have a look at /proc/mdstat.

Regards
Ian Dobson

---

### Post by magogo200 on 2010-03-06
Thanks for the replies. My raid array is not rebuilding and the problem is not the USB bus. I get the same results when copying files from my laptop over a 1Gb/s ethernet connection (I use a dedicated NIC with a crossed cat5f cable).

hdparm stats on the physical drives return a write speed of 80-100MB/s. These are brand new WD Caviar Green 1.5TB drives. My OS is installed in a different partition on one of the drives and I don't have any performance issues with it. Both the OS partition and the raid array use an ext4 file system.

Also, it seems that almost every operation I do on the array gives bad performance. Even when I try to play a movie or a tv episode I get lags every few minutes. 'ls' takes 2-3 seconds to return any answers as well (in directories with 20-30 files in them!)

magogo.

---

### Post by tgalati4 on 2010-03-06
Perhaps the "green" drives are not meant for array architectures.  It's possible that the disk's firmware is going to sleep waiting for i/o (to save power) and that it's interfering with software RAID performance.

Your individual disk performance (via hdparm) is typical for new WD Cavier drives.

cat /proc/interrupts

See if you get a large number of interrupts on your bus.

---

### Post by NullHead on 2010-03-06
I've had five 9.1gb scsi drives from 1998 running in my old PIII Gateway 930 server, and even that old setup had better constant read/write speeds than that ... I could get 30-35 mb/s off that array. There's some serious issues here. 

The other thing you can do, is individually format and partition each drive and do a test on each of 'em.

I would recommend you wipe and return the drives and if possible get the [black series](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136284) drive. 

You might be able to get away with using LVM to span a partition across all the drives. This method doesn't offer any fault tolerance, but it would give you the space you bought the drives for.

---

### Post by magogo200 on 2010-03-06
[FONT=Courier New]Hello,

Here's what /proc/interrupts has to say:
           CPU0       CPU1       
  0:   12284442   12220898   IO-APIC-edge      timer
  1:          1          3   IO-APIC-edge      i8042
  4:          0          1   IO-APIC-edge    
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          5          1   IO-APIC-edge      i8042
 16:      18276      19629   IO-APIC-fasteoi   uhci_hcd:usb3, heci
 18:     640066     635560   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
 19:     330395     331993   IO-APIC-fasteoi   pata_jmicron, uhci_hcd:usb7
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:      40909      12804   IO-APIC-fasteoi   eth1, HDA Intel
 23:     492493     491346   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6, ohci1394
 27:     410141     419984   PCI-MSI-edge      ahci
 28:    1039139    1124842   PCI-MSI-edge      eth0
 29:      72074      71940   PCI-MSI-edge      i915
NMI:          0          0   Non-maskable interrupts
LOC:    5645264    4037700   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:    1258308    1071176   Rescheduling interrupts
CAL:      24465      15957   Function call interrupts
TLB:       6318       5494   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:        258        258   Machine check polls
ERR:          1
MIS:          0

I don't see anything special about it, but then again I'm not an expert. I did, however, run the smart tests several times now as suggested. It seems that sdc keeps returning a read error at 90%. The server is brand new so I still have the original warranty. I'll replace the drive with a new one and let the array rebuild itself. Hopefully that'll fix everything.

Thanks!
[/FONT]

---

### Post by tgalati4 on 2010-03-06
tgalati4@tpad-Gloria7 ~ $ cat /proc/interrupts
           CPU0       
  0:   13121733   IO-APIC-edge      timer
  1:      84612   IO-APIC-edge      i8042
  4:          8   IO-APIC-edge    
  7:          0   IO-APIC-edge      parport0
  8:          1   IO-APIC-edge      rtc0
  9:    7417565   IO-APIC-fasteoi   acpi
 12:   16728436   IO-APIC-edge      i8042
 14:     235087   IO-APIC-edge      ata_piix
 15:       1225   IO-APIC-edge      ata_piix
 16:     332935   IO-APIC-fasteoi   uhci_hcd:usb2, yenta, radeon@pci:0000:01:00.0, eth0
 17:          1   IO-APIC-fasteoi   uhci_hcd:usb3
 18:       2533   IO-APIC-fasteoi   uhci_hcd:usb4
 19:       3311   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5
 21:    4325097   IO-APIC-fasteoi   ipw2200
 22:    8056047   IO-APIC-fasteoi   Intel ICH6
NMI:          0   Non-maskable interrupts
LOC:   15459063   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0
tgalati4@tpad-Gloria7 ~ $ uptime
 16:22:40 up 10 days, 25 min,  5 users,  load average: 0.26, 0.31, 0.25

My thinkpad laptop has been up for 10 days and I have 0 rescheduling interrupts.  What is the uptime on your machine?  I noticed that you have a few:

RES: 1258308 1071176 Rescheduling interrupts

---

### Post by NullHead on 2010-03-06
jon@wopr:~$ cat /proc/interrupts
           CPU0       CPU1
  0:         29        993   IO-APIC-edge      timer
  1:          0          8   IO-APIC-edge      i8042
  7:          1          0   IO-APIC-edge      parport0
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          0        140   IO-APIC-edge      i8042
 14:        298     106870   IO-APIC-edge      pata_amd
 15:          0          0   IO-APIC-edge      pata_amd
 18:          0          3   IO-APIC-fasteoi   ohci1394
 20:          0        126   IO-APIC-fasteoi   ehci_hcd:usb1, HDA Intel
 21:          0          0   IO-APIC-fasteoi   sata_nv
 22:          0          0   IO-APIC-fasteoi   sata_nv
 23:      66455    4655542   IO-APIC-fasteoi   sata_nv, ohci_hcd:usb2
 29:     377315   87046382   PCI-MSI-edge      eth0
 30:     380505  104836713   PCI-MSI-edge      eth1
NMI:          0          0   Non-maskable interrupts
LOC:    3729019    2770793   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:   31065333    2281000   Rescheduling interrupts
CAL:         49         42   Function call interrupts
TLB:       1520       1261   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:        572        572   Machine check polls
ERR:          1
MIS:          0

As you can see from my own server, which, incidentally, also has a malfunctioning 500gb hdd, not in a raid setup, with quite a few "reschedulint interrupts". I will be replacing it soon. 

```
jon@wopr:~$ sudo smartctl -l selftest /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       10%      8725         939251328
# 2  Short offline       Completed without error       00%      8701         -
# 3  Short offline       Completed without error       00%      8701         -
# 4  Extended offline    Completed: read failure       10%      5113         939251328
# 5  Short offline       Completed without error       00%      5111         -
# 6  Short offline       Completed without error       00%      4688         -
# 7  Short offline       Completed without error       00%      4688         -
# 8  Short offline       Completed: read failure       90%      3829         939251328
# 9  Short offline       Completed: read failure       90%      3775         939251328
#10  Extended offline    Completed: read failure       90%      3774         939251328
#11  Short offline       Completed: read failure       10%      3774         939251328
#12  Short offline       Completed: read failure       90%      3774         939251328
#13  Short offline       Completed: read failure       90%      3774         939251328
#14  Short offline       Completed: read failure       90%      3774         939251328
```

---

### Post by Ares Drake on 2010-03-07
Maybe it is indeed the faulty drive causing the pain. [http://en.wikipedia.org/wiki/Time-Limited_Error_Recovery](http://en.wikipedia.org/wiki/Time-Limited_Error_Recovery) suggest that without propper TLER settings disk failures could slow down the entire raid.

---

### Post by tgalati4 on 2010-03-07
That link confirms my suspicion that WD Green drives are for consumers not enterprise use--therefore may not work well in RAID use.  Send an email to WD to confirm.

---

### Post by xianthax on 2010-03-23
I have a similar issue.

I'm using 8 x 1.5TB WD Green's in a mdadm RAID6 setup.  For several months it has been performing perfectly but as it has started to fill up i'm having, i think, the same problem you are.  By fill up i mean its like 20% full if that.  It is also formatted as ext4.

In my case during write operations the array will stall with 1 of 2 drives having its activity light locked on for 30 seconds or a minutes.  This seems completely random, some times i can copy 5GB without seeing it happen, some times a torrent writing at 500kb/sec will trigger it.  It always to the same drives.  During this time the entire system crawls to a halt and shows almost 100% cpu wait time in some cases i can't even ssh into the system during this time.

I run weekly long smart tests on all drives, all are clear.

I have no errors in any logs.

The TLER issue is a response time problem that can cause a raid controller to drop a drive from the array forcing a resync, i have no indication this is occurring.  If this were the issue i would expect to see errors from mdadm indicating communication failure or array out of sync.  Generally this is only an issue with hardware raid controllers never seen it have any impact on software raid.

I'm a bit baffled by it, originally i thought it was a controller issue as the 2 drives in question were on the same controller, i moved both to a different controller and the problem continued.

My next thought was a bad interaction between ext4 and the array but i've tried various mount parameters and found no change.  I'm still exploring this possibility.

I'm not sure what rescheduling interrupts have to do with this issue.  My understanding of rescheduling interrupts is a situation where the scheduler has decided to move work from one core to another sleeping core, if you have a system with speedstep or similar technology, multiple cores and an intermittent cpu load i would expect to see a lot of these.  For a system with 1 core i would expect this value to be much lower or 0.

---

### Post by jrssystemsnet on 2010-03-23
> **xianthax said:**
> I'm using 8 x 1.5TB WD Green's in a mdadm RAID6 setup.

"Green" drives are NOT for use in RAID arrays.  Sorry, as I know it's a little late to tell you that *now*, but... they're not. =\

---

### Post by xianthax on 2010-03-23
> **jrssystemsnet said:**
> "Green" drives are NOT for use in RAID arrays.  Sorry, as I know it's a little late to tell you that *now*, but... they're not. =\

While your tone is entertaining you've provided no technical reason at all for the issue at hand nor any reason not to use a low power drive in a long term storage pool.  

The only known issue is TLER which is only applicable to hardware raid controllers with short time out periods.

---

### Post by wazham on 2010-03-23
Sounds familiar. See here: [http://ubuntuforums.org/showthread.php?t=1328112](http://ubuntuforums.org/showthread.php?t=1328112)

[There]("http://ubuntuforums.org/showpost.php?p=8662914&postcount=8"), sicn says:

> **sicn said:**
> I am afraid you are out of luck. I tried my best to mitigate the problem by all possible and impossible settings (BIOS, Linux, jumpers), however, in the end I gave up.

I sent an e-mail to Western Digital and gave them a very detailed description of the problem to which they simply answered "We just support Windows".

The WD disks are now electronic waste on some landfill and I bought Samsung instead, they work perfectly. :D


... so it may indeed be an inherent Caviar Green problem. I'll not be buying any more of those then, but how are the Black Caviars better? WD still aren't going to support them in Linux I presume?

---

### Post by capscrew on 2010-03-23
> **wazham said:**
> 
... so it may indeed be an inherent Caviar Green problem. I'll not be buying any more of those then, but how are the Black Caviars better? WD still aren't going to support them in Linux I presume?

You are trying to use a desktop (home use) drive for RAID and they are just not designed for that.  Black, Green it doesn't matter.  Use an enterprise class drive with RAID use in the design.  See [**_here _**]("http://www.wdc.com/en/products/Products.asp?DriveID=732")for and example of a WD RE drive.

---

### Post by KB1JWQ on 2010-03-23
...not to mention that software (or really any) RAID5 isn't going to be pleasant on throughput; those parity calculations take up some rather hefty resources.

I prefer RAID1 or 10.

---

### Post by capscrew on 2010-03-23
> **KB1JWQ said:**
> ...not to mention that software (or really any) RAID5 isn't going to be pleasant on throughput; those parity calculations take up some rather hefty resources.

I prefer RAID1 or 10.
When used with hardware adapters the load is carried by the adapter rather than the OS.  At work we have the drive arrays in separate enclosures independent of the OS box.  Better for cooling and noise suppression.

I can't see a need for RAID at home anyway.  If you need RAID then you need a separate room for you hardware or a datacenter arrangement.


I'm not a big believer in software RAID in any form.  RAID is an enterprise tool that is coming to an end with high aural density drives.  The move will be to BtrFS on Linux based systems in the next few years.  See [**_here for the reasons why_**]("http://blogs.zdnet.com/storage/?p=162").

---

### Post by KB1JWQ on 2010-03-24
> **capscrew said:**
> 

I can't see a need for RAID at home anyway.  If you need RAID then you need a separate room for you hardware or a datacenter arrangement.


Maybe because drives are still unreliable compared to other components?  Moving parts break down, and people care about their data.  It's not a backup,but it keeps a dead drive from being a show stopper in the short term.

---

### Post by capscrew on 2010-03-24
> **KB1JWQ said:**
> Maybe because drives are still unreliable compared to other components?  Moving parts break down, and people care about their data.  It's not a backup,but it keeps a dead drive from being a show stopper in the short term.

If you loose a drive in a RAID array using 1TB or larger drives it is a show stopper already.  The errors are catastrophic.  The rebuild time would be excessive.  This is really the driver for improved, self healing file systems like Sun's ZFS and the new Linux [**_BtrFS _**]("http://linuxupdate.blogspot.com/2009/01/btrfs-next-generation-file-system-for.html").

As you say.  If the data is important, back it up.  Saving data is not the same as High availability.

---

### Post by jrssystemsnet on 2010-03-24
> **KB1JWQ said:**
> ...not to mention that software (or really any) RAID5 isn't going to be pleasant on throughput; those parity calculations take up some rather hefty resources.

This is just not true.

[img]http://virtual.tehinterweb.net/livejournal/2009-06-22_zfs_diskperf/zfs-diskperf-5MB-readwrite.png[/img]

See that bright orange line spanking everything else on the graph?  That's mdraid5.  See the red line beating everything else on the graph *except* mdraid5?  That's RAIDZ, which is essentially RAID5 with variable stripe width and per-member checksums as well as per-stripe parity.

Don't get too hung up on the raw numbers; keep in mind that as the label on the tin says, this is measuring a mixed load of concurrent random-access reads and random-access writes, NOT the typical "fastest-contiguous-read-possible" number you see on brag sheets (which would be a heck of a lot higher, but a heck of a lot less usefull as a metric).

RAID5 certainly isn't perfect, but "calculating parity" isn't the source of what performance problems it tends to face (which mostly center around loads weighted heavily towards small random access writes), and offloading parity calculation to hardware very definitely isn't the solution to them (Linux mdraid5 is faster than every hardware solution I've ever tested, including some fairly expensive 3ware products, complete with onboard BBU).

---

### Post by jrssystemsnet on 2010-03-24
If you're interested, this is what happens if you drop the chunk size to 1MB.

[img]http://virtual.tehinterweb.net/livejournal/2009-06-22_zfs_diskperf/zfs-diskperf-1MB-readwrite.png[/img]

Small reads and writes (128k and below), incidentally, are roughly the same (appallingly low, by comparison) speed regardless of what type of RAID array you have, or whether you have one at all.  If you want to speed up small operations, you have to leave conventional hard drives behind altogether, either by moving to SSD or by figuring out a way to serve them from cache hits instead of from the underlying hardware.

---

### Post by NullHead on 2010-03-24
Where are you getting these test results from? They're quite impressive. 

I'm not much of a raid guru, but my old raid5 setup with 10 year old 9.1gb scsi hdds wasn't too shabby (I retired the server last year).

---

### Post by jrssystemsnet on 2010-03-24
> **NullHead said:**
> Where are you getting these test results from? They're quite impressive. 

I'm not much of a raid guru, but my old raid5 setup with 10 year old 9.1gb scsi hdds wasn't too shabby (I retired the server last year).Those are test results I generated personally, using a perl script to do exactly what the labeling on the charts says is being done.  (Data is moved from /dev/zero in write operations, and being dumped to /dev/null in read operations; further, several gigabytes of random unrelated data was read out before each test in order to minimize the effect of filesystem caching as much as possible.)

They're part of a couple of full write-ups I did last year testing ZFS performance specifically; mdraid5 is being used as a benchmark to show where ZFS fits on the scale.

> Hardware used:
AMD Athlon 64+ 3500
2GB DDR2 SDRAM
1 WD 250GB HDD (operating system)
5 Seagate Barracuda 750GB SATA-II HDD (RAID array drives)

Operating systems used:
FreeBSD 7.2-RELEASE amd64 (UFS2 and ZFS testing)
Ubuntu Server 8.04-LTS amd64 (ext3fs testing)

Note that those Barracudas are absolute freaking PIGS - Western Digital RE drives of similar sizes are twice as fast, and in some cases faster, which is why I said not to get too hung up on the raw numbers.  The idea when I was generating these was to compare the performance of various data *architectures*, not to compare the raw single-drive hardware underneath it.

There aren't any numbers shown on those graphs for hardware controllers, but I benchmarked an Areca 8-port PCIe x4 controller and a 3Ware Escalade PCIe x4 controller in other tests a few months before those, and Linux mdraid handily (brutally, even) spanked them both for every possible array configuration that could be done in either hardware RAID or mdraid.  True hardware raid performs much better than "fakeraid" from cheap controllers, but the idea that it outperforms mdraid is a complete myth that people just keep passing along blindly because it sounds reasonable to them.

I defy anybody to actually *test* mdraid5 versus any hardware raid5, with the rest of the hardware and system remaining the same, and come up with better performance from the hardware.

---

### Post by KB1JWQ on 2010-03-24
Two points.
First, I'd be very curious to see how those raid5 numbers look compared to a RAID10 graph.

Secondly, 1TB disks (and higher!) have reduced problems in RAID1 or 10 configurations due to the fact that there isn't a "rebuild" that's anything other than "Dump the entire contents of its counterpart to itself."  Goes relatively quickly these days...

RAID certainly isn't a panacea, but it helps.

---

### Post by jrssystemsnet on 2010-03-24
> **KB1JWQ said:**
> Two points.
First, I'd be very curious to see how those raid5 numbers look compared to a RAID10 graph.mdraid10, or hardware raid10?  Because the answers are very, VERY different. :)

In extremely vague terms, if we're talking about mdraid10, performance is generally similar on reads, with mdraid10's performance in relation to mdraid5 increasing the more concurrent processes and/or the smaller the chunks.  Performance on writes is better for mdraid10 for heavily-saturated small-write loads, better for mdraid5 for lightly-saturated large-write loads.

Being even more vague, mdraid10 is generally a better performer than mdraid5 if you have to put things in uber-simplistic "which one is better" terms, but raid10 offers half the storage capacity on the same hardware as raid5, so you have to be able to afford that sacrifice.

In the real world, if you want to get the most out of your budget, you need to have an actual understanding of the load you're going to put on your server and design around that, not just start out with "what's best" and work from there - because there *is* no single "what's best" answer for all servers.

> Secondly, 1TB disks (and higher!) have reduced problems in RAID1 or 10 configurations due to the fact that there isn't a "rebuild" that's anything other than "Dump the entire contents of its counterpart to itself."This is, for the most part, true.  I say "for the most part" because the parity calculation isn't really the issue with slow RAID5 rebuilds; the issue is the way degraded-mode reads and writes have to happen for RAID5.

---

### Post by xianthax on 2010-03-24
Solved my problem.

The WD Green drives use 4k sectors, you should align your partitions on 4k boundaries.  

The issue is that for compatibility reasons the drive presents itself as a 512 byte sector drive.  The problem is that if you use a file system that uses 4k blocks, such as ext3/4 normally do without aligning the partition to 4k blocks every time you write to disk the drive controller has to read a 4k sector, modify part of it, and write it back to disk, this is very slow.  The same will be true of raid configurations on the disk as stripe size is almost always a multiple of 4k.

You can google for the issue but not aligning the partition can have a 2x to 3x write performance penalty. 

To fix this make sure all your raid partitions are aligned to 4k blocks.  Assuming your using a single partition for each drive just tell fdisk to start the partition at sector 64 instead of the default 63.  Use fdisk -u /dev/sdx to get fdisk to report units in sectors.

Secondly when you format the drive make sure you are handing in proper values to the stride and stripe-width options.  

Stride should be the raid stripe size/file_system_block_size.  For me i use a 4k block size and 128k stripes so stride=128k/4k=32.

This allows the file system to layout metadata/journals such that one drive in the array isn't getting excessive work compared to others.  This seems to be more of an issue on odd size arrays like mine.  By odd size i means when the number of data drives isn't a power of 2.

stripe-width should be set to the # of data drives * stride.  This allows the allocator to optimize itself among other things.  For me this is 32 * 6.  Remember its the number of data drives not the total number of drives, so for RAID6 this is total number of drives - 2 for raid 5 its total number of drives - 1.

So my format command was:

mkfs.ext4 -c -b 4096 -E stride=32,stripe-width=192 -O extent -v /dev/md0

For comparison i have a 3ware 9550 4 port raid card with 4 x WD RE 320GB drives in RAID5 64kb chunks in my system as well, this array gets ~130MB/sec sustained write speed with ext4.

The software RAID6 array now sustains 75mb/sec writes and reads are around 425mb/sec from hdparm which more than saturates the 2 bonded gigabit network links the system has.  Plenty fast enough for me.  Similar setups on a hardware controller seem to see more like 650mb/sec reads but for use as NAS this is of little benefit.

My issue i believe was a combination of not setting the stride correctly when formating the array and not aligning the partitions correctly, as a result some of the drives where getting hammered with meta-data/journal work and since write performance was already crippled by the misaligned partitions it caused the array to grind to a halt.

As to all the complaining about using green drives in raid arrays, thats just silly.  They are exactly what i need for long term redundant network storage.  If your looking to build the fastest possible storage, yea you should be using a hardware controller with TLER drives, probably not using raid5/6 and using an battery backed nvram card as an external journal.  

If you want a high capacity redundant storage location then RAID5/6 with low power, cool running drives is perfect.  They provide enough speed to saturate the network on reads and write fast enough to not be an issue for backup applications while also running cool, quiet and with minimal power. 

Ideally i would have rather ran ZFS with RAID-Z pools but the linux support isn't there in a way i'm confident about, and btfs isn't even close to ready.

---

### Post by jrssystemsnet on 2010-03-24
> **xianthax said:**
> The issue is that for compatibility reasons the drive presents itself as a 512 byte sector drive.  The problem is that if you use a file system that uses 4k blocks, such as ext3/4 normally do without aligning the partition to 4k blocks every time you write to disk the drive controller has to read a 4k sector, modify part of it, and write it back to diskOhhhhh... man, I didn't even think of alignment issues.  Unnecessary read-modify-write fandango.

Thank you for posting your fix, once you'd found it. :)

---

### Post by capscrew on 2010-03-24
> **xianthax said:**
> Solved my problem.

The WD Green drives use 4k sectors, you should align your partitions on 4k boundaries.  

The issue is that for compatibility reasons the drive presents itself as a 512 byte sector drive...
As of January this is not so.  See [**_here_**]("http://blogs.zdnet.com/storage/?p=731") for more information.  

Is it possible you are using earlier drives?

Edit:  These later drives no longer translate back to 512 byte sectors.

---

### Post by xianthax on 2010-03-24
> **capscrew said:**
> 

Is it possible you are using earlier drives?



The drives were purchased in Nov 2009.  Unfortunately at that time the issues with the 4k sector change wasn't as widely discussed as it appears to be now.

As a side note that jumper on the back/their little software app just tricks the controller into increasing the sector by 1 so when the OS sends a write to sector 63 the drive internally bumps its to 64.  

Can't imagine such a hack ending badly :popcorn:

EDIT: just to confirm, yes all 8 drives claim to have 512 byte sectors.

---

### Post by capscrew on 2010-03-24
> **xianthax said:**
> The drives were purchased in Nov 2009.  Unfortunately at that time the issues with the 4k sector change wasn't as widely discussed as it appears to be now.

As a side note that jumper on the back/their little software app just tricks the controller into increasing the sector by 1 so when the OS sends a write to sector 63 the drive internally bumps its to 64.  

Can't imagine such a hack ending badly :popcorn:

EDIT: just to confirm, yes all 8 drives claim to have 512 byte sectors.

It is indeed unfortunate that even the best of us end up in the dark when manufactures play the "I need to sell the old stock" game.  I have always used WD and feel bad that they don't properly explain what their future plans are.

My brother just purchased 3 WD Green drives for his office.  He could have used the latest version, but knew nothing about the change.

There are various hacks for Linux/ZFS. [**_[COLOR="DarkGreen"]Nextenta [/COLOR]_**]("http://www.nexenta.org/")comes to mind.  ZFS and BtrFS are the future for large data stores.  Maybe next year if Chris Mason has the time work out the bugs.  I understand Lucid will have BtrFS as a filesystem type.  I plan on testing it out.

---

### Post by jrssystemsnet on 2010-03-25
> **xianthax said:**
> To fix this make sure all your raid partitions are aligned to 4k blocks.  Assuming your using a single partition for each drive just tell fdisk to start the partition at sector 64 instead of the default 63.  Use fdisk -u /dev/sdx to get fdisk to report units in sectors.Hey xianthax, do you mind giving a sample set of commands telling fdisk to create a partition starting at sector 64?

---

### Post by NullHead on 2010-03-25
I believe when you're creating a partition with fdisk, it asks you where you'd like to make the partition start and end at.

---

### Post by capscrew on 2010-03-25
> **NullHead said:**
> I believe when you're creating a partition with fdisk, it asks you where you'd like to make the partition start and end at.

This is all being worked out as we speak.  See [**_here_**]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/530071") for the comments by the Lucid dev's and Ted Tso (the ext4 maintaner).

---

### Post by xianthax on 2010-03-25
> **jrssystemsnet said:**
> Hey xianthax, do you mind giving a sample set of commands telling fdisk to create a partition starting at sector 64?

fdisk -u /dev/sdx      <--- -u causes fdisk to report units in sectors, i believe the default is cylinders, this is probably the only trick you need.

When it asks you where to start the partition (default 63), just enter 64.  Answer the rest of the questions as usual.

You would need to be more careful, and likely grab a calculator, if you are putting multiple partitions on a drive as you want all of them to be aligned.  I believe the newest versions of fdisk and parted can do this automatically, not sure.

As a side note i did some more tuning, the mount line from my fstab is:

/dev/md0 /mnt/storage ext4 noatime,errors=remount-ro,barrier=0,data=writeback,nobh,commit=600 0 1

Be warned that some of these options delay writing and journaling and if your system is not on a solid UPS with automatic shutdown you should take a good hard look at these options as it can cause data loss if the power is randomly cut.

The end result was a big improvement in write speed.

I copied ~49,000 files, 835GB total to the array, ~500 of the files were between 500mb and 10GB, the rest were mostly smaller (think images, music, multiple git and svn trees)

The large files sustained 130-135MB/sec writing, the smaller files dropped down to around 90-100MB/sec.  All in all I'm very happy with that performance for my needs.

I'm currently doing a test rebuild by forcing a drive out of the array and its been sustaining 50MB/sec rebuild speed through the first 25%.

I have one more test i want to try out.  I still see 1 or 2 drives getting smacked harder than the others in the array, its noticeable in the drive activity lights and seems to sink up with iotop reporting writes from kjournald.  I'm debating putting a small partition on the 3ware array to store the journal for the mdadm array and see what performance impact that has.  This is mostly academic but will be interesting.  Given the commit time of 10min i've set i doubt it will have much impact.


For reference the system consists of:

Supermicro 743 series chassis, 13 hot swap bays across 2 backplanes.  650W power supply, all drives have staggered spin up.
Asus P5E WS Professional (motherboard)
Intel Q6600 CPU as stock clock speed
4GB ram
Ubuntu 9.04 64bit using the server kernel
3ware 9550SX PCI-X controller, 4 WD RE 320GB drives, raid5
WD 150GB Raptor with boot/root partition and swap space on it
8 x 1.5TB WD Green drives, mdadm RAID6 128k chunks

The mdadm raid drives are all attached to the motherboard, 6 via the southbridge and 2 via an extra marvell SATA controller on the motherboard, the boot drive is attached to a Silicon Image based 2 port SATA card in a PCI express slot.

Hopefully this provides some baseline for the OP as to what he can expect from a setup with these drives.

---

### Post by jrssystemsnet on 2010-03-25
Thanks, I really appreciate the detailed information!  I like to set up and viciously benchmark various different RAID setups from time to time, also - I last did that last year, which you can see a couple of the graphs from up there. 

I'm doing another benchmarking run with a Core 2 Quad box, 8GB RAM, 6x 1TB WD Caviar Black; I will be testing RAIDZ, mdraid5, mdraid10, single drive (for reference), and single drive Intel X25-M SSD (for demonstrating that RAID doesn't really help much with small reads and writes, but an SSD certainly does).

I'm most of the way through the ZFS benchmarking now, tomorrow I should be tearing it down and setting it up on Ubuntu for mdraid5, mdraid10, single drive, and single SSD.  Fun stuff.

---

### Post by jrssystemsnet on 2010-03-25
Incidentally, my benchmarks are mixed read/write load, weighted toward reads - currently I'm testing random access reads at 5M, 1M, 512K, 128K, and 16K chunk sizes, with concurrent trickle writes at 16K 10x per sec, 16K 100x per sec, and 1M 5x per sec.  I do tests with 1 to 5 concurrent read processes.

So right now my tables look something like this:

```

                         5MB read chunk          1MB read chunk
                       1   2   3   4   5   |   1   2   3   4   5 
1M write 5 per sec     26  28  27  29  28  |   71  69  66  64  61
16K write 10 per sec   28  30  27  28  28  |   70  63  61  60  56
16K write 100 per sec  27  28  25  27  28  |   68  64  62  62  57

```

... you get the idea.

As you can see, the ZFS doesn't seem real sensitive to much of anything except the read chunk size - it parcels out small writes extremely effectively, to the point that there isn't much difference between 5 1MB writes per second and 100 16K writes per second!

(Incidentally, a write operation is appending the named size of data in zeroes to the end of one of ten files.  Each write is targeted to one of the ten files at random.)

Oh - and the raw numbers are seconds to complete reading 5GB total of data.  So "26" corresponds to 5120MB / 26 secs = 197MB/sec.

---

### Post by smc18 on 2010-03-25
Xianthax, jrssystemsnet, and capscrew... you three amaze me!!

This was an excellent read and it proves that I will have to continue studying for the rest of my life.  :KS

---

### Post by NullHead on 2010-03-25
> **jrssystemsnet said:**
> Incidentally, my benchmarks are mixed read/write load, weighted toward reads - currently I'm testing random access reads at 5M, 1M, 512K, 128K, and 16K chunk sizes, with concurrent trickle writes at 16K 10x per sec, 16K 100x per sec, and 1M 5x per sec.  I do tests with 1 to 5 concurrent read processes.

So right now my tables look something like this:

```

                         5MB read chunk          1MB read chunk
                       1   2   3   4   5   |   1   2   3   4   5 
1M write 5 per sec     26  28  27  29  28  |   71  69  66  64  61
16K write 10 per sec   28  30  27  28  28  |   70  63  61  60  56
16K write 100 per sec  27  28  25  27  28  |   68  64  62  62  57

```

... you get the idea.

As you can see, the ZFS doesn't seem real sensitive to much of anything except the read chunk size - it parcels out small writes extremely effectively, to the point that there isn't much difference between 5 1MB writes per second and 100 16K writes per second!

(Incidentally, a write operation is appending the named size of data in zeroes to the end of one of ten files.  Each write is targeted to one of the ten files at random.)

Oh - and the raw numbers are seconds to complete reading 5GB total of data.  So "26" corresponds to 5120MB / 26 secs = 197MB/sec.

> **smc18 said:**
> Xianthax, jrssystemsnet, and capscrew... you three amaze me!!

This was an excellent read and it proves that I will have to continue studying for the rest of my life.  :KS

Indeed, this thread in a very interesting read! 

jrssystemsnet, you simply must publish all your results to a blog/here/somewhere on the net. I find your testing quite interesting. 

Granted, I'm not much of a raid connesuir, but I am quite intrigued by the concept and I really do love seeing benchmarks on the subject.

---

### Post by jrssystemsnet on 2010-03-27
Finished the ZFS testing (RAIDZ, single 1TB Caviar Black, and single Intel X-25M SSD).  Moving on to the ext4/mdadm testing now.

Xianthax, after some very frustrating trial and error, I found what seems so far to be a much better way of handling partition alignment over at Ted Tso's blog.  Check this out:

> However, with SSD&#8217;s (remember SSD&#8217;s?  This is a blog post about SSD&#8217;s&#8230;) you need to align partitions on at least 128k boundaries for maximum efficiency.  
The best way to do this that I&#8217;ve found is to use 224 (32*7) heads and 56 (8*7) sectors/track.  This results in 12544 (or 256*49) sectors/cylinder, so 
that each cylinder is 49*128k.  You can do this by doing starting fdisk with the following options when first partitioning the SSD:

# fdisk -H 224 -S 56 /dev/sdb


Done this way, no calculators are necessary, everything "just works" - your first partition is aligned on a 4K boundary, and any remaining contiguous partitions will be aligned on 128k boundaries.  The only drawback, if you can call it that, is that when you specify a "100G" partition you're more likely to get a "100.1G" partition.  I can deal with that, in exchange for no more issues with creating partition tables that the BIOS can't understand and won't boot! :)

I'll be back later with the full set of benchmarks; I still need to test:

* ext4 on single WD Caviar Black 1TB
* ext4 on Intel X-25M SSD
* ext4 on mdadm RAID5 6x WD Caviar Black 1TB
* ext4 on mdadm RAID10 6x WD Caviar Black 1TB

Fun fun fun. :)

---

### Post by xianthax on 2010-03-27
If your interested i can run your test script on my setups for extra data points.

I could test the previously mentioned 3ware and software raid's as well as a single WD raptor that in my file server.  Also my workstation runs off 2 OCZ Agility 60GB SSD's in mdadm raid0 if that would be of interest.  All except the raptor are ext4, the raptor is ext3.

---

### Post by jrssystemsnet on 2010-03-27
Sure, I'll be happy to share the scripts... a word of warning, though, they are dirty, primitive, and unkempt, much like their creator. =)

Seriously, they're nowhere NEAR as sophisticated as something like Bonnie++... but that's kinda deliberate; my main interest is in modeling the I/O load of fileservers, so I went about crudely hacking together something that would do that.

The way I go about it tends to minimize the impact of readahead caching without completely throwing it away; of course this isn't very scientific but again it suits me fine, as really what I'm mostly looking at is "fileserver on a bad day"... which tends to translate to "minimal use of caching", but not "*no* use of caching."

Let me finish up this benchmarking run and I'll dump a tarball and instructions somewhere, along with some nice pretty graphs from my stuff.

---

### Post by jrssystemsnet on 2010-03-28
Benchmarks are finished and available in a new [thread](http://ubuntuforums.org/showthread.php?p=9039994#post9039994). :popcorn:

---

### Post by laluz on 2010-05-12
Hi there,
I believe I have the same problem with the 512 block drive. So I have decided to repartition my drives in the array using fdisk -H 224 -S 56. Also I reckoned, it is not necessary to recreate an array. One could add a new correctly partitioned drive to the array, fail one old disk, remove and repartition it. Then repeat. Is that correct?


My problem is, the drive partitioned with fdisk -H 224 -S 56 has less space available. So the mdadm refuses to add it to the array. 
> cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid6 sdf1[4] sdb1[0] sde1[3] sdc1[2] sdd1[1]
      4395407808 blocks level 6, 64k chunk, algorithm 2 [5/5] [UUUUU]
      bitmap: 0/175 pages [0KB], 4096KB chunk


> sudo mdadm /dev/md0 -a /dev/sdg1
mdadm: /dev/sdg1 not large enough to join array
cat /proc/partitions 
major minor  #blocks  name

   8        0   31266648 sda
   8        1   31265792 sda1
   8       16 1465138584 sdb
   8       17 1465136001 sdb1
   8       32 1465138584 sdc
   8       33 1465136001 sdc1
   8       48 1465138584 sdd
   8       49 1465136001 sdd1
   8       64 1465138584 sde
   8       65 1465136001 sde1
   8       80 1465138584 sdf
   8       81 1465136001 sdf1
   8       96 1465138584 sdg
   8       97 1465132800 sdg1
   9        0 4395407808 md0
   8      112 1953514584 sdh
   8      113 1953512001 sdh1
   8      128    7929856 sdi
   8      129      96264 sdi1
   8      130    7807590 sdi2

I have tried to shrink the array but there is a problem with the superblock then as it is written at the end of the disk. 
> sudo mdadm --grow /dev/md0 --bitmap none
sudo mdadm --grow /dev/md0 --size 1465132800 --backup-file=/home/USER/raid.bak
sudo mdadm --wait /dev/md0
sudo mdadm --grow /dev/md0 --bitmap internal
> sudo fsck.jfs -v /dev/md0
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 5/13/2010 0.41.20
Using default parameter: -p
The current device is:  /dev/md0
Open(...READ/WRITE EXCLUSIVE...) returned rc = 0
Incorrect jlog length detected in the superblock (P).
Incorrect jlog length detected in the superblock (S).
Superblock is corrupt and cannot be repaired 
since both primary and secondary copies are corrupt.  


Is there a way to shrink (not grow) an array _without_removing_ drives and keep the filesystem (and files) on it?

below a few links, that are relevant, but did not help however.
[https://raid.wiki.kernel.org/index.php/Growing](https://raid.wiki.kernel.org/index.php/Growing)
[http://www.novell.com/documentation/sles10/stor_evms/data/resizeincr.html#resizeincrpart](http://www.novell.com/documentation/sles10/stor_evms/data/resizeincr.html#resizeincrpart)
[http://www.issociate.de/board/post/395470/Shrinking_a_RAID1--superblock_problems.html](http://www.issociate.de/board/post/395470/Shrinking_a_RAID1--superblock_problems.html)

---

### Post by laluz on 2010-05-14
> **laluz said:**
> Hi there,

Is there a way to shrink (not grow) an array _without_removing_ drives and keep the filesystem (and files) on it?



I supposed that the file-system can be shrinked and it seems that's not the case with the JFS. So please disregard the above question, there is no problem with the array, it is the file-system.

---

