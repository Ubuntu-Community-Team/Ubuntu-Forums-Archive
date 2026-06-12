---
title: "Configuring Apache2?"
date: 2005-10-27
forum: Server Platforms
---

### Post by hcker2000 on 2005-10-27
I'v been trying to use webmin to configure my apache2 which has worked so far but there are a few things I can't seem to do that I need to.

My html document root is /var/www/html I need to point apache2 to this directory. I think I have this set up right in my /etc/apache2/httpd.conf file.

Listen *:85
KeepAlive on
DocumentRoot /var/www/html

Now I also need to tell apache2 to show .htm and .html files. I have no idea how to do this.

I also need to know what package to install to get java scripts going.

The rest of the perl and stuff I think I can get setup on my own threw webmin.

---

### Post by wellery on 2005-10-27
have a look at changing this file:


**[SIZE=2]/usr/local/apache2/conf/mime.types[/SIZE]**

---

### Post by hcker2000 on 2005-10-27
There is no file in that location. I did a locate for mime.types and found some but none in an apache2 foulder.

---

### Post by hcker2000 on 2005-10-28
Problem solved had to edit

/etc/apache2/sites-enabled/000-default

and 

/etc/apache2/httpd.conf

---

