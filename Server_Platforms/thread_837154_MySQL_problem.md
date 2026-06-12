---
title: "MySQL problem"
date: 2008-06-22
forum: Server Platforms
---

### Post by satimis on 2008-06-22
Hi folks,


Ubuntu 7.04 server amd64


It just comes to my notice on running following commands

$ sudo /etc/init.d/mysql stop```

 * Stopping MySQL database server mysqld       [fail]

```


$ sudo /etc/init.d/mysql start```

 * Starting MySQL database server mysqld        [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```


I suppose the problem is caused by running several 'apt-get update' and 'apt-get upgrade'.  Before MySQL start/stop without problem nor having warning.


Please advise how to fix this problem.  TIA


B.R.
satimis

---

### Post by Akula on 2008-06-22
Are you sure that the username (debian-sys-maint) is still existing after updates? That is all I can think since it gives 'access denied' error.

---

### Post by satimis on 2008-06-22
> **Akula said:**
> Are you sure that the username (debian-sys-maint) is still existing after updates? That is all I can think since it gives 'access denied' error.
Hi Akula,


$ sudo cat /etc/mysql/debian.cnf```

Password:
# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = EdKLb0cr3GElkUdM
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
user     = debian-sys-maint
password = EdKLb0cr3GElkUdM
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

```


"user = debian-sys-maint" is still there.


B.R.
satimis

---

### Post by Akula on 2008-06-23
How about priviledges? Are you sure this user has priviledges to databases it is meant to use. Maybe they have disappeared somehow while upgrading?

---

### Post by satimis on 2008-06-23
> **Akula said:**
> How about priviledges? Are you sure this user has priviledges to databases it is meant to use. Maybe they have disappeared somehow while upgrading?
Hi Akula,


Thanks for your advice.

I have another box under building

Ubuntu 6.06 LAMP amd64


It also suffers the same problem recently after running upgrade.  On running;

$ sudo /etc/init.d/mysql status```

Password:
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```


I suspect whether there is problem on the repo packages?


Edit:

From notes on running upgrade, at start upgrade fails.  I have to run "apt-get -f install" to corret the problem.  Also there are packages "kept back".  I have to run "apt-get -u dist-upgrade" to install them.


B.R.
satimis

---

### Post by hyper_ch on 2008-06-23
I think you'll have to add debian-sys-maint again as user in mysql and grant the according rights.

---

### Post by Kolipoki on 2008-06-23
> **hyper_ch said:**
> I think you'll have to add debian-sys-maint again as user in mysql and grant the according rights.

I was going to suggest just that. I had a similar situation earlier today after trying to log on a user created last week. Solved it creating the user again and granting the correspondent privileges, as Hyper suggests.

---

### Post by satimis on 2008-06-23
> **hyper_ch said:**
> I think you'll have to add debian-sys-maint again as user in mysql and grant the according rights.
Hi hyper,


Could you please explain in more detail how to do it.  MySQL starts at safe mode after booting.  I can't login MySQL to make any change.  TIA


B.R.
satimis

---

### Post by hyper_ch on 2008-06-24
how do you try to login?

---

### Post by gcoram on 2008-06-24
I have found that the password in /etc/mysql/debian.cnf for debian-sys-maint has to match something in the mysql lib files. (database:mysql)
So if your migrate by moving /var/lib/mysql then you need to match the debian.cnf password with that of the original server.
worked for me. (or use GRANT to set password to match debian.cnf)

Not the best way to migrate databases though. mysqldump'ing may be a bit more effort but its worth it, me thinks...also worth doing before any mysql upgrade to be safe, added advantage of ensuring the database is clean.

---

### Post by satimis on 2008-06-24
> **gcoram said:**
> I have found that the password in /etc/mysql/debian.cnf for debian-sys-maint has to match something in the mysql lib files. (database:mysql)
So if your migrate by moving /var/lib/mysql then you need to match the debian.cnf password with that of the original server.
worked for me. (or use GRANT to set password to match debian.cnf)

