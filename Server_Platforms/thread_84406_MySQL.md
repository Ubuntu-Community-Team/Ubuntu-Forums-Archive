---
title: "MySQL"
date: 2005-10-31
forum: Server Platforms
---

### Post by 3dmaker on 2005-10-31
Hello, I am using Ubuntu 5.10 Breezy Badger, and I just installed Apache 2, PHP, and MySQL on my computer. After I rebooted my computer MySQL was turned off. I try to run the command "mysqld" but I get this message

051030 23:11:19  InnoDB: Started
051030 23:11:19 Fatal error: Can't open privilege tables: Table 'mysql.host' doesn't exist
051030 23:11:19 Aborting

051030 23:11:19  InnoDB: Starting shutdown...
051030 23:11:21  InnoDB: Shutdown completed
051030 23:11:21 mysqld: Shutdown Complete

I am running under sudo root and everything. I tried the services start mysqld, but Ubuntu does not have a services command. So I am wondering how do I turn on MySQL??

---

### Post by suRoot on 2005-10-31
Try

```
/etc/init.d/mysqld start
```

---

### Post by ubuntu_demon on 2005-10-31
I moved this thread to server talk.

---

### Post by 3dmaker on 2005-10-31
[QUOTE=suRoot]Try

```
/etc/init.d/mysqld start
```[/QUOTE]
bash: /etc/init.d/mysqld: No such file or directory

---

### Post by dbee on 2005-10-31
try 

```
 updatedb 
```

then

```
 locate mysqld 
```

there should be a mysqld or a mysqld_safe stashed away with the mysql binaries
track 'em down and then run 'em. You may have to 

```
 cd 
```

to their directory and then

```
 ./mysqld_safe 
```
 
or  

 ./mysqld

---

### Post by LordHunter317 on 2005-10-31
Nope, you cannot run the daemon directly and have it work.

Run /etc/init.d/mysql start (there is no d).

---

### Post by 3dmaker on 2005-11-01
None of the above work
When I do 
/etc/init.d/mysql start
I get this error

Starting MySQL database server: mysqld
...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Everything else is running (Apache, PHP)

./mysqld_safe I get this
051101 16:21:21  InnoDB: Started
051101 16:21:21 Fatal error: Can't open privilege tables: Table 'mysql.host' doesn't exist
051101 16:21:21 Aborting

051101 16:21:21  InnoDB: Starting shutdown...
051101 16:21:24  InnoDB: Shutdown completed
051101 16:21:24 mysqld: Shutdown Complete


Also I get this error

Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[23821]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[23837]: ended


What should I do?

---

### Post by 3dmaker on 2005-11-01
Now when I type this
sudo /etc/init.d/mysql start

this is what happens

george@compaq:/usr/bin$ sudo /etc/init.d/mysql start
george@compaq:/usr/bin$


Nothing. And the server is not running. My PHPMYADMIN says this
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured) 
how do I configure the socket?

---

### Post by defkewl on 2005-11-01
Have you installed mysql server and mysql client?

---

### Post by vasdee on 2005-11-02
could it be the loopback interface is not up? its troubled me in the past
try ```
ifconfig
```... if 'lo' is not present then try ```
ifconfig lo 127.0.0.1
``` to bring the interface back up. Then run the mysql start command

---

### Post by dbee on 2005-11-02
Have you tried rebooting ?

Sometimes that's just simpler than messing around with the sockets and processes.
I've had luck with a simple reboot before.

Do you have two mysql's installed by any chance ?
Are you just using synaptic ?

---

### Post by henriquemaia on 2005-11-13
Having the same problem here. I have tried everything (at least I think so) I read on the internet with no luck.

Mysql is working, mysql client CAN connect, mysql-query-browser and mysql-admin CAN connect, but phpmyadmin or any webpage that tries to contact mysql gives me the error:

MySQL said: Documentation
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured) 

Maybe a apache module error, but I have everything installed. Anyone has any idea how to solve this?

---

### Post by jnk on 2005-11-13
I got the exact same error.
I'm using Ubuntu Server 5.10 PowerPC on an old iMac G3 400Mhz.
Was thinking of puting this old machine to use as an web/ftp server.
The Apache2/PHP4 install works perfect. I'm able to view the site with php working.
But the MySQL crap isn't working... =( anyone got a good solution to this.?
I've installed MySQL like this:
sudo apt-get install mysql-server libapache2-mod-auth-mysql php4-mysql

---

### Post by jnk on 2005-11-13
got it to work. =)

sudo apt-get remove mysql-server

then

sudo apt-get install mysql-server-4.1

magic, it just worked. ;)

---

### Post by henriquemaia on 2005-11-14
[QUOTE=jnk]got it to work. =)

sudo apt-get remove mysql-server

then

sudo apt-get install mysql-server-4.1

magic, it just worked. ;)[/QUOTE]

It happened the same to me! A bug, maybe? 

My steps were like this. I had the server running previoulsy, but then I installed mysql5. As mysql5 didn't work as I expected, I reinstalled 4.1. That's when the error started. Knowing not what to do, I installed 4.0 and accepted apt's downgrading dialog. Same error again, I reinstalled 4.1. Then, magically, everything worked.

Now it's running fine.

---

### Post by sickdude on 2005-11-23
i have the same problem but i want to do something but i dont want to remove mysql-server unless im shure that it doesnt delete my databases and i dont want to change configureations if its possible

so can somebody let me know for shure that it doesnt delete my DB's ?

---

### Post by henriquemaia on 2005-11-23
[QUOTE=sickdude]i have the same problem but i want to do something but i dont want to remove mysql-server unless im shure that it doesnt delete my databases and i dont want to change configureations if its possible

so can somebody let me know for shure that it doesnt delete my DB's ?[/QUOTE]

I'm (almost) sure that you can remove mysql-server without doing anything wrong to your databases - but, as a good security practice, backup them elsewhere (you just have to copy the folders where they are kept). 

I myself removed the server severall times and nothing happened.

Ps: backup you data first.

---

