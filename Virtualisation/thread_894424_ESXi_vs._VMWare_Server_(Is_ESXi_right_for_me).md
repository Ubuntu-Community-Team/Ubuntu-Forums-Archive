---
title: "ESXi vs. VMWare Server (Is ESXi right for me?)"
date: 2008-08-19
forum: Virtualisation
---

### Post by TheGameAh on 2008-08-19
Hey guys.

A lot of this is just thinking (typing) out loud.  But opinions/feedback are welcome.

In our small network, I needed to consolidate a few servers.  Cost was a factor, whereas the robust features of ESX wasn't a concern.  The solution, just build your own "poor man's" VMWare Server.  Threw together a Debian box, installed VMWare, and let it fly.  Been running fine quite a while now.  It's backed up just by suspending the VMs overnight, tarring and moving, then resuming.

Now, ESXi is a free product.  Hmmm, bare metal virtualization.  Very appealing.  I'll probably download a copy just to test and play with.

However, now I'm seeing a few gotchas.  The addons, of course, cost money.  I read that you need a Windows machine to load a client to manage the server.  Yuck.  Right, I just use SSH/VMWare console, which works beautifully.

A few other things I'll miss too.  ESXi needs server class hardware, where I normally just build my own servers.  Also, having the Debian OS lets me do things like software RAID, where ESXi I'm assuming does not.

So it looks like I'll stay with VMWare server for now.  But did I miss any points above that someone else caught?

---

### Post by HermanAB on 2008-08-19
Don't believe all the marketing blurbs...

VMWare ESXi appears to me to be a modified Redhat Linux.  So in practice, it is probably still best to install your favourite Linux distribution with VMware Server or Workstation on top.

Cheers,

Herman

---

### Post by fjgaude on 2008-08-19
> **HermanAB said:**
> Don't believe all the marketing blurbs...

VMWare ESXi appears to me to be a modified Redhat Linux.  So in practice, it is probably still best to install your favourite Linux distribution with VMware Server or Workstation on top.

Cheers,

Herman

Okay, beginning to understand, appreciate what ESX and ESXi are... sounds reasonable when you think how long VMware has been in business, along with Redhat. <smile>

---

### Post by PilotJLR on 2008-08-19
> **HermanAB said:**
> Don't believe all the marketing blurbs...

VMWare ESXi appears to me to be a modified Redhat Linux.  So in practice, it is probably still best to install your favourite Linux distribution with VMware Server or Workstation on top.

Cheers,

Herman

NO!! This is totally wrong.

ESXi has no service console. It is not linux. It is a bare metal hypervisor and is much faster and more advanced than Server!

You are thinking (probably) of the service console in ESX... well, that's incorrect as well. The SC in ESX in a management domain (like dom0 in Xen) that allows host management features. Its kernel does not run the hypervisor... VMkernel does that.

Be clear on this... ESX and ESXi are not linux!

---

### Post by walkerk on 2008-08-19
double post.

---

### Post by walkerk on 2008-08-19
> **ESX** (20Mb) requires a license but offers more advanced options such as iSCSI.
> **ESXi** (32Mb) is free and gets the job done in most cases.

Once you've loaded ESXi, the only thing you'll configure directly on the ESiX host is the network configuration.

You will use a VMWare client on a separate physical machine to gain remote access to the ESXi server. At this point you can create Virtual Machines on the ESXi server from this or any other standalone physical machine with the client installed and the ESXi host login information.

Example ESX server installations:
```
1. ESXi
2. VM #1 (Server 2003 / DC)
3. VM #2 (Server 2003 / Exchange)
4. VM #3 (Server 2003 / File Print Server)
```

All of the VMs are managed remotely from a standalone physical machine, in my case a laptop.

This is my next project at work.

My last project:
```

1. ESXi
2. VM #1 (Server 2003 / Ciscoworks LMS)
3. VM #2 (Server 2003 / Solarwinds)
4. VM #3 (Server 2003 / Syslog)
```

I'm diggin ESXi :)

Oh and there are hardware requirements. I tried loading it on my work XPS 1710 to test before blowing away a server but it didn't satisfy the hardware requirements. FYI.

---

### Post by PilotJLR on 2008-08-19
Just to clarify... ESX is about 1.2 GB installed and is NOT free. ESX is also what (currently) does include a Service Console. The SC is not the hypervisor... but it is what you see, which mistakenly makes people think ESX=linux.

ESXi comes in 2 forms... ESXi Installable is free and can be installed directly onto a hard disk.
ESXi Embedded is not free and ships embedded into some specific servers and blades.

Good point about the hardware... ESX and ESXi and picky and will not run on some systems. If ESXi doesn't work on your hardware... then you're down to options like VMware Server, Xen, KVM, etc.
Although noticably slower and with fewer features, the nice thing about VMware Server is that it will work, provided you can get Linux or Windows to install on the machine!

---

### Post by gtdaqua on 2008-08-20
When ESXi was made free, I installed on a Dell Server. Definitely, the performance incerases. But, you lose manageability unless you want to buy the expensive virtual centre.

Another dirty thing is you cant manage the ESXi server from  a linux machine. You need .NET Framework 2 to manage it. So it is not os independent. So a lot of drawbacks and lock-ins to pull the customer inside. If you are managing multiple servers, ESXi will be better ONLY with Virtual Centre which is insanely expensive for SMBs.

Not all that good as it seemed when it was made free. I went back to the VMware Server Edition and installed SNMP and Dell's OMSA to monitor individual components.

---

### Post by TheGameAh on 2008-08-20
This is exactly what I've been messing with in my head.  Dying to try ESXi, but I lose some of the Debian additions I like to much.

Like software raid, and SSH, etc.

VMWare server it is, for now  :)

Now I'm trying to think about how much VMWare server can handle.  I've got a server tiny servers (Blackberry, Terminal Server, etc).  But was wondering if a 200+ gigabyte file server is a good idea to virtualize.

---

### Post by gtdaqua on 2008-08-21
> **TheGameAh said:**
> 

...........

..  But was wondering if a 200+ gigabyte file server is a good idea to virtualize.

It is good. At least, I cant say its bad. I have a 250GB VMWare server running rock solid. Size does not matter (atleast for 200G).

---

### Post by kramed on 2008-08-30
Thanks for the discussion (found you from Google). You saved me some time from trying out ESXi when Vmware server would probably be just fine (and has been in the past).

---

### Post by dumarjo on 2008-09-02
What about the Update facility ?

I try to figure if I go with esxi also. I have a Dell bi-xeon that run Vmware server. I have like 6 VM guest running (mostly linux but 1 windows). And the problem is when it's time to upgrade vmware server. I have so hard time to get it run right.

So I would like to know if you have any though about this ?

Dumarjo

---

### Post by sgla1 on 2008-11-15
> **TheGameAh said:**
> This is exactly what I've been messing with in my head.  Dying to try ESXi, but I lose some of the Debian additions I like to much.

