---
title: "Odd, cannot resolve hosted working hosted external domain names from internal network"
date: 2011-09-30
forum: Server Platforms
---

### Post by Tavorisch on 2011-09-30
Title says it all

I have some virtual web sites and a dns server with ISPconfig

last time i loaded it I could resolve everything internally..

now the server can't even resolve the own domains it is hosting.

I am behind a router port forwarding 53

Any ideas on why this would happen? anyone from outside resolves everything just fine.

---

### Post by Tavorisch on 2011-09-30
So my guess is that my ISP's DNS servers won't resolve the name back to my IP address because I just changed my resolv.conf to my local IP first and then my ISPs and the server is able to ping all domains but the other computer on the network is not....

---

### Post by Tavorisch on 2011-09-30
To clarify,

anyone outside my internal network can resolve ALL my domain names just fine.  Internally the server can now with itself at the top of resolvconf.

My other machine which has perfect internet access on the same network cannot resolve ANY of the domain names... MAKES NO SENSE.

---

### Post by Tavorisch on 2011-09-30
what a retarded issue, I don't even care anymore SOLVED by adding my servers local ip into my other machine's DNS.

---

