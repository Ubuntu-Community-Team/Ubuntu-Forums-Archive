---
title: "Virtual AND Dual Boot Windows?"
date: 2013-03-12
forum: Virtualisation
---

### Post by Kasuko on 2013-03-12
I am looking to set up a dual boot windows for my laptop most specifically for gaming. Now I understand that virtualizing a windows setup for gaming is useless, but I was wondering if it would be possible to boot the dual boot partition in a VM to keep it up to date etc. So when I am in the native linux environment I can have it up and Steam and windows will keep everything up to date so when I do need to reboot into the Windows only mode to play the games they are ready to go.

Is this even slightly possible?

Please note that I do not have the windows partition set up yet so any order is allowed. If I have to make it in a VM first then configure the system to boot into it or install windows then configure it to boot in a VM, either or.

Thanks
Kasuko

---

### Post by Ms. Daisy on 2013-03-13
No. A virtual machine is totally unrelated to your dual booted OS. 

You have numerous options though. You could run windows with Virtual Box. Then install Ubuntu in a vm.

---

### Post by TheFu on 2013-03-14
Ms.  Daisy is correct.  Because MS-Windows is tightly tied to the hardware, it is nearly impossible to support both the real physical hardware AND the virtualized hardware in a way that MS-Windows supports.  If you can make everything about the virtual machine match 100% what the physical machine provides, then there would be a chance.  

Which virtualization technology are you planning to use?

In the real world, this means it is extremely unlikely (1:1,000,000,000 chance) that you will be able to match these devices and setup exactly.  I won't say it is impossible, but it is just highly, highly, highly, unlikely.  We're talking PCI slot matching for virtual and real cards, HDD controllers, chipset support, HDDs and graphics adapters.  All these things need to match 100%.  For example, the real GPU in the system has nothing to do with the virtual GPU presented through the virtual machine, so the drivers necessary for running physical MS-Windows and virtual MS-Windows will never match.  

That is just a long-winded way to say - no, can't be done with Linux-based virtualization.

However ... I understand that with Windows7 Ultimate, it is possible to boot  VHD virtual machines both inside a VM and from the boot manager. The downside is the hostOS must be MS-Windows.  [http://www.hanselman.com/blog/LessVirtualMoreMachineWindows7AndTheMagicOfBootToVHD.aspx](http://www.hanselman.com/blog/LessVirtualMoreMachineWindows7AndTheMagicOfBootToVHD.aspx) will explain more.  I have never tried this.

It is possible to game using a virtual machine under Linux, but don't expect any high-end graphics to work sufficiently well.  Older games will probably work just fine.  I have not tried to run my copy of X-Wing or C&C , but I'd think both would work fine under VirtualBox, if I loaded the Guest additions.

---

