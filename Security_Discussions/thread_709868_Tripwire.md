---
title: "Tripwire"
date: 2008-02-27
forum: Security Discussions
---

### Post by Bigmo1942 on 2008-02-27
How do you get tripwire to update and print reports?:confused:

---

### Post by k_grdn on 2008-02-28
Hi,

Just run tripwire --check to print report & run check.

To upate run: 
tripwire --update --twrfile filename.twr (/var/lib/tripwire/report)

To view report

/usr/sbin/twprint -m r --twrfile /var/lib/tripwire/report/<name>.twr

Regards,

k_grdn

---

### Post by Bigmo1942 on 2008-02-28
Thanks for the info.:)

---

