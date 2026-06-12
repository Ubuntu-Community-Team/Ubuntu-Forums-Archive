---
title: "upgrading system drive using dd?"
date: 2010-01-18
forum: Server Platforms
---

### Post by gobbledigook on 2010-01-18
Hi!

I have just found a 120gb scsi drive which i would like to use as my system drive instead of my current 80gb scsi drive. I cannot simply plug the drive in for extra storage as i don't have a spare scsi slot! only have 2 and one is for the dvd-drive

is it ok just to dd the one onto the other? can i do this whilst the system is live? or should i use a live cd? or better still put both drives into a seperate linux box? 

its currently formatted to ext3.

oh! plus would i need to use any special switches using the dd command? or would it simply be :

```
dd if=/dev/sda of=/dev/sdb

```

sorry for lots of questions... just trying to avoid a re-install!! 

Any other suggestions? 

thanx!

---

### Post by kseise on 2010-01-18
That should do it.  Once you have the new drive cloned, you might need to resize the partitions to make use of the additional space.  dd will clone the partitions to be the same size as they currently are.

---

