---
title: "Vista doesn't show USB mics in VirtualBox"
date: 2009-01-03
forum: Virtualisation
---

### Post by dansan on 2009-01-03
I am using the VirtualBox version 2.1.0 

The title summarizes the problem. On my laptop a VM running WinXP recognizes my usb mics without a hitch. So nothing is wrong with my setup in Hardy (i.e., vbusers and fstab) but a VM running Vista does not register usb mics. This makes using WSR impossible. 

My hardware specs are shown in the attachment "Hardware.txt" I think this laptop should be able to handle Vista, but something is wrong.

1. I can't get an installation of Vista inside VB to finish on the laptop. I have to let my desktop model at work create the .vdi. This .vdi works perfectly at work. All the usb devices defined in VB are set up by Vista and work properly, including usb mics.

2. When I copy the .vdi to the laptop, Vista starts normally [del: and installs drivers for the usb mics] but fails to install drivers for usb mics, and Vista doesn't show them in Audio Devices. The attachment "Screenshot..." shows how I've set up the VM's options. "Sound" in Devices shows "USB" with a yellow triangle.

NEW: I installed the audio Hotfix for Vista. No change. I have copied the USBAUDIO.SYS in WinXP and gone through the tedious process of taking over ownership of relevant folders in Vista, renaming those copies of the Vista USBAUDIO.SYS and copying in the XP-version to the relevant folders. 

What is the difference between my desktop and laptop? The desktop PC runs at 2+GHz, while the laptop's processor is 1.6GHz, but this doesn't explain why Vista on the desktop sees the mics, but Vista on the laptop doesn't. By the way, the Vista Home Premium disk is mine. It came with the laptop. I insisted on that. I later decided to move to Ubuntu, and VirtualBox gave me a way to use some additional apps like WSR. At least, that's what I hope.

Before transferring the .vdi to the laptop, I ran Windows Update and it installed a ton but not SP1. Could this be a clue? I read that SP1 cures some audio problems. I still can't see why all the mics are registered when I'm running Vista in VirtualBox on my desktop installation of Hardy, but this fails on the laptop.

Any ideas?

---

### Post by dansan on 2009-01-05
Well, my problem has been looked at 50 times, and no one has jumped in. Meanwhile I've gathered more info. For example, using my desktop, I have successfully installed SP1 to the same vdi as on my laptop, and I have no trouble getting mics recognized and using WSR on the desktop. Note, this was also true before I installed SP1.

So, let me change my questions:

Does anyone with a similar PC (1.66GHz, etc.) run Vista in VB? Using USB mics? With WSR? If so, who makes it? 

Thanks for any clues.

---

### Post by dansan on 2009-01-07
The number of views since my last entry has now nearly doubled, and there have still not been any ideas. I have dug up one additional piece of information that I did not have when I first started this thread. My local computer shop that supplied me with the Vista disc has admitted to me that it is generic, not one specifically for setting up Vista on my laptop (Acer Aspire). Doh! Ding-dong! While this has not been a factor in setting up XP VMs, maybe it's a deal-breaker for the Vista beast.

Let's say that this thread is suspended until I have time to install all of the Acer site's Vista drivers.

---

### Post by dansan on 2009-01-08
Installing Acer Aspire drivers - pretty much a shot in dark, anyway - did not solve the problem, so I guess I'm stumped for now. If anything, this exercise added problems, like destabilizing the display (It randomly goes paisley, now, and freezes Vista.  Nice.) I strongly suspect that Vista's usbaudio.sys is the original culprit, and installing the Hotfix or SP1 hasn't solved the problem. 

Nor does copying an old version of this file into Vista from XP. I'm not sure I did this correctly, anyway. I just tried to follow stuff written by others.

No matter what I've tried, the result is always that the usb mics do not show up in Vista, and the Control Panel\Devices shows USB Audio Device with a yellow triangle. In XP, on the other hand, everything works.

This is my final cry for help here.

Anyone?

---

