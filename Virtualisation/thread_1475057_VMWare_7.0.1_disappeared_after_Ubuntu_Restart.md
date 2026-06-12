---
title: "VMWare 7.0.1 disappeared after Ubuntu Restart"
date: 2010-05-06
forum: Virtualisation
---

### Post by TimWB on 2010-05-06
Rather odd this; and I'm new to Ubuntu so please bear with me...

Installed 10.04/AMD/64 this morning on a surplus HP laptop - all worked fine right out of the box.

Then I downloaded VMWare Workstation 7.01/64/Linux and ran the .bundle from SH to install.

Initially all was fine, VMWare appeared in a Sub-Folder off the Applications menu, and I copied in a bunch of VMs to use.

Then I shut down and restarted when I got home, only to find that VMWare is no longer in the menu.  No errors, nothing - simply just not there.

Trying to open the VMX file runs it in VM player, but I want to use Workstation.

Foolishly I didn't note the name or location of the executable, so I can't just search/browse for it...

A colleague suggests my Path may have changed as result of the update, but that's not much help since I still can't get it back.

Any suggestions either:

- What the VM Executable is called, and where it is likely to be hiding?
- How to retrieve it back to the Menus?

Thanks in advance.

TimWB

PS - forgot to add; If I re-run the VMWare installer, it tells me it's all installed and does nothing...

---

### Post by TimWB on 2010-05-07
Gottit...
The binary is, of course, in /usr/bin, so you just  need to create a Launcher pointing at that file. 

Still no idea why it disappeared from the Apps Menu, tho.
Too  long since I did Unix

---

### Post by cim on 2010-05-20
same thing happened to me, idk why? could anyone shed some light on this one?

---

### Post by fjgaude on 2010-05-20
Right click on the Applications Menu and notice Edit Menus, click it. From there go to System Tools you such see WS and Player. Do then what you have to do.

---

### Post by cim on 2010-05-20
i clicked the box where it says vmware ace, it still doesn't show. i just found out that it doesn't show because there are no entries in that specific menu

---

