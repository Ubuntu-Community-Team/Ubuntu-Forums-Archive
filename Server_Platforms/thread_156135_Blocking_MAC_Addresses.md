---
title: "Blocking MAC Addresses"
date: 2006-04-06
forum: Server Platforms
---

### Post by R Audano on 2006-04-06
Hello,
 I am currently running a gateway router on Ubuntu 5.10, and want to block MAC addresses by default and allow only selected ones. I tried static ip's but had no luck.

I am currently using firestarter. 

I made an attempt to figure out firewall builder, but had no luck because of my in-ability to find current manuals.

Can anybody help me?

Thanks
Robert

---

### Post by nagilum on 2006-04-06
AFAIK firestarter does not allow filtering based on MAC addresses. You can use iptables directly to match packets based on their MAC address (see the manpage for more information). There are also some good tutorials on the iptables homepage ([http://www.netfilter.org)](http://www.netfilter.org)).
MACs can be faked though, you better don't rely on this mechanism alone to protect your network.

---

