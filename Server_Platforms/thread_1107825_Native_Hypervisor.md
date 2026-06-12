---
title: "Native Hypervisor"
date: 2009-03-27
forum: Server Platforms
---

### Post by blazemore on 2009-03-27
I'm looking at running two or three servers in virtual machines off of one server box.
What base should I use to directly interface with the hardware? I heard these are called Native (or bare-metal) hypervisors.

I know I could just use Ubuntu but it seems like overkill.

---

### Post by windependence on 2009-03-27
It IS overkill. I use the free ESXi from VMware. It's picky about hardware but just try it. Mainly, you have to look at the disk controller. Fortunately, there are SATA controllers that work for about $15 US. I don't have the chipset name right here but I'll dig it up and post it for you. I'm sure you can get them in the UK. If not, I am a reseller and I ship overseas. Shipping isn't too bad to you.

ESXi has only a 32MB footprint, and uses very little resources. You'll want to make sure you have a good amount of RAM though. Also, you don't need to allocate as much RAM to each VM as you would if they were on a physical box because they share some resources.

If you need help, feel free to PM me.

-Tim

---

### Post by blazemore on 2009-03-29
I'd feel more at home using a Linux distro. Maybe TinyCore?

---

### Post by doogy2004 on 2009-03-29
I use a bare Ubuntu Server installation with VMware Server on top of that.  For personal use it has worked great for me.

---

### Post by blazemore on 2009-03-30
Did you put a GUI on that?
I'm not sure I'm up to managing VMs from the command-line

---

### Post by blazemore on 2009-03-30
Okay I've decided I'm going to install Crunchbang Lite onto the actual hardware, and then use Virtualbox to load the different servers.

I'd like to SSH into them, however. Could someone please advise me here: [http://ubuntuforums.org/showthread.php?p=6981109#post6981109](http://ubuntuforums.org/showthread.php?p=6981109#post6981109)
??? Thank you

---

### Post by windependence on 2009-03-30
I'm confused. You said you wanted a bare metal hypervisor. Installing virtualization on top of an OS is exactly the opposite. It works OK, but you are basically wasting resources.

-Tim

---

### Post by blazemore on 2009-03-30
Well I'm not really a pro at virtualisation.
I just meant I want a very light, stable base on which to install Virtualbox.

---

### Post by windependence on 2009-03-30
OK, much clearer :)

You should try a bare metal hypervisor when you get a chance. There is a huge performance difference and it takes almost no disk space, plus you don't have to worry about the host OS because there is none.

If you need help, just ask, I'm a VMware partner, and I have attended extensive training and use the product every day.

-Tim

---

### Post by blazemore on 2009-03-30
Okay so I am interested in this, as I want to run a fair few VMs.
What would you recommend (preferably open source, but definately free of charge)

---

### Post by Cheesemill on 2009-03-30
On my VM machines at work I run  a minimal 8.04 server installation with only VMware Server 2.0 installed.

I know that ESXi would give better performance but our hardware isn't compatible.

Don't worry about having to use the command line because VMware Server is managed using a web front-end, even running on a CLI server.

Cheesemill

---

### Post by bwitherell on 2009-07-04
> **windependence said:**
> OK, much clearer :)

You should try a bare metal hypervisor when you get a chance. There is a huge performance difference and it takes almost no disk space, plus you don't have to worry about the host OS because there is none.

If you need help, just ask, I'm a VMware partner, and I have attended extensive training and use the product every day.

-Tim

You are right about the disk space and about ESXi being picky about the hardware it runs on. However, when you install ESXi you are actually installing an OS. So there is an OS to worry about. You have to make sure that it is updated and properly maintained like any other OS. ESXi is actually VMware's own Linux distro. I think it's based off a RedHat kernel (not sure about the distro it is based off of though, But it is a Linux distro). Also upgrading to the next major release (not minor) eg. going from say ESXi 3.0 to 3.5 release can be a bit of a pain because there can be a risk of losing privileges to access the VMs to start, stop or manage them.

All that said, I too would recommend ESXi for its small footprint, ease of VM maintenance, robustness, scalability and the fact that it is an industry proven solution. The fact is that there isn't another solution out there at this time that comes close to matching all the capabilities of ESXi especially when it is used with other tools from VMware.

