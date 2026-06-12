---
title: "mdadm RAID5 array 2 drives removed"
date: 2018-07-19
forum: Server Platforms
---

### Post by vwlinux on 2018-07-19
Hi.

I have 12 disks in a RAID5 array with mdadm.
Disks in raid: sd(bcdefghijklm)
Array: md0

Disk sdi failed and needed to get replaced.
I replaced with a new disk and resynced array.
While resync i lost a nother disk: sde.

Here is the output of cat /proc/mdstat:

```

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[0] sdi1[14](S) sdj1[13] sdl1[12] sdg1[9] sde1[8](F) sdm1[7] sdk1[6] sdd1[11] sdf1[3] sdb1[2] sdh1[1]
      32232904704 blocks super 1.2 level 5, 512k chunk, algorithm 2 [12/10] [UUUUUUU_U_UU]

unused devices: <none>

```

Here is the output of mdadm -D /dev/md0:

```

# mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
  Used Dev Size : 2930264064 (2794.52 GiB 3000.59 GB)
   Raid Devices : 12
  Total Devices : 12
    Persistence : Superblock is persistent

    Update Time : Thu Jul 19 05:16:36 2018
          State : clean, FAILED
 Active Devices : 10
Working Devices : 11
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ingfil:0  (local to host ingfil)
           UUID : 9c5baecf:58212783:fe438251:3b70e113
         Events : 870676

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8      113        1      active sync   /dev/sdh1
       2       8       17        2      active sync   /dev/sdb1
       3       8       81        3      active sync   /dev/sdf1
      11       8       49        4      active sync   /dev/sdd1
       6       8      161        5      active sync   /dev/sdk1
       7       8      193        6      active sync   /dev/sdm1
       7       0        0        7      removed
       9       8       97        8      active sync   /dev/sdg1
       9       0        0        9      removed
      12       8      177       10      active sync   /dev/sdl1
      13       8      145       11      active sync   /dev/sdj1

       8       8       65        -      faulty spare   /dev/sde1
      14       8      129        -      spare   /dev/sdi1

```

