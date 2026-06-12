---
title: "Vmware and Virtualbox"
date: 2013-06-17
forum: Virtualisation
---

### Post by lekevinio on 2013-06-17
Hi.

I'm trying to make a windows 7 and XP virtual machine in ubuntu using Virtulbox but when I'm using Window 8 I want to use those virtual machines in VMware because of the the aero and 3d acceleration support.
When I try to use 3d acceleration with Virtualbox than the resolution is low and cannot get any higher.

Also the auto resize of Windows does not work properly within Virtualbox.
When I'm using ubuntu it does not matter because I only use the VM for small games or Office 2013.
But within Windows its very usefull to use Unity mode because I like a allot more that Virtualsbox's seamless mode.

So what I wanna to ask is: How do I make a virtual machine that I can use with VirtualBox and Vmware without any driver problems?

---

### Post by Cheesemill on 2013-06-17
You could always use VMware on Ubuntu as well.

---

### Post by lekevinio on 2013-06-17
I tried that but it kept crashing in 12.04 and 12.10. I resently reinstalled Windows and still need to reinstall Ubuntu and I will try it with 13.04.
But It would still be neat to have because some classmates use Virtualbox and others use Vmware.

---

### Post by Cheesemill on 2013-06-17
Sorry for not actually answering your question again but you should know that VirtualBox ***does*** support resizing, 3D acceleration and Aero if you install the Guest Additions properly, for more information see my post here...
[http://ubuntuforums.org/showthread.php?t=1960890&p=11853844&viewfull=1#post11853844](http://ubuntuforums.org/showthread.php?t=1960890&p=11853844&viewfull=1#post11853844)

You also need to make sure that you have the VirtualBox extension pack installed on your host machine.

---

### Post by lekevinio on 2013-06-19
Thanks for helping with the Aero effect. That works perfectly.
But when I have it installed using the safemode method the resolution is stuck very low.
I tried running Virtualbox with my Nvidia gpu but no luck.
I do have both 2d and 3d checked in the settings. This is one of the reasons I like Vmware just a bit more than Virtualbox. But if it can be fixed that would be great. I ross kindof work when I resize the wndow manually and only an inch per time. But It is still very slow and when I started a game it said it ran out of memory but it had 2 GB and it works. in W7

---

### Post by 2Stoned on 2013-06-20
> **lekevinio said:**
> 
So what I wanna to ask is: How do I make a virtual machine that I can use with VirtualBox and Vmware without any driver problems?

You can try to convert the VMware image .vmdk to an Virtualbox image .vdi. But you cannot switch back if im correct, even so, big chance it would corrupt the vdisk.

---

### Post by lekevinio on 2013-06-21
That wont be necessary because Virtualbox can also make .vmdk files. But the problem I'm having is with using both VMware and Virtualbox for 1 virtual machine.

---

### Post by 2Stoned on 2013-06-21
> **lekevinio said:**
> That wont be necessary because Virtualbox can also make .vmdk files.


#-oTrue.

---

### Post by lekevinio on 2013-06-23
I've managed to get Vmware to work with the help of this: [http://mergy.org/2013/03/three-tips-to-get-vmware-workstation-9-going-on-kernel-3-8-0/](http://mergy.org/2013/03/three-tips-to-get-vmware-workstation-9-going-on-kernel-3-8-0/). So I will just keep using Vmware.
I do want to thank you guys for thinking and helping me out with this.
I&#314;l try and close this now.

---

