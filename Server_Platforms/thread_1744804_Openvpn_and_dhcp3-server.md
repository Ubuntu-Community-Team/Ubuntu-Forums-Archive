---
title: "Openvpn and dhcp3-server"
date: 2011-04-30
forum: Server Platforms
---

### Post by DrJohn999 on 2011-04-30
A quick question (I think). This is a 10.04 LTS server running openvpn 2.1.0, dhcp3-server, named, etc. No apparent problems with the vpn. 

In man dhcpd.conf it says that a subnet should be declared even if no addresses will be allocated. Openvpn allocates its own addresses on a default 10.0.8.0 subnet: is it necessary to declare this subnet in dhcpd.conf?

Thanks!

---

