---
title: "restoring backup from an LVM Guest OS on KVM Lucid"
date: 2010-09-29
forum: Virtualisation
---

### Post by tapas_mishra on 2010-09-29
I have a Ubuntu 64 bit 10.04 instance running.KVM is used for virtualization.
4 Guest Operating Systems are running on it.
I created 4 lvms after installing the Host OS.
I have a volume group nintendo which have four lvms 
as
```

lvscan
  ACTIVE    '/dev/nintendo/lvm1' [100.00 GiB] inherit
  ACTIVE    '/dev/nintendo/lvm2' [150.00 GiB] inherit
  ACTIVE    '/dev/nintendo/lvm3' [50.00 GiB] inherit
  ACTIVE     '/dev/nintendo/lvm4' [100.00 GiB] inherit

```but in the above 4 lvms I did not created swap partitions.
These things were taken care via virt-manager when I installed the guest OS.
So when I took backup I did not took backup of swap paritions.
I have the complete directory structure from lvm1 which I took the backup.
If I have to replace one of the lvm with the original backup then is just copying the complete directory structure going to work.
Or there is some elegant way to do this?

---

