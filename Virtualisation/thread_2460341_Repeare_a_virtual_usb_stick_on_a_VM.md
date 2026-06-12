---
title: "Repeare a virtual usb stick on a VM"
date: 2021-04-07
forum: Virtualisation
---

### Post by 010421wxc on 2021-04-07
Hello everyone,
i am working on a VM ubuntu and i am usint a virtual USB stick. Since my last update i can't access anymore my usb stick . When i am looking in the permissions i see this:
owner: root
group: root
others: 
 How can i change the groupe to vboxsf? what are the commands in terminal to put??
As you notice i am new on ubuntu:) need help pls!!!
TNX

---

### Post by ajgreeny on 2021-04-07
I have no idea exactly what you mean by **virtual USB stick**. 
Are you trying to mount and use a standard USB flash drive using your virtual install of Ubuntu?  What filesystem is the flash drive formatted to?

You probably need to make sure you have installed the guest additions in the virtual Ubuntu but if the flash drive is formatted to ext4 or another Linux filesystem you will need to change ownership of the mountpoint of that drive to you as user in the virtual system.  This is exactly the same as if you were using a flash drive formatted to ext4 on a hard metal installation of Ubuntu.

Do not change the group, owner, or anything else to vboxsf but make sure that you, the user, are a member of vboxsf group if you wish to use shared folders, that is shared between the host and guest; this has no bearing on use of USB drives in a virtual installation of Ubuntu.

Have a look at the VBox forum which you can get to, as well as some other VBox information from [https://www.virtualbox.org/wiki/Community](https://www.virtualbox.org/wiki/Community). This should allow you to search more easily for the information you need to solve your problems as I think you are getting several things wrong in the questions you asked.

---

