---
title: "VirtualHost"
date: 2011-02-10
forum: Server Platforms
---

### Post by Sfacs on 2011-02-10
Hi!

I would need your help for a little problem I have.

I have a server, which host several website (let's call them siteA, siteB, siteC).

All of those websites have a domain name, and the virtualhosts are working perfectly:
[www.siteA.com](www.siteA.com) -> /var/www/siteA
[www.siteB.com](www.siteB.com) -> /var/www/siteB
[www.siteC.com](www.siteC.com) -> /var/www/siteC

However, I'd like to be able to access to /var/www when I try to reach [http://server_ip_address](http://server_ip_address)
Right now, when I reach this address, it redirects me on siteA.

Is that possible?

Thanks a lot,

Sfacs

---

### Post by acelino on 2011-02-10
Hi,


go to /etc/apache/sites-available then create a new file lets say SiteB. then open SiteB " and key in this apache directive :
```
<VirtualHost *:80>
DocumentRoot /var/www/html/SiteB 
ServerName SiteB.com
<Directory "/var/www/html/SiteB">
Options Indexes FollowSymLinks
allow from all
AllowOverride All
Options -Indexes
</Directory>
ServerAlias www.SiteB.com
DirectoryIndex index.php index.html
</VirtualHost>

```
Then issue the command ```
sudo a2ensite SiteB
```, then reload apache```
 sudo /etc/init.d/apache reload 
```

Same procedure with SiteC


GoodLuck!

---

