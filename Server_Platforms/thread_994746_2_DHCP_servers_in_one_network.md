---
title: "2 DHCP servers in one network"
date: 2008-11-27
forum: Server Platforms
---

### Post by any.linux12 on 2008-11-27
Hello everybody

I'm  configuring a new server to my network and I don't know if it's ok to connect the new one with the old one working because both have DHCP server.
 
Is it any problem??

---

### Post by felker2 on 2008-11-27
Yes, that's a problem; only one DHCP-server should be active.

Solution: de-activate one DHCP-server-process.

---

