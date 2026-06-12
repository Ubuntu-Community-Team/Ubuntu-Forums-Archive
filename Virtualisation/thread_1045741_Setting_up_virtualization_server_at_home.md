---
title: "Setting up virtualization server at home"
date: 2009-01-20
forum: Virtualisation
---

### Post by Ein2015 on 2009-01-20
So after a good few hours of searching, reading, and not finding a good enough conclusion for my questions... I'll just bug the ubuntu community... :)

I'm about to finish a system running an [Intel Core 2 Duo (E6600)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115003") and I wanted to put ubuntu 64-bit server on there.  It'd have 4 gigs of RAM and a good 5 or 6 TB of HDD space from 10 HDDs as well.

The basic idea would be to have a very simple, base operating system that I would touch as little as possible.

From there, I would create virtual machine that would have things like file sharing, torrents, a personal webserver, etc on there.  However, the tricky thing to note is that I imaging more than one virtual machine will be running a webserver, so I'll need to know how to properly deal with that.

I would also create other virtual machines to use in development testing... so it'd need to support linux, osx, and windows VMs.

I was looking into some things like [virtualmin]("http://www.virtualmin.com") and [virtuozzo]("http://www.parallels.com/products/virtuozzo/") in order to give me a nice GUI to control my virtual machines with, create new ones etc.

Since this is to be ran at home and not in a corporate environment, I need my costs to be low.  [VMWare ESX]("http://www.vmware.com/products/vi/esx/") looks really cool... but is rather prohibitively expensive for me.

So my questions to the ubuntu community are as follows:
[LIST]
[*]what are good links to deal with multiple apache servers in virtualized environments?
[*]are there any tutorials for setting up a home virtualization server?
[*]what administrative tools do y'all recommend for creating, managing, and deleting virtual machines?  (also, the ability to limit bandwidth on those VMs would be FANTASTIC!)
[*]any other recommendations?
[/LIST]

Thanks a ton to everybody for their help here!
- Ein2015

---

### Post by samosamo on 2009-01-20
i was about to make this same exact post.

---

### Post by littlegreiger on 2009-01-20
If you're looking at VMware ESX, you should try their free version, ESXi, [http://www.vmware.com/products/esxi/]("http://www.vmware.com/products/esxi/"). I haven't used it and haven't really heard much about it, but if you have time to tinker with it I think it would probably do a good job.

Other than that I would suggest installing Ubuntu Server and running VMware server 2.0 as it includes quite a nice web interface to manage your machines.

As for setting the other things up like apache and bandwidth limiting there's not much I can help you with as I've never done really dealt with what you want.

---

### Post by Brazen on 2009-01-20
I personally use KVM.  You get great information on how to set it up at help.ubuntu.com.  I use libvirtd from the commandline with virsh and virt-install, and I would suggest doing the same as I've encountered bugginess with the graphical tools (on Ubuntu and Fedora, so it's the package's fault, not Ubuntu's).

If you want something a little more newbie- and gui- friendly, you might try VMWare Server.  I've used it and it really is a cinch to set up and gui can be ran remotely (it's all through the web in version 2) and is very intuitive.

As for multiple Apache web servers, there is really nothing to say... it works just like if you had multiple physical servers with Apache on them.  You just connect to the different ip addresses of the virtual machines.

---

### Post by windependence on 2009-01-20
There are a few things I think you are confused about here. Virtualmin is for administering virtual hosting. It has nothing to do with virtual machines. Virtuozzo is Parallels' virtualization solution, and isn't really very popular and I believe is a paid product.

There are two ways you can go here. You can choose one of the many virtualization engines that run on top of another OS like VMware Server or Virtual Box, but these are generally slower and take more resources because of the underlying OS requirement. You also have to be very careful with some of these like KVM because they are very picky about hardware requirements.

