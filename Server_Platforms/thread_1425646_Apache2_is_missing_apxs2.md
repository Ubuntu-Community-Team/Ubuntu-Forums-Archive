---
title: "Apache2 is missing apxs2"
date: 2010-03-09
forum: Server Platforms
---

### Post by scottrcaldwell on 2010-03-09
I'm configuring an Ubuntu server that's running x64 9.1. I installed the LAMP stack during the os installation and now I need to build an apache2 module. It appears as though apxs is missing. I've installed apache2-threaded-dev but am still missing apxs2.

Any help would be appreciated.

Thanks,

Scott

---

### Post by Ilalmi on 2010-03-09
Hi,

could you run a ```
dpkg -l |grep apache2
``` and give us the output?

Thanks

---

### Post by scottrcaldwell on 2010-03-09
Thanks for the help. Here's is the output you asked for.

ii  apache2                              2.2.12-1ubuntu2.1                          Apache HTTP Server metapackage
ii  apache2-mpm-prefork                  2.2.12-1ubuntu2.1                          Apache HTTP Server - traditional non-threade
ii  apache2-threaded-dev                 2.2.12-1ubuntu2.1                          Apache development headers - threaded MPM
ii  apache2-utils                        2.2.12-1ubuntu2.1                          utility programs for webservers
ii  apache2.2-bin                        2.2.12-1ubuntu2.1                          Apache HTTP Server common binary files
ii  apache2.2-common                     2.2.12-1ubuntu2.1                          Apache HTTP Server common files
ii  libapache2-mod-php5                  5.2.10.dfsg.1-2ubuntu6.4                   server-side, HTML-embedded scripting languag

Thanks,

Scott

---

### Post by Ilalmi on 2010-03-09
You're welcome :-)

As you have installed the [non-threaded-MPM-apache (prefork)]("http://httpd.apache.org/docs/2.0/en/mod/prefork.html"), the apxs you need is part of the apache2-prefork-dev package, not of apache2-threaded-dev. 
apache2-threaded-dev is for the apache running with a [multi-threaded MPM (worker)]("http://httpd.apache.org/docs/2.0/en/mod/worker.html").

```
sudo apt-get remove apache2-threaded-dev
sudo apt-get install apache2-prefork-dev 
```
should fix your problem.

Kind regards,
Ilalmi

---

### Post by scottrcaldwell on 2010-03-09
Ilalmi,

Good catch! That did the trick. Now let's see if I can get Railo running...


Thanks,

Scott

---

