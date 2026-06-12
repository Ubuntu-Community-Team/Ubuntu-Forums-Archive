---
title: "Ubuntu - LTSP - DHCP - Syslog Failure..."
date: 2011-10-12
forum: Server Platforms
---

### Post by Roasted on 2011-10-12
I'm setting up an LTSP server, something I've done countless times. This time it's a little different since I am using a PowerPC chroot on the server to utilize it with older Mac systems that are obsolete. 

I've done everything I can think of. I reset the DHCP.leases file, restarted the server, all services I can think of, etc. I'm working from a secluded LAN with a simple 192.168.100.1 IP address, with my scope being 192.168.100.40-254.

Here's my syslog. The end where it repeats itself is confusing to me. What does it suggest?

[http://pastebin.com/Cg7qEMFv](http://pastebin.com/Cg7qEMFv)

---

### Post by zrin on 2011-10-19
do you have failover isc dhcp setup?

---

### Post by Roasted on 2011-10-20
> **zrin said:**
> do you have failover isc dhcp setup?

No, but after talking with LTSP devs it sounds like it's an issue with the actual chroot communicating properly. The DHCP log is now just firing out dhcpack errors.

This PowerPC thing is ridiculous. I sure hope I can get it rolling, but sometimes I'm not so sure.

---

