---
title: "Home server NAS - Do I need LVM now that RAID5 can be resized?"
date: 2011-05-17
forum: Server Platforms
---

### Post by ShiftyPowers on 2011-05-17
I'm setting up my new home server (torrentbox, photos backup, AirMediaServer, etc.) and I'm setting up a RAID5 array.  Now I know that LVM has lots of benefits for partitioning and creating individual partitions within a large volume.  However, in my case, I simply want one large array called "HomeHUB" or something like that.  

My question is that now that RAID5 can be expanded when adding new drives, is it still a good idea to use LVM or is that just adding a layer of complexity to the equation?

---

### Post by rubylaser on 2011-05-17
I personally just use mdadm for resizing.  LVM is very powerful, but it's one more layer to troubleshoot if you have problems, and if the only reason you want it is resizing an existing array, mdadm has you covered there.

---

### Post by ShiftyPowers on 2011-05-17
my thoughts exactly.  just wanted to make sure there wasn't any other big benefits of LVM2 that I could be missing.

---

### Post by rubylaser on 2011-05-17
I would use LVM on top of mdadm for virtualization (snapshots of running VMs) and iSCSI to prevent huge file images but that's about it.

---

### Post by ShiftyPowers on 2011-05-17
yeah but for a home server use where you just want one large bucket then it's not really necessary.  Can mdadm shrink arrays btw?

---

### Post by rubylaser on 2011-05-17
You can shrink the size that it uses by using a combination of resize2fs and mdadm with the --grow and --size options, but I've never tried to reduce the number of disks in an existing array.

Although [COLOR="Red"]I've not tested it[/COLOR], this might work for reducing the number of disks (in this example going from 5 disks to 4...
```
mdadm --grow /dev/md0 --array-size=500GB
mdadm --grow /dev/md0 --raid-devices 4 --backup=/root/backup
```
You'll want to make certain that all of your data fits inside the --array-size value that you pass, or you WILL lose data.

---

### Post by ShiftyPowers on 2011-05-17
gotcha.  reducing disks in the array would be <5% chance occurrence anyway :)

---

