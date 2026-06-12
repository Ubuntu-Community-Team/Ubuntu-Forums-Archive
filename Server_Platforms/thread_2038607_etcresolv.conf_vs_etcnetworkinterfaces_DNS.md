---
title: "/etc/resolv.conf vs /etc/network/interfaces DNS?"
date: 2012-08-07
forum: Server Platforms
---

### Post by hesson on 2012-08-07
What is the point of /etc/resolv.conf if /etc/network/interfaces contains dns-nameservers for each interface that specifies the DNS? Does one override the other?

---

### Post by darkod on 2012-08-07
Yes, I believe the resolv.conf is overwritten with the info in dns-nameservers in /etc/network/interfaces. In fact, in the latest 12.04 LTS the recommendation is not to edit manually resolv.conf any more. Instead use dns-nameservers.

---

### Post by kevinthecomputerguy on 2012-08-08
Its also been my experience that resolv.conf is overwritten with dynamic info.

---

### Post by koenn on 2012-08-08
it's documented behaviour; 

/etc/resolv.conf is the traditional place to keep DNS server info; 
one used to edit it by hand; 

more recently the resolvconf progam has come in use, it automatically updates /etc/resolv.conf on behalf of a number of other network utilities to facilitate autoconfiguration mechanisms and such; 
That's why it's now recommended to have your DNS servers in .../network/interfaces.

---