Output of smartctl -x /dev/sde:
```

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Red (AF)
Device Model:     WDC WD30EFRX-68EUZN0
Serial Number:    WD-WMC4N1007575
LU WWN Device Id: 5 0014ee 6594ee571
Firmware Version: 80.00A80
User Capacity:    3*000*592*982*016 bytes [3,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Jul 19 17:23:32 2018 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM feature is:   Unavailable
Rd look-ahead is: Enabled
Write cache is:   Enabled
ATA Security is:  Disabled, NOT FROZEN [SEC1]
Wt Cache Reorder: Enabled

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
data collection:                (40320) seconds.
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
recommended polling time:        ( 404) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x703d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR-K   200   200   051    -    7
  3 Spin_Up_Time            POS--K   183   170   021    -    5841
  4 Start_Stop_Count        -O--CK   100   100   000    -    344
  5 Reallocated_Sector_Ct   PO--CK   200   200   140    -    0
  7 Seek_Error_Rate         -OSR-K   200   200   000    -    0
  9 Power_On_Hours          -O--CK   051   051   000    -    36167
 10 Spin_Retry_Count        -O--CK   100   100   000    -    0
 11 Calibration_Retry_Count -O--CK   100   100   000    -    0
 12 Power_Cycle_Count       -O--CK   100   100   000    -    185
192 Power-Off_Retract_Count -O--CK   200   200   000    -    103
193 Load_Cycle_Count        -O--CK   001   001   000    -    962848
194 Temperature_Celsius     -O---K   118   097   000    -    32
196 Reallocated_Event_Count -O--CK   200   200   000    -    0
197 Current_Pending_Sector  -O--CK   200   200   000    -    1
198 Offline_Uncorrectable   ----CK   100   253   000    -    0
199 UDMA_CRC_Error_Count    -O--CK   200   200   000    -    0
200 Multi_Zone_Error_Rate   ---R--   100   253   000    -    0
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x01           SL  R/O      1  Summary SMART error log
0x02           SL  R/O      5  Comprehensive SMART error log
0x03       GPL     R/O      6  Ext. Comprehensive SMART error log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      1  Extended self-test log
0x09           SL  R/W      1  Selective self-test log
0x10       GPL     R/O      1  NCQ Command Error log
0x11       GPL     R/O      1  SATA Phy Event Counters
0x21       GPL     R/O      1  Write stream error log
0x22       GPL     R/O      1  Read stream error log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xa0-0xa7  GPL,SL  VS      16  Device vendor specific log
0xa8-0xb7  GPL,SL  VS       1  Device vendor specific log
0xbd       GPL,SL  VS       1  Device vendor specific log
0xc0       GPL,SL  VS       1  Device vendor specific log
0xc1       GPL     VS      93  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (6 sectors)
Device Error Count: 4
        CR     = Command Register
        FEATR  = Features Register
        COUNT  = Count (was: Sector Count) Register
        LBA_48 = Upper bytes of LBA High/Mid/Low Registers ]  ATA-8
        LH     = LBA High (was: Cylinder High) Register    ]   LBA
        LM     = LBA Mid (was: Cylinder Low) Register      ] Register
        LL     = LBA Low (was: Sector Number) Register     ]
        DV     = Device (was: Device/Head) Register
        DC     = Device Control Register
        ER     = Error register
        ST     = Status register
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 4 [3] occurred at disk power-on lifetime: 36155 hours (1506 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 01 4e 8f fb 28 40 00  Error: UNC at LBA = 0x14e8ffb28 = 5613026088

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 01 40 00 80 00 01 4e 90 05 e8 40 08  1d+05:58:34.051  READ FPDMA QUEUED
  60 04 00 00 78 00 01 4e 90 01 e8 40 08  1d+05:58:34.051  READ FPDMA QUEUED
  60 00 40 00 70 00 01 4e 8f fd a8 40 08  1d+05:58:34.010  READ FPDMA QUEUED
  60 00 80 00 68 00 01 4e 8f fd 28 40 08  1d+05:58:34.010  READ FPDMA QUEUED
  60 00 80 00 60 00 01 4e 8f fc a8 40 08  1d+05:58:34.010  READ FPDMA QUEUED

Error 3 [2] occurred at disk power-on lifetime: 36155 hours (1506 days + 11 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 fe 00 01 4e 8f fb 28 40 00  Error: UNC at LBA = 0x14e8ffb28 = 5613026088

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 04 00 00 30 00 01 4e 8f f9 e8 40 08  1d+05:58:30.229  READ FPDMA QUEUED
  60 04 00 00 28 00 01 4e 8f f5 e8 40 08  1d+05:58:30.221  READ FPDMA QUEUED
  60 04 00 00 20 00 01 4e 8f f1 e8 40 08  1d+05:58:30.213  READ FPDMA QUEUED
  60 04 00 00 18 00 01 4e 8f ed e8 40 08  1d+05:58:30.209  READ FPDMA QUEUED
  60 04 00 00 10 00 01 4e 8f e9 e8 40 08  1d+05:58:30.201  READ FPDMA QUEUED

Error 2 [1] occurred at disk power-on lifetime: 36132 hours (1505 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 01 4e 8f fb 28 40 00  Error: UNC at LBA = 0x14e8ffb28 = 5613026088

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 04 00 00 a8 00 01 4e 94 db 78 40 08     07:33:08.137  READ FPDMA QUEUED
  60 04 00 00 b0 00 01 4e 94 d7 78 40 08     07:33:08.132  READ FPDMA QUEUED
  60 04 00 00 c0 00 01 4e 94 d3 78 40 08     07:33:08.125  READ FPDMA QUEUED
  60 04 00 00 c8 00 01 4e 94 cf 78 40 08     07:33:08.120  READ FPDMA QUEUED
  60 04 00 00 d0 00 01 4e 94 cb 78 40 08     07:33:08.113  READ FPDMA QUEUED

Error 1 [0] occurred at disk power-on lifetime: 36132 hours (1505 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 01 00 01 4e 8f fb 28 40 00  Error: UNC at LBA = 0x14e8ffb28 = 5613026088

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 04 00 00 88 00 01 4e 90 17 78 40 08     07:33:01.999  READ FPDMA QUEUED
  60 04 00 00 80 00 01 4e 90 13 78 40 08     07:33:01.999  READ FPDMA QUEUED
  60 04 00 00 78 00 01 4e 90 0f 78 40 08     07:33:01.999  READ FPDMA QUEUED
  60 04 00 00 70 00 01 4e 90 0b 78 40 08     07:33:01.999  READ FPDMA QUEUED
  60 04 00 00 68 00 01 4e 90 07 78 40 08     07:33:01.999  READ FPDMA QUEUED

SMART Extended Self-test Log Version: 1 (1 sectors)
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

SCT Status Version:                  3
SCT Version (vendor specific):       258 (0x0102)
SCT Support Level:                   1
Device State:                        Active (0)
Current Temperature:                    32 Celsius
Power Cycle Min/Max Temperature:     30/38 Celsius
Lifetime    Min/Max Temperature:     -2/54 Celsius
Under/Over Temperature Limit Count:   0/0
SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:      0/60 Celsius
Min/Max Temperature Limit:           -41/85 Celsius
Temperature History Size (Index):    478 (367)

Index    Estimated Time   Temperature Celsius
 368    2018-07-19 09:26    32  *************
 ...    ..(476 skipped).    ..  *************
 367    2018-07-19 17:23    32  *************

SCT Error Recovery Control:
           Read:     70 (7,0 seconds)
          Write:     70 (7,0 seconds)

Device Statistics (GP Log 0x04) not supported

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0002  2            0  R_ERR response for data FIS
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0005  2            0  R_ERR response for non-data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
0x0008  2            0  Device-to-host non-data FIS retries
0x0009  2            3  Transition from drive PhyRdy to drive PhyNRdy
0x000a  2            4  Device-to-host register FISes sent due to a COMRESET
0x000b  2            0  CRC errors within host-to-device FIS
0x000f  2            0  R_ERR response for host-to-device data FIS, CRC
0x0012  2            0  R_ERR response for host-to-device non-data FIS, CRC
0x8000  4       151491  Vendor specific


```



Is it possible to save the array?

---

### Post by darkod on 2018-07-20
First, 12 disks is way too many for raid5. You need at least 2 disk redundancy. Even more if possible...

You should be able to bring the array online. First take a deeper look into each member superblock info:
```
sudo mdadm -E /dev/sd[bcdefghijklm]1
```

That will show you Event counters which are important to figure out how up to date each member is. After you post that output we can advise more...

---

### Post by vwlinux on 2018-07-20
I know this.
Was going to move all data to new server.
Thank you for your reply.

Here is the output of the mdadm -E /dev/sd[bcdefghijklm]1

```

# mdadm -E /dev/sd[bcdefghijklm]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : bd70c6e3:6f0536d1:3cdc907d:cba8a589

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : 1c74c438 - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 571efc24:34a91143:075d21f8:ca040d3b

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : fb7df25d - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f75ff05b:e15fbf7c:d712c3c0:aedf87d8

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : d23c7b6a - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ff5db992:40dc1d0a:46c8b0be:df02baa5

    Update Time : Thu Jul 19 05:15:33 2018
       Checksum : 6181ce3e - correct
         Events : 870672

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 7
   Array State : AAAAAAAAAAAA ('A' == active, '.' == missing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 6599e8ed:dddecd34:76a41633:fb5fbb58

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : eca45b8 - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b050efc5:c7e92c1b:b700de78:043bafb7

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : 71eb3f3d - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 8
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fd99f2f3:a9e46376:3ddfcc1b:f9baff23

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : a64e1df - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860529005 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
  Used Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a8da1419:de490f38:6e2519d8:35887114

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : 9df0a6a5 - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : spare
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860529005 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
  Used Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f4c9feba:470c018d:99a83fcc:5fc18c66

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : db0e14af - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 11
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdk1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1c15eb5c:751ded1b:e5837644:4393b5af

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : cd4612c0 - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdl1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 15070871:74c810a5:5491dfaa:3794a736

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : 57e1be22 - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 10
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)
/dev/sdm1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9c5baecf:58212783:fe438251:3b70e113
           Name : ingfil:0  (local to host ingfil)
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
   Raid Devices : 12

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a75f6f2a:bc3db33a:40bd7b6b:b1e75168

    Update Time : Thu Jul 19 05:16:36 2018
       Checksum : 99320b5c - correct
         Events : 870676

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 6
   Array State : AAAAAAA.A.AA ('A' == active, '.' == missing)

```

