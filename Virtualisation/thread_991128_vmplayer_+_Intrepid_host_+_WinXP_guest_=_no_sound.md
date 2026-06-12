---
title: "vmplayer + Intrepid host + WinXP guest = no sound"
date: 2008-11-23
forum: Virtualisation
---

### Post by orzechowskid on 2008-11-23
howdy,

I'm running VMware Player 2.5.0-118166 on my Intrepid machine, with a WinXP guest OS.  Everything's up and running fine except for sound.  When I boot the guest OS, vmplayer gives me an error box saying "Failed to open sound device /dev/dsp1: invalid argument".  Older versions of VMWare Player have worked fine out of the box (I only needed a newer version due to incompatibilities with the newest kernel), so I'm not quite sure what I need to do or where to look.

Thanks for any help

---

### Post by j_kubik on 2008-12-09
I had the same problem. It turned out that /dev/dsp1 wasn't even my sound card;).
Try setting /dev/dsp as your sound card.

---

### Post by reagle on 2008-12-22
> **j_kubik said:**
> I had the same problem. It turned out that /dev/dsp1 wasn't even my sound card;).
Try setting /dev/dsp as your sound card.

How do you set it to dsp? In the VM's vmx file I change the sounds.fileName = "/dev/dsp", but there's no change. Upon boot, it's still looking for dsp1.

---

### Post by orzechowskid on 2009-02-16
aha!

open up your VM's .vmx file and make sure sound.filename is set to "/dev/dsp" and sound.autodetect is set to "FALSE".  You should now be able to get audio out of your VM.

I can't play music in both the VM and the host OS at the same time; I'll have to look into that sometime, but this is good enough for now.

---

### Post by sanitycheck on 2009-04-07
I had the same problem in VMWare Workstation running under Hardy 8.04 i386, with WinXP guest.  I just upgraded to Workstation 6.5.2, but autodetect still failed.  In Workstation, you get a "Edit Virtual Machine Settings" button.  Under the Sound Card setting, I got it to work from changing the default Auto Detect setting to /dev/dsp (it was looking for /dev/dsp1 when it failed).  I'm pretty sure I tried this setting under Workstation 6.5.1 a few months back and it didn't fix the problem.

---

