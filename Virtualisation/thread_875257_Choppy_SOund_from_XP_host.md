---
title: "Choppy SOund from XP host"
date: 2008-07-30
forum: Virtualisation
---

### Post by dupreesdiamond on 2008-07-30
non OS VirtualBox 1.6.2.  
Ubuntu Hardy Host
XP SP2 Guest

USB Headphones and Mic. (not sure of the brand, they came with ROsetta stone software)

Using both OSS and PULSE Audio the sound, from guest, coming through is choppy with clicks throughout.  

One interesting note is that no matter what I try I cannot get any sound to come from the UBUNTU host via the USB headset (read and tried several things listed in these forums; but this is another topic, I think.)

---

### Post by dupreesdiamond on 2008-07-30
Ok so I figured it out...after reading all the sound posts here in ubuntu forums for the 3rd time...

So the problem with Virtual Box is that I was mounting hte USB device directly into the GUEST system and in this case, apparently, the guest doesn't cache the sound so you get the clipping.

So after getting the USB headset to work correctly in the host (which simply meant configuring AMAROK to push sound out to ALSA) everything in the GUEST works just fine.

Thanks.

---

