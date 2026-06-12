---
title: "iptables matching on TCP OPTIONS"
date: 2010-11-11
forum: Security
---

### Post by burek021 on 2010-11-11
Hi,

I've been trying Google for hours now, and had no luck with this :(

Is it possible to use TCP OPTIONS field ( [http://en.wikipedia.org/wiki/Transmission_Control_Protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol) ) to put a short string (text) in the tcp option area of an TCP packet (as a new, custom, option) and later match those packets with iptables using --tcp-option?

Are there any example out there that are explaining how to match a tcp packet, based on the custom option's value (short text that i'd like to put in it)?

Thanks to all who can help.

---

