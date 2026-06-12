---
title: "Load (site?) distribution for Apache server"
date: 2006-08-01
forum: Server Platforms
---

### Post by spanishwasabi on 2006-08-01
Hi,

First, my network:
I have a machine that connects me to Internet on one side with a single IP address (X.X.X.X) and to my internal network on the other (192.168.0.1).
Then, I have a server (192.168.1.2) that hosts a bunch of virtual servers among who I have several Apache2 servers (192.168.1.3, 192.168.1.4, 192.168.1.5).

I would like to let each one of the three servers take care of a different site that should be accesible from Internet ([www.a.com](www.a.com) for 192.168.1.3, [www.b.com](www.b.com) for 192.168.1.4, [www.c.com](www.c.com) for 192.168.1.5). I could create a new virtual server to install a load manager if needed be.

My problem is, I've searched for it, but the only thing I can find is load distribution links, not site distribution links, and I'm at a loss.

Any link, help or advice would be higly apreciated. Thanks!

G

---

