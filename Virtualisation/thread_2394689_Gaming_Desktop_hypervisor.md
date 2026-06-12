---
title: "Gaming Desktop hypervisor"
date: 2018-06-19
forum: Virtualisation
---

### Post by dimplewidget on 2018-06-19
I'm looking into Virtualizing to play my windows games that won't play with wine (they did until I went from a nvidia 730 to a 1050) but I can play some games under the 1050 that I couldn't with the 730 but Virtualbox is still very limited in video.  But I read that KVM could allow me to assign one full videocard to the virtualized os while the other is used by the host.   using the nouveao driver to work two monitors with 2 cards is not cutting it a and that is  first hurddle is figuring out how tdo I get the 340 drivers and the 384 drivers installed at the same time?

---

### Post by TheFu on 2018-06-23
It has been 3 days without any reply, so I'll reply with what little I think I know.  Don't trust what I say, because
a) I don't game
b) I don't do GPU passthru
c) my newest GPU that isn't onboard intel is an nVidia 430GT

But I do use KVM and used vbox for a few years back around 2011.

Last time I checked. KVM supports PCI passthru of selected GPUs, provided the BIOS and motherboard are compatible. VT-d must be enabled.
The card used by the VM cannot be used by the host.  The VM must have exclusive lock on the GPU and the drivers for it.   So you shouldn't be loading both GPU drivers into the same OS.

Last time I looked, which was long ago, there were about 15 pgs of steps to get GPU passthru working for a linux host and a Windows guest.  Maybe that is much easier now?   IDK.

---

### Post by KillerKelvUK on 2018-06-24
So its a lot simpler now with the later versions of qemu, libvirt and the use of vfio-pci...the longer articles are usually explaining the why of it which if you aren't interested in then you can skip.   Anyway this ([http://vfio.blogspot.com/2015/05/vfio-gpu-how-to-series-part-1-hardware.html](http://vfio.blogspot.com/2015/05/vfio-gpu-how-to-series-part-1-hardware.html)) blog has a 5 part series of articles on the HOW-TO but also the WHY...he's one of the dev's behind kvm and vfio and GFX passthrough.

---

### Post by dimplewidget on 2018-06-24
Thank you very much for your time I was thinking now I wonder if I have to get two drivers working on the host or can I just install the drivers for the pass thru on the client? I'll find out soon enough

---

### Post by KillerKelvUK on 2018-06-25
So you cannot load the nvidia/nouvea modules on the host for the card you wish to passthrough or rather you do not want those modules claiming the card.  Long story short there is a new module/driver needed on the host for passthrough to work called vfio-pci.  You want this module loading at host boot time and you want to get it to claim/bind to the card you wish to passthrough, the actual nvidia drivers for the passthrough card then only get deployed into the guest.

---

