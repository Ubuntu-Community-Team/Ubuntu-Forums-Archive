---
title: "dhcp"
date: 2008-06-16
forum: Server Platforms
---

### Post by fnkhan on 2008-06-16
i want to configure dhcp in 2 networks pools but the main problem is group A user connect to 192.168.1.XX and group B user connect to 192.168.2.XX how i will do this with using mac of every pc.

---

### Post by PacketCollision on 2008-06-16
A little more information is needed.  I assume you are going to be using ISC's dhcpd (dhcp3-server in apt)?  What is the difference between the two groups, are they on different physical LANs connected to different ports on the server or do you want to be able to choose which group a client is based on MAC address or some other characteristic?

---

