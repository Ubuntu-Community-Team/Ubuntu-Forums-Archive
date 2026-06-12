---
title: "Best way to experience different OSs ?"
date: 2014-03-08
forum: Virtualisation
---

### Post by Ardeshir on 2014-03-08
HI Everyone !
I have newly moved to the open source world and I want to experience different free OSs .
Currently I have Ubuntu and I want to see how Mint , Kali , Fedora (s) , Ubuntu studio and ... look like .
I was wondering is it better to use virtual machine or to install it side by side Ubuntu .
I want to be on Ubuntu (I'm not gonna change the main OS)
I want a solution in which after I erase the operating system , It does it clean , without anything remaining .
+I have powerful hardware resources .

VM or side by side ?

---

### Post by ajgreeny on 2014-03-08
Depending on what you mean by powerful hardware, I would suggest you go with a virtual install.

I use VirtualBox PUEL version from Oracle [Downloads &#8211; Oracle VM VirtualBox]("https://www.virtualbox.org/wiki/Downloads") to try out the coming 14.04 version and it works great on my machine with plenty of disk space, 8GB ram and an Intel i5-3570K cpu.

I have also in the past tried OpenSuse, Fedora, PCLinux-OS and various others, all of which seem to work without major problems in VMs provided the GuestAdditions are installed.

---

### Post by OrangeCrate on 2014-03-08
> **Ardeshir said:**
> HI Everyone !
I have newly moved to the open source world and I want to experience different free OSs .
Currently I have Ubuntu and I want to see how Mint , Kali , Fedora (s) , Ubuntu studio and ... look like .
I was wondering is it better to use virtual machine or to install it side by side Ubuntu .
I want to be on Ubuntu (I'm not gonna change the main OS)
I want a solution in which after I erase the operating system , It does it clean , without anything remaining .
+I have powerful hardware resources .

VM or side by side ?

I try out a lot of new distros by downloading the .iso file, and then installing them to USB drives using the preinstalled Ubuntu program, "Startup Disk Creator". Boot up the drive, play with the distro, and reboot, if you don't like it. If you want to keep it, it's sitting there ready to be installed...

(Sometimes I'll go off on a jag, and try so many new distributions over the course of a day or so, that my wife thinks I have OCD.)

Have fun.

---

### Post by C.S.Cameron on 2014-03-08
To try out multiple O/S's on a bootable USB drive checkout MultibootUSB:
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Vbox is a bit easier though, to get a quick introduction to multiple O/S's, without rebooting.

---

### Post by cjhabs on 2014-03-08
I partitioned my system disk to contain 2 primary partitions to hold a root file system - I have my live system on one and my "next" live system on the other.
For testing/playing I like to run a VM so that I can also get real work on my live system while checking out another distro. However my laptop is a bit old and doesn't support 64 bit VMs so I also have an external USB bootable drive for playing with 64 bit OSes

---

### Post by Ardeshir on 2014-03-09
Thanks everyone !
Problem solved !
I didn't like the boot-option . It is a little untidy .
But virtualbox is great .

But I have a question ?
Currently I'm testing Mint 16 64bit on virtualbox .
It is somehow slow motion , even the mouse motion .
Is it because I'm running it live or becuse of virtual machine ?
Or my Hardwares ?
I allocated 4GB of RAM to it .


**+EDIT :** [SOLVED]
THE problem was Graphics Card allocation , THE VirtualBox's default is 1 MB .
THanks Everyone !

---

