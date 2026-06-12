---
title: "VirtualBox and USB"
date: 2011-04-21
forum: Virtualisation
---

### Post by AlanR8 on 2011-04-21
Yo

Heading says it really. Running Natty as of today's version and have VirtualBox 4.06 installed from the VB site. XP is now living in the box and has been fully updated.

Can't get XP in the VB to see my USB devices, camera, Pod, phone etc.

Help please!!!!!

Thanks in advance

---

### Post by cariboo on 2011-04-21
Moved to Virtualization, as this isn't a Natty specific problem.

---

### Post by teimcrr on 2011-04-22
I actually have the same problem.
Fresh install of Natty, Virtualbox and its extension.
VM with XP exported from lucid, USB isn't working anymore.

:o

---

### Post by AlanR8 on 2011-04-22
Should have waited 24 hours then I wouldn't have needed to create the thread!

Today's 22/04/2011 update to Natty seems to have sorted the USB issues in Virtual Box.

All is well so I've marked the thread as solved even though I don't know HOW the problem was solved.

---

### Post by redPirate on 2011-09-29
Virtualbox creates a group vboxusers. In order to access USB in virtualbox user must be in the group vboxusers. I checked and my username was already part of the group. However USB was still not working. All I did to make it work was in Ubuntu User management panel deselected my name, closed the window, again started Ubuntu User management panel and re-selected my username to be part of the group vboxusers and USB worked.

A note of Caution!
Once you re-add user to vboxusers group setup USB filters in virtualbox before starting a windows instanc. Normally keyboard/mouse and network is accessed through the host ubuntu system instead of direct usb access. In my case it was conflicting and the system just froze.

Hope this helps.

---

### Post by abetterlie on 2011-10-13
Yup this works just fine. 
Add your user to vboxusers group, logout, and login. 

Tested on Ubuntu 11.04 virtualbox 4.1.4, Windows XP

---

