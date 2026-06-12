---
title: "VirtualHost Problem"
date: 2008-01-08
forum: Server Platforms
---

### Post by .Shaun on 2008-01-08
I have a couple VirtualHost questions about Apache2. I am planning on using multiple domains on the same IP, so I understand I have to use

NameVirtualHost *:80

But everytime I try and use that it comes up with something along the lines of: No virtualhosts for *:80.

My second question. Whenever I go to one of the virtualhost domains that I am hosting, the site works with [www.example.com](www.example.com), but never example.com. Why is this? 

Any at all help is appreciated.

Thanks,
~Shaun

---

### Post by ecrissman on 2008-01-08
Try NameVirtualHost *

Have you supplied a ServerAlias in your virtual host config? 
It should look like this-
```
<VirtualHost *>
ServerName example.com
ServerAlias *.example.com (or www.example.com)
ServerAdmin user@example.com

etc. etc.

</VirtualHost>

```

---

### Post by .Shaun on 2008-01-08
Hi, thanks much for the reply. I was a little confused about where to put NameVirtualHost too. And yes, this is /etc/apache2/sites-enabled/example.com

```

<VirtualHost *:80>
ServerName www.example.info
ServerAlias example.info
DocumentRoot /var/www/virtual/example.info/htdocs
ServerAdmin webmaster@example.info
ErrorLog /var/www/virtual/example.info/logs
CustomLog /var/log/apache2/www.example.com-access_log common
</VirtualHost>

```

of course with example.info being my domain name.

Thanks,
~Shaun

---

### Post by .Shaun on 2008-01-08
Bump.

---

### Post by .Shaun on 2008-01-09
Bump

---

