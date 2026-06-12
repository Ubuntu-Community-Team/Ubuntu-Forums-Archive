---
title: "Is my hard drive failing???"
date: 2010-05-29
forum: Server Platforms
---

### Post by u-slayer on 2010-05-29
On my old computer the hard drive runs great. I tested it with badblocks and got no errors.

On the new computer, It won't even access the drive without an error in dmesg or it will acesss it, but both badblocks and smartctl show errors.

Here is the smartctl on the new computer

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD103SJ
Serial Number:    S246J90Z145145
Firmware Version: 1AJ100E4
User Capacity:    1,000,204,886,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x28
Local Time is:    Sat May 29 14:38:00 2010 CDT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 120)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (9420) seconds.
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
recommended polling time: 	 ( 157) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       84
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   073   073   025    Pre-fail  Always       -       8329
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       38
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       2325
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       43
191 G-Sense_Error_Rate      0x0022   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   058   000    Old_age   Always       -       33 (Lifetime Min/Max 18/42)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       274
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       2
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       43

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

Error 3 occurred at disk power-on lifetime: 2285 hours (95 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      00:00:06.494  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:06.494  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:00:06.494  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 08      00:00:06.494  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08      00:00:06.494  IDENTIFY DEVICE

Error 2 occurred at disk power-on lifetime: 2285 hours (95 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      00:00:06.256  IDENTIFY DEVICE
  00 00 01 01 00 00 00 08      00:00:06.256  NOP [Abort queued commands]
  00 00 01 01 00 00 00 08      00:00:06.256  NOP [Abort queued commands]
  00 00 01 01 00 00 00 00      00:00:06.256  NOP [Abort queued commands]
  00 00 01 01 00 00 00 00      00:00:06.256  NOP [Abort queued commands]

Error 1 occurred at disk power-on lifetime: 2285 hours (95 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 08      00:00:06.251  IDENTIFY DEVICE
  00 00 00 00 00 00 00 08      00:00:06.251  NOP [Abort queued commands]
  00 00 00 00 00 00 00 08      00:00:06.250  NOP [Abort queued commands]
  00 00 00 d8 37 e0 40 08      00:00:06.250  NOP [Abort queued commands]
  00 00 00 d8 36 e0 40 08      00:00:06.250  NOP [Abort queued commands]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       80%      2324         356482380
# 2  Extended offline    Completed: read failure       80%      2324         356482380
# 3  Short offline       Completed: read failure       90%      2324         356482380
# 4  Short offline       Completed without error       00%      2303         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed_read_failure [80% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```


Should I replace it, or is there something else going on?

---

### Post by u-slayer on 2010-05-30
:confused:

---

### Post by CharlesA on 2010-05-30
What are the exact errors you are getting?

---

### Post by Vegan on 2010-05-30
Your disk is OK, some drives will report errors as they heal themselves, some do not.

Your disk seems to have passed the SMART tests OK.

---

### Post by bumanie on 2010-05-30
Looks OK to me - try this command - if all is OK it will say 'passed'
> sudo smartctl -H /dev/sdxsubstituting x for your drive letter

---

### Post by u-slayer on 2010-05-30
> **Vegan said:**
> Your disk is OK, some drives will report errors as they heal themselves, some do not.

Your disk seems to have passed the SMART tests OK.

How is:

```
1  Extended offline    Completed: read failure       80%      2324         356482380
# 2  Extended offline    Completed: read failure       80%      2324         356482380
```

Okay?

also badblocks reports errors.

---

### Post by ian dobson on 2010-05-30
Hi,

Did you read the output from smartctl?

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

Regards
Ian Dobson

---

### Post by frostschutz on 2010-05-30
I had a drive fail yesterday, with pretty much the same output as yours.

Health assessment OK, reallocated sector count zero, but pending sector count 1, and read errors during the long self test.

I actually discovered while making a backup and the system locked up (shouldn't happen normally but it's an old machine, IDE drive, and the so much praised new pata drivers just couldn't handle this kind of drive failure :popcorn:)

Either way, I managed to copy all data off using rsync, and dd, eventually, worming my way around the defective area. It was one of the lucky cases where only a very small region of the drive could not be read any more.

---

### Post by etdsbastar on 2010-05-30
Try using the following to check and run selftests on your hard drive:

Open system menu, Administration then Disk Utility,

Select your hard drive, click the option Smart Data and then run a self test, you will be prompted with all the results and then post the errors here, if found one...

Please see the screen shot.

---

### Post by Vegan on 2010-05-30
My old WD disk that died when my old server crapped out had a problem or 3 until after about a year it stabilized.

In total there were 638 errors before it was stable.

Today the disk is gone as the PSU shorted kiling it. Now I have other disks as I have been procuring them of late with new low prices.

I bought a 500 GB disk for < $50 of late. Upgraded the Windows box boot disk with it. One before that was $65 and I use that one for general storage. The old 320 GB disk still works too but its earmarked for the new web server.

---

### Post by lwalper on 2010-06-03
Similar question -- is my hard drive failing? I've got a Toshiba Satelite laptop that was running Vista, but came up with an error on boot that it could not find some OS file?? I tried the restore process to no avail - figured the HD was writing some bad data or the data it was looking for was in a bad sector. So, tried to install XP which failed due to hardware problems?? So, since it uses a different file system I thought I'd try Ubuntu. Build 7.04 v1 would not install, but I've now installed Xubuntu 8.10 which installed without a hitch (and I'm currently using the laptop to write this tome).

I entered
sudo smartctl -H /dev/sd0

and get the reply
sudo: smartctl: command not found

Where do I find smartctl ?

---

### Post by migueletorres on 2010-06-04
I'm having the same problems, and not only one but almost every once in a week, and their all come since my installation of 10.04.

I'm very dispointed with the 64 bit version, is awfull and nowhere in the web we can find a real solution for this har disk failures...

---

### Post by CharlesA on 2010-06-04
Use a different distro or version if you are sure that the disk failure warnings are false (and report a bug if it is indeed a bug).

---

### Post by disabledaccount on 2010-06-05
> **u-slayer said:**
> 
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       84
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   073   073   025    Pre-fail  Always       -       8329
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       38
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       2325
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       43
191 G-Sense_Error_Rate      0x0022   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   058   000    Old_age   Always       -       33 (Lifetime Min/Max 18/42)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       274
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       2
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       43

```Should I replace it, or is there something else going on?199 (0xC7)=274, what means that you have broken SATA cable - the main source of your problems. Secondary: you have one Pending Sector: 197(0xC5) - this is not tragedy and taking into account small uptime (2325h) i would say - you can live with this.

...ehh, i have read this topic from begin -> this is strange for me, that winblows clickers creates special topics for SMART on their forums - they understand how important it is in many situations - while linux people seems to know nothing about that - even though, we have better tools to access HDD internals.

"pearls":
> "Your disk is OK, some drives will report errors as they **heal themselves**, some do not."
"Looks OK to me - try this command - **if all is OK it will say 'passed**'":)

The truth about SMART is, that practically it does not work -> at all, on any HDD model.
You can only get SMART alert both by mistake or just too late ->You can **** on the "OK/Passed" indicators. Real and valuable information is "hidden" in numbers - the only way is to learn their meaning.

...i don't know if i will have time for reply, so I say it now:  i'm curious who can discover one intentional error in my diagnostic?

...nobody...
the answer: total drive uptime was only 9h or 38h, not 2325 - and why? Samsung does not show power-on-hours, instead it counts internal clock ticks of frequency about 256Hz or minutes in some models . The same behaviour can be observed in older Maxtor drives - so it is good to know about that "phenomenon" if someone wants to estimate hdd's age ;)
How to check which algorithm is used?
Its simple: power on the drive and check SMART several times, every minute or so..

---

