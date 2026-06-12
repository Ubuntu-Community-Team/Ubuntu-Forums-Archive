---
title: "VirtualHost Problem - Should be an easy fix."
date: 2008-01-18
forum: Server Platforms
---

### Post by .Shaun on 2008-01-18
Ok, so I have setup my virtualhost in /etc/apache2/sites-available/mysite.com, i used a2ensite to enable it, and now no luck. When I run host mysite.com, for some reason it returns nothing found for "mysite.com.new.rr.com" new.rr.com is my ISP x_X. Any help?

~Shaun

---

### Post by Vinno on 2008-01-18
Post up your Virtualhost config.

---

### Post by .Shaun on 2008-01-19
My mysite.com config file, or httpd.conf?

---

### Post by Vinno on 2008-01-19
mysite.com

---

### Post by .Shaun on 2008-01-20
Here is /etc/apache2/sites-available/mysite.com:

```

<VirtualHost *>
ServerAdmin webmaster@localhost
ServerAlias www.mysite.com
DocumentRoot /var/www/
CustomLog /var/log/apache2/mysite.com-access.log combined
</VirtualHost>

```

---

### Post by MJN on 2008-01-21
Assuming mysite.com is not your real domain how do you expect us to help you given the likelihood that this might be a DNS issue? Please don't hide such information as we need to be able to rule out DNS as being the problem before moving on to other possible causes. At the very least do tell us when you've obfuscated the domain (and why) as what's obvious to you might not be for others trying to help you.
 
Incidentally, if you are using name-based virtual hosts then you really need a ServerName directive adding for this virtual site.
 
Mathew

---

