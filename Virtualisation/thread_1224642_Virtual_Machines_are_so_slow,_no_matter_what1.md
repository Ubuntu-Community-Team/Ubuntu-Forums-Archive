---
title: "Virtual Machines are so slow, no matter what1"
date: 2009-07-27
forum: Virtualisation
---

### Post by jocampo on 2009-07-27
Hello guys

Well ... my question is really simple... I've been trying to run Virtual Box on top of Ubuntu Server (1st I tried Hardy now Jaunty) and no matter what ... feels slow. I have 2GB of RAM, 7200rpm disk with Pentium 4 processor, 2.8Ghz. It is not a super fast machine, but should do the trick. I don't know what else should I do. Should I invest on a better machine and if that's my only option, can I buy something decent (used or new) for about $600.00 ? I checked online and found this website: [http://system76.com/]("http://system76.com/") They sell nice servers for about that with Intel Virtualization technology.

Any comment, suggestion? ... by the way, my current processor does not support Virtualization ...

Thanks in advance,

---

### Post by jocampo on 2009-07-27
bump!

no one with a sugggestion? :-)

---

### Post by stlsaint on 2009-07-27
well i have a intel centrino duo core with a nvidia 8400gt with 2gb ram...and i run virtual machines with xp and ubuntu and i too have problems with my v-pc desktop...its just the fact that its a virtual machine and not a real system...your sharing all your resources with that virtual machine...ever try running two virtual machines at the same time along with the host os...not pretty!!! not pretty at all!

---

### Post by philcamlin on 2009-07-27
> **stlsaint said:**
> well i have a intel centrino duo core with a nvidia 8400gt with 2gb ram...and i run virtual machines with xp and ubuntu and i too have problems with my v-pc desktop...its just the fact that its a virtual machine and not a real system...your sharing all your resources with that virtual machine...ever try running two virtual machines at the same time along with the host os...not pretty!!! not pretty at all!

+1 vm's arent suposed to be pretty theyr suposed to give you capability 

i use vm to sync my iphone

its slow as crap but it gets the job done :)

---

### Post by gk_manutd on 2009-09-07
> **jocampo said:**
> 

I've been trying to run Virtual Box on top of Ubuntu Server (1st I tried Hardy now Jaunty) and no matter what ... feels slow. 

I don't know what else should I do. Should I invest on a better machine and if that's my only option

Any comment, suggestion? ... by the way, my current processor does not support Virtualization ...




Well... the thing is... a Virtual Box will ALWAYS be slow... because it opts for FULL virtualization...

You do have another option... It is a paravirtualization technology called XEN. This is a hypervisor that will give you almost NEAR-NATIVE LINUX PERFORMANCE. That means that you can run your 'Virtual Machine image' almost as fast as it would when installed on a REAL CPU. Seriously!

Besides... Xen is made for an uncooperative (READ-   x86) architecture... so it is the worst case... no virtualization support...

The only catch is that I think Jaunty does not support Xen as a dom0 host- meaning it is either difficult/impossible to install a Xen server on Jaunty. 

I've been scavenging the globe (READ- Google) for a definitive guide.. and I've come up with ZILCH so far...

Anyway... this is a really old thread...

If you DO read this... and decide to act upon it... it'd be gr8... 

Chee.. I'd really like to run Xen... It hurts that Fedora has inbuilt support for XEN.. and my dear Ubuntu doesn't! 

Like I said... if you manage to get Xen up and running... please leave some instructions as how to go about doing it! 

Hope that helps... and thanks in advance!

---

### Post by jocampo on 2009-09-07
Well, old thread but lot of things have happened since then ;-) ...

1st, made some tweaks on that Headless server and they do not run so slow anymore. Planning to upgrade up to 4GB but so far is still running; my apache webserver is there as a virtual machine, an Ubuntu server also.

Couple of days ago I was unlucky (or lucky? lol) and the hard drive of my old laptop died. So, got a new one with a CPU which supports virtualization technology. Is running Windows 2003 Enterprise 64bit with Oracle inside and works ok in my opinion. Still I got some questions and doubts about AMD-V and its integration with VirtualBox (log says is not enable but GUI says it is, see another thread here about it) but I am happy with the new purchase.

