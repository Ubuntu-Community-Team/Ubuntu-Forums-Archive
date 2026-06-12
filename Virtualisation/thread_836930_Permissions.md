---
title: "Permissions"
date: 2008-06-22
forum: Virtualisation
---

### Post by Barmaleychik on 2008-06-22
[COLOR="Blue"]I just got an idea: I copied the virtual machine on a CD in Windows and then moved to Linux. Is it possible that files from CD have some kind of protection and that is why I need the permission? This text in color I put after the main post was posted and I just want to make sure that it is marked as edited [/COLOR]

I am trying to start a virtual machine in VmWare and I got the message:

Unable to add virtual machine "/home/vasily/Documents/VmWare Virtual Machine/Clone of XP SP2/Windows XP Professional.vmx" to the inventory: No permission to perform this operation

I understand that I need to furnish some kind of permission. I would like to understand the concept of the permission. Do I give the permission to the file/folder where my virtual machine is or I give permission to VmWare console to use the file? Is there a standard command I need to use to give this permission? And main thing: how do I give that permission?

---

### Post by jpkotta on 2008-06-22
Assuming you're running as user vasily, I don't see why it doesn't have permission, but apparently it doesn't.  You can change permissions with the chmod command.  This might do what you want:
```
chmod +w /home/vasily/Documents/VmWare Virtual Machine/Clone of XP SP2"
```

---

### Post by p_quarles on 2008-06-22
Moved to Virtualization.

I don't know VMWare at all, but in VirtualBox, it's necessary to add a user to the group that owns VirtualBox files before anything will work properly. I'm guessing something similar is going on here. For clues, you might:
```
cat /etc/group
```
and look for something related to VMWare.

---

### Post by jpkotta on 2008-06-22
> **p_quarles said:**
> Moved to Virtualization.

I don't know VMWare at all, but in VirtualBox, it's necessary to add a user to the group that owns VirtualBox files before anything will work properly. I'm guessing something similar is going on here. For clues, you might:
```
cat /etc/group
```
and look for something related to VMWare.

Nope, VMWare doesn't need it's own group or user.

---

