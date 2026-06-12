---
title: "Copying a virtual machine from one OS to another"
date: 2012-11-29
forum: Virtualisation
---

### Post by Carl H on 2012-11-29
I run VirtualBox on my 64 bit Xubuntu 12.10 PC, and have created a WinXP virtual machine.

If I install VirtualBox on my MacBook, can I just copy the virtual machine files to it and run it?

Or does the virtual machine have to be created on the same kind of system that it runs on? 

Thank you in advance.

---

### Post by howefield on 2012-11-29
Use the Virtualbox > File > Export Appliance to create a file which can be imported in to your other Virtualbox install on the other machine only this time using Virtualbox > File > Import Appliance.

Or simply copy the .vdi file over to the other machine, (or whichever format you have used to create the virtual hard disk)  install virtualbox and create a new virtual machine pointing to the copied .vdi hard disk.

---

### Post by 2F4U on 2012-11-29
I have copied the vdi files on several occasions from one computer to another. Never had a problem with it.

---

### Post by BertN45 on 2012-11-29
I copy the whole directory of the virtual machine and on the other system I use the menu entry: Add VM. Between Linux and Windows it works.

---

