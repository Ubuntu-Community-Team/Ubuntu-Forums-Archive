---
title: "log stdout to file during boot"
date: 2010-11-30
forum: Server Platforms
---

### Post by smo0th on 2010-11-30
Hi guys, do you know of a way to redirect stdout during boot time to have a log of the entire process?

I have a remote server which is not booting and I would like to know at which point it gets stucked, what could I do? :confused:

---

### Post by smo0th on 2010-11-30
gee...nevermind.. it seems that enabling bootlogd

sudo vi /etc/default/bootlogd

by changing the No to Yes

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

will log to /var/log/boot

:roll:

---

### Post by smo0th on 2010-11-30
ok... bootlog not working :evil:

any ideas??? :confused:

---

### Post by smo0th on 2010-11-30
ok it's in /var/log/kern.log D:

.-.

---

