---
title: "Can I importvg/access AIX disk from a Ubuntu server?"
date: 2020-03-26
forum: Server Platforms
---

### Post by svangipuram on 2020-03-26
Hello,
I have a disk which was on AIX server (SAN disk with VG,LV and FS created and data on the disk). I unattached it from AIX and attached it to Ubuntu 19 server.  This is a non-bootdisk. How can I import the volume group and mount filesysytems so that I can access data from my Linux server?
I do not want to do NFS or Samba for now.


Thanks
-Raj

---

### Post by TheFu on 2020-03-26
Haven't touched AIX in 20 yrs, but i wouldn't assume AIX LVM to be compatible with the F/LOSS LVM.  And when i used AIX, the normal FS was JFS.  Can't hurt to try, but I'd have very low expectations In It working at all.  I wouldn't force anything.  Really, the best optIon would be to connect up to the AIX machine, Import the PE/VG and use **rsync** to move the data.

---

### Post by svangipuram on 2020-03-27
Thanks for the response The Fu. Tried to importvg and it doesnt throw any output. Also tried to add directly to fstab with jfs and also tried with ext4 but it sayd wrong fs type and bad superblock. And of course cfdsik shows "aix signature on the disk". Looks like only option is to attach it to AIX machine. Thanks again for your inputs.

---

### Post by TheFu on 2020-03-27
On Linux, the command to scan for LVs is **vgchange -ay**.  That would make the dm-mapper create VG and LV devices.
After that, you need to see if any where uncovered.  The command that I&#8217;d use:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Why would ext4 work on AiX?

But again, Unix isn't Linux - so i seriously doubt the LVM objects will be recognized.

---

### Post by svangipuram on 2020-03-27
Tried vgchange -ay but no luck. Was trying all FS types in fstab but yes if it would have worked then it would be JFS and not other fs types.

---

### Post by slickymaster on 2020-03-27
Thread moved to **Server Platforms** for a better fit

---

