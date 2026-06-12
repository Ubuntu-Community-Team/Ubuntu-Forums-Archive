---
title: "configuring software raid5 (mdadm) on ubuntu server 12.04.4 LTS"
date: 2014-06-06
forum: Server Platforms
---

### Post by dmhymers on 2014-06-06
[COLOR=#000000]I recently installed Ubuntu Server 12.04 on a box that I'm trying to use as a samba server. I've been following various online tutorials on how to configure a 4-drive raid5, using mdadm and drives that I previously had running in my desktop under a highpoint software raid card. The reason I am trying to migrate to mdadm is because highpoint does not have proper drivers for kernel version 3.x, only for 2.x, and there are no currently-supported ubuntu versions using 2.x.[/COLOR]

[COLOR=#000000]After trying multiple times and failing every time, I have reset my server, with a fresh install of 12.04.4. The only packages installed were the base ubuntu server, the ssh server and the samba server packages (from the installer). I have not installed any additional software except for mdadm itself.[/COLOR]
[COLOR=#000000]```
sudo apt-get install mdadm
```[/COLOR]
[COLOR=#000000]I have five drives attached to the system. 4x 1TB which I want to use for raid (/dev/sd[a-d]) and a single 250GB drive for boot (/dev/sde).[/COLOR]

[COLOR=#000000]I use parted to remove old partitions from the drives, and create new partitions that I can use for the raid devices.[/COLOR]

[COLOR=#000000]```

root@malamute:~# parted /dev/sdd
GNU Parted 2.3
Using /dev/sdd
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt
Warning: The existing disk label on /dev/sdd will be destroyed and all data on
this disk will be lost. Do you want to continue?
Yes/No? y
(parted) mkpart primary 1 -1
(parted) align-check opt 1
1 aligned
(parted) quit
Information: You may need to update /etc/fstab.
```[/COLOR]```

[COLOR=#000000]Create an array using mdadm[/COLOR]
[COLOR=#000000]Code:
root@malamute:~# mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sd[a-d]1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: size set to 976629248K
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
[/COLOR]
```[COLOR=#000000]
[/COLOR]
[COLOR=#000000]/dev/md0 starts its initial assembly, I watch /proc/mdstat[/COLOR]

[COLOR=#000000]```

watch cat /proc/mdstat
```[/COLOR]
[COLOR=#000000]It looks something like this:[/COLOR]

[COLOR=#000000]```

Every 2.0s: cat /proc/mdstat                             Thu Jun  5 18:20:08 2014

Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdd1[4] sdc1[2] sdb1[1] sda1[0]
      2929887744 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]
      [>....................]  recovery =  0.9% (9542688/976629248) finish=435.9m
in speed=36975K/sec


unused devices: <none>
```

I leave the array to assemble overnight, when I wake, this is what I see:

[/COLOR]```
Every 2.0s: cat /proc/mdstat                             Fri Jun  6 11:11:24 2014


Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdd1[4](S) sdc1[2] sdb1[1] sda1[0](F)
      2929887744 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/2] [_UU_]


unused devices: <none>



```[COLOR=#000000]

Any suggestions?[/COLOR]

---

### Post by fatmann66 on 2014-06-06
I used to run a mdadm software raid 5 setup on my box, but had  multiple problems with superblock corruption and bad inodes. I finally  gave up the idea. ( not that this helps you here) One of the reasons I decided not to do this was, after some research that I read. it stated that building a raid 5 container larger the 2TB wasn't suggested. apparently this is known to cause issues and file corruption. your current setup will put you at 3TB if you use all the drives. 

with my experiences running software raid for 5 years I figured it wasn't worth it. I currently  run a few 2TB drive with a basic ext4 partition on it. and backup using crash plan to an external drive.  

I really didn't need the speed gained by raid 5, I just wanted the storage. with the file corruption issues etc. I wasn't getting the redundancy I wanted so I scrapped the idea altogether. 

some other things to think about. if you built the raid a few times this can cause remnants of the config in the system and on the disk. make sure you clear them out and destroy  MD0.  the beginning of drives should be DDed to clear any raid table info. (can't give particulars off the top of my head, but can look back at my notes if I still have them.)

good Luck.
Fatmann66

---

### Post by TheFu on 2014-06-08
No answers, but questions.
* Are the 4 drives of identical layout?  
* Same sector sizes? 
* Same partition sizes?
* Please post the output from **sudo parted -l**
* Check the SATA connections - you've probably done this 50 times already. Loose cables suck.
* SMART data look ok for each drive?

Also - does the boot drive path change from time to time?  May be useful to use these by labels or UUIDs, not device names if that is an issue.

---

### Post by dmhymers on 2014-06-08
> **TheFu said:**
> No answers, but questions.
* Are the 4 drives of identical layout?  
* Same sector sizes? 
* Same partition sizes?
* Please post the output from **sudo parted -l**
* Check the SATA connections - you've probably done this 50 times already. Loose cables suck.
* SMART data look ok for each drive?

Also - does the boot drive path change from time to time?  May be useful to use these by labels or UUIDs, not device names if that is an issue.

All four drives are the same model, one is a factory refurb and has a slightly different model number. They are all formatted using the parted defaults, can't see why that would cause any inconsistencies.

```

dmhymers@malamute:~$ sudo parted -l
[sudo] password for dmhymers:
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1000GB  1000GB               primary




Model: ATA ST31000524AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1000GB  1000GB               primary




Model: ATA ST31000528AS (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1000GB  1000GB               primary




Model: ATA ST31000528AS (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1000GB  1000GB               primary




Model: ATA WDC WD2500AAJB-2 (scsi)
Disk /dev/sde: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  247GB  247GB   primary   ext4            boot
 2      247GB   250GB  3151MB  extended
 5      247GB   250GB  3151MB  logical   linux-swap(v1)




Error: /dev/md0: unrecognised disk label
```

smart info:

```

dmhymers@malamute:~$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.11.0-22-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST31000528AS
Serial Number:    6VP9N56H
LU WWN Device Id: 5 000c50 0303901d5
Firmware Version: CC38
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Jun  8 15:54:13 2014 EDT
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
data collection:                (  600) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 179) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   096   006    Pre-fail  Always       -       143671110
  3 Spin_Up_Time            0x0003   095   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3261
  5 Reallocated_Sector_Ct   0x0033   096   096   036    Pre-fail  Always       -       192
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       74653579
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       22364
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1656
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       210
188 Command_Timeout         0x0032   100   096   000    Old_age   Always       -       524297
189 High_Fly_Writes         0x003a   098   098   000    Old_age   Always       -       2
190 Airflow_Temperature_Cel 0x0022   067   057   045    Old_age   Always       -       33 (Min/Max 30/33)
194 Temperature_Celsius     0x0022   033   043   000    Old_age   Always       -       33 (0 13 0 0)
195 Hardware_ECC_Recovered  0x001a   033   014   000    Old_age   Always       -       143671110
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       7
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       7
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       182849642719308
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2963731064
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3587402993


SMART Error Log Version: 1
ATA Error Count: 196 (device log contains only the most recent five errors)
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


Error 196 occurred at disk power-on lifetime: 22301 hours (929 days + 5 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 c0 ff ff ff ef 00      08:39:41.272  READ DMA EXT
  25 00 40 ff ff ff ef 00      08:39:41.270  READ DMA EXT
  25 00 00 ff ff ff ef 00      08:39:41.255  READ DMA EXT
  25 00 40 ff ff ff ef 00      08:39:37.229  READ DMA EXT
  25 00 00 ff ff ff ef 00      08:39:37.207  READ DMA EXT


Error 195 occurred at disk power-on lifetime: 22282 hours (928 days + 10 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 ff ff ff ef 00   1d+06:14:29.577  READ DMA EXT
  25 00 80 ff ff ff ef 00   1d+06:14:29.574  READ DMA EXT
  25 00 00 ff ff ff ef 00   1d+06:14:29.559  READ DMA EXT
  25 00 80 ff ff ff ef 00   1d+06:14:27.418  READ DMA EXT
  25 00 00 ff ff ff ef 00   1d+06:14:27.399  READ DMA EXT


Error 194 occurred at disk power-on lifetime: 22273 hours (928 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 ff ff ff ef 00      22:09:32.928  READ DMA EXT
  25 00 00 ff ff ff ef 00      22:09:32.911  READ DMA EXT
  25 00 00 ff ff ff ef 00      22:09:32.899  READ DMA EXT
  25 00 00 ff ff ff ef 00      22:09:32.884  READ DMA EXT
  25 00 00 ff ff ff ef 00      22:09:18.593  READ DMA EXT


Error 193 occurred at disk power-on lifetime: 22259 hours (927 days + 11 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 ff ff ff ef 00      07:11:22.589  READ DMA EXT
  25 00 80 ff ff ff ef 00      07:11:11.466  READ DMA EXT
  25 00 80 ff ff ff ef 00      07:11:11.462  READ DMA EXT
  25 00 00 ff ff ff ef 00      07:10:57.727  READ DMA EXT
  25 00 00 ff ff ff ef 00      07:10:57.710  READ DMA EXT


Error 192 occurred at disk power-on lifetime: 22249 hours (927 days + 1 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 ff ff ff ef 00      07:38:50.653  READ DMA EXT
  25 00 40 ff ff ff ef 00      07:38:36.445  READ DMA EXT
  25 00 00 ff ff ff ef 00      07:38:36.431  READ DMA EXT
  25 00 c0 ff ff ff ef 00      07:38:22.138  READ DMA EXT
  25 00 40 ff ff ff ef 00      07:38:22.128  READ DMA EXT


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     17023         -


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
dmhymers@malamute:~$ sudo smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.11.0-22-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     ST31000524AS
Serial Number:    6VPAVQ43
LU WWN Device Id: 5 000c50 03ce12550
Firmware Version: JC4B
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Jun  8 15:55:43 2014 EDT
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
data collection:                (  600) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 174) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       146690619
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       119
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   060   030    Pre-fail  Always       -       24727210
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       5126
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       127
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       2
189 High_Fly_Writes         0x003a   099   099   000    Old_age   Always       -       1
190 Airflow_Temperature_Cel 0x0022   067   058   045    Old_age   Always       -       33 (Min/Max 31/35)
194 Temperature_Celsius     0x0022   033   042   000    Old_age   Always       -       33 (0 18 0 0)
195 Hardware_ECC_Recovered  0x001a   035   026   000    Old_age   Always       -       146690619
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       140346646336779
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1954640209
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3538629323


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      4853         -


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
dmhymers@malamute:~$ sudo smartctl -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.11.0-22-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST31000528AS
Serial Number:    6VP9JY73
LU WWN Device Id: 5 000c50 02bcfef7e
Firmware Version: CC38
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Jun  8 15:56:22 2014 EDT
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
data collection:                (  617) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 191) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       144340382
  3 Spin_Up_Time            0x0003   096   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3341
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       69363142
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       22461
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1699
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       4295032834
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   052   045    Old_age   Always       -       34 (Min/Max 31/36)
194 Temperature_Celsius     0x0022   034   048   000    Old_age   Always       -       34 (0 12 0 0)
195 Hardware_ECC_Recovered  0x001a   031   009   000    Old_age   Always       -       144340382
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       212373247912339
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4064500875
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3784791925


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     17126         -


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
dmhymers@malamute:~$ sudo smartctl -a /dev/sddsmartctl 5.41 2011-06-09 r3365 [i686-linux-3.11.0-22-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST31000528AS
Serial Number:    5VP6QWJE
LU WWN Device Id: 5 000c50 03042a667
Firmware Version: CC38
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Jun  8 15:59:47 2014 EDT
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
data collection:                (  600) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 179) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       149187355
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   097   020    Old_age   Always       -       31
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       73361383
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       22450
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1698
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       1
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   069   054   045    Old_age   Always       -       31 (Min/Max 28/33)
194 Temperature_Celsius     0x0022   031   046   000    Old_age   Always       -       31 (0 10 0 0)
195 Hardware_ECC_Recovered  0x001a   031   020   000    Old_age   Always       -       149187355
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       44092134287614
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4130260946
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       729610246


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     17118         -


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


SATA connections are fine. This is the same issue I tried to fix on my own -- every time I tried, the raid would assemble properly, but I would get this same exact issue with the disks -- one marked (S) and one marked (F). Running a long self-test on /dev/sda now, will see what happens there. I know it's showing individual errors, but I've run worse drives for a long time (albeit under windows) without any issues.

Labels might change on reboot, but I haven't rebooted the server in a few days -- ever since I built this array. If I can't get it working at all, what's the point of working with UUIDs?

---

### Post by dmhymers on 2014-06-08
> **fatmann66 said:**
> I used to run a mdadm software raid 5 setup on my box, but had  multiple problems with superblock corruption and bad inodes. I finally  gave up the idea. ( not that this helps you here) One of the reasons I decided not to do this was, after some research that I read. it stated that building a raid 5 container larger the 2TB wasn't suggested. apparently this is known to cause issues and file corruption. your current setup will put you at 3TB if you use all the drives. 

with my experiences running software raid for 5 years I figured it wasn't worth it. I currently  run a few 2TB drive with a basic ext4 partition on it. and backup using crash plan to an external drive.  

I really didn't need the speed gained by raid 5, I just wanted the storage. with the file corruption issues etc. I wasn't getting the redundancy I wanted so I scrapped the idea altogether. 

some other things to think about. if you built the raid a few times this can cause remnants of the config in the system and on the disk. make sure you clear them out and destroy  MD0.  the beginning of drives should be DDed to clear any raid table info. (can't give particulars off the top of my head, but can look back at my notes if I still have them.)

good Luck.
Fatmann66

This is a clean system install, and I completely reformatted the drives including a new partition table. I also zeroed the superblocks from the old array using mdadm before I reformatted the system. If this isn't good enough to clear out the superblock data, how would I go about doing so?

I made a few brief searches, and I can't find anything referencing the instability you're attributing to raid5. Care to share a source?

If I can't get a RAID5 working, I may go for a pair of RAID1s, or maybe a RAID 10. I want the redundancy because the data kept on this server is a copy of my parents' music and video library -- so backups exist, but they're far away. I want to be able to tolerate a failure on my end.

---

### Post by dmhymers on 2014-06-08
/dev/sda is being marked with read failures. Guess that solves that issue. 

Does anyone see anything wrong with how I've configured the array in principle, were I to try again with a 3-drive array?

---

### Post by rubylaser on 2014-06-08
sda is definitely bad and should be replaced.  If the drive isn't too old, you may be able to RMA it to Seagate and get a free replacement minus shipping cost.  Your steps look good, and if you want to double check your steps, you can follow my mdadm tutorial in my signature.  I've never seen nor heard of this 2TB issue mentioned previously, and I've used mdadm on disks for years from all manufacturers and of various sizes.

The first thing I would do since you've had this problem before is run badblocks on each of your disks.  This will stress test them (and take a long time), but it will weed out any bad disks.  Use it like this.

```

badblocks -wsv /dev/sdb

```

Also, I'm a big propionate of mdadm on this forum, but for many home users just looking for bulk storage, I think SnapRAID is a better solution.  I have directions for that in my signature too, if you want to see what it's about.

---

### Post by Dale_Whitnall on 2014-06-08
I second the SnapRAID solution, I have used a 6 drive RAID 5 setup before using madam.  When it was working it was great but when I had a drive failing it was a pain to rebuild and keep going.  I ended up going with SnapRAID and using AUFS to pool the drives together, though recently I have moved from AUFS to mhddfs as AUFS also has a few little problems I have come accross.

---

### Post by dmhymers on 2014-06-08
/dev/sda is unfortunately out of warranty. I can't afford to buy a new drive at the moment, but I may add a drive at some point in the future, once I have the money.

That's actually the mdadm tutorial I was using. I think I'll continue with mdadm for now, seeing as nothing intended to sit on this array is irreplaceable. Thanks for the tips.

Will run badblocks and build a new array with the three good drives (assuming they all end up being good). Just to confirm, I can just stop the current array, and zero the superblocks using for example:

```
sudo mdadm --zero-superblock /dev/sdb
```

and I should then be good to make a new array without any issues?

---

### Post by rubylaser on 2014-06-08
> **dmhymers said:**
> 

Will run badblocks and build a new array with the three good drives (assuming they all end up being good). Just to confirm, I can just stop the current array, and zero the superblocks using for example:

```
sudo mdadm --zero-superblock /dev/sdb
```

and I should then be good to make a new array without any issues?

Yup, that will be fine.  And, I'm glad to see you are using my tutorial.  Don't forget to setup email alerts and smartmontools to monitor your disks and get emails if things go sideways.

---

### Post by dmhymers on 2014-06-08
Small problem.

I stopped the array using 
```
mdadm --stop /dev/md0
```

and attempted to zero superblocks, but I ran into a problem: 

```
root@malamute:~# mdadm --zero-superblock /dev/sdb
mdadm: Unrecognised md component device - /dev/sdb
```

---

### Post by SeijiSensei on 2014-06-09
> **dmhymers said:**
> The reason I am trying to migrate to mdadm is because highpoint does not have proper drivers for kernel version 3.x, only for 2.x, and there are no currently-supported ubuntu versions using 2.x.

Just for reference, RedHat and its derivatives like CentOS and Scientific Linux use kernel 2.6.x (currently 2.6.32).  You might consider installing [CentOS]("http://www.centos.org/") instead of Ubuntu and see if that works with your controller card.  The drives themselves do look a bit wonky though.

---

### Post by dmhymers on 2014-06-13
> **SeijiSensei said:**
> Just for reference, RedHat and its derivatives like CentOS and Scientific Linux use kernel 2.6.x (currently 2.6.32).  You might consider installing [CentOS]("http://www.centos.org/") instead of Ubuntu and see if that works with your controller card.  The drives themselves do look a bit wonky though.

If I have trouble getting everything working, I may look into that. I've never used a distro that wasn't based on debian, are redhat derivatives any more difficult to use?

---

### Post by SeijiSensei on 2014-06-13
Not really.  Some files are located in slightly different places.  Now that Ubuntu uses upstart, commands like "service" and "chkconfig" work the same way on both platforms.  Otherwise Linux is Linux no matter what the distribution.

---

### Post by elico on 2014-06-14
How about LVM raid? instead of mdam?
What is the issue? when you have issues with the drive it's either the drive or the MB controller or the disk controller.
It seems that in the case of  a disk faliure you would need to use anohter disk and the issue is not mdam or the kernel...
if it's not the system disk or even the system disk you maybe consider using LVM raid5 which is also working pretty nice.

---

### Post by dmhymers on 2014-06-15
mdadm is what I saw the most recommendations for, and I think I'm going to stick with it unless I find I can't make it work at all for whatever reason.

As to the rest of your questions, they've mostly been dealt with above. Only reason I didn't suspect a disk failure from word one was that I had previously had the disks working under a different controller. Once I get the new array set up, I think I should be good to go. The kernel issue is a driver thing, I have no complaints about the kernel other than highpoint is too lazy to make drivers for kernel 3.x.

---

