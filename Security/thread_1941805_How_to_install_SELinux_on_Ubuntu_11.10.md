---
title: "How to install SELinux on Ubuntu 11.10"
date: 2012-03-16
forum: Security
---

### Post by jeshrel on 2012-03-16
Hi,

I would like to install and use SELinux in ubuntu 11.10, how do i install it?

Thanks

---

### Post by haqking on 2012-03-16
> **jeshrel said:**
> Hi,

I would like to install and use SELinux in ubuntu 11.10, how do i install it?

Thanks

```
sudo apt-get install selinux
```

you might want to take a look at apparmor

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

SELinux is not really for beginners and can be confusing, I assume you are a beginner as you dont know how to install it so be warned.

Cheers

---

### Post by jeshrel on 2012-03-18
thank you

---

### Post by Dangertux on 2012-03-18
Make sure you remove apparmor first. They can and will confllict

---

