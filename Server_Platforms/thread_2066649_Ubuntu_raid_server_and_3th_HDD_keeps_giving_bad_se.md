---
title: "Ubuntu raid server and 3th HDD keeps giving bad sectors."
date: 2012-10-05
forum: Server Platforms
---

### Post by Chupa47 on 2012-10-05
Hey,

i have a Raid 5 with x4 3Tb Western Digital Green disks. (i disabled the timer so they don't fall asleep after 8 sec)

with 3 of them i have no problem, they have been running for more then 2 months and not 1 bad sector. But on 1 i keep getting bad sectors.

_A month ago:_
I saw i had bad sectors. The disk was only in use for over a month so went back to the store got a new one in warranty. Then with placing the new disk i had some problems with rebuilding my raid, so i posted a Thread about my problem and i got it to work again. The raid rebuild-ed and it was working good, but yet again after 2 days i saw i had 15 bad sectors. (i called a friend to ask if i should return to the store again to get a new one, but he said i should first see if it gets any worse, what i did was change the cable from the motherboard to the HDD(dont know if it would help anything))

_25 days later, so yesterday:_
I saw i had 19 bad sectors. so i went back to the store got a new HDD( dident change the timer yet) placed it in the RAID 5 started repairing. after 3 hours i went back to check how far he was and i saw the BRAND NEW DISK already has "Bad Sectors"!!](*,)

Does anybody ever had the same problem? Do i just have bad luck? Would the problem be on the motherboard?

I Feel pretty bad for going back to the store a Fourth time :?

---

### Post by rubylaser on 2012-10-05
Can you provide the output of smartctl -a /dev/sdX for that disk, so that we can see all of the SMART values?

---

### Post by Chupa47 on 2012-10-05
root@Chupa-MediaServer:~# smartctl -a /dev/sde
```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-00MMMB0
Serial Number:    WD-WCAWZ2431387
LU WWN Device Id: 5 0014ee 2071355a8
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Oct  5 16:38:37 2012 CEST
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
data collection:         (52380) seconds.
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
  1 Raw_Read_Error_Rate     0x002f   100   253   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   191   191   021    Pre-fail  Always       -       7408
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       9
  5 Reallocated_Sector_Ct   0x0033   178   178   140    Pre-fail  Always       -       318
  7 Seek_Error_Rate         0x002e   197   188   000    Old_age   Always       -       113
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       23
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       7
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       6
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       10
194 Temperature_Celsius     0x0022   127   120   000    Old_age   Always       -       25
196 Reallocated_Event_Count 0x0032   149   149   000    Old_age   Always       -       51
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

