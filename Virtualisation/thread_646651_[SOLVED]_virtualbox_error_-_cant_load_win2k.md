---
title: "[SOLVED] virtualbox error - cant load win2k"
date: 2007-12-21
forum: Virtualisation
---

### Post by ICEcoffee on 2007-12-21
I can get to load Win2k pro - Virtualbox gives this error message when I click the start button, and before I've loaded Win2k. Need help to resolve.

Thanks

> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

---

### Post by Tteddo on 2007-12-22
You have to do like it says, go to System>>Administration>>Users and Groups. Click manage groups, then scroll down to vboxusers and click it, then properties. Then check off both you and root. Then click ok, close and close. Then logout and back in and you should be all set.
Cheers!

---

### Post by ICEcoffee on 2007-12-24
Tteddo: thanks, it took forty odd views and a couple of days before I got some help, which means there is probably others like me, who may have heard about user and group permissions under Linux, but never understood them properly.

So thanks for your help, I followed the instruction and it worked. So now I'm off to learn about permissions.

---

### Post by Tteddo on 2007-12-24
Here's a nice explanation of permissions if you like:
[http://www.perlfect.com/articles/chmod.shtml]("http://www.perlfect.com/articles/chmod.shtml")

Please mark this solved under thread tools. I think that puts it in a category that helps it get found by others with similar problems. Well, it helps me when I see a thread marked as solved and it is someone with the same problem as me!

---

