---
title: "RAID5 array crashed"
date: 2012-09-09
forum: Server Platforms
---

### Post by Chupa47 on 2012-09-09
Hey,

I'm new to the hole Linux and RAID 5 stuff. But if been working on getting my own Raid 5 server on and i was pretty proud for getting it to work and it worked very good until this morning i could not copy any files to my server anymore. I logged in on my server and there was a error of Linux itself. I restarted the pc and could not get my RAID 5 back on.

if been calling around for people to help me, but so far nobody could help me out. I went on the Internet and found this post : [http://ubuntuforums.org/showthread.php?t=2053664&highlight=mdadm](http://ubuntuforums.org/showthread.php?t=2053664&highlight=mdadm)

and it looks pretty much like my problem but i'm just not sure. And a friend said that the hole "--force" is pretty dangerous.

So i rather want to ask first instead of trying to solve it myself and lose all my data.

[B]cat /etc/mdadm/mdadm.conf
[/B]
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers
#ARRAY /dev/md0 metadata=1.2 name=Chupa-MediaServer UUID=941a8a10:e1427786:3ef667dd:a86f82e4
DEVICE partitions
ARRAY /dev/md127 level=raid5 num-devices=4 metadata=1.2 name=Chupa-MediaServer UUID=941a8a10:e1427786:3ef667dd:a86f82e4
 


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Fri, 13 Jul 2012 20:36:06 +0200
# by mkconf $Id$

```[B]mdadm -E /dev/sd[bcde]1
[/B]```
root@Chupa-MediaServer:~# mdadm -E /dev/sd[bcde]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 941a8a10:e1427786:3ef667dd:a86f82e4
           Name : Chupa-MediaServer
  Creation Time : Fri Jul 13 21:14:42 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5860531053 (2794.52 GiB 3000.59 GB)
     Array Size : 8790795264 (8383.56 GiB 9001.77 GB)
  Used Dev Size : 5860530176 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 84ff1c93:5e495dce:4c642da1:14585ef5

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Sep  8 22:27:35 2012
       Checksum : e2e5438c - correct
         Events : 22489

         Layout : left-symmetric
     Chunk Size : 1024K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 941a8a10:e1427786:3ef667dd:a86f82e4
           Name : Chupa-MediaServer
  Creation Time : Fri Jul 13 21:14:42 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5860531053 (2794.52 GiB 3000.59 GB)
     Array Size : 8790795264 (8383.56 GiB 9001.77 GB)
  Used Dev Size : 5860530176 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e00bc153:c52409f2:01db29ad:64068782

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Sep  9 12:15:41 2012
       Checksum : 605d129e - correct
         Events : 22550

         Layout : left-symmetric
     Chunk Size : 1024K

   Device Role : Active device 2
   Array State : .AA. ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 941a8a10:e1427786:3ef667dd:a86f82e4
           Name : Chupa-MediaServer
  Creation Time : Fri Jul 13 21:14:42 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5860531053 (2794.52 GiB 3000.59 GB)
     Array Size : 8790795264 (8383.56 GiB 9001.77 GB)
  Used Dev Size : 5860530176 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 661db6df:e3c5b256:d3238511:92da86e6

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Sep  9 12:15:41 2012
       Checksum : 1956e241 - correct
         Events : 22550

         Layout : left-symmetric
     Chunk Size : 1024K

   Device Role : Active device 1
   Array State : .AA. ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 941a8a10:e1427786:3ef667dd:a86f82e4
           Name : Chupa-MediaServer
  Creation Time : Fri Jul 13 21:14:42 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5860531053 (2794.52 GiB 3000.59 GB)
     Array Size : 8790795264 (8383.56 GiB 9001.77 GB)
  Used Dev Size : 5860530176 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 49296448:6d8bd27a:3a440bd4:dc10ebf3

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Sep  9 10:17:28 2012
       Checksum : 760df145 - correct
         Events : 22544

         Layout : left-symmetric
     Chunk Size : 1024K

   Device Role : Active device 0
   Array State : AAA. ('A' == active, '.' == missing)

```[B]smartctl -a /dev/sdb
[/B]```
root@Chupa-MediaServer:~# smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-00MMMB0
Serial Number:    WD-WMAWZ0139717
LU WWN Device Id: 5 0014ee 206e40ee4
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Sep  9 17:38:46 2012 CEST
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
data collection:         (50280) seconds.
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
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       3
  3 Spin_Up_Time            0x0027   177   149   021    Pre-fail  Always       -       8108
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       21
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   198   198   000    Old_age   Always       -       57
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1375
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       19
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       8
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       25
194 Temperature_Celsius     0x0022   121   117   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       6

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        59         -
# 2  Short offline       Completed without error       00%        19         -

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

```[B]smartctl -a /dev/sdc
[/B]
```
root@Chupa-MediaServer:~# smartctl -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-00MMMB0
Serial Number:    WD-WCAWZ2095381
LU WWN Device Id: 5 0014ee 206e40ea9
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Sep  9 17:40:15 2012 CEST
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
data collection:         (50760) seconds.
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
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   150   150   021    Pre-fail  Always       -       9491
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       20
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1375
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       18
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       25
194 Temperature_Celsius     0x0022   120   116   000    Old_age   Always       -       32
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

```[B]smartctl -a /dev/sdd

[/B]```
root@Chupa-MediaServer:~# smartctl -a /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-00MMMB0
Serial Number:    WD-WCAWZ2074007
LU WWN Device Id: 5 0014ee 206e40e7c
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Sep  9 17:40:34 2012 CEST
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
data collection:         (51000) seconds.
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
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   149   148   021    Pre-fail  Always       -       9525
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       20
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1375
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       18
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       25
194 Temperature_Celsius     0x0022   120   116   000    Old_age   Always       -       32
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

```[B]smartctl -a /dev/sde

[/B]```
root@Chupa-MediaServer:~# smartctl -a /dev/sde
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-00MMMB0
Serial Number:    WD-WMAWZ0140049
LU WWN Device Id: 5 0014ee 25c392274
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Sep  9 17:40:54 2012 CEST
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
data collection:         (49680) seconds.
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
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       6
  3 Spin_Up_Time            0x0027   151   151   021    Pre-fail  Always       -       9408
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       20
  5 Reallocated_Sector_Ct   0x0033   167   167   140    Pre-fail  Always       -       468
  7 Seek_Error_Rate         0x002e   193   190   000    Old_age   Always       -       185
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1375
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       18
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       28
194 Temperature_Celsius     0x0022   121   117   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   018   018   000    Old_age   Always       -       182
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       5

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

```What options do i have to not lose my data and/or get my Raid 5 up and running again?

Thanks in the first place!!

---

### Post by rubylaser on 2012-09-09
/dev/sde looks like it's failing even though it says it passed the test (I would replace this disk).  You have a bunch of reallocated sectors and Read Errors on that drive.  You are going to need to use either the --force  or --update-summaries option to assemble this array, because you have 3 different event counter numbers spread across your disks.  If you don't want to use --force, you can try to assemble it like this leaving out the /dev/sde that's likely to fail.

```
mdadm --assemble --update=summaries /dev/md0 /dev/sd[bcd]1
```

---

### Post by Chupa47 on 2012-09-10
i tried the command when the array was running and then i got this:

```
root@Chupa-MediaServer:~# mdadm --assemble --update=summaries /dev/md127 /dev/sd[bcd]1
mdadm: /dev/sdb1 is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping

```and when the array was stopped i got this:

```
root@Chupa-MediaServer:~# mdadm --assemble --update=summaries /dev/md127 /dev/sd[bcd]1
mdadm: --update=summaries not understood for 1.x metadata

```I hope i dident made a rookie mistake. this is going further then what i now know from mdadm and linux.

---

### Post by rubylaser on 2012-09-10
> **Chupa47 said:**
> i tried the command when the array was running and then i got this:

```
root@Chupa-MediaServer:~# mdadm --assemble --update=summaries /dev/md127 /dev/sd[bcd]1
mdadm: /dev/sdb1 is busy - skipping
mdadm: /dev/sdc1 is busy - skipping
mdadm: /dev/sdd1 is busy - skipping

```and when the array was stopped i got this:

```
root@Chupa-MediaServer:~# mdadm --assemble --update=summaries /dev/md127 /dev/sd[bcd]1
mdadm: --update=summaries not understood for 1.x metadata

```I hope i dident made a rookie mistake. this is going further then what i now know from mdadm and linux.

You are fine, you just needed to stop your old array first.  You will need to use the --force command, or re-create the array with the --assume-clean option since update summaries isn't working.  This will just pull your array back together and update the event counters on your disks.

---

### Post by Chupa47 on 2012-09-10
Thanks alot, the array started but i cant mount it yet. I guess i have to wait a while. but im wondering what the "active sync" means?

"Edit: It works again i can access all my files. Tomorrow to the store for replacing the broke HDD."

"[rubylaser]("http://ubuntuforums.org/member.php?u=1115132") I really what to thank you!!"

```
root@Chupa-MediaServer:~# mdadm -D /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Fri Jul 13 21:14:42 2012
     Raid Level : raid5
     Array Size : 8790795264 (8383.56 GiB 9001.77 GB)
  Used Dev Size : 2930265088 (2794.52 GiB 3000.59 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Mon Sep 10 22:03:50 2012
          State : active, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 1024K

           Name : Chupa-MediaServer
           UUID : 941a8a10:e1427786:3ef667dd:a86f82e4
         Events : 22554

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1
       2       8       33        2      active sync   /dev/sdc1
       4       8       17        3      active sync   /dev/sdb1

```

---

### Post by rubylaser on 2012-09-10
No problem, glad you got it working :)

---

