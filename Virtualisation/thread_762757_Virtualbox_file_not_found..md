---
title: "Virtualbox file not found."
date: 2008-04-22
forum: Virtualisation
---

### Post by Robbyx on 2008-04-22
I have looked through the other questions close to this but I am not seeing the same problem solved. 

This is the error report. I would appreciate suggestions as to how best to deal with it, as currently VB will not load.


> The floppy controller cannot attach to the floppy drive.
VBox status code: -102 (VERR_FILE_NOT_FOUND).

Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Robbyx on 2008-04-22
The error message arises as Vbox is trying to load the vdi file. It also says "failed to start VM win2k".

I hope someone will be able to help me out.

Robin

---

### Post by Robbyx on 2008-04-22
This worked for me. I am running one copy of Win2k from within VBox. Vbox became damaged as a result of a crash:

[LIST=1]
[*]Home/.virtualbox (it is a hidden folder)
    Backup the complete directory to a new location.
[*]Delete sub folder within 1 called machines, and the other files in the main folder ie compreq.dat and VirtualBox.xml and xpti.dat. Keep VDI subfolder.
   Delete any versions of windows in /home/robin/.VirtualBox/VDI that  you know are useless. Keep the versions of the VM that you wish to load in future.

Uninstall VirtualBox completely via synaptic.
Reinstall Virtualbox.
Open VB
Create a new virtual machine. Give it the same name as the VM that was left in .virtualbox/Machines.
When VBox asks for a Hard disk find the VM that you saved.
Continue the installation.
Start the VM. It worked for me and I was able to operate Win2K again from within VBox.


Robin

 
[/LIST]

---

### Post by jjlido on 2008-04-25
In my case the issue was abut the DVD mount setting.
I just went into the imege property and I took again the correct device (it was set to /dev/hda)

---