The other way you could go and by far the best is a bare metal hypervisor that runs right on the hardware and your VMs run on top of that. There is no "host" OS on these, they run directly on the hardware. VMware ESXi was mentioned and is what I use as it was made free in August. It used to be over $500 retail. Contrary to what many people think, ESXi has a very nice free management console called the Virtual Infrastructure Client. Basically, you load ESXi on your host box, and then you manage it from another box with the VIC. It also has web based management capabilities but some of these are limited. Don't get confused though, you can access your VM host from anywhere you have a web connected machine. You just load the VIC on that machine and connect by IP address or host name. Right now, you can only manage from a Windoze box, but that is about to change as they have a Linux client and even an iPhone client in development.  The ESXi hypervisor is just 32 MB footprint size. You can even run it from a compact flash card. Dell and HP have servers you can order with ESXi on a ROM chip. It's really one of the most stable solutions out there for free with the widest hardware support. You can run almost anything on it.

As for multiple Apache servers, you have to get your mind on a different paradigm and think of your VM box as your data center and your VMs are actual Machines because for all intents and purposes they ARE separate machines. What is running on one machine has nothing to do with what's on another and each machine is totally separate and unaware of the others. You can create virtual routers, switches, and NICs within your virtual environment, therefore you can limit network traffic and route things the way you want. I will tell you, it will not just configure itself though, you will have to learn the software and learn some aspects of networking you probably aren't familiar with. There is a learning curve here but you can literally create as I call it a "data center in a box". It's fantastic new technology and as far as VMware is concerned it's rock solid and proven. IMHO they have the most mature product out there.

If you need help, just post your question and I'll see if I can help you.

-Tim

---

### Post by Ein2015 on 2009-01-21
Hey everybody... thank you for the responses so far!

It looks like the ESXi route which windependence pointed out will be closest what I want.  That's the idea I was intending.

As far as the apache stuff goes, what I am looking for is something like have ubuntu.domain.com, wintest1.domain.com, and osxtest3.domain.com.  I suppose then what I should do is run another VM aptly-named dns.domain.com?  How would I be able to set everything up so that I could have each VM be automatically pointed to as vmname.domain.com?  (Basically if I name a VM to be fedoratest1 then I should be able to access it via fedoratest1.domain.com.)  That seems to be the next step in my puzzle.  I could use another machine as a DNS server if I need to.  Just recommend which is the best choice.

Now time to read about ESXi while I await the responses to this step.  :)

Thanks again!
- Ein2015

Edit: while looking around I find that I love Sun's xVM stuff... now if only it was all free so I could set it up at home!  :P  I really love all the tools for resource monitoring and whatnot.

---

### Post by Brazen on 2009-01-21
> **Ein2015 said:**
> Hey everybody... thank you for the responses so far!

It looks like the ESXi route which windependence pointed out will be closest what I want.  That's the idea I was intending.

As far as the apache stuff goes, what I am looking for is something like have ubuntu.domain.com, wintest1.domain.com, and osxtest3.domain.com.  I suppose then what I should do is run another VM aptly-named dns.domain.com?  How would I be able to set everything up so that I could have each VM be automatically pointed to as vmname.domain.com?  (Basically if I name a VM to be fedoratest1 then I should be able to access it via fedoratest1.domain.com.)  That seems to be the next step in my puzzle.  I could use another machine as a DNS server if I need to.  Just recommend which is the best choice.

Now time to read about ESXi while I await the responses to this step.  :)

Thanks again!
- Ein2015

Edit: while looking around I find that I love Sun's xVM stuff... now if only it was all free so I could set it up at home!  :P  I really love all the tools for resource monitoring and whatnot.

You could host all those subdomains on a single Apache server, if you wanted to.  fedora1.domain.com, mybox.domain.com, hello.domain.com could all be on the same Apache webserver but each serve up different sites.

As for how to get those domain names to point to the correct box (whether all one box, or multiple boxes) will be done entirely within your dns server.

---

### Post by Robstarusa on 2009-01-21
KVM rocks.

With a little finangling I got bridged networking working as well.

Not quite as nice as vmware, but VERY close & the vms seem much more responsive.

I have a a 45w amd dual core and am running 5 VM's.  I have 8G ram and ubuntu 64 bit server.

