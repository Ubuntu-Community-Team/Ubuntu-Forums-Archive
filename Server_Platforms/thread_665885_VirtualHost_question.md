---
title: "VirtualHost question"
date: 2008-01-12
forum: Server Platforms
---

### Post by godsfshrmn on 2008-01-12
I'm running webmin / ispconfig on my ubuntu server. This is a pretty simple question. When I wanted to add a domain before, I'd do it through ispconfig.
How can I add a website that can be available through a specific port? i.e xx.xx.xx.xx:555 from an outside site and internally on the same network? I tried to add a new virtual server with the desired port through webmin but when I try to visit it, firefox tells me the connection was reset. I wish i could just get rid of the "shared ip page" added by ispconfig that appears when I go to the IP of the server on the LAN and be able to see each site's folder.

---

### Post by HermanAB on 2008-01-12
Edit httpd.conf directly with vi, joe, nano or gedit.  In the virtualhost stanza, put the ipaddress:portnumber. Then restart Apache to make the change take effect.  Finally, open the port in your firewall.  

Test TCP connections with telnet:
$ telnet servernameoripaddress portnumber

The server should respond.  If not, then you done sumpin wrong - check the Apache logs to figure out what.

Cheers,

Herman

---

