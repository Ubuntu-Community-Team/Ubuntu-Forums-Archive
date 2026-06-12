---
title: "Snort questions"
date: 2009-11-18
forum: Security
---

### Post by methodtwo on 2009-11-18
Hi there
I'm running a network with just three nodes.One is my router.The others are one wifi client and one wired client.Is there any point in me running snort on the wired client?.I'm guessing not as a hids, on each system(except the router of course) would be more appropriate right?
Also if i did download snort from the repositories would apt-get automatically install the snort rules for me?
Thankyou for your time

---

### Post by Sarmacid on 2009-11-18
I wouldn't see necessary to install snort on a pc behind a rounter unless you're running some services, but that's always up to everybody's paranoia level. As to rules after installing snort from apt-get, yes, you get the rules with it, the package snort-rules-default is listed as a dependency, but I still suggest running oinkmaster to keep them up to date.

---

