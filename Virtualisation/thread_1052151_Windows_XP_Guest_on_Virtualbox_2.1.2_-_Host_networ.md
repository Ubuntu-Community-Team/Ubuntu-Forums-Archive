---
title: "Windows XP Guest on Virtualbox 2.1.2 - Host networking not working"
date: 2009-01-27
forum: Virtualisation
---

### Post by michelf on 2009-01-27
Hi there, 

I've configured the host networking on my WinXP SP2 guest, using the eth0 interface to make a host network, but when i set the ips on the host and the guest then try to ping, while monitoring on wireshark, i see the guest packets knocking on the interface, but no response, causing timeouts

OTOH, when i ping from host to guest, nothing appears on wireshark.

Any clues ?

---

### Post by Dedoimedo on 2009-01-27
What are the actual addresses?

VB uses private addesses for its machines (NAT), but it does the translation in the background. You can't control how it does it. There's no visible VB interface that you can actually route your traffic to. And since private IPs are non-routable from external networks, your attempts at resolution, ping will fail.

If you configure a bridge, the it will work, since you will have an IP that you host network can route to, i.e. the same subnet.

Dedoimedo

---

