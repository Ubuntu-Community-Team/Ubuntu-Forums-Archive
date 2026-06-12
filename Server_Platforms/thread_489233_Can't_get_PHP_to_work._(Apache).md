---
title: "Can't get PHP to work. (Apache)"
date: 2007-07-01
forum: Server Platforms
---

### Post by garyvdm on 2007-07-01
Hi

I'm setting up a Linux webserver for the first time.

I have installed kubuntu edgy. I have installed the following packages through adept:
[LIST]
[*]apache
[*]apache-common
[*]apache2-common
[*]apache2-mpm-prefork
[*]apache2-utils
[*]libapache2-mod-php5
[*]php5
[*]php5-common
[/LIST]

When I visit [http://localhost/](http://localhost/) things work as expected, i.e. I get a directory listing, and I can visit [http://localhost/apache2-default/](http://localhost/apache2-default/) .

I have created /var/www/test.php with the following contents:
> <?php phpinfo();?>

When I visit  [http://localhost/test.php](http://localhost/test.php) , my browser asks me the save the file, and when I examine the file, the contents has not been processed. I would expect the browser to display the php configuration information.

I have uncommented the following line in /etc/apache/httpd.conf, and /etc/apache2/apache2.conf
[LIST]
[*]AddType application/x-httpd-php .php
[*]AddType application/x-httpd-php-source .phps
[/LIST]
and restarted apache, but it did not help.

Side question: why are there 2 config directories (/etc/apache/, and /etc/apache2/) and how do I which I should be editing?

Regards, Gary

---

### Post by garyvdm on 2007-07-01
Aghh - never mind - I fixed it by uninstalling apache, and installing apache2.

Gary

---

