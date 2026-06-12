---
title: "apache mod_rewrite problem"
date: 2009-09-17
forum: Server Platforms
---

### Post by MAKAPOH on 2009-09-17
Hello!

I'm have apache2 with vhost_alias and rewrite modules
when in try to load [http://example.com/view/123](http://example.com/view/123) im have 404 error:
> The requested URL /var/www/example.com/html/view.php was not found on this server.

in error.log
> [error] [client 192.168.1.7] File does not exist: /var/www/example.com/html**/var**

.htaccess
> RewriteEngine on
Options +FollowSymlinks
RewriteRule ^(.*)view/([0-9]+)$ $1view.php?id=$2
RewriteRule ^(.*)view/([0-9]+)/$ $1view.php?id=$2


[http://example.com/view.php?id=123](http://example.com/view.php?id=123) works normally..

What's wrong?


**UPD:** RewriteBase / :)

---

