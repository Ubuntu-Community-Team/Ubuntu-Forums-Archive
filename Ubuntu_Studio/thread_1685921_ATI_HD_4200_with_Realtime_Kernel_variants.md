---
title: "ATI HD 4200 with Realtime Kernel variants"
date: 2011-02-11
forum: Ubuntu Studio
---

### Post by emulashun on 2011-02-11
Greetings all. First I have to say, for the most part I really like Ubuntu Studio with realtime kernel scheduling - my single core 900MHz EEE PC rocks once properly tuned!

Unfortunately, my netbook is just a tad under-powered for the heavy synth work I do. So I decided to go with a quad-core AMD box that I could remote desktop into from a laptop/netbook periodically - most parameters I can modify with a MIDI controller anyway.

System Specs:
-------------
Ubuntu 10.04 LTS
Kernel: 2.6.31-11-rt
Motherboard: MSI 890GXM-G65
CPU: AMD Phenom II quad-core 6MB L3 Cache
RAM: 4GB DDR3 (512MB?? used by video sideport memory)
Video: onboard ATI Radeon HD 4200 (manual says 4290)
Sound: onboard analog/HDMI, and PCI SoundBlaster Live! for soundfonts
HDD: 80GB SATA

The problem I'm experiencing, is that the open-source ATI driver randomly freezes and crashes with the STOCK kernel, and doesn't work AT ALL with the REALTIME kernel. No luck with the PROPRIETARY driver either - stock kernel shows ATI watermark in lower left corner, RT kernel freezes at GDM welcome screen.

I have googled like crazy and come up with nothing for the REALTIME kernel specifically. I've already tried everything from using Ubuntu's "Hardware Drivers" to downloading the latest driver from ATI directly. Nothing appears to work unless you use a "normal" kernel.

All I need is a generic compiz-fusion enabled desktop (or even a generic desktop that JUST works!) that can work with the REALTIME kernel. I can't use anything less than RT, and ATI/NVIDIA are making it difficult (if not impossible) to do that. Seriously, where's the RT kernel love from GPU/Video manufacturers?

If someone even has INSIGHT as to WHY the drivers won't work (i.e. atomic scheduling overhead) with RT very well I'd much appreciate it.

Thanks.

P.S.  On one of my boxes I have a 9500GT with older NVIDIA driver (minor tweaking needed) working with compiz-fusion on RT kernel. Also, Intel Integrated Graphics works out of the box great. So it looks like ATI is mostly at fault here.

P.P.S.  As we speak, I've been working on a collection of scripts/tools that "optimize" performance for realtime audio by adjusting NICE/PRI of JACK and relevant IRQ threads. I'm dying to release them, as soon as I can get NVIDIA/ATI/Intel all working with RT Desktop Environment.

---

### Post by AutoStatic on 2011-02-11
Hello emulashun, 2.6.31-11-rt is not such a good real-time kernel, you could try the far better optimized real-time kernel from [Tango Studios]("http://tangostudio.tuxfamily.org/en"). It's in their lucid-lowlatency repository.

Best,

Jeremy

---

### Post by emulashun on 2011-02-14
AutoStatic, what differences are in the Tango kernel vs. the RT version in Lucid Repo?

Without the RT kernel, say I use a low-latency variant instead, my EEE-PC is incredibly sluggish and behaves the way an average person  would expect an OLD "under-powered" machine to behave.

However, when using an RT kernel, I can adjust BOTH the NICE and PRI values for IRQ's/JACK (and other important threads), which are CRUCIAL for the performance tuning scripts to work.

All I know is that the onboard ATI I have WILL NOT WORK AT ALL on my quad-core system when I use an RT kernel - I can't even CTL+ALT+F1, I have to ssh to reboot or shutdown. I've also checked into possibly buying a CHEAP video card that works with compiz and uses open source drivers, but based on the track records of drivers for newer cards, I can't trust anything with the RT kernel except Intel - which UNFORTUNATELY cannot be found on NEWER AMD Motherboards, or in PCI-e format to my knowledge.

<sigh>
Not trying to troll, but SERIOUSLY, this whole situation with GPU manufacturers playing games with drivers is getting old and it ends up destroying what is otherwise DECENT Audio Software, DECENT  Hardware, and GOOD innovation in general. Too bad I don't have enough kernel knowledge/influence to try and push the RT kernel as the norm, so that hardware/software devs are FORCED to deal with it, instead of side-stepping it and saying "it's special purpose".
</sigh>

---

### Post by emulashun on 2011-02-20
Well, after going through the cycle of removing/installing I dunno how many times, SOMEHOW the "magical elves" in the machine fixed the proprietary driver under System-->Administration-->Hardware Drivers.

So it WORKS, but I only wish I knew the original cause AND the solution.

This ubuntu "magic" is probably going to result in me switching distros after nearly 4 years of using ubuntu, since I need PREDICTABLE and RELIABLE system configurations - video drivers and PulseAudio are the last straw.  

Until I fully transition to another distro though, I'll see what I can do to help those that are stuck with Ubuntu for the time being - especially RT kernel tweaking :)

---

