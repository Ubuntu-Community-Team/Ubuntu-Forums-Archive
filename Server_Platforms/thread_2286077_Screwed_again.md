---
title: "Screwed again?"
date: 2015-07-09
forum: Server Platforms
---

### Post by MakOwner on 2015-07-09
EXT4 file system on a RAID6 array in good health.
I dismount, run fsck, clean the file system, remount and try to write another file and get the same error and journal abort.

This is 16 2 TB volumes in RAID6  -- Am I just screwed by the volume size?


[  462.680976] EXT4-fs error (device md8): ext4_mb_generate_buddy:739: group 30561, 15353 clusters in bitmap, 0 in gd
[  462.695835] Aborting journal on device md8-8.
[  462.751010] EXT4-fs (md8): Remounting filesystem read-only
[  462.791520] EXT4-fs error (device md8): ext4_mb_generate_buddy:739: group 30592, 30643 clusters in bitmap, 30688 in gd
[  482.558216] EXT4-fs error (device md8): ext4_mb_generate_buddy:739: group 60017, 5964 clusters in bitmap, 0 in gd
[  482.575483] EXT4-fs (md8): ext4_da_writepages: jbd2_start: 26085 pages, ino 382667302; err -30
[  482.582957] EXT4-fs (md8): ext4_da_writepages: jbd2_start: 9223372036854775807 pages, ino 382666770; err -30



Must be -- finally got the file system clean and ureadahead is crapping itself.  

This is at 3.2.0-87 - anyone else running into this?

---

### Post by tgalati4 on 2015-07-09
I would check your power supply.  If you have one drive that can't keep its speed, you will get IO Waits.  Run *top* in a terminal and look at the WAIT (wa) statistic.  If it is high (perhaps greater than 5%), then I would look at the health of each drive (SMART parameters) and check the voltages of your PSU.

I would research Error -30 with respect to the journal.  Was *fsck* not able to read it correctly or not able apply the journal due to some other problem?

As far as size, Red Hat recommends XFS when you get over 100 TB, but a 25 TB RAID6 pool should be doable.

---

### Post by MakOwner on 2015-07-10
> **tgalati4 said:**
> I would check your power supply.  If you have one drive that can't keep its speed, you will get IO Waits.  Run *top* in a terminal and look at the WAIT (wa) statistic.  If it is high (perhaps greater than 5%), then I would look at the health of each drive (SMART parameters) and check the voltages of your PSU.

Months of run time with no issues so far, the array enclosure and the server itself are on a UPS.  Might be the power supply - anything is possible - but I doubt it at. In any event, what exactly would I check about the power supply?
No sparks or unusual power consumption or excessive heat.

Smartd monitors with alerts 24x7 and I have some custom scripts that check smart parameters and drive temps every 30 minutes with alerts if certain parameters change - such as temps getting over 100F. 
Sample of the stats I collect on each drive - dunno how this table is going to look here, but maybe you can figure it out.
```

Drive/Serial 	Collect Date 	Collect Time 	Temperature F 	Pending Sectors 	Reallocated Sectors 	Uncorrected Sectors 	Offline Sectors 	Cmd Timeout 	Array Member 	SMART Health 	Start Stop#
/dev/sdo 	  	  	Warn F: 100 	  	  	  	  	  	  	  	 
JK1130YAHPJW1T 	2015-07-10 	04:30:17 	96 	0 	0 	0 	0 	0 	md8 	PASSED 	90
JK1130YAHPJW1T 	2015-07-10 	05:00:17 	96 	0 	0 	0 	0 	0 	md8 	PASSED 	90
JK1130YAHPJW1T 	2015-07-10 	05:30:18 	96 	0 	0 	0 	0 	0 	md8 	PASSED 	90
JK1130YAHPJW1T 	2015-07-10 	06:00:20 	95 	0 	0 	0 	0 	0 	md8 	PASSED 	90

```

> 
I would research Error -30 with respect to the journal.  Was *fsck* not able to read it correctly or not able apply the journal due to some other problem?

I can't find anything related to the Error -30, but my google ability is somewhat limited.

I run fsck, clean up the journal 

```

fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
md8: recovering journal
md8 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'test.txt' in /TestDir (382664705) has deleted/unused inode 382667302.  Clear? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +(1290924645--1291255807) +(1291268096--1291290623) -(1291319013--1291319295) +(1305289454--1305313279) +(1305697888--1305706495) +(1827709744--1827710911) +(1827732960--1827733119) +(1827733140--1827733143) +(1827733152--1827733483) +(1827733488--1827733499)
Fix? yes


md8: ***** FILE SYSTEM WAS MODIFIED *****
md8: 95832/427302912 files (4.5% non-contiguous), 5263667863/6836836608 blocks

```

