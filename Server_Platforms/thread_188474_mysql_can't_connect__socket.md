---
title: "mysql can't connect / socket"
date: 2006-06-04
forum: Server Platforms
---

### Post by toxi-city on 2006-06-04
i'm running kubuntu 6.06 and i just could not connect to mySQL 4.1 server
i have this message:
"Can't connect to local MySQL server through socket '/var/run/mysql/mysql.sock' (111)
Check that mysqld is running and that the socket: '/var/run/mysql/mysql.sock' exists!" 

note that the abovementioned socket exists in /var/run/mysql/

i have read many answers on similar problems on other linux distro's [like to "chown -R mysql.mysql /var/lib/mysql] but none of them was on ubuntu.

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=toxi-city]i'm running kubuntu 6.06 and i just could not connect to mySQL 4.1 server
i have this message:
"Can't connect to local MySQL server through socket '/var/run/mysql/mysql.sock' (111)
Check that mysqld is running and that the socket: '/var/run/mysql/mysql.sock' exists!" [/QUOTE]

check if mysql is really running.

Run [color=green]sudo /etc/init.d/mysql status[/color] into a konsole window to see the status.

Or use [color=green]ps awx | grep mysql[/color] into a konsole to check if the MySQL process is running and alive.

Then you'd check the mysql error log which is stored in /var/log. It seems your mysql server does crash or stop after starting.

Thomas

---

### Post by toxi-city on 2006-06-05
the two commands gave:

[FONT="Courier New"]mo@wildkat:~$ sudo /etc/init.d/mysql
Usage: /etc/init.d/mysql start|stop|restart|reload|force-reload|status
mo@wildkat:~$ ps awx | grep mysql
 8471 pts/4    S+     0:00 grep mysql[/FONT]

and when i restart mysql, i get:
[FONT="Courier New"]
mo@wildkat:/var/log/mysql$ sudo /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
[/FONT]

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=toxi-city]the two commands gave:

[FONT="Courier New"]mo@wildkat:~$ sudo /etc/init.d/mysql
Usage: /etc/init.d/mysql start|stop|restart|reload|force-reload|status[/QUOTE]

please read my first answer again & complete and try it once again ....

[QUOTE=linuxone]Run [color=green]sudo /etc/init.d/mysql **status**[/color] into a konsole window to see the status.[/QUOTE]


> mo@wildkat:~$ ps awx | grep mysql
 8471 pts/4    S+     0:00 grep mysql

as suggested: the mysql server is **NOT** running (no active mysql process into the process list), seems mysql does crash during starting.

> and when i restart mysql, i get:

please read my first answer again & complete and try it once again .... I didn't mention a mysql restart but a completly different hint ... without details from the log file it's quite difficult to solve your problem remotly.

[QUOTE=linuxone]Then you'd check the mysql error log which is stored in /var/log. It seems your mysql server does crash or stop after starting.[/QUOTE]

This hint is also part of the mysql error message ...

[QUOTE=toxi-city]mo@wildkat:/var/log/mysql$ sudo /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
**Please take a look at the syslog.**[/QUOTE]

Thomas

---

### Post by toxi-city on 2006-06-05
hello Thomas :KS 

the status says:
[COLOR="Red"]MySQL is stopped[/COLOR]

however, here's what i got in the syslog; apparentely it's an issue of accessing /tmp. right?

