---
title: "Ubuntu server - Norwegian Filenames"
date: 2010-02-22
forum: Server Platforms
---

### Post by rogersaga on 2010-02-22
I've set up at server solution with Ubuntu 9.10 Server 64-bit, and have installed NFS and Samba. I have a USB disk with folders containing æøå in foldernames, when mounting this USB disk the Norwegian charaters is rubbish...
I have tried the following:

sudo mount -t ntfs-3g -o nls=utf8 /dev/sdb1 /media/usbdisk/
sudo mount -t ntfs -o iocharset=iso8859-1 /dev/sdb1 /media/usbdisk/

The USB disk is NTFS.

How to fix this?

Thanks in advance!

---

