---
title: "mdadm RAID5 - lost 2 drives?/can't boot"
date: 2013-09-12
forum: Server Platforms
---

### Post by mark56 on 2013-09-12
Hi Guys,

Please bear with me, I'm not the most savvy Linux guy, but I try.  I have a 4 drive RAID5 array that failed on a reboot today.  I have 4x3TB WD Red's... and it's saying 2 have failed.  Upon using SMART Tools, all drives are passing (maybe I'm reading something wrong?).  I've done quite a lot of reading around here tonight, and haven't got far.  At first, I wasn't able to boot all the way in, instead getting stuck in busybox.  I found that CTRL D while in busybox actually got things booting, and has allowed me to get in and run the SMART Tools and such.  I also found the thread about the race condition not allowing you to boot, and to add "udevadm settle" to the degraded arrays statement in mdadm-functions.  That didn't help or fix anything in my case. 

From following similar threads, I hope I'm posting all the right outputs... wanted to get them all in before being asked for them as I won't be online till tomorrow night.  Really hoping there is a chance to get this functional in any way.  Even if just read only, to copy the data off.  Thanks in advance to any advice/assistance. 

```
root@MediaMaster:/home/mark# mdadm -D /dev/md0 /dev/md0:
        Version : 1.2
  Creation Time : Fri Mar  8 22:24:01 2013
     Raid Level : raid5
  Used Dev Size : -1
   Raid Devices : 4
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Thu Sep 12 19:14:08 2013
          State : active, FAILED, Not Started 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : MediaMaster:0  (local to host MediaMaster)
           UUID : 5876024f:4dbbcdfc:4d1dde3f:a9857ea3
         Events : 72623


    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       4       8       49        3      active sync   /dev/sdd1

```


```
root@MediaMaster:/home/mark# cat /proc/mdstat Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[2] sdd1[4]
      5860267886 blocks super 1.2
       
unused devices: <none>

```

```
root@MediaMaster:/home/mark# cat /etc/mdadm/mdadm.conf 
ARRAY /dev/md/0 level=raid5 num-devices=4 metadata=1.2 name=MediaMaster:0 UUID=5876024f:4dbbcdfc:4d1dde3f:a9857ea3
   devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1

```


```
root@MediaMaster:/home/mark# sudo mdadm --examine /dev/sd[abcd]
/dev/sda:                                                                                                                         
   MBR Magic : aa55                                                                                                               
Partition[0] :   4294967295 sectors at            1 (type ee)                                                                     
/dev/sdb:                                                                                                                         
   MBR Magic : aa55                                                                                                               
Partition[0] :   4294967295 sectors at            1 (type ee)                                                                     
/dev/sdc:                                                                                                                         
   MBR Magic : aa55                                                                                                               
Partition[0] :   4294967295 sectors at            1 (type ee)                                                                     
/dev/sdd:                                                                                                                         
   MBR Magic : aa55                                                                                                               
Partition[0] :   4294967295 sectors at            1 (type ee)  
```

```
root@MediaMaster:/home/mark# mdadm -E /dev/sd[abcd]1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5876024f:4dbbcdfc:4d1dde3f:a9857ea3
           Name : MediaMaster:0  (local to host MediaMaster)
  Creation Time : Fri Mar  8 22:24:01 2013
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860268943 (2794.39 GiB 3000.46 GB)
     Array Size : 8790398976 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860265984 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 54d279ea:40e33834:1151eef3:ec340b91


    Update Time : Thu Sep 12 15:00:34 2013
       Checksum : f10a7db1 - correct
         Events : 72604


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5876024f:4dbbcdfc:4d1dde3f:a9857ea3
           Name : MediaMaster:0  (local to host MediaMaster)
  Creation Time : Fri Mar  8 22:24:01 2013
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860268943 (2794.39 GiB 3000.46 GB)
     Array Size : 8790398976 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860265984 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 092eab09:74394fc1:c0bf0fd2:90142134


    Update Time : Thu Sep 12 15:00:34 2013
       Checksum : 1e897de9 - correct
         Events : 72604


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5876024f:4dbbcdfc:4d1dde3f:a9857ea3
           Name : MediaMaster:0  (local to host MediaMaster)
  Creation Time : Fri Mar  8 22:24:01 2013
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860268943 (2794.39 GiB 3000.46 GB)
     Array Size : 8790398976 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860265984 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ba109098:175133e9:5dc906d9:ed6559c6


    Update Time : Thu Sep 12 19:14:08 2013
       Checksum : 6e7d0ebc - correct
         Events : 72623


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : ..AA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5876024f:4dbbcdfc:4d1dde3f:a9857ea3
           Name : MediaMaster:0  (local to host MediaMaster)
  Creation Time : Fri Mar  8 22:24:01 2013
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860266830 (2794.39 GiB 3000.46 GB)
     Array Size : 8790398976 (8383.18 GiB 9001.37 GB)
  Used Dev Size : 5860265984 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5025ee4c:74ab696f:a7b704cb:85383d7e


    Update Time : Thu Sep 12 19:14:08 2013
       Checksum : 52f33651 - correct
         Events : 72623


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : ..AA ('A' == active, '.' == missing)



```


