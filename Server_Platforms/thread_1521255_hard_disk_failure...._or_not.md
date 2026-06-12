---
title: "hard disk failure.... or not?"
date: 2010-06-30
forum: Server Platforms
---

### Post by gobbledigook on 2010-06-30
hey guys! i posted this over in the hardware section a while ago but have had no response :( so i apologise for double posting, and hope that one of you may have more time to look at the details and enlighten me :)

hi there! 

i have 10.04 desktop basically running xbmc sabnzbd and as a file server. the loads aren't too large as it is just for my house. But i moved from a server install to the desktop because of sound issues and running xbmc at start was a bit of a pain... so bit of background done.

my problem is that after installing 10.04 i got the disk utility pop-up saying one of samsung spinpoint 1tb (HD103UJ) has a critical error... now i didn't panic (although in the next couple of months i am intending to get another drive) but in the meantime i am simply wondering if this is a false flag? i've been getting this error for over 6 months now... pretty much from the last time i formatted the disk, i wiped it and then used dd to copy over a smaller partition, after which i used gparted to grow the partition to the whole drive. could this have created a false flag?

the 184 error is the only one, here is all the data i can glean from my system, attached is a screen of the relevent info from the disk utility, and this it from smartctl:

```
server@server:~$ sudo smartctl --all /dev/sdb
[sudo] password for server:
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD103UJ
Serial Number:    S13PJ1BQ722103
Firmware Version: 1AA01113
User Capacity:    1,000,204,886,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Fri Jun 25 19:38:19 2010 BST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 137) The previous self-test completed having
                                        a test element that failed and the
                                        device is suspected of having handling
                                        damage.
Total time to complete Offline
data collection:                 (11927) seconds.
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
recommended polling time:        ( 200) minutes.
Conveyance self-test routine
recommended polling time:        (  21) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   075   075   011    Pre-fail  Always       -       8180
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       308
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       14325
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       254
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   001   001   099    Pre-fail  Always   FAILING_NOW 148
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   069   066   000    Old_age   Always       -       31 (Lifetime Min/Max 25/31)
194 Temperature_Celsius     0x0022   069   065   000    Old_age   Always       -       31 (Lifetime Min/Max 25/31)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       3307307
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   099   099   000    Old_age   Always       -       131
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 16 (device log contains only the most recent five errors)
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

Error 16 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 e6 0b 60 e0  Error: ICRC, ABRT at LBA = 0x00600be6 = 6294502

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 df 0b 60 e0 0a      00:32:49.930  READ DMA
  c8 00 08 d7 0b 60 e0 0a      00:32:49.930  READ DMA
  c8 00 08 cf 0b 60 e0 0a      00:32:49.930  READ DMA
  c8 00 08 c7 0b 60 e0 0a      00:32:49.930  READ DMA
  c8 00 08 bf 0b 60 e0 0a      00:32:49.930  READ DMA

Error 15 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 4e 56 60 e0  Error: ICRC, ABRT at LBA = 0x0060564e = 6313550

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 47 56 60 e0 0a      00:32:49.300  READ DMA
  c8 00 08 1f 56 60 e0 0a      00:32:49.300  READ DMA
  c8 00 08 07 56 60 e0 0a      00:32:49.300  READ DMA
  c8 00 08 e7 55 60 e0 0a      00:32:49.300  READ DMA
  c8 00 08 af 55 60 e0 0a      00:32:49.300  READ DMA

Error 14 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 ee 53 60 e0  Error: ICRC, ABRT at LBA = 0x006053ee = 6312942

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 e7 53 60 e0 0a      00:32:48.810  READ DMA
  c8 00 08 9f 53 60 e0 0a      00:32:48.810  READ DMA
  c8 00 08 87 53 60 e0 0a      00:32:48.810  READ DMA
  c8 00 08 67 53 60 e0 0a      00:32:48.810  READ DMA
  c8 00 08 4f 53 60 e0 0a      00:32:48.810  READ DMA

Error 13 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 7e 15 60 e0  Error: ICRC, ABRT at LBA = 0x0060157e = 6296958

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 77 15 60 e0 0a      00:32:48.190  READ DMA
  c8 00 08 6f 15 60 e0 0a      00:32:48.190  READ DMA
  c8 00 08 67 15 60 e0 0a      00:32:48.190  READ DMA
  c8 00 08 5f 15 60 e0 0a      00:32:48.190  READ DMA
  c8 00 08 57 15 60 e0 0a      00:32:48.190  READ DMA

Error 12 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 7e 15 60 e0  Error: ICRC, ABRT at LBA = 0x0060157e = 6296958

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 77 15 60 e0 0a      00:26:07.760  READ DMA
  c8 00 08 6f 15 60 e0 0a      00:26:07.760  READ DMA
  c8 00 08 67 15 60 e0 0a      00:26:07.760  READ DMA
  c8 00 08 5f 15 60 e0 0a      00:26:07.760  READ DMA
  c8 00 08 57 15 60 e0 0a      00:26:07.760  READ DMA

SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: handling damage??  90%     13155         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

server@server:~$
```

any ideas greatly appreciated :)

---

### Post by arrrghhh on 2010-06-30
Hrm... I'm guessing you just hit a threshold for errors on that drive.  I'm not sure what an "end-to-end" error is, but it appears you've gone over the threshold of 99 for that error.

Have you had it run a SMART extended or self test?

---

### Post by BobVila on 2010-06-30
From the SMART entry on wikipedia:
184 B8 **End-to-End error**  [[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Green_Arrow_Down.svg/12px-Green_Arrow_Down.svg.png[/IMG]]("http://en.wikipedia.org/wiki/File:Green_Arrow_Down.svg")  This attribute is a part of [HP]("http://en.wikipedia.org/wiki/HP")'s  SMART IV technology and it means that after transferring through the  cache RAM data buffer the parity data between the host and the hard  drive did not match.[[12]]("http://en.wikipedia.org/wiki/S.M.A.R.T.#cite_note-hdsentinel-11")
I suspect it's a false positive.

---

### Post by gobbledigook on 2010-07-01
> **BobVila said:**
> From the SMART entry on wikipedia:
184 B8 **End-to-End error** I suspect it's a false positive.

thanx for your reply, i have skimmed that wiki page... but who ever looks at the references ;)

it doesn't sound too serious, but i will run an extended test whe i get home and have the time to take it offline, the info on this is really sketchy! i suppose no-one wants to make themselves liable if it turns out to be wrong :s 

will post back my extended test, don't think it's wholly necessary but may be useful to ref at a later date :)

now i can relax... laptop this month... and a new drive next ;)

---

