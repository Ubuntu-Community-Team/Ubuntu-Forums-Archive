---
title: "MDADM, partitioning, formatting and mounting"
date: 2011-02-26
forum: Server Platforms
---

### Post by delpi767 on 2011-02-26
I am finally, and happily ditching Windows IIS,  SQL Server, and ASP in favor of LAMP.  Not only will I save a bunch of money on operating systems but I've found php and MySQL development to be much faster than their Microsoft counterparts.

Currently I have two W2008 and two Ubuntu servers running and doing virtually parallel tasks.  I want to can the W2008 machines but I am not 100% sure of my Ubuntu mirrors.

Everything seems to be working fine. I've copied tons of data back and forth as a primitive test but sometimes things work fine for all the wrong reasons. 

Here's where I get confused.

Question 1
Do I need to partition the RAID device (MD0) and then format it?
From my experience this is necessary to get the device to mount.

Question 2
In this case was it also necessary to format the individual drive partitions?

Question 3
If I do a daily cat /proc/mdstat is this all I need to do to check the drive status.

Question 4
Is there any other check I can do to assure that the mirrors are created, mounted, and operating correctly?

Thanks one and all.

Mac

---

### Post by Kljuka on 2011-02-26
Q1:
You will first create partitions on every hard drive that will be in the raid array and format them as Linux raid autodetect (fd).
Create the raid array afterwards.
Then format the array parition (mdX) to appropriate filesystem (eg.: ext4). So: Yes, you need to format it.

Q2:
See Q1

Q3:
If you plan to do it manually, OK. But I use email alert implemented into mdadm to alert me in case of disk failure. You should also check smart status of disks using smartctl (and email it to you - The configuration is in /etc/smartd.conf).

Q4:
Once in a while I check if all drives are operating correctly - all blocks have correct data in them (correct the device names):
```
echo check >> /sys/block/md0/md/sync_action
```

---

### Post by YesWeCan on 2011-02-28
Apparently, and I only found out last week, "fd linux raid autodetect" is now deprecated and does nothing. I confirmed this on my own RAID.
[https://raid.wiki.kernel.org/index.php/RAID_Boot](https://raid.wiki.kernel.org/index.php/RAID_Boot)

---

### Post by rubylaser on 2011-02-28
I see the wiki is coming in handy:)  I didn't know this either.  I'm going to want to experiment with this script, and get comfortable with it's function.

---

