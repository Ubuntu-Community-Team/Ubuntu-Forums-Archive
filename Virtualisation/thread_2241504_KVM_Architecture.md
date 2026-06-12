---
title: "KVM Architecture"
date: 2014-08-26
forum: Virtualisation
---

### Post by Marty_Grove on 2014-08-26
Looking for some insight from you seasoned KVM experts.  Been using Ubuntu Server for a few years on bare metal, going to give KVM a try on my next Ubuntu provisioning.



 I've just started reading about KVM; from what I've gathered so far, Ubuntu server is initially installed which acts as the host OS, then separate VM's are built as guest OS's that run 'inside' the host installation.  If this is the case, my question is this:  what's the general opinion regarding VM architecture on the host installation?  To elaborate, I want to start with two server instances; one will be used as a file server, and a separate one to be used for various development work.  Should I:

 

 1. Install Ubuntu as the host, then set up two VM's (using KVM), one for the file server and the other for development, or
 

 2. Install Ubuntu as the host and configure it for the file server, then build a single VM for development?
 

 I'm curious that if the host OS is configured to perform some function how it might affect the VM's inside?  Maybe its best to minimize functionality of the host installation and let the VM's have all the processing power?

 

 Any thoughts?

---

### Post by TheFu on 2014-08-26
The answer is "it depends".  Too many unknowns to provide any good answer. Sorry.
Sometimes doing it "1" way makes sense. Other times doing it "2" way makes sense. It depends.

If you want to virtualize a desktop, take a look at VirtualBox instead. If you want to virtualize servers, then stay with KVM and don't load any GUI libraries. - Server on Server VMs are great with KVM.  Desktop on Desktop VMs are ok on virtualbox, not so great on KVM.

Oh - and you won't be happy with whatever decision you make. The first few years doing this stuff, we were stuck with few options. Now there are too many options and sometimes they aren't all good for any specific situation.

So ... try what you think is best, if there are issues, come back and look for help with a specific situation.  The best learning comes from failure or struggles.

---

### Post by ibjsb4 on 2014-08-26
> **TheFu said:**
> Desktop on Desktop VMs are ok on virtualbox, not so great on KVM.

Why is that?

---

### Post by TheFu on 2014-08-26
> **ibjsb4 said:**
> Why is that?

The default graphical video connection to KVM is VNC - which sucks. It is fine for LAN-based office-productivity things.  I wouldn't use it over an internet connection (x2go is sooooooo much better and has ssh-tunnel built-in). X2go (or freeNX on 12.04 and older) are 2x (or more) faster than VNC/RDP solutions.  Still - none of these handles video well even on a GigE wired network. X2go audio does work fine from anywhere in the world in my experience.

Most people expect a desktop to play hidef video without stuttering, without artifacts, and by default without any complicated tweaking. That just isn't the situation with KVM today.

I'd hoped that Spice would allow the video stuff to work better in 14.04. It doesn't and the setup for a secure connection is non-trivial (multiple ports/channels needed), so it is only useful on the LAN unless a full VPN already exists.

VirtualBox includes an impressive guestOS-to-hostOS video driver that DOES handle video with 2D (windows only) and 3D GPU acceleration. Hence, my recommendation above.

Oh - and a few people will say that PCI passthru is an option for nearly native graphics performance - the setup for that stuff is still a black art and not suitable for average users - even then - it appears there are 98% failures and only 2% success with the attempts for people with the right BIOS, CPUs, motherboards, and multiple GPUs in their VM host.

Did I get anything wrong?

---

### Post by ibjsb4 on 2014-08-26
> Did I get anything wrong? 						

You took it as a challenge?  Funny :)

[I think its time to move away from vBox.]("http://ubuntuforums.org/showthread.php?t=2240958&p=13107614#post13107614")

---

### Post by TheFu on 2014-08-26
> **ibjsb4 said:**
> You took it as a challenge?  Funny :)

[I think its time to move away from vBox.]("http://ubuntuforums.org/showthread.php?t=2240958&p=13107614#post13107614")

As you know, virtualization is a huge topic and things change all the time. It is impossible for anyone to try every tool, every 3 months, to see what may or may not have changed.  That was the point of my question.

I've never been able to use virtualbox on a Linux host. It wasn't stable when I tried, the system crashed within 24 hrs every time - THE HOST OS - without running any VMs at all. I moved on over that. At the time, I had Xen, KVM, ESXi VM hosts and a Windows box running vbox which was working ok.

