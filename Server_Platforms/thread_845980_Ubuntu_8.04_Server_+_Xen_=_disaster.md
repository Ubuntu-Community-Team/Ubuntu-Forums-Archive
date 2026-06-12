---
title: "Ubuntu 8.04 Server + Xen = disaster"
date: 2008-07-01
forum: Server Platforms
---

### Post by nocturn on 2008-07-01
I'm in the process of migrating both from Ubuntu 6.06 to 8.04 Server and from Citadel to Zimbra.

My 8.04 server was a breeze to install and I was very, very impressed by this new version (I gave a positive interview to ZDNet/IT professional- in Dutch - on it too BTW).

My problems started when I wanted to install Zimbra and discovered it could not live alongside my existing ldap and apache processes that were already on that machine.
So, my only option was to resort to virtualisation.  This machine is my home server and it does not have VT technology, so the only options I could see where VMWare and Xen.  VMWare is not Free Software, so that is out of the question.

So, I went ahead and installed Xen, even though it was in universe.  Disaster stuck nearly instantly.  After installing the Xen kernel, the system was rebooted and was unusable.  everything seemed to go in slow motion.
After removing Xen and reinstalling 2 times, it ran nearly normal speedwise.  But it behaves weird.  Some services don't start, my routes are messed up sometimes, the keyboard map is not loaded sometimes.