---

### Post by windependence on 2009-07-05
> **bwitherell said:**
> You are right about the disk space and about ESXi being picky about the hardware it runs on. However, when you install ESXi you are actually installing an OS. So there is an OS to worry about. You have to make sure that it is updated and properly maintained like any other OS. ESXi is actually VMware's own Linux distro. I think it's based off a RedHat kernel (not sure about the distro it is based off of though, But it is a Linux distro). Also upgrading to the next major release (not minor) eg. going from say ESXi 3.0 to 3.5 release can be a bit of a pain because there can be a risk of losing privileges to access the VMs to start, stop or manage them.

All that said, I too would recommend ESXi for its small footprint, ease of VM maintenance, robustness, scalability and the fact that it is an industry proven solution. The fact is that there isn't another solution out there at this time that comes close to matching all the capabilities of ESXi especially when it is used with other tools from VMware.

Well technically, you're correct as ESXi is based on RHEL version 3 I believe, however "based on" is where it ends. The kernel is a heavily modified version of the RH kernel, and is almost unrecognizeable as a Linux kernel other than a few commands through the RCLI. With that said, you could argue that ANY bare metal solution is an OS. Let's not split hairs here, OK? I run *BSD on most of my machines and I would have trouble getting a kernel as small as the ESXi hypervisor. You are also correct that like any software, it must be maintained and upgraded at some point.

The point of my post was that ESXi is considerably more efficient than running a VM solution on top of a full OS, and it seems you may agree on that. ESXi IMHO looks like it meets all of the OP's requirements. :-)

-Tim

---

### Post by juancarlospaco on 2009-07-05
VMWare ESXi its a Linux so its not more *"bare metal"* that any linux kernel can do.

Ubuntu Minimal+SSH+KVM and here you get your bare metal hypervisor running on any kind of hardware.

if you explicitly need something more small footprint compile oyour own kernel, 
and then install SSH+KVM.

You can control everything from the GUI, Convirt 1.1 centralized managment console.

---

### Post by PilotJLR on 2009-07-05
> **juancarlospaco said:**
> VMWare ESXi its a Linux so its not more *"bare metal"* that any linux kernel can do.

Ubuntu Minimal+SSH+KVM and here you get your bare metal hypervisor running on any kind of hardware.

if you explicitly need something more small footprint compile oyour own kernel, 
and then install SSH+KVM.

You can control everything from the GUI, Convirt 1.1 centralized managment console.


Wrong. This whole "ESX is just RHEL" nonsense comes up **much** too often.

ESX is NOT Linux. ESXi is NOT Linux.

The confusion stems from the fact that ESX (NOT ESXi) uses a CentOS 3 Service Console. The Service Console is a management virtual machine. The Linux kernel does NOT touch bare metal... the VMkernel does, which is the VMware "special sauce".


[http://www-01.ibm.com/redbooks/community/display/REDP4480/VMware](http://www-01.ibm.com/redbooks/community/display/REDP4480/VMware)

---

### Post by namaku0 on 2009-07-05
Ah, you save my time for explaining. Like you said,
this whole ESX == Linux/RHEL really comes up much
too often.

> **windependence said:**
> Well technically, you're correct as ESXi is based on RHEL version 3 I believe, however "based on" is where it ends. The kernel is a heavily modified version of the RH kernel, and is almost unrecognizeable as a Linux kernel other than a few commands through the RCLI. With that said, you could argue that ANY bare metal solution is an OS. Let's not split hairs here, OK? I run *BSD on most of my machines and I would have trouble getting a kernel as small as the ESXi hypervisor. You are also correct that like any software, it must be maintained and upgraded at some point.

The point of my post was that ESXi is considerably more efficient than running a VM solution on top of a full OS, and it seems you may agree on that. ESXi IMHO looks like it meets all of the OP's requirements. :-)

-Tim
No, you couldn't argue that any bare-metal solution
is an OS. Xen and Hyper-V are bare-metal solution but
has a really different architecture compared to ESX.
Xen or Hyper-V is useless without special VM (called
domain-0 in Xen and Root Partition in Hyper-V).

---

### Post by juancarlospaco on 2009-07-05
ESXi its a modified Linux, i see it,
sometimes when ESXi crashes you see Linux*-like* things on CLI.

---

### Post by melgish on 2009-07-05
> **juancarlospaco said:**
> sometimes when ESXi crashes

You just about talked me out of trying it :)

