---
title: "Apache + phpmyadmin with config method"
date: 2009-12-15
forum: Server Platforms
---

### Post by micschk on 2009-12-15
I want to install phpmyadmin from the repositories, so it will automatically be updated, and I only want to alias it for some domains in Apache's vhosts file, with the 'config method' (use .htaccess to log in, sql user & pass stored in config.inc.php file).

Now my question is; *would it be possible to alias a file to another based on the apache vhosts config file? (or any other way)* I know how to alias a virtual directory;
<VirtualHost *:80>
    ServerName server.com
    ServerAlias [www.server.com](www.server.com)
    DocumentRoot /var/www/server.com
    ...
    # phpMyAdmin
    Alias /phpmyadmin /usr/share/phpmyadmin
    Alias /phpmyadmin/conf.inc.php /var/www/server.com/phpmyadmin.conf.inc.php
...

So, i alias the server.com/phpmyadmin page to phpMyAdmin, this works. But now I want this general phpMyAdmin to include the vhost-specific file conf.inc.php from /var/www/server.com/phpmyadmin.conf.inc.php instead of /usr/share/phpmyadmin/conf.inc.php

On the file system I could just "ln -s" them, but that would point to the same config file for all virtual hosts.

---