---

### Post by darkod on 2018-07-20
Hmmm, this should be easy... All of your members (including sdi1) report 870676 events counter, except sde1 which says 870672. The only difference with sdi1 seems to be that it is marked as spare right now, out of what ever reason. But if its counter is really 870676, it should fit into the array just nicely.

First stop the array and try to force assemble it leaving sde1 out for the moment:
```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble --verbose --force /dev/md0 /dev/sd[bcdfghijklm]1
```

Follow the messages it is giving you during the assemble and lets see how that goes...

---

### Post by vwlinux on 2018-07-21
Here is the output of the command:
```

# mdadm --assemble --verbose --force /dev/md0 /dev/sd[bcdfghijklm]1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 8.
mdadm: /dev/sdh1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdi1 is identified as a member of /dev/md0, slot -1.
mdadm: /dev/sdj1 is identified as a member of /dev/md0, slot 11.
mdadm: /dev/sdk1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdl1 is identified as a member of /dev/md0, slot 10.
mdadm: /dev/sdm1 is identified as a member of /dev/md0, slot 6.
mdadm: added /dev/sdh1 to /dev/md0 as 1
mdadm: added /dev/sdb1 to /dev/md0 as 2
mdadm: added /dev/sdf1 to /dev/md0 as 3
mdadm: added /dev/sdd1 to /dev/md0 as 4
mdadm: added /dev/sdk1 to /dev/md0 as 5
mdadm: added /dev/sdm1 to /dev/md0 as 6
mdadm: no uptodate device for slot 7 of /dev/md0
mdadm: added /dev/sdg1 to /dev/md0 as 8
mdadm: no uptodate device for slot 9 of /dev/md0
mdadm: added /dev/sdl1 to /dev/md0 as 10
mdadm: added /dev/sdj1 to /dev/md0 as 11
mdadm: added /dev/sdi1 to /dev/md0 as -1
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 10 drives and 1 spare - not enough to start the array.

```

Is it possible to get the /dev/sdi1 included to be able to start the array?

/dev/sdi1 is the disk that i replaced.

---

### Post by vwlinux on 2018-07-21
Here is the output of mdadm.conf

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md/0 metadata=1.2 UUID=9c5baecf:58212783:fe438251:3b70e113 name=myserver:0

# This file was auto-generated on Wed, 21 May 2014 11:57:09 +0200
# by mkconf $Id$
ARRAY /dev/md/0 metadata=1.2 UUID=9c5baecf:58212783:fe438251:3b70e113 name=myserver:0 spares=1

```

I run this command:
```

mdadm --examine --scan >> /etc/mdadm/mdadm.conf

```

Before i had no spare in the array.
I think sdi1 is set to spare because is was not finished with rebuild.
Could this be the case?

---

### Post by darkod on 2018-07-21
I am not sure what happened during the rebuild. The counter for sdi1 looked OK, but I am not 100% sure how it should look if the rebuild didn't complete.

You can try assembling the array using sde1 instead of sdi1 in that same command. The counter for sde1 is very close, and it should start... Don't forget to stop the array first.

That is what I would try next. To run those same commands only with sde1 instead of sdi1 in the member list.

---

### Post by vwlinux on 2018-07-22
Here is the output of command with sde instead of sdi:

```

# mdadm --assemble --verbose --force /dev/md0 /dev/sd[bcdefghjklm]1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 7.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 8.
mdadm: /dev/sdh1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdj1 is identified as a member of /dev/md0, slot 11.
mdadm: /dev/sdk1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdl1 is identified as a member of /dev/md0, slot 10.
mdadm: /dev/sdm1 is identified as a member of /dev/md0, slot 6.
mdadm: forcing event count in /dev/sde1(7) from 870672 upto 870676
mdadm: clearing FAULTY flag for device 3 in /dev/md0 for /dev/sde1
mdadm: Marking array /dev/md0 as 'clean'
mdadm: added /dev/sdh1 to /dev/md0 as 1
mdadm: added /dev/sdb1 to /dev/md0 as 2
mdadm: added /dev/sdf1 to /dev/md0 as 3
mdadm: added /dev/sdd1 to /dev/md0 as 4
mdadm: added /dev/sdk1 to /dev/md0 as 5
mdadm: added /dev/sdm1 to /dev/md0 as 6
mdadm: added /dev/sde1 to /dev/md0 as 7
mdadm: added /dev/sdg1 to /dev/md0 as 8
mdadm: no uptodate device for slot 9 of /dev/md0
mdadm: added /dev/sdl1 to /dev/md0 as 10
mdadm: added /dev/sdj1 to /dev/md0 as 11
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 11 drives - not enough to start the array.

```

Here is the output of cat /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdc1[0](S) sdj1[13](S) sdl1[12](S) sdg1[9](S) sde1[8](S) sdm1[7](S) sdk1[6](S) sdd1[11](S) sdf1[3](S) sdb1[2](S) sdh1[1](S)
      32232905142 blocks super 1.2

unused devices: <none>

```

---

### Post by darkod on 2018-07-23
Strange, it is refusing to assemble with 11 drives according to that last message. You could try forcing it to run by adding the parameter --run to the command. That would be the last attempt with --assemble. If that doesn't work, there is only one more thing left to do...

