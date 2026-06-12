---
title: "Phpmyadmin Fatal error: Allowed memory size of 16777216 bytes exhausted"
date: 2009-07-01
forum: Server Platforms
---

### Post by Radio91 on 2009-07-01
I'm getting this error when trying to import a database file in phpmyadmin 
Fatal error: Allowed memory size of 16777216 bytes exhausted (tried to allocate 13937832 bytes) in /usr/share/phpmyadmin/libraries/unzip.lib.php on line 325.

I edited the php.ini file and increased the memory to 32M but still the same error message.

How to I solve this? I also dont understand how 13mb can exhaust 16mb of memory?

---

### Post by TwiceOver on 2009-07-01
Did you restart apache after changing your php.ini?

---

### Post by Radio91 on 2009-07-01
i rebooted the server

whats the command to restart apache anyway?

---

### Post by TwiceOver on 2009-07-01
/etc/init.d/apache2 restart

hrm...

---

### Post by Radio91 on 2009-07-01
still did'nt solve the issue anyway

---

### Post by TwiceOver on 2009-07-01
Sorry, if you've edited the php.ini and changed the value that was already there from 16M to 32M and restarted, I'm not sure what else to tell ya...

Just to be sure the php.ini file that you edited was in:

/etc/php5/apache2/php.ini?

And you did change the value instead of adding a second variable right? 

memory_limit = 32M

Just double checking, this is the only place I know of to allow php to use more memory and is exactly the setting I'm using for my server (with phpmyadmin installed).

After dark the real experts will come out :D

---

### Post by aent on 2009-07-09
> **TwiceOver said:**
> Sorry, if you've edited the php.ini and changed the value that was already there from 16M to 32M and restarted, I'm not sure what else to tell ya...

Just to be sure the php.ini file that you edited was in:

/etc/php5/apache2/php.ini?

And you did change the value instead of adding a second variable right? 

memory_limit = 32M

Just double checking, this is the only place I know of to allow php to use more memory and is exactly the setting I'm using for my server (with phpmyadmin installed).

After dark the real experts will come out :D
It can also be set inside any apache config file. Specifically, I would check /etc/apache2/sites-enabled/phpmyadmin.conf or /etc/apache2/conf.d/phpmyadmin.conf or any .htaccess in phpmyadmin directories to see if its being overriden. You can also check by creating a file in /var/www with <?php phpinfo(); ?> and seeing what the memory limit its reading from php.ini, that should help tell if phpmyadmin's setting is getting overriden.

---

### Post by xslumlordx on 2012-11-12
Note that there may also be a .htaccess file in the phpmyadmin filder that restricts the memory_limit to a different value than the server default values.

---

### Post by cariboo on 2012-11-12
Most of the answers given in this three year old thread, don't apply any more. Thread Closed.

---

