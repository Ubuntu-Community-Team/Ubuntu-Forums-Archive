---
title: "Virtual box not working"
date: 2010-05-26
forum: Virtualisation
---

### Post by mick463 on 2010-05-26
Hi there i have installed Virtual Box on  64 bit 10.04 when i first installed it all the virtual machines hung or blue screened they just never installed.So i installed the virtual box from ubuntu software center and it did not work either. I then un installed it an re installed the latest virtualBox from sun microsystems. I am now getting this error.

Failed to open a session for the virtual machine Windows 7.


Virtual machine 'Windows 7' has terminated unexpectedly during startup with exit code 1.


DETAILS
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}



then this pops up

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I tried to go to the etc/init.d directory but the vboxdrv setup is not there i am at a loss as i love linux and all that it has to offer but i am at a loss as to what to do i am very new at this linux thing and realy need this sorted out thank you in advance.

---

### Post by jjbasken on 2010-05-26
Same thing happened to me also.
Each time I shutdown/restart my computer I have to run the setup for the kernel module in order to get my VM to start.

It looks like vboxdrv was renamed so I have been using:
/etc/init.d/vboxdrv.dpkg-bak setup

I don't know what the permanent solution is but this should at least allow you to startup your VM.

---

### Post by mick463 on 2010-05-26
Thank you i will give it a go in the morning

---

### Post by mick463 on 2010-05-28
Hey i just used an older version and it works fine. I do hope they fix the new one though.
And thank you to all that replied may good fortune smile upon you.

---

