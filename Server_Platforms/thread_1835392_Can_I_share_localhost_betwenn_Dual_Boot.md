---
title: "Can I share localhost betwenn Dual Boot?"
date: 2011-08-29
forum: Server Platforms
---

### Post by stamatiou on 2011-08-29
Hey guys,
I would like to install Ubuntu Server with Dual Boot (with another Linux OS) but I would like to use it also in my other LinuxOS?

---

### Post by CharlesA on 2011-08-29
Are you going to be running a service such as apache (web server) ?

Each install is it's own entity, so any services running on one won't be accessible when you are booted into the other.

---

### Post by volkswagner on 2011-08-29
please clarify.  Are you just trying to access the same date for each OS installed, or are you wanting to access running services. 

You should have no problem sharing the data.  If you want to run services in both OS's at the same time, then dual-boot is not the solution.  Perhaps you should consider running Ubuntu server as a guest virtual machine.  Look into VirtualBox, KVM, or other solutions.

---

### Post by stamatiou on 2011-08-29
Thank you very much for your answers! :)
The thing I want is to program PHP on my Backtrack Laptop and I can not install LAMP Sserver because when I type apt-get install lamp-server^ I take E: Couldn't find task lamp-server  :(

---

### Post by CharlesA on 2011-08-29
Try using:

```
tasksel install lamp-server
```

---

### Post by stamatiou on 2011-08-29
> **CharlesA said:**
> Try using:

```
tasksel install lamp-server
```
I typed it and took:
```
tasksel: aptitude failed (100)
```

---

### Post by CharlesA on 2011-08-29
Running it as root?

---

### Post by stamatiou on 2011-08-29
> **CharlesA said:**
> Running it as root?
Yes

---

### Post by CharlesA on 2011-08-29
I know backtrack doesn't use the normal repos, so maybe try this:

```
apt-get install apache2 php5
```

---

### Post by stamatiou on 2011-08-29
> **CharlesA said:**
> I know backtrack doesn't use the normal repos, so maybe try this:

```
apt-get install apache2 php5
```
It tells me that they are in the latest version but in Firefox when I type localhost it tellse me that it does not exist....

---

### Post by CharlesA on 2011-08-29
Start it up:

```
service apache2 start
```

---

### Post by stamatiou on 2011-08-29
> **CharlesA said:**
> Start it up:

```
service apache2 start
```
:oops::oops:
It works now, both apache and php but how do I test MySQL?

---

### Post by CharlesA on 2011-08-29
> **stamatiou said:**
> :oops::oops:
It works now, both apache and php but how do I test MySQL?
Not sure as I don't use mysql,

Might want to check to see if the service is running by checking service.

---

### Post by Wim Sturkenboom on 2011-08-29
Starting the mysql client should give you an idea if the mysql server is running ;)
```

mysql -u root

```
or
```

mysql -u root -p

```
The first one if you have not set a root password, the second one if you have one set.

---

### Post by stamatiou on 2011-08-29
> **Wim Sturkenboom said:**
> Starting the mysql client should give you an idea if the mysql server is running ;)
```

mysql -u root

```or
```

mysql -u root -p

```The first one if you have not set a root password, the second one if you have one set.
Thanks for answering!
When I type the commands it tells me:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

---

### Post by Wim Sturkenboom on 2011-08-29
That means that the mysql server is not running. You can use ps to verify

mysql daemon is not running
```

wim@desktop-01:~$ **ps -ef |grep mysql |grep -v grep**
wim@desktop-01:~$
```

mysql daemon is running
```

wim@desktop-01:~$ **ps -ef |grep mysql |grep -v grep**
mysql     2947     1  0 20:11 ?        00:00:00 /usr/sbin/mysqld
wim@desktop-01:~
```

Don't know about your distro; in Ubuntu

```

wim@desktop-01:~$ sudo service mysql start
mysql start/running, process 3040
wim@desktop-01:~$ 

```

---

### Post by stamatiou on 2011-08-29
> **Wim Sturkenboom said:**
> That means that the mysql server is not running. You can use ps to verify

mysql daemon is not running
```

wim@desktop-01:~$ **ps -ef |grep mysql |grep -v grep**
wim@desktop-01:~$
```mysql daemon is running
```

wim@desktop-01:~$ **ps -ef |grep mysql |grep -v grep**
mysql     2947     1  0 20:11 ?        00:00:00 /usr/sbin/mysqld
wim@desktop-01:~
```Don't know about your distro; in Ubuntu

```

wim@desktop-01:~$ sudo service mysql start
mysql start/running, process 3040
wim@desktop-01:~$ 

```
Thank you very much, now it works. But when I had installed with the command sudo apt-get install lamp-server^ in ubuntu after the installation I was asked to give a password for MySQL User, now what password and what username should I use?

