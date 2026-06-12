---
title: "Fail2ban installation fails"
date: 2009-07-08
forum: Server Platforms
---

### Post by Radio91 on 2009-07-08
I tried to install Fail2Ban but Im getting the following error:

The following packages have unmet dependencies:
  fail2ban: Depends: python-central (>= 0.6.7) but it is not going to be installed
E: Broken packages


Anybody came across this?

---

### Post by Radio91 on 2009-07-08
ended up getting it installed using aptitude but it fails to start again after a reboot! I no this is a known bug but I could'nt figure out how to resolve it with my version of ubuntu or install a fixed version.

Ended up installing Denyhosts instead.

---

