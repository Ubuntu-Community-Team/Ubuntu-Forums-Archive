---
title: "100% apache cpu usage after upgrade"
date: 2009-09-03
forum: Server Platforms
---

### Post by altitude1 on 2009-09-03
Greetings, as an avid ubuntuforums reader its now time for me to create my very first thread here. Greetings! To the problem:

I run LAMP on an Ubuntu 8.04 server. I recently completed a "sudo apt-get upgrade" and upgraded all components found.

After this, my Apache frequently uses way too much cpu which in turn causes the website its running to become inaccessible. Before the upgrade it never exceeded around 2-3%.

Doing a "sudo /etc/init.d/apache2 restart" does not restart Apache, it has to be killed using "killall apache".

I am running
```
PHP 5.2.4-2ubuntu5.7 with Suhosin-Patch 0.9.6.2 (cli) (built: Aug 21 2009 19:52:39)
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

Server version: Apache/2.2.8 (Ubuntu)
Server built:   Aug 18 2009 14:18:10
```Here is a screenshot taken of "htop": [http://bayimg.com/image/hadoeaack.jpg](http://bayimg.com/image/hadoeaack.jpg)

And here is one of "munin": [http://bayimg.com/image/hadobaack.jpg](http://bayimg.com/image/hadobaack.jpg)

I would be eternally grateful for any help as I am loosing users by the minute! Thank you!

Edit: Maybe there is some correlation here:
```
1144 [Wed Sep 02 03:29:11 2009] [error] server reached MaxClients setting, consider raising the MaxClients setting
1145 [Wed Sep 02 10:07:48 2009] [notice] caught SIGTERM, shutting down
1146 [Wed Sep 02 10:08:22 2009] [notice] Apache/2.2.8 (Ubuntu) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations

-------------------

1162 [Wed Sep 02 16:10:14 2009] [error] server reached MaxClients setting, consider raising the MaxClients setting
1163 [Wed Sep 02 19:03:53 2009] [notice] caught SIGWINCH, shutting down gracefully
1164 [Wed Sep 02 19:04:13 2009] [notice] Apache/2.2.8 (Ubuntu) mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
1165 [Wed Sep 02 19:05:52 2009] [error] server reached MaxClients setting, consider raising the MaxClients setting
```
But reaching MaxClients should not cause Apache to crash...? Surely?

---

### Post by fahadsadah on 2009-09-03
Try raising it, and see if that resolves the problem.

---

### Post by altitude1 on 2009-09-03
Hi, thanks for your reply.. I raised the MaxClients from 150 (standard) to 250, but it still crashed in a matter of hours. I dont understand, it was fine before the upgrade!

---

