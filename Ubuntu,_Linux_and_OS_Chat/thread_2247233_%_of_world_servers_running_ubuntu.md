---
title: "% of world servers running ubuntu ?"
date: 2014-10-06
forum: Ubuntu, Linux and OS Chat
---

### Post by fkkroundabout on 2014-10-06
is there any reliable way to find this statistic ? or is this as unreliable to measure as asking which is the most popular browser ?

i have heard amazon and wikipedia is run on ubuntu, i think ?

---

### Post by grahammechanical on 2014-10-06
How long is a piece of string?

First, tell us how many servers there are? We need the 100% mark in order to calculate a percentage of it. 

> [COLOR=#333333][FONT=Ubuntu]Global enterprises including AT&T, Bharti, Bouygues Telecom, British Telecom, China Telecom, China Unicom, Cogent Communications, Comcast, Deutsche Telekom, Korea Telecom, NEC, NTT, Numergy, Orange France, Time Warner Cable, Turk Telecom, Verizon and Yandex, as well as leading web scale services such as Netflix, Instagram, Hipchat and Quora are all building next generation services on Ubuntu.[/FONT][/COLOR]

[https://insights.ubuntu.com/2014/04/15/ubuntu-14-04-lts-the-cloud-platform-of-choice/](https://insights.ubuntu.com/2014/04/15/ubuntu-14-04-lts-the-cloud-platform-of-choice/)

One thing is certain, Canonical is not sitting back and waiting for people to knock on its door. Putting aside the enthusiastic words about their own product it certainly seems as if Canonical is getting out and about and making partnerships.

[https://insights.ubuntu.com/topic/server/?cat=1172](https://insights.ubuntu.com/topic/server/?cat=1172)

Regards.

---

### Post by tgalati4 on 2014-10-06
1% plus or minus 1%.  

Maybe more.

---

### Post by lammert-nijhof on 2014-10-13
According to Wikipedia 38% of the serves are Linux based. A little bit more than 20% is Ubuntu, which gives us that about 8% of all servers are Ubuntu.

---

### Post by tgalati4 on 2014-10-14
I was close.

---

### Post by SeijiSensei on 2014-10-14
I don't think this number is at all knowable.

First, many measures of "Linux servers" count hardware shipments.  So machines shipped without an OS, on which Linux is later installed, do not count, nor do systems where was Windows was installed and later wiped and replaced with Linux. 

Second, virtualization makes all these numbers suspect.  Suppose I have a server with 16 virtual machines, twelve running Linux and four running Windows.  How are such systems included in the calculation?  If we just count hardware, there is only one server, and whether it's Linux or Windows depends on the choice of host operating system.

Next, the combination of virtualization and cloud computing adds yet another round of complications.  I maintain virtual servers at Linode.  How many other clients are sharing a physical machine with me depends on the level of service I pay for.  For the cheapest plans, the number could be something like 48 VMs or more per physical server.  

There is simply no way to calculate this number any more.

---

