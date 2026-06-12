---
title: "Apache Reverse Proxy not grabbing JSON endpoint"
date: 2013-12-17
forum: Server Platforms
---

### Post by vsiege2 on 2013-12-17
[COLOR=#000000][FONT=Arial]I have setup Apache server on a local server with an IP address of 192.168.16.190. My intention is to use this server to as a proxy API service. To test, I have setup 2 virtual hosts. The first simple virtual host returns the desired webpage (cnn.com) to the requesting client while the second virtual host setup ([http://date.jsontest.com/](http://date.jsontest.com/)) does not return the JSON data back, but instead returns a google web page stating that this address "/" does not exist. Below is my setup. Do I have to adjust my configuration/s (/etc/apache2/httpd.con/ or /etc/apache2/extra/httpd-vhosts.conf)to accomedate for the JSON data.[/FONT][/COLOR]
```
[COLOR=#800000]<VirtualHost[/COLOR] 192.168.16.190:8000[COLOR=#800000]>[/COLOR]
        ProxyRequests Off
        ProxyPreserveHost On
        ServerName service.api
        ServerAlias *.service.api
        ProxyPass / http://cnn.com/
        ProxyPassReverse / http://cnn.com/

        #ErrororLog "/private/var/log/apache2/dummy-host2.example.com-error_log"
        #CustomLog "/private/var/log/apache2/dummy-host2.example.com-access_log" common

        LogLevel debug
        [COLOR=#800000]<Proxy[/COLOR] [COLOR=#0000FF]"http://192.168.16.190:8000/"[/COLOR][COLOR=#800000]>[/COLOR]
                Order Deny,Allow
                Allow from all
        [COLOR=#800000]</Proxy>[/COLOR]
[COLOR=#800000]</VirtualHost>[/COLOR]
[COLOR=#800000]<VirtualHost[/COLOR] 192.168.16.190:8001[COLOR=#800000]>[/COLOR]
        ProxyRequests Off
        ProxyPreserveHost On
        ServerName service1.api
        ServerAlias *.service1.api
        ProxyPass / http://date.jsontest.com/
        ProxyPassReverse / http://date.jsontest.com/

        #ErrororLog "/private/var/log/apache2/dummy-host2.example.com-error_log"
        #CustomLog "/private/var/log/apache2/dummy-host2.example.com-access_log" common

        LogLevel debug
        [COLOR=#800000]<Proxy[/COLOR] [COLOR=#0000FF]"http://192.168.16.190:8001/"[/COLOR][COLOR=#800000]>[/COLOR]
                Order Deny,Allow
                Allow from all
        [COLOR=#800000]</Proxy>[/COLOR]
```

---

### Post by volkswagner on 2013-12-20
Do you have a dns entry for service1.api?

You are pointing to public domains, why are you using port other than :80?

Are you typing [http://service1.api:8001](http://service1.api:8001) in your browser?

When you type [http://service.api:8000](http://service.api:8000) you get directed to cnn.com?

---

