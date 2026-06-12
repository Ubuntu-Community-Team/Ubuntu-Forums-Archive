---
title: "apache2 proxypass to router"
date: 2009-12-07
forum: Server Platforms
---

### Post by electronico_nc on 2009-12-07
Hi all,

I have a server running Jaunty (local IP : 10.0.8.200) and located in DMZ behind a Linksys WAG-200 router (local IP : 10.0.8.1)
I would like to access to the router setup. As it is a server, I don't have GUI ...
I have so enabled mod-proxy in Apache2 and written a VirtualHost like this :```
NameVirtualHost 10.0.8.200:80
<VirtualHost 10.0.8.200:80>
    ServerName my.fdqn.ext
    ProxyPass /router http://10.0.8.1:80
    ProxyPassReverse /router http://10.0.8.1:80/
    ProxyPreserveHost on

    #Fix for Apache bug 39499
    SetEnv force-proxy-request-1.0 1
    SetEnv proxy-nokeepalive 1

        <proxy http://10.0.8.1>
                Order Deny,Allow
                Deny from All
                Allow From  10.0.8. xxx.xxx.xxx.xxx
        </proxy>

        ErrorLog /var/log/apache2/error.log
        LogLevel warn
        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

```xxx.xxx.xxx.xxx stands for my remote public IP
When a type in a broswer : ```
http://my.fdqn.ext/router
```I'm well invited to enter router login/pass, then Broswer tries to go to : ```
http://my.fdqn.ext/setup.cgi?next_file=Setup.htm
```and it displays this error```
**Not Found**

 The requested URL /setup.cgi was not found on this server.
```
 Apache2 log file then shows :```
[Tue Dec 08 13:39:08 2009] [error] [client xxx.xxx.xxx.xxx] File does not exist: /htdocs, referer: http://my.fdqn.ext/router

```I haven't been able to fix this ...
Thanks in advance for your time and tracks !

---

### Post by cariboo on 2009-12-07
Can you acces the router directly, try:

```
http://10.0.8.1
```

---

### Post by electronico_nc on 2009-12-07
Hi, thanks for your answer.

For sure I can access to the router from the LAN : I SSH to the server, then```
lynx 10.0.8.1
``` I can login without error with login/pass, but this router requires Javascript (not supported by Lynx) so I can't see the configuration pages.


The mod-proxy works as I'm well directed to the router 80 port, but something should be missing in the VirtualHost config as I get the error reported above ...

---

### Post by Dratir on 2009-12-17
> **electronico_nc said:**
> ```
    ProxyPass /router http://10.0.8.1:80
    ProxyPassReverse /router http://10.0.8.1:80/
```

Hey electronico_nc!
Try adding a slash, like this:

```
    ProxyPass /router/ http://10.0.8.1:80
    ProxyPassReverse /router/ http://10.0.8.1:80/
```

Not quite sure but probably it helps :confused:

---

### Post by electronico_nc on 2009-12-17
Hello Dratir,
Thanks a lot for pointing this out !
The correct syntax that works is :```
        ProxyPass /router/ http://10.0.8.1:80/
        ProxyPassReverse /router/ http://10.0.8.1:80/

```(I had to add another / at the first line end)
Thanks once more !

---

