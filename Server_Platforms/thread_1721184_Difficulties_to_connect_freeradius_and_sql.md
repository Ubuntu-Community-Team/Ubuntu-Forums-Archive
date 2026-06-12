---
title: "Difficulties to connect freeradius and sql"
date: 2011-04-04
forum: Server Platforms
---

### Post by wanalex on 2011-04-04
Hi, 

I've followed several tutorials to install LAMP-Freeradius-phpmyprepaid. I struggle with the configuration of freeradius.

LAMP-Freeradius-phpmyprepaid can be installed. No problems.

To configure freeradius, I have to edit 3 files:

sql.conf -> no problem
clients.conf -> no problem

And there my problems start again :)

Any change in /etc/freeradius/sites-enabled/default makes the freeradius [FAIL]

I need to set the parameters 
authorize {
         preprocess
         chap
         suffix
         eap
         #files
         sql
 }
 authenticate {
         Auth-Type PAP {
           pap
         }
         Auth-Type CHAP {
           chap
         }
         eap
 }
 accounting {
         detail
         radutmp
         sql
 }
 session {
         sql
 }

But it can't be done!

Help please!

---

### Post by HermanAB on 2011-04-04
Maybe this will help:
[http://www.aeronetworks.ca/howtos/radius.html](http://www.aeronetworks.ca/howtos/radius.html)

---

