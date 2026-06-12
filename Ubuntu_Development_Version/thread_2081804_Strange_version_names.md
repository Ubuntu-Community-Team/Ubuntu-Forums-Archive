---
title: "Strange version names"
date: 2012-11-07
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2012-11-07
Sometimes I'm seeing version names like the current nvidia-current version: 304.51.really.304.43-0ubuntu2

Why is this version called with this name? If this package is really the version 304.43 why isn't it just called 304.43-0ubuntu2?

---

### Post by Mr. Picklesworth on 2012-11-07
This usually happens if a newer version of a package is uploaded, then gets reverted to an older version. It must be done this way because Debian treats the version field as both a functional thing (like a dependency) and an aesthetic thing (like a package description). It says both the version of the *package* (so the system knows when an update is available), as well as the version of the *software* in the package (so you can see it and think "oh, that's the newest version of the driver!").

In order to get systems that already have 305.51 to revert to that older version, they need to make the replacement package somehow have a "bigger" version number without breaking its property of communicating the (lower) upstream version number. These things usually get cleaned up fairly quickly &#8212; as soon as whatever was blocking the newer version gets fixed.

---

### Post by grahammechanical on 2012-11-08
Nvidia drivers are the responsibility of the Nvidia company. The 304.51 driver had a serious bug which was not there in 304.43 version of the driver. There is little the Ubuntu team can do about this except pass the bug reports back to Nvidia and wait until Nvidia fixes the problem.

I guess that the Ubuntu developers are trying to prevent a buggy driver from being installed.

Regards.

---

### Post by Harry33 on 2012-11-08
I think this naming to nvidia-current-updates is also a bit odd.

You see, the newest certified (stable) version is 304.64.
And that one has a name nvidia-current-updates in RR repo.
I thought beta versions (like 310.14) would bear the nvidia-current-updates naming.

Now this is mixed up. :guitar:

---

### Post by Sworddragon on 2012-11-12
> **Mr. Picklesworth said:**
> This usually happens if a newer version of a package is uploaded, then gets reverted to an older version. It must be done this way because Debian treats the version field as both a functional thing (like a dependency) and an aesthetic thing (like a package description). It says both the version of the *package* (so the system knows when an update is available), as well as the version of the *software* in the package (so you can see it and think "oh, that's the newest version of the driver!").

In order to get systems that already have 305.51 to revert to that older version, they need to make the replacement package somehow have a "bigger" version number without breaking its property of communicating the (lower) upstream version number. These things usually get cleaned up fairly quickly — as soon as whatever was blocking the newer version gets fixed.

This explanation makes sense.


> **Harry33 said:**
> I think this naming to nvidia-current-updates is also a bit odd.

You see, the newest certified (stable) version is 304.64.
And that one has a name nvidia-current-updates in RR repo.
I thought beta versions (like 310.14) would bear the nvidia-current-updates naming.

Now this is mixed up. :guitar:

There are even the packages nvidia-settings and nvidia-settings-updates which have currently the same version.

---

