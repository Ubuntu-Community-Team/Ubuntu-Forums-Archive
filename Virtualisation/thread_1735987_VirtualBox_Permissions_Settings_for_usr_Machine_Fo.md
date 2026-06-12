---
title: "VirtualBox Permissions Settings for /usr Machine Folder"
date: 2011-04-22
forum: Virtualisation
---

### Post by UltraZone on 2011-04-22
So, due to my initial choices of how to allocate my harddrive space to three partitions: 1) / (root): 70 gb 2) /home: 60 gb 3) /usr: 60 gb when I installed Ubuntu (I chose this for easy reinstallation if need be).  Now my /home partition is running low on disk space if I want to set up more than one VM with VirtualBox, because typically I need 20 gigs for each one to have anything decent to work with (Fedora and Win7).  So I thought that I would simply change the Machine Folder selection to /usr/VirtualBox (a folder I made) and stick everything in there since it's emptier.  But it doesn't work, presumably due to the need to set correct access permissions.  Does anybody know how to allow VirtualBox access to a folder not within /home ?  Appreciate your input.

---

### Post by An Sanct on 2011-04-22
First: The virtual machine disk sizes ... did you use dynamic disks or static?

second: Have you checked the user group *vboxusers* (in the menu: System->Administration->Users and Groups, then click "Manage Groups")?

Also if you move the virtual machines, you have to own the new folder by that group, to allow to use it (vboxusers).

PS. Also it is advisable to make yourself a member of the *vboxusers* group[I].
[/I]

---

