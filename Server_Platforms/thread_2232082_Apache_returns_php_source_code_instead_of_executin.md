---
title: "Apache returns php source code instead of executing it"
date: 2014-06-29
forum: Server Platforms
---

### Post by van3 on 2014-06-29
Good afternoon.

First of all I have already read dozens of arcticles and questions regarding this issue.
[http://stackoverflow.com/questions/7264014/why-is-my-php-source-code-showing](http://stackoverflow.com/questions/7264014/why-is-my-php-source-code-showing)
[http://stackoverflow.com/questions/11595830/php-not-interpreted-showing-in-view-source-apache2-amazon-aws](http://stackoverflow.com/questions/11595830/php-not-interpreted-showing-in-view-source-apache2-amazon-aws)
[http://stackoverflow.com/questions/12142172/apache-shows-php-code-instead-of-executing](http://stackoverflow.com/questions/12142172/apache-shows-php-code-instead-of-executing)
[http://askubuntu.com/questions/59272/php-not-working-in-apache2-after-system-upgrade](http://askubuntu.com/questions/59272/php-not-working-in-apache2-after-system-upgrade)
[http://stackoverflow.com/questions/5121495/php-code-is-not-being-executed-i-can-see-it-on-source-code-of-page](http://stackoverflow.com/questions/5121495/php-code-is-not-being-executed-i-can-see-it-on-source-code-of-page)
[http://forums.devarticles.com/web-server-configuration-51/php-pages-won-t-load-show-source-code-apache-2t-52648.html](http://forums.devarticles.com/web-server-configuration-51/php-pages-won-t-load-show-source-code-apache-2t-52648.html)
...

Sorry, but all solutions mentioned in these pages do not work for me and I decided to register here and open this question again.

Let's go. My environment.

Ubuntu 12.04

uname -a
> Linux 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

php --version
> PHP 5.4.6-1ubuntu1.8 (cli) (built: Apr  4 2014 01:28:36)
Copyright (c) 1997-2012 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2012 Zend Technologies

a2enmod php5
> Module php5 already enabled

php5.conf contains SetHandler directive
> <IfModule mod_php5.c>
    <FilesMatch ".+\.ph(p[345]?|t|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch ".+\.phps$">
        SetHandler application/x-httpd-php-source
        # Deny access to raw php sources by default
        # To re-enable it's recommended to enable access to the files
        # only in specific virtual host or directory
        Order Deny,Allow
        Deny from all
    </FilesMatch>
    # Deny access to files without filename (e.g. '.php')
    <FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
        Order Deny,Allow
        Deny from all
    </FilesMatch>

    # Running PHP scripts in user directories is disabled by default
    #
    # To re-enable PHP in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>

apache2.conf contains AddType directives
> AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

My test php file
/var/www/wwwowner/data/www/mydomain.com/info.php

[PHP]<?php phpinfo(); ?>[/PHP]

is ANSI encoded and has 755 permissions.
I clear browser cookie & cache every time I test changes. I restart apache2 service also every time.

And every time I see this:
[IMG]http://i.imgur.com/YVtNpoQ.png[/IMG]
I already tried to purge libapache2-mod-php5 and install it again:
> apt-get purge libapache2-mod-php5
apt-get install libapache2-mod-php5

I tried to set php_admin_value engine **On** in php5.conf even directory where this rule is being applied is not match to mine.
> # Running PHP scripts in user directories is disabled by default
    #
    # To re-enable PHP in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine **On**
        </Directory>
    </IfModule>
</IfModule>

I appreciate any help and will provide any info you want in order to find root cause of the problem.

Thank you.

---

### Post by cariboo on 2014-06-30
Have you got libapache2-mod-php5 installed?

---

### Post by van3 on 2014-06-30
> **cariboo907 said:**
> Have you got libapache2-mod-php5 installed?

Yes, see my first post.

---

