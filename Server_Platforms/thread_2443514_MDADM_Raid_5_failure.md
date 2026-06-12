---
title: "MDADM Raid 5 failure"
date: 2020-05-16
forum: Server Platforms
---

### Post by Slownis on 2020-05-16
Fresh install of Ubuntu 20.04
I have a 4 disc drive raid 5 array consisting of four 2 terrabyte WD green drives, migrated from a prior Ubuntu install.
When I installed MDADM on the new system everything seemed fine - for a while.  Raid mounted fine.
Now it seems /dev/sdb is missing from the array and it will no longer mount.  How can I get /dev/sdb back into the /dev/md5 array?  Is it a problem with its magic number?

```
johnw@JW-MediaServ:~$ sudo mdadm --examine /dev/sd[b-f]
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :    429561856 sectors at    804812800 (type 83)
Partition[1] :     16384000 sectors at         2048 (type 82)
Partition[2] :     15886338 sectors at   1234376702 (type 05)
Partition[3] :    788426752 sectors at     16386048 (type 83)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 52c035ba:7524c0e7:9ae73d40:d13ef8b4
           Name : johnw-desktop:5
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 5860150272 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906766848 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=176 sectors
          State : clean
    Device UUID : c805b298:a422eedd:67a295a0:96748203


    Update Time : Sat May 16 04:07:23 2020
       Checksum : dc61b744 - correct
         Events : 31288


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 52c035ba:7524c0e7:9ae73d40:d13ef8b4
           Name : johnw-desktop:5
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 5860150272 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906766848 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=176 sectors
          State : clean
    Device UUID : b35a61bd:e3027883:0be588d7:6b98abd3


    Update Time : Sat May 16 04:07:23 2020
       Checksum : adb89415 - correct
         Events : 31288


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 52c035ba:7524c0e7:9ae73d40:d13ef8b4
           Name : johnw-desktop:5
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 5860150272 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906766848 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=176 sectors
          State : clean
    Device UUID : 1816504c:f6de06bc:3f9103cc:2dbd98a7


    Update Time : Sat May 16 04:07:23 2020
       Checksum : 3d9cbb55 - correct
         Events : 31288


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)





```

---

### Post by lvm on 2020-05-17
mdadm doesn't see anything raid-like on sdb, it only sees a non-raid partition there. If the device is healthy - and that's a big if because something made it fail, and if it is not in use for something else - another big if because partition ee is a GPT blocker implying that there are GPT partitions there, and given that the array was used for some unknown time after the failure, the only way is to fail and remove this device from the array (if it is still there which I doubt - can be checked in /proc/mdstat) and re-add as a new device. Before that checking the disk with something like smartctl or GSmartControl and examining its GPT partitions with [g]parted is strongly recommended. I also don't like the idea of using devices instead of partitions for the array, but if it was created this way it cannot be easily changed.

---

### Post by Slownis on 2020-05-17
I ran smartctl:

```
johnw@JW-MediaServ:/media/johnw/System 2$ sudo smartctl -a /dev/sdb
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-29-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-22MVWB0
Serial Number:    WD-WMAZA4770810
LU WWN Device Id: 5 0014ee 002c80ebc
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sun May 17 15:22:30 2020 CDT
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
data collection:         (38580) seconds.
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
recommended polling time:      ( 372) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       78
  3 Spin_Up_Time            0x0027   253   190   021    Pre-fail  Always       -       1116
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5595
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   062   062   000    Old_age   Always       -       27916
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       5543
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       752
193 Load_Cycle_Count        0x0032   135   135   000    Old_age   Always       -       195245
194 Temperature_Celsius     0x0022   123   102   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       126
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       129
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       33


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


Error 3 occurred at disk power-on lifetime: 348 hours (14 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 00 00 00 00  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d6 01 e0 4f c2 00 08      00:22:02.268  SMART WRITE LOG
  ec 00 01 00 00 00 00 08      00:15:33.340  IDENTIFY DEVICE
  b0 d5 01 e1 4f c2 00 08      00:15:33.338  SMART READ LOG
  b0 d6 01 e0 4f c2 00 08      00:15:33.338  SMART WRITE LOG


Error 2 occurred at disk power-on lifetime: 347 hours (14 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 00 00 00 00  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d5 01 e1 4f c2 00 08      00:15:33.338  SMART READ LOG
  b0 d6 01 e0 4f c2 00 08      00:15:33.338  SMART WRITE LOG


Error 1 occurred at disk power-on lifetime: 347 hours (14 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 00 00 00 00  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d6 01 e0 4f c2 00 08      00:15:33.338  SMART WRITE LOG


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

 mdstat:
```
johnw@JW-MediaServ:/media/johnw/System 2$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md5 : active raid5 sdd[4] sdf[3] sde[1]
      5860150272 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]
      
unused devices: <none>

