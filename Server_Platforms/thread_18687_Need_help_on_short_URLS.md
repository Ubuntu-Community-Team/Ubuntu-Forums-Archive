---
title: "Need help on short URLS"
date: 2005-03-08
forum: Server Platforms
---

### Post by voodoostevie on 2005-03-08
I know this is mainly done via the mod_rewrite module. However I am not entirely sure how to go about it.

I am planning on using the short url feature of MD-Pro (which is a CMS script that is a Postnuke fork using Autotheme). I have placed the .htaccess file in the directory of the script however it won't parse it properly. Where do I turn on the module. 

I am using apache2 not apache 1.3 to do this.

---

### Post by az on 2005-03-08
sudo a2enmod rewrite

---

