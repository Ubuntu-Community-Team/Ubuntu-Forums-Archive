---
title: "zombie process?"
date: 2010-09-05
forum: Server Platforms
---

### Post by PryGuy on 2010-09-05
Good day everyone!
I have a script that mirrors Ubuntu repo every night using apt-mirror. It starts via cron of course. When I log in to server it shows me I have a zombie process. The following command explains it:> ps -el | grep 'Z'
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
5 Z     0  3488  3474  0  80   0 -     0 exit   ?        00:00:00 cron <defunct>
> ps -A | grep cron
 1120 ?        00:00:00 cron
 3474 ?        00:00:00 cron
 3488 ?        00:00:00 cron <defunct>

How do I understand all this? Thanks in advance!

EDIT: Should I demonize the cron process to avoid that?

---

### Post by BkkBonanza on 2010-09-05
Rather than me writing it out, see here,
[http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)

---

