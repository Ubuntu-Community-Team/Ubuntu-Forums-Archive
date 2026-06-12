---
title: "Apache2 SSL"
date: 2007-11-30
forum: Server Platforms
---

### Post by jacknetuk on 2007-11-30
Ive got apache2 and mod_ssl installed successfully. Heres my virtualhost file for apache
```

<VirtualHost *:443>
ServerAdmin jack@jacknet.co.uk
DocumentRoot /var/www/proxy
<Directory "/var/www/proxy">
allow from all
Options +Indexes
</Directory>
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem
</VirtualHost>

```
If i try to visit the site that i want to visit lets say ssl.examplessl.org i get page cannot be displayed but if i visit example.org which is my default site for any site that doesnt have a virtualhost set.

Ive also attached my virtual hosts from in webmin because its a nicer view.

Thanks
Jack Dunn

---

