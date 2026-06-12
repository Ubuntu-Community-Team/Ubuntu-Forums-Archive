---
title: "Can't copy 4.3 gigabyte iso to usb."
date: 2017-04-10
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-04-10
With only 2 seconds left to finishing copying I get a splicing error when copying the iso file.  The usb is a 16 gigabyte sandisk cruzer 3.0.  Any know issues in ubuntu 17.04 or is this normal.

Henry

---

### Post by SeijiSensei on 2017-04-10
What format is on the SanDisk?  It needs to be either NTFS or ext[34] to avoid limitations on file sizes.  Most USB devices are formatted as FAT32 from the factory which cannot accommodate a single fiie of that size.

You can format the device from the command prompt with
```
sudo mkfs -t ntfs /dev/sdb1
```
or
```
sudo mkfs -t ext4 /dev/sdb1
```
assuming that you only have one hard drive in your system.  If you have more, remove the device from the USB port, open a terminal and run the command
```
tail -f /var/log/syslog
```
the plug the device back in.  That log file will report what it is named.

---

### Post by Hewjr100 on 2017-04-10
You got me, it's formatted fat 32 forgot to check that.  Ok will follow instructions for formatting to ext NTFS.

Henry

---

