---
title: "Expires or Cache-Control header"
date: 2011-12-06
forum: Server Platforms
---

### Post by createdcreature on 2011-12-06
Do you know how to fix this problem on the W3C MobileOK Validator?
Screenshot attached.

---

### Post by createdcreature on 2011-12-08
Basically, how would I get to set cache control headers in Apache 2.2? I have read up on this and don't understand a thing!

---

### Post by pholden on 2011-12-09
First search result from Google for "apache cache-control"; [http://www.websiteoptimization.com/speed/tweak/cache/](http://www.websiteoptimization.com/speed/tweak/cache/) ;)

---

### Post by createdcreature on 2011-12-10
So am I right in saying that I put this in the httpd.conf file and restart the web server?

```

LoadModule expires_module modules/mod_expires.so
LoadModule headers_module modules/mod_headers.so
LoadModule deflate_module modules/mod_deflate.so

```

---

### Post by createdcreature on 2011-12-12
Do I add it to .htaccess?:confused:

---

### Post by SeijiSensei on 2011-12-13
This looks promising: [http://www.geekwisdom.com/dyn/cache-control2](http://www.geekwisdom.com/dyn/cache-control2)

---

### Post by createdcreature on 2011-12-15
Works! Here is my sample .htaccess. It is called htaccess.txt for obvious reasons.

---

