---
title: "Sibelius / Cubase / Kontakt / PLAY ?"
date: 2013-06-07
forum: Virtualisation
---

### Post by Coder88 on 2013-06-07
Has anybody had any success in getting Sibelius (I have version 6 and 7), Kontakt, Cubase, or PLAY to work in a virtualized Windows setup on linux? Just wondering if this might be possible, hoping to hear some success stories on any of these music composition software apps for Windows, if anybody has them running in a virtualized Windows OS on linux?

---

### Post by heiko_s on 2013-06-07
I have no experience with these specific programs, but you may expect some problems. Audio is a real-time application and depending on the CPU resources and how they are shared with the guest etc. there may occasionally be some lag. You'd have to experiment with it to see how it works.

I know that Xen has got some new CPU scheduler options that are supposed to improve real-time support. I guess KVM could also be an option, perhaps even Virtualbox.

Currently the advantage of Xen or KVM is that you can pass through the PCI devices to the guest (in your case the sound devices), so that Windows will be able to use its native drivers or the drivers of the manufacturer. This feature has some hardware requirements: VT-d for Intel CPUs, and IOMMU or AMD-Vi for AMD CPUs.

---

### Post by c00kie55 on 2013-06-15
Yes i have tried Cubase 7 in a KVM virtual machine it works but it also costs.. Becourse of the dongle based license i had to pass-through one of mine USB controllers to the virtual machine (for this to work motherboard must support virtual-d) 
luckily i didn't need to blacklist the controller, as it is hot-plug able in KVM.(if Cubase wasn't dongle based it would work in wine) 

I have both tried to use netjack for audio and midi and to pass-through my sound card (M-Audio44) and usb RemoteSL midi Keyboard. for latency the pass-through method is preferable be-course netjack adds another latency layer on top of the workflow
but when in comes to flexibility, a combination of Laddish, netjack and Netjack/Jack for windows is real cool as you can route basely everything. 

for performance, i pinned 4 cores and used 16gb of ram. (8gb is probaly enough) to the virtual machine. I also used disk/by-id method for the hard disk and virtio for the network driver i then fine tuned a power theme on windows be-course Cubase power theme seamed to eat my host CPU.. 

passing-through my graphics adapter seamed to make windows a little smother as the GPU was handling the graphics but i only have 1 monitor, so i had to switch display mode to use the virtual machine also mouse seamed to lack so i also had to pass-through a mouse so for me it was easier just to use a virtual GPU. If it was possible to passthrough GPU to a console i would probably use that.

---

