---
title: "Install VirtualBox+Ubuntu+USB"
date: 2010-05-07
forum: Virtualisation
---

### Post by abtu on 2010-05-07
Hello All!

Total newbie so disregard my ignorance!

I want to install:

[LIST]
[*]VirtualBox 3.1.6 for windows hosts (I see that VirtualBox 3.2.0 Beta 1 was released  on May 01)
[*]Ubuntu Desktop (10.4)
[*]Ubuntu Server (10.4)
[*]4gb USB flashdrive
[/LIST]
I have an XP SP3, 32-Bit, 512 memory pc. I will be upgrading the memory to 2GB max allowed soon.

My questions are:

[LIST=1]
[*]Is VirtualBox 3.1.6 compatible with Ubuntu 10.4 or do I have to use 9.10?
[*]Is the 4gb usb flashdrive large enough?
[*]Any up to date video tutorials on this subject (of installation) that you can link me to? Most of them are out dated, don't match my specifics (usb, 32-bit, virtualbox, ubuntu), or quite frankly are not of good quality (bad audio, shaky camera, out of focus, contradictory, etc.)
[/LIST]
Thank you for any/all help!

---

### Post by lmarmisa on 2010-05-07
I'll try to answer your questions:

[LIST=1]
[*]Ubuntu 10.04 runs fine in VirtualBox 3.1.6
[*]I think that you should not use your usb flashdrive for this purpose. Simply you have to define one virtual disk (really this is a NTFS file) for every virtual machine. I recommend you to select dynamic expanded storage mode when you define the new virtual disk, because initially it occupies a very small amount space of the physical hard disk. VirtualBox will propose a size for your virtual disk according to the operating system that you are installing.
[*]This is a video for installing Ubuntu 9.10. The differences with 10.04 would be minimal. This video is a good reference for you. Only one comment to the video: 512 Mbytes would be a good selection for the memory (use this value if you do not have a lot of memory in your physical computer).
[/LIST]
[INDENT][URL="http://www.youtube.com/watch?v=n5ravk1H6DM"]http://www.youtube.com/watch?v=n5ravk1H6DM
[/URL][/INDENT]Best regards,

Luis

---

### Post by abtu on 2010-05-09
thank you for your help and thank you for the link.

---

### Post by abtu on 2010-05-13
from [post]("http://ubuntuforums.org/showthread.php?t=1481336"):
> 
Gave up waiting for root device. Common problems:
    - boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check rootdelay= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/96b486e8-1df5-4e2b-bb21-5968015f6ad8 does not  exist.
Dropping to shell!

Busybox V1.13.3 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for list of built in commands.

(initramfs)
I get the same response when I start VirtualBox. 

I found this [link]("http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html") helpful, but I'm still needing assistance. 

In the process of researching, I found out to press the "esc" button after starting VirtualBox to  access the above and below, but after that I am totally lost.

uuid (with string of numbers)
kernel  /boot/vmlinuz-x.x.xx-xx-generic-pae root=uuid=(with string of numbers)
initrd   /boot/initrd.img-x.x.xx-xx-generic-pae

Press "b" to boot
Press "e" to edit
Press "c" for a command line
Press "o" to open a new line
Press "d" to remove the selected line
Use up and down arrows to select

Any ideas? :-\"

Thank you!

---

### Post by G_Stewart on 2010-05-13
OK,

I'm not trying to steal this thread, but since I am having an issue with VB also, I figured I'd post also.

Here is my thing, I am running Ubuntu 8.06 and VB vers 1.5.6

It loaded fine, when I try to "start" windows it gives me the following:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 I reinstalled the correct driver 3 times, but I keep getting the same reading.....

help if you can.

---

### Post by abtu on 2010-05-14
> VB vers 1.5.6> Result Code: 0x80004005Hi! ):P, I'm no expert but try the following:

