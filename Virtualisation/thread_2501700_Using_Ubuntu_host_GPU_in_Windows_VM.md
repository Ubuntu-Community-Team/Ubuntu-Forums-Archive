---
title: "Using Ubuntu host GPU in Windows VM"
date: 2024-10-17
forum: Virtualisation
---

### Post by avsilva on 2024-10-17
I have a pc with an i5 12400 processor with virtualization capacity but no video. Host system is Ubuntu Studio 24.10. I installed a Windows 10 virtual machine using Qemu with VMM. I have a 12gb 3060 Nvidia GPU in the system. Is it possible to allow the Windows VM to use the Nvidia GPU without crashing the system or will I need to upgrade my processor to one that has video? No PCI slot empty for another GPU...
That is alll because I wanna run some graphic apps that has no Linux editions... I'm fairly new to Linux, making my best to switch...

Thanks, 

Andre

---

### Post by TheFu on 2024-10-17
Historically, the host OS needs a dedicated GPU and the guest needs a different dedicated GPU for PCI passthru to work.

There have been attempts to make GPU sharing possible, but I haven't kept up with those efforts.  I think most of them would crash the host after less than 10 minutes.  Intel had VT-g (I think that was their marketing name), but read that project was killed earlier this year.  

If you are new to Linux, running 24.10 is a bad idea. You'll need to replace the OS in 6 months with a new one to keep on a supported release.  Better to have your hostOS running 24.04.x now and screw around with newer OSes inside virtual machines.

---

### Post by avsilva on 2024-10-19
Yeah, I've been testing and found I would need a second gpu...and then it would be kinda locked to the virtual machine...so...not sure about this. Found that at least Capture One will work fine inside a Windows VM, as it's not gpu intensive. DXO Photolab becomes a drag when exporting because it does use it. And also found that Windows VM runs faster in VMWare then in KVM, because the former has some degree of video acceleration. Interesting.

> **TheFu said:**
> Historically, the host OS needs a dedicated GPU and the guest needs a different dedicated GPU for PCI passthru to work.

There have been attempts to make GPU sharing possible, but I haven't kept up with those efforts.  I think most of them would crash the host after less than 10 minutes.  Intel had VT-g (I think that was their marketing name), but read that project was killed earlier this year.  

If you are new to Linux, running 24.10 is a bad idea. You'll need to replace the OS in 6 months with a new one to keep on a supported release.  Better to have your hostOS running 24.04.x now and screw around with newer OSes inside virtual machines.

---

### Post by TheFu on 2024-10-19
> **avsilva said:**
>   And also found that Windows VM runs faster in VMWare then in KVM, because the former has some degree of video acceleration. Interesting.

I found exactly the opposite, but perhaps I know how to tune Linux more than others?  Plus, VMware tripled their costs for our setup in 2010, so that made a good reason to dump them.  Now that broadcom owns them, they've been screwing all their customers.  How much we are each willing to be screwed by a company is a personal choice, of course.

Before you spend too much effort using VMware, be certain you understand exactly what you are in for and agreeing to BEFORE it is too late.

---

### Post by avsilva on 2024-10-19
Well I’m new to this game, and the VMware now is free for personal use and I have no idea what’s going on with the paid version, which seems to be the same as the free, only for commercial use. And I’m sure that someone with good skills in Linux could do better, that’s just not me… I just wanna run my windows/mac photo apps alongside Linux ones…

---

