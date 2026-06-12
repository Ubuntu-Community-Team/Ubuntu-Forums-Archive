---
title: "bind9 question"
date: 2008-08-19
forum: Server Platforms
---

### Post by fouadk on 2008-08-19
hi everyone

i have installed bind9 on my ubuntu server....

i have read some tutorials, i faced some problems jailing bind9 in chroot....i was told that in ubuntu 8.04 this is fixed by apparmor and that chrooting the thing was not necessary...

i am wondering how secure is a default installation of bind9 is???

does really apparmor compensate the use of chroot ???

thanks in advance

---

### Post by RealPSL on 2008-08-19
AppArmor does a similar task as the chroot. The AppArmor profile restricts what the bind daemon can do even if it is compromised. In the chroot jail if bind is compromised the jail restricts the actions. 

Personally I find that AppArmor is easier to setup certainly easier to manage than SELinux. AppArmor also seems to be more flexible.

[AppArmor Wiki]("http://https://wiki.ubuntu.com/AppArmor")

---

### Post by fouadk on 2008-08-20
thank you....i still have one more question...

does the default installation that comes with the server secure?
i just added some forward and reverse zones...

---

### Post by RealPSL on 2008-08-20
When you install bind it also installs the AppArmor profile as well so yes it is secure. You can review and modify the profile in /etc/apparmor.d. Take a look at it and see what it does it is not complex like SELinux and very readable.

---

### Post by fouadk on 2008-08-21
thank you

---

