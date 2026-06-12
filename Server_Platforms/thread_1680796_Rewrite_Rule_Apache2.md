---
title: "Rewrite Rule Apache2"
date: 2011-02-03
forum: Server Platforms
---

### Post by daniele75 on 2011-02-03
Hello all, I need some help in writing a rewriterule in apache2, in ubuntu 10.04 server.

I need to append a path to all web request to our web server, for example, if link is

[http://myserver/ppp/](http://myserver/ppp/)
or
[http://myserver/](http://myserver/)
or
[http://myserver/index.html](http://myserver/index.html)

I need to rewrite always with

[http://myserver/proper-link/](http://myserver/proper-link/)

Only in the case

[http://myserver/ppp/USER](http://myserver/ppp/USER)

I need to rewrite to

[http://myserver/proper-link/USER](http://myserver/proper-link/USER)

Is it possible?

I've read apache2 manual but sintax is not clear for me...

Thanks
Daniele

---

### Post by daniele75 on 2011-02-03
I've solved with this configuration

       RewriteEngine On
       RewriteCond %{REQUEST_METHOD} ^TRACE
       RewriteRule .* - [F]
       RewriteRule    ^/$    /correct/Path/    [L,R]
       RewriteRule    ^/correct/path/([^/]+)    /correct/Path/$1 [L,R]
       RewriteRule    ^/correct/path    /correct/Path/    [L,R]

---

