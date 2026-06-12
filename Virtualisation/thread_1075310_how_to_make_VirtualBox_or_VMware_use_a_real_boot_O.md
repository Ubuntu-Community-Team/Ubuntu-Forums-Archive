---
title: "how to make VirtualBox or VMware use a real boot OS"
date: 2009-02-20
forum: Virtualisation
---

### Post by Shady3D on 2009-02-20
hi all, i am working on dual boot machine, one with Ubuntu Intrepid Ibex and the other is XP sp2 and both are x64 version, and i want to keep my dual boot and be able to access the OS from the VM.

so if any one can help me by explaining the process, i will be very thankful to u

---

### Post by howefield on 2009-02-20
There are several step by step guides available, here is one

[http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=47883.0;wap2](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=47883.0;wap2)

But, I have to say, windows installs very much quicker in Virtualbox than for "real" and I would prefer to do a fresh install to VirtualBox.

---

### Post by Shady3D on 2009-02-20
but this process make image of the current OS then use it in VM, is there any way to make VM read the from the actual OS, or in other way when i make changes in VM it appears in the actual OS

---

### Post by howefield on 2009-02-20
Oh I see. I doubt that is possible with virtualbox.

---

### Post by Shady3D on 2009-02-20
not necessary in virtual box, any vm will be good

---

### Post by Doug11 on 2009-02-20
Do you mean have the VM boot Xp right from the second partition? Pretty sure you have to do a separate install in the Vm.

---

### Post by HavocXphere on 2009-02-20
Unless you feel like re-writing half of the virtualbox code, I don't think you'll get that working. The closest you'll get, imho, is to image it, use that image in a VM then reimage it and dump that on the hdd. Hardly a practical procedure.

---

### Post by Shady3D on 2009-02-20
so its impossible for now to do this, unless someone implements function.

Ok, thank u all for ur help

---

### Post by txtiger on 2009-02-20
Unless I am misunderstanding the question, I would disagree.  Virtual box can boot what it calls a "raw disk".  This is covered nicely in the posts at [http://ubuntuforums.org/showthread.php?t=662018](http://ubuntuforums.org/showthread.php?t=662018) and there is a good howto at [http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

I did this and was able to get a clean Virtual Box boot into the hard drive.  However, going beyond the boot screen was unsuccessful because I tried it on a dual boot system with Grub installed in the MBR. So when Virtualbox opened Grub to jump to the WinXP system to boot, it crashed with a grub error.  I think if I had done a fix MBR from windows and then retried, it would have worked.  I just did not have the time or desire to do that at the moment.

My advice on trying this is twofold, first be aware of the risk of direct disk access of a partition from a different OS and be sure you have it all straight.  And second, clean up the boot system from Windows so that it boots cleanly to the WinXP partition (whereever it is).  If you can just power on and end up in WinXP then the raw disk access is made to handle it.

Let us know how it works for you if you do it.

Hope this helps.

---

### Post by Shady3D on 2009-02-20
so ur saying that in real boot GRUB will only let me access Ubuntu

---

### Post by bodhi.zazen on 2009-02-20
booting a physical partition with VBox, VMWare, or KVM is possible.

I personally do it with KVM all the time.

Windows is a restrictive OS and you will need to be willing to configure it. In addition if you make a mistake you may cause data loss.

The default behavior is to use a virtual disk.

If you still with to boot a physical, or raw partition, please see the sticky.

There is a reason it is a sticky ;)

[http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

And the physical partition section : 

[http://ubuntuforums.org/showpost.php?p=6122463&postcount=6](http://ubuntuforums.org/showpost.php?p=6122463&postcount=6)

If, after reviewing the information, you still have questions, please either post in the appropriate thread or start a new one.

---

