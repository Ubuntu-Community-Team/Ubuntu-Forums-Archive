---
title: "Apache2 Won't Start"
date: 2006-06-17
forum: Server Platforms
---

### Post by Syrae on 2006-06-17
It's the oddest thing, Apache2 won't start. Not only that, but it produces no output.

First off, its symlink is in rc2.d as S91apache2 and it properly points to /etc/init.d/apache2.  When I try to start it, I get no output on the console.  (Same results apply if I use sudo to start the process.)  

```
syrae@halit:~$ /etc/init.d/apache2 start
syrae@halit:~$ /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server...                                     [ ok ]
syrae@halit:~$ /etc/init.d/apache2 restart
syrae@halit:~$ /etc/init.d/apache2 start
syrae@halit:~$ /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server...                                     [ ok ]
syrae@halit:~$ /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server...                                     [ ok ]
syrae@halit:~$ /etc/init.d/apache2 start
syrae@halit:~$ ps -ef | grep httpd
syrae     9182  4825  0 18:54 pts/0    00:00:00 grep httpd
syrae@halit:~$
```

It only gives output when I stop it, and based on the message, it can stop itself even after it's stopped itself. :-s 

If I remember right, apache2 still runs as httpd, but I never see the process running.  EVER.  Apache2 doesn't run on start up or when I try to manually start it.  Nothing else is listening on the port.


Now, before I upgraded to Dapper, it still wouldn't start up with the rest of the system, but I could start it manually with /etc/init.d/apache2 start.  Now that doesn't even work.  As you can tell by the terminal output, it's just doing something weird and/or dumb.  The lack of output doesn't help.  

