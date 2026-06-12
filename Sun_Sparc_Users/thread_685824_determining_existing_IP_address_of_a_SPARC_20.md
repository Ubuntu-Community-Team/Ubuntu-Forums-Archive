---
title: "determining existing IP address of a SPARC 20"
date: 2008-02-02
forum: Sun Sparc Users
---

### Post by guitarman on 2008-02-02
Hi silly question,

I just got my Ebay SPARCstation 20 and it has no screen, keyboard or mouse,  I connected it to my laptop with a crossover cable to see if I can telnet into it, however the SPARC has a static IP address on it and I would like to determine what that is so that I can set my laptop to the same subnet.  I'm thinking of putting UBUNTU on it later on and set a new IP address, but for now I just want to  look around to see what is on this old system.

Any ideas ? or is there a shareware that I can download to use on my laptop that would ping the SPARC to reveal it's IP address?  My laptop is running WindowsXP unfortunately.

thanks, much appreciated

---

### Post by ringnebula on 2008-02-02
Easiest way to accomplish this would be with a null modem cable from your laptops serial port to the console port on the SPARC 20. You will need to know the root password to the machine or boot it in single user mode to get in without the root password (depending on the installed OS) though.

---

