---
title: "Replacing a failed RAID5 drive?"
date: 2010-12-06
forum: Server Platforms
---

### Post by James78 on 2010-12-06
As the title says, I have a failed RAID5 hard drive. What's the easiest way I can go by replacing it? I've seen many ways to do this, but I would like to know what other people are saying about this, and see how you would do it. Thanks! ;)

P.S. This is the one I found.
[http://www.ehow.com/how_7442644_replace-linux-software-raid-drive.html](http://www.ehow.com/how_7442644_replace-linux-software-raid-drive.html)

---

### Post by rubylaser on 2010-12-07
It would help if you paste in the output of
```
cat /proc/mdstat
``` and 
```
sudo mdadm --detail --scan
```

But, here are the steps to replace a disk...
First fail the disk
```
sudo mdadm --manage /dev/md0 --fail /dev/sdb1
```
Then, remove it from the array
```
sudo mdadm --manage /dev/md0 --remove /dev/sdb1
```

Then, replace it with a new one...
```
sudo mdadm --manage /dev/md0 --add /dev/sdb1
```

If the disk is not available anymore, you can just fdisk the new drive for linux raid and then add it to the array with the last command I gave above, and mdadm will add it in, and start to resync the array.  Hope that helps.

---

### Post by James78 on 2010-12-07
Thanks.... Ya, you're right, I should've included some drive output information. I'll try to get to that sometime soon! ;)

---

### Post by James78 on 2010-12-09
Turned out the drive hadn't failed afterall. I took it out and checked it with my computer and there was nothing wrong. So I simply re-added it back to the RAID and it's resyncing right now. False alarm I guess. I wonder how/why it got removed though.

---

### Post by bio_amateur on 2012-07-04
Hi, 
   My raid5 has a failed disk. After remove this failed disk and replace with a new one. I cannot add it to the array. The reason is that this new disk doesn't have the same UUID with the two other disk, or it doesn't have the superblock. 

mdadm --assemble /dev/md1 /dev/sda /dev/sdb /dev/sdc
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has no superblock - assembly aborted

   How can I make this new disk the same format with the two other disk

Thanks,

---

### Post by rubylaser on 2012-07-04
> **bio_amateur said:**
> Hi, 
   My raid5 has a failed disk. After remove this failed disk and replace with a new one. I cannot add it to the array. The reason is that this new disk doesn't have the same UUID with the two other disk, or it doesn't have the superblock. 

mdadm --assemble /dev/md1 /dev/sda /dev/sdb /dev/sdc
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has no superblock - assembly aborted

   How can I make this new disk the same format with the two other disk

Thanks,

It would have been better to create your own thread, but I will answer you here.  The assemble process you are trying is not the correct way to do this.
```
mdadm --manage /dev/md1 --add /dev/sdc
```

This should cause a resync. Once it's all done, you should be ready to go.

---

