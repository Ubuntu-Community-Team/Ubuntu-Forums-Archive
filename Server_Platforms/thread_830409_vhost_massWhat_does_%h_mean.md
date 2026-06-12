---
title: "vhost mass:What does %h mean?"
date: 2008-06-15
forum: Server Platforms
---

### Post by saj0577 on 2008-06-15
```
<VirtualHost *:80>
ServerAdmin hostmaster1@kfwebs.com
ServerName host1.kfwebs.net
Include /etc/apache2/vhost_mass.conf
LogFormat "%{Host}i %h %l %u %t "%r" %s %b" vcommon
LogFormat "%{Host}i %h %l %u %t "%r" %>s %b "%{Referer}i" "%{User-agent}i"" vcombined
CustomLog /webs/mass/access_log vcombined
RewriteEngine On
RewriteMap lowercase int:tolower
RewriteCond %{REQUEST_URI} !^/icons/
RewriteCond ${lowercase:%{SERVER_NAME}} ^(?:www\.)?(.+)$
RewriteRule ^/(.*)$ /webs/mass/%1/$1
<Directory "/">
AllowOverride All
</Directory>
</VirtualHost>
```

What do ```
%h %l %u %t "%r" %s %b
``` mean and where are they define?

Saj

---

### Post by soulresin on 2008-06-15
> **saj0577 said:**
> 

What do ```
%h %l %u %t "%r" %s %b
``` mean and where are they define?

Saj

Apache log format docs can be found at

[http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html#formats)

---

### Post by windependence on 2008-06-16
They are all variables that hold certain log data. This way you can customize what is logged and in what format.

As soulresin posted, what each variable stands for is in the documentation.

-Tim

---