Like software raid, and SSH, etc.

VMWare server it is, for now  :)

Now I'm trying to think about how much VMWare server can handle.  I've got a server tiny servers (Blackberry, Terminal Server, etc).  But was wondering if a 200+ gigabyte file server is a good idea to virtualize.

I'm not sure why you would want to virtualize a file server.  The overhead you will incur will probably cancel out the benefit of not powering/managing another physical box.

VMs are good for consolidating lots of underworked physical servers--a local dns server might be a good example here, or dev machines your developers can destroy repeatedly.

File servers are typically i/o bound, so you will want a dedicated server with a fast hardware raid controller and gig ethernet.

That's what we have found here, but we run a pretty busy shop.  Ymmv.

Cheers

---

### Post by Streborekul on 2008-12-09
Thanks for this thread. It put my mind at ease, after just installing a new server for virtual machines.

We too decided to install VMware Server 2.0 on Ubuntu 8.10 64 bit this week (big upgrade of a 6.x ubuntu 32bit server, running vmware server 1.0.5).

We were looking at ESXi (and Microsoft Hyper-V) but ran into some hardware issues (3ware Raid 9550sxu not being supported by ESXi). Hyper-V... I installed it but got pretty confused by the control panel, snapins, etc...

In the end I decided to go Ubuntu 8.10 64 bit. I upgraded the CPU in the machine to an AMD Phenom X4 9750 Quad Core, and also upgraded the RAM to 8GB. I added the 3DM2 Raid monitoring utility for the AMCC/3ware Raid card so all data is safe. We now have a fine VMware server, running test machines and servers on our network. 

Oh yes, our fileserver is a dedicated machine (not a virtual machine), as we want speed.

---

### Post by sgla1 on 2009-01-18
> **HermanAB said:**
> Don't believe all the marketing blurbs...

VMWare ESXi appears to me to be a modified Redhat Linux.  So in practice, it is probably still best to install your favourite Linux distribution with VMware Server or Workstation on top.

Cheers,

Herman

I think you are overlooking the main differences between ESX and VM Server.  ESX offers much better performance because it has less overhead.  It also offers an easy upgrade path to Virtual Center--which is not free, but imho a good value when you compare the cost of additional hardware, power and cooling for more physical boxes, not to mention the cost of my time setting up the new boxes.

ESX does appear to be derived from redhat, but it provides a hypervisor that runs directly on the bare metal.  We were able to run as many as 8-10 busy vms on an HP dl145, which is a low end server.  VMware Server runs as an app on top of a full o/s, so there is considerably more overhead.  Between the o/s and VM server, you'll eat close to a GB of ram, plus ram for the vms.

You do need a windows box for the ESX client.  Oh well.  In every big company I've worked for WinXP is the corporate desktop.  The only reason the Unix admins don't have to use it is because management is afraid of us.  I keep an XP box under my desk and rdp in to run the ESX client, outlook, and whatever else I'm required to run.

Cheers,
Steve G

---

### Post by PilotJLR on 2009-01-19
You're exactly right; thanks for pointing this out! ESX has a red hat service console, but the kernel is not linux at all! ESXi doesn't even have a service console... no linux kernel there at all. That is very often misunderstood. I work with VMware (not FOR them, with them) for a living, and most people that use it don't really understand this point.
Given that (with ESX) the boot process looks and acts like RHEL3, people understandably think ESX is using the linux kernel. This is a really easy mistake to make.

BTW, the VI Client for linux and OS X is coming out sometime in 2009. A Linux appliance based vCenter is as well.

---

### Post by redbrain on 2009-01-24
My opinions is stay away from ESXi!!!!!!

Its really not the way forward using a crap hypervisor! its ok but if you make vm's with all your locked in too much and if you use linux on your desktop you wont be able to manage the server + its even less than ESX its bare metal hypervisor but based of redhat and you have more control esxi is .... VERY basic you dont get any decent features. 

My project lead likes it because he doesn't understand KVM or Xen. But thats where virtulisation is going to take over :)

---

### Post by Dedoimedo on 2009-01-24
Hello,

I'm using ESXi at work, Server at home. Both are good, but serve different purposes. If you have a machine that you can dedicate to ESXi, then sure, by all means ... If you can't, Server will do.

With Server, expect reduced performance, less administration abilities regarding the virtual machine management, like snapshots, cloning, permissions.

For serious work, I'd recommend ESXi.

Cheers,
Dedoimedo

---

### Post by HermanAB on 2009-01-24
I use VMware Workstation, VMware Server and Virtualbox, all to good effect.

ESX is probably good for people who don't know Linux.

The nice thing about Linux is that its scheduler and memory manager are very good.  Anything that is doing nothing, doesn't use resources.  Therefore, on a machine that serves up VMs only, you will find no difference between ESX, Server, Workstation, Virtualbox, Qemu and others in terms of VM performance.

People who claim huge differences in performance do contrived comparisons rigged to prove their point.  If you run a whole load of crap on a Linux system then the VMs will obviously suffer, but if the machine is doing nothing but serve up VMs, then there is no measurable difference between ESX and other decent VM systems.  They all have about 3% overhead.

So, pick the one you like.

Cheers,

Herman

---

### Post by PilotJLR on 2009-01-24
> **redbrain said:**
> My opinions is stay away from ESXi!!!!!!

Its really not the way forward using a crap hypervisor! its ok but if you make vm's with all your locked in too much and if you use linux on your desktop you wont be able to manage the server + its even less than ESX its bare metal hypervisor but based of redhat and you have more control esxi is .... VERY basic you dont get any decent features. 

My project lead likes it because he doesn't understand KVM or Xen. But thats where virtulisation is going to take over :)


Sigh. No, ESX/ESXi is not based on redhat.

The Linux VI Client is coming... yes, it is Win32 only at the moment.

If you WANT service console-like functionality on ESXi, then that's what the RCLI appliance is for.

Do you know about vCenter, DRS, HA, etc? If you don't know of these features, then you really haven't seen what ESX/ESXi is for. This is an enterprise platform. Those features are not free, so that may or may not be relevant to your project manager.
ESXi is meant to be a "get your feet wet" before purchasing VI Enterprise.

---

### Post by PilotJLR on 2009-01-24
> **HermanAB said:**
>  Anything that is doing nothing, doesn't use resources.  Therefore, on a machine that serves up VMs only, you will find no difference between ESX, Server, Workstation, Virtualbox, Qemu and others in terms of VM performance.

People who claim huge differences in performance do contrived comparisons rigged to prove their point.  If you run a whole load of crap on a Linux system then the VMs will obviously suffer, but if the machine is doing nothing but serve up VMs, then there is no measurable difference between ESX and other decent VM systems.  They all have about 3% overhead.


Really? I have to respectfully disagree. It's not hard to show performance gains on bare metal hypervisors (ESX, Xen, etc) verses hosted products (Server, Workstation, VirualBox, etc).

I wouldn't want to run something like a database or a mail server on a product like Server, yet people are doing this (with production workloads) on ESX.

