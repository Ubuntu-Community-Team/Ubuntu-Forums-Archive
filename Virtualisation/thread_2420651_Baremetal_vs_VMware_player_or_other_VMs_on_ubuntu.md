---
title: "Baremetal vs VMware player or other VMs on ubuntu"
date: 2019-06-08
forum: Virtualisation
---

### Post by webmiester on 2019-06-08
Hi everyone,

I am in a conversation with someone who gave a very interesting recommendation.

Instead of having a single server run DHCP, DNS, File server, etc...  We can make VMs for each one and have them operate in their own VMs.  He mentions that with VM's it would be easy to make virtual images of the systems which we can easily replicate with on any machine.  Stuff like device drivers and all can be virtualized so that even if we change the computer later on with different specs from the previous computer, the virtual machine will still make the images feel at home as the devices are virtualized and we can replicate the old setup of the old VM.

When I asked him where to start, he told me to do baremetal VM I think using VMware.  I was looking for opensource or free alternatives to this though...

Here are my questions:

1) How much of a difference will the Baremetal VM make vs. a VM running ontop of Ubuntu?  I read somewhere that the hypervisor technology where the baremetal VMs operate on is basically its own OS.  So with the right setup, wont  ubuntu as a host OS do almost as well?  Like maybe it wont be as fast but the difference wont be that significant.

2) I read that there was a red hat KVM somewhere.  Is there an ubuntu KVM?

3) Ive been reading on "top 5 Baremetal Virtual Machines" and all...  These articles are nice to read, but I am still kind of confused on where to start.  When I visit the Linux KVM page for instance, I dont even see a download link :(  I would very much prefer a recommendation and an explanation as to why they chose this particular recommendation, rather than read articles that makes all the VMs sound good and worthwhile.  Afterall, I will probably just choose 1 in the end.  I would like to request your opinion on this please.  Thank you so much, I know you are all busy, and I appreciate the time that you give in this.

---

### Post by TheFu on 2019-06-08
Didn't we have this same conversation last year about how virtualization decouples the VM from the real hardware and makes all sorts of migrations and DR planning easier?

The "baremetal" crowd are from 2005-ish.  Computers are 50x faster today.  5G disks to hold an OS are trivial today.  The limited hardware supported by "baremetel" VM hosts make them undesireable, inflexible.  Plus, most would not support F/LOSS tools for doing normal things, like backups.  That always bothered me about VMware ESX and ESXi - all the backup tools were $1000 and didn't do versioned backups, just full, image-style backups.

KVM is a kernel module to Linux.  It isn't a distro. It is only available on systems with 64-bit CPUs that have on-CPU support for virtualization.  Basically, very fast context switching (but it is 1000x more complex than that).

When you install Ubuntu Server, you can tell it you want a VM host server.  CentOS and RHEL do the same, but you can add KVM to any 64-bit install that has a capable CPU.

**Forget the "baremetal" hype.**  It is just that.  KVM is still the fastest full hypervisor available.  You might select a different hostOS for many reasons.  I've used pretty much all of the hypervisors that run on Linux. KVM is my choice for many reasons - but the main reason is stability and performance and cost.

I've used 6 of the VMware hypervisors over the years. Ran ESX and ESXi for years at client locations. Ran ESXi at home for a few years too. Never again. 
I've used Xen for 2+ yrs. Had stability issues when the host kernel was modified, guests would refuse to boot. Never again.
I've used the toys - virtualbox and VMware Workstation, player, server .... these are great for home users doing desktop on desktop virtualization where downtime doesn't matter.  If I worked in a manual testing team with manual point-n-click testing needed, then I'd absolutely use VMware Workstation. If I need a VM to run more than 8 hrs a day, nope.
Virtualbox is too slow to be used for servers, even after tuning the VMs and hostOS for performance. Plus, I was never thrilled with Oracle's license.

If you are running more than 25 physical servers with 250+ VMs, then we can talk about different solutions. They will still be based on KVM, but management, setup, migrations, storage and networking are vastly different.

---

### Post by webmiester on 2019-06-08
Thank you TheFu,

So basically what you are telling me is that KVM is the most stable.  Do I just run a command to install this from the command line?

Yeah, I was thinking on the same line about the baremetal thing.  I couldnt even figure out which hardware supports it.  Also, I what I plan to virtualize probably aren't heavy on resources - such as
1) DHCP
2) LDAP and DNS

I am also considering virtualizing the file server (NAS)

so I was thinking of just doing the Ubuntu server approach and have a virtual machine on top of ubuntu.

---

### Post by webmiester on 2019-06-08
I found this one.  I suppose it should do:

