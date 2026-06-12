---
title: "Can I update Virtual Box 4.1.12 in Ubuntu to version 4.2 thru Ubuntu Tweak"
date: 2013-03-16
forum: Virtualisation
---

### Post by send2 on 2013-03-16
I am running Virtual Box vers. 4.1.12 right now with Kubuntu 12.10 and Windows XP as virtual OSs. Can I update Virtual Box version 4.1 to 4.2 thru Ubuntu Tweak or should I uninstall everything from old version and install fresh to 4.2? My host is Ubuntu 12.04 LTS. Any recomendations as to how to best upgrade? TIA

---

### Post by SeijiSensei on 2013-03-17
By far the best solution for VB is to follow the [instructions]("https://www.virtualbox.org/wiki/Linux_Downloads") for "Debian-based" distributions on the VB site.  Then VirtualBox updates will be managed like all other updates.

And, yes, I have upgraded from 4.1 to 4.2 and my virtual machines ran just fine afterward.  If you follow the instructions above, I would remove virtualbox-4.1 then install virtualbox-4.2.  Your virtual machine images are kept in your home directory and won't be touched by the upgrade.

---

### Post by send2 on 2013-03-17
> **SeijiSensei said:**
> By far the best solution for VB is to follow the [instructions]("https://www.virtualbox.org/wiki/Linux_Downloads") for "Debian-based" distributions on the VB site.  Then VirtualBox updates will be managed like all other updates.

And, yes, I have upgraded from 4.1 to 4.2 and my virtual machines ran just fine afterward.  If you follow the instructions above, I would remove virtualbox-4.1 then install virtualbox-4.2.  Your virtual machine images are kept in your home directory and won't be touched by the upgrade.

Thank you SeijiSensei for your reply, which is the best way to uninstall VirtualBox? thru Synaptic, or software center or thru comand line? thanks again for your help.

Ah yes, one more question, which is the best way to uninstall the virtual drives? going thru the virtual machine manager? is that enough to clean all the files if one wants to uninstall everything from a particular virtual OS? Thanks.

---

### Post by SeijiSensei on 2013-03-17
As I said, follow the instructions on the page at VirtualBox.  In brief, it tells you how to add support for Oracle's repository, then you use the normal apt-get method to install.

I'm not sure what you're asking about with regard to the virtual drives.  Everything associated with a particular virtual machine is in the machine's image file in $HOME/.VirtualBox.  Upgrading from 4.1 to 4.2 just changes the executables; it doesn't touch any of the virtual machines themselves.

---

### Post by send2 on 2013-03-17
> **SeijiSensei said:**
> As I said, follow the instructions on the page at VirtualBox.  In brief, it tells you how to add support for Oracle's repository, then you use the normal apt-get method to install.

I'm not sure what you're asking about with regard to the virtual drives.  Everything associated with a particular virtual machine is in the machine's image file in $HOME/.VirtualBox.  Upgrading from 4.1 to 4.2 just changes the executables; it doesn't touch any of the virtual machines themselves.

Actually you just answered my question on the virtual machines, I was trying to make sure that when I uninstalled the old version of VirtualBox my installed virtual machines would not be uninstalled too, by mentioning that the virtual machines themselves are not touched my question is anwered. Thanks for your help, I installed VirtualBox from the page you gave me, now I have to figure out how to install the guest additions in my virtual machine (Kubuntu 12.10), I am getting errors trying to mount the guest iso, but that is for another thread.

thanks very much again, I will mark this thread solved...

---

