---
title: "Help me design a server"
date: 2011-01-11
forum: Server Platforms
---

### Post by abandonedthe_mulletator on 2011-01-11
Hi,  I need to set up a server for my company.  

There are only 4 people working here and we want a server that will allow us to run a cloud-like system.  We want to be able to log in and use programs and have our files available from within the office and at home.  I've used Citrix in the past and would like something similar, but free/open source if possible.

I want an Ubuntu based server that gives the user a windows compatible environment.  What I mean is it needs to be able to run windows software.

What kind of hardware do I need?  We want to run fairly resource hungry software like GIS and mapping software.

I want to run Ubuntu server but what other software will I need?

---

### Post by arrrghhh on 2011-01-11
It sounds like you're describing something like LTSP (the Citrix comment cue'd me into that) but I don't think that's what you need (perhaps I'm misunderstanding ;)).

It sounds like the best option would just be a server setup to share with the PCs via samba - that way each PC will run its own programs, and use its own resources - but files will be saved 'in the cloud' - really just on your server, not technically the cloud!

Now for accessing these files from home - how do you access the computers on your LAN from home currently?  Do you use a VPN or...?

I'm sure we can find something that will fit your needs, but keep in mind there are limitations with every system - especially when integrating between systems.

---

### Post by abandonedthe_mulletator on 2011-01-11
Hi, LTSP looks like it might work.  But I don't think its quite what I have in mind.

At the moment we have a remote ftp server that is used for remote access of files.  We have to put the files on the ftp first though.  We also have an off the shelf remote hard drive.  I want to replace these methods completely.

What we need is a centralized server that we can log in using a username and password and get a virtual desktop (I think that's the right term).  I want to be able to log into the server from home or from work with the same programs and files on the desktop.  I don't want to just access the files from home, I want to get the same virtual desktop at home or at work.  The virtual desktop has to be able to run on a windows or linux box.  Also it has to be user friendly for the end user because some of my co-workers are not all that savvy.

I came accross [NoMachine]("http://www.nomachine.com/") on google.  Anyone ever use this?

---

### Post by arrrghhh on 2011-01-11
I've used NoMachine, but not as LTSP, only as SSH/GUI remote access.

Not sure that's really what you're looking for either - unless you have a rig beefy enough to run VMs for all your users - then each user would have a VM to remote into.  Interesting idea, but again - you'd need a pretty beefy server!

---

### Post by abandonedthe_mulletator on 2011-01-11
It turns out Citrix has a free version of their XenServer.  This is just about exactly what I want for software.  It will run its own linux OS and allow me to create virtual desktops for each user.  Here is an old guide on how to do it, [http://www.howtoforge.com/virtualization-with-xenserver-express-5.0.0](http://www.howtoforge.com/virtualization-with-xenserver-express-5.0.0).

I'm going to give it a shot.  The next version up is $1000 from Citrix if the free one doesn't work.  If there is a open-source free alternative I am all ears.

Now I need to figure out the hardware.  Citrix lists the specs for what is needed but I'm a little unsure on what to buy.  I've never bought a server before.  Please advise me on what to buy.  Should I get a blade type server with multiple blades or just one powerhouse machine?  I need to run the server OS, multiple virtual desktops and some resource hungry programs. 
	

Here's the required specs:
XenServer host
 
 	64-bit x86 server-class system	 
 	
CPU: 1.5 GHz minimum, 2 GHz or faster multi-core recommended
Intel® VT or AMD-V™ required for support of Windows guests
1GB to 256GB physical memory
Up to 64 logical processors
100Mb/s or faster NIC
Up to 16 physical NICs
Local or Fibre Channel boot disk with 16 GB of space minimum, 60 GB or more recommended

---

### Post by abandonedthe_mulletator on 2011-01-27
I picked up a sweet server at an auction.  Its a rack of 4 Sunfire X4100 Servers.  

Here's the specs:
4 x machines have a Dual Core Opteron 2.8 GHz 2220SE Processor
All processors are AMD Northbridge Architecture-three 8.0 gb/sec. 
One MB Level 2 cache per core
All machines have 4.0GB DDR2-667 Memory
All machines have Dual(2) 146GB 10,000 RPM Hard Drives-Hot swappable,2.5" SAS internal 
discs,RAID 0,1 onboard
Four 10/100/1000Base-T Ethernet Ports

[Here's a photo of the Server]("http://www.bcauction.ca/Pictures/6205518_Main.jpg")


This is the first time that I will set up a server of this kind.  I am going to go with Citrix XenServer Express as the OS and virtual desktop server.

Should I cluster the blades into one virtual server?  If so, what kind of cluster?  Should I install XenServer on each individual blade and run them independently?  Any other advice?

Thanks

---

### Post by gordintoronto on 2011-01-27
If people run a "remote desktop" type of setup from home, they might find screen refreshes are pretty slow. Does everybody have high-speed Internet?

Does the GIS software require Windows? If so, the Ubuntu forums probably won't help you a lot.

---

### Post by tgalati4 on 2011-01-27
Citrix purchased Xen, but they still maintain open source development of Xen.  So depending on your needs [http://xen.org](http://xen.org) may be all you need.  You will certainly pay for virtualized Windows apps run through a Citrix server.

You even have room in that rack for an espresso machine.  Just mount the servers up high so you can put the espresso machine under the blades.  Put some plastic sheeting over the UPS and you will be all set.

As far a ganging the blades together, that depends on your workload and how much tinkering you need to do.  I would certainly keep a blade free for tinkering with newer frameworks (xen, lamp, drupal, etc) before putting into production.  If reliability is important, then you might create some failover capability.

---

### Post by abandonedthe_mulletator on 2011-01-27
Thanks tgalati4,

Yeah its a big cabinet.  We got that sucker for $2200 though.  I think its a great idea to cluster 3 of the 4 blades and leave one for screwing around.  Can you give me some info on setting up the cluster.

Thank for the Xen link.  I'll give that a shot, I'm downloading the live cd right now.  The Xen website says it can "support a wide range of guest operating systems including Windows".

---

### Post by abandonedthe_mulletator on 2011-01-28
Here's what I want to do , at least what I think I want to do:

Cluster the blades
Install Xen with an Ubuntu base OS
Set up virtual windows desktops that users can log into

How does that sound?  Can anyone give me some guidance, this is new to me.

---

### Post by tgalati4 on 2011-01-28
Installing Xen as Dom0 (host) using Ubuntu will require some work on your part, including recompiling the kernel.  Ubuntu has decided to support KVM and thus updates will be compatible with KVM.  Using Xen will probably require recompiles every time the server kernel is updated--which is a lot over the life of a server.  You can postpone updates with a slight risk in security, but you will always have to weight the agony units of recompiling versus the improvements gained with updates.  Also updates may break Xen because Ubuntu is not actively supporting it, but I bet KVM will continue to work throughout the upgrade cycle.

Some Ubuntu notes for installing Xen:

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

This is an old article (2006) that gives the basic concept of clustering.  You will have to modify to work with Xen 4.0.1 and Ubuntu.

[http://www.clustermonkey.net//content/view/139/33/](http://www.clustermonkey.net//content/view/139/33/)

I like Xen and I like Ubuntu.  It's a shame that Ubuntu is not actively supporting Xen.  Perhaps that will change in the future.  KVM may work as well for your needs, but I don't think it has the flexibility that Xen has, nor the performance.  But that is for another thread.

I'm building some Xen hosts for some of my small business clients and I am agonizing over this same issue.

---

### Post by abandonedthe_mulletator on 2011-01-30
Will Eucalyptus work for me?  It seems easy to set up the cluster and virtual desktops using Ubuntu and Eucalyptus.  It can use Xen or KVM and can run Windows guest desktops.

---

### Post by spynappels on 2011-02-01
You could also look at VMware ESXi as a bare metal hypervisor, but you will still need to create a Virtual Windows Server or Desktop to give you a Remote Windows Desktop.

---

### Post by ChasHutch on 2011-02-01
I was also thinking of VMWare as I like the idea of a bare metal hyper-visor. Seems like it would be quickest to set up and there is lots of support on line.

You may also need to consider additional drive space (or attach a SAN to the kit).  Currently you have just over 1TB of space if you cluster the machines and the drives. There are many ways to do this. You will likely also need to consider space for backups, etc.

You never mentioned your time-frame. How soon does this need to be done?

Just my two cents.

Hutch

---

### Post by abandonedthe_mulletator on 2011-02-01
Is it easy to set up a cluster using VMware ESXi?  I'm totally new to clusters and virtualization.

I've been reading about Eucalyptus/XEN and it does the cluster almost automatically.  I don't mind doing some work to get it going though.

The important thing is that I have a linux base serving linux and windows guest desktops.  I'm starting to read about VMware ESXi right now.

Time frame?  Pretty soon, I haven't set it up yet.  We hooked up the physical server and it seems to run fine.  The cluster/cloud/virtual desktops or whatever you call it is next.

---

### Post by abandonedthe_mulletator on 2011-02-18
I am currently experimenting with two different systems.  On 2/4 blades I have a Ubuntu Enterprise Cloud (UEC) and on the other 2 blades I have two VMware ESXi servers.  At the moment neither one is doing what I want.

The UEC cluster works fine but I am having trouble accessing the instances.  I have several running instances which I can not ping or SSH.  The community has not been much help.

VMware seems to work fine but I haven't figured out how to cluster the two servers. There are lots of guides online on how to do this but they are for an older version, I'm using the current version 4.1.

Once I get this dialed in I'll put all 4 blades on the best system.

---

