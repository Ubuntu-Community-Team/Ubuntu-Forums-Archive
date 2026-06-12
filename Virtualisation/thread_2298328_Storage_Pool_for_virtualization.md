---
title: "Storage Pool for virtualization"
date: 2015-10-10
forum: Virtualisation
---

### Post by br.dai2008 on 2015-10-10
Hello

We have 4 hosts with 3 disks of 1TB each

We have setup software RAID and grouped those disks together on each machine. On top of software Raid, we setup LVM with one single LV.

Our question now is, is there a way to group the 12 disks together? (3 disks of 1TB x 4 machines)?

Is clvm supposed to do that or is there another way?

Thanks in advance

---

### Post by TheFu on 2015-10-10
Some options: [http://docs.openstack.org/openstack-ops/content/storage_decision.html](http://docs.openstack.org/openstack-ops/content/storage_decision.html)
Sheepdog and swift are where I would begin.

---

### Post by Skaperen on 2015-10-11
or *nbd*: [http://nbd.sourceforge.net/](http://nbd.sourceforge.net/)

this can bring block devices over the network.  hopefully (i have never tried this step) you can combine them with LVM or other means.  if LVM does not like the NBD devices, do LVM on the guest OS.

---

