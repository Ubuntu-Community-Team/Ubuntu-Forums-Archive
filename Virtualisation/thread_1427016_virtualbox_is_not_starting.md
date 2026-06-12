---
title: "virtualbox is not starting:"
date: 2010-03-11
forum: Virtualisation
---

### Post by savin on 2010-03-11
virtualbox is not starting:

error details:

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


so i recompiled


recompiling  /etc/init.d/vboxdrv setup:

 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

this s d log:

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-20-generic-pae/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1




help me on tis

---

### Post by suseendran.rengabashyam on 2010-03-11
Hi,

You can refer this thread for more details

[http://ubuntuforums.org/showthread.php?t=1163811](http://ubuntuforums.org/showthread.php?t=1163811)

Hope this helps.

---

### Post by savin on 2010-03-11
ya its fixd...


 i uninstalld and installd d new version after upgradin to karmic

---

