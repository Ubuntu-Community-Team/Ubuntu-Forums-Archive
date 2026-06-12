---
title: "Server becomes very slow: how to check if it's CPU, HDD or RAM?"
date: 2010-01-08
forum: Server Platforms
---

### Post by Versusnja on 2010-01-08
Hi,

I have 2.4Ghz dual core CPU with 1Gb RAM and an old 20Gb HDD. And it worked good until I bought one web site with 4500 visitors per day. I had about 2000 before that. So, I have abt. 6000 visitors now in total.

Now the server becomes SO SLOW that it even stops responding to ssh client, not to mention that it stops serving web pages.

By htop I can see that SWAP is not used. CPU load on both cores is about 35% (which is high, I guess) and two processes, that cause it are apache2 and mysql.

While I'm pretty sure that 2,4Ghz CPU is good enough for such server load, I can't figure out, what is the reason for my problem: RAM or CPU?!...

Is there any piece of software that could help to monitor? Should I replace HDD or add RAM? Or both? Or CPU?...
I'm totally lost and my site is down. Heeeelp! :confused:

---

### Post by xtjacob on 2010-01-08
While your in ssh you can run the command "top" and it will show you the load, and the programs that are using the most resources.

---

### Post by Digger9 on 2010-01-08
Are you sure it is not a bandwidth issue?

---

### Post by Versusnja on 2010-01-08
xtjacob: as I wrote, I used htop to check it. And I see that apache2 and mysql are using CPU a lot. While 2.4GHz CPU should be definitelly enough here.

Digger9: no, I have at least 5 other working stations behind the same router with the server. They experience no lags in LAN or WAN. Plus, I see in htop that CPU usage is really high: about 35-45% on both cores. 
I mean not peak usage, but average.

---

### Post by Versusnja on 2010-01-08
I'm just wondering, how can I check if my HDD is fast enough for server's tasks? Is there any program, which may help?

---

