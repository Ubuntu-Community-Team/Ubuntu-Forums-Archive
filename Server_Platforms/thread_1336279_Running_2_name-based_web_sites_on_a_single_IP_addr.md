---
title: "Running 2 name-based web sites on a single IP address"
date: 2009-11-24
forum: Server Platforms
---

### Post by dujlinvik on 2009-11-24
Hi All!

As I described in the title of this thread, I want to run 2 websites on my Virtual Private Server with a single IP address.

I'm not an Apache expert so I googled this issue and have read several tutorials and howto's, including Apache's

My configuration :
- Webmin 1.470
- Apache 2.2.8 on Ubuntu Server 8.04.2

What I've done so far :
- I set up the two nameservers ns1.myhostingcompany.com and ns2.myhostingcompany.com at my registrar
- I created a virtual server at Apache Webserver (Address : Any, Port : Any, Server name : mydomain.com, Document roort : /my_root_to_the_HTML_files ) and edited Global configuration for Apache :

```

<Directory "/my_root_to_the_HTML_files">
    Options FollowSymLinks
    AllowOverride All
</Directory>

```
Restarted Apache and I knew it won't work... Maybe that was my main mistake....

Anyway, I would appreciate if someone could help me out, before I decide to hire an Apache Server administrator to do this 10 mins job (just an assume....)

Thank you advanced.
Best wishes!

---

### Post by volkswagner on 2009-11-24
Go to the third sticky thread at the top of this forum (server forum).  From that link select 8.04 server, then scroll down to "httpd Apache2 server".  From there you find help with virtual hosts.

Basically you need to edit /etc/apache2/httpd.conf and add the NamedVirtualHosts directive.  You can then add your individual virtual host config files as described in the above mentioned docs.

---

### Post by Iowan on 2009-11-24
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is one How-To I have stashed away.

---

