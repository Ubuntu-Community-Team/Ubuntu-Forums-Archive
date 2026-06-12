---
title: "[Ubuntu 13.04 Desktop] Virtual box causing system crash"
date: 2013-08-19
forum: Virtualisation
---

### Post by Simon_Goodson on 2013-08-19
Hello,

I'm new to the linux world, but I've done a lot of work on HW in windows. We are trying to run traffic through a switch, but only want to use 1 machine (a Dell R710). I had been using iperf (and jperf) on Windows to do it, but wanted to switch over to Linux for stability.

So I've installed and gotten jperf to work between two 13.04 systems, so I wanted to move to 1 system with both the host and guest running jperf. My host system is an R710 with 24GB of RAM, 2 processors (16 cores each) and a 100+ GB HDD. I've got a base 13.04 64-bit desktop installation with the addition of openjava 7 runtime and virtualbox installed through the package manager. I used the terminal to install iperf, and put a folder with the jperf on the desktop. Nothing else. I've run jperf in this configuration (minus the virtualbox) for several weeks and not had any problems.

I created a virtual machine through virtual box and allocated 4GB of memory, 12GB of fixed HDD space and 4 processors. I've also enabled the "Use host I/O cache" option under the disk controller because I had problems doing a previous install on a different system without it. The network is a bridged adapter to eth3 which has internet access.  The installer starts to download language packs to the virtual machine and it just freezes. Not just the virtual machine but the entire virtualbox program. Restarting the host and then the VM causes the VM to want to re-install and re-installation causes the same issue. I have deleted the virtual drive and retryed, but that didn't help either.

Can anyone help?

Thanks,
Simon

---

### Post by TheFu on 2013-08-20
If stability is your main goal, then use Ubuntu 12.04 Server and don't use GUIs.  
Lots of people have great virtualbox experiences with Linux hosts. I do not.  It has never been stable on my systems. I've used lots of virtualization programs over the years and just finished ripping out Xen, ESX, ESXi and use KVM now.  On Windows, VirtualBox has been fairly stable ... a month at a time.  On Linux, my expectation of stability is 6-12 months without any issues.

I don't know **anything** about iperf or jperf, but I do know that many java programs do not work correctly, if at all, using openjdk. Have you tried using the Sun/Oracle Java?

It is unclear from your description which OSes are involved where. Please describe that aspect more clearly.

Besides that, what do the log files show?  Logs for both the hostOS and clientOSes?
Giving a clientOS too much CPU and too much RAM is not good either. Less is more for Linux clients until you **know** you need it.

---

### Post by Simon_Goodson on 2013-08-20
> **TheFu said:**
> If stability is your main goal, then use Ubuntu 12.04 Server and don't use GUIs.  
Lots of people have great virtualbox experiences with Linux hosts. I do not.  It has never been stable on my systems. I've used lots of virtualization programs over the years and just finished ripping out Xen, ESX, ESXi and use KVM now.  On Windows, VirtualBox has been fairly stable ... a month at a time.  On Linux, my expectation of stability is 6-12 months without any issues.

I don't know **anything** about iperf or jperf, but I do know that many java programs do not work correctly, if at all, using openjdk. Have you tried using the Sun/Oracle Java?

It is unclear from your description which OSes are involved where. Please describe that aspect more clearly.

Besides that, what do the log files show?  Logs for both the hostOS and clientOSes?
Giving a clientOS too much CPU and too much RAM is not good either. Less is more for Linux clients until you **know** you need it.

Thanks for the reply. I did a reinstall of the host system last night and that cured my problem, whatever it was. Iperf is a command-line tool for generating network traffic. Jperf is just a GUI front end written in java.

Linux's main advantage over Windows from my perspective is that it allows iperf to use more bandwidth on the network. I don't know if it is a driver issue or if Linux just doesn't have as much traffic over the PCIe bus to the network cards, but iperf on Linux generates about 10x the traffic.

I was experimenting and tried both Linux and Windows as the host OS. I only used Linux as the guest. The Windows/Linux combination was first and proved easier to set up. I posted here when I was having trouble with the Linux/Linux combo.

I tried installing official java first, but my lack of Linux experience bit me and I was unable to get it installed. This is also why I'm using the GUI version of Linux.

Anyway, I think that I have it fixed. Thanks for the reply.

Regards,
Simon

---

### Post by TheFu on 2013-08-20
> **Simon_Goodson said:**
> Anyway, I think that I have it fixed. Thanks for the reply.

Could you outline the solution so the next person can learn too?
Also, please mark the thread as "solved" in the thread tools so that people easily see that too.
Thanks!

---

### Post by Simon_Goodson on 2013-08-20
> **TheFu said:**
> Could you outline the solution so the next person can learn too?
Also, please mark the thread as "solved" in the thread tools so that people easily see that too.
Thanks!

I used the thread tools to set it to solved and it looks like it reads solved in the thread header. Is there a different way to do it?

And I am not sure what the exact fix was. Reinstalling the host system (starting over) is what seems to have solved it.

Regards,
Simon

---

### Post by TheFu on 2013-08-20
Oops. My mistake. Didn't see that it was marked [SOLVED] when replying. I'm sure it was.
Reinstalling when you are new might help ... you'll choose slightly different settings with a little extra experience.

Well, I hope we can convince you over time to kick the commercial software and proprietary hardware platform habits completely. ;)  There are very few remaining tasks where commercial software is needed still.

---