So, to cut a long story short and from my experience only, Xen is a disaster in Ubuntu.  Which leaves no virtualisation options unless you have VT support (I'm not counting proprietary solutions like VMWare).

Even though I was so impressed with Ubuntu 8.04 as a server, I will now have to switch camps and consider something like CentOS just to be able to run Xen and have Zimbra working.  

Again, I love the progress made in 8.04 Server and I'm still convinced it can be used in production environments, but if you need Xen, it's not a good choice.

---

### Post by windependence on 2008-07-01
> **nocturn said:**
> VMWare is not Free Software, so that is out of the question.



HOLD THE PHONE HERE.

Vmware server IS free and is a great product.


[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

[http://www.vmware.com/download/open_source.html](http://www.vmware.com/download/open_source.html)

I have been running it for over a year now with production web sites on VMs.

-Tim

---

### Post by nocturn on 2008-07-01
> **windependence said:**
> HOLD THE PHONE HERE.

Vmware server IS free and is a great product.


[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

[http://www.vmware.com/download/open_source.html](http://www.vmware.com/download/open_source.html)

I have been running it for over a year now with production web sites on VMs.

-Tim

VmWare server is free as in beer.  It's not Free Software (like Linux) nor is the source code available.
Xen, in contrast, is a Free Software project.

---

### Post by windependence on 2008-07-01
OK, I'm sorry you are a purist. While I agree with your ideals, in practice, it's just not feasible that everything be free and open.

Good luck!

-Tim

---

### Post by nocturn on 2008-07-01
> **windependence said:**
> OK, I'm sorry you are a purist. While I agree with your ideals, in practice, it's just not feasible that everything be free and open.

Good luck!

-Tim

Thanks.
I'm a purist at home.  If a client wants VMWare, I'm okay with that.  If I have to use closed software (as in no open alternative), I will.

But Xen works at least as well as VMWare and it's Free/open.  CentOS supports it very, very well.

Though I would have preferred to keep running my Ubuntu server, was one of the first users of this product.

---

### Post by AnRa on 2008-07-01
You should take look at VirtualBox :)

---

### Post by nocturn on 2008-07-01
> **AnRa said:**
> You should take look at VirtualBox :)

VirtualBox is nice, but it's a desktop virtualisation project (like vmware workstation).  It's not suitable for server use AFAIK.

I'm a bit disappointed that the Xen way turned out like this.  It's a really great virtualisation environment on Linux (with little overhead) and it's completely Free.

---

### Post by windependence on 2008-07-01
I agree with your assesment of vitual box. All these other virtualization technologies has some kind of drawback whether it be hardware not supported, no support for 64 bit, etc. That's why for most of my virtualization I use VMware server. How long it will remain free is certainly a question. I am concerned also about Xen. Since Xen has been purchased by Citrix, I am very dissappointed as they are not known to make anything free or even affordable for the small to medium business, and IMHO they are in bed with M$.

A few things held me back from Xen, one being the CD support sucks, and it just didn't seem as mature as VMware. I hope they keep it free as well as VMware, but with the sudden popularity of Virtualization, I am skeptical. One good thing about Xen is that Red Hat and CentOS have it compiled into the kernel so at least they may fork a version if Citrix should make it not free. I have a CentOS box and I have to say I am very pleased with it.

-Tim

---

### Post by nocturn on 2008-07-01
> **windependence said:**
> I agree with your assesment of vitual box. All these other virtualization technologies has some kind of drawback whether it be hardware not supported, no support for 64 bit, etc. That's why for most of my virtualization I use VMware server. How long it will remain free is certainly a question. I am concerned also about Xen. Since Xen has been purchased by Citrix, I am very dissappointed as they are not known to make anything free or even affordable for the small to medium business, and IMHO they are in bed with M$.

A few things held me back from Xen, one being the CD support sucks, and it just didn't seem as mature as VMware. I hope they keep it free as well as VMware, but with the sudden popularity of Virtualization, I am skeptical. One good thing about Xen is that Red Hat and CentOS have it compiled into the kernel so at least they may fork a version if Citrix should make it not free. I have a CentOS box and I have to say I am very pleased with it.

-Tim

I'm worried about Xen a bit too, but it's GPL'ed so Citrix couldn't close it if they wanted too.  It's still the best option we have (besides hardware virtualisation like KVM) at a community based project.

---

### Post by camccall on 2008-07-01
Thanks for the info, I actually was considering installing xen on my own 8.04 server.  Just a quick question, had you installed xen previously or was this your first attempt?  

I have used Xen for some experimentation a few times and was really impressed.  I had some networking issues but it turned out to be just a dumb mistake involving modules and not the fault of the hypervisor.  Maybe I will give it a try and post my results.

---

### Post by nocturn on 2008-07-01
> **camccall said:**
> Thanks for the info, I actually was considering installing xen on my own 8.04 server.  Just a quick question, had you installed xen previously or was this your first attempt?  

I have used Xen for some experimentation a few times and was really impressed.  I had some networking issues but it turned out to be just a dumb mistake involving modules and not the fault of the hypervisor.  Maybe I will give it a try and post my results.

This was my first try on Ubuntu.  I use it daily on RHEL and CentOS.

---

### Post by camccall on 2008-07-01
I thought that was most likely the case.  Thanks for the info.

---

### Post by AnRa on 2008-07-03
> **nocturn said:**
> VirtualBox is nice, but it's a desktop virtualisation project (like vmware workstation).  It's not suitable for server use AFAIK.Maybe this isn't what you are looking for, but you may run VirtualBox in "headless mode". :)

---

### Post by nocturn on 2008-07-03
> **AnRa said:**
> Maybe this isn't what you are looking for, but you may run VirtualBox in "headless mode". :)

Thanks.  I'm now running Xen on CentOS.  Zimbra is a bit top heavy though...

---

### Post by Seq on 2008-07-03
> **nocturn said:**
> This was my first try on Ubuntu.  I use it daily on RHEL and CentOS.

I am actually looking at virtualization products for my home server (Work unfortunately has a single-provider-when-possible policy, so I can't use anything like xen there).

I thought I'd chime in with two more projects worth following.

[oVirt]("http://ovirt.org/") is a project from Red Hat to create clusters of xen servers supporting live migration, etc. It looks promising, but it is still essentially beta quality, based on xen (+fedora dom0), and seems to require a dedicated management node. This is probably going to be Red Hat's next big product.

[Virt-Manager]("http://virt-manager.et.redhat.com/"), which is also in Ubuntu, allows administration of Virtual Machines on remote hosts using xen, kvm, or qemu. The neat thing here is that you could use qemu to virtualize non x86 environments. It seems to allow remote VM creation and configuration.

Also, I should add that what turned me off of xen at home is the lack of cpu frequency scaling in the xen kernel. My server sits idle 95% of the time, so it would be nice to have it go into a lower power mode.

---

### Post by mindwarp on 2008-07-24
Sorry for the unhelpful replies you received earlier in this thread, but Xen on Ubuntu works great.  If you need a reference point:

[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

---

### Post by windependence on 2008-07-24
Good news! VMware is GIVING AWAY it's hypervisor after July 28th. 

[http://www.eweek.com/c/a/Infrastructure/VMwares-ESXi-Hypervisor-for-Free/?kc=EWWHNEMNL072408STR1](http://www.eweek.com/c/a/Infrastructure/VMwares-ESXi-Hypervisor-for-Free/?kc=EWWHNEMNL072408STR1)

Nope, it's not open source but it IS free and will allow you to run various OSs on one piece of hardware as it does now.

-Tim

---

