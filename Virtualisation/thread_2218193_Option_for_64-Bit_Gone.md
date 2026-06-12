---
title: "Option for 64-Bit Gone"
date: 2014-04-19
forum: Virtualisation
---

### Post by MrBananaMan2011 on 2014-04-19
Hello,
I am using Oracle VM Virtualbox Manager to try and install Fedora 20. My host machine is a 64-bit Ubuntu 14.04 LTS. When I try to set up the machine, it asks me what OS I want (normal so far). When I click on the version, there are only general names such as "Fedora" and "Ubuntu", instead of "Fedora (64 bit)", like I have seen in other pictures. If I try and ignore this and go ahead, when i hit install fedora, it goes to a black screen.

---

### Post by QIII on 2014-04-20
Hello!

Have you made sure that VT-x (if Intel CPU) or AMD-v (If AMD CPU) are enabled in your BIOS/EFI?

You must have either VT-x or AMD-v enabled to install a 64 bit OS in VirtualBox.

---

### Post by RichardET on 2014-04-20
I'll second that .  Some machines ship this bit enabled by default, some don't.

---

### Post by MrBananaMan2011 on 2014-04-20
Hello,
I have gone into the EFI, but have not found anything for vt-x (I am using an Intel CPU) . I am using a 64 bit computer, too. The option was there before, but I was trying to solve a different problem and ran a command like "VBoxManage modifyvm "Fedora VM" --longmode off", and I believe that this may have caused this problem. The one thing is, when I typed "VBoxManage modifyvm "Fedora VM" --longmode on", nothing happened. There was still no option for 64 bit, and Fedora still had the same issue because of no 64 bit.

---

### Post by RichardET on 2014-04-20
Not all 64 bit processors have this VT capability - most of the laptop quality core2duo chips did not, for instance.  True, they are 64 bit, but they could only handle 32 bit VM's.

---

### Post by MrBananaMan2011 on 2014-04-20
The weird thing is is that the option was there before, but is gone now. My processor is an Intel Core i5-3570 CPU @ 3.40GHz × 4. From what I can see, it has vt-x support.

---

### Post by RichardET on 2014-04-20
Yes I think that you are right - that all core i5 variants have this capability.

---

### Post by wrchis on 2014-04-20
To find out for sure whether your CPU supports the virtual extensions you can download and run CPU-Z from cupid.com (it is available in other places like cnet but they often package toolbars and other garbage with it and they are not always up to date either so it is best to go to the original source).  About halfway down the screen there is a box that lists extensions and look for VTx (for Intel CPU) or CPU-Z (for AMD) in the list.

---

### Post by MrBananaMan2011 on 2014-04-20
According to Intel, my processor supports VTX ([http://ark.intel.com/products/65702](http://ark.intel.com/products/65702)). I cannot find an option in my UEFI, though. I might need to look again because I might have missed it. Also, BTW, I can't run the program you said because I am using Ububtu

What I might do (last resort because I have a pretty bad Internet connection) is uninstall and reinstall. To do this, I would just go to my package manager and uninstall virtualbox-4.3, right?

I reinstalled virtualbox 4.3 and when I try and make a new virtual machine, the (32 bit) next to the names is showing up, but there is still no option for 64 bit.

Hello once again,

I did some more snooping around in the UEFI and found the option for VT-X. Virtualbox is now working properly. The only thing I am wondering is that why was the 64 version showing up earlier when it wasn't enabled then disappeared. Oh well, at least it's solved ;)

---

