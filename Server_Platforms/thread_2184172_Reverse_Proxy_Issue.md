---
title: "Reverse Proxy Issue"
date: 2013-10-27
forum: Server Platforms
---

### Post by nownto on 2013-10-27
I have a server, 192.68.1.7 that host several vms

gitlab 192.168.1.12
random web servers 192.168.1.13-15

I also created a ubuntu server install with apache2 that I want to use as a reverse proxy

apache reverse proxy 192.168.1.4

when I go to my domain testDomain3.com I see the /var/www/index.html from 192.168.1.4, which is good, that means the :80 request are hitting the correct server. What I tried next is to setup a reverse proxy on 192.168.1.4, followed guide [http://ubuntuguide.org/wiki/Apache2_reverse_proxies](http://ubuntuguide.org/wiki/Apache2_reverse_proxies)

I created a file called proxiedhosts in sites-available and soft link to sites-eneabled
contents of proxiedhosts:

[http://pastie.org/8436064](http://pastie.org/8436064)

and enable the modules

this issue is when I go to gitlab.testDomain3.com I get the http page for 192.168.1.4, which isn't correct, it should be pointing to the http page for 192.168.1.12.

output of apachectl -S
/usr/sbin/apachectl: 87: ulimit: error setting limit (Operation not permitted)
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         default server [www.testDomain3.com](www.testDomain3.com) (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost [www.testDomain3.com](www.testDomain3.com) (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost gitlab.testDomain3.com (/etc/apache2/sites-enabled/proxiedhosts:1)
Syntax OK
frosty@http

---

