---
title: "Convert from VMWare to OpenBox"
date: 2010-01-04
forum: Virtualisation
---

### Post by stevanbt on 2010-01-04
Hi,
Is it possible to convert a VM (Windows XP guest and Ubuntu host) from VMWare to VirtualBox?  

Thanks, Steve.

---

### Post by TJet1.8 on 2010-01-04
Hello Steve,

It is possible to convert the VMware .vmdk file to VBox .vdi format by invoking the following command:

VBoxManage clonehd source.vmdk destination.vdi --format VDI

You must then create a VBox vm using the virtual disk you just converted.

I don't believe you can out-right convert a complete vm (vm configuration files, virtual disks, etc...) from VMware to VBox...only the virtual disks.

Also (VERY IMPORTANT!!) :
Make sure you un-install the VMware Tools from your Guests in VMware BEFORE you un-install your VMware installation from your computer!!!
Otherwise, the VMware Tools will not un-install if it doesn't find VMware installed on your host.

Good luck :P

---

### Post by K.J. on 2010-01-04
Definitely try the above method first, although I've had it fail.

Another method is to boot the VM to a linux live cd and use DD to copy the virtual drive to another location and then do the reverse in VirtualBox.

---

### Post by stevanbt on 2010-01-05
Hi,
I've used VBoxManage to convert the vmkd images to vdi.  I then added them into a VirtualBox VM.  No errors reported from either operation, but it won't boot - all I get is a blank screen.

If I power off the VirtualBox VM and restart the XP VM reports that there was a problem starting windows previously and asks me what to do.  When I select 'start windows normally' the screen freezes and won't continue.

Any ideas?  Are there any VB logs I should be checking out?

Thanks, Steve.

---

### Post by TJet1.8 on 2010-01-05
Hi Steven,

You need to check a couple of things in your VBox vm configuration.

First, in your settings...go to the General/Basic Tab and ensure you have the correct Operating System selected (i.e. - Windows XP x32 or x64, etc...).

Second, in the System/Motherboard Tab...you may need to check the "Enable IO APIC" option for it to work. I had to do this for my vm's.

Let us know the results.

:)

---

### Post by stevanbt on 2010-01-05
Hi,
The "Enable IO APIC" got the VM to boot up.  Windows now thinks there are errors (minor ones by the looks) on one of the drives so it's performing a boot time disk check.  I get the feeling this could take a while.

Thanks, Steve.

---

### Post by irishwoody on 2010-01-06
I've converted a VMware virtual XP machine created in Vmware workstation runing under Vista to virtualbox 3.1 running in ubuntu 9.10

by
1. creating a new machine in virtualbox.
2. mounting the VMware virtual disk as the new machines disk.

Couple of problems came to light
1. The virtual disk would not boot in virtualbox due to a driver issue, think was agp 440.sys.  It crashed out when booting.  To solve the problem I ran it up in vmware and disabled the driver (remaned the file as far as I recall).  After that virtualbox woudl boot virtual xp machine.
2. Netwoking - had some issue loading the correct driver for virtualbox ontop of the vmware virtual network driver.  Got it working by selecting a different NIC card type in virtualbox.

Since then I have also tried running VMware machines created in Vista in ubuntu and this also works - although when they are on a NTFS spindle VMware runs hem very slowly.

Irishwoody

---

