---
title: "Can i group apache VirtualHosts?"
date: 2008-08-10
forum: Server Platforms
---

### Post by djvishnu on 2008-08-10
Is it possible to define one configuration for several VirtualHosts?

I.e. using the same configuration for [www.domain.org](www.domain.org) and domain.org

---

### Post by mbeach on 2008-08-10
I think the **ServerAlias** directive will do what you are looking for
[http://httpd.apache.org/docs/2.0/mod/core.html](http://httpd.apache.org/docs/2.0/mod/core.html)

---

### Post by ikonia on 2008-08-10
serveralias work well, but be aware that they will all show the same physical site and log to the same place.

---

### Post by djvishnu on 2008-08-11
Thank you! This was exactly what i was looking for :)

---

### Post by djvishnu on 2008-08-29
Another challenge for you apache-guys:

I am trying to force users to use https. I am using the Redirect directive, which works great, however, i have to choose either [www.domain.com](www.domain.com) or domain.com when using ServerAlias.

I want this:
[http://domain.com](http://domain.com) -> [https://domain.com](https://domain.com) 
[http://www.domain.com](http://www.domain.com) -> [https://www.domain.com](https://www.domain.com) 

My current config:
```

<VirtualHost *:80>
   ...
  ServerName domain.com
  ServerAlias www.domain.com
  Redirect permanent / https://domain.com/
  ...
</VirtualHost>

```

Any ideas on how to achieve this while preserving [www.?](www.?)

---

### Post by MJN on 2008-08-29
You probably don't want to do that as, assuming both [https://www.domain.com](https://www.domain.com) and [https://domain.com](https://domain.com) both reside on the same server (and IP address) then you'll only have a single certificate for that site. This will only work if you have multiple subjects within the certificate (or a wildcard) which will push the price of that certificate up for little/no gain.
 
Why don't you standardise on either domain.com or [www.domain.com]("http://www.domain.com") and redirect one to the other? This will also help search engines correctly parse your site (Google, for example, frowns upon you using two names for the same site and may penalise your pagerank for attempted listing manipulation. They [recommend](http://www.mattcutts.com/blog/seo-advice-url-canonicalization) you redirect all name variations to a standard format using a 301 redirect.
 
Mathew

---

### Post by djvishnu on 2008-08-29
You are probably right, we just havent decided on www/not www yet. and yes the sites are on the same server, same docroot, same cert (multiple subjects).

Mostly i am curious if it is possible to do, some kind of condition-based redirect.

---

