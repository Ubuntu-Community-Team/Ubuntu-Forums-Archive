---
title: "bootps"
date: 2006-05-16
forum: Server Platforms
---

### Post by horseradish on 2006-05-16
hi,

with etherape running, I can see a small amount of constant traffic via bootps protocol(?)  from a 10 ip address to a 255 address. Even when I am doing nothing this is the only traffic according to etherape. its maybe 2-10 kbps both ways. Locking firestarter has no effect.

Is this normal ? (and what is it ?).  I only use the computer for surfing.

---

### Post by fbusy on 2007-10-30
i recieve similar connections. im also wondering what protocol the "bootps" is? anyone alive?

---

### Post by MJN on 2007-10-30
It's a somewhat-legacy protocol used to enable clients to gather various parameters, and a boot file, from a centralised server to boot up on a network. It's largely be taken over by DHCP (which is backwards compatible with it).

The destination 255.255.255.255 is the 'broadcast' address - such BOOTP/DHCP calls are done as broadcasts because until a client gets an IP address (and gateway) it doesn't know who to send the requests to and hence floods the network with it, waiting for an answer.

How are you connected to the Internet? Do you have any network or are you connected directly to a cable/ADSL modem? Many ISP configurations result in you being able to see these requests of neighbouring customers and that could be what you're seeing.

Mathew

---

### Post by fbusy on 2007-10-31
thank you. it seems very possible.

---

