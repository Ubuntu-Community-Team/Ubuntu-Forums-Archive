---
title: "viewing contetns of other partitioned hard disk"
date: 2009-12-16
forum: Ubuntu One (CLOSED)
---

### Post by manoj_bamania on 2009-12-16
i have installed ubuntu 9.04 and xp on my laptop, i have two drives c and d and ubuntu is installed on c when i am in ubuntu i can see the contents of my d drive but not my c drive. can someone help me on this............thanks

---

### Post by bruno9779 on 2009-12-16
C? D?

It does not work like that in ubuntu

what you call C, I suppose is sda1 (or sda(some-other-number))
everything in / is likely to be on that.

What you call D is probably sdb1 (or sdb(some-other-number))

---

### Post by manoj_bamania on 2009-12-22
how do i see the contents

---

### Post by drs305 on 2009-12-22
The easiest way to set up viewing Windows partitions is to use the NTFS configuration tool.

Download:
```

sudo apt-get install ntfs-config

```

Run:
System, Admininstration, NTFS Configuration Tool.

It will ask you the name you want for the mountpoint and that mountpoint will be in /media. Enable it to write to the partition, and it will set up fstab for you so you can access your Windows partition.

---

