---
title: "RAID 0 With Different Drives"
date: 2010-01-26
forum: Server Platforms
---

### Post by fiveironfrnzy08 on 2010-01-26
Hello all,

I have two drive on my Ubuntu server. I have a 40GB IDE 5400RPM and an 80GB SATA 7200RPM. 

Is it at all possible to RAID 0 the two of these drive? I know it's pretty unorthodox, but it's what I've got without having to buy anything.

If so, what are the limits, cons, and/or potential pros of doing a RAID of these two?

Thank you!

---

### Post by inobe on 2010-01-26
set it up in the raid bios and try, if anything you will get an error.

personally i never tried an array with different models and capacity.

---

### Post by lukeiamyourfather on 2010-01-26
It will work if you make a software RAID in Linux but will be limited to the capacity of the smallest drive for each drive in the array. So with a 40GB drive and an 80GB drive, the total array would be 80GB (40*2) since the smallest drive is 40GB. Also with one being a slower drive, everything will be waiting on the slowest drive. Probably a good idea to not use RAID in your situation. Cheers!

---

### Post by fiveironfrnzy08 on 2010-01-26
Thank you very much for your replies!

> It will work if you make a software RAID in Linux but will be limited to the capacity of the smallest drive for each drive in the array. So with a 40GB drive and an 80GB drive, the total array would be 80GB (40*2) since the smallest drive is 40GB. Also with one being a slower drive, everything will be waiting on the slowest drive. Probably a good idea to not use RAID in your situation. Cheers!

Couldn't a raid of these two still be faster than the 80GB 7200 on it's own though? For what I'm using the server for I wouldn't care about the loss of space, I'm just wondering if I could make anything faster by using a RAID.

---

### Post by cascade9 on 2010-01-26
Almost certainly not. 

I agree with lukeiamyourfather, RAID is probably not a good idea for your hardware.

---

### Post by Xianath on 2010-01-26
Also consider that a 40G and an 80G drive are probably five years old and thus quite unreliable. If the chance of one drive failing in the next year is, say, 10%, with RAID0 the chance of losing data in the next year will be 19%, which is probably unacceptable for whatever you have in mind.

Regards,
Peter

---

### Post by ian dobson on 2010-01-26
Hi,

I have 1 raid 0 array (1Tb and a 2Tb drive) I only use it for backups so it's not that important.

All I did was create a 1Tb partition on the 1Tb drive and 2 1Tb partitions on the 2Tb drive. Then told mdadm to create a raid0 array with 3 devices (/dev/sde1 /dev/sdf1 /dev/sde2) where sde is the 2Tb drive.

I wouldn't recommend this for normal use. But in my case it's just for a backup that I can remove from the server and store elsewhere. Only having one mount point (/dev/md2) makes the backup system much easier to handle.

Regards
Ian Dobson

---

### Post by lukeiamyourfather on 2010-01-26
> **ian dobson said:**
> Hi,

I have 1 raid 0 array (1Tb and a 2Tb drive) I only use it for backups so it's not that important.

All I did was create a 1Tb partition on the 1Tb drive and 2 1Tb partitions on the 2Tb drive. Then told mdadm to create a raid0 array with 3 devices (/dev/sde1 /dev/sdf1 /dev/sde2) where sde is the 2Tb drive.

I wouldn't recommend this for normal use. But in my case it's just for a backup that I can remove from the server and store elsewhere. Only having one mount point (/dev/md2) makes the backup system much easier to handle.

Regards
Ian Dobson

That's all kinds of wrong, I wouldn't do this. :-s

---

### Post by ian dobson on 2010-01-27
> **lukeiamyourfather said:**
> That's all kinds of wrong, I wouldn't do this. :-s

Wow that's a really usfull answer. If you said why then maybe it would be worth the bits and bytes used.

As I said "I wouldn't recommend this for normal use." but in my case it was the easiest solution. When the backup is finished I just remove the box with the 2 harddisks and put it in the safe. We do differential backups every day but every so often I do a full backup.

Regards
Ian Dobson

---

### Post by lukeiamyourfather on 2010-01-27
> **ian dobson said:**
> Wow that's a really usfull answer. If you said why then maybe it would be worth the bits and bytes used.

As I said "I wouldn't recommend this for normal use." but in my case it was the easiest solution. When the backup is finished I just remove the box with the 2 harddisks and put it in the safe. We do differential backups every day but every so often I do a full backup.

Regards
Ian Dobson

You're right, it wasn't useful. If the goal is just to get a single mount point then a spanned volume with LVM would be a better option (when one disk is full it moves on to the next seamless to the user). It would be more robust because a single disk failure doesn't mean a total volume failure, it would probably perform better because there wouldn't be any RAID calculations or latency between the disks with the abnormal RAID 0 configuration. Maybe that's more useful? Cheers!

---

