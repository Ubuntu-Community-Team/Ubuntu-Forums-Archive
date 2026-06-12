---
title: "Multiple php.ini files"
date: 2010-07-19
forum: Server Platforms
---

### Post by timothy_tim on 2010-07-19
I would like to have multiple php.ini files for multiple sites.

I've a production site (word wide available) and a test site (available to some selected IP-addresses).  I would like to set some different PHP settings for the test site, for example, 'error_reporting' and 'display_errors'.

Is this possible? I'm not looking for some CGI hack, unless it wouldn't work any other way.

---

### Post by zabuch on 2010-07-19
You can use ini_set() function in your PHP application to change many of the configuration variables (you can't change all of them). 
You can also change the configuration (again, some restrictions apply) in your Apache configuration file per vhost or per-directory. You can also do it in .htaccess file using [FONT=Courier New]php_value[/FONT] and [FONT=Courier New]php_flag[/FONT], see [http://php.net/manual/en/configuration.changes.php](http://php.net/manual/en/configuration.changes.php)

---

### Post by timothy_tim on 2010-07-26
Thanks, I've added some '[FONT=Times New Roman]php_value[/FONT]' to a site at 'sites-available/'.
That fits well.

---

