---
title: "DNS server's own IP"
date: 2011-05-18
forum: Server Platforms
---

### Post by peterko on 2011-05-18
hi,
i just finished scratch 10.04/64 bit server, bind9, dhcp3-server install and configurations as master DNS and only DHCP.

IP distribution works good, but  DNS identifies it's own IP incorrectly

dhcpd.conf:
option domain-name-servers ns.ourdomain.com, ns1.ourdomain.com;

computers are getting ns1.ourdomain.com correctly, but ns.ourdomain.com is translated as 127.0.0.1

"ns.ourdomain.com" is the mentioned computer

what causes this?

10x

---

### Post by ZuOverture on 2011-05-18
Could you provide the contents of your zone files and resolv.conf?

---

### Post by peterko on 2011-05-18
...couldn't answer sooner....i was banging my head against rack...

it came from /etc/hosts

changed - reloaded - everything works properly

many thanks

---

