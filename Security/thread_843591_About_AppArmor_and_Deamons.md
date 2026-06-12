---
title: "About AppArmor and Deamons"
date: 2008-06-28
forum: Security
---

### Post by Nullack on 2008-06-28
With AppArmor, how do I tell if it is protecting a program / daemon or not?

For example, if I install the NTP daemon how do I know Im protected with that service?

Many thanks

---

### Post by damatta on 2008-06-28
I know not if this is what youre asking but you can issue:
sudo apparmor_status
and look for profiles in enforce mode. You can also check your system log to see if apparmor is blocking something (eg. attempts to read forbidden directories). However, what counts is how safe your profile is...

---

