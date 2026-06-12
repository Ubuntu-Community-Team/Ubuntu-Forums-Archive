---
title: "Harddrive Noises Wait it Out?"
date: 2012-10-22
forum: The Cafe
---

### Post by mamamia88 on 2012-10-22
My harddrive is occasionaly making weird noises. Should I order an ssd now or wait and see what happens?  Everything is backed up on dropbox as well as my external harddrive so i'm not worried about losing anything.  i also have an extra hd sitting on my dresser that i could slap in and install xubuntu or something while i wait for ssd in the mail.  should i just hope for the best?  don't really want to spend any money until i have too

---

### Post by pqwoerituytrueiwoq on 2012-10-22
is it under warranty?
ssd prices keep going down just like flash drives, longer you wait better you can get for the same price
just don't keep anything on the drive you cant live without

---

### Post by mamamia88 on 2012-10-22
> **pqwoerituytrueiwoq said:**
> is it under warranty?
ssd prices keep going down just like flash drives, longer you wait better you can get for the same price
just don't keep anything on the drive you cant live without

warranty is long gone.   computer seems to be functioning fine. like i said literally everything important is stored elsewhere.   i do have an extra drive just in case to hold me over until an ssd shipped if this one does crash and i need to wait for shipping

---

### Post by ssam on 2012-10-23
did you check its SMART status? you can use disk utility, or if you prefer commandline tool smartmontools/smartctl

---

### Post by stalkingwolf on 2012-10-23
hard to say.  Ive had noisy drives continue to work with no problems for years,
ive also had them go to hard drive heaven within hours.

Use it but keep everything backed up.

---

### Post by mips on 2012-10-23
Post the SMART information here.

---

