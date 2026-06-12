---
title: "Apache 2.2 SSL virtual host don't work"
date: 2009-03-04
forum: Server Platforms
---

### Post by prodsacnetworking on 2009-03-04
Hi, 

II compiled a second instance of apache with SSL.

./configure --prefix=/usr/local/apache2_php5_ssl --disable-include --disable-asis --enable-vhost-alias --disable-negotiation --disable-actions --disable-userdir --enable-rewrite --enable-so --enable-ssl --with-mpm=prefork

I generated a self signed certificate.
I created a vhost file:
[I][SIZE="1"]
<VirtualHost *>
    ServerAdmin [email]sysadmin-enroute@domaine.com[/email]
    DocumentRoot /data/www/domain-sites/domain.com
    ServerName [www.domain.com](www.domain.com)
    ServerAlias domain.com *.domain.com beta.domain2.com
SSLEngine on
SSLCertificateFile /data/ssl/certificats/www.domain.com.crt
SSLCertificateKeyFile /data/ssl/certificats/www.domain.com.key
SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
CustomLog logs/ssl_request_log \
   "%t %h %{SSL_PROTOCOL}x %{SSL_CIPHER}x \"%r\" %b"
    <Directory "/data/www/domain-sites/domain.com/">
    Options -Indexes +FollowSymLinks -MultiViews
    AllowOverride All
    Order allow,deny
    Allow from all
    </Directory>
    ErrorLog /var/log/httpd/www.domain.com-error_log
    CustomLog /var/log/httpd/www.domain.com-access_log combinedio
</VirtualHost>[/SIZE][/I]

And it won't work..

Ideas?

---

### Post by Titan8990 on 2009-03-04
Why didn't you use the package management system?

---

### Post by HermanAB on 2009-03-04
Note that a SSL host must use a static IP address.

Cheers,

Herman

---

