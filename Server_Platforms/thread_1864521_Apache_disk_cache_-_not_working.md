---
title: "Apache disk cache - not working"
date: 2011-10-19
forum: Server Platforms
---

### Post by chrislynch8 on 2011-10-19
Hi,

I've been messing around with apache2 & disk cache. I enabled disk cache on my server and used the default configure that come with apache. Then in the /var/cache/apache2/mod_disk_cache a series of folder where created after a restart and I started using the web application.

I then disbaled the disk cache modules and physically deleted the folder from inside the /var/cache/apache2/mod_disk_cache/ directory. I think I shouldn't have done this. As now when I enable the disk cache again with some more settings after doing some reading I discovered that the folder are not recreated in hte /var/cache/apache2/mod_disk_cache directory.

Is there something I can do to get the disk cache working again. I tried changing the CacheRoot folder to a different folder and this didn;t help either.

I'm on Ubuntu 10.04 LTS
Apache2 2.2.14-5ubuntu8.9


Rgds
Chris

---

### Post by chrislynch8 on 2011-10-19
I disable both cache & disk cache and then enabled them again and its working now.

Rgds
Chris

---

### Post by sireedisson on 2011-10-19
Thanks Chris, I have just done this and mine is now also working :P I was messing around for ages! Such a simple fix.

.........................................
Edward Edisson
[http://findnetone.co.uk/](http://findnetone.co.uk/)

---

