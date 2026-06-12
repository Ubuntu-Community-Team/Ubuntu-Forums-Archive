---
title: "Virtualization.... what's everyone using?"
date: 2010-08-22
forum: Virtualisation
---

### Post by s1gnAl on 2010-08-22
So here's the deal. I'm not new to virtualization, but some of the newer technologies are foreign to me. 

I've spent the better part of last evening and this morning researching my options and I'd like to hear what people are running on their machines. My planned usage of this server is mainly for test/development, and a few in production servers. 

Here are my requirements:

- Ubuntu or Debian LTS 64 bit (No X, server only)
- Ability to run containers (whether it's LXC or OpenVZ)
- Ability to run tru virtualized machines (I'm thinking KVM will fit the bill here, as long as I can virtualize a windows guest)
- Web based management tools

Now before everyone suggests Proxmox, I am looking to migrate from that platform. I need the ability to more finely tune and control my environment, and Proxmox also has it's fair share of problems. In general, I'm just not a fan of "appliance" type solutions. I prefer to roll my own. 

So far I've looked at Virtualbox (to run in headless mode) and would like to run OpenVZ, but my understanding is that OpenVZ is being actively replaced by LXC so there is no need for kernel patching. 

My ideal solution would be an OpenVZ/Virtualbox setup, and I've found a few awesome control panels for each:

OpenVZ Web Panel - [http://code.google.com/p/ovz-web-panel/](http://code.google.com/p/ovz-web-panel/)
PHP Virtualbox - [http://code.google.com/p/phpvirtualbox/](http://code.google.com/p/phpvirtualbox/)

So I'm looking for other suggestions, what's everyone running that they are satisfied with, in the same type of environment I described above?

---

### Post by danieldbird on 2010-08-22
> **s1gnAl said:**
> So I'm looking for other suggestions, what's everyone running that they are satisfied with, in the same type of environment I described above?

I'm using Ubuntu 10.4, been using Virtualbox for a while now with no problems. Like you i did a fair bit of research before making a decision between Virtualbox and VMWare. The guest additions in Virtualbox is easy to install and allows seamless transition between your vm and host. Hope this helps a little.

---

### Post by cespinal on 2010-08-22
currently running xubuntu as host and xp as guest under virtualbox with 2gb of ram.....feelsgoodman and I just don't know how I didn't use this before...

---

### Post by TheFu on 2010-08-23
Just understand that running more than 1 type of virtualization at a time probably won't work.  I found that purging the old virtualization was the best answer after I was done with it.  
Clearly, some OSes will not work under paravirtual VMs.

---

### Post by TNT1 on 2010-08-23
virtualbox with tinyxp...

---

### Post by Warthaug on 2010-08-23
I'm running virtualbox.  For a newbie it seems to be the easiest to get up and running, and it has all of the features I need.

YMMV

Bryan

---

### Post by pricetech on 2010-08-23
Virtualbox OSE.  I keep thinking I'm going to try the PUEL version, but haven't done so.

---

### Post by TheFu on 2010-08-24
I currently run Xen, ESXi, VirtualBox (both Winx64 and Linux x64 hosts), and have run UML, KVM, QEMU previously.

QEMU required too much hand tweaking for me. That was years ago, however.
KVM was too slow 4 months ago.
Xen has been used in production for over 2 years, extremely stable, except after some kernel updates. For example, the kernel update on 8.04 last week left me with an non-booting Dom0. Further, the update was destructive and didn't backup the prior kernel.
ESXi has been used in production for over 2 years, extremely stable - but not FLOSS. VMware hoops for using it (only Windows clients for managers and forced use of commercial backup methods leave bad taste in my mouth).
VirtualBox - seems stable on Windows hosts, but hasn't stayed up more than 5 days under Ubuntu x64 10.04 OSE for me. Performance is fine. headless works, but doesn't help stability.

My main requirements are:
a) No X/Windows needed on the physical machine, especially during installation. Scripting of VM creation needed.
b) STABILITY. Up times above 90 days needed
c) No custom kernel builds needed. I want 'apt-get update' to handle it.
d) Mix paravirtualization AND HMV on the same physical
e) FLOSS so we can grow into thousands of VMs on hundreds of servers
f) Needs to run Linux AND Windows well. 90% Linux, 9% Windows, 1% "other" OSes
g) Ability to migrate VMs between machines with little hassle; switching between VM technologies would be nice too (VMDK--IMG--VDI--QCOW--QCOW2)
h) Intelligent shared memory across VMs. Basically, a shared CS with different DSs.

