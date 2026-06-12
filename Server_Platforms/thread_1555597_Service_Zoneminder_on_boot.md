---
title: "Service Zoneminder on boot"
date: 2010-08-18
forum: Server Platforms
---

### Post by novazion on 2010-08-18
Hello,

I've got a strange problem on ubuntu server (it seems to appear also on a desktop version). I installed zonminder package trough apt. The init script works well with start|stop|status|retsart commands. (Ubuntu server 10.04)

But I can't get this service to start on boot.

I used update-rc.d to add on startup.
a chkconfig give this line :
zoneminder   0: off  1: off  2: on   3: on   4: on   5: on   6: off

Also in every rcX.d directory, there's a link to the init script

But still nothing on startup.

Am I missing something?
Where could I see exactly what happens on startup?

Thnaks for your help.
Best regards.
Emeric.

---

### Post by novazion on 2010-08-23
Up.

Someone with an idea?

Thanks.

---

### Post by quietas on 2010-08-23
You can use sysvconfig to view or edit the startup services. My 4 boxes show Zoneminder starting on 2,3,4,5 like your's.

---

### Post by novazion on 2010-08-30
Ok. Found the problem. Zoneminder was starting before mysql and so fail to start.

To fix that:

update-rc.d -f zoneminder remove
then
update-rc.d zoneminder defaults 92

Hope this will help.

Emeric.

---

