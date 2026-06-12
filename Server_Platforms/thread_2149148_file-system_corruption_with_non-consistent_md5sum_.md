---
title: "file-system corruption with non-consistent md5sum results."
date: 2013-05-27
forum: Server Platforms
---

### Post by danic on 2013-05-27
I am having a hard time figuring why I am having silent file corruption. Most noticeable on large files (1GB+ not exactly sure). For example zip files will become corrupt (IMO, very easy to test for corruption). I first notice the issue when I was coping files from my Windows desktop to a samba share. I ruled out samba from being the culprit because copying the files locally on the server can produce corrupt files. 
My server setup is Ubuntu 10.04 running 3.0.0-32-server kernel. It has two mdadm arrays. RAID1 with two drives and a RAID5 with 3 drives. Both arrays are formatted ext4. RAID1 array is my root folder (including home directories) and RAID5 array is mounted to /share/s. My test.zip file is 2.6GB zip file with many files inside. I start in my home folder and do the following;
```

cp test.zip test.zip2
cp test.zip /share/s
cp test.zip2 /share/s

```
that all goes well, but here comes my confusion
```
jason@server1:~$ md5sum test.zip* /share/s/test.zip*
75a8334c93b0e988cc748003b7ad0924  test.zip
6898a1d1beec92e7a6883cbd91953cee  test.zip2
c8494761a375985cf77ecffb40f66ae9  /share/s/test.zip
cd1d53ff4c45024952e4d3bd67fbee12  /share/s/test.zip2

```
Ack! every zip had different md5sum. and if I use 'unzip -t' to test each zip file the three copies will fail.
it gets worse. I'll run the md5sum again.
```
jason@server1:~$ md5sum test.zip* /share/s/test.zip*
5af99f5b34e51f4f5de8fb52e91eae40  test.zip
6898a1d1beec92e7a6883cbd91953cee  test.zip2
885274400413dfe8e14a66dde215972a  /share/s/test.zip
f361a9229c38a1ab78d1dff5fbc38e16  /share/s/test.zip2

```
Uh oh. I get totally different md5's. If I keep running md5sum over and over sometimes I a pair of matching sums, but never all 4. 
I've ran fsck.ext4 on both filesystems. Forced data check on both mdadm arrays. I've passed 8 hours of memtest. All hard drives are plugged into ASUS P5Q-E (ICH10R chipset) motherboard with AHCI on. All drives pass SMART.

I'm running out of ideas and my understanding of what is going on is non-existent. Can any provide some help or incite? 

Thanks.

---

### Post by SaturnusDJ on 2013-05-28
First thing to test with this kind of corruption is the system memory. With MemTest86 for example.
Other possibilities are the controller of the disks and/or the cables.

Maybe some information can be found with:
```
smartctl -a /dev/sd...
```

---

