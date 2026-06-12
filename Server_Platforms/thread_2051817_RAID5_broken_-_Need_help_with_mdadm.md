---
title: "RAID5 broken - Need help with mdadm"
date: 2012-09-02
forum: Server Platforms
---

### Post by Bakmeel on 2012-09-02
Dear all,

Last week the mstat deamon sent me an email message that my RAID5 array had failed:
I have been trying to recover the array but I got lost in mdadm giving me inconsistent information

the mdstat output was:
```
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdb1[3] sdc1[0] sde1[2] sdd1[4](F)
      5860540224 blocks level 5, 64k chunk, algorithm 2 [4/3] [U_UU]
```Getting the info from mdadm:
```
root@Perseus:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Aug 27 22:06:39 2010
     Raid Level : raid5
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  2 12:01:40 2012
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e8fdb9c9:a21ad335:145f0e20:b7304898
         Events : 0.23996

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1
       3       8       17        3      active sync   /dev/sdb1

```So here it still seems that sdd1 is lost. So, I examine the four drives in my array:

**SDB1**
```
root@Perseus:~# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e8fdb9c9:a21ad335:145f0e20:b7304898
  Creation Time : Fri Aug 27 22:06:39 2010
     Raid Level : raid5
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Sep  2 12:19:53 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 11007cd1 - correct
         Events : 23998

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       17        3      active sync   /dev/sdb1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       0        0        1      faulty removed
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       17        3      active sync   /dev/sdb1
```**SDC1**
```
root@Perseus:~# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e8fdb9c9:a21ad335:145f0e20:b7304898
  Creation Time : Fri Aug 27 22:06:39 2010
     Raid Level : raid5
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Sep  2 12:19:53 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 11007cdb - correct
         Events : 23998

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync   /dev/sdc1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       0        0        1      faulty removed
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       17        3      active sync   /dev/sdb1
```**SDD1**
```
root@Perseus:~# mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e8fdb9c9:a21ad335:145f0e20:b7304898
  Creation Time : Fri Aug 27 22:06:39 2010
     Raid Level : raid5
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Aug 31 11:51:04 2012
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 10fd7354 - expected 10fe138b
         Events : 23405

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       17        3      active sync   /dev/sdb1
```**SDE1**
```
root@Perseus:~# mdadm -E /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e8fdb9c9:a21ad335:145f0e20:b7304898
  Creation Time : Fri Aug 27 22:06:39 2010
     Raid Level : raid5
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Sep  2 12:19:53 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 11007cff - correct
         Events : 23998

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       65        2      active sync   /dev/sde1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       0        0        1      faulty removed
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       17        3      active sync   /dev/sdb1
```So, for some reason mdstat thinks SDD1 is bad, but checking the device itself it is pronounced healthy except for the fact that the checksum is wrong.

I have tried to re-assemble the array but here I find myself lost:
```
root@Perseus:~# umount /dev/md0
root@Perseus:~# mdadm --assemble --scan --verbose
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/block/9:0
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sdd1 is not built for host Perseus.
mdadm: no recogniseable superblock on /dev/sdd
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy

```So what to do next? Any help is appreciated.

---

### Post by rubylaser on 2012-09-02
/dev/sdd1's event counter is lower than your other disks, so as you mentioned, that's the one that fell out of the array.  You should just umount the array, then stop the array, and re-assemble properly like this.

```
umount /dev/md0
mdadm --stop /dev/md0
mdadm --assemble --force /dev/md0  /dev/sd[bcde]1
```

That should cause a resync, and once done, you should be good to go.  As an aside, what does your SMART data actually show on that disk?

```
smartctl -a /dev/sdd
```

---

### Post by Bakmeel on 2012-09-02
Thanks.

I tried, but unfortunately mdadm refused to add the drive to the array.

```
root@Perseus:~# umount /dev/md0
umount: /dev/md0: not mounted
root@Perseus:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@Perseus:~# mdadm --assemble --force --verbose /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 2.
mdadm: failed to add /dev/sdd1 to /dev/md0: Invalid argument
mdadm: added /dev/sde1 to /dev/md0 as 2
mdadm: added /dev/sdb1 to /dev/md0 as 3
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
```

