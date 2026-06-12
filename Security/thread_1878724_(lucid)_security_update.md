---
title: "(lucid) security update"
date: 2011-11-10
forum: Security
---

### Post by robertmf on 2011-11-10
lucid 10.04 i386/32
kernel 2.6.32-35-generic-pae
gnome 2.30.2

I just used the update manager to install today's security fixes.  After reboot, chromium-browser would not load.  Trying from the command line gave me a suggestion to <sudo chmod 1777 /dev/shm>

This allowed chromium to open.

---

### Post by CharlesA on 2011-11-10
That's just a device file. Not sure why it would need the [sticky bit]("http://www.delphifaq.com/faq/f1380.shtml") set and full rwx permissions tho.

Apparently [shm is shared memory]("http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html").

EDIT: Checked my lucid box and the permissions were 1777 on that one - drwxrewrwt

---

