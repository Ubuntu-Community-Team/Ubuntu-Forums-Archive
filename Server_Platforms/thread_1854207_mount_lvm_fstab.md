---
title: "mount lvm fstab"
date: 2011-10-03
forum: Server Platforms
---

### Post by BillGod on 2011-10-03
I am trying to figure out how to mount an lvm partition on boot.

here is what I did 

pvcreate /dev/hdb1 /dev/hdc1
sudo vgcreate vg /dev/hdb1
sudo vgextend vg /dev/hdc1
sudo lvcreate -L250G -ndata  vg
sudo mke2fs -j /dev/vg/data
sudo mkdir /mnt/data
sudo mount /dev/vg/data /mnt/data

so it is mounted right now but how do I add it to fstab?  I tried to fdisk -l to see what drive info I needed to add to fstab but it says "Disk /dev/dm-0 doesn't contain a valid partition table"

Thanks
Bill

---

### Post by lcman on 2011-10-04
> **BillGod said:**
> I am trying to figure out how to mount an lvm partition on boot.

here is what I did 

pvcreate /dev/hdb1 /dev/hdc1
sudo vgcreate vg /dev/hdb1
sudo vgextend vg /dev/hdc1
sudo lvcreate -L250G -ndata  vg
sudo mke2fs -j /dev/vg/data
sudo mkdir /mnt/data
sudo mount /dev/vg/data /mnt/data

so it is mounted right now but how do I add it to fstab?  I tried to fdisk -l to see what drive info I needed to add to fstab but it says "Disk /dev/dm-0 doesn't contain a valid partition table"

Thanks
Bill

The vgextend command was unnecessary; you could have just included that both in the vg like that:
```
vgcreate vg /dev/hdb1 /dev/hdc1
```

sudo lvcreate -L250G -ndata  vg doesn't look right. It should be:
```
sudo lvcreate -L 250GB -n data vg
```

You didn't specify fs type in mke2fs, so, maybe you needed the ext2 partition but if you didn't, you should specify either ext3 or ext4.

Now to mount the drive at boot. i'm assuming you want to mount it at /mnt/data:
```
vi /etc/fstab
```

Add the following line at the bottom:
```
/dev/vg/data /mnt/data ext2 defaults 0 1
```

Reboot and it should be there.

---

