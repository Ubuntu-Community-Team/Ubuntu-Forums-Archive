---
title: "Mount commands in fstab isn't working"
date: 2013-08-29
forum: Ubuntu Development Version
---

### Post by P-I H on 2013-08-29
Mount commands in fstab of folders on an Ubuntu server has stopped to work.
To mount manually from the terminal works OK.
The error message, when I brows a folder in Nautilus, tells that only root is able to mount.

Mount command example:
IP.Address.to.NAS:/srv/Media/home/p-i/NASMedia nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

---

### Post by P-I H on 2013-09-03
It is working now after the fix of this bug [https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/1217610](https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/1217610)

---

