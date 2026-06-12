---
title: "mono on apache"
date: 2008-06-25
forum: Server Platforms
---

### Post by wenek18 on 2008-06-25
Hi all 
I installed mono on apache however I am having problems as am getting the following when I restart apache

apache2: Syntax error on line 186 of /etc/apache2/apache2.conf: Syntax error on line 3 of /etc/apache2/mods-enabled/mod_mono.conf: Could not open configuration file /usr/local/lib/mono/2.0/mono-server2-hosts.conf: No such file or directory
...fail!

I used the following guide

[http://timanisblog.com/2007/07/22/in...ons-in-ubuntu/](http://timanisblog.com/2007/07/22/in...ons-in-ubuntu/)

Please help as I am getting crazy

Awaiting your replies

Thanks - Justin

---

### Post by windependence on 2008-06-25
Does /usr/local/lib/mono/2.0/mono-server2-hosts.conf actually exist? It's looking for the conf file and cannot find it. is it actually there and if not maybe it's in a different location?

-Tim

---

### Post by wenek18 on 2008-06-25
Hi Thanks for your replies, ok managed to load apache however now i have when accesing asp folder from browser:

Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.
Apache/2.2.8 (Ubuntu) mod_mono/1.2.5 Server at localhost Port 80

---

