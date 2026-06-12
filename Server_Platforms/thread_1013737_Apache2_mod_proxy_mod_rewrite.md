---
title: "Apache2 mod_proxy mod_rewrite"
date: 2008-12-17
forum: Server Platforms
---

### Post by aleix on 2008-12-17
Hi everybody,

I've been 4 days trying to do something I thought would be easy, but I'm having a lot of problems.

So, what I want to do is FORWARDING web petitions from 1 webserver to another.

Well, this is the scenary:
 
[b]1 router, and 3 Servers (S1, S2, and S3), and a domain [http://www.example.com](http://www.example.com)
S1 - 10.0.0.5, S2 - 10.0.0.6, S3 - 10.0.0.7
S1 is the Server where Router sends all peticions throught the port 8080
S3 is the Server where Router sends all peticions throught the port 80[/b]

The objective is that when I write [http://www.example.com:8080](http://www.example.com:8080), S1 sends me to S2.

So, I followed these steps:

[list]
**Enable needed modules:**
```
a2enmod rewrite
a2enmod proxy
a2enmod proxy_http

apache restart
```
[/list]
[list]
**Edit /etc/apache2/mods-enabled/proxy.conf**
```
<IfModule mod_proxy.c>
        ProxyRequests Off
        <Proxy *>
               AddDefaultCharset off
                Order deny,allow
                Allow from all
        </Proxy>
        ProxyVia On
</IfModule>
```
[/list]
[list]
**Create /etc/apache2/sites-available/example**
```
NameVirtualHost *:8080
<VirtualHost *:8080>
        <Proxy *>
                Order deny,allow
                Allow from all
        </Proxy>
        ServerName              www.example.com
        RewriteEngine on
        ProxyPass               / http://10.0.0.6
        ProxyPassReverse        / http://10.0.0.6
</VirtualHost>
```
[/list]
[list]
**Enable the new site**
```
a2ensite example
```
[/list]

Finally I restarted apache and added **10.0.0.6  [www.example.com](www.example.com)** to my** /etc/hosts** file.

Well, when I tried it, I see the login page of my web application in 10.0.0.6, but when I login, I get this error:
```
Proxy Error

The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request POST /login.

Reason: DNS lookup failure for: 10.0.0.6login

Apache/2.2.3 (Debian) Server at egestio.ditecsa.com Port 8080
```

Anybody knows whats the problem?

Thanks a lot friends.

---

### Post by RealPSL on 2008-12-24
Try adding a trailing "/" to [http://10.0.0.6](http://10.0.0.6). So it would be 
```

ProxyPass               / http://10.0.0.6/
ProxyPassReverse        / http://10.0.0.6/

```

---

