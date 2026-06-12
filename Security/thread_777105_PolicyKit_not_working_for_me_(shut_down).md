---
title: "PolicyKit not working for me (shut down)"
date: 2008-05-01
forum: Security
---

### Post by MacUntu on 2008-05-01
I want to use /sbin/shutdown w/o the need of typing a password.

What I've tried so far:

1.) I added myself to /etc/sudoers (user ALL=NOPASSWD: /sbin/shutdown): Worked fine - like expected.

2.) I added myself to the list of users that should be able to do a shut down via polkit-gnome-authorization. Didn't worked - not expected.

As I understand the whole policy thingy, it should do exactly what I want, right? So why isn't it working?

TIA for your answers! :)

---

### Post by MacUntu on 2008-05-06
*bump*

---

### Post by Old Narnian on 2009-03-28
The following command should accomplish what you were looking for.  You probably found it by now.

**sudo chmod u+s /sbin/shutdown**

---

