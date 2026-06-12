---
title: "Disk space usage different in webmin than in command du -h"
date: 2015-11-30
forum: Server Platforms
---

### Post by rhandy2 on 2015-11-30
I have one virtual server in virtualmin shows me usage =260.94MB

But if I go to user home dir

> # du-ch
104M    total



Mysql usage 20Mb

I dont understand diference. I check all other Vhosts and are OK.

---

### Post by rhandy2 on 2015-11-30
> # quota -v user
      /dev/sda1  245988  1048576 1048576           31977       0       0




How I can Find all other 140MB of diference?

---

### Post by rhandy2 on 2015-11-30
i FOUND



> #find / -user user_to_find

ITS one backup dir out off Home Dir

---

