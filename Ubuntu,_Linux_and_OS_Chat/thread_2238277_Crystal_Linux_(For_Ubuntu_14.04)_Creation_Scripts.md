---
title: "Crystal Linux (For Ubuntu 14.04) Creation Scripts"
date: 2014-08-07
forum: Ubuntu, Linux and OS Chat
---

### Post by FriedMicro on 2014-08-07
Current Version 2.0

So over the past several weeks and months I've been working on a set of scripts which would allow another user to have their system configured in the same fashion as myself. These scripts have been tested on both live systems and/or virtual machines. Crystal Linux is designed for those whom have a fresh Ubuntu 14.04 install as it may cause problems otherwise. I not responsible for damage resulting from these scripts.

Features:
#UEFI support...which is not possible with an install from Ubuntu Minimal without converting the entire system
#Gnome desktop
#Several Unity Apps have been kept while the rest of the Unity system/interface/daemons have been removed
#FireFox Aurora installed alongside FireFox stable with automatic updates within a Chroot (change the username in the config file)
#A simple cleaning script uses some of the code from Ubuntu Genius in order to remove unused kernel, images, headers, and modules
#A kernel config file (was created for a Lenovo Y510P)
#Numerous development tools for code in C/C++
#Comes with both DosBox and WINE installed
#Simplified construction of .desktop files with Arronax
#Desktop files (require some minor modification) already created
#Linking software and an emulator for the TI-series graphing calculators
#Several pieces of art software included
#Nuvola Player which has support for cloud/internet radio and system integration
#Pidgin chat instead of Empathy chat is used and it can be configured for Facebook chat
#Several WINE scripts included

Several of the apps which come with Ubuntu by default such as Cheese and FireFox are still included.

A full list (or mostly complete) list of software is available at:
[https://github.com/FriedMicro/Crystal-Linux/wiki](https://github.com/FriedMicro/Crystal-Linux/wiki)

You can download all scripts here:
[https://github.com/FriedMicro/Crystal-Linux/archive/master.zip](https://github.com/FriedMicro/Crystal-Linux/archive/master.zip)

Or browse the code at:
[https://github.com/FriedMicro/Crystal-Linux](https://github.com/FriedMicro/Crystal-Linux)

Notes:
#"Transmission" the bitorent client has been replaced with Aria2, but can be reinstalled with:
```
sudo apt-get install transmission-gtk
```

#Configuration for Pidgin to function with FaceBook is available at:
[https://www.facebook.com/sitetour/chat.php](https://www.facebook.com/sitetour/chat.php)

Setup:
1. Extract the zip file
2. Execute the Setup_All.sh script (you will need to mark it as executable)

---

### Post by coffeecat on 2014-08-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

And a quote of the OP's own warning:

> **FriedMicro said:**
> I not responsible for damage resulting from these scripts.

Nor are the forum admins. Please note that this is a first post from a newly registered member. Use this script or not at your own discretion.

---

### Post by sffvba[e0rt on 2014-08-07
> **coffeecat said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*

And a quote of the OP's own warning:



Nor are the forum admins. Please note that this is a first post from a newly registered member. Use this script or not at your own discretion.

And no offence to the OP but the name doesn't inspire any confidence either :p

---

### Post by FriedMicro on 2014-08-07
Yes I'm aware that I'm new member and yeah this is true that the name doesn't exactly inspire confidence :P; the code is open source under an Apache license if there is any suspicion.

If you have your doubts do a fresh install of Ubuntu 14.04 onto a Virtual Machine and test it yourself. It is risky for systems which are not fresh installs, but a fresh install should face little to no risk.

---

### Post by FriedMicro on 2014-08-07
It's very easy for an application to be removed by accident if a dependency was removed in the process hence the reason it's designed for a fresh install. I can say the Aurora install script is perfectly safe even on existing installs and the source code is available at:
[https://github.com/FriedMicro/Crystal-Linux](https://github.com/FriedMicro/Crystal-Linux)

---

### Post by Old_Grey_Wolf on 2014-08-07
The scripts seem to be tied to the Linux/x86_64 3.13.11.2-nuclear Kernel. If true, are you going to update the scripts every time a new kernel comes along? 

I think I will pass, as I can install Ubuntu minimal and add what **I want** to it without the use of your scripts.

---

### Post by FriedMicro on 2014-08-07
They are not tied to any particular kernel and only the Install_Crystal.sh script is linked to any particular version of Ubuntu (14.04 LTS) which since I am currently running and I will be updating the scripts for. I merely uploaded the kernel config as a convience since mine is heavily configured more to share the configuration. Besides the linux kernel doesn't append things like -nuclear to the end of the version by default rather it's there because I put it there. Everything is modular and each script can largely stand on it's own (Make the exception for the two Aurora scripts). Ubuntu minimal is always a possiblity, but I'd like to point out that only installing part of one desktop and then install Gnome rather than unity while still preserving at least some of the Unity apps installed by default. None of these scripts are intended for users whom know how to go from Ubuntu minimal to an entire system since I can say with a reasonable degree of certainty they understand how to do things like setup a chroot or the like. Arronax for example which one script installs is designed for easy creation of .desktop files; as can be seen it's meant to provide easy access to tools for powerusers while still being accessible to entry Linux users.

---

### Post by FriedMicro on 2014-08-07
Edited the title to match more specifically what's posted.

---

