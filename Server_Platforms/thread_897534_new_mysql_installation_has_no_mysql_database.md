---
title: "new mysql installation has no mysql database"
date: 2008-08-22
forum: Server Platforms
---

### Post by sawatdee on 2008-08-22
I am trying to add users to a new mysql 5.0 installation. It was installed using apt-get. CREATE USER tells me "access denied" because I don't have the create user privilege. If I try connecting to mysql with the command "sudo mysql", it tells me "access denied" whether I use a password or not. Every default installation of mysql I have worked with in the past had a default mysql table, but this one has no such table, or at least I can not see it. This is a brand new installation and I haven't changed anything yet. I searched the documentation and found nothing related to this at all. How is a person supposed to add users to this system?

---

### Post by eggdeng on 2008-08-22
The mysql root user has nothing to do with the root user on your system. Unless you set a password for the mysql root user, no such password exists. In that case, you should be able to connect to the mysql database as root with
```
mysql -u root mysql
```

---

### Post by sawatdee on 2008-08-22
Here is what I get:
```
$ mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

Also, there is no mysql database that I can see. I can connect to mysql without specifying a user, but the only database that exists is information_schema. If I try to create a user, I get:
```
ERROR 1227 (42000): Access denied; you need the CREATE USER privilege for this operation
```

---

### Post by sawatdee on 2008-08-22
Here is something else I notice when I restart the mysql server:
```
$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                              [ OK ] 
 * Starting MySQL database server mysqld                                                                              [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
```

Not sure if that has anything to do with my problem or not, but when I try to reinstall using apt-get it tells me that both mysql-server and mysql-common are already the newest versions.

If anyone knows how I can simply create a user in a default installation of mysql on ubuntu, it would be so much appreciated.

---

### Post by de0xyrib0se on 2008-08-22
Dude just read this:

[http://www.linuxweblog.com/blogs/sandip/20060330/reset-mysql-root-password](http://www.linuxweblog.com/blogs/sandip/20060330/reset-mysql-root-password)

---

### Post by de0xyrib0se on 2008-08-22
Dont forget to reboot MySQL afterwards as it has to load the grant tables :)

---

