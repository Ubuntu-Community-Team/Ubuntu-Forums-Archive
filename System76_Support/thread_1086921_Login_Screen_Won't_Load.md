---
title: "Login Screen Won't Load?"
date: 2009-03-04
forum: System76 Support
---

### Post by jpoRS on 2009-03-04
Hey,

This problem has happened a few times, and as far as I can tell there is no rhyme or reason to it.

Sometimes when I boot up my computer (Panp4i) it will go through the normal boot stuff (all that white text, "Starting System" or whatever, and even the black loading screen with the orange progress bar and "Ubuntu") then go to a blank screen.  No gdm screen, no noise, nothing.  The screen isn't off, because I can see the difference between "on" black and "off" black screens.

I really don't know how to diagnose this so I figured I would take it up with the pros.  Running 8.10 btw.

Thanks,
jim

---

### Post by thomasaaron on 2009-03-04
You've gotta love intermittent problems! ](*,)

Is this after a fresh boot up? After hibernate?

---

### Post by jpoRS on 2009-03-04
Always fresh boot, I almost never hibernate.

jim

---

### Post by thomasaaron on 2009-03-05
Since it is intermittent, I'm guessing your filesystem is getting iffy and the OS is failing to find some file, and so the system is stalling.

If you want to dig deeper on it, the next time it fails...
1. Immediately reboot.
2. Mark the time on your *system* clock
3. Go to System > Administraton > System76 Driver > Support > Create and send me the logs.tar file it creates in your logs *with* the time you recorded.

I'll have a look and see if I can figure out anything. But problems like this may not leave a real good record of what happened.

---

### Post by jpoRS on 2009-03-18
Of course after I start looking for help, it doesn't happen again for a long time.  Here is the log from the first entry today to the first time I was able to check the system clock.

