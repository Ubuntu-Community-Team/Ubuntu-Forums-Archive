---
title: "Installing Ubuntu 14.10 in VirtualBox, Garbage on screen"
date: 2014-10-26
forum: Virtualisation
---

### Post by Vince N on 2014-10-26
Hi All!

Wanted to run this past the forum and see if I could get any advice.  I recently downloaded the most recent Ubuntu Desktop version to try it out and attempted to install it under the latest version of VirtualBox.  I configured a base system with the defaults and such and then started it with the ISO image in the virtual CD Rom.  The system boots with no errors, but when it gets to the main screen, the display turns into unreadable garbage.  Is there something obvious i'm missing?  I've never seen Ubuntu do this before.

Also note this is JUST the CD.  I haven't even gotten to try to install it yet.

Thanks

---

### Post by Matthew_Whitwam on 2014-10-30
Had the same problem today. Am still installing but looks resolved. 

Before starting your virtual machine, in "Oracle VM VirtualBox Manager" go to File->Preferences.
In the dialogue that appears, select Display and then set "Maximum Guest Screen Size" to "None". 
Press OK and then launch your virtual machine.

[EDIT] Also seems to require "Enable EFI"

---

### Post by fred.sauze on 2014-11-10
> **Matthew_Whitwam said:**
> Had the same problem today. Am still installing but looks resolved.   Before starting your virtual machine, in "Oracle VM VirtualBox Manager" go to File->Preferences. In the dialogue that appears, select Display and then set "Maximum Guest Screen Size" to "None".  Press OK and then launch your virtual machine.  [EDIT] Also seems to require "Enable EFI" This works. Or easier way I [found](http://www.maketecheasier.com/installing-ubuntu-14-10-in-virtualbox/) is  “Right Ctrl + F1” then  “Right Ctrl + F7” when you see the garbage screen.

---

### Post by slickymaster on 2014-11-10
*Moved to the ***Virtualisation*** sub-forum*

---

