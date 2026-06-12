---
title: "firewall and security concerns"
date: 2011-05-07
forum: Security
---

### Post by PeaceOcean on 2011-05-07
First of all, I am a newbie. do not laugh at me. I turned on the  ufw/iptable by punching "$ sudo ufw enable". And then I did "$ sudo ufw  default deny". from "$ sudo ufw status verbose", I can see 
"Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip".

I am wondering what exactly the "deny" influences and what exactly it  means. when doing internet browsing, the TCP/UDP/HTTP have outgoing  packets to the remote servers. However, my computer also receives  incoming traffic from those web servers. Why my computer can still doing  internet browsing? are there any more steps I need to do for this  security set up? clamav is necessary? do I need to install SElinux or [AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")?

thx

---

### Post by doas777 on 2011-05-07
what you are noticing is called Stateful Packet Inspection.
TCP flows establish a "connection" between both systems. a connection has states like "Connecting", "Connected", and "Disconnecting". a stateful packet filter allows or denies traffic based partly on the state of the connection.

the most common stateful configuration, is to allow all outgoing traffic, and deny all incoming packets except those that are part of an existing connection (eg, one that was initiated from the inside).

[http://en.wikipedia.org/wiki/Stateful_firewall](http://en.wikipedia.org/wiki/Stateful_firewall)

---

### Post by bodhi.zazen on 2011-05-08
Thread closed. Please do not post duplicates, it results in duplication of community effort and confusion.

Your question was asked and answered here:

[http://ubuntuforums.org/showthread.php?t=1749795](http://ubuntuforums.org/showthread.php?t=1749795)

---

