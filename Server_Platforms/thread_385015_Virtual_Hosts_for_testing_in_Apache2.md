---
title: "Virtual Hosts for testing in Apache2"
date: 2007-03-15
forum: Server Platforms
---

### Post by josno on 2007-03-15
Hi,

I'm trying to create a virtual host for testing a website locally. Here's my virtual host config file:
```
<VirtualHost *>
        ServerName xnet-trunk.com
        ServerAlias www.xnet-trunk.com
        ServerAdmin webmaster@localhost
        DocumentRoot /home/rayj/XNET/trunk/public
        <Directory /home/rayj/XNET/trunk/public/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                Allow from all
        </Directory>

        CustomLog /var/log/apache2/xnet-trunk-access.log combined

</VirtualHost>
```
I have xnet-trunk.com redirecting to 127.0.0.1 in /etc/hosts fine, and the permissions on the files are set to rwxr-xr-x, but I get an internal server error 500 when I browse to [http://xnet-trunk.com](http://xnet-trunk.com). Any ideas why?

Thanks

---

### Post by josno on 2007-03-15
Don't worry - found out it was an error in a .htaccess file I had in the directory. :roll:

---

