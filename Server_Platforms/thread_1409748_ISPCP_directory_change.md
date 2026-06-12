---
title: "ISPCP directory change"
date: 2010-02-17
forum: Server Platforms
---

### Post by jvmcintyre on 2010-02-17
Fixed

---

### Post by jvmcintyre on 2010-02-18
Ok ... So heres my update...


Got it working somewhat...


I can go to [www.mydomain.com](www.mydomain.com) and it will go to the cheesy page I put up just to see if I was surfing to it..


But.......


When I put in [www.mydomain.com/ispcp](www.mydomain.com/ispcp)
or any other alias I put under the virtual server I get an internal server error from the ispcp page...

What am I missing????

---

### Post by jvmcintyre on 2010-02-18
***** NEW UPDATE *******

Now I can get the home page to work correctly... However when I try to create aliases to [www.domain.com/ispcp;](www.domain.com/ispcp;) [www.domain.com/ftp;](www.domain.com/ftp;) [www.domain.com/pma;](www.domain.com/pma;) or the [www.domain.com/webmail](www.domain.com/webmail).... 

I just get internal server errors!!! Error 500... I have looked through all the conf files and cannot find what I seem to be missing.


Did some research on Error 500 and it says I may have to recode the whole darn thing!!!!

ARGH!!!!! 

Pleeeeaase tell me there is an easier way to fix this....:(

---

### Post by cariboo on 2010-02-18
I sounds like you have an ownership problem, everything in /var/www should be owned by either root or www-data, and all file permissions should be 755.

Just another suggestion, have a notebook beside you when you are making changes and document them, so you can refer to the notes at another time when you run into problems.

---

