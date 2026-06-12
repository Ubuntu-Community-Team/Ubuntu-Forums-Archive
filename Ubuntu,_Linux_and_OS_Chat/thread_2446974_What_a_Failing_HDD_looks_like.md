---
title: "What a Failing HDD looks like"
date: 2020-07-10
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2020-07-10
Ran some SMART tests today:
```
$ sudo smartctl -t short /dev/sdc
```
Then asked to see the test results:
```
$ sudo smartctl -a /dev/sdc
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.15.0-107-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 3.5" DT01ACA... Desktop HDD
Device Model:     TOSHIBA DT01ACA200
Serial Number:    46G4AEYGS
LU WWN Device Id: 5 000039 fe2de27b8
Firmware Version: MX4OABB0
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Fri Jul 10 09:24:25 2020 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: **PASSED**
...
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALU
E
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       1
  2 Throughput_Performance  0x0005   140   140   054    Pre-fail  Offline      -       69
  3 Spin_Up_Time            0x0007   126   126   024    Pre-fail  Always       -       300 (Ave
rage 301)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       20
**  5 Reallocated_Sector_Ct   0x0033   082   082   005    Pre-fail  Always       -       494**
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   124   124   020    Pre-fail  Offline      -       33
  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       33888
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       18
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       81
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       81
194 Temperature_Celsius     0x0002   181   181   000    Old_age   Always       -       33 (Min/
Max 20/42)
**196 Reallocated_Event_Count 0x0032   068   068   000    Old_age   Always       -       744**
**197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       16**
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       139

SMART Error Log Version: 1
ATA Error Count: 156 (device log contains only the most recent five errors)
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

Error 156 occurred at disk power-on lifetime: 33764 hours (1406 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 93 68 66 57 01  Error: UNC 147 sectors at LBA = 0x01576668 = 22505064
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 fb 64 57 e0 00   1d+05:51:40.964  READ DMA EXT
  25 00 00 fb 5d 57 e0 00   1d+05:51:40.826  READ DMA EXT
  25 00 00 fb 63 57 e0 00   1d+05:51:40.817  READ DMA EXT
  25 00 28 53 59 57 e0 00   1d+05:51:40.814  READ DMA EXT
  25 00 08 f3 64 57 e0 00   1d+05:51:40.814  READ DMA EXT

Error 155 occurred at disk power-on lifetime: 33764 hours (1406 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 fb 62 57 01  Error: UNC at LBA = 0x015762fb = 22504187
...
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     33888         -
# 2  Short offline       Completed without error       00%     33600         -
# 3  Short offline       Completed without error       00%     32762         -
# 4  Short offline       Completed without error       00%      6435         -
# 5  Short offline       Completed without error       00%       995         -

```

So, this disk was replaced today.  It has been running about 3.8 yrs (33888 hrs). It was a Toshiba desktop 2TB HDD. Another, just like it is still in the system being used.  The replacement HDD is a used data center HGST Ultrastar HDD with a 3 yr warranty from my purchase date, 2.0 million hours MTBF, not a consumer desktop version.  People are selling the same HDD model with a 1 yr warranty, so beware as you purchase.  Most new consumer HDDs have a 1 yr warranty. Why buy that when we can get a DC HDD with a 3 yr warranty, for less? These things are tanks.
The Used-but-new-to-me HDD has this in the SMART data:
```
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -
# 2  Short offline       Completed without error       00%     **55127**         -

```
So ... 6.3 yrs already used ... with ZERO Reallocated_Event_Count. It is a middle-aged DC HDD, so broken in.  I have a few other DC hdds with 10+ yrs on them, still with ZERO Reallocated_Event_Counts.

All the "PASSED" and "Completed without error" stuff above is just trying to mislead us.  The drive is definitely failing to the point that replacement is needed. It was part of a RAID1 array and, of course, I have versioned backups for the data too.  Took the disk out of the mdadm array this morning:
```
sudo mdadm --manage /dev/md1  --fail /dev/sdd3
sudo mdadm --manage /dev/md1  --remove  /dev/sdd3
```
Then shutdown the system (it isn't hot-swap cabable), pulled the wrong disk (didn't know that at the time), put in the replacement HDD ... booted and found the wrong disk. Shutdown again, pulled the correct disk, put in the previously pulled Toshiba that was fine and booted. Ah ... /proc/mdstat showed the array as missing 1 disk.
The partitioning was a little funky for the prior disk. On the new-to-me disk, setup a GPT partition table. The drive arrived completely blank.  Actually all SMART data had been reset to 0, including the powered hours, but there was  I only needed 1 partition for the array, so using the start/end sector numbers, I created a partition using fdisk on the drive. Then added the partition to the array.  No format, no setting of RAiD or other Linux partition table bits.
```
sudo mdadm --manage /dev/md1  --add /dev/sdc2
```
and let the sync happen:
```
md1 : active raid1 sdc2[3] sdb3[2]
      1943010816 blocks super 1.2 [2/1] [_U]
      [=====>...............]  recovery = 27.6% (536565760/1943010816) finish=16
9.8min speed=137984K/sec
```

