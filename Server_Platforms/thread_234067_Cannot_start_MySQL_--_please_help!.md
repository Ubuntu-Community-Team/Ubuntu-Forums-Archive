---
title: "Cannot start MySQL -- please help!"
date: 2006-08-10
forum: Server Platforms
---

### Post by ryharv on 2006-08-10
Hello everyone,

I am having serious problems getting mysql up and running.  I installed with sudo apt-get install mysql-server.  

Now, just to get the thing running, here is what I get:

```
ryan@rybuntu:/var/run$ mysqld
060810 19:41:48 [Warning] Can't create test file /var/lib/mysql/rybuntu.lower-test
mysqld: Can't change dir to '/var/lib/mysql/' (Errcode: 2)
060810 19:41:48 [ERROR] Aborting

060810 19:41:48 [Note] mysqld: Shutdown complete
```

When I try to run mysqladmin to set up the root password, I get:

```
ryan@rybuntu:/var/run$ mysqladmin -u root password mypassword
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

I don't even have a directory /var/run/mysqld, let alone the mysqld.sock file inside it!  

I'm very, very lost here.  Please help!

---

### Post by meng on 2006-08-10
Can you start with:
sudo mysqld

---

### Post by ryharv on 2006-08-11
I actually took the advice from the post located here

[http://www.ubuntuforums.org/showthread.php?t=78614](http://www.ubuntuforums.org/showthread.php?t=78614)

and removed mysql v5.0 

and installed mysql-server-4.1.  now everything works fine, but unfortunately i can't test starting mysql 5 using sudo.

---

