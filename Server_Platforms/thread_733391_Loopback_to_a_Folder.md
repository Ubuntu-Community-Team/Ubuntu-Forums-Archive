---
title: "Loopback to a Folder"
date: 2008-03-23
forum: Server Platforms
---

### Post by lightnb on 2008-03-23
I have Apache running on my computer.

When I visit "http://localhost", I see the contents of "/var/www", as expected.

I have a sub folder for a site: "/var/www/mysite"

I would like "http://www.mysite.com" to loopback to the folder "/var/www/mysite".

How can I do that?

---

### Post by lightnb on 2008-03-25
bump

---

### Post by Mr. C. on 2008-03-25
The term "loopback" is incorrect here.  You want a virtual host, for example:

<VirtualHost *:80>
    ServerAdmin [email]webmaster@mysite.com[/email]
    DocumentRoot "/var/www/mysite"
    ServerName [www.mysite.com](www.mysite.com)
</VirtualHost>

Place this in the appropriate apache httpd.conf file for your setup, and restart apache.

Setup your /etc/hosts or internal DNS server to resolve [www.mysite.com](www.mysite.com) to the server's LAN IP, and externally a public IP if you want it reachable externally.

---