```
root@MediaMaster:/home/mark# smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WCC1T0877796
LU WWN Device Id: 5 0014ee 25dcb7aaa
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 12 23:42:17 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (41460) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   168   164   021    Pre-fail  Always       -       6583
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       25
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1227
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       25
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       21
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       3
194 Temperature_Celsius     0x0022   109   099   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


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


root@MediaMaster:/home/mark# smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WMC1T2501603
LU WWN Device Id: 5 0014ee 658841344
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 12 23:42:50 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (40680) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   184   179   021    Pre-fail  Always       -       5783
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       76
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4550
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       76
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       54
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       21
194 Temperature_Celsius     0x0022   111   101   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


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


root@MediaMaster:/home/mark# smartctl -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WMC1T2600294
LU WWN Device Id: 5 0014ee 658848302
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 12 23:42:52 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (42420) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   180   175   021    Pre-fail  Always       -       5966
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       75
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4551
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       75
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       53
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       21
194 Temperature_Celsius     0x0022   110   101   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


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


root@MediaMaster:/home/mark# smartctl -a /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WMC1T2561550
LU WWN Device Id: 5 0014ee 6588486a9
Firmware Version: 80.00A80
User Capacity:    3,000,591,900,160 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 12 23:42:54 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (39840) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   185   180   021    Pre-fail  Always       -       5741
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       77
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4531
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       77
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       55
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       21
194 Temperature_Celsius     0x0022   113   105   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


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
```

---

### Post by SaturnusDJ on 2013-09-13
Concerning S.M.A.R.T., you haven't run any S.M.A.R.T. tests ever.

To do this, run
```

smartctl -t short /dev/sda

```
for every drive.
But it might be a better time to do this after restoring the array.


For now, stay away from doing a re-create. This is last resort.

Start with this:
Stop the array:
```

mdadm --stop /dev/md0

```

Assemble with all drives:
```

mdadm --assemble /dev/md0 /dev/sd[b-e]1

```

This most likely will fail with a error.

Force and run it:
```

mdadm --assemble --force --run /dev/md0 /dev/sd[b-e]1

```

Here I assume /dev/sda is your startup drive. If the RAID array truly failed, you won't be able to boot from it, but since you were able to boot I assume you have a different boot disk.

---

### Post by mark56 on 2013-09-13
You say to assemble with all the drives by running this:

```
[COLOR=#000000][FONT=Ubuntu Mono]mdadm --assemble /dev/md0 /dev/sd[b-e]1
```

This is where I'm a little confused with my own system.  the mdadm.conf as I showed above does show sde1 as being part of it... but if you look at everything else, the array is made up of sd[abcd].

I have no idea why it's showing sde1 in mdadm.conf.  

In July, I had another drive failure, in which I replaced the drive.  this is when it was rebuilding back then (and has been working fine since)

```
[/FONT][/COLOR][COLOR=#500050][FONT=arial]mark@MediaMaster:~$ cat /proc/mdstat[/FONT][/COLOR][COLOR=#500050][FONT=arial]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
[/FONT][/COLOR]
[FONT=arial]md0 : active raid5 sdb1[1] sda1[5] sdc1[2] sdd1[4][/FONT]
[COLOR=#500050][FONT=arial]      8790398976 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [_UUU][/FONT][/COLOR]
[FONT=arial]      [==================>..]  recovery = 93.7% (2746662616/2930132992) finish=40.8min speed=74837K/sec
```

Is part of my problem in my mdadm.conf file?  [/FONT]

---

### Post by mark56 on 2013-09-13
Ok, so I went ahead with a-d instead of b-e, either way, this was the output of the commands:

```
root@MediaMaster:/home/mark# mdadm --stop /dev/md0 mdadm: stopped /dev/md0

root@MediaMaster:/home/mark# mdadm --assemble /dev/md0 /dev/sd[a-d]1
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

root@MediaMaster:/home/mark# mdadm --assemble --force --run /dev/md0 /dev/sd[a-d]1
mdadm: /dev/sda1 is busy - skipping
mdadm: /dev/sdb1 is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping

root@MediaMaster:/home/mark# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[2](S) sdd1[4](S) sdb1[1](S) sda1[5](S)
      11720536829 blocks super 1.2
       

```

---

### Post by SaturnusDJ on 2013-09-13
The skipping is because it already started with not enough members. So you have to use the stop command again before trying assemble with force and run flags.

If you are confused by the letters you can use the UUID:
```
mdadm --assemble /dev/md0 --uuid=5876024f:4dbbcdfc:4d1dde3f:a9857ea3
```

