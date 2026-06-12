---
title: "mod_rewrite how to change ip to html?"
date: 2013-07-07
forum: Server Platforms
---

### Post by rado3105 on 2013-07-07
Hi, In apache I try to change when i put ip adress: 192.168.1.1 in web browser to show me instead ip in webbroser some name of page: e.g: mysite.com

I have installed and enabled mod_rewrite.
I put this in 000-default:
> <VirtualHost  *>
RewriteEngine on
RewriteCond %{HTTP_HOST} ^192\.168\.1\.1
RewriteRule (.*) mysite.com/$1 [R=301,L]
         DocumentRoot /var/www/forum
        <Directory /var/www/forum>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

but this doesnt work....

---

