---
title: "Bug? Apache/php5-fpm returns 500 error over ssl, 200 over http when connection lost"
date: 2015-05-11
forum: Server Platforms
---

### Post by rocky10 on 2015-05-11
I'm having a really strange issue that only started when I changed my site to use SSL.  Basically, If I disconnect from apache during a request originating from the server when using https it throws a 500 error, if I do it over http it just returns 200.  I've tried this using the apache php module (not fpm) and it doesn't have the problem.  It also doesn't happen if I access the server remotely.  It only happens making the request **on** the server.  There are multiple sites on the server so it is using SNI. The page loads fine if it is not interrupted.

To recreate:

Put this script on the server (it just sleeps for two seconds so you have a chance to interrupt it):
delay.php:
[PHP]<?php
sleep(2);[/PHP]

Now, do a curl or wget request of that file **on the server**, and interrupt it before the two seconds by pressing Ctrl+C.
> curl [http://](http://)[site]/delay.php
^C


Check apache log:
> "GET /delay.php HTTP/1.1" 200 163 "-" "curl/7.35.0"

Note the 200 response.

Now try with https (again interrupt before the two seconds by pressing Ctrl+C):
> curl [https://](https://)[site]/delay.php
^C


Check apache log again:
> "GET /delay.php HTTP/1.1" 500 5064 "-" "curl/7.35.0"

*edit*
The error log contains:
> AH00524: Handler for fastcgi-script returned invalid result code 32


Note it now responds with a 500 internal server error.  If I don't interrupt the request it completes successfully and returns a 200 response.

I'm using the latest packages in Ubuntu Server 14.04.2 LTS:
Apache/2.4.7 (Ubuntu)
PHP 5.5.9-1ubuntu4.9 (fpm-fcgi) (built: Apr 17 2015 11:44:58)

Apache config for php5-fpm:
> <IfModule mod_fastcgi.c>
    AddHandler php5-fcgi .php
    Action php5-fcgi /php5-fcgi
    Alias /php5-fcgi /usr/lib/cgi-bin/php5-fcgi
    FastCgiExternalServer /usr/lib/cgi-bin/php5-fcgi -idle-timeout 600 -flush -host 127.0.0.1:9000 -pass-header Authorization
</IfModule>


Anyone have any ideas?

I originally noticed this on a WordPress site because wp-cron was throwing seemingly random 500 errors after I upgraded to SSL.  It turned out it was only happening when wp-cron uses curl with a very small timeout and the cron script takes longer than the timeout to run.  Here is a wordpress forum thread about the issue: [http://wordpress.org/support/topic/wp-cron-throwing-500-errors-on-ssl-sites](http://wordpress.org/support/topic/wp-cron-throwing-500-errors-on-ssl-sites)

---

