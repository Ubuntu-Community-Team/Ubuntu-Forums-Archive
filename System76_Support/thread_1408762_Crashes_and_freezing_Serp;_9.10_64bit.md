---
title: "Crashes and freezing: Serp; 9.10 64bit"
date: 2010-02-16
forum: System76 Support
---

### Post by thinman1189 on 2010-02-16
I have been having numerous problems lately. My laptop will randomly freeze (sometimes with two lights blinking) and sometimes with no indication. Very rarely will commands work: REISUB, etc. 

It will also randomly shut off. Even though it is plugged in, the indicator light won't be on. A few minutes later it turns on, and then I can finally turn my laptop back on. After this, it indicates full battery and sees being plugged in so I don't know why it wasn't even acknowledging the power cable.

After any of this happens (and sometimes even if there were no problems the last time I turned it on) I will get an error on startup saying that a volume is not yet ready to be mounted, and give me the option of going into recovery terminal. Sometimes if I wait, it will continue to load on its own. Sometimes it will begin fsck. Sometimes nothing works (including recovery term) and it takes 5 or more tries to get my laptop to successfully turn on.

Help would be greatly appreciated, as I heavily rely upon this laptop for my studies. Because of the severity of the issues I'm wondering, but hoping it's not, a hardware issue. If it is, I would need to deal with it immediately (it should still be under warranty).

Thanks.


```
sudo smartctl -d ata -a /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 7200.2
Device Model:     ST9200420AS
Serial Number:    5SH0FBZH
Firmware Version: 3.AAA
User Capacity:    200,049,647,616 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Feb 16 19:30:47 2010 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 426) seconds.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 111) minutes.
SCT capabilities: 	       (0x0001)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2347
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   077   060   030    Pre-fail  Always       -       8691518789
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       5200
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2123
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   053   040   045    Old_age   Always   In_the_past 47 (0 20 47 44)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       777
193 Load_Cycle_Count        0x0022   001   001   000    Old_age   Always       -       204292
194 Temperature_Celsius     0x001a   047   060   000    Old_age   Always       -       47 (0 16 0 0)
195 Hardware_ECC_Recovered  0x0012   060   048   000    Old_age   Always       -       40004668
197 Current_Pending_Sector  0x0010   100   100   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x003e   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0000   100   253   000    Old_age   Offline      -       0
254 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

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

### Post by thomasaaron on 2010-02-17
> I have been having numerous problems lately. My laptop will randomly freeze (sometimes with two lights blinking) and sometimes with no indication. Very rarely will commands work: REISUB, etc.

Kernel Panic... could be hardware or software. Most likely hardware given the below information.

> It will also randomly shut off. Even though it is plugged in, the indicator light won't be on. A few minutes later it turns on, and then I can finally turn my laptop back on. After this, it indicates full battery and sees being plugged in so I don't know why it wasn't even acknowledging the power cable.

Can you borrow another ac adapter and see if you get the same symptoms?
Does this happen if you run on AC only?
Does it happen if you run on battery only?

> After any of this happens (and sometimes even if there were no problems the last time I turned it on) I will get an error on startup saying that a volume is not yet ready to be mounted, and give me the option of going into recovery terminal. Sometimes if I wait, it will continue to load on its own. Sometimes it will begin fsck. Sometimes nothing works (including recovery term) and it takes 5 or more tries to get my laptop to successfully turn on.

The shutdowns are probably damaging your filesystem. Please back everything up as soon as possible in case re-imaging becomes necessary.

The instantaneous shutdowns sound a lot like either a memory problem or an overheating issue. Does your fan run?

Can you try running memtest86 on it to see if it throws any errors?

> Reboot your computer. When you see the grub countdown menu, press the 'Esc' key (or 'Shift' key if you're running 9.10). When you see the grub menu, press your 'down' arrow until Memtest86 is highlighted. Then press 'Enter' to start testing.

Please start Ubuntu in the evening before going to bed and let it run all night long. Memory card problems can be subtle, and sometimes they will not show up until the cards start heating up. Often it will take several passes before errors appear.

Please email us the results of your testing.   


In the meantime, let's move this to email. It's most likely a hardware issue, and we should get the RMA formalities handled in case we need to bring it in.

support...at...system76...dot...com

---

