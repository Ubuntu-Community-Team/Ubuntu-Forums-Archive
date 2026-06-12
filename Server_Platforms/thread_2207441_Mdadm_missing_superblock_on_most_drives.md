---
title: "Mdadm missing superblock on most drives"
date: 2014-02-23
forum: Server Platforms
---

### Post by mihairosu on 2014-02-23
Here is my situation:

I used to have a Raid6 array /dev/md2 with the following disks:

sda, sdb, sdc, sde, sdf, sdg, sdh, sdi. (8 in total)

After rebooting today, the array could not rebuild.

```

mihai@ubuntu-nas:~$ sudo mdadm --assemble --scan
mdadm: /dev/md2 assembled from 3 drives - not enough to start the array.

```

Examining the disks, I am getting the following information:

```

mihai@ubuntu-nas:~$ sudo mdadm -E /dev/sd[abcefghi]
/dev/sda:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 3c0308c1:e12f9601:1ef18089:cefb5d8e (local to host ubuntu-nas)
  Creation Time : Sun Jan 17 12:25:12 2010
     Raid Level : raid6
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
     Array Size : 4395446784 (4191.82 GiB 4500.94 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 2


    Update Time : Sun Feb 23 12:29:00 2014
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7e6ea067 - correct
         Events : 902436


         Layout : left-symmetric
     Chunk Size : 32K


      Number   Major   Minor   RaidDevice State
this     4       8        0        4      active sync   /dev/sda


   0     0       8       80        0      active sync   /dev/sdf
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       64        3      active sync   /dev/sde
   4     4       8        0        4      active sync   /dev/sda
   5     5       8      112        5      active sync   /dev/sdh
   6     6       8      128        6      active sync   /dev/sdi
   7     7       8       96        7      active sync   /dev/sdg
mdadm: No md superblock detected on /dev/sdb.
mdadm: No md superblock detected on /dev/sdc.
mdadm: No md superblock detected on /dev/sde.
mdadm: No md superblock detected on /dev/sdf.
mdadm: No md superblock detected on /dev/sdg.
/dev/sdh:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 3c0308c1:e12f9601:1ef18089:cefb5d8e (local to host ubuntu-nas)
  Creation Time : Sun Jan 17 12:25:12 2010
     Raid Level : raid6
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
     Array Size : 4395446784 (4191.82 GiB 4500.94 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 2


    Update Time : Sun Feb 23 12:29:00 2014
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7e6ea0d9 - correct
         Events : 902436


         Layout : left-symmetric
     Chunk Size : 32K


      Number   Major   Minor   RaidDevice State
this     5       8      112        5      active sync   /dev/sdh


   0     0       8       80        0      active sync   /dev/sdf
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       64        3      active sync   /dev/sde
   4     4       8        0        4      active sync   /dev/sda
   5     5       8      112        5      active sync   /dev/sdh
   6     6       8      128        6      active sync   /dev/sdi
   7     7       8       96        7      active sync   /dev/sdg
/dev/sdi:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 3c0308c1:e12f9601:1ef18089:cefb5d8e (local to host ubuntu-nas)
  Creation Time : Sun Jan 17 12:25:12 2010
     Raid Level : raid6
  Used Dev Size : 732574464 (698.64 GiB 750.16 GB)
     Array Size : 4395446784 (4191.82 GiB 4500.94 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 2


    Update Time : Sun Feb 23 12:29:00 2014
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7e6ea0eb - correct
         Events : 902436


         Layout : left-symmetric
     Chunk Size : 32K


      Number   Major   Minor   RaidDevice State
this     6       8      128        6      active sync   /dev/sdi


   0     0       8       80        0      active sync   /dev/sdf
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       64        3      active sync   /dev/sde
   4     4       8        0        4      active sync   /dev/sda
   5     5       8      112        5      active sync   /dev/sdh
   6     6       8      128        6      active sync   /dev/sdi
   7     7       8       96        7      active sync   /dev/sdg

```

Meaning I have superblocks on only 3 of the 8 disks.  

Here is the SMART status of all the drives:

