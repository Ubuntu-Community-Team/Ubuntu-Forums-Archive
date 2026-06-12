---
title: "Ethernet w/o IP"
date: 2009-07-20
forum: Server Platforms
---

### Post by sonicbuddha on 2009-07-20
I am running a VirtualBox on a potentially internet facing machine.  The guest machine bridged to the internet facing interface does not route on the same network as the ethernet device and, for security's sake, I'd like to bring up the ethernet device w/o any IP at all instead of assigning it an unroutable address.  How can I do this?

I am running 8.04 LTS

---

### Post by wirelessmonkey on 2009-07-20
Disable DHCP on the interface, then restart the interface, it should be up, without any IP.

---

