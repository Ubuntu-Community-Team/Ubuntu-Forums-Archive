---
title: "Virutualization: What's the deal"
date: 2007-11-27
forum: Virtualisation
---

### Post by TorchlightJay on 2007-11-27
Okay, this is the dumbest question you may have ever heard but I figured I'd ask Ubuntu fanatics since you'd know. What's the deal with virtualization? Like I understand the basic ideas with virtualbox and VMware and I have installed a virtual Windows XP on my ubuntu desktop. I once read that virtualization is something that all IT people need to learn and I was wondering, what are the overall capabilities of virtualization? 

Like I am sure there must be more than being able to run Windows on your Linux box. Like in terms of server virtualization or whatever. What are the overal capabilities of virtualization, what doors does it open up? I am just curious, I know dumb question. 

Also, if you can tag this into it, what is the best virtualization tool for Ubuntu Linux or Linux in general. I know there is VMware, Virtualbox, KVM in the kernel, Xen, etc, which one is the best do y'all think? I'll probably have more virtualization questions as time progresses but I just wanted to get this out of the way. Thanks all.

---

### Post by omegamike3 on 2007-11-27
As an example, virtualization is great for developers. They can jump from one system to the next for testing without having to invest in multiple physical machines. I will give the obligatory Wikipedia link:
[http://en.wikipedia.org/wiki/Virtualization]("http://en.wikipedia.org/wiki/Virtualization")

---

### Post by peabody on 2007-11-27
As someone else already said, virtualization is a holy grail for development testing.  It's extremely convenient to be able to run an OS in its own sandbox to test for bugs.  I'm doing that now to chase down a problem with hal and gnome-power-manager.  But there are even better uses than that.  Consumers can use virtual machines to sandbox their applications to prevent them from ruining the host OS and snapshots of a guest OS can be taken at any time so you can revert to EXACTLY the way the OS was before a particular event.  It makes it easy and convenient to try out the hundreds of different Linux distributions without having to zap your operating system everytime.  The list goes on and on.

---

### Post by bodhi.zazen on 2007-11-27
The two big ones are development (as has been mentioned) but also servers.

One can consolidate servers, isolate services (server) from the main OS, and increase security.

See something like this for example : [http://www.swsoft.com/en/products/virtuozzo/](http://www.swsoft.com/en/products/virtuozzo/)

---

### Post by TorchlightJay on 2007-11-27
Sounds cool. I have a question. What are the limits to virtualization. I mean there must be some limit because it's not the exact hardware installation. Maybe there's not and I am wrong. When I use Virtualbox, I have a hard time doing certain things when I virtualize windows (like things involving opengl for example). Are there any limits? Also I watched a video on youtube talking about how you install like VMware on the machine and then install operating systems. Can you install some kind of virtual middleware or something on the hardware and then install virtual machines and OSes or do we install some OS and then install the virtual machines? I hope I make sense. Thanks.

---

### Post by bodhi.zazen on 2007-11-27
The limitations depend on what you are virtualizing with. Limitations come from the virtualization program itself and on the hardware emulated. 

When you install in say VMWare/VBox/Qemu you are using virtual hardware and not directly using your videocard for example.

So, you will have limited graphics capabilities (you can not get the 3D effects of compiz on a virtual machine for example).

---

### Post by TorchlightJay on 2007-11-27
makes sense. So I want to setup a virtual server. The server I have is not using all it's CPU capabilites and I am sure I can mod it enough to where it'll be a decent virtual server. Is it possible to run five virtual servers with five different IP addresses? My ISP gave me five ISPs and I've been trying to figure out how to firewall all of them and also use one for DHCP and the rest for whatever else (MySQL server, Apache Server, LDAP server, etc.) I think this may be a solution, any ideas?

---

### Post by peabody on 2007-11-27
Virtualization is certainly a solution for you if you don't mind having all of your eggs in one basket (machine).  You could basically have all five machines be virtual machines via some kind of virtualization software such as vmware, virtualbox, xen, openvz, etc, etc. that would work just fine.

---

### Post by TorchlightJay on 2007-11-28
kewl, now is it necessary for me to install an operating system, then install the virtualization software then the virtual machines or is there a way to bypass the operating system process? Just seems pointless to install the OS if you don't have to. Once that is done, just plug in the server and create say 6 virtual machines one with each IP and a firewal and I'll be good to go? This is all theory of course. Maybe it'd be better to make a firewall and not virtualize it. Oh well, first I need to figure out if I need to install an initial OS in order to utilize virtual machines or if there is special software. Thanks

---

