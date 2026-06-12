---
title: "VMWare boot on startup"
date: 2013-09-04
forum: Virtualisation
---

### Post by david93 on 2013-09-04
Hi All

I have searched the forums quite extensivly and I still cannot seem to get VMWare (and my VM) to boot up on startup.

I have tried all (what I seem) possible options and cmd lines into the "Startup Application" box

vmplayer /home/(dir of the vm)/XP.vmx

I am seking possible other options to try. For some reason it is failing to boot on startup of Ubuntu 12.04 via the startup application folder.

I have found the file (.vmx) and bought its location into the application line, however I am thinking that for some reason it is the vmplayer portion of the command that my machine is not liking

Any possible solutions would be greatly appreciated.

Cheers

---

### Post by JKyleOKC on 2013-09-05
Have you tried the "vmrun" command? That's how I do it in Player 5. Look for the manual at [http://www.vmware.com/support/pubs](http://www.vmware.com/support/pubs) and specifically for the "vmrun start VM_NAME" usage...

EDIT: The specific manual is at [http://www.vmware.com/pdf/vix160_vmrun_command.pdf](http://www.vmware.com/pdf/vix160_vmrun_command.pdf)

---

