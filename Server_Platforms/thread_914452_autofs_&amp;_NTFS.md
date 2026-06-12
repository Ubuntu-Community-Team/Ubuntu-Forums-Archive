---
title: "autofs &amp; NTFS"
date: 2008-09-08
forum: Server Platforms
---

### Post by cfish on 2008-09-08
I'm trying to mount with autofs an USB NTFS Hard Drive.

Question would be has anyone ever achieved this before.  I'm finding it difficult to do.  I can mount the device manually and it works fine. I have the latest ntfs-3g package.  Whenever I autofs the NTFS HD it does however it seems that and cannot write to the device.  I have search just about everything out on google regarding this and I cannot find nothing about mounting using autofs while the drive is a NTFS device.

When I look at the syslog everything appears to be fine until I try to create a directory or a file:

mkdir:
cannot create directory `test': No such file or directory

syslog after autofs is started:
Sep  8 14:33:21 ubuntu automount[5347]: failed to mount /backups/test

mount:
automount(pid4425) on /backups type autofs (rw,fd=4,pgrp=4425,minproto=2,maxproto=4)

ls -ldt /backups:
drwxr-xr-x 2 root root 0 2008-09-08 14:37 /backups


auto.master:
/backups        /etc/auto.backups  --timeout=3

auto.backup:
backups         -fstype=ntfs-3g,gid=1002,umask=0002,async,rw    :/dev/sdb1

---