So, KVM is the best "checklist" answer today, but it was too slow just a few months ago. I need to check it out again and try to tune it some more. Just got a new lab machine to try this out on. 

I've written in other posts here about these experiences and on my blog, if anyone cares.

---

### Post by kgarbutt on 2010-08-24
Virturalbox as well.

---

### Post by s1gnAl on 2010-08-24
> **TheFu said:**
> I currently run Xen, ESXi, VirtualBox (both Winx64 and Linux x64 hosts), and have run UML, KVM, QEMU previously.

QEMU required too much hand tweaking for me. That was years ago, however.
KVM was too slow 4 months ago.
Xen has been used in production for over 2 years, extremely stable, except after some kernel updates. For example, the kernel update on 8.04 last week left me with an non-booting Dom0. Further, the update was destructive and didn't backup the prior kernel.
ESXi has been used in production for over 2 years, extremely stable - but not FLOSS. VMware hoops for using it (only Windows clients for managers and forced use of commercial backup methods leave bad taste in my mouth).
VirtualBox - seems stable on Windows hosts, but hasn't stayed up more than 5 days under Ubuntu x64 10.04 OSE for me. Performance is fine. headless works, but doesn't help stability.

My main requirements are:
a) No X/Windows needed on the physical machine, especially during installation. Scripting of VM creation needed.
b) STABILITY. Up times above 90 days needed
c) No custom kernel builds needed. I want 'apt-get update' to handle it.
d) Mix paravirtualization AND HMV on the same physical
e) FLOSS so we can grow into thousands of VMs on hundreds of servers
f) Needs to run Linux AND Windows well. 90% Linux, 9% Windows, 1% "other" OSes
g) Ability to migrate VMs between machines with little hassle; switching between VM technologies would be nice too (VMDK--IMG--VDI--QCOW--QCOW2)
h) Intelligent shared memory across VMs. Basically, a shared CS with different DSs.

So, KVM is the best "checklist" answer today, but it was too slow just a few months ago. I need to check it out again and try to tune it some more. Just got a new lab machine to try this out on.

This looks almost exactly like my same set of requirements. Some good answers so far, and the general populace seems to suggest Virtual Box. My only fear with Virtual Box is it's future as a free product (source and price) moving forward with Oracle instead of Sun at the helm. 


> I've written in other posts here about these experiences and on my blog, if anyone cares.

I would very much be interested in your progress and experiences with this moving forward, what's the URL to your blog? 

I have used eSXI and while it's a nice product, I am convinced they hate Mac and Linux users as all of their management tools require Windows, I am strictly Mac and Linux only so that is a real show stopper for me, plus it's just to "appliance" like in nature.

---

### Post by UKBB on 2010-08-24
> **pricetech said:**
> Virtualbox OSE.  I keep thinking I'm going to try the PUEL version, but haven't done so.

What are the advantages with the PUEL version?

---

### Post by s1gnAl on 2010-08-24
> **UKBB said:**
> What are the advantages with the PUEL version?

In a nutshell.... RDP and USB support in the PUEL version vs. VNC only in OSE (for consoles). 

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

EDIT: I've also read that PHPVirtualBox (a nice looking web based front end) will not work with the OSE version, only PUEL.... but I haven't torn into this yet to validate.

---

### Post by s1gnAl on 2010-08-25
Just an update on this... I installed virtual box on my server lastnight running Ubuntu 10.04 64 bit and it's working well so far :) 

