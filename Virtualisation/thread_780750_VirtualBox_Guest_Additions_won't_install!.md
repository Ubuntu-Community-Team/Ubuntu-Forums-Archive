---
title: "VirtualBox Guest Additions won't install!"
date: 2008-05-03
forum: Virtualisation
---

### Post by Toadinator on 2008-05-03
I'm having some trouble with installing the Guest Additions in my virtual machine in VirtualBox. Xubuntu 8.04 is running on the virtual machine and when I try to execute the install script (VBoxLinuxAdditions.run) as root I get this:

```
Verifying archive integrity... All good.
Uncompressing VirtualBox 1.5.6 Guest Additions Linux Installation....
.....................................................................
..................................................
VirtualBox 1.5.6 Guest Additions installation
./install.sh: 73: cannot create /var/log/vboxadd-install.log: permision deni
ed
cat: /var/log/vboxadd-install.log: No such file or directory
Error creating log file! Aborting...
```

What am I doing wrong?

---

### Post by Toadinator on 2008-05-03
Nevermind, I found out what to do (run sudo instead of fakeroot). My bad.

---

