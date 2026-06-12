---
title: "Restrict access to particular IP"
date: 2010-10-07
forum: Server Platforms
---

### Post by flyingmunky25 on 2010-10-07
Hi,
I'm running Ubuntu Server 10.04 32-bit.

I'm looking to find if there is anyway I can lock down ubuntu so that remote access, whether it be SSH, ftp, apache...etc can be only accessed from a certain IP range, or a certain set of IPs?

Essentially, we'll say the Server IP is 192.168.1.32, and I want the IP addresses 192.168.1.33-50 to be able to access the server, but no other IPs.

I am in a switched environment, router's are not allowed to be placed on the network, and I do not have access to a DNS or DHCP server.

Is there a way to do this in on the server via a configuration of some sort?

Thanks!!

---

### Post by pricetech on 2010-10-07
Look into configuring a firewall on the Ubuntu box.  Drop everything from the IPs you don't want.

---

### Post by druhboruch on 2010-10-07
/etc/hosts.allow may be just what you need.

---

### Post by flyingmunky25 on 2010-10-13
Perfect! tried the linux firewall and it worked, and I can't believe I forgot about them...both of them!
Thanks much!!

---

