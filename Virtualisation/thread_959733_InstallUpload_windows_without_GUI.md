---
title: "Install/Upload windows without GUI?"
date: 2008-10-26
forum: Virtualisation
---

### Post by Weissbier on 2008-10-26
Hello guys, im new here in this forums and i search for a solution for my Problem.

My Situation: 
System/Server is a Intel E8400, 4GB 1066DDR2 Ram, running Ubuntu 8.04 64bit as Server with just Apache, mySQL, PHP installed and works as a Webserver so to speak. The server is located in a Datacenter far away.
Now i have a software-tool which is only running on Windows and i would like to use some sort of "Virtualization" to install a WinXP version to my physical server.

I already read maybe 1000 sites about which Virtual Machine tool is the best and i decided to use "Virtualbox".

My Problem is that the Server is located in a Datacenter ~500KM away from me and so i would like to ask if it is possible to Install Windows XP without any GUI (without any Desktop like KDE or such)?

Example:
So i could maybe install it here on one of my PCs, use the method provided by Microsoft to reset all IDE/SATA drivers when you do normally a mainboard change , pack the whole windows c-drive in a 7z package, upload it to the virtual c-drive of the Server, start the virtual-machine server and use pre-setup Remotedesktop to connect to windows XP then. :guitar:
Do you think this is possible? :confused:

If not is there any other way to install XP without the need to have a GUI or without to go with a install CD to the Datacenter.
Or maybe any other solutions?

Thank you in advance!

[COLOR="Red"]-SOLVED- Thanks anyway![/COLOR]
Using Qemu with KVM and ist running like hell... no speed difference to native.

---