```

I'm not sure how to interpret the smart data, but I saw "passed", so I just need to re-add it to the array, correct?

re-add doesn't appear to work:
```
johnw@JW-MediaServ:/media/johnw/System 2$ sudo mdadm --manage /dev/md5 --re-add /dev/sdb
mdadm: --re-add for /dev/sdb to /dev/md5 is not possible
```

---

### Post by TheFu on 2020-05-17
```
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       126
```

That means data loss.  Buy a new disk - last week.  Today is too late.
Devices over 1TB shouldn't be run except in RAiD1 or RAiD10 configs, imho.

The "passed" just means the test finished.

Raid is not a backup.  Get the backups ready for restore.

---

### Post by lvm on 2020-05-18
> **Slownis said:**
> I'm not sure how to interpret the smart data, but I saw "passed"
Unfortunately, the overall test line is often misleading and reports 'passed' for disks which are not in good health. It doesn't however mean that it is just the test which is finished, more can be found at the smartmontools site: [https://www.smartmontools.org/wiki/FAQ#ATAdriveisfailingself-testsbutSMARThealthstatusisPASSED.Whatsgoingon](https://www.smartmontools.org/wiki/FAQ#ATAdriveisfailingself-testsbutSMARThealthstatusisPASSED.Whatsgoingon) Non-zero Current_Pending_Sector does not necessarily mean data loss either but it is a cause for concern and probably this is what caused the disk to drop out of array. More information can be found in syslog at the time the array failed. I concur with the previous speaker that it has to be replaced, I however strongly disagree with his statement regarding disk sizes. As a proud owner of md RAID6 built of reasonably fast 7200 rpm 10T disks I can say that rebuild time is quite acceptable - well under 1 day, and even if such views were ever correct these days are long gone.

---

### Post by Impavidus on 2020-05-18
> **Slownis said:**
> I ran smartctl:

```
johnw@JW-MediaServ:/media/johnw/System 2$ sudo smartctl -a /dev/sdb
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-29-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org
```
**sudo smartctl -a /dev/sdb** doesn't actually run the test, it only prints the results from last test. And according to this:```

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]
```no test was performed.

I suggest that you actually run a test:```
sudo smartctl -t long /dev/sdb
```That will run the long test, which according to```

Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 372) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
```will take 6:12 hours. Don't suspend, hibernate or switch off your computer while running the test.

One thing I don't understand about your test is this:```

  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       126
```This tells us that 126 sectors are bad and will be reallocated to spare sectors (if still available), but no sectors have been reallocated yet, so spares must be available. Maybe running that test and printing results again will give more sensible numbers.

---

### Post by darkod on 2020-05-18
1. Best practice is to use mdadm with partitions, not disks. Make a partition spanning the whole disk (do NOT format it) and use that as device member of mdadm raid. In your case you used disks. However, this is not a reason to fail.

2. Raid5 should still work correctly with one member failed. From your last posts it seems md5 is assembled, so post the output of its details:
```
sudo mdadm -D /dev/md5
sudo blkid
```

Don't do anything else for the moment until you get more info. Wrong action can put your data in danger. And if md5 is not mounted right now, don't try to mount it yet.

---

### Post by Slownis on 2020-05-18
> **darkod said:**
> 1. Best practice is to use mdadm with partitions, not disks. Make a partition spanning the whole disk (do NOT format it) and use that as device member of mdadm raid. In your case you used disks. However, this is not a reason to fail.


Yep, I've seen that posted many times, but this was set up many years ago to use the whole disks and its the world I live in for now - until I decide to buy more disks.

[QUOTE=darkod]
2. Raid5 should still work correctly with one member failed. From your last posts it seems md5 is assembled, so post the output of its details:
```
sudo mdadm -D /dev/md5
sudo blkid
```
[/QUOTE]

```
johnw@JW-MediaServ:~$ sudo mdadm -D /dev/md5
[sudo] password for johnw: 
/dev/md5:
           Version : 1.2
     Creation Time : Sun May 17 20:19:05 2020
        Raid Level : raid5
        Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
     Used Dev Size : 1953382400 (1862.89 GiB 2000.26 GB)
      Raid Devices : 4
     Total Devices : 3
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Sun May 17 20:19:05 2020
             State : clean, degraded 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0


            Layout : left-symmetric
        Chunk Size : 512K


Consistency Policy : bitmap


              Name : JW-MediaServ:5  (local to host JW-MediaServ)
              UUID : 26dea2a8:7a9868a6:9dc927a9:4b48d1ee
            Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       64        0      active sync   /dev/sde
       1       8       80        1      active sync   /dev/sdf
       2       8       48        2      active sync   /dev/sdd
       -       0        0        3      removed



