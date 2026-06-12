---
title: "Choosing RAID array."
date: 2005-10-11
forum: The Cafe
---

### Post by void_false on 2005-10-11
Hey all!

I have GA-K8N-SLI motherboard and SATA HD. I want to make this HD primary and install my OS there. First I need to create RAID array. What should I choose: Striping, Mirroring, Striping+Mirroring, Spanning?
I think it should be Striping or Spanning. Is there any difference if I have only one HD installed? And will I be able to change the type later without losing all my data?
Thanks in advance.

P.S.
Google didnt help much and I'm planning to dual boot.

---

### Post by mlomker on 2005-10-11
If you only have one disk then you can't use RAID at all.  The RAID built into system boards is actually a software RAID that requires a driver (and you usually can't get one for linux).  You'll want to disable your motherboard's RAID controller and run it as a regular sata disk instead.

---

