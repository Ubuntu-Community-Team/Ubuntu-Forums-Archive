---
title: "Ubuntu server as DHCP server for IPv4 and IPv6"
date: 2015-07-03
forum: Server Platforms
---

### Post by eltiti55555 on 2015-07-03
[FONT=Helvetica Neue]I currently have an Ubuntu server on virtualbox setup to give hosts on my GNS3 topology IPv4 addresses, and it is working without issues. However, I would like to have that same DHCP server (Ubuntu server) give out IPv6 addresses as well at the same time, and I am not quite sure how to accomplish that.I have drawn a rough sketch of what my network looks like.[/FONT]
[FONT=Helvetica Neue][http://postimg.org/image/u3r8269pv/](http://postimg.org/image/u3r8269pv/)[/FONT]
[FONT=Helvetica Neue]I have done topologies with only IPv4 in the past and they have worked like a charm, however I am learning IPv6 and there doesn't seem to be much material out there on DHCP and dual stacking from what I have been able to gather. Any help would be appreciated. The network I am working on will eventually expand, and I will most likely use OSPF as the routing protocol. Any help is appreciated..[/FONT]
[FONT=Helvetica Neue]Thanks![/FONT]

---

### Post by SeijiSensei on 2015-07-03
[http://mirrors.bieringer.de/Linux+IPv6-HOWTO/hints-daemons-isc-dhcp.html](http://mirrors.bieringer.de/Linux+IPv6-HOWTO/hints-daemons-isc-dhcp.html) looks like a starting point.  The whole HOWTO is probably worth skimming.

---

