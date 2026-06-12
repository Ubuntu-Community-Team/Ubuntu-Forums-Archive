---
title: "Server cannot access the intenet but allows access."
date: 2007-05-13
forum: Server Platforms
---

### Post by librano on 2007-05-13
Hi all!

I am facing a pretty weird problem. I am setting up a router/gateway for a LAN. I have decided to run Ubuntu server edition. However, I have encountered this problem both with Dapper and Feisty.

Here is the problem: the actual server cannot access the internet. Machines on the LAN have access to the internet using the server as a router but the server itself cannot resolve domain names. It can ping IP addresses on the internet but not domain names eg [www.google.com](www.google.com). The DNS server specified in the /etc/network/interface file is the same one specified on the machines that can access the internet on the LAN. During installation I selected to install a DNS and LAMP server.

This is pretty confusing for me... and I need this functionality pretty badly. Strange that Feisty doesn't come with ssh by default.


Thanks for your help in advance.

lib.

---

### Post by craigp84 on 2007-05-13
Hi Librano,

Sounds like a wee DNS issue, no worries, it's an easy fix :)

Just double check that the "nameserver" line in /etc/resolv.conf really is the same as on the workstations that can access the internet.

If they're linux workstations, just "cat /etc/resolv.conf" or if they're windoze, just "ipconfig /all".

I'm guessing you're using the linux server as a caching nameserver, so on the workstations, the DNS server specified is the IP of the linux server. If this is the case, then you want your /etc/resolv.conf to look like:

```
search your.domain.here
nameserver 127.0.0.1
```

Hope this helps,

Craig

---

### Post by librano on 2007-05-13
worked like a charm! thanks a million!

---

