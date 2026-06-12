---
title: "Virtual Box Question"
date: 2008-04-28
forum: Virtualisation
---

### Post by MasterNetra on 2008-04-28
Hi, I am running Hardy the 64bit version (for my labtop which has Intel Core 2 duo) and i had installed Virtualbox OSE and I was wondering how do i share files between the two?

 I am still relatively new to linux so i am still learning my way around so please be detailed with the instructions.
Thanks in advance.

---

### Post by murlosad on 2008-04-28
I used this guide to set mine up: [http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

it's a how-to getting everything up and running, but it does mention the shared folders.

---

### Post by snappy46 on 2008-04-28
This is an extract from the user manual:

There are several ways in which shared folders can be set up for a particular virtual
machine:

  • In the graphical user interface of a running virtual machine, you can select “Shared folders” from the “Devices” menu, or click on the folder icon on the status bar in the bottom right corner of the virtual machine window.

  • If a virtual machine is not currently running, you can configure shared folders in each virtual machine’s “Settings” dialog.


In a Windows guest, starting with VirtualBox 1.5.0, shared folders are
browseable and are therefore visible in Windows Explorer. So, to attach the host’s shared folder to your Windows guest, open Windows Explorer and look for it under “My Networking Places” -> “Entire Network”->“VirtualBox Shared Folders”. By right-clicking on a shared folder and selecting “Map network drive”from the menu that pops up, you can assign a drive letter to that shared folder.

This pretty much explain it all.

Snappy

---

