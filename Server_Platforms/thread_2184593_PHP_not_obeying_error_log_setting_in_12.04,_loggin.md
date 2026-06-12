---
title: "PHP not obeying error_log setting in 12.04, logging to Apache error log instead"
date: 2013-10-29
forum: Server Platforms
---

### Post by mdlueck on 2013-10-29
I bumped into an odd thing with the PHP that ships in Ubuntu Server 12.04.

Previously I had found that PHP will dump errors to the remote web browser, which I reconfigured to log to the server instead. In Apache's .htaccess for a VirtualSite, I set PHP to write error_log thusly:

```
# .htaccess

# PHP 5, Apache 1 and 2.
<IfModule mod_php5.c>
  #Adjusted error handling per http://www.cyberciti.biz/tips/php-howto-turn-on-error-log-file.html
  #And also https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/512167  #3 comment
  php_value display_errors                  Off
  php_value error_log                       /var/log/php5/serverhostname.php_error.log
  php_value log_errors                      On
</IfModule>

```

Like I said, the errors end up in the Apache VirtualSite error log file, not the one I custom specify in the .htaccess file.

Other settings are within this IfModule block and are set correctly when reviewing phpinfo, so I know the IfModule was traversed successfully.

Suggestions as to what happened in the PHP version that ships with Ubuntu 12.04? TIA!

---

### Post by SeijiSensei on 2013-11-01
By default, .htaccess is disabled in 12.04.  In /etc/apache2/sites-available/default, replace "AllowOverride None" with "AllowOverride All" and restart Apache.

Also, the standard keyword for binary switches is "php_flag" while "php_value" is used for strings.  Try changing the directive to php_flag for "display_errors" and "log_errors".

---

### Post by mdlueck on 2013-11-01
> **SeijiSensei said:**
> By default, .htaccess is disabled in 12.04.

Good suggestion, SeijiSensei.

I actually transfered the Apache configs from the prior server, so indeed have:

```
	<Directory />
		Options FollowSymLinks -MultiViews
		**AllowOverride All**
	</Directory>

```

in the configuration already.

Like I said, I am sure that the <IfModule mod_php5.c> block is being traversed as other settings show up as customized in phpinfo.

I suspect that between 10.04 and 12.04, a change was made to Hardened PHP that errors get logged to the Apache Error log... I just would feel more comfortable with some documentation to back up the suspected change.

---

### Post by mdlueck on 2013-11-01
> **SeijiSensei said:**
> Also, the standard keyword for binary switches is "php_flag" while "php_value" is used for strings.  Try changing the directive to php_flag for "display_errors" and "log_errors".

Oops, I forgot to test this one...

```
<IfModule mod_php5.c>
  #Adjusted error handling per http://www.cyberciti.biz/tips/php-howto-turn-on-error-log-file.html
  #And also https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/512167  #3 comment
  **php_flag** display_errors                   Off
  #Now these PHP errors get logged automatically to the Apache error log
  php_value error_log                       /var/log/php5/cirweb01.php_error.log
  **php_flag** log_errors                       On
</IfModule>

```

Restarted the Apache service. Still same behavior... logs to the Apache error log for the virtual site.

Thank you for pointing out the subtle difference! :-)

---

### Post by SeijiSensei on 2013-11-01
I have no idea what "Hardened PHP" is, but it sounds like it doesn't obey the defaults.

What appears in /etc/php5/apache2/php.ini and /etc/php5/apache/conf.d/?  These files control the default PHP configuration.

---

### Post by mdlueck on 2013-11-01
> **SeijiSensei said:**
> I have no idea what "Hardened PHP" is, but it sounds like it doesn't obey the defaults.

Just the standard PHP being distributed by Ubuntu... PHPInfo includes this banner text:

> This server is protected with the Suhosin Patch 0.9.10
Copyright (c) 2006-2007 **Hardened-PHP Project** Copyright (c) 2007-2009 SektionEins GmbH


> **SeijiSensei said:**
> What appears in /etc/php5/apache2/php.ini

I have made no changes to that master file, so that is default as comes with Ubuntu 12.04. Rather lengthy, so not posting the entire file.

 > **SeijiSensei said:**
> and /etc/php5/apache/conf.d/?  These files control the default PHP configuration.

Defaults here as well:

$ ls -al /etc/php5/apache2/conf.d
lrwxrwxrwx 1 root root 9 Sep  4 16:14 /etc/php5/apache2/conf.d -> ../conf.d

$ ls -al /etc/php5/conf.d/
total 28
drwxr-xr-x 2 root root  121 Oct 29 16:05 .
drwxr-xr-x 5 root root   43 Oct 29 15:56 ..
-rw-r--r-- 1 root root   50 Sep  4 16:14 gd.ini
-rw-r--r-- 1 root root   58 Feb 22  2011 mcrypt.ini
-rw-r--r-- 1 root root   57 Sep  4 16:14 mysqli.ini
-rw-r--r-- 1 root root   56 Sep  4 16:14 mysql.ini
-rw-r--r-- 1 root root   52 Sep  4 16:14 pdo.ini
-rw-r--r-- 1 root root   60 Sep  4 16:14 pdo_mysql.ini
-rw-r--r-- 1 root root 3399 Feb 11  2012 suhosin.ini

I prefer, since servers are multi-site, to make specific changes needed in each virtual site and leave the distro defaults alone. YMMV.

---

