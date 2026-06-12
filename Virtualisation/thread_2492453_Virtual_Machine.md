---
title: "Virtual Machine"
date: 2023-11-11
forum: Virtualisation
---

### Post by manikinxvx on 2023-11-11
:::Just this morning I started looking into FREE VMs for Win 8. I've never used one and have a couple questions:::

1) The reason for this is to run my not-a-Cricut vinyl cutter, future purchase of a laser etcher/engraver (unless the one I found that claims to work on Linux actually does), and future purchase of a 3D printer (unless I find a Linux-compatable one).

2) I'll need to install peripheral drivers, so one compatible with the widest range is crucial... if that's ever an issue.

3) My Linux disrtro is 64bit Xubuntu 23.04.

These are probably "stupid questions" to people who know what they're doing.

---

### Post by TheFu on 2023-11-11
I missed any question.  Did you have some?   

VMs don't have direct access to hardware, unless you setup passthru.  USB passthru is easier to setup, but it is for exclusive access.  PCI passthru also requires exclusive access and is more complex,  depending on the motherboard, OS, and hypervisor software.

> 3) My Linux disrtro is 64bit Xubuntu 23.04.
Support for 23.04 ends in January, so before you do this, either upgrade to 23.10 (supported until June) or drop back to 22.04 which is an LTS with either 3 or 5 yrs of support depending on the flavor.  XUbuntu is 3 yrs.  Prevent having to rework this more times than necessary, since PCI passthru is non-trivial.

---

### Post by MAFoElffen on 2023-11-11
I would upgrade it to 23.10, then when 24.04 LTS hits in April, lock it into LTS releases.

I would install KVM, and download the virtio drivers for your Windows Guest from here: [https://launchpad.net/kvm-guest-drivers-windows/+download](https://launchpad.net/kvm-guest-drivers-windows/+download)

On Windows VM... I do DEV testing, so have the links... I was warned not to share them here. It's not like that is a secret, and it is a pain in the behind: [https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/](https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/)

Yes: Window11 VM's... Free. The VM's are released every month, but they are time-bombed for a month of use, before they go dead. Legal to use for a month, then you DL another image (for the next month's release image). They release formats for VMware, Parallel, VirtualBox & Hyper-V, so you have to convert them to raw or qcow2. Wash, rinse, repeat. That is the legal way of doing free. It is not convenient, nor is it meant to be..

A Windows 10 License key for Windows 10 is just under $40 right now. Some things are not worth the continued trouble to try to work around not having a license.

Yes, you can do USB pass-through to whatever.

But also... Didn't I hear that some people were running their app on Wine? Maybe I'm wrong with that.

---

### Post by SeijiSensei on 2023-11-12
[https://www.microsoft.com/software-download/windows11](https://www.microsoft.com/software-download/windows11)

[https://phoenixnap.com/kb/ubuntu-install-kvm](https://phoenixnap.com/kb/ubuntu-install-kvm) (Even though it was written for 20.04, the same steps work with later releases.)

I just install the ISO images directly in either KVM or VirtualBox. You can just point to the ISO during the process of creating the virtual machine.

My other question would be whether you have some old computer lying around that can run Windows. Have it drive all the printers and other devices, then share them with Windows Networking. (Even an i486 with Win7 or earlier can handle this.) On the Linux side you can then mount the shared printers to your machine. If the files you're generating are large, the disk drive in the print server could be a constraint depending on the age of the machine.

---