### Post by danic on 2013-05-29
Well I've already tested the system with Memtest86+ in the past and did so again last night. 8 passes and no errors. I've been testing random files throughout my file server and been finding a lot of corrupt files. Sadly the backups are corrupt as well. I've tried different kernels, went back to non-backported kernel of 2.6.32-47-generic with no change. smartctl reveals no problems to me, but I might be missing something.
here is smartctl output of my two main drives in 
```
jason@server1:~$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3000GLFS-01F8U0
Serial Number:    WD-WXL608016095
Firmware Version: 03.03V01
User Capacity:    300,069,052,416 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed May 29 09:03:45 2013 PDT
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
data collection:                 (4860) seconds.
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
recommended polling time:        (  60) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   199   198   021    Pre-fail  Always       -       3025
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       29
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   045   045   000    Old_age   Always       -       40443
 10 Spin_Retry_Count        0x0012   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       29
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       14
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       29
194 Temperature_Celsius     0x0022   117   100   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     30308         -

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
jason@server1:~$ sudo smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3000GLFS-01F8U0
Serial Number:    WD-WXL608020653
Firmware Version: 03.03V01
User Capacity:    300,069,052,416 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed May 29 09:04:30 2013 PDT
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
data collection:                 (4980) seconds.
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
recommended polling time:        (  61) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   199   198   021    Pre-fail  Always       -       3050
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       30
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   045   045   000    Old_age   Always       -       40445
 10 Spin_Retry_Count        0x0012   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       30
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       14
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0022   119   100   000    Old_age   Always       -       28
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     30309         -

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

### Post by SaturnusDJ on 2013-05-29
Looks good but the tests are outdated. I recommend to test atleast once a week.

```
smartctl -t short /dev/sd..
```
(Long tests the full disk and takes a lot more time.)

The next suspect after this is the controller.

---

### Post by danic on 2013-05-29
Ok I ran Long SMART tests on all hard drives and two main drives are done.
```
jason@server1:~$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3000GLFS-01F8U0
Serial Number:    WD-WXL608016095
Firmware Version: 03.03V01
User Capacity:    300,069,052,416 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed May 29 12:45:43 2013 PDT
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
data collection:                 (4860) seconds.
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
recommended polling time:        (  60) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   199   198   021    Pre-fail  Always       -       3025
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       29
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   045   045   000    Old_age   Always       -       40447
 10 Spin_Retry_Count        0x0012   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       29
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       14
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       29
194 Temperature_Celsius     0x0022   115   100   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     40447         -
# 2  Extended offline    Completed without error       00%     30308         -

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
and
```
jason@server1:~$ sudo smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3000GLFS-01F8U0
Serial Number:    WD-WXL608020653
Firmware Version: 03.03V01
User Capacity:    300,069,052,416 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed May 29 12:46:25 2013 PDT
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
data collection:                 (4980) seconds.
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
recommended polling time:        (  61) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   199   198   021    Pre-fail  Always       -       3050
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       30
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   045   045   000    Old_age   Always       -       40448
 10 Spin_Retry_Count        0x0012   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       30
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       14
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0022   117   100   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     40448         -
# 2  Extended offline    Completed without error       00%     30309         -

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
I see no issues here.

Next you mention it could be the controller. All drives except 1 are connected to a *'Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller'* (name from lspci)
I also have a single 3TB drive just to hold workstation backups that is connected to *Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)*. This is extra two port controller on the motherboard.
I ran the 'unzip -t' and md5sum tests and it also failed. I'm now glad to know that some of my workstation backups are corrupt as well.

Is it worth buying a 8 port controller or time to dump the entire server besides hard drives and start over?

Thanks for the help

---

### Post by tgalati4 on 2013-05-30
40,000 hours is a lot.  Most consumer drives are rated to 50k hours for Mean Time to Failure (MBTF).  It's possible that your drives are failing in a subtle way that SMART is not capturing.  SMART only captures 2/3 of the failure causes.  1/3 are not captured but happen anyway.  

It's also possible that it's a RAID timing problem.  Take another single drive and try to write large files to it and check the md5sum.  It's possible that a timing error when striping the data to the drives goes undetected leaving corrupted files on the disk, yet not triggering a kernel message.  I presume that you checked *dmesg* and your /var/log files for errors.

---

### Post by socolasuadabao on 2013-05-30
Thanks for your tips guys[!]("http://www.chudu24.com")!

---

### Post by SaturnusDJ on 2013-05-30
That's a good point. Earlier this year, my previous setup started to tear apart while changing some things. They where 35k hours.

---

### Post by danic on 2013-05-30
> **tgalati4 said:**
> ....Take another single drive and try to write large files to it and check the md5sum.  It's possible that a timing error when striping the data to the drives goes undetected leaving corrupted files on the disk, yet not triggering a kernel message.  I presume that you checked *dmesg* and your /var/log files for errors.
I have two single drives in the server as well they show the same problem.
I've looked through dmesg and all the log files but I am no guru.
Here is my dmesg output

```
jason@server1:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-47-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #109-Ubuntu SMP Tue May 7 02:02:22 UTC 2013 (Ubuntu 2.6.32-47.109-generic 2.6.32.60+drm33.26)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-47-generic root=UUID=d3cbd641-c0b7-4c59-b73f-8f8d3431a0e8 ro nodmraid nomodeset
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 220000000 mask FF0000000 write-back
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff70 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009c400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  modified: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  modified: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff70000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff70000 page 4k
[    0.000000] kernel direct mapping tables up to cff70000 @ 10000-16000
[    0.000000] init_memory_mapping: 0000000100000000-0000000230000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0230000000 page 2M
[    0.000000] kernel direct mapping tables up to 230000000 @ 14000-1e000
[    0.000000] RAMDISK: 377f2000 - 37fef3e1
[    0.000000] ACPI: RSDP 00000000000fb460 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff70100 0005C (v01 A_M_I_ OEMXSDT  08000820 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff70290 000F4 (v03 A_M_I_ OEMFACP  08000820 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff70440 09675 (v01  A0986 A0986000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff7e000 00040
[    0.000000] ACPI: APIC 00000000cff70390 0006C (v01 A_M_I_ OEMAPIC  08000820 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff70400 0003C (v01 A_M_I_ OEMMCFG  08000820 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff7e040 00081 (v01 A_M_I_ AMI_OEM  08000820 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff79ac0 00038 (v01 A_M_I_ OEMHPET  08000820 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000cff79b00 000B0 (v01 A_M_I_ OEMOSFR  08000820 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff7eb20 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000230000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000230000000
[    0.000000]   NODE_DATA [0000000000019000 - 000000000001dfff]
[    0.000000]   bootmap [000000000001e000 -  0000000000063fff] pages 46
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0230000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a37a44]    TEXT DATA BSS ==> [0001000000 - 0001a37a44]
[    0.000000]   #3 [00377f2000 - 0037fef3e1]          RAMDISK ==> [00377f2000 - 0037fef3e1]
[    0.000000]   #4 [000009c400 - 0000100000]    BIOS reserved ==> [000009c400 - 0000100000]
[    0.000000]   #5 [0001a38000 - 0001a38280]              BRK ==> [0001a38000 - 0001a38280]
[    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #7 [0000014000 - 0000019000]          PGTABLE ==> [0000014000 - 0000019000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0007bfffff] PMD -> [ffff880028600000-ffff88002f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00230000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000cff70
[    0.000000]     0: 0x00100000 -> 0x00230000
[    0.000000] On node 0 totalpages: 2096892
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 111 pages reserved
[    0.000000]   DMA zone: 3813 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833448 pages, LIFO batch:31
[    0.000000]   Normal zone: 17024 pages used for memmap
[    0.000000]   Normal zone: 1228160 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff70000 - 00000000cff7e000
[    0.000000] PM: Registered nosave memory: 00000000cff7e000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91608 r8192 d23080 u524288
[    0.000000] pcpu-alloc: s91608 r8192 d23080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2065421
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-47-generic root=UUID=d3cbd641-c0b7-4c59-b73f-8f8d3431a0e8 ro nodmraid nomodeset
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 8185408k/9175040k available (5443k kernel code, 787472k absent, 202160k reserved, 2983k data, 884k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 83886080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2999.374 MHz processor.
[    0.000005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5998.74 BogoMIPS (lpj=29993740)
[    0.000081] Security Framework initialized
[    0.000123] AppArmor: AppArmor initialized
[    0.010412] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.013590] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.015093] Mount-cache hash table entries: 256
[    0.015239] Initializing cgroup subsys ns
[    0.015270] Initializing cgroup subsys cpuacct
[    0.015300] Initializing cgroup subsys memory
[    0.015332] Initializing cgroup subsys devices
[    0.015361] Initializing cgroup subsys freezer
[    0.015389] Initializing cgroup subsys net_cls
[    0.015434] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.015485] CPU: L2 cache: 6144K
[    0.015513] CPU 0/0x0 -> Node 0
[    0.015541] CPU: Physical Processor ID: 0
[    0.015569] CPU: Processor Core ID: 0
[    0.015598] mce: CPU supports 6 MCE banks
[    0.015631] CPU0: Thermal monitoring enabled (TM2)
[    0.015662] using mwait in idle threads.
[    0.015689] Performance Events: Core2 events, Intel PMU driver.
[    0.015766] ... version:                2
[    0.015794] ... bit width:              40
[    0.015821] ... generic registers:      2
[    0.015849] ... value mask:             000000ffffffffff
[    0.015877] ... max period:             000000007fffffff
[    0.015905] ... fixed-purpose events:   3
[    0.015933] ... event mask:             0000000700000003
[    0.017929] ACPI: Core revision 20090903
[    0.028814] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028845] ftrace: allocating 22598 entries in 89 pages
[    0.030038] Setting APIC routing to flat
[    0.030362] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.136278] CPU0: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 0a
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.290095] CPU1: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 0a
[    0.290357] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300020] Brought up 2 CPUs
[    0.300049] Total of 2 processors activated (11998.03 BogoMIPS).
[    0.302021] CPU0 attaching sched-domain:
[    0.302024]  domain 0: span 0-1 level MC
[    0.302026]   groups: 0 1
[    0.302030] CPU1 attaching sched-domain:
[    0.302031]  domain 0: span 0-1 level MC
[    0.302033]   groups: 1 0
[    0.302083] devtmpfs: initialized
[    0.302083] regulator: core version 0.5
[    0.302083] Time: 15:18:19  Date: 05/29/13
[    0.302083] NET: Registered protocol family 16
[    0.302083] Trying to unpack rootfs image as initramfs...
[    0.302083] ACPI: bus type pci registered
[    0.302083] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.302083] PCI: Not using MMCONFIG.
[    0.302083] PCI: Using configuration type 1 for base access
[    0.310046] bio: create slab <bio-0> at 0
[    0.310369] ACPI: EC: Look up EC in DSDT
[    0.312246] ACPI: Executed 1 blocks of module-level executable AML code
[    0.321121] ACPI: Interpreter enabled
[    0.321151] ACPI: (supports S0 S1 S3 S4 S5)
[    0.321309] ACPI: Using IOAPIC for interrupt routing
[    0.321377] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.323390] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.329441] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.335239] ACPI: No dock devices found.
[    0.335358] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.335474] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.335504] pci 0000:00:01.0: PME# disabled
[    0.335586] pci 0000:00:1a.0: reg 20 io port: [0xa800-0xa81f]
[    0.335648] pci 0000:00:1a.1: reg 20 io port: [0xa880-0xa89f]
[    0.335715] pci 0000:00:1a.2: reg 20 io port: [0xac00-0xac1f]
[    0.335779] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe7ffc00-0xfe7fffff]
[    0.335839] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.335871] pci 0000:00:1a.7: PME# disabled
[    0.335960] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.335992] pci 0000:00:1c.0: PME# disabled
[    0.336082] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.336113] pci 0000:00:1c.4: PME# disabled
[    0.336202] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.336233] pci 0000:00:1c.5: PME# disabled
[    0.336303] pci 0000:00:1d.0: reg 20 io port: [0xa080-0xa09f]
[    0.336366] pci 0000:00:1d.1: reg 20 io port: [0xa400-0xa41f]
[    0.336428] pci 0000:00:1d.2: reg 20 io port: [0xa480-0xa49f]
[    0.336495] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe7ff800-0xfe7ffbff]
[    0.336554] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.336585] pci 0000:00:1d.7: PME# disabled
[    0.336722] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.336757] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 001f)
[    0.336848] pci 0000:00:1f.2: reg 10 io port: [0x9c00-0x9c07]
[    0.336852] pci 0000:00:1f.2: reg 14 io port: [0x9880-0x9883]
[    0.336856] pci 0000:00:1f.2: reg 18 io port: [0x9800-0x9807]
[    0.336860] pci 0000:00:1f.2: reg 1c io port: [0x9480-0x9483]
[    0.336864] pci 0000:00:1f.2: reg 20 io port: [0x9400-0x941f]
[    0.336869] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe7fe800-0xfe7fefff]
[    0.336903] pci 0000:00:1f.2: PME# supported from D3hot
[    0.336935] pci 0000:00:1f.2: PME# disabled
[    0.336984] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe7ff400-0xfe7ff4ff]
[    0.336994] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.337032] pci 0000:01:00.0: reg 10 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.337039] pci 0000:01:00.0: reg 18 64bit mmio: [0xfe8e0000-0xfe8effff]
[    0.337044] pci 0000:01:00.0: reg 20 io port: [0xb000-0xb0ff]
[    0.337050] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfe8c0000-0xfe8dffff]
[    0.337076] pci 0000:01:00.0: supports D1 D2
[    0.337102] pci 0000:01:00.1: reg 10 64bit mmio: [0xfe8fc000-0xfe8fffff]
[    0.337142] pci 0000:01:00.1: supports D1 D2
[    0.337178] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.337180] pci 0000:00:01.0: bridge 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.337182] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.337217] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.337255] pci 0000:03:00.0: reg 10 io port: [0xdc00-0xdc07]
[    0.337261] pci 0000:03:00.0: reg 14 io port: [0xd880-0xd883]
[    0.337268] pci 0000:03:00.0: reg 18 io port: [0xd800-0xd807]
[    0.337274] pci 0000:03:00.0: reg 1c io port: [0xd480-0xd483]
[    0.337281] pci 0000:03:00.0: reg 20 io port: [0xd400-0xd40f]
[    0.337288] pci 0000:03:00.0: reg 24 32bit mmio: [0xfeaffc00-0xfeafffff]
[    0.337341] pci 0000:03:00.0: supports D1
[    0.337342] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.337374] pci 0000:03:00.0: PME# disabled
[    0.337440] pci 0000:00:1c.4: bridge io port: [0xd000-0xdfff]
[    0.337443] pci 0000:00:1c.4: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.337497] pci 0000:02:00.0: reg 10 64bit mmio: [0xfe9fc000-0xfe9fffff]
[    0.337504] pci 0000:02:00.0: reg 18 io port: [0xc800-0xc8ff]
[    0.337526] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfe9c0000-0xfe9dffff]
[    0.337586] pci 0000:02:00.0: supports D1 D2
[    0.337588] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.337619] pci 0000:02:00.0: PME# disabled
[    0.337682] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.337685] pci 0000:00:1c.5: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.337715] pci 0000:05:00.0: reg 10 io port: [0xec00-0xec07]
[    0.337720] pci 0000:05:00.0: reg 14 io port: [0xe880-0xe883]
[    0.337726] pci 0000:05:00.0: reg 18 io port: [0xe800-0xe807]
[    0.337731] pci 0000:05:00.0: reg 1c io port: [0xe480-0xe483]
[    0.337736] pci 0000:05:00.0: reg 20 io port: [0xe400-0xe40f]
[    0.337742] pci 0000:05:00.0: reg 24 32bit mmio: [0xfebffc00-0xfebffdff]
[    0.337747] pci 0000:05:00.0: reg 30 32bit mmio pref: [0xfeb00000-0xfeb7ffff]
[    0.337770] pci 0000:05:00.0: supports D1 D2
[    0.337804] pci 0000:05:02.0: reg 10 32bit mmio: [0xfebf8000-0xfebfbfff]
[    0.337810] pci 0000:05:02.0: reg 14 io port: [0xe000-0xe0ff]
[    0.337831] pci 0000:05:02.0: reg 30 32bit mmio pref: [0xfebc0000-0xfebdffff]
[    0.337863] pci 0000:05:02.0: supports D1 D2
[    0.337864] pci 0000:05:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.337896] pci 0000:05:02.0: PME# disabled
[    0.337959] pci 0000:00:1e.0: transparent bridge
[    0.337989] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.337991] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.338013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.338115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.338157] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.338230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.338269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.338325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.349599] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.349987] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.350360] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.350747] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.351132] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.351566] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.351950] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.352385] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.352785] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.352821] vgaarb: loaded
[    0.352930] SCSI subsystem initialized
[    0.353448] libata version 3.00 loaded.
[    0.353448] usbcore: registered new interface driver usbfs
[    0.353448] usbcore: registered new interface driver hub
[    0.353448] usbcore: registered new device driver usb
[    0.353448] ACPI: WMI: Mapper loaded
[    0.353448] PCI: Using ACPI for IRQ routing
[    0.353469] NetLabel: Initializing
[    0.353498] NetLabel:  domain hash size = 128
[    0.353526] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.353564] NetLabel:  unlabeled traffic allowed by default
[    0.353618] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.353650] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.353795] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.360039] Switching to clocksource tsc
[    0.361319] AppArmor: AppArmor Filesystem Enabled
[    0.361357] pnp: PnP ACPI init
[    0.361391] ACPI: bus type pnp registered
[    0.363400] pnp: PnP ACPI: found 15 devices
[    0.363430] ACPI: ACPI bus type pnp unregistered
[    0.363465] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.363498] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.363530] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.363561] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.363590] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.363620] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.363650] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.363680] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.363710] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.363744] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
[    0.363776] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.363809] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.363841] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.363873] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.363904] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[    0.363935] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.363965] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[    0.368672] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.368703] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.368734] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.368765] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.368802] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.368833] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.368863] pci 0000:00:1c.0:   MEM window: 0xf0000000-0xf03fffff
[    0.368895] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.368932] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.368963] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.368995] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    0.369026] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0400000-0x000000f05fffff
[    0.369062] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.369092] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.369124] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    0.369155] pci 0000:00:1c.5:   PREFETCH window: 0x000000f0600000-0x000000f07fffff
[    0.369193] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.369224] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.369255] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.369287] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.369325]   alloc irq_desc for 16 on node -1
[    0.369327]   alloc kstat_irqs on node -1
[    0.369330] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.369364] pci 0000:00:01.0: setting latency timer to 64
[    0.369369] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.369400]   alloc irq_desc for 17 on node -1
[    0.369401]   alloc kstat_irqs on node -1
[    0.369403] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.369434] pci 0000:00:1c.0: setting latency timer to 64
[    0.369440] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.369473] pci 0000:00:1c.4: setting latency timer to 64
[    0.369479] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.369509] pci 0000:00:1c.5: setting latency timer to 64
[    0.369514] pci 0000:00:1e.0: setting latency timer to 64
[    0.369517] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.369519] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.369521] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.369522] pci_bus 0000:01: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.369524] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.369525] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
[    0.369527] pci_bus 0000:04: resource 1 mem: [0xf0000000-0xf03fffff]
[    0.369528] pci_bus 0000:04: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.369530] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.369532] pci_bus 0000:03: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.369533] pci_bus 0000:03: resource 2 pref mem [0xf0400000-0xf05fffff]
[    0.369535] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.369536] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.369538] pci_bus 0000:02: resource 2 pref mem [0xf0600000-0xf07fffff]
[    0.369540] pci_bus 0000:05: resource 0 io:  [0xe000-0xefff]
[    0.369541] pci_bus 0000:05: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.369543] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.369544] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.369571] NET: Registered protocol family 2
[    0.369781] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.370941] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.373944] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.374368] TCP: Hash tables configured (established 524288 bind 65536)
[    0.374398] TCP reno registered
[    0.374521] NET: Registered protocol family 1
[    0.374578] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.374622] pci 0000:00:1a.0: PCI INT A disabled
[    0.374654]   alloc irq_desc for 21 on node -1
[    0.374656]   alloc kstat_irqs on node -1
[    0.374662] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.374707] pci 0000:00:1a.1: PCI INT B disabled
[    0.374739]   alloc irq_desc for 18 on node -1
[    0.374740]   alloc kstat_irqs on node -1
[    0.374742] pci 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.374784] pci 0000:00:1a.2: PCI INT C disabled
[    0.374819] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.374877] pci 0000:00:1a.7: PCI INT C disabled
[    0.374914]   alloc irq_desc for 23 on node -1
[    0.374915]   alloc kstat_irqs on node -1
[    0.374918] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.374960] pci 0000:00:1d.0: PCI INT A disabled
[    0.374991]   alloc irq_desc for 19 on node -1
[    0.374992]   alloc kstat_irqs on node -1
[    0.374995] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.375037] pci 0000:00:1d.1: PCI INT B disabled
[    0.375070] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.375112] pci 0000:00:1d.2: PCI INT C disabled
[    0.375147] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.375193] pci 0000:00:1d.7: PCI INT A disabled
[    0.375227] pci 0000:01:00.0: Boot video device
[    0.375390] Scanning for low memory corruption every 60 seconds
[    0.375525] audit: initializing netlink socket (disabled)
[    0.375561] type=2000 audit(1369840698.000:1): initialized
[    0.382661] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.383657] VFS: Disk quotas dquot_6.5.2
[    0.383721] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.384141] fuse init (API version 7.13)
[    0.384225] msgmni has been set to 15987
[    0.384394] alg: No test for stdrng (krng)
[    0.384461] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.384495] io scheduler noop registered
[    0.384523] io scheduler anticipatory registered
[    0.384551] io scheduler deadline registered
[    0.384620] io scheduler cfq registered (default)
[    0.384742]   alloc irq_desc for 24 on node -1
[    0.384744]   alloc kstat_irqs on node -1
[    0.384750] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.384753] pcieport 0000:00:01.0: setting latency timer to 64
[    0.384822]   alloc irq_desc for 25 on node -1
[    0.384823]   alloc kstat_irqs on node -1
[    0.384828] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.384833] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.384916]   alloc irq_desc for 26 on node -1
[    0.384917]   alloc kstat_irqs on node -1
[    0.384922] pcieport 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.384927] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.385012]   alloc irq_desc for 27 on node -1
[    0.385013]   alloc kstat_irqs on node -1
[    0.385018] pcieport 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.385023] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.385081] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.385184] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.385294] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.385328] ACPI: Power Button [PWRB]
[    0.385386] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.385420] ACPI: Power Button [PWRF]
[    0.385984] ACPI: SSDT 00000000cff7e0d0 00277 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.386409] ACPI: SSDT 00000000cff7e5d0 004B2 (v01  PmRef  P001Cst 00003001 INTL 20060113)
[    0.386925] Monitor-Mwait will be used to enter C-1 state
[    0.386949] Monitor-Mwait will be used to enter C-2 state
[    0.399570] Monitor-Mwait will be used to enter C-3 state
[    0.399578] Marking TSC unstable due to TSC halts in idle
[    0.399658] processor LNXCPU:00: registered as cooling_device0
[    0.400049] ACPI: SSDT 00000000cff7e350 00277 (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
[    0.400868] ACPI: SSDT 00000000cff7ea90 00085 (v01  PmRef  P002Cst 00003000 INTL 20060113)
[    0.401453] processor LNXCPU:01: registered as cooling_device1
[    0.404251] Linux agpgart interface v0.103
[    0.404304] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.405221] brd: module loaded
[    0.405566] loop: module loaded
[    0.405652] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.405787] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.405843] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.405853] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.406069] Fixed MDIO Bus: probed
[    0.406117] PPP generic driver version 2.4.2
[    0.406165] tun: Universal TUN/TAP device driver, 1.6
[    0.406194] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.406270] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.406307] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.406346] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.406349] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.406405] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.406463] ehci_hcd 0000:00:1a.7: debug port 1
[    0.410393] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.410418] Switching to clocksource hpet
[    0.410421] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[    0.434100] Freeing initrd memory: 8180k freed
[    0.441282] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.441447] usb usb1: configuration #1 chosen from 1 choice
[    0.441503] hub 1-0:1.0: USB hub found
[    0.441537] hub 1-0:1.0: 6 ports detected
[    0.441613] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.441665] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.441668] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.441724] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.441784] ehci_hcd 0000:00:1d.7: debug port 1
[    0.445697] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.445714] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7ff800
[    0.461262] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.461367] usb usb2: configuration #1 chosen from 1 choice
[    0.461427] hub 2-0:1.0: USB hub found
[    0.461458] hub 2-0:1.0: 6 ports detected
[    0.461525] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.461564] uhci_hcd: USB Universal Host Controller Interface driver
[    0.461623] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.461657] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.461659] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.461710] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.461767] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    0.461855] usb usb3: configuration #1 chosen from 1 choice
[    0.461901] hub 3-0:1.0: USB hub found
[    0.461932] hub 3-0:1.0: 2 ports detected
[    0.461989] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.462022] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.462024] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.462078] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.462134] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    0.462225] usb usb4: configuration #1 chosen from 1 choice
[    0.462270] hub 4-0:1.0: USB hub found
[    0.462301] hub 4-0:1.0: 2 ports detected
[    0.462356] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.462389] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.462391] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.462440] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.462490] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[    0.462576] usb usb5: configuration #1 chosen from 1 choice
[    0.462619] hub 5-0:1.0: USB hub found
[    0.462650] hub 5-0:1.0: 2 ports detected
[    0.462708] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.462741] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.462743] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.462790] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.462840] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    0.462925] usb usb6: configuration #1 chosen from 1 choice
[    0.462969] hub 6-0:1.0: USB hub found
[    0.463000] hub 6-0:1.0: 2 ports detected
[    0.463058] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.463091] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.463093] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.463140] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.463195] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    0.463282] usb usb7: configuration #1 chosen from 1 choice
[    0.463325] hub 7-0:1.0: USB hub found
[    0.463356] hub 7-0:1.0: 2 ports detected
[    0.463413] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.463446] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.463448] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.463495] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.463545] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    0.463636] usb usb8: configuration #1 chosen from 1 choice
[    0.463680] hub 8-0:1.0: USB hub found
[    0.463712] hub 8-0:1.0: 2 ports detected
[    0.463802] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.463831] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.464333] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.464426] mice: PS/2 mouse device common for all mice
[    0.464535] rtc_cmos 00:03: RTC can wake from S4
[    0.464591] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.464639] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.464748] device-mapper: uevent: version 1.0.3
[    0.464858] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.464945] device-mapper: multipath: version 1.1.0 loaded
[    0.464975] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.465172] cpuidle: using governor ladder
[    0.465274] cpuidle: using governor menu
[    0.465538] TCP cubic registered
[    0.465663] NET: Registered protocol family 10
[    0.466190] NET: Registered protocol family 17
[    0.466935] PM: Resume from disk failed.
[    0.466944] registered taskstats version 1
[    0.467315]   Magic number: 13:36:337
[    0.467358] tty tty58: hash matches
[    0.467444] rtc_cmos 00:03: setting system clock to 2013-05-29 15:18:19 UTC (1369840699)
[    0.467478] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.467506] EDD information not available.
[    0.467579] Freeing unused kernel memory: 884k freed
[    0.467848] Write protecting the kernel read-only data: 7724k
[    0.477783] udev: starting version 151
[    0.485662] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.512570] md: linear personality registered for level -1
[    0.520893] ahci 0000:00:1f.2: version 3.0
[    0.520908] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.520976]   alloc irq_desc for 28 on node -1
[    0.520977]   alloc kstat_irqs on node -1
[    0.520985] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.521019] ahci: SSS flag set, parallel bus scan disabled
[    0.521075] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.521109] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
[    0.521144] ahci 0000:00:1f.2: setting latency timer to 64
[    0.522948] skge 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.523015] skge 1.13 addr 0xfebf8000 irq 18 chip Yukon-Lite rev 9
[    0.523458] skge eth0: addr 00:22:15:f8:c5:6f
[    0.524726] sky2 driver version 1.25
[    0.524771] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.524807] sky2 0000:02:00.0: setting latency timer to 64
[    0.524825] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 3
[    0.524925]   alloc irq_desc for 29 on node -1
[    0.524927]   alloc kstat_irqs on node -1
[    0.524936] sky2 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.527224] sky2 eth1: addr 00:22:15:f8:bb:f8
[    0.527306] sata_sil 0000:05:00.0: version 2.4
[    0.527324] sata_sil 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.530657] md: multipath personality registered for level -4
[    0.532279] scsi0 : sata_sil
[    0.542285] scsi1 : sata_sil
[    0.542356] ata1: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffc80 irq 16
[    0.542387] ata2: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffcc0 irq 16
[    0.545385] md: raid0 personality registered for level 0
[    0.611348] scsi2 : ahci
[    0.611443] scsi3 : ahci
[    0.611510] scsi4 : ahci
[    0.611581] scsi5 : ahci
[    0.611653] scsi6 : ahci
[    0.611719] scsi7 : ahci
[    0.611862] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 28
[    0.611896] ata4: SATA max UDMA/133 irq_stat 0x00400040 irq 28
[    0.611925] ata5: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    0.611957] ata6: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    0.611990] ata7: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    0.612023] ata8: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    0.890035] ata1: SATA link down (SStatus 0 SControl 310)
[    1.010025] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    1.189982] usb 6-2: configuration #1 chosen from 1 choice
[    1.241298] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.281459] ata2.00: HPA unlocked: 156299375 -> 156301488, native 156301488
[    1.281491] ata2.00: ATA-6: ST380013AS, 3.18, max UDMA/133
[    1.281520] ata2.00: 156301488 sectors, multi 16: LBA48 
[    1.320478] ata2.00: configured for UDMA/100
[    1.320633] scsi 1:0:0:0: Direct-Access     ATA      ST380013AS       3.18 PQ: 0 ANSI: 5
[    1.320757] sd 1:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.320759] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.320866] sd 1:0:0:0: [sda] Write Protect is off
[    1.320896] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.320932] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.321110]  sda: sda1
[    1.327759] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.540114] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.547460] ata3.00: ATA-8: WDC WD3000GLFS-01F8U0, 03.03V01, max UDMA/133
[    1.547498] ata3.00: 586072368 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.555466] ata3.00: configured for UDMA/133
[    1.570126] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3000GLFS-0 03.0 PQ: 0 ANSI: 5
[    1.570242] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.570318] sd 2:0:0:0: [sdb] 586072368 512-byte logical blocks: (300 GB/279 GiB)
[    1.570468] sd 2:0:0:0: [sdb] Write Protect is off
[    1.570498] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.570515] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.570671]  sdb: sdb1 sdb2
[    1.588089] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.641456] mdadm: sending ioctl 1261 to a partition!
[    1.641486] mdadm: sending ioctl 1261 to a partition!
[    1.641654] mdadm: sending ioctl 1261 to a partition!
[    1.641687] mdadm: sending ioctl 1261 to a partition!
[    1.641849] mdadm: sending ioctl 1261 to a partition!
[    1.641880] mdadm: sending ioctl 1261 to a partition!
[    1.642088] mdadm: sending ioctl 1261 to a partition!
[    1.642120] mdadm: sending ioctl 1261 to a partition!
[    1.642222] mdadm: sending ioctl 1261 to a partition!
[    1.642254] mdadm: sending ioctl 1261 to a partition!
[    1.655874] md: bind<sdb2>
[    2.500030] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.505129] ata4.00: ATA-8: WDC WD3000GLFS-01F8U0, 03.03V01, max UDMA/133
[    2.505163] ata4.00: 586072368 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.510327] ata4.00: configured for UDMA/133
[    2.530135] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3000GLFS-0 03.0 PQ: 0 ANSI: 5
[    2.530259] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.530290] sd 3:0:0:0: [sdc] 586072368 512-byte logical blocks: (300 GB/279 GiB)
[    2.530360] sd 3:0:0:0: [sdc] Write Protect is off
[    2.530390] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.530407] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.530738]  sdc: sdc1 sdc2
[    2.550636] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.605827] md: bind<sdc2>
[    2.607976] md: raid1 personality registered for level 1
[    3.460036] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.460738] ata5.00: ATA-6: WDC WD800JD-22JNA0, 05.01C05, max UDMA/133
[    3.460772] ata5.00: 156301488 sectors, multi 0: LBA 
[    3.461564] ata5.00: configured for UDMA/133
[    3.480133] scsi 4:0:0:0: Direct-Access     ATA      WDC WD800JD-22JN 05.0 PQ: 0 ANSI: 5
[    3.480259] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    3.480273] sd 4:0:0:0: [sdd] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    3.480303] sd 4:0:0:0: [sdd] Write Protect is off
[    3.480305] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.480339] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.480449]  sdd: sdd1
[    3.491447] sd 4:0:0:0: [sdd] Attached SCSI disk
[    4.410036] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.460388] ata6.00: ATA-7: ST380815AS, 3.AAC, max UDMA/133
[    4.460421] ata6.00: 156301488 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.518697] ata6.00: configured for UDMA/133
[    4.530118] scsi 5:0:0:0: Direct-Access     ATA      ST380815AS       3.AA PQ: 0 ANSI: 5
[    4.530240] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    4.530325] sd 5:0:0:0: [sde] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    4.530498] sd 5:0:0:0: [sde] Write Protect is off
[    4.530529] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.530567] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.530741]  sde: sde1
[    4.566942] sd 5:0:0:0: [sde] Attached SCSI disk
[    5.460045] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.460474] ata7.00: ATAPI: ATAPI   DVD D  DH16D3S, SP52, max UDMA/100
[    5.462070] ata7.00: configured for UDMA/100
[    5.481404] scsi 6:0:0:0: CD-ROM            ATAPI    DVD D  DH16D3S   SP52 PQ: 0 ANSI: 5
[    5.487402] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    5.487436] Uniform CD-ROM driver Revision: 3.20
[    5.487557] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    5.487591] sr 6:0:0:0: Attached scsi generic sg5 type 5
[    6.410030] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.455269] ata8.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    6.455302] ata8.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.513579] ata8.00: configured for UDMA/133
[    6.530115] scsi 7:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    6.530236] sd 7:0:0:0: Attached scsi generic sg6 type 0
[    6.530310] sd 7:0:0:0: [sdf] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    6.530571] sd 7:0:0:0: [sdf] Write Protect is off
[    6.530601] sd 7:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    6.530636] sd 7:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.530806]  sdf: sdf1
[    6.579590] sd 7:0:0:0: [sdf] Attached SCSI disk
[    6.580494] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.580550] pata_marvell 0000:03:00.0: setting latency timer to 64
[    6.582004] scsi8 : pata_marvell
[    6.582097] scsi9 : pata_marvell
[    6.582149] ata9: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    6.582179] ata10: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[    6.582770] usbcore: registered new interface driver hiddev
[    6.660361] __ratelimit: 46 callbacks suppressed
[    6.660391] mdadm: sending ioctl 1261 to a partition!
[    6.660419] mdadm: sending ioctl 1261 to a partition!
[    6.660763] mdadm: sending ioctl 1261 to a partition!
[    6.660795] mdadm: sending ioctl 1261 to a partition!
[    6.661238] mdadm: sending ioctl 1261 to a partition!
[    6.661277] mdadm: sending ioctl 1261 to a partition!
[    6.661701] mdadm: sending ioctl 1261 to a partition!
[    6.661732] mdadm: sending ioctl 1261 to a partition!
[    6.661833] mdadm: sending ioctl 1261 to a partition!
[    6.661868] mdadm: sending ioctl 1261 to a partition!
[    6.737000] generic-usb 0003:0764:0501.0001: hiddev96,hidraw0: USB HID v1.10 Device [CPS UPS CP1000AVRLCD] on usb-0000:00:1d.0-2/input0
[    6.737062] usbcore: registered new interface driver usbhid
[    6.737091] usbhid: v2.6:USB HID core driver
[    6.950550] ata10.00: ATA-8: ST3000DM001-9YN166, CC9C, max UDMA/133
[    6.950584] ata10.00: 5860533168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    6.990558] ata10.00: configured for UDMA/133
[    6.990687] scsi 9:0:0:0: Direct-Access     ATA      ST3000DM001-9YN1 CC9C PQ: 0 ANSI: 5
[    6.990808] sd 9:0:0:0: [sdg] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    6.990818] sd 9:0:0:0: Attached scsi generic sg7 type 0
[    6.990872] sd 9:0:0:0: [sdg] 4096-byte physical blocks
[    6.990943] sd 9:0:0:0: [sdg] Write Protect is off
[    6.990974] sd 9:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[    6.991011] sd 9:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.991208]  sdg: sdg1
[    7.039891] sd 9:0:0:0: [sdg] Attached SCSI disk
[    7.040285] raid1: raid set md3 active with 2 out of 2 mirrors
[    7.040328] md3: detected capacity change from 0 to 298067558400
[    7.040723] md: bind<sdd1>
[    7.041375]  md3: unknown partition table
[    7.043977] async_tx: api initialized (async)
[    7.055321] md: bind<sde1>
[    7.063286] md: bind<sda1>
[    7.210009] raid6: int64x1   2350 MB/s
[    7.380019] raid6: int64x2   3150 MB/s
[    7.550023] raid6: int64x4   2275 MB/s
[    7.720029] raid6: int64x8   2044 MB/s
[    7.890014] raid6: sse2x1    5365 MB/s
[    8.060013] raid6: sse2x2    5746 MB/s
[    8.230008] raid6: sse2x4    8877 MB/s
[    8.230036] raid6: using algorithm sse2x4 (8877 MB/s)
[    8.230802] xor: automatically using best checksumming function: generic_sse
[    8.280002]    generic_sse: 11422.400 MB/sec
[    8.280034] xor: using function: generic_sse (11422.400 MB/sec)
[    8.282870] md: raid6 personality registered for level 6
[    8.282901] md: raid5 personality registered for level 5
[    8.282929] md: raid4 personality registered for level 4
[    8.286617] md: raid10 personality registered for level 10
[    8.304152] EXT4-fs (md3): mounted filesystem with ordered data mode
[    8.365883] raid5: device sda1 operational as raid disk 0
[    8.365913] raid5: device sde1 operational as raid disk 2
[    8.365942] raid5: device sdd1 operational as raid disk 1
[    8.366197] raid5: allocated 3230kB for md0
[    8.366266] 0: w=1 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[    8.366299] 2: w=2 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[    8.366327] 1: w=3 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[    8.366356] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[    8.366388] RAID5 conf printout:
[    8.366415]  --- rd:3 wd:3
[    8.366442]  disk 0, o:1, dev:sda1
[    8.366469]  disk 1, o:1, dev:sdd1
[    8.366497]  disk 2, o:1, dev:sde1
[    8.366546] md0: detected capacity change from 0 to 160048218112
[   15.408756] udev: starting version 151
[   15.421119] Adding 1951884k swap on /dev/sdb1.  Priority:-1 extents:1 across:1951884k 
[   15.474141] Adding 1951888k swap on /dev/sdc1.  Priority:-2 extents:1 across:1951888k 
[   15.534112] __ratelimit: 20 callbacks suppressed
[   15.534114] mdadm: sending ioctl 1261 to a partition!
[   15.534115] mdadm: sending ioctl 1261 to a partition!
[   15.535278]  md0: unknown partition table
[   15.551521] mdadm: sending ioctl 1261 to a partition!
[   15.551523] mdadm: sending ioctl 1261 to a partition!
[   15.569526] udev: renamed network interface eth0 to eth1
[   15.573580] udev: renamed network interface eth1_rename to eth0
[   15.611003] type=1505 audit(1369840714.542:2):  operation="profile_load" pid=737 name="/sbin/dhclient3"
[   15.611561] type=1505 audit(1369840714.542:3):  operation="profile_load" pid=737 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.611821] type=1505 audit(1369840714.542:4):  operation="profile_load" pid=737 name="/usr/lib/connman/scripts/dhclient-script"
[   15.612774] type=1505 audit(1369840714.542:5):  operation="profile_replace" pid=786 name="/sbin/dhclient3"
[   15.612828] type=1505 audit(1369840714.542:6):  operation="profile_replace" pid=793 name="/sbin/dhclient3"
[   15.613254] type=1505 audit(1369840714.542:7):  operation="profile_replace" pid=786 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.613306] type=1505 audit(1369840714.542:8):  operation="profile_replace" pid=793 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.613512] type=1505 audit(1369840714.542:9):  operation="profile_replace" pid=786 name="/usr/lib/connman/scripts/dhclient-script"
[   15.613565] type=1505 audit(1369840714.542:10):  operation="profile_replace" pid=793 name="/usr/lib/connman/scripts/dhclient-script"
[   15.623008] mdadm: sending ioctl 1261 to a partition!
[   15.623011] mdadm: sending ioctl 1261 to a partition!
[   15.623195] mdadm: sending ioctl 1261 to a partition!
[   15.623197] mdadm: sending ioctl 1261 to a partition!
[   15.623298] mdadm: sending ioctl 1261 to a partition!
[   15.623299] mdadm: sending ioctl 1261 to a partition!
[   15.628201] lp: driver loaded but no devices found
[   15.674589] [drm] Initialized drm 1.1.0 20060810
[   15.675693] sky2 eth0: enabling interface
[   15.677550] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.848516] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.848548] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.876502] [drm] VGACON disable radeon kernel modesetting.
[   15.877237] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.877240] pci 0000:01:00.0: setting latency timer to 64
[   15.877399] [drm] Initialized radeon 1.32.0 20080528 for 0000:01:00.0 on minor 0
[   15.889620] EXT4-fs (sdf1): mounted filesystem with ordered data mode
[   15.900825] vga16fb: initializing
[   15.900828] vga16fb: mapped to 0xffff8800000a0000
[   15.900868] fb0: VGA16 VGA frame buffer device
[   16.018107] Console: switching to colour frame buffer device 80x30
[   16.031806] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   16.059875] EXT4-fs (sdg1): mounted filesystem with ordered data mode
[   16.221273] EXT4-fs (md0): mounted filesystem with ordered data mode
[   16.264273] RPC: Registered udp transport module.
[   16.264275] RPC: Registered tcp transport module.
[   16.264277] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   16.376326] type=1505 audit(1369840715.042:11):  operation="profile_replace" pid=1179 name="/sbin/dhclient3"
[   16.625369] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   18.210408] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   18.211014] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.520018] eth0: no IPv6 routers present
[   29.074068] svc: failed to register lockdv1 RPC service (errno 97).
[   29.074875] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   29.084690] NFSD: starting 90-second grace period
[   31.291437] ppdev: user-space parallel port driver
[  405.545218] nfsd: last server has exited, flushing export cache
[  546.624032] JBD: barrier-based sync failed on md0-8 - disabling barriers
[ 1157.041294] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 1157.041413] usb 6-2: USB disconnect, address 2
[ 1157.320032] usb 6-2: new low speed USB device using uhci_hcd and address 3
[ 1157.500129] usb 6-2: configuration #1 chosen from 1 choice
[ 1157.659138] generic-usb 0003:0764:0501.0002: hiddev96,hidraw0: USB HID v1.10 Device [CPS UPS CP1000AVRLCD] on usb-0000:00:1d.0-2/input0
[11572.010111] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[11572.011594] ata10.00: failed command: SMART
[11572.013300] ata10.00: cmd b0/da:00:00:4f:c2/00:00:00:00:00/00 tag 0
[11572.013301]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[11572.019480] ata10.00: status: { DRDY }
[11572.801335] ata10: soft resetting link
[11573.280609] ata10.00: configured for UDMA/133
[11573.280621] ata10: EH complete
[32484.971445] sd 7:0:0:0: [sdf] Synchronizing SCSI cache
[32484.998083] sd 7:0:0:0: [sdf] Stopping disk
[32484.998213] ata8.00: disabled
[32600.170388] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4010000 action 0xe frozen
[32600.177258] ata8: irq_stat 0x00400040, connection status changed
[32600.181173] ata8: SError: { PHYRdyChg DevExch }
[32600.185193] ata8: hard resetting link
[32600.930042] ata8: SATA link down (SStatus 0 SControl 300)
[32600.930051] ata8: EH complete
[32668.541299] hub 6-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[32668.544969] usb 6-2: USB disconnect, address 3
[32668.820033] usb 6-2: new low speed USB device using uhci_hcd and address 4
[32669.008192] usb 6-2: configuration #1 chosen from 1 choice
[32669.167568] generic-usb 0003:0764:0501.0003: hiddev96,hidraw0: USB HID v1.10 Device [CPS UPS CP1000AVRLCD] on usb-0000:00:1d.0-2/input0
[32680.317984] ata8: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
[32680.326217] ata8: irq_stat 0x00000040, connection status changed
[32680.330735] ata8: SError: { CommWake DevExch }
[32680.335337] ata8: hard resetting link
[32690.090035] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[32690.123202] ata8.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[32690.123206] ata8.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[32690.181526] ata8.00: configured for UDMA/133
[32690.181533] ata8: EH complete
[32690.181635] scsi 7:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[32690.181801] sd 7:0:0:0: Attached scsi generic sg6 type 0
[32690.183112] sd 7:0:0:0: [sdf] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[32690.183158] sd 7:0:0:0: [sdf] Write Protect is off
[32690.183161] sd 7:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[32690.183184] sd 7:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[32690.183326]  sdf: sdf1
[32690.221899] sd 7:0:0:0: [sdf] Attached SCSI disk
[32710.056703] EXT4-fs (sdf1): mounted filesystem with ordered data mode

