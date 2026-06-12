---
title: "Hardware Virtualisation"
date: 2008-06-12
forum: Virtualisation
---

### Post by rossco on 2008-06-12
Hi all,

I just had a general question about virtualisation before I embark on my initiation.  I was wondering about hardware virtualisation whether all hardware is made available to the virtual machines.  I know they have virtualised CPUs, Ram, NIC etc but I was wondering about extension cards eg TV Cards, Sound cards etc?

Basically I like the idea of using virtual machines because if/when I manage to wreck my system it would be great to just kill it and reload the image and start from scratch.  I am a newbie and the number of times I have had to reinstall Ubuntu when I have tried to  do something is rediculous.  What I'd like to do is run a virtual MythTv backend but I want to confirm that the TV card will be accessible to it.  

I've tried to find this info on the web but most of it revolves around setting up networking and not specifically whether hardware will be available.

Thanks

Ross

---

### Post by igwk on 2008-06-12
Hi rossco, as far as I know, your virtual machines will not be able to get direct access to hardware like a TV card.  Generally virtual machines access virtual devices, which the virtual machine monitor (VMM) translates to using the real physical devices for you, so if the VMM doesn't virtualize a TV card device to match your physical TV card device, you're out of luck.

The newer Intel processors and chipsets support a technology called VT-d (Virtualization Technology for Directed I/O), which in theory should allow virtual machines to have direct access to some hardware, but as of now, I don't know of any freely available VMM's that support this.

---

### Post by rossco on 2008-06-14
Hi Igwk,

Thanks for that info, I suspected that was the case, I just wanted to make sure before going ahead.  I think one way I came across to get round the issue is to use an external piece of hardware they specifically referred to a network streaming device which I can't remember the name of.  It's not available where I live anyway.  What about if I got a USB tuner would I be able to access it from the virtual machine and get around the issue that way?  I remember reading somewhere that USB devices can be accessed from the VM.

Thanks.

---

### Post by philinux on 2008-06-15
> **rossco said:**
> Hi Igwk,

Thanks for that info, I suspected that was the case, I just wanted to make sure before going ahead.  I think one way I came across to get round the issue is to use an external piece of hardware they specifically referred to a network streaming device which I can't remember the name of.  It's not available where I live anyway.  What about if I got a USB tuner would I be able to access it from the virtual machine and get around the issue that way?  I remember reading somewhere that USB devices can be accessed from the VM.

Thanks.

Only got into this last week. My final problem was usb. I've now got access to my webcam and 4gig usb stick. Using VBox 1.6.2 excellent stuff and fairly straightforward.

---

