---
title: "LVM Snapshot not updating"
date: 2013-04-10
forum: Server Platforms
---

### Post by horizonuser on 2013-04-10
I will admit that my understanding of the following is a little hazy, however, it seems that if I create a new logical volume as follows
```
sudo lvcreate -L1G -s -n livesnapshots /dev/kvm-server/vm-storage
```

It creates successfully. I then mount this to /mnt/snapshots and sure enough I can see the file system as existing in the original volume. However (and this is where I lose things), I thought that if I make a change on the original volume that the changes should be reflected in the snapshot mount directory too - should this be the case?

Example: The volume /dev/kvm-server/vm-storage is mounted to /mnt/vmstorage and contains one file called 'base_ubuntu_12.10.qcow2'. This, in turn, is a working KVM VM. When I mount the snapshot (as above) I see this file listed in the snapshot mount too (which is to be expected). If I now call up the VM and add/remove a test file/directory I can see the original file's datestamp changes, but the mounted snapshot doesn't. If I restore the VM to the file in the mounted snapshot I can see the changes I made, while mounted, are lost. This shows the actual updates aren't being written to the snapshot.

The output of the logical volume is this:
 ```


  --- Logical volume ---
  LV Path                /dev/kvm-server/vmsnapshots
  LV Name                vmsnapshots
  VG Name                kvm-server
  LV UUID                9KKh1z-23d3-z6Tw-lPu4-Cxxy-RdPG-3dclzP
  LV Write Access        read/write
  LV Creation host, time kvm-server, 2013-04-10 14:32:27 +0100
  LV snapshot status     active destination for vm-storage
  LV Status              available
  # open                 1
  LV Size                350.00 GiB
  Current LE             89600
  COW-table size         1.00 GiB
  COW-table LE           256
  Allocated to snapshot  0.02%
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3


```

Can someone tell me how stupid I am!?

---

