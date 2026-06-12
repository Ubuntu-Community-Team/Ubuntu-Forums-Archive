---
title: "Why do I see out going traffic to Bogon IP addresses in my log"
date: 2014-01-07
forum: Security
---

### Post by Luft on 2014-01-07
The title says it all.  I'm seeing out going traffic to address 224.0.0.22 TCP and 224.0.0.251 UDP which are being blocked and flagged as Bogon.  Just curious why Ubuntu would try to send data to an invalid address.

---

### Post by The Cog on 2014-01-07
224.0.0.251 is a multicast DNS service address and I'm not really surprised to see this. Have a look at the packets with wireshark for a full decode to see what's going on.

224.0.0.22 is IGMP, Internet Group Management Protocol. 

Both addresses are listed here: [http://en.wikipedia.org/wiki/Multicast_address](http://en.wikipedia.org/wiki/Multicast_address)

This command should list everything with an open internet socket, whcich might help explain things:
```
sudo lsof -i -n
```

---

