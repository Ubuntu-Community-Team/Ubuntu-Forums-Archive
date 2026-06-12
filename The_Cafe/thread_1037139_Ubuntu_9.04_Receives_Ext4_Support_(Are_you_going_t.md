---
title: "Ubuntu 9.04 Receives Ext4 Support (Are you going to use it?)"
date: 2009-01-11
forum: The Cafe
---

### Post by Kosimo on 2009-01-11
Here we go. Ext4 (even if at the moment not by default) It's going to be available during Jaunty installation. Would you use it?


[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1)

---

### Post by diablo75 on 2009-01-11
What's so great about ext4?  (Honest question)

---

### Post by Eclipse. on 2009-01-11
Yeap, it got added to the daily builds the other day.

You should probally add other options like xfs, resiers ect.

I will keep using ZFS through FUSE, the benchmarks over ext3 do look good though.

EDIT: To answer the question above it gives quicker write/read acess to your files and increases the max partition size, not that that really matters unless your a big organisation with alot of data.

---

### Post by Kosimo on 2009-01-11
> **Eclipse. said:**
> Yeap, it got added to the daily builds the other day.

You should probally add other options like xfs, resiers ect.

I will keep using ZFS through FUSE, the benchmarks over ext3 do look good though.

EDIT: To answer the question above it gives quicker write/read acess to your files and increases the max partition size, not that that really matters unless your a big organisation with alot of data.

Yes you're right. But I was about to ask between the two Ext.x system.
By the way, can you make a ZFS partition during intrepid installation?

---

### Post by MikeTheC on 2009-01-11
I always keep my data backed up elsewhere, so I'll try out ext4. I just hope it's as solid and production-worth as Canonical thinks it is.

---

### Post by Kosimo on 2009-01-11
> **MikeTheC said:**
> I always keep my data backed up elsewhere, so I'll try out ext4. I just hope it's as solid and production-worth as Canonical thinks it is.

If linus torvalds said that is stable, and added official support in 2.6.28.... I'm 100% sure it is..

---

### Post by jrusso2 on 2009-01-11
I use JFS.  I don't like anything from EXT series of file systems and they should get rid of those old file systems they have always been the bain of Linux.

They need a clean start with a new file system.

---

### Post by SunnyRabbiera on 2009-01-11
> **jrusso2 said:**
> I use JFS.  I don't like anything from EXT series of file systems and they should get rid of those old file systems they have always been the bain of Linux.

They need a clean start with a new file system.

I have yet to encounter any major issues with ext3, and compared to something like NTFS or FAT its a far cleaner system.
I will give EXT4 a shot with Jaunty (I definately intend on giving Jaunty a full test drive as already it seems to be an improvement over Ibex)
Not saying anything bad about JFS, though its not so great when you want to read JFS from windows as to my knowledge there is no way to read JFS from windows (I suspect this is why ext is default as windows can read it with a little help.)

---

### Post by Slug71 on 2009-01-11
> **Kosimo said:**
> If linus torvalds said that is stable, and added official support in 2.6.28.... I'm 100% sure it is..

Using Jaunty already and Ext4 is rock solid so far. Boots quicker for me too.

---

### Post by Slug71 on 2009-01-11
> **jrusso2 said:**
> I use JFS.  I don't like anything from EXT series of file systems and they should get rid of those old file systems they have always been the bain of Linux.

They need a clean start with a new file system.

Btrfs will be here soon. :p

---

### Post by spoons on 2009-01-11
I'll use it, the performance is better according to phoronix...

EIDT: When compared to EXT3.

---

### Post by AlexDudko on 2009-01-11
I've already used ext4 in Fedora and didn't notice any difference with ext3.
Surely I'll give it a second try.

---

### Post by MaxIBoy on 2009-01-11
I'm probably going to use ReiserFS.

---

### Post by Vince4Amy on 2009-01-11
I don't use Ubuntu but when the other distros get ext4 I'm still going to keep with JFS as it works for me.

---

### Post by y@w on 2009-01-11
You're probably not going to notice a difference in the filesystems unless you are managing systems under serious load. Just like any other industry, different tools for different jobs... Some filesystems do better with tons of small files and some do better with larger files. The ext family isn't the greatest on performance but tends to be a good all-around filesystem which makes it great as a default choice. To answer the OP, I wouldn't hesitate to use ext4. It's spent years in dev. and testing.

---

### Post by handy on 2009-01-11
I use JFS, though from a recent set of tests I saw posted in this forum, I really do think that ReiserFS will make a noticeable difference in speed.

So the next set up I do will be on ReiserFS, then I'll know. :-)

---

### Post by EdThaSlayer on 2009-01-12
I will format my hard drive immediately. I don't want to get in the mindset that old is strong and new is weak.

---

### Post by Bachstelze on 2009-01-12
I'll stick with Reiser and XFS. ^^

---

### Post by Circus-Killer on 2009-01-12
for a guy like me, it probably makes little to no difference on what file system i use. as long as it works its fine by me.
having said that, i'll give it a shot.

---

### Post by halovivek on 2009-01-12
Could you please tell me what is the big difference between ext3 and ext4?

---

### Post by bufsabre666 on 2009-01-12
> **halovivek said:**
> Could you please tell me what is the big difference between ext3 and ext4?

the main reason for me switching is the FSCK

on ext3 is scans every block, in ext4 it only scans used blocks, so thats ganna cut down significantly in fsck time

---

### Post by HunterThomson on 2009-01-12
Ya, There are better file-systems the the EXT's. But, I am a home user that tries a lot of new stuff. So, I stick with it because I know it works well in general and I have no problem finding info on it.

When I set up my RAID I will use XFS.

---

### Post by jomiolto on 2009-01-12
Missing option: combination of both of them (and others).

I currently use ext3 for most of my root file systems (I have several distros installed) and XFS for my data. With Jaunty I'm probably going to use ext4 for the root file system.

ext3 and ext4 are really quite antiquated in design (fixed number of inodes for example) and I'm glad to be rid of them, once btrfs and possibly tux3 become stable. I just hope they'll be fast :)

---

### Post by MisterFlibble84 on 2009-01-12
Xfs

---

### Post by Yownanymous on 2009-01-12
Nowadays I personally use Ubuntu on FAT32, on a USB stick, shock-horror. And it does go painfully slowly at times...

---

### Post by adamlau on 2009-01-12
I'll use Ext4 like I use Ext3 now: As /boot with XFS everywhere else :) .

---

### Post by billgoldberg on 2009-01-12
Actually I'm going to use ext2 on the only Ubuntu machine I have in the house, when installing 9.04.

It seems non-journaling filesystems are better for SSD drives due to their finite write cycles.

On Arch I'll stick with ReiserFS thanks.

---

