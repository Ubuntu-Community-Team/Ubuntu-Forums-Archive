---
title: "KVM vs VMware vs Xen?"
date: 2007-04-30
forum: Server Platforms
---

### Post by meheheh on 2007-04-30
Since all three are free, which one is better in terms of stability and speed?

---

### Post by jiminycricket on 2007-04-30
There are some benchmarks here: [http://linuxvirtualization.com/](http://linuxvirtualization.com/) [http://www.phoronix.com/scan.php?page=article&item=623&num=4](http://www.phoronix.com/scan.php?page=article&item=623&num=4) [http://weblog.infoworld.com/virtualization/archives/2006/09/problems_instal.html](http://weblog.infoworld.com/virtualization/archives/2006/09/problems_instal.html) [http://linux.inet.hr/finally-user-friendly-virtualization-for-linux.html](http://linux.inet.hr/finally-user-friendly-virtualization-for-linux.html)


KVM is rapidly improving though, some of these 'marks are old.

Also there's qemu/kqemu accelerator/qemu-launcher and virtualbox to add to the list

Xen and VMWare ESX (if using VMI, I think) are paravirtualizers.  KVM requires hardware support, which is in most modern chips sold recently.

---

### Post by David Brown on 2007-04-30
Does anyone know the status of Linux VServer and/or openvz on feisty?  As far as I can see, the tools are available, but the kernel patches have not been updated for feisty.  These are both lighter and faster virtualisation solutions (albeit less isolated than kvm, vmware and xen).

---

### Post by meheheh on 2007-04-30
> **jiminycricket said:**
> There are some benchmarks here: [http://linuxvirtualization.com/](http://linuxvirtualization.com/) [http://www.phoronix.com/scan.php?page=article&item=623&num=4](http://www.phoronix.com/scan.php?page=article&item=623&num=4) [http://weblog.infoworld.com/virtualization/archives/2006/09/problems_instal.html](http://weblog.infoworld.com/virtualization/archives/2006/09/problems_instal.html) [http://linux.inet.hr/finally-user-friendly-virtualization-for-linux.html](http://linux.inet.hr/finally-user-friendly-virtualization-for-linux.html)


KVM is rapidly improving though, some of these 'marks are old.

Also there's qemu/kqemu accelerator/qemu-launcher and virtualbox to add to the list

Xen and VMWare ESX (if using VMI, I think) are paravirtualizers.  KVM requires hardware support, which is in most modern chips sold recently.Yeah, I've got VT.... because I'm getting a new server (Dell PowerEdge 860) with a Xeon 3060. I wonder if I would want SMP guests though... I guess I'll have to do my SMP tasks outside of virtualization if I chose to use KVM.

OpenVZ looks interesting. I'll look more closely when I have the time.

---

### Post by havenonick on 2007-04-30
> **meheheh said:**
> Yeah, I've got VT.... because I'm getting a new server (Dell PowerEdge 860) with a Xeon 3060. I wonder if I would want SMP guests though... I guess I'll have to do my SMP tasks outside of virtualization if I chose to use KVM.

OpenVZ looks interesting. I'll look more closely when I have the time.

Dont forget that intels VT needs bios support while AMDs doesn't ;)
having a intel cpu supporting VT isn't everything!

---

### Post by David Brown on 2007-04-30
> **meheheh said:**
> Yeah, I've got VT.... because I'm getting a new server (Dell PowerEdge 860) with a Xeon 3060. I wonder if I would want SMP guests though... I guess I'll have to do my SMP tasks outside of virtualization if I chose to use KVM.

OpenVZ looks interesting. I'll look more closely when I have the time.

I have a couple of PowerEdges as well, and am trying to figure out the best virtual server solution.  To my mind, having read about various solutions but not tried them, Linux VServer sounds the best for isolating services.  You get a new virtual environment (install only the services you need, updates independant from the host, users and passwords are independant), but it shares the same kernel and the same networking setup - the guest has a single virtual network connection, so firewalling and routing is handled by the host OS.  OpenVZ is a step up - it's more complex, and has virtualised networking.  Both these support SMP if the host is SMP.  KVM is a much bigger step up - it provides a complete virtual environment, with a new kernel in the guest (or even a completely different OS).  It's more expensive in terms of resources, overhead, and time and effort.  But at the moment, it is the only solution supported out of the box in feisty.  I'm not sure whether to go for KVM, or to try and get VServer or OpenVZ patches and compile the kernel myself (it's been a while since I've had to do that!), or just to delay the decision and hope that someone more experianced will finish the VServer and/or OpenVZ support for feisty.

One useful trick for all this is to get apt-cacher configured - at least then you can share common updates.

---

