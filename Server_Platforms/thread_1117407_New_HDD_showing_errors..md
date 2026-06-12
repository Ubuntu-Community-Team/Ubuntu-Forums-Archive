---
title: "New HDD showing errors."
date: 2009-04-05
forum: Server Platforms
---

### Post by Almeister9 on 2009-04-05
Hi all,
I have created a server using Ubuntu 8.10 server on a 40GB IDE HDD with a (brand new)500GB SATA2 HDD for DATA.
This is on a GA-81865 GMA mobo with 512MB RAM.

The server is to serve 8 mac machines mainly on Leopard 10.5 and one PC via Samba.(latest version)

The installation went live approx 55 days ago and although there have been some problems that it appears may be due to Adobe CS products being incompatible with Leopard, everything seems to have been going OK with the server.

Until last Wednesday.

All mac users started saying that they were getting kicked off the server and could not open files on the server. The monitor connected to the server (not logged on at the time) and was filling up with errors.

I created a Samba mount on the small system HDD (IDE) and copied the required data across so that the users could still work (mainly InDesign files).
After restarting the server to be on the safe side all users were able to use the new Samba Share and the errors started to subside but continued much slower.

On a hunch I powered down the server early Thrursday morning and replaced the SATA cable on the SATA HDD and once I did that, the errors stopped all together. I left it for another day (Friday) and not a single error showed up on the screen.

So this morning I moved the files back onto the SATA HDD Samba Share and let the users back at them, thinking that the problem had been the SATA cable.

After about two hours of use, the errors came back again and users started to get kicked off again.
The errors look like this:
```
[263652.321912] ata3.00: status: {DRDY ERR}
[263652.321931] ata3.00: error: {UNC}
[263655.303655] ata3.00: exception Emask 0x0 SAct 0x0 action 0x0
[263655.303693] ata3.00: BMDMA stst 0x24
[263655.303716] ata3.00  cmd 25/00:98:0f:68:f0/00:31:00:00/e0 tag 0 dma 7782 in
[263655.303718]          res 51/40:00:7b:68:f0/40:00:31:00:00/00 Emask 0x9 (media error)
[263655.303786] ata3.00: status  {DRDYERR}
[263655.303805] ata3.00: error   {UNC}
[263655.430678] end_request:  I/O error, dev sdb, sector 837838971
```

I have installed smartmon last Thursday and when I ran it this morning I got this output:
```
alan@ubuntu:~$ sudo smartctl -a /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3500320AS
Serial Number:    5QM3ZYHD
Firmware Version: SD1A
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Apr  6 12:32:54 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (  25) The self-test routine was aborted by
                                        the host.
Total time to complete Offline
data collection:                 ( 650) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 119) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103b) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   106   100   006    Pre-fail  Always       -       208894399
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       5
  5 Reallocated_Sector_Ct   0x0033   099   099   036    Pre-fail  Always       -       39
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       67366
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1417
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       14
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       670
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       65537
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   074   068   045    Old_age   Always       -       26 (Lifetime Min/Max 26/29)
194 Temperature_Celsius     0x0022   026   040   000    Old_age   Always       -       26 (Lifetime Min/Max 0/26)
195 Hardware_ECC_Recovered  0x001a   036   036   000    Old_age   Always       -       208894399
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       633
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       633
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 676 (device log contains only the most recent five errors)
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

Error 676 occurred at disk power-on lifetime: 1341 hours (55 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 98 ff ff ff ef 00   3d+01:14:32.992  READ DMA EXT
  27 00 00 00 00 00 e0 00   3d+01:14:32.990  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02   3d+01:14:32.970  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 02   3d+01:14:32.955  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   3d+01:14:32.910  READ NATIVE MAX ADDRESS EXT

Error 675 occurred at disk power-on lifetime: 1341 hours (55 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 98 ff ff ff ef 00   3d+01:14:30.011  READ DMA EXT
  27 00 00 00 00 00 e0 00   3d+01:14:30.010  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02   3d+01:14:29.990  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 02   3d+01:14:29.976  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   3d+01:14:29.960  READ NATIVE MAX ADDRESS EXT

Error 674 occurred at disk power-on lifetime: 1341 hours (55 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 98 ff ff ff ef 00   3d+01:14:27.001  READ DMA EXT
  27 00 00 00 00 00 e0 00   3d+01:14:27.000  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02   3d+01:14:26.980  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 02   3d+01:14:26.961  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   3d+01:14:26.940  READ NATIVE MAX ADDRESS EXT

Error 673 occurred at disk power-on lifetime: 1341 hours (55 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 98 ff ff ff ef 00   3d+01:14:24.001  READ DMA EXT
  27 00 00 00 00 00 e0 00   3d+01:14:24.000  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02   3d+01:14:23.980  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 02   3d+01:14:23.962  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   3d+01:14:23.940  READ NATIVE MAX ADDRESS EXT

Error 672 occurred at disk power-on lifetime: 1341 hours (55 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 98 ff ff ff ef 00   3d+01:14:21.022  READ DMA EXT
  27 00 00 00 00 00 e0 00   3d+01:14:21.020  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02   3d+01:14:21.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 02   3d+01:14:20.989  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00   3d+01:14:20.970  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      00%      1321         -

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

This, to me is pointing to a bad Hard Drive (though I am not very experienced in Linux in general), but as I have said, It is a brand new HDD (Seagate).

can it be a problem with the older motherboard's SATA controllers?

can anybody out there shed any light on this or recomend a course of action for me?

Any help at all would be greatly appreciated.
Cheers Al.

---

### Post by wirelessmonkey on 2009-04-06
```
 [263655.430678] end_request:  I/O error, dev sdb, sector 837838971 
```

...Makes it pretty obvious that there is a problem with the physical disk.
I suggest you fdisk it first, replace if necessary.

---

