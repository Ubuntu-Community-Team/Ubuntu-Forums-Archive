---
title: "'The server is not configured as slave' ??"
date: 2006-09-17
forum: Server Platforms
---

### Post by kpm on 2006-09-17
Hi, I opted to install the LAMP version of the server because I have set up WAMP servers before and assumed I could find my way around, find out where and how the setup was located and configured... so far that has proved trying... I was just playing with the MySQL server, still don't know where it stores data, but I wanted to be able to start, stop, and restart it using mysqladmin command so I was able to stop it, but then when I try to start it I am getting something I have never seen before, 'The server is not configured as slave...'  I pasted it all below...  I can restart it by rebooting the server, but would rather figure out what is going on here...
```

server@host:/usr/bin$ mysqladmin version -u userName -p
Enter password:
mysqladmin  Ver 8.41 Distrib 5.0.22, for pc-linux-gnu on i486
Copyright (C) 2000 MySQL AB & MySQL Finland AB & TCX DataKonsult AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version          5.0.22-Debian_0ubuntu6.06.2-log
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 44 min 4 sec

Threads: 1  Questions: 327  Slow queries: 0  Opens: 0  Flush tables: 1  Open tables: 17 Queries per second avg: 0.124
user@host:/usr/bin$ mysqladmin stop -u root -p
Enter password:
Slave stopped
user@host:/usr/bin$ mysqladmin start -u root -p
Enter password:
mysqladmin: Error starting slave: The server is not configured as slave; fix in config file or with CHANGE MASTER TO
user@host:/usr/bin$

```

---

### Post by chrisfay on 2006-09-17
Do you get that error when starting it with:

```
sudo /etc/init.d/mysql start
``` 

If you are trying to get to a mysql cmnd prompt:

```
sudo mysql -u root -p
```

> I was just playing with the MySQL server, still don't know where it stores data

Databases files directory:

/var/lib/mysql

---

### Post by kpm on 2006-09-17
Thanks for the reply.

I am able to get to the command line... I am actually ssh'd into the server from a laptop on the lan... but I have never seen that 'Error starting slave' before... However, I learned that the MySQL server was still running after i issued the stop command... I logged in to a PhpMyAdmin and saw the DB was still up and running... so not sure what 'slave' stopped and failed to start again...

It gets a bit confusing reading MySQL documentation from the MySQL web site when they disscuss a certain setup, and then when seeing the Ubuntu LAMP install does not have the same configuration but has no documentation about that config (that I can find anyway)... but I will muddle through, and try to document it all...

Thanks

---

### Post by chrisfay on 2006-09-18
> It gets a bit confusing reading MySQL documentation from the MySQL web site when they disscuss a certain setup, and then when seeing the Ubuntu LAMP install does not have the same configuration but has no documentation about that config 

What documentation are you referring to and what are you trying to do?

The default commands and file locations/configurations for MySql are well documented for each distro. I am curious to know what is conflicting.  

I'm also not sure why you are trying to stop and start your MySql server using mysqladmin commands when you should be using:

```
sudo /etc/init.d/mysql start
sudo /etc/init.d/mysql stop
```

You can always double check that MySql is running by typing:

```
ps aux | grep mysql
```

---

