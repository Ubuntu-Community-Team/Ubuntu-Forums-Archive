---
title: "Phpmyadmin work only with vhost"
date: 2008-01-13
forum: Server Platforms
---

### Post by JaBa02 on 2008-01-13
Hi. My problem is : 
When i type [http://myserverip/phpmyadmin](http://myserverip/phpmyadmin)  - Not found
But when i make virtual host in /etc/apache2/sites-available/default for phpmyadmin then work [http://myvirtualhost/phpmyadmin](http://myvirtualhost/phpmyadmin).

```
<VirtualHost *:80>
ServerName name.oo.lv
ServerAlias name.oo.lv
DocumentRoot /var/www/phpmyadmin
ErrorLog /var/log/apache2/error.log
</VirtualHost>
``` 

So I don`t get where is problem? Can anyone help me?

---

