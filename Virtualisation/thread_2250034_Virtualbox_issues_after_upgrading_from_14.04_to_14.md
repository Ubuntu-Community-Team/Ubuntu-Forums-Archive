---
title: "Virtualbox issues after upgrading from 14.04 to 14.10"
date: 2014-10-26
forum: Virtualisation
---

### Post by open2linux on 2014-10-26
After upgrading to 14.10, virtualbox does not start win7 that I had before. How to recover that?

---

### Post by Vladlenin5000 on 2014-10-26
Any error message? What happens exactly?

---

### Post by ibjsb4 on 2014-10-27
> **open2linux said:**
> I have exactly the same problem you had, happy that you managed to solve it.
Can you elaborate a little more explaining how did it?
That may help others with the same isse. Certainlly it will help me.
Thanks!
You wish to remove guest additions.
[https://help.ubuntu.com/community/VirtualBox/GuestAdditions](https://help.ubuntu.com/community/VirtualBox/GuestAdditions)

---

### Post by lonewohlf42 on 2014-10-28
You need to recompile the kernel to include virtualbox. There should be an error box saying you have to enter a command "/etc/init.d/vboxdrv setup"
you need to open a command window to enter this. use CTR-ALT-t to open the window terminal and enter "sudo /etc/init.d/vboxdrv setup". At the prompt enter your password and the system will recompile your kernel.
Be patient it could take a minute or two. This has to be done every time the kernel is upgraded. Hope this works for you

---

### Post by open2linux on 2014-11-03
Vladlenin5000, este es el error que me sale:

There is no virtual machine with the identifier f4a630af-29ae-401f-8968-48f687a51d70.
Could not find a registered machine with UUID {f4a630af-29ae-401f-8968-48f687a51d70}.
Result Code: 
VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)
Component: 
VirtualBox
Interface: 
IVirtualBox {fafa4e17-1ee2-4905-a10e-fe7c18bf5554}

Win7 comienza el arranque pero se para en el logotipo de windows.

---

### Post by open2linux on 2014-11-03
Thanks lonewohlf42

After typing the command
"sudo /etc/init.d/vboxdrv setup"
i get the message
"command not found"
am I missing something?

---

### Post by slickymaster on 2014-11-03
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by slickymaster on 2014-11-03
> **open2linux said:**
> Thanks lonewohlf42

After typing the command
"sudo /etc/init.d/vboxdrv setup"
i get the message
"command not found"
am I missing something?

I would suggest a reinstall. Backup your VM, although a reinstall never touches any of the VM files, just to be safe.

---

