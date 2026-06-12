---
title: "Mysql using 100% CPU"
date: 2008-04-19
forum: Server Platforms
---

### Post by robboardman on 2008-04-19
I Had a system happily running on Ubunutn 6.06 server until Thursday last week when I backed off all the data, and installed UBUNTU 7.10, Every so often the mysql processes consumes 100% cpu, causing other processes to stall after a while, the only thing I can do to ensure the stability of the server is to stop mysql, but I need it on the server, for the task in hand

Any advice of how to trouble shoot would be greatly appreciated, but I have already seen the high cpu bugs against the mysql-server-5 in launchpad, and the fixes suggested don't seem to work

Thanks in advance

Robb

---

### Post by DBrocks on 2008-04-19
Please post your system specs.

---

### Post by robboardman on 2008-04-20
it s a dual core xeon HP DL380 with 2Gb ram, without mysql runninbg the looa averages are 0.04 etc

Regards 
Robb

---

### Post by ikonia on 2008-04-20
enable mysql logging, see if there is a specific statment that is using the resource (causing a loop etc.)

If you are using multiple mysql depeant apps (say etomie, vbultin, torrentflux) try only enable one at a time to run to see if it is specific applications casuing a loop

View the start up / shut down logs, it could be doing something like to trying to replicate to a non-exisistant host and getting a lock ?

Increase the debug level.

---

### Post by Dr Small on 2008-04-20
Have you attempted to stop and restart the MySQL server?

---

