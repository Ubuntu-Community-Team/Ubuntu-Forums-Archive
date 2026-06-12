---
title: "Ubuntu for gateway - which software"
date: 2006-10-08
forum: Server Platforms
---

### Post by AnyOne on 2006-10-08
First of all hello to all..
I'm writing this post to ask you guys an sugestion for what I should implement in my company so that i can have a machine that is able to:

- DHCP
- Filter access to Internet Applications, basicly block ports comunication, for like msn messenger and aol chats.
- Allow some other computers that are able to use those ports.
- firewall the Company network from the outside.

I'm not asking for a guide of how to do this, im just asking if its possible to give me your sugestions with which software I should use for these objectives...

Thanks in advance!

---

### Post by Macchi on 2006-10-08
Some useful functions for a gateway are:
DHCPserver, Firewall, Web Proxy, Content Filter, DNS server+cache, ssh server, intrusion avoidance, rootkit detection

Examples of recommended packages to implement those functions are:
dhcp3-server, FireHOL, Squid, DansGuardian, djbdns, openssh-server, DenyHosts, chkrootkit

---

