---
title: "Trouble Finding Second Hard Drive"
date: 2007-05-25
forum: Server Platforms
---

### Post by ryharv on 2007-05-25
Hello all,

I'm using Ubuntu Server 7.04.

I have two hard drives in my machine, and Ubuntu is installed on the "master" drive.  When I boot up, I can't locate the "slave" drive.  I've verified that it's connected to the interface cable and the power cable inside the box.  I'd expect it to automatically mount to /mnt or /media upon bootup, but I can't find it anywhere there.  Any ideas?  I'm sure there's a simple solution I'm missing.

---

### Post by psusi on 2007-05-25
Hard drives are not automatically mounted.  You will need to find it and set it to be mounted.  Paste the output of:

```
sudo fdisk -l
```

---