---

### Post by VMSandman on 2009-09-10
AMD were at VMworld this year sporting a lot of cool buzz around their hardware support for virtualization. Some great new stuff coming out too!

---

### Post by Zhwazi on 2009-09-11
> **gk_manutd said:**
> Well... the thing is... a Virtual Box will ALWAYS be slow... because it opts for FULL virtualization...

You do have another option... It is a paravirtualization technology called XEN. This is a hypervisor that will give you almost NEAR-NATIVE LINUX PERFORMANCE. That means that you can run your 'Virtual Machine image' almost as fast as it would when installed on a REAL CPU. Seriously!

Besides... Xen is made for an uncooperative (READ-   x86) architecture... so it is the worst case... no virtualization support...

The only catch is that I think Jaunty does not support Xen as a dom0 host- meaning it is either difficult/impossible to install a Xen server on Jaunty. 

I've been scavenging the globe (READ- Google) for a definitive guide.. and I've come up with ZILCH so far...

Anyway... this is a really old thread...

If you DO read this... and decide to act upon it... it'd be gr8... 

Chee.. I'd really like to run Xen... It hurts that Fedora has inbuilt support for XEN.. and my dear Ubuntu doesn't! 

Like I said... if you manage to get Xen up and running... please leave some instructions as how to go about doing it! 

Hope that helps... and thanks in advance!
Paravirtualization requires modifications to the OS, and is unsuitable for running most operating systems stock configuration.

If you want virtualization for reasons of security and compartmentalization, going with OS-level virtualization like Solaris Zones or FreeBSD Jails would give you good performance. I think Linux has something equivalent but I don't know what it's called. Using Xen consumes memory and CPU time on the additional hypervisor and kernels, while Zones and Jails use the same kernel.

If you want to tinker with obscure operating systems, you don't need good performance, and they probably don't have paravirtualization-compatible kernels. Most of the time it's probably an OS you wouldn't run natively on that system and would run on an old Pentium III box if you have one.

If you need a compatibility layer to get Windows programs to run, well, last I checked Windows doesn't support paravirtualization. If you're not using a PV-capable kernel, then you might as well just be running it in Virtualbox.

Edit: In all of these cases you have multiple OS instances running on the same CPU, it won't be fast. It may be less egregiously slow, but three OS instances on a Core 2 Duo will not perform like 3 OSes on 3 separate Core 2 Duos. This should be obvious but I just want to make sure.

---

### Post by fjgaude on 2009-09-11
My understanding is there are two ways doing these virtuals, one is about half speed (VMware, VirtualBox) and the other is 90-95% speed (XEN). Take your choice.

---

### Post by Zhwazi on 2009-09-11
> **fjgaude said:**
> My understanding is there are two ways doing these virtuals, one is about half speed (VMware, VirtualBox) and the other is 90-95% speed (XEN). Take your choice.

You don't always have a choice, you need a PV-supporting kernel or Xen will just run that OS in a heavyweight VM.

---

### Post by fjgaude on 2009-09-11
Of course what you say is true. Thanks!

---

### Post by rliegh on 2009-09-11
> **fjgaude said:**
> My understanding is there are two ways doing these virtuals, one is about half speed (VMware, VirtualBox) and the other is 90-95% speed (XEN). Take your choice.

It's my understanding that XEN is only 90-95% speed on OS's that have modified kernels. If you're using it to run something such as Windows, you're right back to half-speed along with VMWare and VirtualBox.

---

### Post by aesis05401 on 2009-09-11
> **Zhwazi said:**
> *snip*... If you want virtualization for reasons of security and compartmentalization, going with OS-level virtualization like Solaris Zones or FreeBSD Jails would give you good performance. I think Linux has something equivalent but I don't know what it's called. Using Xen consumes memory and CPU time on the additional hypervisor and kernels, while Zones and Jails use the same kernel. *snip*...

