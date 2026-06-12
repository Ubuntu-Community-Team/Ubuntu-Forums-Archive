---
title: "Xen boot hangs on forever[Ubuntu Server 12.04]"
date: 2015-03-15
forum: Virtualisation
---

### Post by sklpr on 2015-03-15
Hello all, 

I am totally new into XEN and virtualization and I need to setup a Xen Hypervisor in order to do one project for my university! 

I firstly tried to install XEN 4.1.2[dom0] on Ubuntu *Desktop *10.04 x64 bit but failed like 1000 times to boot it following many guides on google.. 

So i decided it to try Ubuntu *Server * 12.04 LTS x64 bit where i wouldn't need to configure and build my own kernel for XEN ( like on ubuntu 10.04 ).. I followed every step mentioned on official website of ubuntu but still i get this error [http://prntscr.com/6h9now]("http://prntscr.com/6h9now") and can't boot into XEN .. Can someone help me out ? I don't know what am i doing wrong .. ! 

Also I think i have to mention that I am trying to do this Under VMware workstation 11 having enabled  "Virtualize Intel VT-x/EPT or AMD-V/RVI " option for CPUS .

Please ask me if you need further information that might help you solve my problem ! 

Thanks in advance ..

***// UPDATE ***

That's the problem  : "Performance Events : unsupported p6 CPU model 26 no PMU driver, software events only. " 

but if I boot from my main kernel - Ubuntu distro and i run this [IMG]http://i61.tinypic.com/24vqskj.png[/IMG] There is a PMU driver already.. :/

---

### Post by TheFu on 2015-03-16
I had issues with Xen running directly on physical hardware where it refused to boot after a few kernel updates every year.  That lead me to switch out Xen for KVM, which has **never** had that issue.  At a conference, don't recall which one, someone suggested that Xen support for Debian was not nearly as good as for RHEL/CentOS.

If you don't need Xen for a specific reason, I'd strongly suggest using KVM instead - it is much better supported across all the distros.

I've never tried to run HVM with HVM. I've heard it was possible, but seem like a terrible idea to me.  Does a P6 CPU have VT-x support? It isn't like VMware Workstation will emulate that CPU feature.

---

### Post by sklpr on 2015-03-16
Problem is I definitely need to do this project with XEN as it's for my university :/

These are my PC stats by the way (if they help) :
CPU ---- >Intel Core i7 920 @ 2.67GHz [ Bloomfield 45nm Technology-Socket 1366 LGA]
RAM ---- > 12.0GB Triple-Channel DDR3 @ 532MHz (8-8-8-20)
MOTHERBOARD  ---- > Gigabyte  EX58-UD5 (Socket 1366)

And also I need XEN in order to make an HVM guest after [Ubuntu 12.04 desktop x32bit] and do some work-research on guest VM.. But first I need to get XEN work

So you think this is a hardware related issue (compatibility)? it's XEN - kernel fault ? or it's VMWare's fault? :-/

I just follow the tutorials step-by-step and do the commands.. I ain't doing something wrong like tweaking something that's not mentioned ..
 
1]clean install of Ubuntu server 12.04 with LVM , 
2]apt-get update, 
3]apt-get upgrade,
4]install XEN 
5]reboot and boot to XEN 
6]fail -.-

---

### Post by TheFu on 2015-03-16
The Core i7 920 isn't a bad CPU. It definitely has vt-x support. I have one too.
As said before, I've never tried vt-x within vt-x VMs (VM nesting).

For someone new to virtualization, having 1 hypervisor on the system is the best practice. They can interfere with either other.

I assume this is your setup - 
Windows-something running on the physical hardware
--> VMware Workstation running on Windows
-->--> Ubuntu x64 14.04 with Xen kernel running inside a VM-Workstation VM.
---> --> Client VMs under Xen.

Seems crazy to me. Can't you dual boot with Windows and Ubuntu/Xen directly on the hardware?

BTW, you didn't say why Xen was mandatory. KVM really "just works".

---

### Post by sklpr on 2015-03-16
Yeap!! My setup is like you mentioned :-) 

-Windows 8.1 x64 bit 
--VMware workstation 11
--Ubuntu linux 12.04 server running on VMware workstation 11
---Trying to run XEN and then spawn HVM guest:-P

So I guess I will have to try to make this directly on physical hard drive.. Sounds a bit crazy doing it virtually indeed.. 

I was just trying to do it via VMware and virtually so in case I did something wrong I would just revert to a previous snapshot of my system and everything would be fine !

The reason I want to do it with XEN is that I am doing my Bachelor thesis and it has to be based on XEN .. I want to make whatever is possible trying to install XEN before excluding it and then try something else,
but if things don't work out I believe I will have to find another way and will try out KVM for sure!!  Since I don't own a server - harware to boot XEN.. !

