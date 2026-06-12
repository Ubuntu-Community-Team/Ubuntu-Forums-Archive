---
title: "Tough DNS server not giving me a reply to anything"
date: 2011-08-08
forum: Server Platforms
---

### Post by UltraTiga on 2011-08-08
Hi all.

Here is my setup. 

Cisco router running NAT

Access-list allowing protocol 53.  


I have a question about DNS Bind9

I have 2 ubuntu servers.  1 is the primary DNS and the other is a secondary.  I have zone transfer working between the two.  

The primary DNS won't resolve anything when the resolv.conf is pointed to itself, when interfaces has a nameservers equal to itself. recursion is disabled. 

The secondary is pointed (resolv.conf) to the primary. also, in the interfaces file, the nameservers line is also pointed to the primary as well.

Her is the interesting point.

When using the Linux boxes locally, 

I can perform a DIG A or DIG AAAA on the primary, it answers.  When I ping anything on my network or the internet, I can not.

I can perform a DIG A or DIG AAAA on the Secondary, I get no answer from the Primary, but I can resolve normal pings, and DIGs out to the Internet.

If I use a Windows 7 machine and use either the primary or Secondary as a dns server, Nothing gets resolved from either one.


Can Anyone explain why this happens??

---

### Post by UltraTiga on 2011-08-11
Has anyone  had this problem??

---

