---
title: "Cannot install ia32-libs-multiarch:i386"
date: 2012-11-08
forum: Ubuntu Development Version
---

### Post by sparker256 on 2012-11-08
I did reinstall using todays daily build raring-desktop-amd64-20121108.iso and am trying to install ia32-libs-multiarch:i386. Using Ubuntu Software Center I am getting the following errors.

```

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

the following packages have unmet dependencies:

ia32-libs-multiarch:i386:

```

Thanks Bill

---

### Post by funicorn on 2012-11-09
ia32-libs-multiarch:i386 is only needed when you have to input chinese using ibus under i386 environment on the amd64 platform. In that case you have to make ibus-gtk:i386 work to type in Chines, and ibus-gtk:i386 depends on ia32-libs:i386 and hence ia32-libs-multiarch:i386. Are you sure you really need it ?

---

### Post by sparker256 on 2012-11-09
> **funicorn said:**
> ia32-libs-multiarch:i386 is only needed when you have to input chinese using ibus under i386 environment on the amd64 platform. In that case you have to make ibus-gtk:i386 work to type in Chines, and ibus-gtk:i386 depends on ia32-libs:i386 and hence ia32-libs-multiarch:i386. Are you sure you really need it ?
Yes since my machine runs X-Plane I need it to work and did work before I reinstalled. 

I up graded from 12.10 and it was still working but when I did the re install then I can no longer install ia32-libs-multiarch:i386 or X-Plane.

Bill

---

### Post by mc4man on 2012-11-09
Maybe it will shakeout for you down the road. (or if not & if your x-plane doesn't need gvfs, gvfs-libs (i386) then try installing the i386 packages it does.

I think the issue currently is gvfs-libs in raring now deps on libsecret-1-0 which deps on libsecret-common which likely has no "libsecret-common:i386"  installation candidate
(libsecret-common would already be installed & is an 'all.deb', ie. i386

Edit: there may be other gvfs*:i386 issues as well

---

### Post by mc4man on 2012-11-09
As soon as you upgrade libsecret* to 0.11-0ubuntu2 then you'll be able to install ia32-libs-multiarch:i386
(libsecret got some multiarch whatever
> libsecret (0.11-0ubuntu2) raring; urgency=medium

  * debian/control:
    - Add multiarch annotations and pre-depends (LP: #1073269)

---

### Post by sparker256 on 2012-11-09
Did a re install with todays daily build raring-desktop-amd64-20121109.iso and all is well again.

Bill

---

