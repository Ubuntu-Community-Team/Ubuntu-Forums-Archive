---
title: "[SOLVED] Access Denied?"
date: 2008-01-19
forum: Virtualisation
---

### Post by Rwild on 2008-01-19
Well, I am looking to set up another OS to run live in Ubuntu.  When I attempt to start VirtualMachine, it gives me a pop-up 

> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

How can I give myself permission as I am the admin?

---

### Post by melopsittacus on 2008-01-19
Try this:
System -> Administration -> Users and Groups -> Manage Groups

here there should be a group vboxusers. Select it, click Properties and tick your name.

---

### Post by Rwild on 2008-01-19
Perfect...

Now, when the vm starts, I press F12 and select three to boot from CD-ROM.  I have my Vista disk in and I have booted from the disk successfully before.  Any idea of what could be happening?

...Ah.  The tricks of Linux.

---

