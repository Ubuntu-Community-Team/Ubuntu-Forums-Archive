---
title: "Load new php.ini on Ubuntu Server with nginx."
date: 2013-09-17
forum: Server Platforms
---

### Post by cdysthe on 2013-09-17
Hi,

We have a couple of new servers up running Ubuntu Server Edtition 12.04 LTS. The web server used is nginx and PHP5 is installed and configured. It all works fine. However, we are now going to run a PHP based web application which requires some php.ini modifications (max_upload and such). How do I get the new php.ini to load with the new settings? I remember when using Apache you could simply restart Apache and updated PHP settings would take effect, but with nginx just restarting the web server doesn't work and the old settings are still used. Reboot is not an option since the server is in production.

---

### Post by aschlosberg on 2013-09-17
In the Apache case that you mention, the processing of PHP is performed by an Apache module (I assume mod_php) which is why restarting the server will cause the new php.ini to be used. On the other hand nginx passes on processing of PHP files as CGI and it is this service that needs to be restarted.

What are you using to handle PHP? PHP FPM? If so, you can restart it with:

```

sudo service php5-fpm restart

```

---

### Post by cdysthe on 2013-09-18
Thanks! That's it.

---

