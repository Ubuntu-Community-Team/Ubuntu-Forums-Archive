---
title: "Install webserver (nginx, php, mysql, phpmyadmin) on ubuntu 11.04"
date: 2012-01-17
forum: Server Platforms
---

### Post by richskrenta on 2012-01-17
[SIZE=2]hi all

I just use this os (ubuntu) for 2 days, I want to setup my own web  server to create website project in localhost but i want to use nginx  instead of apache.[/SIZE] [SIZE=2]

I've learn how to install : nginx, php, and mysql with using terminal (apt-get) then it's root location is.[/SIZE] [SIZE=2]

> /usr/share/nginx/www
                         
But i found a problem when I trying to install and configure  phpmyadmin, I can't find any site that give me complete reference or  guide to do it. Sound it's very simple task but not for me since I just  use this ubuntu for 2 days, no more.

If you can give me an explanation I will very thank to you.[/SIZE]

---

### Post by sgtGarcia on 2012-01-21
Hmm.. I'm in the same situation. I could get to phpmyadmin login site, but after typing name & password ( doesn't matter if it was good or wrong ) it gave Me error 500 & in logs I've seen
```
 "GET /index.php?token=7f5fb0bb2629115d733deb1097f9a475 HTTP/1.1" 404 31
```

Now I'm trying to install it with help of:
[endofweb.co.uk/2010/10/ubuntu-vps-nginx-mysql-php-fpm-phpmyadmin-wordpress/]("endofweb.co.uk/2010/10/ubuntu-vps-nginx-mysql-php-fpm-phpmyadmin-wordpress/")

But what I need more is connecting through unix socket instead port (heard it is faster & better :) ).
Second - I need to have phpmyadmin access like domain.com/phpmyadmin not phpmyadmin.domain.com

Can someone help?

---

