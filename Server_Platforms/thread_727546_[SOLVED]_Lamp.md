---
title: "[SOLVED] Lamp"
date: 2008-03-17
forum: Server Platforms
---

### Post by anderskitson on 2008-03-17
I am using this site [http://howtoforge.com/ubuntu_lamp_for_newbies](http://howtoforge.com/ubuntu_lamp_for_newbies) to Guide me Through a straighforward Lamp Install. All I want to be able to do is use it localy for now, that's all I need because I am just learning php and Mysql. I am stuck at testing php. When I follow this link, [http://localhost/testphp.php](http://localhost/testphp.php) I am just prompted to download the file not view the test page like it states, what am I missing here. "I have Restarted Apache Server As Well"

---

### Post by hackertarget on 2008-03-17
Was this command from the guide successful?

[INDENT]sudo apt-get install php5 libapache2-mod-php5[/INDENT]

Once you have installed these you should have a line in your httpd configs for AddType application/x-httpd-php .php.

You can test this is present by typing: grep -R php /etc/apache2/*

After restarting apache this should work.

---

### Post by anderskitson on 2008-03-17
This Is what I get from Grep
> /etc/apache2/mods-available/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
/etc/apache2/mods-available/php5.conf:<IfModule mod_php5.c>
/etc/apache2/mods-available/php5.conf:  AddType application/x-httpd-php .php .phtml .php3
/etc/apache2/mods-available/php5.conf:  AddType application/x-httpd-php-source .phps
/etc/apache2/mods-available/php5.load:LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
/etc/apache2/mods-enabled/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

But it is still doing the same thing

---

### Post by anderskitson on 2008-03-18
Not sure if this helps but in my
httpd.conf    file all that is in there is this
> servername localhost

---

### Post by anderskitson on 2008-03-18
I fixed my problem all is good

---

