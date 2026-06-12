---
title: "mysql ran out of space, now cannot start"
date: 2007-10-18
forum: Server Platforms
---

### Post by mklein9 on 2007-10-18
Hi -- running 6.06 LTS with mysql 14.12 Distrib 5.0.22.

I was loading a database table from a file (LOAD INFILE) and ran out of disk space in the /var partition that mysql uses by default to store databases.  I (maybe dumbly) killed the mysql process after watching it do nothing for hours (it was waiting for more disk space to become available, which I figured out later :-(), modified /etc/mysql/my.cnf to place the datadir in a larger partition, copied the entire contents of /var/lib/mysql to the new location, preserving ownerships and permissions, and tried restarting mysqld.

Now mysqld does not start successfully anymore at all, and I have not found any solutions from googling.

Attempting to start with "/etc/init.d/mysql start" results in:

/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld/sock' exists!

Well, the socket doesn't exist and it is not created when attempting the start.  Instead, mysqld does in fact start running, according to 'ps' and 'top', and immediately sucks up 100% CPU time.  But nothing can connect to it and it appears to be in an infinite loop.  /etc/init.d/mysql status reports "MySQL is stopped."

What could be the problem here?  I am unable to figure this out so far.

---

### Post by ntom-taylor on 2007-10-18
I cannot offer a solution to your problem, but the same thing happened to me when i tried to install some updates, literally just crashed during the update process, couldn't login ..etc all the works. Finally just did a reinstall.

---

### Post by KNiT3 on 2007-10-18
First run "fsck" then check if the problem persists.
If it does, then revert your configuration changes and try using "mount" to mount the relocated directory to its original place. That should work w/o reinstalling stuff (<- not really professional). If it worked, then you can do a grep -r /var/<your directory> /etc and see which cfg file you did forgot to modify ;)

---

