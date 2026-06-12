---
title: "Server Install Fails installing in to target"
date: 2008-09-06
forum: Server Platforms
---

### Post by ~Fianna on 2008-09-06
Okay, this box has been driving me insane for a week now, so I'm finally going to stop being stubborn and ask for help :)

Downloaded the latest server ISO.
The download hash matches.
Run the CD check at the start of install... checks out fine.

Go through the set-up, everything works great.

Do a simple partition on the first drive for / and swap, partitions fine.

Starts loading the system, gets to various points and then tells me that various parts are corrupt.  Once it was MySQL, once it was partman, once it was just unable to unpack the base system... last time it got all the way up to about 97% and then crapped out.  Got the red screen that says:

Unable to install the slected kernel
An error was returned while trying to install the kernel into the target system

Kernel package: 'linux server'.

Check /var/log/syslog or see virtual console 4 for the details

<continue>

Continue gets me the installation step failed screen.

Continue there takes me back to the menu.

Executing a shell to see the syslog, here's what it says for the section where it bombs:

<date><time> in-target: 8573 FILES AND DIRECTORIES CURRENTLY INSTALLED
UNPACKING LINUX-IMAGE-2.6.24-19-SERVER (FROM /LINUX-IMAGE-2.6.24-19-SERVER_2.6.24-19.34_AMD64.DEB ... ^M

debconf: Obsolete command TITLE Configuring linux-image-2.6.24-19-server called

in-target: DONE ^M
in-target: DPKG-DEB: SUBPROCESS PASTE KILLED BY SIGNAL (BROKEN PIPE) ^M

in-target: DPKG: ERROR PROCESSING /CDROM//POOL/MAIN/L/LINUX/LINUX-IMAGE-2.6.24-19-SERVER_2.6.24-19.34_AMD64.DEB (--UNPACK): ^M

in-target: SUBPROCESS DPKG-DEB --FSYS-TARFILE RETURNED ERROR IT STATUS 2^M (i'm assuming that something got cut off here, and it's probably INIT STATUS 2?)

in-target: SELECTING PREVIOUSLY DESLECTED PACKAGE LINUX-UBUNTU-MODULES-2.6.24-19-SERVER. ^M

in-target: UNPACKING LINUX-UBUNTU-MODULES-2.6.24-19-SERVER (FROM .../LINUX-UBUNTU-MODULES-2.6.24-19-SERVER_2.6.24-19.28_AMD64DEB)

in-target: DPKG-DEB: SUBPROCESS PASTE KILLED BY SIGNAL (BROKEN PIPE)

in target: SUBPROCESS DPKG-DEB --FSYS-TARFILE RETURNED ERROR

in-target: ERRORS WERE ENCOUNTERED WHILE PROCESSING:
in-target: /CDROM//POOL/MAIN/L/LINUX/LINUX-IMAGE-2.6.24-19-SERVER_2.6.24-19.34_AMD64.DEB

in-target: E: Sub-process /usr/bin/dpkg returned an error code 1

base-installer: error: exiting on error base-installer/kernel/ (something's cut off the screen here...) iled-install

WARNING **: Configuring 'bootstrap-base' failed with error code 1

WARNING **: Menu item 'bootstrap-base' failed

INFO: Modifying debconf priority limit from 'high' to 'medium'

debconf: Setting debconf/priority to medium

DEBUG: resolver (libnewt0.52)L package doesn't exist (ignored)

INFO: Falling back to the package description for console-setup-udeb

" for fdisk-udeb

" for console-setup-udeb

and that's where it shows me going in to the shell

Any thoughts on what the issue is and how I can get around it?

System is home-brew
Gigabyte mobo, everything onboard, no peripherals
AMD64 5000 processor
3 hd 160gb (sda1)/500gb (sda2)/500gb (sda3).  The 160 is partitioned to / and swap.  The other two are not partitioned at all (I was just going to do that from the CLI after the install)

Lemme know if there's anything else you want to see. :)



Thanks!!

---

### Post by windependence on 2008-09-06
Two things you can try:

When installing the boot loader, have it install lilo instead of grub.

If this doesn't work, disconnect from the network ehile doing the install and try it. Just unplug your LAN cable.

If neither of these work, then we may need to "zero" your disk. Let me know if neither of the above works and I will explain how to "clean" your disk.

-Tim

---

### Post by ~Fianna on 2008-09-06
> **windependence said:**
> Two things you can try:

When installing the boot loader, have it install lilo instead of grub.

If this doesn't work, disconnect from the network ehile doing the install and try it. Just unplug your LAN cable.

If neither of these work, then we may need to "zero" your disk. Let me know if neither of the above works and I will explain how to "clean" your disk.

-Tim

Zeroing out the disk worked.

Thanks for the tip - I was totally pulling my hair out.

---

