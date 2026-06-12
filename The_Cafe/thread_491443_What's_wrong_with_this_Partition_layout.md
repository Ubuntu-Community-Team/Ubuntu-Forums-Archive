---
title: "What's wrong with this Partition layout?"
date: 2007-07-03
forum: The Cafe
---

### Post by TravMan63 on 2007-07-03
a) Windows has space
b) Windows has too much space
c) Swap is incorrect
d) Something else

The plan for this came from [ _the fedora forum_]("http://forums.fedoraforum.org/archive/index.php/t-323.html")

TM

---

### Post by bigken on 2007-07-03
well 1st of all you can only have four primary partitions if yyou need more you have to create an extended partition

---

### Post by Lord Illidan on 2007-07-03
swap is incorrect. /swap doesn't exist.

---

### Post by koenn on 2007-07-03
> **Lord Illidan said:**
> swap is incorrect. /swap doesn't exist.
yep, the swap partition should not have filesystem ext3 an be mounted as /swap. 
It has to be formatted as "swap" and not mounted at all.
That's probably what the guy on the fedora forum meant :
> 
Some general guidelines:
/ (root) -- around ~700MB
/boot -- 80 -100MB
/home -- at least 1G
/tmp -- at least 150MB
/usr -- should be your largest partition IMO; holds all software installs -> at least 6GB
/var -- at least 700MB
**<swap> --** 2x RAM, though probably no need for more than 1G (some may say less..)


I do have my doubts about the effectivenes separate partitions for /tmp /usr /var and so on on a PC, but a lot depends on how the computer will be used, and personal preferences.

---

### Post by TravMan63 on 2007-07-03
it's true that /swap doesn't exist... guess I got ext3 happy and...

Have 1GB of RAM  - thought 1GB of swap was plenty (although on windows have run out of virtual memory with that setup (working with large videos)...

I've never setup a linux pc with that many partitions before - I could understand /home and /usr being separate... and maybe boot too...

The partitions (primary and extended) can be identified by the #s - I think any #>4 indicates extended.

-- 
there's gotta b a few windoes comments ;)

TM

---

### Post by macogw on 2007-07-03
And swap should go toward the beginning of the drive.  You don't want to swap if you can help it, but if you have to, you want to swap FAST, and the fastest read/write is at the beginning of the drive.  Put swap and boot at the beginning, then Windows, then an extended partition with everything else.

Trav, I think the numbers >4 is just "theoretically if it's >4 it'll be in extended," but that is only true the first time it's partitioned.  If you have it already partitioned with an extended parition and all, but you only had 2 primary partitions before it, you'd have:
/dev/hda1 primary
/dev/hda2 primary
/dev/hda3 extended
/dev/hda4 logical
/dev/hda4 logical
/dev/hda6 logical

Then, say you delete the 2nd primary partition and decide to split it into 2 primary partitions, the others all retain their partition numbers and the 2 goes away completely, then the new ones are assigned numbers higher than all the others, like this:
/dev/hda1 primary
/dev/hda7 primary
/dev/hda8 primary
/dev/hda3 extended
/dev/hda4 logical
/dev/hda5 logical
/dev/hda6 logical

That's how the numbers rearranged when I've repartitioned without deleting all partitions first.

---

### Post by TravMan63 on 2007-07-03
> And swap should go toward the beginning of the drive. You don't want to swap if you can help it, but if you have to, you want to swap FAST, and the fastest read/write is at the beginning of the drive. Put swap and boot at the beginning, then Windows, then an extended partition with everything else.

I figured having the swap position towards the center would be faster - doesn't the seek time (head movement) factor heavily into that?  Good discussion.  Another point- windows likes to be in the 1st (primary) partition, and I think it's mandatory for the 9x series.

> 
Trav, I think the numbers >4 is just "theoretically if it's >4 it'll be in extended," but that is only true the first time it's partitioned. If you have it already partitioned with an extended parition and all, but you only had 2 primary partitions before it, you'd have:

Hmm.... I just partitioned the drive and the 1st logical drive was hda5...
hda1 - primary
hda2 - primary
hda5 and up - logical

Interestingly - the screenshot from gparted shows hda3 (the extended partition)- which doesn't show up on the 'install' partition setup...

vewwy interesting - maybe the key phrase IS 'only true the 1st time'...

---

### Post by prizrak on 2007-07-03
Windows system partition should be sitting on NTFS

---

### Post by TravMan63 on 2007-07-05
> Windows system partition should be sitting on NTFS

True for NT series (NT 2000 2003 XP Vista(?), but not for 9x.  Early versions of NT wouldn't support FAT32, just FAT.  The newer ones will work on FAT or NTFS, but NTFS is more secure.

---

### Post by lamalex on 2007-07-05
make your /boot ext2, no need for ext3 and it will be a bit faster to boot as well.

---

