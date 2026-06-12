---
title: "uninstall and reinstall Windows in VB"
date: 2014-03-10
forum: Virtualisation
---

### Post by Tom_ZeCat on 2014-03-10
I have reason to believe my install of Windows 7 under VirtualBox (under Kubuntu 13.10) has problems.  I think I'd like to just completely remove it and reinstall it.  In VirtualBox I'm not finding a command to the effect of "remove operating system".  Of course there's that "New" command.  I could go ahead and install it again and remove the other one once the new setup is done.  But once I've got Win 7 setup again how I want it, there's no reason to keep the old install.  How do I remove it?

---

### Post by texpat on 2014-03-10
Try right-clicking for a context menu. I get the option to "Remove..." the OS.

---

### Post by Easy Limits on 2014-03-10
Also do a Ctrl-H on your HOME folder and look in the Virtualbox VM folder for a Windows folder and delete it.  Otherwise you will get grief the next time you try to install Windows in VB.

---

### Post by Tom_ZeCat on 2014-03-13
> **Easy Limits said:**
> Also do a Ctrl-H on your HOME folder and look in the Virtualbox VM folder for a Windows folder and delete it.  Otherwise you will get grief the next time you try to install Windows in VB.

I was actually planning to leave the current install for the time being while I install another instantiation of Windows.  That way I would  not have to immediately install all my applications and I can refer back to the old install.  Then I could finally delete the old Windows once everything is to my satisfaction.  

Bad plan?

---

### Post by JKyleOKC on 2014-03-14
Actually, all you have to do is create another hard disk (VDI file) which will start its life empty, then remove the original VDI from the VM (in the Storage category of the Settings menus) and attach the new one. Set the boot order to CD first, connect the CD or ISO that has Windows' setup files on it, and go to town. You'll have a new installation in the same VM.

Think of it as replacing the original actual drive in a machine. It works exactly the same way. All of the OS-specific information is stored on the (virtual) drive, not in the VM definition itself (although VBox does do a bit of optimization for different systems, which is why the New-VM wizard asks what system you'll be installing).

You could then, if you wish, add the original VDI as a second drive, and be able to access all the files on it from the new machine. I've done this several times to repair damaged WinXP VMs, over the years...

---