---

### Post by TheFu on 2015-03-16
As much as it pains me to say, perhaps you should try CentOS+Xen first?  I've heard that Xen support on CentOS is much better.

I don't own any "server" hardware either. Server hardware is 
* power sucking
* noisy
* heat making
* expensive both initially and for most upgrades
Been running VMs on C2D and better systems for almost a decade.  Used VMware Workstation in the 1990s, but moved to Unix solutions from 2000 and later. Full-time Linux desktop user beginning in 2007, but started running Linux servers in 1993-ish and had a linux desktop at home from the start. Due to work requirements, I used a Windows desktop mostly from 1995 (win95) until 2007. Before then, I had OS/2 with Win3.x running inside - mainly due to being an IBM subcontractor. Plus OS/2 completely rocked compared to the other alternatives available for home use.

My i7 system (system is from "Shuttle") has a terrible disk subsystem and a blue WD 1TB disk), so while I do run a few VMs on it, they are much slower than average KVM VMs running on C2D and Core i5 boxes with good, fast, storage. Don't have any SSDs on those machines, but if I did, I'd use them for VMs. For me, the $/GB is still not attractive enough for general use of SSDs.

BTW, running server VMs under a desktop OS and desktop hypervisor is fine for play stuff, not for production with 24/7/366 uptime requirements.

---

### Post by sklpr on 2015-03-16
I understand and thank you so much for your replies and for the information you provided me :-) 

So i will try to stick with Ubuntu at start! Install Ubuntu Server 12.04 , and then XEN directly on physical disk and see what happens .. maybe it will work ! I will update the post if it worked!   

If I don't manage to get it to work I will try KVM or even CentOS don't know :P !

---

### Post by tgalati4 on 2015-03-16
Which version of XEN are you using?  It is undergoing active development, so you need to select the OS that the version of XEN was developed under.

Using 10.04 (Hardy) I believe you need to recompile the kernel to get the older XEN to work.

Using 12.04, you might need an older version like 3.4.4 if you want stability.

Using 14.04, you might as well use the latest [4.5]("http://www.xenproject.org/downloads/xen-archives/xen-45-series-1/xen-450-1.html")

Since XEN is a moving target, using it for thesis work may be a challenge.

---

### Post by sklpr on 2015-03-19
I am trying to use XEN 4.1.2 version to work.. fist on Ubuntu 10.04 as you mentioned where i needed to recompile the kernel and I couldn't make it work [I got a blackscreen and nothing happened]

and then on Ubuntu server 12.04 x64 bit ..! but as you can see the above errors  and structure [I mean my system , Windows - > VMware -> bla bla ]! I don't know whats wrong I have to try to install it directly on physical disk !

---

### Post by sklpr on 2015-03-20
***// UPDATE !! ***

Finally i managed to install XEN directly on a external hard drive ! and boot to it ! 

I mean after i follow instructions here : [https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager]("https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager") and i reboot .. 

If i type : *xm list* i get : Domain-0 , ID - > 0 , Mem -> 1024, VCPUS - > 1 ,State - > r and Time ..! or even if i type cat /proc/xen/capabilities i get *control_d* as an output

My question is whether it's okay to use an external hard drive for this ? because when i try to update-grub i get many READ DMA errors [failed command READ DMA to be exact] or even when I am trying to boot to xen [but I finally boot after errors] .. Will I have problems in the future ? not being able to use some of XEN capacilities ? 

This happens because my external drive is connected and booted via usb ? [The hard drive  is old and my motherboard doesn't support SATA I so I have to connect it through USB port and not directly to motherboard..]

Thanks in advance

---

### Post by TheFu on 2015-03-20
eSATA will be fine. USB* not-so-much, but it might work. I wouldn't do it, but that isn't your question.  
USB doesn't have the expected performance and doesn't support DMA. Those are the errors you see.  Even USB3 isn't really good for this - I see queuing issues with USB connections which leads to terrible performance when more than a few processes need to read or write from the device.  USB drives are best for single-use needs .... streaming media, backups, 1 request at a time stuff.  Not running an OS or a VM.

But - if it works well enough for you and any file corruption isn't an issue, fine. Otherwise, get an eSATA card and external dock/array - be certain the eSATA card is compatible with the kernel you want to run - some are not.

To the OS, eSATA is just like SATA. Same bus commands, same performance, slightly different connector, but that's it.  Many motherboards come with eSATA - BTW.  Some esata cards support hot-swapping without an OS reboot, which can be very nice.  I've never bought an add-on eSATA card, so cannot recommend one. A few of my systems have eSATA built-in - actually selected those machines (MB and a laptop) because of the eSATA capability.

---

### Post by sklpr on 2015-03-20
I see ! Thanks very much again for your answers and time ! :-) 

I will try this out

---

