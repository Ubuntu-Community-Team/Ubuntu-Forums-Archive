---
title: "Hardware, buntu, or release version - what makes the difference?"
date: 2012-01-19
forum: The Cafe
---

### Post by 23senick on 2012-01-19
I've been running an Acer Aspire One A110L on Xubuntu 10.04 LTS for a couple of years.  Have upped the RAM (1.5gb). It runs - generally - like a dream, reliable, boots quickly, very fast, good wifi. Typically resources used hover around 150mb so it has loads in reserve.  Only issues really are hard drive is SSD so have tweaked fstab, i/o scheduler and firefox to minimise writing to disk, but you can't eliminate this completelly and the result is once in a while I have to wait for hard disk to catch up. Cheese has never really worked, but I stuck with LTS to minimise re-writes to SSD, which aren't supposed to stand up as well as conventional hard disks

Encoraged by this happy experience I decided, when I needed a bigger screen, to try Ubuntu 11.10 64 bit on HP1 4020 with 4gb RAM.  Hmm, not so good. Had a battle with the wifi which I eventually overcame. Though the wifi frequently fails to connect to router - I have to disconnect, wait a bit then reconnect.  The mouse sometimes freezes.  Seems to take longer to load programmes than the Acer. Ubuntu Software Centre takes an age to load.  Resources used hovers about 450-600mb.  Overall feels a bit clunky.  At least Cheese works.

Thought this might be an interesting case study. What's making the difference? Software?  Is it just Xubuntu runs well on Acer Aspire One?  Will Ubuntu catch up with the hardware and make the HP run better in future?  Should I change the buntu on my HP?  Hardware? Is the HP a lemon?  Seems to run ok on Windows 7. Thoughts anyone?

---

### Post by 3Miro on 2012-01-19
Ubuntu with Gnome will take more resources then Xubuntu with XFCE. 11.10 and newer come with Unity and Gnome 3 and it uses even more resources than Gnome 2.

The wifi sounds like a hardware issue, some wifi devices simply don't have proper drivers.

Newer Ubuntu Software Center does load slower than the older ones.

What is the video on the two machines, usually this is the biggest reason for difference in performance.

---

### Post by 23senick on 2012-01-19
You mean video card or apps? Sorry I'm enthusiastic, but still a newby. Can post more details but it's getting late (or early) here in the UK

---

### Post by 3Miro on 2012-01-19
> **23senick said:**
> You mean video card or apps? Sorry I'm enthusiastic, but still a newby. Can post more details but it's getting late (or early) here in the UK

Sorry I mean the video card. The apps should be independent from buntu and DE versions (maybe a bit higher RAM at most), the apps should depend only on hardware and drivers, and the weak point of Linux is the usually the video card.

---

### Post by 23senick on 2012-01-19
Here's the HP from lspci -v

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9806 (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

and the Acer

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME  Express Integrated Graphics Controller (rev 03) 
    Subsystem: Acer Incorporated [ALI] Device 015b 
    Flags: bus master, fast devsel, latency 0, IRQ 16 
    Memory at 78480000 (32-bit, non-prefetchable) [size=512K] 
    I/O ports at 60c0 [size=8] 
    Memory at 60000000 (32-bit, prefetchable) [size=256M] 
    Memory at 78500000 (32-bit, non-prefetchable) [size=256K] 
    Capabilities: <access denied> 
    Kernel driver in use: i915 
    Kernel modules: i915

---

