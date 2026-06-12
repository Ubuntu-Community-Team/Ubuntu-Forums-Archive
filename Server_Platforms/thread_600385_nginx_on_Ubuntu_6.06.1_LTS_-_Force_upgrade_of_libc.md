---
title: "nginx on Ubuntu 6.06.1 LTS - Force upgrade of libc6 and libssl?"
date: 2007-11-02
forum: Server Platforms
---

### Post by YorYor on 2007-11-02
I was thinking of trying out nginx on my 6.06.1 server alongside Apache to compare the speed and memory usage.

But after downloading the .deb file and trying to install it, the following was output:

```

Selecting previously deselected package nginx.
(Reading database ... 61611 files and directories currently installed.)
Unpacking nginx (from nginx_0.6.13~grrr-1_i386.deb) ...
dpkg: dependency problems prevent configuration of nginx:
 nginx depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 nginx depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7ubuntu0.5.
dpkg: error processing nginx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nginx
```

Ok I concede this deb file was meant for 7.04.

Thus, my question: **can I set the sources list to use 7.04's respositories and upgrade only libc6 and libssl?**

---

### Post by MJN on 2007-11-02
Unlikely... because those newer packages will likely in turn depend on other newer packages/libraries and before you know it you'll have some sort of 6.06/7.04 hybrid install which is simply asking for trouble.
 
Mathew

---

### Post by YorYor on 2007-11-02
Ah... ok thanks!
Guess I'll have to make a spare machine appear out of nowhere and give it a shot myself.

---

### Post by hasimir44 on 2008-01-06
for anyone else (like me) who finds this and is wanting to install nginx to edgy, follow these two articles:

installation: 
[http://articles.slicehost.com/2007/10/16/ubuntu-lts-installing-nginx](http://articles.slicehost.com/2007/10/16/ubuntu-lts-installing-nginx)

setting up in runlevels: 
[http://articles.slicehost.com/2007/10/17/ubuntu-lts-adding-an-nginx-init-script](http://articles.slicehost.com/2007/10/17/ubuntu-lts-adding-an-nginx-init-script)

they worked for me.

---