sda
```

mihai@ubuntu-nas:~$ sudo smartctl -d ata -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-55-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE2-GP
Device Model:     WDC WD7500AYPS-01ZKB0
Serial Number:    WD-WCASM0040580
LU WWN Device Id: 5 0014ee 20114876c
Firmware Version: 02.01B01
User Capacity:    750,156,374,016 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 23 14:21:47 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (  24) The self-test routine was aborted by
                                        the host.
Total time to complete Offline
data collection:                (20400) seconds.
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
recommended polling time:        ( 235) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   199   181   021    Pre-fail  Always       -       5025
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       378
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       35349
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       135
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       89
193 Load_Cycle_Count        0x0032   122   122   000    Old_age   Always       -       234292
194 Temperature_Celsius     0x0022   119   101   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
ATA Error Count: 1
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


Error 1 occurred at disk power-on lifetime: 2343 hours (97 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 cf 00 07 00 e0  Error: UNC at LBA = 0x00000700 = 1792


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 30 00 02 00 00 08      00:00:57.131  READ FPDMA QUEUED
  60 00 28 00 03 00 00 08      00:00:57.131  READ FPDMA QUEUED
  60 00 20 00 04 00 00 08      00:00:57.130  READ FPDMA QUEUED
  60 60 18 00 05 00 00 08      00:00:57.130  READ FPDMA QUEUED
  60 a0 10 60 05 00 00 08      00:00:57.130  READ FPDMA QUEUED


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               80%     35349         -


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

sdb
```

mihai@ubuntu-nas:~$ sudo smartctl -d ata -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-55-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE2-GP
Device Model:     WDC WD7500AYPS-01ZKB0
Serial Number:    WD-WCASM0046753
LU WWN Device Id: 5 0014ee 201141038
Firmware Version: 02.01B01
User Capacity:    750,155,292,160 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 23 14:23:39 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (21000) seconds.
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
recommended polling time:        ( 241) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   188   183   021    Pre-fail  Always       -       5583
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       376
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       35365
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       134
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       95
193 Load_Cycle_Count        0x0032   122   122   000    Old_age   Always       -       234161
194 Temperature_Celsius     0x0022   122   108   000    Old_age   Always       -       28
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
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

```

sdc
```

mihai@ubuntu-nas:~$ sudo smartctl -d ata -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-55-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE2-GP
Device Model:     WDC WD7500AYPS-01ZKB0
Serial Number:    WD-WCASM0039870
LU WWN Device Id: 5 0014ee 201144974
Firmware Version: 02.01B01
User Capacity:    750,155,292,160 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 23 14:27:09 2014 CST
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
data collection:                (20400) seconds.
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
recommended polling time:        ( 235) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   190   186   021    Pre-fail  Always       -       5458
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       380
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       35380
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       136
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       95
193 Load_Cycle_Count        0x0032   122   122   000    Old_age   Always       -       234402
194 Temperature_Celsius     0x0022   124   109   000    Old_age   Always       -       26
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
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

```

sde
```

mihai@ubuntu-nas:~$ sudo smartctl -d ata -a /dev/sde
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-55-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE2-GP
Device Model:     WDC WD7500AYPS-01ZKB0
Serial Number:    WD-WCASM0038252
LU WWN Device Id: 5 0014ee 25669c774
Firmware Version: 02.01B01
User Capacity:    750,155,292,160 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 23 14:27:43 2014 CST
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
data collection:                (20400) seconds.
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
recommended polling time:        ( 235) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   189   182   021    Pre-fail  Always       -       5533
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       386
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       35372
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       132
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       99
193 Load_Cycle_Count        0x0032   123   123   000    Old_age   Always       -       233907
194 Temperature_Celsius     0x0022   126   101   000    Old_age   Always       -       24
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     23217         -


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

sdf
```

mihai@ubuntu-nas:~$ sudo smartctl -d ata -a /dev/sdf
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-55-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE2-GP
Device Model:     WDC WD7500AYPS-01ZKB0
Serial Number:    WD-WCASM0040904
LU WWN Device Id: 5 0014ee 201149314
Firmware Version: 02.01B01
User Capacity:    750,155,292,160 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 23 14:28:08 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (21000) seconds.
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
recommended polling time:        ( 241) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   190   186   021    Pre-fail  Always       -       5491
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       383
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       35380
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       135
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       97
193 Load_Cycle_Count        0x0032   123   123   000    Old_age   Always       -       233913
194 Temperature_Celsius     0x0022   122   104   000    Old_age   Always       -       28
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         6         -
# 2  Short offline       Aborted by host               90%         6         -


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

sdg
```