Most of my experience is with ESX, but I've used Xen and VM Server; my test stuff is on Workstation. With little VM's, it doesn't much matter, but once you get closer to production workloads it's a night and day difference. Especially once you get up to 20+ VM's per host, the differences become more significant.

I have actually seen people running production on VM Workstation... once they flip it to ESXi or ESX, guest performance increases and host utilization decreases.

Even doing assessments with vendor agnostic tools, consolidation ratios onto hosted hypervisors are significantly less aggressive than with a bare metal platform.

---

### Post by TheGameAh on 2009-01-28
Nice to see this thread still alive.

I'll provide a little update.

The main purpose of my tiny project was just to consolidate as much hardware as I could.  I had individual servers for BES, RDP, file sharing, etc etc.

I wanted to use ESXi, as it is what is recommended everywhere for production use.  But we needed it to be cheap, (as free as ESXi is, for backup and all the fun stuff, need to spend money).  Also, no SAN available to really push the limits.

So this is what I came up with, which I'm sure others have done.

A linux install (CentOS 64 bit 5.2, 8 gigs ram).  Loaded with VMware server (1.07).  It does happen to also share out files (I've read this is a big no no).  But it's a relatively small file share (200 gigs).  This is done through Samba.  So the only services running on the server are VMs and Samba.  Been running very solid for many months now.

Cron jobs suspend the VMs, tar them, move them elsewhere.  Samba shares get backed up.  I will be setting another server soon (basically a clone), that will just rsync data every so often (tapes are used now as well, but I'm thinking in terms of a MAJOR crash, deal with tapes as less as possible.  Simply use the rsynced clone).

I really wanted to dig in and get ESXi up and running.  But some hardware limitations, as well as my own lack of experience, stopped it all.  Didn't have a dedicated server to run it on.  Plus, how do backups work on ESXi?  Do cron type jobs work?  I know there is an "unofficial" way to get into a service console, but this all just kinda scared me.  Better to stick with what I know, which was Linux and vmware server.

Point of the story, it is a solid setup that has been working reliably.  I have only 3 VM guests, and wouldn't want to add many more.  But this one box now serves samba shares, and 3 Windows 2003 boxes with various things (RRAS, RDP, BES, etc.)

---

### Post by tailwindALWAYS on 2009-02-10
This is a very good thread, and I'm glad it's still alive as well as virtualization is constantly changing.

I work for a University, so our servers may not be as "mission critical" as some businesses.  That being said, we have had very good uptime!  (I really hope this post doesn't jinx this!!!)

We've been using VMware Server 1.0.x for about 1.5 years now.  We have two nearly identical Dell PE2950's with 2xDC 3GHz and 8GB RAM.  The only difference is one has 15K RPM SAS drives and the other 7.2K RPM SATA drives.  So, one with SAS is our primary VM server and light file server, while the other is our main file server and backup VMware server.  These servers are both running Server 2k3 x32 Ent for the host OS.

We are currently running the following VMs
[LIST]
[*]Server 2k3: license server, print server
[*]Server 2k3: multiple sharepoint sites, license server
[*]Server 2k3: run various tools for administration
[*]Debian: ldap master server
[*]Debian: ldap slave server (running on secondary server)
[*]Debian: web server (no PHP or MySQL)
[/LIST]

I was toying with the idea of moving to ESXi as well.  I was close, but I really how we have things setup for backup and recovery.  There's a few things for sure holding me back.
[LIST=1]
[*]Though performance is supposedly better, our systems are running fine and never see any lag.
[*]Once a month when I patch the host OS (patch Tuesdays) I backup all the VMs to the secondary server.  So if our primary server fails, the VMs are already on the secondary server and ready to be fired up.  Obviously, essential data on the VMs are backed up more regularly.  If I did this with with ESXi, in case of hardware failure, I would have to have another ESXi running where I really only need one VMware server.
[*]I like that the host OS is also acting as a file server.  Rather than running file servers in a VM, which I suppose is possible but not recommended, I can run my file server on it's own server, but move VMs over to it if absolutely needed to due to hardware/OS failure.  Why Server 2k3 as host?  Well, they are joined to the domain and the shares are domain shares and it's just easier to have them on Server 2k3 (for me at least).  Plus I am using DFSR in Server 2k3 - which is pretty sweet BTW.
[*]VMware Server also allows expanding drives, which I don't think ESXi does.  Though this is suppose to decrease the performance, I just haven't seen it.  This allows me to give our web server plenty of hard drive space for instance, even though it's only using a few GB of space right now.  This is wonderful for backing up the entire VMs.  I can backup my ENTIRE web server in about 4GB even though the VM sees about 50GB of space!
[/LIST]

Whew ... so, that's where I'm at and why I'm sticking with VMware Server for now rather than ESX/ESXi.  All that being said, the reason I search for this topic (thanks Google) is because I believe VMware Server 1.x.x is hitting end-of-life soon to soonish.  Even though I don't like VMware Server 2 as much, I may need to look at it again ... or other options again such as ESXi and Hyper-V.  Any thoughts or suggestions?  Anyone heard a final date for EOL on VMware Server 1?

---

### Post by sgla1 on 2009-03-21
> **PilotJLR said:**
> Really? I have to respectfully disagree. It's not hard to show performance gains on bare metal hypervisors (ESX, Xen, etc) verses hosted products (Server, Workstation, VirualBox, etc).

I wouldn't want to run something like a database or a mail server on a product like Server, yet people are doing this (with production workloads) on ESX.



I have to respectfully agree with PilotJLR.  There is a big difference between a bare-metal hypervisor and something that runs as an app on top of the o/s.

We are working on deploying some very heavily loaded databases on xenServer, using h/a and shared backend storage.  We should be able to do resource pools and live migration.  This is not an option with vmware server.

Cheers

---

### Post by lewtwo on 2009-03-21
ESXi has one other hidden gotcha that I have not seen mentioned. The VM Disk files are locked. You must manage them via the VM console. If you happen to get a corrupted directory or file then you are screwed. You can not rename, delete, move, copy or anythign else on that file(s) (even with unsupported console interface). The only solution is to reformat the hard disk and start over.

OK ... I will admit this only happened once and I have not bothered to try and reproduce the problem ... once was enought to convince me to avoid the package.

---

### Post by Bailywolf on 2009-03-23
We're building out a dedicated ESXi box right now, and I'm running into issues with networking from my guest OS's.   

Since the machine is still 'in lab' I'm playing with it, and put four VM's on it, and then installed Ibex into the fourth one.  The install went fine, and I was able to download and install all the updates and helper apps I like on a web server (webmin...sweet sweet webmin plus the desktop which I refuse to do without), but the network settings didn't pick up from those provided during the install (the fixed IP, gateway, DNS, etc).  We don't have a DHCP server in our shop (all our IP's are fixed), and so I don't know where it's getting it's config from.  But I was able to connect to the internet immediatly despite the config confusion.  The network tool shows no connection.  I manually input the IP and other info, and then it all stops working.  I have an IP for the ESXi install, and seperate IP's for my VM's.  

I'm liking Vmware so far, but this network thing is annoying as heck.

anyone run into this?

-B

---

### Post by DJMatus23 on 2009-04-16
> **lewtwo said:**
> ESXi has one other hidden gotcha that I have not seen mentioned. The VM Disk files are locked. You must manage them via the VM console. If you happen to get a corrupted directory or file then you are screwed. You can not rename, delete, move, copy or anythign else on that file(s) (even with unsupported console interface). The only solution is to reformat the hard disk and start over.

OK ... I will admit this only happened once and I have not bothered to try and reproduce the problem ... once was enought to convince me to avoid the package.

I've had the front end screw up on me in ESXi and just SSH'd in and fixed it - its not that hard hacking the vmdk files and snapshot files to get things working again.

As for performance, at work we had a whole bunch of test VMs set up on VMWare Server running on Ubuntu Server, and were constantly having problems with one VM going feral and taking all the other VMs out - the only way to resolve it, was work out which VM had gone mad, and kill it...not the easist of tasks, as it was usually a disk i/o issue, not a cpu or ram issue.  I wiped that machine and put ESXi on the same hardware, and migrated all the VMs across about 2 months ago.  So far, performance has been very noticeable, I can have a VM running HeavyLoad (or any disk intensive task) and there is little to no noticeable degradation to the other VMs.

Having said that, I've had the VMware Infrastructure Client freeze up a few times, needing a reboot of the whole server...I keep running the ESXi updates, in the hope that this will resolve things, so it certainly doesn't make me feel confident to roll it out to our infrastructure servers.  Our infrastructure servers are on VMware Server, which, however badly it may perform, under the wrong conditions, has been exceedingly stable - never crashed in the couple of years its been running (and thats VMware server on Win2k3).

Anyway, that's my mileage, yours may differ...

:)

---

### Post by p2d on 2009-05-23
Hi guys! I'm totally new to vmware esxi and server. I've only played with vmware player and fusion before. I have some questions that I hope I can get some answers to:

1. Is it possible to backup your images and snapshots in esxi without buying anything extra? If not, what do I need to purchase?

2. Regarding backups in vmware server I'm reading that you need to suspend your vmware machines before making an backup. Is this true? And how long does the machine have to be suspended (i.e offline?)?

3. I have a 2003 server with terminal services that I would like to convert to a virtual machine. It's used by approx. 10 peoples at the time and they are surfing the web and working with ordinary documents in office via the remote desktop. Would you say that this is enough to see any performance difference between server and esxi?

4. If you install vmware server, why does some people rather prefer the first version instead of the second? And if installing the server in Linux, is there any dist. to prefer regarding performance or easy setup/install?

---

### Post by spectre_25gt on 2009-05-23
Just thought I'd add my two cents in here. I work at a shop that relies heavily on ESX with VirtualCenter for management. Before I got into that position I was a big fan of Xen, but after having spent some time with ESX I'm 100% converted. 

The ease of management alone is enough to consider ESX to be superior to other hypervisors. Networking is abstracted with the idea of virtual switches which are fully 802.1q capable. Each network card in the machine functions as an uplink port to one of these switches. The switches have port groups layered on top of them which can be assigned a vLAN. The host is connected to a trunk port and the port group that the VM connects to decides which vLan it's on.

A general recommended setup is to have 4 NICs in each host machine:

NIC 1 - Management access - Speed mostly not relevent
NIC 2 - Primary production uplink - 1Gig+
NIC 3 - Secondary production uplink - 1Gig+
NIC 4 - VMotion - 1Gig+, the faster the better.

This is obviously dependent on your needs. If you've only got one host, then NIC4 is really not needed. If it's in a lab environment, a single point of failure is not as much of a problem, so you can get rid of NIC 3. If you happen to be using iSCSI without an HBA, then you'll want another NIC (or two) for VMKernel access to your iSCSI SAN.


A few other notes...

The idea that ESX is based on Red Hat, that's a myth that came about because the service console is based on the userspace tools from RHEL 5. There is no Linux kernel.

VMWare Server and ESX are two completely different animals. ESX is a bare-metal hypervisor. There's just enough there to provide virtualization and management of the host. VMWare Server, on the other hand, runs on top of a given host OS. That means you have all of the overhead of that host OS plus the hypervisor.

---

### Post by HDave on 2009-05-24
Great thread...thought I would throw my 2 cents in.  Been a long time user of VMWare Server and Workstation.  I had just built a new high-end virtualization server (8 core AMD, 16GB RAM, 6TB drive) and was expecting to put ESXi on it because it would run my VMware virtual machines and give my maximum performance.

However after finding out:

1) No console support
2) Must login remotely via Windows machine to manage them
3) Max 4 cores per virtual machine
4) flimsy/complicated support for 3ware RAID cards

