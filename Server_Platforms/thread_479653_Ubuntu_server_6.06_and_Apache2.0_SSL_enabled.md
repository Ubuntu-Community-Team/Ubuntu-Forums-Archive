---
title: "Ubuntu server 6.06 and Apache2.0 SSL enabled"
date: 2007-06-20
forum: Server Platforms
---

### Post by mcc666 on 2007-06-20
Hi,
 
    I have some strange problem  with mod_ssl in name based virtual hosts. I've configured SSL and when I'm trying to reach this page via web browser I'm receiving such error message:

```
www.mydomain.pl has sent incorrect or unexpected message. Error Code: -12263.
``` 

I have no info in system logs about that. What can I do to force apache to log more information about that. What that error means?

Config of virtual host looks as follow:
```

NameVirtualHost *:443
<VirtualHost *:443>
DocumentRoot /var/www/site
ServerName www.mydomain.pl
ServerAlias mydomain.pl
AccessFileName .htaccess
<Directory "/var/www/sklepspa.pl">
AllowOverride AuthConfig
Options +Indexes
</Directory>
SSLProtocol -all +SSLv2
SSLCipherSuite SSLv2:+HIGH:+MEDIUM
SSLEngine on
SSLCertificateFile /etc/ssl/certs/cert_mydomain.pl.pem
SSLVerifyDepth 2
SSLCACertificateFile /etc/ssl/certs/cacert.pem
SSLCertificateKeyFile /etc/ssl/private/key_mydomain.pl.pem
</VirtualHost>

```


Many thanks!

MCC

---

### Post by mcc666 on 2007-06-21
Seems to be mozilla bug.

MCC

---

