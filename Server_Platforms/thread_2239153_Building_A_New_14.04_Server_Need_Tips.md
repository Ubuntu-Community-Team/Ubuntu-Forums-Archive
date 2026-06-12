---
title: "Building A New 14.04 Server Need Tips"
date: 2014-08-12
forum: Server Platforms
---

### Post by smuggly on 2014-08-12
I'm gonna build a mini server with a new AM1 AMD 25 watt Soc.
I would like to put the new server on a SSD but was wondering about LVM options. Im gonna use to start 2 2TB drives.
Also a partition scheme any Ideas, /home on a seperate partition?
does LVM use the remaining space from sda?
Please any7 Tips from someone running 14.04 would be great.

Thanks Tom

---

### Post by TheFu on 2014-08-12
I haven't noticed any changes to LVM in 14.04 vs 12.04.  What you already know applies.

Should you have a separate /home?  I do, but there are times when it might not be worth the effort.  On a physical install, I would. It is only for VMs that I wouldn't bother most of the time.

The only time I've had massive data loss was when using LVM to span 3 physical disks into 1 partition.  1 disk failed - lost all the data on all 3 HDDs.  Be certain you have excellent backups regardless.

---

### Post by nerdtron on 2014-08-12
LVM - good but if you don't plan on adding any drives in the near future, then why bother using it?
I'm more concern on your RAID configuration (at least RAID1) and your backup routines.

Separate /home partition? why? For what use? If you have mysql database, better to separate the partition for /var/lib/mysql
And what's the advantage of having a separate partition than just having a large / partition for everthing? It is still a single drive which is a single point of failure.

---

### Post by smuggly on 2014-08-12
Thanks for the tips. I would appreciate any more ideas Thanks Tom

PS Should I maybe just install a Xubuntu say And Share drives instead? Its for a media server only? Thanks Tom

---

### Post by nerdtron on 2014-08-13
Why Xubuntu on a server?

Anyway the GUI is still fine. What type of media files are you going to share? 
If clients will be a mix of windows and/or linux machines, then setting up SAMBA on the sever can be an easy way.
If clients are purely linux, setting up NFS on the server is even more easier.

---

### Post by mastablasta on 2014-08-15
if it will be media server look at xbmcbuntu or something like that. or OpenElec. for media server only you don't need most of standard server stuff installed.depends really what the server will be doing.once you install such a server you can then control it with TV remote control and via SSH connection (if there is a need for any changes to be done to it's setup).

---

