---
title: "re-installation of packages via synaptic requires downloading"
date: 2019-10-16
forum: Ubuntu Development Version
---

### Post by Claus7 on 2019-10-16
Hello,

I was using Developer Options and from there I had enabled the Pre-released updates (eoan-proposed) and at some time a new kernel was installed. So far so good. Disabling that option, that new kernel was assigned as obsolete file, which is normal as well. 

It seems that during the normal upgrades of packages this one was updated accordingly, as a result it was removed from the obsolete section of synaptic and became a regular installed file. Reasonable as well.

Today, I tried to re-install those kernel files. To my surprise it required to download extra more than 100MB. I had noticed this before to other packages even without using the Developer Options, yet the extra data required were some KB. Of course the size of these packages is not compared with those of a kernel, yet still the difference is huge.

What does this mean? Is it that the installed package was missing some libraries? Is there a pattern that should be followed for some packages to get reinstalled? 

Regards!

---

### Post by Claus7 on 2019-10-20
Hello,

I noticed that for the packages in question, even if they have the same main version, they are actually quite different. Usually, when the proposed packages are installed, their version is completely different from that of a regular package. 

During the normal upgrades of the system, with proposed updates not selected any more, it can happen that the versions almost match, something that does not result in the substitution of the proposed package with the regular one. Re-installation though installs the regular version over the proposed one.

In the case of a regular package and its re-installation, some archive files are downloaded, which, from the definition of archive files, include metadata for the package in question. The metadata might have been updated, as a result download of this information is taking place.

Regards!

---

