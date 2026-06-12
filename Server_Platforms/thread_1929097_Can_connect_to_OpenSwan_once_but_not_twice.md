---
title: "Can connect to OpenSwan once but not twice"
date: 2012-02-21
forum: Server Platforms
---

### Post by snaga on 2012-02-21
Using:
Ubuntu Server 10.0.4
OpenSwan 2.26.24 (compiled from source)
l2tpd 1.2.5+dfsg-1

I have set up OpenSwan so that I can have a VPN to my home, mostly for family iPhones and iPads. Its behind a router that is forwarding 500 udp,4500 udp+tcp, and 1701 udp+tcp to the correct internal hardware.

It seems to work fine. I can connect to it externally with an iPhone. But, if I disconnect, I cannot reconnect until I restart ipsec on the server. Here is what I see in the auth.log on the server:

```
Feb 20 21:44:20 hades pluto[23472]: ERROR: asynchronous network error report on eth0 (sport=4500) for message to 174.253.180.137 port 2282, complainant 174.253.180.137: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]
Feb 20 21:44:20 hades pluto[23472]: ERROR: asynchronous network error report on eth0 (sport=4500) for message to 174.253.180.137 port 2282, complainant 174.253.180.137: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]
```


I notice that when I turn off the VPN on the iPhone, there are no logs produced on the server. Its like its still waiting .

My config files are here: [https://gist.github.com/1876923](https://gist.github.com/1876923)

I would appreciate any help. I've never set up a VPN before. I haven't tried to connect more than one device at a time, but I'm betting I can't, which may be the same issue.

---

