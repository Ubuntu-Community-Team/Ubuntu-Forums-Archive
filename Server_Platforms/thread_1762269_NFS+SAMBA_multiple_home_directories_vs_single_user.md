---
title: "NFS+SAMBA multiple home directories vs single user workstations"
date: 2011-05-19
forum: Server Platforms
---

### Post by PryGuy on 2011-05-19
Good day, everyone!

I have a server that has multiple home folders accessible via NFS and Samba. I have to share them twice because I have Windows and Ubuntu clients in my network. It's okay when I register via Samba, the share asks for a password... well, you know the rest, but I run into problems while trying to export it via NFS.

The problem is that as we know NFS works with UID:GID and not the names. So let's say I have a sysadmin accout (UID/GID=1000) of server and regular user accounts (UID/GID=1001 and higher), but I have a single user on my workstation (UID/GID=1000) so when I try to mount share as rw i get ro only (as folder permissions are 755). What is the most flexible way in such a situation? Do not really want to mess with UIDs on my workstations.

Thank you for your answers!

---

