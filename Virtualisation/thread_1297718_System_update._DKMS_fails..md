---
title: "System update. DKMS fails."
date: 2009-10-22
forum: Virtualisation
---

### Post by oraerk on 2009-10-22
Given: Ubuntu 9.04 with VirtualBox 3.0.4 PUEL.

After doing **sudo aptitude update** and **sudo aptitude upgrade** the following happens:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
Resolving dependencies...
The following NEW packages will be installed:
  linux-headers-2.6.28-16{a} linux-headers-2.6.28-16-generic{a} linux-image-2.6.28-16-generic{a} linux-restricted-modules-2.6.28-16-generic{a} 
The following packages will be upgraded:
  libpoppler-glib4 libpoppler4 linux-generic linux-headers-generic linux-image-generic linux-libc-dev linux-restricted-modules-common linux-restricted-modules-generic 
  poppler-utils 
9 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.5MB of archives. After unpacking 173MB will be used.
Do you want to continue? [Y/n/?] 

```I say "yes" and then the following happens:
```

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-16-generic                                                                                                              
 *  vboxdrv (3.0.4)...                                                                                                                                                              
 vboxdrv (3.0.4): Unable to locate /var/lib/dkms/vboxdrv/3.0.4/source/dkms.conf
    DKMS tree must be manually fixed.

 *  vboxnetadp (3.0.4)...                                                                                                                                                           
 vboxnetadp (3.0.4): Unable to locate /var/lib/dkms/vboxnetadp/3.0.4/source/dkms.conf
    DKMS tree must be manually fixed.

 *  vboxnetflt (3.0.4)...                                                                                                                                                           
 vboxnetflt (3.0.4): Unable to locate /var/lib/dkms/vboxnetflt/3.0.4/source/dkms.conf
    DKMS tree must be manually fixed.

```Trying to **locate dkms.conf**. It is here:
```
/etc/modprobe.d/dkms.conf
/usr/share/virtualbox/src/vboxdrv/dkms.conf
/usr/share/virtualbox/src/vboxnetadp/dkms.conf
/usr/share/virtualbox/src/vboxnetflt/dkms.conf
/var/lib/dkms/vboxdrv/3.0.4/build/dkms.conf
/var/lib/dkms/vboxnetadp/3.0.4/build/dkms.conf
/var/lib/dkms/vboxnetflt/3.0.4/build/dkms.conf
/var/lib/dpkg/info/dkms.conffiles
```That's clear why it was not possible to find modules on the needed paths.
After reboot it says that there is no vbox module. Nah... obvious. I guess somewhere in the paths is smth wrong. Just unsure where to start digging, any thoughts?

---

