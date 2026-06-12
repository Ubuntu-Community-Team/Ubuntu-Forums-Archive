---
title: "Looking for a IPV6 DHCP Server can work with Windows 7 in-build client"
date: 2011-01-17
forum: Server Platforms
---

### Post by beterhans on 2011-01-17
Hi
I'm looking for a dhcp6 server which can work with both windows 7 and linux.

I found one called "dibbler"
but it require PC to install a Client to work with server. the in-build client in widnows 7 won't work with it :(

any suggestion?

---

### Post by lemming465 on 2011-01-17
Two possibilities, neither of which I've tried, alas.  Ubuntu 10.10 doesn't have ISC dhcp version 4, so maybe:

(1) You could build the latest ISC DHCP server from source
(2) try the "wide-dhcpv6-server" package

I'm guessing those would both support windows 7 clients.  In a windows-heavy environment I'd be tempted to try Microsoft's windows server 2008 R2 DHCP service, which can probably support Linux clients.

---

