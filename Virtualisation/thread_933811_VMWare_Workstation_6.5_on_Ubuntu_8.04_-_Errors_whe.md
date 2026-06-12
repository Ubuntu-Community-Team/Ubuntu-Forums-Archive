---
title: "VMWare Workstation 6.5 on Ubuntu 8.04 - Errors when VM shuts down"
date: 2008-09-29
forum: Virtualisation
---

### Post by Harry Muscle on 2008-09-29
I would like to make sure that I installed my copy of VMWare Workstation 6.5 properly on Ubuntu 8.04.  Basically all I did was download the "bundle" installer, which is a script that runs a visual installation and configures "everything" according to the manual.  The installation went fine and I was able to create a virtual machine without any issues, however, every time any virtual machine shuts down I get the following error:

***
Unable to change virtual machine power state: Failed to connect to peer process.
***

I also get a message mentioning:

***
VMware Workstation unrecoverable error: (mks)
Unexpected signal: 11.
***

So I'm wondering if I missed something with the way I installed it.  I read up a little on installing version 6 of the VMWare Workstation and there seem to be a lot more things to be done, however, the instructions generally talk about things that don't seem to be present on versoin 6.5 ... for example the vmware-config.pl script doesn't seem to exist for version 6.5 as far as I can tell.

If anyone has successfully installed version 6.5 or knows about a reliable tutorial if you could share the info that would be highly appreciated.  Also if you have any suggestions on how to fix the errors that I'm getting that would be great too.

Thanks,
Harry

---

### Post by Harry Muscle on 2008-09-30
I found the solution ... or at least cause of the problem.  If you disable the 3d acceleration of the virtual machine the error messages go away ... I guess the 3d stuff it's fully mature yet to work on all machines.

Harry

---

