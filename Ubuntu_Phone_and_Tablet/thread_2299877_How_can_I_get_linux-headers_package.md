---
title: "How can I get linux-headers package?"
date: 2015-10-22
forum: Ubuntu Phone and Tablet
---

### Post by kuh74 on 2015-10-22
A few days ago, I bought BQ Aquaris 4.5 Ubuntu Edition.

With Terminal-app installed, it really feel like full linux distro in my hand.

I want to compile a kernel module.

I am impressed with full system monitoring capability of Tomoyo MAC,

 and want to use its module version, Akari.

The default security of Ubuntu Touch is based on AppArmor,

and Akari can coexist with AppArmor while Tomoyo Linux can not.

So, using Akari, I can enjoy full system monitoring of Tomoyo, 

while preserving default security system of Ubutun Touch based on AppArmor.

Akari build instruction told me to obtain kernel header files with 'linux-headers' package.

With OTA-7, kernel version is '3.4.67' as given by `uname -r`.

So, I tried `apt-cache search linux-headers-3.4`

But, there is no linux-headers package for 3.4.67. (only version 3.4.0 exists) 

Is there any method to get proper kernel header files?

If 'header file' alone is not available, full source code of kernel will be ok.

Googling gave me link to full kernel source code for BQ Aquaris 4.5 at github.com,

but, it looks like a little outdated version, not OTA-7.

Any hint or web link will be appreciated.

---

