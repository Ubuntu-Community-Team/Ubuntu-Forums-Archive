---
title: "Best OS variant for a Java virtual appliance??"
date: 2008-07-17
forum: Server Platforms
---

### Post by boraxx on 2008-07-17
I'm hoping to get some expert advice for the next step in my project.

Over the last year, I've built a 10-computer cluster, distributed over 3 location in the U.S., connected through a VPN. Each computer runs under a separate instance of an operating system. They are all working together day and night crunching numbers to solve various quantum mechanics problems. The project started out on a single Windows XP box, and now consists of 3 MacBooks and 7 Ubuntu boxes. The macBooks are used for development (Eclipse) and the GUI (Eclipse RCP)for our distrubuted application. The Ubuntu boxes run a .jar. 

What I want to do next is to increase our cluster size to about 100 computers. I'd like the Ubuntu boxes running the .jar program to run a minimum OS, and the computer itself should consist of no more hardware than necessary. 

My main question is what OS variant would you suggest? I just need to be able to ssh into the machine, and be able to run a .jar (which I know how to do already). A monitor will not be connected to these boxes, and they will be controlled remotely. I've looked at Ubuntu server addition, Xubuntu, and Ubuntu JeOS so far. JeOS seems to be the most minimal OS, but I'm not sure if it will support running .jars, or if it supports 64-bit CPU architectures. Any suggestions or experience with this??

Also, concerning the hardware. I'd like to build several very minimally equipped boxes. They just need a fast 64-bit AMD processor, 512 MB RAM, and LAN. I don't need them to have an optical drive or even USB ports if I can install Ubuntu over the network. The box should be small and perhaps rack mountable. Any suggestions?

Thanks much, Boraxx

---

### Post by windependence on 2008-07-17
JeOS would be my choice. As long as you can run the Java run time on the machine, any OS will work if it supports Java. JeOS is very small, and efficient and that is why it was developed.

If I was going to do this on the scale you are talking about, I would probably run some form of *BSD. Both 32 and 64 bit guests work great in a VM with BSD.

-Tim

---

### Post by gekkio on 2008-07-19
AFAIK the differences between JeOS vs Server edition are
- JeOS installs -virtual kernel, Server edition install a -server kernel
- The virtual kernel is meant for running Ubuntu as a client OS in a virtualized environment
- The server kernel is meant for running Ubuntu as a OS without a virtualization (or as a host OS in virtualized environment)
- JeOS installs less packages than Server edition, but the difference is not that great and you'll probably end installing most of them anyway

And please note that JeOS is 32-bit only. (It makes sense because 64-bit virtualized guests are quite rare).
But if you have only 512 MB ram on the computer, it doesn't really matter, you won't benefit from 64-bit much anyway.

None of the editions have Java support installed by default, but you'll just have to install one package to enable it (same applies to the SSH server).

If I understood correctly, you aren't actually even using virtualization (VMWare products, KVM, Xen, etc..), so I'd go for Ubuntu Server edition. You can remove unneeded packages to make it slightly slimmer but I don't think that will affect performance much.

Virtualization could be useful though...for example you could buy a rack server with 2x Quad-Core processors and 4 GB RAM.
With those specs you could have 8 virtual machines (one core and 512 MB RAM per a virtual server) per a physical server (1U rack size). The physical server would run Server edition, the virtual ones JeOS.

If you are really sure that you can have the server at 100% load all the time (with my 2x Quad-Core example that would mean 8 cores at 100% load!!), you won't be needing virtualization. Your Java program has to be multithreaded and very well programmed or else it won't take advantage of multiple cores fully.

One more thing: if you want rack mountable servers, I recommend to get them with high specs to make good use of the physical space required. Having a slow 1U server is a waste of space, especially if you intend to build a cluster of ~100 servers.

Well, that's my 2 cents, hope it helps. :)

---

### Post by windependence on 2008-07-19
> **gekkio said:**
> 

And please note that JeOS is 32-bit only. (It makes sense because 64-bit virtualized guests are quite rare).
But if you have only 512 MB ram on the computer, it doesn't really matter, you won't benefit from 64-bit much anyway.

