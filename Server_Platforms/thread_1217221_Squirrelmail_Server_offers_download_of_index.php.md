---
title: "Squirrelmail Server offers download of index.php"
date: 2009-07-19
forum: Server Platforms
---

### Post by cirobr on 2009-07-19
Hello,

I have a clean installation of apache2 and squirrelmail on my Intrepid server. My web page (index.html) displays properly when the server default address is typed on Firefox ([http://192.168.0.100](http://192.168.0.100)).

When Squirrelmail page is requested ([http://192.168.0.100/squirrelmail](http://192.168.0.100/squirrelmail)), the file "index.php" is offered for download. By no means Firefox displays the welcome/login screen.

Any help is appreciated.

Thanks.

---

### Post by The Tronyx on 2009-07-19
Hello,

Do you have PHP installed to your server?  Generally speaking, this most often occurs when there is no PHP handler set in the Apache configuration file or PHP is not installed to the system.

You can use the LoadModule directive to load the PHP4/5 module by putting the below in the main section of the Apache configuration file.
```

LoadModule php5_module modules/libphp5.so
AddType application/x-httpd-php .php

```

You might also want to be sure that the shared object file in under modules otherwise this will not work.

---

### Post by cirobr on 2009-07-19
Thanks for replying. Which file you mean by "Apache configuration"? For instance:

* httpd.conf is blank
* apache2.conf has no "php" stated on it.

By the way, php5 is installed.

Thanks,

---

### Post by The Tronyx on 2009-07-19
> **cirobr said:**
> Thanks for replying. Which file you mean by "Apache configuration"? For instance:

* httpd.conf is blank
* apache2.conf has no "php" stated on it.

By the way, php5 is installed.

Thanks,

Greetings.  I am actually at work right now and not near my Ubuntu system however it should be the apache2.conf file located at /etc/apache2/apache2.conf.  If you have error logging enabled, you may wish to check the logs for any verbose failure messages or possible segfaulting.  If PHP is segfaulting, it should generate both a core dump file in the location it is being executed from, i.e. /var/www/mysites/stuff.

*Edit*
Check the modules directory and see if there is a php*.so module.  If so, add the LoadModule and AddType directives as seen above.

---

### Post by The Tronyx on 2009-07-19
cirobr, sorry for the double post but have you installed libapache2-mod-php5?

```

sudo apt-get install libapache2-mod-php5

```

That should take care of the AddType and LoadModule for you.

---

### Post by cirobr on 2009-07-20
Hello The Tronyx,

These are my findings:

* When PHP5 is installed (sudo apt-get install php5), the package libapache2-mod-php5 is also installed. This is verified by an attempt to install this second package.

* PHP5 is loaded on the server. I've loaded the code as on post #2 above and restarted Apache2. In return, I've got the message "[warn] module php5_module is already loaded, skipping".

* Nevertheless, I've purged and reinstalled apache2, php5, squirrelmail and all associated packages. Code on #2 post is removed. Now system is working.

Thanks for helping.

---

