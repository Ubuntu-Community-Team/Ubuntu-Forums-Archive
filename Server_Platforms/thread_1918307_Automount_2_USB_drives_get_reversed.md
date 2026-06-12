---
title: "Automount 2 USB drives get reversed"
date: 2012-01-31
forum: Server Platforms
---

### Post by dandenton on 2012-01-31
I am running Ubuntu Server 11.10 and have connected 2 USB drives. One is DATA and the other is BACKUP. I am using the following in fstab:
/dev/sdc1 /media/data ntfs-3g defaults 0 0
/dev/sdb1 /media/backup ntfs-3g defaults 0 0

then, sudo mount -a and both drives autostart with no problem. However...the drives are reversed no matter what I do. In other words, DATA reads the BACKUP drive and BACKUP reads the DATA drive. I don't understand where I've gone wrong. I have verified that indeed sdc1 is DATA and sdb1 is BACKUP. As a workaround to share these drives on my Windows machines, I have reversed them in my samba shares - not a very good solution but it is working. Any ideas?

---

### Post by redmk2 on 2012-01-31
> **dandenton said:**
> I am running Ubuntu Server 11.10 and have connected 2 USB drives. One is DATA and the other is BACKUP. I am using the following in fstab:
/dev/sdc1 /media/data ntfs-3g defaults 0 0
/dev/sdb1 /media/backup ntfs-3g defaults 0 0

then, sudo mount -a and both drives autostart with no problem. However...the drives are reversed no matter what I do. In other words, DATA reads the BACKUP drive and BACKUP reads the DATA drive. I don't understand where I've gone wrong. I have verified that indeed sdc1 is DATA and sdb1 is BACKUP. As a workaround to share these drives on my Windows machines, I have reversed them in my samba shares - not a very good solution but it is working. Any ideas?

Use UUID's for consistent identification.  Linux arbitrarily assigns /dev/sdx to whatever it enumerates first and that can change.

You can see the UUID for all partitions like this```
sudo blkid
```

Substitute  the UUID for /dev/sdx when mounting the partition.

---

### Post by dandenton on 2012-01-31
> **redmk2 said:**
> Use UUID's for consistent identification.  Linux arbitrarily assigns /dev/sdx to whatever it enumerates first and that can change.

You can see the UUID for all partitions like this```
sudo blkid
```

Substitute  the UUID for /dev/sdx when mounting the partition.

Excellent, thank you very much.

---

