---
title: "Installing Ubuntu 12.10 in VirtualBox"
date: 2013-05-07
forum: Virtualisation
---

### Post by iyerra on 2013-05-07
I am trying to install Ubuntu 12.10 in VirtualBox. I am running VirtualBox on Windows 8. 

At the start of the installation process, I see that one of the options that Ubuntu presents is as follows:

[ ] Erase Disk and Install Ubuntu

If I choose this option, will it delete any other operating system installed on Virtual Box?

If I choose this option, will it delete Windows 8? 

Thanks for clarifying. 

Ramu

---

### Post by alan9800 on 2013-05-07
if you have created a new virtual machine on which to install Ubuntu, there's no problems by choosing "Erase disk"; but if on your virtual machine there's already another OS and you wish to maintain it, then it's preferable to install Ubuntu alongside to that OS.
Regarding to Windows 8, installing Ubuntu on virtualbox doesn't affect it.

---

### Post by arubislander on 2013-05-07
> **iyerra said:**
> I am trying to install Ubuntu 12.10 in VirtualBox. I am running VirtualBox on Windows 8. 

At the start of the installation process, I see that one of the options that Ubuntu presents is as follows:

[ ] Erase Disk and Install Ubuntu

If I choose this option, will it delete any other operating system installed on Virtual Box?

If I choose this option, will it delete Windows 8? 

Thanks for clarifying. 

Ramu

Are you trying to install Ubuntu from a physical CD / DVD / USB drive or are you using the ISO image file you downloaded?
I would suggest that if you have the diskspace available, you create a new Virtual Machine (VM) in VirtualBox to install Ubuntu onto. Then attach the Ubuntu 12.10 iso image to the VM you just created and then start the VM. Since it will be a new VM you should just get the option to Install Ubuntu, without any scary stuff about erasing the disk and such.

---

### Post by slickymaster on 2013-05-07
> **iyerra said:**
> I am trying to install Ubuntu 12.10 in VirtualBox. I am running VirtualBox on Windows 8. 

At the start of the installation process, I see that one of the options that Ubuntu presents is as follows:

[ ] Erase Disk and Install Ubuntu

If I choose this option, will it delete any other operating system installed on Virtual Box?

VirtualBox allows you to run more than one operating system at a time, and each one can be started, paused and stopped independently within its own virtual machine, so if you already have operating system running on your VirtualBox, you have to install Ubuntu 12.10 along side with it, not choosing the "Erase Disk and Install Ubuntu" option.

> **iyerra said:**
> If I choose this option, will it delete Windows 8?
No, each virtual machine has one directory on your host computer where all the files of that machine are stored -- the XML settings file (with a .vbox file extension) and its disk images.
By default, this "machine folder" is placed in a common folder called "VirtualBox VMs", which VirtualBox creates in the current system user's home directory. The location of this home directory depends on the conventions of the host operating system. On Windows, this is %HOMEDRIVE%%HOMEPATH%; typically something like C:\Documents and Settings\Username\.


Here is a very good tutorial on how to do it: [Installing Ubuntu inside Windows using VirtualBox]("http://www.psychocats.net/ubuntu/virtualbox")

---

