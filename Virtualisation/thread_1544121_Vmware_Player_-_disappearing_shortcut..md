---
title: "Vmware Player - disappearing shortcut."
date: 2010-08-02
forum: Virtualisation
---

### Post by Bits &amp; Bobs on 2010-08-02
Hi all - this is beyond my newbie experience and would appreciate some help.

I have **Ubuntu 10.4** installed.  I am trying to install the VMware-Player-3.1.0-261024.i386.bundle.  Using sudo sh <filename> the install appears fine and is reported successful by the installer.  

Note that at this point the expected addition of **System Tools** to the **Applications** menu becomes listed and leads to the appropriate shortcut to launch **Vmware Player**.  Everything in Vmware Player appears to work fine and I can successfully create a virtual machine.

It goes slightly wrong after rebooting my Ubuntu (host) machine.  At this point the **System Tools** menu that holds the **Vmware Player **shortcut disappears from the **Applications** menu.

I can successfully run Vmware Player using a terminal command to launch it, so all isn't lost.  I would like to understand why the menu shortcut was lost, and hopefully be able to repair the missing menu listing.

I have uninstalled/reinstalled a few times with no change in outcome and did previously hash check the original install file before using.

Thanks for any guidance you can offer.

---

### Post by dcstar on 2010-08-02
> **Bits & Bobs said:**
> Hi all - this is beyond my newbie experience and would appreciate some help.

I have **Ubuntu 10.4** installed.  I am trying to install the VMware-Player-3.1.0-261024.i386.bundle.  Using sudo sh <filename> the install appears fine and is reported successful by the installer.  

Note that at this point the expected addition of **System Tools** to the **Applications** menu becomes listed and leads to the appropriate shortcut to launch **Vmware Player**.  Everything in Vmware Player appears to work fine and I can successfully create a virtual machine.

It goes slightly wrong after rebooting my Ubuntu (host) machine.  At this point the **System Tools** menu that holds the **Vmware Player **shortcut disappears from the **Applications** menu.

I can successfully run Vmware Player using a terminal command to launch it, so all isn't lost.  I would like to understand why the menu shortcut was lost, and hopefully be able to repair the missing menu listing.

I have uninstalled/reinstalled a few times with no change in outcome and did previously hash check the original install file before using.

Thanks for any guidance you can offer.

System-Preferences-Main Menu and enable the missing menu.

---

### Post by Bits &amp; Bobs on 2010-08-02
Thanks for the reply dcstar. :)

I took a look there yesterday and unfortunately, the Vmware Player entry definitely wasn't there as a sub-entry in System Tools.

The good news is, the problem has self-repaired and the short-cut is now properly located in the Applications menu.  It may be related to a boot-up event?  This time as I rebooted there was a quick automated system check message of some sort (very quick) - maybe this was a related item?

Anyway, it's now all good,  I just don't really have a clue as to what went wrong, or what mechanism sorted it out.

Thanks again though, it was a good idea.

---

### Post by jnie on 2010-09-01
I had it too, then suddenly gone after reboot. Strange!

I created a new menu item like this,

System > Preferences > Main Menu

Under Menus: find System Tools click [New item] 

Type (Application)
Name (VMPlayer)
Command (/usr/bin/vmplayer)

The only thing I cannot find is the correct Icon to put into place :confused:

Anyone?

*J*

---

### Post by JRBASTIEN on 2010-09-10
I'm bumping up this thread.  Does anyone know how to display the proper icon?  I don't consider this one solved until it is done.

---

### Post by fjgaude on 2010-09-10
I looked all over the place for the icon and couldn't find it. It is likely within the binary for the Player.

---

### Post by JRBASTIEN on 2010-09-10
Ok, I found the icons there:

/usr/share/icons/hicolor/16x16/apps/vmware-player.png
/usr/share/icons/hicolor/32x32/apps/vmware-player.png
/usr/share/icons/hicolor/48x48/apps/vmware-player.png

---