[https://www.cyberciti.biz/faq/installing-kvm-on-ubuntu-16-04-lts-server/](https://www.cyberciti.biz/faq/installing-kvm-on-ubuntu-16-04-lts-server/)

---

### Post by webmiester on 2019-06-08
Well there is another thing that caught my attention with my conversation with this guy.

I shared with him our problem with our old still in use enterprise system.  It runs on an old OS which is no longer supported. Both its OS and the software application we are using have been abandoned by the original developers.  Its running on an old computer which might die on us anytime.  And we cant replicate it because its OS is very particular about device drivers and all.  So if we were to replicate it on another computer with different specs, it would surely fail.  This is like getting the hard disk of my windows computer and installing it on a different computer.  On bootup, it will get so many errors because the drivers the windows was set up to are don't match the machine's equipment.

Now what my consultant told me was that we can just get a new computer and then virtualize the old hardware there.  We can replicate the equipment and use the drivers from VMware to simulate the same setup as the old computer.  So in this case, if we duplicate the hard disk, we can transfer it to the virtualized machine, and it should work fine.

It sounds like an idea that might work to help save legacy systems such as ours.

---

### Post by TheFu on 2019-06-08
> **webmiester said:**
> Thank you TheFu,

So basically what you are telling me is that KVM is the most stable.  Do I just run a command to install this from the command line?

Yeah, I was thinking on the same line about the baremetal thing.  I couldnt even figure out which hardware supports it.  Also, I what I plan to virtualize probably aren't heavy on resources - such as
1) DHCP
2) LDAP and DNS

I am also considering virtualizing the file server (NAS)

so I was thinking of just doing the Ubuntu server approach and have a virtual machine on top of ubuntu.

A $35 Pi can handle most DHCP, LDAP and DNS needs.  If these are all internally facing, I'd put them on the same VM.  It isn't worth setting up 3 VMs just to run each of these services, unless you have thousands of clients/users.  Too much overhead maintaining systems just for those 3 things.  For 150 clients, pretty much any hardware or a 1 vCPU VM can handle it.

There are a few types of systems that I wouldn't virtualize.
* DBMS
* NAS
* WAN routers ... LAN routers can be virtualized.
It basically comes down to either security considerations or having as much I/O available as possible.

BTW, I've been doing virtualization since the late 1990s on pretty much all platforms, except Windows as the host. This is server virtualization. For desktops, I did them in the late 90s and again around 2008 on.

As for moving old physical systems inside VMs, that is a great idea, but only if the hardware can also be virtualized. Not all hardware can and it sounds like the specific hardware you have is different.  OTOH, if you are just worried about storage or ethernet networking stuff, it isn't an issue. Those virtualize easily - actually, using virtual drivers instead of virtual-versions of physical card drivers is much better.

With a physical Linux setup, just move everything into a VM and see how it works in a lab. There will be little issues, but those can usually be handled one by one.

Nothing is guaranteed. Try it in a VM. See if it works.  The only risk is time.

---

### Post by TheFu on 2019-06-08
I'm not there.  Seems you've hired a VMware consultant, not a Virtualization Consultant.  Every solution leads to new hardware with a fresh VMware ESXi install, vSphere licenses, and $xxK in backup licenses ... no doubt.

