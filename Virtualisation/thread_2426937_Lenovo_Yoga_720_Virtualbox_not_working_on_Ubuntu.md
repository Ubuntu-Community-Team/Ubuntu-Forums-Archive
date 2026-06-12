---
title: "Lenovo Yoga 720 Virtualbox not working on Ubuntu"
date: 2019-09-16
forum: Virtualisation
---

### Post by jellyfishing on 2019-09-16
[COLOR=#494949][FONT=&quot]Hello,[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]I'm trying to run a 64bit virtual machine(Ubuntu) on my Yoga 720 using Virtualbox but it fails. When it loads the screen is black with a keyboard + a stick figure at the bottom. [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot] [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]I've enabled virtualization in the BIOS settings. I've tried many other solutions online but none have seemed to help...such as :[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot] [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]Increasing the base memory[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]Increasing the amount of processors[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]Enabling/Disabling PAE/NX[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]Increasing video memory[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]Enabling/Disabling 3D acceleration [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot] [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]Please help if possible.[/FONT][/COLOR]

---

### Post by lammert-nijhof on 2019-09-21
My settings for Ubuntu are:
RAM 2 GB
4 processors on my Ryzen and 2 on my old i5 laptop.
PAE/NX disabled
video memory 128MB, any size above 16MB should be fine, if 3D acceleration is disabled. 
3D acceleration enabled, in case of problems I first disable 3D acceleration.
I mostly use the VM in full screen mode with auto resize enabled in the View menu.

I assume that besides Virtualbox itself, you also installed the Virtualbox Extension Pack of the same release. To be found on the Virtualbox web site. 
Did you install the Virtualbox Guest Additions through the menu. "Devices" and "Insert the Virtualbox Guest Additions CD".

If all this has been done, please specify what release of Virtualbox and Ubuntu you are using and also what is your Host OS. I assume Windows 10 Home edition?

---

