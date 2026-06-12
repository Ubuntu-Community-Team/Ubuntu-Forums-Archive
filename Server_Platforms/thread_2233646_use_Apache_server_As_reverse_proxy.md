---
title: "use Apache server As reverse proxy"
date: 2014-07-09
forum: Server Platforms
---

### Post by jad102 on 2014-07-09
hello all,
actually I'm beginner to deal with Apache server , I have scenario as following:-
I have domain on (cpanel host server ) {e.g www.mydomain.com} in [www.mydomain.com]("http://www.mydomain.com") /abc the client type his query , this query w'll process on server {server A} for exapmle : [www.localhost:3030]("http://www.localhost:3030").
so I'll user Apache server to route the client request to {server A} in order to process it and return the answer.
[LIST=1]
[*]**how the request move from my public domain {[www.mydomain.com/abc]("http://www.mydomain.com/abc") } to my Apache server , what I must put?**
[*]**how must I configure httpd.conf to use apache server as reverse proxy.**
[/LIST]
thanks :):KS:KS:KS

---

### Post by SeijiSensei on 2014-07-10
As always, I would start by reading the official documentation: [http://httpd.apache.org/docs/current/mod/mod_proxy.html](http://httpd.apache.org/docs/current/mod/mod_proxy.html)

---

