---
title: "Need a little help with Ventrilo 2.3.1 Server."
date: 2006-11-23
forum: Server Platforms
---

### Post by T.Louis on 2006-11-23
Hello,

I'm trying to set up a Ventrilo server, and I just downloaded 2.3.1. Everything works fine except for one thing, I can only connect to the Ventrilo server on the local network with a client (192.168.0.x).

My routers port fowarding for 3784 is set correctly as I've run the Ventrilo server on the same network on a Windows XP machine and it works fine connecting from outside the network.

I'm guessing it has something to do with the iptables, and I've tried to open the 3784 port for Ventrilo, but I might not be doing it right.

At this time I've spent 2-3 hours trying everything to get it working but I'm just hitting a wall ](*,) ... any suggestins are welcome.

Thank you in advance.

---

### Post by T.Louis on 2006-11-23
*bump*

---

### Post by T.Louis on 2006-11-23
I tried this... it seems to not work.

```

iptables -A INPUT -p tcp --source-port 3784 --destination-port 3784 -j ACCEPT

```

---

### Post by T.Louis on 2006-11-24
Burrr... talking to myself in this thread, but I resolved it by updating my routers firmware, bad bad D-Link router firmware.

---