But I am curious.  How easy is it to move vm's on/off an ESXi based box?  

I currently run a 9.04 server w/ VMware server 2, FTP, and OpenVPN for hosting my development VM's .. But I sometimes have to go on the road, taking a VM or three with me...

Other than an annoying boot up issue w/ my USB drive, 9.04's been rock solid and hasn't crashed once...let alone "sometimes"

---

### Post by PilotJLR on 2009-07-05
> **juancarlospaco said:**
> ESXi its a modified Linux, i see it,
sometimes when ESXi crashes you see Linux*-like* things on CLI.

Nope. What you see is BusyBox:
[http://www.busybox.net/about.html](http://www.busybox.net/about.html)

BusyBox is a GPL application, yes... it does not run only on Linux. It runs on many platform, of which the VMkernel (ESXi) is one.

---

### Post by PilotJLR on 2009-07-05
> **melgish said:**
> You just about talked me out of trying it :)

But I am curious.  How easy is it to move vm's on/off an ESXi based box?  

I currently run a 9.04 server w/ VMware server 2, FTP, and OpenVPN for hosting my development VM's .. But I sometimes have to go on the road, taking a VM or three with me...

Other than an annoying boot up issue w/ my USB drive, 9.04's been rock solid and hasn't crashed once...let alone "sometimes"

Moving VM's around, even on the free stuff, is easy. However, I wouldn't recommend using ESXi if you plan on moving to and from Workstation on a laptop, though. In that case, you'd have to pass the VM in and out of vConverter each time, which would be slow and (at least to me) irritating.

Once the VM is on ESX/ESXi, the expectation is that it will remain on the enterprise platform.

---

### Post by juancarlospaco on 2009-07-05
*I see Linux-like things on Bootloader crashed too...*
:)

---

### Post by windependence on 2009-07-06
> **namaku0 said:**
> Ah, you save my time for explaining. Like you said,
this whole ESX == Linux/RHEL really comes up much
too often.


No, you couldn't argue that any bare-metal solution
is an OS. Xen and Hyper-V are bare-metal solution but
has a really different architecture compared to ESX.
Xen or Hyper-V is useless without special VM (called
domain-0 in Xen and Root Partition in Hyper-V).

Please understand I totally agree with you and PilotJLR. The difference between ESXi and VMware Server is like night and day. Same with the difference between other virtualization products and ESXi or ESX. Most people on this forum see no difference because they either are not aware of the archutecture difference or they have only been using VM products on top of a full OS. There IS a huge difference. While I have one production VM machine running for about three years on VMware Server v1.06, I do not deploy any more like that. All of my production VMs are on either ESXi or ESX. 

As for the OS argument, I was trying to go a little easy on these guys and not start a flame war, but in my mind you are very correct, a bare metal hypervisor is an abstraction layer, NOT an OS.

Thanks for supporting my position on this, I really didn't want to write yet another novel ;)

-Tim

---

### Post by windependence on 2009-07-06
> **juancarlospaco said:**
> *I see Linux-like things on Bootloader crashed too...*
:)

You can see all you want, but the fact is, a bare metal hypervisor is by order of magnitude more efficient, faster, and more stable than the setup most recommended here in the forums. 

-Tim

*VMware Partner*

---

### Post by melgish on 2009-07-06
> **PilotJLR said:**
> Moving VM's around, even on the free stuff, is easy. However, I wouldn't recommend using ESXi if you plan on moving to and from Workstation on a laptop, though. In that case, you'd have to pass the VM in and out of vConverter each time, which would be slow and (at least to me) irritating.

Once the VM is on ESX/ESXi, the expectation is that it will remain on the enterprise platform.

It's sounding like ESXi isn't for me then. More so when I'd need to add a VM to handle my FTP / OpenVPN services.

