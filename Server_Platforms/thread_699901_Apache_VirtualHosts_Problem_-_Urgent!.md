---
title: "Apache VirtualHosts Problem - Urgent!"
date: 2008-02-17
forum: Server Platforms
---

### Post by .Shaun on 2008-02-17
Allright, so I created this file as /etc/apache2/sites-available/mysite.com:

```
<VirtualHost *>

    ServerName www.mysite.com
    DocumentRoot /var/www/sites/mysite.com
    ServerAdmin shaun@mysite.com
    ErrorLog /var/www/sites/mysite.com/logs/error-log
    CustomLog /var/www/sites/mysite.com/logs/access-log common

</VirtualHost>

```

i do a2ensite mysite.com, i restart apache, and it fails. I then disable it, and then i get a no pid error, i restart the machine, everything works fine. What do i do?

~Shaun

---

### Post by .Shaun on 2008-02-17
Bump

---

### Post by MJN on 2008-02-18
You need to elaborate on what you mean by 'it fails'. Post any errors, log entries etc.
 
Mathew

---

