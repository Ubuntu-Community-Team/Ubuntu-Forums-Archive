---
title: "Drobo-like RAID setup"
date: 2012-10-14
forum: Server Platforms
---

### Post by FieldDoc on 2012-10-14
I'm new to RAID and trying to get my head around things.  I have owned a [Drobo]("http://drobo.com") in the past (which I liked) but it failed.

Here's a hypothetical scenario:

Assume I set up a RAID-5 array consisting of four 1TB hot-swappable 2.5" SATA drives.  I name this volume 'My Data'.  By my calculations, that would give me 2.7TB of usable space and the ability to recover if a single drive fails.

I have a few questions:

1. What happens if I pull out a single 1TB drive and replace it with a 2TB drive?  Would the array automatically rebuild itself with no issues?  Would the maximum capacity remain 2.7TB?

2. If number (1) above is true and the array rebuilds itself with three 1TB drives one 2TB drive what would happen if I then pulled another 1TB drive out and stuck in a 2TB drive (you can see where I'm going here can't you).  Would I eventually be able to gain more storage by gradually adding bigger drives?

From a practical point of view, how much input is required from me as the end user whilst these drives are being pulled out and put in?  On the Drobo, the storage space just automagically handles itself.  Would I have to be actively involved in telling Ubuntu what was going on or would any of it be automated?

Thanks in advance,

---

### Post by rubylaser on 2012-10-14
The following is going to assume you plan to use  mdadm (software RAID) for this task.

1. mdadm will not magically replace your 1TB drive with a new 2TB, it will need some intervention from you to add the new drive.  Ubuntu is a general purpose distro, so having the OS automatically do anything with new hard drives could lead to a very bad outcome. That being said, the intervention needed is pretty simple.  You just tell mdadm to remove the old disk and then add the new one.

2. If you replace all of the disks in the array, you can expand your mdadm array to take advantage of the new storage space (you will need to expand the filesystem too).

I wrote up a quick tutorial for a different Ubuntuforums member a while back to systematically replace disks with larger ones.  [This tutorial]("http://zackreed.me/articles/69-mdadm-replace-smaller-disks-with-larger-ones") covers all of the concepts you've asked for clarification on.

Please let me know if I haven't answered your question well enough, or if you where considering a different setup.

As an aside, when you say your Drobo failed, did you have a hardware failure, or did you lose too many disks for the Drobo to calculate parity?

---

### Post by FieldDoc on 2012-10-15
First of all, thanks for the excellent mdadm howto rubylaser - it's very helpful 

You're correct that I plan on using software RAID. 

Although some intervention is required on my part to handle rebuilding - presumably I could automate this with scripts or a self-written daemon? In essence, I'm trying build a proof of concept media box that requires minimal intervention from the end user (I certainly wouldn't expect the end user to have to use the terminal!).

The idea is to have Drobo like ease of use coupled to XBMC or OpenELEC. 

As for my Drobo, the unit itself failed. Twice :(

---

### Post by LHammonds on 2012-10-15
Notice he said "if" you replace "all" drives.   Drobo is a bit different than standard raid.

With Drobo, you can mix-n-match drive sizes and it utilized the capacity of each one.  In most every other raid implementation (hardware/software), if you replace a failed drive with a larger drive, it will only use the amount of space from the original and the extra space goes unused.

I would also be interested in a Drobo-like management of hard drive for Ubuntu but have not seen it (have not looked very hard yet either)

I hope you find something because Ill be following suit with an XBMC setup as well.

LHammonds

---

### Post by FieldDoc on 2012-10-15
> **LHammonds said:**
> Notice he said "if" you replace "all" drives.   Drobo is a bit different than standard raid.

With Drobo, you can mix-n-match drive sizes and it utilized the capacity of each one.  In most every other raid implementation (hardware/software), if you replace a failed drive with a larger drive, it will only use the amount of space from the original and the extra space goes unused.

I would also be interested in a Drobo-like management of hard drive for Ubuntu but have not seen it (have not looked very hard yet either)

I hope you find something because Ill be following suit with an XBMC setup as well.

LHammonds

For what it's worth - [SnapRAID]("http://snapraid.sourceforge.net") combined with [Greyhole]("http://www.greyhole.net") looks promising...

---

### Post by rubylaser on 2012-10-15
Snapraid + mhddfs or Unraid are other options too.  

As a side note, I've used both mdadm and ZFS backed storage with multiple XBMC frontends for years, and they've been rock solid and very reliable for me.  At this point I wouldn't trust the pictures of my kids or family movies to anything other than ZFS and raidz2 at a minimum.  I love Copy on Write and the end to end checksumming + zfs send|recv for my backup servers.

---

