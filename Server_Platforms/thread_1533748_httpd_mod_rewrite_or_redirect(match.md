---
title: "httpd mod_rewrite or redirect(match"
date: 2010-07-18
forum: Server Platforms
---

### Post by niklasro on 2010-07-18
:ohttpd rewrite or redirect to subdomain 
Posted by Niklas R
httpd rewrite or redirect to subdomain
How to achieve 
http://(www.)domain.com.br/vi/{N}.htm 
redirect or rewrite to 
http://web.domain.com.br/vi/{N}.htm 
? I try for very long time and not right effect ie

RedirectMatch permanent ^/vi/(.*)\.htm$ http://web.domain.com.br/vi/$1

---

### Post by niklasro on 2010-07-18
:oWith
RedirectMatch permanent ^/vi/(.*)$ http://web.domain.com.br/vi/$1

Approaching correct behavior
[http://domain.com.br/vi/abc](http://domain.com.br/vi/abc)
redirects to
[http://web.domain.com.br/vi/abc](http://web.domain.com.br/vi/abc)

It's this part that needs work
http://domain.com.br/vi/{N}.htm
redirects to
http://web.domain.com.br/vi/{N}.htm

where N is some database id
With thanks in advance for any advice, comment and discussion onwards;)

---

### Post by niklasro on 2010-07-18
Ie thing is escaping the dot. Some suggestions made from here that didn't make it all the way are
RedirectMatch permanent ^/anything/(.*)$ http://web.domain.com.br/$1

can't handle dot

RedirectMatch permanent ^/vi/(.*)$ http://web.domain.com.br/vi/$1

can't handle dot

RedirectMatch permanent ^/vi/(.*)\.htm$ http://web.domain.com.br/vi/$1

can't handle dot

RedirectMatch permanent ^/vi/([0-9]+)\.htm$ http://web.domain.com.br/vi/$1

can't handle dot

---

### Post by niklasro on 2010-07-21
Here's a forum thread where it still is none obvious way despite easily stated [http://forums.digitalpoint.com/showthread.php?t=1875706](http://forums.digitalpoint.com/showthread.php?t=1875706)

---

### Post by niklasro on 2010-09-11
This was solved at stackoverflow [http://stackoverflow.com/questions/3237061/how-mod-rewrite-can-add-subdomain](http://stackoverflow.com/questions/3237061/how-mod-rewrite-can-add-subdomain)

---

