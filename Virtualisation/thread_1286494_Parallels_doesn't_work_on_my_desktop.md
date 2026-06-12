---
title: "Parallels doesn't work on my desktop"
date: 2009-10-09
forum: Virtualisation
---

### Post by Vignesh S on 2009-10-09
OK, I wanted to try out Parallels. I installed it, and put in a trial key. Now, just after I created a windows 7 VM, it comes up with a dialogue box saying that Parallels doesn't work on my procesor, which is a Pentium Dual Core E2160 (2 cores). 

Is this actually a limitation with Parallels? I mean, I've been doing virtualisation VMware Workstation and VirtualBox, and there is no way that this is a fault with my CPU, nor am I about to change it to make it compatible any time soon.

Is there any way to hack Parallels to get it to work on my computer? Here are the specs if anyone needs them:

Intel Pentium Dual Core E2160 @ 1.80GHz (2 cores)
Asus P5VD2-X motherboard
Nvidia GeForce 7600GT Graphics card
1x 2GB YeahDome DDR2 RAM module

If there's any other spec you need, let me know

---

### Post by Vignesh S on 2009-10-10
<bump> surely there is a way to hack Parallels to get it to work on my Desktop...

---

### Post by Vignesh S on 2009-10-12
<bump>

---

### Post by Vignesh S on 2009-10-14
<bump>

---

### Post by sh1ny on 2009-10-14
From [http://download.parallels.com/desktop/v4/wl/docs/eu/PD4fWL_Datasheet.pdf](http://download.parallels.com/desktop/v4/wl/docs/eu/PD4fWL_Datasheet.pdf) :

System Requirements

Platform
X86 and x64 platforms with Intel VT-x or AMD-V
hardware virtualization support enabled
is a prerequisite


I don't think your CPU has hardware virtualization support. You can't "hack" that.

---

### Post by Vignesh S on 2009-10-15
> **sh1ny said:**
> From [http://download.parallels.com/desktop/v4/wl/docs/eu/PD4fWL_Datasheet.pdf](http://download.parallels.com/desktop/v4/wl/docs/eu/PD4fWL_Datasheet.pdf) :

System Requirements

Platform
X86 and x64 platforms with Intel VT-x or AMD-V
hardware virtualization support enabled
is a prerequisite


I don't think your CPU has hardware virtualization support. You can't "hack" that.

What do you mean by hardware virtualisation? I virtualise OS's all the time, and VMware Workstation doesn't have a problem with that

---

### Post by chipper_farley on 2009-10-15
> **Vignesh S said:**
> What do you mean by hardware virtualisation? I virtualise OS's all the time, and VMware Workstation doesn't have a problem with that

Some virtualization technologies require that the CPU perform certain tasks in intercepting various functions and directing them to a guest OS versus the host OS.  I'm pretty sure VMWare can do that in software...Virtualbox can.  It sounds though like Parallels might not.  If that's the case and it requires CPU virtualization support and your CPU does not have that, Parallels will never work.  I recommend using Virtualbox.  It works great.

---

### Post by Vignesh S on 2009-10-16
Thanks for the advice, chipper_farley. Looks like I'll have to go on without Parallels. By the way, I am very wary of going back to VirtualBox, because a system32 error in XP as guest started me on a doomed quest for other Virtual Machine solutions, like VMware. 

Besides, VirtualBox doesn't have the features I need in VMware Workstation.

---

