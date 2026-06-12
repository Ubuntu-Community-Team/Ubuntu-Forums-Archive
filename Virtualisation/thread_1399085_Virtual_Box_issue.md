---
title: "Virtual Box issue"
date: 2010-02-05
forum: Virtualisation
---

### Post by TheKingOfTheKings on 2010-02-05
Every time I attempt to install Virtual box (Non ose) whether it be from apt-get or the .dev i get this error when I attempt to start a vm sudo: /etc/init.d/vboxdrv: command not found I have reinstalled many times, and even tried different versions. I am running Ubuntu 9.10 on a 64 bit gateway. I would appreciate any and all assistance.

---

### Post by mkvnmtr on 2010-02-05
Maybe you should explain what is a vm sudo and what you are trying to do. I do not believe my computer has the command vm sudo either. As I remember I installled my Sun Virtual Box by just double clicking on it .

---

### Post by howefield on 2010-02-05
Are you trying to start your virtual machine from the command line ?

---

### Post by TheKingOfTheKings on 2010-02-05
I have attempted to do it both ways, regardless I get this error. /edit it is not vm sudo it is sudo, simply bad placement of words on my part. the command it tells me to do starts with sudo not vm sudo.

---

### Post by howefield on 2010-02-05
To start a virtual machine from the command line you should use something liekthis

```
VBoxManage startvm WindowsXP
```

Where WindowsXP is the name of your virtual machine.

Just to be clear, have you got Virtualbox installed, working and created a virtual machine yet ?

---

### Post by howefield on 2010-02-05
To start a virtual machine from the command line you should use something liekthis

```
VBoxManage startvm WindowsXP
```

Where WindowsXP is the name of your virtual machine.

Just to be clear, have you got Virtualbox installed, working and created a virtual machine yet ?

The command you are using in the original post would suggest you are trying to re-set Virtualbox up.

---

### Post by TheKingOfTheKings on 2010-02-05
> **howefield said:**
> To start a virtual machine from the command line you should use something liekthis

```
VBoxManage startvm WindowsXP
```Where WindowsXP is the name of your virtual machine.

Just to be clear, have you got Virtualbox installed, working and created a virtual machine yet ?

The command you are using in the original post would suggest you are trying to re-set Virtualbox up.

I have set one up on virtual machine OSE however it does not have USB support. It transfered over to this one This is what it says when I attempt it WARNING: The vboxdrv kernel module is not loaded. Either there is no module          available for the current kernel (2.6.31-19-generic) or it failed to          load. Please recompile the kernel module and install it by             sudo /etc/init.d/vboxdrv setup           You will not be able to start VMs until this problem is fixed.

---

### Post by howefield on 2010-02-05
Try going to Synaptic Package Manager and search for Virtualbox and mark for removal. This won't affect any actual virtual machines that you have created. It will only uninstall the program.

Then ensure that you have the correct .deb package for your Ubuntu version from virtualbox.org, and double click to start the install process.

If you get any errors, post them back here.

---

### Post by howefield on 2010-02-05
> **TheKingOfTheKings said:**
> WARNING: The vboxdrv kernel module is not loaded. Either there is no module          available for the current kernel (2.6.31-19-generic) or it failed to          load. Please recompile the kernel module and install it by             sudo /etc/init.d/vboxdrv setup           You will not be able to start VMs until this problem is fixed.You have edited and added more to your post I see.

Open a terminal and enter the command that it gave,

```
sudo /etc/init.d/vboxdrv setup
```

If that doesn't work, try what I said above.

---

### Post by TheKingOfTheKings on 2010-02-05
> **howefield said:**
> Try going to Synaptic Package Manager and search for Virtualbox and mark for removal. This won't affect any actual virtual machines that you have created. It will only uninstall the program.

Then ensure that you have the correct .deb package for your Ubuntu version from virtualbox.org, and double click to start the install process.

If you get any errors, post them back here.

Synaptic does not detect it. sudo apt-get remove does. There were no errors when installing or uninstalling. /edit I then tried the following  VBoxManage startvm Windows\ XP WARNING: The vboxdrv kernel module is not loaded. Either there is no module          available for the current kernel (2.6.31-19-generic) or it failed to          load. Please recompile the kernel module and install it by             sudo /etc/init.d/vboxdrv setup           You will not be able to start VMs until this problem is fixed. VirtualBox Command Line Management Interface Version 3.1.2 (C) 2005-2009 Sun Microsystems, Inc. All rights reserved.  Waiting for the remote session to open... ERROR: Virtual machine 'Windows XP' has terminated unexpectedly during startup Details: code NS_ERROR_FAILURE (0x80004005), component Machine, interface IMachine, callee  It ofcourse didn't work. Follow by this sudo /etc/init.d/vboxdrv setup sudo: /etc/init.d/vboxdrv: command not found

---

### Post by TheKingOfTheKings on 2010-02-06
Update. I'm rather confused, my power kept crashing last night and now it works ;)

---

