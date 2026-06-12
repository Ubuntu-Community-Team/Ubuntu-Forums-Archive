---
title: "Xlibs=? missed dummy package?"
date: 2006-09-15
forum: Repositories &amp; Backports
---

### Post by Omnios on 2006-09-15
Hi I have been playing around with installing some programs and am hitting a brick wall when it comes to  Xlibs. There is a dummy package in synaptic for devlibs-dev however they seemed to miss a dummy package for the actual xlibs. If you do sudo apt-get install Xlibs you get this.

```

Reading package lists... Done
Building dependency tree... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxft1 xkeyboard-config
E: Package xlibs has no installation candidate


```

 Anyways from what I seen I think we missed a dummy package for xlibs as there is one for xlibs-dev.

---

### Post by HAARP on 2006-09-16
There's a dummy package for xlibs around here somewhere in the forums.

---

### Post by Omnios on 2006-09-16
Found it. 

xlibs dummy.deb .zip
 [http://ubuntuforums.org/attachment.php?attachmentid=11386&d=1150598009](http://ubuntuforums.org/attachment.php?attachmentid=11386&d=1150598009)

---

