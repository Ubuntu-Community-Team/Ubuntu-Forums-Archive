---
title: "Problems making a usb to work with a windows 10 virtual machine."
date: 2017-10-29
forum: Virtualisation
---

### Post by philp1863 on 2017-10-29
Hi
I get the impression that what I am trying to do should just work???  I think that I am missing something obvious? This is the first time I am trying a virtual machine.  In the past I have always used grub.
I have started windows 10 using the virtual machine manager(1.4). Windows 10 seems to run ok.
However I would also like to be able to plug a usb into the PC and get the guest windows 10 operating system to mount it.  Unfortunately the host Ubuntu operating system always wants to mount it, even when I am happily running windows 10 as a VM.
When I show the virtual hardware details. If I select usb redirector 1. It just says Type SpiceVMC.
No options are available, what can I do with this? 
 I read this in the "The Virtualization Mega-Thread".[FONT=Times New Roman]kvm 
> [SIZE=2]_KVM / Qemu_[/SIZE]
USB disks work fine in KVM and QEMU. Again, make your user part of the disk group and use the flag 
     Code:
kvm -hdb /dev/sdb1 ... 

where "/dev/sdb1" is the usb disk you wish to use.
For other usb devices, use the -usb flag.


Is this relevant for what I am trying to do?  
I have also been googling around and get the impression that it is not that difficult to do this using the virtual manager gui??
Could someone please put me out of my misery or point me to a link that I should follow?
Thanks for your help

[/FONT]

---

### Post by ODTech on 2017-10-31
> **philp1863 said:**
> Hi
I get the impression that what I am trying to do should just work???  I think that I am missing something obvious? This is the first time I am trying a virtual machine.  In the past I have always used grub.
I have started windows 10 using the virtual machine manager(1.4). Windows 10 seems to run ok.
However I would also like to be able to plug a usb into the PC and get the guest windows 10 operating system to mount it.  Unfortunately the host Ubuntu operating system always wants to mount it, even when I am happily running windows 10 as a VM.
When I show the virtual hardware details. If I select usb redirector 1. It just says Type SpiceVMC.
No options are available, what can I do with this? 
 I read this in the "The Virtualization Mega-Thread".[FONT=Times New Roman]kvm 


Is this relevant for what I am trying to do?  
I have also been googling around and get the impression that it is not that difficult to do this using the virtual manager gui??
Could someone please put me out of my misery or point me to a link that I should follow?
Thanks for your help

[/FONT]

I also tried to use the virt manager when i started out with my vm and couldn't figure out how to get certain things done so i switched to using a bash script containing qemu commands to start the VM. 
From the terminal you can issue commands to the vm. Passing a usb drive for example is as easy as the following.

To identify the usb drive type
```
lsusb
```
Output
```
Bus 003 Device 013: ID **125f:c08a** A-DATA Technology Co., Ltd. C008 Flash Drive
```
Now that i have the bus address i just issue the following command to pass it through.
```
usb_add host:**125f:c08a**
```

---

### Post by philp1863 on 2017-11-01
Thank you ODTech for that suggestion. I must apologize for being a bit of a novice here.
I typed
> virsh
into a terminal window and then used this virtual shell to start the VM.
Unfortunately on my system usb_add is not recognized anywhere so I am not sure where I should type this in?
Could you shed any light on this?

I notice that in the virtual shell there is an attach-device command. I will look into that as well.
Thanks again for your suggestion and help

---

### Post by philp1863 on 2017-11-01
Sorry there seems to be so many different ways that you can do this virtualisation.  I think that I see from your reply that I should try and download qemu and see how that helps me. Thanks

---

