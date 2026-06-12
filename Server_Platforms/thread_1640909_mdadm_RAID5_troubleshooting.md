---
title: "mdadm RAID5 troubleshooting"
date: 2010-12-08
forum: Server Platforms
---

### Post by Snowjoggs on 2010-12-08
Hi

I've had a 4x1TB setup for while and its been humming along nicely, I recently added another 1TB disk and all was fine for some weeks.

Then the raid started to become sluggish, even unresponsive some times.
I suspect either the old VIA sata controller PCI card not handling the additional drive, or a bad SATA cable.

At my attempts to troubleshoot I seem to have done more harm than done, as it would not return from a reboot I had to shut it down forcibly (mind you the server is in the basement with no monitor :S)

It's resyncing right now, I just hope it won't fail again.

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[0] sdg1[5] sdf1[4] sde1[3] sdd1[2] sdc1[1]
      4883799680 blocks level 5, 64k chunk, algorithm 2 [6/6] [UUUUUU]
      [>....................]  resync =  1.5% (15314560/976759936) finish=826.3min speed=19392K/sec

unused devices: <none>
```How should I go about troubleshooting this properly to determine if its a faulty cable, the VIA card or something else, and how to identify which drive is causing the issues?
I was also thinking I should replace the older VIA sata PCI controller with a newer one, with Silicon Image chip. Will this cause an issue for my RAID or is it no problem to swap the hardware controller in a software RAID?

I'm new to linux/mdadm so my knowledge is limited, but I'm learning :)

---

### Post by rubylaser on 2010-12-08
I'd start off by using smartmontools on each of my hard drives to make sure that they each pass a SMART test.  Also, does your power supply put out enough power on one rail to power 6 hard drives?

Finally, you can certainly change out the controller.  That's part of the flexibility of mdadm.  You could throw those disks in a new machine, and still mount the array just fine.

---

### Post by Snowjoggs on 2010-12-09
Thanks for the suggestions, Ill try SMART tools when I get back home.

The PSU powering the box at the moment is a 300w fanless one, 6x20w = 120w so I should I have plenty to go on as the rest of the box components are not sucking that much power (non clocked celeron, only 2 fans etc).

I also ruled this out by hooking up half of the drives to an external PSU, the issue was the same.

---

### Post by Snowjoggs on 2011-01-09
Well SMART tools didn't detect errors of any of the drives.

I brought the box back up to the apartment to be able to troubleshoot some more.

I was able to make the box freeze again by generating alot of IO traffic on the disks (downloading, moving & copying several data at once) 

This time I had a monitor hooked up and the error I got was: soft lockup cpu#0 stuck for 61s

Any ideas?

---

### Post by rubylaser on 2011-01-10
Another option could be the the drives are falling out of the array.  Have you disabled NCQing on the drives?  And, what type of hard drives are they? And, what does the load look like on the machine?

---

### Post by Snowjoggs on 2011-01-11
> **rubylaser said:**
> Another option could be the the drives are falling out of the array.  Have you disabled NCQing on the drives?  And, what type of hard drives are they? And, what does the load look like on the machine?

Seems like I made it worse in my troubleshooting.
Each time it died I had to allow it to resync, now its become very unstable.

I am currently unable to start it at all

```
root@enterprise:~# mdadm --assemble --scan /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 4 drives and 1 spare - not enough to start the array.
```I am able to bring it back into resyncing with all devices if I reboot a couple of times and fiddle about. The result will always be that all 6 drives are OK "[UUUUUU]". Until the next crash ofcourse ;)

My harddrives are as follows

```

SDB
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EARS-00Y5B1
Serial Number:    WD-WMAV51428508
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes

SDC
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EARS-00Y5B1
Serial Number:    WD-WMAV51466805
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes

SDD
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EARS-00Y5B1
Serial Number:    WD-WMAV51430840
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes

SDE
=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HDT721010SLA360
Serial Number:    STF607MH3EBDMK
Firmware Version: ST6OA31B
User Capacity:    1,000,204,886,016 bytes

SDF
=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD103UJ
Serial Number:    S13PJ90S511656
Firmware Version: 1AA01118
User Capacity:    1,000,204,886,016 bytes

SDG
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EARS-00Y5B1
Serial Number:    WD-WCAV5F224088
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes

```DMESG output
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-27-server (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #49-Ubuntu SMP Thu Dec 2 02:05:21 UTC 2010 (Ubuntu 2.6.32-27.49-server 2.6.32.26+drm33.12)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.32-27-server root=/dev/mapper/enterprise-root ro quiet
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f5e0000 (usable)
[    0.000000]  BIOS-e820: 000000003f5e0000 - 000000003f5e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5e3000 - 000000003f5f0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5f0000 - 000000003f600000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3f5e0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CAFFF write-protect
[    0.000000]   CB000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   3 base 03F600000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f5e0000 (usable)
[    0.000000]  modified: 000000003f5e0000 - 000000003f5e3000 (ACPI NVS)
[    0.000000]  modified: 000000003f5e3000 - 000000003f5f0000 (ACPI data)
[    0.000000]  modified: 000000003f5f0000 - 000000003f600000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000003f5e0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 003f400000 page 2M
[    0.000000]  003f400000 - 003f5e0000 page 4k
[    0.000000] kernel direct mapping tables up to 3f5e0000 @ 8000-b000
[    0.000000] RAMDISK: 2efbe000 - 2f8a73ea
[    0.000000] ACPI: RSDP 00000000000f6c20 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 000000003f5e3040 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 000000003f5e30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 000000003f5e3180 040E8 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 000000003f5e0000 00040
[    0.000000] ACPI: HPET 000000003f5e73c0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 000000003f5e7440 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 000000003f5e72c0 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 000000003f5e7ae0 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003f5e0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000003f5e0000
[    0.000000]   NODE_DATA [0000000000009000 - 000000000000dfff]
[    0.000000]   bootmap [000000000000e000 -  0000000000015ebf] pages 8
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 003f5e0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a4caa4]    TEXT DATA BSS ==> [0001000000 - 0001a4caa4]
[    0.000000]   #3 [002efbe000 - 002f8a73ea]          RAMDISK ==> [002efbe000 - 002f8a73ea]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0001a4d000 - 0001a4d0f6]              BRK ==> [0001a4d000 - 0001a4d0f6]
[    0.000000]   #6 [0000008000 - 0000009000]          PGTABLE ==> [0000008000 - 0000009000]
[    0.000000] found SMP MP-table at [ffff8800000f5230] f5230
[    0.000000]  [ffffea0000000000-ffffea0000dfffff] PMD -> [ffff880002000000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f5e0
[    0.000000] On node 0 totalpages: 259450
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 100 pages reserved
[    0.000000]   DMA zone: 3838 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3493 pages used for memmap
[    0.000000]   DMA32 zone: 251963 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f600000 (gap: 3f600000:a0a00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 255801
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-27-server root=/dev/mapper/enterprise-root ro quiet
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1002992k/1038208k available (5512k kernel code, 408k absent, 34808k reserved, 3084k data, 796k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 10485760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2199.959 MHz processor.
[    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4399.91 BogoMIPS (lpj=21999590)
[    0.010039] Security Framework initialized
[    0.010063] AppArmor: AppArmor initialized
[    0.010171] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010892] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.011274] Mount-cache hash table entries: 256
[    0.011462] Initializing cgroup subsys ns
[    0.011469] Initializing cgroup subsys cpuacct
[    0.011472] Initializing cgroup subsys memory
[    0.011481] Initializing cgroup subsys devices
[    0.011483] Initializing cgroup subsys freezer
[    0.011485] Initializing cgroup subsys net_cls
[    0.011509] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.011511] CPU: L2 cache: 512K
[    0.011515] CPU 0/0x0 -> Node 0
[    0.011517] CPU: Physical Processor ID: 0
[    0.011519] CPU: Processor Core ID: 0
[    0.011522] mce: CPU supports 6 MCE banks
[    0.011531] CPU0: Thermal monitoring enabled (TM2)
[    0.011536] using mwait in idle threads.
[    0.011538] Performance Events: Core2 events, Intel PMU driver.
[    0.011545] ... version:                2
[    0.011547] ... bit width:              40
[    0.011548] ... generic registers:      2
[    0.011550] ... value mask:             000000ffffffffff
[    0.011551] ... max period:             000000007fffffff
[    0.011553] ... fixed-purpose events:   3
[    0.011554] ... event mask:             0000000700000003
[    0.014076] ACPI: Core revision 20090903
[    0.020890] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.020900] ftrace: allocating 22827 entries in 90 pages
[    0.030085] Setting APIC routing to flat
[    0.030397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.131466] CPU0: Intel(R) Celeron(R) CPU        E1500  @ 2.20GHz stepping 0d
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 512K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.290035] CPU1: Intel(R) Celeron(R) CPU        E1500  @ 2.20GHz stepping 0d
[    0.290042] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300025] Brought up 2 CPUs
[    0.300027] Total of 2 processors activated (8799.96 BogoMIPS).
[    0.300326] CPU0 attaching sched-domain:
[    0.300330]  domain 0: span 0-1 level MC
[    0.300332]   groups: 0 1
[    0.300339] CPU1 attaching sched-domain:
[    0.300341]  domain 0: span 0-1 level MC
[    0.300343]   groups: 1 0
[    0.300431] devtmpfs: initialized
[    0.302838] regulator: core version 0.5
[    0.302838] Time:  5:15:47  Date: 01/11/11
[    0.302838] NET: Registered protocol family 16
[    0.302838] ACPI: bus type pci registered
[    0.302838] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.302838] PCI: MCFG area at e0000000 reserved in E820
[    0.303564] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.303568] PCI: Using configuration type 1 for base access
[    0.304533] Trying to unpack rootfs image as initramfs...
[    0.304640] bio: create slab <bio-0> at 0
[    0.305328] ACPI: EC: Look up EC in DSDT
[    0.313931] ACPI: Interpreter enabled
[    0.313937] ACPI: (supports S0 S3 S4 S5)
[    0.313961] ACPI: Using IOAPIC for interrupt routing
[    0.319143] ACPI: No dock devices found.
[    0.319276] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.319396] pci 0000:00:02.0: reg 10 32bit mmio: [0xfdf00000-0xfdf7ffff]
[    0.319401] pci 0000:00:02.0: reg 14 io port: [0xff00-0xff07]
[    0.319405] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.319410] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.319492] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff8000-0xfdffbfff]
[    0.319534] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.319538] pci 0000:00:1b.0: PME# disabled
[    0.319599] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.319602] pci 0000:00:1c.0: PME# disabled
[    0.319669] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.319674] pci 0000:00:1c.1: PME# disabled
[    0.319723] pci 0000:00:1d.0: reg 20 io port: [0xfe00-0xfe1f]
[    0.319773] pci 0000:00:1d.1: reg 20 io port: [0xfd00-0xfd1f]
[    0.319821] pci 0000:00:1d.2: reg 20 io port: [0xfc00-0xfc1f]
[    0.319871] pci 0000:00:1d.3: reg 20 io port: [0xfb00-0xfb1f]
[    0.319925] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.320135] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.320140] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.320143] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.320147] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.320188] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.320195] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.320201] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.320207] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.320213] pci 0000:00:1f.1: reg 20 io port: [0xf800-0xf80f]
[    0.320258] pci 0000:00:1f.2: reg 10 io port: [0xf700-0xf707]
[    0.320264] pci 0000:00:1f.2: reg 14 io port: [0xf600-0xf603]
[    0.320270] pci 0000:00:1f.2: reg 18 io port: [0xf500-0xf507]
[    0.320276] pci 0000:00:1f.2: reg 1c io port: [0xf400-0xf403]
[    0.320281] pci 0000:00:1f.2: reg 20 io port: [0xf300-0xf30f]
[    0.320305] pci 0000:00:1f.2: PME# supported from D3hot
[    0.320309] pci 0000:00:1f.2: PME# disabled
[    0.320354] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.320419] pci 0000:00:1c.0: bridge io port: [0xc000-0xcfff]
[    0.320423] pci 0000:00:1c.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
[    0.320429] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
[    0.320476] pci 0000:02:00.0: reg 10 io port: [0xbe00-0xbeff]
[    0.320496] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfddff000-0xfddfffff]
[    0.320513] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdde0000-0xfddeffff]
[    0.320521] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.320564] pci 0000:02:00.0: supports D1 D2
[    0.320566] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.320571] pci 0000:02:00.0: PME# disabled
[    0.320627] pci 0000:00:1c.1: bridge io port: [0xb000-0xbfff]
[    0.320631] pci 0000:00:1c.1: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.320638] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.320675] pci 0000:03:01.0: reg 10 io port: [0xdf00-0xdf0f]
[    0.320682] pci 0000:03:01.0: reg 14 io port: [0xde00-0xde0f]
[    0.320688] pci 0000:03:01.0: reg 18 io port: [0xdd00-0xdd0f]
[    0.320695] pci 0000:03:01.0: reg 1c io port: [0xdc00-0xdc0f]
[    0.320702] pci 0000:03:01.0: reg 20 io port: [0xdb00-0xdb1f]
[    0.320709] pci 0000:03:01.0: reg 24 io port: [0xd800-0xd8ff]
[    0.320716] pci 0000:03:01.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.320777] pci 0000:00:1e.0: transparent bridge
[    0.320781] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.320785] pci 0000:00:1e.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.320790] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
[    0.320817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.320991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.321046] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.321107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.333051] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.333164] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.333258] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.333360] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.333455] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.333556] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.333661] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.333761] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.333925] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.333939] vgaarb: loaded
[    0.334064] SCSI subsystem initialized
[    0.334195] libata version 3.00 loaded.
[    0.334306] usbcore: registered new interface driver usbfs
[    0.334318] usbcore: registered new interface driver hub
[    0.334359] usbcore: registered new device driver usb
[    0.334568] ACPI: WMI: Mapper loaded
[    0.334571] PCI: Using ACPI for IRQ routing
[    0.334755] NetLabel: Initializing
[    0.334757] NetLabel:  domain hash size = 128
[    0.334759] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.334775] NetLabel:  unlabeled traffic allowed by default
[    0.334847] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.334852] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.340093] Switching to clocksource tsc
[    0.342099] AppArmor: AppArmor Filesystem Enabled
[    0.342128] pnp: PnP ACPI init
[    0.342151] ACPI: bus type pnp registered
[    0.345338] pnp: PnP ACPI: found 14 devices
[    0.345342] ACPI: ACPI bus type pnp unregistered
[    0.345359] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.345362] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.345365] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.345368] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.345370] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.345381] system 00:0a: ioport range 0x400-0x4cf could not be reserved
[    0.345387] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.345394] system 00:0c: iomem range 0xcb400-0xcbfff has been reserved
[    0.345396] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.345399] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.345402] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.345405] system 00:0c: iomem range 0x3f5e0000-0x3f5fffff could not be reserved
[    0.345407] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.345410] system 00:0c: iomem range 0x100000-0x3f5dffff could not be reserved
[    0.345413] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.345416] system 00:0c: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.345419] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.345421] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.345424] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.345432] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[    0.345434] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.350218] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.350223] pci 0000:00:1c.0:   IO window: 0xc000-0xcfff
[    0.350228] pci 0000:00:1c.0:   MEM window: 0xfd900000-0xfd9fffff
[    0.350232] pci 0000:00:1c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.350241] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.350244] pci 0000:00:1c.1:   IO window: 0xb000-0xbfff
[    0.350249] pci 0000:00:1c.1:   MEM window: 0xfde00000-0xfdefffff
[    0.350253] pci 0000:00:1c.1:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.350259] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.350262] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.350267] pci 0000:00:1e.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.350271] pci 0000:00:1e.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.350291]   alloc irq_desc for 16 on node -1
[    0.350293]   alloc kstat_irqs on node -1
[    0.350301] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.350306] pci 0000:00:1c.0: setting latency timer to 64
[    0.350314]   alloc irq_desc for 17 on node -1
[    0.350316]   alloc kstat_irqs on node -1
[    0.350319] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.350323] pci 0000:00:1c.1: setting latency timer to 64
[    0.350330] pci 0000:00:1e.0: setting latency timer to 64
[    0.350334] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.350337] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.350340] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.350343] pci_bus 0000:01: resource 1 mem: [0xfd900000-0xfd9fffff]
[    0.350345] pci_bus 0000:01: resource 2 pref mem [0xfd800000-0xfd8fffff]
[    0.350347] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.350349] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.350352] pci_bus 0000:02: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.350354] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.350356] pci_bus 0000:03: resource 1 mem: [0xfdb00000-0xfdbfffff]
[    0.350358] pci_bus 0000:03: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.350361] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.350363] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.350417] NET: Registered protocol family 2
[    0.350545] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.351141] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.352943] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.353784] TCP: Hash tables configured (established 131072 bind 65536)
[    0.353788] TCP reno registered
[    0.353951] NET: Registered protocol family 1
[    0.353989] pci 0000:00:02.0: Boot video device
[    0.354341] Scanning for low memory corruption every 60 seconds
[    0.354524] audit: initializing netlink socket (disabled)
[    0.354538] type=2000 audit(1294722946.349:1): initialized
[    0.363882] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.365394] VFS: Disk quotas dquot_6.5.2
[    0.365484] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.366256] fuse init (API version 7.13)
[    0.366386] msgmni has been set to 1958
[    0.366707] alg: No test for stdrng (krng)
[    0.366822] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.366829] io scheduler noop registered
[    0.366831] io scheduler anticipatory registered
[    0.366833] io scheduler deadline registered (default)
[    0.366883] io scheduler cfq registered
[    0.367033]   alloc irq_desc for 24 on node -1
[    0.367036]   alloc kstat_irqs on node -1
[    0.367048] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.367059] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.367203]   alloc irq_desc for 25 on node -1
[    0.367205]   alloc kstat_irqs on node -1
[    0.367214] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.367221] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.367314] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.367396] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.367512] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.367516] ACPI: Power Button [PWRB]
[    0.367578] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.367581] ACPI: Power Button [PWRF]
[    0.368122] ACPI: SSDT 000000003f5e74c0 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.368349] processor LNXCPU:00: registered as cooling_device0
[    0.368601] ACPI: SSDT 000000003f5e7980 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.368924] processor LNXCPU:01: registered as cooling_device1
[    0.372593] Linux agpgart interface v0.103
[    0.372635] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.372766] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.373155] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.374452] brd: module loaded
[    0.375050] loop: module loaded
[    0.375186] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.375350] ata_piix 0000:00:1f.1: version 2.13
[    0.375369]   alloc irq_desc for 18 on node -1
[    0.375371]   alloc kstat_irqs on node -1
[    0.375379] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.375430] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.375557] scsi0 : ata_piix
[    0.375703] scsi1 : ata_piix
[    0.376392] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf800 irq 14
[    0.376397] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf808 irq 15
[    0.376444]   alloc irq_desc for 19 on node -1
[    0.376446]   alloc kstat_irqs on node -1
[    0.376453] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.376459] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.376503] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.376867] scsi2 : ata_piix
[    0.376973] scsi3 : ata_piix
[    0.377776] ata3: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf300 irq 19
[    0.377780] ata4: SATA max UDMA/133 cmd 0xf500 ctl 0xf400 bmdma 0xf308 irq 19
[    0.378147] Fixed MDIO Bus: probed
[    0.378186] PPP generic driver version 2.4.2
[    0.378269] tun: Universal TUN/TAP device driver, 1.6
[    0.378272] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.378419] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.378452]   alloc irq_desc for 23 on node -1
[    0.378455]   alloc kstat_irqs on node -1
[    0.378463] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.378483] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.378486] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.378537] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.378564] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.382465] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.382511] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    0.399587] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.399762] usb usb1: configuration #1 chosen from 1 choice
[    0.399798] hub 1-0:1.0: USB hub found
[    0.399809] hub 1-0:1.0: 8 ports detected
[    0.399890] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.399907] uhci_hcd: USB Universal Host Controller Interface driver
[    0.399956] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.399966] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.399969] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.400059] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.400090] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fe00
[    0.400198] usb usb2: configuration #1 chosen from 1 choice
[    0.400230] hub 2-0:1.0: USB hub found
[    0.400239] hub 2-0:1.0: 2 ports detected
[    0.400292] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.400300] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.400303] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.400363] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.400392] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fd00
[    0.400506] usb usb3: configuration #1 chosen from 1 choice
[    0.400538] hub 3-0:1.0: USB hub found
[    0.400546] hub 3-0:1.0: 2 ports detected
[    0.400605] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.400615] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.400618] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.400671] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.400709] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[    0.400835] usb usb4: configuration #1 chosen from 1 choice
[    0.400871] hub 4-0:1.0: USB hub found
[    0.400881] hub 4-0:1.0: 2 ports detected
[    0.400942] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.400950] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.400953] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.401018] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.401065] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[    0.401178] usb usb5: configuration #1 chosen from 1 choice
[    0.401212] hub 5-0:1.0: USB hub found
[    0.401225] hub 5-0:1.0: 2 ports detected
[    0.401342] PNP: No PS/2 controller found. Probing ports directly.
[    0.434180] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.434185] If AUX port is really absent please use the 'i8042.noaux' option.
[    0.515441] Freeing initrd memory: 9124k freed
[    0.542563] ata1.00: ATA-7: Maxtor 6B200P0, BAH41B70, max UDMA/133
[    0.542570] ata1.00: 398297088 sectors, multi 16: LBA48 
[    0.581377] ata1.00: configured for UDMA/100
[    0.581544] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6B200P0   BAH4 PQ: 0 ANSI: 5
[    0.581697] sd 0:0:0:0: [sda] 398297088 512-byte logical blocks: (203 GB/189 GiB)
[    0.581749] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.581752] sd 0:0:0:0: [sda] Write Protect is off
[    0.581755] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.581786] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.581991]  sda: sda1 sda2 < sda5 >
[    0.600075] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.679855] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.679994] mice: PS/2 mouse device common for all mice
[    0.680114] rtc_cmos 00:04: RTC can wake from S4
[    0.680167] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.680194] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.680348] device-mapper: uevent: version 1.0.3
[    0.680504] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.680609] device-mapper: multipath: version 1.1.0 loaded
[    0.680612] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.680826] cpuidle: using governor ladder
[    0.680828] cpuidle: using governor menu
[    0.681164] TCP cubic registered
[    0.681323] NET: Registered protocol family 10
[    0.681796] lo: Disabled Privacy Extensions
[    0.682065] NET: Registered protocol family 17
[    0.683487] PM: Resume from disk failed.
[    0.683504] registered taskstats version 1
[    0.683779]   Magic number: 11:42:264
[    0.683869] rtc_cmos 00:04: setting system clock to 2011-01-11 05:15:47 UTC (1294722947)
[    0.683873] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.683874] EDD information not available.
[    0.940015] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.059301] ata4.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.059308] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.071494] ata4.01: HPA unlocked: 1953523055 -> 1953525168, native 1953525168
[    1.071500] ata4.01: ATA-8: Hitachi HDT721010SLA360, ST6OA31B, max UDMA/133
[    1.071503] ata4.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.111992] ata4.00: configured for UDMA/133
[    1.120223] ata3.00: HPA unlocked: 1953523055 -> 1953525168, native 1953525168
[    1.120227] ata3.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.120230] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.129886] usb 4-1: configuration #1 chosen from 1 choice
[    1.150478] ata4.01: configured for UDMA/133
[    1.592331] ata3.01: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.592338] ata3.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.610676] ata3.00: configured for UDMA/133
[    1.632013] ata3.01: configured for UDMA/133
[    1.632160] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.632339] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.632348] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.632403] sd 2:0:0:0: [sdb] Write Protect is off
[    1.632406] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.632462] scsi 2:0:1:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.632466] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.632623] sd 2:0:1:0: Attached scsi generic sg2 type 0
[    1.632654]  sdb:
[    1.632799] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.632948] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.633071] scsi 3:0:1:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    1.633100] sd 3:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.633152] sd 3:0:0:0: [sdd] Write Protect is off
[    1.633155] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.633232] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.633235] sd 3:0:1:0: Attached scsi generic sg4 type 0
[    1.633362] sd 3:0:1:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.633455] sd 3:0:1:0: [sde] Write Protect is off
[    1.633459] sd 3:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    1.633472]  sdd:
[    1.633491] sd 3:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.636736]  sdd1
[    1.636890]  sde: sdb1
[    1.638557] sd 2:0:1:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.638622] sd 2:0:1:0: [sdc] Write Protect is off
[    1.638626] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    1.638676] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.638681] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.638861]  sdc: sde1
[    1.644661] sd 3:0:1:0: [sde] Attached SCSI disk
[    1.644671] sd 3:0:0:0: [sdd] Attached SCSI disk
[    1.647439]  sdc1
[    1.647735] sd 2:0:1:0: [sdc] Attached SCSI disk
[    1.647757] Freeing unused kernel memory: 796k freed
[    1.648076] Write protecting the kernel read-only data: 7804k
[    1.670574] udev: starting version 151
[    1.729391] md: linear personality registered for level -1
[    1.746131] sata_via 0000:03:01.0: version 2.4
[    1.746153] sata_via 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.746204] sata_via 0000:03:01.0: routed to hard irq line 11
[    1.761010] md: multipath personality registered for level -4
[    1.766779] scsi4 : sata_via
[    1.780549] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.780585] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.780643] r8169 0000:02:00.0: setting latency timer to 64
[    1.780690]   alloc irq_desc for 26 on node -1
[    1.780693]   alloc kstat_irqs on node -1
[    1.780713] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    1.795608] scsi5 : sata_via
[    1.804597] Floppy drive(s): fd0 is 1.44M
[    1.810626] eth0: RTL8168c/8111c at 0xffffc9001054e000, 00:24:1d:99:09:57, XID 1c4000c0 IRQ 26
[    1.824592] scsi6 : sata_via
[    1.824674] ata5: SATA max UDMA/133 port i16@0xdf00 bmdma 0xdb00 irq 19
[    1.824678] ata6: SATA max UDMA/133 port i16@0xde00 bmdma 0xdb08 irq 19
[    1.824680] ata7: PATA max UDMA/133 port i16@0xdd00 bmdma 0xdb10 irq 19
[    1.826802] FDC 0 is a post-1991 82077
[    1.831860] md: raid0 personality registered for level 0
[    1.831951] usbcore: registered new interface driver hiddev
[    1.846440] input: Microsoft Microsoft Wireless Optical DesktopÂ® 1.00 as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
[    1.846585] generic-usb 0003:045E:005F.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical DesktopÂ® 1.00] on usb-0000:00:1d.2-1/input0
[    1.907928] input: Microsoft Microsoft Wireless Optical DesktopÂ® 1.00 as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input4
[    1.908126] generic-usb 0003:045E:005F.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical DesktopÂ® 1.00] on usb-0000:00:1d.2-1/input1
[    1.908173] usbcore: registered new interface driver usbhid
[    1.908177] usbhid: v2.6:USB HID core driver
[    1.916446] md: bind<sdd1>
[    1.918262] md: bind<sde1>
[    2.024684] md: bind<sdc1>
[    2.170084] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.210271] ata5.00: HPA unlocked: 1953523055 -> 1953525168, native 1953525168
[    2.210277] ata5.00: ATA-7: SAMSUNG HD103UJ, 1AA01118, max UDMA7
[    2.210281] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.225912] md: bind<sdb1>
[    2.231735] ata5.00: configured for UDMA/133
[    2.231903] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    2.232166] sd 4:0:0:0: Attached scsi generic sg5 type 0
[    2.232195] sd 4:0:0:0: [sdf] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.232302] sd 4:0:0:0: [sdf] Write Protect is off
[    2.232307] sd 4:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    2.232354] sd 4:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.232582]  sdf: sdf1
[    2.243607] sd 4:0:0:0: [sdf] Attached SCSI disk
[    2.580071] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.994424] ata6.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    2.994432] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    3.030816] ata6.00: configured for UDMA/133
[    3.030964] scsi 5:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    3.031207] sd 5:0:0:0: Attached scsi generic sg6 type 0
[    3.031224] sd 5:0:0:0: [sdg] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.031398] sd 5:0:0:0: [sdg] Write Protect is off
[    3.031403] sd 5:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[    3.031459] sd 5:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.031673]  sdg: sdg1
[    3.039261] sd 5:0:0:0: [sdg] Attached SCSI disk
[    3.209078] md: raid1 personality registered for level 1
[    3.212235] async_tx: api initialized (async)
[    3.266310] md: bind<sdg1>
[    3.317287] md: bind<sdf1>
[    3.380027] raid6: int64x1   1722 MB/s
[    3.550024] raid6: int64x2   2358 MB/s
[    3.720035] raid6: int64x4   1662 MB/s
[    3.890008] raid6: int64x8   1517 MB/s
[    4.060009] raid6: sse2x1    3623 MB/s
[    4.230012] raid6: sse2x2    4122 MB/s
[    4.400005] raid6: sse2x4    6564 MB/s
[    4.400007] raid6: using algorithm sse2x4 (6564 MB/s)
[    4.401510] xor: automatically using best checksumming function: generic_sse
[    4.449995]    generic_sse:  8060.400 MB/sec
[    4.449997] xor: using function: generic_sse (8060.400 MB/sec)
[    4.454425] md: raid6 personality registered for level 6
[    4.454429] md: raid5 personality registered for level 5
[    4.454431] md: raid4 personality registered for level 4
[    4.462077] md: raid10 personality registered for level 10
[    4.486223] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    4.486229] EXT4-fs (dm-0): write access will be enabled during recovery
[    5.068570] EXT4-fs (dm-0): recovery complete
[    5.068992] EXT4-fs (dm-0): mounted filesystem with ordered data mode
[   14.176602] udev: starting version 151
[   14.217999] Adding 2969592k swap on /dev/mapper/enterprise-swap_1.  Priority:-1 extents:1 across:2969592k 
[   14.436372] type=1505 audit(1294722961.246:2):  operation="profile_load" pid=538 name="/sbin/dhclient3"
[   14.437071] type=1505 audit(1294722961.246:3):  operation="profile_load" pid=538 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.437455] type=1505 audit(1294722961.246:4):  operation="profile_load" pid=538 name="/usr/lib/connman/scripts/dhclient-script"
[   14.503445] parport_pc 00:09: reported by Plug and Play ACPI
[   14.503497] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   14.545327] lp: driver loaded but no devices found
[   14.581562] lp0: using parport0 (interrupt-driven).
[   14.595365] intel_rng: FWH not detected
[   14.598236] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   14.598445] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   14.610265] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.613666] r8169: eth0: link up
[   14.613674] r8169: eth0: link up
[   14.696195] ppdev: user-space parallel port driver
[   14.892431] coretemp coretemp.0: Using relative temperature scale!
[   14.892504] coretemp coretemp.1: Using relative temperature scale!
[   15.043964] it87: Found IT8718F chip at 0x290, revision 5
[   15.043976] it87: in3 is VCC (+5V)
[   15.121380] [drm] Initialized drm 1.1.0 20060810
[   15.299708] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.299715] i915 0000:00:02.0: setting latency timer to 64
[   15.307933]   alloc irq_desc for 27 on node -1
[   15.307937]   alloc kstat_irqs on node -1
[   15.307948] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[   15.307956] [drm] set up 7M of stolen space
[   15.308440] [drm] initialized overlay support
[   15.502726] fb0: inteldrmfb frame buffer device
[   15.502731] registered panic notifier
[   15.502755] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.502832] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.502861] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.726267] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   15.739969] vga16fb: initializing
[   15.739973] vga16fb: mapped to 0xffff8800000a0000
[   15.739977] vga16fb: not registering due to another framebuffer present
[   15.971543] Console: switching to colour frame buffer device 240x67
[   20.069307] type=1505 audit(1294722967.977:5):  operation="profile_load" pid=910 name="/usr/sbin/mysqld"
[   20.069590] type=1505 audit(1294722967.977:6):  operation="profile_replace" pid=909 name="/sbin/dhclient3"
[   20.070537] type=1505 audit(1294722967.987:7):  operation="profile_replace" pid=909 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.070915] type=1505 audit(1294722967.987:8):  operation="profile_replace" pid=909 name="/usr/lib/connman/scripts/dhclient-script"
[   20.073571] type=1505 audit(1294722967.987:9):  operation="profile_load" pid=911 name="/usr/sbin/tcpdump"
[   20.374135] type=1505 audit(1294722968.287:10):  operation="profile_replace" pid=1039 name="/usr/sbin/mysqld"
[   22.011335] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   22.011408] ata3.01: failed command: IDENTIFY DEVICE
[   22.011461] ata3.01: cmd ec/00:01:00:00:00/00:00:00:00:00/10 tag 0 pio 512 in
[   22.011462]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   22.011528] ata3.01: status: { DRDY }
[   24.940034] eth0: no IPv6 routers present
[   27.050030] ata3: link is slow to respond, please be patient (ready=0)
[   32.030041] ata3: device not ready (errno=-16), forcing hardreset
[   32.030052] ata3: soft resetting link
[   37.230039] ata3: link is slow to respond, please be patient (ready=0)
[   42.090040] ata3: SRST failed (errno=-16)
[   42.090092] ata3: soft resetting link
[   47.290038] ata3: link is slow to respond, please be patient (ready=0)
[   52.150039] ata3: SRST failed (errno=-16)
[   52.150092] ata3: soft resetting link
[   57.351275] ata3: link is slow to respond, please be patient (ready=0)
[   66.411805] ata3.00: configured for UDMA/133
[   66.431792] ata3.01: configured for UDMA/133
[   66.431823] ata3: EH complete
[ 7703.053320] md: md0 stopped.
[ 7703.053342] md: unbind<sdf1>
[ 7703.080036] md: export_rdev(sdf1)
[ 7703.080179] md: unbind<sdg1>
[ 7703.110171] md: export_rdev(sdg1)
[ 7703.110302] md: unbind<sdb1>
[ 7703.150029] md: export_rdev(sdb1)
[ 7703.150187] md: unbind<sdc1>
[ 7703.190027] md: export_rdev(sdc1)
[ 7703.190160] md: unbind<sde1>
[ 7703.230024] md: export_rdev(sde1)
[ 7703.230181] md: unbind<sdd1>
[ 7703.270028] md: export_rdev(sdd1)
[ 7703.282561] md: bind<sdb1>
[ 7703.283598] md: bind<sde1>
[ 7703.284071] md: bind<sdf1>
[ 7703.284400] md: bind<sdg1>
[ 7703.284631] md: bind<sdc1>
[ 7703.284892] md: bind<sdd1>
[ 7786.613432] md: md0 stopped.
[ 7786.613453] md: unbind<sdd1>
[ 7786.640028] md: export_rdev(sdd1)
[ 7786.640091] md: unbind<sdc1>
[ 7786.680020] md: export_rdev(sdc1)
[ 7786.680087] md: unbind<sdg1>
[ 7786.720031] md: export_rdev(sdg1)
[ 7786.720100] md: unbind<sdf1>
[ 7786.760018] md: export_rdev(sdf1)
[ 7786.760068] md: unbind<sde1>
[ 7786.800020] md: export_rdev(sde1)
[ 7786.800073] md: unbind<sdb1>
[ 7786.840021] md: export_rdev(sdb1)
[ 7786.855584] md: bind<sdb1>
[ 7786.856768] md: bind<sde1>
[ 7786.858495] md: bind<sdf1>
[ 7786.858819] md: bind<sdg1>
[ 7786.859290] md: bind<sdc1>
[ 7786.859588] md: bind<sdd1>

```There is almost no load on the server.