I have installed smartctl and ran for SDD.
```
root@Perseus:~# smartctl -a /dev/sdd
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD203WI
Serial Number:    S2GMJ1AZ701018
Firmware Version: 1AN10003
User Capacity:    2,000,398,934,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x28
Local Time is:    Sun Sep  2 14:20:12 2012 CEST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection:                 (25920) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
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
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       29
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   063   061   025    Pre-fail  Always       -       11298
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1098
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       6315
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       31
191 G-Sense_Error_Rate      0x0022   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   060   000    Old_age   Always       -       29 (Lifetime Min/Max 14/46)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       5
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1808

SMART Error Log Version: 1
ATA Error Count: 3
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

Error 3 occurred at disk power-on lifetime: 6311 hours (262 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:12:47.823  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      01:12:47.823  NOP [Abort queued commands]
  00 00 01 01 00 00 00 00      01:12:47.822  NOP [Abort queued commands]
  00 00 01 01 00 00 00 00      01:12:47.822  NOP [Abort queued commands]
  ec 00 00 00 00 00 a0 08      01:12:47.817  IDENTIFY DEVICE

Error 2 occurred at disk power-on lifetime: 6311 hours (262 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:12:47.812  IDENTIFY DEVICE
  00 00 01 01 00 00 40 08      01:12:47.812  NOP [Abort queued commands]
  00 00 01 01 00 00 40 00      01:12:47.811  NOP [Abort queued commands]
  35 00 08 80 87 e0 e0 08      01:12:47.811  WRITE DMA EXT
  27 00 00 00 00 00 e0 08      01:12:47.811  READ NATIVE MAX ADDRESS EXT

Error 1 occurred at disk power-on lifetime: 6311 hours (262 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      01:12:47.806  IDENTIFY DEVICE
  00 00 01 01 00 00 40 08      01:12:47.805  NOP [Abort queued commands]
  00 00 01 01 00 00 40 00      01:12:47.805  NOP [Abort queued commands]
  35 00 08 80 87 e0 e0 08      01:12:47.794  WRITE DMA EXT
  ea 00 00 87 87 e0 e0 08      01:12:47.794  FLUSH CACHE EXIT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3801         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

The counter values generally match up with the rest of the array's devices.

Interesting to notice is that the three logged ATA errors have all occurred approximately 4  hours ago. That would correlate to my attempts this morning to "fix" the problem by trying to reboot the machine.
(I know I didn't need to do that... it is a poor habit of mine from the old Windows days)

---

### Post by Bakmeel on 2012-09-02
I did a bit of google-ing and found an interesting answer here:

[http://lists.lugod.org/pipermail/vox-tech/2005-April/011058.html](http://lists.lugod.org/pipermail/vox-tech/2005-April/011058.html)

His answer was to run mdadm with the "update summaries" option, which seemed to work at first:

```
root@Perseus:~# mdadm --assemble --update summaries --verbose /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdd1 to /dev/md0 as 1
mdadm: added /dev/sde1 to /dev/md0 as 2
mdadm: added /dev/sdb1 to /dev/md0 as 3
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 3 drives (out of 4).

```

So it has added the drive to the array and started it again, but apparently only three disks included.

```
root@Perseus:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Aug 27 22:06:39 2010
     Raid Level : raid5
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  2 12:59:02 2012
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e8fdb9c9:a21ad335:145f0e20:b7304898
         Events : 0.24000

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed
       2       8       65        2      active sync   /dev/sde1
       3       8       17        3      active sync   /dev/sdb1
```

Though now apparently removed from the array, it seemingly did manage to solve the checksum problem.

```
root@Perseus:~# mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e8fdb9c9:a21ad335:145f0e20:b7304898
  Creation Time : Fri Aug 27 22:06:39 2010
     Raid Level : raid5
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Aug 31 11:51:04 2012
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 10fe138b - correct
         Events : 23405

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       17        3      active sync   /dev/sdb1
```

Notice that in examining SDD mdadm suddenly claims that sdd is added and the array is all up and peachy. Examining any other device in the array claims the opposite.

So I guess by updating the summaries I ended up just removing it from the array.. Fine.. I stopped the array and forced a new re-assembly:

```
root@Perseus:~# mdadm --assemble --force --verbose /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdd1 to /dev/md0 as 1
mdadm: added /dev/sde1 to /dev/md0 as 2
mdadm: added /dev/sdb1 to /dev/md0 as 3
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 3 drives (out of 4).

```

And guess what: It suddenly jumps back in business!
```
root@Perseus:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Aug 27 22:06:39 2010
     Raid Level : raid5
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  2 15:00:48 2012
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : e8fdb9c9:a21ad335:145f0e20:b7304898
         Events : 0.24004

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       4       8       49        1      spare rebuilding   /dev/sdd1
       2       8       65        2      active sync   /dev/sde1
       3       8       17        3      active sync   /dev/sdb1

```

The array is recovering as we speak. Being a 2TB disk this will take some time.

I am still wondering though: Why could the drive have failed?

---

### Post by rubylaser on 2012-09-02
Yes, update summaries just kicked the disk out of the array.  You could have accomplished the same thing by just assembling the array as I showed before but leave out disk /dev/sdd1.  Now that you've got it working, that's great :)

Your disk (/dev/sdd) has 5 UDMA CRC errors which are typically caused by a defective SATA cable. These read errors also show up at the end of the SMART log as well. The first thing I would do (once the array is done resyncing) is to swap the cable on that disk with a new one.

---

