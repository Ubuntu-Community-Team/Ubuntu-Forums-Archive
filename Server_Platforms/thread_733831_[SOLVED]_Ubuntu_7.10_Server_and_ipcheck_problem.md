---
title: "[SOLVED] Ubuntu 7.10 Server and ipcheck problem"
date: 2008-03-24
forum: Server Platforms
---

### Post by Gooorn on 2008-03-24
Hello.

I have a problem and I hope someone can give me a direction.

I have Windows 2003 server with VMware player and Ubuntu 7.10 Server no-gui appliance.

I installed ipcheck and it works fine (that means that every cron scheduled check is performed ok) until ISP changes my IP. From that point dyndns-update doesn't work (there is no error message though) if I don't previously delete ipcheck.dat from .dyndns directory.

Windows 2003 has no problem whatsoever with DynDNS since it's updated from the router software and it's always available for RDP access.

I don't know where to start so please help me out.

For ipcheck installation I used straight forward methods described on this beloved forum.  

Thanx and BR,

Sinisa Perovic

---

### Post by Gooorn on 2008-03-30
Solved.

I removed ipcheck and went for ddclient.
IPclient has all sorts of problem regarding crone scheduling, user rights, etc.
ddclient is working "out of the box" and so far without glitch.

---

