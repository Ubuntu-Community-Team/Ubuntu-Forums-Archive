---
title: "Ubuntu 10.04 Apache ByPass Proxy"
date: 2010-06-01
forum: Server Platforms
---

### Post by robertomason on 2010-06-01
I've read the documentation, but I'm still confused. I have two servers,  one running  Postfix and SquirrelMail, and another i want to setup a  wiki(already setup) and Photo Gallery.

On my Second server(2)I have two virutal webservers,  wiki.rmasonfamily.info and photo.rmasonfamily.info, both running on port  80.

My first computer is running my mail server again as a virtual server,  mail.rmasonfamily.info. Default server is not used in either one.



Server 1 will be my proxy server, and if I understand correctly, my  reverse proxy.

Apache is set with a configuration in etc/apache2 using  sites-available and sites-enabled.

My Virtual Servers in Server 2 are working fine, along with my mail  server in Server 1.

this is the code I assume I must use to pass to  wiki.rmasonfamily.info.

In server 1, under sites-available, in the file wiki.rmasonfamily.info  this is the code I put

<VirtualHost *:80>
ServerName wiki.rmasonfamily.info
ProxyRequests Off
ProxyPreserveHost On
RewriteEngine On
ProxyVia On
ProxyPass [http://wiki.rmasonfamily.info]("http://wiki.rmasonfamily.info/")
ProxyPassReverse [http://wiki.rmasonfamily.info]("http://wiki.rmasonfamily.info/")
</VirtualHost>

DNS:

192.168.1.9 SERVER 1
192.168.1.7 SERVER 2

Doesn't work, I know I'm doing something wrong... Thanks for whatever  help is available. Where do I place this code.

---

