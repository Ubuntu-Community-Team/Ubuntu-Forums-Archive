---
title: "Mount systemwide"
date: 2016-04-17
forum: Security
---

### Post by jimmyh1972 on 2016-04-17
HI
Is there a way to prevent system-wide mount and to allow only a particular device to be mounted once it is attached?
like for example only a usb device will be mounted when inserted
Thanks ahead Jimmi

---

### Post by TheFu on 2016-04-17
I think you'd have to remove gvfs support and use manual mount configurations either through fstab or autofs.  Just brainstorming here.  My systems don't automount anything, but I stopping installing any desktop version of Ubuntu years ago.  If you install the server version, it isn't an issue.

---

