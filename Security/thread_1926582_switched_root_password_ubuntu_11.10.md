---
title: "switched root password ubuntu 11.10"
date: 2012-02-16
forum: Security
---

### Post by levente88 on 2012-02-16
i did a really stupid thing that's giving me trouble:
i was trying to modify user privilages in user accounts and switched the administrator account to a standard one ](*,). Now my root password doesn't work and i don't want to reinstall the system again since it took forever the last time. How can i change it back or to something else? Any and all help is apreciated

---

### Post by Bachstelze on 2012-02-19
Boot the system in "recovery mode", then you can edit /etc/groups and add yourself back to the 'admin' group.

---

### Post by hanifsm on 2012-02-19
u can boot it with a bootable or livecd too

---

