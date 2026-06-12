---
title: "NGINX connect() to unix:/var/run/php5-fpm/forums.socket failed"
date: 2013-11-30
forum: Server Platforms
---

### Post by roo4.id on 2013-11-30
[COLOR=#000000]Hello;
I setup my nginx and php-fpm for separate sockets and I get :
```
[COLOR=#000000]2013/12/01 03:59:12 [crit] 1201#0: *5 connect() to unix:/var/run/php5-fpm/forums.socket failed (2: No such file or directory) while connecting to upstream, client: 173.245.53.199, server: forums.DOMAIN.DOM, request: "GET / HTTP/1.1", upstream: "fastcgi://unix:/var/run/php5-fpm/forums.socket:", host: "forums.DOMAIN.DOM", referrer: "http://forums.DOMAIN.DOM/"[/COLOR]
```
[LEFT][COLOR=#000000]the funny thing is that the directory mentioned in the error is there but php-fpm or nginx doesn't spawn the socket there.
A. nginx.conf:
[http://paste.ubuntu.com/6502039/](http://paste.ubuntu.com/6502039/)
B.  /etc/nginx/sites-available/forums
[http://paste.ubuntu.com/6502045/](http://paste.ubuntu.com/6502045/)
C.  /etc/nginx/fastcgi_params
[http://paste.ubuntu.com/6502055/](http://paste.ubuntu.com/6502055/)
D.  /etc/php5/fpm/pool.d/forums.conf
[http://paste.ubuntu.com/6502073/](http://paste.ubuntu.com/6502073/)[/COLOR][/LEFT][/COLOR]

---

