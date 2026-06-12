---
title: "Failed RAID5 drive - replaced, can't assemble"
date: 2014-11-20
forum: Server Platforms
---

### Post by xubuntu84 on 2014-11-20
Hello,

I am having similar problems as [this post]("http://ubuntuforums.org/showthread.php?t=2249261&highlight=mdadm+failed+raid5"), but a couple of oddities, so I wanted to post here and ask the community before running --force.

I had a failed drive (/dev/sda) that I RMA'ed and have reinstalled in the machine.  My RAID5 is /dev/md0, with /dev/sd[abcd]1 as the members.  While the /dev/sda drive was out to Western Digital, I turned on my computer for regular use (/ is on /dev/sde).  During this time, smartctl said /dev/sdd had 18 errors.

I have done the following after reinstalling the hard drive:

```

root@xubuntu-server:~# mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: no recogniseable superblock on /dev/sda1
mdadm: /dev/sda1 has no superblock - assembly aborted

```

This is understandable (to me, I think) because /dev/sda1 is a freshly installed and partitioned hard drive.  I used gparted and marked it with the 'raid' flag.

So, I was going to start the array with /dev/sd[bcd]1, and then add /dev/sda1 once it was assembled:
```

mdadm --zero-superblock /dev/sda1
mdadm --assemble /dev/md0 /dev/sd[bcd]1
mdadm --add /dev/md0 /dev/sda1

```

However, I get
```

root@xubuntu-server:~# mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

```

My next step is to run
```

root@xubuntu-server:~# mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1


```
but that scares me.  

Thoughts?

=======

**smartctl info**

/dev/sda
```

root@xubuntu-server:~# smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-39-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF, SATA 6Gb/s)
Device Model:     WDC WD20EZRX-00D8PB0
Serial Number:    WD-WMC4M1647998
LU WWN Device Id: 5 0014ee 603fde0d3
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Wed Nov 19 19:57:31 2014 HST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (26940) seconds.
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
recommended polling time:      ( 272) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   253   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   100   253   021    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       3
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       2
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       3
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       2
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       8
194 Temperature_Celsius     0x0022   114   113   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         1         -


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

/dev/sdb
```

root@xubuntu-server:~# smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-39-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA0745783
LU WWN Device Id: 5 0014ee 655beb708
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed Nov 19 19:58:59 2014 HST
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
data collection:         (36660) seconds.
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
recommended polling time:      ( 354) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   168   166   021    Pre-fail  Always       -       6558
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1425
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   062   062   000    Old_age   Always       -       27742
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       298
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       241
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       690536
194 Temperature_Celsius     0x0022   114   105   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   197   197   000    Old_age   Always       -       1020
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   188   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     24198         -
# 2  Short offline       Completed without error       00%     10766         -


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

/dev/sdc
```

root@xubuntu-server:~# smartctl -a /dev/sdc
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-39-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA0447336
LU WWN Device Id: 5 0014ee 655be1287
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed Nov 19 19:59:53 2014 HST
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
data collection:         (37980) seconds.
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
recommended polling time:      ( 366) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   170   166   021    Pre-fail  Always       -       6483
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1382
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   062   062   000    Old_age   Always       -       27748
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       301
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       245
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       694735
194 Temperature_Celsius     0x0022   114   105   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     24203         -
# 2  Short offline       Completed without error       00%     10771         -


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

/dev/sdd
```

root@xubuntu-server:~# smartctl -a /dev/sdd
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-39-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA0654948
LU WWN Device Id: 5 0014ee 600698011
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed Nov 19 20:00:37 2014 HST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 113)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (37200) seconds.
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
recommended polling time:      ( 359) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   198   198   051    Pre-fail  Always       -       3905
  3 Spin_Up_Time            0x0027   170   167   021    Pre-fail  Always       -       6466
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1379
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   062   062   000    Old_age   Always       -       27743
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       297
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       243
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       702707
194 Temperature_Celsius     0x0022   117   105   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   196   196   000    Old_age   Always       -       1344
198 Offline_Uncorrectable   0x0030   200   199   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   194   161   000    Old_age   Offline      -       1605