I decided to look for more alternatives.

Not to complicate this thread more, but I have been testing out KVM for the past couple weeks and it seems like a winner.  Granted the remote management tools (virt-manager) need some improvement (and are improving), but I get near ESXi performance from an open source type #1 hypervisor.  Plus I can manage it from Linux, its in the repos, and if I was really desperate could fire up GDM on the server and look at the VMs directly.

If you are considering ESXi, you should really look at KVM.  Both Redhat and Ubuntu are behind this big time as the future in Virtualization.

---

### Post by spectre_25gt on 2009-05-24
> **HDave said:**
> 
1) No console support


I'm curious as to why this should be an issue. ESX is designed to be managed from the VI client and it's very unlikely that anyone would need more than that.

> 
2) Must login remotely via Windows machine to manage them

This truly is a shame. VMWare has gotten a lot of feedback about this but it doesn't seem as though they're doing anything about it. It's surprising for such a forward thinking company.

> 
3) Max 4 cores per virtual machine

This really deserves to be expanded upon. ESX has a fairly well-known limitation when it comes to CPU scheduling. The host schedules CPU clocks for a guest only when there are enough clocks for all vCPUs in the guest. e.g. If you have a quad core guest, the host machine must have 4 cores available for clocks to be allocated for that guest. It's not recommended to allocate more than 1 vCPU to a guest unless you really know what you're doing.

That said, why would you consolidate a machine that requires more than 4 cores? If you find yourself running into trouble with a limitation like this, you may want to rethink what you're plan was in the first place.

> 
4) flimsy/complicated support for 3ware RAID cards

Unfortunately ESX/ESXi is really geared towards a higher-end market right now. It's expected that people running it are doing so on machines built by one of the larger vendors. HP, IBM, Sun and Dell seem to have the most supported hardware.

---

### Post by salim.madni on 2009-05-24
dear gurus

we buy a new hp small entry level server fresh machine no os inside built in. so i try to install boot from cd, i have 2 images  .iso download from vmware for ESXi, 1 used as binary and 1 used as for hp machine.

