---
title: "Ubuntu Server, preinstalled firewall?"
date: 2006-06-03
forum: Server Platforms
---

### Post by Tortanick on 2006-06-03
Just wondering if Ubuntu server edition comes with a firewall, and if so what firewall and where is config files?

---

### Post by foxmulder on 2006-06-04
I don't know about the firewall, but I do know that according to the wiki all ports that are not in use are closed by default, so this only leaves the serverports open like shh, webserver and such.

---

### Post by FredSambo on 2006-06-04
[iptables baby](http://packages.ubuntu.com/hoary/net/iptables)

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=Tortanick]Just wondering if Ubuntu server edition comes with a firewall, and if so what firewall and where is config files?[/QUOTE]

I prefer to write my own firewall rule set for **iptables** .... but there are many other choises:

- enable the recommanded repositories (see repo thread in this forum), open your prefered deb package manager and search for "firewall" .... and you'll find tools like shorewall, guarddog and more.

- or use webmin as GUI to configure your firewall rules.

Thomas

---

### Post by lanux on 2006-06-07
Hi !
Command : "iptables -L" get no rules !
This is not preconfigured firewall !
[http://scan.sygatetech.com/quickscan.html]("http://scan.sygatetech.com/quickscan.html")
ONLY CLOSED ports !

---

