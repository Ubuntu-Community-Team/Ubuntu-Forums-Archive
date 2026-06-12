---
title: "mysqld.sock missing"
date: 2006-11-09
forum: Server Platforms
---

### Post by satimis on 2006-11-09
Hi folks,

ubuntu-6.06.1-LAMP-server-amd64

After running;
$ sudo apt-get -install mysql-server mysql-client.

mySQL did not start, complaining "mysqld.sock" missing.

On googling I found following postings;
[http://ubuntuforums.org/showthread.php?t=111292](http://ubuntuforums.org/showthread.php?t=111292)
[http://ubuntuforums.org/showthread.php?t=140036](http://ubuntuforums.org/showthread.php?t=140036)

$ cat /etc/mysql/my.cnf | grep .sock```

# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
socket          = /var/run/mysqld/mysqld.sock
socket          = /var/run/mysqld/mysqld.sock
socket          = /var/run/mysqld/mysqld.sock

```

It was there.

$ sudo mysqld```

Password:
061109 15:41:52  InnoDB: Started; log sequence number 0 43655
061109 15:41:52 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
061109 15:41:52 [ERROR] Do you already have another mysqld server running on port: 3306 ?
061109 15:41:52 [ERROR] Aborting

061109 15:41:52  InnoDB: Starting shutdown...
061109 15:41:54  InnoDB: Shutdown completed; log sequence number 0 43655
061109 15:41:54 [Note] mysqld: Shutdown complete

```

$ sudo netstat -tap | grep mysql
Password:
No printout.

I can't figure out a solution.  Please help.  TIA


B.R.
satimis

---

### Post by adwait on 2006-11-09
I had the same problem, renaming the /etc/mysql/my.cnf file to something else helped. Don't exactly know why/how though.

---

### Post by satimis on 2006-11-09
Hi adwait,

Tks for your response.

> I had the same problem, renaming the /etc/mysql/my.cnf file to something else helped. Don't exactly know why/how though.
Whether you meant renaming "my.cfn"?  Restart "mySQL" allowing it to recreate a new "my.cfn" automatically.

Tks


B.R.
satimis

---

### Post by adwait on 2006-11-09
Yes, rename my.cnf to my.backup and then try starting mysql.

---

### Post by satimis on 2006-11-09
Hi adwait,

Tks for your advice.

> Yes, rename my.cnf to my.backup and then try starting mysql.

Strangely after rebooting the PC mySQL started automatically.

$ sudo netstat -tap | grep mysql```

Password:
tcp        0      0 localhost:mysql         *:*                     LISTEN     4086/mysqld         

```

I tested it twice including shutdown the PC.  mySQL is now starting.  I haven't done anything to fix the problem, except rebooting the PC.

I'll continue my test to see what will happen.

Tks.


Edit:   ***

$ sudo mysqladmin -u root password rootsql```

Password:

```

It went through without complaint


$ sudo mysqladmin -u root -h localhost password rootsql```

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
satimis@ubuntu:~$ sudo mysqladmin -u root -h localhost password rootsql
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

It complained, even using another password.  Whether localhost is not allowed using password?  Tks


B.R.
satimis

---

### Post by adwait on 2006-11-09
I am not very sure about this, but try checking what address you have bound mysql to in the /etc/mysql/my.cnf file. Also, check if you have granted permissions to the user "root" to access the server from localhost. Its possible that you have given it permissions from some specific LAN address...

---

### Post by satimis on 2006-11-09
Hi adwait,

> ...but try checking what address you have bound mysql to in the /etc/mysql/my.cnf file. Also, check if you have granted permissions to the user "root" to access the server from localhost. Its possible that you have given it permissions from some specific LAN address...

$ cat /etc/mysql/my.cnf | grep address```

bind-address            = 127.0.0.1

```

$ cat /etc/mysql/my.cnf | grep user```

# - "~/.my.cnf" to set user-specific options.
user            = mysql

```

$ cat /etc/mysql/my.cnf | grep localhost```

# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
```

Tks.


B.R.
satimis

---

### Post by adwait on 2006-11-09
THe bind address seems fine, does the root have permissions to login from anywhere? Login into mysql using
```
mysql
```

The fire thequery
```
grant all on *.* to root@%
```

Then try again...

---

### Post by satimis on 2006-11-09
Hi adwait,

> Login into mysql using
```
mysql
```


$ mysql```

ERROR 1045 (28000): Access denied for user 'satimis'@'localhost' (using password: NO)

```

$ sudo mysql
Password: rootsql
Sorry, try again
Password: satimis' password```

ERROR 1045 (28000): Access denies for user 'root@localhost' (using password:NO)

```

Failed to login


B.R.
satimis

---

### Post by satimis on 2006-11-09
Hi adwait,

> Login into mysql using
```
mysql
```


$ mysql```

ERROR 1045 (28000): Access denied for user 'satimis'@'localhost' (using password: NO)

```

$ sudo mysql
Password: rootsql
Sorry, try again
Password: satimis' password[code]
ERROR 1045 (28000): Access denies for user 'root@localhost' (using password:NO)

Failed to login


B.R.
satimis

---

