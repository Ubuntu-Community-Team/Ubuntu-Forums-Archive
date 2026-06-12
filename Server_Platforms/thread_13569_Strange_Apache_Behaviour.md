---
title: "Strange Apache Behaviour"
date: 2005-02-01
forum: Server Platforms
---

### Post by DeusX on 2005-02-01
I installed Apache2 and Php and MySQL and also PhpMyAdmin using Synaptic. I know I did, because I can access [http://localhost/phpmyadmin](http://localhost/phpmyadmin). This also shows me that not only Apache is working, but also Php and MySQL.

But if I create a file named blah.php in /var/www and I run [http://localhost/blah.php](http://localhost/blah.php), the server does not parse the file, but it is being send as a download to the browser.

Why is this happening?

---

### Post by jakobfriis on 2005-02-02
How does your .php file look ? I have seem some systems not realizing that the file is a php file because of the lack of a "?" in the top

if your php file looks like this
<php

Try to change it to 
<?php

Please post your blah file.

---

### Post by DeusX on 2005-02-02
The file is legal:

<?php echo "blah"; ?>

Maybe I should just install these apps from sources.

---

### Post by DeusX on 2005-02-02
Anyway, I did it the classical way, by installing from sources, now it works fine. Mybe it was a permission thingie or something, I really don't know.

---

### Post by ubuntu_fan on 2005-02-02
[QUOTE=DeusX]I installed Apache2 and Php and MySQL and also PhpMyAdmin using Synaptic. I know I did, because I can access [http://localhost/phpmyadmin](http://localhost/phpmyadmin). This also shows me that not only Apache is working, but also Php and MySQL.

But if I create a file named blah.php in /var/www and I run [http://localhost/blah.php](http://localhost/blah.php), the server does not parse the file, but it is being send as a download to the browser.

Why is this happening?[/QUOTE]

I know this is a bit of a silly question, but have you got the handlers for PHP added to your httpd.conf???

```

# Use for PHP 4:
AddHandler php-script   php

```

and the module is loaded

```

LoadModule php4_module        modules/libphp4.so

```

---

### Post by benjamin on 2005-02-02
You have to add 

AddType application/x-httpd-php .php .phtml

to your httpd.conf

Bye

---

### Post by cpinto on 2005-02-02
No you don't. Just symlink (if not already) a couple of files:
% ln -s /etc/apache2/mods-available/php4.load /etc/apache2/mods-enabled/
% ln -s /etc/apache2/mods-available/php4.conf /etc/apache2/mods-enabled/

and restart Apache 2.

---