---

### Post by windependence on 2009-07-06
I don't understand, once you have your server set up and your VM added, you modify it where it is, however, you control it from your laptop remotely, even to the point of loading a new OS via your laptop CDROM! You don't ever have to touch the actual machine once the hypervisor is loaded. How are you planning to use it?

-Tim

---

### Post by juancarlospaco on 2009-07-06
*I dont see VMWare more efficiently than a compiled kernel...*
:)

---

### Post by melgish on 2009-07-07
> **windependence said:**
> I don't understand, once you have your server set up and your VM added, you modify it where it is, however, you control it from your laptop remotely, even to the point of loading a new OS via your laptop CDROM! You don't ever have to touch the actual machine once the hypervisor is loaded. How are you planning to use it?

-Tim

Mostly, I use VM's for development/testing.  I'm a professional services developer, and create custom integration modules to fit between our company's products and the great unknown.  When on-site I've found it's been extremely useful to drag along the environment I created to match that customer's. (specific versions, existing custom bits, etc.) I can't leave them at home because there's no 100% guarantee I'll have connectivity when I get where I'm going.

Here at home however, I run them all on a VMware server based box because it's nice not having them eating laptop memory, and my Gigabit LAN is up to the task.  I was looking at ESXi for the potential performance gains.  But as I've learned, any gains would be later negated by the additional time/trouble to transfer machines on/off the ESXi system.  So it's not for me.

---

### Post by jalyst on 2009-08-08
how do latest versions of Xen packages, & KVM + Virt manager compare to ESXi? I know KVM is a fair bir bigger than (90-odd mb)
but that's irreleanvet if it offers more compatibility, flexibility, & performance for the VM running on top.

---

### Post by windependence on 2009-08-08
Size isn't the problem. You're going to find out that you need specific processors for some of the VM software you mentioned. Xen you still can't install a guest OS from CD without considerable trouble, I guess they think everyone has images everywhere. 

If you just want to run VMs on your laptop, you'd be better off with VMware workstation although it's not free. ESXi is not intended for running on your desktop, it's for production deployment, and it's fantastic at what it does. I have done hundreds of installs for clients and I have yet to have ESXi crash. 

You can also run it from a CF card with an IDE adapter for a really thin install. 

I ran through all these choices before I settled on VMware for my clients. The biggest plus for me was the amount of guest OSs supported. I need support for FreeBSD, and some of the others don't support that or some other OS choices I may run. Of course, YMMV.

-Tim

---

### Post by scorp123 on 2009-08-08
> **blazemore said:**
> I'd feel more at home using a Linux distro. Maybe TinyCore? Why not use ProxMox VE? It's based on Debian, but it's basically a free VMware ESX clone ... sort of (I mean functionality-wise).

