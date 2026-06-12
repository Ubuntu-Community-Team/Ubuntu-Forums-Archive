---
title: "NFS Client fails: mount.nfs: mount(2): No such device"
date: 2010-10-28
forum: Server Platforms
---

### Post by ezsra.mcdonald on 2010-10-28
Greetings fellow ubuntu admins.

I have built many servers but this is the first time a server didn't want to mount NFS shares for me.

OS: Ubuntu 10.10
Kernel: 2.6.35-22-virtual 64bit

Packages installed:
          nfs-common
          portmap
          nfs-kernel-server ( just because someone said it would work )

The system can't find a kernel module for the NFS client.

Attempts to mount NFS shares give the following errors:

root@host:~# mount -v -t nfs nfsServer:/some/share/name /mnt
mount.nfs: timeout set for Thu Oct 28 17:18:08 2010
mount.nfs: trying text-based options 'vers=4,addr=192.168.1.20,clientaddr=192.168.1.33'
mount.nfs: mount(2): No such device
mount.nfs: No such device

---

