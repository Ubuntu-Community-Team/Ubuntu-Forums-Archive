---
title: "Quick Apache2 VirtualHost question"
date: 2009-04-24
forum: Server Platforms
---

### Post by autogun on 2009-04-24
Howdy all,

I have a VirtualHosts configured in my httpd.conf file.
```
NameVirtualHost MY_IP_ADDRESS

<VirtualHost MY_IP_ADDRESS>
ServerName subdomain.domain.com
DocumentRoot /path/to/phpmyadmin
</VirtualHost>
```
So every time I browse to 'subdomain.domain.com' it points me to /path/to/phpmyadmin

How can I configure Apache so each time i come directly to MY_IP_ADDRESS it will point me to Apache's DefaultRoot and not to the VirtualHost?

---

### Post by mrsteveman1 on 2009-04-24
You need to have a default vhost setup to serve requests that aren't matched by another specific vhost. Apache comes with one by default, is it not still there? It should be in /etc/apache2/sites-available/default or something similar.

---

### Post by autogun on 2009-04-24
Found what I was looking for -

```
<VirtualHost _default_:80>
DocumentRoot "/usr/local/apache2/htdocs/"
...
</VirtualHost>

```

---

### Post by sahabcse on 2009-04-24
Hi

Pls do the folowing

vim /etc/apache2/sites-available/virtualdomain.com

NameVirtualHost xx.xx.xxx.xxx
<VirtualHost virtualdomain.com >
ServerAdmin [email]webmaster@virtualdomain.com[/email]
DocumentRoot /var/www/virtual/
ServerName virtualdomain.com
ServerAlias [www.virtualdomain.com](www.virtualdomain.com)
</VirtualHost>

ln -s /etc/apache2/sites-available/virtualdomain.com  /etc/apache2/sites-enabled

a2ensite virtualdomain.com

---

### Post by autogun on 2009-04-24
Thank you but I already found what I was looking for in post #3. =D

---