---

### Post by vwlinux on 2018-07-23
I run the command with sde, but nothing happend.

Then i rebootet the server and this is the output of cat /proc/mdstat

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdh1[1] sdf1[3] sdb1[2] sdj1[13] sdm1[7] sdk1[6] sdi1[14] sdg1[9] sdl1[12] sde1[8] sdc1[0] sdd1[11]
      32232904704 blocks super 1.2 level 5, 512k chunk, algorithm 2 [12/11] [UUUUUUUUU_UU]
      [>....................]  recovery =  4.3% (128174280/2930264064) finish=338.1min speed=138120K/sec

unused devices: <none>

```

This was the output of mdadm -D /dev/md0
```

# mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
  Used Dev Size : 2930264064 (2794.52 GiB 3000.59 GB)
   Raid Devices : 12
  Total Devices : 12
    Persistence : Superblock is persistent

    Update Time : Mon Jul 23 23:57:53 2018
          State : clean, degraded, recovering
 Active Devices : 11
Working Devices : 12
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 4% complete

           Name : ingfil:0  (local to host ingfil)
           UUID : 9c5baecf:58212783:fe438251:3b70e113
         Events : 870682

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8      113        1      active sync   /dev/sdh1
       2       8       17        2      active sync   /dev/sdb1
       3       8       81        3      active sync   /dev/sdf1
      11       8       49        4      active sync   /dev/sdd1
       6       8      161        5      active sync   /dev/sdk1
       7       8      193        6      active sync   /dev/sdm1
       8       8       65        7      active sync   /dev/sde1
       9       8       97        8      active sync   /dev/sdg1
      14       8      129        9      spare rebuilding   /dev/sdi1
      12       8      177       10      active sync   /dev/sdl1
      13       8      145       11      active sync   /dev/sdj1

```

This is the output from the server now:

```

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[8](F) sdd1[11] sdb1[2] sdc1[0] sdg1[9] sdf1[3] sdk1[6] sdl1[12] sdi1[14](S) sdh1[1] sdj1[13] sdm1[7]
      32232904704 blocks super 1.2 level 5, 512k chunk, algorithm 2 [12/10] [UUUUUUU_U_UU]

unused devices: <none>

```

```

# mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Jan 24 20:36:48 2013
     Raid Level : raid5
     Array Size : 32232904704 (30739.69 GiB 33006.49 GB)
  Used Dev Size : 2930264064 (2794.52 GiB 3000.59 GB)
   Raid Devices : 12
  Total Devices : 12
    Persistence : Superblock is persistent

    Update Time : Tue Jul 24 07:09:10 2018
          State : clean, FAILED
 Active Devices : 10
Working Devices : 11
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ingfil:0  (local to host ingfil)
           UUID : 9c5baecf:58212783:fe438251:3b70e113
         Events : 870772

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8      113        1      active sync   /dev/sdh1
       2       8       17        2      active sync   /dev/sdb1
       3       8       81        3      active sync   /dev/sdf1
      11       8       49        4      active sync   /dev/sdd1
       6       8      161        5      active sync   /dev/sdk1
       7       8      193        6      active sync   /dev/sdm1
       7       0        0        7      removed
       9       8       97        8      active sync   /dev/sdg1
       9       0        0        9      removed
      12       8      177       10      active sync   /dev/sdl1
      13       8      145       11      active sync   /dev/sdj1

       8       8       65        -      faulty spare   /dev/sde1
      14       8      129        -      spare   /dev/sdi1

```

Is it possible to replace the sde disk with the disk i just removed?
I might be less errors on this?

---

### Post by vwlinux on 2018-07-24
This is the output of dmesg:

```

