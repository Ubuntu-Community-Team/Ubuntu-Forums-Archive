---
title: "Virtualbox - deleted vboxdrv, how to recreate it?"
date: 2008-08-21
forum: Virtualisation
---

### Post by xunillinux on 2008-08-21
Hi.

I'm new to Ubuntu Server, Virtualbox, Linux and related and I'm currently learning by doing.

My goal:
Virtualbox running on my headless Ubuntu Server (8.04.1) accessed remotely from my laptop.

VRDP and VBoxHeadless seems to be keywords here, but after following [this quide]("http://ubuntuforums.org/showthread.php?t=833923") for a headless setup, I still couldn't get it to work. I don't remember the exact problem, but after googling I got the impression that I should change to the non ose version.

I removed the ose version using apt-get remove, but saw that some Virtualbox components were still loading during server boot, so I searched the server for "virtualbox" and "vbox" and started deleting, expecting everything to be recreated when installing virtualbox_1.6.4-33808_Ubuntu_hardy_i386.deb downloaded from virtualbox.org.

Now, after installing using ```
sudo dpkg -i virtualbox_1.6.4-33808_Ubuntu_hardy_i386.deb
``` I see that I need to install or recompile the kernel module using ```
sudo /etc/init.d/vboxdrv setup
``` The problem is that I have no *vboxdrv* in /etc/init.d/.

So, how do I recreate *vboxdrv* in /etc/init.d/?


Here is the exact output from running$ **VBoxHeadless**
```
 WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.24-19-386) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
VirtualBox Headless Interface 1.6.4
```


_Update 20080822:_ Copied vboxdrv from another location and got things up and running. The challenge now is to connect to this headless virtual machine from my Mac. VBoxHeadless tells me that I should connect to port 3389, but I haven't figured out just how to do that and how to authenticate. Downloaded RDC from Microsoft, but couldn't connect. Hopefully some more searching and trial an error will get me there.

---

### Post by BurkDP on 2008-08-30
I had the same problem, but solved it a different way. Some packages had been held back (I wish that I had written them down somewhere now...maybe linux headers something?) Regardless I'm glad you solved it, as I wouldn't have been much help.

But I too had to find a good mac client. The RPD client 2 from microsoft never worked for me, but this one has - [CoRD]("http://cord.sourceforge.net/")

"CoRD is a Mac OS X remote desktop client for Microsoft Windows servers using the rdp protocol. It is easy to use, fast, and free for anyone to use or modify."

"Starting with version 0.4, CoRD has a built-in help system which should resolve most issues. CoRD only works on Mac OS X 10.4 and 10.5 and only with Microsoft Remote Desktop Protocol, meaning that it can only connect to computers running Windows 2000, XP Pro, or Server 2003 using the built-in remote support (also known as Terminal Services). VNC and the built in OS X remote desktop server aren't supported by CoRD."

I couldn't find if it's ppc or Intel. And from use, the mouse is a *little*...off, though it's off connecting from a Vista machine so I think it might be a VirtualBox thing.

I hope this was helpful, I only stumbled across your post a few minutes ago so the advice may be a bit moot. :)

---

### Post by yobser on 2008-12-10
I do not why, but vboxdrv is provided for previous version of kernel. If you have kernel and all modules for version X and let it be the newest one.
For virtual box you can find the newest package virtualbox-ose-modules-(X-1)

I do not why. So, I installed previous kernel.

---

