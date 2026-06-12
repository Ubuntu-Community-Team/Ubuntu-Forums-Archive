---
title: "Pass traffic from port 27960(on pc) to 5190(on router) by firestarter"
date: 2008-05-01
forum: Security
---

### Post by hullap on 2008-05-01
Um....
Well......
as the title suggests
(im not sure if this is the right section :()

---

### Post by HermanAB on 2008-05-01
Use the iptables redirect feature.

/sbin/iptables -t nat -I PREROUTING -p tcp --dport 27960 -j REDIRECT --to-port 5190


Cheers,

Herman

---

### Post by hullap on 2008-05-01
> **HermanAB said:**
> Use the iptables redirect feature.

/sbin/iptables -t nat -I PREROUTING -p tcp --dport 27960 -j REDIRECT --to-port 5190


Cheers,

Herman

but will i have to do it everytime my computer restarts or my router?

---

