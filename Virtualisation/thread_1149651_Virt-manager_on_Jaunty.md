---
title: "Virt-manager on Jaunty"
date: 2009-05-05
forum: Virtualisation
---

### Post by jkv on 2009-05-05
Hi,

I am using Jaunty as a virtualization(qemu/kvm) host, i have been using virt-manager 0.6.1 and it all worked quite fine.
Yesterday i decided to try out virt-manager 0.7.0 and downloaded and installed the .deb from launchpad. 
For some reason i cant add a new VM with virt-manager 0.7.0, the "forward" button remains grey, same goes for when i try to add a USB device with virt-manager 0.7.0
When i reinstalled virt-manager 0.6.1 i could add new VM's just fine again.

Any ideas to what might be the issue?

Regards,
jkv

---

### Post by Techie03 on 2009-05-13
I have this same exact problem.  Any luck in figuring it out?

---

### Post by geekshlby on 2009-05-13
I assume you could successfully create Virtual Machines with virt-manager 0.6.x.

When you update to 0.7 you also need to update virtinst 0.400.3 which is also available in the ppa.

---

### Post by Techie03 on 2009-05-14
I updated both virt-manager and virtinst, but still have the same issue.

---

### Post by Techie03 on 2009-05-14
Okay, got it to work.  Used the PPA installation.  Thanks!

---

### Post by bhaverkamp on 2009-05-14
What is the PPA installation please?

---

### Post by jkv on 2009-05-15
Perspnal packet archive, get it from here: [https://launchpad.net/~ricotz/+archive/ppa](https://launchpad.net/~ricotz/+archive/ppa)

> **bhaverkamp said:**
> What is the PPA installation please?

---

### Post by njx on 2009-07-26
Hi, 
I have updated to virt-manager 0.7.0 and can add a usb device but I cannot access the device contents from the guest. Please advice if there is a step am missing. 
thanks

---

### Post by gksmithlcw on 2009-09-01
How does one go about installing from this ppa?

Thanks!

*EDIT*

Nevermind, I figured it out. Now, if I could only figure out why USB isn't working...

---

### Post by bodhi.zazen on 2009-09-01
Personally I run KVM directly from the command like. More options and less problems then virt-manager.

No problems with USB from teh command line

kvm -hda /home/you/kvm/ubuntu.qcow2 -hdb /dev/sdb1 -usbdevice tablet &

---

### Post by gksmithlcw on 2009-09-01
> **bodhi.zazen said:**
> Personally I run KVM directly from the command like. More options and less problems then virt-manager.

No problems with USB from teh command line

kvm -hda /home/you/kvm/ubuntu.qcow2 -hdb /dev/sdb1 -usbdevice tablet &

I'm using libvirt and I've added the appropriate stuff to the config.xml file for my guest both manually and through virt-manager and neither scenario has worked.

The device, an external hard drive, shows up on the guest but will not work. It shows up in Windows Device Manager as a USB Mass Storage device but has an exclamation point and states that the device could not be started.

Off topic, I also have a 'PCI Card' that is showing as an exclamation point, any ideas what wouldn't have had proper driver support?

---

