---
title: "MYSQL Stops and starts constantly"
date: 2011-07-15
forum: Server Platforms
---

### Post by mcarrara on 2011-07-15
My first issue with the upgrade from 8.04 to 10.04.  I am setting up our SQL sever.  I am unable to connect from another host to run the MySQL Workbench I use to admin the database.  The monitor show that every 10-12 second the MySQL server stops and 3 seconds later it starts only to stop again in 10-12 seconds.

Is there a way to see if the MySQL server is running in real time on localhost?  I do a ps -ax and see mysqld running.  Will that show the behavior I see on the monitor?  It does not show up when I run top. Or do I really have a connection issue?

Mark

---

### Post by Wim Sturkenboom on 2011-07-15
To check from your localhost, I would simply try a *mysql yourdatabase* (possibly with credentials) and wait and see if it gets disconnected.

Forgot: mysql has a log somewhere that you can check to see if restarts occur. And a pid file that you can read; check if the pid changes might be another option.

---

### Post by mcarrara on 2011-07-15
It is the MYSQL monitor program.  The server is working fine.  

Mark

---

