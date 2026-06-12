---
title: "MySQL chmod and user rights"
date: 2009-05-21
forum: Server Platforms
---

### Post by lenamtl on 2009-05-21
Hi,

I'm new to Linux, and the hardest thing for me is to set folders / users rights and chmod.

I have installed PHP5, Mysql5 and PHPMyAdmin my www is located in my Home.

Everything was working ok.

The problems started when I installed **Joomla**, when I installed new components the rights of the components folders where set to root and I was unable to modify these files... so I have add a new user to PHP (my user) then that was seems to fix the problem.

The day after I was not able to connect to PHPMyAdmin using my username and pw, I'm getting **error 2002** and I'm not able to start MySQL service..**Fail**

So I just don't know what to do... this is very more complicate to set webserver on Linux, in Windows it's working in few minutes.

I want to try to fix this, if I can't I will have no choice and will need to start over my project on Windows...

Any help is appreciate.

---

### Post by Alekz_ on 2009-05-21
MySQL 'error 2002' means that:

MySQL isn't running
or
the sock file doesn't exist (or maybe is wrong!)

Sometimes the folder where the sock file is created doesn't have write permission for the "mysql user" (I don't know how did you set up your server, but usualy the user is 'mysql')! 
Take a look on that (mysql logs will show you where the sock file has been created).

---

### Post by lenamtl on 2009-05-21
syslog
> May 21 20:09:30 mini mysqld_safe[10372]: started
May 21 20:09:30 mini mysqld[10375]: 090521 20:09:30  InnoDB: Operating system error number 13 in a file operation.
May 21 20:09:30 mini mysqld[10375]: InnoDB: The error means mysqld does not have the access rights to
May 21 20:09:30 mini mysqld[10375]: InnoDB: the directory.
May 21 20:09:30 mini mysqld[10375]: InnoDB: File name ./ibdata1
May 21 20:09:30 mini mysqld[10375]: InnoDB: File operation call: 'open'.
May 21 20:09:30 mini mysqld[10375]: InnoDB: Cannot continue operation.
May 21 20:09:30 mini mysqld_safe[10382]: ended
May 21 20:09:44 mini /etc/init.d/mysql[10541]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May 21 20:09:44 mini /etc/init.d/mysql[10541]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
May 21 20:09:44 mini /etc/init.d/mysql[10541]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
May 21 20:09:44 mini /etc/init.d/mysql[10541]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
May 21 20:09:44 mini /etc/init.d/mysql[10541]: 

I'm wondering is there any option in Ubuntu to go back in time like windows like a restore system?

My mysql and www are located under home
Mysql (data) folder permission owner is me
www folder permission owner is me
I have PHPMyadmin into www link to /usr/share/phpmyadmin with permission owner root
It is maybe I had myself as PHP user I'm confused

---

### Post by lenamtl on 2009-05-22
I really need to fix this, I'm stuck..
Anybody know which file or folder I need to change permission?

---

