---
title: "V Box in Ubuntu"
date: 2009-02-09
forum: Virtualisation
---

### Post by Bog_Warrior on 2009-02-09
Just trying to install and received this message in v-box install.log:

Attempting to install using DKMS
removing old DKMS module vboxdrv version

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.1.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.1.2/source ->
/usr/src/vboxdrv-2.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.22-14-generic cannot be found at
/lib/modules/2.6.22-14-generic/build or /lib/modules/2.6.22-14-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.

Too new to know what is going on here but I do have DKMS and "build-essentials" Packages installed.


Result Code:
NS_ERROR_FAILURE (0x80004005)
Component:
Machine
Interface:
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}

Thanks

BW

---

