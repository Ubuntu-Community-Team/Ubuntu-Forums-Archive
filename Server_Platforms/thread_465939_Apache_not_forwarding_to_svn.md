---
title: "Apache not forwarding to svn"
date: 2007-06-06
forum: Server Platforms
---

### Post by ishaqmalik on 2007-06-06
Hi,

     I am running a dedicated server for svn on my LAN, this server runs apache2, and my main server (web server) is used to proxy requests to subversion. Here's a portion of my httpd.conf to give you a better idea

```
NameVirtualHost *:80
<VirtualHost *:80>
  ServerName mainserver.mycompany.com
  DocumentRoot /var/www/html

  ProxyPass /tomcat http://127.0.0.1:8080/
  ProxyPassReverse /tomcat http://127.0.0.1:8080/

  ProxyPass /svn http://subversion/svn/
  ProxyPassReverse /svn http://subversion/svn/

  ProxyPreserveHost off
</VirtualHost>

<VirtualHost _default_:443>
  ProxyPass /svn https://subversion/svn
  ProxyPassReverse /svn https://subversion/svn
  SSLProxyEngine On
</VirtualHost>
```

All other proxy requests working fine except svn, i.e. if I use [http://mainserver.mycompany.com/tomcat](http://mainserver.mycompany.com/tomcat), it works fine, however, when I access, for example, [http://mainserver.mycompany.com/svn](http://mainserver.mycompany.com/svn), It keeps asking my for username/password again and again although I enter the correct right the first time...

Any idea why the main apache server is not passing logon credentials to the svn server?

Regards,
MI

---

