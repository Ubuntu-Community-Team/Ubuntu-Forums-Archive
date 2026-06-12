---
title: "What is going on with forked-daapd?"
date: 2013-05-23
forum: Server Platforms
---

### Post by Spency on 2013-05-23
Hello,

I'm trying to set up a media server to stream music and video to rhythmbox and itunes. 

I installed forked-dapped [https://github.com/jasonmc/forked-daapd](https://github.com/jasonmc/forked-daapd)

It's running, and I'm able to access the shared library it produces on all my machines. However, the library is itself empty, and I'm sure the config file correctly points at my music directory and I'm sure there's music in it.  

Apparently the first time it starts up it does one big scan of the directory, and it is a huge directory (100+GB of music & album artwork) [https://github.com/jasonmc/forked-daapd/blob/master/README](https://github.com/jasonmc/forked-daapd/blob/master/README) even mounting the smb:// drive takes a minute or so.

when I run the command forked-daapd -f (to see what it's doing as it starts up) here's what I get: 

```
root:/# forked-daapd -f    main: Forked Media Server Version 0.19gcd taking off
    main: mDNS init
    mdns: Avahi state change: Client running
      db: ANALYZE failed: step failed: attempt to write a readonly database
      db: Query error: step failed: attempt to write a readonly database
    scan: Error: could not clear old watches from DB
   httpd: Could not bind socket: Address already in use
    http: Could not start HTTP server socket
   httpd: Failed to start v4 HTTP server
    main: HTTPd thread failed to start
    main: Player deinit
      db: Query error: step failed: attempt to write a readonly database
      db: Error saving speaker state: step failed: attempt to write a readonly database
  player: Could not save state for local audio
    main: File scanner deinit
    main: Database deinit
    main: mDNS deinit
    main: Exiting.
```

Which does not look positive. It's now been about 5 minutes too and I would think I should start to see some music appear.

I know this is thing is like 2 years old now but I know lots have had success, but is anyone able to tell me what I'm doing wrong?

-- EDIT-- 

Every 2 minutes, the library auto-ejects. I can connect to it again afterwards but auto-ejecting seems like a problem with the service not starting properly.


Thanks,
Spency

---

### Post by tgalati4 on 2013-05-23
I would create a small library (say 1 GB) of media files and point the daemon to that.  Then restart the daap daemon or reboot the machine and see if the library shows up.  With 100GB library, it could take a long time to fully populate the database before it is available for publication.  

I don't have it installed on this laptop to test, but what version are you running?

tgalati4@Mint14-Extensa ~ $ apt-cache policy forked-daapd
forked-daapd:
  Installed: (none)
  Candidate: 0.19gcd-2ubuntu1
  Version table:
     0.19gcd-2ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages

---

### Post by Spency on 2013-05-23
```
forked-daapd:  Installed: 0.19gcd-2ubuntu1
  Candidate: 0.19gcd-2ubuntu1
  Version table:
 *** 0.19gcd-2ubuntu1 0
        500 http://nl.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
        100 /var/lib/dpkg/status
```

Going to try a restart now and the alt media directory a little bit afterwards. Will post again.

---

### Post by Spency on 2013-05-23
Reboot didn't help, nor did pointing it to a smaller directory (I put just one song into a folder parallel to my main music folder.) Not sure where to start here

---

### Post by tgalati4 on 2013-05-23
What is the SMART status of the disk drive that hosts the database?  Is this disk drive having problems?

---

### Post by ian dobson on 2013-05-23
Hi,

I don't know forked-daapd at all but the Errors about writing to a readonly database make me think you have Problems with the SQL backend.

Regards
Ian Dobson

---

### Post by Spency on 2013-05-24
> **tgalati4 said:**
> What is the SMART status of the disk drive that hosts the database?  Is this disk drive having problems?

It appears so. The system has trouble mounting the disk on startup. Transmission upload speed is down from 7mb to >2 and everything I try to download via torrent ends up becoming corrupt. 

This is the drive that houses ubuntu.
```
$ sudo smartctl -i /dev/sdbsmartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K160
Device Model:     Hitachi HTS541616J9SA00
Serial Number:    SB2404SJCGS9PE
Firmware Version: SB4OC7BP
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Fri May 24 23:24:36 2013 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

This is main storage:
```
$ sudo smartctl -i /dev/sdasmartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD30EZRX-00DC0B0
Serial Number:    WD-WMC1T1738238
LU WWN Device Id: 5 0014ee 6030f0e8a
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri May 24 23:24:44 2013 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

> **ian dobson said:**
> Hi,

I don't know forked-daapd at all but the Errors about writing to a readonly database make me think you have Problems with the SQL backend.

Regards
Ian Dobson 

How can I resolve it?

---

### Post by tgalati4 on 2013-05-24
```
sudo smartctl -x /dev/sdb
dmesg | tail -50
```

---

### Post by Spency on 2013-05-25
Here's what I got:
```
 $ sudo smartctl -x /dev/sdbsmartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-30-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K160
Device Model:     Hitachi HTS541616J9SA00
Serial Number:    SB2404SJCGS9PE
Firmware Version: SB4OC7BP
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Sat May 25 10:05:10 2013 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  645) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  83) minutes.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     PO-R--   100   086   062    -    0
  2 Throughput_Performance  P-S---   100   100   040    -    0
  3 Spin_Up_Time            POS---   234   100   033    -    1
  4 Start_Stop_Count        -O--C-   096   096   000    -    7174
  5 Reallocated_Sector_Ct   PO--CK   100   100   005    -    750 (0, 49)
  7 Seek_Error_Rate         PO-R--   100   100   067    -    0
  8 Seek_Time_Performance   P-S---   100   100   040    -    0
  9 Power_On_Hours          -O--C-   053   053   000    -    20912
 10 Spin_Retry_Count        PO--C-   100   100   060    -    0
 12 Power_Cycle_Count       -O--CK   098   098   000    -    3734
191 G-Sense_Error_Rate      -O-R--   100   093   000    -    0
192 Power-Off_Retract_Count -O--CK   100   100   000    -    178
193 Load_Cycle_Count        -O--C-   071   071   000    -    293277
194 Temperature_Celsius     -O----   141   100   000    -    39 (Min/Max 13/52)
196 Reallocated_Event_Count -O--CK   100   100   000    -    79
197 Current_Pending_Sector  -O---K   100   100   000    -    1
198 Offline_Uncorrectable   ---R--   100   100   000    -    0
199 UDMA_CRC_Error_Count    -O-R--   200   253   000    -    0
223 Load_Retry_Count        -O-R--   100   100   000    -    0
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning


General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
GP/S  Log at address 0x00 has    1 sectors [Log Directory]
SMART Log at address 0x01 has    1 sectors [Summary SMART error log]
SMART Log at address 0x02 has    1 sectors [Comprehensive SMART error log]
GP    Log at address 0x03 has    1 sectors [Ext. Comprehensive SMART error log]
SMART Log at address 0x06 has    1 sectors [SMART self-test log]
GP    Log at address 0x07 has    1 sectors [Extended self-test log]
SMART Log at address 0x09 has    1 sectors [Selective self-test log]
GP    Log at address 0x11 has    1 sectors [SATA Phy Event Counters]
GP/S  Log at address 0x80 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x81 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x82 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x83 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x84 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x85 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x86 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x87 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x88 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x89 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8a has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8b has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8c has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8d has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8e has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8f has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x90 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x91 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x92 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x93 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x94 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x95 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x96 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x97 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x98 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x99 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9a has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9b has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9c has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9d has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9e has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9f has   16 sectors [Host vendor specific log]


SMART Extended Comprehensive Error Log Version: 1 (1 sectors)
Device Error Count: 3725 (device log contains only the most recent 4 errors)
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


Error 3725 [0] occurred at disk power-on lifetime: 20506 hours (854 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  10 -- 51 00 00 00 00 00 00 00 00 04 00  Error: IDNF at LBA = 0x04000000 = 67108864


  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  c8 d0 ff 00 00 00 00 00 00 00 00 04 00     01:12:41.300  READ DMA
  00 d0 ff 00 ec 00 00 00 40 00 00 00 00     01:12:41.300  NOP [Reserved subcommand]
  00 d0 ff 00 14 10 00 00 40 00 00 00 00     01:12:41.300  NOP [Reserved subcommand]
  73 d0 ff 08 00 5f a7 48 43 00 00 00 00     01:12:41.300  SEEK [RET-4]
  48 d0 ff 00 00 00 00 00 00 00 00 05 00     01:12:41.300  [RESERVED]


Error 3724 [3] occurred at disk power-on lifetime: 20504 hours (854 days + 8 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 0e 00 00 04 95 fd ba 44 00  Error: UNC 14 sectors at LBA = 0x0495fdba = 76938682


  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 d8 ff 00 40 00 00 04 95 fd 88 40 00     00:03:48.300  READ DMA EXT
  25 d8 ff 00 40 00 00 04 95 fd 48 40 00     00:03:48.300  READ DMA EXT
  25 d8 ff 00 40 00 00 04 95 fd 08 40 00     00:03:48.300  READ DMA EXT
  25 d8 ff 00 08 00 00 04 95 fe b0 40 00     00:03:48.300  READ DMA EXT
  25 d8 ff 00 08 00 00 04 95 fe b8 40 00     00:03:48.200  READ DMA EXT


Error 3723 [2] occurred at disk power-on lifetime: 20488 hours (853 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 0e 00 00 04 95 fd ba 44 00  Error: UNC 14 sectors at LBA = 0x0495fdba = 76938682


  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 d8 ff 00 40 00 00 04 95 fd 88 40 00     00:03:29.600  READ DMA EXT
  25 d8 ff 00 40 00 00 04 95 fd 48 40 00     00:03:29.600  READ DMA EXT
  25 d8 ff 00 40 00 00 04 95 fd 08 40 00     00:03:29.600  READ DMA EXT
  25 d8 ff 00 08 00 00 04 95 fe b0 40 00     00:03:29.600  READ DMA EXT
  25 d8 ff 00 08 00 00 04 95 fe b8 40 00     00:03:29.500  READ DMA EXT


Error 3722 [1] occurred at disk power-on lifetime: 20473 hours (853 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 0e 00 00 04 95 fd ba 44 00  Error: UNC 14 sectors at LBA = 0x0495fdba = 76938682


  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  25 d8 ff 00 40 00 00 04 95 fd 88 40 00     00:04:33.600  READ DMA EXT
  25 d8 ff 00 40 00 00 04 95 fd 48 40 00     00:04:33.600  READ DMA EXT
  25 d8 ff 00 40 00 00 04 95 fd 08 40 00     00:04:33.600  READ DMA EXT
  25 d8 ff 00 08 00 00 04 95 fe b0 40 00     00:04:33.600  READ DMA EXT
  25 d8 ff 00 08 00 00 04 95 fe b8 40 00     00:04:33.600  READ DMA EXT


SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               90%     17368         -
# 2  Extended offline    Completed without error       00%     17367         -
# 3  Short offline       Completed without error       00%     17366         -
# 4  Extended offline    Completed without error       00%     17366         -
# 5  Short offline       Completed without error       00%     17364         -
# 6  Short offline       Aborted by host               90%     17363         -
# 7  Short offline       Aborted by host               90%     17363         -
# 8  Short offline       Aborted by host               90%     17361         -
# 9  Extended offline    Completed without error       00%     17361         -
#10  Short offline       Completed without error       00%     17359         -
#11  Short offline       Completed without error       00%     16870         -
#12  Extended offline    Aborted by host               90%     16870         -
#13  Short offline       Completed without error       00%     16870         -
#14  Extended offline    Completed without error       00%     16860         -
#15  Short offline       Completed without error       00%     16859         -


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


Warning: device does not support SCT Commands
SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0009  2            0  Transition from drive PhyRdy to drive PhyNRdy
0x000a  2            0  Device-to-host register FISes sent due to a COMRESET
0x000b  2            0  CRC errors within host-to-device FIS
0x000d  2            0  Non-CRC errors within host-to-device FIS
```

Where it says "20504 hours (854 days + 8 hours)" - that's how many hours sdb has run for in it's lifetime?

```
 $ dmesg | tail -50[  609.877080] ata1.00: cmd 61/00:b0:00:38:3e/02:00:15:00:00/40 tag 22 ncq 262144 out
[  609.877080]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.878142] ata1.00: status: { DRDY }
[  609.878670] ata1.00: failed command: WRITE FPDMA QUEUED
[  609.879205] ata1.00: cmd 61/00:b8:00:88:3e/02:00:15:00:00/40 tag 23 ncq 262144 out
[  609.879205]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.880290] ata1.00: status: { DRDY }
[  609.880804] ata1.00: failed command: WRITE FPDMA QUEUED
[  609.881339] ata1.00: cmd 61/00:c0:00:34:3f/02:00:15:00:00/40 tag 24 ncq 262144 out
[  609.881339]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.882403] ata1.00: status: { DRDY }
[  609.882932] ata1.00: failed command: WRITE FPDMA QUEUED
[  609.883467] ata1.00: cmd 61/00:c8:00:48:3f/02:00:15:00:00/40 tag 25 ncq 262144 out
[  609.883467]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.884549] ata1.00: status: { DRDY }
[  609.885062] ata1.00: failed command: WRITE FPDMA QUEUED
[  609.885600] ata1.00: cmd 61/00:d0:00:a0:3f/02:00:15:00:00/40 tag 26 ncq 262144 out
[  609.885600]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.886678] ata1.00: status: { DRDY }
[  609.887217] ata1.00: failed command: WRITE FPDMA QUEUED
[  609.887760] ata1.00: cmd 61/00:d8:00:a6:3f/02:00:15:00:00/40 tag 27 ncq 262144 out
[  609.887760]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.888841] ata1.00: status: { DRDY }
[  609.889358] ata1.00: failed command: WRITE FPDMA QUEUED
[  609.889901] ata1.00: cmd 61/00:e0:00:b2:3f/02:00:15:00:00/40 tag 28 ncq 262144 out
[  609.889901]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.890973] ata1.00: status: { DRDY }
[  609.891497] ata1.00: failed command: WRITE FPDMA QUEUED
[  609.892055] ata1.00: cmd 61/00:e8:00:b6:3f/02:00:15:00:00/40 tag 29 ncq 262144 out
[  609.892055]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.893096] ata1.00: status: { DRDY }
[  609.893625] ata1.00: failed command: WRITE FPDMA QUEUED
[  609.894160] ata1.00: cmd 61/00:f0:00:da:3f/02:00:15:00:00/40 tag 30 ncq 262144 out
[  609.894160]          res 40/00:04:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  609.895222] ata1.00: status: { DRDY }
[  609.895754] ata1: hard resetting link
[  610.832051] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  610.833298] ata1.00: configured for UDMA/33
[  610.833331] ata1: EH complete
[  610.877265] ata1.00: exception Emask 0x10 SAct 0x100000 SErr 0x400100 action 0x6
[  610.877721] ata1.00: irq_stat 0x08000000
[  610.878137] ata1: SError: { UnrecovData Handshk }
[  610.878553] ata1.00: failed command: WRITE FPDMA QUEUED
[  610.878964] ata1.00: cmd 61/68:a0:d0:07:84/00:00:ae:00:00/40 tag 20 ncq 53248 out
[  610.878964]          res 40/00:a4:d0:07:84/00:00:ae:00:00/40 Emask 0x10 (ATA bus error)
[  610.879846] ata1.00: status: { DRDY }
[  610.880402] ata1: hard resetting link
[  613.276054] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  613.277339] ata1.00: configured for UDMA/33
[  613.277363] ata1: EH complete 
```

---

### Post by tgalati4 on 2013-05-25
So we go from a DAAP problem to a hard disk problem.  You have several things going on here.

1.  Your power-on hours (20K hrs) is about 1/2 the life of a typical disk.  Most consumer drives are rated to 50,000 hours before failure.  

2.  You also have a huge load-cycle count--293k!  This could be a bug with the firmware of the drive or with linux.  There are tweaks to fix this.  Basically, the arm moves back and forth too many times causing premature wear.  It could be that the drive tried to spin-down and the arm swung and then it was woken up to write a log file.  Spin-down needs to be turned off or changed to a large value to avoid this situation.

3.  750 relocated sectors is a large number.  If you run out of disk space to move these sectors then you have problems.  I don't know what the default number of relocated sector capability is--it varies with drive size and manufacturer--but 750 seems like a lot.

4.  You have 3,700 errors recorded so far.  So whatever is happening is causing a rapid increase in errors.

5.  SMART status is marked as "Passed" which is strange, but the drive continues to function despite the errors.

6.  Dmesg shows what the kernel is seeing:  write commands that get backed up resulting in ATA bus errors.

What was the issue with DAAP?

---

### Post by Spency on 2013-05-25
I read something about WD drives not behaving: [https://wiki.amahi.org/index.php/Partitions_Over_2.1_TB](https://wiki.amahi.org/index.php/Partitions_Over_2.1_TB) 
I'm going to try the solution mentioned in the article at the bottom.

The issue with DAAP was that it is not listing music in the directory I pointed it to.

---

### Post by tgalati4 on 2013-05-25
It's interesting that the article you referenced mentioned 300K as the load_cycle (head-parking) limit for consumer drives.  I am not aware if Hitachi Travelstars are subject to this problem like WD, but the Hitachi Deskstar drive is commonly refered to as "Deathstar".

In reference to your 2TB limit for partitions, this would show up immediately when trying to use the drive under linux.  So, I presume that your system has been running a while (especially if the boot drive has 20K hours on it.)  So if the partition limit was really a factor, you would have experienced many other problems trying to write to your data drive.

---

### Post by Spency on 2013-05-25
No the partition is not a factor. Sorry, I mixed up drives - no, I thought you were referring to my WD EZRX Drive when you mentioned how large my load cycle was - having stumbled across the guide from Amahi a week or so ago, I thought "he must be talking about the WD drive."

But in any case, the internal drive of the computer is very old (+5 years,) it's not surprising the disk is nearing the end of it's life. But what can I do to tweek it? Is this going to reduce the huge number of errors that are occurring?  

Also is the drive space of the hitachi a problem when the second drive is 3tb?

--EDIT--

I was thinking yesterday, I have two older drives lying around (one is a samsung and the other is a seagate drive.) I'm considering doing a fresh install of Ubuntu server one one of them. Would this help my situation at all?

---

### Post by Spency on 2013-05-31
Partially Solved. Switched out the Hitachi drive for a larger samsung drive. Fresh install of ubuntu 12.04 64 LTS, with amahi installed on top. 

Have not addressed the forked-daapd issue as of yet, but no more drive errors - the machine has run so far without glitch. .

---

### Post by tgalati4 on 2013-05-31
Linux expects perfect hardware and the error messages can be cryptic and misleading when hardware starts to fail.  Nothing you can do about old hard drives except pull the magnets for use on the refrigerator and keep the disks for skeet shooting.

---

