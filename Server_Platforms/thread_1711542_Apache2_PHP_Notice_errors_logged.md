---
title: "Apache2 PHP Notice errors logged"
date: 2011-03-21
forum: Server Platforms
---

### Post by Juddling on 2011-03-21
My /var/log/apache2/error.log is filling up about 1GB per hour with PHP Notice errors.

I've tried adding this: /apache2.conf

php_value error_log none
And in my /cgi/php.ini:

error_reporting = E_ERROR
display_errors = On
display_startup_errors = Off
log_errors = Off

PHP is running through fcgi. Even though display errors is ON, it is NOT displaying errors. 

Also when i check PHP info, I get this:
display_errors	Off	Off
display_startup_errors	Off	Off
error_reporting	22527	22527

Is there a seperate config file I should be editting?

OS: Ubuntu Linux 10.04 PHP: 5.3.2 Apache: 2.2.14

---

### Post by Juddling on 2011-06-22
bump

---

### Post by ruffEdgz on 2011-06-22
Just have some questions about this:
[list]
[*]What is your current 'LogLevel' set to in ./apache2.conf?
[*]Change anything in your ./mods-available/php.conf?
[*]What is the 'php notice' that is being placed into the error.log file?
[*]Anything in your ./conf.d/ that places error logs into /var/log/apache2/error.log?
[*]After making your changes from the first post, did you restart (I just want to make sure I know what you did)?
[/list]
Just because its a PHP notification doesn't mean php is producing it.

Cheers!

---

