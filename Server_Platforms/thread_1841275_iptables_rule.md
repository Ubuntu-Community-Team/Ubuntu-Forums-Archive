---
title: "iptables rule"
date: 2011-09-09
forum: Server Platforms
---

### Post by ovi1 on 2011-09-09
Hello,
 
I have an nagios monitoring server that does a dns query for each service check. I have about 2500 service checks and because of this there are about 20000 dns queries in 5 minutes.
 
The problem is that it queries on IPV6 and then on IPV4. I have disabled everything regarding ipv6 in kernel, services.. but I have read that it queries ipv6 address through ipv4 protocol, this is how the resolver works for my kernel version. So I decided to make an iptables rule to drop the AAAA requests on output so it does not stress the dns server.
 
Here is how I see the dns queries from my nagios server:
[root@sums011 ~]# tcpdump | grep AAAA
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
10:18:49.177033 IP sums011.example.com.36699 > SUDS002.example.com.domain: 16939+ AAAA? SUAS005.example.com. (43)
sums011 is the monitoring server
suds002 is the dns server
suas005 is the name that is requested for resolving
 
If someone can tell me what rule to add to my iptables file so it drops every package that contains AAAA I will be very grateful.
Also if you have other ideas on how to solve my problem I'll be glad.

---

