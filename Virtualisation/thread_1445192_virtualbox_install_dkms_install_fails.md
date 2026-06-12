---
title: "virtualbox install dkms install fails?"
date: 2010-04-02
forum: Virtualisation
---

### Post by KevKing on 2010-04-02
Have just installed Virtualbox-3.1.on Ubuntu 9.04 server.  All looks to be installed apart from the dkms bit?   Get the following error when dkms tries to compile:  Attempting to install using DKMS   removing old DKMS module vboxdrv version  3.1.6  ------------------------------ Deleting module version: 3.1.6 completely from the DKMS tree. ------------------------------ Done.  Creating symlink /var/lib/dkms/vboxdrv/3.1.6/source ->                  /usr/src/vboxdrv-3.1.6  DKMS: add Completed.  Error! Your kernel source for kernel 2.6.32.2-xxxx-grs-ipv6-64 cannot be found at /lib/modules/2.6.32.2-xxxx-grs-ipv6-64/build or /lib/modules/2.6.32.2-xxxx-grs-ipv6-64/source. You can use the --kernelsourcedir option to tell DKMS where it's located. Failed to install using DKMS, attempting to install without Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR= and run Make again.  Stop.  Now obviously it cant find my kernel because it aint where it thinks it is, how can I remedy this, any one any ideas?  Could I copy my kernel to that default location and go from there or would that possibly cause issues when I upgrade the kernel in the future?  Any help would be much appreciated

---

