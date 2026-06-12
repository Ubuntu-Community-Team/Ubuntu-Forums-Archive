---
title: "MetaPackage Questions"
date: 2011-08-10
forum: The Cafe
---

### Post by GreenDance on 2011-08-10
Hi, could someone tell me please, how would I go about downloading a metapackage, editing it's contents, rebuilding the metapackage and installing it.

Thank You :popcorn:

---

### Post by capink on 2011-08-10
```
aptitude download <metapackage>

mkdir -p metapackage/DEBIAN

dpkg --extract <metapackage_version_arch.deb> metapackage

dpkg --control <metapackage_version_arch.deb> metapackage/DEBIAN
```



now edit the contetns of the metapackage folder (the control files will be at metapackage/DEBIAN). After finishing run


sudo chroot root.root -R metapackage

```
sudo dpkg -b metapackage metapackage.deb
```

---

### Post by GreenDance on 2011-08-10
> **capink said:**
> ```
aptitude download <metapackage>

mkdir -p metapackage/DEBIAN

dpkg --extract <metapackage_version_arch.deb> metapackage

dpkg --control <metapackage_version_arch.deb> metapackage/DEBIAN
```



now edit the contetns of the metapackage folder (the control files will be at metapackage/DEBIAN). After finishing run


sudo chroot root.root -R metapackage

```
sudo dpkg -b metapackage metapackage.deb
```

Thank You Very Much :popcorn:

---

### Post by GreenDance on 2011-08-10
Hi, I'm trying to install my edited .deb file, when I type

**dpkg -i metapackage.deb** I get errors, dependency problems,

e.g. 
*_package_* depends on package; however;
package *_package_* is not installed.

Any idea's how I could fix this please?

---

### Post by capink on 2011-08-10
```
sudo apt-get install gdebi

sudo gdebi metapackage.deb
```

---

