---
title: "Virtualbox kernel error"
date: 2008-08-26
forum: Virtualisation
---

### Post by Benjaminp on 2008-08-26
*Note, this Sun's xVM VirtualBox, not virtualbox OSE*

I turned on my virtual computer today (Ubuntu host, with Windows XP guest) and it wouldn't let me start it up. It gave me this error:
'---------------------------------------
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}
'-------------------------------------------
 Anyways, I ran the /etc/init.d/vboxdrv setup command, and it told me that there was an error compiling the kernel:

Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.2/source ->
                 /usr/src/vboxdrv-1.6.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-19-server cannot be found at
/lib/modules/2.6.24-19-server/build or /lib/modules/2.6.24-19-server/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

I have no idea where the kernel files are stored.. I've tried searching with synaptic, but no luck there.

Any way I can fix this?

---

### Post by b0b138 on 2008-08-26
make sure you have the linux-headers installed for your kernel. search synaptic for linux-headers.

---

