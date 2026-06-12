---
title: "mysql server stopped running on LAMP system"
date: 2008-11-26
forum: Server Platforms
---

### Post by jpeckenpaugh on 2008-11-26
Anybody know how I can "reset" my mysql server..?  i'd rather not have to rebuild the system, but about a month ago the mysql server just wouldn't start up one day.  now when i try to use init.d to restart the server, i get a [fail] message.

i'm using ubuntu 8.04 basic lamp setup.

it's okay if i lose the contents of the existing mysql database.  i just want to re-initialize the server process from scratch.  everything i search for on resetting mysql server is about root password resets (not the issue i'm having).

[IMG]http://ubuntuforums.org/picture.php?albumid=721&pictureid=2404[/IMG]

---

### Post by cariboo on 2008-11-26
You have to use sudo to start mysql, as a normal user type:

```
sudo /etc/init.d/mysql start
```

I get exactly the same results trying to start mysql as a normal user:

```
jim@willy:~$ /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [fail] 
jim@willy:~$ mysql -h localhost
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

Your root user doesn't really seem to be a root user.

Jim

---

### Post by jpeckenpaugh on 2008-11-26
No, the mysql service is crashed.  maybe i need to uninstall then reinstall mysql server 5, but i'm afraid that might not fix the problem & I don't want to go playing around with this server.  it has lots of other stuff installed that i don't want to have to reconfigure it all in a new system to fix the problem.

[IMG]http://ubuntuforums.org/picture.php?albumid=721&pictureid=2405[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=721&pictureid=2406[/IMG]

---

