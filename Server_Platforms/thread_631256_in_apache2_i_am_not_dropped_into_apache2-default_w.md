---
title: "in apache2 i am not dropped into apache2-default/ when visiting hosted domain"
date: 2007-12-04
forum: Server Platforms
---

### Post by kraymore on 2007-12-04
when i visit my self hosted domain i am undesireably dropped to

Index of /
[ICO] Name Last modified Size Description
[DIR] apache2-default/ 20-Nov-2004 14:16

instead of inside my apache2-default/ directory.  

-
this is my sites-enabled file

# NameVirtualHost *
<VirtualHost *>
ServerAdmin [email]admin@mydomain.com[/email]
ServerName [www.mydomain.com:80](www.mydomain.com:80)
DocumentRoot /var/www/
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
# RedirectMatch ^/$ /apache2-default/
</Directory>


however i am using apache2 and in my /etc/apache2/sites-available/domain file
which has been activated by sudo a2ensite domain when i edit the */sites-enabled/mydomain file
i have checked and unchecked RedirectMismatch yielding the same results. i've also restarted the apache2 webserver as well inbetween checking as well as clearing the cache.

---

