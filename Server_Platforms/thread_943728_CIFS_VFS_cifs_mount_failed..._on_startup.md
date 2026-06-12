---
title: "CIFS VFS: cifs_mount failed... on startup"
date: 2008-10-10
forum: Server Platforms
---

### Post by lazyart on 2008-10-10
When I start up my mail server I keep finding this message, which ultimately slows down the startup process:

```
CIFS VFS: cifs_mount failed w/return code = -6

```
I don't have anything in /etc/fstab that would suggest a connection to a Windows share.  Where else would I look to find the source of this issue?  It causes a serious hang (in minutes) in the boot process.

---

