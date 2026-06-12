---
title: "Hardy + Apache2 + Hostnamelookups=Off  doesn't work"
date: 2009-02-14
forum: Server Platforms
---

### Post by ambrosa on 2009-02-14
I've searched a solution but I've found none.

I've setup a little pesonal webserver using LAMP Ubuntu Hardy Server.
Apache works fine but it still resolve hostname in /var/log/apache2/access.log
I don't want this: I want simple IP address logged in access.log
In /etc/apache2/apache2.conf I've set **HostnameLookups Off**
The same thing in /etc/apache/sites-available/default
I've checked that all ALLOW/DENY options in every modules and site configuration use IP numbers and not literal hostname.

Any idea ?

---

### Post by spiderbatdad on 2009-02-14
I would not edit apache2.conf specifically. Instead place config directives in httpd.conf

---

### Post by ambrosa on 2009-02-14
> **spiderbatdad said:**
> I would not edit apache2.conf specifically. Instead place config directives in httpd.conf

HostNameLookup is Off by default in apache2.conf so I've not changed apache2.conf

BTW the problem is: HOW DISABLE host name lookup in access.log ?
HostNameLookup Off doesn't work.

---

### Post by moronoid on 2009-05-08
> **ambrosa said:**
> HostNameLookup is Off by default in apache2.conf so I've not changed apache2.conf

BTW the problem is: HOW DISABLE host name lookup in access.log ?
HostNameLookup Off doesn't work.

Hi!
I have the same problem and it is very annoying. Have you found the solution you could share?

Thanks

---

### Post by moronoid on 2009-05-08
Wow!

I've figured out how to solve it in a minute after posting a message here.

Amazing forum :)

Thanks!

PS In case anyone else experiences the same behavior, just turn off mod_authz_host module in Apache config.

---

