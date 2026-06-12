---
title: "failed fsck after crash after upgrade to jaunty: serp"
date: 2009-05-26
forum: System76 Support
---

### Post by thinman1189 on 2009-05-26
Hi all. I've got a bit of a problem. I upgraded from 8.10 to 9.04 last night. Everything seemed fine until I came back from lunch and launched Amarok (already had firefox, pidgin, pdf viewer, and transmission running.) Amarok crashed X on its splash screen and while I had mouse no commands were working. I manually restarted and on reboot it failed fsck. I get a recovery prompt and the log entry in /var/log/fsck/checkfs of

> Log of fsck -CR3 -R -A -a
Tue May 26 15:05:47 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext3: A block group is missin an inode table while checking ext3 journal $
fsck died with exit status 8

Tue May 26 15:05:47 2009
----------------


Not really sure what to do but I need my laptop up and running asap, I have class work I need to get done. Thanks for the help.

---

### Post by whoop on 2009-05-26
Boot from a livecd and run partition editor, run a check on the partition in there...

---

### Post by thinman1189 on 2009-05-26
Okay I will. I found this thread but it's a bit old, anyone have thoughts more current? [http://ubuntuforums.org/showthread.php?t=606774](http://ubuntuforums.org/showthread.php?t=606774)

---

### Post by thomasaaron on 2009-05-26
This looks a whole lot like a bug with tracker (System > Prefs > Search and Indexing). If it is, it will soon hose your entire filesystem.

Do this...

```
sudo apt-get install tracker-utils
tracker-processes -r
```

...ASAP.

---

### Post by thinman1189 on 2009-05-26
Right now I have a livedvd in there checking itself for defects, was going to use the partition editor to scan it for problems but I guess that's not necessary. I'll run that when it's done checking. Before when it brought me into recovery, it had auto mounted the file systems. How do I unmount and install? It doesn't seem to see my internet, would that been included in a livedvd?

---

### Post by thinman1189 on 2009-05-26
Not sure of relevance but here is some weird behaviour I experienced before this happened. 

I was using a custom gtk theme that mimiced kde's oxygen. Last night it worked fine for the account it was enabled on, but when I switched users to another account that used default theme many of the system icons failed to start, and gnome systems manager failed to start when I went into System > Prefs> Appearance citing an already active kde manager. I disabled the theme and restarted. I could then get into Appearance but had to manually had launchers to the panel (volume, network, etc) because they still failed to show.

Also, vhba fails.

Oops, sorry for the double post. I'm used to bbs' that auto merge doubles.

---

### Post by thinman1189 on 2009-05-26
thomasaaron, it fails to fetch. apt-get update doesn't help. I guess it doesn't see my net. Trying to find the network init script. Thoughts? I'm just sitting in recovery term atm, and if my filesystem is that vulnerable I'd rather not dilly dally.

---

### Post by thinman1189 on 2009-05-26
thomasaaron, tracker is no longer part of ubuntu as of jaunty. What should I do?

---

### Post by thinman1189 on 2009-05-26
I can't login, it says my home directory does not exist.

---

### Post by thinman1189 on 2009-05-26
fsck.ext3 -f /dev/sda2 results in fsck.ext3: Superblock invalid, trying backup blocks... fsck.ext3: Bad magic number in super-block while trying to open /dev/sda2 The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>

It seems all is lost. How the hell could this happen? I have most of my music/movies type files backed up but so much for year+ of chat logs, bookmarks and customization.

---

### Post by thinman1189 on 2009-05-26
Issue resolved after using e2fsck. But I would really like to know what caused it. Even so, I may be moving away from Ubuntu to something more stable.

---

### Post by thinman1189 on 2009-05-26
smartctl output.

