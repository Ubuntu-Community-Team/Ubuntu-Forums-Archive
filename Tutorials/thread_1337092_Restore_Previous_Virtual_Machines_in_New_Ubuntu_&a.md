---
title: "Restore Previous Virtual Machines in New Ubuntu &amp; VirtualBox Install"
date: 2009-11-25
forum: Tutorials
---

### Post by the_guv on 2009-11-25
**Set Up Previous VirtualBox Machines in Minutes**

Problem: After a fresh install of VirtualBox, perhaps in a new Linux installation, how can you seamlessly restore previous virtual operating systems, working as before? Here is how ..

 This works for VirtualBox installed in Linux (Debian such as Ubuntu) and should work equally well for other systems such as Windows because the principle is the same. I have only tried for Ubuntu so, if you use VirtualBox as a programme on another operating system, you will have to reapply the logic.

For Ubuntu at least, say if you are upgrading from Jaunty 9.04 to Karmic 9.10, and want to re-implement your old VirtualBox virtual operating systems, this process is wonderfully simple, resulting in you having your old VirtualBox systems, identical to before.
  [B]
How to Reinstate VirtualBox Machines Easily
[/B]
 If you already know your way around Linux, here's the truncated method:-
 
[LIST]
[*]backup .VirtualBox directory from /home/USERNAME
[*]install VirtualBox in new OS, don't run it yet
[*]pull across backed up .VirtualBox folder to new /home/USERNAME directory
[*]run VirtualBox and start up virtual OS'es in the regular way
[/LIST]
 Or if you're not sure about that, read on for the detail ..
 
**Where Do VirtualBox Virtual Operating Systems Live?**

 You can't restore a previous virtual system state if you haven't backed it up, right?, so the first thing to do is to save it.  
 
You can find it (or them), on Debian Linux at least, in:-
 
/home/USERNAME/.VirtualBox/Machines

NB: the dot before VirtualBox denotes that this is a hidden file. If you can't see the folder, you'll have to enable viewing hidden files. To do that in Ubuntu's Nautilus:-
 
CTRL-H

Rather than restoring just the emulated operating systems, let's restore our VirtualBox settings as well, so just copy the entire .VirtualBox directory, which includes the Machines folder. So backup:-
 
/home/USERNAME/.VirtualBox

 **Reinstalling VirtualBox**

 In your shiny new operating system, install VirtualBox in the normal way.  Here's my guide with a few cute tips:-[SIZE=1]

[/SIZE] [SIZE=2][COLOR=DeepSkyBlue]**[VirtualBox: Run XP/VISTA/7 in Ubuntu [KARMIC KOALA BIBLE #25]]("http://guvnr.com/pc/emulate-virtual-operating-systems-virtualbox/")**
[/COLOR][/SIZE] 
But don't start the program just yet.

**Restoring Former Virtual Operating Systems in Ubuntu**

 Open up your /home/USERNAME directory and simply copy to it your old /home/USERNAME/.VirtualBox folder, in its entirety.

 **Running Old Virtual Operating Systems in Ubuntu**

 Now start VirtualBox and access your saved virtual systems in the usual way.
 How simple is that?!  Way easier than reinstalling those virtual systems, complete with service packs and software, from scratch, huh?!

---

### Post by goltoof on 2012-04-11
Unfortunately I can't simply copy over the VM because the OS is on a SSD and the VM is on a separate hard disk.

When I tried reinstalling Vbox and going through the steps of setting up the machine again the OS works but when I try setting up shared drives, etc, it tells me "VBoxManage: error: Could not find a registered machine named..." 

I tried "VBoxManage registervm /home/user/VirtualBox\ VMs/VMXP/VMXP.vbox", but I get an erro... forgot what because I just purged virtualbox and want to try fresh.


So how do I register my machine after reinstall?  I can't try moving it to /home because my SSD is only 64gb while the vm is 50gb.

---

