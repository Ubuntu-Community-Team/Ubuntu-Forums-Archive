---
title: "Dionaea is not getting hits"
date: 2013-06-26
forum: Security
---

### Post by elementX on 2013-06-26
Hi,

I installed dionaea and it seems to work fine. However it is not getting any hits, doesn't seem to be collecting any malware.
It might be(and probably is) due to a config file. I tried to follow an online guide but I might be missing something.
Do you have any suggestions? If necessary I'll post bits of my config file or explain the setting. 
I checked my dionaea-log and the only line is: python module.c:416-error: Import failed dionaea.services

---

### Post by unspawn on 2013-06-26
> **elementX said:**
> If necessary I'll post bits of my config file or explain the setting. IMHO you should start by providing as much information as possible: which version of Dionea, the command line you start it with, any changes from the default setup or configuration and anything else you think might be useful. > **elementX said:**
> I checked my dionaea-log and the only line is: python module.c:416-error: Import failed dionaea.servicesIf you start Dionea with "*-D*" try to start it without it. Else also try explicitly adding *-l all,-debug -L '*'* and post stdout / stderr / log file contents.

---

### Post by elementX on 2013-06-27
It's working now.

Solution: I first installed it using apt-get. For whatever reason this doesn't work(maybe someone with better skills can fix it) but then I installed it again this time following step-by-step instructions from dionaea homepage: [http://dionaea.carnivore.it/#compiling](http://dionaea.carnivore.it/#compiling)

---

