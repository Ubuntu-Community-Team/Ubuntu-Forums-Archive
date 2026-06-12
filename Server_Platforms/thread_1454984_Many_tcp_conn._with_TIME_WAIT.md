---
title: "Many tcp conn. with TIME_WAIT"
date: 2010-04-15
forum: Server Platforms
---

### Post by januzi on 2010-04-15
Hi

First of all sorry for my English, I'll try to describe my problem as clear as possible. 


For some reason there are many TIME_WAIT connections on the netstat list. All of them are from one ip. That ip is from my co-workers who connect to the www server from firefox and livezilla client (the second one is more important). I have got mrtg installed, so I can take a look at the charts and I can see that cpu usage chart is almost the same as the connections chart. 640 connections give 88% of the cpu usage. I checked server-status and I got:
> 
_ 8.78% IP POST /livezilla_srv/server.php?acid=xxxx HTTP/1.1
_ 11.68% IP POST /livezilla_srv/server.php?acid=xxxx HTTP/1.1
_ 9.88% IP POST /livezilla_srv/server.php?acid=xxxx HTTP/1.1
_ 13.35% IP POST /livezilla_srv/server.php?acid=xxxx HTTP/1.1
 (there are 5-10 connections in the wait state)

Edit: So, they disconnected and netstat shows that there are only 150 connections (before it was about 450-480 connections).

Is there a way to prevent apache/livezilla/etc. from flooding tcp queue ? 
I can supply more info, if needed.

---