Not the best way to migrate databases though. mysqldump'ing may be a bit more effort but its worth it, me thinks...also worth doing before any mysql upgrade to be safe, added advantage of ensuring the database is clean.
Hi gcoram,


I haven't done migration.  I even did not touch MySQL eversince this Mail Server started to work about 12 months ago.

I just discovered this problem recently.  Most likely it is caused by running apt-get upgrade.  Same as another Ubuntu LAMP 6.06 amd64 box.  After finishing configuration I left the box standing there w/o turning it on.  I build it for testing SugurCRM.  Becuase I have got time.  The project is pending.  Apache, postfix, squirrelmail, mysql etc. all were running w/o problem after configuration.  Only after running apt-get upgrade the nightmare comes.

I'm considering whether to reinstall MySQL.


Google found me several threads of similar problem, some of them solved and another unsolved.  They were playing around on debian.cf

There is a line on /etc/init.d/mysql```

/usr/bin/mysql --defaults-file=/etc/mysql/debian.cnf -e "\. ${tmpfile}"

```

I have been playing around on that file;

# cat /etc/mysql/debian.cnf```

Password:
# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = EdKLb0cr3GElkUdM
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
user     = debian-sys-maint
password = EdKLb0cr3GElkUdM
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

```
- replacing the password with mysql root password
- deleting the sock lines
- replacing the host with the name of the server

Non of them can solve my problem.


B.R.
satimis

---

### Post by satimis on 2008-06-24
> **hyper_ch said:**
> how do you try to login?
Hi hyper_ch,


# mysql -u root -p```

Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```


# /etc/init.d/mysql status```

/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
 * 
```


# netstat -tap | grep mysql```

tcp        0      0 *:mysql                 *:*                     LISTEN     4679/mysqld         

```

I suspect MySQL is running on safe mode.


Is there any way to re-set MySQL admin password as well as user 'root' password?


Edit:

$ sudo ps ax | grep -i mysql```

 4637 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 4679 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 4680 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 6470 pts/1    S+     0:00 grep -i mysql

```


B.R.
satimis

---

### Post by satimis on 2008-06-25
Hi folks,


My problem solved as follows;


# kill `cat /var/run/mysqld/mysqld.pid`
No complaint


# mysqld_safe --skip-grant-tables &```

[1] 5647
root@mail:/home/satimis# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[5686]: started
mysql -uroot mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.0.38-Ubuntu_0ubuntu1.4-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> UPDATE user SET password=PASSWORD('abcde') WHERE user='debian-sys-maint';
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql> quit
Bye

```


# nano /etc/mysql/debian.cnf
Changing the passwords


# cat /etc/mysql/debian.cnf```

# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = abcde
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
user     = debian-sys-maint
password = abcde
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

