---
title: "Ubuntu 7.04 - jabberd2"
date: 2007-05-28
forum: Server Platforms
---

### Post by ufocek on 2007-05-28
Hi 

I have a server with ubuntu 7.04 where I installed jabberd2.
Now I have run jabberd2 with multiple domains, I configured c2s.xml and second session manager sm-mynewdomain.com.xml
Edit jabberd2.cfg and I add 
sm          /etc/jabberd2/sm-mynewdomain.xml
When I restart jabberd2 /etc/init.d/jabberd2 restart the second config sm not loaded, but when I run jabberd on console like this: jabberd -D second sm config is running.
Anyone know why config isn't load when I restart jabberd2?

Regards
ufocek

---

