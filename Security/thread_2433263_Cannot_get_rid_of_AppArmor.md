---
title: "Cannot get rid of AppArmor"
date: 2019-12-16
forum: Security
---

### Post by godatum2 on 2019-12-16
I am running 16.04. I have run:

```
sudo systemctl stop apparmor
sudo systemctl disable apparmor
sudo apt-get remove apparmor

```

And also added in /etc/default/grub:
```
apparmor=0 
```

Rebooted but apparmor still runs! In the /var/log/kern/log:
```

AppArmor: AppArmor initialized
evm: security.apparmor
AppArmor: AppArmor Filesystem Enabled
AppArmor: AppArmor sha1 policy hashing enabled

```

---

### Post by bernard010 on 2019-12-17
Why would you want to get rid of AppArmor ? The very security feature that helps protect your file system. 
I have uninstalled it before due to a bug. I used the synaptic package manager. Unless it is malfunctioning I would leave it.
It is of course part of the default OS.      > AppArmor is a Mandatory Access Control (MAC) system which is a kernel  (LSM) enhancement to confine programs to a limited set of resources.
I try to avoid uninstalling kernel items.
      Here is the documentation for AppArmor :  [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

---

