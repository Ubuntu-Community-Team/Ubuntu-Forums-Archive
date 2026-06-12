---
title: "Squirrelmail problem"
date: 2010-09-25
forum: Server Platforms
---

### Post by vidak.milacic on 2010-09-25
Hi,

I have problem with Squirrelmail and Ubuntu 10.04 server.

I used [https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail) tutorial to install it and on my two computers and one VPS have same problem.

Insted of seeing login screeen on [http://example.com/squirrelmail](http://example.com/squirrelmail)  squirrelmail index.php is downloading. All sites are working OK.


Thanks in advance.! :)

---

### Post by HermanAB on 2010-09-26
Howdy,

This is not really a problem of Squirrel.  The problem is that Apache is not configured properly.  You need to install the PHP modules in Apache and restart it.

---

### Post by vidak.milacic on 2010-09-26
Thanks HermanAB,

but everything is OK with my LAMP setting, all sites working good.
I did sudo a2ensite squirrelmail and sudo /etc/init.d/apache2 force-reload but have same problem on Ubuntu Desktop 10.04, Ubuntu Server 10.04 and VPS Ubuntu server 10.04 :( . When I try to open [http://localhost_or_my_site/squirrelmail](http://localhost_or_my_site/squirrelmail) insted of seeing login screen, squirrelmail index.php is downloaded.

---

### Post by SeijiSensei on 2010-09-26
> **vidak.milacic said:**
> everything is OK with my LAMP setting, all sites working good.
I did sudo a2ensite squirrelmail and sudo /etc/init.d/apache2 force-reload but have same problem on Ubuntu Desktop 10.04, Ubuntu Server 10.04 and VPS Ubuntu server 10.04 :( . When I try to open [http://localhost_or_my_site/squirrelmail](http://localhost_or_my_site/squirrelmail) insted of seeing login screen, squirrelmail index.php is downloaded.

Do you have the files /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-enabled/php5.load on your server?  php5.load loads the PHP module into Apache, while php5.conf contains the all-important [SetHandler]("http://httpd.apache.org/docs/2.0/mod/core.html#sethandler") directive which tells Apache to apply PHP parsing to files ending in, among other things, the .php extension.  Without a specified handler for a file extension, Apache attempts to download the file directly to the browser causing the pop-up message you see.

---

