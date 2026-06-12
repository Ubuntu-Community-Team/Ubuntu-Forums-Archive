---
title: "Strange server behaviour"
date: 2012-05-17
forum: Server Platforms
---

### Post by tutunmayan on 2012-05-17
Hi all,

I have a strange issue. 

My Ubuntu 10.04 server which gets 100.000 hits a day have got slow down.
When I inspected I noticed that mostly first pageloads and statick js files  and rarely image files are waiting too long before loading. (see image below) Why?

I figured out that server is running outof resources. CPU was 80% utilized (dualcore) and only 500M of memory was available of 4gigs.


After adding a cache layer to software the problem disapeared. Cahching mostly reduces database operations. Application don't have cpu sensitive calculations or etc. Mostly gets data from db and displays. (Yes it's a web site)

Now resources can be seen in image below.



But now there is another strange problem with mysql. I opened a seperate thread about it: **[http://ubuntuforums.org/showthread.php?p=11943639]("http://ubuntuforums.org/showthread.php?p=11943639")**

I am not good at server administration. I am only a developer who has to solve this issue :(


Any help appreciated.

LOADING TIMES:

[IMG]http://s15.postimage.org/5q68mrgqj/loading_times_b.jpg[/IMG]

RESOURCES AFTER CACHE LAYER ADDED

[IMG]http://s13.postimage.org/ntmqtv22v/resource.jpg[/IMG]

---

### Post by d4m1r on 2012-05-17
1) You should have only opened 1 thread, both are caused by the same issue, lack of resources.

2) Normally 4GB and a dual core CPU is more than plenty for running a small website but 100,000 page views daily is NOT a small website....You need to upgrade your machine for such traffic, it is why you are experiencing issues....

---

### Post by tutunmayan on 2012-05-18
Thank you d4m1r,

I was not sure both was because of same issue. And yes ,they are not. (Other thread solved)

The thing I dont understand is why always js files but not the others wait too much under heavy load.

Is it something about gziping?

---

