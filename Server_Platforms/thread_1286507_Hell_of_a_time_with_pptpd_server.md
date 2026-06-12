---
title: "Hell of a time with pptpd server"
date: 2009-10-09
forum: Server Platforms
---

### Post by jcderr on 2009-10-09
I'm getting incredibly inconsistent results out of pptpd server.

I have to rehup the server repeatedly and spend a considerable amount of time screwing with localip and remoteip (in /etc/pptpd.conf) before I can get a connection working. Generally, after I establish a pptp connection, I'll get only a few moments (<10seconds) of traffic before the connection gets stoned. Occasionally, I'll get a minute of few, and very rarely, it'll stay up indefinitely.

I've left everything set to the defaults, except that I've had to play with localip and remoteip, as I said.

My server has one nic and sits behind an Airport Extreme wireless base station, with port mapping properly configured. The LAN subnet is 10.0.1.0/24, with the server at 10.0.1.200.

I pptpd in, connect, and authenticate just fine. currently, i have localip set to 10.0.1.200, and remoteip set to 10.0.1.210. I find that, generally, changing localip to anything I hadn't set it to lately will help... briefly, usually just for one connection.

When it works, it works beautifully. I can connect to anything in the LAN node. I get our LAN's internal DNS. etc etc etc. But it's a major hassle each time...

Any ideas?

---

