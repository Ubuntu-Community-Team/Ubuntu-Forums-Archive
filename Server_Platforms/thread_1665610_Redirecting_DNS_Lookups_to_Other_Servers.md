---
title: "Redirecting DNS Lookups to Other Servers"
date: 2011-01-12
forum: Server Platforms
---

### Post by bsntech on 2011-01-12
Removed the thread; figured out that this does work in the zones config:

<Record you want redirected to another nameserver><tab>IN<tab>NS<tab><name server to redirect the query to>

---

### Post by sj1410 on 2011-01-12
anyways, you can do this with dnsmasq

[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

---

