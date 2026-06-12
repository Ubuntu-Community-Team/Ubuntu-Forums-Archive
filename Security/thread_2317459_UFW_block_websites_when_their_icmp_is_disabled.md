---
title: "UFW block websites when their icmp is disabled"
date: 2016-03-16
forum: Security
---

### Post by spooli on 2016-03-16
Hi guys

I'm looking how to tell to ufw don't block websites when their icmp is disabled (icmp unreachable)

somes websites blocks ping (for some security reasons)..

UFW enabled : website unreachable
UFW disabled : website ok 

any idea ?

---

### Post by haplorrhine on 2016-03-17
Wouldn't you look to iptables?  ufw is only a frontend.

---

### Post by spooli on 2016-03-18
> **haplorrhine said:**
> Wouldn't you look to iptables?  ufw is only a frontend.

the problem was between ufw and pptpd server

when I use vpn (connected to pptpd server with ufw disabled on the server) all ok

but when I enabled ufw on the server, all servers with icmp request disabled will not available on vpn client

---

