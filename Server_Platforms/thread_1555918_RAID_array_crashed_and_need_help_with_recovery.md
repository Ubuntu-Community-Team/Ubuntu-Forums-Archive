---
title: "RAID array crashed and need help with recovery"
date: 2010-08-18
forum: Server Platforms
---

### Post by Plecebo on 2010-08-18
I have an 8 x 1TB drive RAID6 array that broke the other day when I was copying lots of data to it over the network on a hot day. 

I have not yet solved the "how do I backup 6 TB of data in a reasonable way" so I am stuck tip toeing around trying to coax the array into resurrecting long enough for me to get the CRITICAL data (photos etc) off of the thing. 

The first strange thing I noticed was looking at /proc/mdstat was that all 8 of my drives were now marked as spares. I thought that was strange. 

I tried several different things to try and get it to start the /dev/md0 device to no avail. The closest I got was to get it to say it couldn't start with 5 devices and 3 spares (sorry, I don't remember the specific verbiage)

I then ran a short SMART selftest on each of the RAID drives and they all came back fine. 

I tried to fail out the drives:
```
mdadm /dev/md0 --fail /dev/hdb1 --remove /dev/hdb1
```
then re-add them
```
mdadm /dev/mdo --add /dev/hdb1
```
but they are added back as spares. 

Finally I decided to stop the array
```
mdadm --stop /dev/md0
```
and remove it
```
mdadm --remove /dev/md0
```

Then I recreated it
```
mdadm --create /dev/md0 --raid-level=6 /dev/sd{b,c,d,e,f,g,h,i}1
```
I indicated that I wanted to continue even though the devices had a raid superblock already and the device was created. 

Checking /proc/mdstat again this time showed the device resyncing and I hoped that after the rebuild I would be able to access my data. 

That didn't happen, after 15 minutes or so one of the drives failed out of the array. followed over the next few minutes by one more drive failing out. 

I tried much of the same stuff, removing, re-adding etc etc but nothing could keep the array up. 

I tried several more time to --remove and subsequently --create the array anew, with similar results. Not always the same two drives that fail out, but usually one will fail out, and within 10 minutes another will fail out. 

I'm 90% sure that the drives overheated, and it is looking that at least 3, and possibly more drives were impacted. But i'm not sure which ones for sure.

Right now I'm running a badblocks scan of a drive, but not sure if this is the right approach to identifying bad drives, or if there is a better approach?

Is there a trick that might allow the array to resync? Or some reason that the drives keep failing out?

Is there a way for me to scan each drive and find out what is wrong with it? Or at the very least identify the drives that are bad so I can look at replacing them? 

Am I on the right path? 

Any suggestions are welcome.

---

### Post by brettg on 2010-08-18
Query the internal error monitoring on each drive using smartmontools (smartctl) to check whether you are dealing with hardware failures or not.

---

### Post by Plecebo on 2010-08-19
Thanks for the response. When i ran the short smart test i checked the smartctl -a  output of each device and found nothing that looked to me like errors, but admittedly I've not looked at many of these before. 

Here is the output from one of the drives that mdadm kicked out when it was re-syncing

