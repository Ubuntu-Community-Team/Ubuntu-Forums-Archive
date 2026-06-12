---
title: "Debian Lenny help"
date: 2010-09-08
forum: The Cafe
---

### Post by Toast2120 on 2010-09-08
Using Debian Lenny on my second box for class. No GUI, command line only, with only the base install package. Tried to mount a ext4 partition when I realized that Debian Lenny is two versions behind when ext4 partitions were made stable. 

How can I update the kernel or get the package that contains the files to mount ext4? Preferably without compiling the kernel.

---

### Post by NightwishFan on 2010-09-08
Not sure if Debian backports gets a new kernel. You could go update to Testing/Squeeze though.

---

### Post by mikewhatever on 2010-09-08
[http://packages.debian.org/search?keywords=linux-image&searchon=names&section=all&suite=lenny-backports](http://packages.debian.org/search?keywords=linux-image&searchon=names&section=all&suite=lenny-backports)

Looks like 2.6.32 is in the backports for Lenny.

---

