---
title: "Reverse Proxy with Apache2 in Ubuntu Feisty"
date: 2007-08-13
forum: Server Platforms
---

### Post by neiuxe on 2007-08-13
Reverse Proxy 

We are trying to reverse proxy with apach2 in ubuntu server (feisty), it reverses to IIS 6.0, after several connections the proxy gets stuck, the error we have is: 

```
The proxy server could not handle the request GET /proxy/.
```

or 

```
Error reading from remote server
```


Apache Conf

```
  <VirtualHost *:80>
        DocumentRoot /var/www/vhosts/example.com
        ServerName www.example.com 
    	ServerAlias example.com

	ProxyRequests off
	ProxyPass /proxy/ http://proxy.example.com/
	ProxyHTMLURLMap http://proxy.example.com /proxy
 
    <Location /proxy/>
        Order allow,deny
        Allow from all
        ProxyPassReverse /
        SetOutputFilter  proxy-html
        RequestHeader    unset  Accept-Encoding
    </Location> 
</vhosts>  
```

I would be thankful if anyone can help me with this issue.

---

