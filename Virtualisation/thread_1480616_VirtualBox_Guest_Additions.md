---
title: "VirtualBox Guest Additions"
date: 2010-05-11
forum: Virtualisation
---

### Post by Cuco3 on 2010-05-11
Is there a way to get Guest Additions that allow copying+pasting to a guest Ubuntu Server???

---

### Post by lmarmisa on 2010-05-11
GuestAdditions.iso is simply an iso file. So, you can copy it or even burn a CD with it.

The file is located in the following places:

Ubuntu: /usr/share/virtualbox/VBoxGuestAdditions.iso
Windows: c:\Program files\Sun\VirtualBox\VBoxGuestAdditions.iso

---

### Post by Cuco3 on 2010-05-12
LoL I meant copying + pasting text from the Host machine to the Guest Machine (the Ubuntu Server). Thanks anyways.

---

### Post by parn on 2010-05-12
Once you have GuestAddtion installed in the guest os, you will be able to copy/paste between host and guest os.

You simply need to install the GuestAddition to the guest OS.

If you mean where to get the GuestAddition.iso;
If you are on a Windows host, the installer would have included the GuestAddition.iso. 

If you are on Linux, you simply click on the install GuestAddtion menu option and you have the option to download the GuestAddition if you havent downloaded it already.

---

### Post by Cuco3 on 2010-05-12
I can't seem to get it to paste from my computer onto a virtualized Ubuntu Server as the guest. Everything about the Guest Additions installation was successful except the "X.org and XFree86 Window System"

---

