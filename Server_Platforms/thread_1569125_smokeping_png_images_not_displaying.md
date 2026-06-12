---
title: "smokeping png images not displaying"
date: 2010-09-06
forum: Server Platforms
---

### Post by bvt on 2010-09-06
I'm trying to run smokeping on my 10.04 LTS computer but the images don't show up.  Nothing is shown on Firefox, and Chrome shows the image outline and time axis information.  Below is a 'copy url' from Chrome.

[http://localhost/cache/smokeping/images/__navcache/12837850512245_1283785051_1283768820.png](http://localhost/cache/smokeping/images/__navcache/12837850512245_1283785051_1283768820.png)

here is some output from my apache2 log:

[Mon Sep 06 09:58:19 2010] [error] [client 192.168.1.54] File does not exist: /var/www/cache, referer: [http://192.168.1.50/cgi-bin/smokeping.cgi?target=Local.Router](http://192.168.1.50/cgi-bin/smokeping.cgi?target=Local.Router)

[Mon Sep 06 09:58:19 2010] [error] [client 192.168.1.54] File does not exist: /var/www/cache, referer: [http://192.168.1.50/cgi-bin/smokeping.cgi?target=Local.Router](http://192.168.1.50/cgi-bin/smokeping.cgi?target=Local.Router)

I've played around with the 'pathnames' file in /ect/smokeping, but that didn't seem to work. I browsed from another machine and get the same results.  I also re-installed it.

Any ideas?

thanks,
Barry

---