```

[QUOTE=darkod]Don't do anything else for the moment until you get more info. Wrong action can put your data in danger. And if md5 is not mounted right now, don't try to mount it yet.[/QUOTE]

Too late, I've already tried some stuff I googled that made sense to me, the result is what you see above.  Now when I tried to add /dev/sdb to the array, I get "mdadm: add new device failed for /dev/sdb as 4: Invalid argument". When I attempt to mount it, I get a different generally worded error that talks of lack of a partition table.  Lesson learned, I will not take further action until instructed to do so.

---

### Post by darkod on 2020-05-18
Give us again the member's superblocks:
```
sudo mdadm -E /dev/sd[def]
```

---

### Post by Slownis on 2020-05-18
```
johnw@JW-MediaServ:~$ sudo mdadm -E /dev/sd[def]
[sudo] password for johnw: 
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 26dea2a8:7a9868a6:9dc927a9:4b48d1ee
           Name : JW-MediaServ:5  (local to host JW-MediaServ)
  Creation Time : Sun May 17 20:19:05 2020
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=176 sectors
          State : clean
    Device UUID : 42cad468:4b4e48e3:867c4c1a:57cced19


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun May 17 20:19:05 2020
  Bad Block Log : 512 entries available at offset 16 sectors
       Checksum : c4d961a6 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAA. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 26dea2a8:7a9868a6:9dc927a9:4b48d1ee
           Name : JW-MediaServ:5  (local to host JW-MediaServ)
  Creation Time : Sun May 17 20:19:05 2020
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=176 sectors
          State : clean
    Device UUID : 5641c8d4:c87301c5:eb7aca56:568fb6ae


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun May 17 20:19:05 2020
  Bad Block Log : 512 entries available at offset 16 sectors
       Checksum : e3ccbf9a - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAA. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 26dea2a8:7a9868a6:9dc927a9:4b48d1ee
           Name : JW-MediaServ:5  (local to host JW-MediaServ)
  Creation Time : Sun May 17 20:19:05 2020
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 5860147200 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
    Data Offset : 264192 sectors
   Super Offset : 8 sectors
   Unused Space : before=264112 sectors, after=176 sectors
          State : clean
    Device UUID : 81244e01:ed645a74:3417ff76:d5fbe970


Internal Bitmap : 8 sectors from superblock
    Update Time : Sun May 17 20:19:05 2020
  Bad Block Log : 512 entries available at offset 16 sectors
       Checksum : a2139cb2 - correct
         Events : 0


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAA. ('A' == active, '.' == missing, 'R' == replacing)
```

---

### Post by Slownis on 2020-05-18
Here is the output of the blkid command you asked for before - not sure what all the squashfs is about:

```
johnw@JW-MediaServ:~$ sudo blkid
[sudo] password for johnw: 
/dev/sdc2: UUID="743bedfa-dc3a-4da3-b5f0-ccbd7cbe1324" TYPE="swap" PARTUUID="00045b39-02"
/dev/sda1: UUID="36245dc7-67ef-4b33-a88c-814a990340e7" TYPE="ext4" PARTUUID="c5766085-01"
/dev/sde: UUID="26dea2a8-7a98-68a6-9dc9-27a94b48d1ee" UUID_SUB="5641c8d4-c873-01c5-eb7a-ca56568fb6ae" LABEL="JW-MediaServ:5" TYPE="linux_raid_member"
/dev/sdf: UUID="26dea2a8-7a98-68a6-9dc9-27a94b48d1ee" UUID_SUB="81244e01-ed64-5a74-3417-ff76d5fbe970" LABEL="JW-MediaServ:5" TYPE="linux_raid_member"
/dev/sdd: UUID="26dea2a8-7a98-68a6-9dc9-27a94b48d1ee" UUID_SUB="42cad468-4b4e-48e3-867c-4c1a57cced19" LABEL="JW-MediaServ:5" TYPE="linux_raid_member"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda2: UUID="0e00cfc9-918a-422e-8136-e6f9e36498c0" TYPE="swap" PARTUUID="c5766085-02"
/dev/sda3: UUID="4a97b16f-ae23-45d5-8eb1-ee73ea78779e" TYPE="ext4" PARTUUID="c5766085-03"
/dev/sdc1: LABEL="System" UUID="6d3ac538-7e7e-4eae-8c54-16d7b97ff2ba" TYPE="ext4" PTTYPE="dos" PARTUUID="00045b39-01"
/dev/sdc4: LABEL="System 2" UUID="956fa07e-e6e0-4f82-af4e-e54524d4a2e8" TYPE="ext4" PTTYPE="dos" PARTUUID="00045b39-04"
/dev/sdc5: UUID="4f09994f-e439-4207-b067-627f5a4a4986" TYPE="swap" PARTUUID="00045b39-05"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"



```

---

### Post by darkod on 2020-05-18
F*ck, you overwrote the array... Don't do anything right now, if I understood correctly you never mounted the array, so you couldn't have written anything on it... And you never formatted /dev/md5 while trying to save it, right??

With little luck you can still save this. Next post follows, patience!

---

### Post by darkod on 2020-05-18
Forgot to add, stop the current md5 and just leave things as they are until I gather up the commands to use.
```
sudo mdadm --stop /dev/md5
```

---

### Post by darkod on 2020-05-18
OK. The problem here is that somehow you have created new blank array. Notice the values for "Array UUID" and "Creation time" between your first post and last:
Before:
```
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 52c035ba:7524c0e7:9ae73d40:d13ef8b4
           Name : johnw-desktop:5
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
   Raid Devices : 4
```

After:
```
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 26dea2a8:7a9868a6:9dc927a9:4b48d1ee
           Name : JW-MediaServ:5  (local to host JW-MediaServ)
  Creation Time : Sun May 17 20:19:05 2020
     Raid Level : raid5
   Raid Devices : 4
