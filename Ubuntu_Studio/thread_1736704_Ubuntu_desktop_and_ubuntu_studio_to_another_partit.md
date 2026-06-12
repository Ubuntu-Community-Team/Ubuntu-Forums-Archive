---
title: "Ubuntu desktop and ubuntu studio to another partition"
date: 2011-04-22
forum: Ubuntu Studio
---

### Post by vfafou on 2011-04-22
Hello!
I face the following problem: I have ubuntu desktop as primary installation. I need to install a clean ubuntu studio to another partition but I don't want to lose my existing installation. Does the studio installer make the things correct or I will face problems?
Thank you in advance.

---

### Post by jejeman on 2011-04-22
I wouldn't trust the instaler, so you need to manualy specify the partition, for /, /home or whatever you want. Swap can be the same.

---

### Post by sgx on 2011-04-23
> **vfafou said:**
> Hello!
I face the following problem: I have ubuntu desktop as primary installation. I need to install a clean ubuntu studio to another partition but I don't want to lose my existing installation. Does the studio installer make the things correct or I will face problems?
Thank you in advance.
Do you have the new partitions created yet? If not, you can use
the partitioning tool to resize the main partition, so it must have enough free space to make a worthwhile studio. Time for movies! ;)

[http://ubuntuvideotutorials.org/install-ubuntu/guide-to-partitioning/](http://ubuntuvideotutorials.org/install-ubuntu/guide-to-partitioning/)

So a 160 gig disk
with 40 gig free, should be plenty. The resizing will also require
a base amount of free disk space, in which to manipulate files during the resizing. Do a thorough backup, in any case, so nothing of value
can be lost. 

4 to 10 gig for the root partition, and the balance for /home.
Cheers

---

