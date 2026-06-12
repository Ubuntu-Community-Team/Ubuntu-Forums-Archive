---
title: "help - Setting up MYSQL server"
date: 2010-03-26
forum: Server Platforms
---

### Post by Gordonisnz on 2010-03-26
Good day, 

Last night I set up a servber on my local machine, & also PHp - Both working fine.

I'm trying to load up MYSQL

i have installed it, & *can* start/stop the server.  however if I do anything else with it, I get this error :-

> 
root@gordon-desktop:~# sudo mysqladmin -u root -h localhost password MYPASSWORD
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

Query :- 

1) How do I know MYSQL is actually active ? (apart from the message it says that its statrted (or stopped).

2) Is there a way to  

a) Find out the usernames that are recorded on the MYSQL server ?
b) set / RESET the 'root' username (I know MYSQL root user is different to PC root user)
c) anything else I can do on the PHP / website code to see if MYSQL is working 

(as yet, no tables / databases etc have been set up - as I can't get past this error  message - I get the same error when setting up a database.)


Ps I did allow my usermname (when logged in to ubuntu) to edit / create files in the /usr/www/ directory   (but it is still OWNED by 'root' - that directory)

Does that matter ?

PPS - I don't want to log in as root - Any time I want to update any website stuff...

---

### Post by voja15 on 2010-03-26
I think this tutorial will help you. Just scroll down to installing mysql, you will see how to change root password, to edit mysql config file etc.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Gordonisnz on 2010-03-26
I HAVE THIS TOO - status

> 

root@gordon-desktop:~# /etc/init.d/mysql status
 * /usr/bin/mysqladmin  Ver 8.42 Distrib 5.1.37, for debian-linux-gnu on x86_64
Copyright 2000-2008 MySQL AB, 2008 Sun Microsystems, Inc.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version        5.1.37-1ubuntu5.1
Protocol version    10
Connection        Localhost via UNIX socket
UNIX socket        /var/run/mysqld/mysqld.sock
Uptime:            10 hours 40 min 0 sec

Threads: 1  Questions: 100  Slow queries: 0  Opens: 99  Flush tables: 1  Open tables: 23  Queries per second avg: 0.2



according to this - MYSQL is up & running (since last night)

hopefully - oneday, I can actually do something useful :)

---

### Post by voja15 on 2010-03-26
At least it's running. :D
I've been experimenting a bit with my mysql installation (everything went fine, even installed phpmyadmin and created a database), and both mysql -u root and sudo mysql -u root throw the access denied error. But when I tried
```
mysql -u root -p
```
it prompted for password, and I could enter mysql commands after that.

Also, if you installed mysql as root, I think you wil not be able to do the changes as a normal user. I did that, and even /etc/init.d/mysql status throws an error if executed without sudo.

---

### Post by fang0654 on 2010-03-26
instead of

```

sudo mysqladmin -u root -h localhost password MYPASSWORD

```

Log into mysql with this:

```

mysql -u root -p

```

It will ask you for the root password you initially set up.  If you don't know the password, you can reset it with the following instructions:

[http://www.howtoforge.com/reset-forgotten-mysql-root-password]("http://www.howtoforge.com/reset-forgotten-mysql-root-password")

---

