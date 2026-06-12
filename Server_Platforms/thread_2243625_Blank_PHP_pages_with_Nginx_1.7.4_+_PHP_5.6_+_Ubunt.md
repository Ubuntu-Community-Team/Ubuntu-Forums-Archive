---
title: "Blank PHP pages with Nginx 1.7.4 + PHP 5.6 + Ubuntu 14.04?"
date: 2014-09-10
forum: Server Platforms
---

### Post by Eventum on 2014-09-10
I'm running Ubuntu 14.04 with nginx 1.7.4 (ppa:nginx/development) and PHP 5.6 (ppa:ondrej/php5-5.6).

Everything was working just fine with nginx 1.7.1 but when I upgraded to 1.7.4 every single PHP page is blank, even phpinfo.

I tried rebuilding my VPS and starting over from scratch but no matter what I did I still get a blank page with 1.7.4.

As soon as I revert to nginx 1.7.1 or the latest build available with the default Ubuntu LTS 14.04 repository there's no problem.

Has anyone else experienced this with 1.7.4-1+trusty? What might be the cause? Could there be a problem with the trusty build? 

Here is the very basic config I'm testing with:

```
server {
listen 80 default_server;
listen [::]:80 default_server ipv6only=on;

root /var/www/domain.com;
index index.php index.html index.htm;

server_name domain.com;

location / {
try_files $uri $uri/ =404;
}

error_page 404 /404.html;
error_page 500 502 503 504 /50x.html;
location = /50x.html {
root /usr/share/nginx/html;
}

location ~ \.php$ {
try_files $uri =404;
fastcgi_split_path_info ^(.+\.php)(/.+)$;
fastcgi_pass unix:/var/run/php5-fpm.sock;
fastcgi_index index.php;
include fastcgi_params;
}
}
```

---

### Post by SeijiSensei on 2014-09-10
What do the logs report?

---

### Post by Eventum on 2014-09-10
Thanks for the reply! 

I'll try again and investigate the log files further. Was interested to know if anyone else had tried my setup with any success. 

Funny thing is I couldn't find anything strange at first glimpse. PHP5 error log didn't reveal anything at all nor did the ningx error log. It was as if the requests never got passed over to PHP5-FPM.

What other log files do you suggest I check?

---

### Post by SeijiSensei on 2014-09-10
I use Apache, not nginx.  It's configured to send all PHP errors to error.log.  I'd imagine nginx is the same.

If you get an entirely blank page, it's usually because PHP cannot find some include files.  The other possibility might be an error which causes the nginx listener to crash, but that's not very likely.  What happens if you just create a test file, say info.php, with the contents
```
<?php phpinfo() ?>
```
and put it in the website root.  Either you'll see PHP's complete self-report, or the contents of the file itself.

---

### Post by pieman131 on 2014-09-10
I seem to have the same issue. Even a phpinfo page is blank. Accessing an affected page gives no error in nginx's error.log. The php-fpm log has:

 WARNING: [pool www] child 5623 exited with code 1 after 67.126934 seconds from start

There are quite a few of these warnings

---

### Post by pieman131 on 2014-09-10
Changed my nginx config php location section to this and now it's fixed. not sure which line fixed it but this works.

  location ~ ^(.+?\.php)(/.*)?$ {
                try_files $1 = 404;
                include fastcgi_params;
                fastcgi_param SCRIPT_FILENAME $document_root$1;
                fastcgi_param PATH_INFO $2;
                fastcgi_param HTTPS on;
                fastcgi_pass 127.0.0.1:9000;
        }

---

### Post by pieman131 on 2014-09-10
sorry ment to say my vhost config not my nginx config

>   location ~ ^(.+?\.php)(/.*)?$ {                try_files $1 = 404;


                include fastcgi_params;
                fastcgi_param SCRIPT_FILENAME $document_root$1;
                fastcgi_param PATH_INFO $2;
                fastcgi_param HTTPS on;
                fastcgi_pass 127.0.0.1:9000;
                # Or use unix-socket with 'fastcgi_pass unix:/var/run/php5-fpm.$
        }

---

### Post by Eventum on 2014-09-11
> **pieman131 said:**
> Changed my nginx config php location section to this and now it's fixed. not sure which line fixed it but this works. 

  location ~ ^(.+?\.php)(/.*)?$ {
                try_files $1 = 404;
                include fastcgi_params;
                fastcgi_param SCRIPT_FILENAME $document_root$1;
                fastcgi_param PATH_INFO $2;
                fastcgi_param HTTPS on;
                fastcgi_pass 127.0.0.1:9000;
        }

Much obliged! Interesting to see that whatever changed in nginx 1.7.4 seems to be affecting others also. 

I noticed that you switched from sockets to TCP/IP (fastcgi_pass 127.0.0.1:9000). I'm not sure that I can do that as my php5-fpm is configured with this line: listen = /var/run/php5-fpm.sock. As I understand it Ubuntu 14.04+PHP 5.6 uses sockets by default. 

Can you paste your previous configuration?

---

