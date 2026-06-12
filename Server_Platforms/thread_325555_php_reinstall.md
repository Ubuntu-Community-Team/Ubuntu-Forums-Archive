---
title: "php reinstall"
date: 2006-12-25
forum: Server Platforms
---

### Post by xolot1 on 2006-12-25
i havent been able to get php to install to my apache2 webserver. i looked around google/forums/etc, but nothing yet has worked. ive run through the basic install process many times, but to no avail.

background: i was trying to get Gallery2 photo album/organizer set up on my apache2 webserver (currently back at college). it requires apache, php, and mysql. i had apache and php working, so i installed mysql. i ended up not having mysql set up correctly, so i began to mess with the php (i dont have any experience with php, i just needed it working :-/ )

when visiting my root webserver directory, it would display both my apache and php version. however after i messed w/the php, it ceased functioning. i uninstalled apache, php, mysql - everything, and attempted to reinstall, hoping for a fix. no luck.

currently:
im told php5, apache2, and mysql are installed. but my root webpage only mentioned apache being installed.
```

willi@fileserver:/usr/share$ sudo apt-get install apache2 php5 php5-mysql php5-common libapache2-mod-php5 
Reading package lists... Done Building dependency tree... Done 
apache2 is already the newest version. 
php5 is already the newest version. 
php5-mysql is already the newest version. 
php5-common is already the newest version. 
libapache2-mod-php5 is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 

willi@fileserver:/usr/share$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... [ ok ] willi@fileserver:/usr/share$

```

what can i do to get php working?

---

### Post by not_cool on 2006-12-26
Try using synaptic and completely removing all the packages related to AMP (at least the php ones) by selecting "Mark for complete removal." Then reinstall all the packages. (that worked for me when it wanted me to download the php files instead of showing them on the server)

BTW, when it says it will uninstall the dependencies to php and whatnot, make sure your are completely uninstalling all of the those also ("Mark for complete removal")

---

### Post by xolot1 on 2006-12-26
right now im using ssh to connect to a server install back at college. is there a way to use synaptic for this setup? the filesystems are mounted on my laptop via sshfs.

thanks!

---

### Post by not_cool on 2006-12-26
try doing a sudo aptitude purge PACKAGE, it remove the config files also (instead of remove), which is the same as "Mark for complete removal," as far as I know

---

### Post by MrHorus on 2006-12-27
> **xolot1 said:**
> im told php5, apache2, and mysql are installed. but my root webpage only mentioned apache being installed.


Well it would do - Apache knows nothing of PHP until it finds tags that tell it to load the module.

Can you try invoking the phpinfo method and tell us what happens?
Just put the following into a document called test.php and place it in your webroot:

<?php

phpinfo();

?>

---

### Post by xolot1 on 2006-12-27
@not_cool
thanks for the aptitude pointer. i used that to completely remove apache, mysql, and php and reinstall from these from the beginning.

now apache is up and running again, 
```
Index of /

Icon  Name                    Last modified      Size  Description[DIR] apache2-default/        26-Jul-2006 13:50    -   
[DIR] data/                   25-Dec-2006 01:37    -   
[   ] gallery-2.1.2-full.t..> 16-Aug-2006 23:50  7.7M  
[DIR] gallery2/               28-Apr-2006 15:19    -   
[   ] test.php                27-Dec-2006 13:49   22   

Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at #### Port 80
```

and as i click on test.php, it brings up a nice page with the install details. thanks!

willi

---

