---
title: "mdadm Raid 1"
date: 2011-03-23
forum: Server Platforms
---

### Post by NedHanlon on 2011-03-23
Which do you think is better, for a home file server with the goal of fault tolerance, Raid 1 with two drives and a hot spare, or raid 1 with three drives? 

Note: 
I understand that Raid is not an alternative to good backups. I have those as well.

---

### Post by Vegan on 2011-03-23
If you have a good backup solution then use RAID0 which is faster.

Then be religious about backups

I use a script to backup daily, works for me

---

### Post by disabledaccount on 2011-03-23
Raid0 is good for desktop system directed to gaming - if you want to call PC a "server" then HDD redundancy is a must. Not only to protect data - server needs to have redundant swap and temp memory to prevent crashing when HDD problem occurs - this very basic condition elliminates Raid0 from server area of usage.
Both Raid1 and Raid10 have the same read performance as Raid0 under md, ofc writing is slower.

Raid1 for file server is quite good solution, but I would say that using 3 HDDs is not efficient solution, because failure of 2 disks at once is almost impossible. I suggest creatng 2-HDD Raid10 - better write performance than raid1, same level of redundancy with one downside - it's not extendable (what is not really problematic, because it's easy to copy whole system and data to new Raid array).

---

### Post by NedHanlon on 2011-03-24
Thanks!

---

### Post by saibaggins on 2011-05-03
tomazzi, have you actually tried mdadm raid1?

i know in theory it should read as fast as raid0 but it looks to me like it doesnt, nowhere near! 

[http://ubuntuforums.org/showthread.php?p=10765322#post10765322](http://ubuntuforums.org/showthread.php?p=10765322#post10765322)

---

### Post by a2j on 2011-05-04
I'd use software RAID10 with two drives for now.
you don't want RAID0 on the home file server. even if you back it up daily.

its much easier to send a drive back for replacement (if it failed) and still have your server running and accessible. put the new one in, even if its 1-2 weeks after the drive crash, and no down time. no re-installation, no re-configuration.

---

### Post by aphatak on 2011-05-04
If you are planning on three drives or more, I should give RAID5 some serious consideration.  That gives a capacity equal to two drives, but still keeps information to recover if one should fail.  In fact, I have been running three file servers in my home, two with six drives each and the third with five drives, in RAID5 configuration.  I found it works very well for me.

---

### Post by a2j on 2011-05-04
aphatak
**mdadm** so I'm assuming he is on software raid. so unless his boot partition is on separate RAID1 or 10 or just a single disk/partition, RAID5 will not work here.

---

### Post by aphatak on 2011-05-05
@A2J:  Yes, it would be software RAID.

---

### Post by a2j on 2011-05-05
so, I was just saying that OP cannot have the only software RAID5 on the system. only secondary. /boot can not be on sRAID5

---