What is NCQ and how do I disable it?
Any tips on what to try from here?

---

### Post by rubylaser on 2011-01-12
NCQ is Native Command Queuing
```
sudo -i
``` enter your password, then run this command to disable NCQ on each drive.
```
echo "Disabling NCQ on all disks..."
echo 1 > /sys/block/sdb/device/queue_depth
echo 1 > /sys/block/sdc/device/queue_depth
echo 1 > /sys/block/sdd/device/queue_depth
echo 1 > /sys/block/sde/device/queue_depth
echo 1 > /sys/block/sdf/device/queue_depth
echo 1 > /sys/block/sdg/device/queue_depth

```
I would guess that the WD Green are going to sleep waiting for i/o (to save power) and that it's interfering with software RAID.  Just looking at dmesg trying to bring the array up shows there are problems.  This is what it should look like.
```
[   12.857356] md: md0 stopped.
[   12.879668] md: bind<sde1>
[   12.879865] md: bind<sdd1>
[   12.881325] md: bind<sdc1>
[   12.883089] md: bind<sdg1>
[   12.884483] md: bind<sdi1>
[   12.884844] md: bind<sdh1>
[   12.886355] md: bind<sdf1>
[   12.886654] md: bind<sdb1>
[   14.574496] md: raid6 personality registered for level 6
[   14.574499] md: raid5 personality registered for level 5
[   14.574502] md: raid4 personality registered for level 4
[   14.576509] raid5: allocated 8490kB for md0
[   14.577389] raid5: raid level 6 set md0 active with 8 out of 8 devices, algorithm 2
[   14.577462] md0: detected capacity change from 0 to 6001212260352
```

