---
title: "problem with virtual host in nginx server"
date: 2011-03-01
forum: Server Platforms
---

### Post by equinox_ on 2011-03-01
So I have a info.php page which is located on the folder /var/www/nginx-default, however when I go to my ip address/info.php, it always redirects me to this site:

[http://www.iana.org/domains/example/](http://www.iana.org/domains/example/)

is this because I have a virtual host that I called example? Here is my config for the example website:



server {
     listen   80;
     server_name  [www.example.com;](www.example.com;)
     rewrite ^/(.*) http://example.com/$1 permanent;
     }

server {
     listen   80;
     server_name example.com;

     access_log /var/www/example.com/logs/access.log;
     error_log /var/www/example.com/logs/error.log;

     location / {
          root   /var/www/example.com/public/;
          index  index.html;
          }
}


As I don't have a domain name yet and I can only access the server via terminal. The way I access this site via browser is by changing my /etc/hosts in my macbook so that example.com is mapped to my server IP address. however now when I do xxx.xxx.xxx.xxx/info.php in my macbook browser it redirects me to that site I posted above, when I access example.com from my macbook it works just fine.

---

