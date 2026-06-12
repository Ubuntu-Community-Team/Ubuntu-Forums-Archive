---
title: "Need to extend disk(vmware). Silly problem"
date: 2013-06-18
forum: Virtualisation
---

### Post by Greatnesss on 2013-06-18
So I need to extend a disk for one of our ubuntu machines.
The VM has 4 disks.
The problem is, I dont know which disk is what partition.

Say that I have /med/mongoDB and /med/mongoDB-backup
Both of them are exactly the same size. 400GB.

I need to extend /med/mongoDB . How do I know, looking in Vcenter at the VM, what disk is tied to /med/mongoDB ?

Or do I have to do something stupid like, extend one of them randomly with a small amount and then see which is which? =)

Thanks in advance.

Regards
Greatness

---

### Post by TheFu on 2013-06-18
The UUID should have a mapping to the specific device that VMware shows.  **blkid** is the command or you can look under /dev/disk/by-*

Clearly, you'll need to expand the "physical disk" that is presented to the client OS in vsphere, then you'll have to use the client OS methods to access that additional storage ... which is dependent on whether LVM is used or not.  **resize2fs** is likely the command, but be certain to review the man page first, since there are all sorts of strange configurations that can cause issues.

This is the sort of information that someone building VMs should maintain in their build documentation.

---

