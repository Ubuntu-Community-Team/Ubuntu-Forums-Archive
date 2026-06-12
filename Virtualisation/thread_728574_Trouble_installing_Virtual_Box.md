---
title: "Trouble installing Virtual Box"
date: 2008-03-19
forum: Virtualisation
---

### Post by Steve Angelidis on 2008-03-19
Install seemed to go smooth, but when I try to Start a VM, I get this:


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 Any ideas out there? How do I give myself write permissions?

---

### Post by ramjet_1953 on 2008-03-19
Try this:

Navigate to [COLOR="Blue"]System>Administration>Users & Groups[/COLOR]

It'll ask for a password

When the window opens, click on [COLOR="Blue"]Manage Groups[/COLOR]

When the new window opens, click on [COLOR="Blue"]Add Group[/COLOR]

Add the new group [COLOR="Red"]vboxusers[/COLOR] and put yourself in it

Close off and re-boot - to be sure

Try running vbox again.

Regards,
Roger :cool:

---

### Post by Steve Angelidis on 2008-03-19
Thanks!!!

I was messing about in terminal. But my knowledge of syntax is still next to nil.

---

