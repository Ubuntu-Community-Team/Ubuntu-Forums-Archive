---
title: "VirtualBox 4.0.6 not working on Ubuntu 11.04"
date: 2011-05-05
forum: Virtualisation
---

### Post by miguelfd on 2011-05-05
Hi Folks,

I've been using Ubuntu since version 8 and VirtualBox either on Linux and Windows. I'm having an issue with VirtualBox and I could not find someone with an issue like that anywhere.
I've installed Ubuntu 10.10 on my Dell Inspiron N4030 and I've been using VirtualBox 4.0.4. Working perfectly, I've installed Windows XP Pro SP3 on a VM and it was working just as it should. Once I've noticed that Ubuntu 11.04 was available for upgrade, I used the **do-release-upgrade** to bring the new version on my laptop. The upgrade was successful (i thought), but when I tried to run that Windows VM, it crashed. After trying to run it a few more times, upgrading the VirtualBox, downgrading, uninstalling and using the OSE version, it is still crashing.
I've finally released that it crashes everytime it captures the mouse or the keyboard after Windows is loaded. But here is a weird this (really): if I start Windows in Safety Mode it'll work.
After realizing that, I tried to uninstall the mouse and keyboard drivers and restart Windows, but it is still crashing when starting it up normally.
I also tried to reinstall Windows, but it crashes during the installation when it captures the mouse.
Please, please tell me some of you got a clue on what's going on... :-)

---

### Post by SynonM on 2011-05-29
Me too.
Linux header problem.
Doing fresh install of latest Ubuntu .iso 
I let you know if all goes well.

---

### Post by shaunehunter on 2011-05-30
I'm running 4.0.8 as I type this. Do you have Oracles repo added in Kpackageki

I suggest adding it as it provides regular stable updates.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Install it and you'll be up in no time.

---

### Post by SynonM on 2011-05-30
> **shaunehunter said:**
> I'm running 4.0.8 as I type this. Do you have Oracles repo added in Kpackageki

I suggest adding it as it provides regular stable updates.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Install it and you'll be up in no time.

did fresh Ubuntu install after backing up my files...

all is well with VirtboxOSE and I needed a fresh install anyway

---

### Post by wamarobert on 2011-06-02
> **SynonM said:**
> did fresh Ubuntu install after backing up my files...

all is well with VirtboxOSE and I needed a fresh install anyway
Usually after upgrading to natty (AKA Ubuntu 11.04) sometimes if you have VMBOX OSE manager already installed, you will tend to experience different kernel problems and etc...........

Medicine is....
1. visit your Synaptic Manager, look for K**ernel C compilers ** just install them.
2. You will jump with flying colours

.....it has worked for me, and i am having over 4 VM Boxes running happily on natty.

rgds,
RB- [email]wamarobert@hotmail.com[/email]

---

### Post by marchdevin on 2011-06-03
[FONT="Verdana"]In order to fix this issue with Virtualbox 4.0 not running on Ubuntu 11.04:

Run the exact command below in the Terminal:

sudo /etc/init.d/vboxdrv.dpkg-bak setup

This should solve the issue.[/FONT]

---

