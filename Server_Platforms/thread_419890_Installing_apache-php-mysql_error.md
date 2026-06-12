---
title: "Installing apache-php-mysql error"
date: 2007-04-23
forum: Server Platforms
---

### Post by alrave on 2007-04-23
Hi, i followed the instructions to create a LAMP server on the documentation ([https://help.ubuntu.com/community/ApacheMySQLPHP)](https://help.ubuntu.com/community/ApacheMySQLPHP)), but after i install everything i get the following error:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/apache2-default/test.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Im trying to open a file called 'test.php' located on /var/www/apache2-default/test.php. The file contains the following code:

<?php echo 'php its working!'; ?>


If anyone could help me get this server working, ive tried every guide ive found to install everything but i always end up getting the same errors.

---

### Post by deuce868 on 2007-04-23
It looks like you're just dealing with a permission issue. Realize that the web server (apache) is running as the user www-data. If you want it to read/write/execute files it has to have permissions to them. Check the permissions on the file that you're trying to include and I'll bet that www-data isn't allowed access.

---

