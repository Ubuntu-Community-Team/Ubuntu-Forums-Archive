---
title: "EASY Mail Server ?!?!"
date: 2006-10-06
forum: Server Platforms
---

### Post by Zephirus on 2006-10-06
Is there an easy to configure mail server out there for ubuntu LAMP server?  Im new to linux so I dont need something too difficult.  

Our goal is to host a webserver and have domain email addresses for our clients (much like a traditional, commercial, web hosting service does)

It would be REALLY nice if the domain owners had some way of adding addresses themselves instead of the company having to do it but if that is not possible, it is ok.  


Thanks in advance.

---

### Post by bluefrog on 2006-10-06
have a look at [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
isp-config is the thing for you I assume.

---

### Post by zitch on 2006-10-06
You can install a ISP hosting software like [ISPConfig](http://www.ispconfig.org/) like I do, but there's no real *EASY* if you don't fully understand the fundamentals of how email works.  Setting up a ubuntu host using [The Perfect Setup - Ubuntu 6.06 LTS Server (Dapper Drake)](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) then using [these instructions to install and setup ISPConfig](http://www.ispconfig.org/manual_installation.htm) is how I did it.  You can setup clients in the admin panel so that they can administrate and maintain email addresses, forwarding, alias, and spam-checking for their own domains.

You can then provide webmail through the admin interface, or install a webmail package on a virtual host, if you want.

I'm sure there are other ISP packages too, and I do have to admit that ISPConfig is rather sparsely and inconsistently documented and not immediately obvious as to how to use it (as is the nature of most free projects), but it was the first I've stumbled on and I now find it very easy to administrate domains with it.

Add: Gah!  Bluefrog beat me to it by 25 minutes!  :)

---

### Post by Zephirus on 2006-10-06
My thanks to you both.  I will have a look at this package when i get home from work this evening.

---

