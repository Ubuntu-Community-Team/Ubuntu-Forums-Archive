---
title: "mysql won't start..."
date: 2008-10-29
forum: Server Platforms
---

### Post by alecjw on 2008-10-29
alec@Jupiter:~$ sudo /etc/init.d/mysql restart
[sudo] password for alec: 
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
alec@Jupiter:~$ 



Then when I run mysqld to get a more verbose output:
alec@Jupiter:~$ mysqld
081029 11:45:02 [Warning] Can't create test file /var/lib/mysql/Jupiter.lower-test
081029 11:45:02 [Warning] Can't create test file /var/lib/mysql/Jupiter.lower-test
081029 11:45:02 [Warning] One can only use the --user switch if running as root

081029 11:45:02  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
alec@Jupiter:~$ 



Anyone know what the problem is?

---

### Post by leg on 2008-10-29
Add the mysql user to the group that does have acces to that directory.

---

### Post by alecjw on 2008-10-29
Already is :(

alec@Jupiter:~$ ls -l /var/lib/ | grep mysql
drwxr-xr-x 3 mysql    mysql    4096 2008-10-29 11:44 mysql
drwxr-xr-x 2 root     root     4096 2008-09-19 14:23 mysql-cluster
alec@Jupiter:~$ groups mysql
mysql
alec@Jupiter:~$

---

### Post by leg on 2008-10-29
<snip>

oops your not interested in the cluster dir are you.

---

### Post by alecjw on 2008-10-29
I did think of that, but im not sure if mysql needs access to mysql-common... you might be right though...

---

### Post by leg on 2008-10-29
Can you verify if indeed mysql has not started as your server may be running and just unable to write to the log. You have had it running as your first post shows that you stopped it first.

You could also just create the file required as root and then change the owner of the file. Shouldn't have to I know but it could be a quick fix.

---

### Post by alecjw on 2008-10-29
Drupal says it cant contact the mysql database so im guessing its completely down....

---

### Post by alecjw on 2008-10-29
I tried chowning /etc/share/mysql-common to mysql:mysql, but it still wont start

And i've tried apt-get purging it and reinstalling

---

### Post by leg on 2008-11-03
> **alecjw said:**
> Drupal says it cant contact the mysql database so im guessing its completely down....If using Drupal which user(mysql) are you accessing the database with. I only ask as Drupal requires an account that has a password set on it. Mysql root user has no password by default. I have another user created for Drupal and add this user to the permitted users list for a database.

---

