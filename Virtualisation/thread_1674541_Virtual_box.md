---
title: "Virtual box"
date: 2011-01-24
forum: Virtualisation
---

### Post by stevepetmonkey on 2011-01-24
I have started to get error when trying to run virtual machines on Oracle Virtual Box
**this is what I get:**
--------------------------------
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
--------------------------------------

**Try that and get this:**

---------------------------------

monkey@monkey-desktop:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                              /etc/init.d/vboxdrv: 384: cannot create /var/log/vbox-install.log: Permission denied
 *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  /etc/init.d/vboxdrv: 384: cannot create /var/log/vbox-install.log: Permission denied

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        /etc/init.d/vboxdrv: 384: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
monkey@monkey-desktop:~$ 

---------------------------

**Any ideas whats wrong??**

---

### Post by ajgreeny on 2011-01-24
That command needs to be run as root, so try ```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by stevepetmonkey on 2011-01-25
Thankyou, thats seems to have sorted it.

---

