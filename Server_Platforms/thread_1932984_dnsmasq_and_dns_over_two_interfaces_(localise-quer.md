---
title: "dnsmasq and dns over two interfaces (localise-queries)"
date: 2012-02-28
forum: Server Platforms
---

### Post by maxxer on 2012-02-28
Hi.

I've set up my dnsmasq server to use the localise-queries parameter.

That is, in /etc/hosts

172.16.12.1     a.domain.com a b b.domain.com 
10.11.11.99     a.domain.com a b b.domain.com 


then I connect to the interface A and get an ip 172.16.12.2.
if I try to resolve a:

# host a.domain.com
a.domain.com has address 10.11.11.99
a.domain.com has address 172.16.12.1


on dnsmasq logs:
dnsmasq[2019]: query[A] a.domain.com from 172.16.12.2
dnsmasq[2019]: /etc/hosts a.domain.com is 172.16.12.1
dnsmasq[2019]: /etc/hosts a.domain.com is 10.11.11.99


Why? shoudln't it return just 172.16.12.1??

I'm sure there's nothing else on port 53
dnsmasq   2945  0.0  0.1   3284   780 ?        S    10:53   0:00 /usr/sbin/dnsmasq -u dnsmasq --localise-queries

# lsof -i -P -n |grep :53
dnsmasq    2945  dnsmasq    4u  IPv4 610286       UDP *:53 
dnsmasq    2945  dnsmasq    5u  IPv4 610287       TCP *:53 (LISTEN)
dnsmasq    2945  dnsmasq    6u  IPv6 610288       UDP *:53 
dnsmasq    2945  dnsmasq    7u  IPv6 610289       TCP *:53 (LISTEN)

thanks
maxxer

---

