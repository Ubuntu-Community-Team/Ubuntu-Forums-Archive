---
title: "Restarting Apache2 problem"
date: 2006-10-03
forum: Server Platforms
---

### Post by SawnDiddle on 2006-10-03
ok, so I was following this guide and everything went find except for the end. 

[http://forum.ragezone.com/coders-paradise/howto-apache2-mysql-php5-linux-debian-ubuntu-174712.html](http://forum.ragezone.com/coders-paradise/howto-apache2-mysql-php5-linux-debian-ubuntu-174712.html)

Now, as for the guide, I do everything, but when I get to phpmyadmin, I had a problem that the terminal.

Package phpmyadmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package phpmyadmin has no installation candidate

So I went online to [http://packages.ubuntu.com/hoary/web/phpmyadmin](http://packages.ubuntu.com/hoary/web/phpmyadmin) and downloaded the package from there.

I continued with the rest of the guide but when it came time to restart apache2 I got the following error.

sawndiddle@sawndiddle-desktop:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... Syntax error on line 1 of /etc/apache2/mods-enabled/php4.load:
Cannot load /usr/lib/apache2/modules/libphp4.so into server: /usr/lib/apache2/modules/libphp4.so: cannot open shared object file: No such file or directory
                                                                         [fail]

Now, I have also tried to skip to opening MySQL Administrator but I get this.

Could not launch menu item

Details: Failed to execute child process "/usr/bin/mysql-admin" (No such file or directory)

Now, I am VERY new to Ubuntu/Linux so I do need things written out for me, but why is it that I am getting a php4 error when I have php5 on Ubuntu? Also, how would be the best/easiest way to get apache2 to reload (if that is the extent of my problems)?

---

### Post by Jussi Kukkonen on 2006-10-03
You didn't mention which Ubuntu version you are running, but I strongly suggest not installing software for a random version... That's mostly asking for trouble. Either the package is available, but your end has a problem or the package isn't available for your version *for a good reason*.

> 
Package phpmyadmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package phpmyadmin has no installation candidate

phpmyadmin should be available for all Ubuntu versions... Can your try updating the package lists and then trying again:
```
sudo apt-get update
sudo apt-get install phpmyadmin
```
You could also make sure that universe repository is enabled (it should by default), or paste the contents of /etc/apt/sources.list here.

---

### Post by SawnDiddle on 2006-10-03
ok, I am running Ubuntu 6.06 sorry about not clarifying it.

I have removed phpmyadmin and tried putting it back on, but I get the error that says phpmyadmin is not available. I was hoping that was going to let me restart Apache2 but it didn't.

Any ideas on how I can get this fixed?

---