[LIST=1]
[*]upgrade to VirtualBox 3.1.8
[*]Google : "Result Code: 0x80004005" (without the quotes) and you will get a few responses from ubuntuforums.org with people having the same issue.
[/LIST]
Good luck!

---

### Post by timbelish on 2011-01-14
> **abtu said:**
> Hi! ):P, I'm no expert but try the following:

[LIST=1]
[*]upgrade to VirtualBox 3.1.8
[*]Google : "Result Code: 0x80004005" (without the quotes) and you will get a few responses from ubuntuforums.org with people having the same issue.
[/LIST]
Good luck!


Hi i download ubuntu 10.04 LTS on my laptop when i install virtual box the usb it will be hidden i can't enable it even when i enabled from the setting the problem is it read the flash name but it is hidden you can't see it inside the gest please helpe 
and the other problem i can't run tow gest in the same time so how i can solve this problems

---

### Post by Quadunit404 on 2011-01-14
I dunno, but maybe you could try creating a new thread instead of reviving a thread that's been dead for several months.

---

### Post by slooksterpsv on 2011-01-16
You need to add yourself to the vboxusers group. To do so click on:
Settings -> Administration -> Users and Groups
Click on your name 
click on Manage groups
Scroll down and find vboxusers, click on vboxusers then Properties, 
Click on the check in your name. 
Click on OK, authenticate. Close all windows, log out, log in, and USB should function.

EDIT: Umm... I think I posted how to do USB in the wrong thread hahaha, I think there was another tab opened that I was going to reply to that I closed. So yeah ignore my comment.

---

### Post by vidtek on 2011-01-17
> **abtu said:**
> Hello All!

Total newbie so disregard my ignorance!

I want to install:

[LIST]
[*]VirtualBox 3.1.6 for windows hosts (I see that VirtualBox 3.2.0 Beta 1 was released  on May 01)
[*]Ubuntu Desktop (10.4)
[*]Ubuntu Server (10.4)
[*]4gb USB flashdrive
[/LIST]
I have an XP SP3, 32-Bit, 512 memory pc. I will be upgrading the memory to 2GB max allowed soon.

My questions are:

[LIST=1]
[*]Is VirtualBox 3.1.6 compatible with Ubuntu 10.4 or do I have to use 9.10?
[*]Is the 4gb usb flashdrive large enough?
[*]Any up to date video tutorials on this subject (of installation) that you can link me to? Most of them are out dated, don't match my specifics (usb, 32-bit, virtualbox, ubuntu), or quite frankly are not of good quality (bad audio, shaky camera, out of focus, contradictory, etc.)
[/LIST]
Thank you for any/all help!

Abtu-

This is a pretty old thread, but I'll stick my 2 bobs worth in.
You ask if 4gb stick is big enough?  Big enough for what? are you trying to run ubuntu from that stick?  4gb is probably ok, but why not use a hard drive as they are cheap enough and save yourself a whole lot of pain.
With regard to Virtualbox, it is great but don't use the OSE version in the repositories, go to the virtualbox website and download the PUEL version, the open-source one has issues with usb stuff.

This is probably all a bit late now........

Best regards, Tony.

---

### Post by jimbo12345 on 2011-03-12
Hi all,

Not sure if this is really relevant now after all this time, but I finally cracked booting from usb from Virtualbox with a usb multiboot menu loader called multisystem  

[http://liveusb.info/MultiBoot-v3/install-depot-multiboot.sh.tar.bz2](http://liveusb.info/MultiBoot-v3/install-depot-multiboot.sh.tar.bz2),  just run the install script within as sudo and it'll install all the bits & pieces needed.

This gui allows you to easily create a bootable usb using ISO files.  I found it really easy to use and it has options to either boot Qemu or Virtualbox from the USB stick, and it worked really well for me.  I guess what it does is the above steps in this thread, but automated.  I've used it with quite a few other linux distro's - puppy / pclinuxos and so far so good!  Haven't yet tried to drag a Windows install ISO onto it yet, but who needs windows now?

---

