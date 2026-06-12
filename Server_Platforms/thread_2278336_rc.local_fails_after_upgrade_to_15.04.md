---
title: "rc.local fails after upgrade to 15.04"
date: 2015-05-15
forum: Server Platforms
---

### Post by odror on 2015-05-15
OS: 15.04

LAN host (running in lxc) serviced by apache2 with  ip 192.168.0.7
LAN server (with access to WAN) server.com

on server.com in /etc/apache2/conf-enabled/test.conf

> [FONT=Courier New]<VirtualHost *:80>
        
       ServerName service.com
            DocumentRoot /test2
  
        ProxyRequests Off

        <Proxy *>
          Order deny,allow
          Allow from all
        </Proxy>

        ProxyPass / [http://192.168.0.7/dir](http://192.168.0.7/dir)
        ProxyPassReverse / [http://192.168.0.7/dir](http://192.168.0.7/dir)

        ErrorDocument 503 "The guest server is currently offline."
</VirtualHost>[/FONT]


if I am on the LAN I can access the web page at 192.168.0.7/dir

when I try to use the server: server.com/test2

I get The requested URL /test2 was not found on this server.

Idid install the proxy modules on the main and local servers.

and I did activate them

> a2enmod proxy proxy_http

Any help will be appreciated thanks

---

### Post by SeijiSensei on 2015-05-16
```
DocumentRoot /test2
```
First, that points to a directory off the root of the filesystem like /home or /usr.  Is that really where you have the website located?  The entry needs to be a complete file path at the operating system level like "DocumentRoot /var/www/html".

Also, if the DocumentRoot for service.com is /test2, then the URL [http://service.com/test2](http://service.com/test2), refers to the directory /test2/test2.

Finally, none of this has anything to do with rc.local.  I suggest renaming your thread to make it more obviously about Apache.

---

