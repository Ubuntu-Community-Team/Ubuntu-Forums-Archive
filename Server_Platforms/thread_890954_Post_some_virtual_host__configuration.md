---
title: "Post some virtual host  configuration"
date: 2008-08-15
forum: Server Platforms
---

### Post by 2smooth on 2008-08-15
Can you please post some virtual host configurations with a good balance between usability and security?

So i mean something a little more than this:)

```

<VirtualHost 111.22.33.44>
ServerName www.domain.tld
ServerPath /domain
DocumentRoot /web/domain
</VirtualHost>

```

---

### Post by windependence on 2008-08-16
Some ideas:

[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)
```

<VirtualHost *>
ServerAdmin webmaster@virtual-host.net
ServerName www.virtual-host.net
ServerAlias virtual-host.net
DocumentRoot /Volumes/WebServer/virtual-host/Documents
<Directory "/Volumes/WebServer/virtual-host/Documents">
Options None
AllowOverride All
Order allow,deny
Allow from all
</Directory>
ScriptAlias /cgi-bin/ "/Volumes/WebServer/virtual-host/cgi-bin/"
ErrorDocument 404 /messages/404.html
php_value include_path ".:/Volumes/WebServer/virtual-host"
php_value session.cookie_domain "virtual-host.net"
php_value session.save_path "/Volumes/WebServer/virtual-host/php-sessions"
php_value session.use_only_cookies "1"
ErrorLog "/Volumes/WebServer/virtual-host/logs/error_log"
CustomLog "/Volumes/WebServer/virtual-host/logs/referer_log" referer
CustomLog "/Volumes/WebServer/virtual-host/logs/agent_log" agent
CustomLog "/Volumes/WebServer/virtual-host/logs/access_log" common
</VirtualHost>
```

```
#<VirtualHost ip.address.of.host.some_domain.com>
#    ServerAdmin webmaster@host.some_domain.com
#    DocumentRoot /www/docs/host.some_domain.com
#    ServerName host.some_domain.com
#    ErrorLog logs/host.some_domain.com-error_log
#    CustomLog logs/host.some_domain.com-access_log common
#</VirtualHost>
```

-Tim

---

### Post by 2smooth on 2008-08-16
Thanks

> **windependence said:**
> Some ideas:

[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)
-Tim

I had already a look their, but their were only very basic setups

> 
```


<Directory "/Volumes/WebServer/virtual-host/Documents">
Options None
AllowOverride All
Order allow,deny
Allow from all
</Directory>

```


Doesn't this mean that per vhost you can use you're own .htacces file and potentially use insecure settings?

---

### Post by windependence on 2008-08-16
Well yes, you can but the idea behind the .htaccess file is to enhance security, not open it up. ;) You can put almost any directive in your vhost that you can put in your main configuration.

-Tim

---