According to my log files, the last time the apache2 server was up was on June 8th.  (This is a hobbyist server, so I didn't notice for a while.)

---

### Post by linuxone on 2006-06-18
Hi,

[QUOTE=Syrae]It's the oddest thing, Apache2 won't start. Not only that, but it produces no output.[/QUOTE]

/var/log/apache2/error.log should give you the necessary answer to solve your problem.

> syrae@halit:~$ ps -ef | grep httpd

apache2 daemon name is **apache2**, not httpd. See "ps awx | more" or "ps awx | grep apache".

Thomas

---

### Post by Syrae on 2006-06-20
Okay, for the sake of argument, here's what I've done today, in the order I executed everything.  Notice the complete lack of output or feedback.
```
syrae@halit:~$ /etc/init.d/apache2 start
syrae@halit:~$ ps awx | grep apache2
 5687 pts/0    S+     0:00 grep apache2
syrae@halit:~$ ls -l /var/log/apache2
total 276
-rw-r----- 1 root adm      0 2006-05-28 07:36 access.log
-rw-r----- 1 root adm 242209 2006-06-08 08:05 access.log.1
-rw-r----- 1 root adm   3784 2006-05-28 07:36 access.log.2.gz
-rw-r----- 1 root adm      0 2006-05-28 07:36 error.log
-rw-r----- 1 root adm  21512 2006-06-08 15:23 error.log.1
-rw-r----- 1 root adm    965 2006-05-28 07:36 error.log.2.gz
My error log is empty.  The last log that has anything in it is error.log.1

```
Apache definately didn't start.  Also, note that my error log and access log files are both empty and not modified today.  The archived log error.log.1 and access.log.1 were both modified last over two weeks ago.  This is despite the fact that I just tried to start the service.
```
syrae@halit:~$ sudo /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server...                                     [ ok ]
syrae@halit:~$ sudo /etc/init.d/apache2 start
syrae@halit:~$ ps awx | grep apache2
 5739 pts/0    S+     0:00 grep apache2
syrae@halit:~$ ps awx | grep apache
 5741 pts/0    S+     0:00 grep apache
syrae@halit:~$ ps awx | grep httpd
 5743 pts/0    S+     0:00 grep httpd
syrae@halit:~$ ls -l /var/log/apache2
total 276
-rw-r----- 1 root adm      0 2006-05-28 07:36 access.log
-rw-r----- 1 root adm 242209 2006-06-08 08:05 access.log.1
-rw-r----- 1 root adm   3784 2006-05-28 07:36 access.log.2.gz
-rw-r----- 1 root adm      0 2006-05-28 07:36 error.log
-rw-r----- 1 root adm  21512 2006-06-08 15:23 error.log.1
-rw-r----- 1 root adm    965 2006-05-28 07:36 error.log.2.gz
```
Even though stopping the service produces output, nothing still shows up in my logs.  
```
syrae@halit:~$ cat /var/log/apache2/error.log
syrae@halit:~$ cat /var/log/apache2/error.log.1
<last 10 entries shown below>

[Wed Jun 07 12:05:15 2006] [error] [client 203.179.82.122] File does not exist: /var/www/blog
[Wed Jun 07 12:05:16 2006] [error] [client 203.179.82.122] File does not exist: /var/www/blog
[Wed Jun 07 12:05:18 2006] [error] [client 203.179.82.122] File does not exist: /var/www/blogs
[Wed Jun 07 12:05:18 2006] [error] [client 203.179.82.122] File does not exist: /var/www/drupal
[Wed Jun 07 12:05:19 2006] [error] [client 203.179.82.122] File does not exist: /var/www/phpgroupware
[Wed Jun 07 12:05:20 2006] [error] [client 203.179.82.122] File does not exist: /var/www/wordpress
[Wed Jun 07 12:05:20 2006] [error] [client 203.179.82.122] script '/var/www/xmlrpc.php' not found or unable to stat
[Wed Jun 07 12:05:23 2006] [error] [client 203.179.82.122] File does not exist: /var/www/xmlrpc
[Wed Jun 07 12:05:24 2006] [error] [client 203.179.82.122] File does not exist: /var/www/xmlsrv
[Thu Jun 08 15:23:23 2006] [notice] caught SIGTERM, shutting down
```
The error log just shows some guy in Japan scanning for vulnerabilities and then Apache shutting down.  I'm pretty sure that's the day that I upgraded from Breezy to Dapper, so that's why it shut down.  Since then, Apache has been broken.  I've used apt-get to remove Apache2 and then install it again, and it still doesn't work.  I don't care if I loose my settings, I just want to get a working version of Apache2 up again.

---

### Post by Syrae on 2006-06-21
Mmm... the Ubuntu server at work has the same problem.  It was upgraded to Dapper one day after we installed Breezy on it, and though it had Apache2 installed, it was never used.  Now when we try to set it up and start it, it won't start.  Same symptoms.

Additionally, the Services Settings GUI is completely empty and never populates its list even when left alone for several minutes.  When you try and close it, the system reports that the UI is locked up.

So... at least to me it seems like the upgrade process screwed up the services on both machines.  I don't care about doing a reinstall on my home system, but it would NOT be preferable to to do a reinstall on the machine here at work.

---

### Post by spifbv on 2006-06-21
[QUOTE=Syrae]
The error log just shows some guy in Japan scanning for vulnerabilities and then Apache shutting down.  I'm pretty sure that's the day that I upgraded from Breezy to Dapper, so that's why it shut down.  Since then, Apache has been broken.  I've used apt-get to remove Apache2 and then install it again, and it still doesn't work.  I don't care if I loose my settings, I just want to get a working version of Apache2 up again.[/QUOTE]


Try running the following as root:

/usr/sbin/apache2 -t

It should return "Syntax OK".  If not, then it should return some errors which will help you debug your configuration.  If the config is OK, then try running the following as root:

/usr/sbin/apache2 -E apache2test.log

And look at the log and/or any errors that show up on the console.  This may indicate a cause for the failure.

---

### Post by zerok112 on 2006-06-25
I had the same problem.

Check the file: /etc/defaults/apache2 and set NO_START=0

What it does is explained in the file itself. It seems that the default is 1 and when using a program to start/stop services this value isn't changed

---

### Post by Ubuntero-PK on 2008-04-24
Hi friends,

I have a little different problem 

I have successfully install apache 2.2.3 from external website with all nessecary modules, and its works perfect via local browsing , 

When i browse it via command line 

root@Blance-routing: lynx [http://localhost](http://localhost) 
its gives - "it works"

but 

i cannot access it from internet 

also on a same system i m running vsftpd server on port 21 and it works fine for me from local as well as from internet via free dyndns subdomain. 

Few information : 
*I am using firestarter as a firewall
 * my internet is via simple broadband cable modem with no router like feature , (so my all ports are open except those wich are blocked from firewall) .  
* my iptable rules are already set to accept incoming connections on port 21, 22, 80 , 8080 and 443 

Then why i cant access the starter page of apache 2.2 from internet like from local browser  ?
What i am missing ? 

Looking for a quick reply 

Thanks

---

