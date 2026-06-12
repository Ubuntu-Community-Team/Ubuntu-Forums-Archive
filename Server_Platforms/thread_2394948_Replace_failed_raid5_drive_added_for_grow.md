---
title: "Replace failed raid5 drive added for grow"
date: 2018-06-24
forum: Server Platforms
---

### Post by Rookie11 on 2018-06-24
Hi,

I have intended to grow my raid5 array of 5 4TB WD RED Drives, so i plugged in a 6th partitioned it added it to the raid and let mdadm do it's reshape.
After the reshape was done it now shows me that new drive as faulty and the 6th device as removed.

Can I now just proceed with replacing the new one waiting for mdadm and then continue with adjusting the file system size etc.?

Here is the output from mdadm and smartctl if that helps.

```
 sudo mdadm -D /dev/md0/dev/md0:
        Version : 1.2
  Creation Time : Thu Jan  7 08:23:57 2016
     Raid Level : raid5
     Array Size : 19534428160 (18629.48 GiB 20003.25 GB)
  Used Dev Size : 3906885632 (3725.90 GiB 4000.65 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sat Jun 23 23:02:07 2018
          State : clean, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : NAS:0  (local to host NAS)
           UUID : 69ba4b0e:a2427b2a:121cc4e0:5461a8fb
         Events : 252895


    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       65        1      active sync   /dev/sde1
       3       8       81        2      active sync   /dev/sdf1
       4       8       17        3      active sync   /dev/sdb1
       5       8       49        4      active sync   /dev/sdd1
       -       0        0        5      removed


       6       8       97        -      faulty   /dev/sdg1



```

/proc/mdstat
```
cat /proc/mdstatPersonalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid5 sdg1[6](F) sdd1[5] sdf1[3] sdc1[0] sde1[1] sdb1[4]
      19534428160 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/5] [UUUUU_]
      bitmap: 0/30 pages [0KB], 65536KB chunk


unused devices: <none>



```

smartctl on /dev/sdg
```
sudo smartctl --all -T permissive /dev/sdgsmartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-22-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


Short INQUIRY response, skip product id


=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK
Current Drive Temperature:     0 C
Drive Trip Temperature:        0 C


Read defect list: asked for grown list but didn't get it
Error Counter logging not supported


Device does not support Self Test logging



```

Thanks in advance.

---

### Post by Rookie11 on 2018-06-25
So after restarting and plugging in another hdd mdadm just showed the 6th device as removed.

I added the new one as a space and it started recovering. Strange thing now smartctl give me more details for the previously failed device.

Looking like this
```
 sudo smartctl --all /dev/sdgsmartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-22-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Red
Device Model:     WDC WD40EFRX-68N32N0
Serial Number:    WD-WCC7K4EYPC3D
LU WWN Device Id: 5 0014ee 20fbaedc9
Firmware Version: 82.00A82
User Capacity:    4.000.787.030.016 bytes [4,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Jun 25 20:47:17 2018 CEST
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
data collection:                (45360) seconds.
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
recommended polling time:        ( 482) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   253   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   100   253   021    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       2
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       49
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       4
194 Temperature_Celsius     0x0022   119   117   000    Old_age   Always       -       31
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

current mdadm info:
```
sudo mdadm -D /dev/md0/dev/md0:
        Version : 1.2
  Creation Time : Thu Jan  7 08:23:57 2016
     Raid Level : raid5
     Array Size : 19534428160 (18629.48 GiB 20003.25 GB)
  Used Dev Size : 3906885632 (3725.90 GiB 4000.65 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Mon Jun 25 20:48:29 2018
          State : clean, degraded, recovering
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1


         Layout : left-symmetric
     Chunk Size : 512K


 Rebuild Status : 12% complete


           Name : NAS:0  (local to host NAS)
           UUID : 69ba4b0e:a2427b2a:121cc4e0:5461a8fb
         Events : 253523


    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       65        1      active sync   /dev/sde1
       3       8       81        2      active sync   /dev/sdf1
       4       8       17        3      active sync   /dev/sdb1
       5       8       49        4      active sync   /dev/sdd1
       6       8      113        5      spare rebuilding   /dev/sdh1



```

and /proc/mdstat
```
cat /proc/mdstatPersonalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid5 sdh1[6] sdd1[5] sdf1[3] sdc1[0] sde1[1] sdb1[4]
      19534428160 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/5] [UUUUU_]
      [==>..................]  recovery = 12.6% (494242968/3906885632) finish=391.3min speed=145350K/sec
      bitmap: 0/30 pages [0KB], 65536KB chunk


unused devices: <none>



```

So seeing that the previously failed device seems to work fine now, is there any problem adding that as a spare?

---

