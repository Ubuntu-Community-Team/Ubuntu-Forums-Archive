---
title: "VBox kernel module problem"
date: 2009-01-29
forum: Virtualisation
---

### Post by rajcan on 2009-01-29
Hey, I'm running Kubuntu Intrepid and I just tried installing VBox 2.1.2 using the .deb from virtualbox.org and when I run it I get the following output:

(Reading database ... 114321 files and directories currently installed.)
Preparing to replace virtualbox-2.1 2.1.2-41885_Ubuntu_intrepid (using .../virtualbox-2.1_2.1.2-41885_Ubuntu_intrepid_i386.deb) ...
 * Stopping VirtualBox kernel module
 *  done.
Unpacking replacement virtualbox-2.1 ...
Setting up virtualbox-2.1 (2.1.2-41885_Ubuntu_intrepid) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
 * Starting VirtualBox kernel module

 * No suitable module for running kernel found



VBox then shows up in the applications menu, but I can't run any of the VMs I create. Anyone know what's going on?

---

### Post by rajcan on 2009-01-29
I may have found the solution. Here's the out put of /var/log/vbox-install.log

** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/2.1.2/source ->
                 /usr/src/vboxdrv-2.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-19-generic cannot be found at
/lib/modules/2.6.24-19-generic/build or /lib/modules/2.6.24-19-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.



It looks like it's looking for the kernel source in the wrong place. My question now is, where is that source?

---

### Post by rajcan on 2009-01-30
I fixed it, never mind. Come to find out I was booting into the wrong kernel. I just edited my /boot/grub/menu.lst file to boot up the latest kernel and it works just fine.

---

