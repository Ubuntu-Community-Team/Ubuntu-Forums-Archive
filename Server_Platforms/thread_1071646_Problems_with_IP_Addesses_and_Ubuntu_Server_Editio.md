---
title: "Problems with IP Addesses and Ubuntu Server Edition"
date: 2009-02-16
forum: Server Platforms
---

### Post by LeonBlade on 2009-02-16
Hello everyone,

I'm having some trouble with my Ubuntu Server...
It is a great system, but it has the same IP address as this Windows machine I'm currently on right now...

This has happened before, and I cannot access my server outside of the network... it also doesn't show up on my DHCP list...

Thanks,
LeonBlade

---

### Post by kestrel1 on 2009-02-16
If both systems are set to get an IP address via DHCP you shouldn't have a problem. However if you need one machine to have a static IP address, you should either set this to be outside of the DHCP range or tell your DHCP server not to use that particular address.

---

### Post by LeonBlade on 2009-02-17
Alright, I'll look into this when I get back home.
Thanks.

---

