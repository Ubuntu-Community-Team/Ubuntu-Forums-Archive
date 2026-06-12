---
title: "Really confused on which virtualization direction to take here..."
date: 2012-04-09
forum: Virtualisation
---

### Post by greavette on 2012-04-09
Hello,

We've been using VMware Server (1 and 2) for the past 3 years to run roughly 15 VM's in our small office.  Two VM's are pretty big and important for us in that they run Windows Server 2008 Standard with SQL Server databases to run our data collection.  The rest of the VM's we run are a variety of Ubuntu Server, Windows 2003/XP VM's that are still important but not as resource hungry as our two SQL Server VM's.  

VMware Server has done us well over the years but I've always wondered if we could get better performance from level one hypervisor.  

We have two Host Dell T710's to run our VM's.  One has Windows 2008 R2 Standard.  The other is brand new with no O/S yet.  Both have 32 GB's of Ram.  My plan is to run all VM's on one host and have a qnap device setup between the two Hosts for backup.  In the event one host goes down I can quickly fire up all VM's on the other host.  I'm also considering running VM's from the QNAP device but I'm thinking I may be over my head with how to set this up.  

So I'm at a crossroads here.  I want to move away from VMware Server...or I need to move away since it's not being supported anymore anyway.  I've thought of using Hyper-v on both servers since I know these Dell Servers can run Windows with no problem.  But even though Hyper-V is free to install with the Windows O/S, there is licensing costs if I want to run my 15 or so VM's (I don't know exactly what it would cost, but I know it's not free).  I don't mind paying for something if it's worth it, but I'd really like to keep costs to a minimum and see if there are alternatives out there that would suit us better.  I could go with installing Ubuntu on both Hosts, but I'm concerned that this may be a pain to setup with drivers and getting Ubuntu working on them.

Whatever solution we go with I do have some specific requirements:
[LIST]
[*]I support this office remotely and although I'm comfortable with the command line, I need to have a desktop interface in case I need someone at the office to look at the host for me.
[*]I'm more comfortable with Ubuntu as I've not used Fedora/Cent OS before.  I suppose I could use Debian since Ubuntu is based on Debian.  If not a Linux Solution then I could put Windows on both Hosts.  Windows would be ideal for us since anyone at the office would be familiar with a Windows Host.  Both Servers are only used as virtualization hosts.
[*]Whatever virtualization solution we end up using must have a web interface to allow a user to quickly start/stop a VM.  In the event I'm not available, certain people at the office could log into the web interface to see the status of a VM and give it a kick if they need too.
[/LIST]
I'm leaning towards Virtualbox.  It's easy to setup and use.  It can run on Windows or Ubuntu.  My only concern is with performance.  Last year when we bought our first Dell T710 Server we split our two SQL Server VM's across Raid Arrays to help improve performance already which helped immensely.  Is Virtualbox ready for Production in our small office?
Or I could use KVM (maybe proxmox) as I've heard good things about this virtualization product...but KVM is totally new to me too.  Am I biting off more than I can chew by taking on KVM?  I'm not adverse to reading and learning new things but I do have other work/tasks and can't devote all my time to a really steep learning curve.

Okay...I'll open this up to the community now.  What would you suggest I do?

---

### Post by dcstar on 2012-04-10
> **greavette said:**
> 
..........
VMware Server has done us well over the years but I've always wondered if we could get better performance from level one hypervisor.  
..........

You do, that is why things like VMware ESXi outperform all the half-arsed Virtual environments that sit on top of other running OSs.

The only downside to ESXi is that you need to have a Windows client somewhere on the network to manage it.

---

