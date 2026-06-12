---
title: "VirtualBox: VBoxManage fails to start"
date: 2007-11-26
forum: Virtualisation
---

### Post by snaileater on 2007-11-26
I attempt to configure a fresh installed VirtualBox 1.5.0_OSE on Gutsy.
Here my command sequence:
sudo su
cd /usr/lib/virtualbox
./VBoxManage

./VBoxManage results in this error message:
./VBoxManage: error while loading shared libraries: VBoxDDU.so: cannot open shared object file: No such file or directory

ls -l VBoxDDU.so prints:
-rw-r--r-- 1 root root   85892 2007-10-15 16:54 VBoxDDU.so

so VBoxDDU.so obviously exists in /usr/lib/virtualbox

What is wrong?

---

### Post by jba6511 on 2007-11-27
are you a member of the virtualbox group?

---

### Post by snaileater on 2007-11-28
Yes, I'member of the virtualbox group.

Do I need to define some environment variable to point to the folder containing VBoxDDU.so?

---

### Post by goobsoft on 2007-12-27
Instead of running VBoxManage, you need to run vboxmanage

[http://lists.alioth.debian.org/pipermail/pkg-virtualbox-devel/2007-October/000058.html](http://lists.alioth.debian.org/pipermail/pkg-virtualbox-devel/2007-October/000058.html)

---

