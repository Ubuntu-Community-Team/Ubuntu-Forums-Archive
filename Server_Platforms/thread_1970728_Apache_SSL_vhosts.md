---
title: "Apache SSL vhosts"
date: 2012-05-01
forum: Server Platforms
---

### Post by nickaardo on 2012-05-01
Hi,

I have a small problem on my apache conf and i've searched every where and looked a hundred times to my conf, i cant fix it !

I activated an ssl certificate on only one vhost, but the ssl is activated on all the vhosts.
Usually if you you use a ServerName, it should only be working for this serverName.... but it's on for all of them...

Hope someone can help with this, i dont know if it's a conf problem or a bug of this version of apache2, because as far as i remember all was working fine, and i haven't changed my conf.

An email from googlebot pointed this new problem :(

On my vhosts:
- On port 80, example.com and [www.example.com](www.example.com) point to /var/www/example/
- On port 80 and 443 shop.example.com point to /var/www/example2/

Why the server is listening on port 443 on example.com and [www.example.com](www.example.com) ???

Hope someone can help, anyway thanks :)

[B]EDIT :
If you dont have a default virtual host apache will take the first one available
So adding a virtualhost <VirtualHost 192.168.0.1:443> without a serverName and sslengine off fixed my problem :)[/B]


Here is my apache2.conf
```

ServerRoot "/etc/apache2"
LockFile ${APACHE_LOCK_DIR}/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 60
KeepAlive On
KeepAliveTimeout 10
MaxKeepAliveRequests 800
ServerLimit 10

<IfModule mpm_prefork_module>
    StartServers          20
    MinSpareServers       5
    MaxSpareServers      32
    MaxClients          600
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers         4
    MinSpareThreads      50
    MaxSpareThreads      125
    ThreadLimit          100
    ThreadsPerChild      100
    MaxClients           500
    MaxRequestsPerChild  1000
</IfModule>

<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

AccessFileName .htaccess
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

DefaultType text/plain
AddDefaultCharset UTF-8
HostnameLookups Off

ErrorLog ${APACHE_LOG_DIR}/error.log

Include mods-enabled/*.load
Include mods-enabled/*.conf

LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

ServerTokens Prod
ServerSignature Off
TraceEnable Off

<IfModule mod_fastcgi.c>
.   FastCgiExternalServer /usr/lib/cgi-bin/php5-fcgi -socket /var/run/php5-fpm.sock -pass-header Authorization
.   AddHandler php5-fcgi .php
 .  <LocationMatch "/(ping|status)">
.   .   SetHandler php5-fcgi-virt
.   .   Action php5-fcgi-virt /php5-fcgi virtual
.   .   Order deny,allow
.   .   Deny from all
.   .   Allow from 87.111.80.241
 .  </LocationMatch>
.   Action php5-fcgi /php5-fcgi
.   Alias /php5-fcgi /usr/lib/cgi-bin/php5-fcgi
</IfModule>

Listen 80
NameVirtualHost 213.186.44.73:80
<IfModule mod_ssl.c>
.   Listen 443
.   NameVirtualHost 213.186.44.73:443
</IfModule>

Include sites-enabled/

```

And here the vhosts
```

<VirtualHost 192.168.0.1:80>
.   ServerAdmin email@example.com
.   ServerName example.com
.   ServerAlias www.example.com
.   DocumentRoot /var/www/example/
.   <Directory /var/www/example/>
.   .   Options Indexes -FollowSymLinks MultiViews
.   .   AllowOverride All
.   .   Order allow,deny
.   .   allow from all
.   </Directory>
</VirtualHost>

<VirtualHost 192.168.0.1:80>
.   ServerAdmin email@example.com
.   ServerName shop.example.com
.   DocumentRoot /var/www/example2/
.   <Directory /var/www/example2/>
.   .   Options +ExecCGI Indexes FollowSymLinks MultiViews
.   .   AllowOverride All
.   .   Order allow,deny
.   .   allow from all
.   </Directory>
</VirtualHost>

<VirtualHost 192.168.0.1:443>
.   ServerAdmin email@example.com
.   ServerName shop.example.com
.   SSLEngine on
.   SSLCertificateFile /etc/apache2/certificates/shop_example_com.crt
.   SSLCertificateKeyFile /etc/apache2/certificates/shop_example_com.key
.   SSLCertificateChainFile /etc/apache2/certificates/gd_bundle.crt
.   DocumentRoot /var/www/example2/
.   <Directory /var/www/example2/>
.   .   Options +ExecCGI Indexes FollowSymLinks MultiViews
.   .   AllowOverride All
.   .   Order allow,deny
.   .   allow from all
.   </Directory>
</VirtualHost>

```

---

