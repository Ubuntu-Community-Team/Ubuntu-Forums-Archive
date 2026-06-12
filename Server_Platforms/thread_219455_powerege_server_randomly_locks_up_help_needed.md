---
title: "powerege server randomly locks up help needed"
date: 2006-07-20
forum: Server Platforms
---

### Post by mrweirdo on 2006-07-20
Hell I'm runing ubuntu server on a 4u dell p3 poweredge 1400 system that lately has started randomly locking up about every 3-5 days or so at random. I have to go and manualy reset the machine. Basicly it servers as a router, dchp, dns, samba server atm.  How can I find out what is causing the random lockups? by looking at certain logs, etc? hopefully some has some ideas.

---

### Post by mrweirdo on 2006-07-20
hrm think i found what is causing. Itss releated to network activity for example i i do something that causes a heavy network load across any of the three different nics it causes the ubuntu to lock completly. One test that I know for sure locks it is if I issue the comand:
yes /dev/null

from a remote ssh sesion the system crashes about 15-20 seconds later. Now if I run that same comand locally from a terminal session on the box it can run for ever all be it slows the system down somewhat. Hence it has to be caused by network loads. I also am using the SMP kernel.

---

### Post by mrweirdo on 2006-07-20
Just as i suspected it has something to do with the smp kernel in ubuntu package linux-686-smp (2.6.15.24) because runing with the regular single proc kernel doesnt have the same problem however I lost half my processing power that way.

---

