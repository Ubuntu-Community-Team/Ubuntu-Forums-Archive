---
title: "Well here is a weird one."
date: 2013-04-12
forum: Server Platforms
---

### Post by danshea on 2013-04-12
I have my server running Ubuntu with Nginx, php5-fpm and mysql. I have uploaded a script to one of my sites and when I run the install.php, I get a blank page. I then uploaded a phpinfo.php and ran that and it came up. My error log shows ...

2013/04/12 12:20:47 [error] 17059#0: *2 FastCGI sent in stderr: "PHP message: PHP Fatal error:  session_start(): Failed to initialize storage module: memcache (path: /var/lib/php5) in /var/www/mysite/html/install/install.php on line 9" while reading response header from upstream, client: 192.168.1.1, server: mysite.com, request: "GET /install/install.php HTTP/1.1", upstream: "fastcgi://unix:/var/run/php5-fpm.sock:", host: "mysite.com"

so does this mean there is a memcache error? and if so, how would I fix this?

Thanks,
Dan

---

