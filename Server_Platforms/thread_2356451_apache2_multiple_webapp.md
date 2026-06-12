---
title: "apache2 multiple webapp"
date: 2017-03-23
forum: Server Platforms
---

### Post by giane on 2017-03-23
Hi all
I have a problem during configuration of my apache2 service.
I have 3 java webapp hosted on 3 different tomcat and they answer on 3 different ports.
app1 [http://localhost:8091]("http://localhost:8091/")
app2 [http://localhost:8092]("http://localhost:8092/")
app3 [http://localhost:8093]("http://localhost:8093/")
In my first configuration all the 3 apps answer using NamedVirtualHost and they could be reached using dns.
[http://www.app1.com]("http://www.app1.com/")
[http://www.app2.com]("http://www.app2.com/")
[http://www.app3.com]("http://www.app3.com/")
Now I insert the configuration for use https, now all the 3 following url answer me:
[https://www.app1.com]("https://www.app1.com/")
[https://www.app2.com]("https://www.app2.com/")
[https://www.app3.com]("https://www.app3.com/")
But the problem is that using one of the previous url I am redirected to the app1, the default Virtual host.
My site enabled configuration is:
```
<VirtualHost *:80>
     ServerName app1.com
     Redirect / https://www.app1.com/
</VirtualHost>


<VirtualHost *:443>
      ServerName app1.com
      ProxyPreserveHost On
      ProxyPass / http://localhost:8091/
      ProxyPassReverse / http://localhost:8091/
      SSLEngine on
      SSLCertificateFile "/data/apps/certificati/cert2017.cer"
      SSLCertificateKeyFile "/data/apps/certificati/cert2017.key"
</VirtualHost>

<VirtualHost *:80>
     ServerName app3.com
     Redirect / https://www.app3.com/
</VirtualHost>

<VirtualHost *:433>
      ServerName app3.com
      ProxyPreserveHost On
      ProxyPass / http://localhost:8093/
      ProxyPassReverse / http://localhost:8093/
      SSLEngine on
      SSLCertificateFile "/data/apps/certificati/cert2017.cer"
      SSLCertificateKeyFile "/data/apps/certificati/cert2017.key"
</VirtualHost>

<VirtualHost *:80>
     ServerName app3.com
     Redirect / https://www.app3.com/
</VirtualHost>

<VirtualHost *:433>
      ServerName app3.com
      ProxyPreserveHost On
      ProxyPass / http://localhost:8092/
      ProxyPassReverse / http://localhost:8092/
      SSLEngine on
      SSLCertificateFile "/data/apps/certificati/cert2017.cer"
      SSLCertificateKeyFile "/data/apps/certificati/cert2017.key"
</VirtualHost>

```
Someone can help me.
TY

---

### Post by giane on 2017-03-23
Wrong configuration for app2 and app3 the port of virtual host are set to 433 instead of 443:lolflag:

---

