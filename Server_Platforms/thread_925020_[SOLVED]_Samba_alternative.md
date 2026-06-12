---
title: "[SOLVED] Samba alternative"
date: 2008-09-20
forum: Server Platforms
---

### Post by griz on 2008-09-20
Hi,
I'm running 8.04 server, command line only, with Seagate external HDD attached.  External drive is NTFS format which I'm not in a position to change.  I want to be able to access the external HDD with full read/write permissions from computers in my local network, 1 x Windows XP and 1 x Ubuntu 8.04 with Gnome.  External HDD will not work on NFS transfer (probably because of the file system), so Samba should have been the best alternative.  Problem is, keep getting the dreaded "error 13" message.  Tried as many different configuration options, and still no go.  Did get it working at one point, but when I restarted my Linux laptop, wasn't working again.  So, is there a viable alternative to Samba that doesn't need a gui?  Preferably something that's in the repositories, please.

Ok, problem solved.  Seems that, for some reason, the password on the server didn't save.  Reset it and now everything seems fine.

---

