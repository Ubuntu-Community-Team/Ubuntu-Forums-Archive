---
title: "Raising open file limits in ubuntu"
date: 2008-10-23
forum: Server Platforms
---

### Post by Newmaniese on 2008-10-23
This is really stupid but for some reason I can't raise the level of open files that a user can have from 1024. I have changed etc/security/limits.conf for all users and keep looking around for other places where I can raise the limits (setting ulimit -n in the shell is not possible -- init method).

This is kind of important as I am running a Web server that hits this limit quite frequently. 

Thanks for any help,

Mn

---

### Post by cariboo on 2008-10-24
Have a look at this page:

[http://www.karakas-online.de/forum/viewtopic.php?t=9834](http://www.karakas-online.de/forum/viewtopic.php?t=9834)

I have to say I found it very interesting.

Jim

---

