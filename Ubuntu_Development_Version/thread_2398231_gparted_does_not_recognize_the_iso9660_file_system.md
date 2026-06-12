---
title: "gparted does not recognize the iso9660 file system in cloned Ubuntu USB boot drives"
date: 2018-08-09
forum: Ubuntu Development Version
---

### Post by mc4man on 2018-08-09
fixed in gparted some time ago, fixed in 17.10, 18.04 & 18.10 , will never be fixed in 16.04 ( maybe it could be backported if someone was inclined..

---

### Post by sudodus on 2018-08-09
> **mc4man said:**
> fixed in gparted some time ago, fixed in 17.10, 18.04 & 18.10 , will never be fixed in 16.04 ( maybe it could be backported if someone was inclined..

+1

If this is important for you, please install 18.04.1 LTS. Otherwise, live with it. In Ubuntu 16.04.x LTS you can use **lsblk**, which can recognize the iso 9660 file system

```

sudo lsblk -f
sudo lsblk -m

```

---

### Post by C.S.Cameron on 2018-08-09
If you unmount the ISO9660 partition using Disks, GParted can create a new partition table for the partition.

I usually find it quicker to use **mkusb** to fix the partition.

---

