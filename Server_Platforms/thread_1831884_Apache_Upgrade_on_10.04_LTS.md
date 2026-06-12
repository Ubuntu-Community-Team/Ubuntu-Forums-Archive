---
title: "Apache Upgrade on 10.04 LTS"
date: 2011-08-24
forum: Server Platforms
---

### Post by HannesBenson on 2011-08-24
Good morning

I am currently trying to upgrade the Apache installation on our server from v2.2.14 to v2.2.19 using:

[http://httpd.apache.org/docs/2.2/install.html](http://httpd.apache.org/docs/2.2/install.html) as a guide. 

Unfortunately I seem to have hit some walls. When trying to execute ./config.nice I get the following error:

./config.nice: 33: /build/buildd/apache2-2.2.14/configure: not found

Google have not yielded any results as yet. If I leave out this step and use configure, make and make install, v2.2.19 gets installed, but to a different directory and all the config will need to be reformatted as it seems it does not use the Ubuntu Apache config structure.

I hope this all makes sense and I hope someone can guide me in the right direction.

Thanks

---

### Post by HannesBenson on 2011-08-24
It seems I over thought the problem, adding the sources from later versions and then installing apache updated the version and solved my problems.

---

### Post by ravingmad on 2011-08-29
> **HannesBenson said:**
> It seems I over thought the problem, adding the sources from later versions and then installing apache updated the version and solved my problems.

Please could you explain how you did this, I'm confused.

---

### Post by HannesBenson on 2011-08-29
I wasn't able to upgrade all the way to 2.2.19, but adding the 10.10 repos to 10.04 allowed me to install Apache 2.2.16. I did try installing 2.2.19 by adding the Oneiric repos, but there were some issues with dependencies and since this was required on a production server I did not try and mangle the whole OS install.

---

### Post by ravingmad on 2011-08-30
> **HannesBenson said:**
> I wasn't able to upgrade all the way to 2.2.19, but adding the 10.10 repos to 10.04 allowed me to install Apache 2.2.16. I did try installing 2.2.19 by adding the Oneiric repos, but there were some issues with dependencies and since this was required on a production server I did not try and mangle the whole OS install.

Thanks for the reply Hannes, I'll give it a whirl. Is 2.2.16 performing ok for you?

---

### Post by HannesBenson on 2011-08-31
I am quite happy with the performance thus far. I will soon do a comparison in performance between 2.2.16 and 2.2.19 as I have a testing machine with similar hardware config running 2.2.19.

---

