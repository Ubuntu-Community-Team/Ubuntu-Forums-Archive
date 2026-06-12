---
title: "Virtualbox - add key bindings?"
date: 2011-07-27
forum: Virtualisation
---

### Post by Warthaug on 2011-07-27
I am running a Win7 guest in virtualbox, using ubuntu 11.04 has the host system.  The setup is working perfectly so far, but I do have one small headache I would like to fix (if possible).  I use multiple desktops (workspaces?) in ubuntu to organize my workflow.  When in win7 the key bindings used to switch desktops (Ctrl+Alt+arrow key) are not passed to ubuntu, as as such don't do anything.  I was wondering if there was some way to configure virutalbox such that the switch workspace commands will not be passed to win7, and instead passed to ubuntu.

Any help is appreciated

Bryan

---

### Post by lmarmisa on 2011-07-27
I think that this is not a problem. It makes sense to pass the  keys pressed to the guest virtual machine(s), including the Ctrl and Alt keys. In the case of Windows 7, this specific keys combination does not do anything, but this is not the case if the guest system would be Ubuntu.

If you wish to pass that keys to the host system, try to unselect the window of your VM before. For example, click on the desktop wallpaper and then type Alt + Ctrl + Arrow.

**Note:** I suppose you have installed VirtualBox Guest Additions on your virtual machine.

---

### Post by Warthaug on 2011-07-27
Its not a problem, in the sense that it is not preventing things from working.  But it is an inconvenience, as it slows things down (because I have to select the host system by mouse before switching workspaces).

I don't want to set all of the buttons to the host; just the specific combinations used to switch workspaces.

Bryan

---

### Post by lmarmisa on 2011-07-27
Try this sequence:

1) Type Ctrl (right-ctrl key).

2) Type Alt + Ctrl + Arrows

This works pretty well here.

Best regards,

Luis

---

### Post by Warthaug on 2011-07-27
Perfect!  Thanx

---

