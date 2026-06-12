---
title: "apache proxy/redirect"
date: 2012-06-25
forum: Server Platforms
---

### Post by Gompa on 2012-06-25
so iam trying to make [a server for my yard]("http://ubuntuforums.org/showthread.php?t=2009381")

but i dont want to run my main websites on it so i set up a apache proxy like this :
```
<VirtualHost *:80>
  ServerName yardserv.h-bomb.nl
  ProxyPass / http://192.168.1.45/
  ProxyPassReverse / http://192.168.1.45/
</VirtualHost>

```

and my virtual host on the yard server :
```
<VirtualHost *:80>
        DocumentRoot /var/www/wordpress/
        ServerName yardserv.h-bomb.nl
        ServerAlias yardserv.h-bomb.nl
</VirtualHost>
```

but this only shows the www dir and does not redirect to /wordpress/

could one of you please shed some light on this

---

