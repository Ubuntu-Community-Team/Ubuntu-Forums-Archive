---
title: "[SOLVED] Adding to usergroup in virtualbox"
date: 2007-11-13
forum: Virtualisation
---

### Post by mmb1 on 2007-11-13
Hello everyone, I'm new to Linux and this is my first time using virtualization software.  I downloaded Virtualbox and everything went fine.  I downloaded the gOS ISO file and everything went fine.  After getting everything configured and starting the box, I am greeted with the following:
             


 "
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}"


It seems to be fairly simple, but I have no idea how to add myself to the user group, and a web search came up fruitless.

   I have always received fast, reliable, and friendly help from these forums and anyone who would help this poor noob would be greatly appreciated.

---

### Post by scorp123 on 2007-11-13
> **mmb1 said:**
>  it seems to be fairly simple, but I have no idea how to add myself to the user group   Administration > Users and Groups > Manage Groups > vboxusers > Properties .... then add yourself there. :)

---

### Post by mmb1 on 2007-11-13
Thanks a million, scorp123, after a quick logout, that did the trick.  I do feel quite stupid for asking such an obvious quesiton.


Thanks again!:)

---

### Post by Leslie Viljoen on 2011-10-25
To be clear: add the user to the group in the HOST OS.

---

### Post by coffeecat on 2011-10-25
Ancient thread.

Closed.

---