```

Here is now what you need to do to fix this. If you never mounted the array and started writing on it, there is big chance to save the data.

First stop the array if you already haven't:
```
sudo mdadm --stop /dev/md5
```

Then zero the superblocks on all members. They are from the new blank array so they are worthless anyway:
```
sudo mdadm --zero-superblock /dev/sdd
sudo mdadm --zero-superblock /dev/sde
sudo mdadm --zero-superblock /dev/sdf
```

Then, create new array but use the --assume-clean parameter which tells mdadm to read the existing data on the disks instead of creating blank array:
```
sudo mdadm --create --verbose --assume-clean /dev/md5 /dev/sdd /dev/sde /dev/sdf
```

Post the output of this last command so we can see it. Also if any of the previous commands fail, post the error message.

If md5 assembles with this last command, don't try to mount it yet. First lets see the output and then we'll consider the next step.

---

### Post by Slownis on 2020-05-18
> **darkod said:**
> OK. The problem here is that somehow you have created new blank array. Notice the values for "Array UUID" and "Creation time" between your first post and last:
Before:
```
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 52c035ba:7524c0e7:9ae73d40:d13ef8b4
           Name : johnw-desktop:5
  Creation Time : Wed Jan  8 17:58:05 2014
     Raid Level : raid5
   Raid Devices : 4
```

After:
```
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 26dea2a8:7a9868a6:9dc927a9:4b48d1ee
           Name : JW-MediaServ:5  (local to host JW-MediaServ)
  Creation Time : Sun May 17 20:19:05 2020
     Raid Level : raid5
   Raid Devices : 4
```

Here is now what you need to do to fix this. If you never mounted the array and started writing on it, there is big chance to save the data.

First stop the array if you already haven't:
```
sudo mdadm --stop /dev/md5
```

Then zero the superblocks on all members. They are from the new blank array so they are worthless anyway:
```
sudo mdadm --zero-superblock /dev/sdd
sudo mdadm --zero-superblock /dev/sde
sudo mdadm --zero-superblock /dev/sdf
```

Then, create new array but use the --assume-clean parameter which tells mdadm to read the existing data on the disks instead of creating blank array:
```
sudo mdadm --create --verbose --assume-clean /dev/md5 /dev/sdd /dev/sde /dev/sdf
```

Post the output of this last command so we can see it. Also if any of the previous commands fail, post the error message.

If md5 assembles with this last command, don't try to mount it yet. First lets see the output and then we'll consider the next step.

```
johnw@JW-MediaServ:~$ sudo mdadm --stop /dev/md5
[sudo] password for johnw: 
mdadm: stopped /dev/md5
johnw@JW-MediaServ:~$ sudo mdadm --zero-superblock /dev/sdd
johnw@JW-MediaServ:~$ sudo mdadm --zero-superblock /dev/sde
johnw@JW-MediaServ:~$ sudo mdadm --zero-superblock /dev/sdf
johnw@JW-MediaServ:~$ sudo mdadm --create --verbose --assume-clean /dev/md5 /dev/sdd /dev/sde /dev/sdf
mdadm: no raid-devices specified.

```

---

### Post by darkod on 2020-05-18
OK then, the long way. Modify the create to:
```
sudo mdadm --create --verbose --assume-clean --level=raid5 --raid-devices=4 --chunk=512K /dev/md5 /dev/sdd /dev/sde /dev/sdf missing
```

That tells it to create raid5 array of 4 members, and that one of them is missing right now. Should work better.

---

### Post by Slownis on 2020-05-18
Do I continue?
```
johnw@JW-MediaServ:~$ sudo mdadm --create --verbose --assume-clean --level=raid5 --raid-devices=4 --chunk=512K /dev/md5 /dev/sdd /dev/sde /dev/sdf missing
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: partition table exists on /dev/sdd
mdadm: partition table exists on /dev/sdd but will be lost or
       meaningless after creating array
mdadm: size set to 1953382400K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array?
```

Btw, this is close to what I tried before, minus the chunk=512k part, and I had the drives in /dev/sde, /dev/sdf, /dev/sdd order.  Does the drive order matter?

---

### Post by darkod on 2020-05-19
Yes, you should continue.

In theory the drive order shouldn't matter when using --assume-clean because it should be able to figure it out from the existing array data. But it's always best to put the drives in correct order if you know it.

In my command I put the order from the --examine results in your very first post.

Once you create the new md5, run again:
```
sudo blkid
```

You should see a line there for /dev/md5 and the detected filesystem. If it can detect a correct filesystem on md5, that's a good sign.

After that mount the array but read-only, no writing on it yet. Just to confirm if folder structure and data is there:
```
sudo mount -o ro /dev/md5 /mnt
ls /mnt
```

Assuming it mounts, browse and check around in /mnt to confirm the data you expect is there.

---

### Post by Slownis on 2020-05-19
sudo blkid doesn't show a line for /dev/md5:
```
johnw@JW-MediaServ:~$ sudo mdadm --create --verbose --assume-clean --level=raid5 --raid-devices=4 --chunk=512K /dev/md5 /dev/sdd /dev/sde /dev/sdf missing
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: partition table exists on /dev/sdd
mdadm: partition table exists on /dev/sdd but will be lost or
       meaningless after creating array
mdadm: size set to 1953382400K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md5 started.

```
```

