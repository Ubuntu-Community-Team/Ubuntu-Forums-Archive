---
title: "every login gives system error detected for gnome"
date: 2014-04-01
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-04-01
here it is, and message comes up more than once.

---

### Post by grahammechanical on 2014-04-01
I am using Ubuntu+Unity and I had that problem for weeks until last week. It is something that happens until the problem code is updated. In your case it seems that it is Apport that is having the nervous breakdown. You might want to see if there are any updates being held back and if one of them is regarding Apport. In my case there were a lot of updates being held back including kernel 13.19. I run apt-get dist-upgrade which brought in all the held back updates and stopped the system crash messages.

Regards.

---

### Post by sdowney717 on 2014-04-02
Hi, I just tried your idea and reboot still gives me the same error.:(

no held back packages
> boat@boat-MS-7529:~$ sudo apt-get upgrade
[sudo] password for boat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
boat@boat-MS-7529:~$ 

---

### Post by sdowney717 on 2014-04-03
I logged on using ubuntu not gnome and still get this error

---

