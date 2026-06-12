---
title: "vsftpd &quot;chroot_local_user=YES&quot; disables all user connections"
date: 2013-08-12
forum: Server Platforms
---

### Post by beetlejelly on 2013-08-12
I would like to setup vsftpd so that each user can access only their own folder.
I have installed vsftpd and created a number of users using the "adduser" command. When a users connects via FTP, they have access to the entire system.
If I enable "chroot_local_user=YES" then no users can connect to the server at all.
I am runnung Ubuntu 12.04.2 LTS.

---

### Post by soapbox1984 on 2013-08-27
I am having similar issues. I have tried three different workarounds from various online tutorials with no luck.

---

