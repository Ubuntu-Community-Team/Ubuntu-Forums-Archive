---
title: "Online HDD surface update in running RIAD systems"
date: 2013-03-24
forum: Server Platforms
---

### Post by redscorp on 2013-03-24
Hi Ladies and Gentleman,

I've got some problems this month with my home SW RAID enabled NAS box. Two HDDs had started to drop warning massages about sector access timeouts. I didn't took it seriously at beginning, but after some time one of HDD was dropped out from RAID array with failure. After reading SMART information it showed some pending sectors but no relocation of sectors.

I've removed this failed HDD out from array, run some self-tests on it. This showed some damaged regions of surface. I've used 'dd' to overwrite disk surface completely and magically all pending sectors are gone and no relocation took place. Now self-test runs perfectly without errors. So, I assume it was weak magnetic condition of 'cold data' in this disk. Now I add this HDD to array and it runs flawlessly after RAID resync.

The same problem happened to his brother few days later and after repetition of steps mentioned above it also runs well.

Now my question is - how can I update HDD magnetic surface online (on running system) without data loss? Ideally as a 'cron' job...

Basically, I can imagine me few ways to do this:

1. I remove a HDD from RAID array, wipe it with 'dd' and put it back to array. This is a very dangerous way because mentioned array stays unprotected for a very long time.

2. Do the same as in 1. but using spare HDD in the magnetic surface update procedure. It reduces unprotected time but doesn't solve it completely.

3. Somehow I do online update of HDD magnetic surface without erasing data with 'dd', without stopping array and without putting the array in dangerous state.

How to do the 3. ? How can I update HDD magnetic surface online?

Thanks for your suggestions in advance!

--
WBR,
redscorp

---

### Post by tgalati4 on 2013-03-24
You shouldn't have to "update the magnetic surface" of a properly working drive.  How old are these drives?  Perhaps they are not broken in yet.  Like new shoes, disk drives need a break-in period before storing critical data.  How you perform this is up to you.  If these drives are a few years old, then perhaps they are wearing out.

If you are experiencing data corruption on the drives, then perhaps using the zfs filesystem will help to determine such corruption, as that is one of the features of zfs.  It computes and stores the checksums of each file and compares them as they are read from the disk.  Discrepancies are noted and the file system can be "scrubbed" using a cronjob as part of a maintanence program.

What are the SMART parameters of the drives?

---

### Post by redscorp on 2013-03-24
Ok, these two mentioned HDDs (WD30EZRX) where bought in July 2011.

Mentioned 'update' was performed with a help of 'dd'. Something like 'dd if=/dev/zero of=/dev/sde bs=65536' ... It really does fix bad block problem. You may see in a history of self-tests posted below.

ZFS is not an option for me. These HDDs are running as a part of RAID6 array. Above RAID I have ext4 FS. The ideal solution would be to update disk surface under RAID without corrupting RAID data structures.

```
uzzzer@AGVault:~$ sudo smartctl -a /dev/sde
[sudo] password for uzzzer:
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-39-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-00MMMB0
Serial Number:    WD-WCAWZ0814047
LU WWN Device Id: 5 0014ee 2b0a4c98a
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Mar 24 21:33:43 2013 CET
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
data collection:                (51180) seconds.
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
  3 Spin_Up_Time            0x0027   147   145   021    Pre-fail  Always       -       9608
  4 Start_Stop_Count        0x0032   091   091   000    Old_age   Always       -       9934
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   082   082   000    Old_age   Always       -       13773
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       127
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       63
193 Load_Cycle_Count        0x0032   140   140   000    Old_age   Always       -       181655
194 Temperature_Celsius     0x0022   114   109   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     13589         -
# 2  Short offline       Completed without error       00%     13521         -
# 3  Extended offline    Completed without error       00%     13422         -
# 4  Extended offline    Completed: read failure       90%     13355         132284016
# 5  Extended offline    Completed: read failure       90%     13355         132284016
# 6  Short offline       Completed: read failure       90%     13308         132284016
# 7  Extended offline    Completed: read failure       90%     13308         132284016
# 8  Extended offline    Completed: read failure       90%     13308         132284017
# 9  Extended offline    Completed: read failure       90%     13308         132284016
#10  Extended offline    Completed: read failure       90%     13308         4122787848
#11  Extended offline    Completed: read failure       90%     13308         4122787848
#12  Extended offline    Completed: read failure       90%     13301         4122787849
9 of 9 failed self-tests are outdated by newer successful extended offline self-test # 1

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

