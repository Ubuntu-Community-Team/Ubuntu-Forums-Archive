---
title: "how to cancel fsck at boot?"
date: 2010-03-22
forum: Server Platforms
---

### Post by alecz20 on 2010-03-22
Right now I am trying to fix the problems on my server with daemons not starting.

So I have to try different solutions and reboot.

The problem is that after 28 reboots, fsck kicks in and decides to check 2 TB of data.

Is there a way to cancel this???

It takes forever, and by the time it will be done, I will have forgotten what I was testing.


The issue of daemons not starting becomes even more frustrating when fsck decides that I must take a half an hour break.


So again, how do I cancel the fsck on Ubuntu Server?

---

### Post by fang0654 on 2010-03-22
```
sudo tune2fs /dev/partition -c 0
```

---

### Post by alecz20 on 2010-03-22
thanks for the reply.

However for me to see if this will work, I have to wait for the fsck to finish, and it seems it will take much more than 30 minutes.

Seems to be going on for an hour.

---

### Post by lisati on 2010-03-22
I find it frustrating at times too, since I don't like having my server down for too long if I can help it. I think there is a command or setting somewhere where you can change the frequency that fsck kicks in, but it eludes me for the moment; I usually "go with the flow" and let it run to completion, just in case there are problems I've missed.

---

### Post by alecz20 on 2010-03-22
I found out that Ctrl+Alt+Del stops it and then it continues the booting process.

The problem is that the partition that was being checked is not mounted.

This is LVM partition. The command suggested by fang did not work for that LVM partition.

I think I will have to just take a break and wait 1-2 hours until it finished checking and then hope I will fix my problem within the next 28 reboots.

---

### Post by smc18 on 2010-03-22
```
cat /etc/fstab
```

You should have Six Columns, for example:

> 
1 ---------- 2 - 3 ------ 4 --- 5 6
/dev/hda2  	/  	ext2  	defaults  	1      1

The very last column decides if the filesystem is to be checked by fsck on boot (normally after about 30 mounts).

There are three choices available:

If set to '1', this partition is to be checked first.

If set to '2', the partition will be checked after the first.
     (Multiple partitions can be marked with '2' they will be checked after the partition marked '1')

If set to '0', the partition will not be checked.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

