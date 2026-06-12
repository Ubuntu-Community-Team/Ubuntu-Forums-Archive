---
title: "mysql not starting"
date: 2009-09-30
forum: Server Platforms
---

### Post by TheOrangePeanut on 2009-09-30
I'm retiring my old desktop and using my new laptop as my main PC, so I thought I'd use my desktop as a server for my files and projects and whatever else.  I'm trying to set up mysql, but it isn't working.

I did sudo apt-get install mysql-server and it installed okay, but when I try to start the service with sudo /etc/init.d/mysql (re)start it always fails on trying to start.  I don't know where there is a log of this failure, how can I troubleshoot this?

---

### Post by TheOrangePeanut on 2009-09-30
I didn't have my loopback interface configured correctly.  That was the problem.

---