---

### Post by Wim Sturkenboom on 2011-08-29
A mysql install in Ubuntu prompts you to setup a password for the mysql root user.

So that's the password to use when using *_mysql -u root -p_*. If you don't have a password set (meaning *_mysql -u root_* works), I advise to set one.

Read the mysql documentation; can't give instructions right now.

---

### Post by stamatiou on 2011-08-29
> **Wim Sturkenboom said:**
> A mysql install in Ubuntu prompts you to setup a password for the mysql root user.

So that's the password to use when using *_mysql -u root -p_*. If you don't have a password set (meaning *_mysql -u root_* works), I advise to set one.

Read the mysql documentation; can't give instructions right now.
Ok Thank you very much!
Edit: I can not change the password! I type mysqladmin -u root password 'newpassword' after I have stoped mysql daemon and then  when I started and typed    mysql -u root -p and enter the password I take ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by Wim Sturkenboom on 2011-08-29
Stop the mysql daemon and restart it with the --skip-grant-tables
```

wim@ubuntu-desktop01:~$ **sudo service mysql stop**
mysql stop/waiting
wim@ubuntu-desktop01:~$ **sudo /usr/sbin/mysqld --skip-grant-tables**

```Please note that the last command will not return to a prompt

In another terminal
```

wim@ubuntu-desktop01:~$ **mysql -u root**
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> **use mysql**
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> **select user,host,password from user;**
+------------------+------------------+-------------------------------------------+
| user             | host             | password                                  |
+------------------+------------------+-------------------------------------------+
| root             | localhost        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | ubuntu-desktop01 | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | 127.0.0.1        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| debian-sys-maint | localhost        | *2CEE963D42CF5B97AAB6C932B218194DFF95B0D9 |
| backupuser       | localhost        |                                           |
| admin            | localhost        | *0D3CED9BEC10A777AEC23CCC353A8C08A633045E |
| admin2           | localhost        | *0DB96B25D401C2774D9CE2E1D82F81A380FA71D0 |
+------------------+------------------+-------------------------------------------+
7 rows in set (0.00 sec)

mysql> **update user set password=password('hallodaar') where user='[COLOR="Blue"]admin[/COLOR]';**
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select user,host,password from user;
+------------------+------------------+-------------------------------------------+
| user             | host             | password                                  |
+------------------+------------------+-------------------------------------------+
| root             | localhost        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | ubuntu-desktop01 | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | 127.0.0.1        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| debian-sys-maint | localhost        | *2CEE963D42CF5B97AAB6C932B218194DFF95B0D9 |
| backupuser       | localhost        |                                           |
| admin            | localhost        | *0DB96B25D401C2774D9CE2E1D82F81A380FA71D0 |
| admin2           | localhost        | *0DB96B25D401C2774D9CE2E1D82F81A380FA71D0 |
+------------------+------------------+-------------------------------------------+
7 rows in set (0.00 sec)

mysql> exit
Bye
wim@ubuntu-desktop01:~$ 
```

In the above example, replace 'admin' (marked in blue) by 'root'

To cleanup, find the pid of the mysql daemon, kill it and restart the mysql daemon the normal way.
```

wim@ubuntu-desktop01:~$ **ps -ef |grep mysql |grep -v grep**
mysql     **[COLOR="Red"]3093[/COLOR]**  2709  0 04:54 pts/0    00:00:00 /usr/sbin/mysqld --skip-grant-tables
wim@ubuntu-desktop01:~$ **sudo kill [COLOR="Red"]3093[/COLOR]**
wim@ubuntu-desktop01:~$ **ps -ef |grep mysql |grep -v grep**
wim@ubuntu-desktop01:~$ **sudo service mysql start**
mysql start/running, process 3127
wim@ubuntu-desktop01:~$ 
```

---

### Post by stamatiou on 2011-08-30
> **Wim Sturkenboom said:**
> Stop the mysql daemon and restart it with the --skip-grant-tables
```

wim@ubuntu-desktop01:~$ **sudo service mysql stop**
mysql stop/waiting
wim@ubuntu-desktop01:~$ **sudo /usr/sbin/mysqld --skip-grant-tables**

```Please note that the last command will not return to a prompt

