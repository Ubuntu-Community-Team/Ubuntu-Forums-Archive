---
title: "sudo should ALWAYS ask for my password"
date: 2008-09-24
forum: Security
---

### Post by darkweasel on 2008-09-24
Hi everyone,

currently sudo remembers my password for 15 minutes if I enter it once. However, I'm a little paranoid and such, so I'd like it to ask EVERY time. Is this possible, i.e. what do I have to change in /etc/sudoers?

Thanks in advance!

---

### Post by lazyart on 2008-09-24
Taken from [http://polishlinux.org/first-steps/root-account/sudo-faq/](http://polishlinux.org/first-steps/root-account/sudo-faq/)

> 5.a. You can set sudo to never remember passwords.
In order to do this, append the following line in /etc/sudoers:

Defaults:johnny timestamp_timeout=0


Substitute your username for "johnny"

use ```
sudo visudo
``` to edit the sudoers file.

---

