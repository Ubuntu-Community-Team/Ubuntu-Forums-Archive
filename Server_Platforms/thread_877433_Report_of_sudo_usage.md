---
title: "Report of sudo usage"
date: 2008-08-01
forum: Server Platforms
---

### Post by kvizz on 2008-08-01
How can i make my ubuntu server (with no enabled root account) to report of sudo usage via e-mail? 
For example, in CentOS installation i use ```
echo 'ALERT - Root Shell Access:' `who` | mail -s "Alert: Root Access from `who | awk '{print $6}'`" mymail@mymailserver.com
``` in root .bash_profile to report of root login.

---

### Post by StickyStyle on 2008-08-03
Perhaps install the logcheck program and remove the /etc/logcheck/violations.ignore.d/logcheck-sudo file? That should email you anytime that someone uses sudo with what command they ran.

---

