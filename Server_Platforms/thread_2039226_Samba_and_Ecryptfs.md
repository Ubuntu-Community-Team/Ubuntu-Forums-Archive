---
title: "Samba and Ecryptfs"
date: 2012-08-08
forum: Server Platforms
---

### Post by hulk1st on 2012-08-08
Hi there,

I've been setting up a brand new 12.04 ubuntu server, where I set up samba as a primary domain controller. Because I set up all the accounts encrypted using ecryptfs (--encrypt-home option in adduser), every user need to open up a shell in order to mount their home directories. So this of course means when accessing a home folder via a samba share, an active ssh connection is required in order to be able to read/write files.

Is there a way to automatically run ecryptfs-mount-private when loggin in onto a windows machine and ecryptfs-umount-private when logging off, using the credentials provided when prompted at the login screen? Something like a startup and shutdown script or some parameters in appropriate shares section smb.conf?

Thanks a lot in advance,
hulk1st

---