See how it comes right up with no unbinding messages?

---

### Post by Snowjoggs on 2011-01-12
hmm seems disabling NCQ doesn't work, permission issue..

```
root@enterprise:~# echo "Disabling NCQ on all disks..."
Disabling NCQ on all disks...
root@enterprise:~# echo 1 > /sys/block/sdb/device/queue_depth
bash: /sys/block/sdb/device/queue_depth: Permission denied

```

This post [http://forums.fedoraforum.org/archive/index.php/t-191620.html](http://forums.fedoraforum.org/archive/index.php/t-191620.html) mention its to do with AHCI setting in the BIOS, my options are auto, combined, non-combined...

Its at non-combined currently (changed it yesterday) I haven't checked yet if this alone would solve the issue thp-

Raid is OK once more after I re-synced it again btw

```
root@enterprise:~# mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jan 12 11:15:27 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
         Events : 0.1016546

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1

```

---

### Post by Snowjoggs on 2011-01-12
hmm seems disabling NCQ doesn't work, permission issue..

```
root@enterprise:~# echo "Disabling NCQ on all disks..."
Disabling NCQ on all disks...
root@enterprise:~# echo 1 > /sys/block/sdb/device/queue_depth
bash: /sys/block/sdb/device/queue_depth: Permission denied

```

This post [http://forums.fedoraforum.org/archive/index.php/t-191620.html](http://forums.fedoraforum.org/archive/index.php/t-191620.html) mention its to do with AHCI setting in the BIOS, my options are auto, combined, non-combined...

Its at non-combined currently (changed it yesterday) I haven't checked yet if this alone would solve the issue thp-

Raid is OK once more after I re-synced it again btw

```
root@enterprise:~# mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jan 12 11:15:27 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
         Events : 0.1016546

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1

```

---

### Post by Snowjoggs on 2011-01-12
hmm seems disabling NCQ doesn't work, permission issue..

```
root@enterprise:~# echo "Disabling NCQ on all disks..."
Disabling NCQ on all disks...
root@enterprise:~# echo 1 > /sys/block/sdb/device/queue_depth
bash: /sys/block/sdb/device/queue_depth: Permission denied

```This  post [http://forums.fedoraforum.org/archive/index.php/t-191620.html](http://forums.fedoraforum.org/archive/index.php/t-191620.html)  mention its to do with AHCI setting in the BIOS, my options are auto,  combined, non-combined...

Its at non-combined currently (changed it yesterday) I haven't checked yet if this alone would solve the issue tho...

Raid is OK once more after I re-synced it again btw

```
root@enterprise:~# mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jan 12 11:15:27 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
         Events : 0.1016546

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1

```

---

### Post by disabledaccount on 2011-01-12
> [   27.050030] ata3: link is slow to respond, please be patient (ready=0)
[   32.030041] ata3: device not ready (errno=-16), forcing hardreset
[   32.030052] ata3: soft resetting link
[   37.230039] ata3: link is slow to respond, please be patient (ready=0)
[   42.090040] ata3: SRST failed (errno=-16)
[   42.090092] ata3: soft resetting link
[   47.290038] ata3: link is slow to respond, please be patient (ready=0)
[   52.150039] ata3: SRST failed (errno=-16)
[   52.150092] ata3: soft resetting link
[   57.351275] ata3: link is slow to respond, please be patient (ready=0)
[   66.411805] ata3.00: configured for UDMA/133
[   66.431792] ata3.01: configured for UDMA/133
[   66.431823] ata3: EH completeYou **have** broken SATA cable or damaged HDD
For future: you should **never** belive if SMART reports no errors. **Every** harddisk in the world reports SMART error a socond before it starts brak into pieces or not at all.
The **ONLY** way to check SMART is to check values by hand (or by eye :) )
So: show full SMART reports, then I can tell you if they are really ok.

---

### Post by Snowjoggs on 2011-02-09
The problem went away actually... but re-appeared today again.

I had about 7-8 simultaneous download threads going on the rtorrent client when it crashed.

I read the output on the connected monitor and it spews out

 *soft lockup* - *CPU*#[I]0 stuck for 61

[/I]the system is unresponsive and I must hard reset it to get it back up, which obviously causes the array to resync :(

I have tried googling some for this issue, but I can't really find any fix for it.

Any ideas?

---

### Post by rabbit20 on 2011-02-10
Having an issue with my array as well. I have a RAID5 with 4 drives. all 1TB Seagates. I am getting an error that 2 of the for drives are not there for the rebuild when I try mdadm --assemble --scan   When I try to restart the array in Disk Utility I get the error mdadm exited with error code 1:mdadm: cannot open device /dev/sdb: Device or resource busy mdadm: /dev/sdb has no superblock -assembly aborted. 

I was having issues with my raid yesterday. After downloading a file I got an error that it was corrupted. So i did a reboot and my server didn't come back up. It could not mount the drive. In Disk utility all 4 drives are seen and they all show they are part of an array. 

I am not sure where else to go...I might try seeing what I can do in the bios but would that make ubuntu not see the drives anymore because the bois would make them 1 drive on the hardware side?

---

### Post by jbrown96 on 2011-02-10
Are any of the drives "green?"

---

### Post by Snowjoggs on 2011-02-10
Ok I'm one step closer!

Seems like this is not related to my mdadm RAID5 at _all_!

The soft lockup CPU occurs at high loads even when my raid is not in use. I was just thrown by the errors my raid gave me each time I had to reboot due to these lock ups.

I tested this with adding 7-8 simultaneous downloads directly to root (/dev/sda) and the same lockup occured!

I have tried adding the "noapic" variable to the kernel boot, but that did not help.

Someone suggest turning of HT which is not possible in my cheap *** BIOS, and I guess there is no software alternative for doing this either in Ubuntu?

I'm starting a new thread on this, sorry rabbit but hijacking this one with your issues is not really a good idea either :P

---

### Post by Snowjoggs on 2011-02-10
I solved it!!

Google is my friend :grin:

One guy suggested this

```
apt-get install intel-microcode microcode.ctl
```The upgraded  microcode where applied after a quick reboot and now its dead stable, no  locks no matter how much I/O traffic I hit it with :grin:

---

