---
title: "RAID 5 failing to start after power failure"
date: 2010-09-13
forum: Server Platforms
---

### Post by Fafler on 2010-09-13
A SATA power connector broke in my home server the other day and now i can't assemble my RAID 5 array with all 3 drives. The solution is probably quite easy, but i'm hesitant to poke around with mdadm, because i don't want to break the array. I've tried this so far:

```
hydrogen:~# mdadm --examine /dev/sdb
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 56bd37e4:89d0f233:557cb023:ac19cb62 (local to host hydrogen)
  Creation Time : Fri Mar 12 13:12:00 2010
     Raid Level : raid5
  Used Dev Size : 1465137408 (1397.26 GiB 1500.30 GB)
     Array Size : 2930274816 (2794.53 GiB 3000.60 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Aug  8 12:02:52 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7a9f921b - correct
         Events : 55684

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
hydrogen:~# mdadm --examine /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 56bd37e4:89d0f233:557cb023:ac19cb62 (local to host hydrogen)
  Creation Time : Fri Mar 12 13:12:00 2010
     Raid Level : raid5
  Used Dev Size : 1465137408 (1397.26 GiB 1500.30 GB)
     Array Size : 2930274816 (2794.53 GiB 3000.60 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Mon Sep 13 20:27:53 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7ad44797 - correct
         Events : 212504

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       0        0        0      removed
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
hydrogen:~# mdadm --examine /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 56bd37e4:89d0f233:557cb023:ac19cb62 (local to host hydrogen)
  Creation Time : Fri Mar 12 13:12:00 2010
     Raid Level : raid5
  Used Dev Size : 1465137408 (1397.26 GiB 1500.30 GB)
     Array Size : 2930274816 (2794.53 GiB 3000.60 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Mon Sep 13 20:29:36 2010
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 7ad4481b - correct
         Events : 212504

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       48        2      active sync   /dev/sdd
hydrogen:~# mdadm -Af -vv /dev/md0 /dev/sdb /dev/sdc /dev/sdd
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdb to /dev/md0 as 0
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: /dev/md0 has been started with 2 drives (out of 3).
hydrogen:~# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sdc[1] sdd[2]
      2930274816 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      
unused devices: <none>
hydrogen:~# dd if=/dev/sdb of=/dev/null bs=1M count=200
200+0 records in
200+0 records out
209715200 bytes (210 MB) copied, 2,34163 s, 89,6 MB/s
hydrogen:~# smartctl --all /dev/sdb
smartctl 5.40 2010-07-12 r3124 [i686-pc-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format) family
Device Model:     WDC WD15EARS-00Z5B1
Serial Number:    WD-WMAVU1496644
Firmware Version: 80.00A80
User Capacity:    1.500.300.828.160 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Sep 13 21:27:09 2010 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (32400) seconds.
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
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3031)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   194   177   021    Pre-fail  Always       -       5266
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       114
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3605
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       112
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       91
193 Load_Cycle_Count        0x0032   195   195   000    Old_age   Always       -       17419
194 Temperature_Celsius     0x0022   114   103   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

hydrogen:~# 

```

As you can see, /dev/sdb (the connector that failed) isn't re-added to the array, but it's readable and smartctl doesn't show any errors. I have no idea what to make of the mdadm --examine commands.

The OS, by the way is Debian Squeeze and the reason i havent made any partitions and just use the raw block devices is the 4 kb block size issue that might or might not be present in the Linux kernel.

One things for sure. I'm ordering a bunch of these [http://cgi.ebay.com/IDE-SATA-Serial-ATA-Splitter-Power-Cable-Connector-/260571387845?pt=LH_DefaultDomain_0&hash=item3cab43d7c5](http://cgi.ebay.com/IDE-SATA-Serial-ATA-Splitter-Power-Cable-Connector-/260571387845?pt=LH_DefaultDomain_0&hash=item3cab43d7c5)
I've already changed the SATA cables to similar cables with locks, as the ones that came with the board kept falling out of the drives.

---

### Post by Fafler on 2010-09-14
mdadm -a /dev/sdb did the trick. Think i'll look into making a RAID monitoring applet for Gnome, as it seems the drive was actually removed from the RAID for 5 days before i noticed it.

---