[   21.140855] md: bind<sde1>
[   21.144603] md/raid:md0: device sde1 operational as raid disk 7
[   21.144604] md/raid:md0: device sdd1 operational as raid disk 4
[   21.144604] md/raid:md0: device sdb1 operational as raid disk 2
[   21.144605] md/raid:md0: device sdc1 operational as raid disk 0
[   21.144606] md/raid:md0: device sdg1 operational as raid disk 8
[   21.144607] md/raid:md0: device sdf1 operational as raid disk 3
[   21.144608] md/raid:md0: device sdk1 operational as raid disk 5
[   21.144609] md/raid:md0: device sdl1 operational as raid disk 10
[   21.144609] md/raid:md0: device sdh1 operational as raid disk 1
[   21.144610] md/raid:md0: device sdj1 operational as raid disk 11
[   21.144611] md/raid:md0: device sdm1 operational as raid disk 6
[   21.145712] md/raid:md0: allocated 0kB
[   21.145870] md/raid:md0: raid level 5 active with 11 out of 12 devices, algorithm 2
[   21.145870] RAID conf printout:
[   21.145871]  --- level:5 rd:12 wd:11
[   21.145872]  disk 0, o:1, dev:sdc1
[   21.145873]  disk 1, o:1, dev:sdh1
[   21.145874]  disk 2, o:1, dev:sdb1
[   21.145875]  disk 3, o:1, dev:sdf1
[   21.145876]  disk 4, o:1, dev:sdd1
[   21.145877]  disk 5, o:1, dev:sdk1
[   21.145878]  disk 6, o:1, dev:sdm1
[   21.145879]  disk 7, o:1, dev:sde1
[   21.145879]  disk 8, o:1, dev:sdg1
[   21.145880]  disk 9, o:1, dev:sdi1
[   21.145881]  disk 10, o:1, dev:sdl1
[   21.145882]  disk 11, o:1, dev:sdj1
[   21.145895] md0: Warning: Device sdi1 is misaligned
[   21.145896] md0: Warning: Device sdh1 is misaligned
[   21.145897] md0: Warning: Device sdh1 is misaligned
[   21.145899] md0: Warning: Device sdm1 is misaligned
[   21.145899] md0: Warning: Device sdm1 is misaligned
[   21.145921] md0: detected capacity change from 0 to 33006494416896
[   21.145995] RAID conf printout:
[   21.145997]  --- level:5 rd:12 wd:11
[   21.145998]  disk 0, o:1, dev:sdc1
[   21.145999]  disk 1, o:1, dev:sdh1
[   21.146000]  disk 2, o:1, dev:sdb1
[   21.146001]  disk 3, o:1, dev:sdf1
[   21.146002]  disk 4, o:1, dev:sdd1
[   21.146002]  disk 5, o:1, dev:sdk1
[   21.146003]  disk 6, o:1, dev:sdm1
[   21.146004]  disk 7, o:1, dev:sde1
[   21.146005]  disk 8, o:1, dev:sdg1
[   21.146006]  disk 9, o:1, dev:sdi1
[   21.146007]  disk 10, o:1, dev:sdl1
[   21.146007]  disk 11, o:1, dev:sdj1
[   21.146008] RAID conf printout:
[   21.146009]  --- level:5 rd:12 wd:11
[   21.146009]  disk 0, o:1, dev:sdc1
[   21.146010]  disk 1, o:1, dev:sdh1
[   21.146011]  disk 2, o:1, dev:sdb1
[   21.146012]  disk 3, o:1, dev:sdf1
[   21.146012]  disk 4, o:1, dev:sdd1
[   21.146013]  disk 5, o:1, dev:sdk1
[   21.146014]  disk 6, o:1, dev:sdm1
[   21.146015]  disk 7, o:1, dev:sde1
[   21.146015]  disk 8, o:1, dev:sdg1
[   21.146016]  disk 9, o:1, dev:sdi1
[   21.146017]  disk 10, o:1, dev:sdl1
[   21.146018]  disk 11, o:1, dev:sdj1
[   21.146053] md: recovery of RAID array md0
[   21.146054] md: minimum _guaranteed_  speed: 500000 KB/sec/disk.
[   21.146055] md: using maximum available idle IO bandwidth (but not more than 500000 KB/sec) for recovery.
[   21.146080] md: using 128k window, over a total of 2930264064k.
[   21.146081] md: resuming recovery of md0 from checkpoint.
[   21.148489]  md0: unknown partition table
[ 2083.527610] sd 3:0:3:0: [sde] command ffff880575717400 timed out
[ 2083.527613] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [8] tag[8], task [ffff880520b83c00]:
[ 2083.527616] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 7F000320,  slot [8].
[ 2083.527619] sas: sas_ata_task_done: SAS error 8a
[ 2083.527622] sd 3:0:3:0: [sde] command ffff880575717a00 timed out
[ 2083.527625] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [9] tag[9], task [ffff880520b82300]:
[ 2083.527628] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 7F000220,  slot [9].
[ 2083.527631] sas: sas_ata_task_done: SAS error 8a
[ 2083.527634] sd 3:0:3:0: [sde] command ffff880575716a00 timed out
[ 2083.527636] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [1e] tag[1e], task [ffff880520b82580]:
[ 2083.527639] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 7F000020,  slot [1e].
[ 2083.527643] sas: sas_ata_task_done: SAS error 8a
[ 2083.527646] sd 3:0:3:0: [sde] command ffff880575716000 timed out
[ 2083.527649] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [19] tag[19], task [ffff880520b81b80]:
[ 2083.527652] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 3F000020,  slot [19].
[ 2083.527655] sas: sas_ata_task_done: SAS error 8a
[ 2083.527658] sd 3:0:3:0: [sde] command ffff8805760f9d00 timed out
[ 2083.527661] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [18] tag[18], task [ffff880520b835c0]:
[ 2083.527664] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 3D000020,  slot [18].
[ 2083.527667] sas: sas_ata_task_done: SAS error 8a
[ 2083.527670] sd 3:0:3:0: [sde] command ffff8805760f9300 timed out
[ 2083.527673] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [1d] tag[1d], task [ffff880520b81a40]:
[ 2083.527676] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 3C000020,  slot [1d].
[ 2083.527679] sas: sas_ata_task_done: SAS error 8a
[ 2083.527682] sd 3:0:3:0: [sde] command ffff8805760f8500 timed out
[ 2083.527685] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [1c] tag[1c], task [ffff880520b83ac0]:
[ 2083.527688] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 1C000020,  slot [1c].
[ 2083.527691] sas: sas_ata_task_done: SAS error 8a
[ 2083.527694] sd 3:0:3:0: [sde] command ffff880575716600 timed out
[ 2083.527696] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [1b] tag[1b], task [ffff880520b81540]:
[ 2083.527699] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 0C000020,  slot [1b].
[ 2083.527703] sas: sas_ata_task_done: SAS error 8a
[ 2083.527705] sd 3:0:3:0: [sde] command ffff8805724e0200 timed out
[ 2083.527708] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [1a] tag[1a], task [ffff880520b82f80]:
[ 2083.527711] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 04000020,  slot [1a].
[ 2083.527714] sas: sas_ata_task_done: SAS error 8a
[ 2083.527717] sd 3:0:3:0: [sde] command ffff8805724e1600 timed out
[ 2083.527720] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_sas.c 1962:Release slot [5] tag[5], task [ffff880520b82bc0]:
[ 2083.527723] /build/linux-ZqOzIB/linux-3.13.0/drivers/scsi/mvsas/mv_94xx.c 625:command active 00000020,  slot [5].
[ 2083.527726] sas: sas_ata_task_done: SAS error 8a
[ 2083.527729] sd 3:0:3:0: [sde] command ffff8805724e0a00 timed out
[ 2083.527753] sas: Enter sas_scsi_recover_host busy: 31 failed: 31
[ 2083.527759] sas: ata6: end_device-3:3: cmd error handler
[ 2083.527896] sas: ata3: end_device-3:0: dev error handler
[ 2083.527916] sas: ata4: end_device-3:1: dev error handler
[ 2083.527923] sas: ata5: end_device-3:2: dev error handler
[ 2083.527928] sas: ata6: end_device-3:3: dev error handler
[ 2083.528013] sas: ata7: end_device-3:4: dev error handler
[ 2083.528027] sas: ata8: end_device-3:5: dev error handler
[ 2083.528327] ata6.00: exception Emask 0x0 SAct 0x7fffffff SErr 0x0 action 0x6
[ 2083.531777] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.535308] ata6.00: cmd 60/00:00:40:d8:96/04:00:4e:01:00/40 tag 0 ncq 524288 in
[ 2083.535308]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.542317] ata6.00: status: { ERR }
[ 2083.545795] ata6.00: error: { ABRT }
[ 2083.549272] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.552796] ata6.00: cmd 60/00:00:40:d4:96/04:00:4e:01:00/40 tag 1 ncq 524288 in
[ 2083.552796]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.559851] ata6.00: status: { ERR }
[ 2083.563328] ata6.00: error: { ABRT }
[ 2083.566807] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.570343] ata6.00: cmd 60/00:00:40:d0:96/04:00:4e:01:00/40 tag 2 ncq 524288 in
[ 2083.570343]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.577406] ata6.00: status: { ERR }
[ 2083.580886] ata6.00: error: { ABRT }
[ 2083.584294] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.587823] ata6.00: cmd 60/00:00:40:fc:96/04:00:4e:01:00/40 tag 3 ncq 524288 in
[ 2083.587823]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.594895] ata6.00: status: { ERR }
[ 2083.598381] ata6.00: error: { ABRT }
[ 2083.601868] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.605437] ata6.00: cmd 60/00:00:40:f8:96/04:00:4e:01:00/40 tag 4 ncq 524288 in
[ 2083.605437]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.612482] ata6.00: status: { ERR }
[ 2083.615902] ata6.00: error: { ABRT }
[ 2083.619391] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.622965] ata6.00: cmd 60/00:00:40:0c:97/04:00:4e:01:00/40 tag 5 ncq 524288 in
[ 2083.622965]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.630002] ata6.00: status: { ERR }
[ 2083.633490] ata6.00: error: { ABRT }
[ 2083.637021] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.640559] ata6.00: cmd 60/00:00:40:08:97/04:00:4e:01:00/40 tag 6 ncq 524288 in
[ 2083.640559]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.647523] ata6.00: status: { ERR }
[ 2083.651019] ata6.00: error: { ABRT }
[ 2083.654508] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.658042] ata6.00: cmd 60/00:00:40:04:97/04:00:4e:01:00/40 tag 7 ncq 524288 in
[ 2083.658042]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.665069] ata6.00: status: { ERR }
[ 2083.668565] ata6.00: error: { ABRT }
[ 2083.671977] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.675512] ata6.00: cmd 60/00:00:40:00:97/04:00:4e:01:00/40 tag 8 ncq 524288 in
[ 2083.675512]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.682560] ata6.00: status: { ERR }
[ 2083.686040] ata6.00: error: { ABRT }
[ 2083.689523] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.693025] ata6.00: cmd 60/00:00:40:f4:96/04:00:4e:01:00/40 tag 9 ncq 524288 in
[ 2083.693025]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.699994] ata6.00: status: { ERR }
[ 2083.703452] ata6.00: error: { ABRT }
[ 2083.706868] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.710277] ata6.00: cmd 60/00:00:40:ac:96/04:00:4e:01:00/40 tag 10 ncq 524288 in
[ 2083.710277]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.717207] ata6.00: status: { ERR }
[ 2083.720708] ata6.00: error: { ABRT }
[ 2083.724049] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.727466] ata6.00: cmd 60/00:00:40:a8:96/04:00:4e:01:00/40 tag 11 ncq 524288 in
[ 2083.727466]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.734395] ata6.00: status: { ERR }
[ 2083.737862] ata6.00: error: { ABRT }
[ 2083.741291] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.744706] ata6.00: cmd 60/00:00:40:a4:96/04:00:4e:01:00/40 tag 12 ncq 524288 in
[ 2083.744706]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.751666] ata6.00: status: { ERR }
[ 2083.755131] ata6.00: error: { ABRT }
[ 2083.758547] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.762005] ata6.00: cmd 60/00:00:40:a0:96/04:00:4e:01:00/40 tag 13 ncq 524288 in
[ 2083.762005]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.768932] ata6.00: status: { ERR }
[ 2083.772320] ata6.00: error: { ABRT }
[ 2083.775737] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.779157] ata6.00: cmd 60/00:00:40:9c:96/04:00:4e:01:00/40 tag 14 ncq 524288 in
[ 2083.779157]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.786131] ata6.00: status: { ERR }
[ 2083.789589] ata6.00: error: { ABRT }
[ 2083.793010] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.796358] ata6.00: cmd 60/00:00:40:10:97/04:00:4e:01:00/40 tag 15 ncq 524288 in
[ 2083.796358]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.803323] ata6.00: status: { ERR }
[ 2083.806797] ata6.00: error: { ABRT }
[ 2083.810229] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.813657] ata6.00: cmd 60/00:00:40:b4:96/04:00:4e:01:00/40 tag 16 ncq 524288 in
[ 2083.813657]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.820593] ata6.00: status: { ERR }
[ 2083.824008] ata6.00: error: { ABRT }
[ 2083.827441] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.830873] ata6.00: cmd 60/00:00:40:b0:96/04:00:4e:01:00/40 tag 17 ncq 524288 in
[ 2083.830873]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.837820] ata6.00: status: { ERR }
[ 2083.841356] ata6.00: error: { ABRT }
[ 2083.844795] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.848159] ata6.00: cmd 60/00:00:40:ec:96/04:00:4e:01:00/40 tag 18 ncq 524288 in
[ 2083.848159]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.855105] ata6.00: status: { ERR }
[ 2083.858607] ata6.00: error: { ABRT }
[ 2083.862073] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.865513] ata6.00: cmd 60/00:00:40:f0:96/04:00:4e:01:00/40 tag 19 ncq 524288 in
[ 2083.865513]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.872456] ata6.00: status: { ERR }
[ 2083.875963] ata6.00: error: { ABRT }
[ 2083.879433] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.882870] ata6.00: cmd 60/00:00:40:e8:96/04:00:4e:01:00/40 tag 20 ncq 524288 in
[ 2083.882870]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.889812] ata6.00: status: { ERR }
[ 2083.893313] ata6.00: error: { ABRT }
[ 2083.896779] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.900139] ata6.00: cmd 60/00:00:40:e4:96/04:00:4e:01:00/40 tag 21 ncq 524288 in
[ 2083.900139]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.907088] ata6.00: status: { ERR }
[ 2083.910589] ata6.00: error: { ABRT }
[ 2083.914032] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.917488] ata6.00: cmd 60/00:00:40:e0:96/04:00:4e:01:00/40 tag 22 ncq 524288 in
[ 2083.917488]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.924488] ata6.00: status: { ERR }
[ 2083.927917] ata6.00: error: { ABRT }
[ 2083.931351] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.934809] ata6.00: cmd 60/00:00:40:dc:96/04:00:4e:01:00/40 tag 23 ncq 524288 in
[ 2083.934809]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.941760] ata6.00: status: { ERR }
[ 2083.945258] ata6.00: error: { ABRT }
[ 2083.948700] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.952062] ata6.00: cmd 60/00:00:40:cc:96/04:00:4e:01:00/40 tag 24 ncq 524288 in
[ 2083.952062]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.959046] ata6.00: status: { ERR }
[ 2083.962548] ata6.00: error: { ABRT }
[ 2083.965990] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.969398] ata6.00: cmd 60/00:00:40:c8:96/04:00:4e:01:00/40 tag 25 ncq 524288 in
[ 2083.969398]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.976390] ata6.00: status: { ERR }
[ 2083.979895] ata6.00: error: { ABRT }
[ 2083.983333] ata6.00: failed command: READ FPDMA QUEUED
[ 2083.986773] ata6.00: cmd 60/00:00:40:c4:96/04:00:4e:01:00/40 tag 26 ncq 524288 in
[ 2083.986773]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2083.993762] ata6.00: status: { ERR }
[ 2083.997273] ata6.00: error: { ABRT }
[ 2084.000644] ata6.00: failed command: READ FPDMA QUEUED
[ 2084.004011] ata6.00: cmd 60/00:00:40:c0:96/04:00:4e:01:00/40 tag 27 ncq 524288 in
[ 2084.004011]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2084.011011] ata6.00: status: { ERR }
[ 2084.014517] ata6.00: error: { ABRT }
[ 2084.017958] ata6.00: failed command: READ FPDMA QUEUED
[ 2084.021405] ata6.00: cmd 60/00:00:40:bc:96/04:00:4e:01:00/40 tag 28 ncq 524288 in
[ 2084.021405]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2084.028409] ata6.00: status: { ERR }
[ 2084.031919] ata6.00: error: { ABRT }
[ 2084.035361] ata6.00: failed command: READ FPDMA QUEUED
[ 2084.038802] ata6.00: cmd 60/00:00:40:b8:96/04:00:4e:01:00/40 tag 29 ncq 524288 in
[ 2084.038802]          res 01/04:2c:40:0c:97/00:00:4e:01:00/40 Emask 0x2 (HSM violation)
[ 2084.045791] ata6.00: status: { ERR }
[ 2084.049300] ata6.00: error: { ABRT }
[ 2084.052740] ata6.00: failed command: READ FPDMA QUEUED
[ 2084.056109] ata6.00: cmd 60/18:00:28:fb:8f/01:00:4e:01:00/40 tag 30 ncq 143360 in
[ 2084.056109]          res 41/40:00:28:fb:8f/00:00:4e:01:00/40 Emask 0x409 (media error) <F>
[ 2084.063074] ata6.00: status: { DRDY ERR }
[ 2084.066584] ata6.00: error: { UNC }
[ 2084.070029] ata6: hard resetting link
[ 2084.226018] ata6.00: configured for UDMA/133
[ 2084.226103] sd 3:0:3:0: [sde]
[ 2084.226105] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2084.226108] sd 3:0:3:0: [sde]
[ 2084.226110] Sense Key : Medium Error [current] [descriptor]
[ 2084.226113] Descriptor sense data with sense descriptors (in hex):
[ 2084.226115]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 01
[ 2084.226124]         4e 8f fb 28
[ 2084.226128] sd 3:0:3:0: [sde]
[ 2084.226131] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2084.226133] sd 3:0:3:0: [sde] CDB:
[ 2084.226135] Read(16): 88 00 00 00 00 01 4e 8f fb 28 00 00 01 18 00 00
[ 2084.226145] end_request: I/O error, dev sde, sector 5613026088
[ 2084.229544] raid5_end_read_request: 25 callbacks suppressed
[ 2084.229547] md/raid:md0: read error not correctable (sector 5613024040 on sde1).
[ 2084.229551] md/raid:md0: Disk failure on sde1, disabling device.
[ 2084.229551] md/raid:md0: Operation continuing on 10 devices.
[ 2084.236510] md/raid:md0: read error not correctable (sector 5613024048 on sde1).
[ 2084.236513] md/raid:md0: read error not correctable (sector 5613024056 on sde1).
[ 2084.236515] md/raid:md0: read error not correctable (sector 5613024064 on sde1).
[ 2084.236517] md/raid:md0: read error not correctable (sector 5613024072 on sde1).
[ 2084.236520] md/raid:md0: read error not correctable (sector 5613024080 on sde1).
[ 2084.236522] md/raid:md0: read error not correctable (sector 5613024088 on sde1).
[ 2084.236524] md/raid:md0: read error not correctable (sector 5613024096 on sde1).
[ 2084.236526] md/raid:md0: read error not correctable (sector 5613024104 on sde1).
[ 2084.236529] md/raid:md0: read error not correctable (sector 5613024112 on sde1).
[ 2084.236547] ata6: EH complete
[ 2084.236659] sas: --- Exit sas_scsi_recover_host: busy: 0 failed: 0 tries: 1
[ 2084.388599] md: md0: recovery interrupted.
[ 2085.092291] RAID conf printout:
[ 2085.092297]  --- level:5 rd:12 wd:10
[ 2085.092300]  disk 0, o:1, dev:sdc1
[ 2085.092302]  disk 1, o:1, dev:sdh1
[ 2085.092304]  disk 2, o:1, dev:sdb1
[ 2085.092306]  disk 3, o:1, dev:sdf1
[ 2085.092308]  disk 4, o:1, dev:sdd1
[ 2085.092310]  disk 5, o:1, dev:sdk1
[ 2085.092312]  disk 6, o:1, dev:sdm1
[ 2085.092314]  disk 7, o:0, dev:sde1
[ 2085.092316]  disk 8, o:1, dev:sdg1
[ 2085.092318]  disk 9, o:1, dev:sdi1
[ 2085.092320]  disk 10, o:1, dev:sdl1
[ 2085.092322]  disk 11, o:1, dev:sdj1
[ 2085.096832] RAID conf printout:
[ 2085.096837]  --- level:5 rd:12 wd:10
[ 2085.096840]  disk 0, o:1, dev:sdc1
[ 2085.096842]  disk 1, o:1, dev:sdh1
[ 2085.096844]  disk 2, o:1, dev:sdb1
[ 2085.096846]  disk 3, o:1, dev:sdf1
[ 2085.096847]  disk 4, o:1, dev:sdd1
[ 2085.096849]  disk 5, o:1, dev:sdk1
[ 2085.096851]  disk 6, o:1, dev:sdm1
[ 2085.096853]  disk 8, o:1, dev:sdg1
[ 2085.096855]  disk 9, o:1, dev:sdi1
[ 2085.096857]  disk 10, o:1, dev:sdl1
[ 2085.096859]  disk 11, o:1, dev:sdj1
[ 2085.096865] RAID conf printout:
[ 2085.096866]  --- level:5 rd:12 wd:10
[ 2085.096868]  disk 0, o:1, dev:sdc1
[ 2085.096870]  disk 1, o:1, dev:sdh1
[ 2085.096872]  disk 2, o:1, dev:sdb1
[ 2085.096874]  disk 3, o:1, dev:sdf1
[ 2085.096875]  disk 4, o:1, dev:sdd1
[ 2085.096877]  disk 5, o:1, dev:sdk1
[ 2085.096879]  disk 6, o:1, dev:sdm1
[ 2085.096881]  disk 8, o:1, dev:sdg1
[ 2085.096882]  disk 9, o:1, dev:sdi1
[ 2085.096884]  disk 10, o:1, dev:sdl1
[ 2085.096886]  disk 11, o:1, dev:sdj1
[ 2085.104854] RAID conf printout:
[ 2085.104858]  --- level:5 rd:12 wd:10
[ 2085.104861]  disk 0, o:1, dev:sdc1
[ 2085.104863]  disk 1, o:1, dev:sdh1
[ 2085.104865]  disk 2, o:1, dev:sdb1
[ 2085.104867]  disk 3, o:1, dev:sdf1
[ 2085.104869]  disk 4, o:1, dev:sdd1
[ 2085.104871]  disk 5, o:1, dev:sdk1
[ 2085.104873]  disk 6, o:1, dev:sdm1
[ 2085.104875]  disk 8, o:1, dev:sdg1
[ 2085.104876]  disk 10, o:1, dev:sdl1
[ 2085.104878]  disk 11, o:1, dev:sdj1

