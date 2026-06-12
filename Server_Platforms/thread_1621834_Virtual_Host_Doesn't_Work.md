---
title: "Virtual Host Doesn't Work"
date: 2010-11-14
forum: Server Platforms
---

### Post by trentscott on 2010-11-14
I created a new virtual host in Apache using Webmin and am having trouble getting it to work. When I created it, I opted to create the config file as a "New file under virtual servers directory /etc/apache2/sites-available". So now I have a default config file /etc/apache2/sites-available/default and a new one created by Webmin at /etc/apache2/sites-available/webmin.1412323.conf. It seems like the settings in that new Webmin config file aren't being picked up by Apache -- when I try and browse to mywebsite.com it shows my root /var/www folder, not the subdirectory /var/www/mywebsite.

Is there a way I can tell Apache to include the new Webmin config file for the virtual host or should I just copy the directives into the default file at /etc/apache2/sites-available/default? It seems like Webmin should automatically configure Apache to work with any newly generated config files, anyone have an idea as to why didn't that happen?

---

### Post by trentscott on 2010-11-14
Anyone?

---

### Post by Joeb454 on 2010-11-14
I think you might need to enable the site.

What is in /etc/apache2/sites-enabled ?

---

### Post by trentscott on 2010-11-14
Two lines:

```
000-default
webmin.1412323.conf
```

EDIT: I fixed it. Apparently the "Server Name" setting in Webmin should contain your FQDN (mywebsite.com), you should leave Address set to "Any". Oops... :D

---

### Post by James78 on 2010-11-14
You created a VirtualHost in Webmin? In most cases, you should be using Virtualmin for that..

---