```


# /etc/init.d/mysql restart```

 * Stopping MySQL database server mysqld                                                                         
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[5742]: ended
                                                                                                          [ OK ]
 * Starting MySQL database server mysqld                                                                  [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
[1]+  Done                    mysqld_safe --skip-grant-tables

```


# /etc/init.d/mysql status```

 * /usr/bin/mysqladmin  Ver 8.41 Distrib 5.0.38, for pc-linux-gnu on x86_64
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license
Server version          5.0.38-Ubuntu_0ubuntu1.4-log
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 35 sec

Threads: 1  Questions: 136  Slow queries: 0  Opens: 132  Flush tables: 1  Open tables: 17  Queries per second avg
: 3.886

```


# ps ax | grep -i mysql```

 5788 pts/1    S      0:00 /bin/sh /usr/bin/mysqld_safe
 5827 pts/1    Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/
run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 5828 pts/1    S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 5904 pts/1    S+     0:00 grep -i mysql

```


# /etc/init.d/mysql stop```

 * Stopping MySQL database server mysqld          [ OK ] 

```


# /etc/init.d/mysql start```

 * Starting MySQL database server mysqld             [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```


Thanks.


I'll fix another Ubuntu box later.  If there is any problem I'll come back



B.R.
satimis

---

### Post by satimis on 2008-06-25
Hi folks,


My problem solved as follows;


# kill `cat /var/run/mysqld/mysqld.pid`
No complaint


# mysqld_safe --skip-grant-tables &```

[1] 5647
root@mail:/home/satimis# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[5686]: started
mysql -uroot mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.0.38-Ubuntu_0ubuntu1.4-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> UPDATE user SET password=PASSWORD('abcde') WHERE user='debian-sys-maint';
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql> quit
Bye

```


# nano /etc/mysql/debian.cnf
Changing the passwords


# cat /etc/mysql/debian.cnf```

# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = abcde
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
user     = debian-sys-maint
password = abcde
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

```


# /etc/init.d/mysql restart```

 * Stopping MySQL database server mysqld                                                                         
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[5742]: ended
                                                                                                          [ OK ]
 * Starting MySQL database server mysqld                                                                  [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
[1]+  Done                    mysqld_safe --skip-grant-tables

```


# /etc/init.d/mysql status```

 * /usr/bin/mysqladmin  Ver 8.41 Distrib 5.0.38, for pc-linux-gnu on x86_64
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license
Server version          5.0.38-Ubuntu_0ubuntu1.4-log
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 35 sec

Threads: 1  Questions: 136  Slow queries: 0  Opens: 132  Flush tables: 1  Open tables: 17  Queries per second avg
: 3.886

```


# ps ax | grep -i mysql```

 5788 pts/1    S      0:00 /bin/sh /usr/bin/mysqld_safe
 5827 pts/1    Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/
run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 5828 pts/1    S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 5904 pts/1    S+     0:00 grep -i mysql

```


# /etc/init.d/mysql stop```

 * Stopping MySQL database server mysqld          [ OK ] 

```


# /etc/init.d/mysql start```

 * Starting MySQL database server mysqld             [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```


Thanks.


I'll fix another Ubuntu box later.  If there is any problem I'll come back



B.R.
satimis

---

### Post by satimis on 2008-06-25
Hi folks,


I'm in complete lost.  The solution for fixing the problem on Ubuntu server 7.04 amd64 can't work on Ubuntu LAMP 6.06 amd64.

After finish on starting MySQL it complains.


# /etc/init.d/mysql start```

Starting MySQL database server: mysqld.
 * Root password is blank.  To change it use:
 * /etc/init.d/mysql reset-password
root@satimis:/home/satimis# /usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```


Finally I have to reinstall MySQL.  Steps performed as follows;


$ dpkg -l | grep mysql```

ii  libapache2-mod-auth-mysql   4.3.9-2ubuntu3    	Apache 2 module for MySQL authentication
ii  libdbd-mysql-perl           3.0002-2build1    	A Perl5 database interface to the MySQL data
ii  libmysqlclient15off         5.0.22-0ubuntu6.06.10   mysql database client library
ii  mysql-client-5.0            5.0.22-0ubuntu6.06.10   mysql database client binaries
ii  mysql-common                5.0.22-0ubuntu6.06.10   mysql database common files (e.g. /etc/mysql
ii  mysql-server                5.0.22-0ubuntu6.06.10   mysql database server (current version)
ii  mysql-server-5.0            5.0.22-0ubuntu6.06.10   mysql database server binaries
ii  php5-mysql                  5.1.2-1ubuntu3.10       MySQL module for php5
ii  php5-mysqli                 5.1.2-1ubuntu3.10       MySQL Improved module for php5

```


$ sudo apt-get remove --purge libapache2-mod-auth-mysq libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-mysql php5-mysql```

Password:
....
Need to get 0B of archives.
After unpacking 87.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
.....

Should I remove the complete /var/lib/mysql directory tree which is used by all MySQL versions, not necessarily only the one you are about to purge?                                                   
                                                                                                                            
Remove the databases from all MySQL versions?                                                               
                                                                                                                                                                <Yes>            <No>      

select <No>   

.....
Removing mysql-common ...
Purging configuration files for mysql-common ...
dpkg - warning: while removing mysql-common, directory `/etc/mysql' not empty so not removed.

```


$ sudo apt-get install mysql-server-5.0 mysql-common```

....
Selecting previously deselected package mysql-common.
(Reading database ... 25445 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.22-0ubuntu6.06.10_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.22-0ubuntu6.06.10_amd64.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0002-2build1_amd64.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.22-0ubuntu6.06.10_amd64.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.22-0ubuntu6.06.10_amd64.deb) ...
Setting up mysql-common (5.0.22-0ubuntu6.06.10) ...
Setting up libmysqlclient15off (5.0.22-0ubuntu6.06.10) ...

Setting up libdbd-mysql-perl (3.0002-2build1) ...
Setting up mysql-client-5.0 (5.0.22-0ubuntu6.06.10) ...
Setting up mysql-server-5.0 (5.0.22-0ubuntu6.06.10) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.

```


$ dpkg -l|grep mysql```

ii  libdbd-mysql-perl      3.0002-2build1             A Perl5 database interface to the MySQL data
ii  libmysqlclient15off    5.0.22-0ubuntu6.06.10      mysql database client library
ii  mysql-client-5.0       5.0.22-0ubuntu6.06.10      mysql database client binaries
ii  mysql-common           5.0.22-0ubuntu6.06.10      mysql database common files (e.g. /etc/mysql
ii  mysql-server-5.0       5.0.22-0ubuntu6.06.10      mysql database server binaries

```


Following packages found missing, not yet installed;```

ii  libapache2-mod-auth-mysql    4.3.9-2ubuntu3          Apache 2 module for MySQL authentication
ii  mysql-server                 5.0.22-0ubuntu6.06.10   mysql database server (current version)
ii  php5-mysql                   5.1.2-1ubuntu3.10       MySQL module for php5
ii  php5-mysqli                  5.1.2-1ubuntu3.10       MySQL Improved module for php5

```


I have no idea whether "mysql-server" is needed.  Because "mysql-server-5.0" is already installed.  So I leave it and continue installing;


$ sudo apt-get install libapache2-mod-auth-mysql php5-mysql php5-mysqli```

......
.....
Setting up libapache2-mod-auth-mysql (4.3.9-2ubuntu3) ...
Setting up php5-mysql (5.1.2-1ubuntu3.10) ...

Setting up php5-mysqli (5.1.2-1ubuntu3.10) ...

```


$ mysql -u root -p```

Enter password: xyz

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 7 to server version: 5.0.22-Debian_0ubuntu6.06.10-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.


mysql> SET PASSWORD FOR root = PASSWORD('xyzadmin');
ERROR 1133 (42000): Can't find any matching row in the user table


mysql> SET PASSWORD FOR 'root' = PASSWORD('xyzadmin');
ERROR 1133 (42000): Can't find any matching row in the user table


mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('xyzadmin');
Query OK, 0 rows affected (0.00 sec)

mysql> quit
Bye

```


$ sudo /etc/init.d/mysql restart```

Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.

```


$ ps ax | grep -i mysql```

 6504 pts/0    S      0:00 /bin/sh /usr/bin/mysqld_safe
 6565 pts/0    Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 6566 pts/0    S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 6641 pts/0    S+     0:00 grep -i mysql

```


MySQL is working now.


Please help me to understand WHY it needs```

mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('xyzdmin');
Query OK, 0 rows affected (0.00 sec)

```


Why;```

mysql> SET PASSWORD FOR root = PASSWORD('xyzadmin');
ERROR 1133 (42000): Can't find any matching row in the user table


mysql> SET PASSWORD FOR 'root' = PASSWORD('xyzadmin');
ERROR 1133 (42000): Can't find any matching row in the user table

```
don't work ???


What does```

Query OK, 0 rows affected (0.00 sec)

```
indicate ???


Do I need installing "mysql-server" additionally to "mysql-server-5.0" ?


TIA


B.R.
satimis

---

### Post by timebomb_1408 on 2008-06-25
I am having a similar problem, and your solution steps have been extremely helpful to me!

Try this for resetting the root password:

UPDATE user SET Password=PASSWORD('YOURNEWPASSWORD') WHERE
User='root';

---

### Post by satimis on 2008-06-26
> **timebomb_1408 said:**
> I am having a similar problem, and your solution steps have been extremely helpful to me!

Try this for resetting the root password:

UPDATE user SET Password=PASSWORD('YOURNEWPASSWORD') WHERE
User='root';
Hi timebomb,


Thanks for your advice.  It works on Ubuntu LAMP 6.06 drake amd64 only.  It fails to work on Ubuntu server 7.04 amd64.  Same steps were performed on 2 boxes respectively.


On Ubuntu server 7.04

# /etc/init.d/mysql stop```

 * Stopping MySQL database server mysqld                                 [ OK ] 

```


# mysqld_safe --user=mysql --skip-grant-tables --skip-net
working &```

[1] 9205
root@mail:/home/satimis# Starting mysqld daemon with databases from /var/lib/mys
ql
mysqld_safe[9250]: started
mysql -uroot mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.0.38-Ubuntu_0ubuntu1.4-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

```


Here I must run```

mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed

```


Without running "use mysql" it complains'```

mysql> UPDATE user SET Password=PASSWORD('abcde') where User='root';
ERROR 1046 (3D000): No database selected

```


On Ubuntu LAMP 6.06 drake amd64, I don't need to run "use mysql"


Continue;```

mysql> UPDATE user SET Password=PASSWORD('abcde') where User='root';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 0  Changed: 0  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql> quit
Bye

```
From above output "Rows matched: 0  Changed: 0  Warnings: 0" it seems no change effected.


# /etc/init.d/mysql restart```

Password:
 * Stopping MySQL database server mysqld                                                                                    STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[11056]: ended
                                                                                                                     [ OK ]
 * Starting MySQL database server mysqld                                                                             [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```


# mysql -u root -p```

Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

I have been trying hours w/o solution.


The only difference is MySQL on Ubuntu LAMP 6.06 drake amd64 has been reinstalled.


I think I have to reinstall MySQL on Ubuntu server 7.04 amd64 as well.  The upgrade packages on the repo my have problem.


B.R.
satimis

---

### Post by satimis on 2008-06-26
Hi folks,


It seems transparent NOW.


1)
On Ubuntu server 7.10 amd64 box

"debian-sys-maint" is root


Performed following test;

$ mysql -udebian-sys-maint -p```

Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 5.0.38-Ubuntu_0ubuntu1.4-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
+--------------------+
2 rows in set (0.00 sec)

```


```

mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed

mysql> show tables;
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              | 
| db                        | 
| func                      | 
| help_category             | 
| help_keyword              | 
| help_relation             | 
| help_topic                | 
| host                      | 
| proc                      | 
| procs_priv                | 
| tables_priv               | 
| time_zone                 | 
| time_zone_leap_second     | 
| time_zone_name            | 
| time_zone_transition      | 
| time_zone_transition_type | 
| user                      | 
+---------------------------+
17 rows in set (0.00 sec)

```


```

mysql> describe test;
ERROR 1146 (42S02): Table 'mysql.test' doesn't exist

```



2)
On Ubuntu LAMP 6.06 Drake amd64 box

Both;
$ mysql -uroot -p
$ mysql -udebian-sys-maint -p

work the same doing the same job.



The only difference is on 2) above I can create 'root' account but NOT on 1).


B.R.
satimis

---