```

---

### Post by darkod on 2018-07-24
Unfortunately if the rebuild process can't finish, you can't afford to replace sde (one more disk). Taking sde out will mean going from 11 members to 10 and the raid5 will fail with 2 members missing.

The issue you are facing is the biggest danger of running big raid5 arrays. A second disk can fail while still rebuilding one disk that was replaced, at which moment you lose the redundancy count.

---

### Post by vwlinux on 2018-07-24
I think of 3 possible solutions:

1. Clone sde disk with a new one and try to rebuild the array.
2. Switch back the sdi disk that i replaced, to se if the array rebuilds.
3. Run crate to see if the array get back up:
```
mdadm --create /dev/md0 --assume-clean -l5 -n4 -c64 /dev/sd[bcdefghijklm]2 missing
```

Could it also be smart to do a smart selftest with this command?
```
smartctl -l selftest /dev/sdb
```

---

### Post by darkod on 2018-07-24
The create will probably not get you very far. You can already assemble the array but the problem is that sde is failing before the new member (sdi) gets synced. The same will probably happen if you use create with assume-clean.

Cloning is worth a shot, but the risk is again that sde will fail while cloning (from extensive read/write). But you can try it. You don't even need a new disk for that. sdi is already a new disk still not synced with the array, right? Simply try cloning sde onto sdi. After that you will try the assemble again with 11 members, like you already did.

The old sdi already failed and is not up to date with the array. So I doubt you can use it. Maybe only as temporary 12th member in case you manage to successfully assemble the array with 11 members after cloning sde.

---

### Post by vwlinux on 2018-07-24
Thank you so much for all your reply **darkod.**
I have bought a new disk and will try to clone the sde disk.

---

### Post by vwlinux on 2018-08-18
I cloned the sde disk with clonezilla.
There was some bad sectors, but run with the --rescue option.
I then run assemble with all disks, and now i have successfully mounted the filesystem.
I will now move all data to a new server.

Thank you **darkod** for helping me out.

---

### Post by darkod on 2018-08-18
No problem. Glad it worked out. You can mark the thread as solved in Thread Tools above the first post.

---