[COLOR="Green"][FONT="Courier New"]Jun  5 16:01:05 localhost mysqld_safe[11691]: started
Jun  5 16:01:05 localhost mysqld[11694]: ^G/usr/sbin/mysqld: Can't read dir of '/tmp/' (Errcode: 13)
Jun  5 16:01:06 localhost mysqld[11694]: ^G/usr/sbin/mysqld: Can't create/write to file '/tmp/ibbogXKS' (Errcode: 13)
Jun  5 16:01:06 localhost mysqld[11694]: 060605 16:01:06  InnoDB: Error: unable to create temporary file; errno: 13
Jun  5 16:01:06 localhost mysqld[11694]: 060605 16:01:06 [ERROR] Can't init databases
Jun  5 16:01:06 localhost mysqld[11694]: 060605 16:01:06 [ERROR] Aborting
Jun  5 16:01:06 localhost mysqld[11694]: 
Jun  5 16:01:07 localhost mysqld[11694]: 060605 16:01:07 [Note] /usr/sbin/mysqld: Shutdown complete
Jun  5 16:01:07 localhost mysqld[11694]: 
Jun  5 16:01:07 localhost mysqld_safe[11698]: ended
Jun  5 16:01:13 localhost /etc/init.d/mysql[11760]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jun  5 16:01:13 localhost /etc/init.d/mysql[11760]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jun  5 16:01:13 localhost /etc/init.d/mysql[11760]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)'
Jun  5 16:01:13 localhost /etc/init.d/mysql[11760]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jun  5 16:01:13 localhost /etc/init.d/mysql[11760]: [/FONT][/COLOR]

---

### Post by linuxone on 2006-06-05
Hi,

> **toxi-city]however, here's what i got in the syslog said:**
> [FONT="Courier New"]Jun  5 16:01:05 localhost mysqld_safe[11691]: started
Jun  5 16:01:05 localhost mysqld[11694]: ^G/usr/sbin/mysqld: Can't read dir of '/tmp/' (Errcode: 13)

well, this might have different reasons. Did you install Dapper 6.06 freshly or as update into an already existing system?

I'd first try to remove MySQL by using "purge" ("aptitude purge mysql-server-4.1") into a konsole window. Then re-install it again into the konsole to see all messages: "apt-get install mysql-server-4.1".
Already existing mysql database shouldn't not be changed, but of course you should backup all important files before purging. (for example: "tar czvf mysqlbackup.tgz /var/lib/mysql")

Thomas

---

### Post by toxi-city on 2006-06-05
apparently this was an issue of wrong permissions to /tmp
it was:
[COLOR="DarkOrange"]drwx------ user1 user1[/COLOR] -- my fault!
so i did "[COLOR="DarkOrange"]chmod 777 /tmp[/COLOR]" -- is this safe??

thanks T.

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=toxi-city]apparently this was an issue of wrong permissions to /tmp
it was:
[COLOR="DarkOrange"]drwx------ user1 user1[/COLOR] -- my fault![/QUOTE]

**drwx------ user1 user1** ??? :confused: :confused: :confused: 

it's very nice to hear someone did change important system defaults. :mad:
Real great. Such kind of permissions never was done from the system, these settings only could happen after a manual changing by a user.

There is absolutly no choice to solve problems after changing such an important default system configuration.

> so i did "[COLOR="DarkOrange"]chmod 777 /tmp[/COLOR]" -- is this safe??

default system setting for /tmp is: **drwxrwxrwt   root root**.

Thomas

---

### Post by LordHunter317 on 2006-06-05
You should:```
sudo chmod 1777 /tmp
```Which will give the correct permissions.

---

### Post by adamkane on 2006-06-07
Best to avoid mysql 4.1. Choose mysql 4.0 or mysql 5.0.

Method of easiest install/maintenance:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by LordHunter317 on 2006-06-07
[QUOTE=adamkane]Best to avoid mysql 4.1. Choose mysql 4.0 or mysql 5.0.[/quote]Utter nonsense.

And phpmyadmin is not hte best way to admin MySQL.  It's probably one of the worse unless you need a web interface on the box anyway, something most of my DB servers don't have.

---

### Post by adamkane on 2006-06-07
I meant best for ease of use. I realize that mysql + phpmyadmin has many problems. Just a suggestion. Feel free to ignore my poor advice.

---

### Post by LordHunter317 on 2006-06-07
Well, I'll give it's eaiser to use than the GUI admin tools, and eaiser for than monitor if you don't know MySQL's syntax for admin stuff.  

But as a blind suggestion, I'm not sure it's wise.

---

