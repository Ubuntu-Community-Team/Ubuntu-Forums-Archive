---
title: "Need &quot;Idiots Guide&quot; to share files in Virtual Box"
date: 2009-04-17
forum: Virtualisation
---

### Post by Aurora@FleetBuzz on 2009-04-17
Program:  Virtualbox 2.1.4
Host:  Vista
Guest:  Ubuntu 8.10

I have tried to follow the Virtualbox manual and have installed "guest additions", but I can't get the guest (Ubuntu) to "see" the files on the host (Vista).   I have enabled file sharing in Vista.  No luck.  

Is there an easy way to do this?

---

### Post by DGortze380 on 2009-04-17
> **Aurora@FleetBuzz said:**
> Program:  Virtualbox 2.1.4
Host:  Vista
Guest:  Ubuntu 8.10

I have tried to follow the Virtualbox manual and have installed "guest additions", but I can't get the guest (Ubuntu) to "see" the files on the host (Vista).   I have enabled file sharing in Vista.  No luck.  

Is there an easy way to do this?

Be sure Guest Additions are installed.

Open VirtualBox

Select your VM and select Settings

Shared Folders

Click the icon to add a folder

Specify the PATH and Name

Boot into the VM, should show up as a network drive.

---

### Post by Aurora@FleetBuzz on 2009-04-17
Thank you!  However...
I got an error message:
"unable to mount location
failed to retrieve share list from server"

It did recongnize the network (MSHOME) but won't go further than that.

Any suggestions?

---

