---
title: "virt-manager kvm on 9.10 permission denied error creating a vm"
date: 2009-11-01
forum: Virtualisation
---

### Post by extendedping on 2009-11-01
Hi all new ubuntu user here. installed virt-manager and kvm. when I go to install a virtual machine it stops giving a permission denied error. is this because I am not root which ubuntu frowns on from what I have read? and if so how am I to install windows on ubuntu through kvm/virt-manager? thanks.

---

### Post by extendedping on 2009-11-02
well it seems to work if I start it from sudo on the command line. kind of annoying I wish there was a way to start it just from the menu oh well. at least it works with the real time kernel which when I tried ubuntu last year it did not...

---

### Post by sdowney717 on 2009-11-02
some guides
[http://foxgulch.com/WordPress/?p=459](http://foxgulch.com/WordPress/?p=459)
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)
[http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers](http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers)
[http://www.linux-kvm.com/content/improved-support-usb-virt-manager-07](http://www.linux-kvm.com/content/improved-support-usb-virt-manager-07)

usb works now at 1.0 sppeds and you have to edit an ubuntu system file to allow usb passthru as it is turned off by default

[http://ubuntuforums.org/showthread.php?t=1300952](http://ubuntuforums.org/showthread.php?t=1300952)

---

### Post by magicfab on 2009-11-11
See this bug report:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/379991](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/379991)

---

