---
title: "lighttpd with fcgi is slow"
date: 2010-07-19
forum: Server Platforms
---

### Post by DanielWaterworth on 2010-07-19
I'm trying to switch my server over to lighttpd + fcgi from apache + wsgi to lower the memory use. The problem is performance, according to YSlow, Apache is serving the dynamic content in 200ms, but lighttpd is taking 1700ms on zero load. It's noticeably slow. Is this common, how do I fix it? It's a Django app.

I'm sorry if this is the wrong place.

---

### Post by jpl888 on 2010-07-19
I don't know that much about the problem because I haven't used lighttpd for a number of months, however I would recommend checking that fast cgi is definitely working.

For the ultimate in small footprint speed I would recommend Nginx instead, although you may have trouble getting documentation and what not for it.

---

### Post by DanielWaterworth on 2010-07-19
Well, it works, it's serving the page. I'll try any server, but I've heard that lighttpd is fast, and I'd like to know what's going wrong in this case. I may well have the same problem in nginx.

---

### Post by jpl888 on 2010-07-19
So as I said checking that the fcgi module is definitely loaded and working is the first step.

---

### Post by DanielWaterworth on 2010-07-19
I'm not sure I understand. Surely, if the page is loading, albeit slowly, then the fastcgi module is loaded and working?

---

### Post by jpl888 on 2010-07-19
I could be making this up but I seem to remember that by default it just uses standard cgi and you have to jump through hoops to get fastcgi working (that was back in the day when I used Gentoo though) I would hope lighttpd comes better configured out of the box. I used to use Zabbix with it and it would take seconds to load the page without fastcgi.

---

### Post by DanielWaterworth on 2010-07-19
The way that it's configured at the minute, it's reading from a unix socket file, where the the file is created by a process independent of the server. mod_cgi isn't even being loaded, so I don't think this is the case.

---

### Post by jpl888 on 2010-07-19
What does ```
$ php-cgi -v
``` say?

---

### Post by DanielWaterworth on 2010-07-19
I don't have php installed, it's a Django Python app.

---

### Post by jpl888 on 2010-07-19
There doesn't seem to be that much information Googling unfortunately.

Perhaps [http://groups.google.com/group/django-users/msg/01ed0b339f41b5f7](http://groups.google.com/group/django-users/msg/01ed0b339f41b5f7) is what you are experiencing?

From some of the posts I've just read, if you want decent performance running Apache with WSGI or Nginx with it's own WSGI are the best bet.

If you don't want to try another solution perhaps the best way forward would be to install PHP-CGI and load another app on the web server to confirm everythings working on the Lighttpd side, then post to Django users.

Personally I would try alternative ways of achieving it before I go posting.

---

### Post by DanielWaterworth on 2010-07-19
Thanks for finding this. It seems that the Fastcgi adaptor is the bottleneck, although I haven't tested the speed of apache with fastcgi yet. In which case, using nginx with wsgi would seem like the fastest and the least memory consuming solution. I shall try it out and post back here with the results. Thanks again.

edit: I've setup cherokee and uwsgi on my laptop to try it out. It's running just as fast as apache, but using much less memory. I decided not to try nginx as I read raving reviews of cherokee and they are justified.

---

