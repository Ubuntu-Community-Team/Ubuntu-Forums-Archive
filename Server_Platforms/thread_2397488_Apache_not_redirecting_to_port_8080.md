---
title: "Apache not redirecting to port 8080"
date: 2018-07-30
forum: Server Platforms
---

### Post by olivr3 on 2018-07-30
How can we redirect to port 8080 using reverse proxy servers?
The app is accessible on port 8080 but does not default to port 80 for some reason.


I came up with the following config.

```

000-default.config

----------------------------------------------------------------------------------------------------------------------

LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule proxy_wstunnel_module /usr/lib/apache2/modules/mod_proxy_wstunnel.so
<VirtualHost *:80>
    ProxyPreserveHost On
    ProxyRequests Off

    ServerName ofornecedor.com.br
    ServerAlias [http://ofornecedor.com.br](http://ofornecedor.com.br)

    ProxyPass /admin/event ws://localhost:8080/admin/event
    ProxyPassReverse /admin/event ws://localhost:8080/admin/event

    ProxyPass / [http://localhost:8080/](http://localhost:8080/)
    ProxyPassReverse / [http://localhost:8080/](http://localhost:8080/)
</VirtualHost>

----------------------------------------------------------------------------------------------------------------------

  /apache2 -k start
           &#9500;&#9472;14831 /usr/sbin/apache2 -k start apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2; bad; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: active (running) since Mon 2018-07-30 11:46:14 UTC; 8s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 14742 ExecStop=/etc/init.d/apache2 stop (code=exited, status=0/SUCCESS)
  Process: 11742 ExecReload=/etc/init.d/apache2 reload (code=exited, status=0/SUCCESS)
  Process: 14811 ExecStart=/etc/init.d/apache2 start (code=exited, status=0/SUCCESS)
    Tasks: 55
   Memory: 6.5M
      CPU: 61ms
   CGroup: /system.slice/apache2.service
           &#9500;&#9472;14828 /usr/sbin
           &#9492;&#9472;14832 /usr/sbin/apache2 -k start

Jul 30 11:46:13 ip-172-31-13-126 systemd[1]: Starting LSB: Apache2 web server...
Jul 30 11:46:13 ip-172-31-13-126 apache2[14811]:  * Starting Apache httpd web server apache2
Jul 30 11:46:13 ip-172-31-13-126 apache2[14811]: [Mon Jul 30 11:46:13.480124 2018] [so:warn] [pid 14827:tid 139956103014272] AH01574: module proxy_module is already loaded, skipping
Jul 30 11:46:13 ip-172-31-13-126 apache2[14811]: [Mon Jul 30 11:46:13.480178 2018] [so:warn] [pid 14827:tid 139956103014272] AH01574: module proxy_http_module is already loaded, skipping
Jul 30 11:46:14 ip-172-31-13-126 apache2[14811]:  *
Jul 30 11:46:14 ip-172-31-13-126 systemd[1]: Started LSB: Apache2 web server.
```

----------------------------------------------------------------------------------------------------------------------
And yes, I have restarted the apache2 after all these changes. [IMG]https://discourse.ubuntu.com/images/emoji/emoji_one/smile.png?v=5[/IMG]


Do you see anything wrong here? It is not redirecting to port 8080.


Thx in advance.

---

