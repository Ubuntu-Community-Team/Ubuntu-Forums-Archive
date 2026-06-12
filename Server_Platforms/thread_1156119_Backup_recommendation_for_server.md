---
title: "Backup recommendation for server"
date: 2009-05-11
forum: Server Platforms
---

### Post by matthewboh on 2009-05-11
I'm helping out the local Boys and Girls Club set up a server and they have a CDRW drive and I'm trying to find the simplest way to have them back it up.  I use Amanda at home and like it, but would consider something else for them - any suggestions?

---

### Post by Alekz_ on 2009-05-11
Never test, but still.. looks useful:
[http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line](http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line)

Using command line you'll be able to write a script and schedule in crontab!

[]'s

---

### Post by Larry Anderson on 2009-05-11
If its just one machine, a simple TAR back up to a removable HD is probably the best solution, you could make it a script or chron job to automate.

this thread is a great resource on making a 'recoverable' from scratch backup using TAR

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

My issues with CDRW with backup capacity, you will find out you run out of space real quick.  also with CD-Rs you will have a bunch of old backups to destroy, on rewritable you have the added time of erasing the disc before writing and recording speed.  External drives of good capacity are in the $100 range, if you format it ext2 or 3 you can store massive backup files in it too.

Hope that helps

---

### Post by Alekz_ on 2009-05-11
Agree with you Larry! That's the best solution (and cheaper)

But he asks for CD backup, so I give some information (even know if it works fine)

---

### Post by matthewboh on 2009-05-11
Problem is money - they have very few resources and the machine was donated by the local bank.  I suggested maybe S3 backup, but that could get out of hand very quickly since they 1.4 Mbps upload speeds and the server has 330 gb.  Any other suggestions graciously accepted!

---

### Post by Wiebelhaus on 2009-05-11
[Set up raid]("http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks") , seemless and no need for user intervention. You can just mirror the current installation and set up the raid , no worries until it fails.

---

### Post by wirelessmonkey on 2009-05-11
RAID is **_NOT_** a backup solution.

---

### Post by Wiebelhaus on 2009-05-11
> **wirelessmonkey said:**
> RAID is **_NOT_** a backup solution.

O h really , how's that?


> RAID 1 (mirrored settings/disks) duplicates data across every disk in the array, providing full redundancy. Two (or more) disks ***_each store exactly the same data, at the same time, and at all times. Data is not lost as long as one disk survives._*** Total capacity of the array equals the capacity of the smallest disk in the array. At any given instant, the contents of each disk in the array are identical to that of every other disk in the array.

The very definition of seamless back up is one that provides full redundancy.

---

### Post by ktrnka on 2009-05-11
> **sx66gns said:**
> O h really , how's that?




The very definition of seamless back up is one that provides full redundancy.

wirelessmonkey is right. Raid 1 is for redundancy not archival of information.

Just look what happened to journalspace.com

[http://hardware.slashdot.org/article.pl?sid=09/01/02/1546214]("http://hardware.slashdot.org/article.pl?sid=09/01/02/1546214")

I might suggest an external hard drive with an rsync script and cron.

---

### Post by orange-wedge on 2009-05-12
how large do you estimate the backups to be?

---

### Post by wirelessmonkey on 2009-05-13
> **sx66gns said:**
> O h really , how's that?
The very definition of seamless back up is one that provides full redundancy.

If you make a bad change to a RAID 1 disk, it applies to all disks in the RAID.  Where, oh where, is my good data ("backup") now?

---

### Post by centyx on 2009-05-13
CD/DVD backup for ~ 300GB of data really isn't practical.

I would grab a 1TB drive from Newegg or someone similar ( I see one for $75 US ) and throw it in an external USB drive enclosure. One of these for backup use only ( ie. passive cooling only ) can again be found for around $20 US. 

This way the server can backup to the drive each night and someone can even unplug it and take it home with them if they want so that it's kept offsite. This would be a good idea in case the office burns down or is burglarized.

You could also easily encrypt the drive with LUKS.

$100 really isn't much to protect your critical data.

EDIT: I meant to suggest also using rdiff-backup to run the backups. Benefits of rsync with reverse diffs, similar to putting a succession of daily incremental backups on tape via tar or dump.

---

### Post by matthewboh on 2009-05-13
For right now, the backups should be fairly small, but it does have a 750GB drive, so it's possible to get there.

They just have NO money - we're trying to weasel an additional server out of the local bank and use that for the backup server.  I know this isn't the best way, but it's the cheapest and the best that I can think of.

So, I'm going to set up Amanda with separate partitions and write CD images to the disk and show him when to at least get the full backups off to CDR's - any other really cheap ideas graciously accepted.

---

