---
title: "Entire system in read-only mode --can't login and I suspect virus..."
date: 2008-06-11
forum: Security
---

### Post by Gaming4JC on 2008-06-11
Hello,
First of all I have been running Ubuntu just fine for about 3 days no problems on this new installation of Hardy. However, just the day before yesterday and yesterday I got this error message on boot up:

"* the root file system is currently mounted in read-only mode"
"A maintenance shell will now be started"
Then is continues to fail all the way up to the fsck which I ran.

I was able to recover it, but then just yesterday it came back. I tried reseting all the file permissions via "chmod 777 /home/" and a few other commands I found on the forums. 

Please see the full messages below:
[[IMG]http://img136.imageshack.us/img136/1631/dscn1342ud5.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img55.imageshack.us/img55/4888/dscn1344wf4.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img55.imageshack.us/img55/7748/dscn1345sq8.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img55.imageshack.us/img55/322/dscn1346iv7.jpg[/IMG]](http://imageshack.us)

Now the system comes to the logo and makes a freezing halt.

I'd prefer not to have to reinstall to fix this, as I have dial-up the updates took forever.

On thinking back on the only to programs I installed before this happened was aMule and KVIrc. Do you suppose something was modded? I got it right from the package manager, but I've heard KAD network can be exploited. I have been running firestarter and AVG no problems before this and it said my system was clean..

Please if anyone knows anything post, I really would like to get my computer working again as now I lost everything until I can log back in. (I can read the drive via the livecd as I said though I'd prefer not to reinstall everything) :( HELP.

---

### Post by cdenley on 2008-06-11
That looks like a hardware problem, probably the hard drive. Maybe a bad sector. Try booting a livecd, then without mounting the disk, run
```

sudo cat /dev/sda>/dev/null

```
If you get any errors, it's almost definitely a hardware problem.

If you want fsck to fix problems without asking you to press "y", use the -y option.
```

fsck -y /dev/sda

```
fsck obviously can't fix hardware problems, though.

---

### Post by p_quarles on 2008-06-11
Well, since there are no known circulating viruses for Linux, and since this isn't the typical behavior of any virus for any system, and since this *is* the typical behavior for a dying hard drive, I'd say it's a dying hard drive.

---

### Post by /etc/init.d/ on 2008-06-12
It's amazingly clear from those messages that your hard drive is dying.  You don't have a virus.

---

### Post by Gaming4JC on 2008-06-12
Hello Again,
I would have said a hard drive crash too except for the fact I've had 3 of them and this Seagate 320GB I just purchased not more than 7 months ago so it's still under warranty. 

I talked with ASULutzy on the #ubuntu irc channel, he thought it was a hard drive failure as well. When I ran his version of fsck command it produced many errors. The interesting thing is that I have done a dozen hardware diagnostics tools and they say my hard drive is fine. At the moment I am running SeaTools full surface scan, so far no errors.

He also mentioned my hard drive temp had reached 190 degrees and that that was rather hot. My box has one fan on the side blowing in and one pushing out from the power supply in the back. As well as the typical CPU fan.

I also purchased two 1GB memory sticks DDR and a new power supply after I received some memory errors on my WinXP about 6 months ago.

To top all of this I had a nasty virus on my WinXP that may have caused some damages to hardware. Check it out here:
[http://forums.comodo.com/virusmalware_removal_assistance/svchostexe_and_email_exploit_troubles_closed-t23002.0.html](http://forums.comodo.com/virusmalware_removal_assistance/svchostexe_and_email_exploit_troubles_closed-t23002.0.html)
(When you have the time be sure to read over the whole thing, it was quite an experience.)
I noticed my CMOS is saying the overheat shutdown temperature is set to "Disabled" I think it should at least be the maximum preset, on top of this when I was running Windows my computer would occasionally restart itself. That was about a year ago, but I wonder if it is possible the virus could have of infected MBR and flashed my CMOS. I did a zero disk wipe before installing Ubuntu so hopefully it's out of MBR, but you never know...

I pressed Ctrl+Alt+F2 at the frozen boot screen on Ubuntu and it says "Kernel Panic init!" and won't let me get to a console...

As soon as SeaTools is finished I'll post the results and run that fsck command again but this time with your settings. Thanks for your help and let me know if you have any more comments/suggestions on this. 

I sure was enjoying Ubuntu before the whole thing came crashing down. :confused:

---

### Post by ASULutzy on 2008-06-12
heh, I don't know that I said 190 degrees. I don't remember the exact value that your smartmontools returned for temp, but it was hotter than I'd feel comfortable with.

Even if you manage to get this working again, you absolutely should buy a new hard drive because the current on you're using won't be lasting for all that much longer.

Also, you keep mentioning this virus, but there's really no feasible way that it could possibly do all these things. Like I said, no virus/piece of software/whatever, can actually tell your drive to error.

You need a new hard drive (:

---

### Post by Gaming4JC on 2008-06-12
I turned off the memory scan after 16hrs, it had reported no errors, and it should be fine says I just bought them not long ago.

SeaTools full surface scan of sectors passed. It says the hard drive is fine...


sudo cat is running now. I never mounted the drive, but do I need a command to unmount it in live cd? I'm unsure if it's mounted by default or not.

---

### Post by p_quarles on 2008-06-12
> **Gaming4JC said:**
> I turned off the memory scan after 16hrs, it had reported no errors, and it should be fine says I just bought them not long ago..
Are you talking about memtest? That has nothing to do with your hard drive -- it only "tests" "memory" (as the name implies ;) )

---

### Post by Gaming4JC on 2008-06-12
Yes. I ran memtest last night just to make sure memory was fine too.

I ran SeaTools though too (the hard drive diagnostic utility from the official vendor.)

Edit: That sudo cat command seems to be doing nothing. It's just sitting there after I typed it with a |. Shouldn't it say it is running or is it normal?

---

### Post by Gaming4JC on 2008-06-12
Ummm... what now?

```

ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 164090/19161088 files, 1913755/76622009 blocks
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 164090/19161088 files, 1913755/76622009 blocks
ubuntu@ubuntu:~$  sudo fsck -y /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 164090/19161088 files, 1913755/76622009 blocks
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ umount /dev/sda
umount: /dev/sda is not mounted (according to mtab)

```

LOL, now it says it's fine. unless I'm reading something wrong here. :confused:

---

### Post by todb on 2008-06-12
> **Gaming4JC said:**
> That sudo cat command seems to be doing nothing.

This is normal; the command is reading your drive device and writing it to the null device (ie, nowhere).

It should take a while, and report nothing until it's done.

As an aside, this being the security forum, I would advise you to avoid running any "sudo" command without first understanding exactly what it does. Otherwise, you open yourself to mischief makers.

(And really, this applies to all commands ; plenty of damage can be done without sudo).

---

### Post by cdenley on 2008-06-12
> **Gaming4JC said:**
> Ummm... what now?

```

ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 164090/19161088 files, 1913755/76622009 blocks
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 164090/19161088 files, 1913755/76622009 blocks
ubuntu@ubuntu:~$  sudo fsck -y /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 164090/19161088 files, 1913755/76622009 blocks
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ umount /dev/sda
umount: /dev/sda is not mounted (according to mtab)

```

LOL, now it says it's fine. unless I'm reading something wrong here. :confused:

It looks like you probably have a partition on /dev/sda mounted, such as /dev/sda1.
```

mount|grep /dev/sda

```
You may have corrected your filesystem errors, but that doesn't mean you don't still have a hardware problem. I've seen a bad IDE cable cause problems like that before. I wouldn't be surprised if you experience more errors soon.

todb was right about the "sudo cat" command. If you're ever curious about what a command does, use the "man" command.
```

man man
man sudo
man cat
man null

```

---

### Post by /etc/init.d/ on 2008-06-13
Run **smartctl -a /dev/sda** and post the output here.  This will read the drive's SMART data, and it will tell us if the drive is obviously having hardware problems.

There is no point running file system checking tools until you are confident that the drive is okay physically.  By trying to repair the file system on a potentially bad drive, you might only make the problem worse.

---

### Post by Gaming4JC on 2008-06-13
Yes, I think I ran this code once before. Anyhow, here it is again. Let me know if you see anything. :)
```

ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3320620SV
Serial Number:    9QF5LNBQ
Firmware Version: 3.ACH
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Jun 13 16:45:26 2008 UTC
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
data collection: 		 ( 430) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 115) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   100   006    Pre-fail  Always       -       71825124
  3 Spin_Up_Time            0x0003   094   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       351
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       60496799
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2148
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       351
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   066   054   045    Old_age   Always       -       572063778
194 Temperature_Celsius     0x0022   034   046   000    Old_age   Always       -       34 (Lifetime Min/Max 0/15)
195 Hardware_ECC_Recovered  0x001a   072   058   000    Old_age   Always       -       79649612
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   199   000    Old_age   Always       -       593
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 41 (device log contains only the most recent five errors)
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

Error 41 occurred at disk power-on lifetime: 1527 hours (63 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 4e 90 7e e0  Error: ICRC, ABRT at LBA = 0x007e904e = 8294478

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 10 3f 90 7e e0 00      00:22:29.217  READ DMA EXT
  25 03 01 00 00 00 e0 00      00:22:29.181  READ DMA EXT
  ef 03 42 4e 10 00 a0 00      00:22:29.181  SET FEATURES [Set transfer mode]
  ef 03 0c 4e 10 00 a0 00      00:22:29.180  SET FEATURES [Set transfer mode]
  c6 00 10 4e 90 7e a0 00      00:22:31.611  SET MULTIPLE MODE

Error 40 occurred at disk power-on lifetime: 1527 hours (63 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 4e 90 7e e0  Error: ICRC, ABRT at LBA = 0x007e904e = 8294478

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 10 3f 90 7e e0 00      00:22:29.217  READ DMA EXT
  25 00 10 3f 90 7e e0 00      00:22:29.181  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:29.181  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:29.180  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:28.892  READ DMA EXT

Error 39 occurred at disk power-on lifetime: 1527 hours (63 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 4e 90 7e e0  Error: ICRC, ABRT at LBA = 0x007e904e = 8294478

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 10 3f 90 7e e0 00      00:22:29.217  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:29.181  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:29.181  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:29.180  READ DMA EXT
  25 00 10 3f 90 7e e0 00      00:22:28.892  READ DMA EXT

Error 38 occurred at disk power-on lifetime: 1527 hours (63 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 4e 90 7e e0  Error: ICRC, ABRT at LBA = 0x007e904e = 8294478

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 10 3f 90 7e e0 00      00:22:29.217  READ DMA EXT
  35 00 08 2f 00 5e e0 00      00:22:29.181  WRITE DMA EXT
  35 00 08 47 00 5e e0 00      00:22:29.181  WRITE DMA EXT
  35 00 48 87 02 5e e0 00      00:22:29.180  WRITE DMA EXT
  25 00 08 f7 62 4b e0 00      00:22:28.892  READ DMA EXT

Error 37 occurred at disk power-on lifetime: 1527 hours (63 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 4e 90 7e e0  Error: ICRC, ABRT at LBA = 0x007e904e = 8294478

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 10 3f 90 7e e0 00      00:22:27.962  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:27.941  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:27.940  READ DMA EXT
  25 00 01 00 00 00 e0 00      00:22:27.940  READ DMA EXT
  25 00 08 f7 62 4b e0 00      00:22:27.940  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2137         -
# 2  Short offline       Completed without error       00%      2137         -

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

One minor problem, unless I can prove the hard drive is bad I doubt they will let me return it. And the official SeaTools program that the hard drive comes with said it was fine lol. :P

---

### Post by timcredible on 2008-06-13
are you using ext2 on this drive?  can i ask why you're not using ext3?

also, do you have more than 1 device on the bus?  you said it's a new drive, so i'm wondering if you have 2 devices both set as master on the bus.  or 2 devices both set to slave.

---

### Post by Gaming4JC on 2008-06-13
I believe it is ext2, yes. I installed Ubuntu with default settings so it did automatic partioning... is something wrong with this? :(

If you mean is anything on the same IDE cable, no. My hardrive is a SATA-II, so it has it's own cable.

However, I do have 2 CDR,DVDR, combo drives, and 1 floppy drive.

You think somehow the system might think that one my CDR, DVD, combo drives is master making my HardDrive conflict? :confused:

---

### Post by Gaming4JC on 2008-06-14
Ok I checked both of my IDE CD and DVD Rom drives. The one on top is set to master the one on bottom is set to slave. This should be fine?

My SATA-II has no jumper settings anywhere I can see on it for master or slave.  sooo....

I checked all the wiring to make sure it was nice and snug, and put the case back together.

Then I did another zero disk wipe (to remove grub boot loader), and tried reinstalling Ubuntu. I made sure this time it was ext3.
But now it just gives this message at my BIOS:
```

Boot first hard drive:
-

```

The - blinks. But it just stays there locked up.

I tried installing SlackWare and the same problem occurred. It's not a disk boot failure, but it just stay frozen for some strange reason.

I am having the SATA drive exchanged for a new one, we'll see if this doesn't fix some of my problems...

But if the problem were to persist after this new drive? :confused:

I also pulled the memory and the Motherboard battery for the time being. I've heard advanced viruses can remain in memory for up to two hours, so just to be safe.

If allll else fails, or if I'm daring enough. I my try to flash my bios. It's a bit out dated anyhow and I have my manual with all the information on how to do it...

---

### Post by Gaming4JC on 2008-06-15
Ok I flashed my BIOS successfully, and replaced my hard drive.
Now there's a new problem. Everytime I plug in this new SATA drive my BIOS freezes at "Verifying DMI Pool Data...". I checked my BIOS. It is recognized as a hard drive but refuses to get past the DMI check.

My Drive is a Seagate Barracuda 72000.11 320GB. It came with new cables but no software. Here's the spec:
[http://www.seagate.com/ww/v/index.jsp?vgnextoid=e7c048e03b758110VgnVCM100000f5ee0a0aRCRD&vgnextchannel=f424072516d8c010VgnVCM100000dd04090aRCRD&locale=en-US&reqPage=Support](http://www.seagate.com/ww/v/index.jsp?vgnextoid=e7c048e03b758110VgnVCM100000f5ee0a0aRCRD&vgnextchannel=f424072516d8c010VgnVCM100000dd04090aRCRD&locale=en-US&reqPage=Support)

My Mother board is a ABIT NF8-V2. All the specs are over here:
[http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=2&model=292](http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=2&model=292)

Please HELP! :(

---

