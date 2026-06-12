---
title: "phpmyadmin behaves strange"
date: 2012-05-17
forum: Server Platforms
---

### Post by tutunmayan on 2012-05-17
Server: Ubuntu 10.04
RAM : 4Gig
CPU : average dualcore
Web Site Hits: 100.000 pages/daily


I operate 10 different sites in the same server by the help of apache virtualization. 

Server had some performance issues previously.

Now applications (PHP) connects all databases and performs ok. 

But with phpmyadmin I cannot access only 1 of 15 databases on the same local mysql server. All databases have same properties. There is nothing different. I can access and make opreations on 14 databases  but when I clicked the first and the heaviest database it returns this error and logs out :

```
#2003 - Can't connect to MySQL server on '127.0.0.1' (111)
```

Here is the statistics of db [**http://pastehtml.com/view/byd8u3kjn.html**](**http://pastehtml.com/view/byd8u3kjn.html**)

Any ideas?

---

### Post by d4m1r on 2012-05-17
That is a lot of traffic...I wouldn't surprised if you can't access the DB because of lack of resources. Do you have RAM/CPU usage figures?

---

### Post by tutunmayan on 2012-05-18
The problem was I accidentaly wrote a file into that databases directory. I removed that file and problem solved.   

> **d4m1r said:**
> That is a lot of traffic...I wouldn't surprised if you can't access the DB because of lack of resources. Do you have RAM/CPU usage figures?

---

