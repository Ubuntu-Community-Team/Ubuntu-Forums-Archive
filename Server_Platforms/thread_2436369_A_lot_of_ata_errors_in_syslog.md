---
title: "A lot of ata errors in syslog"
date: 2020-02-05
forum: Server Platforms
---

### Post by CrewDK on 2020-02-05
I recently upgraded my small home server from 16.04 to 18.04 and noticed a lot of this errors in syslog. They are appearing every hour. 

> Feb  5 09:23:23 fs kernel: [220360.568373] ata5.00: exception Emask 0x10 SAct 0x20000 SErr 0x4090000 action 0xe frozen
Feb  5 09:23:23 fs kernel: [220360.570409] ata5.00: irq_stat 0x00400040, connection status changed
Feb  5 09:23:23 fs kernel: [220360.572458] ata5: SError: { PHYRdyChg 10B8B DevExch }
Feb  5 09:23:23 fs kernel: [220360.573948] ata5.00: failed command: READ FPDMA QUEUED
Feb  5 09:23:23 fs kernel: [220360.575407] ata5.00: cmd 60/08:88:50:c1:bc/04:00:08:00:00/40 tag 17 ncq dma 528384 in
Feb  5 09:23:23 fs kernel: [220360.575407]          res 40/00:88:50:c1:bc/00:00:08:00:00/40 Emask 0x10 (ATA bus error)
Feb  5 09:23:23 fs kernel: [220360.578343] ata5.00: status: { DRDY }
Feb  5 09:23:23 fs kernel: [220360.579824] ata5: hard resetting link
Feb  5 09:23:24 fs kernel: [220361.292401] ata5: SATA link down (SStatus 0 SControl 310)
Feb  5 09:23:29 fs kernel: [220366.540333] ata5: hard resetting link
Feb  5 09:23:35 fs kernel: [220371.896388] ata5: link is slow to respond, please be patient (ready=0)
Feb  5 09:23:36 fs kernel: [220373.276400] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb  5 09:23:36 fs kernel: [220373.277695] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Feb  5 09:23:36 fs kernel: [220373.280743] No Local Variables are initialized for Method [_GTF]
Feb  5 09:23:36 fs kernel: [220373.280748] No Arguments are initialized for method [_GTF]
Feb  5 09:23:36 fs kernel: [220373.280764] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
Feb  5 09:23:36 fs kernel: [220373.336772] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
Feb  5 09:23:36 fs kernel: [220373.338410] No Local Variables are initialized for Method [_GTF]
Feb  5 09:23:36 fs kernel: [220373.338412] No Arguments are initialized for method [_GTF]
Feb  5 09:23:36 fs kernel: [220373.338415] ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT4._GTF, AE_NOT_FOUND (20170831/psparse-550)
Feb  5 09:23:36 fs kernel: [220373.486034] ata5.00: configured for UDMA/133
Feb  5 09:23:36 fs kernel: [220373.486048] ata5: EH complete



Can someone explain me what is it?

---

### Post by SeijiSensei on 2020-02-05
Your drive is heading toward failure. Make sure you have good backups and consider buying a replacement drive.

You can try running "sudo badblocks /dev/sdX" where X is the partition that is throwing the errors. Run it overnight since it will take some time to complete.

---

### Post by TheFu on 2020-02-05
I would run smartctl in test mode, wait for the tests to complete, then run smartctl in report mode to see the results.  The "raw" column is usually the most helpful.

Look for any attributes with "error" or "relocat" in the name.  Those are bad or at least clues as to what might be going bad.  Best case is a poorly connected SATA cable that just needs to be re-seated.  Worst case is the drive is already dead and no data can be retrieved.

The first things to be done are, in this order:
[LIST=1]
[*]Stop using the disk for anything except ... 
[*]Boot from a "Try Ubuntu" flash drive going forward
[*]Get the data you need off it ASAP. That can be just files in the HOME or a 100% bit-for-bit copy.  Expect failures in any bit-for-bit copy.
[*]After all the data is copied, then use smartctl as stated above.
[/LIST]
If you like, post the SMART data here for interpretation.  Use *code tags* or it cannot be read. In the post here, columns should line up just line in a terminal there. If it doesn't, fix the code tags. It wasn't done correctly.

---

### Post by CrewDK on 2020-02-07
I think that troublemaker was an old bad sata cable.  I've changed it 2 days ago and there are no errors since then. 
Thank you all for advices.

---

### Post by TheFu on 2020-02-07
Still need to run **smartctl**.  Seriously.

---

### Post by CrewDK on 2020-02-07
Thank you for your worrying me. 

Do you think that I need to run long test run or will be enough short one? 
Here is my smart info for 2 HDD: 

```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-76-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA HDWD120
Serial Number:    69N6KPPAS
LU WWN Device Id: 5 000039 fdbc2fcab
Firmware Version: MX4OACF0
User Capacity:    2&#8239;000&#8239;398&#8239;934&#8239;016 bytes [2,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Feb  7 20:13:01 2020 MSK
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
data collection:                (14918) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 249) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   139   139   054    Pre-fail  Offline      -       70
  3 Spin_Up_Time            0x0007   128   128   024    Pre-fail  Always       -       305 (Average 287)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       29
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   124   124   020    Pre-fail  Offline      -       33
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       2208
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       29
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       72
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       72
194 Temperature_Celsius     0x0002   222   222   000    Old_age   Always       -       27 (Min/Max 20/40)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       1

SMART Error Log Version: 1
ATA Error Count: 1
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

Error 1 occurred at disk power-on lifetime: 2159 hours (89 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 28 78 c8 17 05  Error: ICRC, ABRT at LBA = 0x0517c878 = 85444728

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 30 e0 68 34 18 40 00      00:28:22.372  WRITE FPDMA QUEUED
  61 30 d8 38 2c 18 40 00      00:28:22.372  WRITE FPDMA QUEUED
  61 38 d0 d8 28 18 40 00      00:28:22.372  WRITE FPDMA QUEUED
  61 10 c8 60 24 18 40 00      00:28:22.372  WRITE FPDMA QUEUED
  61 a8 c0 a0 d0 17 40 00      00:28:22.372  WRITE FPDMA QUEUED

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

```
smartctl -a /dev/sdc
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-76-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA HDWT360
Serial Number:    X880A08GFB1G
LU WWN Device Id: 5 000039 8f8c90817
Firmware Version: 0603
User Capacity:    6&#8239;001&#8239;175&#8239;126&#8239;016 bytes [6,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA >3.2 (0x1ff), 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Feb  7 20:14:41 2020 MSK
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
data collection:                (  120) seconds.
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
recommended polling time:        ( 641) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       6895
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       139
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   079   079   000    Old_age   Always       -       8539
 10 Spin_Retry_Count        0x0033   100   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       117
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       91
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       4108
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       30 (Min/Max 21/50)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       118882312
222 Loaded_Hours            0x0032   087   079   000    Old_age   Always       -       5593
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       522
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

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

As for me - I don't see any criminal records except one "UDMA_CRC_Error_Count" but it was before I changed SATA cable.

---

### Post by TheFu on 2020-02-07
And now you KNOW that was the only issue.
Make versioned backups, sleep well.

---

### Post by CrewDK on 2020-02-07
This sounds almost like 'Live long and prosper' ))
Thank you for worrying my data )

---

