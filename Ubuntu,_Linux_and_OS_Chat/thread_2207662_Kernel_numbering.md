---
title: "Kernel numbering"
date: 2014-02-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Mariusz_Grecki on 2014-02-24
Hi,I am completely confused with kernel numbering. I have read about the scheme how it is organised etc. The problem is different. I need to modify the usb audio driver for the machine with kernel (uname -r gives that) 3.2.0-58-generic. Ok,  I found /lib/modules/3.2.0-58-generic but when I dig into build and look at the Makefile at the top I found:VERSION = 3PATCHLEVEL = 2SUBLEVEL = 53EXTRAVERSION =NAME = Saber-toothed SquirrelThe same I can find in the kernel sources - the kernel version tagged as Ubuntu-3.2.0-58.88 in git claims in the Makefile:VERSION = 3PATCHLEVEL = 2SUBLEVEL = 53EXTRAVERSION =NAME = Saber-toothed Squirrelso it is apparently consistent and I finally found the right kernel. But why it is organised like that?PS. The 'cat /proc/version_signature ' gives also:Ubuntu 3.2.0-58.88-generic 3.2.53

---

### Post by Dave_L on 2014-02-24
Do these articles answer your question?

[https://wiki.ubuntu.com/Kernel/FAQ](https://wiki.ubuntu.com/Kernel/FAQ)
[http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html)

---

### Post by kostkon on 2014-02-24
> **Mariusz_Grecki said:**
> Hi,I am completely confused with kernel numbering. I have read about the scheme how it is organised etc. The problem is different. I need to modify the usb audio driver for the machine with kernel (uname -r gives that) 3.2.0-58-generic. Ok,  I found /lib/modules/3.2.0-58-generic but when I dig into build and look at the Makefile at the top I found:VERSION = 3PATCHLEVEL = 2SUBLEVEL = 53EXTRAVERSION =NAME = Saber-toothed SquirrelThe same I can find in the kernel sources - the kernel version tagged as Ubuntu-3.2.0-58.88 in git claims in the Makefile:VERSION = 3PATCHLEVEL = 2SUBLEVEL = 53EXTRAVERSION =NAME = Saber-toothed Squirrelso it is apparently consistent and I finally found the right kernel. But why it is organised like that?PS. The 'cat /proc/version_signature ' gives also:Ubuntu 3.2.0-58.88-generic 3.2.53
If you are on 12.04 then instead of patching the 3.2 kernel you could try first upgrading to the latest [LTS enablement stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"), which will install the kernel (version 3.11) and X from Saucy, aka 13.10, and see if that will improve your situation.

Just follow the instructions and then reboot.

Hope that helps.

---

### Post by Mariusz_Grecki on 2014-02-26
thanks Dave_L and kostkon for your help.

---

