---
title: "[SOLVED] Run VirtualBox under the Linux 2.6.22-14-rt kernel"
date: 2007-11-28
forum: Virtualisation
---

### Post by Odd-rationale on 2007-11-28
Hello! I'm having trouble starting VirtualBox under the Linux Real Time Kernel (ubunutstudio).

If I boot into the generic kernel, VirtualBox starts fine. Only when I'm using the RT do i get this error message:
> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


I notice that VirtualBox installs a package called "virtualbox-ose-modules-2.6.22-14-generic". Does VirtualBox therefore not support the rt kernel? Is there a hack to get it to work?

Thanks!

---

### Post by HellMind on 2007-11-30
I'm like you :(
Seem to be something related to the kernel - RT :(

---

### Post by Oguz286 on 2007-11-30
I have the same problem only i use kvm. That's got to be it, because it worked fine when i used the generic kernel on my previous installation, but it crashed with the rt kernel.

---

### Post by rolodoom on 2007-12-03
[FONT=Tahoma]I just found a solution here:
[http://www.mail-archive.com/ubuntu-studio-users@lists.ubuntu.com/msg00428.html](http://www.mail-archive.com/ubuntu-studio-users@lists.ubuntu.com/msg00428.html)

Now I have Virtual box running at Ubuntu studio 7.10 AMD64 with real time kernel. Here is what I did.

1. Downloaded and Installed virtual box (Not OSE):
[http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_amd64.deb](http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_amd64.deb)
2. Added root and my user account to vboxusers group
3. edit this file to automatically load the kernel module [/FONT]```
sudo gedit /etc/modules
```[FONT=Tahoma]and added a line with:
[/FONT]```
vboxdrv
```4.Log Out
5. Enjoy VirtualBox

---

