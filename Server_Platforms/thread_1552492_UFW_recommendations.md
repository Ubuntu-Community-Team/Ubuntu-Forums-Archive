---
title: "UFW recommendations"
date: 2010-08-13
forum: Server Platforms
---

### Post by bone2006 on 2010-08-13
On a server I have without any desktop environment I would like to start using ufw.   I really only have samba and ssh on one of the boxes that I would like to start using it and was wondering what is recommended?

I was planning on only opening up ssh with
$ufw enable
$ufw default deny
$ufw logging on
$ufw 22
$ufw 139

I don't know if I need to open up the samba port if it's only used on the local network and ssh i use remotely, so I know I want to open that port.

Any recommendation or suggestions is appreciated it

---

