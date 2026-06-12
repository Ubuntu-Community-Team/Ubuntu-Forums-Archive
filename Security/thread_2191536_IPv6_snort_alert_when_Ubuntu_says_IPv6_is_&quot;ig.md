---
title: "IPv6 snort alert when Ubuntu says IPv6 is &quot;ignored&quot;"
date: 2013-12-03
forum: Security
---

### Post by doug-ravennasprings on 2013-12-03
I'm running Ubuntu 13.10_x64 and my network tools are showing possibly inappropriate traffic. I'm seeing Snort rules light up with "PROTOCOL-DNS IPv6 host name enumeration" coming from this address. The GUI network information claims IPv6 is "ignored".  I have no idea what that means but I suspect it doesn't mean much of anything.  ifconfig shows an ipv6 address.  Can someone help me figure out what is going on? It seems part of Ubuntu is developing for IPv6 while others (GUI teams) are not. How concerned should I be?

---

### Post by bashiergui on 2013-12-03
> **doug-ravennasprings said:**
> . I'm seeing Snort rules light up with "PROTOCOL-DNS IPv6 host name enumeration" coming from this address. 
Coming from what address?

---

### Post by bashiergui on 2013-12-03
IPv6 will replace IPv4 eventually. Some networks stay on IPv4 and therefore choose to ignore IPv6 in their environment.

Just because you choose to ignore IPv6 doesn't mean it stops existing. Here's a quick article about some security issues resulting from ignoring IPv6. [http://blog.ipspace.net/2013/05/the-dangers-of-ignoring-ipv6.html](http://blog.ipspace.net/2013/05/the-dangers-of-ignoring-ipv6.html)

i'm guessing it's some kind of IPv6 port scan coming from the internet, which is common. Set up a rule on your firewall to drop all IPv6 traffic if you want to block it.

---

