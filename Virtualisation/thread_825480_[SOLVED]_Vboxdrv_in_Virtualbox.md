---
title: "[SOLVED] Vboxdrv in Virtualbox"
date: 2008-06-11
forum: Virtualisation
---

### Post by phildaman46 on 2008-06-11
Why is it whenever I boot into Ubuntu, I have to set the permissions to me on the vboxdrv that Virtualbox uses? If I don't set the permissions to me the user, Virtualbox will give me a error and will not run the OS I'm virtualizing.

Like this error:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

Every time I boot into Ubuntu the permissions change back to root. How do I keep the permissions set to me?

---

### Post by vishzilla on 2008-06-11
Go to System>Admin>Users and Groups>Manage Groups and in the vboxusers group enable your username

---

### Post by phildaman46 on 2008-06-11
Thanks, that worked.

---

