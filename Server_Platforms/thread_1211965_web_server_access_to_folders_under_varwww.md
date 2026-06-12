---
title: "web server access to folders under /var/www"
date: 2009-07-13
forum: Server Platforms
---

### Post by torfosnaes on 2009-07-13
ubuntu 9.04 server set up works fine.

two items need attention
1. users from outside the router can't get an html link on path /var/www/etc/etc/etc.html; error 404 returns from link on index.htm at /var/www; samba share turned on /etc folder
2. procedure to password protect one html file on /var/www using .htaccess and .htpasswd fails every configuration of those two files; Allow All in httpd.conf doesn't work; how many more places should the allow code appear?

Is there any easy configuration for these two problems or are the solutions only arcane and esoteric?

Any help appreciated <tor@mobilewords.ca>

---

