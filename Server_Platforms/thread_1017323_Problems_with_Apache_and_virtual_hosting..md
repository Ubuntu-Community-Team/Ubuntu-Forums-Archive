---
title: "Problems with Apache and virtual hosting."
date: 2008-12-20
forum: Server Platforms
---

### Post by version7x on 2008-12-20
I'm doing some testing with a new apache install and cant get the desired results.

I've got my etc hosts file to show both example1.com and example2.com for the same address.

In my httpd.conf, i have set the server name as example1.com and have an entry for example2 as a virtualhost.

The problem is that I'm getting the virtual hosts index.html for both sites.  If I remove the index.html from the virtualhost directory, i get a message that there is no index.html for either site.

I've posted the relevant lines form httpd.conf below.... what am i missing?

Listen 80
User apache
Group apache
ServerAdmin root@localhost
ServerName example1.com:80
UseCanonicalName Off
DocumentRoot "/var/www/html"
<Directory />
    Options FollowSymLinks
    AllowOverride None
</Directory>
<Directory "/var/www/html">
    Options Indexes FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>



NameVirtualHost *:80

<VirtualHost *:80>
    DocumentRoot /virt1
    ServerName example2.com
    ErrorLog logs/example2.com-error_log
    CustomLog logs/example2.com-access_log common
</VirtualHost>


Any help is appreciated!!!

Thanks in advance

---

### Post by MJN on 2008-12-21
> **version7x said:**
> I've posted the relevant lines form httpd.confDon't use httpd.conf - it exists purely for backwards compatibility and should not be used for new configuration. Use /etc/apache2/sites-available/ instead (and then enable the sites with a2ensite)

> what am i missing?As you are using virtual hosting then all your site configs should be inside <Virtualhost></Virtualhost> containers - that includes your 'main' site.

Mathew

---

### Post by version7x on 2008-12-21
> Don't use httpd.conf - it exists purely for backwards compatibility and should not be used for new configuration. Use /etc/apache2/sites-available/ instead (and then enable the sites with a2ensite)

Good to know!  I'll have to remember that in the future!


As far as the meat of your reply....

> As you are using virtual hosting then all your site configs should be inside <Virtualhost></Virtualhost> containers - that includes your 'main' site.

... that did the trick!  I've been pounding my head on this all day.  Thank you so much!!


Best practices AND usefull advice.  You can't get a better reply than that!


-M

---

### Post by windependence on 2008-12-21
Matthew is da bomb! :)

-Tim

---

