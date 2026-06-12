---
title: "100% CPU load on Ubuntu 10.04.3 LTS 64bit"
date: 2011-11-04
forum: Server Platforms
---

### Post by mikeVi on 2011-11-04
Hardware: DELL Poweredge 1950, 2x Intel Xeon Quad Core E5345 @ 2.33GHz, 16 Gb mem, 2x 146Gb SAS (software RAID1)
Software: Ubuntu 10.04.3 LTS, MySQL 5.1.41

Issue: while mysql is not used and runs with no database, everything seems alright. As soon as I install a database, it has the reason to bring all 8 cores in 100% with low memory consumption. So, you can imagine the load average goes high (I saw 212 load average for the first time). The server doesn't become unresponsive, but you can see it's slow while browsing the project installed.

Additional info:

the database used is not more than 24MB and it was moved from a server with less resources and a lot more larger databases. So I don't suspect the database/project. 
my.cnf is not a reason also, as I used both default one and the one I use on the same distribution on another server.What is interesting is that mysql doesn't close any process and runs to the limit of the max_connections.
The only difference is mysql version: the old one is 5.0.51a, for debian-linux-gnu (x86_64) using readline 5 and the new one is 5.1.41, for debian-linux-gnu (x86_64) using readline 6.1
Logs are quiet. Nothing there.

I switched to this Ubuntu version after I suspected some problems in the newly Ubuntu 11.10 server. This one worked alright for an hour after I made a kernel upgrade to 3.0.1 (it was using the memory also)
I tested disk speed and seems alright.

Some more output on the running server: 

dstat -cndymlp -N total -D total 3: [IMG]http://i.stack.imgur.com/cdOJk.png[/IMG]


htop command: 
[IMG]http://i.stack.imgur.com/UXCwT.png[/IMG]

opcontrol monitoring tool when the high load is happening:
[IMG]http://i.imgur.com/BG1Fs.png[/IMG]

the issue explained in graphs
[IMG]http://i.imgur.com/KJu3e.png[/IMG]

Any other information if you want, I can provide it.
I spend a couple of days monitoring and trying different things. With no success. Any ideas?

---

### Post by BillyBoa on 2011-11-04
I had a similar problem and it disappeared installing the ATI drivers.

---

### Post by mikeVi on 2011-11-04
It has an ATI ES1000. Do you think it could cause troubles since I don't run any X?

---

### Post by mikeVi on 2011-11-08
It seems that the tiny project had some queries that even if they worked smooth on mysql5.0, they were screwing the server on mysql5.1.
Strange!

---

