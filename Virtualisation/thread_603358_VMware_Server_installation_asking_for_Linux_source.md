---
title: "VMware Server installation asking for Linux source in Ubuntu Studio Feisty"
date: 2007-11-05
forum: Virtualisation
---

### Post by shellhrs on 2007-11-05
I've been installing VMware Server in several PCs running Ubuntu Feisty without any problem. I had to install xinetd before I installed VMware though.

On the other hand, I have an IBM Thinkpad T30 running Ubuntu Studio Feisty. I tried the same method as above, but the installer stopped when it asked for Linux source. I had no idea where the source is (I'm a newbie here). I installed Ubuntu Studio the same way I installed Ubuntu Feisty (all default selections).

So, has anybody experienced the same problem? Any solution? I wish to keep running Ubuntu Studio instead of the normal Ubuntu, because I need some of the programs installed by default (and installing them one-by-one is simply out of the question).

Thanks in advance.

---

### Post by shellhrs on 2007-11-06
I didn't remember the exact error message, so I decided to re-run the installation. Here's the error message:
[INDENT]
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include][/INDENT]
If I pressed Enter (for default), another error message appeared:
[INDENT]
The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include][/INDENT]
So I looked into the /usr/src directory, and there is no linux subdirectory. There are only linux-headers-2.6.20.16 and linux-headers-2.6.20.16-generic (also linux-headers-2.6.20.15 and linux-headers-2.6.20.15-generic).

I tried both .16 directory, but still VMware install refused to continue. The error message:

[INDENT]The directory of kernel headers (version 2.6.20-16) does not match your running
kernel (version 2.6.20-16-lowlatency).  Even if the module were to compile 
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include][/INDENT]
So, anyone can help? I really don't want to use the vanilla Ubuntu cause I need some of the programs already installed by default in Ubuntu Studio.

---

### Post by shellhrs on 2007-11-08
Heheheh.... Silly me.

It turned out that I only need to run Synaptic, and install the low-latency file from the list. And.... everything went OK.

Hope this is useful for anyone who has the same problem.

---

