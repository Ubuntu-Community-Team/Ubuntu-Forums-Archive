---
title: "Cannot upgrade VirtualBox on Natty"
date: 2011-10-06
forum: Virtualisation
---

### Post by leptonrover on 2011-10-06
Having recently upgraded to Natty Narwhal I have now attempted to update Virtual box.
It seemed to go OK - Virtual box window manager appears OK but then attempting to start Vista brought up error messages:
"vboxdrv not loaded - install DKMS package first"
The DKMS install does not cure the problem and the log file is:
------------
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  4.1.4

------------------------------
Deleting module version: 4.1.4
completely from the DKMS tree.
------------------------------
Done.
  removing old DKMS module vboxdrv version  3.2.6
  removing old DKMS module vboxdrv version  3.2.6
  removing old DKMS module vboxdrv version  3.2.6
  removing old DKMS module vboxdrv version  3.2.6
  removing old DKMS module vboxnetflt version  3.2.6
  removing old DKMS module vboxnetflt version  3.2.6
  removing old DKMS module vboxnetflt version  3.2.6
  removing old DKMS module vboxnetflt version  3.2.6
  removing old DKMS module vboxnetadp version  3.2.6
  removing old DKMS module vboxnetadp version  3.2.6
  removing old DKMS module vboxnetadp version  3.2.6
  removing old DKMS module vboxnetadp version  3.2.6
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.1.4/source ->
                 /usr/src/vboxhost-4.1.4

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.38-11-generic-pae package.
Failed to install using DKMS, attempting to install without
Makefile:172: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.
----------
I have now got to the "help please " stage.

regards
Roger

---

### Post by CharlesA on 2011-10-06
How did you install the new version?

EDIT: I also moved the post to its own thread.

---

