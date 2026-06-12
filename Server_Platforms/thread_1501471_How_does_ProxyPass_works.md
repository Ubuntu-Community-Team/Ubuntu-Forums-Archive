---
title: "How does ProxyPass works"
date: 2010-06-04
forum: Server Platforms
---

### Post by tapas_mishra on 2010-06-04
want to know how does directive
ProxyPass
and ProxyPassReverse work
if I have an application on an internal webserver running on port 8080 on Lan
but I want it to be accessible on internet via Server A which has public IP
but firewall (which I do not have control blocks all except port 80)
```

 External           Server A -----------------------------------------Server B
Firewall by          Public IP                                         LAN
sysadmins 
(Port 8080 blocked)

```
if I write
```

ProxyPass     /application   http://192.168.1.5:8080
ProxyPassReverse  /application http://192.168.1.5:8080

```
1) Will the application be accessible outside.
Or do I need to contact sysadmin to open 8080 for outside world in A in above diagram.
Also does apache needs to listen at 8080 in above diagram at server A.
Is there any other way to do the same in apache2.

---

### Post by richardjh on 2010-06-05
* The application will be available to the outside world, so **make sure it is secured** as it previously wasn't exposed to the internet.

*You wont need to change any firewall settings.

*You will access [http://external_url/application](http://external_url/application) on port 80, the proxy will connect to serverB on port 8080 but that is not relevant as it will serve the pages back to the client on port 80.

* Apache won't need to listen on port 8080 on serverA 

*You can do this in apache2, here is an example for what you need.

```
<VirtualHost>
...

    ProxyRequests On
    ProxyPreserveHost On
    ProxyVia Full

    ProxyPass               /application    http://serverB:8080/application
    ProxyPassReverse /application    http://serverB:8080/application

...
</VirtualHost>
```

---

### Post by tapas_mishra on 2010-06-07
Thanks for this information.

---

