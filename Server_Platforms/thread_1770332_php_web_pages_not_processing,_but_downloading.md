---
title: "php web pages not processing, but downloading"
date: 2011-05-29
forum: Server Platforms
---

### Post by trans_lux on 2011-05-29
I'm really desperate as I have spent the better part of the last 10 hours trying to sort this out before my boss finds out :(

When I try and browse to one of our websites the browser wants to download the file as the server will not process the php file.
I get which is a: application/x-httpd-php

What's really odd is that from inside the network where the server is located everything works fine, its only from the outside that this happens???

Everything was fine until I ran an system update from webmin that updated a ton of things including Apache2 and PHP5. 

Its a self hosted server that was running UB server 9.10, but I have since upgraded to 10.04.2 LTS but no luck.

Apache version 2.2.14
PHP Version 5.3.2-1ubuntu4.9
Joomla 1.5 -latest

I would be eternally great full for any and all help on this.

Thanks in advance

Eric

---

### Post by LightningCrash on 2011-05-29
sounds like mod_php5 is disabled somehow

try

```
sudo a2enmod php5
sudo service apache2 restart
```

Then try to access the pages again

---

