---
title: "apache with php5 stop working"
date: 2009-12-15
forum: Server Platforms
---

### Post by mitjab on 2009-12-15
I update system and apache stop working.

[http://82.149.25.222:8080/](http://82.149.25.222:8080/)

but

[http://82.149.25.222:10000](http://82.149.25.222:10000) still works. Can anyone help me or give me an advice why and how to fix that?

I already try

sudo apt-get install --reinstall apache2, libapache2-mod-php5 and php5 with no help


regards

---

### Post by idlemind324 on 2009-12-15
Looks like your server is presenting the .phtml file without processing it first? Is the .phtml file for PHP or SSI (Server Side Includes)? If so you need to declare that in your http.conf. The installer should have moved your old configuration to http.conf.bak I believe. You can always reference that vs. what Apache is currently loading.

Tim

---

### Post by mitjab on 2009-12-15
LOG:
[Tue Dec 15 18:26:00 2009] [alert] [client 82.149.25.222] /home/mitjab/public_html/.htaccess: Invalid command 'php_flag', perhaps misspelled or defined by a module not included in the server configuration

where can i find httpd.conf?

mitjab@server:/etc/apache2$ dir
apache2.conf            apache2.conf.orig  conf.d          envvars   httpd.conf  mods-available  ports.conf            README           sites-enabled  workers.properties
apache2.conf.dpkg-dist  auth-files         dav_svn.passwd  flyspray  magic       mods-enabled    ports.conf.dpkg-dist  sites-available  ssl
mitjab@server:/etc/apache2$ cd /etc/php5/apache2/
mitjab@server:/etc/php5/apache2$ dir
conf.d  php.ini  php.ini.ucf-dist
mitjab@server:/etc/php5/apache2$


I can not find it.

---

### Post by dmizer on 2009-12-15
Moved to server platforms. You should get more help here.

Edit:
[s]In Ubuntu, httpd.conf = apache2.conf[/s]

Edit 2:
```
/etc/apache2$ dir
apache2.conf apache2.conf.orig conf.d envvars [COLOR="Red"]httpd.conf[/COLOR] mods-available ports.conf README sites-enabled workers.properties
apache2.conf.dpkg-dist auth-files dav_svn.passwd flyspray magic mods-enabled ports.conf.dpkg-dist sites-available ssl
```
Looks like I was mistaken.

---

### Post by mitjab on 2009-12-15
i copy apache2.conf.dpkg-dist to apache2.conf but it is the same. Here is also no data fo rphp in apache2.conf

---

### Post by cdenley on 2009-12-15
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by HighCommander540 on 2009-12-15
> **cdenley said:**
> ```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

The easiest and most functional way in Ubuntu. Lol, dir.

---

### Post by munky99999 on 2009-12-15
> **cdenley said:**
> ```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

That should fix you up. If not. You need a few extra packages.

[https://help.ubuntu.com/9.10/serverguide/C/php5.html](https://help.ubuntu.com/9.10/serverguide/C/php5.html)

sudo apt-get install php5-cli
or one of the others listed.

---

