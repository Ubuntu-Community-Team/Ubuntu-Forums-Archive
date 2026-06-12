---
title: "Linux Server Installation Guide"
date: 2009-05-29
forum: Server Platforms
---

### Post by speedzonenetwork on 2009-05-29
I Need Linux Server.
 
1, Which Provide Ip To Client Automatically ( Like DHCP)
 
2, In Which i can Bond User Mac With Ip to Access Internet.
 
3, And in which i can make Bandwidth Limit in groups.
 
Can Any Expert Guide Me To Do So.
 
Please Reply.
 
Thanks.

---

### Post by cariboo on 2009-05-30
Have a look at the [Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html") and the [HowtoForge Perfect Server Guide]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts").

---

### Post by speedzonenetwork on 2009-05-30
Thanks Alot :)
 
Can any expert make a installed pack of linux server with required features?

---

### Post by Iowan on 2009-05-31
DHCP server (at least DHCP3) can be set up to issue "static leases" based on MAC address.  This would be configured in /etc/dhcp3/dhcpd.conf. Dunno about the bandwidth limits.

---

