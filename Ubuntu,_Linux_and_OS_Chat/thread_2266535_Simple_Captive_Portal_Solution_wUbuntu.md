---
title: "Simple Captive Portal Solution w/Ubuntu"
date: 2015-02-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Althorax on 2015-02-23
I was wondering if anyone has used ubuntu and for creating a simple captive portal, say maybe with squid and iptables?

I would like a simple solution to present a simple splash page(acceptable use agreement - must click to agree and pass-through)

I have tried other third party apps such as pfsense, Untangle, PacketFence, and they all seem like over kill and pretty beastly...

I need it to serve up dhcp addresses(DHCP Server)

Manage the network traffic from 10.(access point side - eth1) to our DSL modem(eth0), 192.168.0.1

Man in the middle authentication page(User Agreement-click through - squid???)

I'm not sure how to put this all together, but it seems like it should be simple...

Any thoughts?

---

### Post by TheFu on 2015-02-23
I've used pfsense for this. Never considered Ubuntu, sorry.

---

