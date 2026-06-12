---
title: "Unable to install wine1.6 on saucy"
date: 2013-08-02
forum: Ubuntu Development Version
---

### Post by cshubhamrao on 2013-08-02
H iam unable to install wine 1.6 on Saucy. Any Hellp?

---

### Post by jfernyhough on 2013-08-02
As happens regularly during the development process, as packages are updated other packages need to be rebuilt. At the moment, there are a number of packages incompatible with the latest gvfs update. So you can either wait, or manually downgrade gvfs and its related packages (and all other packages since updated to be compatible) to a previous version.

I'd wait.

---

### Post by xeizoo on 2013-08-03
I had the same problem, but wine1.4 works ok so just wait is the right thing to do(I run Photoshop 7 using it, the need for gaming support has lessened since native Steam became true)  :-)

---

### Post by Sworddragon on 2013-08-04
This happens because Wine from the WineHQ ppa depends on libgphoto2-port0 which is not available anymore (it was replaced with libgphoto2-port10). Wine needs just to update its dependencies and all is working fine again: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1208125](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1208125)

---

### Post by D3NMOH on 2013-08-05
maybe just make a transitional meta-package "[COLOR=#000000]libgphoto2-port0" ?[/COLOR]
because required files are included in [COLOR=#000000]libgphoto2-port10[/COLOR]

---

