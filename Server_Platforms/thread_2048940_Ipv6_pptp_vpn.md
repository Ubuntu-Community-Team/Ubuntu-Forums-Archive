---
title: "Ipv6 pptp vpn"
date: 2012-08-27
forum: Server Platforms
---

### Post by sandyd on 2012-08-27
Ive been looking for a full (complete) guide on how to setup a PPTP vpn server with dual stack (both ipv4 and ipv6) support.

Currently, my VPS has 8  ipv6/ipv4 IPS, so I would prefer to simply forward the traffic to the interfaces.

Thanks!

---

### Post by sanderj on 2012-08-27
> **sandyd said:**
> Ive been looking for a full (complete) guide on how to setup a PPTP vpn server with dual stack (both ipv4 and ipv6) support.


Where have you been looking?

---

### Post by sandyd on 2012-08-27
Google.

I can find half-guides or mentions of it, but never a complete tutorial.

---

### Post by sanderj on 2012-08-27
> **sandyd said:**
> Google.

I can find half-guides or mentions of it, but never a complete tutorial.

Yes. Maybe IPv6 & PPTP is too new?

But can't you use the incomplete tutorials? I would first setup a PPtP server with IPv4. As soon as that works, enhance it with Ipv6. Maybe it's just one line extra (net.ipv6.conf.all.forwarding=1 ?) ...

---

