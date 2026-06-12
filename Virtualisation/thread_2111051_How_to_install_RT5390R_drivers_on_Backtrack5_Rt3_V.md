---
title: "How to install RT5390R drivers on Backtrack5 Rt3 VM??"
date: 2013-01-31
forum: Virtualisation
---

### Post by Rnunez95 on 2013-01-31
Hey guys i cant seem to get my drivers on linux OS at all i searched high and low and nothing at all someone help? 
I am running it on a virtual machine on windows 8 im kind of a noob at this lol :redface:

---

### Post by varunendra on 2013-02-14
[I]Thread moved to **Virtualisation**, and Title changed from :
"How to install RT5390R drivers on Backtrack5 Rt3??"
to :
"How to install RT5390R drivers on Backtrack5 Rt3 **VM**??"[/I]
----------------------------------------------------------------------------------------

First of all, welcome to the forums! :)

Hope I'm not too late.

Please note that a Virtual Machine does not see your physical (real) hardware, but only a virtualized version of it.

Therefore the drivers are also different for the VMs, and are often supplied with the virtualization platform *(i.e., the virtualization software you are using)* for supported OS versions.

For example, if you are using VirtualBox, you have to install "Guest Additions" (on a running VM menu, **Devices > "Install Guest Additions...**"). In VMware, it is called "VMware tools" (**VM > Install VMware tools...**).

This will install all the drivers for all the hardware that the guest OS *(the one running in the VM)* can see, provided it is supported by the version of the virtualization softwareyou are using.

As for backtrack (upto version 5), I believe it is fully supported on all new versions of VBox/VMware.

Feel free to post back if you need further help with it.

---

### Post by Rnunez95 on 2013-02-14
The guest drivers are already installed everything works perfect on it except the wireless drivers :( even the screen resolution is perfectsize!

---

### Post by varunendra on 2013-02-15
> **Rnunez95 said:**
> The guest drivers are already installed everything works perfect on it except the wireless drivers :( even the screen resolution is perfectsize!
Unfortunately, the VM can't even see the wireless interface. It will only see the virtual ethernet adapter using the guest driver.

If the wireless adapter is working on the host system, the guest OS can 'talk' to it through its virtual interface using various methods like NAT or bridge.

It simply can not handle or control 'any' real hardware directly.

What is your purpose by the way?

If it is to be able to use internet or local networking on the VM, you should be able to do it easily if the host is able to use the network.

However, if it is something like experimenting with wireless, then a VM is a dead end, unfortunately. You must do a physical installation for that purpose.

---

### Post by Rnunez95 on 2013-02-15
Well that sucks then! Guess il have to dual boot. Know of any good step by step guides to dual booting windows8 and backtrack5? Everytime i try to load the installation ising a usb stock it opens up a file browser instead of running the iso

---

### Post by haqking on 2013-02-15
> **varunendra said:**
> Unfortunately, the VM can't even see the wireless interface. It will only see the virtual ethernet adapter using the guest driver.

If the wireless adapter is working on the host system, the guest OS can 'talk' to it through its virtual interface using various methods like NAT or bridge.

It simply can not handle or control 'any' real hardware directly.

What is your purpose by the way?

If it is to be able to use internet or local networking on the VM, you should be able to do it easily if the host is able to use the network.

However, if it is something like experimenting with wireless, then a VM is a dead end, unfortunately. You must do a physical installation for that purpose.

That is not true unless you refer to built in hardware such as a PCI device, a VM can talk directly to a USB device and does not virtualise it, by mounting the USB  wireless device into the VM by using a filter or selecting the device from the devices menu it is talking to it as real hardware, as for if it works that depends exactly the same as if it was on the host and if supported.

@ OP better checking in Backtrack forums for people who may be using this driver, I myself have no experience of it in BT I use many chipsets, you can check support for it here [http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers](http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers)

or the forums are here [http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)

As I said a USB device is not virtualised so dont worry about it being in a VM but you do need the guest additions and extensions pack and your user in the vboxusers group for full USB access and support. if its a built in wireless device to your host then yes it will be virtualised.

To use wireless in a VM you need a USB device, if you want to use your hosts PCI wireless device you can use as it a ethx device but it will be virtualised and wont act as a wireless adapter as varunendra said.

Peace

---

### Post by varunendra on 2013-02-15
> **haqking said:**
> That is not true unless you refer to built in hardware such as a PCI device, a VM can talk directly to a USB device and does not virtualise it
Oh yes, I totally overlooked the USB scenario and must admit it was a HUGE mistake. I stand corrected.. :redface:

Thank you for correcting me in time!

---

### Post by haqking on 2013-02-16
> **varunendra said:**
> Oh yes, I totally overlooked the USB scenario and must admit it was a HUGE mistake. I stand corrected.. :redface:

Thank you for correcting me in time!

no problem, I thought I would butt in as it is often overlooked and often people think that its impossible to use wireless in a VM.

Peace

---

