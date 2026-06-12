---
title: "[SOLVED] new kernel breaks vmware"
date: 2008-10-15
forum: Virtualisation
---

### Post by StOoZ on 2008-10-15
I tried to reconfigure it , no go , tried to reinstall it (1.07) , no go , when i try to run from the console , this is the errors im getting
> joe@joe-desktop:~$ sudo vmware
[sudo] password for joe:
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)


any idea?

---

### Post by anystupidname on 2008-10-15
I'm afraid that's a very common problem. You'll either have to use a softlink (temporarily) for gcc or install the version they want. You'll likely subsequently have to use the any any patch as well.
```
ln -sf /usr/bin/gcc<whatever> /usr/bin/gcc
```
or
```

sudo apt-get update
sudo apt-get install linux-headers-`uname -r` gcc build-essential
```

[http://blog.creonfx.com/temp/vmware-any-any-update-117-very-ALPHA.tgz](http://blog.creonfx.com/temp/vmware-any-any-update-117-very-ALPHA.tgz)
[http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2625-kernel](http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2625-kernel)

Good luck:)

---

### Post by StOoZ on 2008-10-16
I tried :
> sudo apt-get update
sudo apt-get install linux-headers-`uname -r` gcc build-essential

didnt work.

the other two links you provided , are for kernal version 25.

any idea how to fix this? :confused::(

---

### Post by StOoZ on 2008-10-16
ok problem solved.
I just moved > /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1:
(the problematic lib...) to another (anywhere you want...) dir.

---