### Post by mamamia88 on 2012-10-23
Not sure if overkill but i used smartools on arch if anyone could help interpret results ```
[root@shawn shawn]# smartctl -i /dev/sda
smartctl 6.0 2012-10-10 r3643 [i686-linux-3.6.2-1-ARCH] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint M5
Device Model:     SAMSUNG HM160HI
Serial Number:    S1WWJG0S989153
LU WWN Device Id: 5 0f0000 003989153
Firmware Version: HH100-06
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS, ATA/ATAPI-7 T13/1532D revision 0
SATA Version is:  SATA 2.5, 1.5 Gb/s
Local Time is:    Tue Oct 23 11:57:22 2012 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

[root@shawn shawn]# smartctl -c /dev/sda
smartctl 6.0 2012-10-10 r3643 [i686-linux-3.6.2-1-ARCH] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(   55) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  55) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

[root@shawn shawn]# smartctl -t short /dev/sda
smartctl 6.0 2012-10-10 r3643 [i686-linux-3.6.2-1-ARCH] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Tue Oct 23 12:00:49 2012

Use smartctl -X to abort test.
[root@shawn shawn]# smartctl -a /dev/sda
smartctl 6.0 2012-10-10 r3643 [i686-linux-3.6.2-1-ARCH] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint M5
Device Model:     SAMSUNG HM160HI
Serial Number:    S1WWJG0S989153
LU WWN Device Id: 5 0f0000 003989153
Firmware Version: HH100-06
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS, ATA/ATAPI-7 T13/1532D revision 0
SATA Version is:  SATA 2.5, 1.5 Gb/s
Local Time is:    Tue Oct 23 12:02:11 2012 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(   55) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  55) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2125
  4 Start_Stop_Count        0x0032   002   002   000    Old_age   Always       -       99999
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       12903
 10 Spin_Retry_Count        0x0032   100   100   051    Old_age   Always       -       134
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3048
191 G-Sense_Error_Rate      0x0032   098   098   000    Old_age   Always       -       21294
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       347
194 Temperature_Celsius     0x0022   130   085   000    Old_age   Always       -       36 (Min/Max 12/51)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       14
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   252   098   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       64
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       9
201 Soft_Read_Error_Rate    0x0032   252   252   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   097   097   000    Old_age   Always       -       3903
225 Load_Cycle_Count        0x0032   049   049   000    Old_age   Always       -       522861

SMART Error Log Version: 1
ATA Error Count: 47 (device log contains only the most recent five errors)
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

Error 47 occurred at disk power-on lifetime: 5872 hours (244 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 50 10 08 ec  Error: ICRC, ABRT 8 sectors at LBA = 0x0c081050 = 201855056

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 50 10 08 ec 00      00:04:56.500  READ DMA
  ef 10 03 b7 8a 07 a0 00      00:04:26.000  SET FEATURES [Reserved for Serial ATA]
  c8 00 20 98 8a 07 ec 00      00:04:25.562  READ DMA
  c8 00 50 80 86 07 ec 00      00:04:25.125  READ DMA
  c8 00 20 e0 86 07 ec 00      00:04:25.125  READ DMA

Error 46 occurred at disk power-on lifetime: 5851 hours (243 days + 19 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 a0 2a 9b ec  Error: ICRC, ABRT 8 sectors at LBA = 0x0c9b2aa0 = 211495584

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a0 2a 9b ec 00      00:04:21.750  READ DMA
  ef 10 03 df bb d2 a0 00      00:03:51.000  SET FEATURES [Reserved for Serial ATA]
  ca 00 08 d8 bb d2 ee 00      00:03:50.937  WRITE DMA
  ca 00 48 90 bb d2 ee 00      00:03:50.937  WRITE DMA
  c8 00 08 88 9a 0f ef 00      00:03:50.937  READ DMA

Error 45 occurred at disk power-on lifetime: 4919 hours (204 days + 23 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 00 08 00 e4  Error: ICRC, ABRT 8 sectors at LBA = 0x04000800 = 67110912

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e4 00      00:12:36.250  READ DMA
  ef 10 03 af 98 a1 a0 00      00:12:06.187  SET FEATURES [Reserved for Serial ATA]
  c8 00 08 b0 ff ff ef 00      00:12:05.187  READ DMA
  c8 00 c0 08 00 00 e0 00      00:12:05.125  READ DMA
  c8 00 08 00 08 80 e5 00      00:12:04.562  READ DMA

Error 44 occurred at disk power-on lifetime: 1820 hours (75 days + 20 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 20 18 cc d6 e9  Error: ICRC, ABRT 32 sectors at LBA = 0x09d6cc18 = 165071896

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 18 cc d6 e9 00      01:52:36.187  READ DMA
  ef 10 03 3f 70 a3 a0 00      01:51:55.437  SET FEATURES [Reserved for Serial ATA]
  ca 00 08 38 70 a3 ea 00      01:51:35.062  WRITE DMA
  ca 00 08 38 70 a3 ea 00      01:51:33.062  WRITE DMA
  c8 00 60 00 61 59 ea 00      01:51:31.062  READ DMA

Error 43 occurred at disk power-on lifetime: 1808 hours (75 days + 8 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 18 00 b0 5c ea  Error: ICRC, ABRT 24 sectors at LBA = 0x0a5cb000 = 173846528

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 18 00 b0 5c ea 00      00:05:02.500  READ DMA
  ef 10 03 1f a7 5c a0 00      00:04:25.375  SET FEATURES [Reserved for Serial ATA]
  c8 00 08 18 a7 5c ea 00      00:04:24.812  READ DMA
  c8 00 10 40 a7 5c ea 00      00:04:24.812  READ DMA
  c8 00 08 10 a7 5c ea 00      00:04:24.812  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     12903         -

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
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

---

### Post by CharlesA on 2012-10-23
> **mamamia88 said:**
> Not sure if overkill but i used smartools on arch if anyone could help interpret results ```

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2125
  4 Start_Stop_Count        0x0032   002   002   000    Old_age   Always       -       99999
[COLOR="Red"]  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0[/COLOR]
  7 Seek_Error_Rate         0x000e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       12903
[COLOR="Purple"] 10 Spin_Retry_Count        0x0032   100   100   051    Old_age   Always       -       134[/COLOR]
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3048
191 G-Sense_Error_Rate      0x0032   098   098   000    Old_age   Always       -       21294
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       347
194 Temperature_Celsius     0x0022   130   085   000    Old_age   Always       -       36 (Min/Max 12/51)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       14
[COLOR="Red"]196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   252   098   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0[/COLOR]
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       64
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       9
201 Soft_Read_Error_Rate    0x0032   252   252   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   097   097   000    Old_age   Always       -       3903
225 Load_Cycle_Count        0x0032   049   049   000    Old_age   Always       -       522861

