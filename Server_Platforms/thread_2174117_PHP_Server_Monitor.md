---
title: "PHP Server Monitor"
date: 2013-09-12
forum: Server Platforms
---

### Post by nerdtron on 2013-09-12
Has anyone here tried installing/running PHP server Monitor? I can't seem to understand how to run the script/program.
[http://sourceforge.net/projects/phpservermon/](http://sourceforge.net/projects/phpservermon/)

Even wit the documentation on [how to install]("http://sourceforge.net/projects/phpservermon/files/phpservermon/PHP%20Server%20Monitor%20v2.0.1/") I can't undestand how to execute steps 1-3. Maybe experienced PHP prgrammers can shed light on this?

---

### Post by CharlesA on 2013-09-12
Are you just wanting to monitor your servers to make sure they are up? I've been using [Uptimerobot]("http://www.uptimerobot.com/") for that.

As far as the installation goes, what exactly are you having problems with?

---

### Post by nerdtron on 2013-09-13
Thanks for the heads-up on UptimeRobot but we wish to monitor our servers and services (websites) using our own hosted monitoring tools.

In step 3, it says:
> 3. Run install.php  	Once your database login information is correct, you can run the install.php script located in the  	root dir. This script will create all the database tables you will need.  	After running the install.php script you can remove it.
But I'm not sure if I'm doing it correctly. I run the install.php script and nothing happens.
```
php5 install.php
```
I can't proceed further on the installation instructions.

---

### Post by CharlesA on 2013-09-13
You need to run it from a web browser. I'm not too sure if it will work if you just run it via php.

EDIT: I'm not too fond of the server monitor you linked in the OP. The lack of security out-of-the-box doesn't give me a good feeling.

Have you looked into [Zabbix]("http://www.zabbix.com/")? I've heard good things about it.

---

### Post by LHammonds on 2013-09-13
I don't know anything about PHP Server Monitor but you might want to check out Nagios.  I have a detailed how-to guide in my signature if interested.  I monitor all my network switches, printers, servers, PCs, services, databases, websites, etc. with it (whether it be Windows, Linux or hardware device)

Once you have everything being monitored, it makes some awesome reports with the more history it has behind it.  I have each server's hard drive space being monitored to let us know when they are low but it also helps with growth analysis and prediction models.

LHammonds

---

### Post by nerdtron on 2013-09-13
LHammonds, we already have Nagios and it's doing it's job. Currently only configured for ping. We want to add Server Monitor because it can use cURL to say, download a small part of the webpage, to determine if the website is actually up.

---

### Post by CharlesA on 2013-09-13
> **nerdtron said:**
> LHammonds, we already have Nagios and it's doing it's job. Currently only configured for ping. We want to add Server Monitor because it can use cURL to say, download a small part of the webpage, to determine if the website is actually up.

Nagios can do that as well. :)

---

