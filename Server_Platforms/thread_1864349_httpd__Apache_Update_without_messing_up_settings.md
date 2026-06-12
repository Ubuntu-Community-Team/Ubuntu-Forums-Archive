---
title: "httpd / Apache Update without messing up settings"
date: 2011-10-18
forum: Server Platforms
---

### Post by NetDoc on 2011-10-18
I have three web servers running Ubuntu 8.04.4 LTS with Apache 2.2.15 and PHP 5.2.13 running off of a load balancer and feeding off of a data server. 

One of my servers (1) is simply crashing all the time and causes way high loads on the other two (2 and 3). When I stop httpd on 1, both 2 and 3 do a lot better, but the loads are still around 7 and 8. Unfortunately, my systems engineer is out of pocket: I can't get a hold of him. 

I want to update apache and php on 1 as a test to see if that will help. I just paid a lot of money to tweak and configure my data server and am noticing results already. One of the recommendations was to update apache and php anyway. So how do I do it and retain the settings?

---

### Post by NetDoc on 2011-10-19
I was hoping to have a reply by now. Oh well! I hate to experiment, but I am going to have to try.

---