[http://paste.ubuntu.com/181613/](http://paste.ubuntu.com/181613/)

```
mike@ubuntu:~$ sudo smartctl -d ata -a /dev/sda
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
Local Time is:    Tue May 26 19:10:22 2009 EDT
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
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1151
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   077   060   030    Pre-fail  Always       -       52850634
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2463
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1155
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   049   045   045    Old_age   Always   In_the_past 51 (Lifetime Min/Max 51/53)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       670
193 Load_Cycle_Count        0x0022   008   008   000    Old_age   Always       -       185620
194 Temperature_Celsius     0x001a   051   055   000    Old_age   Always       -       51 (0 16 0 0)
195 Hardware_ECC_Recovered  0x0012   067   048   000    Old_age   Always       -       207965279
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

### Post by freeediver on 2009-05-26
Silly question maybe but could my corrupt superblock issues be fixed with an upgrade to 8.10, I am currently using 8.04? What is the latest?
Thanks

---

### Post by thomasaaron on 2009-05-27
It probably wouldn't be fixed by an *upgrade* to 8.10. Perhaps by a fresh install of 8.10. But it could just be the drive going bad.

---

### Post by thinman1189 on 2009-05-27
It's been iffy, with random things like add/remove not working and icons not showing. Now I can't even boot, I get grub terminal. What is going on?

---

### Post by thomasaaron on 2009-05-28
thinman,

I'm wondering if it is this tracker bug...

We have an ongoing forum post going on it. Please see...
[http://ubuntuforums.org/showthread.p...56#post7225556](http://ubuntuforums.org/showthread.p...56#post7225556)


Running these commands fixed it for one customer...
sudo apt-get install tracker-utils
tracker-processes -r

However, if you can't boot into Jaunty, it may be too late. Try running fsck from a live CD and then immediately booting into the OS and running the above commands.

---

### Post by thinman1189 on 2009-05-28
Ran it after the e2fsck and so far no problems. I'm out of town for the weekend so I'll do more checking when I get back. Thanks for the help :-)

---

### Post by thinman1189 on 2009-06-01
thomasaaron,

Got back today and everything seemed fine until /home became corrupted to the point that partition editor under a liveDVD couldn't even tell what filesystem it was. (I had been deleting files and downloading some personal files when I got errors saying there was no more space on the drive when there should have been around 30gb free. Lost around 4gb of recently added files in the crash.) I ran e2fsck from terminal and after a very long run 'fixed' it. Now I'm getting segfaults from firefox. I don't think this fix is going to last long...

---

### Post by jdb on 2009-06-01
> **thinman1189 said:**
> thomasaaron,

Got back today and everything seemed fine until /home became corrupted to the point that partition editor under a liveDVD couldn't even tell what filesystem it was. (I had been deleting files and downloading some personal files when I got errors saying there was no more space on the drive when there should have been around 30gb free.) I ran e2fsck from terminal and after a very long run 'fixed' it. Now I'm getting segfaults from firefox. I don't think this fix is going to last long...

Fsk can "fix" stuff, but won't keep more errors from occuring.
If there is disk corruption that can't be explained by something like a power failure, then it's time to replace the drive.

A seg fault is usually caused by a read or write to an address that shouldn't be accessed.
Badly written code can do that, but in your case it's more likely code that's been corrupted.
All it takes is one bit changed in an address.

jdb

---

### Post by thinman1189 on 2009-06-02
I guess the drive is dying. Every time I turn it on I lose more data.

---

### Post by phyzome on 2009-06-18
thinman1189: I had the same problems you did and none of the tracker stuff seems to be relevant. I had the drive replaced under warranty, and that didn't fix it either! I reinstalled Intrepid and the filesystem has been fine ever since.

---

### Post by thomasaaron on 2009-06-18
Could be this...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)

...bad SATA controller driver. According to the bug report, it is mostly present on certain machines in the -11 kernel. Try running the -9 kernel.

---

### Post by thinman1189 on 2009-06-30
Well everything seemed to be going just fine until a few days ago. [http://ubuntuforums.org/showthread.php?t=912417](http://ubuntuforums.org/showthread.php?t=912417) happened again. Then the symptoms in this thread started today. 

I had burned a new desktop iso for 9.04 and tried that. Should I try 8.10 again or 9.04 with a different kernel? 

It seems that this is directly related to data transfer. I had held off on adding most of my files to the system until I thought it was stable. Over the past week I added near 100gb of data back on, either by external or ssh, etc. That's when things started going wrong. 

After the crash tonight it tried to do e2fsck on start but it would hang to the point that I had to manually stop it. I'm going to use the cd to do the e2fsck and hopefully get off the bit of new data that's not backed up (unfortunately including the log files after the first crash).

Thanks again for the help.

EDIT:

Ok so when it auto e2fsck'd it right off the bat did some inode fixes, but because the check never finished I didn't get a log of it. I couldn't log in because it said the /home directory didn't exist. I just did it from a live cd and no errors were found, and I can now log in. The system has been rather sluggish this past week, and has only gotten worse since the e2fscks. I'll see if I can track down the original log files, no promises though.

---

### Post by jdb on 2009-06-30
> **thinman1189 said:**
> Well everything seemed to be going just fine until a few days ago. [http://ubuntuforums.org/showthread.php?t=912417](http://ubuntuforums.org/showthread.php?t=912417) happened again. Then the symptoms in this thread started today. 

I had burned a new desktop iso for 9.04 and tried that. Should I try 8.10 again or 9.04 with a different kernel? 

It seems that this is directly related to data transfer. I had held off on adding most of my files to the system until I thought it was stable. Over the past week I added near 100gb of data back on, either by external or ssh, etc. That's when things started going wrong. 

After the crash tonight it tried to do e2fsck on start but it would hang to the point that I had to manually stop it. I'm going to use the cd to do the e2fsck and hopefully get off the bit of new data that's not backed up (unfortunately including the log files after the first crash).

Thanks again for the help.

EDIT:

Ok so when it auto e2fsck'd it right off the bat did some inode fixes, but because the check never finished I didn't get a log of it. I couldn't log in because it said the /home directory didn't exist. I just did it from a live cd and no errors were found, and I can now log in. The system has been rather sluggish this past week, and has only gotten worse since the e2fscks. I'll see if I can track down the original log files, no promises though.

I lose track of what release uses what kernel, but you can find out what you're currently on with:

```
uname -r
```

It's kind of tricky changing kernels in Ubuntu, you're better off picking a release with the kernel you want.

jdb

---

### Post by thinman1189 on 2009-06-30
2.6.28-13-generic

---

### Post by jdb on 2009-06-30
> **thinman1189 said:**
> 2.6.28-13-generic

Anyone know if it was fixed in -13 ???
I haven't heard one way or the other.

You may have to go to something before -11.

I think I read that only 64 bit is affected, if that's true then going to 32 bit would let you stay on the current load.

jdb

---

### Post by thomasaaron on 2009-06-30
I've not been able to duplicate this one yet in the shop. However, based on email support requests I've received, I think it is still present in *-13.

---

### Post by thinman1189 on 2009-06-30
thomasaaron, try transferring 100-200gb of data over a day or so and see if that does it.

---

### Post by thomasaaron on 2009-06-30
Ok.

---

### Post by benjatodd on 2009-06-30
I had this same problem and wound up having to switch to the [[color=blue]2.6.29[/color]](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29) kernel in order to fix it.

I don't know if this helps, but the filesystem corruption started right after I upgraded my RAM from 2gb to 4gb.  I have a daru3 laptop running 64bit 9.04.

---

