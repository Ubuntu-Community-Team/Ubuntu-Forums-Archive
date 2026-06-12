---
title: "Ebox on Intrepid"
date: 2009-03-17
forum: Server Platforms
---

### Post by mrsteveman1 on 2009-03-17
I've looked around the forums, read some of the launchpad lists about this bug but have not yet found a solution.

We currently host on Ubuntu 8.10 (large websites, 10,000+ visitors a day), and are tired of webmin. The Ubuntu server manual mentions ebox and it looks like it might be worth checking out, however with the stock repositories the ebox package has an unmet dependency, one of the apache auth modules i think. It refuses to install ebox. Adding the repository listed on the Ebox website allows it to install, then running it fails with an Orbit error of some kind.

So does anyone know how to actually get Ebox working on Intrepid?

---

### Post by lawbadman on 2009-03-19
Good question I have a similar problem. I have been searching but no one seems to have a solid fix.

Anyone know of a proper fix?

---

### Post by drave on 2009-03-27
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe

put that into sources.list , update and away you go

i'd be cautious though 
i tried it and uninstalled it because the firewall module blocked ssh and ebox itself, even though there were supposed to be rules to let them through.

---