The phpvirtualbox app is just plain awesome and was painless to install. I'm still continuing to put everything through it's paces, but so far it's a really nice app. 

[http://code.google.com/p/phpvirtualbox/](http://code.google.com/p/phpvirtualbox/)

---

### Post by TNT1 on 2010-08-25
I just changed from tinyXP to regular XP, still with virtualbox though. TinyXP just required too much effort to get all the drivers loaded.

---

### Post by Groodles on 2010-08-30
I have a Quad-Core box running Deb5.  It runs concurrent 3 VM Guests (Win2k8, Deb5 and Ubuntu10.04) all using bridged networking.  

Last time I checked the uptime it was in excess of 100 days.

Virtualbox is ROCK solid for me.

---

### Post by VcDeveloper on 2010-09-29
> **Groodles said:**
> I have a Quad-Core box running Deb5.  It runs concurrent 3 VM Guests (Win2k8, Deb5 and Ubuntu10.04) all using bridged networking.  

Last time I checked the uptime it was in excess of 100 days.

Virtualbox is ROCK solid for me.

I have a Quad-Core VT system and would like to know if Vbox performs well in production?  I'm undecided between qemu-kvm and Vbox!  I'm getting mixed pros and cons.  I like Vbox easy interface compared to qemu-kvm, but kvm is native to the os.  Is Vbox emulating the host, because if it is, then it will slow down my server.

Any feed back?

---

### Post by VcDeveloper on 2010-09-29
> **VcDeveloper said:**
> I have a Quad-Core VT system and would like to know if Vbox performs well in production?  I'm undecided between qemu-kvm and Vbox!  I'm getting mixed pros and cons.  I like Vbox easy interface compared to qemu-kvm, but kvm is native to the os.  Is Vbox emulating the host, because if it is, then it will slow down my server.

Any feed back?

Nah! Installed Vbox on top of Ubuntu 10.04, created two Ubuntu 9.10 VM's and already I can see the low performance, freezing, delayed and unresponsive reactions.  

With qemu-kvm I virtually had no problems and fast performance.  Even though it's a bit of a pain to setup but the rewards are far more rewarding than Vbox!  Made up my mind to stay with qemu-kvm period!  Native is better!

---

### Post by arunb on 2010-10-02
Ubuntu 10.04 on laptop, VirtualBox running Windows XP, so far no problem, but some USB devices do not work properly on Windows XP

---

### Post by agent8131 on 2010-11-27
VirtualBox on the desktop for development and testing.  Xen on the server.  It's a good mix.  If you wanted to stick to 1 technology  and had the hardware support KVM + virt-manager might be a good way to go.

---

### Post by HermanAB on 2010-11-28
Howdy,

Ubuntu is aimed at home users and for some odd reason home users tend to favour Virtualbox, probably because it is easier to install.  In industry however, it is almost exclusively VMware.  

So if you want to learn something useful that you can put on your CV, then you should use VMware Player, which to my mind works better than Virtualbox anyway.

---

### Post by kpayton on 2010-11-29
Ive used both VirtualBox and VMWare Workstation/Player.

My opinion VirtualBox does everything VMWare will, and obviously it's free. however VmWare I have found to be slower for whatever reason especailly VM Player.

---

### Post by gdahlm on 2010-11-29
We have moved to from esx to xenserver to libvirt+qemu-kvm.

In my opinion ESX is way too expensive and the requirement to use windows as an admin station is limiting.

xenserver worked well but getting the paravirt drivers to work well is difficult and I really dislike how they make tasks like exporting machines to other platforms overly difficult.  It is just a windows gui on top of xen+clvm, it shouldn't be that difficult.

libvirt+qemu-kvm give great performance with the libvirt paravirt drivers and the ability to script machine creation is a huge advantage. lvm2 volumes also enables a massive amount of flexibility and really helps out balancing IO.

On my workstation I use to have virtualbox installed however I have also migrated that instance to kvm, I find using RDP and the remmina client in a full screen session in one gnome workspace is much more efficient for my work flow.

---

