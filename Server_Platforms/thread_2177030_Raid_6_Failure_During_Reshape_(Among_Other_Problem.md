---
title: "Raid 6 Failure During Reshape (Among Other Problems)"
date: 2013-09-26
forum: Server Platforms
---

### Post by ryydRnF on 2013-09-26
Hello all!  First time posted, long time reader.  By a long string of back luck coincidences, I feel like my only chance to recover (if not fully, then partially) my data is to defer to you.  Here's the deal:

Initially, 6aid 6 (mdadm) with 10 drives, a mix of 1 and 2 TB WD drives (was moving towards all 2 TB).  Needed more space, so I decided to add another drive to the array.  Easy, right?  I partition and add the drive just fine, and it starts to reshape (which is terribly slow, by the way).

About a day into the process, Ubuntu magically decides to kick one of my other drives OFF of the array, turning it into a spare.  Why?  I have no idea.  There was a reboot in there somewhere for some reason I'm not really sure of.  OK, so that's fine...that's why I have raid 6.

Of course, things go downhill from here.  I check the SMART status of my drives, and lo and behold one of my 1 TB drives has not passed a SMART check.  ****.  2 down, I'm nervous but OK.  3, I'm screwed.  I hope that the reshape finishes before this drive fails.

Nope.  Drive fails at about 80% of the way through the reshape.  So now I have 3 drives down in my array, and it's just sitting there, wondering what the hell to do.  I have not done much other than try to get the array up and reshape again, to no avail.

So, any help?  I'll post commands as requested, but at this point I'm out of ideas.  I've been reading for days on what to do, and short of trying to image the failed drive onto a new one, I've tried most everything (whilst making sure I didn't force Ubuntu to do anything drastic).

---

### Post by CharlesA on 2013-09-26
Do you have any recent backups? If the array is toast, the only way you'll be able to recover your data is from backups.

Well, outside of an expensive data recovery solution.

Are you 100% sure you have three failed drives?

Run this:

```
sudo mdadm --detail --scan
```

---

### Post by ryydRnF on 2013-09-27
All of my important information is backed up via Amazon S3...but the TV shows and movies, I don't bother backing up.

Here's the output:

```
root@titanium:~# mdadm --detail --scan
ARRAY /dev/md0 metadata=0.91 spares=2 UUID=e7db05b0:4a9008b8:98883325:0d269d95
```

Which only shows 2 spares, yet the output of this...

```
root@titanium:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdh1[0] sdl1[11](S) sdk1[12](S) sdj1[9] sde1[7] sdb1[6] sdf1[5] sdd1[4] sdg1[3] sdc1[2] sdi1[13](F)
      7814079488 blocks super 0.91 level 6, 64k chunk, algorithm 2 [11/8] [U_UUUUUU_U_]
      [===============>.....]  reshape = 79.5% (777285208/976759936) finish=542800.5min speed=6K/sec


unused devices: <none>
```

...obviously shows 3.

---

### Post by CharlesA on 2013-09-27
I'm not that familiar with mdadm despite using it on one of my backup servers, but it looks like it is showing 2 spares and 1 failed drive. I'm not really sure if this is normal (I doubt it), but I do know when I was resyncing my RAID5 array, it showed one device as a spare.

A speed is 6K/sec seems insanely slow. Can you post the smart stats of all the drives?

EDIT: I think it is showing two spares because it is basically doing a rebuild and has those drives reserves for the parity info. Could be wrong though.

---

### Post by ryydRnF on 2013-09-27
That slow speed is after I received the email about the failed drive:

```
[FONT=arial]This is an automatically generated mail message from mdadm[/FONT]
[FONT=arial]running on titanium[/FONT]

[FONT=arial]A Fail event had been detected on md device /dev/md0.[/FONT]

[FONT=arial]It could be related to component device /dev/sdi1.[/FONT]

[FONT=arial]Faithfully yours, etc.[/FONT]

[FONT=arial]P.S. The /proc/mdstat file currently contains the following:[/FONT]

[FONT=arial]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10][/FONT]
[FONT=arial]md0 : active raid6 sdh1[0] sdl1[11](S) sdk1[12](S) sdj1[9] sde1[7] sdb1[6] sdf1[5] sdd1[4] sdg1[3] sdc1[2] sdi1[13](F)[/FONT]
[FONT=arial]      7814079488 blocks super 0.91 level 6, 64k chunk, algorithm 2 [11/8] [U_UUUUUU_U_][/FONT]
[FONT=arial]      [===============>.....]  reshape = 79.5% (777281600/976759936) finish=1957.6min speed=1698K/sec[/FONT]

[FONT=arial]unused devices: <none>[/FONT]
```

SMART results:

```
root@titanium:~# smartctl -a /dev/sdb1smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WMAZA7111288
LU WWN Device Id: 5 0014ee 2b15f3616
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:29:29 2013 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (41160) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off suppo
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
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_F
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -
  3 Spin_Up_Time            0x0027   180   164   021    Pre-fail  Always       -
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -
  9 Power_On_Hours          0x0032   084   084   000    Old_age   Always       -
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -
193 Load_Cycle_Count        0x0032   167   167   000    Old_age   Always       -
194 Temperature_Celsius     0x0022   109   105   000    Old_age   Always       -
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_
# 1  Extended offline    Completed without error       00%     12135         -


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
root@titanium:~# smartctl -a /dev/sdc1smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD10EARS-22Y5B1
Serial Number:    WD-WCAV5F290045
LU WWN Device Id: 5 0014ee 204ceee57
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:32:03 2013 PDT
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
data collection:                (20460) seconds.
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
recommended polling time:        ( 236) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3031) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       3
  3 Spin_Up_Time            0x0027   138   134   021    Pre-fail  Always       -       6058
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       800
  5 Reallocated_Sector_Ct   0x0033   199   199   140    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   077   077   000    Old_age   Always       -       17185
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       319
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       274
193 Load_Cycle_Count        0x0032   150   150   000    Old_age   Always       -       150604
194 Temperature_Celsius     0x0022   105   100   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     16926         -


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
root@titanium:~# smartctl -a /dev/sdd1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD10EARS-22Y5B1
Serial Number:    WD-WCAV5F290802
LU WWN Device Id: 5 0014ee 2af7a5997
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:32:29 2013 PDT
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
data collection:                (19380) seconds.
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
recommended polling time:        ( 223) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3031) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   136   127   021    Pre-fail  Always       -       6183
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       800
  5 Reallocated_Sector_Ct   0x0033   199   199   140    Pre-fail  Always       -       6
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   077   077   000    Old_age   Always       -       17197
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       319
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       273
193 Load_Cycle_Count        0x0032   150   150   000    Old_age   Always       -       151202
194 Temperature_Celsius     0x0022   105   098   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     16937         -


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
root@titanium:~# smartctl -a /dev/sde1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green
Device Model:     WDC WD10EAVS-00D7B1
Serial Number:    WD-WCAU46593233
LU WWN Device Id: 5 0014ee 2026b06cc
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:33:10 2013 PDT
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
data collection:                (22800) seconds.
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
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   173   159   021    Pre-fail  Always       -       6308
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       876
  5 Reallocated_Sector_Ct   0x0033   199   199   140    Pre-fail  Always       -       6
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   076   076   000    Old_age   Always       -       17626
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       128
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       15
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       876
194 Temperature_Celsius     0x0022   108   095   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   198   198   000    Old_age   Always       -       2
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     17366         -


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
root@titanium:~# smartctl -a /dev/sdf1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green
Device Model:     WDC WD10EADS-00L5B1
Serial Number:    WD-WCAU4D334784
LU WWN Device Id: 5 0014ee 2ae0cbaa1
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:33:37 2013 PDT
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
data collection:                (23400) seconds.
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
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   173   160   021    Pre-fail  Always       -       6316
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       652
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   071   071   000    Old_age   Always       -       21529
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       396
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       62
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       652
194 Temperature_Celsius     0x0022   111   101   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     21270         -
# 2  Extended offline    Completed without error       00%      2379         -


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
root@titanium:~# smartctl -a /dev/sdg1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green
Device Model:     WDC WD10EADS-00L5B1
Serial Number:    WD-WCAU4D297804
LU WWN Device Id: 5 0014ee 2ae0cb99f
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:34:02 2013 PDT
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
data collection:                (22800) seconds.
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
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   172   160   021    Pre-fail  Always       -       6391
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       726
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   071   071   000    Old_age   Always       -       21634
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       398
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       53
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       726
194 Temperature_Celsius     0x0022   111   103   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     21375         -
# 2  Extended offline    Completed without error       00%      2410         -


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
root@titanium:~# smartctl -a /dev/sdh1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green
Device Model:     WDC WD10EADS-00M2B0
Serial Number:    WD-WCAV53419140
LU WWN Device Id: 5 0014ee 258e11b4c
Firmware Version: 01.00A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:34:17 2013 PDT
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
data collection:                (19980) seconds.
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
recommended polling time:        ( 230) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3037) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   120   107   021    Pre-fail  Always       -       6991
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       846
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   071   071   000    Old_age   Always       -       21353
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       389
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       340
193 Load_Cycle_Count        0x0032   149   149   000    Old_age   Always       -       154470
194 Temperature_Celsius     0x0022   106   101   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     21096         -
# 2  Extended offline    Completed without error       00%      2331         -
# 3  Extended offline    Aborted by host               90%      2327         -


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
root@titanium:~# smartctl -a /dev/sdi1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green
Device Model:     WDC WD10EADS-00M2B0
Serial Number:    WD-WCAV52946996
LU WWN Device Id: 5 0014ee 258e10a84
Firmware Version: 01.00A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:34:30 2013 PDT
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
data collection:                (19980) seconds.
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
recommended polling time:        ( 230) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   176   176   051    Pre-fail  Always       -       7191856
  3 Spin_Up_Time            0x0027   120   111   021    Pre-fail  Always       -       6966
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       811
  5 Reallocated_Sector_Ct   0x0033   041   041   140    Pre-fail  Always   FAILING_NOW 1265
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   071   071   000    Old_age   Always       -       21236
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       395
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       347
193 Load_Cycle_Count        0x0032   155   155   000    Old_age   Always       -       136067
194 Temperature_Celsius     0x0022   106   098   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       1265
197 Current_Pending_Sector  0x0032   200   197   000    Old_age   Always       -       23
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   182   001   000    Old_age   Offline      -       3633


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%     20976         -
# 2  Extended offline    Completed without error       00%      2331         -


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
root@titanium:~# smartctl -a /dev/sdj1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EFRX-68AX9N0
Serial Number:    WD-WMC301024475
LU WWN Device Id: 5 0014ee 003864722
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:34:50 2013 PDT
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
data collection:                (26940) seconds.
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
  3 Spin_Up_Time            0x0027   175   172   021    Pre-fail  Always       -       4250
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       23
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       5316
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       22
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       21
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1
194 Temperature_Celsius     0x0022   111   106   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      5057         -


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
root@titanium:~# smartctl -a /dev/sdk1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WMAZA8549760
LU WWN Device Id: 5 0014ee 25c30c6cd
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:35:03 2013 PDT
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
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   180   170   021    Pre-fail  Always       -       6000
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       25
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       5314
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       22
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       21
193 Load_Cycle_Count        0x0032   162   162   000    Old_age   Always       -       116635
194 Temperature_Celsius     0x0022   115   108   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       1


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      5057         -


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
root@titanium:~# smartctl -a /dev/sdl1
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-53-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EFRX-68AX9N0
Serial Number:    WD-WMC301401502
LU WWN Device Id: 5 0014ee 058df67ed
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Sep 26 21:35:15 2013 PDT
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
data collection:                (27540) seconds.
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
  1 Raw_Read_Error_Rate     0x002f   100   253   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   176   175   021    Pre-fail  Always       -       4200
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       8
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       268
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       8
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       7
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   116   109   000    Old_age   Always       -       31
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

'sdi' is the failed drive, and 'sdl' is the brand new one.  'sdk' is the one that got kicked off the RAID array.

---

### Post by CharlesA on 2013-09-27
sdi is definitely toast. sdl looks ok as does sdk, at least according to the smart data.

As far as the spares number goes, check [this]("http://unix.stackexchange.com/questions/88654/what-does-mdadms-spare-number-mean") out.

I would replace the failed drive and let it rebuild, but I don't know if you need to wait for the reshape to complete or cancel it and rebuild the array first.

EDIT: Oh yeah, and bumped this over to Server Platforms. :)

---

### Post by ryydRnF on 2013-09-27
Well unless I want to wait about a year for the reshape to finish ;).  I'll wait until tomorrow to see if anyone else responds, then I'll check out that link and possibly replace the failed drive.  Would mdadm even rebuild the array with 3 drives down?  I feel like it would throw an error and refuse to.

---

### Post by CharlesA on 2013-09-27
> **ryydRnF said:**
> Well unless I want to wait about a year for the reshape to finish ;).  I'll wait until tomorrow to see if anyone else responds, then I'll check out that link and possibly replace the failed drive.  Would mdadm even rebuild the array with 3 drives down?  I feel like it would throw an error and refuse to.

Well, I think the two spares are the drives being used for the parity, so they aren't really "down." That means you only have 1 failed drive. Are you able to copy data off the array?

---

### Post by rubylaser on 2013-09-27
I'm sorry you are going through this. A failed reshape can be a very scary thing. Did you happen to create a backup file when you did your reshape the first time?  The following is a small VBox example I just did to demonstrate this for you.  I will be reshaping from a (4) disk RAID5 to a (5) disk RAID6.  In this example, I restarted the machine in the middle of the reshape.

**Current (4) disk RAID5**
```
root@mdadm-test:~# cat /proc/mdstat Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[4] sdc1[1] sdb1[0] sdd1[3]
      3136512 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
```
[B]During Reshape to RAID6
[/B]The status after reboot is active, degraded, not started. This is a non-functioning array at this point.
```

root@mdadm-test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Sep 27 10:22:06 2013
     Raid Level : raid6
  Used Dev Size : 1045504 (1021.17 MiB 1070.60 MB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent


    Update Time : Fri Sep 27 11:03:10 2013
          State : active, degraded, Not Started 
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1


         Layout : left-symmetric-6
     Chunk Size : 512K


     New Layout : left-symmetric


           Name : mdadm-test:0
           UUID : 340fff52:9d7eb433:3a0fba58:d4aad252
         Events : 1134


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1
       4       8       65        3      active sync   /dev/sde1
       5       8       81        4      spare rebuilding   /dev/sdf1

```

If I stop the running /dev/md0, and use the backup file to get it working...
```
mdadm -S /dev/md0
```
```
mdadm --assemble /dev/md0 /dev/sd[bcdef]1 --backup-file=/md0.backup
```
Everything works again...
```
root@mdadm-test:~# mdadm -D /dev/md0/dev/md0:
        Version : 1.2
  Creation Time : Fri Sep 27 10:22:06 2013
     Raid Level : raid6
     Array Size : 3136512 (2.99 GiB 3.21 GB)
  Used Dev Size : 1045504 (1021.17 MiB 1070.60 MB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent


    Update Time : Fri Sep 27 10:47:36 2013
          State : clean 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : mdadm-test:0
           UUID : 340fff52:9d7eb433:3a0fba58:d4aad252
         Events : 526


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1
       4       8       65        3      active sync   /dev/sde1
       5       8       81        4      active sync   /dev/sdf1
```

If you don't have a backup-file, you can try to pass in the --invalid-backup option instead as a last resort.
```
mdadm --assemble /dev/md0 /dev/sd[bcdef]1 --backup-file=fake --invalid-backup
```
In this case, you can see that it still managed to re-assemble the array correctly.
```

root@mdadm-test:~# mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Sep 27 10:22:06 2013
     Raid Level : raid6
     Array Size : 3136512 (2.99 GiB 3.21 GB)
  Used Dev Size : 1045504 (1021.17 MiB 1070.60 MB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent


    Update Time : Fri Sep 27 11:17:14 2013
          State : clean 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : mdadm-test:0
           UUID : 340fff52:9d7eb433:3a0fba58:d4aad252
         Events : 1560


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1
       4       8       65        3      active sync   /dev/sde1
       5       8       81        4      active sync   /dev/sdf1

```

Good luck and I hope this helps you out!

For future reference, setting up email alerts and SMART monitoring (and testing) your disks can really reduce the chance that something like this can happen again.

**Complete Sidebar:** Almost all home users that have 2TB+ storage are using it primarily to store movies, tv shows, music, pictures, home movies, etc.  In this case, SnapRAID + a disk pooling solution like AUFS can be a great solution.  You never run the risk of losing your whole array like with traditional hardware or software RAID, and it has the added benefit of checksumming your data to fix silent corruption.  I have used many various hardware and software RAID solutions over the years, and at this point, I am convinced that for almost all home users, using something like SnapRAID is the best solution to prevent situations like this.  I have links in my signature for both mdadm and SnapRAID that cover all of these topics.

---

### Post by ryydRnF on 2013-09-28
CharlesA -- Here's what happens when I try to mount the array:

```
root@titanium:~# mount /dev/md0 /media/storagemount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
root@titanium:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.91
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
     Array Size : 7814079488 (7452.09 GiB 8001.62 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0
    Persistence : Superblock is persistent


    Update Time : Sat Sep 28 13:07:33 2013
          State : clean, degraded, reshaping
 Active Devices : 9
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 2


         Layout : left-symmetric
     Chunk Size : 64K


 Reshape Status : 79% complete
  Delta Devices : 1, (10->11)


           UUID : e7db05b0:4a9008b8:98883325:0d269d95
         Events : 0.110351


    Number   Major   Minor   RaidDevice State
       0       8      113        0      active sync   /dev/sdh1
       1       8      129        1      active sync   /dev/sdi1
       2       8       33        2      active sync   /dev/sdc1
       3       8       97        3      active sync   /dev/sdg1
       4       8       49        4      active sync   /dev/sdd1
       5       8       81        5      active sync   /dev/sdf1
       6       8       17        6      active sync   /dev/sdb1
       7       8       65        7      active sync   /dev/sde1
       8       0        0        8      removed
       9       8      145        9      active sync   /dev/sdj1
      10       0        0       10      removed


      11       8      161        -      spare   /dev/sdk1
      12       8      177        -      spare   /dev/sdl1
```

```
root@titanium:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdh1[0] sdk1[11](S) sdl1[12](S) sdj1[9] sde1[7] sdb1[6] sdf1[5] sdd1[4] sdg1[3] sdc1[2] sdi1[1]
      7814079488 blocks super 0.91 level 6, 64k chunk, algorithm 2 [11/9] [UUUUUUUU_U_]
      [===============>.....]  reshape = 79.5% (777467328/976759936) finish=6438.8min speed=515K/sec


unused devices: <none>
```

It shows 'sdi' as fine, but it will fail shortly, that I can promise.

[COLOR=#000000]rubylaser, thanks for that info.  I'll definitely look into snapRAID.  I always considered ZFS (which this sort of sounds like) as a filesystem, but I'm a fan of ubuntu and I know running ZFS on top of ubuntu isn't the fastest thing in the world.

As per your other point, no, no backup was made.  Now I know that that is possible, so I will definitely be doing this every time.  And I do currently have email monitoring of the raid array and SMART status going.[/COLOR]

---

### Post by CharlesA on 2013-09-28
If it keeps up the reshape rate, it will complete in 4ish days. That's still a long time for it to sit there with a potentially bad drive. Can you cancel the reshape and just replace the failing drive and have it rebuild it, then reshape it after?

---

### Post by ryydRnF on 2013-09-28
Could you point me to the command to cancel the reshape?

So the steps would be, mark the failing drive as failed, remove it from the array, replace it physically, format new drive, and start the array again.  At that point, you're thinking it should rebuild using the new drive, then continue reshaping to the other 2 drives after that?

---

### Post by CharlesA on 2013-09-28
> **ryydRnF said:**
> Could you point me to the command to cancel the reshape?

So the steps would be, mark the failing drive as failed, remove it from the array, replace it physically, format new drive, and start the array again.  At that point, you're thinking it should rebuild using the new drive, then continue reshaping to the other 2 drives after that?

I found something mentioning mdadm --stop, but I don't know if that will stop the entire array or what.

My idea was to stop the reshape and swap the bad drive out - rebuild/resync the array then reshape it again.

Does that make sense?

---

### Post by ryydRnF on 2013-09-28
Yeah, mdadm --S /dev/md0 will stop the array.  I didn't know if there was another specific command to simply stop rebuilding.  I will have to mark the drive as failed and remove it from the array before I stop the array though.  I'll try this all later or tomorrow morning and see how things work out.

---

### Post by CharlesA on 2013-09-28
Good luck!

---

### Post by SaturnusDJ on 2013-09-29
Maybe one of the disks (the failing one?) is slowing all others down. The hdparm program might give an indication:
```
hdparm -tT /dev/sda
```
etc.

What could help in such a case, is copying all data from the failing disk to a new healthy disk and continue from there (I'm not sure what happens when you cancel the reshape/resync/recover.)
The right tool to do that is ddrescue.

---

### Post by ryydRnF on 2013-09-29
Thanks for all of your suggestions so far everyone!  Funny thing...I woke up this morning, and the array was just about finished reshaping.  Go figure, right?  The drive 'sdi' is still failing, but I came back from being out all day and the array is now clean, active, and rebuilding to the other two drives:

```
Every 2.0s: cat /proc/mdstat                                                                      Sun Sep 29 16:56:42 2013

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdh1[0] sdk1[11] sdl1[12] sdj1[9] sde1[7] sdb1[6] sdf1[5] sdd1[4] sdg1[3] sdc1[2] sdi1[1]
      8790839424 blocks level 6, 64k chunk, algorithm 2 [11/9] [UUUUUUUU_U_]
      [>....................]  recovery =  4.1% (40822148/976759936) finish=1234.2min speed=12638K/sec


unused devices: <none>
```

Still won't mount though...

---

### Post by CharlesA on 2013-09-29
Wait for it to rebuild and see if it will mount.

---

### Post by ryydRnF on 2013-10-01
I've changed out the bad drive to a new good one and it recovered!  Hooray.

Same problem still around though, that the drive won't mount (same error).  Thoughts?

---

### Post by CharlesA on 2013-10-01
Aw crap. Have you run fsck on the md0 device?

---

### Post by ryydRnF on 2013-10-01
Hm.

```
root@titanium:~$ fsck /dev/md0fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Superblock has an invalid journal (inode 8).
Clear<y>?
```

Is this a good idea?

---

### Post by CharlesA on 2013-10-01
Uh. I wouldn't clear the journal, as it would revert the file system to ext2. Can you check to see if the other superblocks are ok?

Find the alternative superblocks:
```
sudo dumpe2fs /dev/md0 | grep -i superblock
```

[http://ubuntuforums.org/showthread.php?t=1245536](http://ubuntuforums.org/showthread.php?t=1245536)

---

### Post by ryydRnF on 2013-10-01
```
root@titanium:~# dumpe2fs /dev/md0 | grep -i superblockdumpe2fs 1.42 (29-Nov-2011)
Journal superblock magic number invalid!
```

Blah.  I'm reading different things, and I'm worried that I'll do something that there is no coming back from.

---

### Post by CharlesA on 2013-10-01
That's what I'm worried about as well.

Anyway, can you post the complete output of:

```
sudo dumpe2fs /dev/md0
```

---

### Post by ryydRnF on 2013-10-02
```
root@titanium:~# dumpe2fs /dev/md0dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          /media/storage
Filesystem UUID:          62cde81c-d63e-4704-9ddd-df2ab00de9c7
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype n                                                                                        eeds_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nli                                                                                        nk extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              488382464
Block count:              1953519872
Reserved block count:     97659026
Free blocks:              178896900
Free inodes:              487815566
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      558
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              55567
Flex block group size:    16
Filesystem created:       Sun Mar 21 22:39:55 2010
Last mount time:          Mon Sep 16 20:20:46 2013
Last write time:          Mon Sep 16 20:20:46 2013
Mount count:              19
Maximum mount count:      38
Last checked:             Sun Feb 17 17:34:27 2013
Check interval:           15552000 (6 months)
Next check after:         Fri Aug 16 18:34:27 2013
Lifetime writes:          4882 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      5908a3b2-1720-4998-99c9-b0857b46c012
Journal backup:           inode blocks
Journal superblock magic number invalid!
```

I was reading that there might be a possibility if I reassemble the array simply using --assemble --scan, then it might work?  Maybe the array is simply out of order, but I would suspect that if that were the case, there would be some sort of superblock existing.

---

### Post by CharlesA on 2013-10-02
Not sure. You could try reassembling it, but I don't know if that will work or not. I don't have access to the server I run mdadm on, so I can't verify the output of dump2fs.

---

### Post by ryydRnF on 2013-10-02
I dug up an old email that contained a /proc/mdstat reading showing the following:

```
[FONT=arial]md0 : active raid5 sdb1[8](F) sde1[9](F) sdd1[10](F) sdh1[11](F) sdc1[12](F) sdf1[13](F) sdg1[14](F) sdi1[15](F)[/FONT]
```

I have added 3 drives since then, so I'm assuming that at least the first 8 are in this order (or should be).  Running --create shows this:

```
root@titanium:~# mdadm --create /dev/md0 --chunk=64000 --level=6 --raid-devices=11 /dev/sdb1 /dev/sde1 /dev/sdd1 /dev/sdh1 /dev/sdc1 /dev/sdf1 /dev/sdg1 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdh1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdf1 appears to contain an ext2fs file system
    size=-775855104K  mtime=Mon Sep 16 20:20:46 2013
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdi1 appears to contain an ext2fs file system
    size=151086680K  mtime=Sat May 31 13:57:45 1930
mdadm: /dev/sdi1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdj1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdk1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: /dev/sdl1 appears to contain an ext2fs file system
    size=-775855104K  mtime=Tue Oct 10 03:32:04 2028
mdadm: /dev/sdl1 appears to be part of a raid array:
    level=raid6 devices=11 ctime=Sun Mar 21 22:38:08 2010
mdadm: largest drive (/dev/sdb1) exceeds size (976618496K) by more than 1%
Continue creating array?
```

Seems like an...odd...output.  As per [http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using](http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using), it really shouldn't kill my data if I reorder the array incorrectly, just screw up the superblock.

---

### Post by CharlesA on 2013-10-02
Still sounds a bit risky to me. I'd backup the data by doing a clone of the drive via dd to external media before trying anything.

I realize that is probably a huge amount of data to backup, but better safe than sorry.

---

### Post by SaturnusDJ on 2013-10-02
Re-create is the right term here.

The best is indeed to do a full back-up before trying, it is however true that you won't lose data if you only change the order...but that means all other parameters need to be the same too (chunk, level, members, superblock version, etc).
Only thing is I miss here is why the order should be mixed up now.

---

### Post by rubylaser on 2013-10-02
You don't want to re-create the array without passing in the --assume-clean flag.  Without this, it will cause a resync and will [COLOR=#ff0000][SIZE=4]**_VERY likely kill your data_**[/SIZE][/COLOR].  What do the superblocks show on all of your disks?
```

mdadm -E /dev/sd[bcdefghijkl]1

```

---

### Post by SaturnusDJ on 2013-10-02
Ofcourse, how can I forget that flag...
I've seen cases that survived without, but I would never go without it indeed!

---

### Post by ryydRnF on 2013-10-02
Rubylaser:

```
> sudo mdadm -E /dev/sd[bcdefghijkl]1/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a37f - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     6       8       17        6      active sync   /dev/sdb1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a387 - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a39b - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     4       8       49        4      active sync   /dev/sdd1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a3b1 - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     7       8       65        7      active sync   /dev/sde1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdf1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a3b5 - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     1       8       81        1      active sync   /dev/sdf1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdg1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a3cd - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     5       8       97        5      active sync   /dev/sdg1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdh1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a3d9 - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     3       8      113        3      active sync   /dev/sdh1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdi1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a3e3 - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     0       8      129        0      active sync   /dev/sdi1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdj1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a405 - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     9       8      145        9      active sync   /dev/sdj1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdk1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a413 - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     8       8      161        8      active sync   /dev/sdk1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
/dev/sdl1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e7db05b0:4a9008b8:98883325:0d269d95
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5974a427 - correct
         Events : 116984


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this    10       8      177       10      active sync   /dev/sdl1


   0     0       8      129        0      active sync   /dev/sdi1
   1     1       8       81        1      active sync   /dev/sdf1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8       49        4      active sync   /dev/sdd1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8       17        6      active sync   /dev/sdb1
   7     7       8       65        7      active sync   /dev/sde1
   8     8       8      161        8      active sync   /dev/sdk1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      177       10      active sync   /dev/sdl1
```

I also do believe that my data is still in fact intact.  While I was rebuilding the first time (before the drive failed, and even after), I was able to mount and see data.  The only time I have not been able to is after rebuilding and recovering.

---

### Post by rubylaser on 2013-10-02
Based on the metadata from each of your disks, the event counters are exactly the same and the disk order identical (this is a good thing), you need to stop the running array, and re-assemble in the proper order.  Based on the metadata, the following should be the proper order.  Let me know how it goes.

```

mdadm -S /dev/md0
mdadm --assemble /dev/md0 /dev/sd[ifchdgbekjl]1

```

---

### Post by ryydRnF on 2013-10-02
```
sudo mdadm --assemble /dev/md0 /dev/sd[ifchdgbekjl]1
mdadm: /dev/md0 has been started with 11 drives.
```

```
sudo mdadm --detail /dev/md0/dev/md0:
        Version : 0.90
  Creation Time : Sun Mar 21 22:38:08 2010
     Raid Level : raid6
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 11
  Total Devices : 11
Preferred Minor : 0
    Persistence : Superblock is persistent


    Update Time : Tue Oct  1 22:27:29 2013
          State : clean 
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 64K


           UUID : e7db05b0:4a9008b8:98883325:0d269d95
         Events : 0.116984


    Number   Major   Minor   RaidDevice State
       0       8      129        0      active sync   /dev/sdi1
       1       8       81        1      active sync   /dev/sdf1
       2       8       33        2      active sync   /dev/sdc1
       3       8      113        3      active sync   /dev/sdh1
       4       8       49        4      active sync   /dev/sdd1
       5       8       97        5      active sync   /dev/sdg1
       6       8       17        6      active sync   /dev/sdb1
       7       8       65        7      active sync   /dev/sde1
       8       8      161        8      active sync   /dev/sdk1
       9       8      145        9      active sync   /dev/sdj1
      10       8      177       10      active sync   /dev/sdl1
```

```
sudo mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.
```

```
sudo mount /dev/md0 /media/storagemount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Bah!

---

### Post by rubylaser on 2013-10-02
The md device will never have a superblock on it (/dev/md0).  The Superblocks reside on the individual disks (i.e. /dev/sd[bcd]1 etc).  That's what you viewed earlier when I had you run mdadm -E on each disk. Your array is now assembled in the correct order per their metadata, but it appears that your filesystem is corrupt.  Try looking for alternate filesystem superblock on your array.

```

[COLOR=#111111][FONT=Consolas]dumpe2fs /dev/md0 | grep superblock[/FONT][/COLOR]

```

---

### Post by ryydRnF on 2013-10-02
Ah, yes...silly me.  It's been a long week.

```
sudo dumpe2fs /dev/md0 | sudo grep superblockdumpe2fs 1.42 (29-Nov-2011)
Journal superblock magic number invalid!
```

---

### Post by CharlesA on 2013-10-03
Not really sure what else to do with this. That looks like the same output you got before.

I hooked up my backup server and ran dumpe2fs on it and got this:

```
root@Loki:~# dumpe2fs /dev/md0 | grep superblock
dumpe2fs 1.42.5 (29-Jul-2012)
  Primary superblock at 0, Group descriptors at 1-233
  Backup superblock at 32768, Group descriptors at 32769-33001
  Backup superblock at 98304, Group descriptors at 98305-98537
  Backup superblock at 163840, Group descriptors at 163841-164073
  Backup superblock at 229376, Group descriptors at 229377-229609
  Backup superblock at 294912, Group descriptors at 294913-295145
  Backup superblock at 819200, Group descriptors at 819201-819433
  Backup superblock at 884736, Group descriptors at 884737-884969
  Backup superblock at 1605632, Group descriptors at 1605633-1605865
  Backup superblock at 2654208, Group descriptors at 2654209-2654441
  Backup superblock at 4096000, Group descriptors at 4096001-4096233
  Backup superblock at 7962624, Group descriptors at 7962625-7962857
  Backup superblock at 11239424, Group descriptors at 11239425-11239657
  Backup superblock at 20480000, Group descriptors at 20480001-20480233
  Backup superblock at 23887872, Group descriptors at 23887873-23888105
  Backup superblock at 71663616, Group descriptors at 71663617-71663849
  Backup superblock at 78675968, Group descriptors at 78675969-78676201
  Backup superblock at 102400000, Group descriptors at 102400001-102400233
  Backup superblock at 214990848, Group descriptors at 214990849-214991081
  Backup superblock at 512000000, Group descriptors at 512000001-512000233
  Backup superblock at 550731776, Group descriptors at 550731777-550732009
  Backup superblock at 644972544, Group descriptors at 644972545-644972777

```

:(

I kinda wonder if the only way to fix the file system is to clear the journal?

---

### Post by rubylaser on 2013-10-03
> **CharlesA said:**
> Not really sure what else to do with this. That looks like the same output you got before.

I hooked up my backup server and ran dumpe2fs on it and got this:

[code]

:(

I kinda wonder if the only way to fix the file system is to clear the journal?

You can try to clear the journal, and see if that helps.  Here is a [thread]("http://ubuntuforums.org/showthread.php?t=2023481") that cover the same error message.  Unfortunately, even if this works, you will likely end up with a bunch of files in your lost+found folder that need to be moved back to their correct location.  Please keep us posted on your progress.

---

