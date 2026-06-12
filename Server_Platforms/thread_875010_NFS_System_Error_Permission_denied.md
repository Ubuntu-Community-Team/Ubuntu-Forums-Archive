---
title: "NFS: System Error: Permission denied"
date: 2008-07-30
forum: Server Platforms
---

### Post by oavicena on 2008-07-30
Hi there, this is my first post, I hope not to break any rule.
My problem is that I can't mount an NFS exported folder on a ubuntu 8.04 server edition from a 8.04 normal edition (desktop edition). The message I get is:
```
mount.nfs: mount to NFS server '192.168.2.5' failed: System Error: Permission denied
```

**Ubuntu 8.04 server edition:**
IP 192.168.2.5
Installed nfs-kernel-server, nfs-common, portmap
/etc/exports file includes:
/home/borja/files 192.168.2.4/255.255.255.0(rw,no_root_squash,async,no_subtree_check)

The folder files belongs to the user borja on server, an its permissions are 775

I have already done:
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a

Becoming desperate:
sudo reboot

**Ubuntu 8.04 desktop edition:**
IP 192.168.2.4
Installed nfs-common, portmap
Content of /etc/fstab:
192.168.2.5:/home/borja/files /home/borja/.server nfs defaults,rw 0 0

The folder /home/borja/.server DOES exists, and it belongs to the user borja on desktop.
First, it try sudo mount -a and I get the above error
Reboot, re-everything... and still the error

I can't see the problem. I have done research in google, ubuntuforums, etc.
Help appreciated.
Borja

---

