---
title: "Request: cryptsetup-1.0"
date: 2005-06-07
forum: Ubuntu Backports
---

### Post by webwurst on 2005-06-07
[http://packages.ubuntu.com/breezy/admin/cryptsetup](http://packages.ubuntu.com/breezy/admin/cryptsetup)

version 1.0 has an important new feature:
[http://luks.endorphin.org/](http://luks.endorphin.org/)

---

### Post by jdong on 2005-06-07
Alright.

---

### Post by jdong on 2005-06-07
Ok, cryptsetup claims to need libdevmapper-dev 1.01 or higher, but only 1.00 is in Hoary. However, forcing the build to continue worked. Please test the package.

Thanks.

---

### Post by webwurst on 2005-06-30
at first view everything seems allright. i could create a crypted device and format it with ext3. i will check how it works on daily use, carefully ;)

---