johnw@JW-MediaServ:~$ sudo blkid
/dev/sdc2: UUID="743bedfa-dc3a-4da3-b5f0-ccbd7cbe1324" TYPE="swap" PARTUUID="00045b39-02"
/dev/sda1: UUID="36245dc7-67ef-4b33-a88c-814a990340e7" TYPE="ext4" PARTUUID="c5766085-01"
/dev/sde: UUID="398ca20a-5460-39bb-db39-c4b7a1b04a6f" UUID_SUB="8d6b1f08-9308-37fe-8282-8b1fab91745b" LABEL="JW-MediaServ:5" TYPE="linux_raid_member"
/dev/sdf: UUID="398ca20a-5460-39bb-db39-c4b7a1b04a6f" UUID_SUB="9722b399-af1f-dbb7-2bb0-b8ec49658767" LABEL="JW-MediaServ:5" TYPE="linux_raid_member"
/dev/sdd: UUID="398ca20a-5460-39bb-db39-c4b7a1b04a6f" UUID_SUB="9a7ab69e-3329-99d8-c974-40abd0ebd624" LABEL="JW-MediaServ:5" TYPE="linux_raid_member"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda2: UUID="0e00cfc9-918a-422e-8136-e6f9e36498c0" TYPE="swap" PARTUUID="c5766085-02"
/dev/sda3: UUID="4a97b16f-ae23-45d5-8eb1-ee73ea78779e" TYPE="ext4" PARTUUID="c5766085-03"
/dev/sdc1: LABEL="System" UUID="6d3ac538-7e7e-4eae-8c54-16d7b97ff2ba" TYPE="ext4" PTTYPE="dos" PARTUUID="00045b39-01"
/dev/sdc4: LABEL="System 2" UUID="956fa07e-e6e0-4f82-af4e-e54524d4a2e8" TYPE="ext4" PTTYPE="dos" PARTUUID="00045b39-04"
/dev/sdc5: UUID="4f09994f-e439-4207-b067-627f5a4a4986" TYPE="swap" PARTUUID="00045b39-05"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"

```

---

### Post by Slownis on 2020-05-19
New SMART results for /dev/sdb:


```
johnw@JW-MediaServ:~$ sudo smartctl -a /dev/sdb
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-29-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-22MVWB0
Serial Number:    WD-WMAZA4770810
LU WWN Device Id: 5 0014ee 002c80ebc
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Tue May 19 11:44:16 2020 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		(38580) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 372) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       78
  3 Spin_Up_Time            0x0027   253   190   021    Pre-fail  Always       -       1141
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5598
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   062   062   000    Old_age   Always       -       27960
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       5546
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       755
193 Load_Cycle_Count        0x0032   135   135   000    Old_age   Always       -       195552
194 Temperature_Celsius     0x0022   123   102   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       126
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       129
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       33


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


