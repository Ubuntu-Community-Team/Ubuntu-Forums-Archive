---
title: "[SOLVED] Implications of leaving port open"
date: 2008-11-13
forum: Security
---

### Post by rideburton56 on 2008-11-13
Hello All,

I open a port to use my torrent client at my parents house, which i spend every other day at.  I always foward it to my IP at the time, but because the system uses DNS, sometimes when I log back in the next day, the router has reassigned me to new IP.  

Admittedly, sometimes I get lazy and forget to close the port when I leave for work in the morning (thus leaving it open for about 2 days).  My family runs about 4 other machines off this router, all windows.  What are the implications of doing so?

---

### Post by Kinstonian on 2008-11-13
If the router is forwarding traffic to a closed port, there isn't really any risk because there isn't any software that can be exploited that's accepting connections... the port's closed.  While you should be far more worried about things like client side attacks, I'd still try to disable the forwarding.  It's generally good to have as few holes in what's basically a firewall as possible.

---

### Post by rideburton56 on 2008-11-13
Thanks for the reply!

---

### Post by kevdog on 2008-11-13
In addition just b/c a port is forwarded -- a process needs to be listening on the port to pose a security risk.  For example, by default, all Ubuntu incoming ports are open by default.  If you forward through the router a port to host machine -- but if there is no listening process on the port, there is no security risk.

---

