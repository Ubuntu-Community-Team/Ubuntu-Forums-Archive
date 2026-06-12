---
title: "proxypass problem with apache2"
date: 2007-05-25
forum: Server Platforms
---

### Post by huggy77 on 2007-05-25
I am getting the following error when i reboot my apache2 server.
```

 * Forcing reload of web server (apache2)... 
[Fri May 25 22:16:19 2007] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri May 25 22:16:29 2007] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

```

the virtual host that is causing the error is:
```
<VirtualHost *:80>
    ServerName [www.happyinfidel.com](www.happyinfidel.com)
    ProxyPass /weblog [http://www.happyinfidel.com:8080/weblog](http://www.happyinfidel.com:8080/weblog)
    ProxyPassReverse /weblog [http://www.happyinfidel.com:8080/weblog](http://www.happyinfidel.com:8080/weblog)
    DocumentRoot /var/www
</VirtualHost>
```

i think the first line of the virtual host is causing the problem but i dont know what to put in there...  This is the only configuration of the file that was working...

i am trying to get glassfish to server pebble via apache.   Any ideas on how to get rid of this error...  I need to be abe to call the webroot as well as pebble

---

### Post by huggy77 on 2007-05-25
thanks in advance...

---

### Post by huggy77 on 2007-05-29
i am still having that issue - has anyone seen anything similar

---

