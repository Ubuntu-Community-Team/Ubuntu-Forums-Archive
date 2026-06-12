---
title: "Mysql server problem"
date: 2010-07-11
forum: Server Platforms
---

### Post by asai on 2010-07-11
Hi,
I installed a new database into my MySQL server. This database works very well, but all other databases is gone!
Fortunately I have backup of my databases, but I can't get them restored.
Problem is that the root user get access denied.
How can this happen, and is there any way to restore the root@localhost users password?

---

### Post by DaithiF on 2010-07-11
Hi,
there are several ways to reset the root password for mysql.  this is one:

1. stop mysql running:
```
sudo service mysql stop

```
2. create an init-file, somewhere accessible by the mysql user
```
vi /tmp/mysql-init.sql
```
with this content:  -- obviously use whatever password you want :)
```
grant all privileges on *.* to 'root'@'localhost' identified by 'yournewpassword' with grant option;
```
make sure it is readable 
```
chmod 644 /tmp/mysql-init.sql
```

3. start mysqld manually, passing in the location of this init file:
```
sudo /usr/sbin/mysqld --user=mysql --init-file=/tmp/mysql-init.sql &

```

hit return a couple of times if necessary to get back to a prompt, then test you have access:
```
mysql -h localhost -u root -pyournewpassword

```
this should log you in, if so, type exit and hit return to quit mysql.

assuming all is good so far, kill the running instance
```
sudo pkill mysqld

```
and start it using the normal method
```
sudo service mysql start
```

and that should be it.

---

### Post by asai on 2010-07-11
Thanks a lot!! :D
That was the solution! Everything works perfectly again.
I also found out what I did wrong: I somehow managed to grant only privileges to the new database I created, leaving all the existing databases unavailable. :oops:

---