```
smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EADS-65L5B1
Serial Number:    WD-WCAU49102658
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Aug 18 21:40:24 2010 PDT
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
data collection: 		 (22200) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   200   166   021    Pre-fail  Always       -       4975
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       55
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       9246
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       42
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       4
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       55
194 Temperature_Celsius     0x0022   120   105   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       499
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      9221         -
# 2  Extended offline    Completed without error       00%       178         -
# 3  Short offline       Completed without error       00%       171         -

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

### Post by Plecebo on 2010-08-19
So if the SMART short scan showed no errors, and so far my badblocks scans have not turned up any errors (i've scanned 5 drives so far). Is it safe to assume that the drives are not bad (assuming errors don't show up in the other drives once i've finished my badblocks scan)?

If it is not a hardware issue, is there a way to reassemble my drives to get them functioning in a raid array? 

Are there specific log entries that I should be looking for/at that might help explain? 

Apologies if this should be obvious, but I feel like i'm missing something. I know just enough to get myself into trouble LOL.

---

### Post by MakOwner on 2010-08-19
> **Plecebo said:**
> So if the SMART short scan showed no errors, and so far my badblocks scans have not turned up any errors (i've scanned 5 drives so far). Is it safe to assume that the drives are not bad (assuming errors don't show up in the other drives once i've finished my badblocks scan)?

If it is not a hardware issue, is there a way to reassemble my drives to get them functioning in a raid array? 

Are there specific log entries that I should be looking for/at that might help explain? 

Apologies if this should be obvious, but I feel like i'm missing something. I know just enough to get myself into trouble LOL.

Welcome to software raid on the cheap with desktop hardware, amirite? 
I had an array of 8 JBOD drives on two 4 port promise controllers at one point. What I saw were occasional times when drives would for no apparent reason just drop from the array. They would then re-appear as the next device in the array and get added back.
Spent a lot time rebuilding.  I think it was a timing issue. Last crash I lost two disks out of the array so I finally gave up and went the external enclosure with a single eSata controller.

I would up doing pretty much I think what you described above - I was able to get the array to a point where I could read the data off it by forcing an assembly of the array with only one drive missing, and copied the data off. Since the drive weren't really bad this worked, but had I really lost a drive...

I don't recall the exact syntax but there is a 'force' parameter to rebuild an array with mdamd -- be careful though as I have -no clue- what I'm talking about, so don't look for me if you lose data! ):P

---

### Post by Plecebo on 2010-08-19
Thanks for the reply MakOwner!

> **MakOwner said:**
> Welcome to software raid on the cheap with desktop hardware, amirite? 
No kidding right. Part of the reason I went raid6 rather then raid5 was that I was expecting the drives to start crapping out at 1-2 years. I figured I would replace them one at a time with the latest big drives (currently 2TB drives) until they were all replaced, increasing my storage. The original plan was that if I ever had 2 drives fail I would shut down the array and wait for two new drives to minimize potential data loss. The best laid plans *pulls out hair*

> **MakOwner said:**
> 
I don't recall the exact syntax but there is a 'force' parameter to rebuild an array with mdamd -- be careful though as I have -no clue- what I'm talking about, so don't look for me if you lose data! ):P
Thanks for the info. To be clear are you talking about forcing the assembly, or forcing a rebuild? 

I had tried to force the assembly, but the drives keep kicking out of the array during the rebuild process. The furthest I got was like 15% through... which isn't very close :(. 

I've been considering trying to use the assume-clean switch when assembling. from the man page
>        --assume-clean
              Tell mdadm that the array pre-existed and is known to be  clean.
              It  can be useful when trying to recover from a major failure as
              you can be sure  that  no  data  will  be  affected  unless  you
              actually  write to the array.  It can also be used when creating
              a RAID1 or RAID10 if you want to avoid the initial resync,  howâ
              ever  this  practice â while normally safe â is not recommended.
              Use this only if you really know what you are doing.

and of course I would hardly say i "really know what I am doing", but this sounds like it might get me mounted without requireing a resync, then I could try to pull off all the irreplacable data and start over. 

If anyone has a suggestion about assume-clean I'd be glad to hear it. 

For now I continue to check for badblocks, none found so far (seems good :) )

---

### Post by MakOwner on 2010-08-19
> **Plecebo said:**
> Thanks for the reply MakOwner!


No kidding right. Part of the reason I went raid6 rather then raid5 was that I was expecting the drives to start crapping out at 1-2 years. I figured I would replace them one at a time with the latest big drives (currently 2TB drives) until they were all replaced, increasing my storage. The original plan was that if I ever had 2 drives fail I would shut down the array and wait for two new drives to minimize potential data loss. The best laid plans *pulls out hair*


Thanks for the info. To be clear are you talking about forcing the assembly, or forcing a rebuild? 

I had tried to force the assembly, but the drives keep kicking out of the array during the rebuild process. The furthest I got was like 15% through... which isn't very close :(. 

I've been considering trying to use the assume-clean switch when assembling. from the man page

and of course I would hardly say i "really know what I am doing", but this sounds like it might get me mounted without requireing a resync, then I could try to pull off all the irreplacable data and start over. 

If anyone has a suggestion about assume-clean I'd be glad to hear it. 

For now I continue to check for badblocks, none found so far (seems good :) )

Yea, you might try the assume clean - I think it's really intended for when building a new volume without waiting for the sync, but it might work.  be careful.

---

### Post by Plecebo on 2010-08-20
Not sure exactly why, but after running badblocks on 5 out of 8 drives I decided to create the array again and see if it would sync. 

It did! All the way to 100%

Another problem remains however, there is no filesystem that I am able to mount on the array. 

I suspect it is because the geometry may have changed... but not 100% sure. 

I'll make another post with the new issue, hopefully someone can help me recover the data. 

Thanks for your help in this thread!

---

### Post by arrrghhh on 2010-08-20
Lesson learned I think - there is no replacement for a quality hardware RAID controller :D

---

### Post by MakOwner on 2010-08-20
> **arrrghhh said:**
> Lesson learned I think - there is no replacement for a quality hardware RAID controller :D

Or at least stable cheap hardware.  

I have cheap hardware raid (Think HighPoint) in one box, mdadm raid on eSata with port multipliers in two other boxes and had one box with two more-or-less standard PCI based 4 port SATA controllers.

The box with the two controllers was the most problematic.  
I have no proof, but all of my issues boiled down to time outs causing drives to fall out of the array - I think.  I abandoned that configuration. 

I have had drive failures in all of these at one point or another and although I can't say anything good about the performance on the HighPoint, swapping out the bad drive (and it really was - 4k bad sectors but no data loss! yay!) was really easy.

mdamd raid works, but I have to stumble through recovery every time.
Senility setting in I suppose.

---

### Post by Plecebo on 2010-08-20
> **arrrghhh said:**
> Lesson learned I think - there is no replacement for a quality hardware RAID controller :D

I don't know, I'm not really convinced I wouldn't have had the same trouble even with an $600+ 8 drive capable sataII hw raid controller card with battery backup, which is how much I would have had to spend to get the same functionality. [3Ware Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116043&cm_re=9650SE-_-16-116-043-_-Product") + [Backup Unit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116051&cm_re=9650SE-_-16-116-051-_-Product") 

My drives still would have overheated, or whatever happened to them, I still would have had trouble getting the array back online. 

Spending more money doesn't make me smarter. 

If anything the lesson learned is that I need to keep a backup of my data, even if I don't have space for a backup of all of it I need to keep a backup of the irreplaceable stuff at the least (photos of the birth of children/family events). The thousands of hours spent ripping my movie collection is cheap in comparison to loosing the photos/videos of my nieces first steps.

---

### Post by arrrghhh on 2010-08-20
> **Plecebo said:**
> My drives still would have overheated, or whatever happened to them, I still would have had trouble getting the array back online. 

Spending more money doesn't make me smarter. 

If anything the lesson learned is that I need to keep a backup of my data, even if I don't have space for a backup of all of it I need to keep a backup of the irreplaceable stuff at the least (photos of the birth of children/family events). The thousands of hours spent ripping my movie collection is cheap in comparison to loosing the photos/videos of my nieces first steps.

I completely agree with these statements.  You certainly may still have had the issue, but setting up RAID with a hardware controller is usually better (read - more stable) than doing software RAID.

Your point about backing up irreplaceable stuff will always apply tho.  You should have a backup of that stuff in several locations - my parents rotate USB keys between my mom's work and their house, on top of having an external HDD to backup to.  Just depends on how important that data is to you...

---

