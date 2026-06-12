---
title: "Apache2 not opening port 80 to outside world?"
date: 2007-11-21
forum: Server Platforms
---

### Post by lourp on 2007-11-21
A bit of a hair-puller!

Cable modem -> Netgear WGT624v3 router -> Ubuntu PC

Running Dynamic DNS, ddclient service.

I enable port forwarding of port 80 in the router. I allow a rule to accept port 80 in firestarter.

Apache2 is running, I can access my website from another PC behind the router.

However,

from the outside world, port 80 is in full stealth mode!! Won't budge!

I then experimented with other ports (SSH, FTP). When these are port forwarded on the router, and allowed in firestarter - presto - the outside world can come in. Just port 80 does not co-operate! Still scratching the noggin ...

---

### Post by p_quarles on 2007-11-21
Your ISP is probably blocking port 80. Nothing you can do about that other than switching ISPs. 

You can always configure Apache to listen on a different port, but of course that won't really allow you to run a publicly available web site.

---

### Post by lourp on 2007-11-21
I was starting to suspect the same thing. That's pretty cheeky of them, and it's also peculiar that a friend of mine on the same ISP has no problem. Stranger things have happened...

I'll find out and kick them up the bum.

Thanks for the idea about using another port - never thought of that! I only need a personal web site to access my home PC from work.

---

### Post by p_quarles on 2007-11-21
If you only need it for yourself, then changing the port will do the trick. Just edit /etc/apache2/ports.conf to listen on the port you want.

---

