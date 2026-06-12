---
title: "Password protecting a Directory in Apache2"
date: 2008-06-19
forum: Server Platforms
---

### Post by Nitewalker on 2008-06-19
I am trying to password protect a directory in my Apache2 site, and am not having much luck.  I found a tutorial on creating a .htaccess & .htpasswd file in the directory that I want to protect, and it said then to change the /etc/apache2/sites-available/default file to read "AllowOverride None to AllowOverride All", and then restart apache2.  When I do this and try and access my site, the directory that I wanted to protect is no longer listed:confused:

---

### Post by molotov00 on 2008-06-19
Changing the AllowOverride directive only changes whether or not the .htaccess files in that directory are parsed and whether what is in that file 'overrides' the contents of the Apache config file.

Creating .htaccess and .htpasswd files is the way to password protect folders in Apache.

Without more detailed information from you, regarding your specific error and the tutorial you followed, there's nothing we can do to help.

---

### Post by Nitewalker on 2008-06-19
The tutorial that I used came from [http://ag.arizona.edu/ecat/web/password-protect.html](http://ag.arizona.edu/ecat/web/password-protect.html) and [https://help.ubuntu.com/communtiy/EnableingUseOfApacheHtaccesFiles](https://help.ubuntu.com/communtiy/EnableingUseOfApacheHtaccesFiles) - Community and this was all gotten from [http://my.opera.com/IKT/blog/ubuntu-apache2-htaccess](http://my.opera.com/IKT/blog/ubuntu-apache2-htaccess).

I followed the information in the sheet from "ag.arizona.edu", first creating a directory in /var/www titled "images", and then created the .htaccess file and .htpasswd file there, then made the change to my /etc/apache2/sites-enabled/defaut file to what they said, the only thing I saw differnt in my file is that it didn't have the #comment this directive is you want to see apache2's or the next two listed as # default start page or #RedirectMathchg   </Directory>

When I wrote my "AuthUserFile" I put "/var/www/images"
and I also added the "<Directory /var/www/images>, AllowOverride All, </Directory> to the /etc/apache2/apache2.conf.

---

