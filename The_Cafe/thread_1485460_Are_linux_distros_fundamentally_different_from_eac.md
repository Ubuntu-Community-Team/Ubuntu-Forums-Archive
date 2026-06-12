---
title: "Are linux distros fundamentally different from each other?"
date: 2010-05-16
forum: The Cafe
---

### Post by inquilinekea on 2010-05-16
Or is it possible, to say, "convert" one distro to another distro? (if you, say, install the packages that aren't originally in the distro installation but are packages in another distro). Or is it possible to pretty much import the features of one distro into another distro?

---

### Post by ryan858 on 2010-05-16
Packages wouldn't be cross-compatible... They are usually built for the specific distro and architecture that they are being used on. However, you can use source packages, which are architecture and OS independent. Mostly every program/utility for any linux distro is also available for many other distro's and has packages for different distro's, and also has it's source code available for download, which you can compile and install on any machine (even windows if you have the right build tools)

However, you would need the dependencies installed as well, on whatever OS you use the packages on. This is taken care of for you when the distro includes the packages in question, or with package managment tools, such as aptitude...

---

### Post by jerome1232 on 2010-05-16
You can convert rpm's to deb's. Those are just installers for two of the more popular package managers. (rpm being red hat based distro's and deb being debian based distro's).


There are difference's between the distro's in the default programs they come with and how they accomplish certain system functions. They will also differ in where they put configuration files exactly and sometimes the names of system and configuration files will differ slightly.

---

### Post by K.Mandla on 2010-05-16
I sometimes forcibly transplant binary files (compiled programs) from one system to another. Sometimes it works, sometimes it doesn't.

---

### Post by ryan858 on 2010-05-16
It is theoretically possible, but it's not by any means practical... You'd save a lot of time and energy to just re-download and install the packages for the specific distro & arch.

---

### Post by MisfitI38 on 2010-05-17
> **inquilinekea said:**
> Or is it possible, to say, "convert" one distro to another distro? (if you, say, install the packages that aren't originally in the distro installation but are packages in another distro). Or is it possible to pretty much import the features of one distro into another distro?

Absolutely, yes. [This guy]("http://bbs.archlinux.org/viewtopic.php?pid=730024#p730024") started with Gentoo and completely converted it to Arch, against all the naysayers' warnings and admonitions not to try it.
It can be a fun project. Part of the beauty of GNU/Linux is its transparency; nearly everything is readily accessible and available for change or substitution, using basic tools.

---

### Post by philinux on 2010-05-17
Thread moved to Community Cafe.

---

