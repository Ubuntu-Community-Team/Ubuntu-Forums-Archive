---
title: "linux-ntfs vs ntfs-3g"
date: 2008-11-16
forum: The Cafe
---

### Post by ShirishAg75 on 2008-11-16
Hi all, 
 I would like to know people's viewpoints (specifically filesystem folks) about the performance and reliability of linux-ntfs vs ntfs-3g. 

I read an interesting thread (a mini flame-war) about the two of them at [linux-ntfs forum ]("http://forum.linux-ntfs.org/viewtopic.php?t=741")

From the thread the following differences I could make out 

a. Linux-ntfs (some part of it) has been integrated in the kernel. 
b. NTFS-3g started life as a fork of linux-ntfs
c. NTFS-3g has been more widely known (I know about this) and perhaps tested as well (Dunno really)

So my questions are :-

a. Does it make sense to install both ntfsprogs as well as ntfs-3g or just use one or the other?

b. Which of the two is more reliable, better maintained and has more features ?

c. Which of the two projects people perceive as making grounds in the near and medium future?

---

### Post by happysmileman on 2008-11-16
ntfs-3g has generally been more feature-packed than linux-ntfs AFAIK, ntfs-3g offered full write support long before linux-ntfs for example, I'd say it's more widely tested and used because of the amount of people who switched to it early on because of this

---

### Post by Phreaker on 2008-11-16
AFAIK ntfs-3g is more widely used.

---

### Post by jdong on 2008-11-16
ntfs-3g is the preferred driver -- it's derived off the linux-ntfs codebase and has a larger userbase. It's also the only driver that supports write access to NTFS safely -- linux-ntfs has much more restrictions on how files may be written to.


However, you still need ntfsprogs even if you use ntfs-3g, as the filesystem information query tools, resize, creation, etc tools are a part of ntfsprogs, not ntfs-3g. Also, linux-ntfs natively mounts via the kernel while ntfs-3g requires FUSE. This also MIGHT mean linux-ntfs for reading NTFS has faster performance.

---

### Post by sdowney717 on 2008-11-16
I have trouble with large files writing to NTFS. It is very slow.

---