```
FYI, the last set lines is because a backup drive is being rotated (sdf). 

Also tgalati4 mentioned 40k hours is a lot. Those drives are 300GB WD velociraptors. I thought they were enterprise class so should be rated higher than 50k. But the corruption happens on every drive so I leaning towards OS or motherboard failure. Just trying to figure out which before I convince the boss to spend $$$$ on new hardware and find out it was OS/configuration issue.

---

### Post by danic on 2013-05-31
I did a few more tests.
Plugged in a new 1.5TB drive and have done the following
[LIST]
[*]Formatted to ext4 and ran md5sum tests : Failure
[*]re-formated as XFS and ran tests : Failure but after a repeating the test many times
[*]Downloaded and installed [ZFS on linux]("http://zfsonlinux.org/"). Added drive to test pool. The md5sum test so far so good.  After hour of testing and 'zpool scrub', 'zpool status' show 3 checksum errors but the files seem to be intacts.
[/LIST]

So what have I learned? Not much actually. Only thing I gathered over much testing is in higher system load (like during the normal workday with many users) causes my test to fail more often then when I'm stuck in the office after hours.
... the fight continues!


**Edit
Well I loaded up a live CD of Ubuntu 12.04 x64 desktop. Install mdadm, assemble arrays, mounted them, ran tests again. Same problems
Also I replaced the RAM, for good measure, and I ran into all sorts of kernel panics. I guess the new ram is worse than what was in there before.

**Edit 6/11/2013
Solved. Problem is now gone. Re-seating original sticks of RAM fixed it. Troubling that memtest86 didn't find any errors.

---

