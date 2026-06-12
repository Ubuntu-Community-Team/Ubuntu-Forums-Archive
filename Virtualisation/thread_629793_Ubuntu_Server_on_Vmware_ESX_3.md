---
title: "Ubuntu Server on Vmware ESX 3"
date: 2007-12-02
forum: Virtualisation
---

### Post by bitrod on 2007-12-02
Hello,

I have installed Ubuntu Server 7.10 in a Vmware ESX 3 environment, and everything seems on work fine.

Since it is an virtualised enviroment I installed linux-virtual that installs linux-image-virtual that is geared for virtual hardware. But when the system reboot with that kernel it hangs and after some time writes:

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/8568ba03.50f8-4b2d/ac78/ae8ddde5e067 does not exist. Dropping to a shell!

Any one knows what goes wrong ?

Thanks in advance..

---

### Post by GrammatonCleric on 2007-12-04
With what drive (SCSI or ATA) and "Distro" options did you build the Ubuntu VM with?  

Fyi.. I've never used the linux-virtual to build any of my ESX Ubuntu VMs.  I've opted to install the ESX vmware-tools instead.

-GC

---

### Post by bitrod on 2007-12-05
From the Virtual Infrastructure Client, I used the New Virtual Machine Wizards gave the VM a name, selected a datastore for it, and as guest operation system selected Linux - Linux Other... Gave it CPU, memory and the rest.

Then I booted it from the Ubuntu 7.10 Server CD, and followed a normal install.

---

### Post by jmuller on 2008-02-22
The problem is that the ubuntu virtual kernel does not work with the esx simulated lsi logic controller. The trick to get it to work is to change the controller to "bus logic" in esx server (Edit virtual machine settings -> go to "Scsi controller 0" and on the right click on "Change type")

If dont know if this works good when you already installed the os.

If you want to run the Linux Virtual kernel (which is more designed for vmware workstation etc) you'd better install ubuntu jeos 7.10 (just ubuntu but with the virtual kernel pre-installed, beware that you first change the scsi controller to bus logic before installing otherwise it wont boot after install)


My opinion is that ubuntu jeos / virtual kernel is simply not designed to run under esx. I had a lot of problems with it and the maintainers of the virtual kernel do not plan to support the lsi logic controller which simply results in less performace by using the old bus logic controller. If you need fast disk i/o dont install it.

---

