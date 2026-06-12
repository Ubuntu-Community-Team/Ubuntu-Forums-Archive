---
title: "Close access to non-existing sub-domains with https?"
date: 2019-06-06
forum: Server Platforms
---

### Post by CrewDK on 2019-06-06
I have some VDS with apache on board and 2-3 configured domains on each VDS. 

My configs: for http

```
<VirtualHost *:80>
ServerAdmin mymail@gmail.com

ServerName example.ru
ServerAlias www.example.ru
ServerAlias 111.222.333.444

DocumentRoot /var/www/example.ru/www/

<Directory />
  Options FollowSymLinks
  AllowOverride All
 </Directory>

<Directory /var/www/example.ru/www/>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  allow from all
</Directory>

ErrorLog /var/www/example.ru/logs/error.log
LogLevel core:info warn

CustomLog /var/www/example.ru/logs/access.log combined

Redirect 404 /favicon.ico
  <Location /favicon.ico>
    ErrorDocument 404 "No favicon"
  </Location>

<IfModule dir_module>
  DirectoryIndex index.php index.html
</IfModule>

  RewriteEngine on
  RewriteCond %{SERVER_NAME} =example.ru
  RewriteCond %{SERVER_NAME} =111.222.333.444 [OR]
  RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

</VirtualHost>
```

and for https: 

```
<IfModule mod_ssl.c>

<VirtualHost *:443>
ServerAdmin mymail@gmail.com

ServerName example.ru

DocumentRoot /var/www/example.ru/www/

<Directory />
  Options FollowSymLinks
  AllowOverride All
 </Directory>

<Directory /var/www/example.ru/www/>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  allow from all
</Directory>
ErrorLog /var/www/example.ru/logs/error.log

LogLevel core:info warn ssl:warn

CustomLog /var/www/example.ru/logs/access.log combined

Redirect 404 /favicon.ico
  <Location /favicon.ico>
    ErrorDocument 404 "No favicon"
  </Location>

<IfModule dir_module>
  DirectoryIndex index.php index.html
</IfModule>

SSLEngine on
SSLCertificateFile      /etc/letsencrypt/example.ru/fullchain.pem
SSLCertificateKeyFile   /etc/letsencrypt/example.ru/privkey.pem

# Uncomment the following directive when using client certificate authentication
#SSLCACertificateFile    /path/to/ca_certs_for_client_authentication

# HSTS (mod_headers is required) (15768000 seconds = 6 months)
Header always set Strict-Transport-Security "max-age=15768000"

# modern configuration, tweak to your needs
SSLProtocol             all -SSLv3 -TLSv1 -TLSv1.1
SSLCipherSuite          ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AE
S256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256
SSLHonorCipherOrder     on
SSLCompression          off
SSLSessionTickets       off

# Add vhost name to log entries:
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-agent}i\"" vhost_combined
LogFormat "%v %h %l %u %t \"%r\" %>s %b" vhost_common

</VirtualHost>

# OCSP Stapling, only in httpd 2.3.3 and later
SSLUseStapling          on
SSLStaplingResponderTimeout 5
SSLStaplingReturnResponderErrors off
SSLStaplingCache        shmcb:/var/run/ocsp(128000)

</IfModule>
```

Some domains have sub-domains with public or non-public access. For all domains I have wildcard letsencrypt certificates so all working with HTTPS. 
So here is my problem. When I'm working with simple http I have setup simple default virtual host config to stop spamers access to non-existing sub-domains, like pma.example.ru and so they have 404 error. 

```

<VirtualHost *:80>
  ServerName dummy
  Redirect 404 /
</VirtualHost>
```

But this is not working for HTTPS. So is there any way to fix this?

---

