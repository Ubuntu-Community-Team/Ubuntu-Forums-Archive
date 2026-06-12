---
title: "Selfmade mess: LAMP only returns blank (empty) pages"
date: 2009-03-06
forum: Server Platforms
---

### Post by primaxx on 2009-03-06
Ok, this is going to be a long post, sorry!

**Problem:** 
When I, in a browser, visit [http://192.168.1.50/](http://192.168.1.50/) it returns "**It works!**" (which is good).
When I, in a browser, visit [http://192.168.1.50/example/](http://192.168.1.50/example/) (Where Joomla 1.5 is installed) it returns absolutely nothing. No errors, just... nothing (a white, empty page)!

**Final goal:**
To run a webserver with 2 name-based virtual hosts through 1 public, static IP-address.

**What I've done (read: Messed up):**
Where to start...?
This is Ubuntu 8.10 Server-edition, with preinstalled LAMP. In addition I have installed Webmin, SSH and SFTPD, and, as far as I can remember (from yesterday...), thats all.

[LIST]
[*]I configured (through Webmin) my two Virtual Hosts.
[*]I (deliberately but unfortunately) deleted Default Virtual Server through Webmins interface.
[*]I installed Joomla 1.5 in /var/www/example/ (At this moment everything worked fine.).
[*]Everything went white (the empty pages showed) after the installation of Joomla was finished and I wanted to see the frontpage of my fresh Joomla-installation.
[*]I restarted Apache (through Webmin) and got an error, saying something about 000-default not existing.
[*]I (deliberately but unfortunately) deleted 000-default from /etc/apache27sites-enabled.
[*]I started Apache successfully this time, but got 404's all over the place.
[*]I googled, and found a default 000-default on the Internet which I added to /etc/apache2/sites-enabled. Still 404's.
[*]I deleted both of and reestablished on of my virtual servers (Everything here is thorugh Webmin, I am very afraid of Vi...). Still 404's.
[*]I discovered that I was also missing the /etc/apache2/sites-available/default, and did the same as I did with the 000-default. After a restart of Apache again, I was back to my initial problem, with the empty pages on my virtual servers, and "**It works**!" on "root".
[/LIST]

My /etc/apache2/httpd.conf contains one line: *Options -Indexes FollowSymLinks*

I am sure I have done other (stupid) things also, but I no longer remember what...

Another (might be) important issue here is that the domain [www.example.com](www.example.com) allready exists on another server on another ip-address today, meaning no dns-server on the Internet points to my **new **server now. When I am accessing it now it is on the local network.

This is a typical part of .../apache2/error.log:```
[Fri Mar 06 05:32:45 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Mar 06 05:32:54 2009] [error] [client 192.168.1.50] File does not exist: /htdocs
[Fri Mar 06 05:32:54 2009] [error] [client 192.168.1.50] File does not exist: /htdocs
[Fri Mar 06 05:32:56 2009] [error] [client 192.168.1.50] File does not exist: /htdocs
[Fri Mar 06 05:32:57 2009] [error] [client 192.168.1.50] File does not exist: /htdocs
[Fri Mar 06 05:32:57 2009] [error] [client 192.168.1.50] File does not exist: /htdocs
[Fri Mar 06 05:33:07 2009] [notice] Graceful restart requested, doing restart
[Fri Mar 06 05:33:07 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Mar 06 05:33:07 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Mar 06 05:39:36 2009] [notice] Graceful restart requested, doing restart
[Fri Mar 06 05:39:36 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Mar 06 05:39:36 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Mar 06 05:39:38 2009] [notice] caught SIGTERM, shutting down
[Fri Mar 06 05:39:42 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Mar 06 05:40:45 2009] [notice] Graceful restart requested, doing restart
[Fri Mar 06 05:40:45 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Mar 06 05:40:45 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Mar 06 05:40:47 2009] [notice] caught SIGTERM, shutting down
[Fri Mar 06 05:40:52 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Mar 06 05:58:10 2009] [notice] Graceful restart requested, doing restart
[Fri Mar 06 05:58:10 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Fri Mar 06 05:58:10 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Mar 06 05:58:10 2009] [info] Server built: Sep 19 2008 13:43:21
[Fri Mar 06 05:58:10 2009] [debug] prefork.c(1024): AcceptMutex: sysvsem (default: sysvsem)
[Fri Mar 06 05:58:12 2009] [info] removed PID file /var/run/apache2.pid (pid=17712)
[Fri Mar 06 05:58:12 2009] [notice] caught SIGTERM, shutting down
[Fri Mar 06 05:58:15 2009] [notice] Apache/2.2.9 (Ubuntu) configured -- resuming normal operations
[Fri Mar 06 05:58:15 2009] [info] Server built: Sep 19 2008 13:43:21
[Fri Mar 06 05:58:15 2009] [debug] prefork.c(1024): AcceptMutex: sysvsem (default: sysvsem)

```
My .../apache2/access.log looks like this:
```
192.168.1.84 - - [06/Mar/2009:09:34:52 +0100] "GET / HTTP/1.1" 200 56 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US) AppleWebKit/525.19 (KHTML, like Gecko) Chrome/1.0.154.48 Safari/525.19"
192.168.1.84 - - [06/Mar/2009:09:34:56 +0100] "GET /example/ HTTP/1.1" 500 20 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US) AppleWebKit/525.19 (KHTML, like Gecko) Chrome/1.0.154.48 Safari/525.19"

```

I also have a firewall configured, but this should not be the issue here, as long as it worked with the installation of Joomla? (When I say the installation worked, I mean I did it after visiting [http://192.168.1.50/example/](http://192.168.1.50/example/) and did it through Joomla's web-interface.)

Well, that about sums up my problems, and I would be so incredibly grateful for any help I can get on this mess I've made!

(Sorry for my bad English...)

---

### Post by cb951303 on 2009-03-06
I don't know what's your problem but there is one solution to fix a messed up LAMP setup that almost always works

```

sudo apt-get **--purge** remove apache2 php5-common php5-mysql libapache2-mod-php5 mysql-server
```

```

sudo tasksel install lamp-server
```

PS: Note that it will wipe any apache/php/mysql configuration you've done.

:popcorn:

---

### Post by primaxx on 2009-03-06
> **cb951303 said:**
> I don't know what's your problem but there is one solution to fix a messed up LAMP setup that almost always works

```

sudo apt-get **--purge** remove apache2 php5-common php5-mysql libapache2-mod-php5 mysql-server
```

```

sudo tasksel install lamp-server
```

PS: Note that it will wipe any apache/php/mysql configuration you've done.

:popcorn:

Thank you very much (for the popcorn also!), and come to think of it, it's better to just wipe out the LAMP-installation and reinstall it...
**Tasksel **is new to me, Google, here we come.

Once again, thanks! :)

---

### Post by primaxx on 2009-03-06
And now I am up and running...
Imagine I have been struggling with this since yesterday...

Popcorn back! :-)
:popcorn:

---

### Post by cb951303 on 2009-03-06
> **primaxx said:**
> And now I am up and running...
Imagine I have been struggling with this since yesterday...

Popcorn back! :-)
:popcorn:

no problem at all. remember the key is "--purge" which removes the configuration files too (the source of all problems :))
tasksel is very handy to install some special package groups like samba, ssh, lamp or *buntu-dekstops

---

### Post by yelirekim on 2009-08-20
This works like a charm, I had pretty much the same issue and after spending maybe an hour trying to fix it stumbled across this thread.  Thanks for the tip :)

---

