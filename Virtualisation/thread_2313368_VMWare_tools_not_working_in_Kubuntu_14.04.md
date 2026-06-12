---
title: "VMWare tools not working in Kubuntu 14.04"
date: 2016-02-11
forum: Virtualisation
---

### Post by linux_newb2 on 2016-02-11
Hi,

New user to linux here. I'm running a Win 7 64bit host with Kubuntu 64bit guest. I'm having trouble getting the vmtools working for VMWare. It was working fine until I encountered a problem with the GRUB loader (Error: Invalid environment block). I googled that and made a tiny change to the grub config file and reloaded grub as shown here: ubuntuforums.org/showthread.php?t=1284314. Ever since then, the vmware tools have stopped working. I can only increase my screen size to just over half my screen (1920x1080), can no longer cut and paste etc. I've tried:

1) Reinstalling open-vm-tools/desktop packages using apt-get - hasn't helped.
2) Installing VMWare's vm tools through mounting CD drive- hasn't helped either
3) Switching to VirtualBox- this works fine but has problems with 3D acceleration for linux so some programs don't run

I tried running a new virtual machine using the same Kubuntu iso file and the vmtools work fine. So I just need to know what could have changed in between them. Is there a way to copy the vmtools files from the new VM to my old VM? 

Some help would be appreciated. Thanks!

---

### Post by zircon_34 on 2016-02-13
looks like your old vm got somehow screwed up... I would use the new one...why do you want to copy the vmtools from one vm to the other? You may 
Just mout the vmtools as mentioned in 2) and install it. For this you need to cd into that folder using the terminal and run
The .sh install script.

---

### Post by linux_newb2 on 2016-02-13
> **zircon_34 said:**
> looks like your old vm got somehow screwed up... I would use the new one...why do you want to copy the vmtools from one vm to the other? You may 
Just mout the vmtools as mentioned in 2) and install it. For this you need to cd into that folder using the terminal and run
The .sh install script.

I want to copy the files and settings from the working VM to the non-working VM in the hope that they may have changed somehow and replacing them from a functioning VM will make them work again... probably wishful thinking.

I guess the last option is to use the new VM. What is the best way to copy out all my files and programs installed into the new VM?

---

### Post by zircon_34 on 2016-02-16
not sure, I think you can use clonezilla to copy all files AND programs. But I dont know if you will also copy the "false configurations" over to the new VM.

For copying all your files (just copy your home folder), you need to install the [https://www.virtualbox.org/manual/ch04.html#additions-windows](https://www.virtualbox.org/manual/ch04.html#additions-windows) guest addition. I found that quite tricky on mac osX and I never managed to copy large files by drag and drop. However, you could also configure a shared folder between your vm and host system and copy the files there. Perhaps this link may help [https://help.ubuntu.com/community/VirtualBox/SharedFolders ]("https://help.ubuntu.com/community/VirtualBox/SharedFolders")

---

### Post by MAFoElffen on 2016-02-17
I'm curious and have to comment. Your title was a little mis-leading, but that is okay. Read what you said and I understand what you have: Windows 7 Host, with an Kubuntu 15.10 guest.

The link you said you tried was for Ubuntu Karmic, which was 2009, v9.04, when Grub2 was in it's infancy. Around Ubuntu v11.04, there were major changes in Linux kernel, Grub2 and X that made that before a moot point in comparison. What they discussed in that thread was patch long before that...

So you were having what problem with VMPlayer ... with what you thought was the VMPlayer tools ... and did what to grub? Then you had other problems. 

So from doing that from a Winodws host, you create, and when you get to the iso, it is smart enough to autorecognize that it should use an environment for Ubuntu 15.10, 64bit, right? Then after you confirm, it downloads VMPlayer Tools for Linux, and installs it with it. Did it have any erros in that install of that toolset? Did you look at the logs? You did say you had a tools problem, right? What options did you selct during the install of Kubuntu? What eror did it give you on the reboot after the install?

Then you installed VirtualBox and installed it again... Do not mirror the installs. You can copy over data, but not the config of. Let me paint a picture to clearify... Both are type II hypervisors from different vendors. That means that the VM Gust runs on a software virtualized VM, with software virtio drivers to simulate the hardware of the machine. The two are not the same. It would be like doing that between a Dell and an HP (or visa-versa). There are differences there under the hood.

Just don't want you to spend a lot of time and end up breaking you new install. We can help you to get what you need to migrate over, hopefully without causing you more grief... or help you fix your original install. Either way is possible right? What on the original install is what you want? If it was a fresh install... I'm just curious on that.

---

