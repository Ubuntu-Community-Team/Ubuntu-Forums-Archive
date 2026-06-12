---
title: "Always use available eth*, or stop creating new ones."
date: 2010-08-26
forum: Server Platforms
---

### Post by dtfinch on 2010-08-26
To save time, I sometimes install the Ubuntu Server (lately 10.04.1) once, then copy the image to several servers and then customize each. I've run into some network related annoyances that, while fixed for now, I hope to find a better way to deal with in the future, because my current workarounds don't seem very elegant.

The first issue is that when it boots on the new server, it adds all the network interfaces to /etc/udev/rules.d/70-persistent-net.rules, with new names. It also happens if the mac address ever changes. I usually manually delete all the obsolete entries in that file, but it'd be easier if I could disable that feature entirely.

The second issue is that defaults to only bringing up eth0, so I usually edit /etc/network/interfaces to look like this:```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto eth3
iface eth3 inet dhcp
...
```While it works, it looks very unclean. I'm wondering if there's a short way to say "all interfaces" rather than copying/pasting for every possible eth* it may encounter.

Edit: dhclient logs notices for every few seconds for the interfaces that don't have a cable plugged in, so some way to suppress those would help too. I'll probably have to create something in /etc/rsyslog.d/ for that.

---

