---
title: "KVM interferes with VBOX start of a VM"
date: 2011-02-16
forum: Virtualisation
---

### Post by sdowney717 on 2011-02-16
so i wrote a little script file to run when I reboot and want to start a VM

BUT, I dont want to run this al the time after a reboot. How do I fix this. I do have dkms installed

all this started after installing KVM

> scott@scott-desktop:~/Desktop$ ./kvmremove.sh
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service libvirt-bin stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop libvirt-bin
libvirt-bin stop/waiting

 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                   *  done.
 * Starting VirtualBox kernel modules                                            *  done.
scott@scott-desktop:~/Desktop$ 


> gksudo /etc/init.d/libvirt-bin stop
sudo modprobe -r kvm_intel
sudo modprobe -r kvm


gksu /etc/init.d/vboxdrv.dpkg-dist setup


---

