---
title: "Deny acces to tomcat based on ip"
date: 2010-02-11
forum: Server Platforms
---

### Post by vtv on 2010-02-11
Hi, 

We need to only allow access to a web page only to some ips. We want to do this via Apache but it seems like the standard way of denying all and allowing some ips doesn't work because we mount a webapp using tomcat.

The sites-enabled file looks like this:

```

NameVirtualHost *:443
<VirtualHost *:443>
  ServerName web.address.com:443

  ErrorLog /var/log/apache2/app_ssl_error.log
  CustomLog /var/log/apache2/app_ssl_access.log

  SSLEngine On
  SSLCertificateFile /etc/apache2/ssl/web.address.com.crt
  SSLCertificateKeyFile /etc/apache2/ssl/web.address.com.key

  JkMount /* application

  <Directory ".*WEB-INF.*">
     AllowOverride None
     Order Deny,Allow
     Allow from xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
  </Directory>
</VirtualHost>

```It looks like it is no good denying access this way since the user gets the application mounted anyway.

My searches have so far been fruitless. Any help is very appreciated.

---

### Post by jfparis on 2010-02-14
You might want to try with <location>

```

    <location />
        Order Deny,Allow
        Deny from all
        allow from 10.0.1.4
    </location>

```Apache is proxying the request to tomcat and that might work

If that does not work two suggestion:
* try within tomcat
* do not use jkmount but use apache reverse proxy capabilities. In that case the allow/deny will work for sure but the proxy mechanism might not be optimal

---

### Post by vtv on 2010-02-17
Thank you very much! You just relieved me from a major headache.

:popcorn:

---

