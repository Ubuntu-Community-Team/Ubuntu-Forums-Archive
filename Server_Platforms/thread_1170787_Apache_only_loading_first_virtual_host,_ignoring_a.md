---
title: "Apache only loading first virtual host, ignoring all the rest..."
date: 2009-05-26
forum: Server Platforms
---

### Post by Ramzi on 2009-05-26
I'm actually starting to lose my mind on this problem, it's the first time i've ever encountered one of it's kind. I have an Ubuntu 8.04.2 AMD64 server, it's running Apache and Bind9, the only way i've been able to make the server work is to enable only the main virtual host from /etc/apache2/sites-available/main-site.

As soon as i try to enable the default virtual host or any of my other two virtual hosts all hell breaks loose, i use the standard default vhost with a few minor changes:

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/

# I added this part to the apache2.conf file so no need to duplicate
#       <Directory />
#               Options FollowSymLinks
#               AllowOverride None
#       </Directory>

        <Directory /var/www/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature Off

#    Alias /doc/ "/usr/share/doc/"
#    <Directory "/usr/share/doc/">
#        Options Indexes MultiViews FollowSymLinks
#        AllowOverride None
#        Order deny,allow
#        Deny from all
#        Allow from 127.0.0.0/255.0.0.0 ::1/128
#    </Directory>

</VirtualHost>
```

Here is my main site vhost:

```
<Virtualhost *>

        ServerAdmin root@localhost
        ServerName www.site.com
        ServerAlias site.com

        DocumentRoot /var/www/site

        <Directory /var/www/site>
                Options -Indexes -MultiViews FollowSymLinks
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/site.com-error.log

        LogLevel warn
        CustomLog /var/log/apache2/site.com-access.log common

</VirtualHost>
```

When i enable the default vhost it becomes the first one alphabetically and when i try to access [www.site.com](www.site.com) i get a Forbidden permission error, the error log shows it's because of the Options directive put on /var/www.

Here is my other vhost:

```
<Virtualhost *>

        ServerAdmin root@localhost
        ServerName webdav.site.com

        DocumentRoot /var/www/site

        <Directory /var/www/site>
                Options FollowSymLinks Indexes ExecCGI
                AllowOverride None
        </Directory>

        RewriteEngine On
        RewriteRule . davhandler.php

        ErrorLog /var/log/apache2/webdav.site.com-error.log

        LogLevel warn
        CustomLog /var/log/apache2/webdav.site.com-access.log common

</VirtualHost
```

When i enable it, it is behind my main site alphabetically and the server simply opens the main site like i was accessing the server without the other vhost even being enabled.

Can this all be result of a messed up bind configuration, i have A records for webdav and www, and a wildcard entry *.site.com?

And here is my probably equally messed up /etc/hosts file:

```

127.0.0.1       localhost
#i just realised this second line was pointing to another server, maybe this was the source of all my problems? the machines are behind a static NAT
192.168.1.51   www.site.com  www

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

ANY help is greatly appreciated, please can someone help me...

---

### Post by windependence on 2009-05-26
Try putting this line before your virtual hosts section:

```
NameVirtualHost *80 
```So your section would look something like this:

```
NameVirtualHost * 
<VirtualHost *>
DocumentRoot /path/to/site
ServerName alexking.dev
</VirtualHost>
…
```In your main config file you need to make sure your 

```
Include conf/extra/httpd-vhosts.conf
```is uncommented, and then within httpd-vhosts.conf uncomment the line:

```
# NameVirtualHost *:80
```

There is really no need to run Bind at all, you should really use your domain registrar's DNS servers as they are much more reliable.

-Tim

---

