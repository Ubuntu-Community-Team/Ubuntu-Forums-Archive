---
title: "Cannot move files between internal and external drives"
date: 2008-11-05
forum: Server Platforms
---

### Post by Chelmet on 2008-11-05
Hi, I have a dedicated server, accessed through SSH, with 250Gb hard drive. To thiis 2x 500Gb hard drives have been added.

```
 df -h -T
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    2.9G  904M  1.9G  33% /
varrun       tmpfs   1000M   84K 1000M   1% /var/run
varlock      tmpfs   1000M     0 1000M   0% /var/lock
udev         tmpfs   1000M   36K 1000M   1% /dev
devshm       tmpfs   1000M     0 1000M   0% /dev/shm
/dev/sda2     ext3    226G  226G     0 100% /home
/dev/sdb1     ext3    463G  199M  439G   1% /mnt/PHXusb
/dev/sdc1     ext3    463G  199M  439G   1% /mnt/CARDZusb

```

When I access the server through ftp, I can drop files from my computer onto these external drives. However, I don't want to move files from my computer, I want to move files off of the full drive.

```
mv "File1" "/mnt/PHXusb/File1"
mv /home/Torrents_Complete/File1 /mnt/PHXusb/File1: failure
```

Any ideas? The drives are formatted as ext3 and (I think) mounted properly. Why can I ftp in from and move a file to the drives, but not between them? Cheers.

Regards,

Chel


NOTE: The externals are both usb drives

---

### Post by nexes128 on 2008-11-05
It could be the folder permissions on /mnt/PHXusb. Try doing:
```
sudo mv "File1" "/mnt/PHXusb/File1"
```

If that works use chown and chgrp to change there permissions to your username.

```
sudo chown -R USERNAME /mnt/PHXusb
sudo chgrp -R USERNAME /mnt/PHXusb
```

---

