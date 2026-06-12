---
title: "KUbuntu Vista virtualization"
date: 2008-02-09
forum: Virtualisation
---

### Post by wolfdreamer on 2008-02-09
I installed and setup?? kvm on my kubuntu 7.10 install. Reading the kvm tutorial here, I was able to successfully get a Vista vm to install Vista, but I am rather confused about how to get the networking to work. 

I created my VIsta vm with this command :

kvm -m 1000 -cdrom /dev/cdrom -boot d windows-vista.img 

then I start my kvm with this command :

kvm -m 1000 -cdrom /dev/cdrom -boot d windows-vista.img

what do I need to do get the networking up in my Vista VM?

Also the point "for me" of having the VIsta VM is to access content on my actual Vista install located on the primary harddisk. How do I make that and other disks accessible to the VM?

---

### Post by wolfdreamer on 2008-02-10
After realizing that you boot kvm with a iso as a mount cdrom, I was able to install the the missing network driver. But I was still having network issues, so Ive switched to VirtualBox.

Just an opinion but VirtualBox seems faster then KVM, and I was able to install the AMD+PCI VIsta network driver and using "NAT" it came up with a working net connection.

---

### Post by fjgaude on 2008-02-11
The same thing happens in VMware Server using NAT, even wireless, in laptops, everywhere.

---

