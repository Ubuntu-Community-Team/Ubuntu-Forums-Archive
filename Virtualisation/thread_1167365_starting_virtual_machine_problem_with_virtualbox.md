---
title: "starting virtual machine problem with virtualbox"
date: 2009-05-22
forum: Virtualisation
---

### Post by lahook on 2009-05-22
I installed virtualbox. I wanted to try it since I see a lot of people prefer it to vmware server.
I read virtualbox can use a vmware virtual machine so I moved it to the computer, and set it up. I cant get it to start. It brings up the "windows wasn't shutdown properly", chose a starting method. Virtualbox just hangs there.
Any ideas? 
This virtual machine is already activated. If I installed a new one with my xp pro cd I don't think it will activate anymore. I had to call last time.

---

### Post by pytheas22 on 2009-05-22
So it hangs at the Windows failsafe-startup screen and you can't do anything?  Keyboard input doesn't work?  That seems strange.

Did you convert the VMware disk image by following instructions like the ones on [this page]("https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool"), or did you just load the .vmdk file into VirtualBox and try to start it?

Do you know whether your Windows virtual machine was shut down properly the last time you ran it?  Did you copy the disk image while your virtual machine was running, or did you shut it down completely (not hibernate) beforehand?  You should shut it down, or it will cause problems.  It could simply be the case that there are file system errors, as the Windows dialog suggests.

Another source of the problem could be that switching to VirtualBox upset Windows, since most of the hardware that it's detecting is different (because VirtualBox and VMware virtualize different hardware).  Windows could be failing to boot because it doesn't have drivers for some of your hardware, or because it thinks you're trying to use one copy of Windows on two different computers, which Microsoft disallows.

---

### Post by lahook on 2009-05-23
You're correct, I did just load the vmdk file. I will try the conversion when I get home from work.
Thank you for the link. I'm sure that will help.

---

