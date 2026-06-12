---
title: "[SOLVED] Apache Virtual Host Comes Up with wrong site"
date: 2008-09-05
forum: Server Platforms
---

### Post by infecticide on 2008-09-05
I have an issue with my virtual hosts where my xyz.domain2.com is coming up with my default [www.domain1.com](www.domain1.com) site.

The [www.domain2.com](www.domain2.com) works however.

All of my domain1.com subdomains work fine.

/etc/apache2/sites-available:
> 
000-default (domain1.com and [www.domain1.com](www.domain1.com))
001-abc.domain1.com
002-def.domain1.com
003-abc.domain2.com
004-domain2.com (domain2.com and [www.domain2.com](www.domain2.com))



xyz.domain2.com.conf
> 
<VirtualHost *:80>
        ServerName      xyz.domain2.com
        ServerAdmin [email]steve@tuxsteve.net[/email]
        TransferLog /var/log/apache2/xyz.domain2.com-access_log

ErrorLog /var/log/apache2/xyz.domain2.com-error_log
LogLevel warn
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
CustomLog /var/log/apache2/xyz.domain2.com-access_log combined

DocumentRoot    /var/www/domain2/xyz/htdocs
<Directory "/var/www/domain2/xyz/htdocs">
        Options Indexes FollowSymLinks
        AllowOverride None
        Order allow,deny
        Allow from all
</Directory>

Alias /icons/ "/usr/share/apache2/icons/"
<Directory "/usr/share/apache2/icons/">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

ScriptAlias /cgi-bin/ /var/www/domain2/xyz/cgi-bin/

<Directory "/var/www/domain2/xyz/cgi-bin/">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>

##### AWSTATS #####
Alias /awstats/icons "/usr/share/awstats/icon/"
ScriptAlias /awstats/ "/usr/lib/cgi-bin/awstats.pl"
ScriptAlias /awstats "/usr/lib/cgi-bin/awstats.pl"
ScriptAlias /awstats.pl "/usr/lib/cgi-bin/awstats.pl"

</VirtualHost>


I hope this provides enough information to assist in debugging this strange issue.

---

### Post by infecticide on 2008-09-05
Turns out I'm an idiot... :p

I symlinked xyz.domain2.com to the conf file for [www.domain2.com](www.domain2.com).

Fixed that and all is well!

---

### Post by mbeach on 2008-09-06
one of the reasons to use "a2ensite"

---

