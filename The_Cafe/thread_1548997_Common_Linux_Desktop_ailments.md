---
title: "Common Linux Desktop ailments?"
date: 2010-08-09
forum: The Cafe
---

### Post by nerdopolis on 2010-08-09
Hi.

What are some common problems that users experiencing in Linux/Ubuntu that would prevent their system from booting, or starting correctly? I mean things that would normally send users into single user mode, not just BIOS or GRUB issues.

Also are there any tools that make system management easier (like an upstart editor) that you know of?

I am trying to make a live cd ([http://sourceforge.net/projects/linuxrcd/](http://sourceforge.net/projects/linuxrcd/)) that helps for system recovery, and I want to add double-clickable scripts (and interactive if they need to be) scripts to it, to allow them to easily fix some common issues. 

Thanks.

---

### Post by XubuRoxMySox on 2010-08-09
The most common ailments I've experienced in Ubuntu/Xubuntu have been caused by **UPDATES**. I mean updates that completely b0rk a perfectly good working system.

I think they can be avoided simply by setting up Update Manager to *accept only security updates* and ignore the "recommended" ones. So far so good since I started doing that.

-Robin

---

### Post by LowSky on 2010-08-09
I find the easiest way to avoid any problems is to create a seperate /home partition. In the case of failure, all I do is reinstall. I can have a working system in under an hour with all my old applications and settings.

Im currently working on writing all my applicaitons I use into a spreadsheet, and the once that is done I will then write a script that will install them all without me having to hunt them all down again.

---

### Post by Frogs Hair on 2010-08-09
One I discovered  early was that I need to remove the Nividia video driver prior to kernel updates . I had an issue with Wubi and my standard installation. Updates are set to notify only. My mobo is Nvidia based , that includes chip-set , audio ,  graphics card , and bus. As long as I do this one thing I have few problems.

---

### Post by rjbl on 2010-08-09
> **Frogs Hair said:**
> One I discovered  early was that I need to remove the Nividia video driver prior to kernel updates . I had an issue with Wubi and my standard installation. Updates are set to notify only. My mobo is Nvidia based , that includes chip-set , audio ,  graphics card , and bus. As long as I do this one thing I have few problems.

Not seen this problem with my rig at all despite using motherboard NVIDIA graphics etc chipset. The proprietary Nvidia 32-bit driver installs and works just fine in 10.04/32 and has not been compromised by this year's kernel upgrades. 

ATB
rjbl

---

### Post by giddyup306 on 2010-08-09
> **LowSky said:**
> I find the easiest way to avoid any problems is to create a seperate /home partition. In the case of failure, all I do is reinstall. I can have a working system in under an hour with all my old applications and settings.



Do you have a link on how I can make a separate /home folder?  I'm quad booting, and I'd like to have a separate for each...

---

### Post by giddyup306 on 2010-08-09
> **Frogs Hair said:**
> One I discovered  early was that I need to remove the Nividia video driver prior to kernel updates . I had an issue with Wubi and my standard installation. Updates are set to notify only. My mobo is Nvidia based , that includes chip-set , audio ,  graphics card , and bus. As long as I do this one thing I have few problems.
Yep.  I've had more problems with xorg and my Nvidia card than anything else.  From what I understand the newer cards aren't that bad, but my computer is ~7 years old.

---

### Post by Frogs Hair on 2010-08-09
> **rjbl said:**
> Not seen this problem with my rig at all despite using motherboard NVIDIA graphics etc chipset. The proprietary Nvidia 32-bit driver installs and works just fine in 10.04/32 and has not been compromised by this year's kernel upgrades. 

ATB
rjbl

Thats good to here , I am using 64x and read that this should not be an issue anymore  , but I am not alone in this I have seen a number threads on this. I just don't want to spend another afternoon repairing an installation and removing the driver works. My computer is less than a year old so I don't suspect any hardware issues.

---

### Post by nerdopolis on 2010-08-11
Ok. So we Have Nvidia issues. 

is that those DKMS errors that you see, right?

Uh... How do you fix those? (So I can add a script to the Live CD) I can't seem to find any fixes, does it involve reinstalling the Nvidia drivers, or reconfiguring DKMS?

---

### Post by cariboo on 2010-08-11
Most issues are due to rumour. For the majority of us the Nvidia drivers in the repositories work quite well.

To see how quickly an issue with gets solved have a look at [thread]("http:///ubuntuforums.org/showthread.php?t=1549195"). 

When a new version comes out you will plenty of issues with upgrading, but the majority of those are due to user problems. The devs have been making it easier with every new version, but if people don't read the release notes before upgrading, they can run into all sorts of problems.

---

### Post by nerdopolis on 2010-08-23
Are there any other common ailments that would make an Ubuntu (Or any desktop Linux distro) stop working normally?

---

### Post by Paul820 on 2010-08-23
My old (very old :D ) nvidia Gforce fx5200 works fine with all the kernel updates, it even runs compiz with full effects.

---

### Post by julio_cortez on 2010-08-23
> **giddyup306 said:**
> Do you have a link on how I can make a separate /home folder?  I'm quad booting, and I'd like to have a separate for each...
You'd need to specify partitions manually during install..
So you'll be able to have something like my setup:

sda1: Windows 7 (NTFS, primary, 250GB, *not mounted by default in Ubuntu*)
sda2: Data (NTFS, primary, 500GB, shared between W7 and Ubuntu and *mounted by default in Ubuntu*)
sda3: /home (ext4, primary)
sda5: / (ext4, logical)
sda6: swap (logical)

When you reinstall, you only have to format the / partition, leaving the /home untouched :)

YMMV anyway, as I dual-boot..

---

### Post by Frogs Hair on 2010-08-23
> **cariboo907 said:**
> Most issues are due to rumour. For the majority of us the Nvidia drivers in the repositories work quite well.

To see how quickly an issue with gets solved have a look at [thread]("http:///ubuntuforums.org/showthread.php?t=1549195"). 

When a new version comes out you will plenty of issues with upgrading, but the majority of those are due to user problems. The devs have been making it easier with every new version, but if people don't read the release notes before upgrading, they can run into all sorts of problems.

I had no Nvidia issues with latest kernel upgrade. I think my 9.10 experience made me a bit gun shy, as for operator error I have always installed Nvidia current via the hardware and drivers jockey and checked to see if my 8 series card is compatible with the current driver. I do not download from the Nvidia site and attempt  to install the package myself.

---

### Post by del_diablo on 2010-08-23
> **giddyup306 said:**
> Do you have a link on how I can make a separate /home folder?  I'm quad booting, and I'd like to have a separate for each...

Just make another parition, format it to a enjoyable file format, and select it under each install to be mounted as /home.

---

### Post by nerdopolis on 2010-08-28
So besides NVIDIA issues, are there any other issues that might force a user to use single user mode, or chroot from a live cd (If they know how to do that)

---

### Post by d3v1150m471c on 2010-08-28
Adding processes to bashrc without running them in the background.

---