```
Mar 18 11:02:37 ubuntu syslogd 1.5.0#2ubuntu6: restart.
Mar 18 11:02:37 ubuntu kernel: Inspecting /boot/System.map-2.6.27-11-generic
Mar 18 11:02:37 ubuntu kernel: Cannot find map file.
Mar 18 11:02:37 ubuntu kernel: Loaded 53049 symbols from 89 modules.
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash 
Mar 18 11:02:37 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 18 11:02:37 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007d6b1000 (usable)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d6b1000 - 000000007d6b7000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d6b7000 - 000000007d7bb000 (usable)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d7bb000 - 000000007d80f000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d80f000 - 000000007d908000 (usable)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d908000 - 000000007db0f000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db0f000 - 000000007db18000 (usable)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db18000 - 000000007db1f000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db1f000 - 000000007db64000 (usable)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db64000 - 000000007db9f000 (ACPI NVS)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db9f000 - 000000007dbe5000 (usable)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007dbe5000 - 000000007dbfd000 (ACPI data)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007dbfd000 - 000000007dc00000 (usable)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007dc00000 - 000000007de00000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007e000000 - 0000000080000000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] DMI present.
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Mar 18 11:02:37 ubuntu kernel: [    0.000000] last_pfn = 0x7dc00 max_arch_pfn = 0x3ffffffff
Mar 18 11:02:37 ubuntu kernel: [    0.000000] init_memory_mapping
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  0000000000 - 007dc00000 page 2M
Mar 18 11:02:37 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 7dc00000 @ 10000-13000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] last_map_addr: 7dc00000 end: 7dc00000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] RAMDISK: 377c1000 - 37fef4dd
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: RSDP 000F73B0, 0024 (r2 PTLTD )
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: XSDT 7DBF74FE, 0064 (r1 \Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff \Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff  6040000  LTP        0)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: FACP 7DBE9000, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: DSDT 7DBEA000, 5694 (r2 Intel  CANTIGA   6040000 INTL 20050624)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: FACS 7DB9EFC0, 0040
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: HPET 7DBFCD86, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: MCFG 7DBFCDBE, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: APIC 7DBFCDFA, 0068 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: SLIC 7DBFCE62, 0176 (r1 \Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff \Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff  6040000  LTP        0)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: SSDT 7DBE8000, 0655 (r1  PmRef    CpuPm     3000 INTL 20050624)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: SSDT 7DBE7000, 0259 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: SSDT 7DBE6000, 020F (r1  PmRef    ApTst     3000 INTL 20050624)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] No NUMA configuration found
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007dc00000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007dc00000
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   NODE_DATA [0000000000011000 - 0000000000015fff]
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   bootmap [0000000000016000 -  0000000000025b7f] pages 10
Mar 18 11:02:37 ubuntu kernel: [    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007dc00000]
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   #2 [0000200000 - 00008b9f5c]    TEXT DATA BSS ==> [0000200000 - 00008b9f5c]
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   #3 [00377c1000 - 0037fef4dd]          RAMDISK ==> [00377c1000 - 0037fef4dd]
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   #4 [000009d400 - 0000100000]    BIOS reserved ==> [000009d400 - 0000100000]
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   #5 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 18 11:02:37 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f7440] 000f7440
Mar 18 11:02:37 ubuntu kernel: [    0.000000]  [ffffe20000000000-ffffe20001ffffff] PMD -> [ffff880001200000-ffff8800031fffff] on node 0
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 18 11:02:37 ubuntu kernel: [    0.000000] early_node_map[8] active PFN ranges
Mar 18 11:02:37 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Mar 18 11:02:37 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007d6b1
Mar 18 11:02:37 ubuntu kernel: [    0.000000]     0: 0x0007d6b7 -> 0x0007d7bb
Mar 18 11:02:37 ubuntu kernel: [    0.000000]     0: 0x0007d80f -> 0x0007d908
Mar 18 11:02:37 ubuntu kernel: [    0.000000]     0: 0x0007db0f -> 0x0007db18
Mar 18 11:02:37 ubuntu kernel: [    0.000000]     0: 0x0007db1f -> 0x0007db64
Mar 18 11:02:37 ubuntu kernel: [    0.000000]     0: 0x0007db9f -> 0x0007dbe5
Mar 18 11:02:37 ubuntu kernel: [    0.000000]     0: 0x0007dbfd -> 0x0007dc00
Mar 18 11:02:37 ubuntu kernel: [    0.000000] On node 0 totalpages: 514258
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   DMA zone: 2092 pages, LIFO batch:0
Mar 18 11:02:37 ubuntu kernel: [    0.000000]   DMA32 zone: 502293 pages, LIFO batch:31
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar 18 11:02:37 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Setting APIC routing to flat
Mar 18 11:02:37 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 18 11:02:37 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007d6b1000 - 000000007d6b7000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007d7bb000 - 000000007d80f000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007d908000 - 000000007db0f000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007db18000 - 000000007db1f000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007db64000 - 000000007db9f000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007dbe5000 - 000000007dbfd000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
Mar 18 11:02:37 ubuntu kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 504385
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Policy zone: DMA32
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Kernel command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash 
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 18 11:02:37 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Mar 18 11:02:37 ubuntu kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Mar 18 11:02:37 ubuntu kernel: [    0.000000] TSC: using PMTIMER calibration value
Mar 18 11:02:37 ubuntu kernel: [    0.000000] Detected 2393.988 MHz processor.
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Console: colour VGA+ 80x25
Mar 18 11:02:37 ubuntu kernel: [    0.004000] console [tty0] enabled
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Checking aperture...
Mar 18 11:02:37 ubuntu kernel: [    0.004000] No AGP bridge found
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Calgary: detecting Calgary via BIOS EBDA area
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Memory: 2008708k/2060288k available (3116k kernel code, 48324k reserved, 1575k data, 540k init)
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Mar 18 11:02:37 ubuntu kernel: [    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar 18 11:02:37 ubuntu kernel: [    0.004000] hpet clockevent registered
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.97 BogoMIPS (lpj=9575952)
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Security Framework initialized
Mar 18 11:02:37 ubuntu kernel: [    0.004000] SELinux:  Disabled at boot.
Mar 18 11:02:37 ubuntu kernel: [    0.004000] AppArmor: AppArmor initialized
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Mount-cache hash table entries: 256
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Initializing cgroup subsys ns
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Initializing cgroup subsys cpuacct
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Initializing cgroup subsys memory
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU: L2 cache: 3072K
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU 0/0 -> Node 0
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 0
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU0: Thermal monitoring enabled (TM2)
Mar 18 11:02:37 ubuntu kernel: [    0.004000] using mwait in idle threads.
Mar 18 11:02:37 ubuntu kernel: [    0.004000] ACPI: Core revision 20080609
Mar 18 11:02:37 ubuntu kernel: [    0.005668] ACPI: Checking initramfs for custom DSDT
Mar 18 11:02:37 ubuntu kernel: [    0.324412] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 18 11:02:37 ubuntu kernel: [    0.364574] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
Mar 18 11:02:37 ubuntu kernel: [    0.364578] Using local APIC timer interrupts.
Mar 18 11:02:37 ubuntu kernel: [    0.368024] APIC timer calibration result 16624951
Mar 18 11:02:37 ubuntu kernel: [    0.368025] Detected 16.624 MHz APIC timer.
Mar 18 11:02:37 ubuntu kernel: [    0.368128] Booting processor 1/1 ip 6000
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Initializing CPU#1
Mar 18 11:02:37 ubuntu kernel: [    0.004000] Calibrating delay using timer specific routine.. 4787.97 BogoMIPS (lpj=9575955)
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU: L2 cache: 3072K
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU 1/1 -> Node 0
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 1
Mar 18 11:02:37 ubuntu kernel: [    0.004000] CPU1: Thermal monitoring enabled (TM2)
Mar 18 11:02:37 ubuntu kernel: [    0.456586] CPU1: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
Mar 18 11:02:37 ubuntu kernel: [    0.456605] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 18 11:02:37 ubuntu kernel: [    0.460059] Brought up 2 CPUs
Mar 18 11:02:37 ubuntu kernel: [    0.460061] Total of 2 processors activated (9575.95 BogoMIPS).
Mar 18 11:02:37 ubuntu kernel: [    0.460102] CPU0 attaching sched-domain:
Mar 18 11:02:37 ubuntu kernel: [    0.460104]  domain 0: span 0-1 level MC
Mar 18 11:02:37 ubuntu kernel: [    0.460106]   groups: 0 1
Mar 18 11:02:37 ubuntu kernel: [    0.460109]   domain 1: span 0-1 level NODE
Mar 18 11:02:37 ubuntu kernel: [    0.460111]    groups: 0-1
Mar 18 11:02:37 ubuntu kernel: [    0.460115] CPU1 attaching sched-domain:
Mar 18 11:02:37 ubuntu kernel: [    0.460116]  domain 0: span 0-1 level MC
Mar 18 11:02:37 ubuntu kernel: [    0.460117]   groups: 1 0
Mar 18 11:02:37 ubuntu kernel: [    0.460120]   domain 1: span 0-1 level NODE
Mar 18 11:02:37 ubuntu kernel: [    0.460121]    groups: 0-1
Mar 18 11:02:37 ubuntu kernel: [    0.460195] net_namespace: 1552 bytes
Mar 18 11:02:37 ubuntu kernel: [    0.460195] Booting paravirtualized kernel on bare hardware
Mar 18 11:02:37 ubuntu kernel: [    0.460252] Time: 15:02:04  Date: 03/18/09
Mar 18 11:02:37 ubuntu kernel: [    0.460276] NET: Registered protocol family 16
Mar 18 11:02:37 ubuntu kernel: [    0.460290] ACPI: bus type pci registered
Mar 18 11:02:37 ubuntu kernel: [    0.460290] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar 18 11:02:37 ubuntu kernel: [    0.460290] PCI: MCFG area at e0000000 reserved in E820
Mar 18 11:02:37 ubuntu kernel: [    0.470441] PCI: Using MMCONFIG at e0000000 - efffffff
Mar 18 11:02:37 ubuntu kernel: [    0.470443] PCI: Using configuration type 1 for base access
Mar 18 11:02:37 ubuntu kernel: [    0.470454] ACPI: EC: Look up EC in DSDT
Mar 18 11:02:37 ubuntu kernel: [    0.476063] ACPI: BIOS _OSI(Linux) query ignored
Mar 18 11:02:37 ubuntu kernel: [    0.476065] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
Mar 18 11:02:37 ubuntu kernel: [    0.476780] ACPI: Interpreter enabled
Mar 18 11:02:37 ubuntu kernel: [    0.476782] ACPI: (supports S0 S3 S4 S5)
Mar 18 11:02:37 ubuntu kernel: [    0.476796] ACPI: Using IOAPIC for interrupt routing
Mar 18 11:02:37 ubuntu kernel: [    0.476855] ACPI: EC: non-query interrupt received, switching to interrupt mode
Mar 18 11:02:37 ubuntu kernel: [    0.484135] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Mar 18 11:02:37 ubuntu kernel: [    0.484135] ACPI: EC: driver started in interrupt mode
Mar 18 11:02:37 ubuntu kernel: [    0.484168] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 18 11:02:37 ubuntu kernel: [    0.484168] PCI: 0000:00:02.0 reg 10 64bit mmio: [f0000000, f03fffff]
Mar 18 11:02:37 ubuntu kernel: [    0.484168] PCI: 0000:00:02.0 reg 18 64bit mmio: [d0000000, dfffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.484168] PCI: 0000:00:02.0 reg 20 io port: [1800, 1807]
Mar 18 11:02:37 ubuntu kernel: [    0.484168] PCI: 0000:00:02.1 reg 10 64bit mmio: [f0400000, f04fffff]
Mar 18 11:02:37 ubuntu kernel: [    0.484195] PCI: 0000:00:1a.0 reg 20 io port: [1820, 183f]
Mar 18 11:02:37 ubuntu kernel: [    0.484250] PCI: 0000:00:1a.1 reg 20 io port: [1840, 185f]
Mar 18 11:02:37 ubuntu kernel: [    0.484306] PCI: 0000:00:1a.2 reg 20 io port: [1860, 187f]
Mar 18 11:02:37 ubuntu kernel: [    0.484365] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f0a04800, f0a04bff]
Mar 18 11:02:37 ubuntu kernel: [    0.484409] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.484413] pci 0000:00:1a.7: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.484441] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f0a00000, f0a03fff]
Mar 18 11:02:37 ubuntu kernel: [    0.484474] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.484477] pci 0000:00:1b.0: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.484521] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.484524] pci 0000:00:1c.0: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.484566] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.484569] pci 0000:00:1c.1: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.484611] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.484614] pci 0000:00:1c.2: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.484656] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.484659] pci 0000:00:1c.3: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.484701] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.484704] pci 0000:00:1c.4: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.484745] PCI: 0000:00:1d.0 reg 20 io port: [1880, 189f]
Mar 18 11:02:37 ubuntu kernel: [    0.484801] PCI: 0000:00:1d.1 reg 20 io port: [18a0, 18bf]
Mar 18 11:02:37 ubuntu kernel: [    0.484857] PCI: 0000:00:1d.2 reg 20 io port: [18c0, 18df]
Mar 18 11:02:37 ubuntu kernel: [    0.484917] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f0a04c00, f0a04fff]
Mar 18 11:02:37 ubuntu kernel: [    0.484960] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.484963] pci 0000:00:1d.7: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.485101] PCI: 0000:00:1f.2 reg 10 io port: [1818, 181f]
Mar 18 11:02:37 ubuntu kernel: [    0.485106] PCI: 0000:00:1f.2 reg 14 io port: [180c, 180f]
Mar 18 11:02:37 ubuntu kernel: [    0.485111] PCI: 0000:00:1f.2 reg 18 io port: [1810, 1817]
Mar 18 11:02:37 ubuntu kernel: [    0.485116] PCI: 0000:00:1f.2 reg 1c io port: [1808, 180b]
Mar 18 11:02:37 ubuntu kernel: [    0.485121] PCI: 0000:00:1f.2 reg 20 io port: [18e0, 18ff]
Mar 18 11:02:37 ubuntu kernel: [    0.485125] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f0a04000, f0a047ff]
Mar 18 11:02:37 ubuntu kernel: [    0.485146] pci 0000:00:1f.2: PME# supported from D3hot
Mar 18 11:02:37 ubuntu kernel: [    0.485149] pci 0000:00:1f.2: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.485166] PCI: 0000:00:1f.3 reg 10 64bit mmio: [0, ff]
Mar 18 11:02:37 ubuntu kernel: [    0.485178] PCI: 0000:00:1f.3 reg 20 io port: [1c00, 1c1f]
Mar 18 11:02:37 ubuntu kernel: [    0.485262] PCI: 0000:02:00.0 reg 10 64bit mmio: [f0500000, f0501fff]
Mar 18 11:02:37 ubuntu kernel: [    0.485338] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.485344] pci 0000:02:00.0: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.485376] PCI: bridge 0000:00:1c.0 32bit mmio: [f0500000, f05fffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488063] PCI: bridge 0000:00:1c.1 io port: [2000, 2fff]
Mar 18 11:02:37 ubuntu kernel: [    0.488067] PCI: bridge 0000:00:1c.1 32bit mmio: [b8000000, bbffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488072] PCI: bridge 0000:00:1c.1 64bit mmio pref: [c8000000, cbffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488107] PCI: bridge 0000:00:1c.2 io port: [3000, 3fff]
Mar 18 11:02:37 ubuntu kernel: [    0.488110] PCI: bridge 0000:00:1c.2 32bit mmio: [b0000000, b3ffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488115] PCI: bridge 0000:00:1c.2 64bit mmio pref: [c0000000, c3ffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488158] PCI: 0000:08:00.0 reg 10 io port: [4000, 40ff]
Mar 18 11:02:37 ubuntu kernel: [    0.488177] PCI: 0000:08:00.0 reg 18 64bit mmio: [f0600000, f0600fff]
Mar 18 11:02:37 ubuntu kernel: [    0.488190] PCI: 0000:08:00.0 reg 20 64bit mmio: [f0b00000, f0b0ffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488197] PCI: 0000:08:00.0 reg 30 32bit mmio: [0, 1ffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488223] pci 0000:08:00.0: supports D1
Mar 18 11:02:37 ubuntu kernel: [    0.488224] pci 0000:08:00.0: supports D2
Mar 18 11:02:37 ubuntu kernel: [    0.488226] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 18 11:02:37 ubuntu kernel: [    0.488230] pci 0000:08:00.0: PME# disabled
Mar 18 11:02:37 ubuntu kernel: [    0.488260] PCI: bridge 0000:00:1c.3 io port: [4000, 4fff]
Mar 18 11:02:37 ubuntu kernel: [    0.488263] PCI: bridge 0000:00:1c.3 32bit mmio: [f0600000, f06fffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488268] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f0b00000, f0bfffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488310] PCI: 0000:09:00.0 reg 10 32bit mmio: [f0700000, f07000ff]
Mar 18 11:02:37 ubuntu kernel: [    0.488417] PCI: 0000:09:00.2 reg 10 32bit mmio: [f0700400, f07004ff]
Mar 18 11:02:37 ubuntu kernel: [    0.488518] PCI: 0000:09:00.3 reg 10 32bit mmio: [f0700800, f07008ff]
Mar 18 11:02:37 ubuntu kernel: [    0.488621] PCI: 0000:09:00.4 reg 10 32bit mmio: [f0700c00, f0700cff]
Mar 18 11:02:37 ubuntu kernel: [    0.488722] PCI: bridge 0000:00:1c.4 32bit mmio: [f0700000, f07fffff]
Mar 18 11:02:37 ubuntu kernel: [    0.488769] pci 0000:00:1e.0: transparent bridge
Mar 18 11:02:37 ubuntu kernel: [    0.488805] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 18 11:02:37 ubuntu kernel: [    0.489058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Mar 18 11:02:37 ubuntu kernel: [    0.489285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Mar 18 11:02:37 ubuntu kernel: [    0.489398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Mar 18 11:02:37 ubuntu kernel: [    0.489510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Mar 18 11:02:37 ubuntu kernel: [    0.489621] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Mar 18 11:02:37 ubuntu kernel: [    0.489733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Mar 18 11:02:37 ubuntu kernel: [    0.500602] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Mar 18 11:02:37 ubuntu kernel: [    0.500602] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Mar 18 11:02:37 ubuntu kernel: [    0.500602] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Mar 18 11:02:37 ubuntu kernel: [    0.500602] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Mar 18 11:02:37 ubuntu kernel: [    0.500602] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Mar 18 11:02:37 ubuntu kernel: [    0.500683] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Mar 18 11:02:37 ubuntu kernel: [    0.500793] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Mar 18 11:02:37 ubuntu kernel: [    0.500903] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
Mar 18 11:02:37 ubuntu kernel: [    0.504167] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 18 11:02:37 ubuntu kernel: [    0.504183] pnp: PnP ACPI init
Mar 18 11:02:37 ubuntu kernel: [    0.504183] ACPI: bus type pnp registered
Mar 18 11:02:37 ubuntu kernel: [    0.504410] pnp: PnP ACPI: found 11 devices
Mar 18 11:02:37 ubuntu kernel: [    0.504410] ACPI: ACPI bus type pnp unregistered
Mar 18 11:02:37 ubuntu kernel: [    0.504429] PCI: Using ACPI for IRQ routing
Mar 18 11:02:37 ubuntu kernel: [    0.516076] NET: Registered protocol family 8
Mar 18 11:02:37 ubuntu kernel: [    0.516078] NET: Registered protocol family 20
Mar 18 11:02:37 ubuntu kernel: [    0.516089] NetLabel: Initializing
Mar 18 11:02:37 ubuntu kernel: [    0.516089] NetLabel:  domain hash size = 128
Mar 18 11:02:37 ubuntu kernel: [    0.516089] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 18 11:02:37 ubuntu kernel: [    0.516089] NetLabel:  unlabeled traffic allowed by default
Mar 18 11:02:37 ubuntu kernel: [    0.516089] PCI-GART: No AMD northbridge found.
Mar 18 11:02:37 ubuntu kernel: [    0.516089] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Mar 18 11:02:37 ubuntu kernel: [    0.516089] hpet0: 4 64-bit timers, 14318180 Hz
Mar 18 11:02:37 ubuntu kernel: [    0.518086] tracer: 1286 pages allocated for 65536 entries of 80 bytes
Mar 18 11:02:37 ubuntu kernel: [    0.518087]    actual entries 65586
Mar 18 11:02:37 ubuntu kernel: [    0.518163] AppArmor: AppArmor Filesystem Enabled
Mar 18 11:02:37 ubuntu kernel: [    0.520037] Switched to high resolution mode on CPU 0
Mar 18 11:02:37 ubuntu kernel: [    0.520631] Switched to high resolution mode on CPU 1
Mar 18 11:02:37 ubuntu kernel: [    0.528017] system 00:03: iomem range 0xfed00000-0xfed003ff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528023] system 00:05: ioport range 0x680-0x69f has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528025] system 00:05: ioport range 0x480-0x48f has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528027] system 00:05: ioport range 0xffff-0xffff has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528029] system 00:05: ioport range 0xffff-0xffff has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528031] system 00:05: ioport range 0x1000-0x107f has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528033] system 00:05: ioport range 0x1180-0x11ff has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528034] system 00:05: ioport range 0x164e-0x164f has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528036] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528040] system 00:06: ioport range 0x6a0-0x6af has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528042] system 00:06: ioport range 0x6b0-0x6ff has been reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528048] system 00:0a: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528050] system 00:0a: iomem range 0xfed10000-0xfed13fff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528052] system 00:0a: iomem range 0xfed18000-0xfed18fff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528054] system 00:0a: iomem range 0xfed19000-0xfed19fff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528056] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528058] system 00:0a: iomem range 0xfed20000-0xfed3ffff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528060] system 00:0a: iomem range 0xfed40000-0xfed44fff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.528062] system 00:0a: iomem range 0xfed45000-0xfed8ffff could not be reserved
Mar 18 11:02:37 ubuntu kernel: [    0.533002] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Mar 18 11:02:37 ubuntu kernel: [    0.533004] pci 0000:00:1c.0:   IO window: disabled
Mar 18 11:02:37 ubuntu kernel: [    0.533008] pci 0000:00:1c.0:   MEM window: 0xf0500000-0xf05fffff
Mar 18 11:02:37 ubuntu kernel: [    0.533012] pci 0000:00:1c.0:   PREFETCH window: disabled
Mar 18 11:02:37 ubuntu kernel: [    0.533016] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
Mar 18 11:02:37 ubuntu kernel: [    0.533019] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
Mar 18 11:02:37 ubuntu kernel: [    0.533023] pci 0000:00:1c.1:   MEM window: 0xb8000000-0xbbffffff
Mar 18 11:02:37 ubuntu kernel: [    0.533026] pci 0000:00:1c.1:   PREFETCH window: 0x000000c8000000-0x000000cbffffff
Mar 18 11:02:37 ubuntu kernel: [    0.533031] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
Mar 18 11:02:37 ubuntu kernel: [    0.533034] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
Mar 18 11:02:37 ubuntu kernel: [    0.533038] pci 0000:00:1c.2:   MEM window: 0xb0000000-0xb3ffffff
Mar 18 11:02:37 ubuntu kernel: [    0.533041] pci 0000:00:1c.2:   PREFETCH window: 0x000000c0000000-0x000000c3ffffff
Mar 18 11:02:37 ubuntu kernel: [    0.533047] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:08
Mar 18 11:02:37 ubuntu kernel: [    0.533049] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
Mar 18 11:02:37 ubuntu kernel: [    0.533053] pci 0000:00:1c.3:   MEM window: 0xf0600000-0xf06fffff
Mar 18 11:02:37 ubuntu kernel: [    0.533056] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0b00000-0x000000f0bfffff
Mar 18 11:02:37 ubuntu kernel: [    0.533061] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:09
Mar 18 11:02:37 ubuntu kernel: [    0.533063] pci 0000:00:1c.4:   IO window: disabled
Mar 18 11:02:37 ubuntu kernel: [    0.533067] pci 0000:00:1c.4:   MEM window: 0xf0700000-0xf07fffff
Mar 18 11:02:37 ubuntu kernel: [    0.533070] pci 0000:00:1c.4:   PREFETCH window: disabled
Mar 18 11:02:37 ubuntu kernel: [    0.533075] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
Mar 18 11:02:37 ubuntu kernel: [    0.533076] pci 0000:00:1e.0:   IO window: disabled
Mar 18 11:02:37 ubuntu kernel: [    0.533080] pci 0000:00:1e.0:   MEM window: disabled
Mar 18 11:02:37 ubuntu kernel: [    0.533083] pci 0000:00:1e.0:   PREFETCH window: disabled
Mar 18 11:02:37 ubuntu kernel: [    0.533096] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 18 11:02:37 ubuntu kernel: [    0.533100] pci 0000:00:1c.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [    0.533107] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:02:37 ubuntu kernel: [    0.533110] pci 0000:00:1c.1: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [    0.533117] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 18 11:02:37 ubuntu kernel: [    0.533120] pci 0000:00:1c.2: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [    0.533126] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:02:37 ubuntu kernel: [    0.533129] pci 0000:00:1c.3: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [    0.533135] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 18 11:02:37 ubuntu kernel: [    0.533139] pci 0000:00:1c.4: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [    0.533144] pci 0000:00:1e.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [    0.533147] bus: 00 index 0 io port: [0, ffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533148] bus: 00 index 1 mmio: [0, ffffffffffffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533150] bus: 02 index 0 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533151] bus: 02 index 1 mmio: [f0500000, f05fffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533152] bus: 02 index 2 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533153] bus: 02 index 3 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533155] bus: 04 index 0 io port: [2000, 2fff]
Mar 18 11:02:37 ubuntu kernel: [    0.533156] bus: 04 index 1 mmio: [b8000000, bbffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533157] bus: 04 index 2 mmio: [c8000000, cbffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533159] bus: 04 index 3 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533160] bus: 06 index 0 io port: [3000, 3fff]
Mar 18 11:02:37 ubuntu kernel: [    0.533161] bus: 06 index 1 mmio: [b0000000, b3ffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533163] bus: 06 index 2 mmio: [c0000000, c3ffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533164] bus: 06 index 3 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533166] bus: 08 index 0 io port: [4000, 4fff]
Mar 18 11:02:37 ubuntu kernel: [    0.533167] bus: 08 index 1 mmio: [f0600000, f06fffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533168] bus: 08 index 2 mmio: [f0b00000, f0bfffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533169] bus: 08 index 3 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533171] bus: 09 index 0 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533172] bus: 09 index 1 mmio: [f0700000, f07fffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533173] bus: 09 index 2 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533174] bus: 09 index 3 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533176] bus: 0a index 0 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533177] bus: 0a index 1 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533178] bus: 0a index 2 mmio: [0, 0]
Mar 18 11:02:37 ubuntu kernel: [    0.533179] bus: 0a index 3 io port: [0, ffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533181] bus: 0a index 4 mmio: [0, ffffffffffffffff]
Mar 18 11:02:37 ubuntu kernel: [    0.533188] NET: Registered protocol family 2
Mar 18 11:02:37 ubuntu kernel: [    0.572086] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Mar 18 11:02:37 ubuntu kernel: [    0.572697] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Mar 18 11:02:37 ubuntu kernel: [    0.574394] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Mar 18 11:02:37 ubuntu kernel: [    0.574878] TCP: Hash tables configured (established 262144 bind 65536)
Mar 18 11:02:37 ubuntu kernel: [    0.574880] TCP reno registered
Mar 18 11:02:37 ubuntu kernel: [    0.584103] NET: Registered protocol family 1
Mar 18 11:02:37 ubuntu kernel: [    0.584205] checking if image is initramfs... it is
Mar 18 11:02:37 ubuntu kernel: [    1.224576] Freeing initrd memory: 8377k freed
Mar 18 11:02:37 ubuntu kernel: [    1.228428] audit: initializing netlink socket (disabled)
Mar 18 11:02:37 ubuntu kernel: [    1.228447] type=2000 audit(1237388524.228:1): initialized
Mar 18 11:02:37 ubuntu kernel: [    1.233550] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Mar 18 11:02:37 ubuntu kernel: [    1.235443] VFS: Disk quotas dquot_6.5.1
Mar 18 11:02:37 ubuntu kernel: [    1.235508] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Mar 18 11:02:37 ubuntu kernel: [    1.235586] msgmni has been set to 3939
Mar 18 11:02:37 ubuntu kernel: [    1.235682] io scheduler noop registered
Mar 18 11:02:37 ubuntu kernel: [    1.235684] io scheduler anticipatory registered
Mar 18 11:02:37 ubuntu kernel: [    1.235685] io scheduler deadline registered
Mar 18 11:02:37 ubuntu kernel: [    1.235775] io scheduler cfq registered (default)
Mar 18 11:02:37 ubuntu kernel: [    1.235786] pci 0000:00:02.0: Boot video device
Mar 18 11:02:37 ubuntu kernel: [    9.232005] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Mar 18 11:02:37 ubuntu kernel: [   17.232006] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Mar 18 11:02:37 ubuntu kernel: [   17.232215] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   17.232244] pcieport-driver 0000:00:1c.0: found MSI capability
Mar 18 11:02:37 ubuntu kernel: [   17.232275] pci_express 0000:00:1c.0:pcie00: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232307] pci_express 0000:00:1c.0:pcie02: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232336] pci_express 0000:00:1c.0:pcie03: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232410] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   17.232438] pcieport-driver 0000:00:1c.1: found MSI capability
Mar 18 11:02:37 ubuntu kernel: [   17.232466] pci_express 0000:00:1c.1:pcie00: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232494] pci_express 0000:00:1c.1:pcie02: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232523] pci_express 0000:00:1c.1:pcie03: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232593] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   17.232621] pcieport-driver 0000:00:1c.2: found MSI capability
Mar 18 11:02:37 ubuntu kernel: [   17.232649] pci_express 0000:00:1c.2:pcie00: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232677] pci_express 0000:00:1c.2:pcie02: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232706] pci_express 0000:00:1c.2:pcie03: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232777] pcieport-driver 0000:00:1c.3: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   17.232805] pcieport-driver 0000:00:1c.3: found MSI capability
Mar 18 11:02:37 ubuntu kernel: [   17.232833] pci_express 0000:00:1c.3:pcie00: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232861] pci_express 0000:00:1c.3:pcie02: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232892] pci_express 0000:00:1c.3:pcie03: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.232962] pcieport-driver 0000:00:1c.4: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   17.232990] pcieport-driver 0000:00:1c.4: found MSI capability
Mar 18 11:02:37 ubuntu kernel: [   17.233022] pci_express 0000:00:1c.4:pcie00: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.233053] pci_express 0000:00:1c.4:pcie02: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.233081] pci_express 0000:00:1c.4:pcie03: allocate port service
Mar 18 11:02:37 ubuntu kernel: [   17.257581] hpet_resources: 0xfed00000 is busy
Mar 18 11:02:37 ubuntu kernel: [   17.257650] Linux agpgart interface v0.103
Mar 18 11:02:37 ubuntu kernel: [   17.257654] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar 18 11:02:37 ubuntu kernel: [   17.259304] brd: module loaded
Mar 18 11:02:37 ubuntu kernel: [   17.259356] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar 18 11:02:37 ubuntu kernel: [   17.259444] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 18 11:02:37 ubuntu kernel: [   17.263454] i8042.c: Detected active multiplexing controller, rev 1.1.
Mar 18 11:02:37 ubuntu kernel: [   17.266103] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 18 11:02:37 ubuntu kernel: [   17.266107] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Mar 18 11:02:37 ubuntu kernel: [   17.266109] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Mar 18 11:02:37 ubuntu kernel: [   17.266110] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Mar 18 11:02:37 ubuntu kernel: [   17.266112] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Mar 18 11:02:37 ubuntu kernel: [   17.285148] mice: PS/2 mouse device common for all mice
Mar 18 11:02:37 ubuntu kernel: [   17.285243] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Mar 18 11:02:37 ubuntu kernel: [   17.285265] rtc0: alarms up to one month, y3k, hpet irqs
Mar 18 11:02:37 ubuntu kernel: [   17.285291] cpuidle: using governor ladder
Mar 18 11:02:37 ubuntu kernel: [   17.285293] cpuidle: using governor menu
Mar 18 11:02:37 ubuntu kernel: [   17.285585] TCP cubic registered
Mar 18 11:02:37 ubuntu kernel: [   17.285735] registered taskstats version 1
Mar 18 11:02:37 ubuntu kernel: [   17.285854]   Magic number: 1:884:32
Mar 18 11:02:37 ubuntu kernel: [   17.285862] tty ttydf: hash matches
Mar 18 11:02:37 ubuntu kernel: [   17.285974] rtc_cmos 00:07: setting system clock to 2009-03-18 15:02:21 UTC (1237388541)
Mar 18 11:02:37 ubuntu kernel: [   17.285976] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 18 11:02:37 ubuntu kernel: [   17.285977] EDD information not available.
Mar 18 11:02:37 ubuntu kernel: [   17.286048] Freeing unused kernel memory: 540k freed
Mar 18 11:02:37 ubuntu kernel: [   17.286222] Write protecting the kernel read-only data: 4352k
Mar 18 11:02:37 ubuntu kernel: [   17.320758] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar 18 11:02:37 ubuntu kernel: [   17.401671] fuse init (API version 7.9)
Mar 18 11:02:37 ubuntu kernel: [   17.459577] ACPI: SSDT 7DB1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Mar 18 11:02:37 ubuntu kernel: [   17.459993] ACPI: SSDT 7DB18620, 05C5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Mar 18 11:02:37 ubuntu kernel: [   17.620049] Monitor-Mwait will be used to enter C-1 state
Mar 18 11:02:37 ubuntu kernel: [   17.620052] Monitor-Mwait will be used to enter C-2 state
Mar 18 11:02:37 ubuntu kernel: [   17.620054] Monitor-Mwait will be used to enter C-3 state
Mar 18 11:02:37 ubuntu kernel: [   17.620199] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Mar 18 11:02:37 ubuntu kernel: [   17.620243] processor ACPI0007:00: registered as cooling_device0
Mar 18 11:02:37 ubuntu kernel: [   17.620246] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar 18 11:02:37 ubuntu kernel: [   17.620679] ACPI: SSDT 7DB19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
Mar 18 11:02:37 ubuntu kernel: [   17.621027] ACPI: SSDT 7DB19F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
Mar 18 11:02:37 ubuntu kernel: [   17.622043] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Mar 18 11:02:37 ubuntu kernel: [   17.622078] processor ACPI0007:01: registered as cooling_device1
Mar 18 11:02:37 ubuntu kernel: [   17.622081] ACPI: Processor [CPU1] (supports 8 throttling states)
Mar 18 11:02:37 ubuntu kernel: [   17.622192] Marking TSC unstable due to TSC halts in idle
Mar 18 11:02:37 ubuntu kernel: [   17.631024] thermal LNXTHERM:01: registered as thermal_zone0
Mar 18 11:02:37 ubuntu kernel: [   17.643409] ACPI: Thermal Zone [THM0] (26 C)
Mar 18 11:02:37 ubuntu kernel: [   17.811678] usbcore: registered new interface driver usbfs
Mar 18 11:02:37 ubuntu kernel: [   17.811698] usbcore: registered new interface driver hub
Mar 18 11:02:37 ubuntu kernel: [   17.817292] usbcore: registered new device driver usb
Mar 18 11:02:37 ubuntu kernel: [   17.824228] USB Universal Host Controller Interface driver v3.0
Mar 18 11:02:37 ubuntu kernel: [   17.824271] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:02:37 ubuntu kernel: [   17.824279] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   17.824282] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Mar 18 11:02:37 ubuntu kernel: [   17.824324] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Mar 18 11:02:37 ubuntu kernel: [   17.824356] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
Mar 18 11:02:37 ubuntu kernel: [   17.824474] usb usb1: configuration #1 chosen from 1 choice
Mar 18 11:02:37 ubuntu kernel: [   17.824495] hub 1-0:1.0: USB hub found
Mar 18 11:02:37 ubuntu kernel: [   17.824500] hub 1-0:1.0: 2 ports detected
Mar 18 11:02:37 ubuntu kernel: [   17.833434] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Mar 18 11:02:37 ubuntu kernel: [   17.895835] No dock devices found.
Mar 18 11:02:37 ubuntu kernel: [   17.910724] SCSI subsystem initialized
Mar 18 11:02:37 ubuntu kernel: [   17.927496] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 18 11:02:37 ubuntu kernel: [   17.927504] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   17.927508] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Mar 18 11:02:37 ubuntu kernel: [   17.927535] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Mar 18 11:02:37 ubuntu kernel: [   17.927566] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
Mar 18 11:02:37 ubuntu kernel: [   17.927639] usb usb2: configuration #1 chosen from 1 choice
Mar 18 11:02:37 ubuntu kernel: [   17.927658] hub 2-0:1.0: USB hub found
Mar 18 11:02:37 ubuntu kernel: [   17.927664] hub 2-0:1.0: 2 ports detected
Mar 18 11:02:37 ubuntu kernel: [   17.941142] libata version 3.00 loaded.
Mar 18 11:02:37 ubuntu kernel: [   18.029227] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:02:37 ubuntu kernel: [   18.029237] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   18.029240] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Mar 18 11:02:37 ubuntu kernel: [   18.029260] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
Mar 18 11:02:37 ubuntu kernel: [   18.029294] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
Mar 18 11:02:37 ubuntu kernel: [   18.029366] usb usb3: configuration #1 chosen from 1 choice
Mar 18 11:02:37 ubuntu kernel: [   18.029385] hub 3-0:1.0: USB hub found
Mar 18 11:02:37 ubuntu kernel: [   18.029392] hub 3-0:1.0: 2 ports detected
Mar 18 11:02:37 ubuntu kernel: [   18.133514] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:02:37 ubuntu kernel: [   18.133530] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   18.133533] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Mar 18 11:02:37 ubuntu kernel: [   18.133554] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
Mar 18 11:02:37 ubuntu kernel: [   18.137446] ehci_hcd 0000:00:1a.7: debug port 1
Mar 18 11:02:37 ubuntu kernel: [   18.137451] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Mar 18 11:02:37 ubuntu kernel: [   18.137457] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf0a04800
Mar 18 11:02:37 ubuntu kernel: [   18.153016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 18 11:02:37 ubuntu kernel: [   18.153123] usb usb4: configuration #1 chosen from 1 choice
Mar 18 11:02:37 ubuntu kernel: [   18.153145] hub 4-0:1.0: USB hub found
Mar 18 11:02:37 ubuntu kernel: [   18.153151] hub 4-0:1.0: 6 ports detected
Mar 18 11:02:37 ubuntu kernel: [   18.257522] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 18 11:02:37 ubuntu kernel: [   18.257531] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   18.257535] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar 18 11:02:37 ubuntu kernel: [   18.257557] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Mar 18 11:02:37 ubuntu kernel: [   18.257588] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
Mar 18 11:02:37 ubuntu kernel: [   18.257661] usb usb5: configuration #1 chosen from 1 choice
Mar 18 11:02:37 ubuntu kernel: [   18.257681] hub 5-0:1.0: USB hub found
Mar 18 11:02:37 ubuntu kernel: [   18.257687] hub 5-0:1.0: 2 ports detected
Mar 18 11:02:37 ubuntu kernel: [   18.360278] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:02:37 ubuntu kernel: [   18.360284] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   18.360287] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar 18 11:02:37 ubuntu kernel: [   18.360307] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Mar 18 11:02:37 ubuntu kernel: [   18.360329] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
Mar 18 11:02:37 ubuntu kernel: [   18.360392] usb usb6: configuration #1 chosen from 1 choice
Mar 18 11:02:37 ubuntu kernel: [   18.360413] hub 6-0:1.0: USB hub found
Mar 18 11:02:37 ubuntu kernel: [   18.360418] hub 6-0:1.0: 2 ports detected
Mar 18 11:02:37 ubuntu kernel: [   18.464947] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 18 11:02:37 ubuntu kernel: [   18.464952] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   18.464954] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar 18 11:02:37 ubuntu kernel: [   18.464975] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Mar 18 11:02:37 ubuntu kernel: [   18.465008] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
Mar 18 11:02:37 ubuntu kernel: [   18.465067] usb usb7: configuration #1 chosen from 1 choice
Mar 18 11:02:37 ubuntu kernel: [   18.465087] hub 7-0:1.0: USB hub found
Mar 18 11:02:37 ubuntu kernel: [   18.465092] hub 7-0:1.0: 2 ports detected
Mar 18 11:02:37 ubuntu kernel: [   18.500033] Clocksource tsc unstable (delta = -226761715 ns)
Mar 18 11:02:37 ubuntu kernel: [   18.569038] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 18 11:02:37 ubuntu kernel: [   18.569050] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   18.569053] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar 18 11:02:37 ubuntu kernel: [   18.569078] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
Mar 18 11:02:37 ubuntu kernel: [   18.572967] ehci_hcd 0000:00:1d.7: debug port 1
Mar 18 11:02:37 ubuntu kernel: [   18.572971] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Mar 18 11:02:37 ubuntu kernel: [   18.572976] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0a04c00
Mar 18 11:02:37 ubuntu kernel: [   18.585040] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 18 11:02:37 ubuntu kernel: [   18.585116] usb usb8: configuration #1 chosen from 1 choice
Mar 18 11:02:37 ubuntu kernel: [   18.585147] hub 8-0:1.0: USB hub found
Mar 18 11:02:37 ubuntu kernel: [   18.585155] hub 8-0:1.0: 6 ports detected
Mar 18 11:02:37 ubuntu kernel: [   18.690160] ahci 0000:00:1f.2: version 3.0
Mar 18 11:02:37 ubuntu kernel: [   18.690173] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:02:37 ubuntu kernel: [   18.690262] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
Mar 18 11:02:37 ubuntu kernel: [   18.690265] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pio slum part 
Mar 18 11:02:37 ubuntu kernel: [   18.690269] ahci 0000:00:1f.2: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   18.690467] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Mar 18 11:02:37 ubuntu kernel: [   18.690482] r8169 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:02:37 ubuntu kernel: [   18.690496] r8169 0000:08:00.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   18.690767] eth0: RTL8168c/8111c at 0xffffc2000033a000, 00:90:f5:80:00:de, XID 3c2000c0 IRQ 2297
Mar 18 11:02:37 ubuntu kernel: [   18.693382] scsi0 : ahci
Mar 18 11:02:37 ubuntu kernel: [   18.693466] scsi1 : ahci
Mar 18 11:02:37 ubuntu kernel: [   18.693517] scsi2 : ahci
Mar 18 11:02:37 ubuntu kernel: [   18.693756] scsi3 : ahci
Mar 18 11:02:37 ubuntu kernel: [   18.693806] scsi4 : ahci
Mar 18 11:02:37 ubuntu kernel: [   18.693849] scsi5 : ahci
Mar 18 11:02:37 ubuntu kernel: [   18.693887] ata1: SATA max UDMA/133 abar m2048@0xf0a04000 port 0xf0a04100 irq 2298
Mar 18 11:02:37 ubuntu kernel: [   18.693889] ata2: SATA max UDMA/133 abar m2048@0xf0a04000 port 0xf0a04180 irq 2298
Mar 18 11:02:37 ubuntu kernel: [   18.693891] ata3: DUMMY
Mar 18 11:02:37 ubuntu kernel: [   18.693892] ata4: DUMMY
Mar 18 11:02:37 ubuntu kernel: [   18.693894] ata5: SATA max UDMA/133 abar m2048@0xf0a04000 port 0xf0a04300 irq 2298
Mar 18 11:02:37 ubuntu kernel: [   18.693896] ata6: SATA max UDMA/133 abar m2048@0xf0a04000 port 0xf0a04380 irq 2298
Mar 18 11:02:37 ubuntu kernel: [   19.012053] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 18 11:02:37 ubuntu kernel: [   19.012929] ata1.00: ATA-8: Hitachi HTS543225L9A300, FBEOC40C, max UDMA/133
Mar 18 11:02:37 ubuntu kernel: [   19.012931] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Mar 18 11:02:37 ubuntu kernel: [   19.014005] ata1.00: configured for UDMA/133
Mar 18 11:02:37 ubuntu kernel: [   19.332048] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 18 11:02:37 ubuntu kernel: [   19.345262] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TM00, max UDMA/100, ATAPI AN
Mar 18 11:02:37 ubuntu kernel: [   19.345265] ata2.00: applying bridge limits
Mar 18 11:02:37 ubuntu kernel: [   19.359356] ata2.00: configured for UDMA/100
Mar 18 11:02:37 ubuntu kernel: [   19.676045] ata5: SATA link down (SStatus 0 SControl 300)
Mar 18 11:02:37 ubuntu kernel: [   19.996184] ata6: SATA link down (SStatus 0 SControl 300)
Mar 18 11:02:37 ubuntu kernel: [   19.996281] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
Mar 18 11:02:37 ubuntu kernel: [   19.998529] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TM00 PQ: 0 ANSI: 5
Mar 18 11:02:37 ubuntu kernel: [   20.003765] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Mar 18 11:02:37 ubuntu kernel: [   20.003798] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Mar 18 11:02:37 ubuntu kernel: [   20.014863] Driver 'sr' needs updating - please use bus_type methods
Mar 18 11:02:37 ubuntu kernel: [   20.019919] Driver 'sd' needs updating - please use bus_type methods
Mar 18 11:02:37 ubuntu kernel: [   20.019994] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 18 11:02:37 ubuntu kernel: [   20.020022] sd 0:0:0:0: [sda] Write Protect is off
Mar 18 11:02:37 ubuntu kernel: [   20.020024] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 18 11:02:37 ubuntu kernel: [   20.020044] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 18 11:02:37 ubuntu kernel: [   20.020094] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 18 11:02:37 ubuntu kernel: [   20.020106] sd 0:0:0:0: [sda] Write Protect is off
Mar 18 11:02:37 ubuntu kernel: [   20.020107] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 18 11:02:37 ubuntu kernel: [   20.020127] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 18 11:02:37 ubuntu kernel: [   20.020130]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 18 11:02:37 ubuntu kernel: [   20.026598] Uniform CD-ROM driver Revision: 3.20
Mar 18 11:02:37 ubuntu kernel: [   20.026685] sr 1:0:0:0: Attached scsi CD-ROM sr0
Mar 18 11:02:37 ubuntu kernel: [   20.375669]  sda1 sda2 sda3
Mar 18 11:02:37 ubuntu kernel: [   20.375829] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 18 11:02:37 ubuntu kernel: [   20.543065] PM: Starting manual resume from disk
Mar 18 11:02:37 ubuntu kernel: [   20.543068] PM: Resume from partition 8:2
Mar 18 11:02:37 ubuntu kernel: [   20.543069] PM: Checking hibernation image.
Mar 18 11:02:37 ubuntu kernel: [   20.543225] PM: Resume from disk failed.
Mar 18 11:02:37 ubuntu kernel: [   20.573422] kjournald starting.  Commit interval 5 seconds
Mar 18 11:02:37 ubuntu kernel: [   20.573441] EXT3-fs: mounted filesystem with ordered data mode.
Mar 18 11:02:37 ubuntu kernel: [   27.586527] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 18 11:02:37 ubuntu kernel: [   27.612107] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Mar 18 11:02:37 ubuntu kernel: [   27.612190] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
Mar 18 11:02:37 ubuntu kernel: [   27.612192] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Mar 18 11:02:37 ubuntu kernel: [   27.612193] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Mar 18 11:02:37 ubuntu kernel: [   27.957192] udevd version 124 started
Mar 18 11:02:37 ubuntu kernel: [   28.127723] agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset
Mar 18 11:02:37 ubuntu kernel: [   28.128546] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Mar 18 11:02:37 ubuntu kernel: [   28.189330] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Mar 18 11:02:37 ubuntu kernel: [   28.206004] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Mar 18 11:02:37 ubuntu kernel: [   28.232055] ACPI: Power Button (FF) [PWRF]
Mar 18 11:02:37 ubuntu kernel: [   28.232168] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Mar 18 11:02:37 ubuntu kernel: [   28.232978] ACPI: Lid Switch [LID0]
Mar 18 11:02:37 ubuntu kernel: [   28.233020] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Mar 18 11:02:37 ubuntu kernel: [   28.260022] ACPI: Power Button (CM) [PWRB]
Mar 18 11:02:37 ubuntu kernel: [   28.260079] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
Mar 18 11:02:37 ubuntu kernel: [   28.292028] ACPI: Sleep Button (CM) [SLPB]
Mar 18 11:02:37 ubuntu kernel: [   28.309258] ACPI: Battery Slot [BAT0] (battery present)
Mar 18 11:02:37 ubuntu kernel: [   28.508733] ACPI: AC Adapter [ADP0] (on-line)
Mar 18 11:02:37 ubuntu kernel: [   28.509554] ACPI: WMI: Mapper loaded
Mar 18 11:02:37 ubuntu kernel: [   28.515025] acpi device:06: registered as cooling_device2
Mar 18 11:02:37 ubuntu kernel: [   28.515159] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input6
Mar 18 11:02:37 ubuntu kernel: [   28.541042] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Mar 18 11:02:37 ubuntu kernel: [   28.577406] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 18 11:02:37 ubuntu kernel: [   28.585543] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 18 11:02:37 ubuntu kernel: [   28.856052] cfg80211: Using static regulatory domain info
Mar 18 11:02:37 ubuntu kernel: [   28.856055] cfg80211: Regulatory domain: US
Mar 18 11:02:37 ubuntu kernel: [   28.856057] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 18 11:02:37 ubuntu kernel: [   28.856059] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
Mar 18 11:02:37 ubuntu kernel: [   28.856060] ^I(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 18 11:02:37 ubuntu kernel: [   28.856062] ^I(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 18 11:02:37 ubuntu kernel: [   28.856064] ^I(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 18 11:02:37 ubuntu kernel: [   28.856066] ^I(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 18 11:02:37 ubuntu kernel: [   28.856067] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
Mar 18 11:02:37 ubuntu kernel: [   28.856069] cfg80211: Calling CRDA for country: US
Mar 18 11:02:37 ubuntu kernel: [   28.908587] sdhci: Secure Digital Host Controller Interface driver
Mar 18 11:02:37 ubuntu kernel: [   28.908590] sdhci: Copyright(c) Pierre Ossman
Mar 18 11:02:37 ubuntu kernel: [   28.941126] sdhci-pci 0000:09:00.0: SDHCI controller found [197b:2382] (rev 0)
Mar 18 11:02:37 ubuntu kernel: [   28.941145] sdhci-pci 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:02:37 ubuntu kernel: [   28.941179] sdhci-pci 0000:09:00.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   28.944009] mmc0: SDHCI controller on PCI [0000:09:00.0] using ADMA
Mar 18 11:02:37 ubuntu kernel: [   28.944021] sdhci-pci 0000:09:00.2: SDHCI controller found [197b:2381] (rev 0)
Mar 18 11:02:37 ubuntu kernel: [   28.944037] sdhci-pci 0000:09:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:02:37 ubuntu kernel: [   28.944045] sdhci-pci 0000:09:00.2: Refusing to bind to secondary interface.
Mar 18 11:02:37 ubuntu kernel: [   28.944050] sdhci-pci 0000:09:00.2: PCI INT A disabled
Mar 18 11:02:37 ubuntu kernel: [   29.276687] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Mar 18 11:02:37 ubuntu kernel: [   29.276689] iwlagn: Copyright(c) 2003-2008 Intel Corporation
Mar 18 11:02:37 ubuntu kernel: [   29.276773] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:02:37 ubuntu kernel: [   29.276780] iwlagn 0000:02:00.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   29.276799] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
Mar 18 11:02:37 ubuntu kernel: [   29.322048] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
Mar 18 11:02:37 ubuntu kernel: [   29.322195] iwlagn 0000:02:00.0: PCI INT A disabled
Mar 18 11:02:37 ubuntu kernel: [   29.322551] phy0: Selected rate control algorithm 'iwl-agn-rs'
Mar 18 11:02:37 ubuntu kernel: [   29.703430] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar 18 11:02:37 ubuntu kernel: [   29.703455] HDA Intel 0000:00:1b.0: setting latency timer to 64
Mar 18 11:02:37 ubuntu kernel: [   29.781119] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000
Mar 18 11:02:37 ubuntu kernel: [   29.817621] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Mar 18 11:02:37 ubuntu kernel: [   30.416210] lp: driver loaded but no devices found
Mar 18 11:02:37 ubuntu kernel: [   30.573487] Adding 1929676k swap on /dev/sda2.  Priority:-1 extents:1 across:1929676k
Mar 18 11:02:37 ubuntu kernel: [   31.410747] EXT3 FS on sda1, internal journal
Mar 18 11:02:37 ubuntu kernel: [   32.435318] kjournald starting.  Commit interval 5 seconds
Mar 18 11:02:37 ubuntu kernel: [   32.439033] EXT3 FS on sda3, internal journal
Mar 18 11:02:37 ubuntu kernel: [   32.439039] EXT3-fs: mounted filesystem with ordered data mode.
Mar 18 11:02:37 ubuntu kernel: [   32.629217] type=1505 audit(1237388556.373:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4369
Mar 18 11:02:37 ubuntu kernel: [   32.731843] type=1505 audit(1237388556.473:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4374
Mar 18 11:02:37 ubuntu kernel: [   32.732023] type=1505 audit(1237388556.477:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4374
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: Successfully dropped root privileges.
Mar 18 11:02:38 ubuntu kernel: [   34.497747] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: avahi-daemon 0.6.23 starting up.
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: Successfully called chroot().
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: Successfully dropped remaining capabilities.
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: No service file found in /etc/avahi/services.
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: Network interface enumeration completed.
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: Registering HINFO record with values 'X86_64'/'LINUX'.
Mar 18 11:02:38 ubuntu avahi-daemon[5010]: Server startup complete. Host name is ubuntu.local. Local service cookie is 824672140.
Mar 18 11:02:38 ubuntu kernel: [   34.867797] NET: Registered protocol family 10
Mar 18 11:02:38 ubuntu kernel: [   34.868503] lo: Disabled Privacy Extensions
Mar 18 11:02:38 ubuntu kernel: [   35.187807] ppdev: user-space parallel port driver
Mar 18 11:02:40 ubuntu chipcardd[5386]: chipcardd.c:  738: Chipcardd v4.1.3.0stable started.
Mar 18 11:02:40 ubuntu chipcardd[5386]: chipcardd.c:  740: LibSYSFS supported.
Mar 18 11:02:40 ubuntu chipcardd[5390]: devicemanager.c: 3373: Changes in hardware list
Mar 18 11:02:41 ubuntu anacron[5643]: Anacron 2.3 started on 2009-03-18
Mar 18 11:02:41 ubuntu anacron[5643]: Will run job `cron.daily' in 5 min.
Mar 18 11:02:41 ubuntu anacron[5643]: Jobs will be executed sequentially
Mar 18 11:02:44 ubuntu acpid: client connected from 5861[111:123] 
Mar 18 11:02:44 ubuntu bluetoothd[5911]: Bluetooth daemon
Mar 18 11:02:44 ubuntu kernel: [   41.060121] Bluetooth: Core ver 2.13
Mar 18 11:02:44 ubuntu kernel: [   41.060389] NET: Registered protocol family 31
Mar 18 11:02:44 ubuntu kernel: [   41.060392] Bluetooth: HCI device and connection manager initialized
Mar 18 11:02:44 ubuntu kernel: [   41.060394] Bluetooth: HCI socket layer initialized
Mar 18 11:02:44 ubuntu bluetoothd[5911]: Starting SDP server
Mar 18 11:02:44 ubuntu kernel: [   41.078124] Bluetooth: L2CAP ver 2.11
Mar 18 11:02:44 ubuntu kernel: [   41.078128] Bluetooth: L2CAP socket layer initialized
Mar 18 11:02:44 ubuntu kernel: [   41.085508] Bluetooth: SCO (Voice Link) ver 0.6
Mar 18 11:02:44 ubuntu kernel: [   41.085512] Bluetooth: SCO socket layer initialized
Mar 18 11:02:44 ubuntu bluetoothd[5911]: Starting experimental netlink support
Mar 18 11:02:44 ubuntu bluetoothd[5911]: Failed to find Bluetooth netlink family
Mar 18 11:02:44 ubuntu bluetoothd[5911]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 18 11:02:44 ubuntu kernel: [   41.111804] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 18 11:02:44 ubuntu kernel: [   41.111808] Bluetooth: BNEP filters: protocol multicast
Mar 18 11:02:44 ubuntu kernel: [   41.191923] Bridge firewalling registered
Mar 18 11:02:44 ubuntu bluetoothd[5911]: bridge pan0 created
Mar 18 11:02:45 ubuntu kernel: [   41.314396] Bluetooth: RFCOMM socket layer initialized
Mar 18 11:02:45 ubuntu kernel: [   41.314688] Bluetooth: RFCOMM TTY layer initialized
Mar 18 11:02:45 ubuntu kernel: [   41.314691] Bluetooth: RFCOMM ver 1.10
Mar 18 11:02:45 ubuntu NetworkManager: <info>  starting... 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  eth0: driver is 'r8169'. 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_90_f5_80_00_de 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  wlan0: driver is 'iwlagn'. 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_21_5c_11_30_b1 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
Mar 18 11:02:45 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
Mar 18 11:02:45 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
Mar 18 11:02:45 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Mar 18 11:02:45 ubuntu nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Mar 18 11:02:45 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_90_f5_80_00_de, iface: eth0): not well known
Mar 18 11:02:45 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_21_5c_11_30_b1, iface: wlan0): not well known
Mar 18 11:02:45 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
Mar 18 11:02:45 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 18 11:02:45 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 18 11:02:45 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (22896128) ... get_connections.
Mar 18 11:02:45 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (22896128) ... get_connections (managed=false): return empty list.
Mar 18 11:02:45 ubuntu NetworkManager: <info>  (wlan0): supplicant manager is now in state 1 (from 0). 
Mar 18 11:02:45 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Mar 18 11:02:46 ubuntu acpid: client connected from 6080[0:0] 
Mar 18 11:02:47 ubuntu kernel: [   43.414144] Netfilter messages via NETLINK v0.30.
Mar 18 11:02:47 ubuntu ntpd[6126]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:53:39 UTC 2009 (1)
Mar 18 11:02:47 ubuntu ntpd[6127]: precision = 1.000 usec
Mar 18 11:02:47 ubuntu ntpd[6127]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Mar 18 11:02:47 ubuntu ntpd[6127]: Listening on interface #1 wildcard, ::#123 Disabled
Mar 18 11:02:47 ubuntu ntpd[6127]: Listening on interface #2 lo, ::1#123 Enabled
Mar 18 11:02:47 ubuntu ntpd[6127]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Mar 18 11:02:47 ubuntu ntpd[6127]: kernel time sync status 0040
Mar 18 11:02:47 ubuntu ntpd[6127]: frequency initialized -40.970 PPM from /var/lib/ntp/ntp.drift
Mar 18 11:02:47 ubuntu ntpd[6146]: signal_no_reset: signal 17 had flags 4000000
Mar 18 11:02:48 ubuntu /usr/sbin/cron[6206]: (CRON) INFO (pidfile fd = 3)
Mar 18 11:02:48 ubuntu /usr/sbin/cron[6207]: (CRON) STARTUP (fork ok)
Mar 18 11:02:48 ubuntu /usr/sbin/cron[6207]: (CRON) INFO (Running @reboot jobs)
Mar 18 11:02:48 ubuntu kernel: [   45.124802] [drm] Initialized drm 1.1.0 20060810
Mar 18 11:02:48 ubuntu kernel: [   45.177191] pci 0000:00:02.0: power state changed by ACPI to D0
Mar 18 11:02:48 ubuntu kernel: [   45.177216] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:02:49 ubuntu kernel: [   45.177226] pci 0000:00:02.0: setting latency timer to 64
Mar 18 11:02:49 ubuntu kernel: [   45.181885] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): bringing up device. 
Mar 18 11:02:49 ubuntu kernel: [   45.425349] r8169: eth0: link down
Mar 18 11:02:49 ubuntu kernel: [   45.425820] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): preparing device. 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (wlan0): bringing up device. 
Mar 18 11:02:49 ubuntu kernel: [   45.445806] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:02:49 ubuntu kernel: [   45.445927] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
Mar 18 11:02:49 ubuntu kernel: [   45.446140] firmware: requesting lbm-iwlwifi-4965-2.ucode
Mar 18 11:02:49 ubuntu nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_90_f5_80_00_de
Mar 18 11:02:49 ubuntu kernel: [   45.533734] iwlagn loaded firmware version 228.57.2.23
Mar 18 11:02:49 ubuntu kernel: [   45.742217] Registered led device: iwl-phy0:radio
Mar 18 11:02:49 ubuntu kernel: [   45.742237] Registered led device: iwl-phy0:assoc
Mar 18 11:02:49 ubuntu kernel: [   45.742250] Registered led device: iwl-phy0:RX
Mar 18 11:02:49 ubuntu kernel: [   45.742262] Registered led device: iwl-phy0:TX
Mar 18 11:02:49 ubuntu kernel: [   45.786353] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (wlan0): preparing device. 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Mar 18 11:02:49 ubuntu NetworkManager: <WARN>  auto_activate_device(): Connection 'Auto eth0' auto-activation failed: (2) Device not managed by NetworkManager 
Mar 18 11:02:49 ubuntu kernel: [   45.880406] NET: Registered protocol family 17
Mar 18 11:02:49 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Mar 18 11:02:49 ubuntu ntpd_initres[6146]: host name not found: clock.psu.edu
Mar 18 11:02:49 ubuntu ntpd_initres[6146]: couldn't resolve `clock.psu.edu', giving up on it
Mar 18 11:02:49 ubuntu ntpd_initres[6146]: host name not found: louie.udel.edu
Mar 18 11:02:49 ubuntu ntpd_initres[6146]: couldn't resolve `louie.udel.edu', giving up on it
Mar 18 11:02:50 ubuntu kernel: [   46.502043] set status page addr 0x02b58000
Mar 18 11:02:51 ubuntu kernel: [   47.699825] wlan0: authenticate with AP 00:14:bf:39:72:e6
Mar 18 11:02:51 ubuntu kernel: [   47.702668] wlan0: authenticated
Mar 18 11:02:51 ubuntu kernel: [   47.702681] wlan0: associate with AP 00:14:bf:39:72:e6
Mar 18 11:02:51 ubuntu kernel: [   47.705288] wlan0: RX AssocResp from 00:14:bf:39:72:e6 (capab=0x401 status=0 aid=5)
Mar 18 11:02:51 ubuntu kernel: [   47.705301] wlan0: associated
Mar 18 11:02:51 ubuntu kernel: [   47.721607] wlan0: disassociating by local choice (reason=3)
Mar 18 11:02:54 ubuntu gdmgreeter[6481]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Mar 18 11:04:16 ubuntu syslogd 1.5.0#2ubuntu6: restart.
Mar 18 11:04:16 ubuntu kernel: Inspecting /boot/System.map-2.6.27-11-generic
Mar 18 11:04:16 ubuntu kernel: Cannot find map file.
Mar 18 11:04:16 ubuntu kernel: Loaded 53049 symbols from 89 modules.
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash 
Mar 18 11:04:16 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 18 11:04:16 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007d6b1000 (usable)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d6b1000 - 000000007d6b7000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d6b7000 - 000000007d7bb000 (usable)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d7bb000 - 000000007d80f000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d80f000 - 000000007d908000 (usable)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007d908000 - 000000007db0f000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db0f000 - 000000007db18000 (usable)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db18000 - 000000007db1f000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db1f000 - 000000007db64000 (usable)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db64000 - 000000007db9f000 (ACPI NVS)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007db9f000 - 000000007dbe5000 (usable)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007dbe5000 - 000000007dbfd000 (ACPI data)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007dbfd000 - 000000007dc00000 (usable)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007dc00000 - 000000007de00000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007e000000 - 0000000080000000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] DMI present.
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Mar 18 11:04:16 ubuntu kernel: [    0.000000] last_pfn = 0x7dc00 max_arch_pfn = 0x3ffffffff
Mar 18 11:04:16 ubuntu kernel: [    0.000000] init_memory_mapping
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  0000000000 - 007dc00000 page 2M
Mar 18 11:04:16 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 7dc00000 @ 10000-13000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] last_map_addr: 7dc00000 end: 7dc00000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] RAMDISK: 377c1000 - 37fef4dd
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: RSDP 000F73B0, 0024 (r2 PTLTD )
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: XSDT 7DBF74FE, 0064 (r1 \Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff \Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff  6040000  LTP        0)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: FACP 7DBE9000, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: DSDT 7DBEA000, 5694 (r2 Intel  CANTIGA   6040000 INTL 20050624)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: FACS 7DB9EFC0, 0040
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: HPET 7DBFCD86, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: MCFG 7DBFCDBE, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: APIC 7DBFCDFA, 0068 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: SLIC 7DBFCE62, 0176 (r1 \Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff \Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff\Uffffffff  6040000  LTP        0)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: SSDT 7DBE8000, 0655 (r1  PmRef    CpuPm     3000 INTL 20050624)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: SSDT 7DBE7000, 0259 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: SSDT 7DBE6000, 020F (r1  PmRef    ApTst     3000 INTL 20050624)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] No NUMA configuration found
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007dc00000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007dc00000
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   NODE_DATA [0000000000011000 - 0000000000015fff]
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   bootmap [0000000000016000 -  0000000000025b7f] pages 10
Mar 18 11:04:16 ubuntu kernel: [    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007dc00000]
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   #2 [0000200000 - 00008b9f5c]    TEXT DATA BSS ==> [0000200000 - 00008b9f5c]
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   #3 [00377c1000 - 0037fef4dd]          RAMDISK ==> [00377c1000 - 0037fef4dd]
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   #4 [000009d400 - 0000100000]    BIOS reserved ==> [000009d400 - 0000100000]
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   #5 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Mar 18 11:04:16 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f7440] 000f7440
Mar 18 11:04:16 ubuntu kernel: [    0.000000]  [ffffe20000000000-ffffe20001ffffff] PMD -> [ffff880001200000-ffff8800031fffff] on node 0
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 18 11:04:16 ubuntu kernel: [    0.000000] early_node_map[8] active PFN ranges
Mar 18 11:04:16 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Mar 18 11:04:16 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007d6b1
Mar 18 11:04:16 ubuntu kernel: [    0.000000]     0: 0x0007d6b7 -> 0x0007d7bb
Mar 18 11:04:16 ubuntu kernel: [    0.000000]     0: 0x0007d80f -> 0x0007d908
Mar 18 11:04:16 ubuntu kernel: [    0.000000]     0: 0x0007db0f -> 0x0007db18
Mar 18 11:04:16 ubuntu kernel: [    0.000000]     0: 0x0007db1f -> 0x0007db64
Mar 18 11:04:16 ubuntu kernel: [    0.000000]     0: 0x0007db9f -> 0x0007dbe5
Mar 18 11:04:16 ubuntu kernel: [    0.000000]     0: 0x0007dbfd -> 0x0007dc00
Mar 18 11:04:16 ubuntu kernel: [    0.000000] On node 0 totalpages: 514258
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   DMA zone: 2092 pages, LIFO batch:0
Mar 18 11:04:16 ubuntu kernel: [    0.000000]   DMA32 zone: 502293 pages, LIFO batch:31
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar 18 11:04:16 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Setting APIC routing to flat
Mar 18 11:04:16 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 18 11:04:16 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007d6b1000 - 000000007d6b7000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007d7bb000 - 000000007d80f000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007d908000 - 000000007db0f000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007db18000 - 000000007db1f000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007db64000 - 000000007db9f000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000007dbe5000 - 000000007dbfd000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
Mar 18 11:04:16 ubuntu kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 504385
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Policy zone: DMA32
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Kernel command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash 
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 18 11:04:16 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Mar 18 11:04:16 ubuntu kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Mar 18 11:04:16 ubuntu kernel: [    0.000000] TSC: using PMTIMER calibration value
Mar 18 11:04:16 ubuntu kernel: [    0.000000] Detected 2393.988 MHz processor.
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Console: colour VGA+ 80x25
Mar 18 11:04:16 ubuntu kernel: [    0.004000] console [tty0] enabled
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Checking aperture...
Mar 18 11:04:16 ubuntu kernel: [    0.004000] No AGP bridge found
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Calgary: detecting Calgary via BIOS EBDA area
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Memory: 2008708k/2060288k available (3116k kernel code, 48324k reserved, 1575k data, 540k init)
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Mar 18 11:04:16 ubuntu kernel: [    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Mar 18 11:04:16 ubuntu kernel: [    0.004000] hpet clockevent registered
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.97 BogoMIPS (lpj=9575952)
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Security Framework initialized
Mar 18 11:04:16 ubuntu kernel: [    0.004000] SELinux:  Disabled at boot.
Mar 18 11:04:16 ubuntu kernel: [    0.004000] AppArmor: AppArmor initialized
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Mount-cache hash table entries: 256
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Initializing cgroup subsys ns
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Initializing cgroup subsys cpuacct
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Initializing cgroup subsys memory
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU: L2 cache: 3072K
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU 0/0 -> Node 0
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 0
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU0: Thermal monitoring enabled (TM2)
Mar 18 11:04:16 ubuntu kernel: [    0.004000] using mwait in idle threads.
Mar 18 11:04:16 ubuntu kernel: [    0.004000] ACPI: Core revision 20080609
Mar 18 11:04:16 ubuntu kernel: [    0.005673] ACPI: Checking initramfs for custom DSDT
Mar 18 11:04:16 ubuntu kernel: [    0.324414] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 18 11:04:16 ubuntu kernel: [    0.364586] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
Mar 18 11:04:16 ubuntu kernel: [    0.364590] Using local APIC timer interrupts.
Mar 18 11:04:16 ubuntu kernel: [    0.368024] APIC timer calibration result 16624919
Mar 18 11:04:16 ubuntu kernel: [    0.368025] Detected 16.624 MHz APIC timer.
Mar 18 11:04:16 ubuntu kernel: [    0.368128] Booting processor 1/1 ip 6000
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Initializing CPU#1
Mar 18 11:04:16 ubuntu kernel: [    0.004000] Calibrating delay using timer specific routine.. 4787.98 BogoMIPS (lpj=9575975)
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU: L2 cache: 3072K
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU 1/1 -> Node 0
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU: Physical Processor ID: 0
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU: Processor Core ID: 1
Mar 18 11:04:16 ubuntu kernel: [    0.004000] CPU1: Thermal monitoring enabled (TM2)
Mar 18 11:04:16 ubuntu kernel: [    0.456586] CPU1: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
Mar 18 11:04:16 ubuntu kernel: [    0.456605] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 18 11:04:16 ubuntu kernel: [    0.460058] Brought up 2 CPUs
Mar 18 11:04:16 ubuntu kernel: [    0.460061] Total of 2 processors activated (9575.96 BogoMIPS).
Mar 18 11:04:16 ubuntu kernel: [    0.460102] CPU0 attaching sched-domain:
Mar 18 11:04:16 ubuntu kernel: [    0.460105]  domain 0: span 0-1 level MC
Mar 18 11:04:16 ubuntu kernel: [    0.460107]   groups: 0 1
Mar 18 11:04:16 ubuntu kernel: [    0.460110]   domain 1: span 0-1 level NODE
Mar 18 11:04:16 ubuntu kernel: [    0.460111]    groups: 0-1
Mar 18 11:04:16 ubuntu kernel: [    0.460115] CPU1 attaching sched-domain:
Mar 18 11:04:16 ubuntu kernel: [    0.460116]  domain 0: span 0-1 level MC
Mar 18 11:04:16 ubuntu kernel: [    0.460118]   groups: 1 0
Mar 18 11:04:16 ubuntu kernel: [    0.460120]   domain 1: span 0-1 level NODE
Mar 18 11:04:16 ubuntu kernel: [    0.460121]    groups: 0-1
Mar 18 11:04:16 ubuntu kernel: [    0.460196] net_namespace: 1552 bytes
Mar 18 11:04:16 ubuntu kernel: [    0.460196] Booting paravirtualized kernel on bare hardware
Mar 18 11:04:16 ubuntu kernel: [    0.460248] Time: 15:03:38  Date: 03/18/09
Mar 18 11:04:16 ubuntu kernel: [    0.460272] NET: Registered protocol family 16
Mar 18 11:04:16 ubuntu kernel: [    0.460287] ACPI: bus type pci registered
Mar 18 11:04:16 ubuntu kernel: [    0.460287] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Mar 18 11:04:16 ubuntu kernel: [    0.460287] PCI: MCFG area at e0000000 reserved in E820
Mar 18 11:04:16 ubuntu kernel: [    0.470441] PCI: Using MMCONFIG at e0000000 - efffffff
Mar 18 11:04:16 ubuntu kernel: [    0.470442] PCI: Using configuration type 1 for base access
Mar 18 11:04:16 ubuntu kernel: [    0.470454] ACPI: EC: Look up EC in DSDT
Mar 18 11:04:16 ubuntu kernel: [    0.475594] ACPI: BIOS _OSI(Linux) query ignored
Mar 18 11:04:16 ubuntu kernel: [    0.475596] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
Mar 18 11:04:16 ubuntu kernel: [    0.476258] ACPI: Interpreter enabled
Mar 18 11:04:16 ubuntu kernel: [    0.476260] ACPI: (supports S0 S3 S4 S5)
Mar 18 11:04:16 ubuntu kernel: [    0.476274] ACPI: Using IOAPIC for interrupt routing
Mar 18 11:04:16 ubuntu kernel: [    0.476333] ACPI: EC: non-query interrupt received, switching to interrupt mode
Mar 18 11:04:16 ubuntu kernel: [    0.484139] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Mar 18 11:04:16 ubuntu kernel: [    0.484141] ACPI: EC: driver started in interrupt mode
Mar 18 11:04:16 ubuntu kernel: [    0.484170] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 18 11:04:16 ubuntu kernel: [    0.484170] PCI: 0000:00:02.0 reg 10 64bit mmio: [f0000000, f03fffff]
Mar 18 11:04:16 ubuntu kernel: [    0.484170] PCI: 0000:00:02.0 reg 18 64bit mmio: [d0000000, dfffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.484170] PCI: 0000:00:02.0 reg 20 io port: [1800, 1807]
Mar 18 11:04:16 ubuntu kernel: [    0.484170] PCI: 0000:00:02.1 reg 10 64bit mmio: [f0400000, f04fffff]
Mar 18 11:04:16 ubuntu kernel: [    0.484206] PCI: 0000:00:1a.0 reg 20 io port: [1820, 183f]
Mar 18 11:04:16 ubuntu kernel: [    0.484262] PCI: 0000:00:1a.1 reg 20 io port: [1840, 185f]
Mar 18 11:04:16 ubuntu kernel: [    0.484319] PCI: 0000:00:1a.2 reg 20 io port: [1860, 187f]
Mar 18 11:04:16 ubuntu kernel: [    0.484378] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f0a04800, f0a04bff]
Mar 18 11:04:16 ubuntu kernel: [    0.484422] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.484426] pci 0000:00:1a.7: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.484454] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f0a00000, f0a03fff]
Mar 18 11:04:16 ubuntu kernel: [    0.484487] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.484490] pci 0000:00:1b.0: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.484532] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.484535] pci 0000:00:1c.0: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.484578] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.484581] pci 0000:00:1c.1: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.484623] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.484626] pci 0000:00:1c.2: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.484668] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.484671] pci 0000:00:1c.3: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.484713] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.484716] pci 0000:00:1c.4: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.484757] PCI: 0000:00:1d.0 reg 20 io port: [1880, 189f]
Mar 18 11:04:16 ubuntu kernel: [    0.484813] PCI: 0000:00:1d.1 reg 20 io port: [18a0, 18bf]
Mar 18 11:04:16 ubuntu kernel: [    0.484870] PCI: 0000:00:1d.2 reg 20 io port: [18c0, 18df]
Mar 18 11:04:16 ubuntu kernel: [    0.484929] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f0a04c00, f0a04fff]
Mar 18 11:04:16 ubuntu kernel: [    0.484972] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.484976] pci 0000:00:1d.7: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.485116] PCI: 0000:00:1f.2 reg 10 io port: [1818, 181f]
Mar 18 11:04:16 ubuntu kernel: [    0.485121] PCI: 0000:00:1f.2 reg 14 io port: [180c, 180f]
Mar 18 11:04:16 ubuntu kernel: [    0.485126] PCI: 0000:00:1f.2 reg 18 io port: [1810, 1817]
Mar 18 11:04:16 ubuntu kernel: [    0.485130] PCI: 0000:00:1f.2 reg 1c io port: [1808, 180b]
Mar 18 11:04:16 ubuntu kernel: [    0.485135] PCI: 0000:00:1f.2 reg 20 io port: [18e0, 18ff]
Mar 18 11:04:16 ubuntu kernel: [    0.485140] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f0a04000, f0a047ff]
Mar 18 11:04:16 ubuntu kernel: [    0.485161] pci 0000:00:1f.2: PME# supported from D3hot
Mar 18 11:04:16 ubuntu kernel: [    0.485164] pci 0000:00:1f.2: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.485181] PCI: 0000:00:1f.3 reg 10 64bit mmio: [0, ff]
Mar 18 11:04:16 ubuntu kernel: [    0.485193] PCI: 0000:00:1f.3 reg 20 io port: [1c00, 1c1f]
Mar 18 11:04:16 ubuntu kernel: [    0.485277] PCI: 0000:02:00.0 reg 10 64bit mmio: [f0500000, f0501fff]
Mar 18 11:04:16 ubuntu kernel: [    0.485354] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.485360] pci 0000:02:00.0: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.485391] PCI: bridge 0000:00:1c.0 32bit mmio: [f0500000, f05fffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485431] PCI: bridge 0000:00:1c.1 io port: [2000, 2fff]
Mar 18 11:04:16 ubuntu kernel: [    0.485434] PCI: bridge 0000:00:1c.1 32bit mmio: [b8000000, bbffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485439] PCI: bridge 0000:00:1c.1 64bit mmio pref: [c8000000, cbffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485474] PCI: bridge 0000:00:1c.2 io port: [3000, 3fff]
Mar 18 11:04:16 ubuntu kernel: [    0.485477] PCI: bridge 0000:00:1c.2 32bit mmio: [b0000000, b3ffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485482] PCI: bridge 0000:00:1c.2 64bit mmio pref: [c0000000, c3ffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485525] PCI: 0000:08:00.0 reg 10 io port: [4000, 40ff]
Mar 18 11:04:16 ubuntu kernel: [    0.485544] PCI: 0000:08:00.0 reg 18 64bit mmio: [f0600000, f0600fff]
Mar 18 11:04:16 ubuntu kernel: [    0.485557] PCI: 0000:08:00.0 reg 20 64bit mmio: [f0b00000, f0b0ffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485564] PCI: 0000:08:00.0 reg 30 32bit mmio: [0, 1ffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485590] pci 0000:08:00.0: supports D1
Mar 18 11:04:16 ubuntu kernel: [    0.485591] pci 0000:08:00.0: supports D2
Mar 18 11:04:16 ubuntu kernel: [    0.485593] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 18 11:04:16 ubuntu kernel: [    0.485597] pci 0000:08:00.0: PME# disabled
Mar 18 11:04:16 ubuntu kernel: [    0.485627] PCI: bridge 0000:00:1c.3 io port: [4000, 4fff]
Mar 18 11:04:16 ubuntu kernel: [    0.485630] PCI: bridge 0000:00:1c.3 32bit mmio: [f0600000, f06fffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485635] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f0b00000, f0bfffff]
Mar 18 11:04:16 ubuntu kernel: [    0.485678] PCI: 0000:09:00.0 reg 10 32bit mmio: [f0700000, f07000ff]
Mar 18 11:04:16 ubuntu kernel: [    0.485782] PCI: 0000:09:00.2 reg 10 32bit mmio: [f0700400, f07004ff]
Mar 18 11:04:16 ubuntu kernel: [    0.485884] PCI: 0000:09:00.3 reg 10 32bit mmio: [f0700800, f07008ff]
Mar 18 11:04:16 ubuntu kernel: [    0.485987] PCI: 0000:09:00.4 reg 10 32bit mmio: [f0700c00, f0700cff]
Mar 18 11:04:16 ubuntu kernel: [    0.486088] PCI: bridge 0000:00:1c.4 32bit mmio: [f0700000, f07fffff]
Mar 18 11:04:16 ubuntu kernel: [    0.486136] pci 0000:00:1e.0: transparent bridge
Mar 18 11:04:16 ubuntu kernel: [    0.486173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 18 11:04:16 ubuntu kernel: [    0.486425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Mar 18 11:04:16 ubuntu kernel: [    0.488143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Mar 18 11:04:16 ubuntu kernel: [    0.488257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Mar 18 11:04:16 ubuntu kernel: [    0.488369] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Mar 18 11:04:16 ubuntu kernel: [    0.488480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Mar 18 11:04:16 ubuntu kernel: [    0.488591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Mar 18 11:04:16 ubuntu kernel: [    0.500596] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Mar 18 11:04:16 ubuntu kernel: [    0.500596] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Mar 18 11:04:16 ubuntu kernel: [    0.500596] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Mar 18 11:04:16 ubuntu kernel: [    0.500596] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Mar 18 11:04:16 ubuntu kernel: [    0.500596] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Mar 18 11:04:16 ubuntu kernel: [    0.500683] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Mar 18 11:04:16 ubuntu kernel: [    0.500793] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Mar 18 11:04:16 ubuntu kernel: [    0.500904] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
Mar 18 11:04:16 ubuntu kernel: [    0.500959] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 18 11:04:16 ubuntu kernel: [    0.500959] pnp: PnP ACPI init
Mar 18 11:04:16 ubuntu kernel: [    0.500959] ACPI: bus type pnp registered
Mar 18 11:04:16 ubuntu kernel: [    0.504299] pnp: PnP ACPI: found 11 devices
Mar 18 11:04:16 ubuntu kernel: [    0.504299] ACPI: ACPI bus type pnp unregistered
Mar 18 11:04:16 ubuntu kernel: [    0.504401] PCI: Using ACPI for IRQ routing
Mar 18 11:04:16 ubuntu kernel: [    0.528046] NET: Registered protocol family 8
Mar 18 11:04:16 ubuntu kernel: [    0.528048] NET: Registered protocol family 20
Mar 18 11:04:16 ubuntu kernel: [    0.528067] NetLabel: Initializing
Mar 18 11:04:16 ubuntu kernel: [    0.528067] NetLabel:  domain hash size = 128
Mar 18 11:04:16 ubuntu kernel: [    0.528067] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 18 11:04:16 ubuntu kernel: [    0.528067] NetLabel:  unlabeled traffic allowed by default
Mar 18 11:04:16 ubuntu kernel: [    0.528067] PCI-GART: No AMD northbridge found.
Mar 18 11:04:16 ubuntu kernel: [    0.528070] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Mar 18 11:04:16 ubuntu kernel: [    0.528073] hpet0: 4 64-bit timers, 14318180 Hz
Mar 18 11:04:16 ubuntu kernel: [    0.530073] tracer: 1286 pages allocated for 65536 entries of 80 bytes
Mar 18 11:04:16 ubuntu kernel: [    0.530075]    actual entries 65586
Mar 18 11:04:16 ubuntu kernel: [    0.530151] AppArmor: AppArmor Filesystem Enabled
Mar 18 11:04:16 ubuntu kernel: [    0.532039] Switched to high resolution mode on CPU 0
Mar 18 11:04:16 ubuntu kernel: [    0.532632] Switched to high resolution mode on CPU 1
Mar 18 11:04:16 ubuntu kernel: [    0.545015] system 00:03: iomem range 0xfed00000-0xfed003ff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545021] system 00:05: ioport range 0x680-0x69f has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545023] system 00:05: ioport range 0x480-0x48f has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545025] system 00:05: ioport range 0xffff-0xffff has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545027] system 00:05: ioport range 0xffff-0xffff has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545029] system 00:05: ioport range 0x1000-0x107f has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545030] system 00:05: ioport range 0x1180-0x11ff has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545032] system 00:05: ioport range 0x164e-0x164f has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545034] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545038] system 00:06: ioport range 0x6a0-0x6af has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545040] system 00:06: ioport range 0x6b0-0x6ff has been reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545046] system 00:0a: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545048] system 00:0a: iomem range 0xfed10000-0xfed13fff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545050] system 00:0a: iomem range 0xfed18000-0xfed18fff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545052] system 00:0a: iomem range 0xfed19000-0xfed19fff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545054] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545056] system 00:0a: iomem range 0xfed20000-0xfed3ffff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545058] system 00:0a: iomem range 0xfed40000-0xfed44fff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.545060] system 00:0a: iomem range 0xfed45000-0xfed8ffff could not be reserved
Mar 18 11:04:16 ubuntu kernel: [    0.549985] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Mar 18 11:04:16 ubuntu kernel: [    0.549987] pci 0000:00:1c.0:   IO window: disabled
Mar 18 11:04:16 ubuntu kernel: [    0.549991] pci 0000:00:1c.0:   MEM window: 0xf0500000-0xf05fffff
Mar 18 11:04:16 ubuntu kernel: [    0.549995] pci 0000:00:1c.0:   PREFETCH window: disabled
Mar 18 11:04:16 ubuntu kernel: [    0.550000] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
Mar 18 11:04:16 ubuntu kernel: [    0.550002] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
Mar 18 11:04:16 ubuntu kernel: [    0.550006] pci 0000:00:1c.1:   MEM window: 0xb8000000-0xbbffffff
Mar 18 11:04:16 ubuntu kernel: [    0.550009] pci 0000:00:1c.1:   PREFETCH window: 0x000000c8000000-0x000000cbffffff
Mar 18 11:04:16 ubuntu kernel: [    0.550015] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
Mar 18 11:04:16 ubuntu kernel: [    0.550017] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
Mar 18 11:04:16 ubuntu kernel: [    0.550021] pci 0000:00:1c.2:   MEM window: 0xb0000000-0xb3ffffff
Mar 18 11:04:16 ubuntu kernel: [    0.550024] pci 0000:00:1c.2:   PREFETCH window: 0x000000c0000000-0x000000c3ffffff
Mar 18 11:04:16 ubuntu kernel: [    0.550030] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:08
Mar 18 11:04:16 ubuntu kernel: [    0.550032] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
Mar 18 11:04:16 ubuntu kernel: [    0.550036] pci 0000:00:1c.3:   MEM window: 0xf0600000-0xf06fffff
Mar 18 11:04:16 ubuntu kernel: [    0.550040] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0b00000-0x000000f0bfffff
Mar 18 11:04:16 ubuntu kernel: [    0.550045] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:09
Mar 18 11:04:16 ubuntu kernel: [    0.550046] pci 0000:00:1c.4:   IO window: disabled
Mar 18 11:04:16 ubuntu kernel: [    0.550050] pci 0000:00:1c.4:   MEM window: 0xf0700000-0xf07fffff
Mar 18 11:04:16 ubuntu kernel: [    0.550053] pci 0000:00:1c.4:   PREFETCH window: disabled
Mar 18 11:04:16 ubuntu kernel: [    0.550058] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
Mar 18 11:04:16 ubuntu kernel: [    0.550060] pci 0000:00:1e.0:   IO window: disabled
Mar 18 11:04:16 ubuntu kernel: [    0.550064] pci 0000:00:1e.0:   MEM window: disabled
Mar 18 11:04:16 ubuntu kernel: [    0.550067] pci 0000:00:1e.0:   PREFETCH window: disabled
Mar 18 11:04:16 ubuntu kernel: [    0.550080] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 18 11:04:16 ubuntu kernel: [    0.550084] pci 0000:00:1c.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [    0.550091] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:04:16 ubuntu kernel: [    0.550094] pci 0000:00:1c.1: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [    0.550101] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 18 11:04:16 ubuntu kernel: [    0.550104] pci 0000:00:1c.2: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [    0.550110] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:04:16 ubuntu kernel: [    0.550114] pci 0000:00:1c.3: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [    0.550119] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 18 11:04:16 ubuntu kernel: [    0.550123] pci 0000:00:1c.4: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [    0.550128] pci 0000:00:1e.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [    0.550131] bus: 00 index 0 io port: [0, ffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550132] bus: 00 index 1 mmio: [0, ffffffffffffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550134] bus: 02 index 0 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550135] bus: 02 index 1 mmio: [f0500000, f05fffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550136] bus: 02 index 2 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550137] bus: 02 index 3 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550139] bus: 04 index 0 io port: [2000, 2fff]
Mar 18 11:04:16 ubuntu kernel: [    0.550140] bus: 04 index 1 mmio: [b8000000, bbffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550141] bus: 04 index 2 mmio: [c8000000, cbffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550143] bus: 04 index 3 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550144] bus: 06 index 0 io port: [3000, 3fff]
Mar 18 11:04:16 ubuntu kernel: [    0.550145] bus: 06 index 1 mmio: [b0000000, b3ffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550147] bus: 06 index 2 mmio: [c0000000, c3ffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550148] bus: 06 index 3 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550149] bus: 08 index 0 io port: [4000, 4fff]
Mar 18 11:04:16 ubuntu kernel: [    0.550151] bus: 08 index 1 mmio: [f0600000, f06fffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550152] bus: 08 index 2 mmio: [f0b00000, f0bfffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550153] bus: 08 index 3 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550155] bus: 09 index 0 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550156] bus: 09 index 1 mmio: [f0700000, f07fffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550157] bus: 09 index 2 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550158] bus: 09 index 3 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550160] bus: 0a index 0 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550161] bus: 0a index 1 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550162] bus: 0a index 2 mmio: [0, 0]
Mar 18 11:04:16 ubuntu kernel: [    0.550163] bus: 0a index 3 io port: [0, ffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550165] bus: 0a index 4 mmio: [0, ffffffffffffffff]
Mar 18 11:04:16 ubuntu kernel: [    0.550172] NET: Registered protocol family 2
Mar 18 11:04:16 ubuntu kernel: [    0.589085] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Mar 18 11:04:16 ubuntu kernel: [    0.589689] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Mar 18 11:04:16 ubuntu kernel: [    0.591396] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Mar 18 11:04:16 ubuntu kernel: [    0.591879] TCP: Hash tables configured (established 262144 bind 65536)
Mar 18 11:04:16 ubuntu kernel: [    0.591882] TCP reno registered
Mar 18 11:04:16 ubuntu kernel: [    0.601100] NET: Registered protocol family 1
Mar 18 11:04:16 ubuntu kernel: [    0.601199] checking if image is initramfs... it is
Mar 18 11:04:16 ubuntu kernel: [    1.242059] Freeing initrd memory: 8377k freed
Mar 18 11:04:16 ubuntu kernel: [    1.245912] audit: initializing netlink socket (disabled)
Mar 18 11:04:16 ubuntu kernel: [    1.245927] type=2000 audit(1237388618.244:1): initialized
Mar 18 11:04:16 ubuntu kernel: [    1.251029] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Mar 18 11:04:16 ubuntu kernel: [    1.252907] VFS: Disk quotas dquot_6.5.1
Mar 18 11:04:16 ubuntu kernel: [    1.252971] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Mar 18 11:04:16 ubuntu kernel: [    1.253056] msgmni has been set to 3939
Mar 18 11:04:16 ubuntu kernel: [    1.253149] io scheduler noop registered
Mar 18 11:04:16 ubuntu kernel: [    1.253151] io scheduler anticipatory registered
Mar 18 11:04:16 ubuntu kernel: [    1.253152] io scheduler deadline registered
Mar 18 11:04:16 ubuntu kernel: [    1.253242] io scheduler cfq registered (default)
Mar 18 11:04:16 ubuntu kernel: [    1.253254] pci 0000:00:02.0: Boot video device
Mar 18 11:04:16 ubuntu kernel: [    9.252006] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Mar 18 11:04:16 ubuntu kernel: [   17.252005] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
Mar 18 11:04:16 ubuntu kernel: [   17.252216] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   17.252245] pcieport-driver 0000:00:1c.0: found MSI capability
Mar 18 11:04:16 ubuntu kernel: [   17.252275] pci_express 0000:00:1c.0:pcie00: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252307] pci_express 0000:00:1c.0:pcie02: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252336] pci_express 0000:00:1c.0:pcie03: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252407] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   17.252435] pcieport-driver 0000:00:1c.1: found MSI capability
Mar 18 11:04:16 ubuntu kernel: [   17.252463] pci_express 0000:00:1c.1:pcie00: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252492] pci_express 0000:00:1c.1:pcie02: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252520] pci_express 0000:00:1c.1:pcie03: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252592] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   17.252620] pcieport-driver 0000:00:1c.2: found MSI capability
Mar 18 11:04:16 ubuntu kernel: [   17.252648] pci_express 0000:00:1c.2:pcie00: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252676] pci_express 0000:00:1c.2:pcie02: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252705] pci_express 0000:00:1c.2:pcie03: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252776] pcieport-driver 0000:00:1c.3: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   17.252804] pcieport-driver 0000:00:1c.3: found MSI capability
Mar 18 11:04:16 ubuntu kernel: [   17.252832] pci_express 0000:00:1c.3:pcie00: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252860] pci_express 0000:00:1c.3:pcie02: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252888] pci_express 0000:00:1c.3:pcie03: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.252959] pcieport-driver 0000:00:1c.4: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   17.252986] pcieport-driver 0000:00:1c.4: found MSI capability
Mar 18 11:04:16 ubuntu kernel: [   17.253018] pci_express 0000:00:1c.4:pcie00: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.253047] pci_express 0000:00:1c.4:pcie02: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.253078] pci_express 0000:00:1c.4:pcie03: allocate port service
Mar 18 11:04:16 ubuntu kernel: [   17.277387] hpet_resources: 0xfed00000 is busy
Mar 18 11:04:16 ubuntu kernel: [   17.277452] Linux agpgart interface v0.103
Mar 18 11:04:16 ubuntu kernel: [   17.277457] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar 18 11:04:16 ubuntu kernel: [   17.279100] brd: module loaded
Mar 18 11:04:16 ubuntu kernel: [   17.279155] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar 18 11:04:16 ubuntu kernel: [   17.279243] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 18 11:04:16 ubuntu kernel: [   17.283492] i8042.c: Detected active multiplexing controller, rev 1.1.
Mar 18 11:04:16 ubuntu kernel: [   17.286125] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 18 11:04:16 ubuntu kernel: [   17.286129] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Mar 18 11:04:16 ubuntu kernel: [   17.286131] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Mar 18 11:04:16 ubuntu kernel: [   17.286132] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Mar 18 11:04:16 ubuntu kernel: [   17.286134] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Mar 18 11:04:16 ubuntu kernel: [   17.297090] mice: PS/2 mouse device common for all mice
Mar 18 11:04:16 ubuntu kernel: [   17.297190] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Mar 18 11:04:16 ubuntu kernel: [   17.297212] rtc0: alarms up to one month, y3k, hpet irqs
Mar 18 11:04:16 ubuntu kernel: [   17.297239] cpuidle: using governor ladder
Mar 18 11:04:16 ubuntu kernel: [   17.297241] cpuidle: using governor menu
Mar 18 11:04:16 ubuntu kernel: [   17.297531] TCP cubic registered
Mar 18 11:04:16 ubuntu kernel: [   17.297685] registered taskstats version 1
Mar 18 11:04:16 ubuntu kernel: [   17.297807]   Magic number: 1:437:83
Mar 18 11:04:16 ubuntu kernel: [   17.297924] rtc_cmos 00:07: setting system clock to 2009-03-18 15:03:55 UTC (1237388635)
Mar 18 11:04:16 ubuntu kernel: [   17.297926] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 18 11:04:16 ubuntu kernel: [   17.297928] EDD information not available.
Mar 18 11:04:16 ubuntu kernel: [   17.298003] Freeing unused kernel memory: 540k freed
Mar 18 11:04:16 ubuntu kernel: [   17.298179] Write protecting the kernel read-only data: 4352k
Mar 18 11:04:16 ubuntu kernel: [   17.332811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar 18 11:04:16 ubuntu kernel: [   17.445389] fuse init (API version 7.9)
Mar 18 11:04:16 ubuntu kernel: [   17.489464] ACPI: SSDT 7DB1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Mar 18 11:04:16 ubuntu kernel: [   17.489880] ACPI: SSDT 7DB18620, 05C5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Mar 18 11:04:16 ubuntu kernel: [   17.628307] Monitor-Mwait will be used to enter C-1 state
Mar 18 11:04:16 ubuntu kernel: [   17.628309] Monitor-Mwait will be used to enter C-2 state
Mar 18 11:04:16 ubuntu kernel: [   17.628311] Monitor-Mwait will be used to enter C-3 state
Mar 18 11:04:16 ubuntu kernel: [   17.628454] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Mar 18 11:04:16 ubuntu kernel: [   17.628500] processor ACPI0007:00: registered as cooling_device0
Mar 18 11:04:16 ubuntu kernel: [   17.628503] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar 18 11:04:16 ubuntu kernel: [   17.628932] ACPI: SSDT 7DB19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
Mar 18 11:04:16 ubuntu kernel: [   17.629279] ACPI: SSDT 7DB19F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
Mar 18 11:04:16 ubuntu kernel: [   17.630297] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Mar 18 11:04:16 ubuntu kernel: [   17.630332] processor ACPI0007:01: registered as cooling_device1
Mar 18 11:04:16 ubuntu kernel: [   17.630336] ACPI: Processor [CPU1] (supports 8 throttling states)
Mar 18 11:04:16 ubuntu kernel: [   17.631928] Marking TSC unstable due to TSC halts in idle
Mar 18 11:04:16 ubuntu kernel: [   17.639487] thermal LNXTHERM:01: registered as thermal_zone0
Mar 18 11:04:16 ubuntu kernel: [   17.651912] ACPI: Thermal Zone [THM0] (33 C)
Mar 18 11:04:16 ubuntu kernel: [   17.817314] usbcore: registered new interface driver usbfs
Mar 18 11:04:16 ubuntu kernel: [   17.817331] usbcore: registered new interface driver hub
Mar 18 11:04:16 ubuntu kernel: [   17.817361] usbcore: registered new device driver usb
Mar 18 11:04:16 ubuntu kernel: [   17.818605] USB Universal Host Controller Interface driver v3.0
Mar 18 11:04:16 ubuntu kernel: [   17.818641] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:04:16 ubuntu kernel: [   17.818649] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   17.818652] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Mar 18 11:04:16 ubuntu kernel: [   17.818684] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Mar 18 11:04:16 ubuntu kernel: [   17.818715] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
Mar 18 11:04:16 ubuntu kernel: [   17.818821] usb usb1: configuration #1 chosen from 1 choice
Mar 18 11:04:16 ubuntu kernel: [   17.818840] hub 1-0:1.0: USB hub found
Mar 18 11:04:16 ubuntu kernel: [   17.818845] hub 1-0:1.0: 2 ports detected
Mar 18 11:04:16 ubuntu kernel: [   17.863273] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Mar 18 11:04:16 ubuntu kernel: [   17.910132] No dock devices found.
Mar 18 11:04:16 ubuntu kernel: [   17.918993] SCSI subsystem initialized
Mar 18 11:04:16 ubuntu kernel: [   17.929023] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Mar 18 11:04:16 ubuntu kernel: [   17.929031] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   17.929034] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Mar 18 11:04:16 ubuntu kernel: [   17.929054] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Mar 18 11:04:16 ubuntu kernel: [   17.929096] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
Mar 18 11:04:16 ubuntu kernel: [   17.929166] usb usb2: configuration #1 chosen from 1 choice
Mar 18 11:04:16 ubuntu kernel: [   17.929188] hub 2-0:1.0: USB hub found
Mar 18 11:04:16 ubuntu kernel: [   17.929194] hub 2-0:1.0: 2 ports detected
Mar 18 11:04:16 ubuntu kernel: [   17.929351] libata version 3.00 loaded.
Mar 18 11:04:16 ubuntu kernel: [   18.033230] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:04:16 ubuntu kernel: [   18.033241] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   18.033244] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Mar 18 11:04:16 ubuntu kernel: [   18.033265] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
Mar 18 11:04:16 ubuntu kernel: [   18.033298] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
Mar 18 11:04:16 ubuntu kernel: [   18.033371] usb usb3: configuration #1 chosen from 1 choice
Mar 18 11:04:16 ubuntu kernel: [   18.033391] hub 3-0:1.0: USB hub found
Mar 18 11:04:16 ubuntu kernel: [   18.033396] hub 3-0:1.0: 2 ports detected
Mar 18 11:04:16 ubuntu kernel: [   18.137264] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:04:16 ubuntu kernel: [   18.137280] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   18.137283] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Mar 18 11:04:16 ubuntu kernel: [   18.137307] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
Mar 18 11:04:16 ubuntu kernel: [   18.141222] ehci_hcd 0000:00:1a.7: debug port 1
Mar 18 11:04:16 ubuntu kernel: [   18.141227] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Mar 18 11:04:16 ubuntu kernel: [   18.141234] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf0a04800
Mar 18 11:04:16 ubuntu kernel: [   18.160016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 18 11:04:16 ubuntu kernel: [   18.160130] usb usb4: configuration #1 chosen from 1 choice
Mar 18 11:04:16 ubuntu kernel: [   18.160151] hub 4-0:1.0: USB hub found
Mar 18 11:04:16 ubuntu kernel: [   18.160158] hub 4-0:1.0: 6 ports detected
Mar 18 11:04:16 ubuntu kernel: [   18.264629] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 18 11:04:16 ubuntu kernel: [   18.264639] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   18.264642] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar 18 11:04:16 ubuntu kernel: [   18.264664] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Mar 18 11:04:16 ubuntu kernel: [   18.264696] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
Mar 18 11:04:16 ubuntu kernel: [   18.264769] usb usb5: configuration #1 chosen from 1 choice
Mar 18 11:04:16 ubuntu kernel: [   18.264788] hub 5-0:1.0: USB hub found
Mar 18 11:04:16 ubuntu kernel: [   18.264794] hub 5-0:1.0: 2 ports detected
Mar 18 11:04:16 ubuntu kernel: [   18.364269] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:04:16 ubuntu kernel: [   18.364275] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   18.364278] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar 18 11:04:16 ubuntu kernel: [   18.364299] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Mar 18 11:04:16 ubuntu kernel: [   18.364322] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
Mar 18 11:04:16 ubuntu kernel: [   18.364386] usb usb6: configuration #1 chosen from 1 choice
Mar 18 11:04:16 ubuntu kernel: [   18.364406] hub 6-0:1.0: USB hub found
Mar 18 11:04:16 ubuntu kernel: [   18.364411] hub 6-0:1.0: 2 ports detected
Mar 18 11:04:16 ubuntu kernel: [   18.468261] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 18 11:04:16 ubuntu kernel: [   18.468266] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   18.468269] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar 18 11:04:16 ubuntu kernel: [   18.468286] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Mar 18 11:04:16 ubuntu kernel: [   18.468313] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
Mar 18 11:04:16 ubuntu kernel: [   18.468378] usb usb7: configuration #1 chosen from 1 choice
Mar 18 11:04:16 ubuntu kernel: [   18.468397] hub 7-0:1.0: USB hub found
Mar 18 11:04:16 ubuntu kernel: [   18.468402] hub 7-0:1.0: 2 ports detected
Mar 18 11:04:16 ubuntu kernel: [   18.500101] Clocksource tsc unstable (delta = -209836222 ns)
Mar 18 11:04:16 ubuntu kernel: [   18.572300] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 18 11:04:16 ubuntu kernel: [   18.572312] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   18.572315] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar 18 11:04:16 ubuntu kernel: [   18.572334] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
Mar 18 11:04:16 ubuntu kernel: [   18.576230] ehci_hcd 0000:00:1d.7: debug port 1
Mar 18 11:04:16 ubuntu kernel: [   18.576235] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Mar 18 11:04:16 ubuntu kernel: [   18.576239] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0a04c00
Mar 18 11:04:16 ubuntu kernel: [   18.592107] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 18 11:04:16 ubuntu kernel: [   18.592923] usb usb8: configuration #1 chosen from 1 choice
Mar 18 11:04:16 ubuntu kernel: [   18.593351] hub 8-0:1.0: USB hub found
Mar 18 11:04:16 ubuntu kernel: [   18.593357] hub 8-0:1.0: 6 ports detected
Mar 18 11:04:16 ubuntu kernel: [   18.697866] ahci 0000:00:1f.2: version 3.0
Mar 18 11:04:16 ubuntu kernel: [   18.697879] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:04:16 ubuntu kernel: [   18.697964] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
Mar 18 11:04:16 ubuntu kernel: [   18.697967] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pio slum part 
Mar 18 11:04:16 ubuntu kernel: [   18.697970] ahci 0000:00:1f.2: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   18.698308] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Mar 18 11:04:16 ubuntu kernel: [   18.698325] r8169 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 18 11:04:16 ubuntu kernel: [   18.698339] r8169 0000:08:00.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   18.698526] scsi0 : ahci
Mar 18 11:04:16 ubuntu kernel: [   18.698605] scsi1 : ahci
Mar 18 11:04:16 ubuntu kernel: [   18.698605] eth0: RTL8168c/8111c at 0xffffc2000033a000, 00:90:f5:80:00:de, XID 3c2000c0 IRQ 2297
Mar 18 11:04:16 ubuntu kernel: [   18.698649] scsi2 : ahci
Mar 18 11:04:16 ubuntu kernel: [   18.698690] scsi3 : ahci
Mar 18 11:04:16 ubuntu kernel: [   18.698733] scsi4 : ahci
Mar 18 11:04:16 ubuntu kernel: [   18.698776] scsi5 : ahci
Mar 18 11:04:16 ubuntu kernel: [   18.698811] ata1: SATA max UDMA/133 abar m2048@0xf0a04000 port 0xf0a04100 irq 2298
Mar 18 11:04:16 ubuntu kernel: [   18.698814] ata2: SATA max UDMA/133 abar m2048@0xf0a04000 port 0xf0a04180 irq 2298
Mar 18 11:04:16 ubuntu kernel: [   18.698816] ata3: DUMMY
Mar 18 11:04:16 ubuntu kernel: [   18.698817] ata4: DUMMY
Mar 18 11:04:16 ubuntu kernel: [   18.698818] ata5: SATA max UDMA/133 abar m2048@0xf0a04000 port 0xf0a04300 irq 2298
Mar 18 11:04:16 ubuntu kernel: [   18.698821] ata6: SATA max UDMA/133 abar m2048@0xf0a04000 port 0xf0a04380 irq 2298
Mar 18 11:04:16 ubuntu kernel: [   19.017104] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 18 11:04:16 ubuntu kernel: [   19.017977] ata1.00: ATA-8: Hitachi HTS543225L9A300, FBEOC40C, max UDMA/133
Mar 18 11:04:16 ubuntu kernel: [   19.017979] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Mar 18 11:04:16 ubuntu kernel: [   19.019052] ata1.00: configured for UDMA/133
Mar 18 11:04:16 ubuntu kernel: [   19.336102] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 18 11:04:16 ubuntu kernel: [   19.349684] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TM00, max UDMA/100, ATAPI AN
Mar 18 11:04:16 ubuntu kernel: [   19.349687] ata2.00: applying bridge limits
Mar 18 11:04:16 ubuntu kernel: [   19.363765] ata2.00: configured for UDMA/100
Mar 18 11:04:16 ubuntu kernel: [   19.680100] ata5: SATA link down (SStatus 0 SControl 300)
Mar 18 11:04:16 ubuntu kernel: [   20.000109] ata6: SATA link down (SStatus 0 SControl 300)
Mar 18 11:04:16 ubuntu kernel: [   20.000219] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
Mar 18 11:04:16 ubuntu kernel: [   20.002716] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TM00 PQ: 0 ANSI: 5
Mar 18 11:04:16 ubuntu kernel: [   20.009548] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Mar 18 11:04:16 ubuntu kernel: [   20.009581] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Mar 18 11:04:16 ubuntu kernel: [   20.019850] Driver 'sd' needs updating - please use bus_type methods
Mar 18 11:04:16 ubuntu kernel: [   20.019936] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 18 11:04:16 ubuntu kernel: [   20.019949] sd 0:0:0:0: [sda] Write Protect is off
Mar 18 11:04:16 ubuntu kernel: [   20.019951] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 18 11:04:16 ubuntu kernel: [   20.019975] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 18 11:04:16 ubuntu kernel: [   20.020161] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 18 11:04:16 ubuntu kernel: [   20.020173] sd 0:0:0:0: [sda] Write Protect is off
Mar 18 11:04:16 ubuntu kernel: [   20.020175] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 18 11:04:16 ubuntu kernel: [   20.020195] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 18 11:04:16 ubuntu kernel: [   20.020198]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Mar 18 11:04:16 ubuntu kernel: [   20.377035]  sda1 sda2 sda3
Mar 18 11:04:16 ubuntu kernel: [   20.377227] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 18 11:04:16 ubuntu kernel: [   20.385669] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 18 11:04:16 ubuntu kernel: [   20.385672] Uniform CD-ROM driver Revision: 3.20
Mar 18 11:04:16 ubuntu kernel: [   20.385736] sr 1:0:0:0: Attached scsi CD-ROM sr0
Mar 18 11:04:16 ubuntu kernel: [   20.524469] PM: Starting manual resume from disk
Mar 18 11:04:16 ubuntu kernel: [   20.524472] PM: Resume from partition 8:2
Mar 18 11:04:16 ubuntu kernel: [   20.524473] PM: Checking hibernation image.
Mar 18 11:04:16 ubuntu kernel: [   20.524636] PM: Resume from disk failed.
Mar 18 11:04:16 ubuntu kernel: [   20.537507] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar 18 11:04:16 ubuntu kernel: [   20.537509] EXT3-fs: write access will be enabled during recovery.
Mar 18 11:04:16 ubuntu kernel: [   20.588625] kjournald starting.  Commit interval 5 seconds
Mar 18 11:04:16 ubuntu kernel: [   20.588641] EXT3-fs: recovery complete.
Mar 18 11:04:16 ubuntu kernel: [   20.589185] EXT3-fs: mounted filesystem with ordered data mode.
Mar 18 11:04:16 ubuntu kernel: [   27.587857] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 18 11:04:16 ubuntu kernel: [   27.613441] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Mar 18 11:04:16 ubuntu kernel: [   27.613524] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
Mar 18 11:04:16 ubuntu kernel: [   27.613526] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Mar 18 11:04:16 ubuntu kernel: [   27.613528] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Mar 18 11:04:16 ubuntu kernel: [   27.969669] udevd version 124 started
Mar 18 11:04:16 ubuntu kernel: [   28.115022] agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset
Mar 18 11:04:16 ubuntu kernel: [   28.115836] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Mar 18 11:04:16 ubuntu kernel: [   28.126716] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Mar 18 11:04:16 ubuntu kernel: [   28.193526] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Mar 18 11:04:16 ubuntu kernel: [   28.220024] ACPI: Power Button (FF) [PWRF]
Mar 18 11:04:16 ubuntu kernel: [   28.220141] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Mar 18 11:04:16 ubuntu kernel: [   28.220768] ACPI: Lid Switch [LID0]
Mar 18 11:04:16 ubuntu kernel: [   28.220823] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Mar 18 11:04:16 ubuntu kernel: [   28.241025] ACPI: Power Button (CM) [PWRB]
Mar 18 11:04:16 ubuntu kernel: [   28.241104] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
Mar 18 11:04:16 ubuntu kernel: [   28.273022] ACPI: Sleep Button (CM) [SLPB]
Mar 18 11:04:16 ubuntu kernel: [   28.283978] ACPI: Battery Slot [BAT0] (battery present)
Mar 18 11:04:16 ubuntu kernel: [   28.484723] ACPI: AC Adapter [ADP0] (on-line)
Mar 18 11:04:16 ubuntu kernel: [   28.484810] ACPI: WMI: Mapper loaded
Mar 18 11:04:16 ubuntu kernel: [   28.541790] acpi device:06: registered as cooling_device2
Mar 18 11:04:16 ubuntu kernel: [   28.541934] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input6
Mar 18 11:04:16 ubuntu kernel: [   28.568028] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Mar 18 11:04:16 ubuntu kernel: [   28.744618] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 18 11:04:16 ubuntu kernel: [   28.747947] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 18 11:04:16 ubuntu kernel: [   28.916064] cfg80211: Using static regulatory domain info
Mar 18 11:04:16 ubuntu kernel: [   28.916067] cfg80211: Regulatory domain: US
Mar 18 11:04:16 ubuntu kernel: [   28.916068] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 18 11:04:16 ubuntu kernel: [   28.916070] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
Mar 18 11:04:16 ubuntu kernel: [   28.916072] ^I(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 18 11:04:16 ubuntu kernel: [   28.916074] ^I(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 18 11:04:16 ubuntu kernel: [   28.916075] ^I(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 18 11:04:16 ubuntu kernel: [   28.916077] ^I(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Mar 18 11:04:16 ubuntu kernel: [   28.916079] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
Mar 18 11:04:16 ubuntu kernel: [   28.916080] cfg80211: Calling CRDA for country: US
Mar 18 11:04:16 ubuntu kernel: [   29.195933] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Mar 18 11:04:16 ubuntu kernel: [   29.195935] iwlagn: Copyright(c) 2003-2008 Intel Corporation
Mar 18 11:04:16 ubuntu kernel: [   29.196021] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:04:16 ubuntu kernel: [   29.196028] iwlagn 0000:02:00.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   29.196047] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
Mar 18 11:04:16 ubuntu kernel: [   29.238605] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
Mar 18 11:04:16 ubuntu kernel: [   29.240904] iwlagn 0000:02:00.0: PCI INT A disabled
Mar 18 11:04:16 ubuntu kernel: [   29.241266] phy0: Selected rate control algorithm 'iwl-agn-rs'
Mar 18 11:04:16 ubuntu kernel: [   29.320638] sdhci: Secure Digital Host Controller Interface driver
Mar 18 11:04:16 ubuntu kernel: [   29.320640] sdhci: Copyright(c) Pierre Ossman
Mar 18 11:04:16 ubuntu kernel: [   29.473075] sdhci-pci 0000:09:00.0: SDHCI controller found [197b:2382] (rev 0)
Mar 18 11:04:16 ubuntu kernel: [   29.473093] sdhci-pci 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:04:16 ubuntu kernel: [   29.473123] sdhci-pci 0000:09:00.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   29.473157] mmc0: SDHCI controller on PCI [0000:09:00.0] using ADMA
Mar 18 11:04:16 ubuntu kernel: [   29.473165] sdhci-pci 0000:09:00.2: SDHCI controller found [197b:2381] (rev 0)
Mar 18 11:04:16 ubuntu kernel: [   29.473177] sdhci-pci 0000:09:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:04:16 ubuntu kernel: [   29.473185] sdhci-pci 0000:09:00.2: Refusing to bind to secondary interface.
Mar 18 11:04:16 ubuntu kernel: [   29.473190] sdhci-pci 0000:09:00.2: PCI INT A disabled
Mar 18 11:04:16 ubuntu kernel: [   29.772356] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar 18 11:04:16 ubuntu kernel: [   29.772383] HDA Intel 0000:00:1b.0: setting latency timer to 64
Mar 18 11:04:16 ubuntu kernel: [   29.910923] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000
Mar 18 11:04:16 ubuntu kernel: [   29.947175] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Mar 18 11:04:16 ubuntu kernel: [   30.473127] lp: driver loaded but no devices found
Mar 18 11:04:16 ubuntu kernel: [   30.619324] Adding 1929676k swap on /dev/sda2.  Priority:-1 extents:1 across:1929676k
Mar 18 11:04:16 ubuntu kernel: [   31.455113] EXT3 FS on sda1, internal journal
Mar 18 11:04:16 ubuntu kernel: [   37.581657] kjournald starting.  Commit interval 5 seconds
Mar 18 11:04:16 ubuntu kernel: [   37.581667] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Mar 18 11:04:16 ubuntu kernel: [   37.585349] EXT3 FS on sda3, internal journal
Mar 18 11:04:16 ubuntu kernel: [   37.585355] EXT3-fs: mounted filesystem with ordered data mode.
Mar 18 11:04:16 ubuntu kernel: [   37.686483] type=1505 audit(1237388655.429:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4429
Mar 18 11:04:16 ubuntu kernel: [   37.789752] type=1505 audit(1237388655.533:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4434
Mar 18 11:04:16 ubuntu kernel: [   37.789915] type=1505 audit(1237388655.533:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4434
Mar 18 11:04:17 ubuntu kernel: [   39.510811] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: Successfully dropped root privileges.
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: avahi-daemon 0.6.23 starting up.
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: Successfully called chroot().
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: Successfully dropped remaining capabilities.
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: No service file found in /etc/avahi/services.
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: Network interface enumeration completed.
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: Registering HINFO record with values 'X86_64'/'LINUX'.
Mar 18 11:04:17 ubuntu avahi-daemon[5094]: Server startup complete. Host name is ubuntu.local. Local service cookie is 4273521316.
Mar 18 11:04:17 ubuntu kernel: [   39.879462] NET: Registered protocol family 10
Mar 18 11:04:17 ubuntu kernel: [   39.879889] lo: Disabled Privacy Extensions
Mar 18 11:04:17 ubuntu kernel: [   40.178923] ppdev: user-space parallel port driver
Mar 18 11:04:19 ubuntu chipcardd[5514]: chipcardd.c:  738: Chipcardd v4.1.3.0stable started.
Mar 18 11:04:19 ubuntu chipcardd[5514]: chipcardd.c:  740: LibSYSFS supported.
Mar 18 11:04:19 ubuntu chipcardd[5516]: devicemanager.c: 3373: Changes in hardware list
Mar 18 11:04:22 ubuntu acpid: client connected from 5879[111:123] 
Mar 18 11:04:22 ubuntu bluetoothd[5938]: Bluetooth daemon
Mar 18 11:04:22 ubuntu kernel: [   44.972620] Bluetooth: Core ver 2.13
Mar 18 11:04:22 ubuntu kernel: [   44.973843] NET: Registered protocol family 31
Mar 18 11:04:22 ubuntu kernel: [   44.973847] Bluetooth: HCI device and connection manager initialized
Mar 18 11:04:22 ubuntu kernel: [   44.973849] Bluetooth: HCI socket layer initialized
Mar 18 11:04:22 ubuntu bluetoothd[5938]: Starting SDP server
Mar 18 11:04:22 ubuntu kernel: [   44.985545] Bluetooth: L2CAP ver 2.11
Mar 18 11:04:22 ubuntu kernel: [   44.985554] Bluetooth: L2CAP socket layer initialized
Mar 18 11:04:22 ubuntu kernel: [   45.002204] Bluetooth: SCO (Voice Link) ver 0.6
Mar 18 11:04:22 ubuntu kernel: [   45.002215] Bluetooth: SCO socket layer initialized
Mar 18 11:04:22 ubuntu bluetoothd[5938]: Starting experimental netlink support
Mar 18 11:04:22 ubuntu bluetoothd[5938]: Failed to find Bluetooth netlink family
Mar 18 11:04:22 ubuntu bluetoothd[5938]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 18 11:04:22 ubuntu kernel: [   45.024998] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 18 11:04:22 ubuntu kernel: [   45.025010] Bluetooth: BNEP filters: protocol multicast
Mar 18 11:04:22 ubuntu kernel: [   45.060663] Bridge firewalling registered
Mar 18 11:04:22 ubuntu bluetoothd[5938]: bridge pan0 created
Mar 18 11:04:23 ubuntu kernel: [   45.281352] Bluetooth: RFCOMM socket layer initialized
Mar 18 11:04:23 ubuntu kernel: [   45.281365] Bluetooth: RFCOMM TTY layer initialized
Mar 18 11:04:23 ubuntu kernel: [   45.281367] Bluetooth: RFCOMM ver 1.10
Mar 18 11:04:23 ubuntu NetworkManager: <info>  starting... 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  eth0: driver is 'r8169'. 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_90_f5_80_00_de 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  wlan0: driver is 'iwlagn'. 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_21_5c_11_30_b1 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
Mar 18 11:04:23 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
Mar 18 11:04:23 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
Mar 18 11:04:23 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Mar 18 11:04:23 ubuntu nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Mar 18 11:04:23 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_90_f5_80_00_de, iface: eth0): not well known
Mar 18 11:04:23 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_21_5c_11_30_b1, iface: wlan0): not well known
Mar 18 11:04:23 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
Mar 18 11:04:23 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 18 11:04:23 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 18 11:04:23 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (35388928) ... get_connections.
Mar 18 11:04:23 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (35388928) ... get_connections (managed=false): return empty list.
Mar 18 11:04:23 ubuntu NetworkManager: <info>  (wlan0): supplicant manager is now in state 1 (from 0). 
Mar 18 11:04:23 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Mar 18 11:04:24 ubuntu acpid: client connected from 6044[0:0] 
Mar 18 11:04:25 ubuntu kernel: [   48.005311] Netfilter messages via NETLINK v0.30.
Mar 18 11:04:25 ubuntu ntpd[6088]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:53:39 UTC 2009 (1)
Mar 18 11:04:25 ubuntu ntpd[6092]: precision = 1.000 usec
Mar 18 11:04:25 ubuntu ntpd[6092]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Mar 18 11:04:25 ubuntu ntpd[6092]: Listening on interface #1 wildcard, ::#123 Disabled
Mar 18 11:04:25 ubuntu ntpd[6092]: Listening on interface #2 lo, ::1#123 Enabled
Mar 18 11:04:25 ubuntu ntpd[6092]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Mar 18 11:04:25 ubuntu ntpd[6092]: kernel time sync status 0040
Mar 18 11:04:25 ubuntu ntpd[6092]: frequency initialized -40.970 PPM from /var/lib/ntp/ntp.drift
Mar 18 11:04:25 ubuntu ntpd[6111]: signal_no_reset: signal 17 had flags 4000000
Mar 18 11:04:26 ubuntu anacron[6132]: Anacron 2.3 started on 2009-03-18
Mar 18 11:04:26 ubuntu anacron[6132]: Will run job `cron.daily' in 5 min.
Mar 18 11:04:26 ubuntu anacron[6132]: Jobs will be executed sequentially
Mar 18 11:04:26 ubuntu /usr/sbin/cron[6175]: (CRON) INFO (pidfile fd = 3)
Mar 18 11:04:26 ubuntu /usr/sbin/cron[6176]: (CRON) STARTUP (fork ok)
Mar 18 11:04:26 ubuntu /usr/sbin/cron[6176]: (CRON) INFO (Running @reboot jobs)
Mar 18 11:04:26 ubuntu kernel: [   49.132879] [drm] Initialized drm 1.1.0 20060810
Mar 18 11:04:26 ubuntu kernel: [   49.169632] pci 0000:00:02.0: power state changed by ACPI to D0
Mar 18 11:04:26 ubuntu kernel: [   49.169656] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:04:26 ubuntu kernel: [   49.169666] pci 0000:00:02.0: setting latency timer to 64
Mar 18 11:04:26 ubuntu kernel: [   49.173644] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): bringing up device. 
Mar 18 11:04:27 ubuntu kernel: [   49.396803] r8169: eth0: link down
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): preparing device. 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Mar 18 11:04:27 ubuntu kernel: [   49.397271] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 18 11:04:27 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (wlan0): bringing up device. 
Mar 18 11:04:27 ubuntu kernel: [   49.409305] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 11:04:27 ubuntu kernel: [   49.409380] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
Mar 18 11:04:27 ubuntu kernel: [   49.409515] firmware: requesting lbm-iwlwifi-4965-2.ucode
Mar 18 11:04:27 ubuntu kernel: [   49.577808] iwlagn loaded firmware version 228.57.2.23
Mar 18 11:04:27 ubuntu nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_90_f5_80_00_de
Mar 18 11:04:27 ubuntu kernel: [   49.780596] Registered led device: iwl-phy0:radio
Mar 18 11:04:27 ubuntu kernel: [   49.780708] Registered led device: iwl-phy0:assoc
Mar 18 11:04:27 ubuntu kernel: [   49.780788] Registered led device: iwl-phy0:RX
Mar 18 11:04:27 ubuntu kernel: [   49.780864] Registered led device: iwl-phy0:TX
Mar 18 11:04:27 ubuntu kernel: [   49.822362] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (wlan0): preparing device. 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Mar 18 11:04:27 ubuntu NetworkManager: <WARN>  auto_activate_device(): Connection 'Auto eth0' auto-activation failed: (2) Device not managed by NetworkManager 
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Mar 18 11:04:27 ubuntu kernel: [   49.910429] NET: Registered protocol family 17
Mar 18 11:04:27 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Mar 18 11:04:27 ubuntu ntpd_initres[6111]: host name not found: clock.psu.edu
Mar 18 11:04:27 ubuntu ntpd_initres[6111]: couldn't resolve `clock.psu.edu', giving up on it
Mar 18 11:04:27 ubuntu ntpd_initres[6111]: host name not found: louie.udel.edu
Mar 18 11:04:27 ubuntu ntpd_initres[6111]: couldn't resolve `louie.udel.edu', giving up on it
Mar 18 11:04:28 ubuntu kernel: [   50.523533] set status page addr 0x02b58000
Mar 18 11:04:29 ubuntu kernel: [   51.737786] wlan0: authenticate with AP 00:14:bf:39:72:e6
Mar 18 11:04:29 ubuntu kernel: [   51.740450] wlan0: authenticated
Mar 18 11:04:29 ubuntu kernel: [   51.740461] wlan0: associate with AP 00:14:bf:39:72:e6
Mar 18 11:04:29 ubuntu kernel: [   51.751568] wlan0: RX AssocResp from 00:14:bf:39:72:e6 (capab=0x401 status=0 aid=5)
Mar 18 11:04:29 ubuntu kernel: [   51.751584] wlan0: associated
Mar 18 11:04:29 ubuntu kernel: [   51.773186] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 18 11:04:29 ubuntu kernel: [   51.773416] wlan0: disassociating by local choice (reason=3)
Mar 18 11:04:30 ubuntu avahi-daemon[5094]: Registering new address record for fe80::221:5cff:fe11:30b1 on wlan0.*.
Mar 18 11:04:32 ubuntu gdmgreeter[6447]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Mar 18 11:04:39 ubuntu kernel: [   62.084076] wlan0: no IPv6 routers present
Mar 18 11:04:40 ubuntu pulseaudio[6592]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 18 11:04:40 ubuntu pulseaudio[6594]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 18 11:04:40 ubuntu pulseaudio[6594]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 18 11:04:41 ubuntu pulseaudio[6594]: alsa-util.c: Device dmix doesn't support 44100 Hz, changed to 48000 Hz.
Mar 18 11:04:41 ubuntu pulseaudio[6594]: alsa-util.c: Device dmix doesn't support sample format s16le, changed to s32le.
Mar 18 11:04:41 ubuntu pulseaudio[6594]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Mar 18 11:04:41 ubuntu pulseaudio[6594]: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0"): initialization failed.
Mar 18 11:04:42 ubuntu pulseaudio[6594]: source.c: Assertion 'PA_SOURCE_OPENED(s->thread_info.state)' failed at pulsecore/source.c:278, function pa_source_post(). Aborting.
Mar 18 11:04:45 ubuntu x-session-manager[6467]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Mar 18 11:04:47 ubuntu pulseaudio[6688]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 18 11:04:47 ubuntu pulseaudio[6688]: pid.c: Stale PID file, overwriting.
Mar 18 11:04:47 ubuntu pulseaudio[6688]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 18 11:04:47 ubuntu pulseaudio[6688]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 18 11:04:47 ubuntu pulseaudio[6688]: alsa-util.c: Device dmix doesn't support 44100 Hz, changed to 48000 Hz.
Mar 18 11:04:47 ubuntu pulseaudio[6688]: alsa-util.c: Device dmix doesn't support sample format s16le, changed to s32le.
Mar 18 11:04:47 ubuntu pulseaudio[6688]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
Mar 18 11:04:47 ubuntu pulseaudio[6688]: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0"): initialization failed.
Mar 18 11:04:48 ubuntu pulseaudio[6688]: source.c: Assertion 'PA_SOURCE_OPENED(s->thread_info.state)' failed at pulsecore/source.c:278, function pa_source_post(). Aborting.
Mar 18 11:04:48 ubuntu x-session-manager[6467]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Mar 18 11:04:55 ubuntu x-session-manager[6467]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
```

---

### Post by thomasaaron on 2009-03-18
The last two lines of the log tell it all...

> Mar 18 11:04:48 ubuntu x-session-manager[6467]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Mar 18 11:04:55 ubuntu x-session-manager[6467]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout

It is failing to find the Ubuntu theme in the filesystem. If it loads correctly MOST of the time, then you know the necessary files exist. If it fails to find them SOME of the time, your filesystem may be getting a bit iffy.

---

### Post by jpoRS on 2009-03-18
OK! We know what the problem is! . . . so now what?

---

### Post by thomasaaron on 2009-03-18
Well, you could try running fsck from a live CD to see if it finds any errors. Short of that, an install would be my next step.

Or, since it is very intermittent...

---

### Post by jpoRS on 2009-03-19
Ok!  I was planning on doing a fresh install for 9.04 anyway.  Jaunty can't come soon enough I guess.

Thanks Tom!
jim

---

