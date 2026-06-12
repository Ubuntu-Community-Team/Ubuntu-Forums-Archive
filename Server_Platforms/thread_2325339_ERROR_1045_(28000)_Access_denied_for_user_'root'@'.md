---
title: "ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)"
date: 2016-05-21
forum: Server Platforms
---

### Post by devrekli on 2016-05-21
Hello. I can not login to MySQL. I thought it was the wrong password and I tried to change the password..

It has no need to change the password. Because the password is right. **The password is right, but I still can not login mysql**. why? help me please, thanks.

```
root@PC:/home/PC# sudo /etc/init.d/mysql stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
mysql stop/waiting
root@PC:/home/PC# pkill -9 mysql
root@PC:/home/PC# pkill -9 mysqld
root@PC:/home/PC# pkill -9 mysqld_safe
root@PC:/home/PC# ps -ef |grep mysql
root     27690 25962  0 19:51 pts/1    00:00:00 grep --color=auto mysql
root@PC:/home/PC# kill 27690
bash: kill: (27690) - No such process
root@PC:/home/PC# kill 25962
root@PC:/home/PC# ps uaxww | grep -i mysql
PC    24175  0.7  3.8 818760 156020 ?       Sl   19:29   0:10 /usr/lib/firefox/firefox /media/DA94-D856/c/How to Recover_Reset forgotten MySQL root Password on Linux _ 2daygeek.htm
root     27695  0.0  0.0  13588   944 pts/1    S+   19:52   0:00 grep --color=auto -i mysql
root@PC:/home/PC# kill 27695
bash: kill: (27695) - No such process
root@PC:/home/PC# kill 13588
bash: kill: (13588) - No such process
root@PC:/home/PC# sudo mysqld_safe --skip-grant-tables &
[1] 27701
root@PC:/home/PC# 160518 19:53:57 mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.
160518 19:53:57 mysqld_safe Logging to '/var/log/mysql/error.log'.
160518 19:53:57 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
root@PC:/home/PC# mysql -uroot
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.5.34-0ubuntu0.12.04.1 (Ubuntu)

Copyright (c) 2000, 2013, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> update user set password=PASSWORD("mypw") where User='root';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 3  Changed: 0  Warnings: 0

mysql> update user set password=PASSWORD("newpw") where User='root';
Query OK, 3 rows affected (0.00 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> quit
Bye
root@PC:/home/PC# sudo /etc/init.d/mysql stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
root@PC:/home/PC# sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
mysql start/running, process 28137
root@PC:/home/PC# mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

_(or  dpkg-reconfigure mysql-server-5.5)_

```
PC@PC:~$ sudo dpkg-reconfigure mysql-server-5.5
[sudo] password for PC:
mysql stop/waiting
160513  7:09:38 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
mysql start/running, process 4046
PC@PC:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
PC@PC:~$ 
```

```
sudo /etc/init.d/mysql stop
sudo mysqld_safe --skip-grant-tables &
mysql -uroot
use mysql;
update user set password=PASSWORD("newpw") where User='root';
flush privileges;
quit
sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start
```

**Error log** [http://pastebin.com/HN2tGhJJ](http://pastebin.com/HN2tGhJJ)

**etc/mysql/my.cf** [http://pastebin.com/cMSdGUei](http://pastebin.com/cMSdGUei)

---

### Post by Habitual on 2016-05-23
[http://stackoverflow.com/questions/10299148/mysql-error-1045-28000-access-denied-for-user-billlocalhost-using-passw#11216911](http://stackoverflow.com/questions/10299148/mysql-error-1045-28000-access-denied-for-user-billlocalhost-using-passw#11216911)
suggests what the issue may be.

Possibly 
```
sudo dpkg-reconfigure mysql-server
``` may "correct" the problem.

---

### Post by devrekli on 2016-05-23
thanks but 

```
PC@PC:~$ sudo dpkg-reconfigure mysql-server-5.5
[sudo] password for PC:
mysql stop/waiting
160513  7:09:38 [Warning] Using unique option prefix key_buffer instead  of key_buffer_size is deprecated and will be removed in a future  release. Please use the full name instead.
mysql start/running, process 4046
PC@PC:~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): **Access denied for user 'root'@'localhost' (using password: YES)**
PC@PC:~$
```

I tried it but it did not happen. root privileges may have been deleted.

[B]use mysql;
grant all on *.* to 'root'@'localhost';[/B]

```
[sudo] password for PC-2: 
root@PC-2:/home/PC-2# mysql -u root -pFalanca_mypw
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
root@PC-2:/home/PC-2# grep password /etc/mysql/debian.cnf
password = vwSY1PE7GgDRUbB7
password = vwSY1PE7GgDRUbB7
root@PC-2:/home/PC-2# mysql -u debian-sys-maint -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 71
Server version: 5.5.34-0ubuntu0.12.04.1 (Ubuntu)

