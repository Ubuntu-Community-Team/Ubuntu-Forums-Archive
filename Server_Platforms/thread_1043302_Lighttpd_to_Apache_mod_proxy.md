---
title: "Lighttpd to Apache mod_proxy"
date: 2009-01-18
forum: Server Platforms
---

### Post by Thirtysixway on 2009-01-18
I currently have lighttpd setup so that a different hostname will either redirect to a different folder, or a different server.

```

$HTTP["host"] =~ "oxy.noobbox.com" {
        server.document-root = "/var/www/oxy"
}
$HTTP["host"] =~ "sora.noobbox.com" {
        server.document-root = "/var/www"
}
$HTTP["host"] =~ "ipod.hopto.org" {
        server.document-root = "/var/www/ipod.hopto.org"
}
 
$HTTP["host"] =~ "waim.noobbox.com" {
    proxy.server  = ( "" => ( ( "host" => "192.168.1.11" ) ) )
}

```


I want to move back over to Apache, so can I get the above functionality with mod_proxy?  If so, how do I configure that?

---

### Post by Thirtysixway on 2009-01-19
Solved.  After some googling, it was very simple.

First, I enabled the mod_proxy and mod_proxy_html modules by running
```

a2enmod proxy
a2enmod proxy_html

```

Editing my /etc/apache2/httpd.conf fle I added virtual hosts for each domain name I'm using.  Then added a special configuration for the proxy.

```

NameVirtualHost *

<VirtualHost *>
        ServerName oxy.noobbox.com
        DocumentRoot /var/www/oxy
</VirtualHost>

<VirtualHost *>
        ServerName sora.noobbox.com
        DocumentRoot /var/www
</VirtualHost>

<VirtualHost *>
        DocumentRoot /var/www
</VirtualHost>

<VirtualHost *>
        ServerName ipod.hopto.org
        DocumentRoot /var/www/ipod.hopto.org
</VirtualHost>

<VirtualHost *>
        ServerName waim.noobbox.com
        DocumentRoot /var/www/waim 
        ProxyRequests Off

        <Proxy *>
          Order deny,allow
          Allow from all  
        </Proxy>

        ProxyPass / http://192.168.1.11/
        ProxyPassReverse / http://192.168.1.11/
</VirtualHost>

```


so now I have preserved the simple proxy functionality of lighttpd with apache.  It seems pretty straightforward now that I have it configured correctly.

---

