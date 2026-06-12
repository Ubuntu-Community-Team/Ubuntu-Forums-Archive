---
title: "What is Ubuntu?"
date: 2014-07-19
forum: Ubuntu, Linux and OS Chat
---

### Post by sam64 on 2014-07-19
Hi. I'm a complete noob with both Virtual Box and Linux. I'm still slightly confused to what Ubunto is. Is Ubunto an ISO for a VM, or can Ubunto be applied as some sort of application to a guest Windows 7 operating system in Virtual Box? The whole reason I'm doing all this is because I want to learn enough about Linux to prepare myself for penetration testing training with Kali Linux without breaking my host operating system.

---

### Post by QIII on 2014-07-19
Moved to its own thread from [here]("http://ubuntuforums.org/showthread.php?t=2231309").

---

### Post by grahammechanical on 2014-07-19
So, you have no intention of using Ubuntu. What help did you get from the Kali Linux forums?

Ubuntu is a Linux distribution. It can be installed on to a hard disk. It can be installed into a virtual machine that is running on another OS provided the hardware is capable of running a VM.

Penetration testing in a VM? I am not sure there is any benefit to that.  And I do not think this forum supports discussions of penetration testing.

[http://en.wikipedia.org/wiki/Linux_distribution](http://en.wikipedia.org/wiki/Linux_distribution)


Regards.

---

### Post by Mark Phelps on 2014-07-19
> The whole reason I'm doing all this is because I want to learn enough about Linux ...

Linux is an operating system kernel.  Ubuntu is a distribution (often abbreviated as "distro") that contains a Linux kernel, some other middleware, and some applications -- packaged with an installer.

There are literally hundreds of distros, but only a handful are well known and most Linux folks use one of them.

For a list of the more well-known distros, visit distrowatch.com.

In my experience, the best place to start would be to get your hands on the Beginner's Guide to Linux (a book) and to go to various website that offer intro material -- as in the Beginner tutorials at Linux.org.

Other folks may have some links to material that they wish to share.

---

### Post by sam64 on 2014-07-20
> **grahammechanical said:**
> So, you have no intention of using Ubuntu.
I'm not sure yet. All I want (and have been struggling to find) is some kind of tool or application that will allow me to learn Linux hands on, safely, on my Windows 7 operating system. The only way I know of to do that is installing the Ubuntu distro tool/application/program/whatever-it-is onto a VM in Virtual Box. That way if something goes wrong, my VM is toast instead of my main host OS. But I'm open to suggestions.

 > **grahammechanical said:**
> What help did you get from the Kali Linux forums?
[http://docs.kali.org/introduction/should-i-use-kali-linux](http://docs.kali.org/introduction/should-i-use-kali-linux)

I'm not ready for help with Kali yet (I need to learn some Linux first, so I don't break anything).

---

### Post by yancek on 2014-07-21
> The only way I know of to do that is installing the Ubuntu distro tool/application/program/whatever-it-is 

As explained above, Ubuntu is an operating system and not an application or program.  You can install it in VirtualBox or some other virtual software.  You can also download the Ubuntu iso and burn it as an image to a DVD or put it on a flash drive and run it live.  A Live CD is an unfamiliar term to windows users as it is not available.  You can run Ubuntu (or most any other Linux) that way to test it without installing it.  The big difference between a Live CD and an installed system is that a Live CD is a read-only filesystem and no changes are saved on reboot. 

Installing it on your hard drive with another system is not that complicated and many millions of users have done that.

---

### Post by mastablasta on 2014-07-21
here is how you do it in virtualbox - the easy way...: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

as other said it's an operating system running most of the internet. i mean not Ubuntu but Linux kernel and it's versions of the OS.

Kali is Debian based, Debian is another operating system and Ubuntu's "father". So it is slightly different. but not that much.

Backbox is like Kali and is Ubuntu based.

---

### Post by Bucky Ball on 2014-07-21
*Thread moved to **Ubuntu, Linux and OS Chat**.*

And better here. Not a support request. ;)

---

### Post by d-cosner on 2014-07-21
I will share with you the MOST VALUABLE information I have ever been given in my life! My brother told me years ago, "It's only software." In other words, if you screw it up you can always put it back on. Way back when I began tinkering with computers I bought a new video card, installed it and totally screwed up my system.