Copyright (c) 2000, 2013, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> grant all on *.* to 'root'@'localhost';
ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)
```

---

### Post by Habitual on 2016-06-15
> **devrekli said:**
> I tried it but it did not happen. root privileges may have been deleted.

[B]use mysql;
grant all on *.* to 'root'@'localhost';[/B]
Wildcard "%" hosts were deleted, some included the mysql_root_user during the "security" script run.
test db also removed (can can verify with "show databases;" in mysql > )?
db users with no password got a password.

---

### Post by devrekli on 2016-06-15
> **Habitual said:**
> Wildcard "%" hosts were deleted, some included the mysql_root_user during the "security" script run.
test db also removed (can can verify with "show databases;" in mysql > )?
db users with no password got a password.

**select host,user from mysql.user;**
```
+-----------+------------------+
| host      | user             |
+-----------+------------------+
| 127.0.0.1 | root             |
| ::1       | root             |
| PC-2     |                  |
| PC-2     | root             |
| localhost |                  |
| localhost | debian-sys-maint |
| root      |                  |
+-----------+------------------+
```

**mysql> show databases;**

```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| DB     |
| mysql              |
| performance_schema |
| test               |
+--------------------+
```
**mysql> show tables;**

```
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              |
| db                        |
| event                     |
| func                      |
| general_log               |
| help_category             |
| help_keyword              |
| help_relation             |
| help_topic                |
| host                      |
| ndb_binlog_index          |
| plugin                    |
| proc                      |
| procs_priv                |
| proxies_priv              |
| servers                   |
| slow_log                  |
| tables_priv               |
| time_zone                 |
| time_zone_leap_second     |
| time_zone_name            |
| time_zone_transition      |
| time_zone_transition_type |
| user                      |
+---------------------------+
```

I think root user undeleted but It does not have permission to connect.
thanks

---

### Post by Habitual on 2016-06-15
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset) is the best I got.

---

### Post by devrekli on 2016-06-16
> **Habitual said:**
> [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset) is the best I got.

Thanks but I've tried it many times. See my first post, please. [http://ubuntuforums.org/showthread.php?t=2325339&p=13492776#post13492776](http://ubuntuforums.org/showthread.php?t=2325339&p=13492776#post13492776)

```
sudo /etc/init.d/mysql stop
sudo mysqld_safe --skip-grant-tables &
mysql -uroot
use mysql;
update user set password=PASSWORD("newpw") where User='root';
flush privileges;
quit
sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start
```

```
mysql> update user set password=PASSWORD("newpw") where User='root';

Query OK, 3 rows affected (0.00 sec)

Rows matched: 3  Changed: 3  Warnings: 0

mysql> flush privileges;

Query OK, 0 rows affected (0.00 sec)
mysql> quit

Bye
root@PC:/home/PC# sudo /etc/init.d/mysql stop
Rather than invoking init scripts through /etc/init.d, use the service(8)

utility, e.g. service mysql stop
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql

root@PC:/home/PC# sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
mysql start/running, process 28137

root@PC:/home/PC# mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES) 
```

It gives the same error when I change the password.

---

### Post by Habitual on 2016-06-16
```
UPDATE user SET Password = PASSWORD('newpwd') where User='root'; 
```
NOT
```
update user set password=PASSWORD(**[COLOR=#ff0000]"[/COLOR]**newpw**[COLOR=#ff0000]"[/COLOR]**) where User='root';
```

Single quotes for 'newpw'.

Let us know.

---

### Post by devrekli on 2016-06-18
> **Habitual said:**
> ```
UPDATE user SET Password = PASSWORD('newpwd') where User='root'; 
```
NOT
```
update user set password=PASSWORD(**[COLOR=#ff0000]"[/COLOR]**newpw**[COLOR=#ff0000]"[/COLOR]**) where User='root';
```

Single quotes for 'newpw'.

Let us know.

thanks but ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```
PC-2@PC-2:~$ sudo /etc/init.d/mysql stop
[sudo] password for PC-2: 
Rather than invoking init scriPC through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
mysql stop/waiting
PC-2@PC-2:~$ sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
[1] 6816
PC-2@PC-2:~$ 160618 11:41:47 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
PC-2@PC-2:~$  mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.5.34-0ubuntu0.12.04.1 (Ubuntu)

Copyright (c) 2000, 2013, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql>    UPDATE mysql.user SET Password=PASSWORD('newpd') WHERE User='root';
Query OK, 3 rows affected (0.02 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

Aborted
PC-2@PC-2:~$ sudo /etc/init.d/mysql stop
Rather than invoking init scriPC through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
PC-2@PC-2:~$ sudo /etc/init.d/mysql start
Rather than invoking init scriPC through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
mysql start/running, process 6889
PC-2@PC-2:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
PC-2@PC-2:~$ 
```

---

### Post by mennan on 2016-06-19
Hi, did you solve the authentication problem?

---

### Post by dom134 on 2016-06-20
I am not sure that this is your problem, but this sounds similar to what I had when I tried to log in to mysql via ssh.  I had previously run > sudo mysql_secure_installation and had selected no remote log in.  When I logged into the actual server and re ran the secure_installation, I was then able to log in remotely.

Hope this helps

---

### Post by devrekli on 2016-06-20
> **dom134 said:**
> I am not sure that this is your problem, but this  sounds similar to what I had when I tried to log in to mysql via ssh.  I  had previously run  and had selected no remote log in.  When I logged  into the actual server and re ran the secure_installation, I was then  able to log in remotely.

Hope this helps

We do not use ssh. The server physically here. I'll try it, thanks.


> **mennan said:**
> Hi, did you solve the authentication problem?

No :(

+

mysql -u root -p -h 127.0.0.1

```
ERROR 2003 (HY000): Can't connect to MySQL server on '127.0.0.1' (111)
```

**etc/mysql/my.cf** [http://pastebin.com/cMSdGUei](http://pastebin.com/cMSdGUei)

---

