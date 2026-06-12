---
title: "Degraded Raid 5, finding faulty HDD"
date: 2008-07-08
forum: Server Platforms
---

### Post by siDDis on 2008-07-08
I just lost a disk in my raid 5 array. The disk don't show up as /dev/sde anymore.

When I'm removing it from the chassis now I will try to unplug the disks one by one while the computer is online to find which one has failed.

Is it safe enough to just unmount the raid when I do this?

---

### Post by fjgaude on 2008-07-08
Yes, you can umount the array, using LiveCD if you have to.

Also you can find the relationship of a physical drive, its /dev/sd[n] and serial number (SN) by using this command:

```
sudo hdparm -i -v /dev/sd[n]
```

Good hunting, but let us know how you are doing. I assume you are using **mdadm**?

---

### Post by siDDis on 2008-07-08
Thank you, yeah I'm using mdadm :)

---

### Post by siDDis on 2008-07-08
Okey I found the harddrive, it started again after I replugged the powercable

So I ran smartmon and got these results:

> 
olav@olav-linux:~$ sudo smartctl --all /dev/sdj
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE16 family
Device Model:     WDC WD5000KS-00MNB0
Serial Number:    WD-WCANU1337955
Firmware Version: 07.02E07
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Jul  8 21:35:46 2008 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (14400) seconds.
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
recommended polling time:        ( 179) minutes.
Conveyance self-test routine
recommended polling time:        (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   248   224   021    Pre-fail  Always       -       4600
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       221
  5 Reallocated_Sector_Ct   0x0033   117   117   140    Pre-fail  Always   FAILING_NOW 664
  7 Seek_Error_Rate         0x000f   176   052   051    Pre-fail  Always       -       894
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       9354
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       215
194 Temperature_Celsius     0x0022   253   253   000    Old_age   Always       -       50
196 Reallocated_Event_Count 0x0032   188   188   000    Old_age   Always       -       12
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 22 (device log contains only the most recent five errors)
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

Error 22 occurred at disk power-on lifetime: 9354 hours (389 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 00 02   1d+11:07:28.083  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00   1d+11:07:28.083  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 02   1d+11:07:28.074  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 02   1d+11:07:22.592  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00   1d+11:07:22.592  READ NATIVE MAX ADDRESS EXT

Error 21 occurred at disk power-on lifetime: 9354 hours (389 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 00 00 00 00 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  27 00 00 00 00 00 00 00   1d+11:07:28.083  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 02   1d+11:07:28.074  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 02   1d+11:07:22.592  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00   1d+11:07:22.592  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 02   1d+11:07:22.583  IDENTIFY DEVICE

Error 20 occurred at disk power-on lifetime: 9354 hours (389 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 00 02   1d+11:07:22.592  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00   1d+11:07:22.592  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 02   1d+11:07:22.583  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 02   1d+11:07:17.102  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00   1d+11:07:17.102  READ NATIVE MAX ADDRESS EXT

Error 19 occurred at disk power-on lifetime: 9354 hours (389 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 00 00 00 00 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  27 00 00 00 00 00 00 00   1d+11:07:22.592  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 02   1d+11:07:22.583  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 02   1d+11:07:17.102  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00   1d+11:07:17.102  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 02   1d+11:07:17.093  IDENTIFY DEVICE

Error 18 occurred at disk power-on lifetime: 9354 hours (389 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 45 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 45 00 00 00 00 02   1d+11:07:17.102  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00   1d+11:07:17.102  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 02   1d+11:07:17.093  IDENTIFY DEVICE
  29 ff 01 2f 5a 38 3a 00   1d+11:06:42.138  READ MULTIPLE EXT
  29 ff 01 2f 5c 38 3a 00   1d+11:06:42.138  READ MULTIPLE EXT

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


I guess this disc is just thrash :/

---

### Post by fjgaude on 2008-07-08
Time to acquire another drive, eh?

You might find this piece interesting, infomative:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

Carry one!

---

