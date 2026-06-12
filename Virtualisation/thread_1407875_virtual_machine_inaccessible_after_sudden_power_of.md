---
title: "virtual machine inaccessible after sudden power off"
date: 2010-02-15
forum: Virtualisation
---

### Post by charonred on 2010-02-15
PC powered off while in VirtualBox, virtual machine now inaccessible

My system suddenly powered off and rebooted, but when I opened VBox again, I got the following message;
> Start tag expected, '<' not found.
Location: '/home/(user)/.VirtualBox/Machines/Win-XP-SP3/Win-XP-SP3.xml', line 1 (0), column 1.
/home/vbox/vbox-3.1.2/src/VBox/Main/MachineImpl.cpp[5821] (nsresult Machine::loadSettings(bool)).
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {2158464a-f706-414b-a8c4-fb589dfc6b62}

how do I get my XP up n running again

---

### Post by Perryg on 2010-02-17
I suspect that either the .VirtualBox.xml or the machine xml is now corrupt or missing.  If you have a backup of them you can usually restore this to a working state.  If not then you would need to recreate the VM and re-attach the VDI file to the newly created VM.  You will need to make sure that the settings are the same as the original but it will work.  Now if you had snap shots this can be an extremely difficult task. You would need to recreate the snap shot entries in the machine xml.  Hopefully you don't have them.

---

### Post by charonred on 2010-02-17
Thanks for that, 
it worked a treat (nah, no snapshots, did that previously and ended up using tons of disk space)

---

