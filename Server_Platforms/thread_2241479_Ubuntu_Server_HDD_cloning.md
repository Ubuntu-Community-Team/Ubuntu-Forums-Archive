---
title: "Ubuntu Server HDD cloning"
date: 2014-08-26
forum: Server Platforms
---

### Post by rahul4557 on 2014-08-26
I am running a Ubuntu Server 12.04 LTS, Its running from a single HDD (no RAID) and i want to keep spare HDDs cloned from current running HDD, So incase of HDD crash the swapping the HDD should fix the server.



Filesystem       1K-blocks        Used        Available       Use%   Mounted on
/dev/sda2      471852344    3262940     444597596       1%         /
udev                4072428             4         4072424       1%        /dev
tmpfs               1632800          260         1632540       1%       /run
none                    5120              0              5120       0%      /run/lock
none               4082000              0          4082000       0%     /run/shm
/dev/sda1          497696         2116           495580       1%      /boot/efi



Can Norton Ghost used to clone this HDD..?? what about Clonezilla..??

Any other easy way this could be done..??

---

### Post by TheFu on 2014-08-26
Imaging is the inefficient way. To do it properly, the main OS needs to be shutdown, another OS booted (flash drive, CD/DVD), then run a mirroring tool - like clonezilla, partimage, fsarchive, dd, ddrescue, or any of 20 others.

Or you could create an image once with those tools and use nightly backups to maintain it while the original system keeps running.  This is less than ideal, because it doesn't allow for versioned backups - which are critical if a virus hits or files are corrupted in some way. After the mirror happens, we are left with 2 corrupted copies. Not good.  If a virus hits, it often takes a few days or weeks to notice it - versioned backups for 30, 60, 90, 120 days certainly are nice.  Of course, it is a little more work to setup, but once you have to going - it is zero effort. [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is what I use.

Any actively open and modified files need to be quiesced for a safe backup. This usually applies to DBs. Usually a DB dump to text is what we do - let the differential backups handle any versioning - be happy.

If the RTO and RPO requirements demand it - don't slack off.  Need both HA and quick failover?  Regardless, everyone still needs 30+ days of versioned backups - then you need multiple solutions - RAID, a mirror AND nightly, versioned, backups.

---

### Post by rahul4557 on 2014-08-27
Thanks TheFu,

There are no changes made into the server, as its a web server, no DBs.So just one backup will be enough.
It should be such that even in my absence any person should be able to restore it with simple steps.

I just found [Mondo Rescue]("http://www.mondorescue.org/")
how about it..?? would that be useful..?? will it backup entire installation and will be easy to restore..??

---

### Post by TheFu on 2014-08-27
Never heard of or used Mondo Rescue. Sorry.

---

### Post by Hugo_Serrano on 2014-08-27
Hi!
Yes you can use Mondo to image your system. 
As a best practice, backup and test your backups! You will have to do it in a different server or disk. (and you can save that disk to recover from a failure)

It's not the best backup method, but if it works for you, it's all you need! 


Cheers,
Hugo.

---

