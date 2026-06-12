---
title: "Apache2 SSL server timeout (not opening port 443) - no errors"
date: 2015-05-21
forum: Server Platforms
---

### Post by BEaSTFX on 2015-05-21
Hello, i installed a geotrust ssl and configured it on apache2. The apache config is okay, no errors and the http version of the website is working. 
The https and the domainame.com:443 doesnt not open, it tries to conenct and gives me time out. I'm not sure what to do maybe there is something wrong with the virtualhost configuration.

> apachectl configtest
Syntax OK


> a2enmod ssl
Module ssl already enabled


The only thing in the apache log is:

> [Wed May 20 14:46:10.904922 2015] [mpm_event:notice] [pid 20655:tid 140477527750528] AH00489: Apache/2.4.7 (Ubuntu) OpenSSL/1.0.1f configured -- resuming normal operations



This is my vhost conf:

> <VirtualHost *:80>
  ServerName domainname.com

  DocumentRoot /var/www/domainname/current
  ProxyPassMatch ^/(.*\.php(/.*)?)$ fcgi://127.0.0.1:9000/var/www/domainname/current/$1
  DirectoryIndex index.html index.php

  <Directory /var/www/domainname/current>
    Options FollowSymLinks
    AllowOverride All
    Require all granted
  </Directory>

  <Directory />
    Options FollowSymLinks
    AllowOverride None
  </Directory>

  <Location /server-status>
    SetHandler server-status
    Require local
  </Location>

  RewriteEngine On

  ErrorLog /var/log/apache2/domainname.com-error.log
  CustomLog /var/log/apache2/domainname.com-access.log combined

  DirectoryIndex index.html index.php


  RewriteCond %{DOCUMENT_ROOT}/system/maintenance.html -f
  RewriteCond %{SCRIPT_FILENAME} !maintenance.html
  RewriteRule ^.*$ /system/maintenance.html [L]
</VirtualHost>

    <VirtualHost *:443>
           ServerName [www.domainname.com](www.domainname.com)
            DocumentRoot /var/www/domainname/current
            SSLEngine on
            SSLCertificateFile /usr/local/ssl/geotrust.crt
            SSLCertificateKeyFile /usr/local/ssl/privatekey.key
            SSLCertificateChainFile /usr/local/ssl/GeoTrustDVSSLCAG4.crt
    </VirtualHost>


I will gladly appreciate if you could help.

Best regards

---

### Post by allan7 on 2015-05-21
Did you check iptable/firewall if it's allowing 443?

---

