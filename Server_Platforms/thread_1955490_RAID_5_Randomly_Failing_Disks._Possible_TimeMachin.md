---
title: "RAID 5 Randomly Failing Disks. Possible TimeMachine Issue."
date: 2012-04-09
forum: Server Platforms
---

### Post by Bushflyr on 2012-04-09
Hi all. I'm currently building a small home server, Ubuntu server 11.10, for music, movies, storage, and security cams. It's an i5 processor on a Jetway JNF9A mobo with 1 WD 500GB OS drive and 4 Seagate 2TB drives set up 3 RAID 5 1 spare. 

My other machines are all Mac's so I mostly followed the instructions in [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=1895084"). The first two times I tried to back up my iMac to the server with TM it completely crashed it so I reinstalled from scratch. The second time it crashed the RAID, but (I think) it was only SDB that it had listed as failed. I was able to unmount and recover the RAID with mdadm. The third time I left it to back up over night and woke to find two disks (I think sdb and sdc, but not sure) listed as failed. After much tooth gnashing I found the "failed" disks listed as part of md127 and was able to reconstruct the RAID from scratch. 

This last time I went to bed and disabled sleep on my iMac. TM successfully backed up over night. Now I just came home from the beach to find the raid rebuilding from a failed sdc and a fresh, successful, TM backup as of 30 minutes ago.

So, I'm trying to figure out why it's "failing" the disks erroneously and how to fix it. Any help is greatly appreciated.

```
[~]: sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sdd1[4] sde1[3] sdc1[1](F)
      3907023872 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      [==========>..........]  recovery = 53.5% (1045589816/1953511936) finish=135.0min speed=112012K/sec
      
unused devices: <none>
[~]: sudo smartctl -t short /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-17-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

```So after it finally finished rebuilding I did an examine and detail scan and got:

```

[~]: sudo mdadm --examine /dev/sdc
mdadm: No md superblock detected on /dev/sdc.
[~]: sudo mdadm --detail --scan
ARRAY /dev/md0 metadata=1.2 name=mars:0 UUID=9ec6ec09:8834b3f7:adc08875:2ae05753
[~]: sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Apr  6 10:14:03 2012
     Raid Level : raid5
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Mon Apr  9 14:52:38 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : mars:0  (local to host mars)
           UUID : 9ec6ec09:8834b3f7:adc08875:2ae05753
         Events : 384

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       3       8       65        1      active sync   /dev/sde1
       4       8       49        2      active sync   /dev/sdd1

       1       8       33        -      faulty spare   /dev/sdc1

```And Smartctl returned:
```
[~]: sudo smartctl -d ata -a /dev/sdc -T permissive
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-17-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Smartctl: Device Read Identity Failed: Input/output error

=== START OF INFORMATION SECTION ===
Device Model:     [No Information Found]
Serial Number:    [No Information Found]
Firmware Version: [No Information Found]
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   [No Information Found]
ATA Standard is:  [No Information Found]
Local Time is:    Mon Apr  9 14:59:51 2012 HST
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 85-87 don't show if SMART is enabled.
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

```

Then after rebooting I get:
```
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD796YM
LU WWN Device Id: 5 000c50 046e10bb7
Firmware Version: CC3C
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Apr  9 15:08:03 2012 HST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  612) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x30b7)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   102   099   006    Pre-fail  Always       -       200408
  3 Spin_Up_Time            0x0003   092   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       127
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   064   060   030    Pre-fail  Always       -       2784264
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       238
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       135
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       11
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   053   045    Old_age   Always       -       37 (Min/Max 37/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       57
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       135
194 Temperature_Celsius     0x0022   037   047   000    Old_age   Always       -       37 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   024   012   000    Old_age   Always       -       200408
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       277643865882863
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       200775748
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2481998573

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        42         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

Possible cable issue?

---

### Post by rubylaser on 2012-04-10
It's not a cable issue, because your SMART data would reflect it on this line.

```
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       **0**
```

You have zero CRC errors, so that's not the problem.  

Sorry, here's a bunch of questions to get started:
1. How do you have your disks hooked up (directly to the motherboard or to a HBA card)?  
2. Does this only happen with that drive or are drives randomly failing out of the array? 
3. Have you tried checking dmesg after this happens?
4. What do you have in /etc/mdadm/mdadm.conf?
```
cat /etc/mdadm/mdadm.conf
```

That should be enough to get me up to speed :)

---

### Post by Bushflyr on 2012-04-10
> **rubylaser said:**
> It's not a cable issue, because your SMART data would reflect it on this line.

```
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       **0**
```You have zero CRC errors, so that's not the problem.  

Thanks for the response. One potential eliminated. :)

> 
Sorry, here's a bunch of questions to get started:
1. How do you have your disks hooked up (directly to the motherboard or to a HBA card)?

Questions are great, after searching for a few days, I still had no idea where to start. The Mobo is a [Jetway JNF9A]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813153222"),  it has 2 6gb SATA ports and 4 3gb SATA ports. The 4 2TB drives are plugged into the 3GB ports and the WD OS drive is plugged into one of the 6gb ports.

> 
2. Does this only happen with that drive or are drives randomly failing out of the array? 


I think it's random. I don't exactly recall which drives it kicked out on previous failures, but last time it kicked 2 drives. I just turned TM back on, so I expect it'll do it again shortly.

> 
3. Have you tried checking dmesg after this happens?


I did, but don't really know enough to know what it's telling me. Here's the current output (if it helps) but it's after a reboot and adding the drive back in, so I don't know if the old errors were dumped.

```

