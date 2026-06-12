---
title: "Warning: (null) PHP ERROR"
date: 2005-09-07
forum: Server Platforms
---

### Post by Bon-Bon on 2005-09-07
I keep getting the following error when trying to access a php page containing:

<?php phpinfo(); ?>

error:```
Warning: Unknown(/var/www/apache2-default/test.php): failed to open stream: Permission denied in Unknown on line 0

Warning: (null)(): Failed opening '/var/www/apache2-default/test.php' for inclusion (include_path='.') in Unknown on line 0
```

If I try to access other pages written in PHP they are sent as text files.

---

### Post by relix42 on 2005-09-08
What is in your /etc/apache2/mods-enable directory?  If php isn't listed, that could be your problem.

Sounds like php isn't be loaded as a module by Apache.

---

### Post by LordHunter317 on 2005-09-08
That or you have a serious permissions issue, did you install libapache2-mod-php4?

---

### Post by Bon-Bon on 2005-09-08
[QUOTE=LordHunter317]did you install libapache2-mod-php4?[/QUOTE]

I did, and in the mods-enabled directory there are only 3 shortcuts to other places and none of which are PHP.

I do not have any PHP files in my mods available directory either.

---

### Post by LordHunter317 on 2005-09-08
Then you don't have the right package installed, or it's not configured right... post the output of :```
dpkg --get-selections | grep php
```

---

### Post by Bon-Bon on 2005-09-08
```
libapache2-mod-php4                             install
php4                                            install
php4-common                                     install
php4-pgsql                                      install
```

---

### Post by Bon-Bon on 2005-09-08
To save me the hassle I have reinstalled Ubuntu, everything is working now apart from PHP and MySQL.

Here is my phpinfo page:
[http://matthewbonner.homeip.net/test.php](http://matthewbonner.homeip.net/test.php)

I tried to setup a mysql user and I could not because the mysqladmin command was not found.

---

### Post by Bon-Bon on 2005-09-08
I have got it all sorted now, thanks.

---