mihai@ubuntu-nas:~$ sudo smartctl -d ata -a /dev/sdg
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-55-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE2-GP
Device Model:     WDC WD7500AYPS-01ZKB0
Serial Number:    WD-WCASM0037366
LU WWN Device Id: 5 0014ee 256681ad3
Firmware Version: 02.01B01
User Capacity:    750,155,292,160 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 23 14:28:31 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (21000) seconds.
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
recommended polling time:        ( 241) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   188   181   021    Pre-fail  Always       -       5566
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       389
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       35361
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       135
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       96
193 Load_Cycle_Count        0x0032   123   123   000    Old_age   Always       -       233606
194 Temperature_Celsius     0x0022   125   102   000    Old_age   Always       -       25
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
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

```

sdh
```

mihai@ubuntu-nas:~$ sudo smartctl -d ata -a /dev/sdh
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-55-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE2-GP
Device Model:     WDC WD7500AYPS-01ZKB1
Serial Number:    WD-WCASM0061412
LU WWN Device Id: 5 0014ee 20230200d
Firmware Version: 02.01B02
User Capacity:    750,156,374,016 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 23 14:28:53 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (21000) seconds.
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
recommended polling time:        ( 241) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   184   179   021    Pre-fail  Always       -       5783
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       300
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       35294
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       93
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       52
193 Load_Cycle_Count        0x0032   115   115   000    Old_age   Always       -       255578
194 Temperature_Celsius     0x0022   120   100   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
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

```

sdi
```
mihai@ubuntu-nas:~$ sudo smartctl -d ata -a /dev/sdi
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-55-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE2-GP
Device Model:     WDC WD7500AYPS-01ZKB0
Serial Number:    WD-WCASM0039861
LU WWN Device Id: 5 0014ee 201144910
Firmware Version: 02.01B01
User Capacity:    750,156,374,016 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 23 14:29:11 2014 CST
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
data collection:                (20400) seconds.
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
recommended polling time:        ( 235) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   189   183   021    Pre-fail  Always       -       5516
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       383
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   052   052   000    Old_age   Always       -       35341
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       135
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       125
193 Load_Cycle_Count        0x0032   123   123   000    Old_age   Always       -       233989
194 Temperature_Celsius     0x0022   126   100   000    Old_age   Always       -       24
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
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

