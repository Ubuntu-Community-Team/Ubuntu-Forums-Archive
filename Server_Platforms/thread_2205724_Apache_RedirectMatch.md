---
title: "Apache RedirectMatch"
date: 2014-02-15
forum: Server Platforms
---

### Post by sam31 on 2014-02-15
Hi! Below is the basic configuration of my apache server. All pages are served through *index.php *and I need to redirect pages under *secure* directory to HTTPS and otherwise use HTTP only. With the RedirectMatch expression shown below I'm able to be redirected to HTTPS but after that every page is served under HTTPS. And of course I'm able to get back to HTTP with similar expression to one page but what would be the right expression to get back to HTTP always unless we're under the *secure *directory thus avoiding to write own expression for all the other pages? Or what would be a good way to manage this?

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        RedirectMatch ^/public/index\.php/secure/(.*)$ https://localhost/public/index\.php/secure/$1
</VirtualHost>       

<IfModule mod_ssl.c>
<VirtualHost _default_:443>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        RedirectMatch <What wiould be the right expression?>
</VirtualHost>
<IfModule>

```

Thanks in advance. Best regards, Sam.

---

