---
title: "1 to 1 Nat for Multiple Public IPs"
date: 2010-03-07
forum: Server Platforms
---

### Post by debianfan on 2010-03-07
Hi,

  I am trying to figure out the best way to set up 1-1 NAT for three public ips to three private ips through a ubuntu gateway machine.

  I am running ubuntu server 9.10 and the set up is:

Internet/ISP modem -> NIC 1 Ubuntu Gateway Machine  NIC 2 -> Three PCs with Private IPs

  I had a few questions on how to do this correctly and securely.

1) What packages do I need to install (aside from the basic ubuntu server installation and possibly DHCP3-Server)

2) How do I assign all three public IPs to the NIC connected to the ISP modem?  All addresses will be static, will I need the DHCP3-Server package?

3) Once I have the three public IPs assigned how do I map each specific public IP to the private IP address associated with it and provide the correct loopback?  I want to make sure each response from the internal machines are sent out as their specific public IP.

4) Aside from allowing all connections, how should IP tables be configured to allow web services to one internal machine, mail to another internal machine and DNS to the other internal machine?

I appreciate any pointers or direction on where to look.  Thanks.

---