remount the filesystem and everything looks good.  
fsck *REALLY* will only fix this on a reboot.  Dismounting the filesystem and running fsck results in output that _says_ the filesystem is clean, but if you look in dmesg you see a line that says:

```

ext4_put_super:819: Couldn't clean up the journal

```

During reboot fsck you see a mesage about a fix for the bad inode.
After a clean filesystem is mounted, I try to sftp a file onto it, and the process starts all over again.
The ureadahead segfault seems to be NFS related, as NFSD started immediately prior to that.
I'm not using NFS to write to the filesystem anyway and I have stopped the NFS daemon during the attempted writes anyway.

```

[  873.607095] ureadahead[517]: segfault at 7f2372a2af48 ip 00007f237296bb46 sp 00007ffee1dac260 error 6 in ureadahead[7f2372966000+a000]
[  881.620031] init: ureadahead main process (517) killed by SEGV signal
[  934.733295] init: tty1 main process ended, respawning
[41123.018272] EXT4-fs error (device md8): ext4_lookup:1047: inode #382664705: comm sftp-server: deleted inode referenced: 382667302
[41123.018642] Aborting journal on device md8-8.
[41123.041510] EXT4-fs (md8): Remounting filesystem read-only
[41144.251281] EXT4-fs error (device md8): ext4_lookup:1047: inode #382664705: comm sftp-server: deleted inode referenced: 382667302

```

> As far as size, Red Hat recommends XFS when you get over 100 TB, but a 25 TB RAID6 pool should be doable.

This happens at the 20TB boundary of a 26TB volume.


I have run out of google options, on a reboot the filesystem comes back clean, and I can read the remainder of the content with no issue, but any writes to the volume trigger this behavior.
I'm at a loss.

Perhaps the journal is out of space and it isn't a file system issue?
I'm looking for ext4 journal resize and rebuild information.


Just found this -- I may be hitting a kernel bug?  [LINK]http://superuser.com/questions/472835/ext4-fs-error-device-loop0-ext4-mb-generate-buddy#516447[/LINK]

I should stop editing my own post and start replying to myself.  

I removed the journal, fsck'd the file system and rebuilt the journal, forced another fsck on next reboot and rebooted.
Nice clean, file system mounted read write with a clean boot.

I copied one file from another local file system onto the filesystem in another location that the original problem directory structure.
Filesystem promptly **** itself again - I used midnight commander to copy the file.

```

Jul 10 08:24:49 PE850-05 kernel: [ 1951.428230] EXT4-fs error (device md8): ext4_lookup:1047: inode #382664705: comm mc: deleted inode referenced: 382667302
Jul 10 08:24:49 PE850-05 kernel: [ 1951.428591] Aborting journal on device md8-8.
Jul 10 08:24:49 PE850-05 kernel: [ 1951.453078] EXT4-fs (md8): Remounting filesystem read-only

```


Does anyone have any idea how to fix this???

---

### Post by tgalati4 on 2015-07-10
OK, so you have a 26 TB RAID6 pool with 20 TB used and you are having problems with the pool going RO--due to a variety of errors.  Some errors are journal-related, some are ureadahead, some are simply inode reference during a delete.  First, I would make a backup, since strange things are happening.  If you have problems copying existing data from the pool to another media, then that would be revealing.

Check the spin-up times of each drive.  Slow spin up times can indicate worn bearings.  Clean the hardware with compressed air and reseat all of the cabling.  Check the wait times (wa) with *top* when copying files from the pool.  IO Waits can be indicative of a power or cable connection problem that is intermittent but recoverable and not always generate log entires.

SMART only captures ~2/3 of drive failure modes, so things like AC ripple noise in your power supply can cause drive problems that SMART doesn't capture.

The kernel bug you reference was from a 2.6.X to 3.0.X kernel change and appeared to involve a single, problematic disk drive.  It's possible that there is a timing issue with a RAID6 pool writing data to the full pool and updating the journal such that the file system synchronization fails.  You would have to remove a lot of data, fill the pool again to the 20 TB mark and see if the problems reappear.  If you get consistent behavior, then go ahead and file a bug against the kernel version that you are running.  Unfortunately, running such tests can put the entire pool at risk, so make sure you have backups.

