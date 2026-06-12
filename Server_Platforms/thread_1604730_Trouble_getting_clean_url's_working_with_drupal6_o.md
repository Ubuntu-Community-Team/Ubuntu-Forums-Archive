---
title: "Trouble getting clean url's working with drupal6 on 10.10"
date: 2010-10-24
forum: Server Platforms
---

### Post by meredin on 2010-10-24
after googling I followed the following instructions:-


sudo a2enmod rewrite
sudo pico /etc/apache2/sites-available/default 

in this section:
<directory /var/www/>
change  
AllowOverride None
to
AllowOverride All

Restart apache: 

sudo apachectl restart


however I'm still getting the following message.
Your system configuration does not currently support this feature.

could anyone tell me what I'm doing wrong?
Thanks

---

