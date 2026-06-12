---
title: "php5 upgrade failed"
date: 2010-03-05
forum: Server Platforms
---

### Post by Kieeps on 2010-03-05
Yesterday i did a dist upgrade and it seems PHP updated to 5.3, the problem now is it wont even load anymore....Apache works fine and the PHP module is still in the modules-enabled :/ 

I checked the error logs of apache and found that there where some problems with some files having # instead of ; as comment signs, I corrected this and eventualy i had no error messages in the log anymore but still PHP wont work :(

[http://kieeps.com/~kieeps/index.php](http://kieeps.com/~kieeps/index.php) is suppose to be a phpinfo page but all that happens is that the entire page gets downloaded instead of loaded.

HTML on the other hand works just fine
[http://kieeps.com/~kieeps/apa.html](http://kieeps.com/~kieeps/apa.html)

Anyone know how to troubleshoot this? or even have an answer to whats wrong now that i cant find anything wrong in the error.log :O

---

### Post by ICEB3AR on 2010-03-05
Have you defined anywhere in the apache configuration files what should happen with .php files ?

Looks like - to me - as if apache don't know how to handle them and let you download the files. ;)

---

### Post by Kieeps on 2010-03-05
never actually messed with that on ubuntu and it's fancy module system, so i removed it from mods-enabled and made a php.conf file in /etc/apache2/conf.d/ containing this:

```

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
<Files *.php>
SetOutputFilter PHP
SetInputFilter PHP
LimitRequestBody 9524288
</Files>
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
DirectoryIndex index.php

```

It loads fine but still no change :(

EDIT:
took a look into the php5.conf that was in the mods-enabled and it seems as that file already defined *.php:
```
<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
        SetHandler application/x-httpd-php-source
    </FilesMatch>
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>

```

---

