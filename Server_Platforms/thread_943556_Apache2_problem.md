---
title: "Apache2 problem"
date: 2008-10-10
forum: Server Platforms
---

### Post by sigwise on 2008-10-10
I installed Apache2 under Ubuntu, and set the router, however, I can only
access my website from local network, can not visit it from outside. Does
anyone have idea about it? btw, I can ssh to my machine.
Thanks a lot.

---

### Post by lykwydchykyn on 2008-10-10
Have forwarded port 80 on your router?

---

### Post by sigwise on 2008-10-10
Yes, I have opened ports 22 and 80 in my router, ssh works fine from outside, apache2 does not work.

---

### Post by MJN on 2008-10-10
Does your ISP block incoming port 80?

Mathew

---

### Post by sigwise on 2008-10-10
> **MJN said:**
> Does your ISP block incoming port 80?

Mathew
I don't think so, I use optimum online.
I use nmap to scan ports from internet, only see 22;
while I scan on my local machine, I see 22 and 80.
I also checked apache2.conf and set "allow from all" for everything. Do I need to lower Ubuntu security level somewhere?

---

### Post by MJN on 2008-10-10
According to [http://en.wikipedia.org/wiki/Optimum_Online](http://en.wikipedia.org/wiki/Optimum_Online) running a web server is against their TOS on the 'standard' service (allowed on the 'Boost' package) and so there is every chance they are blocking port 80.

Try changing to another port (something random, say 4000) and see if that works however you may find they are actually blocking incoming HTTP requests hence this will apply equally to all ports.

Mathew

---

### Post by sigwise on 2008-10-10
> **MJN said:**
> According to [http://en.wikipedia.org/wiki/Optimum_Online](http://en.wikipedia.org/wiki/Optimum_Online) running a web server is against their TOS on the 'standard' service (allowed on the 'Boost' package) and so there is every chance they are blocking port 80.

Try changing to another port (something random, say 4000) and see if that works however you may find they are actually blocking incoming HTTP requests hence this will apply equally to all ports.

Mathew
OK, thanks a lot! I will have a try and report the result later.

---

### Post by mbeach on 2008-10-10
If you need to see what others can see, try:

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

It might indicate if your ISP is blocking port 80, or if your server/router is not responding on port 80.

---

### Post by sigwise on 2008-10-10
Yes, it is the ISP problem. I changed port number, now it works fine.
Thanks a lot for your help!

---

