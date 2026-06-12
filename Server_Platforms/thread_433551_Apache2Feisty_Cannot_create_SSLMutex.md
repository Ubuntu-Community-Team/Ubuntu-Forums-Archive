---
title: "Apache2/Feisty: Cannot create SSLMutex"
date: 2007-05-05
forum: Server Platforms
---

### Post by sav2005 on 2007-05-05
I have just upgraded from Edgy to Feisty and Apache2 will not start. The log gives the error message
Cannot create SSLMutex in /var/run/apache2/sslmutex

If I manually create the directory then apache is happy. The directory disappears after a reboot and has to be manually recreated !:confused: 

I am going to file this as a bug in Feisty.

---

### Post by moanin on 2008-05-10
I've solved creating the apache2 dir:

mkdir /var/run/apache2/

It works for me, either after reboot.

bye!

***** !!!

hello again..... sorry, i'm not right.  /var/run/apache2 disappear after each reboot!

thanks L

---