Finished hours later:
```
md1 : active raid1 sdc2[3] sdb3[2]
      1943010816 blocks super 1.2 [2/2] [UU]
```

For fun, I'll take the old HDD and zero everything, run badblocks and try to force the many bad sectors to be "good" again. I could always use a spare 2TB swap-able HDD.  The ZERO ddrescue task has been running over 7 hrs now.

Did I get screwed on that new disk?
Will the old disk actually come back with zero failed sectors?

---

### Post by exploder on 2020-07-10
Good information! I general spend the extra money on the HGST drives if I need a spinning drive, they hold up well! Western Digital Blue drives seem to have a high failure rate.

---

### Post by TheFu on 2020-07-10
I&#8217;ve had 2 hgst NAS disks fail just before 4 yrs of use - 3 yr warranty.  
I&#8217;ve had a few WD-Blue HDDs fail, after a long life.  

At this point in my life avoiding storage hassles for 6-10 yrs is more important than saving $20.  There's only 1 storage vendor where my personal experience has me striving to never give them another penny.  That vendor appears to make excellent 8TB and larger disks now.

I&#8217;ve had some cheap SSDs too that died in under 2 yrs.  There is a difference.

---

### Post by TheFu on 2020-07-18
So I put in the replacement Hitachi HUA723020ALA641 HDD into the array about a week ago and told it to join the array - all was good.

Er ... so I thought.

About 2 days after the install, I started getting these email notifications from SMART:
```
The following warning/error was logged by the smartd daemon:

Device: /dev/sdc [SAT], 2 Currently unreadable (pending) sectors

Device info:
Hitachi HUA723020ALA641, S/N:YFHXBXXX, WWN:5-000cca-223dafxxx, FW:MK7OA840, 2.00 TB

```
What?  That makes no sense.  Before I even inserted the HDD into the machine, I'd checked the SMART data and it was all Zero'd.
```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   054    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   100   100   024    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   020    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       0
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       1
194 Temperature_Celsius     0x0002   193   193   000    Old_age   Always       -       31 (Min/Max 25/31)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
```
See!  No issues.
But now it has:
```
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   133   133   054    Pre-fail  Offline      -       91
  3 Spin_Up_Time            0x0007   100   100   024    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       4
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   125   125   020    Pre-fail  Offline      -       30
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       62
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       4
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       4
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       4
194 Temperature_Celsius     0x0002   157   157   000    Old_age   Always       -       38 (Min/Max 25/40)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
**197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       2**
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

```
2 pending sectors?  You've got to be kidding.  I'm not going to worry - just going to return the drive for a credit. I wouldn't mind if the dead sectors had been automatically relocated. That would be expected behavior, but having them just sit there means something is wrong.

---

### Post by MartyBuntu on 2020-07-19
> **TheFu said:**
> There's only 1 storage vendor where my personal experience has me striving to never give them another penny.  That vendor appears to make excellent 8TB and larger disks now.


Seagate?

---

### Post by mastablasta on 2020-07-20
one thing that always confuses me i the* thresh* parameter. i mean it confuses me because i am not sure if it should up to that point or until that point. so it is it shouldn't' drop below that point or it should go up to that point.

i stopped worrying so much about brands. it's all about real world tests and not having the latest model. seagate was bad, but they fixed the error and then newer tests (indata centers) were much better than WD and for the same price. so i took one, then another one. both work well.

i also bought WD essential (external) which was used as secondary backup of some family photos. so it was not used much at all. once i plugged it in and wanted to transfer a new batch. it didnd't want to read it. i did all sorts of tests and yes the disk failed. just like that. total "usage" must have been measured in a few hours. 

