---
title: "[SOLVED] Virtual Box Permissions"
date: 2008-06-21
forum: Virtualisation
---

### Post by SyntheticShield on 2008-06-21
Hello all.

I have installed Virtual Box PUEL but when I start it up I get the following error message:

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

```

Can anyone help me with this?  I know its a permissions issue, but I dont know how to go about correcting it.  I went to users and groups and added myself to the vboxusers group but that has not corrected it the problem.

I would appreciate any assistance.  I need the PUEL version so I have usb access, if I dont get that then I might as well dual boot.

---

### Post by SyntheticShield on 2008-06-21
I found the answer.

I ran a google search on

VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE)

And found information that stated if I ran into that you had to run the following commnad to correct the issue:

sudo chmod 666 /dev/vboxdrv

---

