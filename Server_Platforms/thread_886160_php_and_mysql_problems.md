---
title: "php and mysql problems"
date: 2008-08-10
forum: Server Platforms
---

### Post by sawatdee on 2008-08-10
I tried configuring php5 with the command
```
$ sudo ./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-gd --with-mysql --with-mysqli --with-pdo-mysql --enable-soap --with-libxml-dir
```
but I kept getting a mysql error. It couldn't link with the mysql libraries because the packages installed binaries.

So I uninstalled the mysql packages, downloaded the mysql source, built mysql from scratch, and installed it manually. Then php5 configured okay, but I get an error when I try to start mysqld_safe and I can't follow the directions at [http://dev.mysql.com/doc/refman/5.0/en/installing-binary.html]("http://dev.mysql.com/doc/refman/5.0/en/installing-binary.html") because ubuntu has no root user. I don't really know how to get this version of mysql running, but I need the specific configuration of php5 shown above. I am sure I will also need to configure php again in the future.

I tried installing the ubuntu php package but I have no idea how to configure it as shown above. I have only ever built php5 manually and prefer to do it that way.

My other concern is that if I use this mysql source installation to build php5, but then install the ubuntu mysql package so that I can start it with the simple "sudo /etc/init.d/mysql start" command, then my version of php5 will not actually be built using the libraries from the version of mysql that I am using.

Does anyone know how I can either:
[LIST=1]
[*]get this installation of mysql to run on ubuntu
[*]configure (and reconfigure) php5 as shown above using the ubuntu mysql packages
[/LIST]

---

### Post by RealPSL on 2008-08-10
Why do you feel you can not follow the instructions because Ubuntu does not have a root account. The root account does exist it is just not "commonly" used. The preferred method is to use sudo to execure commands as root. Is there a particular command you could not run using sudo? What was the error message you received when you tried to start mysql?

---

### Post by sawatdee on 2008-08-11
Most of the mysql instructions can be done except for the chown -R root. This is the first time I have set up an ubuntu system and I am used to being able to use su - to become root. But root has no password on this system, so I feel lost.

When I start mysql, I get this:
```
[1] 22721
$ nohup: ignoring input and redirecting stderr to stdout
Starting mysqld daemon with databases from /usr/local/var
STOPPING server from pid file /usr/local/var/hofmann.pid
080810 19:13:36  mysqld ended

```

If I then try to connect to the server using the mysql command, I get:
```
$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

```

---

### Post by RealPSL on 2008-08-11
You can still run that command with ```
sudo chown -R root some_file_or_directory
```

As for becoming root you can still do this with ```
sudo -i
``` but that is generally frowned on. I have not really found a reason to have to do it yet. 

Does that /tmp/mysql.sock file already exist? Which user are you starting mysql as?

---

