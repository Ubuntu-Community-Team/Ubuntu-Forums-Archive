---
title: "No VirtualBox modules for kernel 3.8.1"
date: 2013-03-01
forum: Virtualisation
---

### Post by Stonecold1995 on 2013-03-01
I just installed the generic kernel 3.8.1 via the .deb files, however, upon installing, they gave me an error from dkms saying the VirtualBox kernel modules could not be installed.  When I rebooted into the 3.8.1 kernel, I cannot run VirtualBox (the application gives me the error "Kernel driver not installed (rc=-1908)").

Where can I find the VirtualBox kernel drivers for 3.8.1?

---

### Post by Cheesemill on 2013-03-02
You need to install the headers for your kernel otherwise the kernel modules can't be built.

Running the standard kernel these can be installed by doing...
```
sudo apt-get install linux-headers-`uname -r`
```

However as you are using a non-standard kernel you will have to source the headers yourself, I presume that there will be a linux-headers-3.8.1.deb package to be found at the same place you downloaded your kernel from.

---

### Post by Grinage on 2013-03-02
there's also a virtual box quirk every time the kernel updates even a little you will often need to run this from root
/etc/init.d/vboxdrv setup
make sure you close all sessions of Virtualbox that are loaded or attempting to load and be patient it takes five to ten minutes to run at the longest.  If you want you can also downloat virtualbox dkms from the repositories, it's not required, but the setup will try with dkms first and if not found will move on.

---

