---
title: "Virtualbox + XP - Installed vm tools lost resolution"
date: 2014-01-20
forum: Virtualisation
---

### Post by mr_si on 2014-01-20
As per thread title, I've been running XP @ 1024 x 768 in a VM. Virtual box prompted me to install tools, now XP reports that I have a Virtual Box graphics adaptor that's only capable of 800 x 600. 

(My VM runs with 32Mb graphics ram / 256Mb Ram, 2d and 3d acceleration enabled). My laptop is not very capable, but I don't see that's an issue.

I'd like 1024 x 768 back, but I'd prefer to run in my monitor's native resoltion (1280 x 768). Any ideas?

Thanks

---

### Post by ajgreeny on 2014-01-20
Have you got the vbox-guest-additions installed, and if so, after a linux kernel upgrade you will need to reinstall the guest-additions for your running kernel.

If you're using the open-source version of VB from the repos it is probably worth uninstalling that and getting the PUEL version direct from Oracle, as it allows some additional possibilities that the OS version does not.  I am fairly sure you can use the same VMs in either version of VB so you shouldn't need to create new VMs.

---

### Post by mr_si on 2014-01-20
Sorry, to be clear 'tools' in my post refers to guest additions.

From what you say, in the VM I ought to uninstall and reinstall the guest tools once I've got a VBox direct from Oracle. Thanks.

---

### Post by mr_si on 2014-01-22
Uninstalled and reinstalled (in the XP VM) and it works at my my laptops lcd resolution. Solved!

---

