---
title: "Downgrade php ubuntu 10.04"
date: 2010-09-09
forum: Server Platforms
---

### Post by richbate on 2010-09-09
Hello all, 

I've been in a bit of a pickle for a few days now. 

in short, my server went down and I was a bit too keen with the upgrades. 
I updated to Ubuntu 10.04 without knowing the consequences. I'll never do that again. 

I've been trying to downgrade php form 5.3.2 to 5.2.10
I've found some great resources if other users find are having the same problem. 

[http://2bits.com/drupal-planet/various-ways-running-php-52-ubuntu-1004-lucid-lynx.html](http://2bits.com/drupal-planet/various-ways-running-php-52-ubuntu-1004-lucid-lynx.html)
[http://thejibe.com/blog/10/5/php-5210-debs-ubuntu-104-lucid](http://thejibe.com/blog/10/5/php-5210-debs-ubuntu-104-lucid)

I've followed these instructions, but am still getting errors. 

php -v give the following errors. 


richbate@dmwebsvr:~$ php -v
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/imagick.so' - /usr/lib/php5/20060613+lfs/imagick.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/imap.so' - /usr/lib/php5/20060613+lfs/imap.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/ldap.so' - /usr/lib/php5/20060613+lfs/ldap.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/ming.so' - /usr/lib/php5/20060613+lfs/ming.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pspell.so' - /usr/lib/php5/20060613+lfs/pspell.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/recode.so' - /usr/lib/php5/20060613+lfs/recode.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/snmp.so' - /usr/lib/php5/20060613+lfs/snmp.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite3.so' - /usr/lib/php5/20060613+lfs/sqlite3.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/tidy.so' - /usr/lib/php5/20060613+lfs/tidy.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP 5.2.10-2ubuntu6.5 with Suhosin-Patch 0.9.7 (cli) (built: May 21 2010 05:51:15) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2009 Zend Technologies


I know this is my own stupid fault for being too quick on the update, so keep the teasing to a minimum please :)

many thanks

---

### Post by Kelly Bell on 2010-11-18
I am having a similar problem. I had to re-install php5.2 on my 8.04 Ubuntu server because it was missing several critical libraries I was missing for Drupal. Everything works okay on the surface, but I have these underlying errors, and I really want my system to be clean. Errors are the similar to above. If I run a status command, for instance, I get:

> PHP Warning:  Module 'mcrypt' already loaded in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613/pdo_sqlite.so' - /usr/lib/php5/20060613/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613/sqlite.so' - /usr/lib/php5/20060613/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP 5.2.14-0.dotdeb.0 with Suhosin-Patch 0.9.7 (cli) (built: Jul 24 2010 17:09:50) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2010 Zend Technologies
    with Suhosin v0.9.32.1, Copyright (c) 2007-2010, by SektionEins GmbH
Does anyone have any advice on how I can get these errors fixed, or point me in the right direction?

Thanks,
Kelly

---

### Post by hobbestec on 2010-11-18
You just need to turn off the display_errors variable.  Edit the php.ini file from /etc/php5/apache2/php.ini and around line 531 of the file you can change display_errors to Off

display_errors = Off

Then restart the apache server and it should take effect.

---

### Post by Kelly Bell on 2010-11-18
I don't mean to be an idiot, but I want to *fix* the root causes of these warnings, not hide them so I don't have to look at them. :-)

Thoughts?

---

