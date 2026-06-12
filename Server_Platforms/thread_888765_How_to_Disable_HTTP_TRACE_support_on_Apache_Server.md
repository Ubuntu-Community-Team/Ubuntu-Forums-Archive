---
title: "How to Disable HTTP TRACE support on Apache Server"
date: 2008-08-13
forum: Server Platforms
---

### Post by haryoh on 2008-08-13
I was reading an article about http header trace whereby attackers can use that to get cookies, and other information they might need to attack your server. 

The Tutorial will be short on how to disable the process on Apache Server. I hope it helps the newbies.

The HTTP TRACE method returns the contents of client HTTP requests in the entity-body of the TRACE response.

to Disable this in Apache Server do this:
Apache HTTP Server

[PHP] RewriteEngine On
      RewriteCond %{REQUEST_METHOD} ^TRACE
      RewriteRule .* - [F][/PHP]

---

### Post by StickyStyle on 2008-08-13
[http://ubuntuforums.org/showthread.php?t=879378#2](http://ubuntuforums.org/showthread.php?t=879378#2)

---

