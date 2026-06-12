---
title: "Random Transport endpoint is not connected Message"
date: 2017-02-20
forum: Server Platforms
---

### Post by damo12 on 2017-02-20
Hi,

I have recently replaced our server and have installed a clean build of Ubuntu Server 16.04 from a USB pen drive.  The server is used as a file server set up with two additional hard drives and  one of two USB drives in use at any one time.

The two hard drives are used as the "server" and "backup" drives and the backup drive is copied to whichever USB is connected.

The fstab is:```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=1a38846b-33c4-4b43-90e2-415694426a5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=ab662096-05d9-45f7-afcd-624734172954 none            swap    sw              0       0


UUID=15C000CF33B70FB3	/media/server	ntfs	defaults,nofail	0	0
UUID=363A4F864A5D47FB	/media/backup	ntfs	nofail,defaults	0	0

UUID=8474FFAB74FF9DDC	/mnt/usb_backup_1	ntfs	defaults,nofail	0	0
UUID=DAF4F0F8F4F0D829	/mnt/usb_backup_2	ntfs	defaults,nofail	0	0

```


The backup scripts are set to check that all drives are mounted before they start using ```
mount -a
```
and unmount both USB drives on completion using ```
umount /mnt/usb_backup_1
umount /mnt/usb_backup_2
```each morning so the user can swap the USB drives over without having to log in to unmount one drive then mount the new one.


Every now and then, one of the disks seems to disappear, running "df -ah" gives the message```
df: /media/server: Transport endpoint is not connected
```

with the mount point changing to which ever disk is missing.  There does not seem to be a pattern as to which disk this happens to or when it will happen.

Sometimes I can unmount the disk and then remount it but often the only way to resolve this is to reboot the server.

Google searches seem to point to this being a Fuse or Fuser error but as far as I am aware, I am not using either of these.

Any help would be greatly appreciated.

---

### Post by cariboo on 2017-02-20
Closed duplicate thread.

---

