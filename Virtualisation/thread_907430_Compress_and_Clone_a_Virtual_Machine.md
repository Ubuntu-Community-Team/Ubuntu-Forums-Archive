---
title: "Compress and Clone a Virtual Machine"
date: 2008-09-01
forum: Virtualisation
---

### Post by johnehowe on 2008-09-01
When creating a Virtual Machine in Vbox the initial size of the VM image would be more or less equal to the disk space actually used in the VM. However over time you will find that the size of the VM image will continue to increase. The disk space actually used is much less than the VM actual image size. We will compress the VM image to the space actually used up inside the VM.

***[SIZE="2"]Note: The image that you are going to shrink must have been created as a dynamically expanding type, when you created the disk very first time.[/SIZE]***
**Getting Started**

You will need the following tools:
1.[INDENT][http://www.feyrer.de/g4u/nullfile-1.02.exe](http://www.feyrer.de/g4u/nullfile-1.02.exe) : This tool zeros out free space, which the  next tool actually compresses the VM.
Note: For Linux based OS, search for a file, zerospace.c, which you will need to compile yourself.[/INDENT]

2.[INDENT]VBoxManage : This tool is the command line management tool that is provided with VirtualBox. [/INDENT]
Follow these steps:
[LIST]
[*]First boot-up your VM and Defragment (assuming a Window$ machine) your drive at least twice.
[/LIST]
[LIST]
[*]Copy the tool, nullfile mentioned above to the VM and run it. A simple double click should do it.
[/LIST]
[LIST]
[*]Wait for the nullfile to finish and then shutdown the guest VM.
[/LIST]

[LIST]
[*]Open a terminal in the VM image directory on the Host machine. Typically /home/username/.VirtualBox/VDI
[/LIST]

Run the final command to compact the VM
	[LIST]
[*]VBoxManage modifyvdi name_of_your_VM.vdi compact
[/LIST]
		(ie. . VBoxManage modifyvdi VboxXP.vdi compact)

That is all that is required. After a few minutes, you will have a much smaller compressed VM image.
Using the steps above, I was able to compress my VM from 4.2 GB to 2.3 GB

**Copy/Clone/Backup Virtual Machine**
Most people don&#8217;t realize that there is more to making a backup of a VirtualBox Machine (.vdi) than simply just doing a copy/paste. If you do that, you will not realize that it does not work  until you need it, and then it is too late! The following is the proper command to backup your VirtualBox Machine:

[LIST]
[*]VBoxManage clonevdi [path of existing VM] [desired path of copied VM]
[/LIST]

i.e. VBoxManage clonevdi /home/john/.VirtualBox/VDI/VboxXP.vdi /home/VboxXP2.vdi

---

### Post by Oldsoldier2003 on 2008-09-01
Moving to virtualization.

---

