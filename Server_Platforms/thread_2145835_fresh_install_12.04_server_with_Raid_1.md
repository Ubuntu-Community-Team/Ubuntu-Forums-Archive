---
title: "fresh install 12.04 server with Raid 1"
date: 2013-05-16
forum: Server Platforms
---

### Post by ganewbie on 2013-05-16
Hello,
I am trying to install 12.04 fresh on a dell R320 server, the RAM is 24 GB
The two 1TB hard drives shall be configured as RAID 1. and that is my trouble. 

Here is the first step: [ATTACH=CONFIG]242654[/ATTACH]

Now when I go here to create MD, I see only three drives.
[ATTACH=CONFIG]242655[/ATTACH]

Why I see only three partitions and not 4, and how do I move forward from here?

---

### Post by Vegan on 2013-05-16
Unless you have hardware RAID, I suggest using 1 disk for the server and the other for backups

clonezilla can make a clone 

running from a cron script will make an automatic backup

works for me

---

### Post by ganewbie on 2013-05-16
Thanks for the quick response,
So, DO I take it as no way I can do a software Raid 1?!

---

### Post by darkod on 2013-05-16
Of course you can, and you should. mdadm is often much better and more flexible than HW raid. Not always much better but definitely more flexible.

It's strange it's not showing sda1. Maybe it already has a superblock from an earlier attempt?

Have you tried writing a new partition table on sda and creating new partitions? See if that helps.

---

### Post by ganewbie on 2013-05-16
Thanks, it looks like there is a light at the end of the tunnel.
I had couple of earlier attempt and it could be superBlocked as you mentioned (although I do not know what it means as this is my first attempt to setup a server with Raid), can you please point me to where do I get info top solve this, please be awar that there is nothing installed yet on this machine. But I can remove the HD and connect them to a desktop if needed.

---

### Post by ganewbie on 2013-05-17
I would appreciate if someone can let me know how to make the two hard drives as brand new again. I need to setup the server ASAP. I am assuming it should be easy as I have no data to worry about.

---

### Post by darkod on 2013-05-17
Try writing new blank partition tables. When at the partitioning step of the server installer (the image you posted above), select the hdd (like /dev/sda and /dev/sdb) and hit Enter. It will ask you if you want to write new partition table. Confirm.

That will make brand new partition tables, and you can create new partitions.

See if it will allow you to create the mdadm arrays you need then.

Also, does this server have a hardware raid card? If it does, can you set it up to simply pass through the disks? Because for mdadm you shouldn't have raid configured on the HW card. The OS should see the disks as plain disks without any fakeraid or HW raid.

---

### Post by ganewbie on 2013-05-24
After several hours of trials, I have decided to buy new hard drive instead of the one that I have used in the begining before I start setting up RAID1.
The whole process went very smooth and I have the system up and running, although I am not sure if there is a better way to solve the problem but I am happy it has been completed.

---

### Post by mobo on 2013-06-06
Here is a wonderful walk through ofa Fresh Ubuntu server install with a two drive raid 1 setup for you to have a look at.
[http://www.youtube.com/watch?v=vQtUBp5aad8](http://www.youtube.com/watch?v=vQtUBp5aad8)

---

