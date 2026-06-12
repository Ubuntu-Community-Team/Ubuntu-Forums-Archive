---
title: "Reasons why I love VMWare"
date: 2009-09-24
forum: Virtualisation
---

### Post by mkotasek on 2009-09-24
Reasons why I love VMware and the many products it provides:

No two setups are the same!  Even if the hardware, OS, software and configurations are the same, VMware never is.  Instead of that g_thread_gettime error you were just getting familiar with, you get the joy of experiencing an all new failing scenario!

VMware is persistent!  If you've ever felt tired, just ready to give up on some failing task don't worry, VMWare will never give up.  It will never get frustrated trying to shut down the non-existent web service, start a list of VMware images that aren't there, or generally any task that you'd expect to time out!

VMware is philosophical!  I've often wondered what came first, the chicken or the egg, but VMWare tries to answer this age old question but requiring the configuration utility to shut down existing services, but the services can't be shut down because they haven't been configured by the utility yet!  Maybe one day you'll get it VMware!

VMware survives anything!  Whether it's the user's attempts to remove it, it's own uninstaller, or other VMware products, it will persist!  Sure, the installer may say it's replacing those old files, but how else could you know the joy of two VMware server instances duking it out on your system?

VMware protects me from awful things!  Even when the installer says everything installed successfully and exits out with a good exit code, it's really just trying to protect me from all those error messages that would totally bum me out in /var/log/* that occurred.  Protect this illusion of success VMware!

VMware keeps me learning! How else could I know to comment out infinite loops, extraneous requirements, and figure what the hell you really are doing under the covers of thousands of lines of bash code.  It lets me keep adding to my resume having to deal with all this!

Speaking of resumes, I get to add VMWare experience as another bullet point in a long list of skills!  It's right next to my 'Agile' development style, my 'six sigma' training and my other 'enterprise' skills.

But best of all, I love that vmware  employs just so many engineers.  If this wasn't the case, my company may be tempted to hire one of these individuals and I could would have to work with that development prowess! Whew, how could anyone compare to that?

---

### Post by darco on 2009-09-24
I didnt read the entire message....but I am a big fan of vmware......just upgraded my kernel to .31 and vmware rebuilt its modules and never skipped a beat! It works great!

darco

---

### Post by SoftwareExplorer on 2009-09-24
Nice use of sarcasm. Dare I ask what you think of VirtualBox?

---

### Post by openfly on 2009-09-25
Heh angry operations guys are the best operations guys... means they are doing their jobs.

---

### Post by __p1n__ on 2009-09-25
A colleage of mine has been doing vmware consulting for the past few years and is making some nice coin at it.

My current preference is xen based upon technical and licensing business drivers (circa Sep'09) but you have to continually reevaluate and not make decisions instinctively on folklore.

---

### Post by bodhi.zazen on 2009-09-25
> **mkotasek said:**
> Reasons why I love VMware and the many products it provides:

I agree with your observations , but I would add, it sounds as if you are running VMWare on an unsupported (host) platform.

If you run vmware on a supported platform some (not all) of your problems will be solved.

Also keep in mind VMWare is not "free" , they give you a demo, ie server, hoping you will then Buy Workstation (or another product).

Personally I have changed over to KVM and OpenVZ (Proxmox).

---

### Post by fjgaude on 2009-09-25
> **darco said:**
> I didnt read the entire message....but I am a big fan of vmware......just upgraded my kernel to .31 and vmware rebuilt its modules and never skipped a beat! It works great!

darco

Wow, I've tried to rebuild vmware server 1.09 for .31 since Alpha 5 with no success... any clues?

---

### Post by darco on 2009-09-26
I previously ran the mainline .30 kernel. I d/l a patch from the vmware forums which rebuilt the modules for that kernel. When I updated to the Karmic .31 kernel, vmware just kicked in on the first startup. Running vmware ws 6.5.3

good luck 
darco

---

### Post by fjgaude on 2009-09-26
Thanks, darco, I'll see if that patch works for me on vmware server.

---

### Post by scorp123 on 2009-09-26
> **mkotasek said:**
> Reasons why I love VMware and the many products it provides:

... lots of sarcasm ...  :lolflag:

I feel you. :D

---

### Post by scorp123 on 2009-09-26
> **bodhi.zazen said:**
> KVM and OpenVZ (Proxmox). Yes, ProxMox is very cool.

---

### Post by mkotasek on 2009-09-29
I think the absolute best part of this whole VMware complaint is that I went to post it originally at the official vmware forums and I encountered a infinite loop of logging in and registering an account on their forums that I couldn't get past.

I think that company was founded to irritate people.

And to those who may be interested, I am still forced to use VMware Server 2.0, because 1.07, which I had working on a few other machines failed to start on this one citing the slightly infamous 'libgio-2.so.0: undefined symbol: g_thread_gettime' error, where additionally the option 'VMWARE_USE_SHIpPED_GTK' doesn't fix the issue because it wasn't shipped with the right libraries anyways apparently.

Nor did 'unset LD_LIBRARY_PATH' fix the issue of the undefined symbol.

I wonder if they test VMware products at all?

---

### Post by chrisjsmith on 2009-09-29
VMware is good.  Forget workstation though - look at the big picture:

We have a HUGE virtual infrastructure setup with a few very hefty VMware ESX hosts and over 100 virtual machines on them.  We have virtual load balancers, virtual routers, virtual switches, virtual caches and virtual web servers.  If something breaks, it just gets moved.  It doesn't go down - ever.  

We can even vmotion one machine from one data center to the other.

We need a new host, we just copy another one and bring it online.  

We get a load spike, we just throw another couple of ESX hosts into the pool and clone some more web servers.

All from the comfort of our bottoms :)

---

### Post by openfly on 2009-09-30
> **chrisjsmith said:**
> VMware is good.  Forget workstation though - look at the big picture:

We have a HUGE virtual infrastructure setup with a few very hefty VMware ESX hosts and over 100 virtual machines on them.  We have virtual load balancers, virtual routers, virtual switches, virtual caches and virtual web servers.  If something breaks, it just gets moved.  It doesn't go down - ever.  

We can even vmotion one machine from one data center to the other.

We need a new host, we just copy another one and bring it online.  

We get a load spike, we just throw another couple of ESX hosts into the pool and clone some more web servers.

All from the comfort of our bottoms :)

All well and good until your cluster loses it's mind and starts failing all the VMs over onto opposing systems all the same time.  =P  Been there done that.

But yeah, nothing is on par with VI4 yet.  Xen could get there eventually, but they aren't there yet.  Critical functionality is missing.

---

