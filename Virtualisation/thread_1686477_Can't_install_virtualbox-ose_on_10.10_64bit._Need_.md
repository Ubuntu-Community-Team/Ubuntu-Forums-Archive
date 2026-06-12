---
title: "Can't install virtualbox-ose on 10.10 64bit. Need help."
date: 2011-02-12
forum: Virtualisation
---

### Post by ingramproductions on 2011-02-12
I was using virtualbox-ose fine at first, and then I removed through the software center so I could try out the non ose version. I then removed the non ose version, and reinstalled virtalbox-ose through the software center.


Now when I try to start a virtual machine, I get the error message, "Kernel driver not installed (rc=-1908) Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root".
So I run "sudo apt-get install virtualbox-ose-dkms", and I get,

"Setting up virtualbox-ose-dkms (3.2.8-dfsg-2ubuntu1) ...
Removing old virtualbox-ose-3.2.8 DKMS files...
/usr/lib/dkms/common.postinst: 135: dkms: not found
dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 virtualbox-ose-dkms"

Any ideas?

---

### Post by Mohrphium on 2011-04-07
Do you still have this problem?

---

### Post by dmelo on 2011-07-13
I had a similar problem after upgrading to ubuntu 11.04. Turns out the problem was being cause by the kernel I was using generic-pae . I put the steps I took to solve the problem on my blog ;) [http://diogomelo.net/blog/11/please-install-virtualbox-ose-dkms-package-and-execute-modprobe-vboxdrv-root]("http://diogomelo.net/blog/11/please-install-virtualbox-ose-dkms-package-and-execute-modprobe-vboxdrv-root")

---

### Post by ingramproductions on 2011-07-24
Thanks for the info. I actually ended up re-installing the OS

---

