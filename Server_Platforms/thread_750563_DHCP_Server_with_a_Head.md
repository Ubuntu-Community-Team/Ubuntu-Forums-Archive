---
title: "DHCP Server with a Head?"
date: 2008-04-09
forum: Server Platforms
---

### Post by damonjablons on 2008-04-09
Hi,

Currently I run Ubuntu 7.10 Desktop on a spare computer I have in order to run Azureus with the web interface installed, this way I have an easily controllable seedbox.  I attempted to install 7.10 Server with wTorrent, but it wouldn't compile.

Anyway, is it possible to use this as a DHCP server as well?  All the computer currently does is run Azureus, a LAMP environment, and SAMBA.  It still has a head as well.

If it is okay for me to run this as a DHCP server, and it wouldn't be too slow (the computer is four years old), are there any network cards that aren't compatible?  Also, what kind of wireless network switch should I buy?  I currently own two linksys routers which are absolutely terrible, and cannot run the router linux firmware.

Or should I abandon all hope for using this machine as a DHCP server, and instead buy a decent router?  Thanks in advance for the help.

---

### Post by p_quarles on 2008-04-09
Moved to Server Platforms. 

There shouldn't be any hardware barrier to using this machine as a DHCP server, but I think you are better off buying a good router, or configuring another spare machine to use as the server. Any kind of service which is responsible for some basic level of security (including a DHCP server) should usually be as separated as possible from any other function.

---

