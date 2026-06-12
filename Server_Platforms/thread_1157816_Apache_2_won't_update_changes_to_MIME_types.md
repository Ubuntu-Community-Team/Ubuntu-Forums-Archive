---
title: "Apache 2 won't update changes to MIME types"
date: 2009-05-13
forum: Server Platforms
---

### Post by tom_soderlund on 2009-05-13
I have problems with MIME types on my Apache 2 server (Apache/2.2.8, on Ubuntu 8.04.1). I have a Ruby on Rails (Mongrel) site with Apache 2 as web server.

Specifically, I want to add MIME support for mobile JAD/JAR files. These file types were already included in the file **/etc/mime.types** on my Ubuntu server:
```
text/vnd.sun.j2me.app-descriptor        jad
application/java-archive            jar
```So, I added a line to **/etc/apache2/apache2.conf**:
```
TypesConfig /etc/mime.types
```I also checked that the **mime mod** was in use.

And restarted my server:
```
/etc/init.d/apache2 reload
```But still, the website reports the JAD file to be a **application/octet-stream** type file.

What to do?

---

### Post by tom_soderlund on 2009-05-14
It seems the problem is not related to Apache, but that Mongrel/Rails picks up the request instead. Hmm....

---

### Post by tom_soderlund on 2009-05-14
Solved it, finally!

Had to add these lines to my site configuration file (sites-available/mysite):
```
ProxyPass /images !
Alias /images /MY-RAILS-SITE-FOLDER/public/images
```(Note: must be _before_ the existing ProxyPass statements)

and similar for stylesheets, my JAD/JAR files etc.


Tom.

---

