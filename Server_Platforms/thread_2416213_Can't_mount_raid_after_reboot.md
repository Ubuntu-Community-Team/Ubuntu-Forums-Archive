---
title: "Can't mount raid after reboot"
date: 2019-04-07
forum: Server Platforms
---

### Post by mattiash on 2019-04-07
So during the night my new Ubuntu server has been busy building the RAID 6 array with 8 2TB disks.
It went well no errors, so I saved it to mdadm.config and fstab. Mounted it, I did see it with df -h.
I had to restart to get the backup disk visible, so I did, now all I see is this:
mount /dev/md0 /mnt/storage/
mount: /mnt/storage: can't read superblock on /dev/md0

What to do?

---

### Post by darkod on 2019-04-07
Try to get the details if the raid is assembled first. What is the output of:
```
cat /proc/mdstat
sudo mdadm -D /dev/md0
```

---

