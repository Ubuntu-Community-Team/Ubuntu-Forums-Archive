---
title: "Geronimo Tomcat 6 slow startup"
date: 2009-01-09
forum: Server Platforms
---

### Post by don_eros on 2009-01-09
Hi there,

I recently installed Geronimo Tomcat on my Ubuntu 8.04 server (64 bit version). I had to install it manually since there's no package for that yet. Everything seems to work fine, except that Tomcat takes forever (1 to 4 minutes) to start up.

I really don't know where to look, I have the exact same setup on another server (the only difference is it's the 32 bit version) and the problem doesn't manifest itself.

The package is geronimo-tomcat6-javaee5-2.1.3.

I attached the log from the last startup where you can see that module 25/69 started in 3:46.585s. I monitored system activity with top while that particular module was starting up, but I didn't notice anything suspicious.

Thanks a lot for any pointers,
Eros

---

### Post by don_eros on 2009-01-14
I finally figured out what the problem was and I thought I should leave a note here for posterity: the server runs out of entropy and this somehow slows down Tomcat startup.

The full story is here:

[http://www.nabble.com/Startup-time-delay-in-Ubuntu-server-td21301711s134.html](http://www.nabble.com/Startup-time-delay-in-Ubuntu-server-td21301711s134.html)

E

---

