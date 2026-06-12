---
title: "Make ubuntu go full screen in virtual box"
date: 2008-05-15
forum: Virtualisation
---

### Post by Raccoon1400 on 2008-05-15
Installed guest additions
resolution set at 800x600
change it to 1024
resolution goes down to 480
try to change it back, screen gets chopped up.
I want it to get to 1440x900 resolution

---

### Post by mafiafattony on 2011-01-07
Hello there go to system appearance reset to and enter numbers you wish.

---

### Post by thane1 on 2011-01-07
I'm fairly new to virtualbox as well, but I got my resolution to go to 1920x1200 only after upping the memory alloted to the display.  Guest additions alone wouldn't do it.

---

### Post by JohnMac on 2011-01-09
I have the same problem. Trying Natty for the first time In VirtualBox4.0 (Maverick host). I get a small display and I can't change it. To change the numbers do I go System-Preferences-Appearance? What option then?

Once I have created the VirtualMachine am I able to change the settings afterwards, if for instance I need to add Video memory or include 3D acceleration?

---

### Post by thane1 on 2011-01-09
I find some commands are just easier to perform and research through using Terminal.  Open a Terminal session and enter "vboxmanage --help" without the quotes.  There is no manual page for vboxmanage.  But with the --help option you can see the arguments needed to perform various tasks in vbox, to fine tune your system including video.  This is how I gave my vbox ubuntu guest enough vid memory to display larger resolutions, when just trying to set them after installing Guest Additions alone wouldn't do it.  Cheers.

---

### Post by JohnMac on 2011-01-10
Thanks for getting back to me quickas thane1. I'll have to swat up on using the terminal, I'm afraid I have been of a lazy GUI user in the past.

---

### Post by JKyleOKC on 2011-01-10
You can get the help file from the GUI also, and it's very complete. Open vbox, then select "help" on its menu bar, and from there select "Contents" which is the top entry. Scroll down to "vboxmanage" and you'll get everything you need.

You can change just about any setting of the VM from the vbox screens, but only when the VM is powered off. You can't change anything about it when it is running.

---

