---
title: "hyper-V server hangs from time to time"
date: 2012-03-15
forum: Server Platforms
---

### Post by gangaskan on 2012-03-15
i have a Ubuntu 11.10 VM on Hyper-v and ceases to respond via networking, is there anything in particular i need to look at in dmesg?  or in /var/log for that matter?  


tools for linux were installed and i was using the gigabit adapter.  

i am going to switch to legacy to see if anything changes 

i have dansguardian, squid, and FOG running on this server if that helps any.

---

### Post by maci4 on 2012-04-03
I have this same problem. How Can you resolve this?

---

### Post by arrrghhh on 2012-04-04
> **maci4 said:**
> I have this same problem. How Can you resolve this?

Honestly I found Hyper-V to run Windows VM's fairly well - but in a mixed or heavily virtualized production environment, Hyper-V just didn't stack up, at all.  The cost was becoming so great, that VMWare was actually cheaper because we didn't have so much downtime, and didn't need to spend so much engineer time trying to keep the entire thing running.

Either way, if you're looking to virtualize Ubuntu for free, look into VirtualBox.

---

### Post by spynappels on 2012-04-04
> **arrrghhh said:**
> Honestly I found Hyper-V to run Windows VM's fairly well - but in a mixed or heavily virtualized production environment, Hyper-V just didn't stack up, at all.  The cost was becoming so great, that VMWare was actually cheaper because we didn't have so much downtime, and didn't need to spend so much engineer time trying to keep the entire thing running.

Either way, if you're looking to virtualize Ubuntu for free, look into VirtualBox.

+1

I had to set up some virtualised servers for a client in Australia, and I was supplied with a Win2008 server with Hyper-V. I had so many problems, not only with Ubuntu but also with CentOS, that I eventually just installed VirtualBox and used that. Ironically, they could just have installed Ubuntu on the base server and run VBox headless on that and saved themselves a bunch of money, but there you go...

---

### Post by rubylaser on 2012-04-04
> **arrrghhh said:**
> Honestly I found Hyper-V to run Windows VM's fairly well - but in a mixed or heavily virtualized production environment, Hyper-V just didn't stack up, at all.  The cost was becoming so great, that VMWare was actually cheaper because we didn't have so much downtime, and didn't need to spend so much engineer time trying to keep the entire thing running.

Either way, if you're looking to virtualize Ubuntu for free, look into VirtualBox.

Or [Proxmox]("http://pve.proxmox.com/wiki/Main_Page") for another free solution.

---

### Post by geudrik on 2012-04-04
You should look into using KVM or Xen also. These are two well-documented and supported hypervisors (and they're free)

I realize these are Linux hypervisors, but in a perfect world, your Win Server install would be virtualized giving you more freedom with the hardware you have. This would also allow a more virtualized environment for individual services as you can deploy on the fly, on an as-need basis as well.

---

