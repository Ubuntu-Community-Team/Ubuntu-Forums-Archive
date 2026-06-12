---
title: "Is It Ok To Run A Server Virtually?"
date: 2010-06-29
forum: Server Platforms
---

### Post by SecretLegend on 2010-06-29
Hey Guys, so I just got me a mac pro 8 core a couple days ago ( Which took forever to save up for). I have parallels installed on the mac and I wanted to know if it is ok to run Ubuntu server virtually in parallels. I got it working perfectly fine but I want to know if its fine for production, as my main use for it is as a web server. 

BTW since the mac pro has 12 gigs of ram I allow 4 gigs to ubuntu server and 4 cores on the cpu to ubuntu server. So do you guys think it is fine to run Ubuntu Server 10.04 virtually? Thanks in advance :)

---

### Post by CharlesA on 2010-06-29
That should be fine, just be sure to keep backups and whatnot. As long as you don't mind the host always being on, it'll be good.

Only downside is that if the host goes down, you are boned.

---

### Post by SecretLegend on 2010-06-29
> **CharlesA said:**
> That should be fine, just be sure to keep backups and whatnot. As long as you don't mind the host always being on, it'll be good.

Only downside is that if the host goes down, you are boned.
I really don't mind the host being on all the time. So hopefully all will go will I also bought a power backup system. I may also consider buying a mac mini and install parallels on it, because I bet a dual core processor with 4 gigs of ram is fine. I have about 500-600 people always accessing the web server. Hoping soon it will grow to more :)

---

### Post by NullHead on 2010-06-30
A mini will definitely not host a website with that much traffic I don't think. Mind you I've never used a mini for such tasks, but I figure after you get ubuntu running virtually on there, it won't be very fast. 

I'm sure ubuntu 10.04 run virtually will be just fine. I mean, [http://linode.com](http://linode.com) [http://hostgator.com](http://hostgator.com) are a few examples of companies that run virtual servers. I think your mac pro would be more than powerful enough to host a website such as that. 

As mentioned earlier, make backups.

---

