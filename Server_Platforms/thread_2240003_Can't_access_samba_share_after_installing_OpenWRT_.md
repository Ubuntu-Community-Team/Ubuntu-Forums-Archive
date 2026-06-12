---
title: "Can't access samba share after installing OpenWRT on router."
date: 2014-08-17
forum: Server Platforms
---

### Post by paranoiid on 2014-08-17
Hello, having a strange problem here. I have a file server on an Ubuntu Server running samba. My router has been feeling under the weather so I decided to upgrade it to OpenWRT. After a bit of heartache I managed to get it going. Now I'm having a strange issue. I can't access the samba share there any more through Windows 8 on LAN. My Windows 7 laptop on wifi can still access the shares as normal but Windows 8 just have decided that it isn't for it. I did that net show thing in CMD and it comes up with a System Error 53. 

First I thought it was a security issue so I disabled the 128-bit required encryption and that required authentication. Then since I had an assigned IPv6 address I thought that might be the issue so I disabled all IPv6 support/tunnels on the Windows machine and still I can't access the share. I can ping the machine's netbios name, I can do pretty much anything except accessing the shared files.

This is probably more windows related than anything but asking the windows forums for technical assistance is like going to 4chan for dating advice. 

Any help whatsoever is greatly appreciated.

---

### Post by volkswagner on 2014-08-17
One thing that comes to mind. 

Windows 8 may be seeing at a new network.  Make sure it's list as home or work. For whichever type of network it's listed as, make sure file sharing is enabled.

---

### Post by paranoiid on 2014-08-17
> **volkswagner said:**
> One thing that comes to mind. 

Windows 8 may be seeing at a new network.  Make sure it's list as home or work. For whichever type of network it's listed as, make sure file sharing is enabled.

Did and done, no change.

---

