---
title: "Desktop virtualization on a headless server"
date: 2012-11-10
forum: Virtualisation
---

### Post by woland on 2012-11-10
I'm looking for your advice on feasibility of the following solution:

Problem:
I have a quad core machine with 8Gb of RAM running Ubuntu 12.04 server that is used for Samba, and Apache for Mantis and WebSVN. Also I have also an old Lenovo R60e craptop that runs WinXP that I use for about everything else.
I'm trying to delay the inevitable - to replace my craptop, by using my server machine.

Proposed solution:
I was planning on setting up 2 VMs, one with Ubuntu 12.10 desktop and the other with Win7/8 as my dev machines, while keeping the headless 12.04 server as the host and using the craptop as the terminal.

My questions are:
1. Is this solution feasible, or am I over-complicating things? If yes, are there better solutions, besides replacing the craptop?
2. What are the best virtualization solution for hosting both Linux and Windows VMs that allows suspending the VM, while releasing the memory, so I could assign 6Gb or RAM per VM?

Thanks!

---

### Post by guht on 2012-11-10
> **woland said:**
> I'm looking for your advice on feasibility of the following solution:

Problem:
I have a quad core machine with 8Gb of RAM running Ubuntu 12.04 server that is used for Samba, and Apache for Mantis and WebSVN. Also I have also an old Lenovo R60e craptop that runs WinXP that I use for about everything else.
I'm trying to delay the inevitable - to replace my craptop, by using my server machine.

Proposed solution:
I was planning on setting up 2 VMs, one with Ubuntu 12.10 desktop and the other with Win7/8 as my dev machines, while keeping the headless 12.04 server as the host and using the craptop as the terminal.

My questions are:
1. Is this solution feasible, or am I over-complicating things? If yes, are there better solutions, besides replacing the craptop?
2. What are the best virtualization solution for hosting both Linux and Windows VMs that allows suspending the VM, while releasing the memory, so I could assign 6Gb or RAM per VM?

Thanks!

I don't want to thread jack, but I am basically looking to do the same exact thing, except my server would be a little beefier with  Intel i7-3770 3.4GHZ and 32GB of RAM.

I want to have the Ubuntu server for web, but also want to setup desktop virtualization so that I can connect and do dev work on my Ubuntu machine from my machine at work which runs Windows 7.

So community you have two people looking to do the same/similar things. Please help!  ;-)

---

### Post by BertN45 on 2012-11-10
I would suggest to use Virtualbox (Vbox). Set up the VMs on the server and enable the remote desktop facility for each VM in Virtualbox. Afterwards you could use any OS with an RDP client to log in to your VMs on the server. The used RDP protocol is the microsoft one, I think the XP version. 

With respect to the network: If you do not use the Vbox bridged network facility with different fixed static IP addresses for each VM, you could specify different port numbers for each VM using the Vbox default NAT facility.

Using the GUI: You could control the VMs using RDP to your physical server and for that you have to install the linux rdp server "xrdp".

Using the CLI: In the past I started and stopped the VM on the headless server using ssh and used the RDP client to control the VM itself. There are ssh clients for windows too. You could use the following commands.

VBoxManage startvm          <uuid>|<name>
and
VBoxManage controlvm        <uuid>|<name> pause|resume|reset|poweroff|savestate|                       acpipowerbutton|acpisleepbutton|
 
Savestate in the CLI or snapshot in the GUI is probably what you are looking for. It saves the state of the machine including all open windows and it saves the state on disk.

Having worked with CLI from 1969 till 1992, I always recommend to use the GUI if possible.

---

