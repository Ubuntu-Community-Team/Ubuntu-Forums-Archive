---
title: "Dmesg: Out of Socket Memory"
date: 2008-04-28
forum: Server Platforms
---

### Post by jtvmind on 2008-04-28
Greetings,
 I've been getting this message when running dmesg:
Out of Socket Memory

I'm running Nginx on Linux uw 2.6.18-5-686. I'm trying to determine what would cause this message. 

Any help is appreciated. 

Cheers,
j

---

### Post by wirelessmonkey on 2008-04-28
Without any further information, I can only guess that something, (nginx?)is opening a whole bunch of sockets, and your system can't keep up, either due to too many open at once, or too many services using the same sockets.

If you could put your error into context, i.e. 10 or so lines above and below the message in dmesg, maybe we can get some useful information.

---

