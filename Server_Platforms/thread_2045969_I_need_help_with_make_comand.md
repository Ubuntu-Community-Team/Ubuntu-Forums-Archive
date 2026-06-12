---
title: "I need help with make comand"
date: 2012-08-22
forum: Server Platforms
---

### Post by nikibg on 2012-08-22
Hi,
can someone give me literature for make menuconfig to see for what is all options

---

### Post by miegiel on 2012-08-22
> **nikibg said:**
> Hi,
can someone give me literature for make menuconfig to see for what is all options

Do:
```
man make
```
or go to
[http://manpages.ubuntu.com/manpages/precise/en/man1/make.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/make.1.html)
and
[http://manpages.ubuntu.com/manpages/precise/en/man1/make.1posix.html](http://manpages.ubuntu.com/manpages/precise/en/man1/make.1posix.html)

A warning in advance: I quit compiling stuff and make .deb packages instead. It's much easier to uninstall a package later if you want to.

---

### Post by SeijiSensei on 2012-08-22
"make menuconfig" is usually a part of compiling the Linux kernel.  Why are you bothering to do that?  Is there something missing from the stock kernel that you need?  Otherwise you should stick to the Ubuntu kernel releases since they have been thoroughly tested.  I haven't compiled a kernel in at least half-a-dozen years, probably longer.

If you're looking to experiment with a cutting-edge kernel, add [this repository](https://launchpad.net/~kernel-ppa/+archive/ppa) to your software sources, run "sudo apt-get update", then run "sudo install linux-image-3.x.xx-generic" using the kernel version you're interested in testing.

---

