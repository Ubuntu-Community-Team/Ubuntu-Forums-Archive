---
title: "Ubuntu Server running fast/slow"
date: 2017-04-30
forum: Server Platforms
---

### Post by Mrkrabz1 on 2017-04-30
Don't really know how to explain this one!

Just installed a fresh copy of Ubuntu Server 16.10 64x, started to run some of our applications and realized that we were seeing some very odd issues.

It seems to be that the server is running too fast? Running the command "watch -n 1 date" I can see that it's updating every 0.2-0.5 seconds rather than every 1 second. Running a program such as "dstat" that prints out server usage (network usage etc), it's suppose to print every second. However, this will print every second, then suddenly 5-10 times in a second and then slow down or pause for a while.

Any ideas what this could be? We previously ran Windows on this server is no issues at all.

Edit:
While running the "watch -n 1 date" command, I can see it speeds up to the incorrect time, it will then reset back a few moments later and repeat.

---

### Post by wildmanne39 on 2017-04-30
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2017-04-30
Virtual machine? Which hypervisor?

---