All my VM guests are 64 bit FreeBSD. Agreed that you may not benefit from it though, especially if you are not running 4 gig of RAM on each guest which is rarely necessary.



> **gekkio said:**
> Virtualization could be useful though...for example you could buy a rack server with 2x Quad-Core processors and 4 GB RAM.
With those specs you could have 8 virtual machines (one core and 512 MB RAM per a virtual server) per a physical server (1U rack size). The physical server would run Server edition, the virtual ones JeOS.

If you are really sure that you can have the server at 100% load all the time (with my 2x Quad-Core example that would mean 8 cores at 100% load!!), you won't be needing virtualization. Your Java program has to be multithreaded and very well programmed or else it won't take advantage of multiple cores fully.



You don't quite fully understand how virtualization works. You can run more machines than cores, and in fact this is done regularly. the scheduler on the host OS takes care of scheduling CPU time for each VM, so that when one is idle, that CPU can be used for the others. I would probably not run a VM with 512K RAM unless it was a very light  load server though. Also, just because you have a VM set up doesn't mean it will consume 100% of one core, far from it in most cases. 

I certainly think Ubuntu Server for the host and JeOS for the guests would be the hot ticket here.

-Tim

---

### Post by gekkio on 2008-07-20
> **windependence said:**
> 
You don't quite fully understand how virtualization works. You can run more machines than cores, and in fact this is done regularly. the scheduler on the host OS takes care of scheduling CPU time for each VM, so that when one is idle, that CPU can be used for the others. I would probably not run a VM with 512K RAM unless it was a very light  load server though. Also, just because you have a VM set up doesn't mean it will consume 100% of one core, far from it in most cases. 

Sorry, I failed to make my point clear enough. :)
What I meant that assuming you have a single-threaded program that will completely saturate one cpu core with 100% usage, you'll need at least as many VMs as you have cores to fully saturate a multi-core system. Naturally having more VMs will more likely get you 100% usage for the processor(s). (For example I'm running a test system with a dual-core host and three dual-core guest VMs. So practically I'm dividing a dual-core processor into six virtual cores to get as high cpu utilization as possible)

Anyway, thanks for the clarification.
And I totally agree with you on what you said about the VM memory amount. Having more memory might even speed up things a lot. Some Java programs (for example ECM systems such as Alfresco) will happily eat up all the memory you give it and speed things up (this especially applies to programs that cache a lot of stuff in memory). This depends entirely on the application, but even if the application doesn't directly benefit from more memory, having more memory for the OS is always good (->larger buffers and caches are at least good for disk IO sensitive applications).

---

### Post by sadara on 2008-07-20
I assume your problem is embarising parrelel, so my first question is how much RAM does each worker thread need/want?

There are better distributions targeted at what you need. If you don't mind spending ~ 40 man hous I would suggest using linuxfromscratch.org to build your own. If you want something smaller try buildroot from the uClibc project. If your chasing a complete distro try Rocks Cluster.

Finally, if you are planning on purchasing new equiptment, don't buy single cpu computers. Carefully weight the $/ghz of the complete system, not just the motherboard/cpu/ram. Include the cost of switches/racks/Aircondictioning etc, and finally electrical requirements. A P4 system is more expencive if you are planning on using it for more than 12 months than a Dual Quad core harpertown.

---

### Post by windependence on 2008-07-21
> **sadara said:**
> 
There are better distributions targeted at what you need. If you don't mind spending ~ 40 man hous I would suggest using linuxfromscratch.org to build your own. If you want something smaller try buildroot from the uClibc project. If your chasing a complete distro try Rocks Cluster.


Agreed, in fact if it was me, I'd run FreeBSD on my VMs. I mean, if you're gonna put him through that much trouble, *BSD at least doesn't need to be built from scratch, but apps can be compiled from source for bare metal performance.

-Tim

---

### Post by boraxx on 2008-07-21
Thanks a lot for your great advice - much appreciated. Those were definitely the answers I was hoping to get from someone with expertise in this area.

THANK YOU!

---

