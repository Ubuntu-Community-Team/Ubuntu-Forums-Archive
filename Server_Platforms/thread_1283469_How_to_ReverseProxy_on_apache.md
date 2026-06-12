---
title: "How to ReverseProxy on apache"
date: 2009-10-05
forum: Server Platforms
---

### Post by theRemix on 2009-10-05
i got the module loaded fine, however, i get 500  errors when using Proxy. 
 
i think the problem is that i don't know how to do a reverse proxy, and  i've read the apache documentation over and over.
 
in my .htaccess (yes i've tried it in my vhost config file as well, same  thing) 
                      ```
ProxyRequests Off 
<Proxy *> 
        Order deny,allow 
        Allow from all 
</Proxy> 
ProxyPass /images/ http://assets.myvhost.com/images/ 
ProxyPassReverse /images/ http://assets.myvhost.com/images/ 

```simple right? 
 
i get this when i load [http://myvhost.com/images/header.png](http://myvhost.com/images/header.png) in a browser 
                      ```
Internal Server Error 
 
The server encountered an internal error or misconfiguration and was  unable to complete your request. 
 
Please contact the server administrator, [no address given] and inform  them of the time the error occurred, and anything you might have done  that may have caused the error. 
 
More information about this error may be available in the server error  log. 
Apache Server at myvhost.com Port 80
```what am i doing wrong? 
 
tia

---

### Post by cdenley on 2009-10-05
First of all, it does not appear those directives are allowed in the htaccess context. The apache docs indicate it can only be used in "server config, virtual host, directory".
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxypass](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxypass)
I would try putting it back in your virtualhost config, make sure mod_proxy is enabled
```

sudo a2enmod proxy

```
reload apache
```

sudo /etc/init.d/apache2 reload

```
then if you still get a 500 error, post any details given in error.log
```

tail /var/log/apache2/error.log

```

---

