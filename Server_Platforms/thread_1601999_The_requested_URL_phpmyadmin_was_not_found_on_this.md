---
title: "The requested URL /phpmyadmin was not found on this server."
date: 2010-10-20
forum: Server Platforms
---

### Post by acompay on 2010-10-20
Hello There!
I followed instruction from here: [http://www.hackourlives.com/install-apache-mysql-php-phpmyadmin-lamp-on-ubuntu-10-04-or-mint-linux-9/](http://www.hackourlives.com/install-apache-mysql-php-phpmyadmin-lamp-on-ubuntu-10-04-or-mint-linux-9/) after getting the error: The requested URL /phpmyadmin was not found on this server. Everything went through okay. The only difference was that during the installation of phpmyadmin it did not ask me for the server name to select. The info.php works okay when open in the browser: localhost/info.php but localhost/phpmyadmin shows up  still the error "The requested URL /phpmyadmin was not found on this server." What can I do now? 
Regards,

---

### Post by Barriehie on 2010-10-20
It's missing the part where you have to enable phpmyadmin in apache.  This needs to be in the apache2.conf file:
```

Include /etc/phpmyadmin/apache.conf
```

Also can use the ServerName directive in the apache2.conf file.

---