```

All drives pass the SMART test from what I can see.

Can this RAID be rebuilt?

---

### Post by greyday on 2014-02-23
How are your drives connected?  If via eSATA, try swapping out the cables.  I had two drives constantly dropping out of RAIDs a while back and swapping out the eSATA cable on the port multiplier did the trick...

---

### Post by mihairosu on 2014-02-23
None are eSATA.

Most are connected to the [mobo SATA]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128359") ports and 1 or two of them are connected to this [PCIE 2 port SATA adapter]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815280009").

But I can connect to them just fine, and they're been working okay since I bought them in Nov 2009 without problems, except those that I caused, ha ha.  So this is not a recurring problem.

---

### Post by greyday on 2014-02-24
Hmm.  Probably not a mechanical problem then, but I'd still test your data cables.  What are your read speeds?  Install smartmontools (if you haven't already, just an apt-get install) and run ```
[COLOR=#000000][FONT=Lucida Grande]hdparm -Tt /dev/sda[/FONT][/COLOR]
```where a is your specific drive (sudo su in first); this will tell you the speed and you can make sure all the internal cables and connections are working ok.  If there are some drives with slower speeds than the rest, swap out those cables and see if that sorts it.

Sorry to be stuck on the physical, but I've found that 90% of my RAID problems like these in the past have been cable or PCI/PCIe card related (or, if you added anything new to the server, like an upgraded processor or a new GPU, making sure the PSU is rated high enough).  There is a decent amount that can go wrong physically, so any change (or even just parts wearing out, as they do) should be dismissed before starting to mess with the RAID drives themselves...

On the software level there are some things you can try, but do you have a backup of the important data?  If you're careful, you won't lose anything, but anything can happen (I've lost entire volumes doing "non-destructive" things).

Are you doing auto assemblies or direct ones?  What file format is the volume? LVM or standard? Have you made ANY changes between when the array worked and when it didn't, no matter how small (changes to fstab ot mdadm.conf, distro upgrade, moved the server itself, a powerout--anything out of the ordinary)?

---

### Post by mihairosu on 2014-02-24
```

hdparm -Tt /dev/sd[abcefghi] 

/dev/sda:
 Timing cached reads:   2598 MB in  2.00 seconds = 1299.73 MB/sec
 Timing buffered disk reads: 220 MB in  3.02 seconds =  72.76 MB/sec
mihai@ubuntu-nas:~$ sudo hdparm -Tt /dev/sd[abcefghi]


/dev/sda:
 Timing cached reads:   2602 MB in  2.00 seconds = 1301.30 MB/sec
 Timing buffered disk reads: 222 MB in  3.00 seconds =  73.95 MB/sec


/dev/sdb:
 Timing cached reads:   2570 MB in  2.00 seconds = 1285.15 MB/sec
 Timing buffered disk reads: 222 MB in  3.01 seconds =  73.75 MB/sec


/dev/sdc:
 Timing cached reads:   2582 MB in  2.00 seconds = 1291.08 MB/sec
 Timing buffered disk reads: 226 MB in  3.01 seconds =  75.06 MB/sec


/dev/sde:
 Timing cached reads:   2552 MB in  2.00 seconds = 1276.71 MB/sec
 Timing buffered disk reads: 228 MB in  3.02 seconds =  75.38 MB/sec


/dev/sdf:
 Timing cached reads:   2554 MB in  2.00 seconds = 1277.28 MB/sec
 Timing buffered disk reads: 226 MB in  3.00 seconds =  75.21 MB/sec


/dev/sdg:
 Timing cached reads:   2522 MB in  2.00 seconds = 1261.63 MB/sec
 Timing buffered disk reads: 218 MB in  3.01 seconds =  72.44 MB/sec


/dev/sdh:
 Timing cached reads:   2586 MB in  2.00 seconds = 1293.46 MB/sec
 Timing buffered disk reads: 216 MB in  3.02 seconds =  71.53 MB/sec


/dev/sdi:
 Timing cached reads:   2580 MB in  2.00 seconds = 1290.54 MB/sec
 Timing buffered disk reads: 232 MB in  3.01 seconds =  77.03 MB/sec

```


> 
Are you doing auto assemblies or direct ones?


I'm not fully sure what you mean by this question, but normally the array is mounted at boot via fstab.

```

/dev/md2        /media/HomeNAS  xfs defaults,noatime 0  0

```

> 
What file format is the volume? LVM or standard? 


Standard XFS volume.  I don't have any LVM set up.

> 
Have you made ANY changes between when the array worked and when it didn't, no matter how small (changes to fstab ot mdadm.conf, distro upgrade, moved the server itself, a powerout--anything out of the ordinary)?


Something I do every month.  Rebooting the server to boot Clonezilla from a CD.  I was cloning the SSD on which the OS was installed onto a separate external HD.

After this problem, I even imaged a backup from a month ago to see if it would fix it, but it did not.

Since my first post I haven't done anything on the software level to any of the raid drives.  

I do weekly backups of some the more important data from the RAID onto the same external HD mentioned earlier, via cron jobs.

---

### Post by mihairosu on 2014-02-27
I have read elsewhere, that I may be able to just create the raid array anew, and it might possibly save the data.

```

/mdadm --create /dev/md2 /dev/sda /dev/sdb /dev/sdc /dev/sde /dev/sdf /dev/sdg /dev/sdh /dev/sdi

```

Any thoughts on trying this? Will this preserve the xfs filesystem and raid type?

 I haven't done anything yet because I want to make sure that I don't destroy the data, unless there is no other choice.

---

