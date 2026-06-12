---
title: "Oracle VM or KVM ?"
date: 2022-04-03
forum: Virtualisation
---

### Post by oygle on 2022-04-03
I'm having problems with booting with the Oracle VM (see [https://ubuntuforums.org/showthread.php?t=2473409](https://ubuntuforums.org/showthread.php?t=2473409)  ). The guide at [https://phoenixnap.com/kb/ubuntu-install-kvm](https://phoenixnap.com/kb/ubuntu-install-kvm) looks nice and easy ..

```
egrep -c '(vmx|svm)' /proc/cpuinfo
```

> 4

```
sudo kvm-ok
```

> INFO: /dev/kvm exists
KVM acceleration can be used

Which product is better suited to the install of a VM to test openSUSE please ?

---

### Post by CharlesA on 2022-04-03
Seeing as you already have VirtualBox installed, you should probably see why the ISO won't boot. I would bet it's related to Secure Boot, but I haven't used VirtualBox in many years, so that's all I've got.

---

### Post by oygle on 2022-04-03
Thanks. I read a few more articles and one stated to make sure the VM is powered off. I noticed the boot order was always greyed out. I was used to ending with a 'saved state', so removed that, and it showed 'powered off'. Then I was able to modify the boot order and it is installing the openSUSE now, thanks.

---

