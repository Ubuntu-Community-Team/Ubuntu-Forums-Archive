---
title: "What should I use for a webserver?."
date: 2010-04-30
forum: Virtualisation
---

### Post by sunrex on 2010-04-30
So what type of virtual machine will run a webserver best with the least amount of performance loss?. Xen, OpenVZ, VMWare... etc. I would like to know which one would be the best performance wise and installation wise. The host machine (ubuntu) will be running a desktop as well.

---

### Post by TheFu on 2010-04-30
I hate to say this, but I don't understand your question after reading twice. If you can add some specifics describing what you'd like to do, perhaps?

"webserver" is a little generic. There are lots of different uses for a webserver that impact how you'd like to install and configure it.

"VMware" is a little generic. There are lots of products from VMware used in virtualization. Workstation, Server, ESX, ESXi, Player ... off the top of my head.

This is an Ubuntu forum, so where does CentOS fit? I'm guessing you want to use Ubuntu somewhere, but you mention VMware so I'm confused.

Any use of "performance" probably needs some comparison or alternative.

I'd all like to help, if possible.

---

### Post by sunrex on 2010-04-30
The host will be ubuntu...

---

### Post by TheFu on 2010-04-30
> *"what type should I use for a webserver"*Apache.

---

### Post by sunrex on 2010-04-30
> **TheFu said:**
> Apache.

Please don't act like an idiot, I was talking about what kind of virtual machine, such as Xen.

---

### Post by HermanAB on 2010-05-01
Simple really.  You use the one that happens to work on your hardware.

Apart from working at all, or not at all, there isn't much difference performance wise between virtualizers.

---

### Post by TheFu on 2010-05-01
First, thank you for rewording the original question. I understand now.
I don't think I was acting like an "idiot" - I was just trying to answer your question with the available information.

Ok, onto the real question, as I understand it.

The VM technology that will have the least performance hit or overhead is one that uses paravirtualization.  There are many drawbacks to this technology.  I've used Xen in this mode for a few years and been very happy on 8.04. It appears that 10.04 may not work with Xen, since Ubuntu is pushing KVM/QEMU and libvirt now.  [http://ubuntuforums.org/showthread.php?t=1465767](http://ubuntuforums.org/showthread.php?t=1465767) may become helpful for 10.04 Xen hopefuls.

I think OpenVZ also uses paravirtualization, but I've never used it.

BSD has "jails" which some like to consider a VM technology - I don't.

The other virtualization technologies use hardware virtualization. VMware has a long history of doing this and VirtualBox does as well as KVM/QEMU. I think QEMU may have a paravirtualization capability, but I don't have any experience with it.

If you go with full machine virtualization, the default drivers (disk, network) are usually considered bottlenecks. OTOH, you can run any OS that you like.

With paravirtualization, it is important (if not required) to run the same kernel as the host. Further, the Client OS (DomU in Xen-speak) needs to be modified to support the host virtualization.

Like I said, I've been running Xen 3.2 under Ubuntu 8.04 Server for a few years, but we use all Ubuntu 8.04 DomUs as well. That limits my knowledge on mixing the HostOS and ClientOS between vendors. The xen-create-img command does show examples doing that, I've just never tried it.

I've also used VirtualBox, but only on Windows hosts. It works fine for a desktop, but I don't think it is mature enough to trust for a server. In my use over the last 18 months, it usually wouldn't stay up more than a week before crashing. Then again, that could easily have been the host OS.

If you want to run a Desktop AND virtualization, I'd point you towards KVM and VirtualBox.  I wrote a server virtualization overview article that may also be helpful. [http://jdpfu.com:82/2009/12/22/virtualization-survey-an-overview](http://jdpfu.com:82/2009/12/22/virtualization-survey-an-overview) last year.  Of course, it is from my experiences which may not be helpful at all for a desktop requirement.

BTW, I still think you want to use Apache for your web server. ;)

---

