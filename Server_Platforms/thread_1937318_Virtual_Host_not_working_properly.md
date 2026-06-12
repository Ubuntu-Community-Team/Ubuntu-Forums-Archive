---
title: "Virtual Host not working properly"
date: 2012-03-07
forum: Server Platforms
---

### Post by newbie67 on 2012-03-07
Hi,
I am new to Linux/Apache. 
 
I am trying to set up two virtual hosts. For this, I changed the file /etc/apache2/apache2.conf as follow:
......
#Include sites-enabled 
 
<VirtualHost *:80>
DocumentRoot "/var/www"
</VirtualHost>
 
<VirtualHost *:80>
DocumentRoot "/var/www/applications/myapps"
ServerName myapps.myserver.com
 
<directory "/var/www/applications/myapps">
Allow from all
Options +Indexes
</directory>
</VirtualHost>
 
<VirtualHost *:80>
DocumentRoot "/var/www/phpmyadmin"
ServerName phpmyadmin.myserver.com
 
<directory "/var/www/phpmyadmin">
Allow from all
Options +Indexes
</directory>
</VirtualHost>
 
Now, I can access phpmyadmin application by the URL [http://phpmyadmin.myserver.com](http://phpmyadmin.myserver.com). However, I cannot access the myapps application by the URL [http://myapps.myserver.com](http://myapps.myserver.com). If I do so, a default index.html placed at /var/www is shown. The actual index.html of myapps, can be accessed if I give the full URL like [http://myapps.myserver.com/applications/myapps/index.html](http://myapps.myserver.com/applications/myapps/index.html). What is the problem? 
 
Earlier I put separate configuration files for phpmyadmin and myapps in /etc/apache2/sites-enabled. However, the same problem was seen there also. 
Any help is appreciated.
Thanks in advance,

---

### Post by nothingspecial on 2012-03-08
*Thread moved to **Server Platforms**.*

---

