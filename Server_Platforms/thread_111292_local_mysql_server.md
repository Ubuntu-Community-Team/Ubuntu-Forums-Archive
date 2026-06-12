---
title: "local mysql server"
date: 2006-01-02
forum: Server Platforms
---

### Post by stuffradio on 2006-01-02
Hey, I am getting an error when I try and start mysql. The error is,

ERROR 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I had done something with the tutorial found here: 
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

One of those pages I had to move some files and I think that's what's causing the problem. And there are no files in /var/run/mysqld/ please help me.

---

### Post by jocke1s on 2006-01-02
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by stuffradio on 2006-01-02
... that doesn't fix my problem, haha. That just gives me some other piece of software, I need mysql fixed not apache.

---

### Post by paddyg on 2006-01-02
If there is no mysqld.sock, this means the MySQL server is not running.

Just take a look at the socket line in /etc/mysql/my.cnf, which tells you where the socket file must be. Just check out, if there is no socket file the server is not running.

---

### Post by stuffradio on 2006-01-02
is there a way I can make a mysqld.sock file, or should I reinstall mysql

---

### Post by paddyg on 2006-01-03
Just try and start the server, and it should make both mysqld.pid and mysqld.sock in /var/run/mysqld. To do that, just invoke the script mysqld_safe in /usr/bin.
Good luck.

---

