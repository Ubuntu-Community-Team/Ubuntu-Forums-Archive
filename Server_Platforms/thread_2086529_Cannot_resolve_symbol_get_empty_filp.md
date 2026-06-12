---
title: "Cannot resolve symbol get_empty_filp"
date: 2012-11-21
forum: Server Platforms
---

### Post by hiboujid on 2012-11-21
Hi
i am trying to install " Kaspersky Anti-Virus for Linux File Server" on a new installed Ubuntu Server 12.04

i installed :
sudo apt-get install build-essential
sudo apt-get install --reinstall linux-image-3.2.0-23-generic-pae
sudo apt-get install --reinstall linux-headers-generic-pae

then i executed :
/opt/kaspersky/kav4fs/bin/kav4fs-setup.pl --build=/usr/src/linux-headers-3.2.0-33-generic-pae

the actual error is :
[COLOR=Red]**checking for get_empty_filp... configure: error: "Cannot resolve symbol get_empty_filp"**[/COLOR]

the current server is a test one, i've just installed it, it's very clean

*********************************************************************************************
root@UbuntuServer:/home/virus#
root@UbuntuServer:/home/virus# uname -r
3.2.0-23-generic-pae
root@UbuntuServer:/home/virus#
root@UbuntuServer:/home/virus# ls /usr/src/
linux-headers-3.2.0-33  linux-headers-3.2.0-33-generic-pae
root@UbuntuServer:/home/virus#
root@UbuntuServer:/home/virus#
root@UbuntuServer:/home/virus#
root@UbuntuServer:/home/virus#
root@UbuntuServer:/home/virus#
root@UbuntuServer:/home/virus# /opt/kaspersky/kav4fs/bin/kav4fs-setup.pl --build=/usr/src/linux-headers-3.2.0-33-generic-pae

Kaspersky Anti-Virus for Linux File Server version 8.0.2.160/RELEASE


Setting up the kernel-level real-time protection

>>> Configuring the kernel-level real-time protection module using the Linux kernel source code from /usr/src/linux-headers-3.2.0-33-generic-pae
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
Debian wheezy/sid
checking for linux kernel sources... /usr/src/linux-headers-3.2.0-33-generic-pae
checking for linux kernel version file... /usr/src/linux-headers-3.2.0-33-generic-pae/include/generated/utsrelease.h
checking for linux kernel version... 3.2
checking for arch_ptrace... found, address 0
checking for access_process_vm... found, address 0
checking for __ptrace_link... found, address 0
checking for __ptrace_unlink... found, address 0
checking for ptrace_attach_task... found, address 0
checking for ptrace_attach_utrace... found, address 0
checking for get_empty_filp... configure: error: "Cannot resolve symbol get_empty_filp"

Warning: The kernel-level real-time protection module is not compiled.
To manually recompile the kernel-level real-time protection module, start
/opt/kaspersky/kav4fs/bin/kav4fs-setup.pl --build[=PATH].
root@UbuntuServer:/home/virus#
*********************************************************************************************

if i execute the command above without path :
/usr/src# /opt/kaspersky/kav4fs/bin/kav4fs-setup.pl --build
then the default proposed path is not working

*********************************************************************
root@UbuntuServer:**/usr/src# /opt/kaspersky/kav4fs/bin/kav4fs-setup.pl --build**

Kaspersky Anti-Virus for Linux File Server version 8.0.1.145/RELEASE


Setting up the kernel-level real-time protection

The installer found the source code for your Linux kernel. Press Enter to
confirm this path, or enter another path to the source code for your Linux
kernel, or enter 'cancel' to interrupt the compilation of the kernel-level
real-time protection module: [/lib/modules/3.2.0-23-generic-pae/build]:


**Warning: Couldn't find the Linux kernel source code in**
/lib/modules/3.2.0-23-generic-pae/build.

Warning: The kernel-level real-time protection module is not compiled.
To manually recompile the kernel-level real-time protection module, start
/opt/kaspersky/kav4fs/bin/kav4fs-setup.pl --build[=PATH].
root@UbuntuServer:/usr/src#
*********************************************************************

Thanks

---

