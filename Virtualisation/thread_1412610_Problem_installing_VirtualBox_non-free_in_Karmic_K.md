---
title: "Problem installing VirtualBox non-free in Karmic Koala AMD64"
date: 2010-02-21
forum: Virtualisation
---

### Post by toddk111 on 2010-02-21
I downloaded virtualbox-3.1_3.1.4-57640_Ubuntu_karmic_amd64.deb from the VirtualBox website and after I install it on my x64 machine and try to launch it, I get the following message:

```
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.31-19-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed
```

When I type in sudo /etc/init.d/vboxdrv I get the following message:

```
sudo: /etc/init.d/vboxdrv: command not found
```

Does anyone know what I should do to fix this problem?  Here is my install log:

```
** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.1.4/source ->
                 /usr/src/vboxdrv-3.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-19-generic -C /lib/modules/2.6.31-19-generic/build M=/var/lib/dkms/vboxdrv/3.1.4/build".............

Running the post_build script:
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-19-generic/updates/dkms/

depmod......

DKMS: install Completed.
** Compiling vboxnetflt
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetflt/3.1.4/source ->
                 /usr/src/vboxnetflt-3.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-19-generic -C /lib/modules/2.6.31-19-generic/build M=/var/lib/dkms/vboxnetflt/3.1.4/build"....
cleaning build area....

DKMS: build Completed.

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-19-generic/updates/dkms/

depmod....

DKMS: install Completed.
** Compiling vboxnetadp
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetadp/3.1.4/source ->
                 /usr/src/vboxnetadp-3.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-19-generic -C /lib/modules/2.6.31-19-generic/build M=/var/lib/dkms/vboxnetadp/3.1.4/build"....
cleaning build area....

DKMS: build Completed.

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-19-generic/updates/dkms/

depmod....

DKMS: install Completed.
```

Any suggestions would be appreciated. 

Thanks,
Todd

---

### Post by kiranmurari on 2010-02-22
Hi,

As you are installing from a .deb file, the errors could arise due to missing dependencies.
Please check if all the dependencies for the .deb are already installed. You can get the list of dependencies with the following command:
```
dpkg -I virtualbox-3.1_3.1.4-57640_Ubuntu_karmic_amd64.deb
```While installing from .deb file, dependency related errors are seen on the console.
Can you post the console log during the installation using the .deb file. And are you seeing something like:
```
dpkg: dependency problems prevent configuration of virtualbox-3.1:
 virtualbox-3.1 depends on libqt4-network (>= 4.5.1); however:
 Package libqt4-network is not installed.
 virtualbox-3.1 depends on libqt4-opengl (>= 4.5.1); however:
 Package libqt4-opengl is not installed.
 virtualbox-3.1 depends on libqtcore4 (>= 4.5.1); however:
 Package libqtcore4 is not installed.
 virtualbox-3.1 depends on libqtgui4 (>= 4.5.1); however:
 Package libqtgui4 is not installed.
dpkg: error processing virtualbox-3.1 (--install):
 dependency problems - leaving unconfigured
```You also need to have the kernel headers of the corresponding kernel version. The following command would install the kernel headers.
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by kiranmurari on 2010-02-22
I have simulated your problem and the following specifics might help:

First completely uninstall VirtualBox
```
$ sudo dpkg -P virtualbox-3.1
```Install the required dependencies
```
$ sudo apt-get install libqt4-network libqt4-opengl libqtcore4 libqtgui4 linux-headers-$(uname -r)
```Install VirtualBox
```
$ sudo dpkg -i virtualbox-3.1_3.1.4-57640_Ubuntu_karmic_amd64.deb
```Hope this helps.

---

### Post by toddk111 on 2010-02-23
Thank you SO much for the instructions.  That fixed my problem.  I really appreciate your help!

Take care,
Todd

---

