---
title: "Linux / Windows - 1080p / 4K"
date: 2021-07-28
forum: The Cafe
---

### Post by Shibblet on 2021-07-28
On my recent attempt to bring hardware acceleration to my browser, for things like Stadia, GeForce Now, XCloud, I did some testing with VLC.

VLC will output to VDPAU, in essence, uses the hardware acceleration of my video card for H.264 playback.  My GTX 780ti will support up to 1080p / 60fps playback via VDPAU.  Any other type of video that is not supported via VDPAU, uses the CPU to decode.  This can be beneficial, since my computer does not have hardware acceleration for 4K resolutions and/or VP9.  

So, when VLC or my browser sees a VP9 stream, even one that is up to 4K resolution, I can still play it.  It just takes us a lot more CPU usage. 

However, when testing this on a friends Windows 10 PC (he has the same video card as I do.) using VLC and the Browser, he couldn't play-back 4K video at all.  His computer just wouldn't do it.  We even downloaded some 4K streams just to test if it had something to do with his internet speed, and it did not.  VLC just blockify-stuttered, dropped frames, and continuously re-buffered the entire thing.  Same thing with YouTube in the Browser... it's like his PC just couldn't handle it.

We have identical PC's from the Video Card / Processor / RAM standpoint.  Both GTX 780ti / Intel Core i7-3770 / 16g RAM (He might have faster RAM than I do... not sure.)
I absolutely love when Linux can do something that Windows cannot.  And after this HW Acceleration fiasco, this makes me giggle even more.

Does this have something to do with the Graphics Drivers for Windows 10?  Something with Nvidia's PureVideo?  Why does Ubuntu (or Linux in general) have no problem playing 4K video via the CPU, and Windows does?

---

### Post by bcschmerker on 2021-07-29
**What intel® Express Set for 3rd-Generation Core Processors™ (FCLGA 1155)?**  Microsoft® Windows® 10.0.19041.1 and later, in my experience, is a video memory hog.  My ASUS® CM1630-06 (Advance Micro Devices® Athlon II® x2 220 (2.8 GHz), RS780/SB700 chipset; Antec® TPN750B PSU; 8 GiB DDR3-1333 unbuffered main RAM) has 1 GiB dedicated VRAM aboard the EAH6850DC/2DIS/1GD5 (AMD Barts Pro GPU), but Win 10 uses 4 GiB for video.  The GTX 780 Titanium packs an 876 MHz (928 MHz boost) nVIDIA® GK110 Kepler GPU and 3 GiB 384-bit video memory.  I cannot rule out the need for driver updates on the Win 10 installation.

---