Error 3 occurred at disk power-on lifetime: 348 hours (14 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 00 00 00 00  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d6 01 e0 4f c2 00 08      00:22:02.268  SMART WRITE LOG
  ec 00 01 00 00 00 00 08      00:15:33.340  IDENTIFY DEVICE
  b0 d5 01 e1 4f c2 00 08      00:15:33.338  SMART READ LOG
  b0 d6 01 e0 4f c2 00 08      00:15:33.338  SMART WRITE LOG


Error 2 occurred at disk power-on lifetime: 347 hours (14 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 00 00 00 00  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d5 01 e1 4f c2 00 08      00:15:33.338  SMART READ LOG
  b0 d6 01 e0 4f c2 00 08      00:15:33.338  SMART WRITE LOG


Error 1 occurred at disk power-on lifetime: 347 hours (14 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 01 00 00 00 00  Error: ABRT


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  b0 d6 01 e0 4f c2 00 08      00:15:33.338  SMART WRITE LOG


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     27936         9


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

### Post by darkod on 2020-05-19
Unfortunately looks like you ended up with blank array...

You can check if it's really started with:
```
cat /proc/mdstat
sudo mdadm -D /dev/md5
```

But it doesn't look good so far unfortunately.

Do you have any history or documentation which mdadm commands you executed before you opened this thread?

---

### Post by Slownis on 2020-05-19
```
johnw@JW-MediaServ:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md5 : active raid5 sdf[2] sde[1] sdd[0]
      5860147200 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]
      bitmap: 0/15 pages [0KB], 65536KB chunk


unused devices: <none>
```

I can tell you that I never *SUCCESSFULLY* mounted the array.  I did reboot once, and it came back as md127.  I have stopped it multiple times and tried a very similar command to what you gave me in attempts to rebuild it.

I tried [COLOR=#242729][FONT=Consolas]mdadm --manage /dev/md5 --re-add /dev/sdb multiple times with no success.

I spent some time reading this:  [/FONT][/COLOR][https://www.linuxquestions.org/questions/linux-server-73/mdadm-error-replacing-a-failed-disk-909577/](https://www.linuxquestions.org/questions/linux-server-73/mdadm-error-replacing-a-failed-disk-909577/)

Which led me to try 
```
[COLOR=#000000]
mdadm --create /dev/md5 --assume-clean --level=5 --verbose --raid-devices=4 /dev/sde /dev/sdf /dev/sdd missing[/COLOR]
```[COLOR=#000000]

I tried that multiple times, but was never able to successfully mount.[/COLOR]

---

### Post by darkod on 2020-05-20
Try to mount it RO with:
```
sudo mount -o ro /dev/md5 /mnt
```

But I doubt it will work. I don't know what to say, the commands you specify above shouldn't have hurt the original array.

The --re-add can't destroy it, and the --create when using --assume-clean also can't destroy the data.

Despite this, it looks like there is no filesystem on md5 now because blkid can't detect it. If there really is no filesystem, any mount command will fail of course.

---

### Post by Slownis on 2020-05-20
Now it seems like mount is getting frustrated with me..... ](*,)

```
johnw@JW-MediaServ:~$ sudo mount -o ro /dev/md5 /mnt
NTFS signature is missing.
Failed to mount '/dev/md5': Invalid argument
The device '/dev/md5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

What else can I try?  Anything I can do to rescue /dev/sdb?  I've read where people have made copies of failed arrays using dd for all the discs in the array and tried things using a virtual install.  Is that where I'm at?

---

### Post by darkod on 2020-05-20
Weird that mount is trying to use NTFS. Usually when no type is specified it should try ext4. What filesystem type di you have on the old /dev/md5? Also, were you using anything else, like LVM etc?

Unfortunately I don't see a way out of this. Your problem is not with the disks, it is with the fact that the array on them looks empty. Like if you created new array at one point forgetting to use --assume-clean. If you still had your original array data on the disks you would be able to easily assemble raid5 with three members out of four. It can work correctly with one member missing. However the data does not seem to be there.

I don't know if there are any deeper rescue steps to try save the raid.

Rescue of sdb won't help much, it is only one raid member out of four.

---

### Post by Slownis on 2020-05-20
I ran smartctl for the other three discs.  Looks like /dev/sde also has issues:

```
johnw@JW-MediaServ:~$ sudo smartctl -a /dev/sde
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-29-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Green
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WCAZAF087441
LU WWN Device Id: 5 0014ee 104bd2049
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Wed May 20 19:36:22 2020 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(37800) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 364) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   198   198   051    Pre-fail  Always       -       32314
  3 Spin_Up_Time            0x0027   178   171   021    Pre-fail  Always       -       6075
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       231
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   021   021   000    Old_age   Always       -       57726
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       231
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       156
193 Load_Cycle_Count        0x0032   094   094   000    Old_age   Always       -       320615
194 Temperature_Celsius     0x0022   125   110   000    Old_age   Always       -       25
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
**[COLOR=#ff0000]197 Current_Pending_Sector  0x0032   191   191   000    Old_age   Always       -       2988[/COLOR]**
198 Offline_Uncorrectable   0x0030   200   197   000    Old_age   Offline      -       0
[COLOR=#ff0000]**199 UDMA_CRC_Error_Count    0x0032   200   137   000    Old_age   Always       -       41284**[/COLOR]
200 Multi_Zone_Error_Rate   0x0008   200   001   000    Old_age   Offline      -       10


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
Should I do the extended self test on this drive too?

The other two drives look clean, with no pending sector.

---

### Post by darkod on 2020-05-21
The drives might be old but according to the --examine output in your first post, it looks like the superblock and the array was still good on three of them at that time. It remains unclear when did it change.

About the drives, if two of them show prefail or fail status in SMART what you do with them is your choice. You can get new drives but that doesn't help you in getting the data.

Do you have sufficiently good backup to forget about saving the data from this array and start from scratch with new array?

---

### Post by Slownis on 2020-05-24
No, backups do not exist :(.  18 years of pictures and home videos lost.

---

### Post by Slownis on 2020-05-31
> **darkod said:**
> Try to mount it RO with:
```
sudo mount -o ro /dev/md5 /mnt
```

But I doubt it will work. I don't know what to say, the commands you specify above shouldn't have hurt the original array.

The --re-add can't destroy it, and the --create when using --assume-clean also can't destroy the data.

Despite this, it looks like there is no filesystem on md5 now because blkid can't detect it. If there really is no filesystem, any mount command will fail of course.

Can I run fsck on /dev/md5?  Is there any possibility that it will fix the ext4 filesystem?  This seems to suggest it could work:  [https://wiki.sabayon.org/index.php?title=HOWTO:_Repair_filesystem_using_fsck_on_a_raid_setup](https://wiki.sabayon.org/index.php?title=HOWTO:_Repair_filesystem_using_fsck_on_a_raid_setup)

---

### Post by darkod on 2020-05-31
You can try it but it doesn't look like it can detect any ext4 on md5. First run it with -n to only report possible found problems, not to try and repair anything. Something like:
```
sudo fsck -n /dev/md5
```

We still don't know what exactly happened here. This was not just disk failure. One disk failed in raid5 is no problem at all, the array shouldn't even stop because of that.

---

### Post by Slownis on 2020-05-31
```
johnw@JW-MediaServ:/$ sudo fsck -n /dev/md5
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md5


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

---

### Post by darkod on 2020-06-01
Well it doesn't look like it is detecting any ext4 filesystem, same like blkid not showing any ext4 on md5.

---

### Post by Slownis on 2020-06-01
Yeah, I'm close to giving up.  Any recommended data recovery specialists?

---

### Post by darkod on 2020-06-01
No, no specialist that I can recommend.

If you wanna try some recovery yourself, one option is Photorec. [https://www.cgsecurity.org/wiki/PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec)

I haven't used it myself but people have mentioned it here. It has step by step on its website, I suppose it's good enough to start with.

One important note is that even if it recovers some data it will not retrieve filenames. So you will have to browse through all recovered files later and get them in order somehow. But I assume that is something you can accept if it means getting most of the data back.

Also, I assume you will need new storage with at least the same size of the current data array because Photorec will need somewhere to write. You should find that info on its website.

You can search yourself on Google for other SW, free or paid for, and it will probably be cheaper than specialists.

Not to rub salt on the wound, but just a reminder that you would probably have more options if you used partitions with mdadm. For example the same company that created Photorec has a program called Testdisk which can recover lost partitions. In theory if you had the chance to recover an earlier partition on the disks maybe you would have had more options to bring back your data. But you had no partitions so nothing that can be retrieved. Always make sure you use partitions with mdadm.

---

### Post by Slownis on 2020-06-04
I poked around on the site you mentioned.  I decided to mess around with testdisk before doing the photorec.

I ran testdisk's analysis against /dev/md5 with the 3 hard drives and one missing drive.  I let it run overnight and came back to this:

```

TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
[https://www.cgsecurity.org]("https://www.cgsecurity.org/")


Disk /dev/md5 - 6000 GB / 5588 GiB - CHS 1465036800 2 4


The harddisk (6000 GB / 5588 GiB) seems too small! (< 7020024 TB / 6384675 TiB)
Check the harddisk size: HD jumper settings, BIOS detection...


The following partitions can't be recovered:
Partition Start End Size in sectors
> ext4 243825794 0 1 1708863361 1 4 11720300544 [Raid]
ext4 243826050 0 1 1708863617 1 4 11720300544 [Raid]
WBFS 255470375 1 4 970938407 1 3 108802959360
WBFS 708675995 1 3 473794971 1 2 430216405057536
btrfs 779385571 0 4 899379525 0 4 13710979677795088 [(%d stripes (%d substripes) of %l
WBFS 785014222 0 2 3737804238 0 1 11309634585362432
NTFS 976690815 1 4 1465069183 1 3 3907026944
NTFS 976690943 1 4 1465069311 1 3 3907026944






[ Continue ]
ext4 blocksize=4096 Large_file Sparse_SB Recover, 6000 GB / 5588 GiB
```

```

TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org


Disk /dev/md5 - 6000 GB / 5588 GiB - CHS 1465036800 2 4
     Partition               Start        End    Size in sectors
>P NTFS                  8886   1  4 153782   1  3    1159168
 P FAT12                78189262   0  1 78189853   1  4       4736 [EFI System Partition] [NO NAME]
 P HFSX                 125877637   0  1 164193658   1  4  306528176
 P Sys=0C               266576856   1  3 267100112   1  2    4186048
 P HFS                  282242255   1  4 282242325   0  4        557
 P HFS                  321371368   1  1 658448874   0  1 2696620045 [\M-&~]nj ~U~XAfM-=M-'&^O ^KT]
 P Linux md 1.x RAID    488312448   0  1 976690768   1  4 3907026568 [johnw-desktop:0]
 P NTFS                 488312448   0  1 976690815   1  4 3907026944
 P Linux md 1.x RAID    488312576   0  1 976690896   1  4 3907026568 [johnw-desktop:0]
 P NTFS                 488312576   0  1 976690943   1  4 3907026944
 P FAT32                717379687   0  1 721130856   1  1   30009357 [GIGGEM]
 P FAT12                722320720   0  1 722321079   1  4       2880 [BOOTTEST]
 P HFSX                 725164154   1  1 763480176   0  4  306528176
 P HFS+                 765715848   0  1 765741447   1  4     204800
 P HFS+                 766379400   0  1 766427565   1  4     385328
 P HFS+                 766431654   1  3 766479820   1  2     385328
 P FAT12                779384873   0  1 779384984   1  4        896
 P FAT12                793820166   0  1 793822758   0  3      20739 [NO NAME]
 P HFS                  826224913   1  1 827273489   1  2    8388610 [~?~?~?M-:D^A]
 P HFS                  828432396   1  4 828440589   0  1      65538
 P FAT12                829857076   0  1 829857435   1  4       2880 [EFI System Partition] [EFISECTOR]
 P NTFS                 829860770   0  4 829861542   0  1       6174
 P NTFS                 829861542   0  1 829862313   1  2       6174 [Boot]
 P NTFS                 829861544   0  4 829862316   0  1       6174
 P NTFS                 829862316   0  1 829863087   1  2       6174 [Boot]
 P NTFS                 829862318   0  4 829863090   0  1       6174
 P NTFS                 829863090   0  1 829863861   1  2       6174 [Boot]
 P FAT12                829863966   0  1 829864325   1  4       2880 [EFI System Partition] [EFISECTOR]
 P FAT12                831170425   0  4 831173017   1  2      20739 [NO NAME]
 P FAT12                831508826   0  1 831509185   1  4       2880 [EFI System Partition] [EFISECTOR]
 P HFS                  834850330   0  2 834858522   0  3      65538
Structure: Ok.




Keys T: change type, P: list files,
     Enter: to continue
NTFS, blocksize=4096, 593 MB / 566 MiB

```
Although it says none of the file system candidates are recoverable, testdisk allows you to go in and look at the possible file systems and even files it has identified within those candidates.

When I go in and look at the second one listed I find these files:
```

TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org
   P FAT12                78189262   0  1 78189853   1  4       4736 [EFI System Partition] [NO NAME]
Directory /EFI/BOOT


>drwxr-xr-x     0     0         0 19-Jul-2016 17:18 .
 drwxr-xr-x     0     0         0 19-Jul-2016 17:18 ..
 -rwxr-xr-x     0     0   1289424 19-Jul-2016 17:18 BOOTX64.EFI
 -rwxr-xr-x     0     0   1099128 19-Jul-2016 17:18 GRUBX64.EFI

```

Seems like it found some junk from an issue I had back in 2016 when I did an upgrade to 16.04. Here is the post I made back then:  [https://ubuntuforums.org/showthread.php?t=2337339](https://ubuntuforums.org/showthread.php?t=2337339)
My solution then was to fail and remove /dev/sdb and then add it back and let it rebuild, which worked like a champ.  You'lld think I would have learned something back then and made a backup, but no, as soon as I had my array back I went along my merry way.  I'll continue looking at the other identified partitions to see what other files it has identified.

---

### Post by darkod on 2020-06-04
Honestly I don't know if testdisk can be used again mdadm arrays. The thing is that array is not all on the same disk (not counting raid1). The point of testdisk is to scan the HDD and restore older partition on that HDD.

But I haven't heard of it being used across multiple HDDs. I assume that is why it says those ext4 partitions are unrecoverable.

This is why in previous posts I mentioned it would probably be easier to recover some data if you had used partitions. In such case you can try restoring partitions to the HDDs in question, and then assemble/recreate new array from those partitions.

Anyway, take a look at testdisk and photorec and see what you find out.

---

### Post by TheFu on 2020-06-04
> **Slownis said:**
> Yeah, I'm close to giving up.  Any recommended data recovery specialists?

[http://myharddrivedied.com/](http://myharddrivedied.com/)  Scott trains lots of other data recovery people around the US and he has all the equipment necessary.  I haven't spoken to him in a few years, but attended a data recovery/forensics overview session at OuterZ0ne and was highly impressed.

But you REALLY have to want this data back. It isn't cheap. There's no guarantee.

I have doubts about photorec working on RAID volumes, but I don't know.  I've used it a few times, immediately after realizing I'd deleted files that weren't on a backup, just on temporary "work" storage.

---

### Post by Slownis on 2020-06-27
I would like to thank everyone who helped in this thread.  I have recovered every bit of data.

@TheFu:  Thanks so much for that link.  That got me digging around in Scotts online resources, which pointed me to some different recovery software options.  There was a specific PDF about raid recovery that was VERY helpful.

@darkod: Thanks so much for all your guidance.  I probably ruined any chance at an easy recovery before I started to heed your advice.

I had to use windows to recover the data - the raid recovery options I found didn't have a Linux variant, but some (like File Scavenger) are able to read from EXT3/4 partitions to recover the data from within windows.

Here is what I did to recover the data:
1) Purchase a 6TB drive to copy the rescued data to.  I went with a Toshiba NAS drive - seems like it gets decent reviews.
2) Create USB install media for Windows 10 on a USB thumb stick: [FONT=Verdana]https://support.microsoft.com/en-us/help/15088/windows-10-create-installation-media, using a separate windows laptop.
3) Replaced the UBUNTU system drive with a spare laptop drive that I wasn't using.
4) Installed windows 10 on the laptop drive using the USB stick.  I also installed the new 6TB drive, along with the 4 disks from the original array, so all 6 SATA ports are being used on my rig.[/FONT]
5) Tried various windows raid recovery softwares:[INDENT]1) The first one I tried was [Raid Reconstructor]("http://runtime.org/raid.htm") from Runtime Software.  This was recommended in Scott's presentation, and seems very advanced.  I might have been able to use this, but after several tries I wasn't able to determine the correct parameters.
2) The next one I tried was ReclaiMe's, [free Raid recovery tool]("http://www.freeraidrecovery.com/default.aspx").  It has a simpler user interface, and it correctly identified the drive order.  The cool thing is that it provides information about the parameters to use for several other recovery tools, including Reclaime File Recovery.  It got everything correct, except for the data offset which it identified as zero.
3) Using the identified parameters in ReclaiMe's Raid recovery, I ran [Reclaime's File recovery tool]("https://www.reclaime.com/default.aspx"), which has a free version that allows you to see what you can get.  The paid version allows you to copy the files somewhere.  In messing the with free version, it was able to find tons of files, but it couldn't tell they were part of an EXT4 partition, and thus there was no folder structure or metadata (including file name, date, etc).  Also, the jpeg previews were striped, or incomplete.  Getting closer......
4) I then tried [File Scavenger]("http://www.quetek.com/") using the parameters from ReclaiMe's Raid recovery tool, but on a whim I changed the offset sectors to a different value that I found in an old ubuntu forum post where I was asking for help with the array several years ago.  File Scavenger then correctly identified the EXT4 partition, and I was able to see the entire folder structure and preview the files.  Once I saw that I happily paid the $99 license for the Premium version (required for RAID recovery).  Using File Scavenger, I'm copying all the data from the ext4 partion on the 3 remaining disks of the array directly to the 6TB drive, which I have formatted to NTFS since I'm in windows.  I'll determine a better storage solution once I figure out which disks I want to replace, etc.
[/INDENT]

---

### Post by darkod on 2020-06-27
Great news. First step is always saving the data first. :)

After that you can dive into planning how to construct the new array.

---

### Post by TheFu on 2020-06-28
Imagine how much easier all this would have been with a simple backup. The time, effort, worry, all gone.
RAID is never a backup solution.

---

