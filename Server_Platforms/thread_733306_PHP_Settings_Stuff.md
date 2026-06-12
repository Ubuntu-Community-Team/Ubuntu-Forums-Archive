---
title: "PHP Settings Stuff"
date: 2008-03-23
forum: Server Platforms
---

### Post by kooseefoo on 2008-03-23
Okay, this should be simple. I have a setting that needs to be different for two different things hosted on my apache server. If it helps, they are both on different virtuals with apache.

The setting is session.save_handler. To get Drupal 6 to work, I had to change it from the default setting of "files" to "user". Unfortunately, doing this has totally botched my acidbase web interface I use for security stuff.
I modified it in my main php configuration file - /etc/php5/apache2/php.ini

Yeah. I'm sure this is simple stuff. I'm just going to admit that I have no idea what I'm doing and ask for help.


Chris

---

### Post by ctyc on 2008-03-23
forget the snort on acid, and just learn Drupal.

---

### Post by kooseefoo on 2008-03-23
I'm not sure what you mean.

The setting change had to be done because of a drupal update. I had both of them working before... I'm just wondering if I can make that particular setting change depending on if someone is on drupal or acid.

Thanks,
Chris

---

