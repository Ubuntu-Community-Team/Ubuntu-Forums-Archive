---
title: "nginx always redirects the page"
date: 2010-07-10
forum: Server Platforms
---

### Post by bvidinli on 2010-07-10
Hi,

i have a subdomain that is redirected to my server: server2.10tl.net

when I try to access the page [http://server2.10tl.net/mybb/create](http://server2.10tl.net/mybb/create) in the browser,
it always redirect me to [http://10tl.net/mybb/create](http://10tl.net/mybb/create)  (which is located on another server.. )

why this redirection happens?

I tried a few things before, about redirection, but currently, there isn't any directive about redirection (rewrite directive) in any nginx configs.

here is my vhost nginx config:


server {
listen 80 ;
server_name 10tl.net *.10tl.net;

access_log /var/www/vhosts/bvidinli/10tl.net/logs/access_log2 ;
error_log /var/www/vhosts/bvidinli/10tl.net/logs/error_log2 ;
access_log /var/log/apache_common_access_log;

location / {

root /var/www/vhosts/bvidinli/10tl.net/httpdocs;
index index.html index.htm index.php;
}

location ~ /\.ht {
deny all;
}

}




it seems as if like, nginx remembers the old rewrite directive and sends me to that url.
it is same when I try access [http://server2.10tl.net/mybb/xxx](http://server2.10tl.net/mybb/xxx) or any url that has mybb inside.
really strange for me.
i am new in nginx and want to use it.



i am almost sure that redirection occurs because of nginx, since the directory /var/www/vhosts/bvidinli/10tl.net/httpdocs does not contain any redirection code, only index.php that has not any redirection.

one more clue:
the redirection occurs only I enter no php file at end of url.
if I enter [http://server2.10tl.net/mybb/create/dene.php](http://server2.10tl.net/mybb/create/dene.php) for example (a file that has sample output), it shows it to me as expected..

the redirection occurs only when I try to access [http://server2.10tl.net/mybb/create](http://server2.10tl.net/mybb/create) without php filename at end.

---

