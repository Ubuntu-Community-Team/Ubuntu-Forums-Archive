---
title: "Can you only let certain ip addresses to a certain site?"
date: 2008-11-03
forum: Server Platforms
---

### Post by linuxisevolution on 2008-11-03
For instance, If I wanted to only allow the ip 192.168.1.144 to [www.example.com/restricted](www.example.com/restricted).

How would I go about doing this? I'm using apache2. My site is [http://www.winrid.co.nr]("http://www.winrid.co.nr"). My other site, which I'm working on, is [http://www.thelinuxhowto.co.nr]("http://www.thelinuxhowto.co.nr")

Thanks for your time.

---

### Post by cmatheson on 2008-11-04
This is possible by adding a directive like this to your VirtualHost config:

<Location /restricted>
Order Allow,Deny
Allow from 192.168.1.144
Deny from all
</Location>

For more information, see:

[http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html)

---

