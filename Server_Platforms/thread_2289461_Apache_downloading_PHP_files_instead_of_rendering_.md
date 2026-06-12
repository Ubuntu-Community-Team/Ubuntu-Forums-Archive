---
title: "Apache downloading PHP files instead of rendering them after uddate form php 5.3.3 to"
date: 2015-08-04
forum: Server Platforms
---

### Post by GodsDead on 2015-08-04
I have some scripts that need to use a newer version of PHP, Im running Debian 6 which has PHP 5.3.3 support, I found I could install php 5.4 using [https://www.dotdeb.org/instructions/](https://www.dotdeb.org/instructions/) packages. This worked, it updated my PHP to a newer version, the only issue is that when the install completed apache now downloads the PHP file instead of rendering it, Ive been troweling google and stackoverflow and servefault for hours now and I cant find a solution.

Im guessing this has something to do with the Apache configs, but I don't know what to do.


```

tom@vps:~$ dpkg --list |grep -E '(apache)|(php5-)'
ii  apache2                                  2.2.16-6+squeeze12           Apache                                                                                                                     HTTP Server metapackage
ii  apache2-doc                              2.2.16-6+squeeze12           Apache                                                                                                                     HTTP Server documentation
ii  apache2-mpm-prefork                      2.2.16-6+squeeze12           Apache                                                                                                                     HTTP Server - traditional non-threaded model
ii  apache2-utils                            2.2.16-6+squeeze12           utilit                                                                                                                    y programs for webservers
ii  apache2.2-bin                            2.2.16-6+squeeze12           Apache                                                                                                                     HTTP Server common binary files
ii  apache2.2-common                         2.2.16-6+squeeze12           Apache                                                                                                                     HTTP Server common files
ii  libapache2-mod-php5                      5.4.43-1~dotdeb+6.1          server                                                                                                                    -side, HTML-embedded scripting language (Apache 2 module)
ii  php5-apc                                 5.4.43-1~dotdeb+6.1          apc mo                                                                                                                    dule for php5
ii  php5-cli                                 5.4.43-1~dotdeb+6.1          comman                                                                                                                    d-line interpreter for the php5 scripting language
ii  php5-common                              5.4.43-1~dotdeb+6.1          Common                                                                                                                     files for packages built from the php5 source
ii  php5-gd                                  5.4.43-1~dotdeb+6.1          GD mod                                                                                                                    ule for php5
ii  php5-mcrypt                              5.4.43-1~dotdeb+6.1          MCrypt                                                                                                                     module for php5
ii  php5-mysql                               5.4.43-1~dotdeb+6.1          MySQL                                                                                                                     module for php5
rc  php5-suhosin                             0.9.32.1-1                   advanc                                                                                                                    ed protection module for php5

```

---

### Post by SeijiSensei on 2015-08-04
Usually libapache2-mod-php5 is the key package, as it installs files in the Apache configuration that tell the web server to use its PHP parser on files with extensions like .php or .phtml. 

Does Debian not have a meta package like [lamp-server^]("https://help.ubuntu.com/community/ApacheMySQLPHP") for Ubuntu? That's what I would suggest using if it's an option.

---

### Post by GodsDead on 2015-08-04
Hey SeijiSensei, Yes it does, that's how I originally installed my LAMP stack, but being debian 6, it uses php 5.3.3 and I needed to upgrade it to at least php 5.4 thats why I used the dotdeb repository, Im sure its got to be something simple in the apache config..

---

### Post by cj13579 on 2015-08-05
You *should* be able to do this in 3 simple steps. Load the PHP Module, add the application type, and match file types to applications types (all in http.conf)
```

LoadModule php5_module

AddType application/x-httpd-php .php

<FilesMatch \.php$>
    SetHandler application/x-httpd-php
</FilesMatch>

```

See here for more details.

[http://php.net/manual/en/install.unix.apache2.php](http://php.net/manual/en/install.unix.apache2.php)

---

### Post by SeijiSensei on 2015-08-05
The file /etc/apache2/mods-available/php5.conf contains a more elaborate version of the commands suggested.  The file ../php5.load loads the PHP5 module.

OP, check to make sure those files exist in /etc/apache2/mods-available/ and that there are symbolic links to them in /etc/apache2/mods-enabled/.  Maybe you're missing those links?

---

