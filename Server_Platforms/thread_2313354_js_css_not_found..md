---
title: "js /css not found."
date: 2016-02-11
forum: Server Platforms
---

### Post by joss2 on 2016-02-11
[COLOR=#31302B][FONT=Open Sans]Hi everyone[/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans] [/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans]I'm having a strange issue with my Magento webshop that after a period of time, the webpage cannot find the css and JS files anymore. They all give a 404 error. This results in prices displayed in USD instead of EUR and the admin page not reachable.[/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans]I see that in the link, the "js" folder is missing. So instead of[www.domain.com/js/mage/adminhtml/form.js,]("http://www.domain.com/js/mage/adminhtml/form.js,") the webpage tries to reach[www.domain.com/mage/...]("http://www.domain.com/mage/...") resulting in a 404 error. [/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans]The issue is resolved when I restart the apache service on my server. Not when I clear the cache. [/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans] [/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans]Any idea why this happens? It started a few months ago when I started using virtualhostfiles to host different websited on one server. [/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans] [/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans]Sincerely[/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans] [/FONT][/COLOR]
[COLOR=#31302B][FONT=Open Sans]Jen[/FONT][/COLOR]

---

### Post by nerdtron on 2016-02-11
Might as weel post your virtual host config setup. Error 404 means not found. So more likely the error will be incorrect declaration of RootDirectory for you virtual hosts.

---

### Post by joss2 on 2016-02-12
This is my virtualhost file: 

<VirtualHost *:80>
               Documentroot /var/www/shop
               ServerName shop.test.be
               <Directory /var/www/shop>
                              Options FollowSymlinks
                              AllowOverride All
                              Order allow,deny
                              Allow from all
               </Directory>
               ErrorLog /var/www/shop/error.log
               CustomLog /var/www/shop/access.log combined
</VirtualHost>

So the issue is that all works good until a sudden moment (a few days, weeks, a month) the "js" and css folder is skipped.

---

