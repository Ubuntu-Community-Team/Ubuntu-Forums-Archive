---
title: "The preformance loss"
date: 2009-04-03
forum: Virtualisation
---

### Post by dE_logics on 2009-04-03
What are the performance losses on running a version of windows (7, vista, or XP) on UBUNTU?

I mean the performance losses if the program is made to run on the virtual environment.


And what about the efficiency at which DX10 games work?

Will WINE make the application preform better as compared to Virtualization (not talking about the DX10 games, I think WINE doesn't support that till now)?

---

### Post by James_Lochhead on 2009-04-03
The performance loss is significant. You won't be able to play DX10 games in a VM. I tried COD2 DX9 - released 2005 I think and that lagged very badly. VMs are primarily for desktop applications like Word and software testing.

Wine is your best bet. It is a compatibility layer rather than an emulator, meaning that you don't have to run one OS on top of another (i.e. much less, if any, performance less). The same game works perfectly in WINE (except for PB).

---

### Post by dE_logics on 2009-04-04
But WINE doesn't play DX10 games right?

---

### Post by dE_logics on 2009-04-04
Also I heard that the linux kernel is being modified to aid high performance Virtualization.

Is that true?

---

### Post by UranUtan on 2009-04-06
> **dE_logics said:**
> What are the performance losses on running a version of windows (7, vista, or XP) on UBUNTU?

I mean the performance losses if the program is made to run on the virtual environment.


And what about the efficiency at which DX10 games work?

Will WINE make the application preform better as compared to Virtualization (not talking about the DX10 games, I think WINE doesn't support that till now)?

Assuming you have a decent host hardware. Here is the hardware I used for some tests: Intel Core 2 Duo 3.0GHz, 8 GB Ram, 2 independant SATA drives. Host is Ubuntu 8.10 x64.

Using VirtualBox 2.20 beta2, the performance is pretty good. Booting WinXP (800 MB Ram) takes less than 30 seconds. The WinXP VM runs even better than on my old computer (P3 1 Ghz, 700 MB ram). Booting Windows Server 2008 x64 takes 1.5 to 2 minutes. I read somewhere that VirtualBox allows around 80 to 85% of performance of a native machine.

I have also used VMWare Workstation 6.5 and I find that VirtualBox is snappier.

I don't do any games or multimedia stuffs on these Windows VMs so I cannot comment on the graphic part. For the dev, tests, stuffs I find that the VMs are satisfactory.

As for Wine, I can only get it work for text based programs like MP3Tag. Each time I try a game on Wine it ruins my Ubuntu machine. The games never works, hung the machine or male the computer crawl very slowly. Whgen I could exit or reboot, the graphic configuration in a wierd way I have a lots of troubles to fix. In short, even if you pay me to play games with Wine I won't accept. And the games I talk about are not the high end games, those are the board or puzzle games.


If you really like game, I think the safest option is to dual boot.

If you want the best performance in VM, you'll need to go with a "bare-metal" type of virtualization (the machine is dedicated to operate the hypervisor and nothing else) like VMWare ESX or XEN Server. I've read some benchmark, this approach gives you almost the same performance than a native machine when the number of guest OS is less than 16. However, this is just FYI. This approach is overkill for the question you asked.

Hope that help.

---

### Post by veloce on 2009-04-07
> **dE_logics said:**
> What are the performance losses on running a version of windows (7, vista, or XP) on UBUNTU?

I mean the performance losses if the program is made to run on the virtual environment.


And what about the efficiency at which DX10 games work?

Will WINE make the application preform better as compared to Virtualization (not talking about the DX10 games, I think WINE doesn't support that till now)?

vm performance of anything graphic intensive will be poor as 3d acceleration is beta at best.

On the other hand, for my excel 2003 modelling, I get slightly **better** than native performance.  This is a combination of linux' better smp support and that the vm has none of the extra rubbish I would have installed on a native windows box.

---

