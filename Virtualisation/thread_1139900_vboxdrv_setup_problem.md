---
title: "vboxdrv setup problem"
date: 2009-04-27
forum: Virtualisation
---

### Post by celticbhoy on 2009-04-27
when I try to run a guest os in virtualbox it tells me to run /etc/init.d/vboxdrv setup. When I run vboxdrv it says to check the log file for an error. When I check the log file it says it cant find headers file. When I run :-

sudo apt-get install build-essential linux-headers-`uname -r`

I get this :-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package linux-headers-2.6.28.3.20090331

How do I get round this.

---

### Post by bluefrog on 2009-04-27
what about an update of your system?

actual linux-headers on jaunty are 2.6.28-11.42

---

### Post by celticbhoy on 2009-04-27
I run updates every day and that is the reported kernel ???

---

