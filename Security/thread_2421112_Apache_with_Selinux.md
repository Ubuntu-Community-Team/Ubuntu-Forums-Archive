---
title: "Apache with Selinux"
date: 2019-06-16
forum: Security
---

### Post by xavierbaez on 2019-06-16
In short, what is the best way to allow apache2 to listen to port 80 with selinux?

I have always disabled selinux, when you are developing and in a hurry your first reaction is to disable and get it out of the way.

but I would like to know how to make sure I keep using selinux and also listen on port 80

---

### Post by TheFu on 2019-06-17
SELinux isn't part of Ubuntu. Using it on Ubuntu would be strange. Odd. Unusual. It isn't installed on Ubuntu systems.

If you want SELinux, you'll want to use a RHEL-variant distro.

---

### Post by xavierbaez on 2019-06-17
> **TheFu said:**
> SELinux isn't part of Ubuntu. Using it on Ubuntu would be strange. Odd. Unusual. It isn't installed on Ubuntu systems.

If you want SELinux, you'll want to use a RHEL-variant distro.

So is there an equivalent on Ubuntu?

---

### Post by TheFu on 2019-06-17
> **xavierbaez said:**
> So is there an equivalent on Ubuntu?

No, not equivalent.  Start here:
[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)
[https://help.ubuntu.com/lts/serverguide/apparmor.html.en](https://help.ubuntu.com/lts/serverguide/apparmor.html.en)
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

But many other protection systems exist since SElinux/AppArmor were introduced. Some of those have already been deployed by default in newer releases.

---