i have a samsung book (external 3.5") that i bough for videos on RPi. i thought it was going to fail after about 5 years. it is now into it's 9th year and doing fine.

as i understand there are basically only 2 manufacturers of hard disks. WD and Seagate. maybe there is still Hitachi. others are just OEM.

back to brands. remember how first Ryzens had issue with linux? well they do not anymore and are really good CPUs. Now Intel has issues taht impacts perofmance. so while you get what you pay for that may change with next patch and speed is then down.

i work for house appliance manufacturer that also makes premium brands. We had a 3,2% failure on one model (untested/unexpected user behaviour), but only those that were made in the first month of production. issue was reported, found and corrected and now they are very reliable with hardly any failures in the first 5 years. so if you bought one from the first batch you might think this is really bad appliance. but actually  they are super reliable, built from good components from trusted suppliers. 
i also have a car that was the last of the model (they were selling out the stock). it was a cheap one at the time (16 years ago) and i thought - well it will do for 5 -6 years and then i will exchange it. but the car had so far only one electronic failure. the rest was old age replacements and external damage (e.g. AC got punctured by small rock or something). so i mostly had only regular services which cost me only about 80 EUR a year. now it started showing it's age (rust). if i had money i would repaint it and fixed it up. it just drives so well and is good enough for my modest needs. the lady at repairs says these are built like "tanks", they just keep going. and it's true. but as i remember when  the first models came out they had many smaller issues. so at the time they offered longer warranty to be able to still get consumers to buy them.but these later models were really reliable. and that's how it is will all products. 

so brand is a guidance but it doesn't mean it will be flawless or reliable. it does mean that older models from that brand will likely be very good.

---

### Post by TheFu on 2020-07-20
Vendors make different models for different purposes. Some are there to be cheap as the primary purpose. Some are meant for heavy duty use in data centers with long lifespans. There are all sorts in between those trying to find a reliability and price mix that customers want.  In general, the warranty tells you how reliable over time a specific vendor's model line is expected/engineered to be.  Sometimes they miss their design goals - high or low.  As a purchaser, I want the cheapest storage that lasts 15 yrs in my type of use. ;)  But I've never seen any storage that wasn't optical with a warranty over 5 yrs.  

I've had storage with 90 day, 1 yr, 3 yr, 5 yr warranties.
Usually, the 90 day warranty was not really about the HDD, but about the external USB case they wrapped around the HDD.  Put "portable" in the title for the model and it almost always gets a 90 day warranty. People drop "portable" storage all the time.

I've had 1 yr warranty disks last 8+ yrs for my use pattern.  I consider those disks a bargain!
I've had multiple 1 yr warranty{insert bad vendor} disks last 13 months and 18 months.  I consider those a rip off, especially since they were sitting next to and used exactly like 1 yr warranty disks from other vendors.

I've had a number of 3 yr warranty disks. I'm sad to say, these haven't met my expectations, but did last beyond the warranty period. Usually, these are "desktop" HDDs.  I have a few WD "Red" HDDs that came with 3 yr warranties. All of these are still running, over 5 yrs old.  Unfortunately, WD has been selling "Red" HDDs that use less than great technology starting this year, so we can't just by a "Red" HDD and know it is good anymore.

I have a number of 5 yr warranty disks.  Up until recently, these were Seagate "Barracuda" or WD "Black" HDDs.  All of these have surpassed my expectations until my last purchase of a HGST "Gold" HDD (see above in this thread).  The only trick here is that "Black" is not about the color of the case, though marketing has certainly been using that ambiguity in a smart (lying to customer) way.

So, as a consumer of storage devices, I'm always looking for devices that are incorrectly priced for the value provided. It is exactly how I handle stock market purchases and selling.  I want to buy when the current price is lower than the "value" for that device.  Of course, with stock investments, I want to "buy low and sell high."  Sounds easy, right?  The market has some inefficiencies built in a few times every year, so if we are ready, we can get good deals on quality companies. Then just wait until the value swings in the opposite way ... overpriced ... and sell then.  
To make all this happen, means we need to be educated buyers.  This is really important for HDDs and SSDs now. There are so many different technologies being sold. They are not all the same.  

"New" technologies scare me for storage. I want 3+ yrs for any new tech to become proven as solid for specific purposes.  I was very late in adding any SSDs to my storage. I was initially burned by SSDs in 2013. Early versions that weren't "enterprise" had terrible write durability. As I became more and more educated about SSDs, I've made some decisions for my simple mind to ensure I'm getting the correct mix in endurance and price for my usage.  If a vendor refuses to publish the **endurance** number for their storage, I won't buy from them. Clearly, they are hiding something they know. There are some popular internet brands that won't tell anyone their endurance TBW engineering targets. Fortunately, there are plenty of other vendors who do.

Hitachi was bought my WD in 2013, but they appear to have retained some separate manufacturing for specific models.  Just read last week that the Ultrastor and Gold lines from each are merging in some models, but not all.  The WD Gold are designed for 10x fewer errors based on engineering designs than the Ultrastor line. These are both data center storage lines. 

If the interest is to compare "Green" vs "Blue" or EasyStore vs Passport lines, I can't help. I've used all of those in the 3.5 inch size.  I've never bought any external 2.5 inch enclosure with a HDD included.  I have a number of 2.5 inch enclosures, but always just put old laptop HDDs into them. Because they only get power from the USB connection, they are really slow, even the USB3 cases.

That's enough blabbering.

---

