---
title: "drupal install help"
date: 2009-12-10
forum: Server Platforms
---

### Post by jonabyte on 2009-12-10
I installed drupal using the apt-get install command and it went well and I was able to get to the admin page, etc. The problem now is the drupal site is located at "www.example.com/drupal6", instead of the preferred "www.example.com". The admin section of drupal does not seem to allow me to change the site address.

Anyone have any ideas how to change it so it points directly to the .com address without the additional "drupal6" location?

Thanks

---

### Post by tlsarles on 2010-01-13
There are a couple of places to look, but most likly under /etc/apache2/sites-availible there should be a config file called drupal. Edit the documentroot line to reflect the drupal6 folder. There may also be a default config file there, you can try editing that one too

---

