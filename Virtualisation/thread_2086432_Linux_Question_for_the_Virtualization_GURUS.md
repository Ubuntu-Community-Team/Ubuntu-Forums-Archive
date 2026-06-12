---
title: "Linux Question for the Virtualization GURUS"
date: 2012-11-20
forum: Virtualisation
---

### Post by ghat on 2012-11-20
hi
I am well versed in Linux, even at a system-admin level, but have less experience with virtualization(even though I run a couple of KVM virtualized instances etc)

I am looking at my next "laptop system" and am thinking what the current gen hardware can provide.. I am looking at least at a core i5+ system with 4 or even 8GB RAM. 

My dream is to install a very base linux like debian-minimal or like DSL which can boot up superfast and run the production Windows or Ubuntu as a VM guest. for various reasons the Windows needs to have to run on vmware-player (free) and the Linux can even run using libvirt. I should be able to use the graphics card/accel from the virtualized OS properly.. 

I like the concept of openelec which is a distro specifically made to run XBMC, is there any distro which is specifically made to only run VM's ?

G

---

### Post by wildmanne39 on 2012-11-20
*Thread moved to **Virtualisation**.*

---

### Post by andrew.46 on 2012-11-21
You would get more raw power from a desktop rather than a laptop I suspect. I built my current desktop in part to give me the capability to run multiple vms, some at the same time. For this I would recommend 8gb rather than 4gb ram as this will allow you to be more generous with your memory allowance for the vms. 

I built an 8 core machine, the much maligned Bulldozer 8050 and the ability to allocate multiple cores to each vm is big plus. Perhaps look at the amd 8 core chip: the Piledriver FX-8350. This is the chip I would be buying if I was building right now and the price is quite competitive with intel offerings...

---

### Post by ghat on 2012-11-26
> **andrew.46 said:**
> You would get more raw power from a desktop rather than a laptop I suspect. I built my current desktop in part to give me the capability to run multiple vms, some at the same time. For this I would recommend 8gb rather than 4gb ram as this will allow you to be more generous with your memory allowance for the vms. 

I built an 8 core machine, the much maligned Bulldozer 8050 and the ability to allocate multiple cores to each vm is big plus. Perhaps look at the amd 8 core chip: the Piledriver FX-8350. This is the chip I would be buying if I was building right now and the price is quite competitive with intel offerings...

Well, to get back to the point, I am looking for a OS options not the hardware... 
what options are there for a light weight OS, to run a VM/s

G

---

### Post by DuckHook on 2012-11-26
I am interested in much the same thing and my research has led to the following (very tentative/preliminary) conclusions:

AFAIK there is no ideal DE. They are all designed to provide a complete user exp out of the box and consequently contain a lot of features (bloat?) that is unneeded for a VM. So, I am toying with the idea of doing a minimal install using the 12.04 mini.iso. I can then add just the apps I want/need. Even installing a DE at that point will give me a tighter system than a default desktop install that assumes I want all the bells and whistles.

Re: accelerated graphics

I just posted a related thread on this very subject, which has not generated any replies yet. Once we are past experimenting with the various VMs the next desire for many of us is to pass through video requests on the VM client to the hardware GPU instead of having to settle for the virtualized graphics adapter on the VM. The sources of knowledge for doing this are obscure and very hard to find anywhere on the net. However, my explorations indicate that Xen is the only virtualizer which allows this for now. Ergo, my question about the better VM: KVM or Xen?

I really have no answers for you. Just common purpose and solidarity in desiring some knowledge/direction.

---

