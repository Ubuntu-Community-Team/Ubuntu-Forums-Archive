---
title: "Mysql problem: Can't start server : Bind on unix socket: Permission denied"
date: 2006-03-14
forum: Server Platforms
---

### Post by nibbo on 2006-03-14
Hi. First of all i would like to tell you that i am a total newbie to linux. Now to the problem.

Some days ago i noticed that my database wasn't working. After some investigation i found that it wasn't started. I Tried to start it manually with the command mysqld. I got the following error:

nibbo@ubuntuserver:/$ mysqld
060314  8:34:31 Warning: Can't create test file /var/lib/mysql/ubuntuserver.lower-test
060314  8:34:31 Can't start server : Bind on unix socket: Permission denied
060314  8:34:31 Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
060314  8:34:31 Aborting

060314  8:34:31 mysqld: Shutdown Complete

I tried to google the error and found out that allmost everyone solved it by changing some permissions. I tried and tried every solution i found but my mysql-server still won't start.:cry:  Any ideas?

Thanks for any help and sorry for my bad english :-|

---

### Post by pitr on 2006-03-14
By the looks of it you are not running mysqld with the right permission. 

You can try "sudo mysqld" and see if it works.

If you have installed mysql using apt-get/synaptic then I suggest you use the startup script instead.

sudo /etc/init.d/mysqld start

---

### Post by nibbo on 2006-03-14
buy running sudo /etc/init.d/mysqld start i just got the error telling me that the command does not exist. I tried sudo /etc/init.d/mysql start (mysql not mysql**d**) and got the error:

nibbo@ubuntuserver:/$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

What log am i supposed to look at?

---

### Post by pitr on 2006-03-14
You should be able to find logfiles for mysql under /var/log (might even be /var/log/mysql/)

---

### Post by nibbo on 2006-03-14
No errors in the logs... Just some info about the last stuff put in the database...

---

### Post by nibbo on 2006-03-15
so nobody has any idea about how to solve this problem? I am really desperate now. A forum i am hosting has been down for allmost two weeks :(

---

### Post by nibbo on 2006-03-15
I found a log containing some intresting stuff.

mysqldump: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect

---

### Post by nibbo on 2006-03-18
somebody! Please!!! I will give you all the information you need. Anything! Or if somebody can fix this over ssh?

---

### Post by gmclachl on 2006-03-18
have you tried cd'ing to the directory and checking out the permissions

   cd /var/run/mysqld ; ls -la 

  Is mysql.sock owned by mysql and in the mysql group. Should look like
  srwxrwxrwx  1 mysql mysql   0 2006-03-18 16:33 mysqld.sock

George

---

### Post by nibbo on 2006-03-19
[QUOTE=gmclachl]have you tried cd'ing to the directory and checking out the permissions

   cd /var/run/mysqld ; ls -la 

  Is mysql.sock owned by mysql and in the mysql group. Should look like
  srwxrwxrwx  1 mysql mysql   0 2006-03-18 16:33 mysqld.sock

George[/QUOTE]

This is what i got: 


nibbo@ubuntuserver:/var/run/mysqld$ sudo ls -la
Password:
totalt 8
d-wx-wx-wx   2 mysql mysql 4096 2006-03-16 08:10 .
drwxr-xr-x  17 root  root  4096 2006-03-19 07:35 ..
srwxrwxrwx   1 nibbo nibbo    0 2006-03-16 08:10 mysqld.sock

So it does look a bit diffrent than it is supposed to do, huh?
How to fix this then?

---

### Post by LordHunter317 on 2006-03-19
Does ps show the database server already running?

You likely borked up your my.cnf file.  Post it.

---

### Post by gmclachl on 2006-03-19
[QUOTE=nibbo]This is what i got: 


nibbo@ubuntuserver:/var/run/mysqld$ sudo ls -la
Password:
totalt 8
d-wx-wx-wx   2 mysql mysql 4096 2006-03-16 08:10 .
drwxr-xr-x  17 root  root  4096 2006-03-19 07:35 ..
srwxrwxrwx   1 nibbo nibbo    0 2006-03-16 08:10 mysqld.sock

So it does look a bit diffrent than it is supposed to do, huh?
How to fix this then?[/QUOTE]

 Well I may be wrong, but mysqld runs under mysql so as it is owned by you and your group thats most likely what the problem is. 

  Try 
    sudo chown mysql mysql.sock 
    sudo chgrp mysql mysql.sock 

 That might work.

---

### Post by nibbo on 2006-03-19
[QUOTE=LordHunter317]Does ps show the database server already running?

You likely borked up your my.cnf file.  Post it.[/QUOTE]

AHH!! I GOT IT WORKING!!!! The problem was a messed up config :) Wrong user given :)

---

