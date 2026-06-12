---
title: "Iptables question - throttling surges of web traffic"
date: 2008-01-09
forum: Server Platforms
---

### Post by Sporkman on 2008-01-09
Consider the following iptables line, intended to limit web traffic surges from, for example, links from popular sites:

iptables -A INPUT -p tcp --dport 80 -m limit --limit 100/second --limit-burst 200 -j ACCEPT

Question: does this limit requests to 100/sec from *all sources*, or just from any given IP address source?

---

### Post by The Cog on 2008-01-09
It is my understnding that it limits matches on this line of iptables. In your example, that would limit incoming TCP packets/Second to your web server to 100/Sec (regardless of IP address) without limiting other protocols or TCP ports.

Note that there is a separate Traffic Control program (man tc) in Linux for limiting throughput, which works on bit/Sec rather than packet/Sec it you want.
[http://www.rns-nis.co.yu/~mps/linux-tc.html](http://www.rns-nis.co.yu/~mps/linux-tc.html)

---

### Post by Sporkman on 2008-01-09
Thanks! :cool:

---

