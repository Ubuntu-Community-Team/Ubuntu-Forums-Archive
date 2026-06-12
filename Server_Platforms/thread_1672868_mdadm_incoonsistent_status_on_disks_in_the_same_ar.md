---
title: "mdadm incoonsistent status on disks in the same array"
date: 2011-01-21
forum: Server Platforms
---

### Post by dantrevino on 2011-01-21
So, this one is new to me.  when I start my raid5, only 2 disks of 3 are active on md0.  The 3rd disk is inactive on md_d0.

When I do mdadm --examine, the two active disks report 2 active, 2 working, 1 failed.  the inactive disk resports 3 active, 3 working, 0 failed.

see here:
[http://paste.ubuntu.com/556596/](http://paste.ubuntu.com/556596/) 

Not sure how to fix this, any ideas?

tia,
dan

---

### Post by dtfinch on 2011-01-21
When I get this, it's because I forgot to add my arrays to /etc/mdadm/mdadm.conf, and mdadm autoassembly has a bug where it sometimes steals one disk to make a new offline raid md_d0, making the disk unavailable when it tries to assembly md0.

I'm a bit hurried right now, but I think you need to stop md_d0 (mdadm --stop /dev/md_d0 I think) and then retry assembling (mdadm --assemble --scan). Then you need to add your array to mdadm.conf (maybe mdadm -Es >> /etc/mdadm/mdadm.conf).

---

### Post by dantrevino on 2011-01-22
thx dtfinch.  I had checked my mdadm.conf to make sure the array was listed, but apparently I didnt check well enough.  The line was there, but with an incorrect UUID, ... a relic from a previous installation... ow

Anyway, updated the UUID in mdadm.conf, restarted md0 (--assemble --scan) and now its recovering properly.

thx!

---

