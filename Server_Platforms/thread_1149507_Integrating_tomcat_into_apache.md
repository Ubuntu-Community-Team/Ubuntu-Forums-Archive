---
title: "Integrating tomcat into apache"
date: 2009-05-05
forum: Server Platforms
---

### Post by _sluimers_ on 2009-05-05
See the third post

---

### Post by _sluimers_ on 2009-05-07
See the third post

---

### Post by _sluimers_ on 2009-05-08
I've been trying to configure tomcat and apache so that they can both be used on port 80 and asked here.
Problem solved now, so if anyone would like to know, there's a very good link on: [http://www.waterlovinghead.com/Tomcat](http://www.waterlovinghead.com/Tomcat)

Here's my config:

/etc/apache2/httpd.conf is empty

/etc/apache2/ports.conf 
```

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
Listen 443
</IfModule>

```

/etc/apache2/sites-available/default
```

<VirtualHost *:80>
        ServerName *mydomainname*
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        DirectoryIndex index.html index.php index.jsp
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/ajp.error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/ajp.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order Deny,Allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

        <Proxy *>
                AddDefaultCharset Off
                Order Deny,Allow
                Allow from all
        </Proxy>

        ProxyPass  /manager  http://localhost:8080/manager/html
        ProxyPassReverse /manager  http://localhost:8080/manager/html

        ProxyPass /examples ajp://localhost:8009/examples
        ProxyPassReverse /examples ajp://localhost:8009/examples

        RewriteEngine On
        RewriteCond %{REQUEST_URI} /.*\.(jsp|do)
        RewriteRule ^/(.*) ajp://localhost:8009/$1 [P]
        RewriteCond %{REQUEST_URI} /examples/.*
        RewriteRule ^/(.*) ajp://localhost:8009/$1 [P]
        RewriteCond %{REQUEST_URI} /j_security_check
        RewriteRule ^/(.*) ajp://localhost:8009/$1 [P]

</VirtualHost>



```

/etc/apache2/mods-enabled/ajp.load
```

LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_balancer_module /usr/lib/apache2/modules/mod_proxy_balancer.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule proxy_ajp_module  /usr/lib/apache2/modules/mod_proxy_ajp.so

```

/etc/tomcat6/server.xml
```

....
<Connector port="8009" enableLookups="false" protocol="AJP/1.3" redirectPort="8443" />
....

```

---

