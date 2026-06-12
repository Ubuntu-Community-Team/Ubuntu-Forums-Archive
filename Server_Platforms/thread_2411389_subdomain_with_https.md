---
title: "subdomain with https"
date: 2019-01-29
forum: Server Platforms
---

### Post by cazz on 2019-01-29
Hi
I have letsencrypt on my domain on my ubuntu server 18.04 that run apache2

Everything looks nice and works nice too but now I like to add a subdomain to my domain and I use then virtual host.
But the subdomain I need to make sure it run HTTPS to because it going to use proxypass to send me to another server that running webmail.

I have try alot but not even got connect to my webmail thru the subdomain, only works local when I use the IP address.

domain.nu and domain.se is not real, I have change my real to just show some example ;)

A friend use this code and got it to work, he is not sure how

```
<VirtualHost *:80>
    ProxyPreserveHost On
	SSLProxyEngine on
    ProxyPass "/" "http://192.168.0.10/SOGo/"
    ProxyPassReverse "/" "http://192.168.0.10/SOGo/"
    ServerName webmail.domain.nu
RewriteEngine on
RewriteCond %{SERVER_NAME} =webmail.domain.nu
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>
```


it does HTTP to HTTPS and send it to a backend server


But it does not work for me.


It say


that is wrong domain cert (I have two domain on the server domain.nu and domain.se)
and somehow it like to use the other domain and when I say it is ok it show the domain.se frontpage




The latest I did try with this code from this Place
[https://github.com/streamaserver/streama/wiki/Deploying-SSL-on-Apache2-on-Ubuntu-(with-letsEncrypt-&-Certbot)](https://github.com/streamaserver/streama/wiki/Deploying-SSL-on-Apache2-on-Ubuntu-(with-letsEncrypt-&-Certbot))


```
<VirtualHost *:80>
    ServerName webmail.domain.nu
    ServerAdmin webmaster@localhost
    ErrorLog /var/log/apache2/syslog
    LogLevel warn
    CustomLog /var/log/apache2/syslog combined
    ServerSignature on

    ProxyPreserveHost On
    ProxyPass / http://192.168.0.10/SOGo/
    ProxyPassReverse / http://192.168.0.10/SOGo/

    RewriteEngine on
    RewriteCond %{SERVER_NAME} =webmail.domain.nu
    RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>

<VirtualHost *:443>
    ServerName webmail.domain.nu
    ServerAdmin webmaster@localhost
    ErrorLog /var/log/apache2/syslog
    LogLevel warn
    CustomLog /var/log/apache2/syslog combined
    ServerSignature On

    Include /etc/letsencrypt/options-ssl-apache.conf
    SSLCertificateFile  /etc/letsencrypt/live/domain.nu/fullchain.pem
    SSLCertificateKeyFile /etc/letsencrypt/live/domain.nu/privkey.pem

    ProxyPreserveHost On
    ProxyPass / http://192.168.0.10/SOGo:443/
    ProxyPassReverse / http://192.168.0.10/SOGo:443/

    SSLProxyEngine On
    SSLProxyVerify none
    SSLProxyCheckPeerCN off
    SSLProxyCheckPeerName off
    SSLProxyCheckPeerExpire off
</VirtualHost>

```

At first it does not like that the address is webmail.domain.nu, it say it have to be domain.nu so I maybe have to create a cert for the subdomain too.
But I say in the browser that is ok and go further but then is say 500 error Internal Server Error

---

