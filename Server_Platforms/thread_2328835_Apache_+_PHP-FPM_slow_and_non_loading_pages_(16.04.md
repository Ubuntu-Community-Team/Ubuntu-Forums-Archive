---
title: "Apache + PHP-FPM slow and non loading pages (16.04)"
date: 2016-06-24
forum: Server Platforms
---

### Post by gijs007 on 2016-06-24
I've setup Apache with PHP 7-fpm and fastcgi.
Most of the php pages load normally, but a few of the Joomla 3.5 Admin pages load really slowly or timeout. 

The Apache error log shows: 
```
[Fri May 06 20:44:20.789615 2016] [fastcgi:error] [pid 6063:tid  139747715245824] [client 5.199.157.1:61446] FastCGI: comm with server  "/usr/lib/cgi-bin/php7.0" aborted: idle timeout (30 sec), referer:  https://www.xgclan.com/administrator/index.php 
[Fri May 06 20:44:20.789671 2016] [fastcgi:error] [pid 6063:tid  139747715245824] [client 5.199.157.1:61446] FastCGI: incomplete headers  (0 bytes) received from server "/usr/lib/cgi-bin/php7.0", referer:  https://www.xgclan.com/administrator/index.php
```

But I don't get any errors elsewhere, despite all PHP log options being turned on:
```
error_reporting = E_ALL 
display_errors = On 
display_startup_errors = On 
log_errors = On 
log_errors_max_len = 0 
ignore_repeated_errors = Off 
ignore_repeated_source = Off 
report_memleaks = On 
track_errors = On 
html_errors = On 
error_log = /var/log/php_errors.log
```

My mod fastcgi settings are as follow:

```
<IfModule mod_fastcgi.c> 
 AddType application/x-httpd-fastphp7.0 .php 
 Action application/x-httpd-fastphp7.0 /php7.0-fcgi 
 Alias /php7.0-fcgi /usr/lib/cgi-bin/php7.0 
 FastCgiExternalServer /usr/lib/cgi-bin/php7.0 -socket /var/run/php/php7.0-fpm.sock -pass-header Authorization 
 <Directory /usr/lib/cgi-bin> 
  Require all granted 
 </Directory> 
</IfModule>
```

I'm not sure what the problem is and already asked around on the Apachelounge forum([https://www.apachelounge.com/viewtopic.php?p=33373#33373](https://www.apachelounge.com/viewtopic.php?p=33373#33373)), but so far with no luck :(
They only suggested using fcgid instead of fastcgi, but fcgid doesn't support PHP-FPM as far as I know.

---

### Post by Graham_Willis on 2016-07-01
Are you sure that the the cause of the problem is the configuration of the server? It is quite possible that this is something wrong with these sites themselves. Try to compare them against other Joomla sites running on your machine and see what the differences are. Try to disable all plugins, extensions which are not turned off by default. It'll really help to isolate the problem. Please tell us about the results of the aforementioned tests - it's possible that with more specific information we'll be able to provide better help.

---

