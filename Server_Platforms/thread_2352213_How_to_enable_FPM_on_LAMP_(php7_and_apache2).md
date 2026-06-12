---
title: "How to enable FPM on LAMP (php7 and apache2)?"
date: 2017-02-10
forum: Server Platforms
---

### Post by spectatorx on 2017-02-10
I'm trying to enable FPM on my LAMP installation (php v7.1.1 and apache 2.4.25), most instructions i was able to find are made for php5 and rely on tcp instead on socket. I've tried some of them with replacing all "5"s in them to "7.1"s or "7"s with no success, after apache2 restart phpinfo() still shows:I 
```
Server API
Apache 2.0 Handler
```


I have installed php7-fpm and libapache2-mod-fastcgi and few other required components but still, no success. Any ideas how to make fpm work?

Ubuntu 16.10 budgie remix amd64.

---

