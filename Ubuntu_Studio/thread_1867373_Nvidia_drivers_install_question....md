---
title: "Nvidia drivers install question..."
date: 2011-10-22
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2011-10-22
So I've got a stock Lucid installation.  I've done this many times so I know the problems...

I install the Nvidia driver (recommended) from the "Hardware Drivers" application, install the rt kernel and of course the video driver doesn't work in the newly installed RT kernel.

Sooo, I download the driver directly from Nvidia, run the installer and now I have Nvidia drivers working on the RT kernel, but now the generic kernel is broken and can't use Nvidia, at least until I re-run the installer.

So how do I install the Nvidia driver for both kernels, so that I can switch back and forth from the RT kernel that I record on, and the generic kernel that I do my normal computing on?

I've actually installed the Nvidia driver in the RT kernel and then switched back to install it in the generic.  I don't remember that working out to well.  Now we're talking about the Nvidia driver that you download and have to kill Xserver to run the NVIDIALINUXRUN.sh file, or whatever its called.  That's the one that I've got working on the RT kernel.



Thanks

---

### Post by jejeman on 2011-10-22
At the bottom line you don't need to switch beetween kernels. Use rt kernel all the time.
It's not recommended to use driver from nvidia site. Because it does not register it self with dkms.
Maybe you should try the preempt kernel. It has no problem with nvidia drivers, and for me runs with no problems for audio. 
It's default kernel for ubuntustudio.

---

### Post by pepsifx357 on 2011-10-22
I might be interested in that.  Can you tell me your PC specs and lowest latency at 44100Hz?

I've got a 24 channel mixer that I use instead of internal mixing.  I just use Ardour for recording and editing.  I've been trying to figure out how to get the lowest possible latency.

My meager specs are...

ASUS A8N-32-SLI Deluxe
AMD Athlon X2 4800+
2 gigs of memory
Intel SSD hard drive

A little old, but it has been my Multi Track Recorder for 6 years now.  Mostly Windows....BLAH!!  Talk about a latency killer.

---

### Post by jejeman on 2011-10-23
I have at 48Khz 2ms latency with:

core2duo @ 3 GHz
edirol fa-66

I have at 48Khz 5ms latency with:

core2duo @ 2.33 GHz
internal hda audio

First machine works better, probably because of the audio card. No xruns (the ones that are important) at all. Second one gets occasional xruns when stresed, but only when stressed. Stressed means, playing/mixing full song with effects etc.

---