---

### Post by mark56 on 2013-09-13
Oh my god!  You're awesome!  I stopped it and re-ran my command, and presto it's there!!

```
[COLOR=#000000][FONT=Ubuntu Mono]mdadm --assemble /dev/md0 --uuid=5876024f:4dbbcdfc:4d1dde3f:a9857ea3
```[/FONT][/COLOR]

Now, can you please offer a suggestion as to where to go next?  I'm starting to get rather sour from RAID right now.  While this is the second time I've been able to recover, it's only been with the assistance of a good friend last time, and yourself this time.  

I'm serving Media all around my home.  I have about 7-8TB of data.  My friend is suggesting with the issues I've been having to possibly look into moving over to Windows Home Server and looking into UnRaid or FlexRAID.  Admittedly, I'd feel infinitely more comfortable in Windows Server, since I use it at work... but that's not very geeky of me, and honestly, my media streaming experience has been MUCH better with Linux vs Windows based serving.  

Moving over to JBOD is a lot less technical, but a drive loss is a total loss.  But it's better than a total array loss which is what I was really nervous about here.  LOL  

I'm open to suggestions, even if those suggestions are to stick with what I have, but to somehow improve my luck?  :-)  

Thanks so much, and thanks in advance.

---

### Post by mark56 on 2013-09-13
Short test has been run on all 4 drives, doesn't seem to be any errors.  Will probably run the long test tonight. 

```
root@MediaMaster:/home/mark# smartctl -a /dev/sdasmartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WCC1T0877796
LU WWN Device Id: 5 0014ee 25dcb7aaa
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Sep 13 17:03:13 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (41460) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   168   164   021    Pre-fail  Always       -       6583
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       25
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1245
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       25
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       21
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       3
194 Temperature_Celsius     0x0022   106   099   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1245         -


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


root@MediaMaster:/home/mark# smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WMC1T2501603
LU WWN Device Id: 5 0014ee 658841344
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Sep 13 17:03:15 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (40680) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   184   179   021    Pre-fail  Always       -       5783
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       76
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4568
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       76
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       54
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       21
194 Temperature_Celsius     0x0022   108   101   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      4568         -


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


root@MediaMaster:/home/mark# smartctl -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WMC1T2600294
LU WWN Device Id: 5 0014ee 658848302
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Sep 13 17:03:18 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (42420) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   180   175   021    Pre-fail  Always       -       5966
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       75
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4568
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       75
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       53
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       21
194 Temperature_Celsius     0x0022   108   101   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      4568         -


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


root@MediaMaster:/home/mark# smartctl -a /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.5.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EFRX-68AX9N0
Serial Number:    WD-WMC1T2561550
LU WWN Device Id: 5 0014ee 6588486a9
Firmware Version: 80.00A80
User Capacity:    3,000,591,900,160 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Sep 13 17:03:19 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (39840) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   185   180   021    Pre-fail  Always       -       5741
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       77
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4548
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       77
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       55
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       21
194 Temperature_Celsius     0x0022   110   105   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      4548         -


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

---

### Post by SaturnusDJ on 2013-09-13
Concerning the mdadm.conf, you can do uuid based assembly there too.

I admit mdadm can be difficult sometimes. But in the end it's up to the user to not make stupid mistakes. I've dealt with data loss and near data loss myself. The first time was by not using my head. The second time was more complicated. The lessons are: Always have a backup of the most important data and run S.M.A.R.T. (use smartmontools / smartctl) tests on regular base, and verify the outcome.

From my personal experience I can't tell you about other kind of setups. If you are a bit geeky and want to learn new things, you should stay with Linux. If you want to protect against yourself you should choose what you know best.

What I do know is that [Rubylaser]("http://ubuntuforums.org/member.php?u=1115132") suggests [SnapRAID]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04") over mdadm RAID for these kind of situations.

---

### Post by tgalati4 on 2013-09-14
I would go with JBOD for home video.  RAID can be too fussy for the home user and if one drive takes a dump, the amount of time it takes to rebuild can cause another drive to fail, which then results in the entire RAID taking a dump.  RAID is not a backup strategy, it provides improved data availablity for business users, but it requires some maintanence and a plan for failover when the RAID does take a dump.

---

### Post by mark56 on 2013-09-23
Thanks SaturnusDJ for all your help with this.  I appreciate the reference to Rubylaser's SnapRAID tutorial.  He has some great stuff on his site, and I put together a test box following his instructions, and finally rebuilt my server this weekend.   I have some questions about what I did (which I'll start a new thread on), but all the data is copying back over now, and with following some of his other tutorials, it seems I'll have proper monitoring, emailing, and even proper implementation of UPS setup.  

tgalati4, thanks for your response too, I seriously wanted to go back to JBOD, but I think Rubylasers SnapRAID & AUFS implementation is the best of both worlds.  (I hope... lol).

---