If anyone needs help with bridged networking, please let me know.  There is a VERY SMALL bug in one of the python scripts that comes with libvirt that I have a patch for (really it's, I believe a single change of a single line) and once you have that it rocks.

I even have all vm's bridged to a bonded interface & it works flawlessly.

---

### Post by bodhi.zazen on 2009-01-21
I suggest either openvz or KVM (or BOTH).

The openvz kernel is supported on 8.04 (LTS). From what you are asking, do a minimal install, then install KVM and OpenVZ.

[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)

If you like you can download the OpenVZ live CD (I like the Centos version) and, once you boot, there will be a pop up tutorial that explains how to run OpenVZ.

You may also wish to look at 

    Proxmox : [http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

Proxmox = Open source = KVM + OpenVZ + web admin tool

---

### Post by Ein2015 on 2009-01-24
Thanks bodhi.zazen, I'm looking into what you have suggested as well.

It looks like the Sun xVM Server is free but is only in Early Access mode now... with a first general release due later this quarter.

From what I've read, hypervisor solutions (like xVM Server and ESXi) seem to get better performance than a full-fledged Ubuntu server install with virtualization software.  Any opinions on this?

I'll continue my research and will definitely post again once I have more updates. :)

---

### Post by windependence on 2009-01-24
> **Ein2015 said:**
> Thanks bodhi.zazen, I'm looking into what you have suggested as well.

It looks like the Sun xVM Server is free but is only in Early Access mode now... with a first general release due later this quarter.

From what I've read, hypervisor solutions (like xVM Server and ESXi) seem to get better performance than a full-fledged Ubuntu server install with virtualization software.  Any opinions on this?

I'll continue my research and will definitely post again once I have more updates. :)

I have servers running both ways and by far, bare metal wins. Running your VMs on top of a host OS takes much more system resources. Why do it if you can install a hypervisor that takes up just 32MB and runs super efficiently? You could even use one of the VMs as your desktop. Also, I can host many more VMs on ESXi than I could using VMware server. ESXi and the VIC administration tools are free. People will tell you they aren't but that's because VMware's documentation leaves a lot to be desired and doesn't explain how to get this stuff. It's easy and it's all there. I'm even running ESXi on a flash card adapter attached to the IDE channel on the motherboard of one of my boxes. Runs great on a 1GB flash card.

-Tim

---

### Post by redbrain on 2009-01-24
Yeah def try and stay away from ESXi because its just a bit useless because its VERY basic, its ok for virtulisation if you have a windows system about to control it! And you cant acess the web interface unless you pay out for the new Virtual center 4 and then you have fix it so you can get rid of the SSL problems.

And then you still cant do anything with your hardware other than make virtul machines which has very poor disk read/write :P.

Yeah.. i dont like vmware i work with it all day at work and i am getting most of every over to xen/kvm now! Its been a pain! :P

I like [http://pve.proxmox.com/wiki/Main_Page]("http://pve.proxmox.com/wiki/Main_Page")

Its probably what your looking for or just stick ubuntu server on and use KVM :)its all better because your always supported and updated!

---

### Post by dnorrishill on 2009-01-26
I have been experimenting with VMWare esxi and now have a very old Dell PC running Ubuntu in a virtual machine. One of the perceived downsides of esxi is that it has a very limited set of officially supported hardware. However there is an excellent site [www.vm-help.com](www.vm-help.com) which has loads of tips on getting esxi running on non-supported hardware. They even have a whitelist of configurations that other users have used to run esxi.

I know its a little tedious that the config tool only runs in Windows, but I think it also has an optional command-line interface.

---

### Post by windependence on 2009-01-26
I agree, that site is great and remember, they are officially supporting machines from Dell, HP, and IBM, so whatever controllers they use almost have to be supported. Dell Perc (LSI) controllers work really well as well as several Adaptec controllers. There is even a $19 controller that works for loading the hypervisor. Some of this can be bypassed by using a CF to IDE adapter and running the hypervisor off the CF card. It runs in memory after it's loaded anyway, so it doesn't affect performance.

-Tim

VMware Partner

---

### Post by Ein2015 on 2009-01-30
So I want to do a nice bare metal hypervisor... so ESXi or xVM Server?

Any opinions?

---

### Post by fishy6969 on 2009-01-31
I've messed around with all the freely available options and have found openvz to be the least problematic - I'm running it from 8.04 server, with 2Gb RAM. Running 6 VM's - even one running a myth backend in one. One word of warning - if anything tries to install udev within a VM, let it, but then issue an 'apt-get remove --purge udev' or there will be problems!

---

### Post by Ein2015 on 2009-02-04
fishy6969,

I would do that, except I'm hoping to install a hypervisor instead of a full-out Ubuntu server install.  (From there I can run ubuntu server in a VM! :D)

---

### Post by Poleh on 2009-02-04
> **littlegreiger said:**
> If you're looking at VMware ESX, you should try their free version, ESXi, [http://www.vmware.com/products/esxi/]("http://www.vmware.com/products/esxi/"). I haven't used it and haven't really heard much about it, but if you have time to tinker with it I think it would probably do a good job.

This absolutely would be your best option, particularly if you want to keep the underlying host OS overheads down so you have as much as possible for VM's.

ESX comes with full blown virtual networking, so multiple servers, ip's and web services etc. is no problem at all. Then think what you could do with cloning vm's, snapshotting them, isolating them in dedicated dev networks ... etc. :)

---

### Post by Brazen on 2009-02-26
Just to clear up any confusion, KVM _is_ a hypervisor just like Xen or ESX.  KVM turns the linux kernel into a hypervisor and the command line that you interact with would be the equivalent of the "service console" on ESX.

> **Robstarusa said:**
> 

I even have all vm's bridged to a bonded interface & it works flawlessly.

Ah, now that is one thing I would like to get set up.  Right now I do have bridges going to multiple vlans so I can isolate my vms on different networks based on the bridge device assigned to the nic.  I would really like to get vlans going over a bonded interface, though.

---

### Post by mckenna1977 on 2009-02-26
Howrya?

My recommendation would be to do a bare-metal install using VMware ESXi as it's simple, fast and heavily documented. Then either install ubuntu on top or easier again go to the vmware appliances site (here's ubuntu [http://www.vmware.com/appliances/directory/1224](http://www.vmware.com/appliances/directory/1224)) and download a ready made virtual machine that you load through the vmware infrastructure client into your datastore and you're done. 

as for the apache sites, i'd set up apache virtual sites - you just do this as per here : [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html) - you create named sites to folders and resolve those site names via DNS.

That's my tuppence worth and very good luck to you!!

---

### Post by dmizer on 2009-02-26
Moved to virtualization :)

---

### Post by starfry on 2009-03-03
Hello, Glad I found this thread.

I will soon have a nice core-i7 machine with loads of RAM for the purpose of running VMs. The thing that is confusing my choice is the fact that this machine will be my workstation. It will run servers also, but it needs to support desktop environments also.

This is where my confusion kicks in!

I think a lot of products - Vmware ESXi, Xen, Kvm and others are designed for the server world and may not lend themselves to virtualised desktop environments and some may not run Windows guests.

I currently run VirtualBox on my existing system and I have VMs for a few Windows XP environments, some Ubuntu and some other - including my LFS (Linux From Scratch) machines. One of my Windows XP VMs is a bare-metal VMDK that I can also dual boot into (so I have the choice of booting Windows, or booting Linux and running the same Windows install in a VM). VirtualBox supports all this nicely and can run unmodified guests, so it all works.

However, I am not sure if it is the best solution now that there are a lot of options out there.

I was thinking that running openvz may be a more efficient solution for my Linux VMs but, if they share the same kernel will this cause problems ?

It seems to me that KVM, being part of the Linux Kernel, will be the ultimate winner long term just because it is there (draw a parallel with integrated Internet Explorer in the Whindows world).

I like the idea of KVM because it can do PCI passthrough; VirtualBox can't (but Virtualbox has excellent USB support).

I looked at Xen but have read you can't use Nvidia drivers with an Xen capable kernel which is a problem. Not sure if this is still true.
  
I am not sure if certain solutions will work together - can I use openvz with KVM/Xen/Virtualbox ? (I think so because openvz is not a hardware virtualiser but I am not sure). Can I run KVM and VirtualBox etc...

I have existing VMs in VirtualBox VMDK and VDI images and would like to continue using them (either with VirtualBox or by porting them to another format or using a solution that supports VDI/VMDK).

Sorry, loads of questions but hopefully the knowledge base here can provide some intelligent answers. I want to do this once and do it right :)