[http://www.howtoforge.com/kvm-and-openvz-virtualization-and-cloud-computing-with-proxmox-ve](http://www.howtoforge.com/kvm-and-openvz-virtualization-and-cloud-computing-with-proxmox-ve)

Download URL:
[http://pve.proxmox.com/wiki/Downloads](http://pve.proxmox.com/wiki/Downloads)

"ProxMox VE" can do full virtualisation via KVM (requires a 64-bit CPU with hardware virtualisation support) and so called para-virtualisation via OpenVZ (great for running Linux on Linux). Getting ProxMox clustered is easy too (just follow the tutorial above).

---

### Post by Vegan on 2009-08-08
I see comments all day about virtualization. Seems to be blown all out of proportion.

Only place as a web operator that virtualization seems useful is for SSL sites as Apache2 cannot vhost SSL yet.

Anything else is overkill. My old IBM can do all kinds of things and while its old as the hills it still works.

Database, check
web gizmo, check
file server, check
print server, check

authentication, available, not needed in my shop yet

As I said 1000 time before, stop spinning your wheels.

Its not the machine, its what you do with it that counts.

---

### Post by windependence on 2009-08-09
Obviously you don't do this professionally. Virtualization IS the future, especially in web hosting and development. 

As to your second point, you are confusing virtual hosting with virtualizing hardware. I think you might want to do a little more reading, and there are ways around the SSL thing you are talking about.

You seem rather uninformed about this.

-Tim

---

### Post by scorp123 on 2009-08-09
> **Vegan said:**
>  Only place as a web operator that virtualization seems useful is for SSL sites as Apache2 cannot vhost SSL yet. You seem to be confusing several things here. I'm with the previous poster "windependence": No insult intended, but you are in need of more reading. Sorry to say so.

---

### Post by juancarlospaco on 2009-08-09
> **juancarlospaco said:**
> *i dont see vmware more efficiently than a compiled kernel...*
:)

:p

---

### Post by Vegan on 2009-08-09
> **scorp123 said:**
> You seem to be confusing several things here. I'm with the previous poster "windependence": No insult intended, but you are in need of more reading. Sorry to say so.

The problem is I have is the stupid ports are all over the map with layer after layer of crud.

The standard port for SSL is 443 but with a vanilla Apache2 its fine. But I have to graunch it to make it use the vhosts with SSL.

As for virtualization, that was a big pitch a few years ago over at IBM selling a machine that could support 1000 instances of Linux for applications.

My old IBM runs Ubuntu on a so-called bare machine. I see no reason for virtualization, all I see is more overhead on a machine.

I perfer reentrant code and threads.

---

### Post by scorp123 on 2009-08-10
> **Vegan said:**
>  As for virtualization, that was a big pitch a few years ago over at IBM selling a machine that could support 1000 instances of Linux for applications. Well, then this is going to be a rude awakening for you: Virtualisation still is a big pitch. And at other vendors too. Not just IBM.

> **Vegan said:**
>  My old IBM runs Ubuntu on a so-called bare machine. I see no reason for virtualization, all I see is more overhead on a machine. Buy a few Sun Fire X4600M2 with 256 GB RAM and 32 CPU cores each and have customers that demand funny things such as "99.99% uptime" (= roughly 1 hour max. downtime per year!) . Then we talk again, OK? 

BTW: It would be nice if you would refrain from kidnapping this thread. The thread clearly is about virtualisation solutions such as VMware ESX, ESXi, ProxMox VE, XEN Server, and such things ... and not about running "vhosts" or anything else on Apache, OK?

Regards.

---

### Post by samosamo on 2009-08-10
> **scorp123 said:**
> Well, then this is going to be a rude awakening for you: Virtualisation still is a big pitch. And at other vendors too. Not just IBM.

 Buy a few Sun Fire X4600M2 with 256 GB RAM and 32 CPU cores each and have customers that demand funny things such as "99.99% uptime" (= roughly 1 hour max. downtime per year!) . Then we talk again, OK? 

BTW: It would be nice if you would refrain from kidnapping this thread. The thread clearly is about virtualisation solutions such as VMware ESX, ESXi, ProxMox VE, XEN Server, and such things ... and not about running "vhosts" or anything else on Apache, OK?

Regards.

<snip>

Anyway, back to the topic...

For my custom built machine at home I use VMWare Server 2.0 for about six months now.  The host is Hardy and so are the 8 guests running on it. I couldn't find a better solution. The VMWare Infastructure Client and the web interface are amazing, and so are the commandline management utilities.  Performance is exactly what I expected from this box. Load averages are about 5-10% at idle. Uptime is 99.99%. VMWare forums are very supportive.

VMWare is a proven solution. I would be running ESX/ESXi if I had compatible hardware. Still, I'm always open to new ideas.  Please, prove me wrong.

---

### Post by scorp123 on 2009-08-10
> **samosamo said:**
> For my custom built machine at home I use VMWare Server 2.0 for about six months now.  How is the performance on this thing? I have one 8-core machine running "good ol'" (sarcasm right here) VMware Server 1.x and about a dozen or so VM's on it... and I meanwhile I hate that thing (e.g. patching and upgrading kernels has become a royal PITA ...). I am looking at migrating this server to other solutions, but there are various conditions that have to be met (loooong story ...). I took a look once at VMware Server 2.x when it was new ... but I found it too slow compared to the previous 1.x release. Has the speed improved? Especially the web-based GUI seemed horribly slow when compared to the native client VMware 1.x Server used to ship with ... 

BTW: For end-user office desktops were going to use Sun Ray ultra-thin clients and Sun VDI3: [http://wikis.sun.com/display/VDI3/Home](http://wikis.sun.com/display/VDI3/Home)

Those thin-clients only consume a fraction of electrical power that modern PC's consume ... and the "hot-desking" feature is definitely a bonus.

For server virtualisation some of my colleagues want to use the commercial (but available for free it seems?) "Citrix XENserver 5.5" ... I myself have not yet made up my opinion.

My personal favourite used to be "Sun xVM Server" (basically Solaris + XEN + a incredibly powerful and yet easy-to-use web frontend ...) ... but for incredibly stupid reasons Sun Microsystems has decided to cease development after "Early Access Release #2", so the product is dead already even before it ever reached a beta-testing state. :(

> **samosamo said:**
>  I would be running ESX/ESXi if I had compatible hardware.  The deal-breaker here is that ESX is prohibitively expensive like hell. As soon as you want "advanced features" such as 8-way SMP and "VMotion" (= the ability to move VM's between physical hosts without interrupting the operation in any way) the prices almost double. And there have been some news about the quality of VMware's recent software releases being rather questionable (e.g. ESX 3.5 Update 2 from last year), e.g. reports like this one:

[http://www.virtualization.info/2008/08/vmware-mistake-shuts-down-thousands-of.html](http://www.virtualization.info/2008/08/vmware-mistake-shuts-down-thousands-of.html)

Maaan, imagine. Thousands of VM's down because those idiots in QA didn't catch that piece of code in time .... Just proves why a Open Source solution might be a better idea (a lot more eyeballs to catch bugs ...)

Right now I am evaluating "ProxMox VE" ... It has tons of very nice features. Clustering it is easy too. But there are a few features that I still miss, e.g. "VMotion"-style auto-migrating a VM from one cluster node to other cluster nodes in case of problems. Right now you'd have to do it manually ... and as you can't be sitting 24 hours in front of the screen this missing feature precludes it from productive use for the really critical stuff ... I just hope they will add this feature sometime soon.

---

### Post by PilotJLR on 2009-08-10
> **scorp123 said:**
> 
 The deal-breaker here is that ESX is prohibitively expensive like hell. As soon as you want "advanced features" such as 8-way SMP and "VMotion" (= the ability to move VM's between physical hosts without interrupting the operation in any way) the prices almost double. And there have been some news about the quality of VMware's recent software releases being rather questionable (e.g. ESX 3.5 Update 2 from last year), e.g. reports like this one:

[http://www.virtualization.info/2008/08/vmware-mistake-shuts-down-thousands-of.html](http://www.virtualization.info/2008/08/vmware-mistake-shuts-down-thousands-of.html)

Maaan, imagine. Thousands of VM's down because those idiots in QA didn't catch that piece of code in time .... Just proves why a Open Source solution might be a better idea (a lot more eyeballs to catch bugs ...)


I don't disagree with you regarding the values of open sources, but let's also not spread FUD about VMware. 

The flaw in Update 2 did NOT result in thousands of VM's going down, despite some reporter's attempt to tell people so. The flaw would prevent a power-on of a VM that is already off (so why is the VM off if it's critical?) and would prevent a VMotion from occuring.

VMware patched this is less than 36 hours, and you could apply the patch with ZERO guest downtime. Simply bring up a swing host with Update 1 or Update 2 Respin, then Vmotion TO that, then apply patches one host at a time. Keep in mind that you could VMotion TO a non-affected host. Hence the need for a swing host.

So it was a bad bug, for sure, but most people experienced zero downtime because of it.

---

### Post by scorp123 on 2009-08-10
> **PilotJLR said:**
>  The flaw in Update 2 did NOT result in thousands of VM's going down OK, you're correct. "Going down" wasn't the problem. But getting up and running again was. And I have admin-friends who got badly burned by this, e.g. as the report said there was this Microsoft patch-day at around the same time and some of the Windows VM's were supposed to get patched and then reboot ... And VMware's knowledge base having gone down too wasn't really helpful at finding a workaround.

> **PilotJLR said:**
>  The flaw would prevent a power-on of a VM that is already off (so why is the VM off if it's critical?) That's simple to answer. VDI desktops.

You know what a Sun Ray is?
[http://en.wikipedia.org/wiki/Sun_Ray](http://en.wikipedia.org/wiki/Sun_Ray)

You can have Windows on those things too. The possibly uninformed end-user gets to think "this small plastic box here, that's my 'PC' ... "

But fact is that the instance of Windows the end-user sees is in fact a VM running somewhere on a VMware server (with VDI3 you can also use headless VirtualBox on Solaris 10 u7 now ...)

The problem starts when in a really big company which has deployed thousands of those things throughout their buildings absolutely _NOBODY_ can work because none of the Windows VM's is running anymore (e.g. they got rebooted after having been patched).

There's your "critical VMs" right there. As I said: I have admin-friends who got badly burned by this. They had to explain to a really angry crowd why none of those plastic boxes throughout the buildings were working and why this energy-saving measure (Sun Rays consume only around 4 to 12 Watts, depending on the model) that was supposed to save millions backfired so badly all of a sudden ... OK, some people had laptops and such ... But still. It's not funny if something like this happens.

> **PilotJLR said:**
>  and would prevent a VMotion from occuring. That was the other bad thing. 

> **PilotJLR said:**
>  VMware patched this is less than 36 hours That's almost two days during which some people simply could not work because the VDI VM's would not come back up. It's great that it took them only almost two working days to fix this, yes. But it would have been nicer if their Q&A and other controls had caught this before it did any damage.

> **PilotJLR said:**
>  So it was a bad bug, for sure, but most people experienced zero downtime because of it. We don't seem to hang around in the same circles then I guess? :D

As for people around the globe having gotten hit by this bug, please read here:

[http://communities.vmware.com/thread/162377?tstart=0](http://communities.vmware.com/thread/162377?tstart=0)

---

### Post by samosamo on 2009-08-10
> **scorp123 said:**
> How is the performance on this thing?

I have never used VMWare Server 1.0 so I cannot comment on it.  At first I thought 2.0 was a dud because iowait levels on the host were through the roof until I found the well-documented tweak to load the vmware file systems directly onto a RAM disk.  Why it does not ship like this by default is beyond me. It was smooth sailing after that.

As I said regarding performance, I run 8 linux guests and I have no complaints. I use them all with no notice of slowdown.  I can hit one guest hard, only one core spikes to 100%, and all the other guests don't even feel it. Hard drive speeds are similar to a SATA drive. Uptime is 99.9%. Network speeds are what I expect from gigabit. What else can I ask for? When I first decided to migrate to virtualization I never expected it to go so great.

It's very simple.  I am reading this thread and all the other solutions sound very complicated.

---

### Post by windependence on 2009-08-10
FYI, the patch, at least for ESXi was issued within HOURS, and even before that, an urgent e-mail was sent to all registered VMware customers letting them know NOT to power down their machines. If this is the only large bug within the last 4 or 5 years (AFAIK), that's not bad at all. Think about how many bugs have caused all kinds of trouble with Mickey$oft and you had to wait a WEEK for the fix. Virtualization has now allowed you to simply take a snapshot, load the pathces, and if it breaks someting, revert to the snapshot or if you did it the proper way, you had an identical backup machine to try the pathces or service pack before you even messed with the changes. Virtualization has changed the whole face of the server room - for the good.

Those of you who run VMware server really need to try ESXi. You can use a simple $15 SATA controller OR a CF card to load the hypervisor, and then run your VMs from a SAN or NAS box with an NFS or iSCSI share. That''s how I get around the hardware thing. The performance is MUCH better, with only about a 1% hit on the box for overhead. I can't even tell the difference. Here is a list of whitebox and harware stuff that has been tested and works. This is from the user community:

ESX/ESXi 4.0:

[http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php](http://www.vm-help.com//esx40i/esx40_whitebox_HCL.php)


ESX/ESXi 3.5:

[http://www.vm-help.com/esx/esx3.5/Whiteboxes_SATA_Controllers_for_ESX_3.5_3i.htm](http://www.vm-help.com/esx/esx3.5/Whiteboxes_SATA_Controllers_for_ESX_3.5_3i.htm)

Vmware Server has served me well but I don't deploy those anymore. I have some VMs running web sites on Server 1.06, and they have been running without downtime for YEARS, but ESXi IMHO is sill a better, more stable product. If anyone needs help to get it loaded, I can help you, I have been there and got the T-shirt :-)

-Tim

---

### Post by PilotJLR on 2009-08-10
> **scorp123 said:**
> 
 We don't seem to hang around in the same circles then I guess? :D

As for people around the globe having gotten hit by this bug, please read here:

[http://communities.vmware.com/thread/162377?tstart=0](http://communities.vmware.com/thread/162377?tstart=0)

You'd be surprised. I don't work for VMware, but am with a very large partner and am a beta tester, so I get involved with some weird use cases.

I have a lot of clients that experienced zero downtime from this bug, and my company also experienced zero downtime as a result. We have just over 600 production VM's.

Your VDI example is a good one, though there's obviously another caveat whether unused guests are suspended or remain on. I've seen installations (of View or VDM or XenDesktop) use either. VDI does not necessarily mean this bug results in sessions down, though it obviously may.

The flipside is that there are very few large (1000+) VDI implementations out there, mainly due to the TCO and MS licensing. Certainly no excuse... again, it's a bad bug, but few people were strongly affected by this. I would still trust VMware much more over their competitors.

---

### Post by scorp123 on 2009-08-11
> **PilotJLR said:**
>  I would still trust VMware much more over their competitors. I guess that's something one might argue about for hours. 

BTW, anyone ever heard of Oracle's XEN-based "**Oracle VM**" virtualisation solution? Yes, no kidding, they also have one. But it's almost impossible to find it unless you Google for it ... so I guess they're not advertising it so much?

[http://www.virtualization.info/2007/11/oracle-announces-its-own-xen-based.html](http://www.virtualization.info/2007/11/oracle-announces-its-own-xen-based.html)

[http://wiki.oracle.com/page/Oracle+VM](http://wiki.oracle.com/page/Oracle+VM)

[http://www.oracle.com/technologies/virtualization/index.html](http://www.oracle.com/technologies/virtualization/index.html)


Looking at the tech specs "Oracle VM" looks like a clone of "Citrix XenServer" (and vice versa). But when you mention "Oracle" to people the first thing that comes to their minds is "databases" and then "license costs, ouch ouch ouch .... " .... But "Oracle" and "virtualisation" seemed to mutually exclude each other.

Has anyone ever used this?

---

### Post by scorp123 on 2009-08-11
> **windependence said:**
>  Those of you who run VMware server really need to try ESXi. I have it here on a small Sun Fire X2250. Correct me if I am wrong: But you still need a dedicated client to control and operate ESXi, right? I installed the software VMware's web site suggested "VMware-viclient-all-4.0.0-162856.exe" into a Windows VM running on VirtualBox ... If I am not mistaken this is the same client software you'd use to remote-control ESX ... or "vSphere" as they call it now. And it still requires you to get a license code (which in the case of ESXi can be obtained for free when you download the software).

Is there any way you could do without that Windows software if you use ESXi? I'd definitely prefer a web-based solution a la VMware Server 2.x when it comes to remote-controlling the hypervisor ...

---

### Post by PilotJLR on 2009-08-11
Yes, the VI Client or vSphere client is Win32 only, and is required to control ESXi. I know a linux and OS X vSphere Client is in the works, but I've not even seen the beta bits yet, so I have no idea how long that will take.

I *think* ESXi has a very basic web interface, but you can only power things on and off, so it's not enough for day to day activities. I'm not sure if the web interface is even still there, since I only use licensed ESX/ESXi hosts with vCenter.

I'm lukewarm about Oracle VM, but I've only used it in a lab setting. It's basically Xen + their web interface. The overall adoption of it is quite small, so I shy away from it. 
Citrix XenServer, though, is really very good. The free one does not include HA, but it does include live migration, which is not something VMware will give away for free.

---

