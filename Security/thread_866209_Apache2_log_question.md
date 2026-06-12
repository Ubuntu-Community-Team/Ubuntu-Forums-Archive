---
title: "Apache2 log question"
date: 2008-07-21
forum: Security
---

### Post by champishere on 2008-07-21
I'm new to running a web server
I started this for practice purposes.

I recently notice this in my access log file

206.169.193.251 - - [16/Jul/2008:14:41:10 -0500] "GET [http://www.mit.edu/](http://www.mit.edu/) HTTP/1.1" 200 416

It's interesting to me because it resolved with 200 and not 404

When I tried this myself I received the expected results

192.168.1.100 - - [21/Jul/2008:11:19:54 -0500] "GET /http://www.mit.edu/ HTTP/1.1" 404 342

Does anyone know how this could have happen on my server,
or can anyone lead me to where I can read more information about how this happen.

Thanks in advance for all answers.

---

### Post by Dr Small on 2008-07-21
I had some strange things similar to that happen on my server. I never could figure out how they happened though.

---

### Post by cdenley on 2008-07-21
It looks like someone is trying to use your webserver as a proxy. You can configure firefox to use your server as a http proxy, but it will only serve your site.

Notice the difference between the two logged events. The proxy request begins with [http://.](http://.) Your request begins with /http://

---

### Post by champishere on 2008-07-21
Again thanks for the help.

It seems that if I add the following lines to my virtual host file it would stop this.

<Proxy *>
Order Deny,Allow
Deny from all
Allow from yournetwork.example.com
</Proxy> 

Also it seems that I may have to add the corresponding module.

this was copied from apache web site
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxy](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxy)

---

