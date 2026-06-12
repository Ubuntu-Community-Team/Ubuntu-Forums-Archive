---
title: "Trouble with Web server"
date: 2011-06-06
forum: Server Platforms
---

### Post by talk2montu on 2011-06-06
Hello all,

I am a newbie (please spear me), I installed the latest Ubuntu 11.04 server and it is running fine.  I installed a trial version of wing ftp server, which seems to be working great.  The problem I have currently is that port 80 is being used by some other web server on this machine.  For example when i type [http://192.168.x.x](http://192.168.x.x) it states the following message listed below:
**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.

When i type [https://192.168.x.x](https://192.168.x.x), it goes into the wing ftp server and loads up.

I have verified that i dont have tomcat and apache installed.  Any ideas forum?

---

### Post by Apollo87 on 2011-06-07
Hey,

That page looks like the default apache web page.  Are you 100% positive that apache is not installed?

Apaches default document root is /var/www , if you put a page in there are you able to access it?  Also, are you able to see any apache processes running?

Try running this in a terminal and see what you get:

```

ps aux | grep apache

```

Maybe you have another web server running as well like nginx or lighttpd, which may be something to look in to.

---

### Post by crispy_420 on 2011-06-07
Try this:

[http://www.cyberciti.biz/faq/what-process-has-open-linux-port/](http://www.cyberciti.biz/faq/what-process-has-open-linux-port/)

Don't know if this is the obvious or not but ftp and http use different ports. Maybe try 127.0.0.1:20 I think or [ftp://127.0.0.1](ftp://127.0.0.1) is another option but I may be wrong, I'm tired and it is late.

---

### Post by lisati on 2011-06-07
*Thread moved to **Server Platforms**.*

---

### Post by Dry Lips on 2011-06-07
You can also try:
```
sudo netstat -plntu
```
Are you sure you don't installed a LAMP server
during the installation? (see screenshot.)

---

### Post by talk2montu on 2011-06-08
When i ran the following commands above I saw that Apache was installed
[B]
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1498/apache[/B]


I try to uninstall it with the following command  (sudo apt-get purge apache2) and I get this result

[B]montu@VIRUS:~$ sudo apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

I also did this as well


[B]montu@VIRUS:~$ apachectl status
Can't create config directory (/.w3m)!Apache Server Status for localhost

Server Version: Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch
Server Built: Feb 22 2011 18:35:08

-------------------------------------------------------------------------------

Current Time: Wednesday, 08-Jun-2011 20:53:52 EDT
Restart Time: Monday, 06-Jun-2011 20:05:43 EDT
Parent Server Generation: 0
Server uptime: 2 days 48 minutes 8 seconds
Total accesses: 95 - Total Traffic: 23 kB
CPU Usage: u0 s0 cu0 cs0
.000541 requests/sec - 0 B/second - 247 B/request
1 requests currently being processed, 8 idle workers

__W______.......................................................
................................................................
................................................................
................................................................

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current proce[/B]

---

### Post by Apollo87 on 2011-06-08
Maybe you installed apache through source?

Can you stop the process by running:

```
sudo /etc/init.d/apache2 stop
```

---