Many thanks!

---

### Post by dmizer on 2009-03-03
I don't think you can run more than one virtualizer on your machine at a time. Otherwise they would be competing over who gets to control the hardware.

Vmware runs whatever I throw at it, Windows, OSX, Linux ... name it, I've not had a problem running it. Never had a problem running a couple of virtual machines while using my desktop either. My old server (a 2.66GHz P4 box with a gig of ram) ran my web server and my mail server in virtual machines, all while I used the desktop to do whatever I pleased.

Now I have a Core Duo (quad core) box with 4 gig of ram, and I can have up to 10 (depending on memory configuration) virtual machines all running at once before I start to notice a performance hit on the desktop.

And, vmware isn't especially efficient either. I don't think you'll have any problem.

---

### Post by bodhi.zazen on 2009-03-03
I find if you are running a lot of virtual machines it helps to dedicate the machine to be a server of the VM and not a desktop, but that is an opinion and you can certainly install a desktop as well.

Also you can use multiple technologies with some limits.

The big one is that KVM conflicts with VMWare.

Otherwise, a great combination is KVM + OpenVZ.

You can run VMWare + Virtualbox and / or KVM + VirtualBox.

Xen when commercial has as such is falling out of favor, even with Red Hat / Fedora. Not that Xen does not have a great product mind you.

