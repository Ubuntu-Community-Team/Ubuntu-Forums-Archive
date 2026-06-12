---
title: "lmms uninstallable in ubuntu studio 8.04?"
date: 2009-08-28
forum: Ubuntu Studio
---

### Post by rixtr66 on 2009-08-28
why cant i install the latest version of lmms?
ive added the repositories,but i get a message saying the following packages have unresolvable dependancies
libqt4-xml(>=4.4.0)but is not installable,etc.is there a workaround for this?please help.
Rick:(

---

### Post by scrooge_74 on 2009-08-28
Because some other library or app which depends on the same app cant be upgraded.

You need to upgrade the dependencies as well.

Post your source list

---

### Post by snowpine on 2009-08-28
The error message is telling you that whatever version you're trying to install depends on a newer "library" than what is found in 8.04. 

```
sudo apt-get install lmms
```

will give you the correct version of lmms for your Ubuntu release.

Understand that all of the applications in Hardy Heron 8.04 are over a year old.

You might try enabling the backports repository; I believe that will give you qt 4.4.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by rixtr66 on 2009-08-28
o.k thanks for the backport info!!!after the update from the backports,
i installed lmms from the console and it now works!:guitar:
thanks again!
Rick

---

