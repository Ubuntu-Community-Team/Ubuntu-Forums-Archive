---
title: "Linking DNS FTP and VirtualHost together"
date: 2010-05-23
forum: Server Platforms
---

### Post by waYYne on 2010-05-23
HI All,
I am using Ubuntu 10.04 Server on my private network for the first time coming from a Microsoft world :-)
i am a little lost to say the least.  I would love some help here please to the following issues.
[B]

the common scenario i had with Windows, now i want with Ubuntu:[/B]  to have multiple websites running on my server box (called ub1) this will be in a Dev/testing capacity and then sites will be uploaded to production servers hosted by host companies.  i would like the public to see ub1 it with host headers as its a single dynamic ip.  I want an ftp account associated with each site locked to that only. 


1 followed several tutorials but they all assume that another part is configured already.  i.e.   multiple virtualHost tutorial but no info on how to tie it to DNS  zone files, bind9 settings and the like.

as a result i have a set up that needs some guidance  (long... i know :) ) 

[LIST=1]
[*]i have a dynamic dns service using the url [http://ub1.selfip.com](http://ub1.selfip.com).  My windows server called "ub1" used this.  should the replacement Ubuntu server be called ub1?  or ub1.selfip.com
[*]all examples talks about site names eg example.com but i have the live sites which would have that domain name registered so for example i have [http://www.thecpc.org.uk](http://www.thecpc.org.uk) as a live production site but i wanted [http://test.thecpc.org.uk](http://test.thecpc.org.uk) as a site on ub1 remembering that ub1.selfip.com is the full name. so how would i name this to resolve correctly?
[*]throw in an ftp account for that user also.
[/LIST]
any help on this is much much appreciated 

thx

---

### Post by cariboo on 2010-05-23
Moved to server platforms.

---

