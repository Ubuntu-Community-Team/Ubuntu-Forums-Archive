---
title: "Mysql Start error"
date: 2008-12-29
forum: Server Platforms
---

### Post by Drezard on 2008-12-29
Mysql will not start and I can not work out how to fix the issue. In Syslog its showing that it thinks something else is running on port 3306 as shown by this (please excuse the timestamps):

> 
Dec 31 06:29:56 lamp mysqld[3393]: 081231  6:29:56 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Dec 31 06:29:56 lamp mysqld[3393]: 081231  6:29:56 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Dec 31 06:29:56 lamp mysqld[3393]: 081231  6:29:56 [ERROR] Aborting
Dec 31 06:29:56 lamp mysqld[3393]:
Dec 31 06:29:56 lamp mysqld[3393]: 081231  6:29:56  InnoDB: Starting shutdown...
Dec 31 06:29:59 lamp mysqld[3393]: 081231  6:29:59  InnoDB: Shutdown completed; log sequence number 0 43655
Dec 31 06:29:59 lamp mysqld[3393]: 081231  6:29:59 [Note] /usr/sbin/mysqld: Shutdown complete
Dec 31 06:29:59 lamp mysqld[3393]:
Dec 31 06:29:59 lamp mysqld_safe[3429]: ended
Dec 31 06:30:11 lamp /etc/init.d/mysql[3595]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Dec 31 06:30:11 lamp /etc/init.d/mysql[3595]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Dec 31 06:30:11 lamp /etc/init.d/mysql[3595]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Dec 31 06:30:11 lamp /etc/init.d/mysql[3595]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Dec 31 06:30:11 lamp /etc/init.d/mysql[3595]:


But this shows no other mysql server is running:
> 
lamp:/var/log# ps aux | grep mysql
root     18123  0.0  0.2   3116   712 pts/0    S+   10:52   0:00 grep mysql


What can I do to fix this?

Daniel

---

### Post by lykwydchykyn on 2008-12-30
What does this command show?
```

sudo netstat -tunap |grep 3306

```

Also, is this the stock mysql package and config from the repos, or have you changed anything? (file locations, config file, directory permissions, etc).  Are you starting it using the init script, or by running mysqld directly?

Finally, are you using the repository version, or something like XAMPP?

---

### Post by Drezard on 2008-12-30
The netstat shows nothing is running on port 3306. Wierd isn't it.

Im using the repo package, standard, nothing changed in the configs either. Im not using XAMPP, because I believe its terribly insecure. 

Plus, im using the command:
> 
/etc/init.d/mysql start


Any other ideas?

Daniel

---

### Post by david_lynch on 2008-12-30
If it can't bind to port 3306, either something else is listening on that port, or you don't have rights to bind to the port. In either case it sounds like something is wrong there. Has anybody else had access to the machine?

---

### Post by lykwydchykyn on 2008-12-30
> **Drezard said:**
> The netstat shows nothing is running on port 3306. Wierd isn't it.

Im using the repo package, standard, nothing changed in the configs either. Im not using XAMPP, because I believe its terribly insecure. 

Plus, im using the command:


Any other ideas?

Daniel

Are you using sudo with that command?  Or in a shell owned by root (e.g., via sudo -s or sudo -i)?  That would certainly account for the error.

---

### Post by Drezard on 2008-12-30
Its actually a Debian server. (I figure the problem would be the same on Ubuntu, plus Debian has almost no good forums, none like Ubuntus), so im logged in as root. This machine is currently on the inside LAN with no ability to connect to it via the internet on any port, but I plan to stick this on the DMZ once its up and running. No one else has access to it or really knows it exists as of yet, its fairly locked down otherwise and had Debian 5 Lenny installed only 2 days ago so, Im fairly confident theres been no hax or no one has screwed with it. I can rkhunter it and check other connection and auth logs if thats all thats left but Im almost 100% certain nothing like that has happened. 

Any other ideas?

Daniel

---

### Post by Drezard on 2008-12-30
Sweet as...

Looks like its a full format and reinstall. 

*Solved*

Daniel

---

