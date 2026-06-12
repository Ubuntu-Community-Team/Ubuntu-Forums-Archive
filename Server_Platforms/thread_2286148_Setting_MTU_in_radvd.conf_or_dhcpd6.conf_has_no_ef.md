---
title: "Setting MTU in radvd.conf or dhcpd6.conf has no effect"
date: 2015-07-10
forum: Server Platforms
---

### Post by richard51 on 2015-07-10
Setting** option interface-mtu 1492** in the **dhcpd6.conf** file or **AdvLinkMTU 1492** in the **radvd.conf** file on the server seems to have no effect when using stateful IPv6. The client computers MTU is always set to 1500 even though the client's are configured via there **dhclient.conf** files to **request interface-mtu**?

**Question:** Is there a way for the host PC's to get/use the MTU set by the server?

---