---

### Post by gordintoronto on 2015-07-11
"This is at 3.2.0-87" Is that your kernel version? A lot has changed since that was current.

---

### Post by MakOwner on 2015-07-12
> **tgalati4 said:**
> OK, so you have a 26 TB RAID6 pool with 20 TB used and you are having problems with the pool going RO--due to a variety of errors.  Some errors are journal-related, some are ureadahead, some are simply inode reference during a delete.  First, I would make a backup, since strange things are happening.  If you have problems copying existing data from the pool to another media, then that would be revealing.

ureadahead error seems to be related to a mac client that mounts the space with a read only NFS export.
Shutting that client (or NFS server altogether) removes the ureadahead issue.  Or seems to at this point.

> 
Check the spin-up times of each drive.  Slow spin up times can indicate worn bearings.  Clean the hardware with compressed air and reseat all of the cabling.  Check the wait times (wa) with *top* when copying files from the pool.  IO Waits can be indicative of a power or cable connection problem that is intermittent but recoverable and not always generate log entires.

[SMART only captures ~2/3 of drive failure modes, so things like AC ripple noise in your power supply can cause drive problems that SMART doesn't capture.


This is what is really bothering me -- the first entry of any sort in any of the logs - dmesg, kern, syslog - is the file system error, then the remount read only.  I would expect *something* in the logs about the mdadm array.  No other indications of individual drive issues, or enclosure backplane issues at all.
One place that I haven't looked that I would need debug mode for is the LSI driver that handles the external enclosure.

> 
The kernel bug you reference was from a 2.6.X to 3.0.X kernel change and appeared to involve a single, problematic disk drive.  It's possible that there is a timing issue with a RAID6 pool writing data to the full pool and updating the journal such that the file system synchronization fails.  You would have to remove a lot of data, fill the pool again to the 20 TB mark and see if the problems reappear.  If you get consistent behavior, then go ahead and file a bug against the kernel version that you are running.  Unfortunately, running such tests can put the entire pool at risk, so make sure you have backups.

I have backups, and in answer to one of your above questions, I can copy the data off with no issues so far.  I was able to do an rsync copy of data added since the last backup without any issue at least.
I have even tried deleting a 1.4 GB file from the filesystem and copying it back.  That worked with no issue.

---

### Post by MakOwner on 2015-07-12
> **gordintoronto said:**
> "This is at 3.2.0-87" Is that your kernel version? A lot has changed since that was current.

Ugh, yea it is a bit old, but it's 12.04.5 LTS which is supported until 2017.
I do need to upgrade it, but not in the middle of this.

---

### Post by MakOwner on 2015-07-12
> **tgalati4 said:**
> I would check your power supply.  If you have one drive that can't keep its speed, you will get IO Waits.  Run *top* in a terminal and look at the WAIT (wa) statistic.  If it is high (perhaps greater than 5%), then I would look at the health of each drive (SMART parameters) and check the voltages of your PSU. 

PSU swapped with a healthy one.  

Running fsck I do see some times where IO Wait is higher than 50%, where as most of the time it's 5% or less.
During group summary information section of the fsck, wa was higher than 80%, and CPU drop off to less than 1%.
I can't find anything in any logs that might indicate which drive might be causing the issue.  

Smart parameters, right down to command timeouts are clean -- all still reporting 0.

Anyone having any hints on what to put into debug mode to cause sufficient logs to identify this?

Using a SAS1068E PCI-Express Fusion-MPT SAS controller for the enclosure and the mptsas module is loaded.

---

### Post by MakOwner on 2015-07-12
Speaking of potential drive issues with this array, this array is the cleanest set of drives I have - not a single reallocated sector in the lot, knock on wood.
I did find one drive with a "multi-zone error rate" with a value of 1.

I'm going to replace that drive with a standby I have and if that's not the bad drive, maybe the array fix will flush the bad one out.

---

### Post by MakOwner on 2015-07-14
After many hours of trial and error, I have identified a port on the backplane in the enclosure that appears to be failing.
I would humbly submit that the default logging options with the various drivers involved was somehow masking errors that would have helped identify this.
A week of trial and error seems a bit excessive when _some_ type of error logged _somewhere_ might have helped narrow this down.

Part of that is on me, as I don't know how to manipulate the error logging level of some (ok, most) of the modules loaded.  
On the other hand, something as catastrophic as this should have been filling syslog with errors.

Summary -- port failing on 16 bay external SAS enclosure, presumably causing I/O delays long enough to cause writes to force the mdadm volume to corrupt the write and re-mount RO.
No errors were _ever_ logged in syslog, dmesg, or anything else in /var/log.

I identified what I think is the problem port by failing a drive I had suspicions about, rebuilding the array and the rebuild time to continued to increase as the rebuild time ran.
It never failed and never threw any errors.  It just continued to slow down.

I replaced that drive and tried rebuilding the array in the same enclosure, and had the same issue.

I moved all of the disks to a different (identical model) enclosure and it's rebuilding now at 15536K/sec.

Any tips on increasing the logging level in whatever module, and any ideas as to why mdam wouldn't start screaming during the rebuild and failed I/O that caused the volume to remount RO would be really appreciated.

---

### Post by tgalati4 on 2015-07-15
My experience is that Linux expects perfect hardware, so most errors that are logged are strictly repeatable, software errors.  I suspected IO Wait (wa) in *top* because I encountered that on a Dapper Drake system with 6 years of uptime.  One drive's power connector had vibrated loose and the drive was cutting in and out--no log messages, just IO Waits.  After cleaning and reseating, everything was back to normal.

SATA controllers fail, cable connections fail, PSU's fail, but these failures won't trigger helpful log messages.  They will trigger error messages that cause you to chase every other possible cause.  My intuition when I see multiple, related errors is to assume that perfect hardware is no longer perfect.  Now I go through a verification and validation process for each piece of hardware in the system.  Sometimes that means reducing the system to a minimum state--pull out RAM, hard disks, all cards and just stress test the motherboard and CPU using a LiveUSB.  If it passes, then add something back in, like more RAM, or a hard disk.

I can't help you with increasing logging levels.  The documentation will tell you if debug levels are available, but understand that even high debug levels can't accurately detect intermittent hardware problems.  I would share your experience with the hardware manufacturer.  They may have a interest in their hardware's behavior.

Thanks for sharing your debug steps in this situation.

---

### Post by MakOwner on 2015-07-16
> **tgalati4 said:**
> My experience is that Linux expects perfect hardware, so most errors that are logged are strictly repeatable, software errors.  I suspected IO Wait (wa) in *top* because I encountered that on a Dapper Drake system with 6 years of uptime.  One drive's power connector had vibrated loose and the drive was cutting in and out--no log messages, just IO Waits.  After cleaning and reseating, everything was back to normal.

SATA controllers fail, cable connections fail, PSU's fail, but these failures won't trigger helpful log messages.  They will trigger error messages that cause you to chase every other possible cause.  My intuition when I see multiple, related errors is to assume that perfect hardware is no longer perfect.  Now I go through a verification and validation process for each piece of hardware in the system.  Sometimes that means reducing the system to a minimum state--pull out RAM, hard disks, all cards and just stress test the motherboard and CPU using a LiveUSB.  If it passes, then add something back in, like more RAM, or a hard disk.

I can't help you with increasing logging levels.  The documentation will tell you if debug levels are available, but understand that even high debug levels can't accurately detect intermittent hardware problems.  I would share your experience with the hardware manufacturer.  They may have a interest in their hardware's behavior.

Thanks for sharing your debug steps in this situation.

This is what I have done so far:

And keep in mind this is all SAS from controller right up to the drive.  

To identify the bad part, which at this point appears to the drive to backplane connection of one of the hard drives, I worked off a hunch.
I compared all the drive firmwares and started with the odd one out, just as a random "eliminate difference first" method.
Three drives were different and I selected the oldest of those three, with the hopes it was the drive causing the issue.

I failed it out of the array and replaced it with a drive I had in cold standby.
As soon as the rebuild started, SMART indicated the new drive was failing and reallocated sectors and command timeouts ramped into the thousands.

I moved all the drives into a cold standby enclosure, and restarted the rebuild with another drive to replace the one with the SMART failure indicator.

That rebuild in the new (not new, just different) enclosure just completed.

I ran fsck across the filesystem and it fixed a bad inode.  I updated the mount count so that fsck would be forced on reboot, updated the fstab so that it would mount on reboot and rebooted.

Right after reboot, I ran ls -al across the filesystem and it **** itself again and remounted read only.

I don't know if this is a linux issue with the EXT4 filesystem, or something specific to the Ubuntu server build. but I'm operating on blind luck because the OS isn't providing any logging of any sort of usefulness.
This is what happens: 

Dismount the filesystem, run fsck, and it cleans up, removing inode 382667302

```

# fsck -f /dev/md8
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
md8: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'test.txt' in /Downloads (382664705) has deleted/unused inode 382667302.  Clear<y>? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

md8: ***** FILE SYSTEM WAS MODIFIED *****
md8: 95833/427302912 files (4.5% non-contiguous), 5263667863/6836836608 blocks

```

Remount the file system, run 'ls -al' on the file system where the test.tx file was removed by fsck and start the process all over again.

```

[ 1034.566823] EXT4-fs error (device md8): ext4_lookup:1047: inode #382664705: comm ls: deleted inode referenced: 382667302
[ 1034.567184] Aborting journal on device md8-8.
[ 1034.623688] EXT4-fs (md8): Remounting filesystem read-only

```

Same with a clean up and reboot that forces a fsck.
Voila.  Right back where I started, this time without any hardware errors.  Curious that the exact same inode has miraculously been revived from the dead.
Groundhog day ...


So, to sum it up, the only real troubleshooting so far has been gut hunches and lack of any sort of real logging to identify issues or direction.

---

### Post by tgalati4 on 2015-07-16
I believe there is a way to block certain inodes from being used.  It would be a work-around, without knowing the exact reason for the failure.  It could be a memory controller issue, a front-side-bus timing issue, a RAM issue, who knows?

Sometimes vibration can cause connection issues.  Does your drive enclosure have all of the rubber bumpers intact?  All it takes is one broken tab so that the drive doesn't seat firmly.  I would inspect the latching mechanism and the contact pins.

---

### Post by MakOwner on 2015-07-20
Operating off hunches and guess work I have come up with this, and so far (knock on wood) has held up over changing back to the original enclosure which I thought to have a bad backplane port.

The drive in the slot I thought to be bad was a Western Digital drive, and I had a spare Western Digital RE4-GP that I had still sealed in anti-static as an RMA replacement from another failed WD drive.
That replacement drive when placed in the slot immediately started racking up sector re-allocations and command timeouts.  
I put all of the drives in another enclosure, used a Hitachi drive as a replacements and placed them both of the WDs in an eSATA enclosure for testing to validate that the enclosure was the source of the issue.
The new enclosure rebuilt the array and things were looking good.

The original WD passed all SMART tests and sustained writes, but had the the one zone transfer error in the SMART data.
The drive received as an RMA replacement from WD continued to rack reallocated sectors under any writes at all.

(Keep in mind all of these are WD "Enterprise" class disks...)
I have RMAd the disks and moved the original array back to the original enclosure.

Lessons learned:  
[LIST]
[*]Don't trust WD.  Even "Enterprise" class disks appear to be dodgy.  Commence disk manufacturer flame war. (OK, to be completely fair maybe they just stick whatever random disk is about for an RMA.  Maybe someone will start seeing 6TB replacements for 2TB disks.)
[*]Learn to figure out how to ramp up logging (Don't get me started about the latest logging changes in Ubuntu...)
[/LIST]

I still have some dodgy stuff going on with the RAID array during boot --  After stabilizing the array, I upgraded to Ubuntu 14.04 LTS - figured I may as well catch that server up.
BOOT_DEGRADED no longer works for MD devices other than 0 and 1.  Rather than boot the MD8 array degraded, the boot continues and leaves all the disks that were in that array marked as spares, and that MD device not started.
Under 12.04 a reboot would have brought the array up degraded and the file system would have then mounted.
Under 14.04, you pause at boot because the mount point is not available and the boot process is waiting for the M or S key to be pressed.  [sarcasm]That's an improvement![/sarcasm]


TL;DR; 
Don't use WD disks. 
       *Also to be fair, when I spoke to WD support about it they immediately offered to let me pay postage for the return and seemed completely unsurprised I had received such a disk as an RMA.
It would be super useful for some human readable debug-logging instructions that an idiot like me could understand.
Random boot weirdness with Ubuntu 14.04 and mdadm volume assembly.

---

### Post by tgalati4 on 2015-07-21
RMA disks that you get are typically RMA'd from someone else and they go through a cursory test.  If they pass, they put them in the mail.  It's possible that their diagnostics do not include putting such drives in a RAID6 array with an Ubuntu OS.  

Debug logs make perfect sense to those who wrote them into the code.  For the rest of us, they are simply suggestions.

---