SMART Error Log Version: 1
ATA Error Count: 18 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.


Error 18 occurred at disk power-on lifetime: 27741 hours (1155 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 0c 00 00 00 00  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 0c 00 00 00 00 00  41d+16:30:46.649  SET FEATURES [Set transfer mode]
  b0 da 00 00 4f c2 e0 00  41d+16:30:46.562  SMART RETURN STATUS
  ec d8 00 00 00 00 e0 00  41d+16:30:46.558  IDENTIFY DEVICE
  b0 d8 00 00 4f c2 e0 00  41d+16:30:46.083  SMART ENABLE OPERATIONS
  ec 00 00 00 00 00 e0 00  41d+16:30:46.078  IDENTIFY DEVICE


Error 17 occurred at disk power-on lifetime: 27741 hours (1155 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 0c 00 00 00 00  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 0c 00 00 00 00 00  41d+16:29:54.861  SET FEATURES [Set transfer mode]
  b0 da 00 00 4f c2 e0 00  41d+16:29:54.774  SMART RETURN STATUS
  ec d8 00 00 00 00 e0 00  41d+16:29:54.770  IDENTIFY DEVICE
  b0 d8 00 00 4f c2 e0 00  41d+16:29:54.666  SMART ENABLE OPERATIONS
  ec 00 00 00 00 00 e0 00  41d+16:29:54.662  IDENTIFY DEVICE


Error 16 occurred at disk power-on lifetime: 27740 hours (1155 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 a0 08  41d+15:53:10.401  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  41d+15:53:10.392  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  41d+15:53:04.933  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08  41d+15:53:04.926  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  41d+15:53:04.917  IDENTIFY DEVICE


Error 15 occurred at disk power-on lifetime: 27740 hours (1155 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 a0 08  41d+15:53:04.926  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  41d+15:53:04.917  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  41d+15:52:59.462  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08  41d+15:52:59.455  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  41d+15:52:59.446  IDENTIFY DEVICE


Error 14 occurred at disk power-on lifetime: 27740 hours (1155 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 a0 08  41d+15:52:59.455  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  41d+15:52:59.446  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  41d+15:52:58.963  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  41d+15:52:58.956  SET FEATURES [Set transfer mode]


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       10%     27742         3731903968
# 2  Short offline       Completed without error       00%     24199         -
# 3  Short offline       Completed without error       00%     10768         -


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

So, sdd does look to have some errors, but it still says PASSED, so I'm hoping it's still usable.

==========
[B]mdadm info


[/B]```
root@xubuntu-server:~# mdadm -E /dev/sda1
mdadm: No md superblock detected on /dev/sda1.

```

```

root@xubuntu-server:~# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 9e7ab348:9594fe28:0308d362:1f0077d8
  Creation Time : Tue Nov 30 12:45:38 2010
     Raid Level : raid5
  Used Dev Size : 1953510912 (1863.01 GiB 2000.40 GB)
     Array Size : 5860532736 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0


    Update Time : Fri Nov  7 18:56:38 2014
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 15092ca2 - correct
         Events : 17480


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1


   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       49        4      faulty   /dev/sdd1

```


```

root@xubuntu-server:~# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 9e7ab348:9594fe28:0308d362:1f0077d8
  Creation Time : Tue Nov 30 12:45:38 2010
     Raid Level : raid5
  Used Dev Size : 1953510912 (1863.01 GiB 2000.40 GB)
     Array Size : 5860532736 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0


    Update Time : Fri Nov  7 18:56:38 2014
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 15092cb4 - correct
         Events : 17480


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1


   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       49        4      faulty   /dev/sdd1

```

```

root@xubuntu-server:~# mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 9e7ab348:9594fe28:0308d362:1f0077d8
  Creation Time : Tue Nov 30 12:45:38 2010
     Raid Level : raid5
  Used Dev Size : 1953510912 (1863.01 GiB 2000.40 GB)
     Array Size : 5860532736 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0


    Update Time : Fri Nov  7 18:19:49 2014
          State : active
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 1508dfc3 - correct
         Events : 17466


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1


   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8        0        4      spare   /dev/sda

```

```

root@xubuntu-server:~# mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/sdb1 is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping
root@xubuntu-server:~# mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

```

```

root@xubuntu-server:~# mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
root@xubuntu-server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[0](S) sdd1[3](S) sdc1[1](S)
      5860534784 blocks
       
unused devices: <none>

```


=========

If you need more info, I would be glad to post.

Thanks!

---

### Post by rubylaser on 2014-11-20
sdd and sdb both don't look very healthly (sdd is worse).  Since the event counter on sdd does not match the other two array members, you are going to have to force assemble at this point.  I hope you have a backup of your important data, because even if you can re-assemble the array, I'm not feeling too optimistic that your re-sync will finish successfully before sdd takes a dump :(

---

### Post by xubuntu84 on 2014-11-20
rubylaser,

Thanks for your response; I too am worried sdd will not survive a the assembly, but I really have no other choice at this point.  As soon as this catastrophe is over, I'm considering RAID6.  And no, this array was too large to backup onto anything else I have, and too expensive to back up to the cloud.

Would you suggest running 
```

mdadm --assemble --force /dev/md0 /dev/sd[abcd]1

or

mdadm --assemble --force /dev/md0 /dev/sd[bcd]1
then
mdadm --add /dev/md0 /dev/sda1

```

---

### Post by xubuntu84 on 2014-11-20
Disregard my last post, I have to force assemble using sdb, sdc, and sdd first, and then add sda since it has no superblock.

---

### Post by xubuntu84 on 2014-11-20
The --force was successful, and the array is now rebuilding.

Should the data not be available to the operating system once md0 is available, do I have recovery options before replacing sdd?  For example, within gparted there is an option for "Attempt data rescue".  Has anyone had success with this?  If not, what are options do I have?  I hate to just call it a complete loss, when I know all the 1's and 0's are still there, albeit not completely intact.

---

### Post by tgalati4 on 2014-11-21
Your experience is precisely the reason for RAID6 and above.  As disks have gotten large, and disks of similar age tend to fail in a similar fashion and at the same time, the rebuilding time is long and another failure during that rebuild can cause a total data loss.

Unless you are prepared to spend some money to provide a backup plan for your data (since RAID is not a backup strategy), your current efforts are about the only thing you can do.  You could send your array out to a data-recovery service and they might have some tools to recover the data, but I don't know of a simple and efficient way beyond *testdisk*.  That will only recover small files (like thumbnails, configuration files, and similar).  This can be useful to remind yourself of what was on the disk, but won't help you recover larger files that were striped across a bad drive.

A google search brings up lots of services:

[http://www.datarecovery.net/raid/raid-5-data-recovery.html](http://www.datarecovery.net/raid/raid-5-data-recovery.html)

[http://www.freeraidrecovery.com/library/what-is-raid.aspx](http://www.freeraidrecovery.com/library/what-is-raid.aspx)

Just hope that your resync is successful.  Loss of that second drive is loss of the entire pool.

---

### Post by xubuntu84 on 2014-11-21
Thank you for your response.  It appears it may be a total loss:

```

root@xubuntu-server:~# mdadm -D /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Tue Nov 30 12:45:38 2010
     Raid Level : raid5
     Array Size : 5860532736 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953510912 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Nov 20 21:53:31 2014
          State : clean, FAILED 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 9e7ab348:9594fe28:0308d362:1f0077d8
         Events : 0.17656

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed
       3       0        0        3      removed

       4       8        1        -      spare   /dev/sda1
       5       8       49        -      faulty spare   /dev/sdd1

```

This was after resync.  My new sdd should be coming in the mail shortly.  I've been looking into RAID6, and it is looking more and more like the way to go.  Unfortunately I will have to get a SATA card since my mobo ports are all full.  It's really strange that 2 drives failed at the exact same time; makes me curious if there was a power issue that my UPS did not take care of.

Anyways, thanks all for your help.

Ben

---

