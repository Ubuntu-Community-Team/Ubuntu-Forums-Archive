---
title: "ia32-libs"
date: 2012-05-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-05-26
Just down a dist-upgrade and in the process Google Earth was removed along with ia32-libs and ia32-libs-multiarch and now I can't reload either Google earth or ia32-libs, any thoughts on the subject would be appreciated.
Regards Miykel

---

### Post by Odur on 2012-05-27
Do you have the xorg-edgers ppa installed? If so it's because pixman failed to build on i386. Replace libpixman-1-0 (both amd64 and i386) with the versions from this repository [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing) and you will be able to install Google Earth again.

---

### Post by Miykel on 2012-05-29
Thanks for the help Odur; that allowed me to install ia32-libs, then Google Earth.
Kind Regards Miykel

---

### Post by Odur on 2012-05-29
I'm glad I could help you.

By the way, the pixman in xorg-edgers is now working again.

---

