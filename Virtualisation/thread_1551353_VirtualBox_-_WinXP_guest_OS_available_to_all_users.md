---
title: "VirtualBox - WinXP guest OS available to all users"
date: 2010-08-12
forum: Virtualisation
---

### Post by Dimco on 2010-08-12
Hi I'm fairly new to VB and need some clarification on its capabilities. 
I have installed VB in Ubuntu 10.04 and installed WinXP as guest OS. I have administrator rights on the machine and do not have problems running the WinXP in VB as myself. :D
I have created "desktop user" accounts in Ubuntu 10.04 for the other members of my family. When the other members of the family log with their accounts and start VB they could not see the guest OS (WinXP). 
Is this the normal behavior? I.e. do they need to install separate instance of WinXP in "their" VB? Do I need to allow HD space for multiple (discrete) WinXP installs?
If not normal behavior, how can I make the WinXP guest OS instance installed by the "administrator" available to all users when they are logged as themselves?

Many thanks

---

### Post by cpmman on 2010-08-12
Check the vboxusers group to ensure the users are in there.

---

### Post by Joe of loath on 2010-08-12
Virtualbox virtual hard drives are stored in your home directory. You would need to put it in another directory and set the permissions so that all users can r/w to it. If virtualbox needs it to be in the specific home folder of each user, you could setup a dynamic link to their respective folders.

---

### Post by JKyleOKC on 2010-08-14
There's a package called "vboxtool" that can be used to start up the VM when you boot the system, with no need for you to be logged in. Its configuration file tells the boot process where the VBox files are located, and which VM to launch. The rest happens automatically.

Once you install it, you access the VM from the command line as "rdesktop-vrdp localhost" or from the GUI via a launcher that executes that command. Your guest users could probably have that command as part of their autostart list and come up in the VM automagically...

Search the forum for "vboxtool" to find out more about the package. It solved a similar problem for me!

---

