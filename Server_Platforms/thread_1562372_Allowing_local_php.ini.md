---
title: "Allowing local php.ini"
date: 2010-08-27
forum: Server Platforms
---

### Post by Fliggerty on 2010-08-27
Hey all,

I'm running Ubuntu 10.04.1 LTS with Apache2 and PHP5. 

For some reason I'm not able to use a local php.ini.  Even when it does exist, phpinfo reports that the Loaded Configuration File is /etc/php5/apache2/php.in.

If I define it in the conf file for any of my virtual hosts, it then becomes global...which is definitely less than ideal.

I added this in the .htaccess file in the directory I'm working with:

SetEnv PHPRC /var/www/path_to/php.ini

Still no luck.  That works on every other system I've worked with.

Any suggestions on what I am missing here?

Thanks!

---

### Post by quixote on 2010-08-29
Just a wild guess: when I got tripped up with some similar config stuff, it turned out to be because they've pretty much rearranged a lot of the apache-related files.  I had to alter settings in /etc/apache2/mods-available & /etc/apache2/sites-available, and then copy the changed file to sites-enabled, mods-enabled, and restart networking.  Maybe that's the direction to look in for you too?

---

