---
title: "Is my PC Spec powerful enough to run Windows 11 in a Virtual Machine?"
date: 2024-06-03
forum: Virtualisation
---

### Post by nictu2 on 2024-06-03
Hello,

I'm thinking of running Windows 11 in a virtual machine, and would like to know if my PC is powerful enough. 
The PC spec is:

AMD Ryzen 5 5600X
24Gb RAM
Nvidia GTX1050 ti

Windows 11 would be used for: 

General office work activities including Zoom video calls & conferencing. 
Photo and Video editing with Adobe suite and an old version (V.14) of Davinci Resolve.
I'll also be using Steam for gaming, though not high performance gaming.
I would expect to be running Anti Virus.

Any thoughts and advice you can give would be much appreciated. Thank you.

---

### Post by Paddy Landau on 2024-06-03
I think that you would be fine with that. There's a simple way to find out, though &#8212; try it and see! If it doesn't work well, you can simply delete the VM.

For the antivirus, I'd imagine that the default Windows Security, which seems to have a good reputation, would suffice.

Steam and Zoom both have native Linux implementations, so perhaps you'd like to use the Linux versions instead? It's up to you, of course; you might have reasons why you specifically want to use Windows for those two.

---

### Post by nicolasdentremont on 2024-06-03
My computer is less powerful than that and it runs Windows 11 in a Virtual Machine without issue. I used Virtual Box and that has a limit of 256 MB of video memory for Windows 11 so if that's what you're using, gaming may not work unless they're really old games.

But like was said above, Steam is available for Linux and many games will work just fine like that.

---

### Post by lammert-nijhof on 2024-06-12
I run Windows 11 Pro in a Virtualbox VM on a Ryzen 3 2200G (4C4T; 3.7GHz) and 16GB of DDR4 (3000MHz). the storage is a 512GB nvme-SSD (3400/2300MB/s).  The Host OS is Ubuntu and I run the VMs from OpenZFS with the L1ARC memory cache limited to max 4GB.  I use Windows with MS-Edge; Office stuff; Microsoft Defender and once per week I run the Windows updates. It is responsive for this type of work, because the disk-io runs from L1ARC memory cache.  I have a hit rated of 99% for disk-io from the L1ARC.  The system boots in ~50 seconds and most of the time is used for lz4 decompression of the L1ARC or nvme-SSD.  Your CPU is at least 3x faster than mine.

---