SMART Error Log Version: 1
[COLOR="Red"]ATA Error Count: 47 (device log contains only the most recent five errors)[/COLOR]
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

[COLOR="Red"]Error 47 occurred at disk power-on lifetime: 5872 hours (244 days + 16 hours)[/COLOR]
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 50 10 08 ec  Error: ICRC, ABRT 8 sectors at LBA = 0x0c081050 = 201855056

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 50 10 08 ec 00      00:04:56.500  READ DMA
  ef 10 03 b7 8a 07 a0 00      00:04:26.000  SET FEATURES [Reserved for Serial ATA]
  c8 00 20 98 8a 07 ec 00      00:04:25.562  READ DMA
  c8 00 50 80 86 07 ec 00      00:04:25.125  READ DMA
  c8 00 20 e0 86 07 ec 00      00:04:25.125  READ DMA

[COLOR="Red"]Error 46 occurred at disk power-on lifetime: 5851 hours (243 days + 19 hours)[/COLOR]
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 a0 2a 9b ec  Error: ICRC, ABRT 8 sectors at LBA = 0x0c9b2aa0 = 211495584

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a0 2a 9b ec 00      00:04:21.750  READ DMA
  ef 10 03 df bb d2 a0 00      00:03:51.000  SET FEATURES [Reserved for Serial ATA]
  ca 00 08 d8 bb d2 ee 00      00:03:50.937  WRITE DMA
  ca 00 48 90 bb d2 ee 00      00:03:50.937  WRITE DMA
  c8 00 08 88 9a 0f ef 00      00:03:50.937  READ DMA

[COLOR="Red"]Error 45 occurred at disk power-on lifetime: 4919 hours (204 days + 23 hours)[/COLOR]
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 00 08 00 e4  Error: ICRC, ABRT 8 sectors at LBA = 0x04000800 = 67110912

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e4 00      00:12:36.250  READ DMA
  ef 10 03 af 98 a1 a0 00      00:12:06.187  SET FEATURES [Reserved for Serial ATA]
  c8 00 08 b0 ff ff ef 00      00:12:05.187  READ DMA
  c8 00 c0 08 00 00 e0 00      00:12:05.125  READ DMA
  c8 00 08 00 08 80 e5 00      00:12:04.562  READ DMA

[COLOR="Red"]Error 44 occurred at disk power-on lifetime: 1820 hours (75 days + 20 hours)[/COLOR]
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 20 18 cc d6 e9  Error: ICRC, ABRT 32 sectors at LBA = 0x09d6cc18 = 165071896

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 18 cc d6 e9 00      01:52:36.187  READ DMA
  ef 10 03 3f 70 a3 a0 00      01:51:55.437  SET FEATURES [Reserved for Serial ATA]
  ca 00 08 38 70 a3 ea 00      01:51:35.062  WRITE DMA
  ca 00 08 38 70 a3 ea 00      01:51:33.062  WRITE DMA
  c8 00 60 00 61 59 ea 00      01:51:31.062  READ DMA

[COLOR="Red"]Error 43 occurred at disk power-on lifetime: 1808 hours (75 days + 8 hours)[/COLOR]
  When the command that caused the error occurred, the device was in an unknown state.
```

That doesn't look right at all.

Here's what the smart log from one of the drives on my server:

```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   096   096   016    Pre-fail  Always       -       393218
  2 Throughput_Performance  0x0005   132   132   054    Pre-fail  Offline      -       103
  3 Spin_Up_Time            0x0007   151   151   024    Pre-fail  Always       -       395 (Average 563)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       172
[COLOR="Blue"]  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       3[/COLOR]
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   107   107   020    Pre-fail  Offline      -       41
  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       23248
[COLOR="Purple"] 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0[/COLOR]
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       172
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       901
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       901
194 Temperature_Celsius     0x0002   181   181   000    Old_age   Always       -       33 (Min/Max 22/54)
[COLOR="Blue"]196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       3
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0[/COLOR]
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 0
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

See highlighted parts. I would back up any data on the drive and get a replacement asap.

---

