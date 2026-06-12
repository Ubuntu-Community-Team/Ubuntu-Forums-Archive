---
title: "Apache2 used to start on boot, now it won't..."
date: 2007-02-10
forum: Server Platforms
---

### Post by omega13a on 2007-02-10
I had it set up so that apache2 would start when I turn on my computer.  However, something has happened recently, and it doesn't anymore.  The only way I can get it to start is if I run sudo /etc/init.d/apache2 start in the command prompt.  I've tried that update-rd.d command as well as sysv-rc-conf and neither works.  Any help would be greatly appreciated.

BTW, I'm using Ubuntu 6.10 Edgy.

---

### Post by flossgeek on 2007-02-10
I would install BUM (Boot-up-manager), then select it to start from the list.

**To install bum**

sudo apt-get install bum

---

### Post by omega13a on 2007-02-10
That didn't help.  Here's what I see in BUM in advance mode just after I login.  Everything looks ok except it says its not running...

---

