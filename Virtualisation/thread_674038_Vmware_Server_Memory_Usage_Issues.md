---
title: "Vmware Server Memory Usage Issues"
date: 2008-01-21
forum: Virtualisation
---

### Post by ndube on 2008-01-21
I am running VMWARE Server  1.0.4 build-56528 on Ubuntu Server 7.04 X64. 

Whenever I start multiple virtual machines, the memory usage starts at what the virtual machines are assigned, but it creeps up over time (~5MB per second). When the usage reaches my systems limit, all the virtual machines stop responding and I am forced to reboot. Does anyone have any idea why this is happening and how I can fix it?

---

### Post by sausagn on 2008-02-25
Realy?
I have the opposite problem. VMware Server is set to use 900MB of ram for my xp, but when i look in my task manager its only using 15MB!!!!!! so mydisk thrashes a fair bit...   anyone have any idea why?

---

### Post by fjgaude on 2008-02-25
I think I've noticed that nothing either in Ubuntu or WinXP meausures memory used correctly.

I further have noticed if I give more than 512M to the guest my disk swapping seems to start.

In WinXP the Task Manager never shows more than about 250M being used.

All seems okay if I only give 512M; the trouble starts if I give 768M or more, out of my total of 2G.

As time goes on I'm sure VMware will fix some of this, and maybe Linux will learn how to read vm used memory.

I'm a happy camper the way things are presently, but still would like to understand more.

---

### Post by Braino on 2008-02-27
First off, my experience is with VMware Workstation 6, which is the version you have to pay for (I use it at work). I use VMware Server for maemo development at home, but I have never used more than one VM at a time and never over 512MB of RAM regardless of what version I'm using (I have 4GB of memory at home and work). 

ndube, how many virtual machines are you running at one time? Most modern computers, with adequate memory (2+ GB), can usually handle around 3 VMs at one time with decent speed (atleast in Workstation). Also, be sure you aren't over-allocating your memory. If I know I'm going to be running 3 VMs, I'll usually set each VM to about 256MB. Your VMware (not the individual VMs) should also be configured to only take a fraction (3/4 max) of your total system memory. I'm not sure if you can change this setting with VMware Server. If it goes over that, then you have 3 VMs and the host swapping, so of course it is going to be very slow and may even stop responding (not to mention your CPU is spread over 4 OSes). 

Sausagn, I have noticed that when you view the process info for VMware, it is split up into different sections. What you are probably looking at is just the memory VMware is using itself. There are other processes listed that correspond to each individual VM, which is probably the number you are looking for. 900 does seem like over kill, you prob want it in the 500 range. VMware will usually give you a good indication of what the range should be (don't go past the blue triangle). I don't ever set my XP VMs to be over 512MB, and I have 4GB of memory. If the OS needs more memory than that, you prob shouldn't be running it in VMware. 

fjgaude, have you read in the settings what your recommended memory setting is? 768 may not seem like a lot out of 2GB, but that is a lot for a VM running in VMware Server. If Windows is only using 250MB, why do you feel the need to increase it beyond 512MB?

I use VMware for QA and for an easy to setup scratchbox for development. What do you guys use it for?

---

### Post by fjgaude on 2008-02-27
I don't at this point feel a need to increase memory beyond 512M. The recommended is only 256M. As I said, I'm a happy camper presently.

I use vmware for three or four Windows programs that I can't get rid of, as my signature shows.

My box is so fast that quickness is not an issue, either in host or guest.

I usually only run WinXP as a single guest. VMware is smokin'... but I still await for KVM to get a frontend in Ubuntu. It already has one in Fedora. Hopefully, in Hardy...

---

### Post by amelbguy on 2008-09-09
> **sausagn said:**
> Realy?
I have the opposite problem. VMware Server is set to use 900MB of ram for my xp, but when i look in my task manager its only using 15MB!!!!!! so mydisk thrashes a fair bit...   anyone have any idea why?
Hi Sausagn,

I have had a similiar issue. I should note however I am experiencing this issue on Windows Host. I tried upgrade to v1.0.7 and just now found an option to force VMServer to only use physical RAM allocated. Hoping that will forward issue of stopping Page file/disk swap.

Cheers, Amelbguy

---

