---
title: "Calibre using Reverse Proxy"
date: 2016-05-10
forum: Server Platforms
---

### Post by dom134 on 2016-05-10
Hello all

I have recently installed Owncloud on a mini-server running Ubuntu 16.04.  This is working nicely so the next project is to install a calibre server.  I have managed to use a reverse proxy to Calibre whilst on the LAN using http, but when I try to access over the internet I have a few issues.  I am only allowing ssl through my router.

My starting point is this useful post:[URL="http://ubuntuforums.org/showthread.php?t=2319088"]
Reverse Proxy Clarification[/URL]

My 000-default.conf file looks like this:
> <VirtualHost *:443>
        ServerName [www.dom134.com](www.dom134.com)
        ServerAdmin webmaster@localhost
        ServerAlias [www.dom134.com](www.dom134.com)
        DocumentRoot /var/www/html
        SSLEngine On
        SSLCertificateFile /etc/ssl/certs/www_dom134_com.crt
        SSLCertificateKeyFile /etc/ssl/certs/server.key
        SSLCACertificateFile /etc/ssl/certs/www_dom134_com.ca-bundle
        ProxyPass /calibre [http://192.168.1.19:8080](http://192.168.1.19:8080)
        ProxyPassReverse /calibre [http://192.168.1.19:8080](http://192.168.1.19:8080)
</VirtualHost>

This works adequately for the home page, but as soon as I browse to .../calibre/browse or .../calibre/some_other_place , the reverse proxy has issues and I will get a 404 Not Found error.  Also the graphics on the home page do not show up correctly.  Does anyone have any suggestions?

---

### Post by dom134 on 2016-05-30
I managed to get help from mobileread and this is now solved.
[http://www.mobileread.com/forums/showthread.php?t=274589](http://www.mobileread.com/forums/showthread.php?t=274589)

---

