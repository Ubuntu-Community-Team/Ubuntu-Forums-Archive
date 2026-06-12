---
title: "Compaq A900 Series: A931nr on Jaunty"
date: 2009-09-08
forum: Wine
---

### Post by jasonditz on 2009-09-08
This isn't the newest system in the world but I still see them in stores every once in awhile (dirt cheap too) so I thought I'd report my findings:

Processor: Comes with a Dual-Core T2370 Pentium. Despite the fact that it shipped with a 32-bit version of Vista from the factory, it IS a 64-bit processor, and the AMD64 version of Jaunty should be used. 

Memory: Ships with 3 GB which is frankly plenty. This was the practical limit with a 32-bit OS, but since it is running 64-bit Jaunty now it seems... possible... that it supports an upgrade at least to 4. 

GPU: The Intel X3100. Works fabulously and out-of-the-box for Ubuntu stuff. Drivers are not very mature for OpenGL support, so not a great choice for 3D games in Wine (though Wine will run 2D games like Patrician 2 and EHM 07 like a dream).

Sound: Intel 81801H. Works perfectly out of the box. Built-in speakers are also fine

Ethernet: Realtek 8139C+ (rev 10). Works perfectly out of the box. Seems like a trend...

Wifi: Atheros AR242x. The scary Atheros wifi chipset gave me nightmares in OpenSuSE 11 (even with madwifi I never got it running satisfactorily). In Jaunty it too works out of the box, and found and connected to my router almost instantly (unlike my Hardy-based Netbook which takes almost a minute to find it).

Media Reader: Works fine for SD-Cards, hasn't been tried with anything else. 

S-Video Out: hasn't been tried either. C'mon, who uses these things? 

DVD Drive: 8x DVD+-R/RW Dual Layer. This drive actually used to give me a lot of trouble in Vista, creating a lot of coasters when I wanted to make backup discs and even read errors when I tried to install DVD-based software. I thought the hardware might be faulty, but since installing Jaunty the errors have totally vanished. 

Of course getting DVD movie playback working wasn't the most obvious thing in the world. Here's a hint:

sudo apt-get install ubuntu-restricted-extras

Since then not only does playback work, but Handbrake does too. 


Conclusion: The only thing that doesn't work out of the box is that little Wifi button on the top left of the keyboard, which is supposed to turn blue when connected. It's always orange and pressing it doesn't cause the Wifi to disconnect. This is probably a trivial fix, but I just plain don't care.

---