This mistake was the start of my learning how to do things for myself! I had no idea how to install an OS, no idea how to even get started. I found an out of date book and learned one command from it, dir -w, that was all it took for me to find the setup exe for the first release of Win 95. Everything was easy after that!

Today Windows and most Linux distributions have automated installers, my son installed Ubuntu for me when he was 5 and I was recovering from major eye surgery! Why am I telling you all this? You can not be afraid to mess things up or you will never learn anything. I have learned far more from mistakes I have made over the years than all the things that have just worked.

Back up your data and do whatever you want with your computer, it's only software!

---

### Post by stalkingwolf on 2014-07-21
you might also want to look at installing ubuntu to a flash drive or ssd.  I use a 16 gb flash drive.  then just plug it in and boot into your ubuntu system.  this way you can install programs you want.

---

### Post by sam64 on 2014-07-23
> **yancek said:**
> Installing it on your hard drive with another system is not that complicated and many millions of users have done that.

So it's possible to install a Linux Ubuntu OS as a VM on a Windows OS as the host (which cannot be done legally with a Mac OS X)? If so, is there a Ubuntu ISO available to download for free anywhere on this Ubuntu website?

---

### Post by QIII on 2014-07-23
You can get Ubuntu from Canonical:  [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You can get Kubuntu form kubuntu.org:  [http://www.kubuntu.org/](http://www.kubuntu.org/)

You can get Lubuntu from lubuntu.net:  [http://lubuntu.net/](http://lubuntu.net/)

You can get Xubuntu from xubuntu.org:  [http://xubuntu.org/](http://xubuntu.org/)

You can get Edubuntu from edubuntu.org:  [http://edubuntu.org/](http://edubuntu.org/)

You can get mythbuntu from mythbuntu.org:  [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

You can get Ubuntu Studio from ubuntustudio.org:  [http://ubuntustudio.org/](http://ubuntustudio.org/)

You can get Ubuntu Gnome from ubuntugnome.org:  [http://ubuntugnome.org/](http://ubuntugnome.org/)

If you want a Chinese flavor:  [https://wiki.ubuntu.com/Ubuntu%20Kylin](https://wiki.ubuntu.com/Ubuntu%20Kylin)

---

### Post by deadflowr on 2014-07-23
> **sam64 said:**
> So it's possible to install a Linux Ubuntu OS as a VM on a Windows OS as the host (which cannot be done legally with a Mac OS X)? If so, is there a Ubuntu ISO available to download for free anywhere on this Ubuntu website?

At the top of this page, you see a line that says "Quick Links | Forum Community | Ubuntu Communioty | other stuff, blah blah".
click on the Ubuntu Community, and go to Get Ubuntu.
It'll bring you to the Ubuntu download page.

Ubuntu is free. Always has been, always will be.

---

### Post by stalkingwolf on 2014-07-23
you can also check out distro watch to get an idea of how many choices there are.

---

### Post by SeijiSensei on 2014-07-24
Once you have an ISO image from QIII's list, you can install it in a VirtualBox virtual machine in a few easy steps.  

First, download the VirtualBox software for Windows at [https://www.virtualbox.org/](https://www.virtualbox.org/).  Also download the "Extension Pack" while you're there.

Install VirtualBox into Windows the usual way by double-clicking the downloaded installer and following the prompts.

Now when you start VB in Windows, it will offer to set up your first virtual machine.  You'll need to decide on how much disk space to allocate to Linux (20 GB is a good number if you have the space; 10 GB otherwise), and how much memory to allocate to the VM when it is running.  For a current Ubuntu distribution like 14.04, I'd allocate at least a gigabyte.  On machines with 4 GB, I give Ubuntu 1 GB and leave the other three for Windows.  On an 8 GB machine, I give Ubuntu 2 GB.

Follow the prompts from VirtualBox.  You'll eventually be asked the location of the boot medium; point to the Ubuntu ISO file you downloaded earlier.  Eventually you'll see Ubuntu's installer appear in the VirtualBox window.  Follow the prompts to install Ubuntu to the virtual machine.

---

