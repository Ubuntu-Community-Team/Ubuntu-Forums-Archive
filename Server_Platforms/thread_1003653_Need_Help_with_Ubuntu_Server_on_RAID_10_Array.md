---
title: "Need Help with Ubuntu Server on RAID 10 Array"
date: 2008-12-06
forum: Server Platforms
---

### Post by Jonniefive79 on 2008-12-06
I'm stuck, I think there is a simple easy answer here, but I don't know that much about linux or sys admin.

I have a RAID 10 array 4x 1 TB hdds.  I followed a [guide]("http://www.howtoforge.com/install-ubuntu-with-software-raid-10") to set this up.  I stopped after step 3 as suggested for Ubuntu Server setups.

I am trying to use this [guide]("http://www.howtoforge.net/minimal-ubuntu-8.04-server-install") to set up the server, but when I enter ```
mkfs.xfs /dev/sda2
``` I get "mkfs.xfs: cannot open /dev/sda2: Device or resource busy"

All the steps I took are in the linked guides.

Thanks,
-Jon

---

### Post by Mattventura on 2008-12-06
First, check if it is mounted. If it is mounted, and umount says it is busy, do "lsof | grep "/path/to/mount/point". Find which process has files open on the device, kill those processes, then umount it.

If it is still busy, or it was not mounted, try "lsof | grep "/dev/sda2". Kill any process that has it open.

Or, if you just want a couple of commands to do this for you, then do this:
```

mount
kill -9 `lsof | awk '/\/path\/to\/mount\/point/ {print $2}'` #skip this if it is not mounted
umount /dev/sda2
kill -9 `lsof | awk '/\/dev\/sda2/ {print $2}'`


```

---

### Post by adaptr on 2008-12-06
> **Jonniefive79 said:**
> I'm stuck, I think there is a simple easy answer here, but I don't know that much about linux or sys admin.
Or RAID.

> 
I have a RAID 10 array 4x 1 TB hdds.  I followed a [guide]("http://www.howtoforge.com/install-ubuntu-with-software-raid-10") to set this up.  I stopped after step 3 as suggested for Ubuntu Server setups.
No clue what that did, but if you successfully managed to set up some RAID partitions and activate them with mdadm then you are left with one or more /dev/md* devices.
These are the ones you will use; NEVER use the raw disk partitions directly, you WILL screw up your data.

```
mkfs.xfs /dev/md0
```

---

### Post by Jonniefive79 on 2008-12-06
Thanks

I think I figured out this problem, I had missed a step some where, I think ```
mkfs.xfs /dev/md0  

```
I did it over and got through the install, just used the first guide for RAID 10, ignored all steps from minimal server guide.

Now when I rebooted after install, grub loads then reports "error 2"

Any more ideas?


@adaptr - Thanks for pointing out my lack of RAID knowledge

---

