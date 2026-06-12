---
title: "Setting up a new Ubuntu Server 12.04 box"
date: 2012-10-01
forum: Server Platforms
---

### Post by crankyoldbugger on 2012-10-01
I'm in the process of setting up a new Ubuntu Server 12.04 box.  I am somewhat of an Ubuntu noob, but I am learning.

I have the basic server installed, and I even got minidlna to talk to my TV over ethernet so I can watch movies.

But now I need expert guidance on a couple of issues.

First off, this Ubuntu server is replacing a Windows Server Hyper-V host, so I want to build some virtual machines on this box (both Ubuntu Desktop machines and a variety of Windows servers and desktops).  The box has 16 gig RAM and tons of HDD so that's not an issue.

What I need advice for is a) is there a decent step-by-step howto build a VM in KVM that encompasses both Windows and Linux guests?  I've looked a quite a number of howto's online and none of them seem complete or consistent (I've found several that say "Ubuntu Server" as the host, but they insist of using a GUI)

Also, this machine has three NIC cards.  What's the best way to automatically assign them to virtual machine guests from within KVM?  Right now they're set up for static IP.

Lastly, I want to access this machine from the internet.  I have a domain name reserved and I'm not above buying an account on dyndns.org if necessary (for static IP, my ISP is cable and does not offer static IPs).  How does one go about throwing this box onto the internet (so I could get to it via [http://machinename.website.com](http://machinename.website.com))  I would probably also like to set up some of the virtual machines in a similar fashion.

Again, I confess that I am a bit of a Linux noob, but I am learning!  I'm actually having a lot of fun building this Ubuntu server and configuring the little details.  I'm becoming more of a Linux fan each day.

---

### Post by hasan.akgoz on 2012-10-02
Hi Crankyoldbugger;
 
Rewiew the site to start with [http://devilsworkshop.org/create-virtual-machineos-ubuntu-1204-kvm/](http://devilsworkshop.org/create-virtual-machineos-ubuntu-1204-kvm/). Write here if you get any errors make the necessary installations. Auto IP configuration required to set up a DHCP environment, but this is not recommended for server operating systems. Static IP is absolutely necessary. if your ISP does not give you a static IP, look at you data center co-location services.Buy a static ip to access internet and redirect these domain names to IP ;) .

---

### Post by hasan.akgoz on 2012-10-02
also I'd be happy to help you ;)

---

### Post by LHammonds on 2012-10-02
From what I have read, if you have a machine that can run VMware ESXi, it would be better to do that unless you need features that the free version does not offer.

I run all my production servers on ESXi (with an Enterprise Plus license for HA clustering) but have looked at various other VM platforms to move to (back when the VMware 5.0 licensing fiasco happened) but did not find anything comparable to the big boy on the block.

---

### Post by crankyoldbugger on 2012-10-02
LHammonds, VMWare would probably be the easiest solution since we use VMWare at work, but to be honest, this box is for me to learn Linux on, so I'm trying to avoid shortcuts.  Good idea, though..

I will have a look at the KVM instructions posted here and have a go at it, hopefully tonight.

Thanks everyone for your help so far.

---

### Post by LHammonds on 2012-10-02
Good luck with your project.  I wish you well.  As for me, I'm about to upgrade from ESXi 4.1 to 5.1 (now that they got rid of the crap-tastic vRAM license model)

If you like to take notes and would like to share your steps for success, you would have an eager audience here. ;)

LHammonds

---

### Post by houstonbofh on 2012-10-02
There are tow different classes of VM systems.  One is bare metal.  A lightweight OS is installed that is just enough to mount and run VMs.  This is VMWare Server, ESXi and Xen.  There are also desktop visualizations. The is VMWare Workstation, Virtual Box, Qemu, Windows Hyper V, and KVM.  However, KVM is kinda a little in the middle of both classes, but it really runs best on a workstation type install.

If you want to run a headless box in your closet, install Xen, ESXi, or VMWare server.  Seriously.  Installing an OS on a headless KVM system is a nightmare.  It is doable, but not easy or intuitive.

If you really want to run KVM, install a desktop, and remove GDM.  This will allow you to boot to a shell, and run "startx" when you need a GUI.  Next, for your guest systems to have real IPs on your lan, you will need to install bridge-utils and set up br0.  When you do, say goodbye to Network Manager and any VPNs you have configured, by the way.  (I am still working on a hack for this, but no love yet.)

If you have not guessed by now, I use KVM, on my primary Linux workstation in a GUI.  I use a GUI tool to manage my VMs as well, Virtual Machine Manager.  Once installed and configured, I can connect to them from other systems in many ways, so you could do this with a temporary GUI.  Also, with the GUI installed, but not active, you can still tunnel X applications over ssh and use the Virtual Machine Manager installed on your server from your Linux desktop over ssh.  (ssh -X [email]me@hidden.box.int[/email])

Once you decide the direction you want to go, we can point you to easy to follow HowTos.

---

### Post by Cheesemill on 2012-10-02
Another option to look at for your VM host is Proxmox, which is basically a Debian+KVM system with a Web UI.

[http://www.proxmox.com/products/proxmox-ve](http://www.proxmox.com/products/proxmox-ve)

---

