---
title: "new domain same box htaccess?"
date: 2011-08-24
forum: Server Platforms
---

### Post by SlugSlug on 2011-08-24
Hi All

I am changing domain name for web, web is staying on same IP / Server

I want [www.OLD.com]("http://www.OLD.com")  to redirect (change address name in browser) to [www.NEW.com]("http://www.NEW.com")

at the moment both point to same IP..

am not sure why but this .htaccess is not working.

```
#Options +FollowSymLinks
RewriteEngine on
RewriteCond %{HTTP_HOST} ^www.OLD.co.cc$[OR]
RewriteCond %{HTTP_HOST} ^OLD.co.cc$
RewriteRule ^(.*)$ http://www.NEW.com/$1 [R=301,L]
```

I've chmod'd .htaccess 777 for time been (whats correct permisions?)

I also have this in sites-available + site-enabled    default

```

ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

```

---

### Post by SlugSlug on 2011-08-24
ok solved with 

Options +FollowSymLinks
RewriteEngine on
RewriteCond %{HTTP_HOST} ^(.*)OLD.co.cc [NC]
RewriteRule ^(.*)$ http://NEW.com/$1 [R=301,L]

---

