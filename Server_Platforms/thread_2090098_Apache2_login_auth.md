---
title: "Apache2 login auth"
date: 2012-12-01
forum: Server Platforms
---

### Post by sucabuntu on 2012-12-01
Hello 
I'm trying to configure authentication for my apache web server

I created files .htaccess and .htpasswd in the directory /var/www

This is .htaccess

AuthName "Please log in"
AuthType Basic
AuthUserFile /var/www/.htpasswd
require user sucabuntu

This is .htpasswd

sucabuntu:$apr1$3o7y[CUT]ccZ3silh/0



Why login it's not working?

---

### Post by SeijiSensei on 2012-12-01
In Ubuntu, .htaccess files are disabled by default.  To change this, edit the file /etc/apache2/sites-available/default:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
[...]

```

Replace the "AllowOverride None" line with "AllowOverride All", then restart Apache.

In general, if you have full control over the machine, it is considered better practice to place all the directives in the configuration file for the site like this one.  The .htaccess model was designed so that web hosting companies could grant individual site owners control over the features of their specific sites.

---

### Post by Lars Noodén on 2012-12-01
> **SeijiSensei said:**
> In general, if you have full control over the machine, it is considered better practice to place all the directives in the configuration file for the site like this one.  The .htaccess model was designed so that web hosting companies could grant individual site owners control over the features of their specific sites.

+1, use the config file instead of adding in .htaccess

Also, it is a good idea to put the AuthUserFile somewhere outside of /var/www/  It should be outside of any area that the web server shows to the public.

---

