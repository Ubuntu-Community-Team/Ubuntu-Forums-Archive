---
title: "Partitioning a mirrored har drive"
date: 2011-05-02
forum: Server Platforms
---

### Post by dodgyphil on 2011-05-02
Hi,

Have just installed Ubuntu Server 10.04 on a dell with a perc 700 raid card. Running a mirrored raid1 (2x 500G as one drive). All went well. Have installed a basic Gnome front end and Webmin.

I want to partition the hard drive into system and data storage areas. What is the best way to do this with a mirrored RAID system? 

Any advice gratefully received.

Cheers
Phil D

---

### Post by collisionystm on 2011-05-02
> **dodgyphil said:**
> Hi,

Have just installed Ubuntu Server 10.04 on a dell with a perc 700 raid card. Running a mirrored raid1 (2x 500G as one drive). All went well. Have installed a basic Gnome front end and Webmin.

I want to partition the hard drive into system and data storage areas. What is the best way to do this with a mirrored RAID system? 

Any advice gratefully received.

Cheers
Phil D


Do you plan on doing samba shares?

You really don't need to partition. However, if you so choose... I believe this needed to be done with an LVM installation.

When you installed, did you choose LVM partition?

If you want to use a web interface with your Ubuntu Server, I really suggest you stop what your doing now and install Zentyal over top of what you have.

It is based on Ubuntu Server 10.04 and has a much better Web interface, software installation is easier, and its all around BETTER. I use it as a PDC and Samba share in an environment of 120 users.

[http://www.zentyal.com/](http://www.zentyal.com/)

---

### Post by dodgyphil on 2011-05-02
Hi,

Yes, need to run an Access database out to windows machines, mail for about 5 users and shared data resources.

Cheers

Phil

---

### Post by tgalati4 on 2011-05-03
Typically you would put the OS on a separate, non-RAID drive and put the user space on the mirrored RAID.  If the OS drive fails, then you can live boot off of the CD for either repair or reinstall (if you need to replace the OS disk.)  Mirroring for the userspace protects the data, but RAIDs can fail in many ways including RAID controller failures, power supply failures, lightning strikes that burn up your UPS, etc.  So you need a decent off-site or hotswap backup as well.

Since servers perform a lot of logging, it's sometimes not recommended to include the OS in the RAID because of the excessive writes and mirroring of those writes (which is really not as important as user data).

I have a PERC controller on my Dell poweredge servers, but I'm not familiar with the 700 model features.  You could partition each drive with a small, but similar size OS partition, then create a data partition on each and simply RAID mirror the data partitions and perform a static dd copy of the OS to the extra OS partition.  I'm not sure if the PERC controller can RAID secondary partitions across two drives.  That is something you would have to research.  I know that you can use an additional drive bay and perform hotswaps.  That's helpful for snapshotting the entire system once a week and storing the drive offsite.

---

### Post by dodgyphil on 2011-05-03
Well on another question how big should my system partition be?

Cheers
Phil D

---

### Post by tgalati4 on 2011-05-05
15 to 30 gb depending on how many services you are running.

---

