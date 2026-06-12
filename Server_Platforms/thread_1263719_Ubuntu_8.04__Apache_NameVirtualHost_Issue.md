---
title: "Ubuntu 8.04 / Apache NameVirtualHost Issue"
date: 2009-09-11
forum: Server Platforms
---

### Post by eymorais on 2009-09-11
Hello Everyone!

Issue this morning with my new virtual host on my Lamp server...

> 
 Starting web server apache2
Syntax error on line 1 of /etc/apache2/sites-enabled/site-dev.domain.com.conf:
Invalid command '<NameVirtualHost', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!
Copy and pasted my original working site config file and updated with my new domain information and directories. I have then created a sym link from my /sites-available to my /sites-enabled directory.

Here is a copy of the config file.

> 
<NameVirtualHost site-dev.domain.com>

# defining site-dev.domain.com

        DocumentRoot /var/www/site-dev
        ServerName site-dev.domain.com[FONT=monospace]
[/FONT]ServerAlias [www.site-dev.domain.com]("http://www.site-dev.domain.com")
             CustomLog /var/log/apache2/site-dev.domain.com-access.log combined

    <Directory /var/www/site-dev>
        AllowOverride AuthConfig
        AuthType Basic
        AuthName "Restricted Files"
        AuthUserFile /etc/apache2/htpasswd/site-dev.htpasswd
        Require valid-user
    </Directory>

</NameVirtualHost>



---

### Post by terazen on 2009-09-11
If you look at /etc/apache2/sites-available/default it looks like this:

NameVirtualHost *
<VirtualHost *>
 ...
</VirtualHost>

Check the <> around VirtualHost and not NameVirtualHost.

---

### Post by eymorais on 2009-09-11
Thanks!

It did the trick. Was working with the wrong config file as my template.

---

