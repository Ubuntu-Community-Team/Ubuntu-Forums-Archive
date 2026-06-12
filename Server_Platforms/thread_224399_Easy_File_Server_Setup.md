---
title: "Easy File Server Setup"
date: 2006-07-27
forum: Server Platforms
---

### Post by srg0425 on 2006-07-27
What is the easiest way to set ubuntu up as a file server for my home network>

What wireless network adapters are compatible with ubuntu?

Thanks for your help.

---

### Post by navilon on 2006-07-28
The choice of file serving applications depends heavily on your network enviroment. Are you running a heterogeneous network? (Windows, Linux, Macintosh, etc.)

If you only have linux nodes on your network, try NFS:
Tutorial: [http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html)

On the otherhand, if you plan on 'mixing it up' a little, use SAMBA:
Tutorial: [http://www.ubuntutorial.com/?p=5](http://www.ubuntutorial.com/?p=5)

---

