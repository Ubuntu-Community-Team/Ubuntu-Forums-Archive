---
title: "RAID Alternatives"
date: 2011-01-20
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-20
Hey Everyone,
I'm setting up my first server today. I only have one hard drive, so I can't RAID yet... although I'd like to use RAID 1 in the future.

Here's my question: What is the best RAID 1 alternative or backup strategy? I know I should assume that what can go wrong, WILL go wrong. How do I reconcile that with my budget?

Thanks!

---

### Post by arrrghhh on 2011-01-20
Really depends on your budget.

If you're concerned about the data, RAID1 is a good way to ensure that you can recover from a single hard disk failure.

RAID5 you could lose 1 disk, RAID6 2.

You have to weigh how much redundancy/security blankets you want, and how much you want to spend.

As far as a RAID1 alternative, I would just backup the essentials - documents, configuration files, etc.  A lot of people like to just take a backup of the /etc directory, that way they get (almost) all of their configuration files in one shot.

If you're looking for software for backing up, clonezilla is good if you want to do bit-for-bit hard drive replication, and bacula is good if you just want to backup data.

---

### Post by arrrghhh on 2011-01-20
Ugh, again I swear I only hit submit once!  The Ubuntu Forums have been having issues these last few days... Sorry for the doublepost!

---

### Post by kgatan on 2011-01-21
Think of it like this, RAID is a backup for keeping the server running if one drive crashes.

Raid is more secure with small amounts of data since rebuild of the array in case of a failure is short. 
But with more data rebuild takes a long time and if anything happens during that time all is lost.

For an actual backup of data there is no shortcut, you need it on another machine and offsite (fire, theft etc etc proof) or backups on removable devices stored offsite.

For two machines id use rsync and rsnapshots to backup. If you have one machine id rotate removable devices and use rsync.

---

### Post by Vegan on 2011-01-21
> **arrrghhh said:**
> Really depends on your budget.

If you're concerned about the data, RAID1 is a good way to ensure that you can recover from a single hard disk failure.

RAID5 you could lose up to 2 disks.

You have to weigh how much redundancy/security blankets you want, and how much you want to spend.

As far as a RAID1 alternative, I would just backup the essentials - documents, configuration files, etc.  A lot of people like to just take a backup of the /etc directory, that way they get (almost) all of their configuration files in one shot.

If you're looking for software for backing up, clonezilla is good if you want to do bit-for-bit hard drive replication, and bacula is good if you just want to backup data.

**WRONG**



RAID5 can tolerate a single disk failure, RAID 6 can tolerate 2 failed disks.

---

### Post by arrrghhh on 2011-01-21
> **Vegan said:**
> RAID5 can tolerate a single disk failure, RAID 6 can tolerate 2 failed disks.

Ah, my mistake - you are correct.

---

### Post by Boondoklife on 2011-01-22
Actually RAID 5 is fairly nice, and if you leave drives in it set as spares, you can loose more than one. The downside of rebuild time is a real problem so if it does worry you then maybe RAID6 would be a better choice.

I personally like to use at least 5 drives. This can give you the power of a 4 disk RAID5 with a spare. This would give you the safety of loosing 2 drives and still keep your data as well as a speed boost.

---

### Post by katakaio on 2011-02-24
I will say that RAID5 has turned out to be less of a "magic bullet" than it was touted to be. I got on the RAID5 train back in 2006, but I was disappointed with slow read and write speeds. To be fair, this was because the parity calculation was performed on my processor instead of a dedicated controller, but in my experience RAID5 has not lived up to the higher read speeds that multiple drive heads were promised to deliver.

In terms of reliability, well - there are countless stories of entire RAID5 arrays going down. Some are due to two-drive failures, some are due to a failed rebuild due to a read error, and some are due to the controller itself giving up the ghost. My RAID5 failure was due to the last reason, and since most RAID controllers are proprietary, you can't simply plug your drives into another RAID controller to recover your data.

The bottom line is that hard drive sizes are increasing at a rate that is beginning to test the limits of RAID rebuilding. And if you aren't using a very robust hardware-controlled RAID solution, your disk performance may actually suffer. The folks over at [_BAARF_]("http://www.miracleas.com/BAARF/BAARF2.html") have many good (albeit critical) articles on the subject if you want some late-night reading material. I would personally choose something like ZFS (which is very Ubuntu-friendly, mind you) over RAID any day. Check out [_this video_]("http://www.youtube.com/watch?v=X8bFbK7c_NU") to see how simple it is in Ubuntu.

---

### Post by gtfourdreams on 2011-02-24
> **Ranger_Joe said:**
> 
Here's my question: What is the best RAID 1 alternative or backup strategy? I know I should assume that what can go wrong, WILL go wrong. How do I reconcile that with my budget?

Going back to the original question here... The correct answer is, "it depends". How critical is the data and how much work do you want to do? 

If you just want to be able to have the server back up and running ASAP when there is a hard drive failure, the quickest and easiest method is RAID1. Get 2 identical hard drives and maybe a cold spare if its important. This would be suitable for a standard workstation or basic server.

If you want an alternative to this, there are too many to go in detail without knowing your requirements are. Other viable options would RAID5/6 or a NAS device, but that would require more hardware and more work on your part.

---

### Post by rubylaser on 2011-02-25
If the OP doesn't have enough money for an extra hard drive, why are you bothering to tell them to buy an expensive hardware RAID card?  Is hardware a nice solution, sure, but mdadm works great as well, and has no problem producing very fast read and write speeds with decent hardware, and it's free, and not tied to a specific type of hardware.

All that being send, RAID is not a backup solution.  I would set your system up with a single drive now, and come up with some inexpensive backup (burn to DVD, dropbox, google docs, crashplan with a friend, etc).  And add a second disk when you have to money, and migrate to an mdadm RAID1.  That's probably the most cost effective solution based on what you've mentioned of your available finances.  Hope that helps.

---

### Post by YesWeCan on 2011-02-25
> **Ranger_Joe said:**
> Hey Everyone,
I'm setting up my first server today. I only have one hard drive, so I can't RAID yet... although I'd like to use RAID 1 in the future.

Here's my question: What is the best RAID 1 alternative or backup strategy? I know I should assume that what can go wrong, WILL go wrong. How do I reconcile that with my budget?

Thanks!
Hi there.
My advice is not to assume just because a particular RAID level *can* recover from n disk failures that it will.
IMO the most dependable is RAID1 or 1+0. It is also the fastest to write and fastest to resync. No complicated parity schemes to go wrong or impede data recovery from a failed array.
RAID 5 is less reliable than RAID 1 and gets less and less reliable the more disks you use. Distributed parity scheme. I wouldn't touch it.
RAID 6 is good with not too many disks. Depends on the quality of the disks and the controller. Pretty uP intensive during writes. Distributed parity scheme.

As for alternatives, it depends on your budget and what you are trying to guard against. Ubuntu comes with sbackup which is adequate for most situations but you need a disk to back up to! I guess the two big worries are disk failure and accidental data deletion. Both require some secondary storage somewhere. I use a couple of external USB disks to back up to. Backup doesn't need to be fast. I suppose one can even back up to "The Cloud" but I don't know anything about that.

---

