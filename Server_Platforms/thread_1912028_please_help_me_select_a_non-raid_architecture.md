---
title: "please help me select a non-raid architecture"
date: 2012-01-19
forum: Server Platforms
---

### Post by Wiico on 2012-01-19
Context:
I have a (multi)media server which holds three categories of files: video, music and photos.

Files are shared to MS Windows desktops using SAMBA.
to the Windows desktops it should appear that there are three directories (one for each category). 

Problem:
[LIST]
[*]I want to be abled to add HDDs on the fly to increase storage yet retaining the data.
[*]I don't need a lot of performance
[*]I want some form of redundancy on photos (can't lose these to hdd failure)
[*]I don't want any redundancy on video and music (HDDs aren't dirt cheap anymore.
[*]When one (or more) of the HDDs containing video or music crashes I want to be abled to still be abled to use the remainder of the video/music files.
[*]I want to be abled to hotswap drives to replace a section of my video/music 'library'.
[/LIST]

I think I want some form of RAID (RAID 1) on my photos (two small 2.5" HDDs). 

Question:
What would you advice me to use for my Music/Video files.
JBOD or LVM or ???? or is it just impossible



p.s. My drives are empty at the moment :).

---

### Post by rubylaser on 2012-01-20
Why are you against RAID?  I would just suggest setting up an mdadm RAID5 or 6 array as a container for all of your stuff.  You can easily add new drives to the array, and the disk you where planning to use as redundancy for your pictures could be used for all of your data.

If you're completely against RAID, you could look at [Unraid]("http://lime-technology.com/"), but frankly, mdadm will work great, it's free, and you might as well try to protect all of your data instead of just a part, if you're already planning to build an array.

Another idea could be to use [Greyhole]("http://www.greyhole.net/") or [FlexRAID]("http://openegg.org/"), but mdadm is so easy to use and it's very proven, that's what I always use. 

Finally, how much data do you need to store?  A (3) 2TB RAID5 array would give you 4TB of usable space, and although they're around $50-75/each more expensive than they used to be, they are getting cheaper again.

---

### Post by Wiico on 2012-01-20
Basically the data which i want to store hasn't got much value to me, I just use it as a buffer for my home cinema. The thing I don't want is having to rebuild (at least some part of) my RAID array when I add another HDD (Slow processor, no dedicated raid card).

I just want to span another HDD to the end which contains more files. I'd like to think of it as some sort of unordered linked list on which I can remove and insert HHDs on the fly without having to worry about rebuilding. 

Think about it as one of those old multi disc dvd changer consumer electronic devices, if one dvd disc fails I still have the other dvd discs from which I can play media. If the device fails I still can remove the media from it and put it in another device.

Also the HHDs containing pictures cannot be used in the RAID array because these are much smaller (maybe 50GB in size compared to 2+TB for the other media types).

---

### Post by rubylaser on 2012-01-20
I'd use Greyhole then.  You can do [disk pooling]("http://www.amahi.org/tour/disk-pooling") which is exactly what you're talking about.  You could even choose to use [Amahi]("http://www.amahi.org/") which has Greyhole baked right in.

---

### Post by Wiico on 2012-01-20
Thank you for your responses, rubylaser.
Greyhole sounds good... now I only need to find out if I want greyhole standalone or amahi with Greyhole.

I'm closing the Thread now.

---

### Post by rubylaser on 2012-01-20
Glad to be of service :)

---

### Post by Wiico on 2012-01-22
update:
I think I'll be going for mhddfs instead :P

amahi is difficult to install from USB key (and most free software plugins aren't free (though I could manually install them)).

And greyhole is too time consuming to set up myself

mhddfs should allow me to mount X hdd's with different filesystems on it and make it appear as if though their files are mounted into one directory.

---

### Post by codmate on 2012-01-23
Weird that nobody mentioned the tried and tested LVM2...

---

### Post by rubylaser on 2012-01-23
LVM would work as well and is definitely well tested. mhddfs works pretty well, and is dead simple to setup too.  As I said earlier though, I would be going with mdadm and software raid for all of your data.

---

### Post by Wiico on 2012-01-23
I'd rather have a FS per disk so that I KNOW not all data is lost when a drive dies.

RAID 5 is nice, but if 2 disks crash (which is likely because I'm using old HDDs) I lose everything, plus not everything is the same size.

I've tried LVM and removed a HDD to simulate a crash.. but it didn't much like it :). Sure I could possibly repair it and consider all data on the dead HDD as bad blocks on the Logical Volume but that seems like too much work.

As I said Earlier I don't want or need RAID I just don't want to lose everything at once. And I wanted all volumes to mount on one mountpoint (which is possible using mhddfs (and greyhole and ...probably some other methods)).

But since greyhole takes longer to set up than mhddfs (which is basically one extra line in /etc/fstab) I chose mhddfs.

RAID 5 might however be a solution in the future when HDD prices drop back to normal but for the moment I'll be using 2x 2TB 1x 1.5 TB 1x 1 TB (which would leave me at 3TB for RAID 5 instead of 6.5 TB)

---

### Post by codmate on 2012-01-24
> **Wiico said:**
> I'd rather have a FS per disk so that I KNOW not all data is lost when a drive dies.

RAID 5 is nice, but if 2 disks crash (which is likely because I'm using old HDDs) I lose everything, plus not everything is the same size.

RAID redundancy is no substitute for regular backups, and should never be used in place of such.

Whichever system you chose to use - make sure you are regularly replicating your data, or at some point you will lose it, RAID or no RAID.

> **Wiico said:**
> 
I've tried LVM and removed a HDD to simulate a crash.. but it didn't much like it :). Sure I could possibly repair it and consider all data on the dead HDD as bad blocks on the Logical Volume but that seems like too much work.

As I said Earlier I don't want or need RAID I just don't want to lose everything at once. And I wanted all volumes to mount on one mountpoint (which is possible using mhddfs (and greyhole and ...probably some other methods)).

But since greyhole takes longer to set up than mhddfs (which is basically one extra line in /etc/fstab) I chose mhddfs.

RAID 5 might however be a solution in the future when HDD prices drop back to normal but for the moment I'll be using 2x 2TB 1x 1.5 TB 1x 1 TB (which would leave me at 3TB for RAID 5 instead of 6.5 TB)

LVM2 on RAID5 with regular rsync backups to another location would be my choice. It is for most things these days to be honest.

---

### Post by Wiico on 2012-01-24
Even though my issue is solved I still feel the need to reply (again).

I know RAID isn't a subsitute for backups. But I don't want backups and I don't need RAID. The only thing I wanted is that when a hdd crashed I still had another hdd with other data on it to play. I don't mind losing 80% of all data as long as I can kill some time watching/listening to the remaining 20%. 

All I wanted was 
A) have some data remaining when n-1 HDD crash (don't even care about which part). which can be viewed without having to go through rebuilding data.
B) have all my data accessible from one directory (for each type)
C) if everything crashes.. too bad I'll watch a dvd instead :P

my pictures however are backed-up at multiple locations on multiple discs and multiple media types. Simply because I cannot recreate them.

---

