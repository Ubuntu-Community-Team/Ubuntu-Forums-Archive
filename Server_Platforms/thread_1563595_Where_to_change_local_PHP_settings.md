---
title: "Where to change local PHP settings"
date: 2010-08-29
forum: Server Platforms
---

### Post by wesg on 2010-08-29
I need to change the sendmail path of PHP. I changed /etc/php5/apache2/php.ini but the changes didn't take into affect. Where might I find the file that contains local PHP settings?

---

### Post by baudday on 2010-08-29
Did you restart apache after making the changes?

---

### Post by vuetrip on 2010-08-29
restart using:

sudo /etc/init.d/apache2 restart

then see if it's worked if not load the phpinfo in your browser:

Save as phpinfo.php and load in browser to view phpinfo
<?php
phpinfo();
?>

---

### Post by wesg on 2010-08-29
Did all that. When I changed a setting to see what it did, it was changed under Global. It seems that when PHP mails something, it's still using local settings.

---

