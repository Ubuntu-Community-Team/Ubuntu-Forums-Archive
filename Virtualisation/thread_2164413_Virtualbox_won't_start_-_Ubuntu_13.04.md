---
title: "Virtualbox won't start - Ubuntu 13.04"
date: 2013-07-31
forum: Virtualisation
---

### Post by jamarsh123 on 2013-07-31
Used the Ubuntu software center to install Virtualbox.  My goal is to try a new Linux version called Bodhi.  When I press 'start', I get the following error message:  Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

I tried the command above and received the following message:
no such file or directory.

---

### Post by SeijiSensei on 2013-07-31
First, this is a common problem which has been answered often.  You need to install the tools to recompile the kernel.

However, I recommend you take an entirely different path.  Remove the version of VirtualBox that you installed from the repositories and install the version on the VirtualBox site itself.  Follow the instructions on [this page](https://www.virtualbox.org/wiki/Linux_Downloads) for "Debian-based" distributions.  Even though it is not in the list, you can install the version for 13.04 by adding this entry in /etc/apt/sources.list:

```
deb http://download.virtualbox.org/virtualbox/debian raring contrib
```

and following the remaining instructions on the VB site to install the Oracle public key.

Don't forget to install the [Extension Pack](http://download.virtualbox.org/virtualbox/4.2.16/Oracle_VM_VirtualBox_Extension_Pack-4.2.16-86992.vbox-extpack).

---

### Post by jamarsh123 on 2013-07-31
Thanks for your response.  I did try to search for this topic but did not find anything.  At any rate, I followed your instructions.  So far, no success; I get the same error message.  I pasted the 13.04 version in sources.list at the end of the file.  I did upgrade from 12.10; I don't know if this is important.  I wasn't sure what, if anything, to do with the key fingerprint.

---

### Post by yuanshizhu on 2013-07-31
You should download Virtualbox from [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