KVM, however, is amazing and opensource. Not as many GUI options, but many options from the command line. You can use USB storage devices or physical partitions with KVM no problem.

---

### Post by starfry on 2009-03-03
Thanks for your reply Bodhi.

> **bodhi.zazen said:**
> a great combination is KVM + OpenVZ.

You can run VMWare + Virtualbox and / or KVM + VirtualBox.

I was thinking the way to go would be KVM + VirtualBox. However I also like the sound of OpenVZ for the Linux based VMs. So, Is KVM + OpenVZ + VirtualBox an option that will work ?

I guess, by what you have said, it will work unless there is a conflict between OpenVZ and VirtualBox.

I can see [here]("http://packages.ubuntu.com/search?searchon=names&keywords=virtualbox") there are Ubuntu packages mentioning VirtualBox and OpenVZ so I guess that means it works ?

If so, does this apply to the PUEL version as well as the OSE verson (I want to run the PUEL version of VirtualBox).

Thanks for your help.

---

### Post by bodhi.zazen on 2009-03-03
> **starfry said:**
> Thanks for your reply Bodhi.



I was thinking the way to go would be KVM + VirtualBox. However I also like the sound of OpenVZ for the Linux based VMs. So, Is KVM + OpenVZ + VirtualBox an option that will work ?

I guess, by what you have said, it will work unless there is a conflict between OpenVZ and VirtualBox.

I can see [here]("http://packages.ubuntu.com/search?searchon=names&keywords=virtualbox") there are Ubuntu packages mentioning VirtualBox and OpenVZ so I guess that means it works ?

If so, does this apply to the PUEL version as well as the OSE verson (I want to run the PUEL version of VirtualBox).

Thanks for your help.

At the moment I am running OpenVZ + KVM on 8.04. The Openvz Kernel patch is not available for higher kernels as of yet (to the best of my knowledge that is).

I have run KVM + OpenVZ + VirtualBox in the past, but really with KVM, IMO, there really is no good reason to run Virtualbox. IMO VirtualBox is in fairly rapid development and KVM does everything I need (I personally am used to running qemu, so kvm is easy and personally I run it from the command line with a wrapper script).

So I have not tried KVM + the latest VirtualBox and can not confirm if it works or not.

If I were going to install an OS from scratch to use a a platform for virtual servers, however, I would go with Proxmox :

[http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)

