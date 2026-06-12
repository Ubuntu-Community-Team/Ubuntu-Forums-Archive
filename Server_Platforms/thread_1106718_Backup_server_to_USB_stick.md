---
title: "Backup server to USB stick"
date: 2009-03-26
forum: Server Platforms
---

### Post by sswittch on 2009-03-26
Hi,

Just wondering if anyone knew of a TUT or has instructions how to backup an ubuntu 8.10 server to usb stick.  I want to create a complete image of the server and have no other PCs on that network.  I am also unable to connect another pc to that network or I would have used systemimager

Cheers.

---

### Post by warchief_ryan on 2009-03-26
You could just use dd, like ```
dd if=/dev/sda of=/dev/sdb/backup_image.img
```
/dev/sda being the servers drive and /dev/sdb being the usb drive.


To restore the server from the backup .img you'd do, ```
dd if=/dev/sdb/backup_image.img of=/dev/sda
```

Just make sure you have enough space.


You can even use the count, skip and seek options to segment the image into smaller parts if needed.

---

### Post by mrsteveman1 on 2009-03-26
> **warchief_ryan said:**
> You could just use dd, like ```
dd if=/dev/sda of=/dev/sdb/backup_image.img
```
/dev/sda being the servers drive and /dev/sdb being the usb drive.


To restore the server from the backup .img you'd do, ```
dd if=/dev/sdb/backup_image.img of=/dev/sda
```

Just make sure you have enough space.


You can even use the count, skip and seek options to segment the image into smaller parts if needed.

Just don't do that while the drive being backed up is mounted and in use, or you might get an inconsistent filesystem. There are probably better ways to do this by copying files or using LVM and cloning or making a snapshot of the filesystem but i've never done either one before. We usually only back up mysql databases and webroot directories, and sometimes configuration files, and leave the system files alone since they can be recovered easily with a reinstallation.

---

### Post by BkkBonanza on 2009-03-26
Second that. I usually use a script with tar commands that select web content, databases and other customized stuff. It would make sense to save a drive image snapshot of the system once only that you can restore quickly and then apply your latest tar backups onto. I haven't bothered because it's not hard to install fresh.

A typical tar script might be like,

```
TODAY=`date +%F`
tar -czf /var/bak/www-${TODAY}.tar.gz /var/www
... etc more the same ...
```

My script does a lot more because it also encrypts the tar file and sends it up to S3 for safe backup. It's called by cron each day.

For safe drive imaging you might look at booting on Clonezilla to image the system drive. Download and burn an iso of that or put it on a usb stick and boot off it. Booting off it means your system drive isn't in use.

---

