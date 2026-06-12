---
title: "Gateway Firewall"
date: 2010-08-31
forum: Security
---

### Post by Monem on 2010-08-31
Hello all' i'm trying to setup a gateway to my internal network using giptabless-1.1 and squid proxy and web cache but giptables-1.1 dosen't working with me and i trying to look find support but seem the developers of giptables their last release was in 2003, so do any one implemented giptables firewall?

---

### Post by BkkBonanza on 2010-08-31
I wouldn't bother with a firewall that hasn't been updated in 7 years.

For a gateway you're going to be adding iptables rules for NAT and routing anyway so  just add any port forwarding and firewall rules you want along with that. Or run one of the router/gateway web panels around like eBox or monoWall etc.

---

### Post by anomie on 2010-09-01
[QUOTE=BkkBonaza]Or run one of the router/gateway web panels around like eBox or monoWall etc.[/QUOTE]

Exactly. If you're OK with a pre-packaged solution, then check out [pfsense](http://www.pfsense.org/), [m0n0wall](http://m0n0.ch/wall/), [ipcop](http://sourceforge.net/apps/trac/ipcop/wiki), et al.

---