### Post by stuffradio on 2006-01-03
That still doesn't fix it :'(

---

### Post by paddyg on 2006-01-03
What do you mean---
1. the server isn't running and you can't start it?
2. the server is running and you can't find mysqld.sock?

As for
1. If /usr/bin/mysqld_safe doesn't start the server, in terminal (a very uncommon method, though) type
```
sudo mysqld
```
Or just check out System-->Administration-->Services and tick off the Database server (mysql) entry.

2. What does the [mysqld] section in /ect/mysql/my.cnf read?

---

### Post by stuffradio on 2006-01-03
that's another thing, in that install it doesn't install the gui for like gnome, etc. so I am stuck in command line and when i type start x it says: "bash: start: command not found and when I type startx it says: 
/etc/X11/xinit/xerverrc: line 2: /urs/bin/X11/X: No such file or directory
/etc/X11/xinit/xserverrc: line 2: exec: /urs/bin/X11/X: cannot execute: No such file or directory

Also for mysql there might be a process running on port 3306 but don't know how to find out and kill it.

---

### Post by paddyg on 2006-01-03
You can use the following to learn about processes
```
ps -A
```
And you should look for mysqld among them.
If you want to kill a process
```
sudo kill processPID
```

---

### Post by iyeat on 2006-01-09
[QUOTE=paddyg]What do you mean---
1. the server isn't running and you can't start it?
2. the server is running and you can't find mysqld.sock?

As for
1. If /usr/bin/mysqld_safe doesn't start the server, in terminal (a very uncommon method, though) type
```
sudo mysqld
```
Or just check out System-->Administration-->Services and tick off the Database server (mysql) entry.

2. What does the [mysqld] section in /ect/mysql/my.cnf read?[/QUOTE]
In my case...

Immediately after installation, the server attempts to start, and I get an error:

```
Setting up mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

So I check syslog and find the following error:

```
Jan  8 06:53:44 localhost mysqld_safe[7555]: Installing all prepared tables
Jan  8 06:53:45 localhost mysqld_safe[7555]: ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
Jan  8 06:53:45 localhost last message repeated 7 times
Jan  8 06:53:45 localhost mysqld_safe[7555]: 060108  6:53:45 /usr/sbin/mysqld: Shutdown Complete
```

looks like mysql is having trouble writing the default DB... however I'm not sure how to fix this. I attemptd to chmod 777 the /var/lib/mysql directory and its contents, but this did not fix the issue.

As for the mysqld section of my.cnf:

```
[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
```

---

### Post by paddyg on 2006-01-09
You can try running mysql_install_db in /usr/bin, which should reinstall the default mysql db and grant tables. Before doing that you should either rename or remove the old mysql default db folder.

I wouldn't change the datadir permissions. It should only be accessible to the MySQL server user (chmod 700).

---

### Post by LordHunter317 on 2006-01-09
Stop trying to run the database in funny ways, for starters.  

Always use:```
/etc/init.d/mysql
``` to start/stop the DB.

---

### Post by iyeat on 2006-01-09
[QUOTE=paddyg]You can try running mysql_install_db in /usr/bin, which should reinstall the default mysql db and grant tables. Before doing that you should either rename or remove the old mysql default db folder.

I wouldn't change the datadir permissions. It should only be accessible to the MySQL server user (chmod 700).[/QUOTE]

OK I've erased and installed the breezy 5.10 ubuntu server install off of the CD. After installing openssh-server via apt-get, I've installed mysql-server. I received the same errors when attempting to start mysql.

I ran /usr/bin/mysql_install_db as suggested. Here is the output:

```
caio@ubuntu:~$ sudo /usr/bin/mysql_install_db 
Preparing db table
Preparing host table
Preparing user table
Preparing func table
Preparing tables_priv table
Preparing columns_priv table
Installing all prepared tables
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
060109 11:10:06 /usr/sbin/mysqld: Shutdown Complete


To start mysqld at boot time you have to copy support-files/mysql.server
to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:
/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h ubuntu password 'new-password'
See the manual for more instructions.

You can start the MySQL daemon with:
cd /usr ; /usr/bin/mysqld_safe &

You can test the MySQL daemon with the benchmarks in the 'sql-bench' directory:
cd sql-bench ; perl run-all-tests

Please report any problems with the /usr/bin/mysqlbug script!

The latest information about MySQL is available on the web at
http://www.mysql.com
Support MySQL by buying support/licenses at https://order.mysql.com
```

---

### Post by iyeat on 2006-01-09
[QUOTE=LordHunter317]Stop trying to run the database in funny ways, for starters.  

Always use:```
/etc/init.d/mysql
``` to start/stop the DB.[/QUOTE]

Here is the output:

```
caio@ubuntu:~$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

---

### Post by paddyg on 2006-01-09
My last ideas:
1. Have you deleted the old mysql default db folder before running /usr/bin/mysql_install_db?
2. Is the mysql datadir chowned mysql.mysql (the MySQL server user)?

---

### Post by weissed on 2006-02-19
I also had problems starting the mysql server after install. Here's what I did:

Go to the folder where mysql keeps its databases & tables data (*mysql* and *test* folder should be there, with **.frm* files inside them):

```
$ cd /var/lib/mysql
```

Now backup previous mysql folder to mysql_bkp 
(NOTE: backup the "mysql" folder inside the parent "/var/lib/mysql" folder)

```
$ mv mysql mysql_bkp
```

Run the script to reinstall the mysql db tables

```
$ sudo mysql_install_db
```

Now change the ownership & permissions to the folders to what they should be (*test *and *mysql* are my only 2 existing & default created databases)

```

$ sudo chown mysql:mysql mysql
$ sudo chmod 750 mysql
$ sudo chown mysql:mysql test
$ sudo chmod 750 test

```

Now you should have something like this:

```

$ ls -lrt
*drwxr-x---  2 mysql mysql*     4096 2006-02-19 11:59 test
drwxr-xr-x  2 mysql root      4096 2006-02-19 11:59 mysql_bkp
*drwxr-x---  2 mysql mysql*     4096 2006-02-19 12:28 mysql
...

```

Now you can start the mysql server. 
Remember that by default, after installing, there is a root user with blank password to your mysql server. Don't worry if you get some errors that user blablabla can't connect.

```

$ sudo /etc/init.d/mysql start

```

Then you can change your root's password:

```

$ mysqladmin -u root password your_new_root_password

```

To check that your mysql server is up and accepts your root user/pass run:

```

$ mysql -u root -p

```

Hope this will help you.

---

### Post by LordHunter317 on 2006-02-19
That's totally wasteful.  **Rebuilding the default database is not a solution.**

If you can't login or start, you have a problem with the command you're running.  Pure and simple.  You might have a authorization problem, but that can only come from a command problem.

---

### Post by joal on 2006-04-06
This problem would occur if you accidentally mess up your /etc/myslq/my.cnf file. I got that error when adding a non valid line....

-j-

---

### Post by engelbert on 2006-04-12
I have the same problem as above. I tried sudo mysql_install_db by it gave my this error:

060412  9:38:10 /usr/sbin/mysqld: unknown variable 'old_passwords=1'

so I tried to fix that by remarking that line, and still no go.



I think something got messed up with those apt-get installs from the howto.

---

### Post by cyteen on 2006-10-04
To recap:

Error:

 Connecting to database..FAILED 

and syslog says:

 /usr/sbin/mysqld: unknown variable 'old_passwords=1'

Solution: in:

 /etc/mysql/my.cnf  

Comment out

 old_passwords = 1 

If this still doesn't work for you

 apt-get remove mysql-server mysql-common
 dpkg -P mysql-common
 apt-get install mysql-server

---

