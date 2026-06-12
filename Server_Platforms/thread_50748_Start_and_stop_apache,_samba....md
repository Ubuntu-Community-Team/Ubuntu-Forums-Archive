---
title: "Start and stop apache, samba..."
date: 2005-07-21
forum: Server Platforms
---

### Post by janhelge on 2005-07-21
I installed samba and apache on a redhat system, I can easily stop and start samba and apache from the terminal with: service smb stop or service httpd stop...

But in Ubuntu? How can I stop and start services?

Jan Helge :roll:

---

### Post by Natja on 2005-07-21
Hi,

Apache: 
/etc/init.d/apache2 start
/etc/init.d/apache2 stop
/etc/init.d/apache2 restart

SSH : 
/etc/init.d/ssh start
/etc/init.d/ssh stop
/etc/init.d/ssh reload

etc.

---

### Post by odin on 2005-07-21
I think the mate above is right.

---

### Post by janhelge on 2005-07-23
Hi,

Thanks! That helped  :smile:

---

### Post by monkster on 2005-07-23
invoke-rc.d <service> <start|stop|et cetera> does much the same thing as the service command in Red Hat

---

