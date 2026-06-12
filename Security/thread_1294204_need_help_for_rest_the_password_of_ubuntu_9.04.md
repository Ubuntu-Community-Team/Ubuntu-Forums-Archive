---
title: "need help for rest the password of ubuntu 9.04"
date: 2009-10-18
forum: Security
---

### Post by envisonhong on 2009-10-18
i forget my password...can anyone tell me how to rest the root password?

---

### Post by Agent ME on 2009-10-18
Normally, to rest a password, you turn your computer off for a few hours, and optionally give bits of hard drive's /etc/shadow file a massage.

However, in Ubuntu, the root password doesn't exist, so there is no need to wish rest for it.
__________________________________________________

To *reset* a password, either log onto any user that is part of the admin group and do "sudo passwd *username*".
If you don't have any other admin accounts besides the one you want to reset, you'll need to reboot, go into recovery mod from the Grub boot-up selection screen, open a root terminal session, and type "passwd *username*".

---

### Post by wilee-nilee on 2009-10-18
If you need to reset your personal password follow this link. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

