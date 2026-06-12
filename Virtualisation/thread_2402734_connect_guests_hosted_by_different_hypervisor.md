---
title: "connect guests hosted by different hypervisor"
date: 2018-10-03
forum: Virtualisation
---

### Post by luca31 on 2018-10-03
Hi all I'm just a little confused about how to link guests hosted by different hypervisor on the same host. 
In my laptop i play a bit trying different hypervisor. I managed to install some guests using virtualbox exploiting pxe installation from a guest in a isoleted (host-only) network.
Now I'm studying kvm and I'd like to make pxe installation of kvm guests exploiting the service available on guests on virtualbox
I'm thinking to setup the two networks in bridged mode, so I'll end up having two different virtual bridge linked to a phisical interface (should be the same phisical interface)
but I'm wondering if that's enough to make the hosts connect each other.. 
what the best strategies? Could you recommend some article?
 

thanks a lot 

Luca

---

### Post by TheFu on 2018-10-05
My only recommendation is not to have 2 hypervisors running on the same physical hardware.

---

### Post by luca31 on 2018-10-08
Hi, could i ask why not? for a performance reason or do you think the two hypervisors could interfere?
Anyway I'm only making some tests on my laptop, so I'm not too worried about performance...
I discovered that virtualbox use netfilter to make bridging (I suppose it means that the code of the virtual network driver injects trafic on the real ethernet device), hence no virtual bridge is created on the host.   
I've also read a old and clarifying article on tun tap device [https://backreference.org/&#8230;/03/26/tuntap-interface-tutorial/]("https://backreference.org/2010/03/26/tuntap-interface-tutorial/")
but it doesn't seem the tun/tap device be exploited by the hypervisor anymore, what a pity (just when I figured out how they work under the hood)

---

### Post by DuckHook on 2018-10-08
> **luca31 said:**
> Hi, could i ask why not? for a performance reason or do you think the two hypervisors could interfere?
I doubt you will be able to get it to work. Modern hypervisors are not just abstractions, but hook into the actual CPU to work. This is required for performance. AFAIK two hypervisors cannot hook into the same CPU without corrupting each other, hence are not allowed to run concurrently. If you manage to get this to work, you will be the first.

---

### Post by kevin160 on 2018-10-15
Nonsense.  I run multiple hypervisors without issues.  Just to double check, I just fired up a 4 core Ubuntu Mate 18.04 in VirtualBox, 2 instances of single core Ubuntu Server in multipass, and a 4 core Alpine Linux instance in vmware.  That's 10 virtual cores on an old (4c/8t) i7 macbook from 2012.  

Yes, having them talk to each other is a challenge with NAT being the default in most hypervisor software, but that's definitely possible too.

---

