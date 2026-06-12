---
title: "Ubuntu will not recognize any USB in any of my ports.  Why?"
date: 2024-01-04
forum: Virtualisation
---

### Post by bobhurd on 2024-01-04
I am using Ubuntu 23.10.1.  I keep getting an error that states:

 "The device "PNY USB 3.2.2FD" was unable to connect to its ideal host controller.  AN attempt will be made to connect this device to the best available host controller.  This might result in undefined behavior for this device."

Then I get no USB icon in Ubuntu and no way to access it or the data I need on it.

I don't know what to do.

---

### Post by ActionParsnip on 2024-01-04
Looks like a run of the mill USB stick. Before you physically unplug the device do you use the "safe remove" feature in the OS before you yank it out?

What is the output of
```

sudo lsb_release -a; uname -a; sudo fdisk -l

```

---

### Post by yancek on 2024-01-04
Have you been able to successfully use this usb previously?  Does the usb contain only data?  What filesystem type is on the device?  Do you have a second computer you can use to test to see if it detects the usb.  What type of usb device is it (flash drive, external hard drive) and what type of ports do you have?

---

### Post by coffeecat on 2024-01-04
I suspect that the OP is using Ubuntu in a virtual machine. A quick google search of the error message suggests that this is so, specifically VMWare. If that is the case that is a fundamental piece of information that is needed for troubleshooting.

@bobhurd, are you using Ubuntu as a virtual guest machine?
If so, what is the host OS?
Some details of the hardware you are using, please.
Some google hits suggest that USB3 and USB2 incompatibility may be an issue. Details please.

And, welcome to the forum.

---

### Post by bobhurd on 2024-01-04
> **coffeecat said:**
> I suspect that the OP is using Ubuntu in a virtual machine. A quick google search of the error message suggests that this is so, specifically VMWare. If that is the case that is a fundamental piece of information that is needed for troubleshooting.

@bobhurd, are you using Ubuntu as a virtual guest machine?
If so, what is the host OS?
Some details of the hardware you are using, please.
Some google hits suggest that USB3 and USB2 incompatibility may be an issue. Details please.

And, welcome to the forum.

I am using Ubuntu on a virtual machine in VMware, yes.
The Host OS is Windows 11 Pro
I am using a brand new Dell G16 laptop
The USB is formatted to FAT32

I have my old laptop running Windows 11 Pro on a Dell G7 laptop with Ubuntu running in VMware.   Exactly the same as the new machine and software. Only any USB I try on the old machine works, but it does not on the new machine.  The setups are identical.

Thank you for your quick answers to my original query!

---

### Post by coffeecat on 2024-01-04
As this is a VMWare issue/bug rather than one in Ubuntu, I've moved your thread to the Virtualisation forum.

Here are a couple of the google hits that I found earlier, and which may give you some leads:

[https://communities.vmware.com/t5/VMware-Fusion-Discussions/USB-3-0-support/td-p/1288281](https://communities.vmware.com/t5/VMware-Fusion-Discussions/USB-3-0-support/td-p/1288281)
[https://communities.vmware.com/t5/VMware-Fusion-Discussions/Unable-to-connect-USB-drive-on-VM-with-Linux-Mint/td-p/2309436](https://communities.vmware.com/t5/VMware-Fusion-Discussions/Unable-to-connect-USB-drive-on-VM-with-Linux-Mint/td-p/2309436)

Is your USB device USB3? That might be the problem and a few ways of dealing with that are described in those two links. Beyond that I have no experience of using VMWare but, hopefully, someone with the appropriate expertise will be along to help.

---

### Post by bobhurd on 2024-01-04
I fixed it!!!

Since I had a older machine already running Ubuntu under VMware, I copied the entire Virtual Disk to the new computer.  Then I ran the Ubuntu in VMware and fixed any files that it complained about until it finally booted successfully.  I tested it with various USB drives and the new Dell G16 laptop now recognizes any USB I put into it, just like the old Dell G7 machine.

Problem solved.

---