My company and our clients were screwed by VMware, so I have an anti-VMware stance. [https://www.infoworld.com/article/2622945/vmware-listens-to-customers--changes-vsphere-5-licensing-again.html](https://www.infoworld.com/article/2622945/vmware-listens-to-customers--changes-vsphere-5-licensing-again.html)
Everyone using VMware had a firedrill for 2-3 months as the different pricing was going to make it impossible for them to afford it. It wasn't in their budgets.  Companies expect a 15% increase every few years, if they aren't under maintenance.
They've done it before. They can do it again.   Beware.

If you intend to run mainly Linux systems in the VMs, don't touch VMware.

I've said my peace.  Good luck.

---

### Post by webmiester on 2019-06-11
> **TheFu said:**
> I'm not there.  Seems you've hired a VMware consultant, not a Virtualization Consultant.  Every solution leads to new hardware with a fresh VMware ESXi install, vSphere licenses, and $xxK in backup licenses ... no doubt.

My company and our clients were screwed by VMware, so I have an anti-VMware stance. [https://www.infoworld.com/article/2622945/vmware-listens-to-customers--changes-vsphere-5-licensing-again.html](https://www.infoworld.com/article/2622945/vmware-listens-to-customers--changes-vsphere-5-licensing-again.html)
Everyone using VMware had a firedrill for 2-3 months as the different pricing was going to make it impossible for them to afford it. It wasn't in their budgets.  Companies expect a 15% increase every few years, if they aren't under maintenance.
They've done it before. They can do it again.   Beware.

If you intend to run mainly Linux systems in the VMs, don't touch VMware.

I've said my peace.  Good luck.

Oh TheFu,

You are so right.  We have 2 buildings here.  So building 1 is under me.  Building 2 decided to hire this consultant...  They are now crying over the costs.  I think what he does is he virtualizes the DHCP, the File Server, and the DNS servers into separate Windows server instances.  So imagine the costs...  VMware + 3 Windows Servers + CALs.  Man this guy isnt thinking about economics at all.

I want to do mostly linux since I dont see any real advantages with Windows for any of those.  I am only considering windows for the file server for its active directory vs Linux' LDAP, but Im concerned about CAL licences that it is per user.

You guys are really doing great!  Thank you so much.

---

### Post by webmiester on 2019-06-11
> **TheFu said:**
> A $35 Pi can handle most DHCP, LDAP and DNS needs.  If these are all internally facing, I'd put them on the same VM.  It isn't worth setting up 3 VMs just to run each of these services, unless you have thousands of clients/users.  Too much overhead maintaining systems just for those 3 things.  For 150 clients, pretty much any hardware or a 1 vCPU VM can handle it.

There are a few types of systems that I wouldn't virtualize.
* DBMS
* NAS
* WAN routers ... LAN routers can be virtualized.
It basically comes down to either security considerations or having as much I/O available as possible.

BTW, I've been doing virtualization since the late 1990s on pretty much all platforms, except Windows as the host. This is server virtualization. For desktops, I did them in the late 90s and again around 2008 on.

As for moving old physical systems inside VMs, that is a great idea, but only if the hardware can also be virtualized. Not all hardware can and it sounds like the specific hardware you have is different.  OTOH, if you are just worried about storage or ethernet networking stuff, it isn't an issue. Those virtualize easily - actually, using virtual drivers instead of virtual-versions of physical card drivers is much better.

With a physical Linux setup, just move everything into a VM and see how it works in a lab. There will be little issues, but those can usually be handled one by one.

Nothing is guaranteed. Try it in a VM. See if it works.  The only risk is time.

I actually want to do the RPi approach for the DHCP and the possible the DNS.  I compared it to a PC on paper though and I find that around 4 RPis will cost more or less 1 PC here.  So if I get a PC and split it into 4 VMs, it might more or less cost like the RPI without so many power cables and with the possibility of using more types of OS's.  But yeah, I really love RPIs...  

One idea I have is to put 4 or more RPi's into a server type chassis and then mount them into my server rack.  They will look clean, and their cabling wont be bothered so much.  As for the NAS, there have been people who adviced me against using the RPi due to its slow 100MBPs NIC.  But it is something in my dreams...

So its RPis vs VMs.  So hopefully, with inputs from what I get from you guys here, I can decide on this matter soon.

---

### Post by kevdog on 2019-06-12
You guys seem to have a lot more experience with VM's than me.  Interesting take.

I'm currently using xcp-ng which is the freeware version of Citrix Xen and on it I've virtualized pfSense and a couple of Ubuntu and Arch installs.  xcp-ng isn't a "bare-metal" hypervisor since it runs on top of CentOS. I'm not sure how this setup would scale in a large organization however for home use it seems to work quite well.
In terms of baremetal I've tried proxmox (which is Debian running the KVM modules) as you've described.  Since I'm rather new to the use of hypervisors, one of the things I like about running xcp-ng/proxmox is they come built with managment software running within a gui.  It's fairly easy for me to see what's up and running with the gui. Ubuntu with KVM installed -- I dont think you get these GUI features and the process is much more command line driven -- which is a little more difficult to manage and troubleshoot --- I'm sure its like everything -- if you've done it a lot use of the command line is easy -- learning curve is steep however.

---

### Post by TheFu on 2019-06-12
Don't use a r-pi inside a business for non-IoT work.  SD storage for an OS must be avoided. Failure is the only option.

At home, a r-pi (or something similar AND a little faster), can be used for things like DNS/DHCP and even backup servers if you get a SBC with SATA or USB3 and a GigE interface that is really GigE and doesn't share a single USB2 bus for all peripherals. Odroid-N2, RockPro-64 ($65) are examples.  There's a cheap Intel-Atom SBC now for $40 too. Each needs a PSU and case, but the performance, I/O, networking make it worthwhile.  If you already have a VM server at home, I'd virtualize everything except the WAN router/firewall.  A single $200 Ryzen 1600 build can easily handle 20 VMs with 16GB or RAM.

kevdog - **virt-manager** - remotely manage any VM through the ssh connection. GUI is like virtualbox/VMware Player, but with access to more advanced stuff.  
I ran xen for a few years. KVM is better, IMHO.  Amazon has been switching to KVM the last few years, BTW. [https://medium.com/@dbclin/aws-just-announced-a-move-from-xen-towards-kvm-so-what-is-kvm-2091f123991](https://medium.com/@dbclin/aws-just-announced-a-move-from-xen-towards-kvm-so-what-is-kvm-2091f123991)

---

