---
title: "Disk Likely to Fail Soon - Reallocate Sector Count"
date: 2015-10-12
forum: Ubuntu/Debian BASED
---

### Post by HatoExB on 2015-10-12
Hi,

The "Reallocate Sector Count" SMART assessment is failing on my drive.

The logs are as followed, issuing this command: ```
smartctl -a /dev/sda
``` 

```
tangerine@tangerine-Studio-1535:~$ sudo smartctl -a /dev/sda
[sudo] password for tangerine: 
smartctl 6.2 2013-07-26 r3841 [i686-linux-3.19.0-31-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD2500BEVT-75ZCT2
Serial Number:    WD-WXEY08JC6614
LU WWN Device Id: 5 0014ee 0aba4bcda
Firmware Version: 11.01A11
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 3.0 Gb/s
Local Time is:    Sun Oct 11 21:22:23 2015 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (  73)    The previous self-test completed having
                    a test element that failed and the test
                    element that failed is not known.
Total time to complete Offline 
data collection:         ( 7500) seconds.
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
recommended polling time:      (  90) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       63
  3 Spin_Up_Time            0x0027   185   180   021    Pre-fail  Always       -       1708
  4 Start_Stop_Count        0x0032   034   034   000    Old_age   Always       -       66124
  5 Reallocated_Sector_Ct   0x0033   133   133   140    Pre-fail  Always   FAILING_NOW 536
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   078   078   000    Old_age   Always       -       16584
 10 Spin_Retry_Count        0x0032   100   099   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   093   093   000    Old_age   Always       -       7697
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       524
193 Load_Cycle_Count        0x0032   042   042   000    Old_age   Always       -       476882
194 Temperature_Celsius     0x0022   102   088   000    Old_age   Always       -       45
196 Reallocated_Event_Count 0x0032   092   092   000    Old_age   Always       -       108
197 Current_Pending_Sector  0x0032   200   199   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   082   082   000    Old_age   Always       -       13469
241 Total_LBAs_Written      0x0032   031   001   000    Old_age   Always       -       169273441748316
242 Total_LBAs_Read         0x0032   200   200   000    Old_age   Always       -       36608412523

SMART Error Log Version: 1
ATA Error Count: 783 (device log contains only the most recent five errors)
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

Error 783 occurred at disk power-on lifetime: 16471 hours (686 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 10 87 40  Error: WP at LBA = 0x0087103b = 8851515

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 10 a8 28 a9 2b 14 00      06:48:53.333  WRITE FPDMA QUEUED
  60 08 a0 38 10 87 15 00      06:48:53.326  READ FPDMA QUEUED
  61 08 98 60 88 d4 13 00      06:48:53.316  WRITE FPDMA QUEUED
  61 08 90 60 4b 64 14 00      06:48:53.303  WRITE FPDMA QUEUED
  61 08 88 a8 3e ce 13 00      06:48:53.303  WRITE FPDMA QUEUED

Error 782 occurred at disk power-on lifetime: 16471 hours (686 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 10 87 40  Error: WP at LBA = 0x0087103b = 8851515

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 10 28 10 a9 2b 14 00      06:48:50.040  WRITE FPDMA QUEUED
  61 08 20 78 b9 f5 13 00      06:48:50.028  WRITE FPDMA QUEUED
  61 08 18 d0 51 2b 14 00      06:48:50.028  WRITE FPDMA QUEUED
  61 10 10 48 ec 2d 14 00      06:48:50.025  WRITE FPDMA QUEUED
  61 08 08 f0 a8 2b 14 00      06:48:50.015  WRITE FPDMA QUEUED

Error 781 occurred at disk power-on lifetime: 16471 hours (686 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 10 87 40  Error: WP at LBA = 0x0087103b = 8851515

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 a8 f8 66 56 15 00      06:48:46.763  WRITE FPDMA QUEUED
  60 08 a0 38 10 87 15 00      06:48:46.757  READ FPDMA QUEUED
  60 40 98 e8 10 87 15 00      06:48:46.756  READ FPDMA QUEUED
  60 08 90 e0 10 87 15 00      06:48:46.756  READ FPDMA QUEUED
  60 08 88 d8 10 87 15 00      06:48:46.756  READ FPDMA QUEUED

Error 780 occurred at disk power-on lifetime: 16471 hours (686 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 10 87 40  Error: UNC at LBA = 0x0087103b = 8851515

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 78 38 10 87 15 00      06:48:43.421  READ FPDMA QUEUED
  60 08 70 30 10 87 15 00      06:48:43.421  READ FPDMA QUEUED
  60 08 68 28 10 87 15 00      06:48:43.421  READ FPDMA QUEUED
  60 08 60 20 10 87 15 00      06:48:43.421  READ FPDMA QUEUED
  60 08 58 18 10 87 15 00      06:48:43.420  READ FPDMA QUEUED

Error 779 occurred at disk power-on lifetime: 16471 hours (686 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 3b 10 87 40  Error: UNC at LBA = 0x0087103b = 8851515

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 f8 f8 0f 87 15 00      06:48:40.294  READ FPDMA QUEUED
  60 00 f0 f8 0e 87 15 00      06:48:40.276  READ FPDMA QUEUED
  60 00 e8 f8 0d 87 15 00      06:48:40.260  READ FPDMA QUEUED
  60 00 e0 f8 0c 87 15 00      06:48:40.258  READ FPDMA QUEUED
  60 00 d8 f8 0b 87 15 00      06:48:40.256  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: unknown failure    90%     16584         -
# 2  Short offline       Completed: read failure       90%     10319         94643696
# 3  Extended offline    Completed without error       00%         1         -

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

I found out about this error about 3-4 years ago. Windows told (spammed) me that my drive was failing, so I backed the data off another computer and braced for a "Unable to access hard drive" message. Fast forward to now and it's....still working?? I've been using this computer for a long time (and kinda frequent too!) running Ubuntu and it's not dead yet?? The log says the drive will fail in less than 24 hours, but it also said that about a year ago of issuing the command (when I switched to Linux).

Based on the command I issued, will my drive last me a few more years? Most of my data is safe in the cloud, but I've got a few important documents.

Running Elementary OS freya (Ubuntu 14.04.3LTS) 32 bit on a Dell Studio 1535 laptop (purchased very close to launch).

---

### Post by Bashing-om on 2015-10-12
HatoExB; Hello;

That drive as is now is toast .. I would not trust it at all:
> 
5 Reallocated_Sector_Ct   0x0033   133   133   140    Pre-fail  Always   FAILING_NOW 536
197 Current_Pending_Sector  0x0032   200   199   000    Old_age   Always       -       3

You might and the stress is on might ... be able to zero out that drive. reformat it and use it as a data disk. But I would never ever fully trust that drive.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2015-10-12
You can run *badblocks* on it and capture the list.

```
sudo badblocks > mylistofbadblocksonthisdiskdrive.txt
```

Then examine the list and determine where, physically the sectors lie on the platters.  You can repartition the disk drive to work around the bad sectors.  Typically the blocks are labeled 0 to n and start on the inside cylinder.  So the badblock numbers tell you the location:

> tgalati4@Mint17 ~ $ sudo fdisk -l
[sudo] password for tgalati4: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT


For this drive, a block is composed of 2 sectors each.

I've have rescued a few disks that had high badblock counts, but making a small partition that captures most of the failing sectors (and not using it) means you can get several more years out of the disk drive.  This won't work for all failing-sector drives, but it's worth a shot.  If the badblocks are scattered throughout the drive, then partitioning them off won't work.   

In fact the drive that I'm using right now I partitioned off the badblocks.  It was a Win7 drive that failed and was discarded by IT staff.  I examined it and found a tight cluster of bad sectors.  Partitioned them off and put on Linux.  That was 2 years ago.

If you have a drive that has been spinning and working for 16,500 hours, then you can get about 35k more hours, since many drives can run for 50k hours.

Or it could die tomorrow.

---

### Post by coffeecat on 2015-10-13
> **HatoExB said:**
> 
Running Elementary OS freya

*Thread moved to **Ubuntu/Debian BASED**.*

---