but none of them giving response. it boot then it stop working

also it says sata drive does not support. the new server is sata base hdd attached single hdd no raid on this

can some one advise how can i install, since it work or behave like OS...so we just need hardware to install it right? or first we need to install ubuntu or windows then isntall ESXi?

can some one put more highlight the installation,configuration,setup related issues for the FIRST TIME

regards

---

### Post by spectre_25gt on 2009-05-24
Salim, ESXi sits on bare metal. You do not need to install an OS beforehand. It sounds as if your hardware may not be supported. What model server are you trying to run it on?

VMWare has a compatibility guide here:
[http://www.vmware.com/resources/compatibility/search.php](http://www.vmware.com/resources/compatibility/search.php)

---

### Post by zaphod777 on 2009-05-25
Also the esx console management is mostly based on BSD not redhat. The purpose of ESXI is to get you started and later you can upgrade to ESX and virtual center. 

I have 12 esx servers running over 200 VM servers including domain controllers (for development domains Microsoft doesn't support dc's as VM's)
Terminal servers SQL clusters, file servers, Blackberry servers, etc. 

I have it all fiber connected to an EMC cx600 with over 64 TB of disk space. Also I have it connected to an eva 4400 and an eva 8100. 

When our NY office closed I virtualized the whole data center to 4 physical esx servers so that is all we had to move. That makes it well worth the money. 

ESX is expensive but well worth the investment in hardware savings alone. Not to mention the ability to bring up a new server in 15 min or less and fail over an entire esx server to another with no down time. Can you VMOTION with regular vmware server?

---

### Post by PilotJLR on 2009-05-25
> **zaphod777 said:**
> Also the esx console management is mostly based on BSD not redhat. The purpose of ESXI is to get you started and later you can upgrade to ESX and virtual center. 



Just to clarify... it's not BSD at all. ESX 3 uses a CentOS 3 service console, and ESX 4 uses a CentOS 5.2 service console.

I agree ESXi is a great way to start. If you want to add functionality, ESXi can remain in place; just add licensing for VI-Enterprise and a vCenter, and you're in business.

---

### Post by zaphod777 on 2009-05-25
> **PilotJLR said:**
> Just to clarify... it's not BSD at all. ESX 3 uses a CentOS 3 service console, and ESX 4 uses a CentOS 5.2 service console.

I agree ESXi is a great way to start. If you want to add functionality, ESXi can remain in place; just add licensing for VI-Enterprise and a vCenter, and you're in business.

Maybe BSD was some of the older versions. I know they lock it down in a similar fashion can't ssh using root etc. 

I can't wait until the come out with a VI (Virtual Infrastructure) Client for Linux. I know that will make a lot of people happy. Doesn't really mater to me anymore though I had to switch back to XP on my work machine.

---

### Post by tester321 on 2009-12-02
This is a very informative thread!  Thank you all for the great info.

---

### Post by NixHR on 2010-01-13
> **tester321 said:**
> This is a very informative thread!  Thank you all for the great info.

Yep, lots of good info on this topic.

---

### Post by TRaymond on 2010-01-20
What about storage?

I currently have 4 Large Dell Servers running VMWare 2.x.  All 4 servers are running windows (sorry we're a MS Shop here) and are in a cluster.  The only real cluster resource is a EMC SAN.  The idea behind this is that each VM has a slice of the SAN.  With the SAN Clustered like this, I can easily move one lun from Machine to machine and bring up the VM on any of the 4 boxes in the event that a host server goes down.

How would this work (or would it) with ESXi?  Is ESXi SAN aware?  Assuming a Lun on the san can only be granted to any one machine, how would you move lun's from machine to machine without Windows Clustering?

Thanks in advance!

TRaymond

---

### Post by PilotJLR on 2010-01-20
> **TRaymond said:**
> What about storage?

I currently have 4 Large Dell Servers running VMWare 2.x.  All 4 servers are running windows (sorry we're a MS Shop here) and are in a cluster.  The only real cluster resource is a EMC SAN.  The idea behind this is that each VM has a slice of the SAN.  With the SAN Clustered like this, I can easily move one lun from Machine to machine and bring up the VM on any of the 4 boxes in the event that a host server goes down.

How would this work (or would it) with ESXi?  Is ESXi SAN aware?  Assuming a Lun on the san can only be granted to any one machine, how would you move lun's from machine to machine without Windows Clustering?

Thanks in advance!

TRaymond


Hi there. Can you elaborate on what exactly you mean by "clustering" in this setup? This is most certainly not VMware clustering.

I'd frankly run, not walk, away from Server 2.X. ESXi is vastly more efficient. Running Windows Server below Server introduces significant performance hits. Saying "we're a windows shop" in this context has little meaning, to be blunt. My employer has 1200 windows servers and you can bet we don't use it to host a hypervisor!

ESXi support FC and iSCSI and NFS presented disk. So if you are presenting LUNs via FC or iSCSI on your Clariion (making a guess about your EMC platform here), then you could present a few LUNs to each ESXi host, at which point ESXi would nuke the LUN and format it to vmfs3. Keep in mind NTFS is not a cluster filesystem, which is why I asked my initial question there.

Since vmfs3 supports concurrent read/write on multiple hosts, you would have multiple VM's on each LUN. Failure of an ESXi host would not require any action on the Clariion. You'd just re-register a VM in a new host and start it.

Of course, if you implement vSphere and vCenter (neither are free), then this action would be fully automatic.

---

### Post by peterlorimer on 2010-06-23
Hi

I used ESX 3.5 for a long time then upgraded to ESXi V4 and wow no Web interface and no way of copying ISOs or backing up VMs off site. However after Googling for a while I found out you can type the word 'unsupported' on the main ESX screen. This opens up an Ash shell, or Busybox which allowed me to go in and activate the ssh server, it is already there but disabled. Of course doing this means I get no support whatsoever from VMWARE but hey, I was never one for calling support anyway, all i need is IRC.

Next up I could set up the Vswitches e.t.c old style using the shell but what I did was this.

Downloaded the 30 day trial of VMware Workstation for linux, created an XP PRO VM, then played it in the free vmplayer, used the XP VM to download Vsphere Client and used it to connect to ESX. After my 30 day trial I was  forced to buy it for $900 which I was not happy about but it is a reasonably good app. 

However I got a second server and realized my licence was for 2 servers 2 processors and 6 cores. My first server had 2 quad cores so my licence was invalid.

Now I've put Ubuntu on the second server and Vmware Workstation. I'm going to create all my VMs in advance and play them on VMplayer before my licence expires. Either that or pay $180 for a workstation licence.

I've noticed no performance issues  in fact workstation/server is better because if i run out of space I simply add a USB drive and mount it. That is not possible with ESXi

I'm happy with that

---

### Post by PilotJLR on 2010-06-23
What did you buy for $900? The vSphere Client is free. ESXi is free as well.

---

### Post by peterlorimer on 2010-06-24
VSphere Client. It was free but disabled itself after 60 days. Then you have to buy a licence from Vmware. That was 2 months ago.
Here is the Vmware page 

[https://www.vmware.com/tryvmware/index.php?p=vsphere&lp=1](https://www.vmware.com/tryvmware/index.php?p=vsphere&lp=1)

---

### Post by PilotJLR on 2010-06-24
> **peterlorimer said:**
> VSphere Client. It was free but disabled itself after 60 days. Then you have to buy a licence from Vmware. That was 2 months ago.
Here is the Vmware page 

[https://www.vmware.com/tryvmware/index.php?p=vsphere&lp=1](https://www.vmware.com/tryvmware/index.php?p=vsphere&lp=1)


No, that's not true. I sell and design VMware at my job. You probably bought a couple sockets of vSphere, which would including licensing for additional features and a vCenter Agent.

vSphere Client itself is free. With standalone ESXi hosts (no vMotion, no DRS, no HA, no vCenter), your total cost would be zero.

---

### Post by PilotJLR on 2010-06-24
Just to clarify - what likely expired was ESXi. You need to provide that with a license, but they give you free serial numbers for that.
If you've deployed vCenter, then you would need a non-free license after 60 days every time. vCenter is not required for standalone hosts with none of the vSphere feature set.

---

### Post by asv on 2010-09-28
Any word on a Vpshere Linux client yet? It seems like people have been waiting years for it..

---

### Post by zaphod777 on 2010-09-28
> **asv said:**
> Any word on a Vpshere Linux client yet? It seems like people have been waiting years for it..

Not as far as  I know I think from what I understand the problem is it was written in .net and would need a complete re-write  to work in Linux. Or something like that. You might be able to get it to work in Wine but I have never tried. 

At work I had to use a Windows machine anyway to use all of the Active Directory Management tools.

---

### Post by qhash on 2010-10-13
Hi guys,

I am new to the forum as I found that thread researching on a configuration I have to create so maybe it is a good time to say hello :)

Moving to the point - as the thread title states - is the ESXi right for me?

My company is going to install a new server and I have to virtualize it to have several machines running on 1 HW:

VM #1 DC
VM #2 Exchange
VM #3 Fileserver (small shares, very few people using it <10)
VM #4 Webserver
VM #5 Dev/tests

The virtualization technology must be free. I came to the point where I wanted to install a VMServer on a debian, but then two problems arised - performance (server will be 1 CPU, Xeon4c,12GB ram) and my very little knowledge in linux. That's why I thought about ESXi, but as I have no experience in virtualization except I used VMWorkstation and I had some contact with WMServer, will it create a lot of problems to me? If I can't backup the whole machine on the fly, without stopping it, can I just backup the data from within the guest OS to an external storage using ESXi? And how do I actually manage VMs using ESXi (working on the free option of ESXi)?

---

### Post by zaphod777 on 2010-10-13
> **qhash said:**
> Hi guys,

I am new to the forum as I found that thread researching on a configuration I have to create so maybe it is a good time to say hello :)

Moving to the point - as the thread title states - is the ESXi right for me?

My company is going to install a new server and I have to virtualize it to have several machines running on 1 HW:

VM #1 DC
VM #2 Exchange
VM #3 Fileserver (small shares, very few people using it <10)
VM #4 Webserver
VM #5 Dev/tests

The virtualization technology must be free. I came to the point where I wanted to install a VMServer on a debian, but then two problems arised - performance (server will be 1 CPU, Xeon4c,12GB ram) and my very little knowledge in linux. That's why I thought about ESXi, but as I have no experience in virtualization except I used VMWorkstation and I had some contact with WMServer, will it create a lot of problems to me? If I can't backup the whole machine on the fly, without stopping it, can I just backup the data from within the guest OS to an external storage using ESXi? And how do I actually manage VMs using ESXi (working on the free option of ESXi)?

ESXi is probably the easiest but if you have no experience on virtualization you are setting yourself up for a world of hurt. Look into a product called Vmware Converter it is useful for creating the VM's.

Otherwise you can probably use clonezilla to backup  the machines and restore them in vmware. 

Vmware converter can backup server while they are running but it is better to do it when they are shutdown. Also I believe MS doesn't recommend DC's or Exchange as a VM.

If you feel like you are in over your head if you buy ESX then you can get support from VMware they have great support.

MS Server 2008 also has Hyper-V built in for virtualization so that may be easier too since you know MS stuff.

---

### Post by qhash on 2010-10-14
Thanks a lot for your comment. Do you know why Exchange is not recommended for VMs? I have seen many people doing that. Is it a performance issue? My server will not be heavily loaded, I think until the end of2011 there will not be more than 20 ppl using it, and I think it will be rather 15. Same goes for DC, but actually it may happen there won't be a domain used at all.

Then, maybe Virtualization is not needed for me at all, I just wanted to seperate web server from our more "internal" use servers, and DC/Exchange 2007+ need to be installed on two machines, can not work together. 

Moreover, now the virtualization is actually not a must for us, but I would like to be ready, because it may be a need in 2011/2012.

---

### Post by zaphod777 on 2010-10-14
> **qhash said:**
> Thanks a lot for your comment. Do you know why Exchange is not recommended for VMs? I have seen many people doing that. Is it a performance issue? My server will not be heavily loaded, I think until the end of2011 there will not be more than 20 ppl using it, and I think it will be rather 15. Same goes for DC, but actually it may happen there won't be a domain used at all.

Then, maybe Virtualization is not needed for me at all, I just wanted to seperate web server from our more "internal" use servers, and DC/Exchange 2007+ need to be installed on two machines, can not work together. 

Moreover, now the virtualization is actually not a must for us, but I would like to be ready, because it may be a need in 2011/2012.

If it has a pretty light load it is probably fine I have seen Exchange and DC's run in VM's fine Microsoft just doesn't recommend it.

Also FYI Exchange 2007 will use 100% of the ram you allocate it so don't freak out when you see it. It is by design. 

I would also recommend you have at least two domain controllers. Even if they are virtual.

---

### Post by bhaverkamp on 2010-10-15
Windows physical box is not required. Can be VM running on same ESX host. This is my setup. Also you can pass through the storage controllers to your linux VM and run software raid there and export via iscsi the storage back to ESX for use as datastores for VMs. You could use openfiler or other opensource NAS programs for managing this. The environment is much more flexible than you might think.

---

### Post by qhash on 2010-12-01
Diggin up.

I am back to the virtualization , but now more in educational manner. It might go a little bit off-topic from the thread root, but I have gathered a lot of good info here before, so I hope someone can help me on that.

I have Primergy TX100S2 server. At the Fujitsu webpage it is stated that supported OSes are: W2003,W2008,Hyper-V2008,RedHatEnterprise linux and SUSE. 

I would like to create a virtual environment on which I can set up some VMs among which I need one W2008R2 server. The whole thing does not have any direct goal now, but I need to get familiar with virtual environment and maybe later move some VMs to the new virtual host. I also want to check whether i.e. FreeBSD or ubuntu will run with no problems on that hardware as a VM.

Can you suggest some configuration for that? If the supported OS/hypervisor is said to be HyperV only, or can I use ESXi or VMWare? Someone tried that? Maybe there is some good manual?  

And one more thing - if I create a virtualized environment, let us say using ESXi, how the hardware is seen by the hosted OS? Will the hosted OS recognize hardwarde same as I it would have been installed on the pure hardware?

If my post is really OT, i will move it somewhere suitable.

---

### Post by bhaverkamp on 2010-12-01
Once you go virtual you can run pretty much any OS you want as a guest. The details of the host hardware are camouflaged by the virtualization layer. The guest sees really vanilla disk and network controllers. The only issue is whether your host is supported by ESXi. Since you can try it for free it should be easy to find this out. I would recommend the flash stick approach as this will not effect any OSs you currently have installed and will let you quickly check if your hardware is supported.

---

### Post by zaphod777 on 2010-12-01
> **qhash said:**
> Diggin up.

I am back to the virtualization , but now more in educational manner. It might go a little bit off-topic from the thread root, but I have gathered a lot of good info here before, so I hope someone can help me on that.

I have Primergy TX100S2 server. At the Fujitsu webpage it is stated that supported OSes are: W2003,W2008,Hyper-V2008,RedHatEnterprise linux and SUSE. 

I would like to create a virtual environment on which I can set up some VMs among which I need one W2008R2 server. The whole thing does not have any direct goal now, but I need to get familiar with virtual environment and maybe later move some VMs to the new virtual host. I also want to check whether i.e. FreeBSD or ubuntu will run with no problems on that hardware as a VM.

Can you suggest some configuration for that? If the supported OS/hypervisor is said to be HyperV only, or can I use ESXi or VMWare? Someone tried that? Maybe there is some good manual?  

And one more thing - if I create a virtualized environment, let us say using ESXi, how the hardware is seen by the hosted OS? Will the hosted OS recognize hardwarde same as I it would have been installed on the pure hardware?

If my post is really OT, i will move it somewhere suitable.

Ubuntu and freeBSD should run fine as they are mainstream OS's. The VM's will see generic hardware since it is abstracted from the server hardware. The only time this would really be an issue is if you need direct hardware access to something like a com port from the VM. I think it may be possible now but it used to be a problem.

---

### Post by qhash on 2010-12-02
Thanks for your fast replies guys.
I will try ESXi then.

update:
actually I may try XEN/KVM on RH Enerprise linux as well , I am right? What do you think about that? Maybe it is not Ubuntu, but still its linux ;). Would it be easier/harder for a linux noob like me when compared to ESXi?

---

### Post by PilotJLR on 2010-12-05
> **qhash said:**
> Thanks for your fast replies guys.
I will try ESXi then.

update:
actually I may try XEN/KVM on RH Enerprise linux as well , I am right? What do you think about that? Maybe it is not Ubuntu, but still its linux ;). Would it be easier/harder for a linux noob like me when compared to ESXi?


I would also encourage you to try RHEL and KVM, though I would avoid Xen. Xen is not even available in RHEL6... KVM is the newer hypervisor of choice (for most).

KVM and libvirt on RHEL is pretty straightforward, though it would require you to learn a small amount of Linux (as opposed to ESXi, which would obviously require learning ESXi itself).

---

### Post by xiotech on 2010-12-11
Amazing Thread! Now for the really stupid questions: I want to setup a test platform and get my feet wet with all of this.  

1. So let me make sure I've got this right... ESXi is free and not bare metal so it requires a host, so thats where the Ubuntu Server 10.10 can come in... as the host OS running on the physical box?

2. The Ubuntu is to be installed first and given ALL the available physical resources of the box... nothing is to be held in reserve for ESXi or for future VM's... ESXi will allocate the available resources?

3. ESXi can be installed directly on top of the Ubuntu (as a package?) and then I can create VM's?

4. Can I come back after the fact and install/uprgade new host hardware (ram, disks, nics,) and will it be aggregated outward into ESXi and made available to reconfigure/allot expanded resources on a VM by VM basis if necessary?

5. So heavy I/O items Primary FS, DC, Exchange, SQL, Sharepoint, etc... are they best left out of the VM mix and would you just use your own better judgement say for example, if you've got an Accounting Dept SQL2000 Server thats hammered day and night it's probably not a good VM candidate?

Thanks, awesome discussion
Tim

---

### Post by zaphod777 on 2010-12-11
> **xiotech said:**
> Amazing Thread! Now for the really stupid questions: I want to setup a test platform and get my feet wet with all of this.  

1. So let me make sure I've got this right... ESXi is free and not bare metal so it requires a host, so thats where the Ubuntu Server 10.10 can come in... as the host OS running on the physical box?

2. The Ubuntu is to be installed first and given ALL the available physical resources of the box... nothing is to be held in reserve for ESXi or for future VM's... ESXi will allocate the available resources?

3. ESXi can be installed directly on top of the Ubuntu (as a package?) and then I can create VM's?

4. Can I come back after the fact and install/uprgade new host hardware (ram, disks, nics,) and will it be aggregated outward into ESXi and made available to reconfigure/allot expanded resources on a VM by VM basis if necessary?

5. So heavy I/O items Primary FS, DC, Exchange, SQL, Sharepoint, etc... are they best left out of the VM mix and would you just use your own better judgement say for example, if you've got an Accounting Dept SQL2000 Server thats hammered day and night it's probably not a good VM candidate?

Thanks, awesome discussion
Tim

ESXi is it's own OS that runs on the bare metal there is no need to install a separate OS. Systems that have very heavy IO are not good candidates unless you have a separate raid group dedicated to it. otherwise you can slow down the whole server but you just need to really test to see what works best for you. 

as far as hardware goes you can install more nics and ram as needed. I would recommend about 3 NIC'S, one for management and then you can team the other two just make sure they are on the compatibility list. I think most Intel cards should be fine. Any compatible RAM can be added latter.  

You can also attach ISCSI storage for more disk space.

---

### Post by xiotech on 2010-12-11
> **zaphod777 said:**
> ESXi is it's own OS that runs on the bare metal there is no need to install a separate OS. Systems that have very heavy IO are not good candidates unless you have a separate raid group dedicated to it. otherwise you can slow down the whole server but you just need to really test to see what works best for you. 

as far as hardware goes you can install more nics and ram as needed. I would recommend about 3 NIC'S, one for management and then you can team the other two just make sure they are on the compatibility list. I think most Intel cards should be fine. Any compatible RAM can be added latter.  

You can also attach ISCSI storage for more disk space.

Thanks for replying, is there an Open Source alternative (Suite) like VMware vSphere out yet, or do you ever see that happening?

Are any of the Open Source Products previously mentioned in this thread: KVM, Xen, Virtualbox comparable or better to what one could get with ESXi as far as performance and manageability go?

Thanks
Tim

---

### Post by qhash on 2011-01-10
i was wondering - is it possible to migrate VMs from VMWare to ESXi? The problem is that the system I have right now does not have ESXi support ( Fujitsu TX100S2 ) but has RH Enteprise Linux on which I can run VMWare server. After some time, will I be able to move my VMs from one host environment to another, if I will change VMServer to ESXi?

update:
I am having problems with installing RHEL 5.4 onto RAID matrix as well. Maybe you guys can suggest a solution what would be the best option in my situation - 4 hdd drives 500GB SATA 7200, Intel PCH 3420 software RAID and a requirement to install virtual environment as reliable as possible on config given above.

I thought on buying a 2GB good quality USB flashdrive or IDE-to-CompactFlash + CF card an installing ESXi on it and then using 2 drives for VM and 2 other drives as a backup storage for VMs. Will it work for a small company with a very limited budget?

---

### Post by pcapademic on 2011-03-15
> **qhash said:**
> i was wondering - is it possible to migrate VMs from VMWare to ESXi? 

It is possible to migrate a vm from vmware-server-2 to ESXi. The easiest way is to use the VMware Converter application.

The hard way is to copy files to ESXi, convert the vmdk with vmkfstools, and then edit the .vmx file.

Basic usage for vmkfstools:

```
vmkfstools -i <path-to-disk-file.vmdk> -d thin  <path-to-disk-file-**esxi**.vmdk>
```

---

### Post by pcapademic on 2011-03-15
Does anyone have any benchmark / performance data to show that ESXi performs better that vmware-server?

I did a test, and in my test they performed the same.

---

### Post by bhaverkamp on 2011-03-15
What kind of test did you do? For a single VM running on an otherwise idle system you would expect CPU related benchmarks to be about the same. IO related benchmarks could vary quite a bit. With server the host OS can do some file caching for the quest which could speed things up. With ESXi performance would be expected to be better because of a more direct path to the storage devices. ESXi does not do any file caching on behalf of the VMs.

---

### Post by pcapademic on 2011-03-16
The test I performed involved hitting a webapp running on a single vm, with that vm being the only vm running on the system.

I will try some new tests that are more IO intensive.

---

### Post by den_ on 2011-12-09
Hello,

I am playing a little with ESXi 5. It runs on my server at ovh. Server has two IPs, one of them is for failover.

I have installed 4 Ubuntus, actually Turnkey appliances, what is again Ubuntu 10.04 : ), but I have no idea how to configure networking...

I was using VirtualBox and VMWare Server before, and had no problems with bridged network configuration. But I was doing it at home, where I have my router wich provides IPs via dhcp.

If I am correct, I need to configure a virtual router by my self, to manage my virtual network, do port forwardig or NAT etc. But I have no idea how/what to set as default gw, and how to configure the ESXi.

I tried to asign a failover ip to the guest as described here:
[http://help.ovh.co.uk/BridgeClient]("http://help.ovh.co.uk/BridgeClient")
but that didn't work.

I have contacted technical support via email a couple of minutes ago, but then I found this thread. Does ayone here has an idea what could I eventualy try to solve this, or what is the proper way to enable guest to access the internet on the hosted root server with ESXi 5 on it and with one IP address and one NIC?

Thanks and regards


denis

---

### Post by dcstar on 2011-12-10
> **den_ said:**
> 
..........
I have contacted technical support via email a couple of minutes ago, but then I found this thread. Does ayone here has an idea what could I eventualy try to solve this, or what is the proper way to enable guest to access the internet on the hosted root server with ESXi 5 on it and with one IP address and one NIC?


The ESXI box had an IP (for maintenance) and is usually on your network.

Any VM you install that connects to that LAN device is just the same as anything else connected to your network.

There is nothing complicated in this except for people who try to make it complicated.

---

### Post by den_ on 2011-12-10
> **dcstar said:**
> The ESXI box had an IP (for maintenance) and is usually on your network.

Any VM you install that connects to that LAN device is just the same as anything else connected to your network.



Yes that's why I need NAT or something what ESXi doesn't provide. The machine with private IPs can see and ping each other, since all are connected to the same swicth. What I am not succeeding is to ping host and access the internet with them. I have followed the instructios from the link above to implement bridge with failover IP, but that didn't work.

I find that instruction are little strange. The failover IP and host one are not on the same network, so it is not clear to me how could Guest use host IP's gw with his IP from another network to route the traffic...? And that is what they suggest. If I understood the instructions well...

Btw. I mentioned that I am renting the server at OVH. The machine has the IP for maintance. Without it I couldn't be able to connect to it, and I would have no Guests... When you say my network, you mean network of my guests?

> There is nothing complicated in this except for people who try to make it complicated.

:) One of the best comments I saw in my life. Not everyone is smart,with profound IT knowledge like yours, as you are.

---

### Post by dcstar on 2011-12-23
> **den_ said:**
> Yes that's why I need NAT or something what ESXi doesn't provide. The machine with private IPs can see and ping each other, since all are connected to the same swicth. What I am not succeeding is to ping host and access the internet with them. I have followed the instructios from the link above to implement bridge with failover IP, but that didn't work.
..........

ESXi does not do routing. ESXi does not do NAT. ESXi provides a Bridged network connection to your VMs (just like if you plug a physical machine into an Ethernet switch). If you want these functions then they need to be done by something separate.

---

### Post by zaphod777 on 2011-12-23
> **den_ said:**
> Yes that's why I need NAT or something what ESXi doesn't provide. The machine with private IPs can see and ping each other, since all are connected to the same swicth. What I am not succeeding is to ping host and access the internet with them. I have followed the instructios from the link above to implement bridge with failover IP, but that didn't work.

I find that instruction are little strange. The failover IP and host one are not on the same network, so it is not clear to me how could Guest use host IP's gw with his IP from another network to route the traffic...? And that is what they suggest. If I understood the instructions well...

Btw. I mentioned that I am renting the server at OVH. The machine has the IP for maintance. Without it I couldn't be able to connect to it, and I would have no Guests... When you say my network, you mean network of my guests?



:) One of the best comments I saw in my life. Not everyone is smart,with profound IT knowledge like yours, as you are.

look into PFsence it is a virtual firewall and they even have vm image you can use.Then just assign your public ip to one interface and set it up like you would a home router.

---

### Post by den_ on 2011-12-23
Thanks for your feedback. I have forgot to reply here.

I solved the issue with discarding Turnkeylinux, and switching to Ubuntu LTS. It seems they messed something in networking with their customisations. I remember was getting 'failed to open directory /etc/resolvconf/update-libc.d: No such file or directory' warning after restart of the the networking service.

The bridge instructions from the link I posted above (here again: [http://help.ovh.co.uk/BridgeClient]("http://help.ovh.co.uk/BridgeClient")) work well with Ubuntu 10.04. I have tried CentOS 6.1 too, and it works also.

Thanks for your time and replies.

Regards

denis

---

