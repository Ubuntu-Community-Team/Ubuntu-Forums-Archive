---
title: "running windows xp on kvm, ubuntu 9.04"
date: 2009-10-13
forum: Virtualisation
---

### Post by pythonscript on 2009-10-13
Does anyone know how (or can point me to a good tutorial) for running Windows XP Professional through KVM on jaunty? This lets me run win xp closer to the hardware than virtualbox, right? I tried googling this but came up kind of short. I won't be viewing the machines over a network, either; I'll just be running and viewing the machines on my laptop. Thanks!  EDIT:  Would xen be better for this? I'm looking for a parallel virtualization solution that's free to run windows and linux concurrently on my hardware. Of course, I want to be able to share my hard disk, stuff like that. Thanks!

---

### Post by sh1ny on 2009-10-14
I've been running Windows 7 and 2008 R2 server on kvm for quite a while. What parts exactly of the whole process are unclear ?

---

### Post by pythonscript on 2009-10-14
I guess I'm unclear on where to begin and set these apps up. If I use xen, is this the same thing as parallel virtualization? I'd like a parallel solution, but if kvm will do this, then that sounds like what I'm after. I'm really new to this aspect of virtualization, so my apologies for my "non-technical" phrasing. Thanks!

---

### Post by roussain on 2009-10-15
I'm more a less a newbie to Ubuntu -- I've got it working on my desktop and it performs just great -- however it takes a lot of steps to get a VM running with Windows XP.   I'd like to install a single windows guest for compatibility reasons -- has anyone written a simple script that automates all the configuration tasks?

---

### Post by wsims2 on 2009-10-15
I followed the guide here [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I've installed 2 windows XP VM's and they run pretty well.

---

### Post by pythonscript on 2009-10-15
> **wsims2 said:**
> I followed the guide here [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I've installed 2 windows XP VM's and they run pretty well.

Could you elaborate on this? Are you running these virtual machines on a server and viewing them from across the network, or running and viewing on the same machine? I'm going to be doing all of this on my laptop, so I'm looking for a one-machine solution. Thanks!

---

### Post by wsims2 on 2009-10-15
I'm running the VM's on a server and viewing them on my laptop.
The guide is relevant to hosting and viewing VM's on the same machine from what i can see. 

If you are using just your laptop, I would highly recommend Virtual Box. I think others have said the same thing. I've never had any problems with virtual box.

I'm not sure which version is in the repos, but i would suggest the latest 3.0.8 version here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by pythonscript on 2009-10-15
I've used virtualbox, but I'm looking for bare hardware virtualization all on my laptop, and virtualbox doesn't satisfy this for me.

---

### Post by wsims2 on 2009-10-15
I'm not sure if KVM meets your requirement of "bare hardware virtualization", but the guide i linked above will work for  machines that both host and view your VM's, including your laptop.

I trust the guide, but I'm going to verify and try it out on my laptop. 

Good luck :)

---

### Post by bmullan on 2009-10-15
I've worked with several of the virtualization technologies and KVM is looking very good.

This article by [Qumranet]("http://www.qumranet.com/files/white_papers/KVM_Whitepaper.pdf") makes apparent some of the inherent benefits of KVM.

fyi for those that aren't familiar... Qumranet was one of the leading KVM development groups and one of the founders had previously led XenSource (which Citrix bought).

Qumranet was recently purchased by Red Hat.   

One interesting sidenote is that Red Hat has stated they will Open Source most or all of Qumranet's SPICE and Solid ICE.. good news if/when it happens.

Solid ICE is the virtual desktop server and controller front end. 

The SPICE protocol (Simple Protocol for Independent Computing Environments) creates a standard connection protocol alternative to RDP for VDI.

Some Red Hat SPICE protocol testing claims:

- video quality (30+ frames per second)
- bi-directional audio and video
  support for IP phones and video for video telephony & video conferencing
- sw only client (akin to NoMachine's NX Web Companion) that automatically install itself via Active-X 
  -- requieres a browser on the client machine

So if SPICE and Solid ICE go Open Source it could become very useful.

---

