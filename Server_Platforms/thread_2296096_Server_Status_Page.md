---
title: "Server Status Page"
date: 2015-09-23
forum: Server Platforms
---

### Post by lewis11 on 2015-09-23
I am a massive noob with Ubuntu and have been tasked with creating a status page for the several servers at my workplace. I would like to know the easiest possible way to create a page that when loaded would state if a server was on/off/or getting errors. Any help is appreciated!

Thanks in advance!

---

### Post by TheFu on 2015-09-23
This is called "monitoring" - there are 20 different programs that do it.  If all you care is green/red (and no other details), something like bigbrother is what we used 20 yrs ago. I think that project is dead/forked now.  BTW - just because you can ping a server, that does'nt mean it is working.  You really need to verify different parts of every service listening on every port.  Munin is easy. Cacti is pretty. There are many others.

However, most people fine that getting an alarm when things go bad is better than having to check a "green/red" webpage. OpenNMS, nagios, and others of that sort do the alarming.

Don't reinvent this wheel.

---

### Post by tgalati4 on 2015-09-23
Pick one or two and play with them.

[http://www.infoworld.com/article/2683857/network-monitoring/article.html](http://www.infoworld.com/article/2683857/network-monitoring/article.html)

---

### Post by LHammonds on 2015-09-24
I keep track of a hundred servers and switches on our LAN/WAN network and have implemented a Nagios monitoring system to do so with great effect.  I documented how I setup my server in my sig.  It takes a while to get planned and setup but once its going, it works great.

As said earlier, you need the ability to see if your services are actually working rather than just power to the machine.  With Nagios and others, you can create scripts that will perform customized tests to ensure your system is working.  There are many ready-to-use checks such as MySQL and Apache tests but its nice being able to hand-craft your own tests.

LHammonds

---

