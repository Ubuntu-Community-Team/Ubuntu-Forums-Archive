---
title: "want to mount VHD"
date: 2015-01-28
forum: Virtualisation
---

### Post by sumangsh on 2015-01-28
Hi,
I want to mount a vhd file by tapdisk.
I ran the below command.
root@ubuntu:/dev/xen/blktap-2# tap-ctl open -m 0 -p 6685 -a vhd:/media/suman/My\ Passport1/Vdisk_System.vhd

but how do I access the vhd file now? where it will be mounted?

---

### Post by deadflowr on 2015-01-28
Moved to Virtualisation.



My guess is it is mounted at /media/suman/My\ Passport/.

---