OTOH, with a Windows hostsOS and vbox, it worked fine after the 1st year Win7 was released. Under XP, Vista stability was less than 7 days. A year after Win7 was released - stability was from patch-tues to patch-tues. Good enough for desktop-on-desktop.

Servers running either Xen or KVM have uptimes in months and only get rebooted when there is a critical server kernel update. I am a little nervous about Canonical's choice of 3.13.xx kernels. This is a development tree, not meant for stable deployments. I don't know what they were thinking. [https://www.kernel.org/category/releases.html](https://www.kernel.org/category/releases.html) Hopefully, Canonical will push to the 3.14 or 3.16 lines ASAP.  OTOH, a few 14.04 KVM servers here have been working non-stop since late May without issue.

Should people use virtualbox for desktop-on-desktop needs, I can't say. I think it is the least of the evil options (anything from Oracle is still evil, just less than VMware-anything or MS-anything) where playback of video is required in a virtual environment.  For server-on-anything, I would NOT select vbox.

---

### Post by ibjsb4 on 2014-08-26
Thanks and back to Marty :)

---

### Post by Marty_Grove on 2014-08-27
Thanks Fu.

After reading your message and giving it some thought, I think I'll build host install as a file server and then run a single KVM VM for development.  The file server portion will be there long term, the development instances will come and go as needed.  

I guess the thing that I'm having a tough time wrapping my head around is having a host machine that can fully function as a server and then the VM instances which also function as servers.  Not that I don't understand the concept of virtualization... its just that nearly all my experience has been with VMWare, with hosts built upon ESXi, and then the guests run as VM instances.  The hosts' only function is to support the guests.  Pretty much all host resources are allocated to the VM's.

I am guessing that with Ubuntu server and KVM, the host OS is essentially treated as a VM right along with the guest OS's when it comes to allocating resources like cores, memory, storage, etc.?  

Marty

---

### Post by TheFu on 2014-08-27
Sounds like a good plan.
Only 1 caution - do not allow any internet facing services on the hostOS. It that instance is hacked - all other VMs are gone too.

No - the hostOS is NOT like any other guestOS. 
[http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization](http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization) may be helpful.

---

### Post by Marty_Grove on 2014-08-28
Thanks again, Fu.  Good blog article.  One more question though (if I may).... 

You mentioned in your last message to "not allow any internet facing services on the hostOS".  I'd like some more info on how to harden the host OS when running VM's, but I'm particularly curious why the host OS is especially vulnerable to malicious activity.  Is the host OS more vulnerable when running VM's (e.g. via KVM) than, say, running a single Ubuntu Server instance without KVM installed?  Maybe the need for some type of DMZ is required for externally-facing ports to the Internet?  

If you have any recommended reading on the security issues of the host OS, please share a link or two.  I'd appreciate it.

Thanks again,
Marty

---

### Post by mastablasta on 2014-08-28
what kind of power (CPU) do you intend to use/think you will need?

I was thinking of seting up something similar. I see FreeNAS has jails while many use vbox to add these virtual servers. though I am a bit worried that kind of setup will be outside my price range :-)

even though it doesn't seem to be too demanding to run these specialised servers (bitnami stack, turnekey Linux) etc. on lower end hardware. they actually run quite well on my low end desktops... I never put them under any serious load though.

---

### Post by TheFu on 2014-08-28
> **Marty_Grove said:**
> Thanks again, Fu.  Good blog article.  One more question though (if I may).... 

You mentioned in your last message to "not allow any internet facing services on the hostOS".  I'd like some more info on how to harden the host OS when running VM's, but I'm particularly curious why the host OS is especially vulnerable to malicious activity.  Is the host OS more vulnerable when running VM's (e.g. via KVM) than, say, running a single Ubuntu Server instance without KVM installed?  Maybe the need for some type of DMZ is required for externally-facing ports to the Internet?  

If you have any recommended reading on the security issues of the host OS, please share a link or two.  I'd appreciate it.

Thanks again,
Marty

Thanks. I write and present about virtualization a bunch. You might find a step-by-step presentation I did for beginning KVM + libvirt + virt-manager - I'd have to google to find it myself.

No, the hostOS is not more vulnerable - it is just that if they hack that, then every guestOS is "owned" too. Security experts have learned over the years that placing non-complementary services on the same host leads to extra complexity. Extra complexity leads to mistakes.  Is it generally accepted to
* put 1 service on every VM
* don't have ANY public facing services available to the internet - actually, it is best to have the hostOS on a different LAN than where the internet access is provided to guests.
* only allow services that absolutely must be on the internet access from the internet. Best to force a VPN whenever possible, especially for any hard-to-secure services (like anything written in PHP).