[~]: dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-17-server (buildd@yellow) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 22:15:30 UTC 2012 (Ubuntu 3.0.0-17.30-server 3.0.22)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-server root=UUID=9eba3f6d-7b5d-4674-8965-201c628c115d ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c000 (usable)
[    0.000000]  BIOS-e820: 000000000009c000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bad93000 (usable)
[    0.000000]  BIOS-e820: 00000000bad93000 - 00000000bade7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bade7000 - 00000000bae0a000 (reserved)
[    0.000000]  BIOS-e820: 00000000bae0a000 - 00000000bae0c000 (usable)
[    0.000000]  BIOS-e820: 00000000bae0c000 - 00000000bae1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000bae1c000 - 00000000bae1d000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bae1d000 - 00000000bae28000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bae28000 - 00000000bae49000 (reserved)
[    0.000000]  BIOS-e820: 00000000bae49000 - 00000000bae8c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bae8c000 - 00000000bb000000 (usable)
[    0.000000]  BIOS-e820: 00000000bb800000 - 00000000bfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000023e600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: SONOSCAN NAF92Q67/ , BIOS 4.6.4 10/13/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x23e600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0BB800000 mask FFF800000 uncachable
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   5 base 23E600000 mask FFFE00000 uncachable
[    0.000000]   6 base 23E800000 mask FFF800000 uncachable
[    0.000000]   7 base 23F000000 mask FFF000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3000MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3GB, range: 1GB, type UC
[    0.000000] reg 5, base: 9190MB, range: 2MB, type UC
[    0.000000] reg 6, base: 9192MB, range: 8MB, type UC
[    0.000000] reg 7, base: 9200MB, range: 16MB, type UC
[    0.000000] total RAM covered: 8094M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 9      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3000MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 1GB, type WB
[    0.000000] reg 6, base: 9190MB, range: 2MB, type UC
[    0.000000] reg 7, base: 9192MB, range: 8MB, type UC
[    0.000000] reg 8, base: 9200MB, range: 16MB, type UC
[    0.000000] e820 update range: 00000000bb800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcdb0] fcdb0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bb000000
[    0.000000]  0000000000 - 00bb000000 page 2M
[    0.000000] kernel direct mapping tables up to bb000000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000023e600000
[    0.000000]  0100000000 - 023e600000 page 2M
[    0.000000] kernel direct mapping tables up to 23e600000 @ baff6000-bb000000
[    0.000000] RAMDISK: 36544000 - 3729a000
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000baddc068 00054 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000bade3a98 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000baddc150 07942 (v02 ALASKA    A M I 00000A04 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bae1ff80 00040
[    0.000000] ACPI: APIC 00000000bade3b90 00086 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000bade3c18 00102 (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000bade3d20 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bade3d60 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
[    0.000000] ACPI: ASF! 00000000bade3d98 000A0 (v32 INTEL       HCG 00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000023e600000
[    0.000000] Initmem setup node 0 0000000000000000-000000023e600000
[    0.000000]   NODE_DATA [000000023e5fb000 - 000000023e5fffff]
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880235c00000-ffff88023cbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0023e600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bad93
[    0.000000]     0: 0x000bae0a -> 0x000bae0c
[    0.000000]     0: 0x000bae8c -> 0x000bb000
[    0.000000]     0: 0x00100000 -> 0x0023e600
[    0.000000] On node 0 totalpages: 2069653
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 747329 pages, LIFO batch:31
[    0.000000]   Normal zone: 17829 pages used for memmap
[    0.000000]   Normal zone: 1286235 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bad93000 - 00000000bade7000
[    0.000000] PM: Registered nosave memory: 00000000bade7000 - 00000000bae0a000
[    0.000000] PM: Registered nosave memory: 00000000bae0c000 - 00000000bae1c000
[    0.000000] PM: Registered nosave memory: 00000000bae1c000 - 00000000bae1d000
[    0.000000] PM: Registered nosave memory: 00000000bae1d000 - 00000000bae28000
[    0.000000] PM: Registered nosave memory: 00000000bae28000 - 00000000bae49000
[    0.000000] PM: Registered nosave memory: 00000000bae49000 - 00000000bae8c000
[    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bb800000
[    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000bfa00000
[    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bfa00000 (gap: bfa00000:3f31c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88023e200000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2037483
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-server root=UUID=9eba3f6d-7b5d-4674-8965-201c628c115d ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8068028k/9410560k available (6222k kernel code, 1131948k absent, 210584k reserved, 6902k data, 904k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3093.307 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6186.61 BogoMIPS (lpj=12373228)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000022] Security Framework initialized
[    0.000033] AppArmor: AppArmor initialized
[    0.000035] Yama: becoming mindful.
[    0.000604] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001982] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002517] Mount-cache hash table entries: 256
[    0.002590] Initializing cgroup subsys cpuacct
[    0.002595] Initializing cgroup subsys memory
[    0.002600] Initializing cgroup subsys devices
[    0.002602] Initializing cgroup subsys freezer
[    0.002604] Initializing cgroup subsys net_cls
[    0.002606] Initializing cgroup subsys blkio
[    0.002611] Initializing cgroup subsys perf_event
[    0.002630] CPU: Physical Processor ID: 0
[    0.002632] CPU: Processor Core ID: 0
[    0.002637] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002637] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002642] mce: CPU supports 9 MCE banks
[    0.002654] CPU0: Thermal monitoring enabled (TM1)
[    0.002661] using mwait in idle threads.
[    0.004477] ACPI: Core revision 20110413
[    0.006727] ftrace: allocating 26099 entries in 103 pages
[    0.014123] x2apic not enabled, IRQ remapping init failed
[    0.014527] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.054208] CPU0: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz stepping 07
[    0.161770] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.161777] ... version:                3
[    0.161779] ... bit width:              48
[    0.161781] ... generic registers:      8
[    0.161782] ... value mask:             0000ffffffffffff
[    0.161784] ... max period:             000000007fffffff
[    0.161786] ... fixed-purpose events:   3
[    0.161788] ... event mask:             00000007000000ff
[    0.162059] Booting Node   0, Processors  #1
[    0.162062] smpboot cpu 1: start_ip = 97000
[    0.269939]  #2
[    0.269942] smpboot cpu 2: start_ip = 97000
[    0.377916]  #3 Ok.
[    0.377920] smpboot cpu 3: start_ip = 97000
[    0.485840] Brought up 4 CPUs
[    0.485845] Total of 4 processors activated (24744.34 BogoMIPS).
[    0.487835] devtmpfs: initialized
[    0.488430] PM: Registering ACPI NVS region at bad93000 (344064 bytes)
[    0.488437] PM: Registering ACPI NVS region at bae1d000 (45056 bytes)
[    0.488439] PM: Registering ACPI NVS region at bae49000 (274432 bytes)
[    0.489375] print_constraints: dummy: 
[    0.489401] Time:  1:07:13  Date: 04/10/12
[    0.489422] NET: Registered protocol family 16
[    0.489487] ACPI: bus type pci registered
[    0.489492] Trying to unpack rootfs image as initramfs...
[    0.489524] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.489528] PCI: not using MMCONFIG
[    0.489530] PCI: Using configuration type 1 for base access
[    0.490040] bio: create slab <bio-0> at 0
[    0.490905] ACPI: EC: Look up EC in DSDT
[    0.491796] ACPI: Executed 1 blocks of module-level executable AML code
[    0.493330] ACPI: SSDT 00000000bae1e918 003E0 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.493563] ACPI: Dynamic OEM Table Load:
[    0.493566] ACPI: SSDT           (null) 003E0 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.493585] ACPI: SSDT 00000000bae1dd98 000E4 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.493786] ACPI: Dynamic OEM Table Load:
[    0.493789] ACPI: SSDT           (null) 000E4 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.494132] ACPI: Interpreter enabled
[    0.494135] ACPI: (supports S0 S1 S4 S5)
[    0.494147] ACPI: Using IOAPIC for interrupt routing
[    0.494162] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.494209] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.533226] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.536967] ACPI: No dock devices found.
[    0.536970] HEST: Table not found.
[    0.536973] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.537102] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.537237] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.537240] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.537243] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.537246] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff]
[    0.537249] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xffffffff]
[    0.537254] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000c8000-0x000dffff] conflicts with Video ROM [mem 0x000c0000-0x000cd9ff]
[    0.537263] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
[    0.537293] pci 0000:00:02.0: [8086:0102] type 0 class 0x000300
[    0.537301] pci 0000:00:02.0: reg 10: [mem 0xfe000000-0xfe3fffff 64bit]
[    0.537306] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.537310] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.537378] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.537411] pci 0000:00:16.0: reg 10: [mem 0xfe529000-0xfe52900f 64bit]
[    0.537523] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.537528] pci 0000:00:16.0: PME# disabled
[    0.537557] pci 0000:00:16.2: [8086:1c3c] type 0 class 0x000101
[    0.537583] pci 0000:00:16.2: reg 10: [io  0xf190-0xf197]
[    0.537596] pci 0000:00:16.2: reg 14: [io  0xf180-0xf183]
[    0.537608] pci 0000:00:16.2: reg 18: [io  0xf170-0xf177]
[    0.537621] pci 0000:00:16.2: reg 1c: [io  0xf160-0xf163]
[    0.537634] pci 0000:00:16.2: reg 20: [io  0xf150-0xf15f]
[    0.537738] pci 0000:00:16.3: [8086:1c3d] type 0 class 0x000700
[    0.537762] pci 0000:00:16.3: reg 10: [io  0xf140-0xf147]
[    0.537775] pci 0000:00:16.3: reg 14: [mem 0xfe528000-0xfe528fff]
[    0.537923] pci 0000:00:19.0: [8086:1502] type 0 class 0x000200
[    0.537952] pci 0000:00:19.0: reg 10: [mem 0xfe500000-0xfe51ffff]
[    0.537965] pci 0000:00:19.0: reg 14: [mem 0xfe527000-0xfe527fff]
[    0.537978] pci 0000:00:19.0: reg 18: [io  0xf060-0xf07f]
[    0.538087] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.538091] pci 0000:00:19.0: PME# disabled
[    0.538125] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.538154] pci 0000:00:1a.0: reg 10: [mem 0xfe526000-0xfe5263ff]
[    0.538287] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.538292] pci 0000:00:1a.0: PME# disabled
[    0.538325] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.538350] pci 0000:00:1b.0: reg 10: [mem 0xfe520000-0xfe523fff 64bit]
[    0.538469] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.538474] pci 0000:00:1b.0: PME# disabled
[    0.538505] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.538637] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.538642] pci 0000:00:1c.0: PME# disabled
[    0.538682] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
[    0.538807] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.538811] pci 0000:00:1c.6: PME# disabled
[    0.538851] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.538881] pci 0000:00:1d.0: reg 10: [mem 0xfe525000-0xfe5253ff]
[    0.539016] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.539020] pci 0000:00:1d.0: PME# disabled
[    0.539048] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.539149] pci 0000:00:1f.0: [8086:1c4e] type 0 class 0x000601
[    0.539312] pci 0000:00:1f.2: [8086:1c00] type 0 class 0x000101
[    0.539337] pci 0000:00:1f.2: reg 10: [io  0xf130-0xf137]
[    0.539350] pci 0000:00:1f.2: reg 14: [io  0xf120-0xf123]
[    0.539363] pci 0000:00:1f.2: reg 18: [io  0xf110-0xf117]
[    0.539376] pci 0000:00:1f.2: reg 1c: [io  0xf100-0xf103]
[    0.539387] pci 0000:00:1f.2: reg 20: [io  0xf0f0-0xf0ff]
[    0.539401] pci 0000:00:1f.2: reg 24: [io  0xf0e0-0xf0ef]
[    0.539484] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.539507] pci 0000:00:1f.3: reg 10: [mem 0xfe524000-0xfe5240ff 64bit]
[    0.539542] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.539597] pci 0000:00:1f.5: [8086:1c08] type 0 class 0x000101
[    0.539624] pci 0000:00:1f.5: reg 10: [io  0xf0d0-0xf0d7]
[    0.539636] pci 0000:00:1f.5: reg 14: [io  0xf0c0-0xf0c3]
[    0.539649] pci 0000:00:1f.5: reg 18: [io  0xf0b0-0xf0b7]
[    0.539659] pci 0000:00:1f.5: reg 1c: [io  0xf0a0-0xf0a3]
[    0.539672] pci 0000:00:1f.5: reg 20: [io  0xf090-0xf09f]
[    0.539685] pci 0000:00:1f.5: reg 24: [io  0xf080-0xf08f]
[    0.539832] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.539838] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.539843] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.539852] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.539958] pci 0000:02:00.0: [8086:10d3] type 0 class 0x000200
[    0.539994] pci 0000:02:00.0: reg 10: [mem 0xfe400000-0xfe41ffff]
[    0.540043] pci 0000:02:00.0: reg 18: [io  0xe000-0xe01f]
[    0.540069] pci 0000:02:00.0: reg 1c: [mem 0xfe420000-0xfe423fff]
[    0.540283] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.540292] pci 0000:02:00.0: PME# disabled
[    0.545704] pci 0000:00:1c.6: PCI bridge to [bus 02-02]
[    0.545710] pci 0000:00:1c.6:   bridge window [io  0xe000-0xefff]
[    0.545714] pci 0000:00:1c.6:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.545722] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.545811] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.545817] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.545822] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.545830] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.545831] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.545833] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.545834] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.545836] pci 0000:00:1e.0:   bridge window [mem 0xbfa00000-0xffffffff] (subtractive decode)
[    0.545862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.545918] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.545944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.545966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
[    0.546039]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.546127]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.546130] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.548539] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.548571] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.548602] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.548633] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.548663] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.548693] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.548724] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.548754] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.548819] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.548825] vgaarb: loaded
[    0.548827] vgaarb: bridge control possible 0000:00:02.0
[    0.548930] SCSI subsystem initialized
[    0.548966] libata version 3.00 loaded.
[    0.548990] usbcore: registered new interface driver usbfs
[    0.548997] usbcore: registered new interface driver hub
[    0.549010] usbcore: registered new device driver usb
[    0.549055] PCI: Using ACPI for IRQ routing
[    0.559438] PCI: pci_cache_line_size set to 64 bytes
[    0.559512] reserve RAM buffer: 000000000009c000 - 000000000009ffff 
[    0.559513] reserve RAM buffer: 00000000bad93000 - 00000000bbffffff 
[    0.559516] reserve RAM buffer: 00000000bae0c000 - 00000000bbffffff 
[    0.559518] reserve RAM buffer: 00000000bb000000 - 00000000bbffffff 
[    0.559519] reserve RAM buffer: 000000023e600000 - 000000023fffffff 
[    0.559581] NetLabel: Initializing
[    0.559584] NetLabel:  domain hash size = 128
[    0.559585] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.559593] NetLabel:  unlabeled traffic allowed by default
[    0.559622] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.559628] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.561641] Switching to clocksource hpet
[    0.561825] Switched to NOHz mode on CPU #1
[    0.561829] Switched to NOHz mode on CPU #2
[    0.561833] Switched to NOHz mode on CPU #3
[    0.565177] AppArmor: AppArmor Filesystem Enabled
[    0.565196] pnp: PnP ACPI init
[    0.565207] ACPI: bus type pnp registered
[    0.565302] pnp 00:00: [bus 00-ff]
[    0.565304] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.565305] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.565306] pnp 00:00: [io  0x0d00-0xffff window]
[    0.565307] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.565309] pnp 00:00: [mem 0x000c8000-0x000dffff window]
[    0.565310] pnp 00:00: [mem 0xbfa00000-0xffffffff window]
[    0.565311] pnp 00:00: [mem 0x00000000 window]
[    0.565355] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.565390] pnp 00:01: [mem 0xfed10000-0xfed19fff]
[    0.565391] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.565393] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.565394] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.565395] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.565420] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.565423] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.565426] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.565429] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.565432] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.565435] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.565502] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.565504] pnp 00:02: [io  0x0a00-0x0a1f]
[    0.565505] pnp 00:02: [io  0x0a30-0x0a3f]
[    0.565506] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.565526] system 00:02: [io  0x0a00-0x0a1f] has been reserved
[    0.565528] system 00:02: [io  0x0a30-0x0a3f] has been reserved
[    0.565531] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.565546] pnp 00:03: [io  0x0060]
[    0.565547] pnp 00:03: [io  0x0064]
[    0.565555] pnp 00:03: [irq 1]
[    0.565569] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.565593] pnp 00:04: [irq 12]
[    0.565608] pnp 00:04: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.565684] Switched to NOHz mode on CPU #0
[    0.565927] pnp 00:05: [io  0x03f8-0x03ff]
[    0.565931] pnp 00:05: [irq 4]
[    0.565932] pnp 00:05: [dma 0 disabled]
[    0.565964] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.566110] pnp 00:06: [io  0x02f8-0x02ff]
[    0.566114] pnp 00:06: [irq 3]
[    0.566115] pnp 00:06: [dma 0 disabled]
[    0.566145] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.566293] pnp 00:07: [io  0x02a0-0x02a7]
[    0.566295] pnp 00:07: IRQ 10 override to level, low
[    0.566300] pnp 00:07: [irq 10]
[    0.566302] pnp 00:07: [dma 0 disabled]
[    0.566320] pnp 00:07: Plug and Play ACPI device, IDs FIT0002 (active)
[    0.566329] pnp 00:08: [dma 4]
[    0.566330] pnp 00:08: [io  0x0000-0x000f]
[    0.566331] pnp 00:08: [io  0x0081-0x0083]
[    0.566332] pnp 00:08: [io  0x0087]
[    0.566333] pnp 00:08: [io  0x0089-0x008b]
[    0.566334] pnp 00:08: [io  0x008f]
[    0.566335] pnp 00:08: [io  0x00c0-0x00df]
[    0.566346] pnp 00:08: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.566352] pnp 00:09: [io  0x0070-0x0071]
[    0.566356] pnp 00:09: [irq 8]
[    0.566369] pnp 00:09: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.566373] pnp 00:0a: [io  0x0061]
[    0.566384] pnp 00:0a: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.566393] pnp 00:0b: [io  0x0010-0x001f]
[    0.566394] pnp 00:0b: [io  0x0022-0x003f]
[    0.566395] pnp 00:0b: [io  0x0044-0x005f]
[    0.566396] pnp 00:0b: [io  0x0062-0x0063]
[    0.566397] pnp 00:0b: [io  0x0065-0x006f]
[    0.566398] pnp 00:0b: [io  0x0072-0x007f]
[    0.566399] pnp 00:0b: [io  0x0080]
[    0.566400] pnp 00:0b: [io  0x0084-0x0086]
[    0.566401] pnp 00:0b: [io  0x0088]
[    0.566402] pnp 00:0b: [io  0x008c-0x008e]
[    0.566404] pnp 00:0b: [io  0x0090-0x009f]
[    0.566405] pnp 00:0b: [io  0x00a2-0x00bf]
[    0.566406] pnp 00:0b: [io  0x00e0-0x00ef]
[    0.566407] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.566432] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.566435] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.566440] pnp 00:0c: [io  0x00f0-0x00ff]
[    0.566444] pnp 00:0c: [irq 13]
[    0.566456] pnp 00:0c: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.566554] pnp 00:0d: [io  0x0400-0x0453]
[    0.566555] pnp 00:0d: [io  0x0458-0x047f]
[    0.566556] pnp 00:0d: [io  0x1180-0x119f]
[    0.566559] pnp 00:0d: [io  0x0500-0x057f]
[    0.566560] pnp 00:0d: [mem 0xfed1c000-0xfed1ffff]
[    0.566561] pnp 00:0d: [mem 0xfec00000-0xfecfffff]
[    0.566562] pnp 00:0d: [mem 0xfed08000-0xfed08fff]
[    0.566563] pnp 00:0d: [mem 0xff000000-0xffffffff]
[    0.566585] system 00:0d: [io  0x0400-0x0453] has been reserved
[    0.566588] system 00:0d: [io  0x0458-0x047f] has been reserved
[    0.566590] system 00:0d: [io  0x1180-0x119f] has been reserved
[    0.566593] system 00:0d: [io  0x0500-0x057f] has been reserved
[    0.566596] system 00:0d: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.566599] system 00:0d: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.566601] system 00:0d: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.566604] system 00:0d: [mem 0xff000000-0xffffffff] has been reserved
[    0.566607] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.566630] pnp 00:0e: [io  0x0454-0x0457]
[    0.566651] system 00:0e: [io  0x0454-0x0457] has been reserved
[    0.566655] system 00:0e: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.566721] pnp 00:0f: [mem 0xfed00000-0xfed003ff]
[    0.566741] pnp 00:0f: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.566837] pnp: PnP ACPI: found 16 devices
[    0.566839] ACPI: ACPI bus type pnp unregistered
[    0.572059] PCI: max bus depth: 1 pci_try_num: 2
[    0.572096] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.572099] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.572106] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.572112] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.572122] pci 0000:00:1c.6: PCI bridge to [bus 02-02]
[    0.572125] pci 0000:00:1c.6:   bridge window [io  0xe000-0xefff]
[    0.572133] pci 0000:00:1c.6:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.572139] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.572147] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.572149] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.572157] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.572162] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.572181] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.572188] pci 0000:00:1c.0: setting latency timer to 64
[    0.572197] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.572202] pci 0000:00:1c.6: setting latency timer to 64
[    0.572210] pci 0000:00:1e.0: setting latency timer to 64
[    0.572214] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.572215] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.572217] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.572218] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xffffffff]
[    0.572220] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.572221] pci_bus 0000:02: resource 1 [mem 0xfe400000-0xfe4fffff]
[    0.572222] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.572224] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.572225] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.572227] pci_bus 0000:03: resource 7 [mem 0xbfa00000-0xffffffff]
[    0.572246] NET: Registered protocol family 2
[    0.572412] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.573115] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.574166] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.574294] TCP: Hash tables configured (established 524288 bind 65536)
[    0.574297] TCP reno registered
[    0.574309] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.574337] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.574409] NET: Registered protocol family 1
[    0.574420] pci 0000:00:02.0: Boot video device
[    0.925693] PCI: CLS 64 bytes, default 64
[    0.925695] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.925699] Placing 64MB software IO TLB between ffff8800b6d93000 - ffff8800bad93000
[    0.925702] software IO TLB at phys 0xb6d93000 - 0xbad93000
[    0.925985] audit: initializing netlink socket (disabled)
[    0.925995] type=2000 audit(1334020033.768:1): initialized
[    0.949310] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.965173] VFS: Disk quotas dquot_6.5.2
[    0.965209] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.965555] fuse init (API version 7.16)
[    0.965606] msgmni has been set to 15757
[    0.965917] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.965943] io scheduler noop registered
[    0.965945] io scheduler deadline registered (default)
[    0.965967] io scheduler cfq registered
[    0.966165] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.966179] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.966205] intel_idle: MWAIT substates: 0x1120
[    0.966206] intel_idle: v0.4 model 0x2A
[    0.966207] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.966272] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.966278] ACPI: Power Button [PWRB]
[    0.966301] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.966305] ACPI: Power Button [PWRF]
[    0.966324] ACPI: acpi_idle yielding to intel_idle
[    0.971026] thermal LNXTHERM:00: registered as thermal_zone0
[    0.971029] ACPI: Thermal Zone [THRM] (51 C)
[    0.971044] ERST: Table is not found!
[    0.971086] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.991489] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.001381] Freeing initrd memory: 13656k freed
[    1.082041] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.178094] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.198531] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.198611] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.218818] 0000:00:16.3: ttyS4 at I/O 0xf140 (irq = 17) is a 16550A
[    1.221782] Linux agpgart interface v0.103
[    1.221831] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.221923] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.222809] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.222891] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.223448] brd: module loaded
[    1.223699] loop: module loaded
[    1.223800] ata_piix 0000:00:1f.2: version 2.13
[    1.223816] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.223823] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.377589] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.377780] scsi0 : ata_piix
[    1.377843] scsi1 : ata_piix
[    1.378513] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf0f0 irq 14
[    1.378520] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf0f8 irq 15
[    1.378535] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.378542] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.378573] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.378692] scsi2 : ata_piix
[    1.378732] scsi3 : ata_piix
[    1.379313] ata3: SATA max UDMA/133 cmd 0xf0d0 ctl 0xf0c0 bmdma 0xf090 irq 19
[    1.379318] ata4: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf098 irq 19
[    1.379345] pata_acpi 0000:00:16.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.379361] pata_acpi 0000:00:16.2: setting latency timer to 64
[    1.379372] pata_acpi 0000:00:16.2: PCI INT C disabled
[    1.379397] ata_generic 0000:00:16.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.379412] ata_generic 0000:00:16.2: setting latency timer to 64
[    1.379556] scsi4 : ata_generic
[    1.379596] scsi5 : ata_generic
[    1.379613] ata5: PATA max UDMA/100 cmd 0xf190 ctl 0xf180 bmdma 0xf150 irq 18
[    1.379616] ata6: PATA max UDMA/100 cmd 0xf170 ctl 0xf160 bmdma 0xf158 irq 18
[    1.379761] Fixed MDIO Bus: probed
[    1.379775] PPP generic driver version 2.4.2
[    1.379796] tun: Universal TUN/TAP device driver, 1.6
[    1.379798] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.379845] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.379860] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.379873] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.379876] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.379896] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.379923] ehci_hcd 0000:00:1a.0: debug port 2
[    1.383821] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.383831] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe526000
[    1.397564] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.397676] hub 1-0:1.0: USB hub found
[    1.397680] hub 1-0:1.0: 3 ports detected
[    1.397721] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.397732] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.397735] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.397755] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.397778] ehci_hcd 0000:00:1d.0: debug port 2
[    1.401673] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.401683] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe525000
[    1.417559] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.417662] hub 2-0:1.0: USB hub found
[    1.417666] hub 2-0:1.0: 3 ports detected
[    1.417701] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.417708] uhci_hcd: USB Universal Host Controller Interface driver
[    1.417749] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.418131] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.418136] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.418170] mousedev: PS/2 mouse device common for all mice
[    1.418229] rtc_cmos 00:09: RTC can wake from S4
[    1.418307] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.418337] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.418393] device-mapper: uevent: version 1.0.3
[    1.418432] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.418488] cpuidle: using governor ladder
[    1.418572] cpuidle: using governor menu
[    1.418575] EFI Variables Facility v0.08 2004-May-17
[    1.418697] TCP cubic registered
[    1.418767] NET: Registered protocol family 10
[    1.419007] NET: Registered protocol family 17
[    1.419016] Registering the dns_resolver key type
[    1.419066] PM: Hibernation image not present or could not be loaded.
[    1.419073] registered taskstats version 1
[    1.431072]   Magic number: 8:903:103
[    1.431188] rtc_cmos 00:09: setting system clock to 2012-04-10 01:07:14 UTC (1334020034)
[    1.431685] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.431687] EDD information not available.
[    1.709514] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.842113] hub 1-1:1.0: USB hub found
[    1.842194] hub 1-1:1.0: 6 ports detected
[    1.853543] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.853679] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.862026] ata3.00: ATA-8: ST2000DL003-9VT166, CC3C, max UDMA/133
[    1.862034] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.862115] ata4.00: ATA-8: ST2000DL003-9VT166, CC3C, max UDMA/133
[    1.862117] ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.877866] ata4.00: configured for UDMA/133
[    1.878048] ata3.00: configured for UDMA/133
[    1.925465] Refined TSC clocksource calibration: 3092.973 MHz.
[    1.925474] Switching to clocksource tsc
[    1.953461] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.086048] hub 2-1:1.0: USB hub found
[    2.086128] hub 2-1:1.0: 8 ports detected
[    2.173498] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.173515] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.202594] ata1.00: ATA-7: WDC WD5000AAJS-00TKA0, 12.01C01, max UDMA/133
[    2.202602] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.202915] ata1.01: ATA-8: ST2000DL003-9VT166, CC3C, max UDMA/133
[    2.202923] ata1.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.218118] ata1.00: configured for UDMA/133
[    2.233892] ata1.01: configured for UDMA/133
[    2.234103] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-0 12.0 PQ: 0 ANSI: 5
[    2.234190] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.234255] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.234273] scsi 0:0:1:0: Direct-Access     ATA      ST2000DL003-9VT1 CC3C PQ: 0 ANSI: 5
[    2.234343] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    2.234451] sd 0:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.234455] sd 0:0:1:0: [sdb] 4096-byte physical blocks
[    2.234471] sd 0:0:0:0: [sda] Write Protect is off
[    2.234474] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.234581] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.234595] sd 0:0:1:0: [sdb] Write Protect is off
[    2.234599] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.234694] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.280251]  sda: sda1 sda2 < sda5 >
[    2.315538]  sdb: sdb1
[    2.315737] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.316087] sd 0:0:1:0: [sdb] Attached SCSI disk
[    2.357447] usb 2-1.3: new full speed USB device number 3 using ehci_hcd
[    2.405347] ata2.00: failed to resume link (SControl 0)
[    2.451205] hub 2-1.3:1.0: USB hub found
[    2.451430] hub 2-1.3:1.0: 3 ports detected
[    2.721495] usb 2-1.3.1: new full speed USB device number 4 using ehci_hcd
[    2.881332] ata2.00: SATA link down (SStatus 4 SControl 0)
[    2.881347] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.897759] ata2.01: ATA-8: ST2000DL003-9VT166, CC3C, max UDMA/133
[    2.897767] ata2.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.913749] ata2.01: configured for UDMA/133
[    2.913936] scsi 1:0:1:0: Direct-Access     ATA      ST2000DL003-9VT1 CC3C PQ: 0 ANSI: 5
[    2.914018] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    2.914099] sd 1:0:1:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.914103] sd 1:0:1:0: [sdc] 4096-byte physical blocks
[    2.914211] scsi 2:0:0:0: Direct-Access     ATA      ST2000DL003-9VT1 CC3C PQ: 0 ANSI: 5
[    2.914286] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    2.914381] sd 2:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.914385] sd 2:0:0:0: [sdd] 4096-byte physical blocks
[    2.914426] scsi 3:0:0:0: Direct-Access     ATA      ST2000DL003-9VT1 CC3C PQ: 0 ANSI: 5
[    2.914496] sd 3:0:0:0: Attached scsi generic sg4 type 0
[    2.914518] sd 1:0:1:0: [sdc] Write Protect is off
[    2.914521] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    2.914609] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.914660] sd 3:0:0:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.914664] sd 3:0:0:0: [sde] 4096-byte physical blocks
[    2.914765] sd 2:0:0:0: [sdd] Write Protect is off
[    2.914769] sd 2:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.914833] sd 3:0:0:0: [sde] Write Protect is off
[    2.914837] sd 3:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.914848] sd 2:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.914930] sd 3:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.968108]  sde: sde1
[    2.968376] sd 3:0:0:0: [sde] Attached SCSI disk
[    2.970076]  sdc: sdc1
[    2.970433] sd 1:0:1:0: [sdc] Attached SCSI disk
[    2.973494]  sdd: sdd1
[    2.973965] sd 2:0:0:0: [sdd] Attached SCSI disk
[    3.081685] Freeing unused kernel memory: 904k freed
[    3.081762] Write protecting the kernel read-only data: 12288k
[    3.085728] Freeing unused kernel memory: 1952k freed
[    3.088528] Freeing unused kernel memory: 1360k freed
[    3.098877] udevd[103]: starting version 173
[    3.100898] md: linear personality registered for level -1
[    3.104064] md: multipath personality registered for level -4
[    3.111040] md: raid0 personality registered for level 0
[    3.115957] md: raid1 personality registered for level 1
[    3.117622] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    3.117627] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    3.117657] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.117668] e1000e 0000:00:19.0: setting latency timer to 64
[    3.117788] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    3.130520] async_tx: api initialized (async)
[    3.136823] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.0/input/input2
[    3.136885] generic-usb 0003:413C:2002.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.0-1.3.1/input0
[    3.138131] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.1/input/input3
[    3.138167] generic-usb 0003:413C:2002.0002: input,hidraw1: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.0-1.3.1/input1
[    3.138178] usbcore: registered new interface driver usbhid
[    3.138179] usbhid: USB HID core driver
[    3.183643] mdadm: sending ioctl 1261 to a partition!
[    3.183647] mdadm: sending ioctl 1261 to a partition!
[    3.183915] mdadm: sending ioctl 1261 to a partition!
[    3.183917] mdadm: sending ioctl 1261 to a partition!
[    3.184149] mdadm: sending ioctl 1261 to a partition!
[    3.184161] mdadm: sending ioctl 1261 to a partition!
[    3.184757] mdadm: sending ioctl 1261 to a partition!
[    3.184760] mdadm: sending ioctl 1261 to a partition!
[    3.184913] mdadm: sending ioctl 1261 to a partition!
[    3.184916] mdadm: sending ioctl 1261 to a partition!
[    3.188261] md: bind<sde1>
[    3.195024] md: bind<sdc1>
[    3.197182] raid6: int64x1   3123 MB/s
[    3.208907] md: bind<sdd1>
[    3.265152] raid6: int64x2   3968 MB/s
[    3.317941] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:30:18:a3:48:74
[    3.317945] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.317978] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    3.317989] e1000e 0000:02:00.0: Disabling ASPM L0s 
[    3.318003] e1000e 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.318027] e1000e 0000:02:00.0: setting latency timer to 64
[    3.318319] e1000e 0000:02:00.0: irq 41 for MSI/MSI-X
[    3.318322] e1000e 0000:02:00.0: irq 42 for MSI/MSI-X
[    3.318324] e1000e 0000:02:00.0: irq 43 for MSI/MSI-X
[    3.333148] raid6: int64x4   3394 MB/s
[    3.335884] md: bind<sdb1>
[    3.337690] md: kicking non-fresh sdc1 from array!
[    3.337694] md: unbind<sdc1>
[    3.401119] raid6: int64x8   2694 MB/s
[    3.430477] e1000e 0000:02:00.0: eth1: (PCI Express:2.5GT/s:Width x1) 00:30:18:a3:48:75
[    3.430482] e1000e 0000:02:00.0: eth1: Intel(R) PRO/1000 Network Connection
[    3.430568] e1000e 0000:02:00.0: eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.469098] raid6: sse2x1    9010 MB/s
[    3.537079] raid6: sse2x2   11100 MB/s
[    3.605066] raid6: sse2x4   12903 MB/s
[    3.605068] raid6: using algorithm sse2x4 (12903 MB/s)
[    3.605538] xor: automatically using best checksumming function: generic_sse
[    3.625062]    generic_sse: 15038.000 MB/sec
[    3.625065] xor: using function: generic_sse (15038.000 MB/sec)
[    3.625840] md: raid6 personality registered for level 6
[    3.625844] md: raid5 personality registered for level 5
[    3.625846] md: raid4 personality registered for level 4
[    3.628342] md: raid10 personality registered for level 10
[    3.637220] md: export_rdev(sdc1)
[    3.638060] bio: create slab <bio-1> at 1
[    3.638074] md/raid:md0: device sdb1 operational as raid disk 0
[    3.638077] md/raid:md0: device sdd1 operational as raid disk 2
[    3.638079] md/raid:md0: device sde1 operational as raid disk 1
[    3.638291] md/raid:md0: allocated 3230kB
[    3.638373] md/raid:md0: raid level 5 active with 3 out of 3 devices, algorithm 2
[    3.638375] RAID conf printout:
[    3.638376]  --- level:5 rd:3 wd:3
[    3.638377]  disk 0, o:1, dev:sdb1
[    3.638378]  disk 1, o:1, dev:sde1
[    3.638379]  disk 2, o:1, dev:sdd1
[    3.638394] md0: detected capacity change from 0 to 4000792444928
[    3.645183]  md0: unknown partition table
[    3.787577] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.488967] udevd[376]: starting version 173
[   10.539789] Adding 8276988k swap on /dev/sda5.  Priority:-1 extents:1 across:8276988k 
[   10.540131] scsi_verify_blk_ioctl: 116 callbacks suppressed
[   10.540133] mdadm: sending ioctl 1261 to a partition!
[   10.540134] mdadm: sending ioctl 1261 to a partition!
[   10.542130] lp: driver loaded but no devices found
[   10.542351] [drm] Initialized drm 1.1.0 20060810
[   10.543447] coretemp coretemp.0: TjMax is 99 C.
[   10.543453] coretemp coretemp.0: TjMax is 99 C.
[   10.543459] coretemp coretemp.0: TjMax is 99 C.
[   10.543466] coretemp coretemp.0: TjMax is 99 C.
[   10.544522] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   10.544810] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.544815] mei 0000:00:16.0: setting latency timer to 64
[   10.546212] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.552519] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   10.554578] fintek_cir: first portsel read was bunk, trying alt
[   10.554619] fintek_cir: Unknown vendor ID: 0xff05
[   10.556193] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   10.557594] IR NEC protocol handler initialized
[   10.559152] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.559156] i915 0000:00:02.0: setting latency timer to 64
[   10.559546] IR RC5(x) protocol handler initialized
[   10.560108] IR RC6 protocol handler initialized
[   10.567423] IR JVC protocol handler initialized
[   10.570701] IR Sony protocol handler initialized
[   10.571539] lirc_dev: IR Remote Control driver registered, major 249 
[   10.571677] IR LIRC bridge handler initialized
[   10.587523] Registered IR keymap rc-rc6-mce
[   10.587576] input: Fintek LPC SuperIO Consumer IR Transceiver as /devices/pnp0/00:07/rc/rc0/input4
[   10.587638] rc0: Fintek LPC SuperIO Consumer IR Transceiver as /devices/pnp0/00:07/rc/rc0
[   10.587820] rc rc0: lirc_dev: driver ir-lirc-codec (fintek-cir) registered at minor = 0
[   10.587825] fintek_cir: driver has been successfully loaded
[   10.601952] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   10.601957] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.601958] [drm] Driver supports precise vblank timestamp query.
[   10.601983] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.603377] mdadm: sending ioctl 1261 to a partition!
[   10.603379] mdadm: sending ioctl 1261 to a partition!
[   10.603662] type=1400 audit(1334020043.670:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=461 comm="apparmor_parser"
[   10.603901] type=1400 audit(1334020043.670:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=461 comm="apparmor_parser"
[   10.604053] type=1400 audit(1334020043.670:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=461 comm="apparmor_parser"
[   10.604809] type=1400 audit(1334020043.670:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=463 comm="apparmor_parser"
[   10.605048] type=1400 audit(1334020043.670:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
[   10.605200] type=1400 audit(1334020043.670:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
[   10.605951] type=1400 audit(1334020043.670:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=509 comm="apparmor_parser"
[   10.606191] type=1400 audit(1334020043.670:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=509 comm="apparmor_parser"
[   10.606342] type=1400 audit(1334020043.670:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=509 comm="apparmor_parser"
[   10.606654] mdadm: sending ioctl 1261 to a partition!
[   10.606656] mdadm: sending ioctl 1261 to a partition!
[   10.608361] mdadm: sending ioctl 1261 to a partition!
[   10.608363] mdadm: sending ioctl 1261 to a partition!
[   10.609089] mdadm: sending ioctl 1261 to a partition!
[   10.609091] mdadm: sending ioctl 1261 to a partition!
[   10.763664] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   10.823566] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   10.824027] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.017550] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.371962] fbcon: inteldrmfb (fb0) is primary device
[   11.429723] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
[   12.111833] Console: switching to colour frame buffer device 160x64
[   12.114230] fb0: inteldrmfb frame buffer device
[   12.114231] drm: registered panic notifier
[   12.114946] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   12.114983] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.115021] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.115178] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.115262] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   12.115293] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.138044] irq 10: nobody cared (try booting with the "irqpoll" option)
[   12.138069] Pid: 0, comm: swapper Tainted: G         C  3.0.0-17-server #30-Ubuntu
[   12.138071] Call Trace:
[   12.138072]  <IRQ>  [<ffffffff810cf31d>] __report_bad_irq+0x3d/0xe0
[   12.138079]  [<ffffffff810cf5a5>] note_interrupt+0x135/0x180
[   12.138081]  [<ffffffff810cd559>] handle_irq_event_percpu+0xa9/0x220
[   12.138083]  [<ffffffff810cd71e>] handle_irq_event+0x4e/0x80
[   12.138085]  [<ffffffff810cfed4>] handle_fasteoi_irq+0x64/0xf0
[   12.138087]  [<ffffffff8100c212>] handle_irq+0x22/0x40
[   12.138090]  [<ffffffff816116ea>] do_IRQ+0x5a/0xe0
[   12.138092]  [<ffffffff81607d13>] common_interrupt+0x13/0x13
[   12.138095]  [<ffffffff81065f90>] ? __do_softirq+0x60/0x210
[   12.138098]  [<ffffffff816077fe>] ? _raw_spin_lock+0xe/0x20
[   12.138100]  [<ffffffff81610e9c>] ? call_softirq+0x1c/0x30
[   12.138101]  [<ffffffff8100c295>] ? do_softirq+0x65/0xa0
[   12.138103]  [<ffffffff810663be>] ? irq_exit+0x8e/0xb0
[   12.138105]  [<ffffffff816116f3>] ? do_IRQ+0x63/0xe0
[   12.138106]  [<ffffffff81607d13>] ? common_interrupt+0x13/0x13
[   12.138107]  <EOI>  [<ffffffff814c5111>] ? poll_idle+0x41/0x80
[   12.138111]  [<ffffffff814c50e3>] ? poll_idle+0x13/0x80
[   12.138112]  [<ffffffff814c53ed>] ? cpuidle_idle_call+0x9d/0x280
[   12.138115]  [<ffffffff8100920b>] ? cpu_idle+0xab/0x100
[   12.138119]  [<ffffffff815d177e>] ? rest_init+0x72/0x74
[   12.138122]  [<ffffffff81ce7c2b>] ? start_kernel+0x3d4/0x3df
[   12.138124]  [<ffffffff81ce7388>] ? x86_64_start_reservations+0x132/0x136
[   12.138125]  [<ffffffff81ce7140>] ? early_idt_handlers+0x140/0x140
[   12.138127]  [<ffffffff81ce7459>] ? x86_64_start_kernel+0xcd/0xdc
[   12.138128] handlers:
[   12.138141] [<ffffffffa02eb9f0>] fintek_cir_isr
[   12.138157] Disabling IRQ #10
[   12.675262] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
[   12.675403] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.411605] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   14.412005] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.418714] [UFW BLOCK] IN= OUT=eth0 SRC=0000:0000:0000:0000:0000:0000:0000:0000 DST=ff02:0000:0000:0000:0000:0000:0000:0016 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=143 CODE=0 
[   15.962383] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:0002 LEN=56 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=ICMPv6 TYPE=133 CODE=0 
[   15.970359] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:0016 LEN=96 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=143 CODE=0 
[   16.009959] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=250 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=210 
[   16.032175] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=428 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=388 
[   16.282711] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=428 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=388 
[   16.533349] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=428 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=388 
[   16.733792] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=398 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=358 
[   17.029316] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=250 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=210 
[   17.753164] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=398 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=358 
[   19.945477] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   20.022205] init: ssh main process (833) terminated with status 255
[   20.029569] init: failsafe main process (815) killed by TERM signal
[   20.037502] type=1400 audit(1334020053.106:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=967 comm="apparmor_parser"
[   20.037623] type=1400 audit(1334020053.106:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=966 comm="apparmor_parser"
[   20.037863] type=1400 audit(1334020053.106:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=966 comm="apparmor_parser"
[   20.038012] type=1400 audit(1334020053.106:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=966 comm="apparmor_parser"
[   20.093935] init: apport pre-start process (1017) terminated with status 1
[   20.096289] init: apport post-stop process (1038) terminated with status 1
[   20.163570] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
[   20.537738] init: plymouth-upstart-bridge main process (853) killed by TERM signal
[   21.663387] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=239.255.255.250 LEN=165 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1901 DPT=1900 LEN=145 
[   21.665093] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=224.0.0.22 LEN=48 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   21.674135] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=239.255.255.250 LEN=165 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=145 
[   22.163183] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
[   24.162704] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
[   24.980353] eth0: no IPv6 routers present
[   26.162267] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
[   30.035256] [UFW BLOCK] IN= OUT=eth0 SRC=192.168.1.101 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   33.732043] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=26665 DF PROTO=TCP SPT=60837 DPT=6283 WINDOW=65535 RES=0x00 SYN URGP=0 
[   33.734312] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=43353 DF PROTO=TCP SPT=60838 DPT=18530 WINDOW=65535 RES=0x00 SYN URGP=0 
[   33.736568] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=55089 DF PROTO=TCP SPT=60839 DPT=7179 WINDOW=65535 RES=0x00 SYN URGP=0 
[   36.026472] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=91 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=51 
[  205.554855] scsi_verify_blk_ioctl: 18 callbacks suppressed
[  205.554859] mdadm: sending ioctl 1261 to a partition!
[  205.554862] mdadm: sending ioctl 1261 to a partition!
[ 2799.953932] mdadm: sending ioctl 1261 to a partition!
[ 2799.953937] mdadm: sending ioctl 1261 to a partition!
[ 2799.975775] mdadm: sending ioctl 1261 to a partition!
[ 2799.975779] mdadm: sending ioctl 1261 to a partition!
[ 2800.004901] md: export_rdev(sdc1)
[ 2800.004933] mdadm: sending ioctl 1261 to a partition!
[ 2800.004935] mdadm: sending ioctl 1261 to a partition!
[ 2800.039111] mdadm: sending ioctl 1261 to a partition!
[ 2800.039115] mdadm: sending ioctl 1261 to a partition!
[ 2800.039898] mdadm: sending ioctl 1261 to a partition!
[ 2800.039902] mdadm: sending ioctl 1261 to a partition!
[ 2800.147867] md: bind<sdc1>
[ 3730.782005] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[ 4967.149509] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=140 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=100 
[ 4967.175958] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:86:dd SRC=fe80:0000:0000:0000:0223:dfff:fefe:04ea DST=fe80:0000:0000:0000:0230:18ff:fea3:4874 LEN=84 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=64685 DPT=548 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4967.496499] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=91 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=51 
[ 4972.899938] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:86:dd SRC=fe80:0000:0000:0000:0223:dfff:fefe:04ea DST=fe80:0000:0000:0000:0230:18ff:fea3:4874 LEN=84 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=64692 DPT=548 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4972.930730] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:86:dd SRC=fe80:0000:0000:0000:0223:dfff:fefe:04ea DST=fe80:0000:0000:0000:0230:18ff:fea3:4874 LEN=84 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=64695 DPT=548 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 5517.381154] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=140 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=100 
[ 5517.407435] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:86:dd SRC=fe80:0000:0000:0000:0223:dfff:fefe:04ea DST=fe80:0000:0000:0000:0230:18ff:fea3:4874 LEN=84 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=65285 DPT=548 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 5621.384612] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=140 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=100 
[ 5621.410201] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:86:dd SRC=fe80:0000:0000:0000:0223:dfff:fefe:04ea DST=fe80:0000:0000:0000:0230:18ff:fea3:4874 LEN=84 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=65365 DPT=548 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 5621.437982] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:86:dd SRC=fe80:0000:0000:0000:0223:dfff:fefe:04ea DST=fe80:0000:0000:0000:0230:18ff:fea3:4874 LEN=84 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=65368 DPT=548 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 5621.475528] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:86:dd SRC=fe80:0000:0000:0000:0223:dfff:fefe:04ea DST=fe80:0000:0000:0000:0230:18ff:fea3:4874 LEN=84 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=65371 DPT=548 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 5621.502942] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:86:dd SRC=fe80:0000:0000:0000:0223:dfff:fefe:04ea DST=fe80:0000:0000:0000:0230:18ff:fea3:4874 LEN=84 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=TCP SPT=65374 DPT=548 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 5861.944619] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=95 TOS=0x00 PREC=0x00 TTL=64 ID=23613 PROTO=UDP SPT=65294 DPT=28930 LEN=75 
[ 6708.853275] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=58 TOS=0x00 PREC=0x00 TTL=64 ID=5873 PROTO=UDP SPT=65294 DPT=28930 LEN=38 
[ 6708.853301] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=59347 DF PROTO=TCP SPT=50905 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6709.828149] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=26331 DF PROTO=TCP SPT=50905 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6710.829397] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=57825 DF PROTO=TCP SPT=50905 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6711.830771] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=51929 DF PROTO=TCP SPT=50905 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6711.853174] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=58 TOS=0x00 PREC=0x00 TTL=64 ID=23435 PROTO=UDP SPT=65294 DPT=28930 LEN=38 
[ 6712.832066] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=60108 DF PROTO=TCP SPT=50905 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6713.834201] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=43162 DF PROTO=TCP SPT=50905 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6715.835981] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=57266 DF PROTO=TCP SPT=50905 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6719.840675] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=48119 DF PROTO=TCP SPT=50905 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6804.827227] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=58 TOS=0x00 PREC=0x00 TTL=64 ID=10956 PROTO=UDP SPT=65294 DPT=28930 LEN=38 
[ 6807.826263] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=58 TOS=0x00 PREC=0x00 TTL=64 ID=38862 PROTO=UDP SPT=65294 DPT=28930 LEN=38 
[ 6812.824156] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=61347 DF PROTO=TCP SPT=51065 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6813.822333] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=41415 DF PROTO=TCP SPT=51065 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6814.822817] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=37280 DF PROTO=TCP SPT=51065 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 6831.838100] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=11572 DF PROTO=TCP SPT=51065 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7069.787416] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=58 TOS=0x00 PREC=0x00 TTL=64 ID=8204 PROTO=UDP SPT=65294 DPT=28930 LEN=38 
[ 7072.786750] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=58 TOS=0x00 PREC=0x00 TTL=64 ID=49965 PROTO=UDP SPT=65294 DPT=28930 LEN=38 
[ 7098.789026] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=2057 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7099.778482] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=7212 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7100.779333] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=28516 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7101.780416] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=19734 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7102.781560] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=38522 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7103.782636] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=58685 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7105.784664] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=54617 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7109.787179] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=42505 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7117.793975] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:18:a3:48:74:00:23:df:fe:04:ea:08:00 SRC=192.168.1.10 DST=192.168.1.101 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=49469 DF PROTO=TCP SPT=51561 DPT=28930 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 7330.369783] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[10929.794209] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[14529.348799] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[14766.683743] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:fb:e4:ce:8f:41:cc:30:86:dd SRC=fe80:0000:0000:0000:e6ce:8fff:fe41:cc30 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=131 CODE=0 
[14766.683846] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:e4:ce:8f:41:cc:30:08:00 SRC=192.168.1.15 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=47264 PROTO=2 
[14767.064213] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[14767.092500] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=113 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=73 
[14769.113884] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:e4:ce:8f:41:cc:30:08:00 SRC=192.168.1.15 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=45191 PROTO=2 
[14769.713759] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:fb:e4:ce:8f:41:cc:30:86:dd SRC=fe80:0000:0000:0000:e6ce:8fff:fe41:cc30 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=131 CODE=0 
[18128.881145] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[21725.272619] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[22230.694871] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:fb:e4:ce:8f:41:cc:30:86:dd SRC=fe80:0000:0000:0000:e6ce:8fff:fe41:cc30 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=131 CODE=0 
[22230.694928] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:e4:ce:8f:41:cc:30:08:00 SRC=192.168.1.15 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=42973 PROTO=2 
[22231.018502] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[22231.087770] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=113 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=73 
[22231.881044] [UFW BLOCK] IN=eth0 OUT= MAC=33:33:00:00:00:fb:e4:ce:8f:41:cc:30:86:dd SRC=fe80:0000:0000:0000:e6ce:8fff:fe41:cc30 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=72 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=131 CODE=0 
[22237.682710] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:e4:ce:8f:41:cc:30:08:00 SRC=192.168.1.15 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=62661 PROTO=2 
[25324.816048] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[28924.359050] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[32523.812816] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[36123.393754] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[39722.910353] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[43322.426517] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[46921.940939] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[50521.500890] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[54121.051080] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 
[54908.650398] scsi_verify_blk_ioctl: 36 callbacks suppressed
[54908.650400] mdadm: sending ioctl 1261 to a partition!
[54908.650402] mdadm: sending ioctl 1261 to a partition!
[57720.570972] [UFW BLOCK] IN= OUT=eth0 SRC=fe80:0000:0000:0000:0230:18ff:fea3:4874 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=167 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=5353 DPT=5353 LEN=127 

