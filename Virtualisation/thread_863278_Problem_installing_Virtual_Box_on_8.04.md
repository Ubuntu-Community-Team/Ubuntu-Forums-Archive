---
title: "Problem installing Virtual Box on 8.04"
date: 2008-07-18
forum: Virtualisation
---

### Post by rlgates on 2008-07-18
Everyone,

I have attempted to install the virtualbox deb package on Ubuntu 8.04 and it failed. The followin is an except from the vbox-install.log. What is the easiest way to fix? Relatively new to Linux.

Thanks in advance.

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)

---

### Post by Potatoj316 on 2008-07-18
I think virtual box is in the repositories.  Try (in a terminal) "sudo aptitude install virtualbox" (no quotes)

---

### Post by icarus42 on 2008-07-18
The one in the repositories is great however it doesn't support USB. If you are new I would really recommend the one in the repositories like was previously mentioned.

However if you want USB, you can try sudo apt-get install -f, maybe that would fix the problem.

---

