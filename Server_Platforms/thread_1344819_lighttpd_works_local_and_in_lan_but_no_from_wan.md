---
title: "lighttpd works local and in lan but no from wan"
date: 2009-12-03
forum: Server Platforms
---

### Post by sartic on 2009-12-03
I forwarded port 80 from nat to this machine width lighttpd.
When someone from outside demands web server I can see in log that is from WAN to IP of server on port 80 but www r not opening.
What I am missing?
ps: standard install from repo Ubuntu 9.10 64bit (desktop system)

---

### Post by sartic on 2009-12-03
update: 
It opens simple index.htm (not like default from lighttpd).

---

### Post by sartic on 2009-12-03
i tried cherokee server. same problem from wan.
even forwarded https port (only static wwww)

---

### Post by sartic on 2009-12-03
nat/firewall is not problem, i established web server under xp on same lan.

---

### Post by ghettofreeryder on 2009-12-03
Sounds like apache is running, try turning it off.

---

### Post by sartic on 2009-12-03
apache is not installed and i think 2 deamons won't work on same port.
this line solved problem:
sudo adduser user www-data
jesus after 6h and googling and trying, still can not believe that this is it.

---

