---
title: "Make GTX 970 use MSI based interrupts = Better Performance!"
date: 2016-01-31
forum: Virtualisation
---

### Post by KillerKelvUK on 2016-01-31
All, not a problem to be solved just sharing some info to help others possibly, I'm sure the comments will tell me if this is old news ;-)

I use PCI passthrou for a number of devices...GFX but also DVB and PSTN/FXO.  I've recently upgrade by old GFX card from an NVIDIA GTX 650 to a 970, as part of the change I moved the cards around the PCI slots and noticed some changes in my linux config.  The first observation was that my DVB card was using an MSI based interrupt (nothing new here I don't think) but my new GFX card wasn't, it was using INTx...I'd not noticed any performance issues with this however the problem was that the interrupt it was using as INTx conflicts with an interrupt my PSTN/FXO card needs.  The PSTN card is an older standard which doesn't support INTx, the bugger needs the entire interrupt to itself, so when my 970 mapped the same interrupt it essentially meant my Elastix VM which has the PSTN card passed through couldn't start.  Anyways the above observations caused me to google the differences between vfio-intx and vfio-msi (cat /proc/interrupts is where you see these) which is where I found Alex's blog about changing a passthrough from INTx to MSI...[https://vfio.blogspot.co.uk/2014/09/vfio-interrupts-and-how-to-coax-windows.html](https://vfio.blogspot.co.uk/2014/09/vfio-interrupts-and-how-to-coax-windows.html)

Alex's blog actually references a post elsewhere ([http://forums.guru3d.com/showthread.php?t=378044](http://forums.guru3d.com/showthread.php?t=378044)) but Alex summarises the article for his readers.  The key bit here is that its a simple Windows registry hack to move the card onto an MSI based interrupt and achieve improved performance.  The key bit I found was that as I was passing through both the video and audio devices of my GTX 970 the Windows registry hack needs to be applied to both.  The results were both a successful change without borking my Windows install as well as moving the vfio interrupt mapping out of the way of my PSTN/FXO card and the Elastix VM using it.

Simple change really but possibly one most won't know to look out for it passthrough works on first attempt

---

