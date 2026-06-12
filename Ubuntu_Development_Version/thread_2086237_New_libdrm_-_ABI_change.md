---
title: "New libdrm - ABI change"
date: 2012-11-20
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-11-20
The new libdrm (2.4.40-1) brings a an ABI change to nouveau.
We used to have libdrm-nouveau1a, now it is libdrm-nouveau2.

However, the old version of libdrm-nouveau1a (2.4.39-0ubuntu1) cannot be removed now yet (nor updated - there is no libdrm-nouveau1a anymore).
You see, plymouth depends on libdrm-nouveau1a.

---

### Post by jppr on 2012-11-20
Don´t works with 3.7 kernel... I still have the same problem with the 3.7 kernel doesn´t work at all ... :( System don´t boot...

---

### Post by ronacc on 2012-11-20
I am showing libdrm-nouveau-1a still available and installed here as well as 
libdrm-nouveau-2  . but as jppr noted 3.7 kernel still no boot .

---

### Post by dino99 on 2012-11-20
since libdrm upgrade, i've rebooted without issue here on RR i386 and "nouveau" & 3.7 rc6

---

### Post by Harry33 on 2012-11-20
> **ronacc said:**
> I am showing libdrm-nouveau-1a still available and installed here as well as 
libdrm-nouveau-2  . but as jppr noted 3.7 kernel still no boot .

Yes of course it is available. Otherwise the system would be broken, because of plymouth dependency issue.

I was just saying two things here:

1) libdrm-nouveau1a will not be updated anymore, it will stay at 2.4.39.
2) plymouth will soon be upgraded to meet this new nouveau ABI.

---

### Post by ronacc on 2012-11-20
I mis understood your OP . Thanks for the clarification .

---

### Post by Harry33 on 2012-11-23
The new plymouth package (0.8.8-0ubuntu1) solves the dependency issue.
Old libdrm-nouveau1a can now be removed.

---

