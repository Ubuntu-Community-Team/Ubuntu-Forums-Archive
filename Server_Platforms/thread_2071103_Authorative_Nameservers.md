---
title: "Authorative Nameservers"
date: 2012-10-14
forum: Server Platforms
---

### Post by sandyd on 2012-10-14
I currently have a nameserver on one of my servers.

I have several IPs - in the case that a DDOS attack or something causes me to blackhole the IP.

In total, I have 3 nameserver addresses, all bound to bind. However, only the first nameserver (in the SOA record) is considered Authorative, and that is the only one that Hurricane Electric DNS (dns.he.net) will add.

Is it supposed to be this way, or am I doing something wrong?

---

### Post by hictio on 2012-10-14
What do yo mean, "3 name server addresses"?

---

### Post by sandyd on 2012-10-25
> **hictio said:**
> What do yo mean, "3 name server addresses"?

three ip addresses that bind is listening on

---

