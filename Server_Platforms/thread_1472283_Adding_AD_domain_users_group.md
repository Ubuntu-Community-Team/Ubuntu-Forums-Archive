---
title: "Adding AD domain users group"
date: 2010-05-04
forum: Server Platforms
---

### Post by LebLinux on 2010-05-04
Hello,

I have server 9.04 and joined thru winbind to Windows Domain and subversion installed. Windows AD users can use their own credentials to join and everything is working fine. However the group svn which is used to access the repos in /etc/groups has some users. However I would like to add the domain users group to the svn group but the domain users contains Space. And /etc/groups does not happend to read the space any ideas on how to add "domain users" to the svn group in /etc/groups ! Many thanks

Regards,

Saad

---

### Post by tumandro on 2010-05-04
Do you mean a space in between words? If so you'd just use "\ " (no quotations).

---

