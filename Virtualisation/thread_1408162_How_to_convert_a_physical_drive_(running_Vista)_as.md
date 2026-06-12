---
title: "How to convert a physical drive (running Vista) as VM to be run on KVM"
date: 2010-02-16
forum: Virtualisation
---

### Post by satimis on 2010-02-16
Hi folks,

Host - Fedora 12 64bit
Windows Vista 32bit - running another drive
KVM


$ sudo fdisk -l```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003a4bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              26      121601   976555201   8e  Linux LVM

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0883bef2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4867    39086080    7  HPFS/NTFS

Disk /dev/dm-0: 989.7 GB, 989704749056 bytes
255 heads, 63 sectors/track, 120324 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 10.3 GB, 10284433408 bytes
255 heads, 63 sectors/track, 1250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

```


I have created;

$ sudo dd if=/dev/sdb of=/home/satimis/VM/VMWIN/vm07_vista.qcow2```

78177792+0 records in
78177792+0 records out
40027029504 bytes (40 GB) copied, 1160.35 s, 34.5 MB/s

```


I haven't figured out what options will be up on running;

qemu /home/satimis/VM/VMWIN/vm07_vista.qcow2 <options>

-m 1024 ?
-soundhw all ?

etc.


Will /etc/libvirt/qemu/vm07_vista.xml be created automatically running above command?

Please shed me some light.  Pointer would be appreciated.  TIA


B.R.
satimis

---

