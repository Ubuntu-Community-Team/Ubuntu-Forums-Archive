---
title: "help with run levels"
date: 2013-05-03
forum: Server Platforms
---

### Post by SlugSlug on 2013-05-03
Can someone tell me how to make a service start after X has loaded?

I have 2 services in /etc/init.d that I installed using

update-rc.d SERVICE defaults

problem is they take about 5 seconds each to load and my boot seems to only run one service after another (can this be change to run both at same time?)

---

### Post by TheFu on 2013-05-03
The version of Ubuntu matters here.  Newer versions use "upstart", so checking the man page and google for use of that command would be where I would start.

In the old /etc/init.d/ structure, just find the number that starts X/Windows and make the other links for the services you want to start later have a higher number.  On my desktop, that number is 70, but it could be different on yours. 71-99 would be the choices to start after X11.  I suspect there is a way to manage this using update-rc.d, but I'd simply make the softlink have the number I wanted.

---

### Post by SlugSlug on 2013-05-03
Thanks, I've added mine as S99Service

---

