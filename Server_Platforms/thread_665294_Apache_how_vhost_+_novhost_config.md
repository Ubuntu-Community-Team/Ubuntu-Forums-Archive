---
title: "Apache how vhost + novhost config?"
date: 2008-01-12
forum: Server Platforms
---

### Post by JaBa02 on 2008-01-12
Hi. Can anyone help me with apache configuration with vhosts + novhosts.

**Configuration:**

**/etc/apache2/apache2.conf**
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

**/etc/apache/sites-available/**
```
NameVirtualHost *:80

<VirtualHost *:80>
ServerName something.oo.lv //something.oo.lv
ServerAlias something.oo.lv
DocumentRoot /var/www/lapsai
ErrorLog /var/log/apache2/error.log
</VirtualHost>
```

**Problems:**
1.) When i type to go to my ip adress it automatically goes to something.oo.lv, is posible to add other folder for my ip if connect to ip? And how then need create vhost or something?

2.) I add symlink to /var/www/phpmyadmin, but when i go [http://myip/phpmyadmin](http://myip/phpmyadmin), shows "Not Found", i think need change something in apache configuration files? Any ideas?

---

### Post by JaBa02 on 2008-01-12
So I do till, now still phpmyadmin, not works, but how can i get back this directory(wih all conf files on it), i think with that have problem:
/etc/phpmyadmin

---

