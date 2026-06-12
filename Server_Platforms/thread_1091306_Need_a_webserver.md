---
title: "Need a webserver"
date: 2009-03-09
forum: Server Platforms
---

### Post by happyhacker on 2009-03-09
On my server (no GUI) I am sure I have Apache installed but no LAMP arrangement e.g. mysql, phpMyAdmin. How can I convert to LAMP without upsetting whatever Apache is there for now? I want to run a website with Drupal CMS installed which requires a DB and I need full browser access to the usual WAMP/LAMP features.

---

### Post by cherva on 2009-03-09
LAMP stands for Linux, Apache, MySQL, PHP, just apt-get the other things you need....

---

### Post by happyhacker on 2009-03-09
But does that mean they all tie in together and I get PHPMyAdmin and a MYSQL GUI as well? I do not have the experience to do expert configuration.

---

### Post by cdenley on 2009-03-09
LAMP does not imply anything about web interfaces or GUI. I have never installed either one. I believe installing apache's php module will enable it by default. If not:
```

sudo a2enmod php5

```
Simply installing php5-mysql should make php work with mysql.

---

### Post by Iowan on 2009-03-09
LAMP comes with PHP, but not PHPmyAdmin (which is a MySQL GUI - as I recall), but it can be added as a package.

---

### Post by hyper_ch on 2009-03-09
run

```

sudo apt-get install libapache2-mod-php5 mysql-server mysql-client libmysqlclient15-dev
```

that will install php5 and mysql

then run

```

sudo a2enmod php5

```

that will activate the php5 module for apache

then run

```

sudo /etc/init.d/apache2 restart
```

to restart apache with php5.

That's it.

---

### Post by happyhacker on 2009-03-11
Hm, I have 3 PIDs running according to webmin and they are called "www-data /usr/sbin/apache2 -k start". Is that proof that I have the server running because it does not appear as a server as webmin only lists "Read user mail", "ssh", and "Samba".

Can I also add to hyper-ch's post PHPMyAdmin?

sudo apt-get install libapache2-mod-php5 mysql-server mysql-client libmysqlclient15-dev [COLOR="Blue"]phpmyadmin[/COLOR].

Can this be done from the webmin command line utility as I do not have a console/keyboard fitted for direct access?

---

### Post by hyper_ch on 2009-03-11
can't you log into the server with ssh? that's how you should learn to manage the server ;)

---

### Post by happyhacker on 2009-03-11
I do not want to manage the server via the command line. I prefer a remote GUI method like webmin.

---

### Post by cdenley on 2009-03-11
> **cantthinkofanickname said:**
> I do not want to manage the server via the command line. I prefer a remote GUI method like webmin.

It sounds like you want both.
> 
Can this be done from the webmin command line utility as I do not have a console/keyboard fitted for direct access?


---

### Post by hyper_ch on 2009-03-11
> **cantthinkofanickname said:**
> I do not want to manage the server via the command line. I prefer a remote GUI method like webmin.

managing a server is not too comlicated from the cli... it's just when you want a fully function web/email/proxy/dns/file/print/vpn/... server to setup at the same time that it's overwhelming.

If you have time, just do it one after the other... there are many good tutorials out there and basically the only few things you need to know in the cli is:

(1) how to travers directories
(2) how to manipulate (create/edit/copy/move) files
(3) how to install software from the cli
(4) how to start/stop/restart services
(5) how to read log files
(6) how to use the man pages
[(7) how to setup wireless networking - but I'd rather start with ethernet on a server]

those are the very basic things. Server will be configure by editing their config files. For that you just need to know what config options you have available and for that you just need to have internet access - although a lot of servers have by default good configs and they are also good documented in the config files themselves.

Of course "webmin" makes it easier but what if one day webmin refuses to work. What will you do then? The cli or administrating from the cli is not a science... it's quite easy actually but it requires time.

---

