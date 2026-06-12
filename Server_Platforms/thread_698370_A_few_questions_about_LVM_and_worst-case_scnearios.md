---
title: "A few questions about LVM and worst-case scnearios"
date: 2008-02-16
forum: Server Platforms
---

### Post by Cadmus on 2008-02-16
Ok, I'm interested in using LVM for a home media centre, possibly using mythTV as a front-end.

My questions are about worst-case scenarios with LVM and how easy is it to recover from them. I've read a lot of the HowTos and recipes, but they don't go into what happens if it cocks up

Assume I have two partitions making up an LVM used only for media files, sdb1 and sdc1, the ensuing LVM is formatted with something good for big files like XFS.

Now, what do I do if disaster strikes and sdb suffers a cricitical hardware fault, what happens to the LVM? What happens to files who had no parts of themselves on sdb1? Are they recoverable? What happens to XFS when half of it disappears?

I know for a media centre this is overkill, but LVM also interests me for a production server and if I can answer these questions it's one step closer to an Ubuntu server where before there was Windows.

---

### Post by Cadmus on 2008-02-28
Just seeing if anyone else has got any answers on this one. I'm trying to get a production server ready for this and I need to satisfy myself and my superiors that a failure of one machine won't take the entire array with it.

---

### Post by Cato2 on 2008-02-28
Here are some notes I made when researching LVM2 (current Linux version) - generally I would avoid LVM snapshots as they have been flaky for other people, and I'm also sceptical about RAID generally (1 or 5) in the absence of the NetApp/ZFS style media scrubbing and checksumming.

Sorry about the formatting, this is in TWiki format which is how I keep my notes on Ubuntu  - it's very easy to install though :)

SystemRescueCD is an excellent recovery disk that has LVM support - Knoppix also supports this but is larger and less recovery oriented.  Burn a copy of both and practice using them.

The only real solution is to have really good backups ideally offsite, of the entire system, and to include in these backups the partition data (output of sfdisk) *and* the LVM metadata (output of vgcfgbackup) and to maintain good recovery procedures.  Really you should test a bare metal recovery of the whole system.

Recovering LVM when some disks have gone could be harder - I would tend to keep each VG within one physical disk, which reduces flexibility a bit but also reduces impact of a complete disk failure.

Also run SMART, with the options to do a full test on whole HD periodically (helps to flush out failling sectors that would otherwise be found only on recovery).

Some other tips:

- read up on the LVM 'extend FS size online' and preferably extend offline - I had an ext3 FS get very corrupted as a result of this and I'm not sure why.

-  Linux software RAID has a problem in that the first bad sector while in reconstruct mode causes the whole array to be lost - and this is very common: [[[http://www.nber.org/sys-admin/linux-nas-raid.html](http://www.nber.org/sys-admin/linux-nas-raid.html) Linux RAID experiences]] (this is a **very, very good article**  - net result is that your chance of 2 disks failing 'at same time' is far higher than it should be, rendering RAID far less useful.  Hence backups are really critical.

Hope this helps

---+++ LVM resources

[[[http://sourceware.org/lvm2/](http://sourceware.org/lvm2/) LVM home]] including LVM IRC channel etc.


---+++ LVM and RAID: Config Backup and Recovery

Need to look at corruption-of-LVM issues re recovery - more complex on-disk format and less complete tool support.

[[[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874) Recovery of LVM2 volumes on top of RAID]] - not that simple, but not too bad.

Important to use =vgcfgbackup=, which creates copy of each VG's config in =/etc/lvm/backup - done on valluga.


[[[http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html?page=last](http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html?page=last) LVM/RAID recovery issues]] particularly if LVM VG corrupted 

---++++ RAID recovery

[[[http://deb.riseup.net/storage/software-raid/](http://deb.riseup.net/storage/software-raid/) Software RAID article]] including how to boot GRUB if RAID 1 disk has moved 
from hdb to hda.


---+++++ Use of UUIDs by LVM

Ubuntu LVM2/EVMS managed to cope OK when drives moved from hda to hdb - each volume has a UUID so it can figure out what's what automatically.  Only the non-LVM /boot needed to be changed in /etc/fstab (after booting via !SysRecCD.)

---++++ LVM RecoveryDisk

Knoppix 5.0.x does support LVM2.  [[[http://www.knoppix.net/wiki/LVM2](http://www.knoppix.net/wiki/LVM2) LVM2 page]] includes good summary of commands to scan for VGs and mount their LVs, namely:

```

Find the volume groups
# vgscan

Make them available
# vgchange -a y

To mount a logical volume first find out what it is called, unless you know already. Use lvs or vgdisplay/lvdisplay for this. 
# lvs
LV   VG   Attr   LSize Origin Snap%  Move Log Copy%
home vg   -wi-ao 2.09G
var  vg   -wi-ao 1.32G

In this example, the volume group 'vg' contains two logical volumes, called 'home' and 'var'. To mount the 'home' volume: 
# mount /dev/vg/home /mnt/tmp


```

[[[http://mkcdrec.ota.be/](http://mkcdrec.ota.be/) MkCDRec]] recovery disc, claims to support LVM/RAID

---

### Post by Cadmus on 2008-02-28
Thanks for all the advice, it's always good to get some ideas from someone who's been using it a while.

Now to convince my bosses that installing Ubuntu won't cause the sky to fall down, black to become white, and the wind to start making a noise like a TIE Fighter backing up.

---

