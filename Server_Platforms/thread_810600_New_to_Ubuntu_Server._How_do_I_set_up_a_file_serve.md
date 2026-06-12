---
title: "New to Ubuntu Server. How do I set up a file server?"
date: 2008-05-28
forum: Server Platforms
---

### Post by grs on 2008-05-28
I've just installed Ubuntu Server on a USB key to try it out before I load it onto a HDD. I want to set it up as a file server for a PC running Linux Ubuntu Studio. How do I go about this?

---

### Post by NateMan on 2008-05-28
is there any reason you wish to setup a fileserver running on ubuntu studio edition? I'd like to get a better idea of exactly what you wish to do with this box before I tell you how I would approach the situation.

---

### Post by grs on 2008-05-28
Sorry I worded that wrong. I have two PC's, the first with Ubuntu Server and the second with Ubuntu Studio. I want to set up the first as a file server which can be accessed by the first and I plan to add a third PC running MythUbuntu.

---

### Post by cdtech on 2008-05-28
Samba file and print services. Used for both GNU/Linux and Window's

---

### Post by NateMan on 2008-05-28
Gotcha, I was confused. Ok here's a nice guide, get a groundwork server setup and then from there pick which type of filesharing you need, nfs for all unix systems or samba for mixed environments. Then you can set that all up. If you need help after doing this guide then let me know, be glad to assist.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

Good luck with it!

---

### Post by grs on 2008-05-28
I tried Samba through ClarkConnect but I couldn't get it going. I didn't know NFS was for Unix/Linux.
During the installation I only selected to install one or two of the server options, how do I go about loading in the others after the main install?
I just hard quick look through that guide, I didn't notice a section on NFS.

---

### Post by NateMan on 2008-05-28
nfs is very easy to setup, it hardly needs a guide. 

However, here's an old one for 6.06 that you should be able to use most of. 
[http://ubuntu-tutorials.com/2006/10/20/network-file-system-nfs-ubuntu-606-610/](http://ubuntu-tutorials.com/2006/10/20/network-file-system-nfs-ubuntu-606-610/)

---

### Post by NateMan on 2008-05-28
The server guide is so that you have a nice running server BEFORE you go about setting up nfs. You can easily modify the guide, but basic lamp setup is a nice starting point, since many server apps with a webbased interface expect you to have this already.

---

