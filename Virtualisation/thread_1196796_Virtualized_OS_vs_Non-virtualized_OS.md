---
title: "Virtualized OS vs Non-virtualized OS"
date: 2009-06-25
forum: Virtualisation
---

### Post by LesterPalooza on 2009-06-25
Is running Windows 7 (dual-boot) better than virtualizing windows 7 on VirtualBox? Let's say, both virtualized and actual windows 7 run on the same hardware. Virtualized windows 7 run on 2Gb ram, 100Gb HD, and video acceleration.

---

### Post by christopher.adams360 on 2009-06-25
If you are asking whether dual-booting would be faster, then yes, it would be much faster than virtualizing.

---

### Post by LesterPalooza on 2009-06-25
But what if I alot a huge chunk of RAM for the virtualized OS? Wouldn't that make the experience feel like there is no layer between the hardware and the virtualized OS?

---

### Post by Dragonbite on 2009-06-25
As I understand it, basically with dual-boot you get 100% of the resources available to you.  

If you virtualize then you have 
(100%) - (Host OS[Ubuntu,whatever])- (VM app[VMWare,VB,etc]) 
which will be less than 100% no matter how far you trim it.

---

### Post by Therion on 2009-06-25
I've done both (VM and dual-boot) and honestly, XP runs damn quick in a VM.  Further, find it a heck of lot more convenient being able to run both OS'es simultaneously rather than having to boot into one, and then the other.  Can't speak to Win7 specifically, though, as I've not tried it.

Typically I only needed something in XP for a quick minute and wanted to get back to my 'buntu as quick as I could.  THAT'S when you want to use a VM, in my opinion.

---

### Post by anonmars on 2009-06-25
> **LesterPalooza said:**
> But what if I alot a huge chunk of RAM for the virtualized OS? Wouldn't that make the experience feel like there is no layer between the hardware and the virtualized OS?
Not entirely. If you don't have any hardware support for virtualization then there is some serious overhead. You may not notice it that much if you've got beefy hardware and you're not doing too much on your host or guest (just web browsing, listening to music, etc).

If your hypervisor (ie virtual box) is making use of intel-vt then it helps some. With intel-vt (or amd-v) your guest is able to run on the processor (no emulation or paravirtualization necessary), thus with something like Xen you don't have to have a patched guest OS. However, certain instructions may still cause the processor to transfer control back to the hypervisor to validate what the guest is trying to do. And guest OS's don't have access to hardware page tables, so if there's a miss it must be handled by the VMM.

With Nehalem they're adding extended page tables (among some other things) which allows the TLB to keep track of individual guest OS's virtual and physical memory reducing some of the memory management overhead.

IO is a whole different ballgame and if you're running a VM there is definitely IO overhead (at this time) because individual IO devices haven't progressed with processors in adding support for virtualization.

In summary: IO will introduce overhead no matter what (disk, network, etc.). If you have no hardware support then something along the lines of modifying the guest OS kernel or binary translation has to happen and it's going to slow you down quite a bit. If you have intel VT, you'll get some of a performance boost (maybe not huge, my understanding was that VMware did a good job with the binary translation for instance). And if you have a Nehalem, right on, that's the best you can do for virtualization at this time.

---

### Post by jimv on 2009-06-25
It depends what you are trying to do.  If you just need to use a few Windows apps, go with virtualization.  If you want to play 3D games, dual boot.

---

