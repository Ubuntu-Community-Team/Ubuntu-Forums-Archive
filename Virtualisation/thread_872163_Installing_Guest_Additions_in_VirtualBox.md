---
title: "Installing Guest Additions in VirtualBox"
date: 2008-07-27
forum: Virtualisation
---

### Post by eival on 2008-07-27
i found this article about how to do it

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

when i click on Devices > Install Guest Additions, nothing comes up, ever. i know he says it could take a while to open but i waited 5 minutes an nothing opened.


is there a way to do this through a terminal? is so how.

thankx.

---

### Post by jonian_g on 2008-07-27
> when i click on Devices > Install Guest Additions, nothing comes up, ever. i know he says it could take a while to open but i waited 5 minutes an nothing opened.

When you do that make sure that there is no cd, dvd in your drives. If there is one, remove them, restart the virtual machine and you will be able to install the additions.

---

### Post by jimmy the saint on 2008-07-27
The process can vary a lot.  Are you attempting to install guest additions on a linux guest?  You will probably need to install build-essential and your kernel headers first.  Then navigate to the guest additions cd (cd /media/cdrom) and run [code]sudo sh ./VBoxLinux*).  I had to us sh in order for it to work.  Good luck.

---

### Post by jonian_g on 2008-07-27
> **jonian_g said:**
> When you do that make sure that there is no cd, dvd in your drives. If there is one, remove them, restart the virtual machine and you will be able to install the additions.

Sorry, I got it wrong. That is for windows being the guest os not the host...

---

### Post by eival on 2008-07-27
i should of said this at the beginning

Ubuntu is the main OS on my hdd and Windows XP is installed through the VM.


are either of you guy's instructions for my situation or were you refering to the opposite setup?(installing ubuntu in the VM with windows as the main OS)

---

### Post by jonian_g on 2008-07-27
> **eival said:**
> i should of said this at the beginning

Ubuntu is the main OS on my hdd and Windows XP is installed through the VM.


are either of you guy's instructions for my situation or were you refering to the opposite setup?(installing ubuntu in the VM with windows as the main OS)

I was refering at having windows installed in a virtual machine using ubuntu as the main os.

---

### Post by eival on 2008-07-28
i tried restarting after i took out the XP disc, but it still doesnt respond when i click on Install Guest Addition.

do you know what else it could be?

---

### Post by jonian_g on 2008-07-28
Sorry mate, no ideas.

EDIT: I found something that might do the job for you. You can download an .exe installer and run it in your virtual windows to install the additions. Get it here:

[http://code.google.com/p/virtual-box-windows-guest-additions-installer/downloads/list](http://code.google.com/p/virtual-box-windows-guest-additions-installer/downloads/list)

Generaly when you try to install the guest additions from the vbox menu, it dowbloads an .iso file and mounts it. The only problem that might occur is the drive to be occupied (a disc in the drive or another .iso mounted).

---

### Post by eival on 2008-07-28
> **jonian_g said:**
> Sorry mate, no ideas.

EDIT: I found something that might do the job for you. You can download an .exe installer and run it in your virtual windows to install the additions. Get it here:

[http://code.google.com/p/virtual-box-windows-guest-additions-installer/downloads/list](http://code.google.com/p/virtual-box-windows-guest-additions-installer/downloads/list)

Generaly when you try to install the guest additions from the vbox menu, it dowbloads an .iso file and mounts it. The only problem that might occur is the drive to be occupied (a disc in the drive or another .iso mounted).

alright ill try this when i get home. thanks

---

### Post by J_Boi on 2008-12-31
> **jonian_g said:**
> Sorry mate, no ideas.

EDIT: I found something that might do the job for you. You can download an .exe installer and run it in your virtual windows to install the additions. Get it here:

[http://code.google.com/p/virtual-box-windows-guest-additions-installer/downloads/list](http://code.google.com/p/virtual-box-windows-guest-additions-installer/downloads/list)

Generaly when you try to install the guest additions from the vbox menu, it dowbloads an .iso file and mounts it. The only problem that might occur is the drive to be occupied (a disc in the drive or another .iso mounted).
How are you supposed to run the .exe in VirtualBox when you have no mouse control?? :confused:

---

### Post by Dedoimedo on 2008-12-31
Try this:
[http://ubuntuforums.org/showthread.php?t=1024744](http://ubuntuforums.org/showthread.php?t=1024744)

Dedoimedo

---

