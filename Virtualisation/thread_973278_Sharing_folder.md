---
title: "Sharing folder"
date: 2008-11-06
forum: Virtualisation
---

### Post by ubuntuubuntu on 2008-11-06
I use Ubuntu under VirtualBox. I've just upgraded from Ubuntu 8.04 to Ubuntu 8.10, and now the folder sharing isn't working. When I use
 sudo mount -t vboxsf share /home/lse/share ,
I get the message /sbin/mount.vboxsf: mounting failed with the error: No such device .

When I type "sudo modprobe vboxvfs", I get the message

FATAL: Error inserting vboxvfs (/lib/modules/2.6.27-7-generic/updates/dkms/vboxvfs.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Does someone know how to solve this?
Thank you!

---

### Post by hashstat on 2008-11-13
I ran into the same problem.  After receiving the same error message I tailed /var/log/syslog for more info.  It appears that the vboxadd module is not being built properly by dkms; vboxvfs is unable to access symbols in the vboxadd module.

I was able to work around the problem by building the kernel modules without dkms.  I just removed the dkms package using apt.  But I imagine you could also temporarily rename dkms or move it from the PATH.  Then rerun the guest additions installer and reboot.

Without dkms, you will need to rebuild the modules whenever the kernel is updated.  But at least you can share your files.

---

