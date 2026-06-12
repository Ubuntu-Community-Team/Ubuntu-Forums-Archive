---
title: "Firewall, Filter setup questions"
date: 2008-11-13
forum: Server Platforms
---

### Post by mexlinux on 2008-11-13
I have a network with the following hardware:

2 ADSL 2wire modem/routers.
1 email/web server with dynamic IP via no-ip.com to host my own domain.
10 laptops
20 desktops

I want to install a content filter, such as squid, in order to restrict internet access.

I want to install a firewall to restrict protocols, such as applications like messenger, limewire, torrents.


So my first questions are:

1-What Hardware do I need:
a)Do I need a Hardware Firewall such as FortiGate appliances.
b)Or do I need a Linux server to handle that?

2-If the options is the linux server:
a)Do I need a Server with two NICs, one connected to the ADSLs, and the other one connected to the LAN?
b)Or, Do I need a Server with one NIC only, and the routes, gateways, proxyes, etc. are to be assigned by the same server's DHCP, DNS?


Thanks in advance

---

### Post by hictio on 2008-11-13
I know this is the Ubuntu forum, but, for your situation, I would use [IPCop](http://www.ipcop.org/), it is free, runs on just any type of hardware, and it is already built in to "become" a router firewall.
Yes, you'll need 2 NICs (at least), one for the external, the internet, connection, and another for the internal, the LAN, connection.

---

### Post by windependence on 2008-11-14
Same here, not Ubuntu but you could use pfsense, M0n0wall, or Untangle. All, ready to use ISO images, just load and go. You can even put them in a VM.

-Tim

---