So - if we put 1 service on a host - then KVM is that service for the hostOS. Done. Move on to others and put them inside a VM.  A case can be made that storage (AoE, iSCSI, NFS) are special, so allowed. Just be certain they are not accessible on the public facing network if you must put them on the KVM hostOS.

As to security hardening - there are thousands of tiny things to be done on every host after creating a secure network first. DMZ?  Not for a home user. It is just a bad idea, since home users tend to put an entire open machine there, which is always a bad idea.  Use router filters, port forwards to open pin-pricks into the non-secure side of a network.

For reading, I like Bob **Toxen**'s book and the **Practical UNIX and Internet Security** by Garfinkel.
I'll include my signature which has links for more security stuff. Lots of good options online.
Don't forget about joining your local **DefCon** and **OWASP** groups too. We eat, sleep, dream, about security.

Security is hard. Get a process, follow it, improve it, and automate as much of it as you can.  I like Ansible for that aspect. I'm constantly improving the playbooks here for bringing up new servers. [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

Oh and don't forget to have a little fun too.

---

### Post by Marty_Grove on 2014-08-28
> **mastablasta said:**
> what kind of power (CPU) do you intend to use/think you will need?

I'm planning on going with the configuration I've been discussing with Fu (Ubuntu Host OS and a single VM running under KVM) on to an 8-core box that I have.  For starters I was looking at dedicating 4 cores to the host OS and 4 cores to the VM.  Over time I may need to add additional VM's, and I'll divvy up the cores appropriately.  Memory on this machine is at 16GB; i'll most likely increase that in the near future.  My current file server is running fine with 4GB memory, so I would expect it to continue merrily along with 8GB on the new machine.  

Marty

---

### Post by Marty_Grove on 2014-08-28
Again, excellent post Fu.  

I'm planning on getting a start on this new box with the KVM configuration this weekend.  And if any more questions come up, I'll know who to send a message off to!  Thanks for all the help/pointers/suggestions/etc.  Its cleared up a lot of my curiosities.  

Marty

---

### Post by TheFu on 2014-08-28
1 core for a VM, please. Until it is proven that 2 is needed. I think you'll be surprised. No need to waste so many CPUs.
If the hostOS is a pure VM server, 1 core is fine there too.  That means you should be able to have excellent performance (RAM/CPU-wise) for 7 VMs.  Disk I/O and network performance are different issues.

DO NOT OVER ALLOCATE CPU OR RAM for VMs.  None of my VMs have more than 1.8G of RAM allocated.

---

### Post by Marty_Grove on 2014-08-29
> **TheFu said:**
> 1 core for a VM, please. Until it is proven that 2 is needed. I think you'll be surprised. No need to waste so many CPUs.

I agree, but since I have 8 cores and will only be installing one VM (I might go ahead and create 2 VM's while I'm at it), I suppose all the remaining cores will be utilized by the host OS.  

I'll create the first one (or two) VM's with one core apiece when I build the system.  

As always, thanks.

Marty

---

### Post by TheFu on 2014-08-29
For Linux, more is NOT always better.  There are many examples where performance slows with more vCPUs.
Adding 1 more vCPU to a VM is just a shutdown, change the setting, restart effort for Linux. Trivial.  Start with 1.

---

### Post by Marty_Grove on 2014-09-09
Thought I'd add a few updates from my experiences with KVM.  

My first (few) installation attempts went well, but I wasn't getting the performance I would like to see.  It appears to be mostly due to the X11 protocol; very slow screen refreshes.  I see Spice is supported but I haven't configured it yet.  Might give it a shot in the next few days.  

But for setting up KVM/libvirtd/QEMU, it was all pretty straight forward.  Seemed pretty stable.  

I'll try to get another update out in a few days after I've had a VM cooking for a while.  

Marty

---

### Post by TheFu on 2014-09-09
You are trying to virtualize desktops?  Which apps?  I use x2go for remote desktops and it works really well, securely from anywhere in the world. Clearly, it doens't handle video, but that is an issue for every free remote desktop offering available.  The only solution for that I know is using Xen and their paid remote desktop solution.

For servers - X11 performance doesn't matter, obviously. Plus NOT having any X11 dependences is smart for servers.

---

### Post by Marty_Grove on 2014-09-10
> **TheFu said:**
> You are trying to virtualize desktops?  Which apps? 

Only to experiment with the installation and performance of KVM.  Long-term I doubt I'll have any need for a desktop installation of any VM.  Over the weekend I experimented with the installation of the following VM's:


[LIST]
[*]Ubuntu 64 minimal install 
[*]Ubuntu 64 Desktop 
[*]Fedora 64 
[*]CentOS 7 minimal install 
[*]CentOS 7 KDE desktop 
[/LIST]

All the VM's installed fine.  I played around with VNC for a bit on the installs that had desktops installed, and noticed that the graphical interface was pretty poor... really unusable for the most part.  But again, these tests were only to experiment with VM installations since I've never worked with KVM before.  Overall I am very satisfied with the performance of the VM's.  I have two minimal installs running now: Ubuntu and CentOS 7.  Both seem to be performing very well as minimal installs.  If I need a GUI of some app... say gparted... I can always run it in an X-window session from the minimal installs.

Marty

---

### Post by TheFu on 2014-09-10
Inside a VM, you generally don't need any GUI apps ... except for a remote desktop. Remote GUI stuff is to be **avoided.**  VNC performance through VMM - er ... sucks.  Use **x2go**. This is a c/s thing and nothing to do with VMs.  Highly acceptable performance for non-video stuff - think "productivity" apps like LibreOffice.

Servers virtualize great, provided you follow commonly understood techniques to improve sharing of shared resources and provide the most efficient I/O for disk and networking possible.  Do the hard storage stuff outside the VM, not inside.  Same for the redundancy stuff (if you need it).

If you need Gparted - boot off a gparted ISO - make the changes, after all the storage can't be mounted anyway - then reboot the VM, removing the ISO before it comes up.

You've installed desktops. Try Ubuntu Server, Debian Server, CentOS without any GUI. Performance should be excellent.  For tips on getting the best performance: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) - it is for virtualbox, but everything does transfer to KVM, ESXi, and VMware Player.  Except - don't allow any disk caching from inside the VM storage parameters - only let the hostOS handle disk caching. Of course, if the storage has direct passthru (like using a VT-d and PCI card) then let the clientOS do disk cache management.

Pretty much everything can easily be changed later for Linux guests - except the storage.

---

### Post by heiko_s on 2014-09-26
Any reason(s) for preferring KVM over Xen? Probably I'm not familiar enough with KVM to judge, but I can't see the benefits over the latter (long-term stability, features, documentation, etc.).

Note: I'm asking this here since other options have been mentioned, such as VB, ESXi, and VMware Player.

---

### Post by BrokenPoet on 2015-03-08
Marty (Fu, et al)-
   I'm at the same place as you were back in August.  I'm curious as to where you ended up putting your network storage (host or guest?)  I'm pondering the below two architecture options with storage on the host & within a VM respectively, and am looking for any lessons learned from your install.  I'm leaning towards putting the storage on the host and sharing with VMs/network via Samba.
   Thanks!
(edit: Slides should say 'LAMP', not 'SWAT'.  Not sure where my brain was.)
[ATTACH=CONFIG]260525[/ATTACH]
[ATTACH=CONFIG]260524[/ATTACH]

---

### Post by TheFu on 2015-03-08
I ran Xen for 3 years on Ubuntu. About once a year, Xen updates would break the hostOS so it wouldn't boot, thus taking a VM host down and all the client VMs.  After 4 yrs of these kinds of issues, KVM was mature enough to be tested.  We brought up a single KVM host and moved some unimportant VMs there.  After a year with ZERO issues (truly ZERO issues), we started migrating all our prior VMs off Xen and ESXi.  Ran ESXi for 3 years. It was really, really, picky about hardware.  Had to get off ESXi for other reasons ($$$) too when they changed licenses that would increase costs 2-3x.  That was 2010-ish and we've been on KVM since and extremely happy. We treat KVM VMs like physical hosts for the most part.

Today I moved 10 VMs between different servers - no issues. I didn't expect any.

Perhaps Xen is better these days. I just don't see the reason to switch. I've heard from others that Xen works best on RHEL/CentOS, not-so-great on Debian/Ubuntu. That maps to my experiences.  KVM is extremely well-supported. It is the core of OpenStack and a few other cloud management systems. 

And just to be clear - ESXi, KVM, Xen were all rock solid for many months when they ran.  ESXi and KVM never refused to boot, not once.  Xen did. I was always nervous about Xen updates and having 2+ hrs to work through issues if anything didn't work right.  Many times, we'd have to fall back to an older kernel after an update with Xen.

Hope that explains more why we use KVM.  Our needs do not necessarily map to those for anyone else. 
Our experiences don't necessarily map to anyone elses either. Lots of people are happy running Xen and/or ESXi. 
The issues we experienced could easily have been user-error.

---