```

> 
4. What do you have in /etc/mdadm/mdadm.conf?
```
cat /etc/mdadm/mdadm.conf
```That should be enough to get me up to speed :)

```
[~]: cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR ****@gmail.com

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=9ec6ec09:8834b3f7:adc08875:2ae05753

```

---

### Post by rubylaser on 2012-04-10
You mdadm.conf looks good, and so does dmesg, other than the mdadm messages like this.
```
mdadm: sending ioctl 1261 to a partition!
```
But, those are harmless and will be suppressed in a newer kernel version.

Does the array run fine without using the array for Timemachine backups?  It would be nice to see the dmesg output the next time it drops a disk.  Right now, it's hard to tell what's happening, because everything is working as it should.

---

### Post by Bushflyr on 2012-04-10
The array seems to run fine when not being used for TM. I've been streaming from Subsonic all day and dumping files on it to try and make it fail. It's also been running TM backups fine. It **seems** to be an issue with TM and sleep, but I'll see if it's still working OK in the morning.

Again, thanks for your help. You posts in several other threads got some other issues I was having all sorted.

---

### Post by Vegan on 2012-04-10
using consumer grade disks for RAID is begging for trouble they will crap out frequently

:guitar:

---

### Post by Bushflyr on 2012-04-11
Why? Is RAID harder on them than regular use? Maybe I'm just lucky but in over 30 years I've (maybe) had 1 drive fail. That particular one may also be a failure of the enclosure. I've had 1 enclosure (POS Mybookworld) fail with the loss of all the data, but the dishs check out OK. I'm reusing them.

Besides, isn't that the point of the "inexpensive" in RAID? Use 'em, fail 'em, toss 'em.

---

### Post by Bushflyr on 2012-04-13
Thanks for the help rubylaser. I think you scared it into behaving. It's been up and running fine for the last two days. :confused: Maybe an issue with sdc, since that's now the spare, but I've done a few tests and they all come back fine. I'll 'fail' sde next and see if it rebuilds OK and stays up, but I think it's solved for now.

---

### Post by rubylaser on 2012-04-13
Great, thanks for the update :)  If you have problems in the future, please create a new thread, and I'll be happy to help for real next time.

---