The LinuxFromScratch stable book teaches how to use root jails on Linux.  It takes a lot of time to set up and maintain a system like that, but it is well worth the effort as a learning experience.  I found the project to be worth the effort even though I am no longer running straight jail based execution separation.

Jails probably don't stack up to what most users are hoping for when they are looking for virtualization information, though.  It is way too hands on.

---

### Post by Zhwazi on 2009-09-11
> **aesis05401 said:**
> The LinuxFromScratch stable book teaches how to use root jails on Linux.  It takes a lot of time to set up and maintain a system like that, but it is well worth the effort as a learning experience.  I found the project to be worth the effort even though I am no longer running straight jail based execution separation.

Jails probably don't stack up to what most users are hoping for when they are looking for virtualization information, though.  It is way too hands on.

Chroot jails or root jails? A chroot jail doesn't provide nearly the same degree of isolation as the jails impemented in FreeBSD and Solaris, which each have their own process ID space and IP address, which chroot does not do, although I'm not familiar with the term "root jail" a quick googling suggests it's most likely another word for chroot jail.

It is more than most people asking questions here are going to want to get into though, you're right about that.

---

### Post by aesis05401 on 2009-09-11
> **Zhwazi said:**
> Chroot jails or root jails? A chroot jail doesn't provide nearly the same degree of isolation as the jails impemented in FreeBSD and Solaris, which each have their own process ID space and IP address, which chroot does not do, although I'm not familiar with the term "root jail" a quick googling suggests it's most likely another word for chroot jail.

It is more than most people asking questions here are going to want to get into though, you're right about that.

Chroot jails is what I am familiar with, but you can use LSM (Linux Security Modules) to implement BSD jails on Linux.

You make good points about jail differences - I probably should have mentioned that Linux based chroot jails are not designed to contain root authenticated activity.. Within the context of exposing services/shell environments for specific non-root activity chroot jails work really well.  So the ability to compartmentalize is clearly not as granular with Linux chroot as with the other systems.  It still works really well when configured properly :)

The only time I know of that a chroot jail should be hosting root level activity is when you want multiple bootable environments on the same partition.

Anyhow, good points to consider.

---

### Post by gk_manutd on 2009-09-12
> **Zhwazi said:**
> 
If you need a compatibility layer to get Windows programs to run, well, last I checked Windows doesn't support paravirtualization. If you're not using a PV-capable kernel, then you might as well just be running it in Virtualbox.

This should be obvious but I just want to make sure.

Nopes :)  I don't wnat it for Windows.... I wanted Fedora to get some non-Ubuntu-type work done (READ: Need to have a RHEL system- nothing else will do)... and I was reluctant to partition my /home ... wanted to run Fedora on Jaunty (didn't feel like letting go)... 
so decided to try XEN.  

Thanks anyway though!

---

### Post by __p1n__ on 2009-09-13
Try running a Type-1 VMM configuration.  I think that the mistake is using ubuntu as the dom0.  IMHO NetBSD makes for a more minimal and robust dom0 and ubuntu will run perfectly as a domu.

Don't forget to setup vcpu's as well. Assign 1 or 2 hyperthreads to the dom0 vcpu and the rest to the domu vcpu.

I'm currently running kubuntu 8.04 (domu) / NetBSD 5.1 (dom0) / Xen 3.4.1 in hardware virtualization.  The performance of the kubuntu instance is not noticably slow at all.

---

### Post by inportb on 2009-09-13
> **Zhwazi said:**
> If you want virtualization for reasons of security and compartmentalization, going with OS-level virtualization like Solaris Zones or FreeBSD Jails would give you good performance. I think Linux has something equivalent but I don't know what it's called. Using Xen consumes memory and CPU time on the additional hypervisor and kernels, while Zones and Jails use the same kernel.

Chroot is awesome, but OpenVZ is ftw. I'd take OpenVZ over Xen for running a virtual Linux server.

---

### Post by Zhwazi on 2009-09-14
> **inportb said:**
> Chroot is awesome, but OpenVZ is ftw. I'd take OpenVZ over Xen for running a virtual Linux server.

I wasn't talking about chroot. :P

---

