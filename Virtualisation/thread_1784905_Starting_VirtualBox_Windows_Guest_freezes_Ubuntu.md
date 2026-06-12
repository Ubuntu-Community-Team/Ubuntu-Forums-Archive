---
title: "Starting VirtualBox Windows Guest freezes Ubuntu"
date: 2011-06-17
forum: Virtualisation
---

### Post by beau.raines on 2011-06-17
Today, when I'm starting a Windows XP guest in VirtualBox 4.0, Ubuntu crashes.  This does not happen when I start a ChromeOS guest nor did it happen yesterday.

When this crash occurs, I am dropped to the terminal which all the boot output was directed too and the computer is frozen. The only way I've recovered has been by pressing the power button.

Is anyone else having this issue?

This morning I updated the following packages via the Update Manager.

Start-Date: 2011-06-17  08:29:03
Upgrade: python-libxml2 (2.7.6.dfsg-1ubuntu1.1, 2.7.6.dfsg-1ubuntu1.2), dkms (2.1.1.2-2fakesync1, 2.1.1.2-2ubuntu1), libxml2 (2.7.6.dfsg-1ubuntu1.1, 2.7.6.dfsg-1ubuntu1.2), sysvinit-utils (2.87dsf-4ubuntu17.3, 2.87dsf-4ubuntu17.4), libxml2-utils (2.7.6.dfsg-1ubuntu1.1, 2.7.6.dfsg-1ubuntu1.2), grub-common (1.98-1ubuntu10, 1.98-1ubuntu12), sysv-rc (2.87dsf-4ubuntu17.3, 2.87dsf-4ubuntu17.4), initscripts (2.87dsf-4ubuntu17.3, 2.87dsf-4ubuntu17.4)
End-Date: 2011-06-17  08:29:46

I have removed and re-installed virtual box with no luck.


||/ Name                             Version                          Description
+++-================================-================================-=====================
ii  virtualbox-4.0                   4.0.8-71778~Ubuntu~lucid         Oracle VM VirtualBox

I am running Linux 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux


Should I use force the previous versions, confirm that VirtualBox still works and then one by one upgrade them? Or is there a better solution?

---

### Post by lmarmisa on 2011-06-17
Maybe you have defined too much memory for your XP virtual machine. Try to reduce the Base Memory (512 MB could be a good value for testing if this the cause of your problem).

---

### Post by wolfgangmcq on 2011-06-17
Define "crashes": if it's an older machine, it may just be overloaded. I once tried running VirtualBox on a machine made for Windows 98--the system sat for 20mins trying to log me in to CTRL-ALT-F1, then another 5 to killall virtual box. It might help if you described the symptoms.

---

### Post by beau.raines on 2011-06-18
Thanks for the responses

> **lmarmisa said:**
> Maybe you have defined too much memory for your XP virtual machine. Try to reduce the Base Memory (512 MB could be a good value for testing if this the cause of your problem).

My XP vm has the least amount of memory of all of my other vms. I was able to run two other linux based vms (OpenBravo ERP net appliance and ChromiumOS) both with more base memory assigned to them.

> **wolfgangmcq said:**
> Define "crashes": if it's an older machine, it may just be overloaded. I once tried running VirtualBox on a machine made for Windows 98--the system sat for 20mins trying to log me in to CTRL-ALT-F1, then another 5 to killall virtual box. It might help if you described the symptoms.

Crash symptoms...

I start the vm from the Virtual Box manager, all within my GNOME desktop. The new window will open, show the VirtualBox splash and then the monitor will switch to a full screen terminal (like tty1), showing some of the output messages from when the computer first boots and will be frozen. No typing, no Ctrl+Alt+number to switch to another tty.  The only way out is to turn the computer off.

Its not that the xp guest crashes, my Ubuntu 10.04 /host/ crashes!

The only configuration change was the package updates which I installed.  None of those packages (as far as I can tell) really have anything to do with virtualization, so I don't think that is the problem, but its something that changed.

I'm open to ideas and thanks again!

---

### Post by beau.raines on 2011-06-23
Interestingly, this issue has stopped. I've not made any configuration changes or installed new packages.

---

### Post by zero244 on 2011-06-25
One of those strange things using computers......sometimes they magically fix the problem on their own.
I had a windows xp machine that would freeze while playing flash vids..........then one day it stopped and hasnt frozen up since.

---

### Post by bj0 on 2012-01-26
This thread is marked as [SOLVED] although there is no solution.

I have run into this problem lately, but it is not consistant.  I have several virtualbox VMs defined, and it seems that often when I launch my XP virtual machine, the window will open, the splash screen will show, and then the whole *host* machine will simply freeze.  The only thing I can do is either use the power button or sysrq+b.

The odd thing is that it doesn't always happen, but it happens a lot.  Also, after rebooted from the freeze I can launch the XP virtual machine fine, so I'm not sure if it has something to do with the computer running for a while or launching/closing other VMs before launching the XP VM.  No other VM causes the same problem.

My system is an i5 2500k with 16gb ram, which is never close to being filled.  My XP vm has 1gb ram allocated, I'm using VBox 4.1.8.

---

