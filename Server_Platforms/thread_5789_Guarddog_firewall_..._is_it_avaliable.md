---
title: "Guarddog firewall ... is it avaliable?"
date: 2004-11-22
forum: Server Platforms
---

### Post by svarreby on 2004-11-22
I have never been a fan of Firestarter ... I've always opted for Guarddog when it's avaliable in a package.

Does anyone know if there's a Ubuntu-package for Guarddog?

---

### Post by jdong on 2004-11-22
```

 apjdong@jd64:~ $ apt-cache show guarddog
 Package: guarddog
 Priority: optional
 Section: universe/net
 Installed-Size: 1112
 Maintainer: Paul Cupis <paul@cupis.co.uk>
 Architecture: i386
 Version: 2.3.2-1
 Depends: kdelibs4 (>= 4:3.2.3), libart-2.0-2 (>= 2.3.16), libc6 (>= 2.3.2.ds1-4), libfam0c102, libgcc1 (>= 1:3.4.1-3), libice6 | xlibs (>> 4.1.0), libpng12-0 (>= 1.2.5.0-4), libqt3c102-mt (>= 3:3.2.3-3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxrender1, zlib1g (>= 1:1.2.1), gawk
 Filename: pool/universe/g/guarddog/guarddog_2.3.2-1_i386.deb
 Size: 310206
 MD5sum: 76a3309f8f7adf01c04471ae3a675e91
 Description: firewall configuration utility for KDE
  Guarddog is a firewall configuration utility for KDE. It is aimed at two
  groups of users: novice to intermediate users who are not experts in TCP/IP
  networking and security, and those users who don't want the hassle of
  dealing with cryptic shell scripts and ipchains/iptables parameters.
 Bugs: mailto:ubuntu-users@lists.ubuntu.com
 Origin: Ubuntu
 
 jdong@jd64:~ $
 
```
 
 Yes, it's available. GuardDog is really a KDE program, which may not fit into Gnome's look-and-feel too well. They both control the same firewall -- iptables -- so it makes little difference which interface you use.

---