### Post by mamamia88 on 2012-10-23
Thanks for all your help.  Just ordered a 80gb ssd from tigerdirect.    Look forward to installing it and seeing how fast it is.   Any opinions on the one i ordered?  It's a netbook so ssd should be better because i can't break the hd by dropping it. [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4969041](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4969041) hopefully the rebate is still good.  Last thing will a tiny bit of wd40 hurt a motherboard? can't get last damn screw out

---

### Post by Paqman on 2012-10-23
> **mamamia88 said:**
> Last thing will a tiny bit of wd40 hurt a motherboard? can't get last damn screw out

Using oils on electronics is not good practice. You'd have to thoroughly degrease it afterwards. 

The best way to get stubborn screws out is some diamond paste (eg: Screw Grab) on the screw head, also try a better screwdriver, and push really hard while turning. Some screwdrivers will accept a spanner on the shaft to give you some extra torque while you lean hard on the driver. You should be able to get anything out without resorting to something gash like WD40.

---

### Post by CharlesA on 2012-10-23
> **Paqman said:**
> Using oils on electronics is not good practice. You'd have to thoroughly degrease it afterwards. 

The best way to get stubborn screws out is some diamond paste (eg: Screw Grab) on the screw head, also try a better screwdriver, and push really hard while turning. Some screwdrivers will accept a spanner on the shaft to give you some extra torque while you lean hard on the driver. You should be able to get anything out without resorting to something gash like WD40.
+1. diamond paste would probably help.

If the screw is stripped, some advice can be found here:
[http://www.todayifoundout.com/index.php/2010/02/the-12-best-ways-to-remove-stripped-screws/](http://www.todayifoundout.com/index.php/2010/02/the-12-best-ways-to-remove-stripped-screws/)

---

### Post by mips on 2012-10-23
> **mamamia88 said:**
>   Last thing will a tiny bit of wd40 hurt a motherboard? can't get last damn screw out

Don't use wd40 or other penetrating oils on a MB. I suspect you have a MB screw that's not coming out. This usually means you have a stuck/stripped MB standoff. best way to deal with it is to remove the chassis/case side panel on the MB backplate side and then using some pliers to turn out the offending standoff, once you get the MB off the backplate you can use pliers to grip the standoff and turn the screw with a normal screwdriver.

---

### Post by CharlesA on 2012-10-23
> **mips said:**
> Don't use wd40 or other penetrating oils on a MB. I suspect you have a MB screw that's not coming out. This usually means you have a stuck/stripped MB standoff. best way to deal with it is to remove the chassis/case side panel on the MB backplate side and then using some pliers to turn out the offending standoff, once you get the MB off the backplate you can use pliers to grip the standoff and turn the screw with a normal screwdriver.
That would be a pain on a netbook, wouldn't it?

---

### Post by mamamia88 on 2012-10-23
> **mips said:**
> Don't use wd40 or other penetrating oils on a MB. I suspect you have a MB screw that's not coming out. This usually means you have a stuck/stripped MB standoff. best way to deal with it is to remove the chassis/case side panel on the MB backplate side and then using some pliers to turn out the offending standoff, once you get the MB off the backplate you can use pliers to grip the standoff and turn the screw with a normal screwdriver.
no it's a hinge screw by where the display connects to rest of computer.   i just quirted a tiny little drop and managed to get it out.  hopefully didn't do any damage.   going to replace the screws with new ones when the new hd comes in.  Anyone know where to buy screws that small?

---

### Post by mips on 2012-10-23
> **mamamia88 said:**
> no it's a hinge screw by where the display connects to rest of computer.

I need a picture as i have no idea what you are referring too. Is this a laptop?
I have thousands of screws in my drawer ifs you are interested, dunno if it's worth a trip to africa though :biggrin:

---

### Post by Paqman on 2012-10-23
> **mamamia88 said:**
> Anyone know where to buy screws that small?

Lilliput?

I'm sure you can pick them up at your local electronics store. Tbh once you've pulled a few computers apart you tend to end up with about a trillion of the little suckers, I've never had to buy any. Ask a geeky friend?

---

### Post by stalkingwolf on 2012-10-25
also  they are usually available on ebay.  usually reasonable.

---

