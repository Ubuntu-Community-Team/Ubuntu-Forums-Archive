---
title: "Dynamic IP Firewall Entry?"
date: 2008-07-20
forum: Security
---

### Post by davidshq on 2008-07-20
Lets say you have a firewall setup using iptables. Now you have a few administrators - perhaps one needs access to MySQL, one to Webmin, one to SSH. They have dynamic IP addresses at their home. Is there a way to somehow identify a machine/location in such a way that one can tell iptables to allow specific ports to be open if that machine/location contacts it?
Instead of saying open up for ip x.x.x.x, saying something like, "if dynamic dns is mydns.dnsdynamic.com open up".
David.

---

### Post by kevdog on 2008-07-20
Probably not want you want, however here are two options:

Matching by MAC address (source MAC address)

Port Knocking utility -- but requires a client on each connecting machine.

---

### Post by cdenley on 2008-07-21
> **davidshq said:**
> Lets say you have a firewall setup using iptables. Now you have a few administrators - perhaps one needs access to MySQL, one to Webmin, one to SSH. They have dynamic IP addresses at their home. Is there a way to somehow identify a machine/location in such a way that one can tell iptables to allow specific ports to be open if that machine/location contacts it?
Instead of saying open up for ip x.x.x.x, saying something like, "if dynamic dns is mydns.dnsdynamic.com open up".
David.

You can't use iptables to filter based on domain. You can create a script that creates iptables rules after resolving the domain.

Something like this
```

#!/bin/sh
myip=`dig mydomain.dnsdynamic.com +short`
iptables -A INPUT -s $myip -j ACCEPT

```

---

