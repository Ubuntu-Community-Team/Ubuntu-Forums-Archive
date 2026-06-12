---
title: "[Question] Ubuntu apache reverse proxy to jboss"
date: 2013-12-04
forum: Server Platforms
---

### Post by adrianus2 on 2013-12-04
Hello,


I hope that someone here can assist me with this problem because I am currently trying fix it for 2 weeks now and can’t seem to get it working. Well let’s start with explaining my situation.


Environment(home server/learning):
```
-    1 Public IP
-    Host Windows Server 2008 R2 AD/DNS/Hyper-V (server0)
o    VM Windows Server 2008 R2 Exchange 2010/IIS (server1)
o    VM Ubuntu server 13.11 Apache 2.4.6 with virtual hosts (server2)
o    VM Windows Server 2008 R2 Blackberry Enterprise Server running on a Jboss webserver (server3)
-    All port 80,443 requests points  Ubuntu  server 13.11 (server2)

```

Within Apache 2.4.6  I have virtualhost where  the setup are as followed 
```
-    SomeWebsite:80
-    SomeOtherWebsite:80
-    Mail.server1.com:443 (internet <---> server2 reverse proxy:443 +CERT <--->  443+CERT server1)
-    Bes.dnsname.com:443 (internet <---> server2 reverse proxy:443 +CERT <--->  443+CERT server3)

```

The problem:
For learning purpose I am configuring a blackberry enterprise server(bes)  on server3. It’s a clean installation with only the needed applications to run a bes. Because I only have 1 public ip I am trying to reverse proxy this webservice two like server1. The bes webservice is  configured to accept connections on port 443. So my first web.conf setup was similar to the setup I used for server1 but I noticed that the webpage was displayed  but I couldn’t interact with the page because it was a java application. So digging deeper into this i found that the webpage that bes provided me to use isn’t the real application but more like a iframe setup. 


```
Example:
BES Console address: https://server3.com/webconsole/login
Real address: https://server3.com/websconsole/app 

```

 Unfortunately after finding this and editing my web.conf to proxypass –reverse to this real address I encountered a other problem. The bes webconsole works with session id’s and parameters 


```
Example:
https://bes.server3.com/webconsole/app;jsessionid=2C10DDA521DB8408479AAD8F34255C7F?component=login.goToChangeLanguagePageLink&consoleSId=&page=Login&service=direct&session=T

```

Current used web.conf for  server3:
```
<VirtualHost *:80>
DocumentRoot /var/www/bes.server3.com
ServerName bes.server3.com
<Directory "/var/www/bes.server3.com">
allow from all
Options +Indexes
</Directory>


RewriteEngine On
RewriteCond %{HTTPS} !=on
RewriteRule ^/?(.*) https://bes.server3.com/webconsole/login$1 [R,L]


ProxyPreserveHost On
ProxyVia Full
RequestHeader edit Transfer-Encoding Chunked chunked early
RequestHeader unset Accept-Encoding
ProxyRequests Off
TimeOut 1800


SSLEngine On
SSLProxyEngine On
SSLProtocol -all +SSLv3 +TLSv1
SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL:+SSLv3
SSLCertificateFile /var/www/bes.server3.com/cert/server.crt
SSLCertificateKeyFile /var/www/bes.server3.com/cert/server.key


<Location /webconsole/login>
ProxyPass https://bes.server3.com/webconsole/app
ProxyPassReverse https://bes.server3.com/webconsole/app
ProxyPassReverseCookiePath /webconsole/app /webconsole/login
SSLRequireSSL
</Location>


<Location /webconsole/assets>
ProxyPass https://bes.server3.com/webconsole/assets
ProxyPassReverse https://bes.server3.com/webconsole/assets
SSLRequireSSL
</Location>


<Location /webconsole/com>
ProxyPass https://bes.server3.com/webconsole/com
ProxyPassReverse https://bes.server3.com/webconsole/com
SSLRequireSSL
</Location>


<Location /webconsole/Loader>
ProxyPass https://bes.server3.com/webconsole/Loader
ProxyPassReverse https://bes.server3.com/webconsole/Loader
SSLRequireSSL
</Location>


<Location /webconsole/META-INF>
ProxyPass https://bes.server3.com/webconsole/META-INF
ProxyPassReverse https://bes.server3.com/webconsole/META-INF
SSLRequireSSL
</Location>




<Location /webconsole/reset>
ProxyPass https://bes.server3.com/webconsole/reset
ProxyPassReverse https://bes.server3.com/webconsole/reset
SSLRequireSSL
</Location>


<Location /webconsole/WEB-INF>
ProxyPass https://bes.server3.com/webconsole/WEB-INF
ProxyPassReverse https://bes.server3.com/webconsole/WEB-INF
SSLRequireSSL
</Location>


ErrorLog /var/log/apache2/bes_server3_errorlog
CustomLog /var/log/apache2/bes_server3_com common
</VirtualHost>

```

as I mentioned before the server I am working on is my own private server used for learning purpose, and if I must rate myself I would say I am a little bit above beginner with Ubuntu servers and apache. I looked all over the internet to find the solution  for this but every example  did not work for me. I hope with posting my own situation I have more chance to find the answer that will work for me.

---

