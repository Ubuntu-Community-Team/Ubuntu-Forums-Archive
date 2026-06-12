---
title: "How to resize a volume group"
date: 2009-07-26
forum: Server Platforms
---

### Post by Trollslayer on 2009-07-26
OK, I might be going about this the wrong way.
I have a system with a RAID5 array under LVM and it is happy.
I've added another RAID5 array and added it to the volume group with the resulting output for vgdisplay:
VG size           5.00 TB
PE size           4.00 MB
Total PE          1311568
Alloc PE / Size   946056 / 3.61 TB
Free  PE / Size   365512 / 1.39 TB

How do I resize this to make use of the added space without destroying my data already on the first array?
Thanks.

---

### Post by wizardry on 2009-07-27
here try this link as a how to:
[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

this link covers everything for lvm:
[http://www.linux.org/docs/ldp/howto/LVM-HOWTO/](http://www.linux.org/docs/ldp/howto/LVM-HOWTO/)

hope this helps

---

