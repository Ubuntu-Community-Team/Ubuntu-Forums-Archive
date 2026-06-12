---
title: "mdadm raid6 loop?"
date: 2014-09-17
forum: Server Platforms
---

### Post by scatman2 on 2014-09-17
I have a raid 6 with 6 hd (hda->hdf).
Last week i noticed one disk failed (hdd).
I added the disk again to the raid using:
mdadm /dev/md0 -a /dev/sdd

The disk was added without a problem, but during the syncing another disk (sdf) failed and got thrown out.
So i added that one again too:
mdadm /dev/md0 -a /dev/sdf

Again, the disk was added without a problem.
During the syncing of sdf, sdd got thrown out again so i added that one again too
mdadm /dev/md0 -a /dev/sdd

But once more, during that sync, sdf got thrown out again and i added that one again.
And once more sdd got thrown out again.

So basicly:
1. during syncing sdd, sdf gets thrown out every time
2. i readd sdf
3. during syncing sdf, sdd gets thrown out every time
4. i readd sdd
5. #1 once more
6. ...

---

### Post by lukeiamyourfather on 2014-09-18
Are you adding the same drives back to the array or are these different drives? What do you mean when you say "got thrown out" and are there any errors when this happens? Does dmesg say anything about the drives?

---

### Post by scatman2 on 2014-09-19
> **lukeiamyourfather said:**
> Are you adding the same drives back to the array or are these different drives? What do you mean when you say "got thrown out" and are there any errors when this happens? Does dmesg say anything about the drives?

I'm adding the same drives again.
thrown out = Mdadm labels them als faulty

Herby my smart data after doing:
sudo smartctl -t short /dev/sdX
```
******@LubuntuNas:~$ sudo smartctl -a /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD30EZRX-00DC0B0
Serial Number:    WD-WMC1T0722658
LU WWN Device Id: 5 0014ee 003703b66
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ACS-2 (revision not indicated)
Local Time is:    Fri Sep 19 07:44:35 2014 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (39600) seconds.
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
recommended polling time:        ( 398) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70b5) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   182   175   021    Pre-fail  Always       -       5883
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       155
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       13551
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       149
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       62
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       803
194 Temperature_Celsius     0x0022   112   102   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
SMART Error Log Version: 1
No Errors Logged
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     13551         -
# 2  Short offline       Completed without error       00%     13551         -
# 3  Short offline       Aborted by host               80%        45         -
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
```
******@LubuntuNas:~$ sudo smartctl -a /dev/sdb
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD30EZRX-00DC0B0
Serial Number:    WD-WMC1T0722468
LU WWN Device Id: 5 0014ee 0037043bc
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ACS-2 (revision not indicated)
Local Time is:    Fri Sep 19 07:44:44 2014 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (40980) seconds.
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
recommended polling time:        ( 411) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70b5) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   181   177   021    Pre-fail  Always       -       5933
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       155
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       13551
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       149
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       62
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       797
194 Temperature_Celsius     0x0022   111   098   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
SMART Error Log Version: 1
No Errors Logged
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     13551         -
# 2  Short offline       Completed without error       00%       126         -
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
```

******@LubuntuNas:~$ sudo smartctl -a /dev/sdc
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD30EZRX-00DC0B0
Serial Number:    WD-WMC1T0713138
LU WWN Device Id: 5 0014ee 003704373
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ACS-2 (revision not indicated)
Local Time is:    Fri Sep 19 07:44:46 2014 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (40860) seconds.
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
recommended polling time:        ( 410) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70b5) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   183   178   021    Pre-fail  Always       -       5816
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       155
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       13551
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       149
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       62
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       820
194 Temperature_Celsius     0x0022   110   097   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
SMART Error Log Version: 1
No Errors Logged
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     13551         -
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
```
*****@LubuntuNas:~$ sudo smartctl -a /dev/sdd
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD30EZRX-00DC0B0
Serial Number:    WD-WMC1T0801510
LU WWN Device Id: 5 0014ee 058c58d56
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ACS-2 (revision not indicated)
Local Time is:    Fri Sep 19 08:53:07 2014 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (  40) The self-test routine was interrupted
                                        by the host with a hard or soft reset.
Total time to complete Offline
data collection:                (41160) seconds.
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
recommended polling time:        ( 413) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70b5) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   197   178   021    Pre-fail  Always       -       5108
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       156
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       11166
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       149
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       62
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       807
194 Temperature_Celsius     0x0022   110   097   000    Old_age   Always       -       40
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   193   000    Old_age   Always       -       679645
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
SMART Error Log Version: 1
No Errors Logged
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Interrupted (host reset)      80%     11165         -
# 2  Short offline       Completed without error       00%     11164         -
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
```
******@LubuntuNas:~$ sudo smartctl -a /dev/sde
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
Vendor:               /2:0:0:0
Product:
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```
```
******@LubuntuNas:~$ sudo smartctl -a /dev/sdf
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-47-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD30EZRX-00DC0B0
Serial Number:    WD-WMC1T0802339
LU WWN Device Id: 5 0014ee 00370497c
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ACS-2 (revision not indicated)
Local Time is:    Fri Sep 19 07:44:50 2014 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (40020) seconds.
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
recommended polling time:        ( 401) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x70b5) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   179   175   021    Pre-fail  Always       -       6016
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       155
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       13551
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       149
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       62
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       916
194 Temperature_Celsius     0x0022   109   096   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
SMART Error Log Version: 1
No Errors Logged
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     13551         -
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

### Post by lukeiamyourfather on 2014-09-19
It sounds like the issue is not necessarily bad drives. Could be a bad controller, cables, or power supply. When one of the drives drops check dmesg and see what it says. This is an explanation of what the error messages mean.

[https://ata.wiki.kernel.org/index.php/Libata_error_messages](https://ata.wiki.kernel.org/index.php/Libata_error_messages)

---

### Post by rubylaser on 2014-09-19
/dev/sdd has the highest UDMA_CRC_ERROR_COUNT that I have ever seen.  That indicates either a bad SATA cable, SATA head, or there's something wrong with the disk (it's almost always the cable, so replace that first). This could certainly cause it to be labeled faulty.  /dev/sde isn't even beginning to report SMART data, so it appears there is something wrong with that disk.  Also, it's a good idea to keep track of the serial number of the disk that's causing the issue, because the system disk ordering can change (/dev/sd[a-f]), etc.).

---

