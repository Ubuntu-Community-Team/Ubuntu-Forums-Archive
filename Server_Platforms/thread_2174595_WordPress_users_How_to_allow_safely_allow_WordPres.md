---
title: "WordPress users: How to allow safely allow WordPress to write to wp-content?"
date: 2013-09-15
forum: Server Platforms
---

### Post by icebox83 on 2013-09-15
I am so frustrated right now. I have a Ubuntu Server install running LAMP and am installing WordPress under /var/www/wordpress. It has been recommended to me NOT to chown user:www-data /var/www/wordpress due to security concerns, yet the ONLY way WordPress can write to /var/www/wordpress/wp-content in order to install themes and plugins and upload things is if the group is www-data OR I chmod 777. What do I do? Surely there are experts on this forum who run WordPress.

---

### Post by Habitual on 2013-09-15
[http://wordpress.org/support/topic/directory-and-file-permissions](http://wordpress.org/support/topic/directory-and-file-permissions)

---

