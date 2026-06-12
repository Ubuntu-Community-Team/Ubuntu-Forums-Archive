---
title: "php error message to file"
date: 2009-07-07
forum: Server Platforms
---

### Post by DoppyNL on 2009-07-07
Hi people,

I'm having difficulty getting PHP to store it's errormessages in a file.
I've succesfully configured apache and php, wich is running fine from the browser.

The problem is that PHP doesn't leave errormessage's anywhere in a logfile.
Since it is a semi-production-server i've configured PHP to not display any error messages in php.ini:
```
display_errors = Off
display_startup_errors = Off
log_errors = On
```

Since I want an error log per virtual host, I've configured a bit further in the configuration-file.

```
DocumentRoot /home/sites/whatever/www/
php_admin_value open_basedir /home/sites/whatever/
php_admin_value upload_tmp_dir /home/sites/whatever/tmp/
php_admin_value error_log /home/sites/whatever/logs/error-php
ErrorLog /home/sites/whatever/logs/error-apache
CustomLog /home/sites/whatever/logs/access combined
LogLevel warn
```

This results in apache running some code in this virtual host, but encountering a fatal error, probably due to a syntax error in a php-script.
But because PHP-errors don't come up anywhere, it's quite difficult to solve the error.

Apache only creates the files "access" and "error-apache", not "error-php".


**Question: How do I configure Apache/PHP so it saves the PHP-error-messages in a file?**
It's fine if this is also the apache-error-file.

please help [-o<

---

### Post by wojox on 2009-07-07
Look in /var/log/apaches/error.log that's were my error are thrown.

---

### Post by DoppyNL on 2009-07-07
> **wojox said:**
> Look in /var/log/apaches/error.log that's were my error are thrown.
There are some general error messages there not related to a virtual host or PHP.
Not the PHP-error message's I'm looking for.

Tnx for the suggestion, unfortunatly, not the answer.

---

### Post by wojox on 2009-07-07
put this under log_errors=on in php.ini and create the dir and file

 error_log = /var/logs/php/phperr.log

---

### Post by DoppyNL on 2009-07-07
Put this line in my php.ini:
```
error_log=/home/logs/php
```
created the file and restarted apache.
("log_errors" was allready on...)

no result.

on a side-note: that php-configuration-option was also set in each virtual host with a different filename, wich didn't work.

Tried also:
- making the file world-readable.
- removing the configuration-option in the virtual host.

---

### Post by DoppyNL on 2009-07-08
Have been playing a bit more with access rights to the different logfiles.
No result so far.

Is there an option in PHP that tells it to log it's errors to the error-log used by the virtual host in apache. ie: the apache-error-log. ?

---

### Post by DoppyNL on 2009-07-08
Allright, I got it fixed in the end!

Alltough I get the idea that PHP is not doing everything properly as it should...


Basicly I added the following line to my virtual host:
```
php_value error_reporting 2147483647
php_flag log_errors 1
```

error_reporting: allthough this is set to "E_ALL&E_STRICT" in the php.ini, it didn't seem to work. Setting the numerical value here worked...

I also added " around the filename where I want the log, that could also effect things...

---

