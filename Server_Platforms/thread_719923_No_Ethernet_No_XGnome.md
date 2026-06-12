---
title: "No Ethernet No X/Gnome"
date: 2008-03-09
forum: Server Platforms
---

### Post by RandomUsr on 2008-03-09
ok so my ethernet wasn't configured upon install, because I thought I would use the gui tools after the fact.... OOoops


Now I have NO Xwindows environment or ethernet. Can someone please assist?

---

### Post by Petersonz on 2008-03-13
You need to manually edit /etc/network/interfaces file and setup eth0 like the following example:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
   address 10.1.1.100
   netmask 255.255.255.0
   network 10.1.1.0
   broadcast 10.1.1.255
   gateway 10.1.1.1

#       # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.1.1.50 10.1.1.200

---

### Post by RandomUsr on 2008-03-13
I lied I some how magically have a connection now... trying to figure out why I can't pull ubuntu-desktop from the repo's. Gettin some help with that on another post.

---

