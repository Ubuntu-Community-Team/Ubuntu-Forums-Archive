---
title: "Apache 2 mod_headers won't rewrite my Server header"
date: 2008-08-13
forum: Server Platforms
---

### Post by theyranos on 2008-08-13
Snort repeatedly warns me that Apache is sending invalid headers to people (IPs masked for privacy reasons):
```

Events from same host to same destination using same method
=========================================================================
 # of  from             to               method
=========================================================================
    9  10.212.1.13      *xx.xxx.xx.xx*     WEB-MISC Invalid HTTP Version String
    5  10.212.1.13      *xx.xxx.xx.xx*     WEB-MISC Invalid HTTP Version String
    4  10.212.1.13      *xx.xxx.xx.xx*     WEB-MISC Invalid HTTP Version String
    4  10.212.1.13      *xx.xxx.xx.xx*     WEB-MISC Invalid HTTP Version String
    4  10.212.1.13      *xx.xxx.xx.xx*     WEB-MISC Invalid HTTP Version String

```

Here's the typical header that gets sent (provided by **curl -I localhost**).

```

HTTP/1.1 200 OK
Date: Wed, 13 Aug 2008 13:51:42 GMT
Server: Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_fastcgi/2.4.6 mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24) mod_ssl/2.2.8 OpenSSL/0.9.8g
Content-Type: text/html

```

If you try to view a page on this server with Konqueror, Konqueror treats the page as a text file consisting of the second half of the Server: line.

Even if **Server:** isn't my problem, I'd like to remove it, since it makes it glaringly obvious to potential attackers exactly what software I'm running. After searching, I found [this page](http://www.securesauce.com/?p=5), which suggested that I could use the headers module to remove the Server header entirely with

```

Header unset Server

```

in my **apache2.conf**, but unfortunately, this does absolutely nothing. Setting ServerSignature to Prod helps a little: ```
HTTP/1.1 200 OK
Date: Wed, 13 Aug 2008 14:17:07 GMT
Server: Apache
Content-Type: text/html

```
but I'm curious: As this is apache 2.2.8, does anybody know why **Header unset Server** didn't work?

*Edit: Wow. That was a really rambling way to ask that question. Sorry.*

---

### Post by theyranos on 2008-08-15
As it turns out, the IP addresses I masked out were all Canonical mirrors, and the events were actually coming from **apt**, not apache. 

More detail: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/258155](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/258155)

---

