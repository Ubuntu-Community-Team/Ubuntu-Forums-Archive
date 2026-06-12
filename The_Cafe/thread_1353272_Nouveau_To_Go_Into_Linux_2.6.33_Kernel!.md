---
title: "Nouveau To Go Into Linux 2.6.33 Kernel!"
date: 2009-12-12
forum: The Cafe
---

### Post by Chame_Wizard on 2009-12-12
:o
> Wow, the day has come, open-source fans with NVIDIA hardware that run Linux have quite the present this holiday season. Yesterday there was the first DRM pull request for the Linux 2.6.33 kernel that brought many changes to the ATI/AMD and Intel DRM along with other core DRM improvements (such as to the TTM memory manager). These changes were quite significant and we even called it a great present in the Linux 2.6.33 kernel. 

[Link]("http://www.phoronix.com/scan.php?page=news_item&px=Nzc5NQ")

That's fast,cause I readied that Torvalds himself was pissed off for not being included in 2.6.32 .:P

---

### Post by chris200x9 on 2009-12-12
awesome, maybe i can go 100% FOSS

---

### Post by Keyper7 on 2009-12-12
As a heavy OpenGL user, I don't see myself leaving the NVIDIA proprietary driver soon, as Nouveau's 3D capabilities are just in the beggining.

That said, the Linux video is quickly progressing and NVIDIA's proprietary driver is losing momentum. NVIDIA always compensated the fact that they are closed-source with good 3D capabilities, constant updates and extra features like VDPAU. But they are progressing very slowly in standard features such as framebuffer and RandR and have no immediate plans of supporting KMS.

As I watch the progress of Intel and ATI drivers, for the first time I'm feeling that, despite still reigning in the 3D realm, NVIDIA is starting to lag behind in terms of overall features and integration. This is going to be particularly evident now that the final piece for building a flicker-free experience on Linux (the KMS) is in place and a lot of distributions of make use of it, Ubuntu included.

I really appreciate the work NVIDIA has done so far, but they should be careful from this point on to not let the price for good 3D acceleration rise too much.

---

### Post by SunnyRabbiera on 2009-12-12
This is very good.
Maybe ATI will push out more open drivers next that will heal some more issues.
Proper open source support for nvidia and ATI might be right around the corner.

---

### Post by BigSilly on 2009-12-12
I'm no expert, but could this mean KMS for Nvidia users during boot to give us the new boot sequences, then a possible switch to the proprietary alternative afterwards? It's clumsy, but wouldn't this be useful to those of us who use Nvidia and want to have our cake and eat it on Linux.

---

### Post by Regenweald on 2009-12-12
> **BigSilly said:**
> I'm no expert, but could this mean KMS for Nvidia users during boot to give us the new boot sequences, then a possible switch to the proprietary alternative afterwards? It's clumsy, but wouldn't this be useful to those of us who use Nvidia and want to have our cake and eat it on Linux.

Seems like a *lot* of unnecessary development hours for a pretty boot though. I tried nouveau for a few months this year and it was fast, light and stable. Will be great soon, but for now i'll stick to the binary, nouveau had some 2d issues with video and well.... no 3D.
Good thing is, with the bigger distros shipping, there will be more testing and user feedback. Which will be great for the devs. Although, for the areas in which nouveau lacks, I can just imagine the whining posts already ;)

---

### Post by Chame_Wizard on 2009-12-12
Everything will work fine.:P

---

### Post by murderslastcrow on 2009-12-12
I hope nouveau will improve soon and include some compositing. This is a big problem for NVidia-based graphics on PowerPC Macs. (G4s are still popular, and could benefit a lot from compositing in Linux to make them more epic-looking than the newer Macs).

Also, KMS would be nice. We need to get rid of the flicker.

---

### Post by gnomeuser on 2009-12-25
> **murderslastcrow said:**
> I hope nouveau will improve soon and include some compositing. This is a big problem for NVidia-based graphics on PowerPC Macs. (G4s are still popular, and could benefit a lot from compositing in Linux to make them more epic-looking than the newer Macs).

Also, KMS would be nice. We need to get rid of the flicker.

A number of nvidia cards already support and run Compiz using the Gallium driver. This isn't ready for primetime but users can and d use this today. 

The Nouveau driver also supports KMS, to see this in action today, get a Fedora 12 LiveCD (or an upcoming Lucid LiveCD since the Nouveau driver is being merged and supported in Lucid).

---

### Post by phrostbyte on 2009-12-25
> **Regenweald said:**
> Seems like a *lot* of unnecessary development hours for a pretty boot though. I tried nouveau for a few months this year and it was fast, light and stable. Will be great soon, but for now i'll stick to the binary, nouveau had some 2d issues with video and well.... no 3D.
Good thing is, with the bigger distros shipping, there will be more testing and user feedback. Which will be great for the devs. Although, for the areas in which nouveau lacks, I can just imagine the whining posts already ;)

It has experimental 3D support (for instance, glxgears seems to be accelerated), but it's definitely not as far developed as the binary driver. :)

---

### Post by sertse on 2009-12-25
I wish someone in nouveau development would focus on the power saving features..

---

