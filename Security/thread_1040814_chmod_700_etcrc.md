---
title: "chmod 700 /etc/rc*"
date: 2009-01-15
forum: Security
---

### Post by victorbrca on 2009-01-15
Hi all,


  I'm building a Ubuntu virtual machine to do my online banking. I'm trying to get it as tight as possible.

  I read on a few sites directed to distros that use /etc/rc.d/ (like slack), that one of the security options is to 'chmod 700' your /etc/rc.d folder. 

  Anyone know if this is also doable on Ubuntu? If so, should I be doing it under rc3.d (graphical machine) or init.d? 

Thanks!

Vic.


PS: Any security links specific for Ubuntu are also very welcome!! :)

---

### Post by The Cog on 2009-01-17
I'm not sure I see the point, but if you want to, do it on /etc/init.d, not on the rc.? directories, because they are all just symlinks to the init.d directory.

---

