---
title: "Error while installing latest Swiftfox *.deb"
date: 2006-09-15
forum: System76 Support
---

### Post by frainbart on 2006-09-15
I tried to install the latest Swiftfox version and I get this error about trying to overite the debian binary:

```
 ~/Downloads$ sudo dpkg --install swiftfox_1.5.0.7-1ubuntu_pentium-m.deb
Password:
(Reading database ... 91487 files and directories currently installed.)
Unpacking swiftfox (from swiftfox_1.5.0.7-1ubuntu_pentium-m.deb) ...
dpkg: error processing swiftfox_1.5.0.7-1ubuntu_pentium-m.deb (--install):
 trying to overwrite `/debian-binary', which is also in package system76-driver
Errors were encountered while processing:
 swiftfox_1.5.0.7-1ubuntu_pentium-m.deb

```

Any thoughts?

---

### Post by crichell on 2006-09-15
hi frainbart - i'll give this a shot on a test machine and get back to you soon.

---

### Post by kevinlyfellow on 2006-09-27
I forced it to install and everything seemed to work ok (my system was out of whack at the time anyways).  I did not notice any difference in speed with my T2300.

---