In another terminal
```

wim@ubuntu-desktop01:~$ **mysql -u root**
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> **use mysql**
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> **select user,host,password from user;**
+------------------+------------------+-------------------------------------------+
| user             | host             | password                                  |
+------------------+------------------+-------------------------------------------+
| root             | localhost        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | ubuntu-desktop01 | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | 127.0.0.1        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| debian-sys-maint | localhost        | *2CEE963D42CF5B97AAB6C932B218194DFF95B0D9 |
| backupuser       | localhost        |                                           |
| admin            | localhost        | *0D3CED9BEC10A777AEC23CCC353A8C08A633045E |
| admin2           | localhost        | *0DB96B25D401C2774D9CE2E1D82F81A380FA71D0 |
+------------------+------------------+-------------------------------------------+
7 rows in set (0.00 sec)

mysql> **update user set password=password('hallodaar') where user='[COLOR=Blue]admin[/COLOR]';**
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select user,host,password from user;
+------------------+------------------+-------------------------------------------+
| user             | host             | password                                  |
+------------------+------------------+-------------------------------------------+
| root             | localhost        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | ubuntu-desktop01 | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| root             | 127.0.0.1        | *58364B2092FC2BF7A21616D9442D8250D2627B5B |
| debian-sys-maint | localhost        | *2CEE963D42CF5B97AAB6C932B218194DFF95B0D9 |
| backupuser       | localhost        |                                           |
| admin            | localhost        | *0DB96B25D401C2774D9CE2E1D82F81A380FA71D0 |
| admin2           | localhost        | *0DB96B25D401C2774D9CE2E1D82F81A380FA71D0 |
+------------------+------------------+-------------------------------------------+
7 rows in set (0.00 sec)

mysql> exit
Bye
wim@ubuntu-desktop01:~$ 
```In the above example, replace 'admin' (marked in blue) by 'root'

To cleanup, find the pid of the mysql daemon, kill it and restart the mysql daemon the normal way.
```

wim@ubuntu-desktop01:~$ **ps -ef |grep mysql |grep -v grep**
mysql     **[COLOR=Red]3093[/COLOR]**  2709  0 04:54 pts/0    00:00:00 /usr/sbin/mysqld --skip-grant-tables
wim@ubuntu-desktop01:~$ **sudo kill [COLOR=Red]3093[/COLOR]**
wim@ubuntu-desktop01:~$ **ps -ef |grep mysql |grep -v grep**
wim@ubuntu-desktop01:~$ **sudo service mysql start**
mysql start/running, process 3127
wim@ubuntu-desktop01:~$ 
```
Yes but now it tells me 
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

---

### Post by Wim Sturkenboom on 2011-08-30
So we're back where we were :( The daemon is not running. Did you start the daemon again (last command in my previous post)? If you did, check /var/log/mysql/error.log to see what went wrong; should be in there.

---

### Post by stamatiou on 2011-08-30
> **Wim Sturkenboom said:**
> So we're back where we were :( The daemon is not running. Did you start the daemon again (last command in my previous post)? If you did, check /var/log/mysql/error.log to see what went wrong; should be in there.
I checked it, it is running and now that I tried again the /usr/sbin/mysqld --skip-grant-tables it does not give me anything and I can't do anything, something like a loop that I press Ctrl + C and nothing happens....
Edit: Actually it was not an  loop with no end, just a very big one....

---

### Post by Wim Sturkenboom on 2011-08-30
I'm a bit at a loss with your description.

1)
You stopped the mysql service using *_sudo service mysql stop_*
2)
You started it again with *_sudo /usr/sbin/mysqld --skip-grant-tables_*
3)
You used *_mysql -u root_* in another terminal to connect
4)
You did set a root password
5)
You ended the mysql client
6)
You killed the mysql server
7)
You started the mysql server using *_sudo service mysql start_*
[noparse]8)[/noparse]
You tried to connect using the client and you got the connection error posted in post #21
9)
You tried (2) again and it just sits there just like it did when you did (2) above for the first time

Where do I go wrong or where did it fail on you?

---

### Post by stamatiou on 2011-08-30
> **Wim Sturkenboom said:**
> I'm a bit at a loss with your description.

1)
You stopped the mysql service using *_sudo service mysql stop_*
2)
You started it again with *_sudo /usr/sbin/mysqld --skip-grant-tables_*
3)
You used *_mysql -u root_* in another terminal to connect
4)
You did set a root password
5)
You ended the mysql client
6)
You killed the mysql server
7)
You started the mysql server using *_sudo service mysql start_*
[noparse]8)[/noparse]
You tried to connect using the client and you got the connection error posted in post #21
9)
You tried (2) again and it just sits there just like it did when you did (2) above for the first time

Where do I go wrong or where did it fail on you?
It did not fail, I just followed your guide in the previous post

---

### Post by Wim Sturkenboom on 2011-08-30
So it's solved ?

---

### Post by stamatiou on 2011-08-30
Yes

---

