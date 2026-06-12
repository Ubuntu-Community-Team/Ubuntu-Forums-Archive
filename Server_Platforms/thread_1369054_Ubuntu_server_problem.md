---
title: "Ubuntu server problem"
date: 2009-12-31
forum: Server Platforms
---

### Post by _yuri_ on 2009-12-31
Hey guys!
I've installed ubuntu server 9.10 with tomcat6 and postgres. I've configured ufw to allow in and out on port xxxx. I also configured my router's virtual server and firewall to allow connections on port xxxx.

But the problem is that people outside of my private network cannot download files from me more than about 30k via tomcat. And the same is with postgres - cannot select tables more than 20-30k. The process of downloading or selecting tables just freezes.

I'm sure it's nothing with my router settings because on my windows machine tomcat works fine.

What's wrong with Ubuntu (that problem was also on ubuntu server 9.04)?

Network: d-link di-804hv, private lan, 3 windows PC and ubuntu server.

---

### Post by _yuri_ on 2009-12-31
I've solved my problem). It was the d-link di-804hv. Turns out ubuntu + d-link doesn't work properly. When I changed it to asus wl-500gp everything works fine!

---

### Post by uelkfr on 2011-10-23
But I have same router and same problem, please help. I can't change router, no money. All Windows network applications works fine.

---

