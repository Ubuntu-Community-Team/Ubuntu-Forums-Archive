---
title: "Ubuntu Server httpd.pl consuming CPU"
date: 2011-07-21
forum: Security
---

### Post by piyush.pv@gmail.com on 2011-07-21
Hello All,

Before few weeks I setup email and webserver based on ubuntu server.


Recently I noticed that cpu is fully used by http.pl, httpd.pl, https.pl process.

 2473 www-data  20   0 36800 6948 1332 R   54  0.7   8:45.96 https.pl           
 2348 www-data  20   0 38332 7464 1332 R   52  0.7   8:55.28 http.pl            
 2475 www-data  20   0 36688 6884 1332 R   45  0.7   8:29.28 httpd.pl           
 2474 www-data  20   0 36952 6948 1332 R   35  0.7   8:37.41 httpd.pl

I restarted system and after 10 min situation is same and because of that web serving can't work properly.

Is my server hacked ?

I also try to kill process by sudo kill 2473 but nothing happen to this process ....

any suggestion how to identify and fix issue ?

---

### Post by cariboo on 2011-07-22
https.pl is the module used for secure http connections, it's normal.

---

