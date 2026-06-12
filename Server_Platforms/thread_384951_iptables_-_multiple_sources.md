---
title: "iptables - multiple sources?"
date: 2007-03-15
forum: Server Platforms
---

### Post by lyna on 2007-03-15
Hi all,

I'd like to see when someone out of the ordinary uses ssh to my Ubuntu server.  I've set a rule to log these attempts, i.e. 

  iptables -A INPUT -m state --state NEW -s ! 123.456.789.0/24 -p tcp -ddport ssh -j LOG

I'd like to limit this further to only a few addresses within the 123.456.789.0 network, but I can't figure if that's possible.  Is there such a thing as an "and" or "or" within iptables?  What I'd like to know about is anyone other than 123.456.789.10 and 123.456.789.20, rather than the entire subnet.  Can this be done, and how?

Cheers,
Lyn

---

### Post by DaveArb on 2007-03-15
iptables processes rules sequentially. You should be able to place rules that specifically ACCEPT ssh from ...10 and ...20, then a rule that LOGs everything else.

I don't play with iptables much any more, but I'm pretty sure this will work.

---

### Post by Mr. C. on 2007-03-15
Yes, it can.  But I would recommend you log ALL the connections anyway.  It is easy to filter logs later of what you *do not* want to see.  You are going to find that there are thousands of SSH rejects and a very small handful of passes.  Better to have the info when you need to debug then to learn this after the fact.

MrC

---

