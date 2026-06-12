---
title: "Ubuntu 18.04: Failed to start apparmor initialization"
date: 2018-03-01
forum: Ubuntu Development Version
---

### Post by imsentina on 2018-03-01
I'm using Ubuntu 18.04.

At boot, I have this error

Failed to start apparmor initialization.

Please tell where to start.

---

### Post by vasa1 on 2018-03-01
Moved here since it's about 18.04.

---

### Post by zika on 2018-03-01
It would help us to help You if You would give us logs pertinent to AppArmour...
[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)

---

### Post by imsentina on 2018-03-01
> [INDENT]                     It would help us to help Yoi if You would give us logs pertinent to AppArmour...
[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)    [/INDENT]
[INDENT]             
Thanks Zika.

[/INDENT]

---

### Post by imsentina on 2018-03-01
Ok, so the page that Zika provided is about filing a bug.
It says there in introductionto to first determine if its bug in application or bug in apparmor profile.

I have attached significant (I believe) portion in my /var/log/kern.log.

Guidance please on how to proceed.

---

### Post by rockorequin on 2018-03-19
I am seeing the same thing with my Ubuntu 18.04, so I logged a bug at [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1756800](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1756800).

---

### Post by imsentina on 2018-04-23
Since I'm the one that started this thread, I'm obliged to inform everyone that I do not see this error anymore. Maybe, its a bug that have been fixed. Thanks!

---

