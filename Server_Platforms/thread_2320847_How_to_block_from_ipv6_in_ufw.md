---
title: "How to block from ipv6 in ufw"
date: 2016-04-18
forum: Server Platforms
---

### Post by mbnoimi on 2016-04-18
Hi,

I want to block all **from** IPs in ipv6. How can I write the right rule for it?

---

### Post by darkod on 2016-04-18
Are you using your ipv6 IP at all? If not, simply remove it and the ipv6 traffic has nowhere to go.

---

### Post by MAFoElffen on 2016-04-19
darkod is right... by concept. 

Internet is not really ipv6 friendly yet. Meaning that something can only travel from point a to z in all the points between are talking the same language. If a router somewhere in the middle does not support ipv6, then it would stop there. That does not include if tunneled within ipv4... And most routers need to have ipv6 turned on (if they are capable, not usually turned on on by default) to handled it.

Having said that-- Recently seeing more traffic probes via ipv6...

It depends on the rule. If you look at man ufw, most to the rules that also apply to ipv6 use a "ipv6" option to apply to that protocol. That allows you to apply a filter that can allow ipv4, but on the same concept, deny ipv6.(or vice versa). But again, it depends on the rule on how that plays out. Personally, I have to look it up and play with it, to make sure it's working like I want it to ... and "think" it should be working.

---

