---
title: "VMWare ESXi for free?"
date: 2008-08-18
forum: Virtualisation
---

### Post by TheGameAh on 2008-08-18
I understand VMWare has a new free product, ESXi?  Are there any other differences between this and VMWare server, except for running on bare metal?

---

### Post by fjgaude on 2008-08-18
From what I'm reading it would seem that ESXi is not able to actually create VMs... you would need something like VMware Server to do that. At least this is what I get from reading the vmware web site... I could be wrong.

Well, on second thought ESXi can create VMs... hope someone can testify to it.

---

### Post by schmick on 2008-08-18
What I've seen about VMware ESX servers is kind of a virtualization OS.
First you instal ESX on an brand new box with no OS.
You boot up to ESX and now you can create your virtual drives, split the ram and create all the machines you want.
ESX acts as the host, all your machines are vitual.
That way, instead of buying 10 machines for specific purposes, you can run multiple machines on the same physical box which is supposed to be more cost effective. Well.. kinda true.. until THAT machine breaks and... well.. you loose all your virtual ones as well.

My way of thinking:
Remember thoes TVs that came with a VCR and Radio all-in-one?.. break one, loose all.
So.. don't put all the eggs on the same basket.
ESX is a nice idea.. but.. just a nice idea.

---

### Post by jayson.rowe on 2008-08-18
> **schmick said:**
> What I've seen about VMware ESX servers is kind of a virtualization OS.
First you instal ESX on an brand new box with no OS.
You boot up to ESX and now you can create your virtual drives, split the ram and create all the machines you want.
ESX acts as the host, all your machines are vitual.
That way, instead of buying 10 machines for specific purposes, you can run multiple machines on the same physical box which is supposed to be more cost effective. Well.. kinda true.. until THAT machine breaks and... well.. you loose all your virtual ones as well.

My way of thinking:
Remember thoes TVs that came with a VCR and Radio all-in-one?.. break one, loose all.
So.. don't put all the eggs on the same basket.
ESX is a nice idea.. but.. just a nice idea.

In a production environment only a fool would have Virtual Machines running from "local storage" on any box. Generally, in the enterprise, you'll be using VMWAre ESX or Citrix XenServer on servers that are connected to SAN Devices, and that is where your virtuals will reside, preferably on a nice RAID5 or RAID10, with a couple or more spares.

Also the "real" version of ESX and Citrix XenServer will allow you to "live migrate" a virtual from one host server to another with zero downtime. Citrix calls it "XenMotion".

I use it at my work - when we first started testing it (before production) I set up a Windows 2003 server, had it streaming a video to my desktop, and I moved that virtual from one host to another without so much as a glitch in the video - it's pretty awesome.

I think what VMware is aiming at with the "free" ESXi is the SBO with little resources, and light needs - just like it markets VMware Server. The "traditional" VMware-Server is still going to be better for most folks however, since ESX's hardware compatibility list is quite small. Also, ESX runs on a 2.4 Linux kernel (quite old - unless they've recently upgraded to 2.6, I could be wrong there).

You can do something VERY similar to ESX by loading up Ubuntu Server (sans GUI) and installing VMWare server on that box, and connecting to it from another machine with VMWare Server Console.

It's very cost effective when you need several light-duty servers - you can take one nice server w/ 8 cores, and 16GB of ram and load up Vmware or XEN and get 10 light duty servers easily, and get near 100% utilization with (still) good performance...much better than having a server sit 5-10% utilized.

---

### Post by PilotJLR on 2008-08-19
To the OP - the bare metal part is an important component... ESX/ESXi will blow away VMware Server (or any other hosted product).

Note that you'll need access to a Windows machine (or hosted Windows VM) to manage it, as the VI Client is windows only right now. Sure, there is web access too, but it simply does not work as well.

ESXi is free because it is "only" a hypervisor. It's great for virtualization, but the value-add features you buy on top of it are not free.
For example - with the free ESXi, if your physical host fails, you'll get downtime on every VM on the box! With ESXi (free) + HA and VCMS (not free), the VM's restart elsewhere in a cluster. ESXi is just there to get you hooked.  :-)

---

### Post by PilotJLR on 2008-08-19
> **schmick said:**
> 
Remember thoes TVs that came with a VCR and Radio all-in-one?.. break one, loose all.
So.. don't put all the eggs on the same basket.
ESX is a nice idea.. but.. just a nice idea.


Lots of eggs, fewer baskets. Buy HA and VCMS.  :-)

---

### Post by fjgaude on 2008-08-19
Okay, ESXi, you load OSs and then load apps into the OSs... no VMs, really.

I wonder what speed, quickness you give up?

---

### Post by walkerk on 2008-08-19
VMWare ESXi is very nice. You install it on your server (32mb footprint), configure the network interfaces and add it to your LAN. At that point you can remote to its web interface to download the VMWare client.

Now load up the client, enter your ESXi hosts IP address, login, and build your VMs. You can virtualize CPUs, RAM, NICs, etc.

It's actually very cool. I've virtualized 3 servers at work with it. A Ciscoworks LMS Server, Solarwinds Server, and a Syslog/File Server.

---

### Post by fjgaude on 2008-08-19
You load your client? Does the client do the building of the VM?

These clients are OSs, huh?

---

### Post by walkerk on 2008-08-19
> **fjgaude said:**
> You load your client? Does the client do the building of the VM?

These clients are OSs, huh?

The Client is only a version of VMWare that remotes to the ESXi server, not an OS. With the client you remote to, login, and build your VMs on the ESXi Server.

In the past VMWare usually ran as a Windows/Linux client installed on top of an OS. ESX has changed that. Now its a minimal installation (32mb based on Linux) that can host standalone VMs of any OS.

You can download the VMware client on any computer with network access to your ESXi host machine and log in to the Server. At that point you'll see a list of your VMs just like VMWare Server. You can close out the VMWare client and leave the VMs running on the ESXi Server.

I hope that explains it.

---

### Post by walkerk on 2008-08-19
There is a good visual on [this page]("http://vmware.com/products/vi/esx/") that shows how it's setup.

---

### Post by fjgaude on 2008-08-19
Thanks again, walkerk! I'd looked over that page before but not to the extent I just did... VMware is so at there, eh?

---