[http://pve.proxmox.com/wiki/Downloads](http://pve.proxmox.com/wiki/Downloads)

But again that is not a desktop, but Proxmox offers very nice management tools for your VM.

---

### Post by starfry on 2009-03-04
> **bodhi.zazen said:**
> At the moment I am running OpenVZ + KVM on 8.04. The Openvz Kernel patch is not available for higher kernels as of yet (to the best of my knowledge that is).
Does that mean that it only works on Hardy then? 
Well I am running Hardy atm so that means I am ok right?
> **bodhi.zazen said:**
> 
I have run KVM + OpenVZ + VirtualBox in the past, but really with KVM, IMO, there really is no good reason to run Virtualbox. IMO VirtualBox is in fairly rapid development and KVM does everything I need (I personally am used to running qemu, so kvm is easy and personally I run it from the command line with a wrapper script).
Not sure I understand - if VirtualBox is in rapid development then surely that's a good thing? ;)
I would most likely use KVM for my newly created VMs going forwards but I have reasons for needing VirtualBox:
 - KVM requires Hardware Virtualization. I don't have a machine with HV on it yet so I can't use KVM just yet
 - I have existing VMDK images running off bare metal
 - I have existing VDI images that I would like to avoid rebuilding

> **bodhi.zazen said:**
> 
So I have not tried KVM + the latest VirtualBox and can not confirm if it works or not.
Well, last night I decided to install OpenVZ and got that working, but my VirtualBox just hangs (doesn't even pop up the VM window) if I am booted with the openvz kernel. It still works fine if booted into the generic kernel.

I found [this thread]("http://forum.openvz.org/index.php?t=msg&&th=6700&goto=32893#msg_34609") that implies it does work. I may try re-installing VirtualBox after booting the openvz kernel and downloading the kernel sources and headers as that thread suggests. I will report back.

I may also take a look at Proxmox.

---

### Post by bodhi.zazen on 2009-03-04
> **starfry said:**
> Does that mean that it only works on Hardy then? 
Well I am running Hardy atm so that means I am ok right?

You will be fine with 8.04

> Not sure I understand - if VirtualBox is in rapid development then surely that's a good thing? ;)

Rapid development is great so long as it does not cause breakage. You are talking about running a virtuilization server and although I understand this is new to you, many people run the guests 24/7/365 for "mission critical" tasks. In a "production environment" stability is very much more important then the newest, latest, greatest.

As I see from your latter posts, the newest latest VirtualBox is not running :(. I hope it is just a matter of reinstalling the kernel modules, you need to do this with each (new) kernel, what error message are you getting ?

> I would most likely use KVM for my newly created VMs going forwards but I have reasons for needing VirtualBox:
 - KVM requires Hardware Virtualization. I don't have a machine with HV on it yet so I can't use KVM just yet
 - I have existing VMDK images running off bare metal
 - I have existing VDI images that I would like to avoid rebuilding

Those are all good reasons to run VBox. FYI, if you ever need, you can convert your virtual machines to run in KVM.

> Well, last night I decided to install OpenVZ and got that working, but my VirtualBox just hangs (doesn't even pop up the VM window) if I am booted with the openvz kernel. It still works fine if booted into the generic kernel.

I found [this thread]("http://forum.openvz.org/index.php?t=msg&&th=6700&goto=32893#msg_34609") that implies it does work. I may try re-installing VirtualBox after booting the openvz kernel and downloading the kernel sources and headers as that thread suggests. I will report back.

I may also take a look at Proxmox.

Good luck. OpenVZ is very nice IMO for single servies. The guests are very llight weight. Check out how little and enter the guest and run

ps aux

---

### Post by starfry on 2009-03-05
I can confirm that OpenVZ and VirtualBox can run together on the Host.

I had to just rebuild the VirtualBox kernel driver. Quite easy:

```

$ sudo apt-get install linux-headers-$(uname -r)
$ sudo /etc/init.d/vboxdrv setup

```

It's that simple :)

Now, I haven't done any extensive testing but I do have a OpenVZ VPS running alongside a VirtualBox running Windows XP.

---

### Post by sefs on 2009-03-23
> **windependence said:**
> There are a few things I think you are confused about here. Virtualmin is for administering virtual hosting. It has nothing to do with virtual machines. Virtuozzo is Parallels' virtualization solution, and isn't really very popular and I believe is a paid product.

There are two ways you can go here. You can choose one of the many virtualization engines that run on top of another OS like VMware Server or Virtual Box, but these are generally slower and take more resources because of the underlying OS requirement. You also have to be very careful with some of these like KVM because they are very picky about hardware requirements.

The other way you could go and by far the best is a bare metal hypervisor that runs right on the hardware and your VMs run on top of that. There is no "host" OS on these, they run directly on the hardware. VMware ESXi was mentioned and is what I use as it was made free in August. It used to be over $500 retail. Contrary to what many people think, ESXi has a very nice free management console called the Virtual Infrastructure Client. Basically, you load ESXi on your host box, and then you manage it from another box with the VIC. It also has web based management capabilities but some of these are limited. Don't get confused though, you can access your VM host from anywhere you have a web connected machine. You just load the VIC on that machine and connect by IP address or host name. Right now, you can only manage from a Windoze box, but that is about to change as they have a Linux client and even an iPhone client in development.  The ESXi hypervisor is just 32 MB footprint size. You can even run it from a compact flash card. Dell and HP have servers you can order with ESXi on a ROM chip. It's really one of the most stable solutions out there for free with the widest hardware support. You can run almost anything on it.

As for multiple Apache servers, you have to get your mind on a different paradigm and think of your VM box as your data center and your VMs are actual Machines because for all intents and purposes they ARE separate machines. What is running on one machine has nothing to do with what's on another and each machine is totally separate and unaware of the others. You can create virtual routers, switches, and NICs within your virtual environment, therefore you can limit network traffic and route things the way you want. I will tell you, it will not just configure itself though, you will have to learn the software and learn some aspects of networking you probably aren't familiar with. There is a learning curve here but you can literally create as I call it a "data center in a box". It's fantastic new technology and as far as VMware is concerned it's rock solid and proven. IMHO they have the most mature product out there.

If you need help, just post your question and I'll see if I can help you.

-Tim

Vmware Inc. should hire you as part of their sales team.  You have me very well sold on this technology. Amazing is all I can say.

---

### Post by lewtwo on 2009-03-24
VmWare Server will run on nearly anything. VMware ESXi is much more picky (i have the none supported hardware to prove it). If you are talking about a small server only solution for a home network then you might want to take a look at Proxmox. Based on Debian Etch, Qemu, KVM, Open VZ and VLan it is small and efficent with a Web Base GUI for routine tasks. More specific stuff has to be done via SSH CLI but it does need a CPU with support for Virtualization (a lot RAM depending on the number of VMs that you need to run at once).

---

### Post by Ein2015 on 2009-04-15
I figure I might as well update the community.

Off and on I've been working on setting the server up, trying OpenSolaris (since the barebones xVM server hypervisor is not yet complete)... but it's proving to be an order of magnitude more difficult to do.

This basically means that more than likely I'll be switching BACK to Ubuntu and try some of the other options presented in this thread.

Ubuntu rocks. :guitar:

---

### Post by samosamo on 2009-04-28
As you can see in the second post of this thread, back in January I started with the same idea as you.  Virtualize all my home servers.  Web, torrenting, email, whatever. Shouldn't be a big deal, right?  All light duty servers to support a total of one users (me).  I went the route of VMWare Server running 8 ubuntu guests.  It looks great, it has a great management interface and all but I just can't recommend it.  I have been playing around for a few weeks now and I'm not happy with it.  Performance, specifically high iowait, is unacceptable.  It may have been the way I designed it but I can't blame myself for lack of documentation on setting this thing up.  I have spent way too much time trying to figure out exactly what is causing it and I really need to start looking at other solutions.

I'm not trashing VMWare Server because I feel it's stupid to without technical proof to back it up.  I just think there is a better way to go about this. I wish there was more troubleshooting documentation on it.

---

### Post by dmizer on 2009-04-29
A couple things that could cause IO wait:

1) Large virtual disks. The bigger your virtual machine's image, the more difficult it is for your host OS to read it. So if your virtual images get to be more than 10 or 15 gig (depending on your hardware), you'll start to see extreme performance decrease. In other words, you should not be hosting large numbers of file shares from your virtual machine. Your files should be located on a physical disk and mounted into the virtual machine.

There are a couple ways you can reduce that restriction. One is to allow vmware to split your image into 2gig files upon creation. Another way would be to enable ext4 on the host OS, as ext4 can handle larger file sizes without sacrificing performance.

2) Your IO performance may be related to an incorrectly configured network. Sometimes vmware needs non-default MTU settings.

3) Not enough/too much memory for your virtual image. Make sure to check the vmware settings to see what the suggested minimum and maximum virtual memory is. Something to keep in mind is that, sometimes, giving it maximum virtual memory will reduced performance.

Try trobleshooting your IO speed problem just as you would a physical machine.

---

