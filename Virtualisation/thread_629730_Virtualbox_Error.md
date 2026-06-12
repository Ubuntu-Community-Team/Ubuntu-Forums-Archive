---
title: "Virtualbox Error"
date: 2007-12-02
forum: Virtualisation
---

### Post by Bought A Dog on 2007-12-02
dpkg: regarding .../virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb contaning virtualbox:
 Virtualbox_ose conflicts with virtualbox
  virtualbox  (version 1.5.2_25433_ubuntu_gutsy) is to be installed.
dpkg: error precessing /home/fatpigmeat/Desktop/virtualbox_1.5.2_25433_Ubuntu_gutsy_i386.deb (--install): 
 Conflicting packages - not installing virtualbox


So why did this happen  ?

---

### Post by Vadi on 2007-12-02
Because there are two versions of virtualbox - an open-source one, and a non-oss one. Try going to Synaptic (System - Preferences - Synaptic package manager), search for "virtualbox", remove all packages that come up, and try installing again.

---

### Post by Bought A Dog on 2007-12-02
ok thanks now i get this error. How do i fix this ?


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Vadi on 2007-12-02
You didn't follow the instructions on adding yourself to the vboxusers group. I don't have them at hand, but find the manual on their website, they explain how to do it there

---

### Post by Khalis7 on 2008-03-24
> **Bought A Dog said:**
> ok thanks now i get this error. How do i fix this ?


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


You may want to visit this blog: [www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

There, you'll find complete guide to solve your problem n add USB functionality to your virtualbox.

I followed the instruction n everything went smoothly.

Gud Luck.

---

### Post by redunbar on 2008-05-21
After I upgraded Ubuntu to Hardy Heron, I get the following error when trying to start my virtual XP installation:


PIIX3 cannot attach drive to the Secondary Master.
VBox status code: -102 (VERR_FILE_NOT_FOUND).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

What can I do to correct this?

---

### Post by Vadi on 2008-05-21
Tried resetting the machine status?

The problem with VirtualBox is that you can't upgrade it like another app. To upgrade, you must discard the state of all machines, and then uninstall it. Which didn't happen when you upgraded Ubuntu - it, or you, just installed a newer version of virtualbox (like you'd do with any other application) without uninstalling it first & discarding states.

I had this problem too, but I don't remember how I solved it. Some people mention having to install an older version of vb, discarding states, uninstalling, installing new one again.

---

### Post by redunbar on 2008-05-21
Not sure what you mean by "states".  I had no snapshots.  I had upgraded another Ubuntu system from Gutsy to Hardy, and its VirtualBox survived OK.  There was a small problem, but when it came up, the diagnostic told exactly what command to issue to fix it.  However, that VB installation was the Personal Use version, whereas this one is the OSE version. The diagnostic in this case is more obscure.  Before I upgraded, I copied the contents of the .VirtualBox directory to a safe place.  Can I uninstall VB, then reinstall it and copy the .VirtualBox directory back to get my virtual XP installation running again?

---

### Post by Vadi on 2008-05-21
No, not snapshots, but when you close the machine - do you shut it down, or "save the machine state"?

---

### Post by redunbar on 2008-05-22
I always shut it down by logically powering it off, via the Start menu.  

Start > Turn off computer

---

