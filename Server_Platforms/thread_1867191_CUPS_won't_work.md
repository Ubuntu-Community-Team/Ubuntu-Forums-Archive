---
title: "CUPS won't work"
date: 2011-10-22
forum: Server Platforms
---

### Post by Howy on 2011-10-22
So I'm running a home server. Setup was easy, just tack this, tack that, and so on. I chose Print server, LAMP server, Virtual Machine server and Samba file server. I managed to set up Samba and the Apache server with few changes, but I'm having a couple of problems with CUPS.
Around CUPS I've installed Epson drivers for my printer (Stylus SX110) from Avasys from experience with my desktop where they work fine. I've also install cupsys-client in a hope that it'll work as a web GUI.
This is what I want to do:
I want to share the printer (which is connected by USB to the server, it is discovered by lsusb) on the network through Samba so that you can print with it by using Samba user accounts. (I don't want guest access. Too unsafe.)
I believe it's quite doable, as it says it's a part of Samba.
(Since I don't want to make this page longer than necessary, I'll add smb.conf and cupsd.conf after request.)

The man pages included weren't really helpful, to put it like that. :|

---

