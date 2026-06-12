---
title: "Virtual Box setup help"
date: 2008-01-09
forum: Virtualisation
---

### Post by JaggedOne on 2008-01-09
I just installed virtual box on linux mint 4.0. It installed just fine, but when I went to install windows XP in a virtual machine I got this error. 

> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



It looks like i need to change permissions on that file (am I right?). How do I do that?

---

### Post by john6six on 2008-01-09
Add yourself to the vboxusers group.

sudo adduser *username* vboxusers

---

### Post by CCBalla10 on 2008-01-09
or you could go to System>Admin>Users and Groups.....click manage groups....scroll down to vboxusers and hit properties and check your username and click ok and close all the boxes....then start virtualbox!

**Edit** just remembered you install Mint....so just follow what ^^he said

---

### Post by jasonrandolph on 2008-01-10
I've been doing it this way:

*sudo chmod a+rw /dev/vboxdrv*

I've had to do that every time I restarted my computer, but I'll have to try the other ways you all suggested.

---

### Post by spur on 2008-01-14
I am having the same problem and my username is in the vboxusers group. It gets to be a pain having to alter the permissions every time I want to use the program. Any solutions?
The adding to the users group via command line just tells me I am already in the group and making it read/writable etc for every one doesn't seem very secure. It only lasts for that session as well.

---

